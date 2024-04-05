Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


17. Assemblies
18. Reflection and Metadata
19. Dynamic Programming
25h 47m remaining
Chapter 18. Reflection and Metadata
As we saw in Chapter 17, a C# program compiles into an assembly that includes metadata, compiled code, and resources. Inspecting the metadata and compiled code at runtime is called reflection.

The compiled code in an assembly contains almost all of the content of the original source code. Some information is lost, such as local variable names, comments, and preprocessor directives. However, reflection can access pretty much everything else, even making it possible to write a decompiler.

Many of the services available in .NET and exposed via C# (such as dynamic binding, serialization, and data binding) depend on the presence of metadata. Your own programs can also take advantage of this metadata and even extend it with new information using custom attributes. The System.Reflection namespace houses the reflection API. It is also possible at runtime to dynamically create new metadata and executable instructions in Intermediate Language (IL) via the classes in the System.Reflection.Emit namespace.

The examples in this chapter assume that you import the System and Sys⁠tem.Reflection as well as System.Reflection.Emit namespaces.

NOTE
When we use the term “dynamically” in this chapter, we mean using reflection to perform some task whose type safety is enforced only at runtime. This is similar in principle to dynamic binding via C#’s dynamic keyword, although the mechanism and functionality is different.

Dynamic binding is much easier to use and employs the Dynamic Language Runtime (DLR) for dynamic language interoperability. Reflection is relatively clumsy to use, but it is more flexible in terms of what you can do with the CLR. For instance, reflection lets you obtain lists of types and members, instantiate an object whose name comes from a string, and build assemblies on the fly.

Reflecting and Activating Types
In this section, we examine how to obtain a Type, inspect its metadata, and use it to dynamically instantiate an object.

Obtaining a Type
An instance of System.Type represents the metadata for a type. Because Type is widely used, it lives in the System namespace rather than the System.Reflection namespace.

You can get an instance of a System.Type by calling GetType on any object or with C#’s typeof operator:

Type t1 = DateTime.Now.GetType();     // Type obtained at runtime
Type t2 = typeof (DateTime);          // Type obtained at compile time
You can use typeof to obtain array types and generic types, as follows:

Type t3 = typeof (DateTime[]);          // 1-d Array type
Type t4 = typeof (DateTime[,]);         // 2-d Array type
Type t5 = typeof (Dictionary<int,int>); // Closed generic type
Type t6 = typeof (Dictionary<,>);       // Unbound generic type
You can also retrieve a Type by name. If you have a reference to its Assembly, call Assembly.GetType (we describe this further in the section “Reflecting Assemblies”):

Type t = Assembly.GetExecutingAssembly().GetType ("Demos.TestProgram");
If you don’t have an Assembly object, you can obtain a type through its assembly qualified name (the type’s full name followed by the assembly’s fully or partially qualified name). The assembly implicitly loads as if you called Assembly.Load(string):

Type t = Type.GetType ("System.Int32, System.Private.CoreLib");
After you have a System.Type object, you can use its properties to access the type’s name, assembly, base type, visibility, and so on:

Type stringType = typeof (string);
string name     = stringType.Name;          // String
Type baseType   = stringType.BaseType;      // typeof(Object)
Assembly assem  = stringType.Assembly;      // System.Private.CoreLib
bool isPublic   = stringType.IsPublic;      // true
A System.Type instance is a window into the entire metadata for the type—and the assembly in which it’s defined.

NOTE
System.Type is abstract, so the typeof operator must actually give you a subclass of Type. The subclass that the CLR uses is internal to .NET and is called RuntimeType.

TypeInfo
Should you target .NET Core 1.x (or an older Windows Store profile), you’ll find most of Type’s members are missing. These missing members are exposed instead on a class called TypeInfo, which you obtain by calling GetTypeInfo. So, to get our previous example to run, you would do this:

Type stringType = typeof(string);
string name = stringType.Name;
Type baseType = stringType.GetTypeInfo().BaseType;
Assembly assem = stringType.GetTypeInfo().Assembly;
bool isPublic = stringType.GetTypeInfo().IsPublic;
TypeInfo also exists in .NET Core 2 and 3 and .NET 5+ (and .NET Framework 4.5+ and all .NET Standard versions), so the preceding code works almost universally. TypeInfo also includes additional properties and methods for reflecting over members.

Obtaining array types
As we just saw, typeof and GetType work with array types. You can also obtain an array type by calling MakeArrayType on the element type:

Type simpleArrayType = typeof (int).MakeArrayType();
Console.WriteLine (simpleArrayType == typeof (int[]));     // True
You can create multidimensional arrays by passing an integer argument to MakeArrayType:

Type cubeType = typeof (int).MakeArrayType (3);       // cube shaped
Console.WriteLine (cubeType == typeof (int[,,]));     // True
GetElementType does the reverse: it retrieves an array type’s element type:

Type e = typeof (int[]).GetElementType();     // e == typeof (int)
GetArrayRank returns the number of dimensions of a rectangular array:

int rank = typeof (int[,,]).GetArrayRank();   // 3
Obtaining nested types
To retrieve nested types, call GetNestedTypes on the containing type:

foreach (Type t in typeof (System.Environment).GetNestedTypes())
  Console.WriteLine (t.FullName);

OUTPUT: System.Environment+SpecialFolder
Or:

foreach (TypeInfo t in typeof (System.Environment).GetTypeInfo()
                                                  .DeclaredNestedTypes)
  Debug.WriteLine (t.FullName);
The one caveat with nested types is that the CLR treats a nested type as having special “nested” accessibility levels:

Type t = typeof (System.Environment.SpecialFolder);
Console.WriteLine (t.IsPublic);                      // False
Console.WriteLine (t.IsNestedPublic);                // True
Type Names
A type has Namespace, Name, and FullName properties. In most cases, FullName is a composition of the former two:

Type t = typeof (System.Text.StringBuilder);

Console.WriteLine (t.Namespace);      // System.Text
Console.WriteLine (t.Name);           // StringBuilder
Console.WriteLine (t.FullName);       // System.Text.StringBuilder
There are two exceptions to this rule: nested types and closed generic types.

NOTE
Type also has a property called AssemblyQualifiedName, which returns FullName followed by a comma and then the full name of its assembly. This is the same string that you can pass to Type.GetType, and it uniquely identifies a type within the default loading context.

Nested type names
With nested types, the containing type appears only in FullName:

Type t = typeof (System.Environment.SpecialFolder);

Console.WriteLine (t.Namespace);      // System
Console.WriteLine (t.Name);           // SpecialFolder
Console.WriteLine (t.FullName);       // System.Environment+SpecialFolder
The + symbol differentiates the containing type from a nested namespace.

Generic type names
Generic type names are suffixed with the ' symbol, followed by the number of type parameters. If the generic type is unbound, this rule applies to both Name and FullName:

Type t = typeof (Dictionary<,>); // Unbound
Console.WriteLine (t.Name);      // Dictionary'2
Console.WriteLine (t.FullName);  // System.Collections.Generic.Dictionary'2
If the generic type is closed, however, FullName (only) acquires a substantial extra appendage. Each type parameter’s full assembly qualified name is enumerated:

Console.WriteLine (typeof (Dictionary<int,string>).FullName);

// OUTPUT:
System.Collections.Generic.Dictionary`2[[System.Int32, 
System.Private.CoreLib, Version=4.0.0.0, Culture=neutral,
PublicKeyToken=7cec85d7bea7798e],[System.String, System.Private.CoreLib,
Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e]]
This ensures that AssemblyQualifiedName (a combination of the type’s full name and assembly name) contains enough information to fully identify both the generic type and its type parameters.

Array and pointer type names
Arrays present with the same suffix that you use in a typeof expression:

Console.WriteLine (typeof ( int[]  ).Name);      // Int32[]
Console.WriteLine (typeof ( int[,] ).Name);      // Int32[,]
Console.WriteLine (typeof ( int[,] ).FullName);  // System.Int32[,]
Pointer types are similar:

Console.WriteLine (typeof (byte*).Name);     // Byte*
ref and out parameter type names
A Type describing a ref or out parameter has an & suffix:

public void RefMethod (ref int p)
{
  Type t = MethodInfo.GetCurrentMethod().GetParameters()[0].ParameterType;
  Console.WriteLine (t.Name);    // Int32&
}
More on this later, in the section “Reflecting and Invoking Members”.

Base Types and Interfaces
Type exposes a BaseType property:

Type base1 = typeof (System.String).BaseType;
Type base2 = typeof (System.IO.FileStream).BaseType;

Console.WriteLine (base1.Name);     // Object
Console.WriteLine (base2.Name);     // Stream
The GetInterfaces method returns the interfaces that a type implements:

foreach (Type iType in typeof (Guid).GetInterfaces())
  Console.WriteLine (iType.Name);

IFormattable
IComparable
IComparable'1
IEquatable'1
(The GetInterfaceMap method returns a struct that shows how each member of an interface is implemented in a class or struct—we illustrate a use for this advanced feature in “Calling Static Virtual/Abstract Interface Members”.)

Reflection provides three dynamic equivalents to C#’s static is operator:

IsInstanceOfType
Accepts a type and instance
IsAssignableFrom and (from .NET 5) IsAssignableTo
Accepts two types
Here’s an example of the first:

object obj  = Guid.NewGuid();
Type target = typeof (IFormattable);

bool isTrue   = obj is IFormattable;             // Static C# operator
bool alsoTrue = target.IsInstanceOfType (obj);   // Dynamic equivalent
IsAssignableFrom is more versatile:

Type target = typeof (IComparable), source = typeof (string);
Console.WriteLine (target.IsAssignableFrom (source));         // True
The IsSubclassOf method works on the same principle as IsAssignableFrom but excludes interfaces.

Instantiating Types
There are two ways to dynamically instantiate an object from its type:

Call the static Activator.CreateInstance method

Call Invoke on a ConstructorInfo object obtained from calling GetConstructor on a Type (advanced scenarios)

Activator.CreateInstance accepts a Type and optional arguments that it passes to the constructor:

int i = (int) Activator.CreateInstance (typeof (int));

DateTime dt = (DateTime) Activator.CreateInstance (typeof (DateTime),
                                                   2000, 1, 1);
CreateInstance lets you specify many other options such as the assembly from which to load the type and whether to bind to a nonpublic constructor. A MissingMethodException is thrown if the runtime can’t find a suitable constructor.

Calling Invoke on a ConstructorInfo is necessary when your argument values can’t disambiguate between overloaded constructors. For example, suppose that class X has two constructors: one accepting a parameter of type string and another accepting a parameter of type StringBuilder. The target is ambiguous should you pass a null argument into Activator.CreateInstance. This is when you need to use a ConstructorInfo, instead:

// Fetch the constructor that accepts a single parameter of type string:
ConstructorInfo ci = typeof (X).GetConstructor (new[] { typeof (string) });

// Construct the object using that overload, passing in null:
object foo = ci.Invoke (new object[] { null });
Or, if you’re targeting .NET Core 1, an older Windows Store profile:

ConstructorInfo ci = typeof (X).GetTypeInfo().DeclaredConstructors
  .FirstOrDefault (c =>
     c.GetParameters().Length == 1 && 
     c.GetParameters()[0].ParameterType == typeof (string));
To obtain a nonpublic constructor, you need to specify BindingFlags—see “Accessing Nonpublic Members” in the later section “Reflecting and Invoking Members”.

WARNING
Dynamic instantiation adds a few microseconds onto the time taken to construct the object. This is quite a lot in relative terms because the CLR is ordinarily very fast in instantiating objects (a simple new on a small class takes in the region of tens of nanoseconds).

To dynamically instantiate arrays based on just element type, first call MakeArrayType. You can also instantiate generic types: we describe this in the next section.

To dynamically instantiate a delegate, call Delegate.CreateDelegate. The following example demonstrates instantiating both an instance delegate and a static delegate:

class Program
{
  delegate int IntFunc (int x);

  static int Square (int x) => x * x;        // Static method
  int        Cube   (int x) => x * x * x;    // Instance method

  static void Main()
  {
    Delegate staticD = Delegate.CreateDelegate
      (typeof (IntFunc), typeof (Program), "Square");

    Delegate instanceD = Delegate.CreateDelegate
      (typeof (IntFunc), new Program(), "Cube");

    Console.WriteLine (staticD.DynamicInvoke (3));      // 9
    Console.WriteLine (instanceD.DynamicInvoke (3));    // 27
  }
}
You can invoke the Delegate object that’s returned by calling DynamicInvoke, as we did in this example, or by casting to the typed delegate:

IntFunc f = (IntFunc) staticD;
Console.WriteLine (f(3));         // 9 (but much faster!)
You can pass a MethodInfo into CreateDelegate instead of a method name. We describe MethodInfo shortly, in “Reflecting and Invoking Members”, along with the rationale for casting a dynamically created delegate back to the static delegate type.

Generic Types
A Type can represent a closed or unbound generic type. Just as at compile time, a closed generic type can be instantiated, whereas an unbound type cannot:

Type closed = typeof (List<int>);
List<int> list = (List<int>) Activator.CreateInstance (closed);  // OK

Type unbound   = typeof (List<>);
object anError = Activator.CreateInstance (unbound);    // Runtime error
The MakeGenericType method converts an unbound into a closed generic type. Simply pass in the desired type arguments:

Type unbound = typeof (List<>);
Type closed = unbound.MakeGenericType (typeof (int));
The GetGenericTypeDefinition method does the opposite:

Type unbound2 = closed.GetGenericTypeDefinition();  // unbound == unbound2
The IsGenericType property returns true if a Type is generic, and the IsGenericTypeDefinition property returns true if the generic type is unbound. The following tests whether a type is a nullable value type:

Type nullable = typeof (bool?);
Console.WriteLine (
  nullable.IsGenericType &&
  nullable.GetGenericTypeDefinition() == typeof (Nullable<>));   // True
GetGenericArguments returns the type arguments for closed generic types:

Console.WriteLine (closed.GetGenericArguments()[0]);     // System.Int32
Console.WriteLine (nullable.GetGenericArguments()[0]);   // System.Boolean
For unbound generic types, GetGenericArguments returns pseudotypes that represent the placeholder types specified in the generic type definition:

Console.WriteLine (unbound.GetGenericArguments()[0]);      // T
NOTE
At runtime, all generic types are either unbound or closed. They’re unbound in the (relatively unusual) case of an expression such as typeof(Foo<>); otherwise, they’re closed. There’s no such thing as an open generic type at runtime: all open types are closed by the compiler. The method in the following class always prints False:

class Foo<T>
{
  public void Test()
    => Console.Write (GetType().IsGenericTypeDefinition);  
}
Reflecting and Invoking Members
The GetMembers method returns the members of a type. Consider the following class:

class Walnut
{
  private bool cracked;
  public void Crack() { cracked = true; }
}
We can reflect on its public members, as follows:

MemberInfo[] members = typeof (Walnut).GetMembers();
foreach (MemberInfo m in members)
  Console.WriteLine (m);
This is the result:

Void Crack()
System.Type GetType()
System.String ToString()
Boolean Equals(System.Object)
Int32 GetHashCode()
Void .ctor()
REFLECTING MEMBERS WITH TYPEINFO
TypeInfo exposes a different (and somewhat simpler) protocol for reflecting over members. Using this API is optional (except in .NET Core 1 and older Windows Store apps given that there’s no exact equivalent to the GetMembers method).

Instead of exposing methods like GetMembers that return arrays, TypeInfo exposes properties that return IEnumerable<T>, upon which you typically run LINQ queries. The broadest is DeclaredMembers:

IEnumerable<MemberInfo> members =
  typeof(Walnut).GetTypeInfo().DeclaredMembers;
Unlike with GetMembers(), the result excludes inherited members:

Void Crack()
Void .ctor()
Boolean cracked
There are also properties for returning specific kinds of members (DeclaredProperties, DeclaredMethods, DeclaredEvents, and so on) and methods for returning a specific member by name (e.g., GetDeclaredMethod). The latter cannot be used on overloaded methods (because there’s no way to specify parameter types). Instead, you run a LINQ query over DeclaredMethods:

MethodInfo method = typeof (int).GetTypeInfo().DeclaredMethods
  .FirstOrDefault (m => m.Name == "ToString" &&
                        m.GetParameters().Length == 0);
When called with no arguments, GetMembers returns all the public members for a type (and its base types). GetMember retrieves a specific member by name—although it still returns an array because members can be overloaded:

MemberInfo[] m = typeof (Walnut).GetMember ("Crack");
Console.WriteLine (m[0]);                              // Void Crack()
MemberInfo also has a property called MemberType of type MemberTypes. This is a flags enum with these values:

All           Custom        Field        NestedType     TypeInfo
Constructor   Event         Method       Property
When calling GetMembers, you can pass in a MemberTypes instance to restrict the kinds of members that it returns. Alternatively, you can restrict the result set by calling GetMethods, GetFields, GetProperties, GetEvents, GetConstructors, or GetNestedTypes. There are also singular versions of each of these to home in on a specific member.

NOTE
It pays to be as specific as possible when retrieving a type member so that your code doesn’t break if additional members are added later. If you’re retrieving a method by name, specifying all parameter types ensures that your code will still work if the method is later overloaded (we provide examples shortly, in “Method Parameters”).

A MemberInfo object has a Name property and two Type properties:

DeclaringType
Returns the Type that defines the member
ReflectedType
Returns the Type upon which GetMembers was called
The two differ when called on a member that’s defined in a base type: DeclaringType returns the base type, whereas ReflectedType returns the subtype. The following example highlights this:

// MethodInfo is a subclass of MemberInfo; see Figure 18-1.

MethodInfo test = typeof (Program).GetMethod ("ToString");
MethodInfo obj  = typeof (object) .GetMethod ("ToString");

Console.WriteLine (test.DeclaringType);      // System.Object
Console.WriteLine (obj.DeclaringType);       // System.Object

Console.WriteLine (test.ReflectedType);      // Program
Console.WriteLine (obj.ReflectedType);       // System.Object

Console.WriteLine (test == obj);             // False
Because they have different ReflectedTypes, the test and obj objects are not equal. Their difference, however, is purely a fabrication of the reflection API; our Program type has no distinct ToString method in the underlying type system. We can verify that the two MethodInfo objects refer to the same method in either of two ways:

Console.WriteLine (test.MethodHandle == obj.MethodHandle);    // True

Console.WriteLine (test.MetadataToken == obj.MetadataToken    // True
                   && test.Module == obj.Module);
A MethodHandle is unique to each (genuinely distinct) method within a process; a MetadataToken is unique across all types and members within an assembly module.

MemberInfo also defines methods to return custom attributes (see “Retrieving Attributes at Runtime”).

NOTE
You can obtain the MethodBase of the currently executing method by calling MethodBase.GetCurrentMethod.

Member Types
MemberInfo itself is light on members because it’s an abstract base for the types shown in Figure 18-1.


Figure 18-1. Member types
You can cast a MemberInfo to its subtype, based on its MemberType property. If you obtained a member via GetMethod, GetField, GetProperty, GetEvent, GetConstructor, or GetNestedType (or their plural versions), a cast isn’t necessary. Table 18-1 summarizes what methods to use for each kind of C# construct.

Table 18-1. Retrieving member metadata
C# construct	Method to use	Name to use	Result
Method	GetMethod	(method name)	MethodInfo
Property	GetProperty	(property name)	PropertyInfo
Indexer	GetDefaultMembers		MemberInfo[] (containing PropertyInfo objects if compiled in C#)
Field	GetField	(field name)	FieldInfo
Enum member	GetField	(member name)	FieldInfo
Event	GetEvent	(event name)	EventInfo
Constructor	GetConstructor		ConstructorInfo
Finalizer	GetMethod	"Finalize"	MethodInfo
Operator	GetMethod	"op_" + operator name	MethodInfo
Nested type	GetNestedType	(type name)	Type
Each MemberInfo subclass has a wealth of properties and methods, exposing all aspects of the member’s metadata. This includes such things as visibility, modifiers, generic type arguments, parameters, return type, and custom attributes.

Here is an example of using GetMethod:

MethodInfo m = typeof (Walnut).GetMethod ("Crack");
Console.WriteLine (m);                             // Void Crack()
Console.WriteLine (m.ReturnType);                  // System.Void
All *Info instances are cached by the reflection API on first use:

MethodInfo method = typeof (Walnut).GetMethod ("Crack");
MemberInfo member = typeof (Walnut).GetMember ("Crack") [0];

Console.Write (method == member);       // True
As well as preserving object identity, caching improves the performance of what is otherwise a fairly slow API.

C# Members Versus CLR Members
The preceding table illustrates that some of C#’s functional constructs don’t have a 1:1 mapping with CLR constructs. This makes sense because the CLR and reflection API were designed with all .NET languages in mind—you can use reflection even from Visual Basic.

Some C# constructs—namely indexers, enums, operators, and finalizers—are contrivances as far as the CLR is concerned. Specifically:

A C# indexer translates to a property accepting one or more arguments, marked as the type’s [DefaultMember].

A C# enum translates to a subtype of System.Enum with a static field for each member.

A C# operator translates to a specially named static method, starting in “op_”; for example, "op_Addition".

A C# finalizer translates to a method that overrides Finalize.

Another complication is that properties and events actually comprise two things:

Metadata describing the property or event (encapsulated by PropertyInfo or EventInfo)

One or two backing methods

In a C# program, the backing methods are encapsulated within the property or event definition. But when compiled to IL, the backing methods present as ordinary methods that you can call like any other. This means that GetMethods returns property and event backing methods alongside ordinary methods:

class Test { public int X { get { return 0; } set {} } }

void Demo()
{
  foreach (MethodInfo mi in typeof (Test).GetMethods())
    Console.Write (mi.Name + "  ");
}

// OUTPUT:
get_X  set_X  GetType  ToString  Equals  GetHashCode
You can identify these methods through the IsSpecialName property in MethodInfo. IsSpecialName returns true for property, indexer, and event accessors, as well as operators. It returns false only for conventional C# methods—and the Finalize method if a finalizer is defined.

Here are the backing methods that C# generates:

C# construct	Member type	Methods in IL
Property	Property	get_XXX and set_XXX
Indexer	Property	get_Item and set_Item
Event	Event	add_XXX and remove_XXX
Each backing method has its own associated MethodInfo object. You can access these as follows:

PropertyInfo pi = typeof (Console).GetProperty ("Title");
MethodInfo getter = pi.GetGetMethod();                   // get_Title
MethodInfo setter = pi.GetSetMethod();                   // set_Title
MethodInfo[] both = pi.GetAccessors();                   // Length==2
GetAddMethod and GetRemoveMethod perform a similar job for EventInfo.

To go in the reverse direction—from a MethodInfo to its associated PropertyInfo or EventInfo—you need to perform a query. LINQ is ideal for this job:

PropertyInfo p = mi.DeclaringType.GetProperties()
                   .First (x => x.GetAccessors (true).Contains (mi));
Init-only properties
Init-only properties, introduced in C# 9, can be set via an object initializer but are subsequently treated as read-only by the compiler. From the CLR’s perspective, an init accessor is just like an ordinary set accessor, but with a special flag applied to the set method’s return type (which means something to the compiler).

Curiously, this flag is not encoded as a convention attribute. Instead, it uses a relatively obscure mechanism called a modreq, which ensures that previous versions of the C# compiler (which don’t recognize the new modreq) ignore the accessor rather than treat the property as writable.

The modreq for init-only accessors is called IsExternalInit, and you can query for it as follows:

bool IsInitOnly (PropertyInfo pi) => pi
  .GetSetMethod().ReturnParameter.GetRequiredCustomModifiers()
  .Any (t => t.Name == "IsExternalInit");
NullabilityInfoContext
From .NET 6, you can use the NullabilityInfoContext class to obtain information about the nullability annotations for a field, property, event or parameter:

void PrintPropertyNullability (PropertyInfo pi)
{
  var info = new NullabilityInfoContext().Create (pi);
  Console.WriteLine (pi.Name + " read " + info.ReadState);
  Console.WriteLine (pi.Name + " write " + info.WriteState);
  // Use info.Element to get nullability info for array elements
}
Generic Type Members
You can obtain member metadata for both unbound and closed generic types:

PropertyInfo unbound = typeof (IEnumerator<>)  .GetProperty ("Current");
PropertyInfo closed = typeof (IEnumerator<int>).GetProperty ("Current");

Console.WriteLine (unbound);   // T Current
Console.WriteLine (closed);    // Int32 Current

Console.WriteLine (unbound.PropertyType.IsGenericParameter);  // True
Console.WriteLine (closed.PropertyType.IsGenericParameter);   // False
The MemberInfo objects returned from unbound and closed generic types are always distinct, even for members whose signatures don’t feature generic type parameters:

PropertyInfo unbound = typeof (List<>)  .GetProperty ("Count");
PropertyInfo closed = typeof (List<int>).GetProperty ("Count");

Console.WriteLine (unbound);   // Int32 Count
Console.WriteLine (closed);    // Int32 Count

Console.WriteLine (unbound == closed);   // False

Console.WriteLine (unbound.DeclaringType.IsGenericTypeDefinition); // True
Console.WriteLine (closed.DeclaringType.IsGenericTypeDefinition); // False
Members of unbound generic types cannot be dynamically invoked.

Dynamically Invoking a Member
NOTE
Dynamically invoking a member can be accomplished more easily using the Uncapsulator open-source library (available on NuGet and GitHub). Uncapsulator was written by the author, and provides a fluent API for invoking public and non-public members via reflection, using a custom dynamic binder.

After you have a MethodInfo, PropertyInfo, or FieldInfo object, you can dynamically call it or get/set its value. This is called late binding because you choose which member to invoke at runtime rather than compile time.

To illustrate, the following uses ordinary static binding:

string s = "Hello";
int length = s.Length;
Here’s the same thing performed dynamically with late binding:

object s = "Hello";
PropertyInfo prop = s.GetType().GetProperty ("Length");
int length = (int) prop.GetValue (s, null);               // 5
GetValue and SetValue get and set the value of a PropertyInfo or FieldInfo. The first argument is the instance, which can be null for a static member. Accessing an indexer is just like accessing a property called “Item,” except that you provide indexer values as the second argument when calling GetValue or SetValue.

To dynamically call a method, call Invoke on a MethodInfo, providing an array of arguments to pass to that method. If you get any of the argument types wrong, an exception is thrown at runtime. With dynamic invocation, you lose compile-time type safety, but you still have runtime type safety (just as with the dynamic keyword).

Method Parameters
Suppose that we want to dynamically call string’s Substring method. Statically, we would do this, as follows:

Console.WriteLine ("stamp".Substring(2));                  // "amp"
Here’s the dynamic equivalent with reflection and late binding:

Type type = typeof (string);
Type[] parameterTypes = { typeof (int) };
MethodInfo method = type.GetMethod ("Substring", parameterTypes);

object[] arguments = { 2 };
object returnValue = method.Invoke ("stamp", arguments);
Console.WriteLine (returnValue);                           // "amp"
Because the Substring method is overloaded, we had to pass an array of parameter types to GetMethod to indicate which version we wanted. Without the parameter types, GetMethod would throw an AmbiguousMatchException.

The GetParameters method, defined on MethodBase (the base class for MethodInfo and ConstructorInfo), returns parameter metadata. We can continue our previous example, as follows:

ParameterInfo[] paramList = method.GetParameters();
foreach (ParameterInfo x in paramList)
{
  Console.WriteLine (x.Name);                 // startIndex
  Console.WriteLine (x.ParameterType);        // System.Int32
}
Dealing with ref and out parameters
To pass ref or out parameters, call MakeByRefType on the type before obtaining the method. For instance, you can dynamically execute this code:

int x;
bool successfulParse = int.TryParse ("23", out x);
as follows:

object[] args = { "23", 0 };
Type[] argTypes = { typeof (string), typeof (int).MakeByRefType() };
MethodInfo tryParse = typeof (int).GetMethod ("TryParse", argTypes);
bool successfulParse = (bool) tryParse.Invoke (null, args);

Console.WriteLine (successfulParse + " " + args[1]);       // True 23
This same approach works for both ref and out parameter types.

Retrieving and invoking generic methods
Explicitly specifying parameter types when calling GetMethod can be essential in disambiguating overloaded methods. However, it’s impossible to specify generic parameter types. For instance, consider the System.Linq.Enumerable class, which overloads the Where method, as follows:

public static IEnumerable<TSource> Where<TSource>
 (this IEnumerable<TSource> source, Func<TSource, bool> predicate);

public static IEnumerable<TSource> Where<TSource>
 (this IEnumerable<TSource> source, Func<TSource, int, bool> predicate);
To retrieve a specific overload, we must retrieve all methods and then manually find the desired overload. The following query retrieves the former overload of Where:

from m in typeof (Enumerable).GetMethods()
where m.Name == "Where" && m.IsGenericMethod 
let parameters = m.GetParameters()
where parameters.Length == 2
let genArg = m.GetGenericArguments().First()
let enumerableOfT = typeof (IEnumerable<>).MakeGenericType (genArg)
let funcOfTBool = typeof (Func<,>).MakeGenericType (genArg, typeof (bool))
where parameters[0].ParameterType == enumerableOfT
   && parameters[1].ParameterType == funcOfTBool
select m
Calling .Single() on this query gives the correct MethodInfo object with unbound type parameters. The next step is to close the type parameters by calling MakeGenericMethod:

var closedMethod = unboundMethod.MakeGenericMethod (typeof (int));
In this case, we’ve closed TSource with int, allowing us to call Enumerable.Where with a source of type IEnumerable<int> and a predicate of type Func<int,bool>:

int[] source = { 3, 4, 5, 6, 7, 8 };
Func<int, bool> predicate = n => n % 2 == 1;   // Odd numbers only
We can now invoke the closed generic method:

var query = (IEnumerable<int>) closedMethod.Invoke 
  (null, new object[] { source, predicate });

foreach (int element in query) Console.Write (element + "|");  // 3|5|7|
NOTE
If you’re using the System.Linq.Expressions API to dynamically build expressions (Chapter 8), you don’t need to go to this trouble to specify a generic method. The Expression.Call method is overloaded to let you specify the closed type arguments of the method that you want to call:

int[] source = { 3, 4, 5, 6, 7, 8 };
Func<int, bool> predicate = n => n % 2 == 1;

var sourceExpr = Expression.Constant (source);
var predicateExpr = Expression.Constant (predicate);

var callExpression = Expression.Call (
  typeof (Enumerable), "Where",
  new[] { typeof (int) },  // Closed generic arg type.
  sourceExpr, predicateExpr);
Using Delegates for Performance
Dynamic invocations are relatively inefficient, with an overhead typically in the few-microseconds region. If you’re calling a method repeatedly in a loop, you can shift the per-call overhead into the nanoseconds region by instead calling a dynamically instantiated delegate that targets your dynamic method. In the following example, we dynamically call string’s Trim method a million times without significant overhead:

MethodInfo trimMethod = typeof (string).GetMethod ("Trim", new Type[0]);
var trim = (StringToString) Delegate.CreateDelegate
                                    (typeof (StringToString), trimMethod);
for (int i = 0; i < 1000000; i++)
  trim ("test");

delegate string StringToString (string s);
This is faster because the costly late binding (shown in bold) happens just once.

Accessing Nonpublic Members
All of the methods on types used to probe metadata (e.g., GetProperty, GetField, etc.) have overloads that take a BindingFlags enum. This enum serves as a metadata filter and allows you to change the default selection criteria. The most common use for this is to retrieve nonpublic members (this works only in desktop apps).

For instance, consider the following class:

class Walnut
{
  private bool cracked;
  public void Crack() { cracked = true; }

  public override string ToString() { return cracked.ToString(); }
}
We can uncrack the walnut, as follows:

Type t = typeof (Walnut);
Walnut w = new Walnut();
w.Crack();
FieldInfo f = t.GetField ("cracked", BindingFlags.NonPublic |
                                     BindingFlags.Instance);
f.SetValue (w, false);
Console.WriteLine (w);         // False
Using reflection to access nonpublic members is powerful, but it is also dangerous because you can bypass encapsulation, creating an unmanageable dependency on the internal implementation of a type.

The BindingFlags enum
BindingFlags is intended to be bitwise-combined. To get any matches at all, you need to start with one of the following four combinations:

BindingFlags.Public    | BindingFlags.Instance
BindingFlags.Public    | BindingFlags.Static
BindingFlags.NonPublic | BindingFlags.Instance
BindingFlags.NonPublic | BindingFlags.Static
NonPublic includes internal, protected, protected internal, and private.

The following example retrieves all the public static members of type object:

BindingFlags publicStatic = BindingFlags.Public | BindingFlags.Static;
MemberInfo[] members = typeof (object).GetMembers (publicStatic);
The following example retrieves all the nonpublic members of type object, both static and instance:

BindingFlags nonPublicBinding =
  BindingFlags.NonPublic | BindingFlags.Static | BindingFlags.Instance;

MemberInfo[] members = typeof (object).GetMembers (nonPublicBinding);
The DeclaredOnly flag excludes functions inherited from base types, unless they are overridden.

NOTE
The DeclaredOnly flag is somewhat confusing in that it restricts the result set (whereas all the other binding flags expand the result set).

Generic Methods
You cannot directly invoke generic methods; the following throws an exception:

class Program
{
  public static T Echo<T> (T x) { return x; }

  static void Main()
  {
    MethodInfo echo = typeof (Program).GetMethod ("Echo");
    Console.WriteLine (echo.IsGenericMethodDefinition);    // True
    echo.Invoke (null, new object[] { 123 } );             // Exception
  }
}
An extra step is required, which is to call MakeGenericMethod on the MethodInfo, specifying concrete generic type arguments. This returns another MethodInfo, which you can then invoke, as follows:

MethodInfo echo = typeof (Program).GetMethod ("Echo");
MethodInfo intEcho = echo.MakeGenericMethod (typeof (int));
Console.WriteLine (intEcho.IsGenericMethodDefinition);            // False
Console.WriteLine (intEcho.Invoke (null, new object[] { 3 } ));   // 3
Anonymously Calling Members of a Generic Interface
Reflection is useful when you need to invoke a member of a generic interface and you don’t know the type parameters until runtime. In theory, the need for this arises rarely if types are perfectly designed; of course, types are not always perfectly designed.

For instance, suppose that we want to write a more powerful version of ToString that could expand the result of LINQ queries. We could start out as follows:

public static string ToStringEx <T> (IEnumerable<T> sequence)
{
  ...
}
This is already quite limiting. What if sequence contained nested collections that we also want to enumerate? We’d need to overload the method to cope:

public static string ToStringEx <T> (IEnumerable<IEnumerable<T>> sequence)
And then what if sequence contained groupings, or projections of nested sequences? The static solution of method overloading becomes impractical—we need an approach that can scale to handle an arbitrary object graph, such as the following:

public static string ToStringEx (object value)
{
  if (value == null) return "<null>";
  StringBuilder sb = new StringBuilder();

  if (value is List<>)                                            // Error
    sb.Append ("List of " + ((List<>) value).Count + " items");   // Error

  if (value is IGrouping<,>)                                      // Error
    sb.Append ("Group with key=" + ((IGrouping<,>) value).Key);   // Error

  // Enumerate collection elements if this is a collection,
  // recursively calling ToStringEx()
  // ...

  return sb.ToString();
}
Unfortunately, this won’t compile: you cannot invoke members of an unbound generic type such as List<> or IGrouping<>. In the case of List<>, we can solve the problem by using the nongeneric IList interface, instead:

  if (value is IList)
    sb.AppendLine ("A list with " + ((IList) value).Count + " items");
NOTE
We can do this because the designers of List<> had the foresight to implement IList classic (as well as IList generic). The same principle is worthy of consideration when writing your own generic types: having a nongeneric interface or base class upon which consumers can fall back can be extremely valuable.

The solution is not as simple for IGrouping<,>. Here’s how the interface is defined:

public interface IGrouping <TKey,TElement> : IEnumerable <TElement>,
                                             IEnumerable
{
  TKey Key { get; }
}
There’s no nongeneric type we can use to access the Key property, so here we must use reflection. The solution is not to invoke members of an unbound generic type (which is impossible) but to invoke members of a closed generic type, whose type arguments we establish at runtime.

NOTE
In the following chapter, we solve this more simply with C#’s dynamic keyword. A good indication for dynamic binding is when you would otherwise need to perform type gymnastics—as we are doing right now.

The first step is to determine whether value implements IGrouping<,>, and if so, obtain its closed generic interface. We can do this most easily by executing a LINQ query. Then, we retrieve and invoke the Key property:

public static string ToStringEx (object value)
{
  if (value == null) return "<null>";
  if (value.GetType().IsPrimitive) return value.ToString();

  StringBuilder sb = new StringBuilder();

  if (value is IList)
    sb.Append ("List of " + ((IList)value).Count + " items: ");

  Type closedIGrouping = value.GetType().GetInterfaces()
    .Where (t => t.IsGenericType &&
                 t.GetGenericTypeDefinition() == typeof (IGrouping<,>))
    .FirstOrDefault();

  if (closedIGrouping != null)   // Call the Key property on IGrouping<,>
  {
    PropertyInfo pi = closedIGrouping.GetProperty ("Key");
    object key = pi.GetValue (value, null);
    sb.Append ("Group with key=" + key + ": ");
  }

  if (value is IEnumerable)
    foreach (object element in ((IEnumerable)value))
      sb.Append (ToStringEx (element) + " ");

  if (sb.Length == 0) sb.Append (value.ToString());

  return "\r\n" + sb.ToString();
}
This approach is robust: it works whether IGrouping<,> is implemented implicitly or explicitly. The following demonstrates this method:

Console.WriteLine (ToStringEx (new List<int> { 5, 6, 7 } ));
Console.WriteLine (ToStringEx ("xyyzzz".GroupBy (c => c) ));

List of 3 items: 5 6 7

Group with key=x: x
Group with key=y: y y
Group with key=z: z z z
Calling Static Virtual/Abstract Interface Members
From .NET 7 and C# 11, interfaces can define static virtual and abstract members (see “Static virtual/abstract interface members”). An example is the .NET IParsable<TSelf> interface:

public interface IParsable<TSelf> where TSelf : IParsable<TSelf>
{
  static abstract TSelf Parse (string s, IFormatProvider provider);
  ...
}
With a constrained type parameter, static abstract interface members can be called polymorphically:

T ParseAny<T> (string s) where T : IParsable<T> => T.Parse (s, null);
To call a static abstract interface member via reflection, you must obtain a MethodInfo from the concrete type that implements the interface—not from the interface itself. The obvious solution is to retrieve the concrete member by signature:

MethodInfo GetParseMethod (Type concreteType) =>
  concreteType.GetMethod ("Parse",
    new[] { typeof (string), typeof (IFormatProvider) });
However, this will fail if the member has been implemented explicitly. To solve this in a general fashion, we will start by writing a function that retrieves the MethodInfo on a concrete type that implements a specified interface method:

MethodInfo GetImplementedInterfaceMethod (Type concreteType,
  Type interfaceType, string methodName, Type[] paramTypes)
{
  var map = concreteType.GetInterfaceMap (interfaceType);

  return map.InterfaceMethods
    .Zip (map.TargetMethods)
    .Single (m => m.First.Name == methodName &&
             m.First.GetParameters().Select (p => p.ParameterType)
                                    .SequenceEqual (paramTypes))
    .Second;
}
The key to making this work is the call to GetInterfaceMap. This method returns the following struct:

public struct InterfaceMapping
{   
   public MethodInfo[] InterfaceMethods;    // These arrays each
   public MethodInfo[] TargetMethods;       // have the same length.
   ...
}
This struct tells us how the members of the implemented interface (InterfaceMe⁠thods) map to the concrete type’s members (TargetMethods).

NOTE
GetInterfaceMap works with ordinary (instance) methods as well; it just happens to be particularly useful when working with static abstract interface members.

We then used LINQ’s Zip method to align the elements in the two arrays, allowing us to easily obtain the target method corresponding to the interface method with the desired signature.

We can now use this to write a reflection-based ParseAny method:

object ParseAny (Type type, string value)
{
  MethodInfo parseMethod = GetImplementedInterfaceMethod (type,
    type.GetInterface ("IParsable`1"),
    "Parse",
    new[] { typeof (string), typeof (IFormatProvider) });

  return parseMethod.Invoke (null, new[] { value, null });
}

Console.WriteLine (ParseAny (typeof (float), ".2"));   // 0.2
When calling GetImplementedInterfaceMethod, we needed to provide the (closed) interface type, which we obtained by calling GetInterface("IParsable`1") on the concrete type. Given that (in this scenario) we knew the desired interface at compile time, we could have used the following expression instead:

typeof (IParsable<>).MakeGenericType (type)
Reflecting Assemblies
You can dynamically reflect an assembly by calling GetType or GetTypes on an Assembly object. The following retrieves from the current assembly, the type called TestProgram in the Demos namespace:

Type t = Assembly.GetExecutingAssembly().GetType ("Demos.TestProgram");
You can also obtain an assembly from an existing type:

typeof (Foo).Assembly.GetType ("Demos.TestProgram");
The next example lists all the types in the assembly mylib.dll in e:\demo:

Assembly a = Assembly.LoadFile (@"e:\demo\mylib.dll");

foreach (Type t in a.GetTypes())
  Console.WriteLine (t);
Or:

Assembly a = typeof (Foo).GetTypeInfo().Assembly;

foreach (Type t in a.ExportedTypes)
  Console.WriteLine (t);
GetTypes and ExportedTypes return only top-level and not nested types.

Modules
Calling GetTypes on a multimodule assembly returns all types in all modules. As a result, you can ignore the existence of modules and treat an assembly as a type’s container. There is one case, though, for which modules are relevant—and that’s when dealing with metadata tokens.

A metadata token is an integer that uniquely refers to a type, member, string, or resource within the scope of a module. IL uses metadata tokens, so if you’re parsing IL, you’ll need to be able to resolve them. The methods for doing this are defined in the Module type and are called ResolveType, ResolveMember, ResolveString, and ResolveSignature. We revisit this in the final section of this chapter, on writing a disassembler.

You can obtain a list of all the modules in an assembly by calling GetModules. You can also access an assembly’s main module directly via its ManifestModule property.

Working with Attributes
The CLR allows additional metadata to be attached to types, members, and assemblies through attributes. This is the mechanism by which some important CLR functions (such as assembly identification or the marshaling of types for native interoperability) are directed, making attributes an indivisible part of an application.

A key characteristic of attributes is that you can write your own and then use them just as you would any other attribute to “decorate” a code element with additional information. This additional information is compiled into the underlying assembly and can be retrieved at runtime using reflection to build services that work declaratively, such as automated unit testing.

Attribute Basics
There are three kinds of attributes:

Bit-mapped attributes

Custom attributes

Pseudocustom attributes

Of these, only custom attributes are extensible.

NOTE
The term “attribute” by itself can refer to any of the three, although in the C# world, it most often refers to custom attributes or pseudocustom attributes.

Bit-mapped attributes (our terminology) map to dedicated bits in a type’s metadata. Most of C#’s modifier keywords, such as public, abstract, and sealed, compile to bit-mapped attributes. These attributes are very efficient because they consume minimal space in the metadata (usually just one bit), and the CLR can locate them with little or no indirection. The reflection API exposes them via dedicated properties on Type (and other MemberInfo subclasses), such as IsPublic, IsAbstract, and IsSealed. The Attributes property returns a flags enum that describes most of them in one hit:

static void Main()
{
  TypeAttributes ta = typeof (Console).Attributes;
  MethodAttributes ma = MethodInfo.GetCurrentMethod().Attributes;
  Console.WriteLine (ta + "\r\n" + ma);
}
Here’s the result:

AutoLayout, AnsiClass, Class, Public, Abstract, Sealed, BeforeFieldInit
PrivateScope, Private, Static, HideBySig
In contrast, custom attributes compile to a blob that hangs off the type’s main metadata table. All custom attributes are represented by a subclass of System.Attribute and, unlike bit-mapped attributes, are extensible. The blob in the metadata identifies the attribute class, and also stores the values of any positional or named argument that was specified when the attribute was applied. Custom attributes that you define yourself are architecturally identical to those defined in the .NET libraries.

Chapter 4 describes how to attach custom attributes to a type or member in C#. Here, we attach the predefined Obsolete attribute to the Foo class:

[Obsolete] public class Foo {...}
This instructs the compiler to incorporate an instance of ObsoleteAttribute into the metadata for Foo, which then can be reflected at runtime by calling GetCustomAt⁠tributes on a Type or MemberInfo object.

Pseudocustom attributes look and feel just like standard custom attributes. They are represented by a subclass of System.Attribute and are attached in the standard manner:

[System.Runtime.InteropServices.StructLayout(LayoutKind.Sequential)]
class SystemTime { ... }
The difference is that the compiler or CLR internally optimizes pseudocustom attributes by converting them to bit-mapped attributes. Examples include StructLayout, In, and Out (Chapter 24). Reflection exposes pseudocustom attributes through dedicated properties such as IsLayoutSequential, and in many cases they are also returned as System.Attribute objects when you call GetCustomAttributes. This means that you can (almost) ignore the difference between pseudo- and non-pseudocustom attributes (a notable exception is when using Reflection.Emit to generate types dynamically at runtime; see “Emitting Assemblies and Types”).

The AttributeUsage Attribute
AttributeUsage is an attribute applied to attribute classes. It instructs the compiler how the target attribute should be used:

public sealed class AttributeUsageAttribute : Attribute
{
  public AttributeUsageAttribute (AttributeTargets validOn);

  public bool AllowMultiple        { get; set; }
  public bool Inherited            { get; set; }
  public AttributeTargets ValidOn  { get; }
}
AllowMultiple controls whether the attribute being defined can be applied more than once to the same target; Inherited controls whether an attribute applied to a base class also applies to derived classes (or in the case of methods, whether an attribute applied to a virtual method also applies to overriding methods). ValidOn determines the set of targets (classes, interfaces, properties, methods, parameters, etc.) to which the attribute can be attached. It accepts any combination of values from the AttributeTargets enum, which has the following members:

All	Delegate	GenericParameter	Parameter
Assembly	Enum	Interface	Property
Class	Event	Method	ReturnValue
Constructor	Field	Module	Struct
To illustrate, here’s how the authors of .NET have applied AttributeUsage to the Serializable attribute:

[AttributeUsage (AttributeTargets.Delegate |
                 AttributeTargets.Enum     |
                 AttributeTargets.Struct   |
                 AttributeTargets.Class,     Inherited = false)
]
public sealed class SerializableAttribute : Attribute { }
This is, in fact, almost the complete definition of the Serializable attribute. Writing an attribute class that has no properties or special constructors is this simple.

Defining Your Own Attribute
Here’s how to write your own attribute:

Derive a class from System.Attribute or a descendent of System.Attribute. By convention, the class name should end with the word “Attribute,” although this isn’t required.

Apply the AttributeUsage attribute, described in the preceding section.

If the attribute requires no properties or arguments in its constructor, the job is done.

Write one or more public constructors. The parameters to the constructor define the positional parameters of the attribute and will become mandatory when using the attribute.

Declare a public field or property for each named parameter you wish to support. Named parameters are optional when using the attribute.

NOTE
Attribute properties and constructor parameters must be of the following types:

A sealed primitive type: in other words, bool, byte, char, double, float, int, long, short, or string

The Type type

An enum type

A one-dimensional array of any of these

When an attribute is applied, it must also be possible for the compiler to statically evaluate each of the properties or constructor arguments.

The following class defines an attribute for assisting an automated unit-testing system. It indicates that a method should be tested, the number of test repetitions, and a message in case of failure:

[AttributeUsage (AttributeTargets.Method)]
public sealed class TestAttribute : Attribute
{
  public int     Repetitions;
  public string  FailureMessage;

  public TestAttribute () : this (1)     { }
  public TestAttribute (int repetitions) { Repetitions = repetitions; }
}
Here’s a Foo class with methods decorated in various ways with the Test attribute:

class Foo
{
  [Test]
  public void Method1() { ... }

  [Test(20)]
  public void Method2() { ... }

  [Test(20, FailureMessage="Debugging Time!")]
  public void Method3() { ... }
}
Retrieving Attributes at Runtime
There are two standard ways to retrieve attributes at runtime:

Call GetCustomAttributes on any Type or MemberInfo object

Call Attribute.GetCustomAttribute or Attribute.GetCustomAttributes

These latter two methods are overloaded to accept any reflection object that corresponds to a valid attribute target (Type, Assembly, Module, MemberInfo, or ParameterInfo).

NOTE
You can also call GetCustomAttributesData() on a type or member to obtain attribute information. The difference between this and GetCustomAttributes() is that the former lets you know you how the attribute was instantiated: it reports the constructor overload that was used, and the value of each constructor argument and named parameter. This is useful when you want to emit code or IL to reconstruct the attribute to the same state (see “Emitting Type Members”).

Here’s how we can enumerate each method in the preceding Foo class that has a TestAttribute:

foreach (MethodInfo mi in typeof (Foo).GetMethods())
{
  TestAttribute att = (TestAttribute) Attribute.GetCustomAttribute
    (mi, typeof (TestAttribute));

  if (att != null)
    Console.WriteLine ("Method {0} will be tested; reps={1}; msg={2}",
                        mi.Name, att.Repetitions, att.FailureMessage);
}
Or:

foreach (MethodInfo mi in typeof (Foo).GetTypeInfo().DeclaredMethods)
...
Here’s the output:

Method Method1 will be tested; reps=1; msg=
Method Method2 will be tested; reps=20; msg=
Method Method3 will be tested; reps=20; msg=Debugging Time!
To complete the illustration on how we could use this to write a unit-testing system, here’s the same example expanded so that it actually calls the methods decorated with the Test attribute:

foreach (MethodInfo mi in typeof (Foo).GetMethods())
{
  TestAttribute att = (TestAttribute) Attribute.GetCustomAttribute
    (mi, typeof (TestAttribute));

  if (att != null)
    for (int i = 0; i < att.Repetitions; i++)
      try
      {
        mi.Invoke (new Foo(), null);    // Call method with no arguments
      }
      catch (Exception ex)       // Wrap exception in att.FailureMessage
      {
        throw new Exception ("Error: " + att.FailureMessage, ex);
      }
}
Returning to attribute reflection, here’s an example that lists the attributes present on a specific type:

object[] atts = Attribute.GetCustomAttributes (typeof (Test));
foreach (object att in atts) Console.WriteLine (att);

[Serializable, Obsolete]
class Test
{
}
And, here’s the output:

System.ObsoleteAttribute
System.SerializableAttribute
Dynamic Code Generation
The System.Reflection.Emit namespace contains classes for creating metadata and IL at runtime. Generating code dynamically is useful for certain kinds of programming tasks. An example is the regular expressions API, which emits performant types tuned to specific regular expressions. Another example is Entity Framework Core, which uses Reflection.Emit to generate proxy classes to enable lazy loading.

Generating IL with DynamicMethod
The DynamicMethod class is a lightweight tool in the System.Reflection.Emit namespace for generating methods on the fly. Unlike TypeBuilder, it doesn’t require that you first set up a dynamic assembly, module, and type in which to contain the method. This makes it suitable for simple tasks—as well as serving as a good introduction to Reflection.Emit.

NOTE
A DynamicMethod and the associated IL are garbage-collected when no longer referenced. This means you can repeatedly generate dynamic methods without filling up memory. (To do the same with dynamic assemblies, you must apply the AssemblyBuilderAccess.RunAndCollect flag when creating the assembly.)

Here is a simple use of DynamicMethod to create a method that writes Hello world to the console:

public class Test
{
  static void Main()
  {
    var dynMeth = new DynamicMethod ("Foo", null, null, typeof (Test));
    ILGenerator gen = dynMeth.GetILGenerator();
    gen.EmitWriteLine ("Hello world");
    gen.Emit (OpCodes.Ret);
    dynMeth.Invoke (null, null);                    // Hello world
  }
}
OpCodes has a static read-only field for every IL opcode. Most of the functionality is exposed through various opcodes, although ILGenerator also has specialized methods for generating labels and local variables and for exception handling. A method always ends in Opcodes.Ret, which means “return,” or some kind of branching/throwing instruction. The EmitWriteLine method on ILGenerator is a shortcut for Emitting a number of lower-level opcodes. We would get the same result if we replaced the call to EmitWriteLine with this:

MethodInfo writeLineStr = typeof (Console).GetMethod ("WriteLine",
                           new Type[] { typeof (string) });
gen.Emit (OpCodes.Ldstr, "Hello world");     // Load a string
gen.Emit (OpCodes.Call, writeLineStr);       // Call a method
Note that we passed typeof(Test) into DynamicMethod’s constructor. This gives the dynamic method access to the nonpublic methods of that type, allowing us to do this:

public class Test
{
  static void Main()
  {
    var dynMeth = new DynamicMethod ("Foo", null, null, typeof (Test));
    ILGenerator gen = dynMeth.GetILGenerator();

    MethodInfo privateMethod = typeof(Test).GetMethod ("HelloWorld",
      BindingFlags.Static | BindingFlags.NonPublic);

    gen.Emit (OpCodes.Call, privateMethod);     // Call HelloWorld
    gen.Emit (OpCodes.Ret);

    dynMeth.Invoke (null, null);                // Hello world
  }

  static void HelloWorld()       // private method, yet we can call it
  {
    Console.WriteLine ("Hello world");
  }
}
Understanding IL requires a considerable investment of time. Rather than understand all the opcodes, it’s much easier to compile a C# program and then examine, copy, and tweak the IL. LINQPad displays the IL for any method or code snippet that you type, and assembly viewing tools such ILSpy are useful for examining existing assemblies.

The Evaluation Stack
Central to IL is the concept of the evaluation stack. To call a method with arguments, you first push (“load”) the arguments onto the evaluation stack and then call the method. The method then pops the arguments it needs from the evaluation stack. We demonstrated this previously, in calling Console.WriteLine. Here’s a similar example with an integer:

var dynMeth = new DynamicMethod ("Foo", null, null, typeof(void));
ILGenerator gen = dynMeth.GetILGenerator();
MethodInfo writeLineInt = typeof (Console).GetMethod ("WriteLine",
                                        new Type[] { typeof (int) });

// The Ldc* op-codes load numeric literals of various types and sizes.

gen.Emit (OpCodes.Ldc_I4, 123);        // Push a 4-byte integer onto stack
gen.Emit (OpCodes.Call, writeLineInt);

gen.Emit (OpCodes.Ret);
dynMeth.Invoke (null, null);           // 123
To add two numbers together, you first load each number onto the evaluation stack, and then call Add. The Add opcode pops two values from the evaluation stack and pushes the result back on. The following adds 2 and 2, and then writes the result using the writeLine method obtained previously:

gen.Emit (OpCodes.Ldc_I4, 2);           // Push a 4-byte integer, value=2
gen.Emit (OpCodes.Ldc_I4, 2);           // Push a 4-byte integer, value=2
gen.Emit (OpCodes.Add);                 // Add the result together
gen.Emit (OpCodes.Call, writeLineInt);
To calculate 10 / 2 + 1, you can do either this:

gen.Emit (OpCodes.Ldc_I4, 10);
gen.Emit (OpCodes.Ldc_I4, 2);
gen.Emit (OpCodes.Div);
gen.Emit (OpCodes.Ldc_I4, 1);
gen.Emit (OpCodes.Add);
gen.Emit (OpCodes.Call, writeLineInt);
or this:

gen.Emit (OpCodes.Ldc_I4, 1);
gen.Emit (OpCodes.Ldc_I4, 10);
gen.Emit (OpCodes.Ldc_I4, 2);
gen.Emit (OpCodes.Div);
gen.Emit (OpCodes.Add);
gen.Emit (OpCodes.Call, writeLineInt);
Passing Arguments to a Dynamic Method
The Ldarg and Ldarg_XXX opcodes load an argument passed into a method onto the stack. To return a value, leave exactly one value on the stack upon finishing. For this to work, you must specify the return type and argument types when calling DynamicMethod’s constructor. The following creates a dynamic method that returns the sum of two integers:

DynamicMethod dynMeth = new DynamicMethod ("Foo",
  typeof (int),                              // Return type = int
  new[] { typeof (int), typeof (int) },      // Parameter types = int, int
  typeof (void));

ILGenerator gen = dynMeth.GetILGenerator();

gen.Emit (OpCodes.Ldarg_0);      // Push first arg onto eval stack
gen.Emit (OpCodes.Ldarg_1);      // Push second arg onto eval stack
gen.Emit (OpCodes.Add);          // Add them together (result on stack)
gen.Emit (OpCodes.Ret);          // Return with stack having 1 value

int result = (int) dynMeth.Invoke (null, new object[] { 3, 4 } );   // 7
WARNING
When you exit, the evaluation stack must have exactly 0 or 1 item (depending on whether your method returns a value). If you violate this, the CLR will refuse to execute your method. You can remove an item from the stack without processing it by emitting OpCodes.Pop.

Rather than calling Invoke, it can be more convenient to work with a dynamic method as a typed delegate. The CreateDelegate method achieves just this. In our case, the delegate that we need has two integer parameters and an integer return type. We can use the Func<int, int, int> delegate for this purpose. The last line of our preceding example then becomes the following:

var func = (Func<int,int,int>) dynMeth.CreateDelegate
                                 (typeof (Func<int,int,int>));
int result = func (3, 4);  // 7
NOTE
A delegate also eliminates the overhead of dynamic method invocation—saving a few microseconds per call.

We demonstrate how to pass by reference in “Emitting Type Members”.

Generating Local Variables
You can declare a local variable by calling DeclareLocal on an ILGenerator. This returns a LocalBuilder object, which you can use in conjunction with opcodes such as Ldloc (load a local variable) or Stloc (store a local variable). Ldloc pushes the evaluation stack; Stloc pops it. For example, consider the following C# code:

int x = 6;
int y = 7;
x *= y;
Console.WriteLine (x);
The following generates the preceding code dynamically:

var dynMeth = new DynamicMethod ("Test", null, null, typeof (void));
ILGenerator gen = dynMeth.GetILGenerator();

LocalBuilder localX = gen.DeclareLocal (typeof (int));    // Declare x
LocalBuilder localY = gen.DeclareLocal (typeof (int));    // Declare y

gen.Emit (OpCodes.Ldc_I4, 6);        // Push literal 6 onto eval stack
gen.Emit (OpCodes.Stloc, localX);    // Store in localX
gen.Emit (OpCodes.Ldc_I4, 7);        // Push literal 7 onto eval stack
gen.Emit (OpCodes.Stloc, localY);    // Store in localY

gen.Emit (OpCodes.Ldloc, localX);    // Push localX onto eval stack
gen.Emit (OpCodes.Ldloc, localY);    // Push localY onto eval stack
gen.Emit (OpCodes.Mul);              // Multiply values together
gen.Emit (OpCodes.Stloc, localX);    // Store the result to localX

gen.EmitWriteLine (localX);          // Write the value of localX
gen.Emit (OpCodes.Ret);

dynMeth.Invoke (null, null);         // 42
Branching
In IL, there are no while, do, and for loops; it’s all done with labels and the equivalent of goto and conditional goto statements. These are the branching opcodes, such as Br (branch unconditionally), Brtrue (branch if the value on the evaluation stack is true), and Blt (branch if the first value is less than the second value).

To set a branch target, first call DefineLabel (this returns a Label object), and then call MarkLabel at the place where you want to anchor the label. For example, consider the following C# code:

int x = 5;
while (x <= 10) Console.WriteLine (x++);
We can emit this as follows:

ILGenerator gen = ...

Label startLoop = gen.DefineLabel();                  // Declare labels
Label endLoop = gen.DefineLabel();

LocalBuilder x = gen.DeclareLocal (typeof (int));     // int x
gen.Emit (OpCodes.Ldc_I4, 5);                         //
gen.Emit (OpCodes.Stloc, x);                          // x = 5
gen.MarkLabel (startLoop);
  gen.Emit (OpCodes.Ldc_I4, 10);              // Load 10 onto eval stack
  gen.Emit (OpCodes.Ldloc, x);                // Load x onto eval stack

  gen.Emit (OpCodes.Blt, endLoop);            // if (x > 10) goto endLoop

  gen.EmitWriteLine (x);                      // Console.WriteLine (x)

  gen.Emit (OpCodes.Ldloc, x);                // Load x onto eval stack
  gen.Emit (OpCodes.Ldc_I4, 1);               // Load 1 onto the stack
  gen.Emit (OpCodes.Add);                     // Add them together
  gen.Emit (OpCodes.Stloc, x);                // Save result back to x

  gen.Emit (OpCodes.Br, startLoop);           // return to start of loop
gen.MarkLabel (endLoop);

gen.Emit (OpCodes.Ret);
Instantiating Objects and Calling Instance Methods
The IL equivalent of new is the Newobj opcode. This takes a constructor and loads the constructed object onto the evaluation stack. For instance, the following constructs a StringBuilder:

var dynMeth = new DynamicMethod ("Test", null, null, typeof (void));
ILGenerator gen = dynMeth.GetILGenerator();

ConstructorInfo ci = typeof (StringBuilder).GetConstructor (new Type[0]);
gen.Emit (OpCodes.Newobj, ci);
After loading an object onto the evaluation stack, you can use the Call or Callvirt opcode to invoke the object’s instance methods. Extending this example, we’ll query the StringBuilder’s MaxCapacity property by calling the property’s get accessor and then write out the result:

gen.Emit (OpCodes.Callvirt, typeof (StringBuilder)
                            .GetProperty ("MaxCapacity").GetGetMethod());

gen.Emit (OpCodes.Call, typeof (Console).GetMethod ("WriteLine",
                                         new[] { typeof (int) } ));
gen.Emit (OpCodes.Ret);
dynMeth.Invoke (null, null);              // 2147483647
To emulate C# calling semantics:

Use Call to invoke static methods and value type instance methods.

Use Callvirt to invoke reference type instance methods (whether or not they’re declared virtual).

In our example, we used Callvirt on the StringBuilder instance—even though MaxProperty is not virtual. This doesn’t cause an error: it simply performs a nonvirtual call, instead. Always invoking reference type instance methods with Callvirt avoids risking the opposite condition: invoking a virtual method with Call. (The risk is real. The author of the target method may later change its declaration.) Callvirt also has the benefit of checking that the receiver is non-null.

WARNING
Invoking a virtual method with Call bypasses virtual calling semantics and calls that method directly. This is rarely desirable and, in effect, violates type safety.

In the following example, we construct a StringBuilder passing in two arguments, append ", world!" to the StringBuilder, and then call ToString on it:

// We will call:   new StringBuilder ("Hello", 1000)

ConstructorInfo ci = typeof (StringBuilder).GetConstructor (
                     new[] { typeof (string), typeof (int) } );

gen.Emit (OpCodes.Ldstr, "Hello");   // Load a string onto the eval stack
gen.Emit (OpCodes.Ldc_I4, 1000);     // Load an int onto the eval stack
gen.Emit (OpCodes.Newobj, ci);       // Construct the StringBuilder

Type[] strT = { typeof (string) };
gen.Emit (OpCodes.Ldstr, ", world!");
gen.Emit (OpCodes.Call, typeof (StringBuilder).GetMethod ("Append", strT));
gen.Emit (OpCodes.Callvirt, typeof (object).GetMethod ("ToString"));
gen.Emit (OpCodes.Call, typeof (Console).GetMethod ("WriteLine", strT));
gen.Emit (OpCodes.Ret);
dynMeth.Invoke (null, null);        // Hello, world!
For fun, we called GetMethod on typeof(object) and then used Callvirt to perform a virtual method call on ToString. We could have gotten the same result by calling ToString on the StringBuilder type itself:

gen.Emit (OpCodes.Callvirt, typeof (StringBuilder).GetMethod ("ToString",
                                                          new Type[0] ));
(The empty type array is required in calling GetMethod because StringBuilder overloads ToString with another signature.)

NOTE
Had we called object’s ToString method nonvirtually:

gen.Emit (OpCodes.Call,
          typeof (object).GetMethod ("ToString"));
the result would have been System.Text.StringBuilder. In other words, we would have circumvented StringBuilder’s ToString override and called object’s version directly.

Exception Handling
ILGenerator provides dedicated methods for exception handling. Thus, the translation for this C# code:

try                               { throw new NotSupportedException(); }
catch (NotSupportedException ex)  { Console.WriteLine (ex.Message);    }
finally                           { Console.WriteLine ("Finally");     }
is this:

MethodInfo getMessageProp = typeof (NotSupportedException)
                            .GetProperty ("Message").GetGetMethod();

MethodInfo writeLineString = typeof (Console).GetMethod ("WriteLine",
                                             new[] { typeof (object) } );
gen.BeginExceptionBlock();
  ConstructorInfo ci = typeof (NotSupportedException).GetConstructor (
                                                        new Type[0] );
  gen.Emit (OpCodes.Newobj, ci);
  gen.Emit (OpCodes.Throw);
gen.BeginCatchBlock (typeof (NotSupportedException));
  gen.Emit (OpCodes.Callvirt, getMessageProp);
  gen.Emit (OpCodes.Call, writeLineString);
gen.BeginFinallyBlock();
  gen.EmitWriteLine ("Finally");
gen.EndExceptionBlock();
Just as in C#, you can include multiple catch blocks. To rethrow the same exception, emit the Rethrow opcode.

WARNING
ILGenerator provides a helper method called ThrowException. This contains a bug, however, preventing it from being used with a DynamicMethod. It works only with a MethodBuilder (see the next section).

Emitting Assemblies and Types
Although DynamicMethod is convenient, it can generate only methods. If you need to emit any other construct—or a complete type—you need to use the full “heavyweight” API. This means dynamically building an assembly and module. The assembly need not have a disk presence (in fact, it cannot, because .NET 5+ and .NET Core do not let you save generated assemblies to disk).

Let’s assume that we want to dynamically build a type. Because a type must reside in a module within an assembly, we first must create the assembly and module before we can create the type. This is the job of the AssemblyBuilder and ModuleBuilder types:

AssemblyName aname = new AssemblyName ("MyDynamicAssembly");

AssemblyBuilder assemBuilder =
  AssemblyBuilder.DefineDynamicAssembly (aname, AssemblyBuilderAccess.Run);

ModuleBuilder modBuilder = assemBuilder.DefineDynamicModule ("DynModule");
NOTE
You can’t add a type to an existing assembly, because an assembly is immutable after it’s created.

Dynamic assemblies are not garbage-collected and remain in memory until the process ends, unless you specify AssemblyBuilderAccess.RunAndCollect when defining the assembly. Various restrictions apply to collectible assemblies (see http://albahari.com/dynamiccollect).

After we have a module in which the type can reside, we can use TypeBuilder to create the type. The following defines a class called Widget:

TypeBuilder tb = modBuilder.DefineType ("Widget", TypeAttributes.Public);
The TypeAttributes flags enum supports the CLR type modifiers you see when disassembling a type with ildasm. As well as member visibility flags, this includes type modifiers such as Abstract and Sealed—and Interface for defining a .NET interface. It also includes Serializable, which is equivalent to applying the [Serializable] attribute in C#, and Explicit, which is equivalent to applying [StructLayout(LayoutKind.Explicit)]. We describe how to apply other kinds of attributes later in this chapter, in “Attaching Attributes”.

NOTE
The DefineType method also accepts an optional base type:

To define a struct, specify a base type of System.ValueType.

To define a delegate, specify a base type of System.MulticastDelegate.

To implement an interface, use the constructor that accepts an array of interface types.

To define an interface, specify TypeAttributes.Interface | TypeAttributes.Abstract.

Defining a delegate type requires a number of extra steps. In his weblog, Joel Pobar demonstrates how this is done in his article titled “Creating delegate types via Reflection.Emit”.

We can now create members within the type:

MethodBuilder methBuilder = tb.DefineMethod ("SayHello",
                                             MethodAttributes.Public,
                                             null, null);
ILGenerator gen = methBuilder.GetILGenerator();
gen.EmitWriteLine ("Hello world");
gen.Emit (OpCodes.Ret);
We’re now ready to create the type, which finalizes its definition:

Type t = tb.CreateType();
After the type is created, we can use ordinary reflection to inspect and perform late binding:

object o = Activator.CreateInstance (t);
t.GetMethod ("SayHello").Invoke (o, null);        // Hello world
The Reflection.Emit Object Model
Figure 18-2 illustrates the essential types in System.Reflection.Emit. Each type describes a CLR construct and is based on a counterpart in the System.Reflection namespace. This allows you to use emitted constructs in place of normal constructs when building a type. For example, we previously called Console.WriteLine, as follows:

MethodInfo writeLine = typeof(Console).GetMethod ("WriteLine",
                                       new Type[] { typeof (string) });
gen.Emit (OpCodes.Call, writeLine);
We could just as easily call a dynamically generated method by calling gen.Emit with a MethodBuilder instead of a MethodInfo. This is essential—otherwise, you couldn’t write one dynamic method that called another in the same type.


Figure 18-2. System.Reflection.Emit
Recall that you must call CreateType on a TypeBuilder when you’ve finished populating it. Calling CreateType seals the TypeBuilder and all its members—so nothing more can be added or changed—and gives you back a real Type that you can instantiate.

Before you call CreateType, the TypeBuilder and its members are in an “uncreated” state. There are significant restrictions on what you can do with uncreated constructs. In particular, you cannot call any of the members that return MemberInfo objects, such as GetMembers, GetMethod, or GetProperty—these all throw an exception. If you want to refer to members of an uncreated type, you must use the original emissions:

TypeBuilder tb = ...

MethodBuilder method1 = tb.DefineMethod ("Method1", ...);
MethodBuilder method2 = tb.DefineMethod ("Method2", ...);

ILGenerator gen1 = method1.GetILGenerator();

// Suppose we want method1 to call method2:

gen1.Emit (OpCodes.Call, method2);                    // Right
gen1.Emit (OpCodes.Call, tb.GetMethod ("Method2"));   // Wrong
After calling CreateType, you can reflect on and activate not only the Type returned but also the original TypeBuilder object. The TypeBuilder, in fact, morphs into a proxy for the real Type. You’ll see why this feature is important in “Awkward Emission Targets”.

Emitting Type Members
All the examples in this section assume a TypeBuilder, tb, has been instantiated, as follows:

AssemblyName aname = new AssemblyName ("MyEmissions");

AssemblyBuilder assemBuilder = AssemblyBuilder.DefineDynamicAssembly (
  aname, AssemblyBuilderAccess.Run);

ModuleBuilder modBuilder = assemBuilder.DefineDynamicModule ("MainModule");

TypeBuilder tb = modBuilder.DefineType ("Widget", TypeAttributes.Public);
Emitting Methods
You can specify a return type and parameter types when calling DefineMethod, in the same manner as when instantiating a DynamicMethod. For instance, the following method:

public static double SquareRoot (double value) => Math.Sqrt (value);
can be generated like this:

MethodBuilder mb = tb.DefineMethod ("SquareRoot",
  MethodAttributes.Static | MethodAttributes.Public,
  CallingConventions.Standard,
  typeof (double),                     // Return type
  new[]  { typeof (double) } );        // Parameter types

mb.DefineParameter (1, ParameterAttributes.None, "value");  // Assign name

ILGenerator gen = mb.GetILGenerator();
gen.Emit (OpCodes.Ldarg_0);                                // Load 1st arg
gen.Emit (OpCodes.Call, typeof(Math).GetMethod ("Sqrt"));
gen.Emit (OpCodes.Ret);

Type realType = tb.CreateType();
double x = (double) tb.GetMethod ("SquareRoot").Invoke (null,
                                                new object[] { 10.0 });
Console.WriteLine (x);   // 3.16227766016838
Calling DefineParameter is optional and is typically done to assign the parameter a name. The number 1 refers to the first parameter (0 refers to the return value). If you call DefineParameter, the parameter is implicitly named __p1, __p2, and so on. Assigning names makes sense if you will write the assembly to disk; it makes your methods friendly to consumers.

NOTE
DefineParameter returns a ParameterBuilder object upon which you can call SetCustomAttribute to attach attributes (see “Attaching Attributes”).

To emit pass-by-reference parameters, such as in the following C# method:

public static void SquareRoot (ref double value)
  => value = Math.Sqrt (value);
call MakeByRefType on the parameter type(s):

MethodBuilder mb = tb.DefineMethod ("SquareRoot",
  MethodAttributes.Static | MethodAttributes.Public,
  CallingConventions.Standard,
  null,
  new Type[] { typeof (double).MakeByRefType() } );

mb.DefineParameter (1, ParameterAttributes.None, "value");

ILGenerator gen = mb.GetILGenerator();
gen.Emit (OpCodes.Ldarg_0);
gen.Emit (OpCodes.Ldarg_0);
gen.Emit (OpCodes.Ldind_R8);
gen.Emit (OpCodes.Call, typeof (Math).GetMethod ("Sqrt"));
gen.Emit (OpCodes.Stind_R8);
gen.Emit (OpCodes.Ret);

Type realType = tb.CreateType();
object[] args = { 10.0 };
tb.GetMethod ("SquareRoot").Invoke (null, args);
Console.WriteLine (args[0]);                     // 3.16227766016838
The opcodes here were copied from a disassembled C# method. Notice the difference in semantics for accessing parameters passed by reference: Ldind and Stind mean “load indirectly” and “store indirectly,” respectively. The R8 suffix means an eight-byte floating-point number.

The process for emitting out parameters is identical, except that you call DefineParameter, as follows:

mb.DefineParameter (1, ParameterAttributes.Out, "value");
Generating instance methods
To generate an instance method, specify MethodAttributes.Instance when calling DefineMethod:

MethodBuilder mb = tb.DefineMethod ("SquareRoot",
  MethodAttributes.Instance | MethodAttributes.Public
  ...
With instance methods, argument zero is implicitly this; the remaining arguments start at 1. So, Ldarg_0 loads this onto the evaluation stack; Ldarg_1 loads the first real method argument.

Overriding methods
Overriding a virtual method in a base class is easy: simply define a method with an identical name, signature, and return type, specifying MethodAttributes.Virtual when calling DefineMethod. The same applies when implementing interface methods.

TypeBuilder also exposes a method called DefineMethodOverride that overrides a method with a different name. This makes sense only with explicit interface implementation; in other scenarios, use DefineMethod.

HideBySig
If you’re subclassing another type, it’s nearly always worth specifying MethodAt⁠tributes.HideBySig when defining methods. HideBySig ensures that C#-style method-hiding semantics are applied, which is that a base method is hidden only if a subtype defines a method with an identical signature. Without HideBySig, method hiding considers only the name, so Foo(string) in the subtype will hide Foo() in the base type, which is generally undesirable.

Emitting Fields and Properties
To create a field, you call DefineField on a TypeBuilder, specifying the desired field name, type, and visibility. The following creates a private integer field called “length”:

FieldBuilder field = tb.DefineField ("length", typeof (int),
                                      FieldAttributes.Private);
Creating a property or indexer requires a few more steps. First, call DefineProperty on a TypeBuilder, providing it with the name and type of the property:

PropertyBuilder prop = tb.DefineProperty (
                         "Text",                      // Name of property
                         PropertyAttributes.None,
                         typeof (string),             // Property type
                         new Type[0]                  // Indexer types
                       );
(If you’re writing an indexer, the final argument is an array of indexer types.) Note that we haven’t specified the property visibility: this is done individually on the accessor methods.

The next step is to write the get and set methods. By convention, their names are prefixed with “get_” or “set_”. You then attach them to the property by calling SetGetMethod and SetSetMethod on the PropertyBuilder.

To give a complete example, let’s take the following field and property declaration

string _text;
public string Text
{
  get          => _text;
  internal set => _text = value;
}
and generate it dynamically:

FieldBuilder field = tb.DefineField ("_text", typeof (string),
                                      FieldAttributes.Private);
PropertyBuilder prop = tb.DefineProperty (
                         "Text",                      // Name of property
                         PropertyAttributes.None,
                         typeof (string),             // Property type
                         new Type[0]);                // Indexer types

MethodBuilder getter = tb.DefineMethod (
  "get_Text",                                         // Method name
  MethodAttributes.Public | MethodAttributes.SpecialName,
  typeof (string),                                    // Return type
  new Type[0]);                                       // Parameter types

ILGenerator getGen = getter.GetILGenerator();
getGen.Emit (OpCodes.Ldarg_0);        // Load "this" onto eval stack
getGen.Emit (OpCodes.Ldfld, field);   // Load field value onto eval stack
getGen.Emit (OpCodes.Ret);            // Return

MethodBuilder setter = tb.DefineMethod (
  "set_Text",
  MethodAttributes.Assembly | MethodAttributes.SpecialName,
  null,                                                 // Return type
  new Type[] { typeof (string) } );                     // Parameter types

ILGenerator setGen = setter.GetILGenerator();
setGen.Emit (OpCodes.Ldarg_0);        // Load "this" onto eval stack
setGen.Emit (OpCodes.Ldarg_1);        // Load 2nd arg, i.e., value
setGen.Emit (OpCodes.Stfld, field);   // Store value into field
setGen.Emit (OpCodes.Ret);            // return

prop.SetGetMethod (getter);           // Link the get method and property
prop.SetSetMethod (setter);           // Link the set method and property
We can test the property as follows:

Type t = tb.CreateType();
object o = Activator.CreateInstance (t);
t.GetProperty ("Text").SetValue (o, "Good emissions!", new object[0]);
string text = (string) t.GetProperty ("Text").GetValue (o, null);

Console.WriteLine (text);             // Good emissions!
Notice that in defining the accessor MethodAttributes, we included SpecialName. This instructs compilers to disallow direct binding to these methods when statically referencing the assembly. It also ensures that the accessors are handled appropriately by reflection tools and Visual Studio’s IntelliSense.

NOTE
You can emit events in a similar manner, by calling DefineE⁠vent on a TypeBuilder. You then write explicit event accessor methods and attach them to the EventBuilder by calling SetAddOnMethod and SetRemoveOnMethod.

Emitting Constructors
You can define your own constructors by calling DefineConstructor on a type builder. You’re not obliged to do so—a default parameterless constructor is automatically provided if you don’t. The default constructor calls the base class constructor if subtyping, just like in C#. Defining one or more constructors displaces this default constructor.

If you need to initialize fields, the constructor’s a good spot. In fact, it’s the only spot: C#’s field initializers don’t have special CLR support—they are simply a syntactic shortcut for assigning values to fields in the constructor.

So, to reproduce this:

class Widget
{
  int _capacity = 4000;
}
you would define a constructor, as follows:

FieldBuilder field = tb.DefineField ("_capacity", typeof (int),
                                      FieldAttributes.Private);
ConstructorBuilder c = tb.DefineConstructor (
  MethodAttributes.Public,
  CallingConventions.Standard,
  new Type[0]);                  // Constructor parameters

ILGenerator gen = c.GetILGenerator();

gen.Emit (OpCodes.Ldarg_0);             // Load "this" onto eval stack
gen.Emit (OpCodes.Ldc_I4, 4000);        // Load 4000 onto eval stack
gen.Emit (OpCodes.Stfld, field);        // Store it to our field
gen.Emit (OpCodes.Ret);
Calling base constructors
If subclassing another type, the constructor we just wrote would circumvent the base class constructor. This is unlike C#, in which the base class constructor is always called, whether directly or indirectly. For instance, given the following code:

class A     { public A() { Console.Write ("A"); } }
class B : A { public B() {} }
the compiler, in effect, will translate the second line into this:

class B : A { public B() : base() {} }
This is not the case when generating IL: you must explicitly call the base constructor if you want it to execute (which nearly always, you do). Assuming the base class is called A, here’s how to do it:

gen.Emit (OpCodes.Ldarg_0);
ConstructorInfo baseConstr = typeof (A).GetConstructor (new Type[0]);
gen.Emit (OpCodes.Call, baseConstr);
Calling constructors with arguments is just the same as with methods.

Attaching Attributes
You can attach custom attributes to a dynamic construct by calling SetCustomAttribute with a CustomAttributeBuilder. For example, suppose that we want to attach the following attribute declaration to a field or property:

[XmlElement ("FirstName", Namespace="http://test/", Order=3)]
This relies on the XmlElementAttribute constructor that accepts a single string. To use CustomAttributeBuilder, we must retrieve this constructor as well as the two additional properties that we want to set (Namespace and Order):

Type attType = typeof (XmlElementAttribute);

ConstructorInfo attConstructor = attType.GetConstructor (
  new Type[] { typeof (string) } );

var att = new CustomAttributeBuilder (
  attConstructor,                        // Constructor
  new object[] { "FirstName" },          // Constructor arguments
  new PropertyInfo[] 
  {
    attType.GetProperty ("Namespace"),   // Properties
    attType.GetProperty ("Order")
  },
  new object[] { "http://test/", 3 }     // Property values
);

myFieldBuilder.SetCustomAttribute (att);
// or propBuilder.SetCustomAttribute (att);
// or typeBuilder.SetCustomAttribute (att);  etc
Emitting Generic Methods and Types
All the examples in this section assume that modBuilder has been instantiated as follows:

AssemblyName aname = new AssemblyName ("MyEmissions");

AssemblyBuilder assemBuilder = AssemblyBuilder.DefineDynamicAssembly (
  aname, AssemblyBuilderAccess.Run);

ModuleBuilder modBuilder = assemBuilder.DefineDynamicModule ("MainModule");
Defining Generic Methods
To emit a generic method:

Call DefineGenericParameters on a MethodBuilder to obtain an array of GenericTypeParameterBuilder objects.

Call SetSignature on a MethodBuilder using these generic type parameters.

Optionally, name the parameters as you would otherwise.

For example, the following generic method:

public static T Echo<T> (T value)
{
  return value;
}
can be emitted like this:

TypeBuilder tb = modBuilder.DefineType ("Widget", TypeAttributes.Public);

MethodBuilder mb = tb.DefineMethod ("Echo", MethodAttributes.Public |
                                            MethodAttributes.Static);
GenericTypeParameterBuilder[] genericParams
  = mb.DefineGenericParameters ("T");

mb.SetSignature (genericParams[0],     // Return type
                 null, null,
                 genericParams,        // Parameter types
                 null, null);

mb.DefineParameter (1, ParameterAttributes.None, "value");   // Optional

ILGenerator gen = mb.GetILGenerator();
gen.Emit (OpCodes.Ldarg_0);
gen.Emit (OpCodes.Ret);
The DefineGenericParameters method accepts any number of string arguments—these correspond to the desired generic type names. In this example, we needed just one generic type called T. GenericTypeParameterBuilder is based on System.Type, so you can use it in place of a TypeBuilder when emitting opcodes.

GenericTypeParameterBuilder also lets you specify a base type constraint:

genericParams[0].SetBaseTypeConstraint (typeof (Foo));
and interface constraints:

genericParams[0].SetInterfaceConstraints (typeof (IComparable));
To replicate this:

public static T Echo<T> (T value) where T : IComparable<T>
you would write:

genericParams[0].SetInterfaceConstraints (
  typeof (IComparable<>).MakeGenericType (genericParams[0]) );
For other kinds of constraints, call SetGenericParameterAttributes. This accepts a member of the GenericParameterAttributes enum, which includes the following values:

DefaultConstructorConstraint
NotNullableValueTypeConstraint
ReferenceTypeConstraint
Covariant
Contravariant
The last two are equivalent to applying the out and in modifiers to the type parameters.

Defining Generic Types
You can define generic types in a similar fashion. The difference is that you call DefineGenericParameters on the TypeBuilder rather than the MethodBuilder. So, to reproduce this:

public class Widget<T>
{
  public T Value;
}
you would do the following:

TypeBuilder tb = modBuilder.DefineType ("Widget", TypeAttributes.Public);

GenericTypeParameterBuilder[] genericParams
  = tb.DefineGenericParameters ("T");

tb.DefineField ("Value", genericParams[0], FieldAttributes.Public);
Generic constraints can be added, just as with a method.

Awkward Emission Targets
All of the examples in this section assume that a modBuilder has been instantiated as in previous sections.

Uncreated Closed Generics
Suppose that you want to emit a method that uses a closed generic type:

public class Widget
{
  public static void Test() { var list = new List<int>(); }
}
The process is fairly straightforward:

TypeBuilder tb = modBuilder.DefineType ("Widget", TypeAttributes.Public);

MethodBuilder mb = tb.DefineMethod ("Test", MethodAttributes.Public |
                                            MethodAttributes.Static);
ILGenerator gen = mb.GetILGenerator();

Type variableType = typeof (List<int>);

ConstructorInfo ci = variableType.GetConstructor (new Type[0]);

LocalBuilder listVar = gen.DeclareLocal (variableType);
gen.Emit (OpCodes.Newobj, ci);
gen.Emit (OpCodes.Stloc, listVar);
gen.Emit (OpCodes.Ret);
Now suppose that instead of a list of integers, we want a list of widgets:

public class Widget
{
  public static void Test() { var list = new List<Widget>(); }
}
In theory, this is a simple modification; all we do is replace this line:

Type variableType = typeof (List<int>);
with this one:

Type variableType = typeof (List<>).MakeGenericType (tb);
Unfortunately, this causes a NotSupportedException to be thrown when we then call GetConstructor. The problem is that you cannot call GetConstructor on a generic type closed with an uncreated type builder. The same goes for GetField and GetMethod.

The solution is unintuitive. TypeBuilder provides three static methods:

public static ConstructorInfo GetConstructor (Type, ConstructorInfo);
public static FieldInfo       GetField       (Type, FieldInfo);
public static MethodInfo      GetMethod      (Type, MethodInfo);
Although it doesn’t appear so, these methods exist specifically to obtain members of generic types closed with uncreated type builders! The first parameter is the closed generic type; the second parameter is the member that you want on the unbound generic type. Here’s the corrected version of our example:

MethodBuilder mb = tb.DefineMethod ("Test", MethodAttributes.Public |
                                            MethodAttributes.Static);
ILGenerator gen = mb.GetILGenerator();

Type variableType = typeof (List<>).MakeGenericType (tb);

ConstructorInfo unbound = typeof (List<>).GetConstructor (new Type[0]);
ConstructorInfo ci = TypeBuilder.GetConstructor (variableType, unbound);

LocalBuilder listVar = gen.DeclareLocal (variableType);
gen.Emit (OpCodes.Newobj, ci);
gen.Emit (OpCodes.Stloc, listVar);
gen.Emit (OpCodes.Ret);
Circular Dependencies
Suppose that you want to build two types that reference each other, such as these:

class A { public B Bee; }
class B { public A Aye; }
You can generate this dynamically, as follows:

var publicAtt = FieldAttributes.Public;

TypeBuilder aBuilder = modBuilder.DefineType ("A");
TypeBuilder bBuilder = modBuilder.DefineType ("B");

FieldBuilder bee = aBuilder.DefineField ("Bee", bBuilder, publicAtt);
FieldBuilder aye = bBuilder.DefineField ("Aye", aBuilder, publicAtt);

Type realA = aBuilder.CreateType();
Type realB = bBuilder.CreateType();
Notice that we didn’t call CreateType on aBuilder or bBuilder until we populated both objects. The principle is this: first hook everything up, and then call CreateType on each type builder.

Interestingly, the realA type is valid but dysfunctional until you call CreateType on bBuilder. (If you started using aBuilder prior to this, an exception would be thrown when you tried to access field Bee.)

You might wonder how bBuilder knows to “fix up” realA after creating realB. The answer is that it doesn’t: realA can fix itself the next time it’s used. This is possible because after calling CreateType, a TypeBuilder morphs into a proxy for the real runtime type. So, realA, with its references to bBuilder, can easily obtain the metadata it needs for the upgrade.

This system works when the type builder demands simple information of the unconstructed type—information that can be predetermined—such as type, member, and object references. In creating realA, the type builder doesn’t need to know, for instance, how many bytes realB will eventually occupy in memory. This is just as well because realB has not yet been created! But now imagine that realB was a struct. The final size of realB is now critical information in creating realA.

If the relationship is noncyclical; for instance:

struct A { public B Bee; }
struct B {               }
you can solve this by first creating struct B and then struct A. But consider this:

struct A { public B Bee; }
struct B { public A Aye; }
We won’t try to emit this because it’s nonsensical to have two structs contain each other (C# generates a compile-time error if you try). But the following variation is both legal and useful:

public struct S<T> { ... }    // S can be empty and this demo will work.

class A { S<B> Bee; }
class B { S<A> Aye; }
In creating A, a TypeBuilder now needs to know the memory footprint of B, and vice versa. To illustrate, let’s assume that struct S is defined statically. Here’s the code to emit classes A and B:

var pub = FieldAttributes.Public;

TypeBuilder aBuilder = modBuilder.DefineType ("A");
TypeBuilder bBuilder = modBuilder.DefineType ("B");

aBuilder.DefineField ("Bee", typeof(S<>).MakeGenericType (bBuilder), pub);
bBuilder.DefineField ("Aye", typeof(S<>).MakeGenericType (aBuilder), pub);

Type realA = aBuilder.CreateType();    // Error: cannot load type B
Type realB = bBuilder.CreateType();
CreateType now throws a TypeLoadException no matter in which order you go:

Call aBuilder.CreateType first, and it says “cannot load type B”.

Call bBuilder.CreateType first, and it says “cannot load type A”!

To solve this, you must allow the type builder to create realB partway through creating realA. You do this by handling the TypeResolve event on the AppDomain class just before calling CreateType. So, in our example, we replace the last two lines with this:

TypeBuilder[] uncreatedTypes = { aBuilder, bBuilder };

ResolveEventHandler handler = delegate (object o, ResolveEventArgs args)
{
  var type = uncreatedTypes.FirstOrDefault (t => t.FullName == args.Name);
  return type == null ? null : type.CreateType().Assembly;
};

AppDomain.CurrentDomain.TypeResolve += handler;

Type realA = aBuilder.CreateType();
Type realB = bBuilder.CreateType();

AppDomain.CurrentDomain.TypeResolve -= handler;
The TypeResolve event fires during the call to aBuilder.CreateType, at the point when it needs you to call CreateType on bBuilder.

NOTE
Handling the TypeResolve event as in this example is also necessary when defining a nested type, when the nested and parent types refer to each other.

Parsing IL
You can obtain information about the content of an existing method by calling GetMethodBody on a MethodBase object. This returns a MethodBody object that has properties for inspecting a method’s local variables, exception handling clauses, and stack size, as well as the raw IL. Rather like the reverse of Reflection.Emit!

Inspecting a method’s raw IL can be useful in profiling code. A simple use would be to determine which methods in an assembly have changed when an assembly is updated.

To illustrate parsing IL, we’ll write an application that disassembles IL in the style of ildasm. This could be used as the starting point for a code analysis tool or a higher-level language disassembler.

NOTE
Remember that in the reflection API, all of C#’s functional constructs are either represented by a MethodBase subtype or (in the case of properties, events, and indexers) have MethodBase objects attached to them.

Writing a Disassembler
Here is a sample of the output that our disassembler will produce:

IL_00EB:  ldfld        Disassembler._pos
IL_00F0:  ldloc.2
IL_00F1:  add
IL_00F2:  ldelema      System.Byte
IL_00F7:  ldstr        "Hello world"
IL_00FC:  call         System.Byte.ToString
IL_0101:  ldstr        " "
IL_0106:  call         System.String.Concat
To obtain this output, we must parse the binary tokens that make up the IL. The first step is to call the GetILAsByteArray method on MethodBody to obtain the IL as a byte array. To make the rest of the job easier, we will write this into a class as follows:

public class Disassembler
{
  public static string Disassemble (MethodBase method)
    => new Disassembler (method).Dis();

  StringBuilder _output;    // The result to which we'll keep appending
  Module _module;           // This will come in handy later
  byte[] _il;               // The raw byte code
  int _pos;                 // The position we're up to in the byte code

  Disassembler (MethodBase method)
  {
    _module = method.DeclaringType.Module;
    _il = method.GetMethodBody().GetILAsByteArray();
  }

  string Dis()
  {
    _output = new StringBuilder();
    while (_pos < _il.Length) DisassembleNextInstruction();
    return _output.ToString();
  }
}
The static Disassemble method will be the only public member of this class. All other members will be private to the disassembly process. The Dis method contains the “main” loop where we process each instruction.

With this skeleton in place, all that remains is to write DisassembleNextInstruction. But before doing so, it will help to load all the opcodes into a static dictionary so that we can access them by their 8- or 16-bit value. The easiest way to accomplish this is to use reflection to retrieve all the static fields whose type is OpCode in the OpCodes class:

static Dictionary<short,OpCode> _opcodes = new Dictionary<short,OpCode>();

static Disassembler()
{
  Dictionary<short, OpCode> opcodes = new Dictionary<short, OpCode>();
    foreach (FieldInfo fi in typeof (OpCodes).GetFields
                             (BindingFlags.Public | BindingFlags.Static))
      if (typeof (OpCode).IsAssignableFrom (fi.FieldType))
      {
        OpCode code = (OpCode) fi.GetValue (null);   // Get field's value
        if (code.OpCodeType != OpCodeType.Nternal)
          _opcodes.Add (code.Value, code);
      }
}
We’ve written it in a static constructor so that it executes just once.

Now we can write DisassembleNextInstruction. Each IL instruction consists of a one- or two-byte opcode, followed by an operand of zero, one, two, four, or eight bytes. (An exception is inline switch opcodes, which are followed by a variable number of operands.) So, we read the opcode, then the operand, and then write out the result:

void DisassembleNextInstruction()
{
  int opStart = _pos;

  OpCode code = ReadOpCode();
  string operand = ReadOperand (code);

  _output.AppendFormat ("IL_{0:X4}:  {1,-12} {2}",
                        opStart, code.Name, operand);
  _output.AppendLine();
}
To read an opcode, we advance one byte and see whether we have a valid instruction. If not, we advance another byte and look for a two-byte instruction:

OpCode ReadOpCode()
{
  byte byteCode = _il [_pos++];
  if (_opcodes.ContainsKey (byteCode)) return _opcodes [byteCode];

  if (_pos == _il.Length)  throw new Exception ("Unexpected end of IL");

  short shortCode = (short) (byteCode * 256 + _il [_pos++]);

  if (!_opcodes.ContainsKey (shortCode))
    throw new Exception ("Cannot find opcode " + shortCode);

  return _opcodes [shortCode];
}
To read an operand, we first must establish its length. We can do this based on the operand type. Because most are four bytes long, we can filter out the exceptions fairly easily in a conditional clause.

The next step is to call FormatOperand, which attempts to format the operand:

string ReadOperand (OpCode c)
{
  int operandLength =
    c.OperandType == OperandType.InlineNone
      ? 0 :
    c.OperandType == OperandType.ShortInlineBrTarget ||
    c.OperandType == OperandType.ShortInlineI ||
    c.OperandType == OperandType.ShortInlineVar
      ? 1 :
    c.OperandType == OperandType.InlineVar
      ? 2 :
    c.OperandType == OperandType.InlineI8 ||
    c.OperandType == OperandType.InlineR
      ? 8 :
    c.OperandType == OperandType.InlineSwitch
      ? 4 * (BitConverter.ToInt32 (_il, _pos) + 1) :
      4;  // All others are 4 bytes

  if (_pos + operandLength > _il.Length)
    throw new Exception ("Unexpected end of IL");

  string result = FormatOperand (c, operandLength);
  if (result == null)
  {                        // Write out operand bytes in hex
    result = "";
    for (int i = 0; i < operandLength; i++)
      result += _il [_pos + i].ToString ("X2") + " ";
  }
  _pos += operandLength;
  return result;
}
If the result of calling FormatOperand is null, it means the operand needs no special formatting, so we simply write it out in hexadecimal. We could test the disassembler at this point by writing a FormatOperand method that always returns null. Here’s what the output would look like:

IL_00A8:  ldfld        98 00 00 04
IL_00AD:  ldloc.2
IL_00AE:  add
IL_00AF:  ldelema      64 00 00 01
IL_00B4:  ldstr        26 04 00 70
IL_00B9:  call         B6 00 00 0A
IL_00BE:  ldstr        11 01 00 70
IL_00C3:  call         91 00 00 0A
...
Although the opcodes are correct, the operands are not much use. Instead of hexadecimal numbers, we want member names and strings. The FormatOperand method, when it’s written, will address this—identifying the special cases that benefit from such formatting. These comprise most four-byte operands and the short branch instructions:

string FormatOperand (OpCode c, int operandLength)
{
  if (operandLength == 0) return "";

  if (operandLength == 4)
    return Get4ByteOperand (c);
  else if (c.OperandType == OperandType.ShortInlineBrTarget)
    return GetShortRelativeTarget();
  else if (c.OperandType == OperandType.InlineSwitch)
    return GetSwitchTarget (operandLength);
  else
    return null;
}
There are three kinds of four-byte operands that we treat specially. The first is references to members or types—with these, we extract the member or type name by calling the defining module’s ResolveMember method. The second case is strings—these are stored in the assembly module’s metadata and can be retrieved by calling ResolveString. The final case is branch targets, where the operand refers to a byte offset in the IL. We format these by working out the absolute address after the current instruction (+ four bytes):

string Get4ByteOperand (OpCode c)
{
  int intOp = BitConverter.ToInt32 (_il, _pos);

  switch (c.OperandType)
  {
    case OperandType.InlineTok:
    case OperandType.InlineMethod:
    case OperandType.InlineField:
    case OperandType.InlineType:
      MemberInfo mi;
      try   { mi = _module.ResolveMember (intOp); }
      catch { return null; }
      if (mi == null) return null;

      if (mi.ReflectedType != null)
        return mi.ReflectedType.FullName + "." + mi.Name;
      else if (mi is Type)
        return ((Type)mi).FullName;
      else
        return mi.Name;

    case OperandType.InlineString:
      string s = _module.ResolveString (intOp);
      if (s != null) s = "'" + s + "'";
      return s;

    case OperandType.InlineBrTarget:
      return "IL_" + (_pos + intOp + 4).ToString ("X4");

    default:
      return null;
  }
}
NOTE
The point where we call ResolveMember is a good window for a code analysis tool that reports on method dependencies.

For any other four-byte opcode, we return null (this will cause ReadOperand to format the operand as hex digits).

The final kinds of operand that need special attention are short branch targets and inline switches. A short branch target describes the destination offset as a single signed byte, as at the end of the current instruction (i.e., + one byte). A switch target is followed by a variable number of four-byte branch destinations:

string GetShortRelativeTarget()
{
  int absoluteTarget = _pos + (sbyte) _il [_pos] + 1;
  return "IL_" + absoluteTarget.ToString ("X4");
}

string GetSwitchTarget (int operandLength)
{
  int targetCount = BitConverter.ToInt32 (_il, _pos);
  string [] targets = new string [targetCount];
  for (int i = 0; i < targetCount; i++)
  {
    int ilTarget = BitConverter.ToInt32 (_il, _pos + (i + 1) * 4);
    targets [i] = "IL_" + (_pos + ilTarget + operandLength).ToString ("X4");
  }
  return "(" + string.Join (", ", targets) + ")";
}
This completes the disassembler. We can test it by disassembling one of its own methods:

MethodInfo mi = typeof (Disassembler).GetMethod (
  "ReadOperand", BindingFlags.Instance | BindingFlags.NonPublic);

Console.WriteLine (Disassembler.Disassemble (mi));

Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


18. Reflection and Metadata
19. Dynamic Programming
20. Cryptography
25h 47m remaining
Chapter 19. Dynamic Programming
Chapter 4 explained how dynamic binding works in the C# language. In this chapter, we look briefly at the Dynamic Language Runtime (DLR) and then explore the following dynamic programming patterns:

Dynamic member overload resolution

Custom binding (implementing dynamic objects)

Dynamic language interoperability

NOTE
In Chapter 24, we describe how dynamic can improve COM interoperability.

The types in this chapter reside in the System.Dynamic namespace, except for CallSite<>, which resides in System.Runtime.CompilerServices.

The Dynamic Language Runtime
C# relies on the DLR to perform dynamic binding.

Contrary to its name, the DLR is not a dynamic version of the CLR. Rather, it’s a library that sits atop the CLR—just like any other library such as System.Xml.dll. Its primary role is to provide runtime services to unify dynamic programming—in both statically and dynamically typed languages. Hence, languages such as C#, Visual Basic, IronPython, and IronRuby all use the same protocol for calling functions dynamically. This allows them to share libraries and call code written in other languages.

The DLR also makes it relatively easy to write new dynamic languages in .NET. Instead of having to emit Intermediate Language (IL), dynamic language authors work at the level of expression trees (the same expression trees in System.Linq.Expressions that we talked about in Chapter 8).

The DLR further ensures that all consumers get the benefit of call-site caching, an optimization whereby the DLR prevents unnecessarily repeating the potentially expensive member resolution decisions made during dynamic binding.

WHAT ARE CALL SITES?
When the compiler encounters a dynamic expression, it has no idea who will evaluate that expression at runtime. For instance, consider the following method:

public dynamic Foo (dynamic x, dynamic y)
{
  return x / y;   // Dynamic expression
}
The x and y variables could be any CLR object, a COM object, or even an object hosted in a dynamic language. The compiler cannot, therefore, take its usual static approach of emitting a call to a known method of a known type. Instead, the compiler emits code that eventually results in an expression tree that describes the operation, managed by a call site that the DLR will bind at runtime. The call site essentially acts as an intermediary between caller and callee.

A call site is represented by the CallSite<> class in System.Core.dll. We can see this by disassembling the preceding method—the result is something like this:

static CallSite<Func<CallSite,object,object,object>> divideSite;

[return: Dynamic]
public object Foo ([Dynamic] object x, [Dynamic] object y)
{
  if (divideSite == null)
    divideSite =
      CallSite<Func<CallSite,object,object,object>>.Create (
        Microsoft.CSharp.RuntimeBinder.Binder.BinaryOperation (
          CSharpBinderFlags.None,
          ExpressionType.Divide,
          /* Remaining arguments omitted for brevity */ ));

  return divideSite.Target (divideSite, x, y);
}
As you can see, the call site is cached in a static field to avoid the cost of re-creating it on each call. The DLR further caches the result of the binding phase and the actual method targets. (There can be multiple targets depending on the types of x and y.)

The actual dynamic call then happens by calling the site’s Target (a delegate), passing in the x and y operands.

Notice that the Binder class is specific to C#. Every language with support for dynamic binding provides a language-specific binder to help the DLR interpret expressions in a manner specific to that language, so as not to surprise the programmer. For instance, if we called Foo with integer values of 5 and 2, the C# binder would ensure that we got back 2. In contrast, a VB.NET binder would give us 2.5.

Dynamic Member Overload Resolution
Calling a statically known method with dynamically typed arguments defers member overload resolution from compile time to runtime. This is useful in simplifying certain programming tasks—such as simplifying the Visitor design pattern. It’s also useful in working around limitations imposed by C#’s static typing.

Simplifying the Visitor Pattern
In essence, the Visitor pattern allows you to “add” a method to a class hierarchy without altering existing classes. Although useful, this pattern in its static incarnation is subtle and unintuitive compared to most other design patterns. It also requires that visited classes be made “visitor-friendly” by exposing an Accept method, which can be impossible if the classes are not under your control.

With dynamic binding, you can achieve the same goal more easily—and without needing to modify existing classes. To illustrate, consider the following class hierarchy:

class Person
{
  public string FirstName { get; set; }
  public string LastName  { get; set; }

  // The Friends collection may contain Customers & Employees:
  public readonly IList<Person> Friends = new Collection<Person> ();
}

class Customer : Person { public decimal CreditLimit { get; set; } }
class Employee : Person { public decimal Salary      { get; set; } }
Suppose that we want to write a method that programmatically exports a Person’s details to an XML XElement. The most obvious solution is to write a virtual method called ToXElement() in the Person class that returns an XElement populated with a Person’s properties. We would then override it in Customer and Employee classes such that the XElement was also populated with CreditLimit and Salary. This pattern can be problematic, however, for two reasons:

You might not own the Person, Customer, and Employee classes, making it impossible to add methods to them. (And extension methods wouldn’t give polymorphic behavior.)

The Person, Customer, and Employee classes might already be quite big. A frequent antipattern is the “God Object,” in which a class such as Person attracts so much functionality that it becomes a nightmare to maintain. A good antidote is to avoid adding functions to Person that don’t need to access Person’s private state. A ToXElement method might be an excellent candidate.

With dynamic member overload resolution, we can write the ToXElement functionality in a separate class, without resorting to ugly switches based on type:

class ToXElementPersonVisitor
{
  public XElement DynamicVisit (Person p) => Visit ((dynamic)p);

  XElement Visit (Person p)
  {
    return new XElement ("Person",
      new XAttribute ("Type", p.GetType().Name),
      new XElement ("FirstName", p.FirstName),
      new XElement ("LastName", p.LastName),
      p.Friends.Select (f => DynamicVisit (f))
    );
  }

  XElement Visit (Customer c)   // Specialized logic for customers
  {
    XElement xe = Visit ((Person)c);   // Call "base" method
    xe.Add (new XElement ("CreditLimit", c.CreditLimit));
    return xe;
  }

  XElement Visit (Employee e)   // Specialized logic for employees
  {
    XElement xe = Visit ((Person)e);   // Call "base" method
    xe.Add (new XElement ("Salary", e.Salary));
    return xe;
  }
}
The DynamicVisit method performs a dynamic dispatch—calling the most specific version of Visit as determined at runtime. Notice the line in boldface, in which we call DynamicVisit on each person in the Friends collection. This ensures that if a friend is a Customer or Employee, the correct overload is called.

We can demonstrate this class, as follows:

var cust = new Customer
{
  FirstName = "Joe", LastName = "Bloggs", CreditLimit = 123
};
cust.Friends.Add (
  new Employee { FirstName = "Sue", LastName = "Brown", Salary = 50000 }
);

Console.WriteLine (new ToXElementPersonVisitor().DynamicVisit (cust));
Here’s the result:

<Person Type="Customer">
  <FirstName>Joe</FirstName>
  <LastName>Bloggs</LastName>
  <Person Type="Employee">
    <FirstName>Sue</FirstName>
    <LastName>Brown</LastName>
    <Salary>50000</Salary>
  </Person>
  <CreditLimit>123</CreditLimit>
</Person>
Variations
If you plan more than one visitor class, a useful variation is to define an abstract base class for visitors:

abstract class PersonVisitor<T>
{
  public T DynamicVisit (Person p) { return Visit ((dynamic)p); }

  protected abstract T Visit (Person p);
  protected virtual T Visit (Customer c) { return Visit ((Person) c); }
  protected virtual T Visit (Employee e) { return Visit ((Person) e); }
}
Subclasses then don’t need to define their own DynamicVisit method: all they do is override the versions of Visit whose behavior they want to specialize. This also has the advantages of centralizing the methods that encompass the Person hierarchy and allowing implementers to call base methods more naturally:

class ToXElementPersonVisitor : PersonVisitor<XElement>
{
  protected override XElement Visit (Person p)
  {
    return new XElement ("Person",
      new XAttribute ("Type", p.GetType().Name),
      new XElement ("FirstName", p.FirstName),
      new XElement ("LastName", p.LastName),
      p.Friends.Select (f => DynamicVisit (f))
    );
  }

  protected override XElement Visit (Customer c)
  {
    XElement xe = base.Visit (c);
    xe.Add (new XElement ("CreditLimit", c.CreditLimit));
    return xe;
  }

  protected override XElement Visit (Employee e)
  {
    XElement xe = base.Visit (e);
    xe.Add (new XElement ("Salary", e.Salary));
    return xe;
  }
}
You then can even subclass ToXElementPersonVisitor itself.

Anonymously Calling Members of a Generic Type
The strictness of C#’s static typing is a double-edged sword. On the one hand, it enforces a degree of correctness at compile time. On the other hand, it occasionally makes certain kinds of code difficult or impossible to express, at which point you must resort to reflection. In these situations, dynamic binding is a cleaner and faster alternative to reflection.

An example is when you need to work with an object of type G<T> where T is unknown. We can illustrate this by defining the following class:

public class Foo<T> { public T Value; }
Suppose that we then write a method as follows:

static void Write (object obj)
{
  if (obj is Foo<>)                           // Illegal
    Console.WriteLine ((Foo<>) obj).Value);   // Illegal
}
This method won’t compile: you can’t invoke members of unbound generic types.

Dynamic binding offers two means by which we can work around this. The first is to access the Value member dynamically as follows:

static void Write (dynamic obj)
{
  try { Console.WriteLine (obj.Value); }
  catch (Microsoft.CSharp.RuntimeBinder.RuntimeBinderException) {...}
}
MULTIPLE DISPATCH
C# and the CLR have always supported a limited form of dynamism in the form of virtual method calls. This differs from C#’s dynamic binding in that for virtual method calls, the compiler must commit to a particular virtual member at compile time—based on the name and signature of a member you called. This means that:

The calling expression must be fully understood by the compiler (e.g., it must decide at compile time whether a target member is a field or property).

Overload resolution must be completed entirely by the compiler, based on the compile-time argument types.

A consequence of that last point is that the ability to perform virtual method calls is known as single dispatch. To see why, consider the following method call (in which Walk is a virtual method):

animal.Walk (owner);
The runtime decision of whether to invoke a dog’s Walk method or a cat’s Walk method depends only on the type of the receiver, animal (hence, “single”). If many overloads of Walk accept different kinds of owner, an overload will be selected at compile time without regard to the actual runtime type of the owner object. In other words, only the runtime type of the receiver can vary which method gets called.

In contrast, a dynamic call defers overload resolution until runtime:

animal.Walk ((dynamic) owner);
The final choice of which Walk method to call now depends on the types of both animal and owner—this is called multiple dispatch because the runtime types of arguments, in addition to the receiver type, contribute to the determination of which Walk method to call.

This has the (potential) advantage of working with any object that defines a Value field or property. However, there are a couple of problems. First, catching an exception in this manner is somewhat messy and inefficient (and there’s no way to ask the DLR in advance, “Will this operation succeed?”). Second, this approach wouldn’t work if Foo were an interface (say, IFoo<T>) and either of the following conditions were true:

Value was implemented explicitly

The type that implemented IFoo<T> was inaccessible (more on this soon)

A better solution is to write an overloaded helper method called GetFooValue and to call it using dynamic member overload resolution:

static void Write (dynamic obj)
{
  object result = GetFooValue (obj);
  if (result != null) Console.WriteLine (result);
}

static T GetFooValue<T> (Foo<T> foo) => foo.Value;
static object GetFooValue (object foo) => null;
Notice that we overloaded GetFooValue to accept an object parameter, which acts as a fallback for any type. At runtime, the C# dynamic binder will pick the best overload when calling GetFooValue with a dynamic argument. If the object in question is not based on Foo<T>, it will choose the object-parameter overload instead of throwing an exception.

NOTE
An alternative is to write just the first GetFooValue overload and then catch the RuntimeBinderException. The advantage is that it distinguishes the case of foo.Value being null. The disadvantage is that it incurs the performance overhead of throwing and catching an exception.

In Chapter 18, we solved the same problem with an interface using reflection—with a lot more effort (see “Anonymously Calling Members of a Generic Interface”). The example we used was to design a more powerful version of ToString() that could understand objects such as IEnumerable and IGrouping<,>. Here’s the same example solved more elegantly using dynamic binding:

static string GetGroupKey<TKey,TElement> (IGrouping<TKey,TElement> group)
  => "Group with key=" + group.Key + ": ";

static string GetGroupKey (object source) => null;

public static string ToStringEx (object value)
{
  if (value == null) return "<null>";
  if (value is string s) return s;
  if (value.GetType().IsPrimitive) return value.ToString();

  StringBuilder sb = new StringBuilder();

  string groupKey = GetGroupKey ((dynamic)value);   // Dynamic dispatch
  if (groupKey != null) sb.Append (groupKey);

  if (value is IEnumerable)
    foreach (object element in ((IEnumerable)value))
      sb.Append (ToStringEx (element) + " ");

  if (sb.Length == 0) sb.Append (value.ToString());

  return "\r\n" + sb.ToString();
}
Here it is in action:

Console.WriteLine (ToStringEx ("xyyzzz".GroupBy (c => c) ));

Group with key=x: x
Group with key=y: y y
Group with key=z: z z z
Notice that we used dynamic member overload resolution to solve this problem. If we instead did the following:

dynamic d = value;
try { groupKey = d.Value); }
catch (Microsoft.CSharp.RuntimeBinder.RuntimeBinderException) {...}
it would fail because LINQ’s GroupBy operator returns a type implementing IGrouping<,>, which itself is internal and therefore inaccessible:

internal class Grouping : IGrouping<TKey,TElement>, ...
{
  public TKey Key;
  ...
}
Even though the Key property is declared public, its containing class caps it at internal, making it accessible only via the IGrouping<,> interface. And as is explained in Chapter 4, there’s no way to instruct the DLR to bind to that interface when invoking the Value member dynamically.

Implementing Dynamic Objects
An object can provide its binding semantics by implementing IDynamicMetaObjectProvider—or more easily by subclassing DynamicObject, which provides a default implementation of this interface. This is demonstrated briefly in Chapter 4 via the following example:

dynamic d = new Duck();
d.Quack();                  // Quack method was called
d.Waddle();                 // Waddle method was called

public class Duck : DynamicObject
{
  public override bool TryInvokeMember (
    InvokeMemberBinder binder, object[] args, out object result)
  {
    Console.WriteLine (binder.Name + " method was called");
    result = null;
    return true;
  }
}
DynamicObject
In the preceding example, we overrode TryInvokeMember, which allows the consumer to invoke a method on the dynamic object—such as a Quack or Waddle. DynamicObject exposes other virtual methods that enable consumers to use other programming constructs as well. The following correspond to constructs that have representations in C#:

Method	Programming construct
TryInvokeMember	Method
TryGetMember, TrySetMember	Property or field
TryGetIndex, TrySetIndex	Indexer
TryUnaryOperation	Unary operator such as !
TryBinaryOperation	Binary operator such as ==
TryConvert	Conversion (cast) to another type
TryInvoke	Invocation on the object itself—e.g., d("foo")
These methods should return true if successful. If they return false, the DLR will fall back to the language binder, looking for a matching member on the DynamicOb⁠ject (subclass) itself. If this fails, a RuntimeBinderException is thrown.

We can illustrate TryGetMember and TrySetMember with a class that lets us dynamically access an attribute in an XElement (System.Xml.Linq):

static class XExtensions
{
  public static dynamic DynamicAttributes (this XElement e)
    => new XWrapper (e);
  
  class XWrapper : DynamicObject
  {
    XElement _element;
    public XWrapper (XElement e) { _element = e; }

    public override bool TryGetMember (GetMemberBinder binder,
                                       out object result)
    {
      result = _element.Attribute (binder.Name).Value;
      return true;
    }

    public override bool TrySetMember (SetMemberBinder binder,
                                       object value)
    {
      _element.SetAttributeValue (binder.Name, value);
      return true;
    }
  }
}
Here’s how to use it:

XElement x = XElement.Parse (@"<Label Text=""Hello"" Id=""5""/>");
dynamic da = x.DynamicAttributes();
Console.WriteLine (da.Id);           // 5
da.Text = "Foo";
Console.WriteLine (x.ToString());    // <Label Text="Foo" Id="5" />
The following does a similar thing for System.Data.IDataRecord, making it easier to use data readers:

public class DynamicReader : DynamicObject
{
  readonly IDataRecord _dataRecord;
  public DynamicReader (IDataRecord dr) { _dataRecord = dr; }

  public override bool TryGetMember (GetMemberBinder binder,
                                     out object result)
  {
    result = _dataRecord [binder.Name];
    return true;
  }
}
...
using (IDataReader reader = someDbCommand.ExecuteReader())
{
  dynamic dr = new DynamicReader (reader);
  while (reader.Read())
  {
    int id = dr.ID;
    string firstName = dr.FirstName;
    DateTime dob = dr.DateOfBirth;
    ...
  }
}
The following demonstrates TryBinaryOperation and TryInvoke:

dynamic d = new Duck();
Console.WriteLine (d + d);          // foo
Console.WriteLine (d (78, 'x'));    // 123

public class Duck : DynamicObject
{
  public override bool TryBinaryOperation (BinaryOperationBinder binder,
                                           object arg, out object result)
  {
    Console.WriteLine (binder.Operation);   // Add
    result = "foo";
    return true;
  }

  public override bool TryInvoke (InvokeBinder binder,
                                  object[] args, out object result)
  {
    Console.WriteLine (args[0]);    // 78
    result = 123;
    return true;
  }
}
DynamicObject also exposes some virtual methods for the benefit of dynamic languages. In particular, overriding GetDynamicMemberNames allows you to return a list of all member names that your dynamic object provides.

NOTE
Another reason to implement GetDynamicMemberNames is that Visual Studio’s debugger makes use of this method to display a view of a dynamic object.

ExpandoObject
Another simple application of DynamicObject would be to write a dynamic class that stored and retrieved objects in a dictionary, keyed by string. However, this functionality is already provided via the ExpandoObject class:

dynamic x = new ExpandoObject();
x.FavoriteColor = ConsoleColor.Green;
x.FavoriteNumber = 7;
Console.WriteLine (x.FavoriteColor);    // Green
Console.WriteLine (x.FavoriteNumber);   // 7
ExpandoObject implements IDictionary<string,object>—so we can continue our example and do this:

var dict = (IDictionary<string,object>) x;
Console.WriteLine (dict ["FavoriteColor"]);    // Green
Console.WriteLine (dict ["FavoriteNumber"]);   // 7
Console.WriteLine (dict.Count);                // 2
Interoperating with Dynamic Languages
Although C# supports dynamic binding via the dynamic keyword, it doesn’t go as far as allowing you to execute an expression described in a string at runtime:

string expr = "2 * 3";
// We can’t "execute" expr
This is because the code to translate a string into an expression tree requires a lexical and semantic parser. These features are built into the C# compiler and are not available as a runtime service. At runtime, C# merely provides a binder, which instructs the DLR how to interpret an already-built expression tree.

True dynamic languages such as IronPython and IronRuby do allow you to execute an arbitrary string, and this is useful in tasks such as scripting, writing dynamic configuration systems, and implementing dynamic rules engines. So, although you can write most of your application in C#, it can be useful to call out to a dynamic language for such tasks. In addition, you might want to use an API that is written in a dynamic language where no equivalent functionality is available in a .NET library.

NOTE
The Roslyn scripting NuGet package Microsoft.CodeAnalysis.CSharp.Scripting provides an API that lets you execute a C# string, although it does so by first compiling your code into a program. The compilation overhead makes it slower than Python interop, unless you intend to execute the same expression repeatedly.

In the following example, we use IronPython to evaluate an expression created at runtime from within C#. You could use the following script to write a calculator.

NOTE
To run this code, add the NuGet packages DynamicLanguageRuntime (not to be confused with the System.Dynamic.Runtime package) and IronPython to your application.

using System;
using IronPython.Hosting;
using Microsoft.Scripting;
using Microsoft.Scripting.Hosting;


int result = (int) Calculate ("2 * 3");
Console.WriteLine (result);              // 6

object Calculate (string expression)
{
  ScriptEngine engine = Python.CreateEngine();
  return engine.Execute (expression);
}
Because we’re passing a string into Python, the expression will be evaluated according to Python’s rules and not C#’s. It also means that we can use Python’s language features, such as lists:

var list = (IEnumerable) Calculate ("[1, 2, 3] + [4, 5]");
foreach (int n in list) Console.Write (n);  // 12345
Passing State Between C# and a Script
To pass variables from C# to Python, a few more steps are required. The following example illustrates those steps and could be the basis of a rules engine:

// The following string could come from a file or database:
string auditRule = "taxPaidLastYear / taxPaidThisYear > 2";

ScriptEngine engine = Python.CreateEngine ();    

ScriptScope scope = engine.CreateScope ();       
scope.SetVariable ("taxPaidLastYear", 20000m);
scope.SetVariable ("taxPaidThisYear", 8000m);

ScriptSource source = engine.CreateScriptSourceFromString (
                      auditRule, SourceCodeKind.Expression);

bool auditRequired = (bool) source.Execute (scope);
Console.WriteLine (auditRequired);   // True
You can also get variables back by calling GetVariable:

string code = "result = input * 3";

ScriptEngine engine = Python.CreateEngine();

ScriptScope scope = engine.CreateScope();
scope.SetVariable ("input", 2);

ScriptSource source = engine.CreateScriptSourceFromString (code,
                                  SourceCodeKind.SingleStatement);
source.Execute (scope);
Console.WriteLine (scope.GetVariable ("result"));   // 6
Notice that we specified SourceCodeKind.SingleStatement in the second example (rather than Expression) to inform the engine that we want to execute a statement.

Types are automatically marshaled between the .NET and Python worlds. You can even access members of .NET objects from the scripting side:

string code = @"sb.Append (""World"")";

ScriptEngine engine = Python.CreateEngine ();

ScriptScope scope = engine.CreateScope ();
var sb = new StringBuilder ("Hello");
scope.SetVariable ("sb", sb);

ScriptSource source = engine.CreateScriptSourceFromString (
                      code, SourceCodeKind.SingleStatement);
source.Execute (scope);
Console.WriteLine (sb.ToString());   // HelloWorld

Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


19. Dynamic Programming
20. Cryptography
21. Advanced Threading
25h 47m remaining
Chapter 20. Cryptography
In this chapter, we discuss the major cryptography APIs in .NET:

Windows Data Protection API (DPAPI)

Hashing

Symmetric encryption

Public key encryption and signing

The types covered in this chapter are defined in the following namespaces:

System.Security;
System.Security.Cryptography;
Overview
Table 20-1 summarizes the cryptography options in .NET. In the remaining sections, we explore each of these.

Table 20-1. Encryption and hashing options in .NET
Option	Keys to manage	Speed	Strength	Notes
File.Encrypt	0	Fast	Depends on user’s password	Protects files transparently with filesystem support. A key is derived implicitly from the logged-in user’s credentials. Windows only.
Windows Data Protection	0	Fast	Depends on user’s password	Encrypts and decrypts byte arrays using an implicitly derived key.
Hashing	0	Fast	High	One-way (irreversible) transformation. Used for storing passwords, comparing files, and checking for data corruption.
Symmetric Encryption	1	Fast	High	For general-purpose encryption/decryption. The same key encrypts and decrypts. Can be used to secure messages in transit.
Public Key Encryption	2	Slow	High	Encryption and decryption use different keys. Used for exchanging a symmetric key in message transmission and for digitally signing files.
.NET also provides more specialized support for creating and validating XML-based signatures in System.Security.Cryptography.Xml and types for working with digital certificates in System.Security.Cryptography.X509Certificates.

Windows Data Protection
NOTE
Windows Data Protection is available on Windows only, and throws a PlatformNotSupportedException on other operating systems.

In the section “File and Directory Operations”, we described how you could use File.Encrypt to request that the operating system transparently encrypt a file:

File.WriteAllText ("myfile.txt", "");
File.Encrypt ("myfile.txt");
File.AppendAllText ("myfile.txt", "sensitive data");
The encryption in this case uses a key derived from the logged-in user’s password. You can use this same implicitly derived key to encrypt a byte array with the Windows Data Protection API (DPAPI). The DPAPI is exposed through the ProtectedData class—a simple type with two static methods:

public static byte[] Protect
  (byte[] userData, byte[] optionalEntropy, DataProtectionScope scope);

public static byte[] Unprotect
  (byte[] encryptedData, byte[] optionalEntropy, DataProtectionScope scope);
Whatever you include in optionalEntropy is added to the key, thereby increasing its security. The DataProtectionScope enum argument allows two options: Curren⁠tUser or LocalMachine. With CurrentUser, a key is derived from the logged-in user’s credentials; with LocalMachine, a machine-wide key is used, common to all users. This means that with the CurrentUser scope, data encrypted by one user cannot be decrypted by another. A LocalMachine key provides less protection but works under a Windows Service or a program needing to operate under a variety of accounts.

Here’s a simple encryption and decryption demonstration:

byte[] original = {1, 2, 3, 4, 5};
DataProtectionScope scope = DataProtectionScope.CurrentUser;

byte[] encrypted = ProtectedData.Protect (original, null, scope);
byte[] decrypted = ProtectedData.Unprotect (encrypted, null, scope);
// decrypted is now {1, 2, 3, 4, 5}
Windows Data Protection provides moderate security against an attacker with full access to the computer, depending on the strength of the user’s password. With LocalMachine scope, it’s effective only against those with restricted physical and electronic access.

Hashing
A hashing algorithm distills a potentially large number of bytes into a small fixed-length hashcode. Hashing algorithms are designed such that a single-bit change anywhere in the source data results in a significantly different hashcode. This makes it suitable for comparing files or detecting accidental (or malicious) corruption to a file or data stream.

Hashing also acts as one-way encryption, because it’s difficult to impossible to convert a hashcode back into the original data. This makes it ideal for storing passwords in a database, because should your database become compromised, you don’t want the attacker to gain access to plain-text passwords. To authenticate, you simply hash what the user types in and compare it to the hash that’s stored in the database.

To hash, you call ComputeHash on one of the HashAlgorithm subclasses, such as SHA1 or SHA256:

byte[] hash;
using (Stream fs = File.OpenRead ("checkme.doc"))
  hash = SHA1.Create().ComputeHash (fs);   // SHA1 hash is 20 bytes long
The ComputeHash method also accepts a byte array, which is convenient for hashing passwords (we describe a more secure technique in “Hashing Passwords”):

byte[] data = System.Text.Encoding.UTF8.GetBytes ("stRhong%pword");
byte[] hash = SHA256.Create().ComputeHash (data);
NOTE
The GetBytes method on an Encoding object converts a string to a byte array; the GetString method converts it back. An Encoding object cannot, however, convert an encrypted or hashed byte array to a string, because scrambled data usually violates text encoding rules. Instead, use Convert.ToBase64String and Convert.FromBase64String: these convert between any byte array and a legal (and XML- or JSON-friendly) string.

Hash Algorithms in .NET
SHA1 and SHA256 are two of the HashAlgorithm subtypes provided by .NET. Here are the major algorithms, in ascending order of security:

Class	Algorithm	Hash length in bytes	Strength
MD5	MD5	16	Very poor
SHA1	SHA-1	20	Poor
SHA256	SHA-2	32	Good
SHA384	SHA-2	48	Good
SHA512	SHA-2	64	Good
All five algorithms execute at roughly similar speeds in their current implementations, with the exception of SHA256, which is 2-3 times faster (this may vary with hardware and operating system). To give a ballpark figure, you can expect at least 500 MB per second on a 2024-era desktop or server with all algorithms. The longer hashes decrease the possibility of collision (two distinct files yielding the same hash).

WARNING
Use at least SHA256 when hashing passwords or other security-sensitive data. MD5 and SHA1 are considered insecure for this purpose and are suitable to protect only against accidental corruption, not deliberate tampering.

NOTE
.NET 8 and above also support the latest SHA-3 hashing note via the SHA3_256, SHA3_384, and SHA3_512 classes. The SHA-3 algorithms are considered even more secure (and slower) than the previously listed algorithms, but require Windows Build 25324+ or Linux with OpenSSL 1.1.1+. You can test whether OS support is available via the static IsSupported property on these classes.

Hashing Passwords
The longer SHA algorithms are suitable as a basis for password hashing, if you enforce a strong password policy to mitigate a dictionary attack—a strategy whereby an attacker builds a password lookup table by hashing every word in a dictionary.

A standard technique, when hashing passwords, is to incorporate “salt”—a long series of bytes that you initially obtain via a random number generator and then combine with each password before hashing. This frustrates hackers in two ways:

They must also know the salt bytes.

They cannot use rainbow tables (publicly available precomputed databases of passwords and their hashcodes), although a dictionary attack might still be possible with sufficient computing power.

You can further strengthen security by “stretching” your password hashes—repeatedly rehashing to obtain more computationally intensive byte sequences. If you rehash 100 times, a dictionary attack that might otherwise take one month would take eight years. The KeyDerivation, Rfc2898DeriveBytes, and PasswordDeriveBytes classes perform exactly this kind of stretching while also allowing for convenient salting. Of these, KeyDerivation.Pbkdf2 offers the best hashing:

byte[] encrypted = KeyDerivation.Pbkdf2 (
    password: "stRhong%pword",
    salt: Encoding.UTF8.GetBytes ("j78Y#p)/saREN!y3@"),
    prf: KeyDerivationPrf.HMACSHA512,
    iterationCount: 100,
    numBytesRequested: 64);
NOTE
KeyDerivation.Pbkdf2 requires the NuGet package Microsoft.AspNetCore.Cryptography.KeyDerivation. Though it’s in the ASP.NET Core namespace, any .NET application can use it.

Symmetric Encryption
Symmetric encryption uses the same key for encryption as for decryption. The .NET BCL provides four symmetric algorithms, of which Rijndael (pronounced “Rhine Dahl” or “Rain Doll”) is the premium; the other algorithms are intended mainly for compatibility with older applications. Rijndael is both fast and secure and has two implementations:

The Rijndael class

The Aes class

The two are almost identical, except that Aes does not let you weaken the cipher by changing the block size. Aes is recommended by the CLR’s security team.

Rijndael and Aes allow symmetric keys of length 16, 24, or 32 bytes: all are currently considered secure. Here’s how to encrypt a series of bytes as they’re written to a file, using a 16-byte key:

byte[] key = {145,12,32,245,98,132,98,214,6,77,131,44,221,3,9,50};
byte[] iv  = {15,122,132,5,93,198,44,31,9,39,241,49,250,188,80,7};

byte[] data = { 1, 2, 3, 4, 5 };   // This is what we're encrypting.

using (SymmetricAlgorithm algorithm = Aes.Create())
using (ICryptoTransform encryptor = algorithm.CreateEncryptor (key, iv))
using (Stream f = File.Create ("encrypted.bin"))
using (Stream c = new CryptoStream (f, encryptor, CryptoStreamMode.Write))
  c.Write (data, 0, data.Length);
The following code decrypts the file:

byte[] key = {145,12,32,245,98,132,98,214,6,77,131,44,221,3,9,50};
byte[] iv  = {15,122,132,5,93,198,44,31,9,39,241,49,250,188,80,7};

byte[] decrypted = new byte[5];

using (SymmetricAlgorithm algorithm = Aes.Create())
using (ICryptoTransform decryptor = algorithm.CreateDecryptor (key, iv))
using (Stream f = File.OpenRead ("encrypted.bin"))
using (Stream c = new CryptoStream (f, decryptor, CryptoStreamMode.Read))
  for (int b; (b = c.ReadByte()) > -1;)
    Console.Write (b + " ");                            // 1 2 3 4 5
In this example, we made up a key of 16 randomly chosen bytes. If the wrong key was used in decryption, CryptoStream would throw a CryptographicException. Catching this exception is the only way to test whether a key is correct.

As well as a key, we made up an IV, or Initialization Vector. This 16-byte sequence forms part of the cipher—much like the key—but is not considered secret. If you’re transmitting an encrypted message, you would send the IV in plain text (perhaps in a message header) and then change it with every message. This would render each encrypted message unrecognizable from any previous one—even if their unencrypted versions were similar or identical.

NOTE
If you don’t need—or want—the protection of an IV, you can defeat it by using the same 16-byte value for both the key and the IV. Sending multiple messages with the same IV, though, weakens the cipher and might even make it possible to crack.

The cryptography work is divided among the classes. Aes is the mathematician; it applies the cipher algorithm, along with its encryptor and decryptor transforms. CryptoStream is the plumber; it takes care of stream plumbing. You can replace Aes with a different symmetric algorithm yet still use CryptoStream.

CryptoStream is bidirectional, meaning you can read or write to the stream depending on whether you choose CryptoStreamMode.Read or CryptoStreamMode.Write. Both encryptors and decryptors are read and write savvy, yielding four combinations—the choice can have you staring at a blank screen for a while! It can be helpful to model reading as “pulling” and writing as “pushing.” If in doubt, start with Write for encryption and Read for decryption; this is often the most natural.

To generate a random key or IV, use RandomNumberGenerator in System.Cryptography. The numbers it produces are genuinely unpredictable, or cryptographically strong (the System.Random class does not offer the same guarantee). Here’s an example:

byte[] key = new byte [16];
byte[] iv  = new byte [16];
RandomNumberGenerator rand = RandomNumberGenerator.Create();
rand.GetBytes (key);
rand.GetBytes (iv);
Or, from .NET 6:

byte[] key = RandomNumberGenerator.GetBytes (16);
byte[] iv = RandomNumberGenerator.GetBytes (16);
If you don’t specify a key and IV, cryptographically strong random values are generated automatically. You can query these through the Aes object’s Key and IV properties.

Encrypting in Memory
From .NET 6, you can utilize the EncryptCbc and DecryptCbc methods to shortcut the process of encrypting and decrypting byte arrays:

public static byte[] Encrypt (byte[] data, byte[] key, byte[] iv)
{
  using Aes algorithm = Aes.Create();
  algorithm.Key = key;
  return algorithm.EncryptCbc (data, iv);
}

public static byte[] Decrypt (byte[] data, byte[] key, byte[] iv)
{
  using Aes algorithm = Aes.Create();
  algorithm.Key = key;
  return algorithm.DecryptCbc (data, iv);
}
Here’s an equivalent that works in all.NET versions:

public static byte[] Encrypt (byte[] data, byte[] key, byte[] iv)
{
  using (Aes algorithm = Aes.Create())
  using (ICryptoTransform encryptor = algorithm.CreateEncryptor (key, iv))
    return Crypt (data, encryptor);
}

public static byte[] Decrypt (byte[] data, byte[] key, byte[] iv)
{
  using (Aes algorithm = Aes.Create())
  using (ICryptoTransform decryptor = algorithm.CreateDecryptor (key, iv))
    return Crypt (data, decryptor);
}

static byte[] Crypt (byte[] data, ICryptoTransform cryptor)
{
  MemoryStream m = new MemoryStream();
  using (Stream c = new CryptoStream (m, cryptor, CryptoStreamMode.Write))
    c.Write (data, 0, data.Length);
  return m.ToArray();
}
Here, CryptoStreamMode.Write works best for both encryption and decryption, since in both cases we’re “pushing” into a fresh memory stream.

Here are overloads that accept and return strings:

public static string Encrypt (string data, byte[] key, byte[] iv)
{
  return Convert.ToBase64String (
    Encrypt (Encoding.UTF8.GetBytes (data), key, iv));
}

public static string Decrypt (string data, byte[] key, byte[] iv)
{
  return Encoding.UTF8.GetString (
    Decrypt (Convert.FromBase64String (data), key, iv));
}
The following demonstrates their use:

byte[] key = new byte[16];
byte[] iv = new byte[16];

var cryptoRng = RandomNumberGenerator.Create();
cryptoRng.GetBytes (key);
cryptoRng.GetBytes (iv);

string encrypted = Encrypt ("Yeah!", key, iv);
Console.WriteLine (encrypted);                 // R1/5gYvcxyR2vzPjnT7yaQ==

string decrypted = Decrypt (encrypted, key, iv);
Console.WriteLine (decrypted);                 // Yeah!
Chaining Encryption Streams
CryptoStream is a decorator, meaning that you can chain it with other streams. In the following example, we write compressed encrypted text to a file and then read it back:

byte[] key = new byte [16];
byte[] iv = new byte [16];

var cryptoRng = RandomNumberGenerator.Create();
cryptoRng.GetBytes (key);
cryptoRng.GetBytes (iv);

using (Aes algorithm = Aes.Create())
{
  using (ICryptoTransform encryptor = algorithm.CreateEncryptor(key, iv))
  using (Stream f = File.Create ("serious.bin"))
  using (Stream c = new CryptoStream (f, encryptor, CryptoStreamMode.Write))
  using (Stream d = new DeflateStream (c, CompressionMode.Compress))
  using (StreamWriter w = new StreamWriter (d))
    await w.WriteLineAsync ("Small and secure!");

  using (ICryptoTransform decryptor = algorithm.CreateDecryptor(key, iv))
  using (Stream f = File.OpenRead ("serious.bin"))
  using (Stream c = new CryptoStream (f, decryptor, CryptoStreamMode.Read))
  using (Stream d = new DeflateStream (c, CompressionMode.Decompress))
  using (StreamReader r = new StreamReader (d))
    Console.WriteLine (await r.ReadLineAsync());     // Small and secure!
}
(As a final touch, we make our program asynchronous by calling WriteLineAsync and ReadLineAsync and awaiting the result.)

In this example, all one-letter variables form part of a chain. The mathematicians—algorithm, encryptor, and decryptor—are there to assist CryptoStream in the cipher work, as illustrated in Figure 20-1.

Chaining streams in this manner demands little memory, regardless of the ultimate stream sizes.


Figure 20-1. Chaining encryption and compression streams
Disposing Encryption Objects
Disposing a CryptoStream ensures that its internal cache of data is flushed to the underlying stream. Internal caching is necessary for encryption algorithms because they process data in blocks, rather than one byte at a time.

CryptoStream is unusual in that its Flush method does nothing. To flush a stream (without disposing it) you must call FlushFinalBlock. In contrast to Flush, you can call FlushFinalBlock only once, and then no further data can be written.

We also disposed the mathematicians—the Aes algorithm and ICryptoTransform objects (encryptor and decryptor). When the Rijndael transforms are disposed, they wipe the symmetric key and related data from memory, preventing subsequent discovery by other software running on the computer (we’re talking malware). You can’t rely on the garbage collector for this job, because it merely flags sections of memory as available; it doesn’t write zeros over every byte.

The easiest way to dispose an Aes object outside of a using statement is to call Clear. Its Dispose method is hidden via explicit implementation (to signal its unusual disposal semantics, whereby it clears memory rather than releasing unmanaged resources).

NOTE
You can further reduce your application’s vulnerability to leaking secrets via released memory by doing the following:

Avoiding strings for security information (being immutable, a string’s value can never be cleared once created)

Overwriting buffers as soon as they’re no longer needed (for instance, by calling Array.Clear on a byte array)

Key Management
Key management is a critical element of security: if your keys are exposed, so is your data. You need to consider who should have access to keys and how to back them up in case of hardware failure while storing them in a manner that prevents unauthorized access.

It is inadvisable to hardcode encryption keys because popular tools exist to decompile assemblies with little expertise required. A better option (on Windows) is to manufacture a random key for each installation, storing it securely with Windows Data Protection.

For applications deployed to the cloud, Microsoft Azure and Amazon Web Services (AWS) offer key-management systems with additional features that can be useful in an enterprise environment, such as audit trails. If you’re encrypting a message stream, public-key encryption still provides the best option.

Public-Key Encryption and Signing
Public-key cryptography is asymmetric, meaning that encryption and decryption use different keys.

Unlike symmetric encryption, for which any arbitrary series of bytes of appropriate length can serve as a key, asymmetric cryptography requires specially crafted key pairs. A key pair contains a public key and private key component that work together as follows:

The public key encrypts messages.

The private key decrypts messages.

The party “crafting” a key pair keeps the private key secret while distributing the public key freely. A special feature of this type of cryptography is that you cannot calculate a private key from a public key. So, if the private key is lost, encrypted data cannot be recovered; conversely, if a private key is leaked, the encryption system becomes useless.

A public key handshake allows two computers to communicate securely over a public network, with no prior contact and no existing shared secret. To see how this works, suppose that computer Origin wants to send a confidential message to computer Target:

Target generates a public/private key pair and then sends its public key to Origin.

Origin encrypts the confidential message using Target’s public key and then sends it to Target.

Target decrypts the confidential message using its private key.

An eavesdropper will see the following:

Target’s public key

The secret message, encrypted with Target’s public key

But without Target’s private key, the message cannot be decrypted.

NOTE
This doesn’t prevent against a man-in-the-middle attack: in other words, Origin cannot know that Target isn’t some malicious party. To authenticate the recipient, the originator needs to already know the recipient’s public key or be able to validate its key through a digital site certificate.

Because public key encryption is relatively slow and its message size limited, the secret message sent from Origin to Target typically contains a fresh key for subsequent symmetric encryption. This allows public key encryption to be abandoned for the remainder of the session, in favor of a symmetric algorithm capable of handling larger messages. This protocol is particularly secure if a fresh public/private key pair is generated for each session because no keys then need to be stored on either computer.

NOTE
The public key encryption algorithms rely on the message being smaller than the key. This makes them suitable for encrypting only small amounts of data, such as a key for subsequent symmetric encryption. If you try to encrypt a message much larger than half the key size, the provider will throw an exception.

The RSA Class
.NET provides a number of asymmetric algorithms, of which RSA is the most popular. Here’s how to encrypt and decrypt with RSA:

byte[] data = { 1, 2, 3, 4, 5 };   // This is what we're encrypting.

using (var rsa = new RSACryptoServiceProvider())
{
  byte[] encrypted = rsa.Encrypt (data, true);
  byte[] decrypted = rsa.Decrypt (encrypted, true);
}
Because we didn’t specify a public or private key, the cryptographic provider automatically generated a key pair, using the default length of 1,024 bits; you can request longer keys in increments of eight bytes, through the constructor. For security-critical applications, it’s prudent to request 2,048 bits:

var rsa = new RSACryptoServiceProvider (2048);
Generating a key pair is computationally intensive—taking perhaps 10 ms. For this reason, the RSA implementation delays this until a key is actually needed, such as when calling Encrypt. This gives you the chance to load in an existing key—or key pair, should it exist.

The methods ImportCspBlob and ExportCspBlob load and save keys in byte array format. FromXmlString and ToXmlString do the same job in a string format, the string containing an XML fragment. A bool flag lets you indicate whether to include the private key when saving. Here’s how to manufacture a key pair and save it to disk:

using (var rsa = new RSACryptoServiceProvider())
{
  File.WriteAllText ("PublicKeyOnly.xml", rsa.ToXmlString (false));
  File.WriteAllText ("PublicPrivate.xml", rsa.ToXmlString (true));
}
Because we didn’t provide existing keys, ToXmlString forced the manufacture of a fresh key pair (on the first call). In the next example, we read back these keys and use them to encrypt and decrypt a message:

byte[] data = Encoding.UTF8.GetBytes ("Message to encrypt");

string publicKeyOnly = File.ReadAllText ("PublicKeyOnly.xml");
string publicPrivate = File.ReadAllText ("PublicPrivate.xml");

byte[] encrypted, decrypted;

using (var rsaPublicOnly = new RSACryptoServiceProvider())
{
  rsaPublicOnly.FromXmlString (publicKeyOnly);
  encrypted = rsaPublicOnly.Encrypt (data, true);


  // The next line would throw an exception because you need the private
  // key in order to decrypt:
  // decrypted = rsaPublicOnly.Decrypt (encrypted, true);
}

using (var rsaPublicPrivate = new RSACryptoServiceProvider())
{
  // With the private key we can successfully decrypt:
  rsaPublicPrivate.FromXmlString (publicPrivate);
  decrypted = rsaPublicPrivate.Decrypt (encrypted, true);
}
Digital Signing
You also can use public key algorithms to digitally sign messages or documents. A signature is like a hash, except that its production requires a private key and so cannot be forged. The public key is used to verify the signature. Here’s an example:

byte[] data = Encoding.UTF8.GetBytes ("Message to sign");
byte[] publicKey;
byte[] signature;
object hasher = SHA1.Create();         // Our chosen hashing algorithm.

// Generate a new key pair, then sign the data with it:
using (var publicPrivate = new RSACryptoServiceProvider())
{
  signature = publicPrivate.SignData (data, hasher);
  publicKey = publicPrivate.ExportCspBlob (false);    // get public key
}

// Create a fresh RSA using just the public key, then test the signature.
using (var publicOnly = new RSACryptoServiceProvider())
{
  publicOnly.ImportCspBlob (publicKey);
  Console.Write (publicOnly.VerifyData (data, hasher, signature)); // True

  // Let's now tamper with the data and recheck the signature:
  data[0] = 0;
  Console.Write (publicOnly.VerifyData (data, hasher, signature)); // False

  // The following throws an exception as we're lacking a private key:
  signature = publicOnly.SignData (data, hasher);
}
Signing works by first hashing the data and then applying the asymmetric algorithm to the resultant hash. Because hashes are of a small fixed size, large documents can be signed relatively quickly (public key encryption is much more CPU-intensive than hashing). If you want, you can do the hashing yourself and then call SignHash instead of SignData:

using (var rsa = new RSACryptoServiceProvider())
{
  byte[] hash = SHA1.Create().ComputeHash (data);
  signature = rsa.SignHash (hash, CryptoConfig.MapNameToOID ("SHA1"));
  ...
}
SignHash still needs to know what hash algorithm you used; CryptoConfig.MapNa⁠meToOID provides this information in the correct format from a friendly name such as “SHA1”.

RSACryptoServiceProvider produces signatures whose size matches that of the key. Currently, no mainstream algorithm produces secure signatures significantly smaller than 128 bytes (suitable for product activation codes, for instance).

NOTE
For signing to be effective, the recipient must know, and trust, the sender’s public key. This can happen via prior communication, preconfiguration, or a site certificate. A site certificate is an electronic record of the originator’s public key and name—itself signed by an independent trusted authority. The namespace System.Security.Cryptography.X509Certificates defines the types for working with certificates.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


20. Cryptography
21. Advanced Threading
22. Parallel Programming
25h 47m remaining
Chapter 21. Advanced Threading
We started Chapter 14 with the basics of threading as a precursor to tasks and asynchrony. Specifically, we showed how to start and configure a thread, and covered essential concepts such as thread pooling, blocking, spinning, and synchronization contexts. We also introduced locking and thread safety, and demonstrated the simplest signaling construct, ManualResetEvent.

This chapter picks up where Chapter 14 left off on the topic of threading. In the first three sections, we flesh out synchronization, locking, and thread safety in greater detail. We then cover:

Nonexclusive locking (Semaphore and reader/writer locks)

All signaling constructs (AutoResetEvent, ManualResetEvent, Countdow⁠nEvent, and Barrier)

Lazy initialization (Lazy<T> and LazyInitializer)

Thread-local storage (ThreadStaticAttribute, ThreadLocal<T>, and GetData/SetData)

Timers

Threading is such a vast topic that we’ve put additional material online to complete the picture. Visit http://albahari.com/threading for a discussion on the following, more arcane, topics:

Monitor.Wait and Monitor.Pulse for specialized signaling scenarios

Nonblocking synchronization techniques for micro-optimization (Interlocked, memory barriers, volatile)

SpinLock and SpinWait for high-concurrency scenarios

Synchronization Overview
Synchronization is the act of coordinating concurrent actions for a predictable outcome. Synchronization is particularly important when multiple threads access the same data; it’s surprisingly easy to run aground in this area.

The simplest and most useful synchronization tools are arguably the continuations and task combinators described in Chapter 14. By formulating concurrent programs into asynchronous operations strung together with continuations and combinators, you lessen the need for locking and signaling. However, there are still times when the lower-level constructs come into play.

The synchronization constructs can be divided into three categories:

Exclusive locking
Exclusive locking constructs allow just one thread to perform some activity or execute a section of code at a time. Their primary purpose is to let threads access shared writing state without interfering with one another. The exclusive locking constructs are lock, Mutex, and SpinLock.
Nonexclusive locking
Nonexclusive locking lets you limit concurrency. The nonexclusive locking constructs are Semaphore(Slim) and ReaderWriterLock(Slim).
Signaling
These allow a thread to block until receiving one or more notifications from other thread(s). The signaling constructs include ManualResetEvent(Slim), AutoResetEvent, CountdownEvent, and Barrier. The former three are referred to as event wait handles.
It’s also possible (and tricky) to perform certain concurrent operations on shared state without locking through the use of nonblocking synchronization constructs. These are Thread.MemoryBarrier, Thread.VolatileRead, Thread.VolatileWrite, the volatile keyword, and the Interlocked class. We cover this topic online, along with Monitor’s Wait/Pulse methods, which you can use to write custom signaling logic.

Exclusive Locking
There are three exclusive locking constructs: the lock statement, Mutex, and SpinLock. The lock construct is the most convenient and widely used, whereas the other two target niche scenarios:

Mutex lets you span multiple processes (computer-wide locks).

SpinLock implements a micro-optimization that can lessen context switches in high-concurrency scenarios (see http://albahari.com/threading).

The lock Statement
To illustrate the need for locking, consider the following class:

class ThreadUnsafe
{
  static int _val1 = 1, _val2 = 1;

  static void Go()
  {
    if (_val2 != 0) Console.WriteLine (_val1 / _val2);
    _val2 = 0;
  }
}
This class is not thread-safe: if Go were called by two threads simultaneously, it would be possible to get a division-by-zero error because _val2 could be set to zero in one thread right as the other thread was in between executing the if statement and Console.WriteLine. Here’s how lock fixes the problem:

class ThreadSafe
{
  static readonly object _locker = new object();
  static int _val1 = 1, _val2 = 1;

  static void Go()
  {
    lock (_locker)
    {
      if (_val2 != 0) Console.WriteLine (_val1 / _val2);
      _val2 = 0;
    }
  }
}
Only one thread can lock the synchronizing object (in this case, _locker) at a time, and any contending threads are blocked until the lock is released. If more than one thread contends the lock, they are queued on a “ready queue” and granted the lock on a first-come, first-served basis.1 Exclusive locks are sometimes said to enforce serialized access to whatever’s protected by the lock because one thread’s access cannot overlap with that of another. In this case, we’re protecting the logic inside the Go method as well as the fields _val1 and _val2.

Monitor.Enter and Monitor.Exit
C#’s lock statement is in fact a syntactic shortcut for a call to the methods Monitor.Enter and Monitor.Exit, with a try/finally block. Here’s (a simplified version of) what’s actually happening within the Go method of the preceding example:

Monitor.Enter (_locker);
try
{
  if (_val2 != 0) Console.WriteLine (_val1 / _val2);
  _val2 = 0;
}
finally { Monitor.Exit (_locker); }
Calling Monitor.Exit without first calling Monitor.Enter on the same object throws an exception.

The lockTaken overloads
The code that we just demonstrated has a subtle vulnerability. Consider the (unlikely) event of an exception being thrown between the call to Monitor.Enter and the try block (due, perhaps, to an OutOfMemoryException or, in .NET Framework, if the thread is aborted). In such a scenario, the lock might or might not be taken. If the lock is taken, it won’t be released—because we’ll never enter the try/finally block. This will result in a leaked lock. To avoid this danger, Monitor.Enter defines the following overload:

public static void Enter (object obj, ref bool lockTaken);
lockTaken is false after this method if (and only if) the Enter method throws an exception and the lock was not taken.

Here’s the more robust pattern of use (which is exactly how C# translates a lock statement):

bool lockTaken = false;
try
{
  Monitor.Enter (_locker, ref lockTaken);
  // Do your stuff...
}
finally { if (lockTaken) Monitor.Exit (_locker); }
TryEnter
Monitor also provides a TryEnter method that allows a timeout to be specified, either in milliseconds or as a TimeSpan. The method then returns true if a lock was obtained, or false if no lock was obtained because the method timed out. TryEnter can also be called with no argument, which “tests” the lock, timing out immediately if the lock can’t be obtained immediately. As with the Enter method, TryEnter is overloaded to accept a lockTaken argument.

Choosing the Synchronization Object
You can use any object visible to each of the partaking threads as a synchronizing object, subject to one hard rule: it must be a reference type. The synchronizing object is typically private (because this helps to encapsulate the locking logic) and is typically an instance or static field. The synchronizing object can double as the object it’s protecting, as the _list field does in the following example:

class ThreadSafe
{
  List <string> _list = new List <string>();

  void Test()
  {
    lock (_list)
    {
      _list.Add ("Item 1");
      ...
A field dedicated for the purpose of locking (such as _locker, in the example prior) allows precise control over the scope and granularity of the lock. You can also use the containing object (this) as a synchronization object:

lock (this) { ... }
Or even its type:

lock (typeof (Widget)) { ... }    // For protecting access to statics
The disadvantage of locking in this way is that you’re not encapsulating the locking logic, so it becomes more difficult to prevent deadlocking and excessive blocking.

You can also lock on local variables captured by lambda expressions or anonymous methods.

NOTE
Locking doesn’t restrict access to the synchronizing object itself in any way. In other words, x.ToString() will not block because another thread has called lock(x); both threads must call lock(x) in order for blocking to occur.

When to Lock
As a basic rule, you need to lock around accessing any writable shared field. Even in the simplest case—an assignment operation on a single field—you must consider synchronization. In the following class, neither the Increment nor the Assign method is thread-safe:

class ThreadUnsafe
{
  static int _x;
  static void Increment() { _x++; }
  static void Assign()    { _x = 123; }
}
Here are thread-safe versions of Increment and Assign:

static readonly object _locker = new object();
static int _x;

static void Increment() { lock (_locker) _x++; }
static void Assign()    { lock (_locker) _x = 123; }
Without locks, two problems can arise:

Operations such as incrementing a variable (or even reading/writing a variable, under certain conditions) are not atomic.

The compiler, CLR, and processor are entitled to reorder instructions and cache variables in CPU registers to improve performance—as long as such optimizations don’t change the behavior of a single-threaded program (or a multithreaded program that uses locks).

Locking mitigates the second problem because it creates a memory barrier before and after the lock. A memory barrier is a “fence” through which the effects of reordering and caching cannot penetrate.

NOTE
This applies not just to locks but to all synchronization constructs. So, if your use of a signaling construct, for instance, ensures that just one thread reads/writes a variable at a time, you don’t need to lock. Hence, the following code is thread-safe without locking around x:

var signal = new ManualResetEvent (false);
int x = 0;
new Thread (() => { x++; signal.Set(); }).Start();
signal.WaitOne();
Console.WriteLine (x);    // 1 (always)
In “Nonblocking Synchronization”, we explain how this need arises and how the memory barriers and the Interlocked class can provide alternatives to locking in these situations.

Locking and Atomicity
If a group of variables are always read and written within the same lock, you can say that the variables are read and written atomically. Let’s suppose that fields x and y are always read and assigned within a lock on object locker:

lock (locker) { if (x != 0) y /= x; }
We can say that x and y are accessed atomically because the code block cannot be divided or preempted by the actions of another thread in such a way that it will change x or y and invalidate its outcome. You’ll never get a division-by-zero error, provided that x and y are always accessed within this same exclusive lock.

NOTE
The atomicity provided by a lock is violated if an exception is thrown within a lock block (whether or not multithreading is involved). For example, consider the following:

decimal _savingsBalance, _checkBalance;

void Transfer (decimal amount)
{
  lock (_locker)
  {
    _savingsBalance += amount;
    _checkBalance -= amount + GetBankFee();
  }
}
If an exception were thrown by GetBankFee(), the bank would lose money. In this case, we could avoid the problem by calling GetBankFee earlier. A solution for more complex cases is to implement “rollback” logic within a catch or finally block.

Instruction atomicity is a different, albeit analogous, concept: an instruction is atomic if it executes indivisibly on the underlying processor.

Nested Locking
A thread can repeatedly lock the same object in a nested (reentrant) fashion:

lock (locker)
  lock (locker)
    lock (locker)
    {
       // Do something...
    }
Alternatively:

Monitor.Enter (locker); Monitor.Enter (locker);  Monitor.Enter (locker); 
// Do something...
Monitor.Exit (locker);  Monitor.Exit (locker);   Monitor.Exit (locker);
In these scenarios, the object is unlocked only when the outermost lock statement has exited—or a matching number of Monitor.Exit statements have executed.

Nested locking is useful when one method calls another from within a lock:

object locker = new object();

lock (locker)
{
  AnotherMethod();
  // We still have the lock - because locks are reentrant.
}

void AnotherMethod()
{
  lock (locker) { Console.WriteLine ("Another method"); }
}
A thread can block on only the first (outermost) lock.

Deadlocks
A deadlock happens when two threads each wait for a resource held by the other, so neither can proceed. The easiest way to illustrate this is with two locks:

object locker1 = new object();
object locker2 = new object();

new Thread (() => {
                    lock (locker1)
                    {
                      Thread.Sleep (1000);
                      lock (locker2);      // Deadlock
                    }
                  }).Start();
lock (locker2)
{
  Thread.Sleep (1000);
  lock (locker1);                          // Deadlock
}
You can create more elaborate deadlocking chains with three or more threads.

NOTE
The CLR, in a standard hosting environment, is not like SQL Server and does not automatically detect and resolve deadlocks by terminating one of the offenders. A threading deadlock causes participating threads to block indefinitely, unless you’ve specified a locking timeout. (Under the SQL CLR integration host, however, deadlocks are automatically detected, and a [catchable] exception is thrown on one of the threads.)

Deadlocking is one of the most difficult problems in multithreading—especially when there are many interrelated objects. Fundamentally, the hard problem is that you can’t be sure what locks your caller has taken out.

So, you might lock private field a within your class x, unaware that your caller (or caller’s caller) has already locked field b within class y. Meanwhile, another thread is doing the reverse—creating a deadlock. Ironically, the problem is exacerbated by (good) object-oriented design patterns, because such patterns create call chains that are not determined until runtime.

The popular advice “lock objects in a consistent order to prevent deadlocks,” although helpful in our initial example, is difficult to apply to the scenario just described. A better strategy is to be wary of locking around calls to methods in objects that might have references back to your own object. Also, consider whether you really need to lock around calls to methods in other classes (often you do—as you’ll see in “Locking and Thread Safety”—but sometimes there are other options). Relying more on higher-level synchronization options such as task continuations/combinators, data parallelism and immutable types (later in this chapter) can lessen the need for locking.

NOTE
Here is an alternative way to perceive the problem: when you call out to other code while holding a lock, the encapsulation of that lock subtly leaks. This is not a fault in the CLR; it’s a fundamental limitation of locking in general. The problems of locking are being addressed in various research projects, including Software Transactional Memory.

Another deadlocking scenario arises when calling Dispatcher.Invoke (in a WPF application) or Control.Invoke (in a Windows Forms application) while in possession of a lock. If the user interface happens to be running another method that’s waiting on the same lock, a deadlock will happen right there. You often can fix this simply by calling BeginInvoke instead of Invoke (or relying on asynchronous functions that do this implicitly when a synchronization context is present). Alternatively, you can release your lock before calling Invoke, although this won’t work if your caller took out the lock.

Performance
Locking is fast: you can expect to acquire and release a lock in less than 20 nanoseconds on a 2020-era computer if the lock is uncontended. If it is contended, the consequential context switch moves the overhead closer to the microsecond region, although it can be longer before the thread is actually rescheduled.

Mutex
A Mutex is like a C# lock, but it can work across multiple processes. In other words, Mutex can be computer-wide as well as application-wide. Acquiring and releasing an uncontended Mutex takes around half a microsecond—more than 20 times slower than a lock.

With a Mutex class, you call the WaitOne method to lock and ReleaseMutex to unlock. Just as with the lock statement, a Mutex can be released only from the same thread that obtained it.

NOTE
If you forget to call ReleaseMutex and simply call Close or Dispose, an AbandonedMutexException will be thrown upon anyone else waiting upon that mutex.

A common use for a cross-process Mutex is to ensure that only one instance of a program can run at a time. Here’s how it’s done:

// Naming a Mutex makes it available computer-wide. Use a name that's
// unique to your company and application (e.g., include your URL).

using var mutex = new Mutex (true, @"Global\oreilly.com OneAtATimeDemo");
// Wait a few seconds if contended, in case another instance
// of the program is still in the process of shutting down.

if (!mutex.WaitOne (TimeSpan.FromSeconds (3), false))
{
  Console.WriteLine ("Another instance of the app is running. Bye!");
  return;
}
try { RunProgram(); }
finally { mutex.ReleaseMutex (); }

void RunProgram()
{
  Console.WriteLine ("Running. Press Enter to exit");
  Console.ReadLine();
}
NOTE
If you’re running under Terminal Services or in separate Unix consoles, a computer-wide Mutex is ordinarily visible only to applications in the same session. To make it visible to all terminal server sessions, prefix its name with Global\, as shown in the example.

Locking and Thread Safety
A program or method is thread-safe if it can work correctly in any multithreading scenario. Thread safety is achieved primarily with locking and by reducing the possibilities for thread interaction.

General-purpose types are rarely thread-safe in their entirety, for the following reasons:

The development burden in full thread safety can be significant, particularly if a type has many fields (each field is a potential for interaction in an arbitrarily multithreaded context).

Thread safety can entail a performance cost (payable, in part, whether or not the type is actually used by multiple threads).

A thread-safe type does not necessarily make the program using it thread-safe, and often the work involved in the latter makes the former redundant.

Thread safety is thus usually implemented just where it needs to be in order to handle a specific multithreading scenario.

There are, however, a few ways to “cheat” and have large and complex classes run safely in a multithreaded environment. One is to sacrifice granularity by wrapping large sections of code—even access to an entire object—within a single exclusive lock, enforcing serialized access at a high level. This tactic is, in fact, essential if you want to use thread-unsafe third-party code (or most .NET types, for that matter) in a multithreaded context. The trick is simply to use the same exclusive lock to protect access to all properties, methods, and fields on the thread-unsafe object. The solution works well if the object’s methods all execute quickly (otherwise, there will be a lot of blocking).

NOTE
Primitive types aside, few .NET types, when instantiated, are thread-safe for anything more than concurrent read-only access. The onus is on the developer to superimpose thread safety, typically with exclusive locks. (The collections in System.Collections.Concurrent that we cover in Chapter 22 are an exception.)

Another way to cheat is to minimize thread interaction by minimizing shared data. This is an excellent approach and is used implicitly in “stateless” middle-tier application and web-page servers. Because multiple client requests can arrive simultaneously, the server methods they call must be thread-safe. A stateless design (popular for reasons of scalability) intrinsically limits the possibility of interaction because classes do not save data between requests. Thread interaction is then limited just to the static fields that you might choose to create, for such purposes as caching commonly used data in memory and in providing infrastructure services such as authentication and auditing.

Yet another solution (in rich-client applications) is to run code that accesses shared state on the UI thread. As we saw in Chapter 14, asynchronous functions make this easy.

Thread Safety and .NET Types
You can use locking to convert thread-unsafe code into thread-safe code. A good application of this is .NET: nearly all of its nonprimitive types are not thread-safe (for anything more than read-only access) when instantiated, and yet you can use them in multithreaded code if all access to any given object is protected via a lock. Here’s an example in which two threads simultaneously add an item to the same List collection and then enumerate the list:

class ThreadSafe
{
  static List <string> _list = new List <string>();

  static void Main()
  {
    new Thread (AddItem).Start();
    new Thread (AddItem).Start();
  }

  static void AddItem()
  {
    lock (_list) _list.Add ("Item " + _list.Count);

    string[] items;
    lock (_list) items = _list.ToArray();
    foreach (string s in items) Console.WriteLine (s);
  }
}
In this case, we’re locking on the _list object itself. If we had two interrelated lists, we would need to choose a common object upon which to lock (we could nominate one of the lists, or better: use an independent field).

Enumerating .NET collections is also thread-unsafe in the sense that an exception is thrown if the list is modified during enumeration. Rather than locking for the duration of enumeration, in this example, we first copy the items to an array. This avoids holding the lock excessively if what we’re doing during enumeration is potentially time-consuming. (Another solution is to use a reader/writer lock; see “Reader/Writer Locks”.)

Locking around thread-safe objects
Sometimes, you also need to lock around accessing thread-safe objects. To illustrate, imagine that .NET’s List class was, indeed, thread-safe, and we want to add an item to a list:

if (!_list.Contains (newItem)) _list.Add (newItem);
Regardless of whether the list was thread-safe, this statement is certainly not! The whole if statement would need to be wrapped in a lock to prevent preemption in between testing for containership and adding the new item. This same lock would then need to be used everywhere we modified that list. For instance, the following statement would also need to be wrapped in the identical lock to ensure that it did not preempt the former statement:

_list.Clear();
In other words, we would need to lock exactly as with our thread-unsafe collection classes (making the List class’s hypothetical thread safety redundant).

NOTE
Locking around accessing a collection can cause excessive blocking in highly concurrent environments. To this end, .NET provides a thread-safe queue, stack, and dictionary, which we discuss in Chapter 22.

Static members
Wrapping access to an object around a custom lock works only if all concurrent threads are aware of—and use—the lock. This might not be the case if the object is widely scoped. The worst case is with static members in a public type. For instance, imagine if the static property on the DateTime struct, DateTime.Now, was not thread-safe and that two concurrent calls could result in garbled output or an exception. The only way to remedy this with external locking might be to lock the type itself—lock(typeof(DateTime))—before calling DateTime.Now. This would work only if all programmers agreed to do this (which is unlikely). Furthermore, locking a type creates problems of its own.

For this reason, static members on the DateTime struct have been carefully programmed to be thread-safe. This is a common pattern throughout .NET: static members are thread-safe; instance members are not. Following this pattern also makes sense when writing types for public consumption, so as not to create impossible thread-safety conundrums. In other words, by making static methods thread-safe, you’re programming so as not to preclude thread safety for consumers of that type.

NOTE
Thread safety in static methods is something that you must explicitly code: it doesn’t happen automatically by virtue of the method being static!

Read-only thread safety
Making types thread-safe for concurrent read-only access (where possible) is advantageous because it means that consumers can avoid excessive locking. Many .NET types follow this principle: collections, for instance, are thread-safe for concurrent readers.

Following this principle yourself is simple: if you document a type as being thread-safe for concurrent read-only access, don’t write to fields within methods that a consumer would expect to be read-only (or lock around doing so). For instance, in implementing a ToArray() method in a collection, you might begin by compacting the collection’s internal structure. However, this would make it thread-unsafe for consumers that expected this to be read-only.

Read-only thread safety is one of the reasons that enumerators are separate from “enumerables”: two threads can simultaneously enumerate over a collection because each gets a separate enumerator object.

NOTE
In the absence of documentation, it pays to be cautious in assuming whether a method is read-only in nature. A good example is the Random class: when you call Random.Next(), its internal implementation requires that it update private seed values. Therefore, you must either lock around using the Random class or maintain a separate instance per thread.

Thread Safety in Application Servers
Application servers need to be multithreaded to handle simultaneous client requests. ASP.NET Core and Web API applications are implicitly multithreaded. This means that when writing code on the server side, you must consider thread safety if there’s any possibility of interaction among the threads processing client requests. Fortunately, such a possibility is rare; a typical server class is either stateless (no fields) or has an activation model that creates a separate object instance for each client or each request. Interaction usually arises only through static fields, sometimes used for caching in memory parts of a database to improve performance.

For example, suppose that you have a RetrieveUser method that queries a database:

// User is a custom class with fields for user data
internal User RetrieveUser (int id) { ... }
If this method were called frequently, you could improve performance by caching the results in a static Dictionary. Here’s a conceptually simple solution that takes thread safety into account:

static class UserCache
{
  static Dictionary <int, User> _users = new Dictionary <int, User>();

  internal static User GetUser (int id)
  {
    User u = null;

    lock (_users)
      if (_users.TryGetValue (id, out u))
        return u;

    u = RetrieveUser (id);           // Method to retrieve from database;
    lock (_users) _users [id] = u;
    return u;
  }
}
We must, at a minimum, lock around reading and updating the dictionary to ensure thread safety. In this example, we choose a practical compromise between simplicity and performance in locking. Our design creates a small potential for inefficiency: if two threads simultaneously called this method with the same previously unretrieved id, the RetrieveUser method would be called twice—and the dictionary would be updated unnecessarily. Locking once across the whole method would prevent this, but it would create a worse inefficiency: the entire cache would be locked up for the duration of calling RetrieveUser, during which time other threads would be blocked in retrieving any user.

For an ideal solution, we need to use the strategy we described in “Completing synchronously”. Instead of caching User, we cache Task<User>, which the caller then awaits:

static class UserCache
{
  static Dictionary <int, Task<User>> _userTasks = 
     new Dictionary <int, Task<User>>();
  
  internal static Task<User> GetUserAsync (int id)
  {
    lock (_userTasks)
      if (_userTasks.TryGetValue (id, out var userTask))
        return userTask;
      else
        return _userTasks [id] = Task.Run (() => RetrieveUser (id));
  }
}
Notice that we now have a single lock that covers the entire method’s logic. We can do this without hurting concurrency because all we’re doing inside the lock is accessing the dictionary and (potentially) initiating an asynchronous operation (by calling Task.Run). Should two threads call this method at the same time with the same ID, they’ll both end up awaiting the same task, which is exactly the outcome we want.

Immutable Objects
An immutable object is one whose state cannot be altered—externally or internally. The fields in an immutable object are typically declared read-only and are fully initialized during construction.

Immutability is a hallmark of functional programming—where instead of mutating an object, you create a new object with different properties. LINQ follows this paradigm. Immutability is also valuable in multithreading in that it avoids the problem of shared writable state—by eliminating (or minimizing) the writable.

One pattern is to use immutable objects to encapsulate a group of related fields, to minimize lock durations. To take a very simple example, suppose that we had two fields, as follows:

int _percentComplete;
string _statusMessage;
Now let’s assume that we want to read and write them atomically. Rather than locking around these fields, we could define the following immutable class:

class ProgressStatus    // Represents progress of some activity
{
  public readonly int PercentComplete;
  public readonly string StatusMessage;

  // This class might have many more fields...

  public ProgressStatus (int percentComplete, string statusMessage)
  {
    PercentComplete = percentComplete;
    StatusMessage = statusMessage;
  }
}
Then we could define a single field of that type, along with a locking object:

readonly object _statusLocker = new object();
ProgressStatus _status;
We can now read and write values of that type without holding a lock for more than a single assignment:

var status = new ProgressStatus (50, "Working on it");
// Imagine we were assigning many more fields...
// ...
lock (_statusLocker) _status = status;    // Very brief lock
To read the object, we first obtain a copy of the object reference (within a lock). Then, we can read its values without needing to hold onto the lock:

ProgressStatus status;
lock (_statusLocker) status = _status;   // Again, a brief lock
int pc = status.PercentComplete;
string msg = status.StatusMessage;
...
Nonexclusive Locking
The nonexclusive locking constructs serve to limit concurrency. In this section, we cover semaphores and read/writer locks, and also illustrate how the SemaphoreSlim class can limit concurrency with asynchronous operations.

Semaphore
A semaphore is like a nightclub with a limited capacity, enforced by a bouncer. When the club is full, no more people can enter, and a queue builds up outside.

A semaphore’s count corresponds to the number of spaces in the nightclub. Releasing a semaphore increases the count; this typically happens when somebody leaves the club (corresponding to a resource being released), and also when the semaphore is initialized (to set its starting capacity). You can also call Release at any time to increase capacity.

Waiting on a semaphore decrements the count, and typically occurs prior to a resource being obtained. Calling Wait on a semaphore whose current count is greater than 0 completes immediately.

A semaphore can optionally have a maximum count that serves as a hard limit. Increasing the count beyond this limit throws an exception. When constructing a semaphore, you specify the initial count (starting capacity), and optionally, a maximum limit.

A semaphore with an initial count of one is similar to a Mutex or lock, except that the semaphore has no “owner”—it’s thread agnostic. Any thread can call Release on a Semaphore, whereas with Mutex and lock, only the thread that obtained the lock can release it.

NOTE
There are two functionally similar versions of this class: Semaphore and SemaphoreSlim. The latter has been optimized to meet the low-latency demands of parallel programming. It’s also useful in traditional multithreading because it lets you specify a cancellation token when waiting (see “Cancellation”), and it exposes a WaitAsync method for asynchronous programming. You cannot use it, however, for interprocess signaling.

Semaphore incurs about one microsecond in calling WaitOne and Release; SemaphoreSlim incurs about one-tenth of that.

Semaphores can be useful in limiting concurrency—preventing too many threads from executing a particular piece of code at once. In the following example, five threads try to enter a nightclub that allows only three threads in at once:

class TheClub      // No door lists!
{
  static SemaphoreSlim _sem = new SemaphoreSlim (3);    // Capacity of 3
 
  static void Main()
  {
    for (int i = 1; i <= 5; i++) new Thread (Enter).Start (i);
  }

  static void Enter (object id)
  {
    Console.WriteLine (id + " wants to enter");
    _sem.Wait();
    Console.WriteLine (id + " is in!");           // Only three threads
    Thread.Sleep (1000 * (int) id);               // can be here at
    Console.WriteLine (id + " is leaving");       // a time.
    _sem.Release();
  }
}

1 wants to enter
1 is in!
2 wants to enter
2 is in!
3 wants to enter
3 is in!
4 wants to enter
5 wants to enter
1 is leaving
4 is in!
2 is leaving
5 is in!
It’s also legal to instantiate a semaphore with an initial count (capacity) of 0 and then call Release to increase its count. The following two semaphores are equivalent:

var semaphore1 = new SemaphoreSlim (3);
var semaphore2 = new SemaphoreSlim (0); semaphore2.Release (3);
A Semaphore, if named, can span processes in the same way as a Mutex (named Semaphores are available only on Windows, whereas named Mutex also work on Unix platforms).

Asynchronous semaphores and locks
It is illegal to lock across an await statement:

lock (_locker)
{
  await Task.Delay (1000);    // Compilation error
  ...
}
Doing so would make no sense, because locks are held by a thread, which typically changes when returning from an await. Locking also blocks, and blocking for a potentially long period of time is exactly what you’re not trying to achieve with asynchronous functions.

It’s still sometimes desirable, however, to make asynchronous operations execute sequentially—or limit the parallelism such that not more than n operations execute at once. For example, consider a web browser: it needs to perform asynchronous downloads in parallel, but it might want to impose a limit such that a maximum of 10 downloads happen at a time. We can achieve this by using a SemaphoreSlim:

SemaphoreSlim _semaphore = new SemaphoreSlim (10);

async Task<byte[]> DownloadWithSemaphoreAsync (string uri)
{
    await _semaphore.WaitAsync();
    try { return await new WebClient().DownloadDataTaskAsync (uri); }
    finally { _semaphore.Release(); }
}
Reducing the semaphore’s initialCount to 1 reduces the maximum parallelism to 1, turning this into an asynchronous lock.

Writing an EnterAsync extension method
The following extension method simplifies the asynchronous use of SemaphoreSlim by using the Disposable class that we wrote in “Anonymous Disposal”:

public static async Task<IDisposable> EnterAsync (this SemaphoreSlim ss)
{
  await ss.WaitAsync().ConfigureAwait (false);
  return Disposable.Create (() => ss.Release());
}
With this method, we can rewrite our DownloadWithSemaphoreAsync method as follows:

async Task<byte[]> DownloadWithSemaphoreAsync (string uri)
{
  using (await _semaphore.EnterAsync())
    return await new WebClient().DownloadDataTaskAsync (uri);
}
Parallel.ForEachAsync
From .NET 6, another approach to limit asynchronous concurrency is to use the Parallel.ForEachAsync method. Assuming uris in an array of URIs that you wish to download, here’s how to download them in parallel, while limiting the concurrency to a maximum of 10 parallel downloads:

await Parallel.ForEachAsync (uris,
  new ParallelOptions { MaxDegreeOfParallelism = 10 },
  async (uri, cancelToken) =>
   {
    var download = await new HttpClient().GetByteArrayAsync (uri);
    Console.WriteLine ($"Downloaded {download.Length} bytes");
  });
The other methods in the Parallel class are intended for (compute-bound) parallel programming scenarios, which we describe in Chapter 22.

Reader/Writer Locks
Quite often, instances of a type are thread-safe for concurrent read operations, but not for concurrent updates (nor for a concurrent read and update). This can also be true with resources such as a file. Although protecting instances of such types with a simple exclusive lock for all modes of access usually does the trick, it can unreasonably restrict concurrency if there are many readers and just occasional updates. An example of where this could occur is in a business application server, for which commonly used data is cached for fast retrieval in static fields. The ReaderWriterLockSlim class is designed to provide maximum-availability locking in just this scenario.

NOTE
ReaderWriterLockSlim is a replacement for the older “fat” ReaderWriterLock class. The latter is similar in functionality, but it is several times slower and has an inherent design fault in its mechanism for handling lock upgrades.

When compared to an ordinary lock (Monitor.Enter/Exit), ReaderWriterLockSlim is still twice as slow, though. The trade-off is less contention (when there’s a lot of reading and minimal writing).

With both classes, there are two basic kinds of lock—a read lock and a write lock:

A write lock is universally exclusive.

A read lock is compatible with other read locks.

So, a thread holding a write lock blocks all other threads trying to obtain a read or write lock (and vice versa). But if no thread holds a write lock, any number of threads may concurrently obtain a read lock.

ReaderWriterLockSlim defines the following methods for obtaining and releasing read/write locks:

public void EnterReadLock();
public void ExitReadLock();
public void EnterWriteLock();
public void ExitWriteLock();
Additionally, there are “Try” versions of all EnterXXX methods that accept timeout arguments in the style of Monitor.TryEnter (timeouts can occur quite easily if the resource is heavily contended). ReaderWriterLock provides similar methods, named AcquireXXX and ReleaseXXX. These throw an ApplicationException if a timeout occurs, rather than returning false.

The following program demonstrates ReaderWriterLockSlim. Three threads continually enumerate a list, while two further threads append a random number to the list every 100 ms. A read lock protects the list readers, and a write lock protects the list writers:

class SlimDemo
{
  static ReaderWriterLockSlim _rw = new ReaderWriterLockSlim();
  static List<int> _items = new List<int>();
  static Random _rand = new Random();

  static void Main()
  {
    new Thread (Read).Start();
    new Thread (Read).Start();
    new Thread (Read).Start();

    new Thread (Write).Start ("A");
    new Thread (Write).Start ("B");
  }

  static void Read()
  {
    while (true)
    {
      _rw.EnterReadLock();
      foreach (int i in _items) Thread.Sleep (10);
      _rw.ExitReadLock();
    }
  }

  static void Write (object threadID)
  {
    while (true)
    {
      int newNumber = GetRandNum (100);
      _rw.EnterWriteLock();
      _items.Add (newNumber);
      _rw.ExitWriteLock();
      Console.WriteLine ("Thread " + threadID + " added " + newNumber);
      Thread.Sleep (100);
    }
  }

  static int GetRandNum (int max) { lock (_rand) return _rand.Next(max); }
}
NOTE
In production code, you’d typically add try/finally blocks to ensure that locks were released if an exception were thrown.

Here’s the result:

Thread B added 61
Thread A added 83
Thread B added 55
Thread A added 33
...
ReaderWriterLockSlim allows more concurrent Read activity than a simple lock. We can illustrate this by inserting the following line in the Write method, at the start of the while loop:

Console.WriteLine (_rw.CurrentReadCount + " concurrent readers");
This nearly always prints “3 concurrent readers” (the Read methods spend most of their time inside the foreach loops). As well as CurrentReadCount, ReaderWriterLockSlim provides the following properties for monitoring locks:

public bool IsReadLockHeld            { get; }
public bool IsUpgradeableReadLockHeld { get; }
public bool IsWriteLockHeld           { get; }

public int  WaitingReadCount          { get; }
public int  WaitingUpgradeCount       { get; }
public int  WaitingWriteCount         { get; }

public int  RecursiveReadCount        { get; }
public int  RecursiveUpgradeCount     { get; }
public int  RecursiveWriteCount       { get; }
Upgradeable locks
Sometimes, it’s useful to swap a read lock for a write lock in a single atomic operation. For instance, suppose that you want to add an item to a list only if the item wasn’t already present. Ideally, you’d want to minimize the time spent holding the (exclusive) write lock, so you might proceed as follows:

Obtain a read lock.

Test whether the item is already present in the list; if so, release the lock and return.

Release the read lock.

Obtain a write lock.

Add the item.

The problem is that another thread could sneak in and modify the list (e.g., adding the same item) between Steps 3 and 4. ReaderWriterLockSlim addresses this through a third kind of lock called an upgradeable lock. An upgradeable lock is like a read lock except that it can later be promoted to a write lock in an atomic operation. Here’s how you use it:

Call EnterUpgradeableReadLock.

Perform read-based activities (e.g., test whether the item is already present in the list).

Call EnterWriteLock (this converts the upgradeable lock to a write lock).

Perform write-based activities (e.g., add the item to the list).

Call ExitWriteLock (this converts the write lock back to an upgradeable lock).

Perform any other read-based activities.

Call ExitUpgradeableReadLock.

From the caller’s perspective, it’s rather like nested or recursive locking. Functionally, though, in Step 3, ReaderWriterLockSlim releases your read lock and obtains a fresh write lock, atomically.

There’s another important difference between upgradeable locks and read locks. Although an upgradeable lock can coexist with any number of read locks, only one upgradeable lock can itself be taken out at a time. This prevents conversion deadlocks by serializing competing conversions—just as update locks do in SQL Server:

SQL Server	ReaderWriterLockSlim
Share lock	Read lock
Exclusive lock	Write lock
Update lock	Upgradeable lock
We can demonstrate an upgradeable lock by changing the Write method in the preceding example such that it adds a number to the list only if it’s not already present:

while (true)
{
  int newNumber = GetRandNum (100);
  _rw.EnterUpgradeableReadLock();
  if (!_items.Contains (newNumber))
  {
    _rw.EnterWriteLock();
    _items.Add (newNumber);
    _rw.ExitWriteLock();
    Console.WriteLine ("Thread " + threadID + " added " + newNumber);
  }
  _rw.ExitUpgradeableReadLock();
  Thread.Sleep (100);
}
NOTE
ReaderWriterLock can also do lock conversions—but unreliably because it doesn’t support the concept of upgradeable locks. This is why the designers of ReaderWriterLockSlim had to start afresh with a new class.

Lock recursion
Ordinarily, nested or recursive locking is prohibited with ReaderWriterLockSlim. Hence, the following throws an exception:

var rw = new ReaderWriterLockSlim();
rw.EnterReadLock();
rw.EnterReadLock();
rw.ExitReadLock();
rw.ExitReadLock();
It runs without error, however, if you construct ReaderWriterLockSlim as follows:

var rw = new ReaderWriterLockSlim (LockRecursionPolicy.SupportsRecursion);
This ensures that recursive locking can happen only if you plan for it. Recursive locking can create undesired complexity because it’s possible to acquire more than one kind of lock:

rw.EnterWriteLock();
rw.EnterReadLock();
Console.WriteLine (rw.IsReadLockHeld);     // True
Console.WriteLine (rw.IsWriteLockHeld);    // True
rw.ExitReadLock();
rw.ExitWriteLock();
The basic rule is that after you’ve acquired a lock, subsequent recursive locks can be less, but not greater, on the following scale:

Read Lock→Upgradeable Lock→Write Lock

A request to promote an upgradeable lock to a write lock, however, is always legal.

Signaling with Event Wait Handles
The simplest kind of signaling constructs are called event wait handles (unrelated to C# events). Event wait handles come in three flavors: AutoResetEvent, ManualRe⁠setEvent(Slim), and CountdownEvent. The former two are based on the common EventWaitHandle class from which they derive all their functionality.

AutoResetEvent
An AutoResetEvent is like a ticket turnstile: inserting a ticket lets exactly one person through. The “auto” in the class’s name refers to the fact that an open turnstile automatically closes or “resets” after someone steps through. A thread waits, or blocks, at the turnstile by calling WaitOne (wait at this “one” turnstile until it opens), and a ticket is inserted by calling the Set method. If a number of threads call WaitOne, a queue2 builds up behind the turnstile. A ticket can come from any thread; in other words, any (unblocked) thread with access to the AutoResetEvent object can call Set on it to release one blocked thread.

You can create an AutoResetEvent in two ways. The first is via its constructor:

var auto = new AutoResetEvent (false);
(Passing true into the constructor is equivalent to immediately calling Set upon it.) The second way to create an AutoResetEvent is as follows:

var auto = new EventWaitHandle (false, EventResetMode.AutoReset);
In the following example, a thread is started whose job is simply to wait until signaled by another thread (see Figure 21-1):

class BasicWaitHandle
{
  static EventWaitHandle _waitHandle = new AutoResetEvent (false);

  static void Main()
  {
    new Thread (Waiter).Start();
    Thread.Sleep (1000);                  // Pause for a second...
    _waitHandle.Set();                    // Wake up the Waiter.
  }

  static void Waiter()
  {
    Console.WriteLine ("Waiting...");
    _waitHandle.WaitOne();                // Wait for notification
    Console.WriteLine ("Notified");
  }
}

// Output:
Waiting... (pause) Notified.

Figure 21-1. Signaling with an EventWaitHandle
If Set is called when no thread is waiting, the handle stays open for as long as it takes until some thread calls WaitOne. This behavior helps prevent a race between a thread heading for the turnstile and a thread inserting a ticket (“Oops, inserted the ticket a microsecond too soon; now you’ll have to wait indefinitely!”). However, calling Set repeatedly on a turnstile at which no one is waiting doesn’t allow an entire party through when they arrive: only the next single person is let through, and the extra tickets are “wasted.”

DISPOSING WAIT HANDLES
After you’ve finished with a wait handle, you can call its Close method to release the OS resource. Alternatively, you can simply drop all references to the wait handle and allow the garbage collector to do the job for you sometime later (wait handles implement the disposal pattern whereby the finalizer calls Close). This is one of the few scenarios for which relying on this backup is (arguably) acceptable, because wait handles have a light OS burden.

Wait handles are released automatically when a process exits.

Calling Reset on an AutoResetEvent closes the turnstile (should it be open) without waiting or blocking.

WaitOne accepts an optional timeout parameter, returning false if the wait ended because of a timeout rather than obtaining the signal.

NOTE
Calling WaitOne with a timeout of 0 tests whether a wait handle is “open,” without blocking the caller. Keep in mind, though, that doing this resets the AutoResetEvent if it’s open.

Two-way signaling
Suppose that we want the main thread to signal a worker thread three times in a row. If the main thread simply calls Set on a wait handle several times in rapid succession, the second or third signal can become lost because the worker might take time to process each signal.

The solution is for the main thread to wait until the worker’s ready before signaling it. We can do this by using another AutoResetEvent, as follows:

class TwoWaySignaling
{
  static EventWaitHandle _ready = new AutoResetEvent (false);
  static EventWaitHandle _go = new AutoResetEvent (false);
  static readonly object _locker = new object();
  static string _message;

  static void Main()
  {
    new Thread (Work).Start();

    _ready.WaitOne();                  // First wait until worker is ready
    lock (_locker) _message = "ooo";
    _go.Set();                         // Tell worker to go

    _ready.WaitOne();
    lock (_locker) _message = "ahhh";  // Give the worker another message
    _go.Set();

    _ready.WaitOne();
    lock (_locker) _message = null;    // Signal the worker to exit
    _go.Set();
  }

  static void Work()
  {
    while (true)
    {
      _ready.Set();                          // Indicate that we're ready
      _go.WaitOne();                         // Wait to be kicked off...
      lock (_locker)
      {
        if (_message == null) return;        // Gracefully exit
        Console.WriteLine (_message);
      }
    }
  }
}

// Output:
ooo
ahhh
Figure 21-2 shows this process.


Figure 21-2. Two-way signaling
Here, we’re using a null message to indicate that the worker should end. With threads that run indefinitely, it’s important to have an exit strategy!

ManualResetEvent
As we described in Chapter 14, a ManualResetEvent functions like a simple gate. Calling Set opens the gate, allowing any number of threads calling WaitOne to be let through. Calling Reset closes the gate. Threads that call WaitOne on a closed gate will block; when the gate is next opened, they will be released all at once. Apart from these differences, a ManualResetEvent functions like an AutoResetEvent.

As with AutoResetEvent, you can construct a ManualResetEvent in two ways:

var manual1 = new ManualResetEvent (false);
var manual2 = new EventWaitHandle (false, EventResetMode.ManualReset);
NOTE
There’s another version of ManualResetEvent called ManualResetEventSlim. The latter is optimized for short waiting times—with the ability to opt into spinning for a set number of iterations. It also has a more efficient managed implementation and allows a Wait to be canceled via a CancellationToken. ManualResetEventSlim doesn’t subclass WaitHandle; however, it exposes a WaitHandle property that returns a WaitHandle-based object when called (with the performance profile of a traditional wait handle).

SIGNALING CONSTRUCTS AND PERFORMANCE
Waiting or signaling an AutoResetEvent or ManualResetEvent takes about one microsecond (assuming no blocking).

ManualResetEventSlim and CountdownEvent can be up to 50 times faster in short-wait scenarios because of their nonreliance on the OS and judicious use of spinning constructs. In most scenarios, however, the overhead of the signaling classes themselves doesn’t create a bottleneck; thus, it is rarely a consideration.

A ManualResetEvent is useful in allowing one thread to unblock many other threads. The reverse scenario is covered by CountdownEvent.

CountdownEvent
CountdownEvent lets you wait on more than one thread. The class has an efficient, fully managed implementation. To use the class, instantiate it with the number of threads, or “counts,” that you want to wait on:

var countdown = new CountdownEvent (3);  // Initialize with "count" of 3.
Calling Signal decrements the “count”; calling Wait blocks until the count goes down to zero:

new Thread (SaySomething).Start ("I am thread 1");
new Thread (SaySomething).Start ("I am thread 2");
new Thread (SaySomething).Start ("I am thread 3");

countdown.Wait();   // Blocks until Signal has been called 3 times
Console.WriteLine ("All threads have finished speaking!");

void SaySomething (object thing)
{
  Thread.Sleep (1000);
  Console.WriteLine (thing);
  countdown.Signal();
}
NOTE
You can sometimes more easily solve problems for which CountdownEvent is effective by using the structured parallelism constructs that we describe in Chapter 22 (PLINQ and the Parallel class).

You can reincrement a CountdownEvent’s count by calling AddCount. However, if it has already reached zero, this throws an exception: you can’t “unsignal” a CountdownEvent by calling AddCount. To prevent the possibility of an exception being thrown, you can instead call TryAddCount, which returns false if the countdown is zero.

To unsignal a countdown event, call Reset: this both unsignals the construct and resets its count to the original value.

Like ManualResetEventSlim, CountdownEvent exposes a WaitHandle property for scenarios in which some other class or method expects an object based on WaitHandle.

Creating a Cross-Process EventWaitHandle
EventWaitHandle’s constructor allows a “named” EventWaitHandle to be created, capable of operating across multiple processes. The name is simply a string, and it can be any value that doesn’t unintentionally conflict with someone else’s! If the name is already in use on the computer, you get a reference to the same underlying EventWaitHandle; otherwise, the OS creates a new one. Here’s an example:

EventWaitHandle wh = new EventWaitHandle (false, EventResetMode.AutoReset,
                                      @"Global\MyCompany.MyApp.SomeName");
If two applications each ran this code, they would be able to signal each other: the wait handle would work across all threads in both processes.

Named event wait handles are available only on Windows.

Wait Handles and Continuations
Rather than waiting on a wait handle (and blocking your thread), you can attach a “continuation” to it by calling ThreadPool.RegisterWaitForSingleObject. This method accepts a delegate that is executed when a wait handle is signaled:

var starter = new ManualResetEvent (false);

RegisteredWaitHandle reg = ThreadPool.RegisterWaitForSingleObject
 (starter, Go, "Some Data", -1, true);

Thread.Sleep (5000);
Console.WriteLine ("Signaling worker...");
starter.Set();
Console.ReadLine();
reg.Unregister (starter);    // Clean up when we’re done.

void Go (object data, bool timedOut)
{
  Console.WriteLine ("Started - " + data);
  // Perform task...
}

// Output:
(5 second delay)
Signaling worker...
Started - Some Data
When the wait handle is signaled (or a timeout elapses), the delegate runs on a pooled thread. You are then supposed to call Unregister to release the unmanaged handle to the callback.

In addition to the wait handle and delegate, RegisterWaitForSingleObject accepts a “black box” object that it passes to your delegate method (rather like ParameterizedThreadStart) as well as a timeout in milliseconds (-1 meaning no timeout) and a Boolean flag indicating whether the request is a one-off rather than recurring.

NOTE
You can reliably call RegisterWaitForSingleObject only once per wait handle. Calling this method again on the same wait handle causes an intermittent failure, whereby an unsignaled wait handle fires a callback as though it were signaled.

This limitation makes (the nonslim) wait handles poorly suited to asynchronous programming.

WaitAny, WaitAll, and SignalAndWait
In addition to the Set, WaitOne, and Reset methods, there are static methods on the WaitHandle class to crack more complex synchronization nuts. The WaitAny, WaitAll, and SignalAndWait methods perform signaling and waiting operations on multiple handles. The wait handles can be of differing types (including Mutex and Semaphore given that these also derive from the abstract WaitHandle class). ManualResetEventSlim and CountdownEvent can also partake in these methods via their WaitHandle properties.

NOTE
WaitAll and SignalAndWait have a weird connection to the legacy COM architecture: these methods require that the caller be in a multithreaded apartment, the model least suitable for interoperability. The main thread of a WPF or Windows Forms application, for example, is unable to interact with the clipboard in this mode. We discuss alternatives shortly.

WaitHandle.WaitAny waits for any one of an array of wait handles; WaitHan⁠dle.WaitAll waits on all of the given handles, atomically. This means that if you wait on two AutoResetEvents:

WaitAny will never end up “latching” both events.

WaitAll will never end up “latching” only one event.

SignalAndWait calls Set on one WaitHandle and then calls WaitOne on another WaitHandle. After signaling the first handle, it will jump to the head of the queue in waiting on the second handle; this helps it succeed (although the operation is not truly atomic). You can think of this method as “swapping” one signal for another, and use it on a pair of EventWaitHandles to set up two threads to rendezvous, or “meet,” at the same point in time. Either AutoResetEvent or ManualResetEvent will do the trick. The first thread executes the following:

WaitHandle.SignalAndWait (wh1, wh2);
The second thread does the opposite:

WaitHandle.SignalAndWait (wh2, wh1);
Alternatives to WaitAll and SignalAndWait
WaitAll and SignalAndWait won’t run in a single-threaded apartment. Fortunately, there are alternatives. In the case of SignalAndWait, it’s rare that you need its queue-jumping semantics: in our rendezvous example, for instance, it would be valid simply to call Set on the first wait handle, and then WaitOne on the other, if wait handles were used solely for that rendezvous. In the following section, we explore yet another option for implementing a thread rendezvous.

In the case of WaitAny and WaitAll, if you don’t need atomicity, you can use the code we wrote in the previous section to convert the wait handles to tasks and then use Task.WhenAny and Task.WhenAll (Chapter 14).

If you need atomicity, you can take the lowest-level approach to signaling and write the logic yourself with Monitor’s Wait and Pulse methods. We describe Wait and Pulse in detail in http://albahari.com/threading.

The Barrier Class
The Barrier class implements a thread execution barrier, allowing many threads to rendezvous at a point in time (not to be confused with Thread.MemoryBarrier). The class is very fast and efficient, and is built upon Wait, Pulse, and spinlocks.

To use this class:

Instantiate it, specifying how many threads should partake in the rendezvous (you can change this later by calling AddParticipants/RemoveParticipants).

Have each thread call SignalAndWait when it wants to rendezvous.

Instantiating Barrier with a value of 3 causes SignalAndWait to block until that method has been called three times. It then starts over: calling SignalAndWait again blocks until called another three times. This keeps each thread “in step” with every other thread.

In the following example, each of three threads writes the numbers 0 through 4 while keeping in step with the other threads:

var barrier = new Barrier (3);

new Thread (Speak).Start();
new Thread (Speak).Start();
new Thread (Speak).Start();

void Speak()
{
  for (int i = 0; i < 5; i++)
  {
    Console.Write (i + " ");
    barrier.SignalAndWait();
  }
}

OUTPUT:  0 0 0 1 1 1 2 2 2 3 3 3 4 4 4
A really useful feature of Barrier is that you can also specify a post-phase action when constructing it. This is a delegate that runs after SignalAndWait has been called n times, but before the threads are unblocked (as shown in the shaded area in Figure 21-3). In our example, if we instantiate our barrier as follows:

static Barrier _barrier = new Barrier (3, barrier => Console.WriteLine());
the output is this:

0 0 0 
1 1 1 
2 2 2 
3 3 3 
4 4 4

Figure 21-3. Barrier
A post-phase action can be useful for coalescing data from each of the worker threads. It doesn’t need to worry about preemption, because all workers are blocked while it does its thing.

Lazy Initialization
A frequent problem in threading is how to lazily initialize a shared field in a thread-safe fashion. The need arises when you have a field of a type that’s expensive to construct:

class Foo
{
  public readonly Expensive Expensive = new Expensive();
  ...
}
class Expensive {  /* Suppose this is expensive to construct */  }
The problem with this code is that instantiating Foo incurs the performance cost of instantiating Expensive—regardless of whether the Expensive field is ever accessed. The obvious answer is to construct the instance on demand:

class Foo
{
  Expensive _expensive;
  public Expensive Expensive         // Lazily instantiate Expensive
  {
    get
    {
      if (_expensive == null) _expensive = new Expensive();
      return _expensive;
    }
  }
  ...
}
The question then arises, is this thread-safe? Aside from the fact that we’re accessing _expensive outside a lock without a memory barrier, consider what would happen if two threads accessed this property at once. They could both satisfy the if statement’s predicate and each thread end up with a different instance of Expensive. Because this can lead to subtle errors, we would say, in general, that this code is not thread-safe.

The solution to the problem is to lock around checking and initializing the object:

Expensive _expensive;
readonly object _expenseLock = new object();

public Expensive Expensive
{
  get
  {
    lock (_expenseLock)
    {
      if (_expensive == null) _expensive = new Expensive();
      return _expensive;
    }
  }
}
Lazy<T>
The Lazy<T> class is available to help with lazy initialization. If instantiated with an argument of true, it implements the thread-safe initialization pattern just described.

NOTE
Lazy<T> actually implements a micro-optimized version of this pattern, called double-checked locking. Double-checked locking performs an additional volatile read to avoid the cost of obtaining a lock if the object is already initialized.

To use Lazy<T>, instantiate the class with a value factory delegate that tells it how to initialize a new value, and the argument true. Then, access its value via the Value property:

Lazy<Expensive> _expensive = new Lazy<Expensive>
  (() => new Expensive(), true);

public Expensive Expensive { get { return _expensive.Value; } }
If you pass false into Lazy<T>’s constructor, it implements the thread-unsafe lazy initialization pattern that we described at the beginning of this section—this makes sense when you want to use Lazy<T> in a single-threaded context.

LazyInitializer
LazyInitializer is a static class that works exactly like Lazy<T> except:

Its functionality is exposed through a static method that operates directly on a field in your own type. This prevents a level of indirection, improving performance in cases where you need extreme optimization.

It offers another mode of initialization in which multiple threads can race to initialize.

To use LazyInitializer, call EnsureInitialized before accessing the field, passing a reference to the field and the factory delegate:

Expensive _expensive;
public Expensive Expensive
{ 
  get          // Implement double-checked locking
  { 
    LazyInitializer.EnsureInitialized (ref _expensive,
                                      () => new Expensive());
    return _expensive;
  }
}
You can also pass in another argument to request that competing threads race to initialize. This sounds similar to our original thread-unsafe example except that the first thread to finish always wins—and so you end up with only one instance. The advantage of this technique is that it’s even faster (on multicores) than double-checked locking because it can be implemented entirely without locks using advanced techniques that we describe in “Nonblocking Synchronization” and “Lazy Initialization” at http://albahari.com/threading. This is an extreme (and rarely needed) optimization that comes at a cost:

It’s slower when more threads race to initialize than you have cores.

It potentially wastes CPU resources performing redundant initialization.

The initialization logic must be thread-safe (in this case, it would be thread-unsafe if Expensive’s constructor wrote to static fields, for instance).

If the initializer instantiates an object requiring disposal, the “wasted” object won’t be disposed without additional logic.

Thread-Local Storage
Much of this chapter has focused on synchronization constructs and the issues arising from having threads concurrently access the same data. Sometimes, however, you want to keep data isolated, ensuring that each thread has a separate copy. Local variables achieve exactly this, but they are useful only with transient data.

The solution is thread-local storage. You might be hard-pressed to think of a requirement: data you’d want to keep isolated to a thread tends to be transient by nature. Its main application is for storing “out-of-band” data—that which supports the execution path’s infrastructure, such as messaging, transaction, and security tokens. Passing such data around in method parameters can be clumsy and can alienate all but your own methods; storing such information in ordinary static fields means sharing it among all threads.

Thread-local storage can also be useful in optimizing parallel code. It allows each thread to exclusively access its own version of a thread-unsafe object without needing locks—and without needing to reconstruct that object between method calls.

There are four ways to implement thread-local storage. We take a look at them in the following subsections.

[ThreadStatic]
The easiest approach to thread-local storage is to mark a static field with the ThreadStatic attribute:

[ThreadStatic] static int _x;
Each thread then sees a separate copy of _x.

Unfortunately, [ThreadStatic] doesn’t work with instance fields (it simply does nothing); nor does it play well with field initializers—they execute only once on the thread that’s running when the static constructor executes. If you need to work with instance fields—or start with a nondefault value—ThreadLocal<T> provides a better option.

ThreadLocal<T>
ThreadLocal<T> provides thread-local storage for both static and instance fields, and allows you to specify default values.

Here’s how to create a ThreadLocal<int> with a default value of 3 for each thread:

static ThreadLocal<int> _x = new ThreadLocal<int> (() => 3);
You then use _x’s Value property to get or set its thread-local value. A bonus of using ThreadLocal is that values are lazily evaluated: the factory function evaluates on the first call (for each thread).

ThreadLocal<T> and instance fields
ThreadLocal<T> is also useful with instance fields and captured local variables. For example, consider the problem of generating random numbers in a multithreaded environment. The Random class is not thread-safe, so we have to either lock around using Random (limiting concurrency) or generate a separate Random object for each thread. ThreadLocal<T> makes the latter easy:

var localRandom = new ThreadLocal<Random>(() => new Random());
Console.WriteLine (localRandom.Value.Next());
Our factory function for creating the Random object is a bit simplistic, though, in that Random’s parameterless constructor relies on the system clock for a random number seed. This may be the same for two Random objects created within ~10 ms of each other. Here’s one way to fix it:

var localRandom = new ThreadLocal<Random>
 ( () => new Random (Guid.NewGuid().GetHashCode()) );
We use this in Chapter 22 (see the parallel spellchecking example in “PLINQ”).

GetData and SetData
The third approach is to use two methods in the Thread class: GetData and SetData. These store data in thread-specific “slots.” Thread.GetData reads from a thread’s isolated data store; Thread.SetData writes to it. Both methods require a LocalDataStoreSlot object to identify the slot. You can use the same slot across all threads and they’ll still get separate values. Here’s an example:

class Test
{
  // The same LocalDataStoreSlot object can be used across all threads.
  LocalDataStoreSlot _secSlot = Thread.GetNamedDataSlot ("securityLevel");

  // This property has a separate value on each thread.
  int SecurityLevel
  {
    get
    {
      object data = Thread.GetData (_secSlot);
      return data == null ? 0 : (int) data;    // null == uninitialized
    }
    set { Thread.SetData (_secSlot, value); }
  }
  ...
In this instance, we called Thread.GetNamedDataSlot, which creates a named slot—this allows sharing of that slot across the application. Alternatively, you can control a slot’s scope yourself with an unnamed slot, obtained by calling Thread.AllocateDataSlot:

class Test
{
  LocalDataStoreSlot _secSlot = Thread.AllocateDataSlot();
  ...
Thread.FreeNamedDataSlot will release a named data slot across all threads, but only once all references to that LocalDataStoreSlot have dropped out of scope and have been garbage-collected. This ensures that threads don’t have data slots pulled out from under their feet, as long as they keep a reference to the appropriate LocalDataStoreSlot object while the slot is needed.

AsyncLocal<T>
The approaches to thread-local storage that we’ve discussed so far are incompatible with asynchronous functions, because after an await, execution can resume on a different thread. The AsyncLocal<T> class solves this by preserving its value across an await:

static AsyncLocal<string> _asyncLocalTest = new AsyncLocal<string>();

async void Main()
{
  _asyncLocalTest.Value = "test";  
  await Task.Delay (1000);  
  // The following works even if we come back on another thread:
  Console.WriteLine (_asyncLocalTest.Value);   // test
}
AsyncLocal<T> is still able to keep operations started on separate threads apart, whether initiated by Thread.Start or Task.Run. The following writes “one one” and “two two”:

static AsyncLocal<string> _asyncLocalTest = new AsyncLocal<string>();

void Main()
{
  // Call Test twice on two concurrent threads:
  new Thread (() => Test ("one")).Start();
  new Thread (() => Test ("two")).Start();
}

async void Test (string value)
{
  _asyncLocalTest.Value = value;
  await Task.Delay (1000);
  Console.WriteLine (value + " " + _asyncLocalTest.Value);
}
AsyncLocal<T> has an interesting and unique nuance: if an AsyncLocal<T> object already has a value when a thread is started, the new thread will “inherit” that value:

static AsyncLocal<string> _asyncLocalTest = new AsyncLocal<string>();

void Main()
{
  _asyncLocalTest.Value = "test";
  new Thread (AnotherMethod).Start();
}

void AnotherMethod() => Console.WriteLine (_asyncLocalTest.Value);  // test
The new thread, however, gets a copy of the value, so any changes that it makes will not affect the original:

static AsyncLocal<string> _asyncLocalTest = new AsyncLocal<string>();

void Main()
{
  _asyncLocalTest.Value = "test";
  var t = new Thread (AnotherMethod);
  t.Start(); t.Join();
  Console.WriteLine (_asyncLocalTest.Value);   // test  (not ha-ha!)
}

void AnotherMethod() => _asyncLocalTest.Value = "ha-ha!";
Keep in mind that the new thread gets a shallow copy of the value. So, if you were to replace Async<string> with Async<StringBuilder> or Async<List<string>>, the new thread could clear the StringBuilder or add/remove items to the List<string>, and this would affect the original.

Timers
If you need to execute some method repeatedly at regular intervals, the easiest way is with a timer. Timers are convenient and efficient in their use of memory and resources—compared with techniques such as the following:

new Thread (delegate() {
                         while (enabled)
                         {
                           DoSomeAction();
                           Thread.Sleep (TimeSpan.FromHours (24));
                         }
                       }).Start();
Not only does this permanently tie up a thread resource, but without additional coding, DoSomeAction will happen at a later time each day. Timers solve these problems.

.NET provides five timers. Two of these are general-purpose multithreaded timers:

System.Threading.Timer

System.Timers.Timer

The other two are special-purpose single-threaded timers:

System.Windows.Forms.Timer (Windows Forms timer)

System.Windows.Threading.DispatcherTimer (WPF timer)

The multithreaded timers are more powerful, accurate, and flexible; the single-threaded timers are safer and more convenient for running simple tasks that update Windows Forms controls or WPF elements.

Finally, from .NET 6, there’s the PeriodicTimer, which we will cover first.

PeriodicTimer
PeriodicTimer is not really a timer; it’s a class to help with asynchronous looping. It’s important to consider that since the advent of async and await, traditional timers are not usually necessary. Instead, the following pattern works nicely:

StartPeriodicOperation();

async void StartPeriodicOperation()
{
  while (true)
  {
    await Task.Delay (1000);
    Console.WriteLine ("Tick");   // Do some action
  }
 }
NOTE
If you call StartPeriodicOperation from a UI thread, it will behave as a single-threaded timer, because the await will always return on the same synchronization context.

You can make it behave as a multithreaded timer simply by adding .ConfigureAwait(false) to the await.

PeriodicTimer is a class to simplify this pattern:

var timer = new PeriodicTimer (TimeSpan.FromSeconds (1));
StartPeriodicOperation();
// Optionally dispose timer when you want to stop looping.

async void StartPeriodicOperation()
{
  while (await timer.WaitForNextTickAsync())
    Console.WriteLine ("Tick");    // Do some action
}
PeriodicTimer also allows you to stop the timer by disposing the timer instance. This results in WaitForNextTickAsync returning false, allowing the loop to end.

Multithreaded Timers
System.Threading.Timer is the simplest multithreaded timer: it has just a constructor and two methods (a delight for minimalists, as well as book authors!). In the following example, a timer calls the Tick method, which writes “tick...” after five seconds have elapsed, and then every second after that, until the user presses Enter:

using System;
using System.Threading;

// First interval = 5000ms; subsequent intervals = 1000ms
Timer tmr = new Timer (Tick, "tick...", 5000, 1000);
Console.ReadLine();
tmr.Dispose();         // This both stops the timer and cleans up.

void Tick (object data)
{
  // This runs on a pooled thread
  Console.WriteLine (data);          // Writes "tick..."
}
NOTE
See “Timers” for a discussion on disposing multithreaded timers.

You can change a timer’s interval later by calling its Change method. If you want a timer to fire just once, specify Timeout.Infinite in the constructor’s last argument.

.NET provides another timer class of the same name in the System.Timers namespace. This simply wraps the System.Threading.Timer, providing additional convenience while using the identical underlying engine. Here’s a summary of its added features:

An IComponent implementation, allowing it to be sited in Visual Studio’s Designer’s component tray

An Interval property instead of a Change method

An Elapsed event instead of a callback delegate

An Enabled property to start and stop the timer (its default value being false)

Start and Stop methods in case you’re confused by Enabled

An AutoReset flag for indicating a recurring event (default value is true)

A SynchronizingObject property with Invoke and BeginInvoke methods for safely calling methods on WPF elements and Windows Forms controls

Here’s an example:

using System;
using System.Timers;          // Timers namespace rather than Threading

var tmr = new Timer();        // Doesn't require any args
tmr.Interval = 500;
tmr.Elapsed += tmr_Elapsed;   // Uses an event instead of a delegate
tmr.Start();                  // Start the timer
Console.ReadLine();
tmr.Stop();                   // Stop the timer
Console.ReadLine();
tmr.Start();                  // Restart the timer
Console.ReadLine();
tmr.Dispose();                // Permanently stop the timer

void tmr_Elapsed (object sender, EventArgs e)
  => Console.WriteLine ("Tick");
Multithreaded timers use the thread pool to allow a few threads to serve many timers. This means that the callback method or Elapsed event can fire on a different thread each time it is called. Furthermore, the Elapsed event always fires (approximately) on time—regardless of whether the previous Elapsed event finished executing. Hence, callbacks or event handlers must be thread-safe.

The precision of multithreaded timers depends on the OS, and is typically in the 10- to 20-millisecond region. If you need greater precision, you can use native interop and call the Windows multimedia timer. This has precision down to one millisecond, and it is defined in winmm.dll. First call timeBeginPeriod to inform the OS that you need high timing precision, and then call timeSetEvent to start a multimedia timer. When you’re done, call timeKillEvent to stop the timer and timeEndPeriod to inform the OS that you no longer need high timing precision. Chapter 24 demonstrates calling external methods with P/Invoke. You can find complete examples on the internet that use the multimedia timer by searching for the keywords dllimport winmm.dll timesetevent.

Single-Threaded Timers
.NET provides timers designed to eliminate thread-safety issues for WPF and Windows Forms applications:

System.Windows.Threading.DispatcherTimer (WPF)

System.Windows.Forms.Timer (Windows Forms)

NOTE
The single-threaded timers are not designed to work outside their respective environments. If you use a Windows Forms timer in a Windows Service application, for instance, the Timer event won’t fire!

Both are like System.Timers.Timer in the members that they expose—Interval, Start, and Stop (and Tick, which is equivalent to Elapsed)—and are used in a similar manner. However, they differ in how they work internally. Instead of firing timer events on pooled threads, they post the events to the WPF or Windows Forms message loop. This means that the Tick event always fires on the same thread that originally created the timer—which, in a normal application, is the same thread used to manage all user interface elements and controls. This has a number of benefits:

You can forget about thread safety.

A fresh Tick will never fire until the previous Tick has finished processing.

You can update user interface elements and controls directly from Tick event handling code without calling Control.BeginInvoke or Dispatcher.BeginInvoke.

Thus, a program employing these timers is not really multithreaded: you end up with the same kind of pseudo-concurrency that’s described in Chapter 14 with asynchronous functions that execute on a UI thread. One thread serves all timers as well as the processing UI events, which means that the Tick event handler must execute quickly, otherwise the UI becomes unresponsive.

This makes the WPF and Windows Forms timers suitable for small jobs, typically updating some aspect of the UI (e.g., a clock or countdown display).

In terms of precision, the single-threaded timers are similar to the multithreaded timers (tens of milliseconds), although they are typically less accurate because they can be delayed while other UI requests (or other timer events) are processed.

1 Nuances in the behavior of Windows and the CLR mean that the fairness of the queue can sometimes be violated.

2 As with locks, the fairness of the queue can sometimes be violated due to nuances in the operating system.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


21. Advanced Threading
22. Parallel Programming
23. Span<T> and Memory<T>
25h 47m remaining
Chapter 22. Parallel Programming
In this chapter, we cover the multithreading APIs and constructs aimed at leveraging multicore processors:

Parallel LINQ or PLINQ

The Parallel class

The task parallelism constructs

The concurrent collections

These constructs are collectively known (loosely) as Parallel Framework (PFX). The Parallel class together with the task parallelism constructs is called the Task Parallel Library (TPL).

You’ll need to be comfortable with the fundamentals in Chapter 14 before reading this chapter—particularly locking, thread safety, and the Task class.

NOTE
.NET offers a number of additional specialized APIs to help with parallel and asynchronous programming:

System.Threading.Channels.Channel is a high-performance asynchronous producer/consumer queue, introduced in .NET Core 3.

Microsoft Dataflow (in the System.Thread⁠ing.Tasks.Dataflow namespace) is a sophisticated API for creating networks of buffered blocks that execute actions or data transformations in parallel, with a semblance to actor/agent programming.

Reactive Extensions implements LINQ over IObservable (an alternative abstraction to IAsyncEnumerable) and excels at combining asynchronous streams. Reactive extensions ships in the System.Reactive NuGet package.

Why PFX?
Over the past 15 years, CPU manufacturers have shifted from single-core to multicore processors. This is problematic for us as programmers because single-threaded code does not automatically run faster as a result of those extra cores.

Utilizing multiple cores is easy for most server applications, where each thread can independently handle a separate client request, but it’s more difficult on the desktop because it typically requires that you take your computationally intensive code and do the following:

Partition it into small chunks.

Execute those chunks in parallel via multithreading.

Collate the results as they become available, in a thread-safe and performant manner.

Although you can do all of this with the classic multithreading constructs, it’s awkward—particularly the steps of partitioning and collating. A further problem is that the usual strategy of locking for thread safety causes a lot of contention when many threads work on the same data at once.

The PFX libraries have been designed specifically to help in these scenarios.

NOTE
Programming to leverage multicores or multiple processors is called parallel programming. This is a subset of the broader concept of multithreading.

PFX Concepts
There are two strategies for partitioning work among threads: data parallelism and task parallelism.

When a set of tasks must be performed on many data values, we can parallelize by having each thread perform the (same) set of tasks on a subset of values. This is called data parallelism because we are partitioning the data between threads. In contrast, with task parallelism we partition the tasks; in other words, we have each thread perform a different task.

In general, data parallelism is easier and scales better to highly parallel hardware because it reduces or eliminates shared data (thereby reducing contention and thread-safety issues). Also, data parallelism exploits the fact that there are often more data values than discrete tasks, increasing the parallelism potential.

Data parallelism is also conducive to structured parallelism, which means that parallel work units start and finish in the same place in your program. In contrast, task parallelism tends to be unstructured, meaning that parallel work units may start and finish in places scattered across your program. Structured parallelism is simpler and less error prone and allows you to farm the difficult job of partitioning and thread coordination (and even result collation) out to libraries.

PFX Components
PFX comprises two layers of functionality, as shown in Figure 22-1. The higher layer consists of two structured data parallelism APIs: PLINQ and the Parallel class. The lower layer contains the task parallelism classes—plus a set of additional constructs to help with parallel programming activities.


Figure 22-1. PFX components
PLINQ offers the richest functionality: it automates all the steps of parallelization—including partitioning the work into tasks, executing those tasks on threads, and collating the results into a single output sequence. It’s called declarative—because you simply declare that you want to parallelize your work (which you structure as a LINQ query) and let the runtime take care of the implementation details. In contrast, the other approaches are imperative, in that you need to explicitly write code to partition or collate. As the following synopsis shows, in the case of the Parallel class, you must collate results yourself; with the task parallelism constructs, you must partition the work yourself, too:

Partitions work	Collates results
PLINQ	Yes	Yes
The Parallel class	Yes	No
PFX’s task parallelism	No	No
The concurrent collections and spinning primitives help you with lower-level parallel programming activities. These are important because PFX has been designed to work not only with today’s hardware, but also with future generations of processors with far more cores. If you want to move a pile of chopped wood and you have 32 workers to do the job, the biggest challenge is moving the wood without the workers getting in each other’s way. It’s the same with dividing an algorithm among 32 cores: if ordinary locks are used to protect common resources, the resultant blocking can mean that only a fraction of those cores are ever actually busy at once. The concurrent collections are tuned specifically for highly concurrent access, with the focus on minimizing or eliminating blocking. PLINQ and the Parallel class themselves rely on the concurrent collections and on spinning primitives for efficient management of work.

OTHER USES FOR PFX
The parallel programming constructs are useful not only for leveraging multicores, but also in other scenarios:

The concurrent collections are sometimes appropriate when you want a thread-safe queue, stack, or dictionary.

BlockingCollection provides an easy means to implement producer/consumer structures, and is a good way to limit concurrency.

Tasks are the basis of asynchronous programming, as we saw in Chapter 14.

When to Use PFX
The primary use case for PFX is parallel programming: leveraging multicore processors to speed up computationally intensive code.

A challenge in parallel programming is Amdahl’s law, which states that the maximum performance improvement from parallelization is governed by the portion of the code that must execute sequentially. For instance, if only two-thirds of an algorithm’s execution time is parallelizable, you can never exceed a threefold performance gain—even with an infinite number of cores.

So, before proceeding, it’s worth verifying that the bottleneck is in parallelizable code. It’s also worth considering whether your code needs to be computationally intensive—optimization is often the easiest and most effective approach. There’s a trade-off, though, in that some optimization techniques can make it more difficult to parallelize code.

The easiest gains come with what’s called embarrassingly parallel problems—this is when a job can be easily divided into tasks that efficiently execute on their own (structured parallelism is very well suited to such problems). Examples include many image-processing tasks, ray tracing, and brute-force approaches in mathematics or cryptography. An example of a non-embarrassingly parallel problem is implementing an optimized version of the quicksort algorithm—a good result takes some thought and might require unstructured parallelism.

PLINQ
PLINQ automatically parallelizes local LINQ queries. PLINQ has the advantage of being easy to use in that it offloads the burden of both work partitioning and result collation to .NET.

To use PLINQ, simply call AsParallel() on the input sequence and then continue the LINQ query as usual. The following query calculates the prime numbers between 3 and 100,000, making full use of all cores on the target machine:

// Calculate prime numbers using a simple (unoptimized) algorithm.

IEnumerable<int> numbers = Enumerable.Range (3, 100000-3);

var parallelQuery = 
  from n in numbers.AsParallel()
  where Enumerable.Range (2, (int) Math.Sqrt (n)).All (i => n % i > 0)
  select n;

int[] primes = parallelQuery.ToArray();
AsParallel is an extension method in System.Linq.ParallelEnumerable. It wraps the input in a sequence based on ParallelQuery<TSource>, which causes the LINQ query operators that you subsequently call to bind to an alternate set of extension methods defined in ParallelEnumerable. These provide parallel implementations of each of the standard query operators. Essentially, they work by partitioning the input sequence into chunks that execute on different threads, collating the results back into a single output sequence for consumption, as depicted in Figure 22-2.


Figure 22-2. PLINQ execution model
Calling AsSequential() unwraps a ParallelQuery sequence so that subsequent query operators bind to the standard query operators and execute sequentially. This is necessary before calling methods that have side effects or are not thread-safe.

For query operators that accept two input sequences (Join, GroupJoin, Concat, Union, Intersect, Except, and Zip), you must apply AsParallel() to both input sequences (otherwise, an exception is thrown). You don’t, however, need to keep applying AsParallel to a query as it progresses, because PLINQ’s query operators output another ParallelQuery sequence. In fact, calling AsParallel again introduces inefficiency in that it forces merging and repartitioning of the query:

mySequence.AsParallel()           // Wraps sequence in ParallelQuery<int>
          .Where (n => n > 100)   // Outputs another ParallelQuery<int>
          .AsParallel()           // Unnecessary - and inefficient!
          .Select (n => n * n)
Not all query operators can be effectively parallelized. For those that cannot (see “PLINQ Limitations”), PLINQ implements the operator sequentially, instead. PLINQ might also operate sequentially if it suspects that the overhead of parallelization will actually slow a particular query.

PLINQ is only for local collections: it doesn’t work with Entity Framework, for instance, because in those cases the LINQ translates into SQL, which then executes on a database server. However, you can use PLINQ to perform additional local querying on the result sets obtained from database queries.

WARNING
If a PLINQ query throws an exception, it’s rethrown as an AggregateException whose InnerExceptions property contains the real exception (or exceptions). For more details, see “Working with AggregateException”.

WHY ISN’T ASPARALLEL THE DEFAULT?
Given that AsParallel transparently parallelizes LINQ queries, the question arises: Why didn’t Microsoft simply parallelize the standard query operators and make PLINQ the default?

There are a number of reasons for the opt-in approach. First, for PLINQ to be useful, there must be a reasonable amount of computationally intensive work for it to farm out to worker threads. Most LINQ-to-Objects queries execute very quickly; thus, not only would parallelization be unnecessary, but the overhead of partitioning, collating, and coordinating the extra threads might actually slow things down.

Additionally:

The output of a PLINQ query (by default) can differ from a LINQ query with respect to element ordering (see “PLINQ and Ordering”).

PLINQ wraps exceptions in an AggregateException (to handle the possibility of multiple exceptions being thrown).

PLINQ will give unreliable results if the query invokes thread-unsafe methods.

Finally, PLINQ offers quite a few hooks for tuning and tweaking. Burdening the standard LINQ-to-Objects API with such nuances would add distraction.

Parallel Execution Ballistics
Like ordinary LINQ queries, PLINQ queries are lazily evaluated. This means that execution is triggered only when you begin consuming the results—typically via a foreach loop (although it can also be via a conversion operator such as ToArray or an operator that returns a single element or value).

As you enumerate the results, though, execution proceeds somewhat differently from that of an ordinary sequential query. A sequential query is powered entirely by the consumer in a “pull” fashion: each element from the input sequence is fetched exactly when required by the consumer. A parallel query ordinarily uses independent threads to fetch elements from the input sequence slightly ahead of when they’re needed by the consumer (rather like a teleprompter for newsreaders). It then processes the elements in parallel through the query chain, holding the results in a small buffer so that they’re ready for the consumer on demand. If the consumer pauses or breaks out of the enumeration early, the query processor also pauses or stops so as not to waste CPU time or memory.

NOTE
You can tweak PLINQ’s buffering behavior by calling WithMergeOptions after AsParallel. The default value of AutoBuffered generally gives the best overall results. NotBuffered disables the buffer and is useful if you want to see results as soon as possible; FullyBuffered caches the entire result set before presenting it to the consumer (the OrderBy and Reverse operators naturally work this way, as do the element, aggregation, and conversion operators).

PLINQ and Ordering
A side effect of parallelizing the query operators is that when the results are collated, it’s not necessarily in the same order that they were submitted (see Figure 22-2). In other words, LINQ’s normal order-preservation guarantee for sequences no longer holds.

If you need order preservation, you can force it by calling AsOrdered() after AsParallel():

myCollection.AsParallel().AsOrdered()...
Calling AsOrdered incurs a performance hit with large numbers of elements because PLINQ must keep track of each element’s original position.

You can negate the effect of AsOrdered later in a query by calling AsUnordered: this introduces a “random shuffle point,” which allows the query to execute more efficiently from that point on. So, if you wanted to preserve input-sequence ordering for just the first two query operators, you’d do this:

inputSequence.AsParallel().AsOrdered()
  .QueryOperator1()
  .QueryOperator2()
  .AsUnordered()       // From here on, ordering doesn’t matter
  .QueryOperator3()
  ...
AsOrdered is not the default because for most queries, the original input ordering doesn’t matter. In other words, if AsOrdered were the default, you’d need to apply AsUnordered to the majority of your parallel queries to get the best performance, which would be burdensome.

PLINQ Limitations
There are practical limitations on what PLINQ can parallelize. The following query operators prevent parallelization by default unless the source elements are in their original indexing position:

The indexed versions of Select, SelectMany, and ElementAt

Most query operators change the indexing position of elements (including those that remove elements, such as Where). This means that if you want to use the preceding operators, they’ll usually need to be at the start of the query.

The following query operators are parallelizable but use an expensive partitioning strategy that can sometimes be slower than sequential processing:

Join, GroupBy, GroupJoin, Distinct, Union, Intersect, and Except

The Aggregate operator’s seeded overloads in their standard incarnations are not parallelizable—PLINQ provides special overloads to deal with this (see “Optimizing PLINQ”).

All other operators are parallelizable, although use of these operators doesn’t guarantee that your query will be parallelized. PLINQ might run your query sequentially if it suspects that the overhead of parallelization will slow down that particular query. You can override this behavior and force parallelism by calling the following after AsParallel():

.WithExecutionMode (ParallelExecutionMode.ForceParallelism)
Example: Parallel Spellchecker
Suppose that we want to write a spellchecker that runs quickly with very large documents by utilizing all available cores. By formulating our algorithm into a LINQ query, we can very easily parallelize it.

The first step is to download a dictionary of English words into a HashSet for efficient lookup:

if (!File.Exists ("WordLookup.txt")    // Contains about 150,000 words
  File.WriteAllText ("WordLookup.txt",
    await new HttpClient().GetStringAsync (
      "http://www.albahari.com/ispell/allwords.txt"));

var wordLookup = new HashSet<string> (
  File.ReadAllLines ("WordLookup.txt"),
  StringComparer.InvariantCultureIgnoreCase);
We then use our word lookup to create a test “document” comprising an array of a million random words. After we build the array, let’s introduce a couple of spelling mistakes:

var random = new Random();
string[] wordList = wordLookup.ToArray();

string[] wordsToTest = Enumerable.Range (0, 1000000)
  .Select (i => wordList [random.Next (0, wordList.Length)])
  .ToArray();

wordsToTest [12345] = "woozsh";     // Introduce a couple
wordsToTest [23456] = "wubsie";     // of spelling mistakes.
Now we can perform our parallel spellcheck by testing wordsToTest against wordLookup. PLINQ makes this very easy:

var query = wordsToTest
  .AsParallel()
  .Select  ((word, index) => (word, index))
  .Where   (iword => !wordLookup.Contains (iword.word))
  .OrderBy (iword => iword.index);

foreach (var mistake in query)
  Console.WriteLine (mistake.word + " - index = " + mistake.index);

// OUTPUT:
// woozsh - index = 12345
// wubsie - index = 23456
The wordLookup.Contains method in the predicate gives the query some “meat” and makes it worth parallelizing.

NOTE
Notice that our query uses tuples (word, index) rather than anonymous types. Because tuples are implemented as value types rather than reference types, this improves peak memory consumption and performance by reducing heap allocations and subsequent garbage collections. (Benchmarking reveals the gains to be moderate in practice, due to the efficiency of the memory manager and the fact that the allocations in question don’t survive beyond Generation 0.)

Using ThreadLocal<T>
Let’s extend our example by parallelizing the creation of the random test-word list itself. We structured this as a LINQ query, so it should be easy. Here’s the sequential version:

string[] wordsToTest = Enumerable.Range (0, 1000000)
  .Select (i => wordList [random.Next (0, wordList.Length)])
  .ToArray();
Unfortunately, the call to random.Next is not thread-safe, so it’s not as simple as inserting AsParallel() into the query. A potential solution is to write a function that locks around random.Next; however, this would limit concurrency. The better option is to use ThreadLocal<Random> (see “Thread-Local Storage”) to create a separate Random object for each thread. We then can parallelize the query, as follows:

var localRandom = new ThreadLocal<Random>
 ( () => new Random (Guid.NewGuid().GetHashCode()) );

string[] wordsToTest = Enumerable.Range (0, 1000000).AsParallel()
  .Select (i => wordList [localRandom.Value.Next (0, wordList.Length)])
  .ToArray();
In our factory function for instantiating a Random object, we pass in a Guid’s hashcode to ensure that if two Random objects are created within a short period of time, they’ll yield different random number sequences.

WHEN TO USE PLINQ
It’s tempting to search your existing applications for LINQ queries and experiment with parallelizing them. This is usually unproductive, because most problems for which LINQ is obviously the best solution tend to execute very quickly and so don’t benefit from parallelization. A better approach is to find a CPU-intensive bottleneck and then consider whether it can be expressed as a LINQ query. (A welcome side effect of such restructuring is that LINQ typically makes code smaller and more readable.)

PLINQ is well suited to embarrassingly parallel problems. It can be a poor choice for imaging, however, because collating millions of pixels into an output sequence creates a bottleneck. Instead, it’s better to write pixels directly to an array or unmanaged memory block and use the Parallel class or task parallelism to manage the multithreading. (It is possible, however, to defeat result collation using ForAll—we discuss this in “Optimizing PLINQ”. Doing so makes sense if the image processing algorithm naturally lends itself to LINQ.)

Functional Purity
Because PLINQ runs your query on parallel threads, you must be careful not to perform thread-unsafe operations. In particular, writing to variables is side-effecting and therefore thread-unsafe:

// The following query multiplies each element by its position.
// Given an input of Enumerable.Range(0,999), it should output squares.
int i = 0;
var query = from n in Enumerable.Range(0,999).AsParallel() select n * i++;
We could make incrementing i thread-safe by using locks, but the problem would still remain that i won’t necessarily correspond to the position of the input element. And adding AsOrdered to the query wouldn’t fix the latter problem, because AsOrdered ensures only that the elements are output in an order consistent with them having been processed sequentially—it doesn’t actually process them sequentially.

The correct solution is to rewrite our query to use the indexed version of Select:

var query = Enumerable.Range(0,999).AsParallel().Select ((n, i) => n * i);
For best performance, any methods called from query operators should be thread-safe by virtue of not writing to fields or properties (non-side-effecting, or functionally pure). If they’re thread-safe by virtue of locking, the query’s parallelism potential will be limited by the effects of contention.

Setting the Degree of Parallelism
By default, PLINQ chooses an optimum degree of parallelism for the processor in use. You can override it by calling WithDegreeOfParallelism after AsParallel:

...AsParallel().WithDegreeOfParallelism(4)...
An example of when you might increase the parallelism beyond the core count is with I/O-bound work (downloading many web pages at once, for instance). However, task combinators and asynchronous functions provide a similarly easy and more efficient solution (see “Task Combinators”). Unlike with Tasks, PLINQ cannot perform I/O-bound work without blocking threads (and pooled threads, to make matters worse).

Changing the degree of parallelism
You can call WithDegreeOfParallelism only once within a PLINQ query. If you need to call it again, you must force merging and repartitioning of the query by calling AsParallel() again within the query:

"The Quick Brown Fox"
  .AsParallel().WithDegreeOfParallelism (2)
  .Where (c => !char.IsWhiteSpace (c))
  .AsParallel().WithDegreeOfParallelism (3)   // Forces Merge + Partition
  .Select (c => char.ToUpper (c))
Cancellation
Canceling a PLINQ query whose results you’re consuming in a foreach loop is easy: simply break out of the foreach and the query will be automatically canceled as the enumerator is implicitly disposed.

For a query that terminates with a conversion, element, or aggregation operator, you can cancel it from another thread via a cancellation token (see “Cancellation”). To insert a token, call WithCancellation after calling AsParallel, passing in the Token property of a CancellationTokenSource object. Another thread can then call Cancel on the token source (or we can call it ourselves with a delay). This then throws an OperationCanceledException on the query’s consumer:

IEnumerable<int> tenMillion = Enumerable.Range (3, 10_000_000);

var cancelSource = new CancellationTokenSource();
cancelSource.CancelAfter (100);   // Cancel query after 100 milliseconds

var primeNumberQuery = 
  from n in tenMillion.AsParallel().WithCancellation (cancelSource.Token)
  where Enumerable.Range (2, (int) Math.Sqrt (n)).All (i => n % i > 0)
  select n;

try 
{
  // Start query running:
  int[] primes = primeNumberQuery.ToArray();
  // We'll never get here because the other thread will cancel us.
}
catch (OperationCanceledException)
{
  Console.WriteLine ("Query canceled");
}
Upon cancellation, PLINQ waits for each worker thread to finish with its current element before ending the query. This means that any external methods that the query calls will run to completion.

Optimizing PLINQ
Output-side optimization
One of PLINQ’s advantages is that it conveniently collates the results from parallelized work into a single output sequence. Sometimes, though, all that you end up doing with that sequence is running some function once over each element:

foreach (int n in parallelQuery)
  DoSomething (n);
If this is the case—and you don’t care about the order in which the elements are processed—you can improve efficiency with PLINQ’s ForAll method.

The ForAll method runs a delegate over every output element of a ParallelQuery. It hooks directly into PLINQ’s internals, bypassing the steps of collating and enumerating the results. Here’s a trivial example:

"abcdef".AsParallel().Select (c => char.ToUpper(c)).ForAll (Console.Write);
Figure 22-3 shows the process.


Figure 22-3. PLINQ ForAll
NOTE
Collating and enumerating results is not a massively expensive operation, so the ForAll optimization yields the greatest gains when there are large numbers of quickly executing input elements.

Input-side optimization
PLINQ has three partitioning strategies for assigning input elements to threads:

Strategy	Element allocation	Relative performance
Chunk partitioning	Dynamic	Average
Range partitioning	Static	Poor to excellent
Hash partitioning	Static	Poor
For query operators that require comparing elements (GroupBy, Join, GroupJoin, Intersect, Except, Union, and Distinct), you have no choice: PLINQ always uses hash partitioning. Hash partitioning is relatively inefficient in that it must precalculate the hashcode of every element (so that elements with identical hashcodes can be processed on the same thread). If you find this to be too slow, your only option is to call AsSequential to disable parallelization.

For all other query operators, you have a choice as to whether to use range or chunk partitioning. By default:

If the input sequence is indexable (if it’s an array or implements IList<T>), PLINQ chooses range partitioning.

Otherwise, PLINQ chooses chunk partitioning.

In a nutshell, range partitioning is faster with long sequences for which every element takes a similar amount of CPU time to process. Otherwise, chunk partitioning is usually faster.

To force range partitioning:

If the query starts with Enumerable.Range, replace that method with ParallelEnumerable.Range.

Otherwise, simply call ToList or ToArray on the input sequence (obviously, this incurs a performance cost in itself, which you should take into account).

WARNING
ParallelEnumerable.Range is not simply a shortcut for calling Enumerable.Range(…).AsParallel(). It changes the performance of the query by activating range partitioning.

To force chunk partitioning, wrap the input sequence in a call to Partitioner.Create (in System.Collection.Concurrent), as follows:

int[] numbers = { 3, 4, 5, 6, 7, 8, 9 };
var parallelQuery =
  Partitioner.Create (numbers, true).AsParallel()
  .Where (...)
The second argument to Partitioner.Create indicates that you want to load-balance the query, which is another way of saying that you want chunk partitioning.

Chunk partitioning works by having each worker thread periodically grab small “chunks” of elements from the input sequence to process (see Figure 22-4). PLINQ starts by allocating very small chunks (one or two elements at a time). It then increases the chunk size as the query progresses: this ensures that small sequences are effectively parallelized and large sequences don’t cause excessive round-tripping. If a worker happens to get “easy” elements (that process quickly), it will end up getting more chunks. This system keeps every thread equally busy (and the cores “balanced”); the only downside is that fetching elements from the shared input sequence requires synchronization (typically an exclusive lock)—and this can result in some overhead and contention.

Range partitioning bypasses the normal input-side enumeration and preallocates an equal number of elements to each worker, avoiding contention on the input sequence. But if some threads happen to get easy elements and finish early, they sit idle while the remaining threads continue working. Our earlier prime number calculator might perform poorly with range partitioning. An example of when range partitioning would do well is in calculating the sum of the square roots of the first 10 million integers:

ParallelEnumerable.Range (1, 10000000).Sum (i => Math.Sqrt (i))

Figure 22-4. Chunk versus range partitioning
ParallelEnumerable.Range returns a ParallelQuery<T>, so you don’t need to subsequently call AsParallel.

NOTE
Range partitioning doesn’t necessarily allocate element ranges in contiguous blocks—it might instead choose a “striping” strategy. For instance, if there are two workers, one worker might process odd-numbered elements while the other processes even-numbered elements. The TakeWhile operator is almost certain to trigger a striping strategy to avoid unnecessarily processing elements later in the sequence.

Optimizing custom aggregations
PLINQ parallelizes the Sum, Average, Min, and Max operators efficiently without additional intervention. The Aggregate operator, though, presents special challenges for PLINQ. As described in Chapter 9, Aggregate performs custom aggregations. For example, the following sums a sequence of numbers, mimicking the Sum operator:

int[] numbers = { 1, 2, 3 };
int sum = numbers.Aggregate (0, (total, n) => total + n);   // 6
We also saw in Chapter 9 that for unseeded aggregations, the supplied delegate must be associative and commutative. PLINQ will give incorrect results if this rule is violated, because it draws multiple seeds from the input sequence in order to aggregate several partitions of the sequence simultaneously.

Explicitly seeded aggregations might seem like a safe option with PLINQ, but unfortunately these ordinarily execute sequentially because of the reliance on a single seed. To mitigate this, PLINQ provides another overload of Aggregate that lets you specify multiple seeds—or rather, a seed factory function. For each thread, it executes this function to generate a separate seed, which becomes a thread-local accumulator into which it locally aggregates elements.

You must also supply a function to indicate how to combine the local and main accumulators. Finally, this Aggregate overload (somewhat gratuitously) expects a delegate to perform any final transformation on the result (you can achieve this as easily by running some function on the result yourself afterward). So, here are the four delegates, in the order they are passed:

seedFactory
Returns a new local accumulator
updateAccumulatorFunc
Aggregates an element into a local accumulator
combineAccumulatorFunc
Combines a local accumulator with the main accumulator
resultSelector
Applies any final transformation on the end result
NOTE
In simple scenarios, you can specify a seed value instead of a seed factory. This tactic fails when the seed is a reference type that you want to mutate, because the same instance will then be shared by each thread.

To give a very simple example, the following sums the values in a numbers array:

numbers.AsParallel().Aggregate (
 () => 0,                                      // seedFactory
  (localTotal, n) => localTotal + n,           // updateAccumulatorFunc
  (mainTot, localTot) => mainTot + localTot,   // combineAccumulatorFunc
  finalResult => finalResult)                  // resultSelector
This example is contrived in that we could get the same answer just as efficiently using simpler approaches (such as an unseeded aggregate, or better, the Sum operator). To give a more realistic example, suppose that we want to calculate the frequency of each letter in the English alphabet in a given string. A simple sequential solution might look like this:

string text = "Let’s suppose this is a really long string";
var letterFrequencies = new int[26];
foreach (char c in text)
{
  int index = char.ToUpper (c) - 'A';
  if (index >= 0 && index < 26) letterFrequencies [index]++;
};
NOTE
An example of when the input text might be very long is in gene sequencing. The “alphabet” would then consist of the letters a, c, g, and t.

To parallelize this, we could replace the foreach statement with a call to Parallel.ForEach (which we cover in the following section), but this will leave us to deal with concurrency issues on the shared array. And locking around accessing that array would all but kill the potential for parallelization.

Aggregate offers a tidy solution. The accumulator, in this case, is an array just like the letterFrequencies array in our preceding example. Here’s a sequential version using Aggregate:

int[] result =
  text.Aggregate (
    new int[26],                // Create the "accumulator"
    (letterFrequencies, c) =>   // Aggregate a letter into the accumulator
    {
      int index = char.ToUpper (c) - 'A';
      if (index >= 0 && index < 26) letterFrequencies [index]++;
      return letterFrequencies;
    });
And now the parallel version, using PLINQ’s special overload:

int[] result =
  text.AsParallel().Aggregate (
   () => new int[26],             // Create a new local accumulator

    (localFrequencies, c) =>       // Aggregate into the local accumulator
    {
      int index = char.ToUpper (c) - 'A';
      if (index >= 0 && index < 26) localFrequencies [index]++;
      return localFrequencies;
    },
                                   // Aggregate local->main accumulator
    (mainFreq, localFreq) =>
      mainFreq.Zip (localFreq, (f1, f2) => f1 + f2).ToArray(),

    finalResult => finalResult     // Perform any final transformation
  );                               // on the end result.
Notice that the local accumulation function mutates the localFrequencies array. This ability to perform this optimization is important—and is legitimate because localFrequencies is local to each thread.

The Parallel Class
PFX provides a basic form of structured parallelism via three static methods in the Parallel class:

Parallel.Invoke
Executes an array of delegates in parallel
Parallel.For
Performs the parallel equivalent of a C# for loop
Parallel.ForEach
Performs the parallel equivalent of a C# foreach loop
All three methods block until all work is complete. As with PLINQ, after an unhandled exception, remaining workers are stopped after their current iteration and the exception (or exceptions) are thrown back to the caller—wrapped in an AggregateException (see “Working with AggregateException”).

Parallel.Invoke
Parallel.Invoke executes an array of Action delegates in parallel and then waits for them to complete. The simplest version of the method is defined as follows:

public static void Invoke (params Action[] actions);
Just as with PLINQ, the Parallel.* methods are optimized for compute-bound and not I/O-bound work. However, downloading two web pages at once provides a simple way to demonstrate Parallel.Invoke:

Parallel.Invoke (
 () => new WebClient().DownloadFile ("http://www.linqpad.net", "lp.html"),
 () => new WebClient().DownloadFile ("http://microsoft.com", "ms.html"));
On the surface, this seems like a convenient shortcut for creating and waiting on two thread-bound Task objects. But there’s an important difference: Parallel.Invoke still works efficiently if you pass in an array of a million delegates. This is because it partitions large numbers of elements into batches that it assigns to a handful of underlying Tasks rather than creating a separate Task for each delegate.

As with all of Parallel’s methods, you’re on your own when it comes to collating the results. This means that you need to keep thread safety in mind. The following, for instance, is thread-unsafe:

var data = new List<string>();
Parallel.Invoke (
 () => data.Add (new WebClient().DownloadString ("http://www.foo.com")),
 () => data.Add (new WebClient().DownloadString ("http://www.far.com")));
Locking around adding to the list would resolve this, although locking would create a bottleneck if you had a much larger array of quickly executing delegates. A better solution is to use the thread-safe collections, which we cover in later sections—ConcurrentBag would be ideal in this case.

Parallel.Invoke is also overloaded to accept a ParallelOptions object:

public static void Invoke (ParallelOptions options,
                           params Action[] actions);
With ParallelOptions, you can insert a cancellation token, limit the maximum concurrency, and specify a custom task scheduler. A cancellation token is relevant when you’re executing (roughly) more tasks than you have cores: upon cancellation, any unstarted delegates will be abandoned. Any already executing delegates will, however, continue to completion. See “Cancellation” for an example of how to use cancellation tokens.

Parallel.For and Parallel.ForEach
Parallel.For and Parallel.ForEach perform the equivalent of a C# for and foreach loop but with each iteration executing in parallel instead of sequentially. Here are their (simplest) signatures:

public static ParallelLoopResult For (
  int fromInclusive, int toExclusive, Action<int> body)

public static ParallelLoopResult ForEach<TSource> (
  IEnumerable<TSource> source, Action<TSource> body)
This sequential for loop:

for (int i = 0; i < 100; i++)
  Foo (i);
is parallelized like this:

Parallel.For (0, 100, i => Foo (i));
or more simply:

Parallel.For (0, 100, Foo);
And this sequential foreach:

foreach (char c in "Hello, world")
  Foo (c);
is parallelized like this:

Parallel.ForEach ("Hello, world", Foo);
To give a practical example, if we import the System.Security.Cryptography namespace, we can generate six public/private keypair strings in parallel, as follows:

var keyPairs = new string[6];

Parallel.For (0, keyPairs.Length,
              i => keyPairs[i] = RSA.Create().ToXmlString (true));
As with Parallel.Invoke, we can feed Parallel.For and Parallel.ForEach a large number of work items and they’ll be efficiently partitioned onto a few tasks.

NOTE
The latter query could also be done with PLINQ:

string[] keyPairs =
  ParallelEnumerable.Range (0, 6)
  .Select (i => RSA.Create().ToXmlString (true))
  .ToArray();
Outer versus inner loops
Parallel.For and Parallel.ForEach usually work best on outer rather than inner loops. This is because with the former, you’re offering larger chunks of work to parallelize, diluting the management overhead. Parallelizing both inner and outer loops is usually unnecessary.

In the following example, we’d typically need more than 100 cores to benefit from the inner parallelization:

Parallel.For (0, 100, i =>
{
  Parallel.For (0, 50, j => Foo (i, j));   // Sequential would be better
});                                        // for the inner loop.
Indexed Parallel.ForEach
Sometimes, it’s useful to know the loop iteration index. With a sequential foreach, it’s easy:

int i = 0;
foreach (char c in "Hello, world")
  Console.WriteLine (c.ToString() + i++);
Incrementing a shared variable, however, is not thread-safe in a parallel context. You must instead use the following version of ForEach:

public static ParallelLoopResult ForEach<TSource> (
  IEnumerable<TSource> source, Action<TSource,ParallelLoopState,long> body)
We’ll ignore ParallelLoopState (which we cover in the following section). For now, we’re interested in Action’s third type parameter of type long, which indicates the loop index:

Parallel.ForEach ("Hello, world", (c, state, i) =>
{
   Console.WriteLine (c.ToString() + i);
});
To put this into a practical context, let’s revisit the spellchecker that we wrote with PLINQ. The following code loads up a dictionary along with an array of a million words to test:

if (!File.Exists ("WordLookup.txt"))    // Contains about 150,000 words
  new WebClient().DownloadFile (
    "http://www.albahari.com/ispell/allwords.txt", "WordLookup.txt");

var wordLookup = new HashSet<string> (
  File.ReadAllLines ("WordLookup.txt"),
  StringComparer.InvariantCultureIgnoreCase);

var random = new Random();
string[] wordList = wordLookup.ToArray();

string[] wordsToTest = Enumerable.Range (0, 1000000)
  .Select (i => wordList [random.Next (0, wordList.Length)])
  .ToArray();

wordsToTest [12345] = "woozsh";     // Introduce a couple
wordsToTest [23456] = "wubsie";     // of spelling mistakes.
We can perform the spellcheck on our wordsToTest array using the indexed version of Parallel.ForEach, as follows:

var misspellings = new ConcurrentBag<Tuple<int,string>>();

Parallel.ForEach (wordsToTest, (word, state, i) =>
{
  if (!wordLookup.Contains (word))
    misspellings.Add (Tuple.Create ((int) i, word));
});
Notice that we had to collate the results into a thread-safe collection: having to do this is the disadvantage when compared to using PLINQ. The advantage over PLINQ is that we avoid the cost of applying an indexed Select query operator—which is less efficient than an indexed ForEach.

ParallelLoopState: breaking early out of loops
Because the loop body in a parallel For or ForEach is a delegate, you can’t exit the loop early with a break statement. Instead, you must call Break or Stop on a ParallelLoopState object:

public class ParallelLoopState
{
  public void Break();
  public void Stop();

  public bool IsExceptional { get; }
  public bool IsStopped { get; }
  public long? LowestBreakIteration { get; }
  public bool ShouldExitCurrentIteration { get; }
}
Obtaining a ParallelLoopState is easy: all versions of For and ForEach are overloaded to accept loop bodies of type Action<TSource,ParallelLoopState>. So, to parallelize this:

foreach (char c in "Hello, world")
  if (c == ',')
    break;
  else
    Console.Write (c);
do this:

Parallel.ForEach ("Hello, world", (c, loopState) =>
{
  if (c == ',')
    loopState.Break();
  else
    Console.Write (c);
});

// OUTPUT: Hlloe
You can see from the output that loop bodies can complete in a random order. Aside from this difference, calling Break yields at least the same elements as executing the loop sequentially: this example will always output at least the letters H, e, l, l, and o in some order. In contrast, calling Stop instead of Break forces all threads to finish immediately after their current iteration. In our example, calling Stop could give us a subset of the letters H, e, l, l, and o if another thread were lagging behind. Calling Stop is useful when you’ve found something that you’re looking for—or when something has gone wrong and you won’t be looking at the results.

NOTE
The Parallel.For and Parallel.ForEach methods return a ParallelLoopResult object that exposes properties called IsCompleted and LowestBreakIteration. These tell you whether the loop ran to completion; if it didn’t, it indicates at what cycle the loop was broken.

If LowestBreakIteration returns null, it means that you called Stop (rather than Break) on the loop.

If your loop body is long, you might want other threads to break partway through the method body in case of an early Break or Stop. You can do this by polling the ShouldExitCurrentIteration property at various places in your code; this property becomes true immediately after a Stop—or soon after a Break.

NOTE
ShouldExitCurrentIteration also becomes true after a cancellation request—or if an exception is thrown in the loop.

IsExceptional lets you know whether an exception has occurred on another thread. Any unhandled exception will cause the loop to stop after each thread’s current iteration: to avoid this, you must explicitly handle exceptions in your code.

Optimization with local values
Parallel.For and Parallel.ForEach each offer a set of overloads that feature a generic type argument called TLocal. These overloads are designed to help you optimize the collation of data with iteration-intensive loops. The simplest is this:

public static ParallelLoopResult For <TLocal> (
  int fromInclusive,
  int toExclusive,
  Func <TLocal> localInit,
  Func <int, ParallelLoopState, TLocal, TLocal> body,
  Action <TLocal> localFinally);
These methods are rarely needed in practice because their target scenarios are covered mostly by PLINQ (which is fortunate because these overloads are somewhat intimidating!).

Essentially, the problem is this: suppose that we want to sum the square roots of the numbers 1 through 10,000,000. Calculating 10 million square roots is easily parallelizable, but summing their values is troublesome because we must lock around updating the total:

object locker = new object();
double total = 0;
Parallel.For (1, 10000000,
              i => { lock (locker) total += Math.Sqrt (i); });
The gain from parallelization is more than offset by the cost of obtaining 10 million locks—plus the resultant blocking.

The reality, though, is that we don’t actually need 10 million locks. Imagine a team of volunteers picking up a large volume of litter. If all workers shared a single trash can, the travel and contention would make the process extremely inefficient. The obvious solution is for each worker to have a private or “local” trash can, which is occasionally emptied into the main bin.

The TLocal versions of For and ForEach work in exactly this way. The volunteers are internal worker threads, and the local value represents a local trash can. For Parallel to do this job, you must feed it two additional delegates that indicate the following:

How to initialize a new local value

How to combine a local aggregation with the master value

Additionally, instead of the body delegate returning void, it should return the new aggregate for the local value. Here’s our example refactored:

object locker = new object();
double grandTotal = 0;

Parallel.For (1, 10000000,

  () => 0.0,                        // Initialize the local value.

  (i, state, localTotal) =>         // Body delegate. Notice that it
     localTotal + Math.Sqrt (i),    // returns the new local total.

  localTotal =>                                    // Add the local value
    { lock (locker) grandTotal += localTotal; }    // to the master value.
);
We must still lock, but only around aggregating the local value to the grand total. This makes the process dramatically more efficient.

NOTE
As stated earlier, PLINQ is often a good fit in these scenarios. Our example could be parallelized with PLINQ like this:

ParallelEnumerable.Range (1, 10000000)
                  .Sum (i => Math.Sqrt (i))
(Notice that we used ParallelEnumerable to force range partitioning: this improves performance in this case because all numbers will take equally long to process.)

In more complex scenarios, you might use LINQ’s Aggregate operator instead of Sum. If you supplied a local seed factory, the situation would be somewhat analogous to providing a local value function with Parallel.For.

Task Parallelism
Task parallelism is the lowest-level approach to parallelization with PFX. The classes for working at this level are defined in the System.Threading.Tasks namespace and comprise the following:

Class	Purpose
Task	For managing a unit for work
Task<TResult>	For managing a unit for work with a return value
TaskFactory	For creating tasks
TaskFactory<TResult>	For creating tasks and continuations with the same return type
TaskScheduler	For managing the scheduling of tasks
TaskCompletionSource	For manually controlling a task’s workflow
We covered the basics of tasks in Chapter 14; in this section, we look at advanced features of tasks that are aimed at parallel programming:

Tuning a task’s scheduling

Establish a parent/child relationship when one task is started from another

Advanced use of continuations

TaskFactory

WARNING
The Task Parallel Library lets you create hundreds (or even thousands) of tasks with minimal overhead. But if you want to create millions of tasks, you’ll need to partition those tasks into larger work units to maintain efficiency. The Parallel class and PLINQ do this automatically.

NOTE
Visual Studio provides a window for monitoring tasks (Debug®Window®Parallel Tasks). This is equivalent to the Threads window, but for tasks. The Parallel Stacks window also has a special mode for tasks.

Creating and Starting Tasks
As described in Chapter 14, Task.Run creates and starts a Task or Task<TResult>. This method is actually a shortcut for calling Task.Factory.StartNew, which allows greater flexibility through additional overloads.

Specifying a state object
Task.Factory.StartNew lets you specify a state object that is passed to the target. The target method’s signature must then comprise a single object-type parameter:

var task = Task.Factory.StartNew (Greet, "Hello");
task.Wait();  // Wait for task to complete.

void Greet (object state) { Console.Write (state); }   // Hello
This avoids the cost of the closure required for executing a lambda expression that calls Greet. This is a micro-optimization and is rarely necessary in practice, so we can put the state object to better use, which is to assign a meaningful name to the task. We can then use the AsyncState property to query its name:

var task = Task.Factory.StartNew (state => Greet ("Hello"), "Greeting");
Console.WriteLine (task.AsyncState);   // Greeting
task.Wait();

void Greet (string message) { Console.Write (message); }
NOTE
Visual Studio displays each task’s AsyncState in the Parallel Tasks window, so having a meaningful name here can ease debugging considerably.

TaskCreationOptions
You can tune a task’s execution by specifying a TaskCreationOptions enum when calling StartNew (or instantiating a Task). TaskCreationOptions is a flags enum with the following (combinable) values:

LongRunning, PreferFairness, AttachedToParent
LongRunning suggests to the scheduler to dedicate a thread to the task, and as we described in Chapter 14, this is beneficial for I/O-bound tasks and for long-running tasks that might otherwise force short-running tasks to wait an unreasonable amount of time before being scheduled.

PreferFairness instructs the scheduler to try to ensure that tasks are scheduled in the order in which they were started. It might ordinarily do otherwise because it internally optimizes the scheduling of tasks using local work-stealing queues—an optimization that allows the creation of child tasks without incurring the contention overhead that would otherwise arise with a single work queue. A child task is created by specifying AttachedToParent.

Child tasks
When one task starts another, you can optionally establish a parent-child relationship:

Task parent = Task.Factory.StartNew (() =>
{
  Console.WriteLine ("I am a parent");

  Task.Factory.StartNew (() =>        // Detached task
  {
    Console.WriteLine ("I am detached");
  });

  Task.Factory.StartNew (() =>        // Child task
  {
    Console.WriteLine ("I am a child");
  }, TaskCreationOptions.AttachedToParent);
});
A child task is special in that when you wait for the parent task to complete, it waits for any children, as well. At which point any child exceptions bubble up:

TaskCreationOptions atp = TaskCreationOptions.AttachedToParent;
var parent = Task.Factory.StartNew (() => 
{
  Task.Factory.StartNew (() =>   // Child
  {
    Task.Factory.StartNew (() => { throw null; }, atp);   // Grandchild
  }, atp);
});

// The following call throws a NullReferenceException (wrapped
// in nested AggregateExceptions):
parent.Wait();
This can be particularly useful when a child task is a continuation, as you’ll see shortly.

Waiting on Multiple Tasks
We saw in Chapter 14 that you can wait on a single task either by calling its Wait method or by accessing its Result property (if it’s a Task<TResult>). You can also wait on multiple tasks at once—via the static methods Task.WaitAll (waits for all the specified tasks to finish) and Task.WaitAny (waits for just one task to finish).

WaitAll is similar to waiting out each task in turn, but is more efficient in that it requires (at most) just one context switch. Also, if one or more of the tasks throw an unhandled exception, WaitAll still waits out every task. It then rethrows an AggregateException that accumulates the exceptions from each faulted task (this is where AggregateException is genuinely useful). It’s equivalent to doing this:

// Assume t1, t2 and t3 are tasks:
var exceptions = new List<Exception>();
try { t1.Wait(); } catch (AggregateException ex) { exceptions.Add (ex); }
try { t2.Wait(); } catch (AggregateException ex) { exceptions.Add (ex); }
try { t3.Wait(); } catch (AggregateException ex) { exceptions.Add (ex); }
if (exceptions.Count > 0) throw new AggregateException (exceptions);
Calling WaitAny is equivalent to waiting on a ManualResetEventSlim that’s signaled by each task as it finishes.

As well as a timeout, you can also pass in a cancellation token to the Wait methods: this lets you cancel the wait—not the task itself.

Canceling Tasks
You can optionally pass in a cancellation token when starting a task. Then, if cancellation occurs via that token, the task itself enters the “Canceled” state:

var cts = new CancellationTokenSource();
CancellationToken token = cts.Token;
cts.CancelAfter (500);

Task task = Task.Factory.StartNew (() => 
{
  Thread.Sleep (1000);
  token.ThrowIfCancellationRequested();  // Check for cancellation request
}, token);

try { task.Wait(); }
catch (AggregateException ex)
{
  Console.WriteLine (ex.InnerException is TaskCanceledException);  // True
  Console.WriteLine (task.IsCanceled);                             // True
  Console.WriteLine (task.Status);                             // Canceled
}
TaskCanceledException is a subclass of OperationCanceledException. If you want to explicitly throw an OperationCanceledException (rather than calling token.ThrowIfCancellationRequested), you must pass the cancellation token into OperationCanceledException’s constructor. If you fail to do this, the task won’t end up with a TaskStatus.Canceled status and won’t trigger OnlyOnCanceled continuations.

If the task is canceled before it has started, it won’t get scheduled—an OperationCanceledException will instead be thrown on the task immediately.

Because cancellation tokens are recognized by other APIs, you can pass them into other constructs and cancellations will propagate seamlessly:

var cancelSource = new CancellationTokenSource();
CancellationToken token = cancelSource.Token;

Task task = Task.Factory.StartNew (() =>
{
  // Pass our cancellation token into a PLINQ query:
  var query = someSequence.AsParallel().WithCancellation (token)...
  ... enumerate query ...
});
Calling Cancel on cancelSource in this example will cancel the PLINQ query, which will throw an OperationCanceledException on the task body, which will then cancel the task.

NOTE
The cancellation tokens that you can pass into methods such as Wait and CancelAndWait allow you to cancel the wait operation and not the task itself.

Continuations
The ContinueWith method executes a delegate immediately after a task ends:

Task task1 = Task.Factory.StartNew (() => Console.Write ("antecedent.."));
Task task2 = task1.ContinueWith (ant => Console.Write ("..continuation"));
As soon as task1 (the antecedent) completes, fails, or is canceled, task2 (the continuation) starts. (If task1 had completed before the second line of code ran, task2 would be scheduled to execute immediately.) The ant argument passed to the continuation’s lambda expression is a reference to the antecedent task. ContinueWith itself returns a task, making it easy to add further continuations.

By default, antecedent and continuation tasks may execute on different threads. You can force them to execute on the same thread by specifying TaskContinuatio⁠nOptions.ExecuteSynchronously when calling ContinueWith: this can improve performance in very fine-grained continuations by lessening indirection.

Continuations and Task<TResult>
Just like ordinary tasks, continuations can be of type Task<TResult> and return data. In the following example, we calculate Math.Sqrt(8*2) using a series of chained tasks and then write out the result:

Task.Factory.StartNew<int> (() => 8)
  .ContinueWith (ant => ant.Result * 2)
  .ContinueWith (ant => Math.Sqrt (ant.Result))
  .ContinueWith (ant => Console.WriteLine (ant.Result));   // 4
Our example is somewhat contrived for simplicity; in real life, these lambda expressions would call computationally intensive functions.

Continuations and exceptions
A continuation can know whether an antecedent faulted by querying the antecedent task’s Exception property—or simply by invoking Result / Wait and catching the resultant AggregateException. If an antecedent faults and the continuation does neither, the exception is considered unobserved and the static TaskScheduler.Unob⁠servedTaskException event fires when the task is later garbage-collected.

A safe pattern is to rethrow antecedent exceptions. As long as the continuation is Waited upon, the exception will be propagated and rethrown to the Waiter:

Task continuation = Task.Factory.StartNew     (()  => { throw null; })
                                .ContinueWith (ant =>
  {
    ant.Wait();
    // Continue processing...
  });

continuation.Wait();    // Exception is now thrown back to caller.
Another way to deal with exceptions is to specify different continuations for exceptional versus nonexceptional outcomes. This is done with TaskContinuationOptions:

Task task1 = Task.Factory.StartNew (() => { throw null; });

Task error = task1.ContinueWith (ant => Console.Write (ant.Exception),
                                 TaskContinuationOptions.OnlyOnFaulted);

Task ok = task1.ContinueWith (ant => Console.Write ("Success!"),
                              TaskContinuationOptions.NotOnFaulted);
This pattern is particularly useful in conjunction with child tasks, as you’ll see very soon.

The following extension method “swallows” a task’s unhandled exceptions:

public static void IgnoreExceptions (this Task task)
{
  task.ContinueWith (t => { var ignore = t.Exception; },
    TaskContinuationOptions.OnlyOnFaulted);
}
(This could be improved by adding code to log the exception.) Here’s how it would be used:

Task.Factory.StartNew (() => { throw null; }).IgnoreExceptions();
Continuations and child tasks
A powerful feature of continuations is that they kick off only when all child tasks have completed (see Figure 22-5). At that point, any exceptions thrown by the children are marshaled to the continuation.

In the following example, we start three child tasks, each throwing a NullReferen⁠ceException. We then catch all of them in one fell swoop via a continuation on the parent:

TaskCreationOptions atp = TaskCreationOptions.AttachedToParent;
Task.Factory.StartNew (() =>
{
  Task.Factory.StartNew (() => { throw null; }, atp);
  Task.Factory.StartNew (() => { throw null; }, atp);
  Task.Factory.StartNew (() => { throw null; }, atp);
})
.ContinueWith (p => Console.WriteLine (p.Exception),
                    TaskContinuationOptions.OnlyOnFaulted);

Figure 22-5. Continuations
Conditional continuations
By default, a continuation is scheduled unconditionally, whether the antecedent completes, throws an exception, or is canceled. You can alter this behavior via a set of (combinable) flags included within the TaskContinuationOptions enum. Following are the three core flags that control conditional continuation:

NotOnRanToCompletion = 0x10000,
NotOnFaulted = 0x20000,
NotOnCanceled = 0x40000,
These flags are subtractive in the sense that the more you apply, the less likely the continuation is to execute. For convenience, there are also the following precombined values:

OnlyOnRanToCompletion = NotOnFaulted | NotOnCanceled,
OnlyOnFaulted = NotOnRanToCompletion | NotOnCanceled,
OnlyOnCanceled = NotOnRanToCompletion | NotOnFaulted
(Combining all the Not* flags [NotOnRanToCompletion, NotOnFaulted, NotOnCan⁠celed] is nonsensical because it would result in the continuation always being canceled.)

“RanToCompletion” means that the antecedent succeeded without cancellation or unhandled exceptions.

“Faulted” means that an unhandled exception was thrown on the antecedent.

“Canceled” means one of two things:

The antecedent was canceled via its cancellation token. In other words, an OperationCanceledException was thrown on the antecedent, whose CancellationToken property matched that passed to the antecedent when it was started.

The antecedent was implicitly canceled because it didn’t satisfy a conditional continuation predicate.

It’s essential to grasp that when a continuation doesn’t execute by virtue of these flags, the continuation is not forgotten or abandoned—it’s canceled. This means that any continuations on the continuation itself will then run unless you predicate them with NotOnCanceled. For example, consider this:

Task t1 = Task.Factory.StartNew (...);

Task fault = t1.ContinueWith (ant => Console.WriteLine ("fault"),
                              TaskContinuationOptions.OnlyOnFaulted);

Task t3 = fault.ContinueWith (ant => Console.WriteLine ("t3"));
As it stands, t3 will always get scheduled—even if t1 doesn’t throw an exception (see Figure 22-6). This is because if t1 succeeds, the fault task will be canceled, and with no continuation restrictions placed on t3, t3 will then execute unconditionally.

If we want t3 to execute only if fault actually runs, we must instead do this:

Task t3 = fault.ContinueWith (ant => Console.WriteLine ("t3"),
                              TaskContinuationOptions.NotOnCanceled);
(Alternatively, we could specify OnlyOnRanToCompletion; the difference is that t3 would not then execute if an exception were thrown within fault.)


Figure 22-6. Conditional continuations
Continuations with multiple antecedents
You can schedule continuation to execute based on the completion of multiple antecedents with the ContinueWhenAll and ContinueWhenAny methods in the TaskFactory class. These methods have become redundant, however, with the introduction of the task combinators discussed in Chapter 14 (WhenAll and WhenAny). Specifically, given the following tasks:

var task1 = Task.Run (() => Console.Write ("X"));
var task2 = Task.Run (() => Console.Write ("Y"));
we can schedule a continuation to execute when both complete as follows:

var continuation = Task.Factory.ContinueWhenAll (
  new[] { task1, task2 }, tasks => Console.WriteLine ("Done"));
Here’s the same result with the WhenAll task combinator:

var continuation = Task.WhenAll (task1, task2)
                       .ContinueWith (ant => Console.WriteLine ("Done"));
Multiple continuations on a single antecedent
Calling ContinueWith more than once on the same task creates multiple continuations on a single antecedent. When the antecedent finishes, all continuations will start together (unless you specify TaskContinuationOptions.ExecuteSynchronously, in which case the continuations will execute sequentially).

The following waits for one second and then writes either XY or YX:

var t = Task.Factory.StartNew (() => Thread.Sleep (1000));
t.ContinueWith (ant => Console.Write ("X"));
t.ContinueWith (ant => Console.Write ("Y"));
Task Schedulers
A task scheduler allocates tasks to threads and is represented by the abstract TaskScheduler class. .NET provides two concrete implementations: the default scheduler that works in tandem with the CLR thread pool, and the synchronization context scheduler. The latter is designed (primarily) to help you with the threading model of WPF and Windows Forms, which requires that user interface elements and controls are accessed only from the thread that created them (see “Threading in Rich Client Applications”). By capturing it, we can instruct a task or a continuation to execute on this context:

// Suppose we are on a UI thread in a Windows Forms / WPF application:
_uiScheduler = TaskScheduler.FromCurrentSynchronizationContext();
Assuming Foo is a compute-bound method that returns a string and lblResult is a WPF or Windows Forms label, we could then safely update the label after the operation completes, as follows:

Task.Run (() => Foo())
  .ContinueWith (ant => lblResult.Content = ant.Result, _uiScheduler);
Of course, C#’s asynchronous functions would more commonly be used for this kind of thing.

It’s also possible to write our own task scheduler (by subclassing TaskScheduler), although this is something you’d do only in very specialized scenarios. For custom scheduling, you’d more commonly use TaskCompletionSource.

TaskFactory
When you call Task.Factory, you’re calling a static property on Task that returns a default TaskFactory object. The purpose of a task factory is to create tasks; specifically, three kinds of tasks:

“Ordinary” tasks (via StartNew)

Continuations with multiple antecedents (via ContinueWhenAll and ContinueWhenAny)

Tasks that wrap methods that follow the defunct APM (via FromAsync; see “Obsolete Patterns”)

Another way to create tasks is to instantiate Task and call Start. However, this lets you create only “ordinary” tasks, not continuations.

Creating your own task factories
TaskFactory is not an abstract factory: you can actually instantiate the class, and this is useful when you want to repeatedly create tasks using the same (nonstandard) values for TaskCreationOptions, TaskContinuationOptions, or TaskScheduler. For example, if we want to repeatedly create long-running parented tasks, we could create a custom factory, as follows:

var factory = new TaskFactory (
  TaskCreationOptions.LongRunning | TaskCreationOptions.AttachedToParent,
  TaskContinuationOptions.None);
Creating tasks is then simply a matter of calling StartNew on the factory:

Task task1 = factory.StartNew (Method1);
Task task2 = factory.StartNew (Method2);
...
The custom continuation options are applied when calling ContinueWhenAll and ContinueWhenAny.

Working with AggregateException
As we’ve seen, PLINQ, the Parallel class, and Tasks automatically marshal exceptions to the consumer. To see why this is essential, consider the following LINQ query, which throws a DivideByZeroException on the first iteration:

try
{
  var query = from i in Enumerable.Range (0, 1000000)
              select 100 / i;
  ...
}
catch (DivideByZeroException)
{
  ...
}
If we asked PLINQ to parallelize this query and it ignored the handling of exceptions, a DivideByZeroException would probably be thrown on a separate thread, bypassing our catch block and causing the application to die.

Hence, exceptions are automatically caught and rethrown to the caller. But unfortunately, it’s not quite as simple as catching a DivideByZeroException. Because these libraries utilize many threads, it’s actually possible for two or more exceptions to be thrown simultaneously. To ensure that all exceptions are reported, exceptions are therefore wrapped in an AggregateException container, which exposes an InnerExceptions property containing each of the caught exception(s):

try
{
  var query = from i in ParallelEnumerable.Range (0, 1000000)
              select 100 / i;
  // Enumerate query
  ...
}
catch (AggregateException aex)
{
  foreach (Exception ex in aex.InnerExceptions)
    Console.WriteLine (ex.Message);
}
NOTE
Both PLINQ and the Parallel class end the query or loop execution upon encountering the first exception—by not processing any further elements or loop bodies. More exceptions might be thrown, however, before the current cycle is complete. The first exception in AggregateException is visible in the InnerException property.

Flatten and Handle
The AggregateException class provides a couple of methods to simplify exception handling: Flatten and Handle.

Flatten
AggregateExceptions will quite often contain other AggregateExceptions. An example of when this might happen is if a child task throws an exception. You can eliminate any level of nesting to simplify handling by calling Flatten. This method returns a new AggregateException with a simple flat list of inner exceptions:

catch (AggregateException aex)
{
  foreach (Exception ex in aex.Flatten().InnerExceptions)
    myLogWriter.LogException (ex);
}
Handle
Sometimes, it’s useful to catch only specific exception types, and have other types rethrown. The Handle method on AggregateException provides a shortcut for doing this. It accepts an exception predicate which it runs over every inner exception:

public void Handle (Func<Exception, bool> predicate)
If the predicate returns true, it considers that exception “handled.” After the delegate has run over every exception, the following happens:

If all exceptions were “handled” (the delegate returned true), the exception is not rethrown.

If there were any exceptions for which the delegate returned false (“unhandled”), a new AggregateException is built up containing those exceptions and is rethrown.

For instance, the following ends up rethrowing another AggregateException that contains a single NullReferenceException:

var parent = Task.Factory.StartNew (() => 
{
  // We’ll throw 3 exceptions at once using 3 child tasks:

  int[] numbers = { 0 };

  var childFactory = new TaskFactory
   (TaskCreationOptions.AttachedToParent, TaskContinuationOptions.None);

  childFactory.StartNew (() => 5 / numbers[0]);   // Division by zero
  childFactory.StartNew (() => numbers [1]);      // Index out of range
  childFactory.StartNew (() => { throw null; });  // Null reference
});

try { parent.Wait(); }
catch (AggregateException aex)
{
  aex.Flatten().Handle (ex =>   // Note that we still need to call Flatten
  {
    if (ex is DivideByZeroException)
    {
      Console.WriteLine ("Divide by zero");
      return true;                           // This exception is "handled"
    }
    if (ex is IndexOutOfRangeException)
    {
      Console.WriteLine ("Index out of range");
      return true;                           // This exception is "handled"   
    }
    return false;    // All other exceptions will get rethrown
  });
}
Concurrent Collections
.NET offers thread-safe collections in the System.Collections.Concurrent namespace:

Concurrent collection	Nonconcurrent equivalent
ConcurrentStack<T>	Stack<T>
ConcurrentQueue<T>	Queue<T>
ConcurrentBag<T>	(none)
ConcurrentDictionary<TKey,TValue>	Dictionary<TKey,TValue>
The concurrent collections are optimized for high-concurrency scenarios; however, they can also be useful whenever you need a thread-safe collection (as an alternative to locking around an ordinary collection). There are some caveats, though:

The conventional collections outperform the concurrent collections in all but highly concurrent scenarios.

A thread-safe collection doesn’t guarantee that the code using it will be thread-safe (see “Locking and Thread Safety”).

If you enumerate over a concurrent collection while another thread is modifying it, no exception is thrown—instead, you get a mixture of old and new content.

There’s no concurrent version of List<T>.

The concurrent stack, queue, and bag classes are implemented internally with linked lists. This makes them less memory-efficient than the nonconcurrent Stack and Queue classes, but better for concurrent access because linked lists are conducive to lock-free or low-lock implementations. (This is because inserting a node into a linked list requires updating just a couple of references, whereas inserting an element into a List<T>-like structure might require moving thousands of existing elements.)

In other words, these collections are not merely shortcuts for using an ordinary collection with a lock. To demonstrate, if we execute the following code on a single thread:

var d = new ConcurrentDictionary<int,int>();
for (int i = 0; i < 1000000; i++) d[i] = 123;
it runs three times more slowly than this:

var d = new Dictionary<int,int>();
for (int i = 0; i < 1000000; i++) lock (d) d[i] = 123;
(Reading from a ConcurrentDictionary, however, is fast because reads are lock-free.)

The concurrent collections also differ from conventional collections in that they expose special methods to perform atomic test-and-act operations, such as TryPop. Most of these methods are unified via the IProducerConsumerCollection<T> interface.

IProducerConsumerCollection<T>
A producer/consumer collection is one for which the two primary use cases are:

Adding an element (“producing”)

Retrieving an element while removing it (“consuming”)

The classic examples are stacks and queues. Producer/consumer collections are significant in parallel programming because they’re conducive to efficient lock-free implementations.

The IProducerConsumerCollection<T> interface represents a thread-safe producer/consumer collection. The following classes implement this interface:

ConcurrentStack<T>
ConcurrentQueue<T>
ConcurrentBag<T>
IProducerConsumerCollection<T> extends ICollection, adding the following methods:

void CopyTo (T[] array, int index);
T[] ToArray();
bool TryAdd (T item);
bool TryTake (out T item);
The TryAdd and TryTake methods test whether an add/remove operation can be performed; if so, they perform the add/remove. The testing and acting are atomically performed, eliminating the need to lock as you would around a conventional collection:

int result;
lock (myStack) if (myStack.Count > 0) result = myStack.Pop();
TryTake returns false if the collection is empty. TryAdd always succeeds and returns true in the three implementations provided. If you wrote your own concurrent collection that prohibited duplicates, however, you’d make TryAdd return false if the element already existed (an example would be if you wrote a concurrent set).

The particular element that TryTake removes is defined by the subclass:

With a stack, TryTake removes the most recently added element.

With a queue, TryTake removes the least recently added element.

With a bag, TryTake removes whatever element it can remove most efficiently.

The three concrete classes mostly implement the TryTake and TryAdd methods explicitly, exposing the same functionality through more specifically named public methods such as TryDequeue and TryPop.

ConcurrentBag<T>
ConcurrentBag<T> stores an unordered collection of objects (with duplicates permitted). ConcurrentBag<T> is suitable in situations for which you don’t care which element you get when calling Take or TryTake.

The benefit of ConcurrentBag<T> over a concurrent queue or stack is that a bag’s Add method suffers almost no contention when called by many threads at once. In contrast, calling Add in parallel on a queue or stack incurs some contention (although a lot less than locking around a nonconcurrent collection). Calling Take on a concurrent bag is also very efficient—as long as each thread doesn’t take more elements than it Added.

Inside a concurrent bag, each thread gets its own private linked list. Elements are added to the private list that belongs to the thread calling Add, eliminating contention. When you enumerate over the bag, the enumerator travels through each thread’s private list, yielding each of its elements in turn.

When you call Take, the bag first looks at the current thread’s private list. If there’s at least one element,1 it can complete the task easily and without contention. But if the list is empty, it must “steal” an element from another thread’s private list and incur the potential for contention.

So, to be precise, calling Take gives you the element added most recently on that thread; if there are no elements on that thread, it gives you the element added most recently on another thread, chosen at random.

Concurrent bags are ideal when the parallel operation on your collection mostly comprises Adding elements—or when the Adds and Takes are balanced on a thread. We saw an example of the former previously, when using Parallel.ForEach to implement a parallel spellchecker:

var misspellings = new ConcurrentBag<Tuple<int,string>>();

Parallel.ForEach (wordsToTest, (word, state, i) =>
{
  if (!wordLookup.Contains (word))
    misspellings.Add (Tuple.Create ((int) i, word));
});
A concurrent bag would be a poor choice for a producer/consumer queue because elements are added and removed by different threads.

BlockingCollection<T>
If you call TryTake on any of the producer/consumer collections we discussed in the previous section, ConcurrentStack<T>, ConcurrentQueue<T>, and ConcurrentBag<T>, and the collection is empty, the method returns false. Sometimes, it would be more useful in this scenario to wait until an element is available.

Rather than overloading the TryTake methods with this functionality (which would have caused a blowout of members after allowing for cancellation tokens and timeouts), PFX’s designers encapsulated this functionality into a wrapper class called BlockingCollection<T>. A blocking collection wraps any collection that implements IProducerConsumerCollection<T> and lets you Take an element from the wrapped collection—blocking if no element is available.

A blocking collection also lets you limit the total size of the collection, blocking the producer if that size is exceeded. A collection limited in this manner is called a bounded blocking collection.

To use BlockingCollection<T>:

Instantiate the class, optionally specifying the IProducerConsumerCollection<T> to wrap and the maximum size (bound) of the collection.

Call Add or TryAdd to add elements to the underlying collection.

Call Take or TryTake to remove (consume) elements from the underlying collection.

If you call the constructor without passing in a collection, the class will automatically instantiate a ConcurrentQueue<T>. The producing and consuming methods let you specify cancellation tokens and timeouts. Add and TryAdd may block if the collection size is bounded; Take and TryTake block while the collection is empty.

Another way to consume elements is to call GetConsumingEnumerable. This returns a (potentially) infinite sequence that yields elements as they become available. You can force the sequence to end by calling CompleteAdding: this method also prevents further elements from being enqueued.

BlockingCollection also provides static methods called AddToAny and TakeFro⁠mAny, which let you add or take an element while specifying several blocking collections. The action is then honored by the first collection able to service the request.

Writing a Producer/Consumer Queue
A producer/consumer queue is a useful structure, both in parallel programming and general concurrency scenarios. Here’s how it works:

A queue is set up to describe work items—or data upon which work is performed.

When a task needs executing, it’s enqueued, and the caller gets on with other things.

One or more worker threads plug away in the background, picking off and executing queued items.

A producer/consumer queue gives you precise control over how many worker threads execute at once, which is useful not only in limiting CPU consumption but other resources, as well. If the tasks perform intensive disk I/O, for instance, you can limit concurrency to avoid starving the operating system and other applications. You can also dynamically add and remove workers throughout the queue’s life. The CLR’s thread pool itself is a kind of producer/consumer queue, optimized for short-running compute-bound jobs.

A producer/consumer queue typically holds items of data upon which (the same) task is performed. For example, the items of data may be filenames, and the task might be to encrypt those files. By making the item a delegate, however, you can write a more general-purpose producer/consumer queue where each item can do anything.

At http://albahari.com/threading, we show how to write a producer/consumer queue from scratch using an AutoResetEvent (and later, using Monitor’s Wait and Pulse). However, writing a producer/consumer from scratch is unnecessary because most of the functionality is provided by BlockingCollection<T>. Here’s how to use it:

public class PCQueue : IDisposable
{
  BlockingCollection<Action> _taskQ = new BlockingCollection<Action>();

  public PCQueue (int workerCount)
  {
    // Create and start a separate Task for each consumer:
    for (int i = 0; i < workerCount; i++)
      Task.Factory.StartNew (Consume);
  }

  public void Enqueue (Action action) { _taskQ.Add (action); }

  void Consume()
  {
    // This sequence that we’re enumerating will block when no elements
    // are available and will end when CompleteAdding is called.

    foreach (Action action in _taskQ.GetConsumingEnumerable())
      action();     // Perform task.
  }

  public void Dispose() { _taskQ.CompleteAdding(); }
}
Because we didn’t pass anything into BlockingCollection’s constructor, it instantiated a concurrent queue automatically. Had we passed in a ConcurrentStack, we’d have ended up with a producer/consumer stack.

Using Tasks
The producer/consumer that we just wrote is inflexible in that we can’t track work items after they’ve been enqueued. It would be nice if we could do the following:

Know when a work item has completed (and await it)

Cancel a work item

Deal elegantly with any exceptions thrown by a work item

An ideal solution would be to have the Enqueue method return some object giving us the functionality just described. The good news is that a class already exists to do exactly this—the Task class, which we can generate either with a TaskCompletionSource or by instantiating directly (creating an unstarted or cold task):

public class PCQueue : IDisposable
{
  BlockingCollection<Task> _taskQ = new BlockingCollection<Task>();

  public PCQueue (int workerCount)
  {
    // Create and start a separate Task for each consumer:
    for (int i = 0; i < workerCount; i++)
      Task.Factory.StartNew (Consume);
  }

  public Task Enqueue (Action action, CancellationToken cancelToken
                                            = default (CancellationToken))
  {
    var task = new Task (action, cancelToken);
    _taskQ.Add (task);
    return task;
  }

  public Task<TResult> Enqueue<TResult> (Func<TResult> func, 
              CancellationToken cancelToken = default (CancellationToken))
  {
    var task = new Task<TResult> (func, cancelToken);
    _taskQ.Add (task);
    return task;
  }
  
  void Consume()
  {
    foreach (var task in _taskQ.GetConsumingEnumerable())
      try 
      {
          if (!task.IsCanceled) task.RunSynchronously();
      } 
      catch (InvalidOperationException) { }  // Race condition
  }

  public void Dispose() { _taskQ.CompleteAdding(); }
}
In Enqueue, we enqueue and return to the caller a task that we create but don’t start.

In Consume, we run the task synchronously on the consumer’s thread. We catch an InvalidOperationException to handle the unlikely event that the task is canceled in between checking whether it’s canceled and running it.

Here’s how we can use this class:

var pcQ = new PCQueue (2);    // Maximum concurrency of 2
string result = await pcQ.Enqueue (() => "That was easy!");
...
Hence, we have all the benefits of tasks—with exception propagation, return values, and cancellation—while taking complete control over scheduling.

1 Due to an implementation detail, there actually needs to be at least two elements to avoid contention entirely.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


22. Parallel Programming
23. Span<T> and Memory<T>
24. Native and COM Interoperability
25h 47m remaining
Chapter 23. Span<T> and Memory<T>
The Span<T> and Memory<T> structs act as low-level façades over an array, string, or any contiguous block of managed or unmanaged memory. Their main purpose is to help with certain kinds of micro-optimization—in particular, writing low-allocation code that minimizes managed memory allocations (thereby reducing the load on the garbage collector), without having to duplicate your code for different kinds of input. They also enable slicing—working with a portion of an array, string, or memory block without creating a copy.

Span<T> and Memory<T> are particularly useful in performance hotspots, such as the ASP.NET Core processing pipeline, or a JSON parser that serves an object database.

NOTE
Should you come across these types in an API and not need or care for their potential performance advantages, you can deal with them easily as follows:

When calling a method that expects a Span<T>, ReadOnlySpan<T>, Memory<T>, or ReadOnlyMemory<T>, pass in an array instead; that is, T[]. (This works thanks to implicit conversion operators.)

To convert from a span/memory to an array, call the ToArray method. And if T is char, ToString will convert the span/memory into a string.

From C# 12, you can also use collection initializers to create spans.

Specifically, Span<T> does two things:

It provides a common array-like interface over managed arrays, strings, and pointer-backed memory. This gives you the freedom to employ stack-allocated and unmanaged memory to avoid garbage collection, without having to duplicate code or mess with pointers.

It allows “slicing”: exposing reusable subsections of the span without making copies.

NOTE
Span<T> comprises just two fields, a pointer and a length. For this reason, it can represent only contiguous blocks of memory. (Should you need to work with noncontiguous memory, the ReadOnlySequence<T> class is available to serve as a linked list.)

Because Span<T> can wrap stack-allocated memory, there are restrictions on how you can store or pass around instances (imposed, in part, by Span<T> being a ref struct). Memory<T> acts as a span without those restrictions, but it cannot wrap stack-allocated memory. Memory<T> still provides the benefit of slicing.

Each struct comes with a read-only counterpart (ReadOnlySpan<T> and ReadOnlyMe⁠mory<T>). As well as preventing unintentional change, the read-only counterparts further improve performance by allowing the compiler and runtime additional freedom for optimization.

.NET itself (and ASP.NET Core) use these types to improve efficiency with I/O, networking, string handling, and JSON parsing.

NOTE
Span<T> and Memory<T>’s ability to perform array slicing make the old ArraySegment<T> class redundant. To help with any transition, there are implicit conversion operators from ArraySegment<T> to all of the span/memory structs, and from Memory<T> and ReadOnlyMemory<T> to ArraySegment<T>.

Spans and Slicing
Unlike an array, a span can easily be sliced to represent different subsections of the same underlying data, as illustrated in Figure 23-1.

To give a practical example, suppose that you’re writing a method to sum an array of integers. A micro-optimized implementation would avoid LINQ in favor of a foreach loop:

int Sum (int[] numbers)
{
  int total = 0;
  foreach (int i in numbers) total += i;
  return total;
}

Figure 23-1. Slicing
Now imagine that you want to sum just a portion of the array. You have two options:

First copy the portion of the array that you want to sum into another array

Add additional parameters to the method (offset and count)

The first option is inefficient; the second option adds clutter and complexity (which worsens with methods that need to accept more than one array).

Spans solve this nicely. All you need to do is to change the parameter type from int[] to ReadOnlySpan<int> (everything else stays the same):

int Sum (ReadOnlySpan<int> numbers)
{
  int total = 0;
  foreach (int i in numbers) total += i;
  return total;
}
NOTE
We used ReadOnlySpan<T> rather than Span<T> because we don’t need to modify the array. There’s an implicit conversion from Span<T> to ReadOnlySpan<T>, so you can pass a Span<T> into a method that expects a ReadOnlySpan<T>.

We can test this method, as follows:

var numbers = new int [1000];
for (int i = 0; i < numbers.Length; i++) numbers [i] = i;

int total = Sum (numbers);
We can call Sum with an array because there’s an implicit conversion from T[] to Span<T> and ReadOnlySpan<T>. Another option is to use the AsSpan extension method:

var span = numbers.AsSpan();
The indexer for ReadOnlySpan<T> uses C#’s ref readonly feature to reach directly into the underlying data: this allows our method to perform almost as well as the original example that used an array. But what we’ve gained is that we can now “slice” the array and sum just a portion of the elements as follows:

// Sum the middle 500 elements (starting from position 250):
int total = Sum (numbers.AsSpan (250, 500));
If you already have a Span<T> or ReadOnlySpan<T>, you can slice it by calling the Slice method:

Span<int> span = numbers;
int total = Sum (span.Slice (250, 500));
You can also use C#’s indices and ranges (from C# 8):

Span<int> span = numbers;
Console.WriteLine (span [^1]);            // Last element
Console.WriteLine (Sum (span [..10]));    // First 10 elements
Console.WriteLine (Sum (span [100..]));   // 100th element to end
Console.WriteLine (Sum (span [^5..]));    // Last 5 elements
Although Span<T> doesn’t implement IEnumerable<T> (it can’t implement interfaces by virtue of being a ref struct), it does implement the pattern that allows C#’s foreach statement to work (see “Enumeration”).

CopyTo and TryCopyTo
The CopyTo method copies elements from one span (or Memory<T>) to another. In the following example, we copy all of the elements from span x into span y:

Span<int> x = [1, 2, 3, 4];   // Collection expression
Span<int> y = new int[4];
x.CopyTo (y);
NOTE
Notice that we initialized x with a collection expression. Collection expressions (from C# 12) are not only a useful shortcut, but in the case of spans, they allow the compiler the freedom to choose the underlying type. When the element count is small, the compiler may allocate memory on the stack (rather than creating an array) to avoid the overhead of a heap allocation.

Slicing makes this method much more useful. In the next example, we copy the first half of span x into the second half of span y:

Span<int> x = [1,  2,  3,  4 ];
Span<int> y = [10, 20, 30, 40];
x[..2].CopyTo (y[2..]);                 // y is now [10, 20, 1, 2]
If there’s not enough space in the destination to complete the copy, CopyTo throws an exception, whereas TryCopyTo returns false (without copying any elements).

The span structs also expose methods to Clear and Fill the span as well as an IndexOf method to search for an element in the span.

Searching in Spans
The MemoryExtensions class defines numerous extension methods to help with searching for values within spans such as Contains, IndexOf, LastIndexOf, and BinarySearch (as well as methods that mutate spans, such as Fill, Replace, and Reverse).

From .NET 8, there are also methods to search for any one of a number of values, such as ContainsAny, ContainsAnyExcept, IndexOfAny, and IndexOfAnyExcept. With these methods, you can specify the values to search either as a span or as a SearchValues<T> instance (in System.Buffers), which you instantiate by calling SearchValues.Create:

ReadOnlySpan<char> span = "The quick brown fox jumps over the lazy dog.";
var vowels = SearchValues.Create ("aeiou");
Console.WriteLine (span.IndexOfAny (vowels));   // 2
SearchValues<T> improves performance when the instance is reused across multiple searches.

NOTE
You can also utilize these methods when working with arrays or strings, simply by calling AsSpan() on the array or string.

Working with Text
Spans are designed to work well with strings, which are treated as ReadOnlySpan<char>. The following method counts whitespace characters:

int CountWhitespace (ReadOnlySpan<char> s)
{
  int count = 0;
  foreach (char c in s)
    if (char.IsWhiteSpace (c))
      count++;
  return count;
}
You can call such a method with a string (thanks to an implicit conversion operator):

int x = CountWhitespace ("Word1 Word2");   // OK
or with a substring:

int y = CountWhitespace (someString.AsSpan (20, 10));
The ToString() method converts a ReadOnlySpan<char> back to a string.

Extension methods ensure that some of the commonly used methods on the string class are also available to ReadOnlySpan<char>:

var span = "This ".AsSpan();                    // ReadOnlySpan<char>
Console.WriteLine (span.StartsWith ("This"));   // True
Console.WriteLine (span.Trim().Length);         // 4
(Note that methods such as StartsWith use ordinal comparison, whereas the corresponding methods on the string class use culture-sensitive comparison by default.)

Methods such as ToUpper and ToLower are available, but you must pass in a destination span with the correct length (this allows you to decide how and where to allocate the memory).

Some of string’s methods are unavailable, such as Split (which splits a string into an array of words). It’s actually impossible to write the direct equivalent of string’s Split method because you cannot create an array of spans.

NOTE
This is because spans are defined as ref structs, which can exist only on the stack.

(By “exist only on the stack,” we mean that the struct itself can exist only on the stack. The content that the span wraps can—and does, in this case—exist on the heap.)

The System.Buffers.Text namespace contains additional types to help you work with span-based text, including the following:

Utf8Formatter.TryFormat does the equivalent of calling ToString on built-in and simple types such as decimal, DateTime, and so on but writes to a span instead of a string.

Utf8Parser.TryParse does the reverse and parses data from a span into a simple type.

The Base64 type provides methods for reading/writing base-64 data.

NOTE
From .NET 8, the .NET numeric and date/time types (as well as other simple types) allow direct formatting and parsing of UTF-8, via new TryFormat and Parse/TryParse methods that operate on a Span<byte>. The new methods are defined in the IUtf8SpanFormattable and IUtf8SpanParsable<TSelf> interfaces (the latter leverages C# 12’s ability to define static abstract interface members).

Fundamental CLR methods such as int.Parse have also been overloaded to accept ReadOnlySpan<char>.

Memory<T>
Span<T> and ReadOnlySpan<T> are defined as ref structs to maximize their optimization potential as well as allowing them to work safely with stack-allocated memory (as you’ll see in the next section). However, it also imposes limitations. In addition to being array-unfriendly, you cannot use them as fields in a class (this would put them on the heap). This, in turn, prevents them from appearing in lambda expressions—and as parameters in asynchronous methods, iterators, and asynchronous streams:

async void Foo (Span<int> notAllowed)   // Compile-time error!
(Remember that the compiler processes asynchronous methods and iterators by writing a private state machine, which means that any parameters and local variables end up as fields. The same applies to lambda expressions that close over variables: these also end up as fields in a closure.)

The Memory<T> and ReadOnlyMemory<T> structs work around this, acting as spans that cannot wrap stack-allocated memory, allowing their use in fields, lambda expressions, asynchronous methods, and so on.

You can obtain a Memory<T> or ReadOnlyMemory<T> from an array via an implicit conversion or the AsMemory() extension method:

Memory<int> mem1 = new int[] { 1, 2, 3 };
var mem2 = new int[] { 1, 2, 3 }.AsMemory();
You can easily “convert” a Memory<T> or ReadOnlyMemory<T> into a Span<T> or ReadOnlySpan<T> via its Span property so that you can interact with it as though it were a span. The conversion is efficient in that it doesn’t perform any copying:

async void Foo (Memory<int> memory)   
{
  Span<int> span = memory.Span;
  ...
}
(You can also directly slice a Memory<T> or ReadOnlyMemory<T> via its Slice method or a C# range, and access its length via its Length property.)

NOTE
Another way to obtain a Memory<T> is to rent it from a pool, using the System.Buffers.MemoryPool<T> class. This works just like array pooling (see “Array Pooling”) and offers another strategy for reducing the load on the garbage collector.

We said in the previous section that you cannot write the direct equivalent of string.Split for spans, because you cannot create an array of spans. This limitation does not apply to ReadOnlyMemory<char>:

// Split a string into words:
IEnumerable<ReadOnlyMemory<char>> Split (ReadOnlyMemory<char> input)
{
  int wordStart = 0;
  for (int i = 0; i <= input.Length; i++)
    if (i == input.Length || char.IsWhiteSpace (input.Span [i]))
    {
      yield return input [wordStart..i];   // Slice with C# range operator
      wordStart = i + 1;
    }
}
This is more efficient than string’s Split method: instead of creating new strings for each word, it returns slices of the original string:

foreach (var slice in Split ("The quick brown fox jumps over the lazy dog"))
{
  // slice is a ReadOnlyMemory<char>
}
NOTE
You can easily convert a Memory<T> into a Span<T> (via the Span property), but not vice versa. For this reason, it’s better to write methods that accept Span<T> than Memory<T> when you have a choice.

For the same reason, it’s better to write methods that accept ReadOnlySpan<T> rather than Span<T>.

Forward-Only Enumerators
In the preceding section, we employed ReadOnlyMemory<char> as a solution to implementing a string-style Split method. But by giving up on ReadOnlySpan<char>, we lost the ability to slice spans backed by unmanaged memory. Let’s revisit ReadOnlySpan<char> to see whether we can find another solution.

One possible option would be to write our Split method so that it returns ranges:

Range[] Split (ReadOnlySpan<char> input)
{
  int pos = 0;
  var list = new List<Range>();
  for (int i = 0; i <= input.Length; i++)
    if (i == input.Length || char.IsWhiteSpace (input [i]))
    {
      list.Add (new Range (pos, i));
      pos = i + 1;
    }
  return list.ToArray();
}
The caller could then use those ranges to slice the original span:

ReadOnlySpan<char> source = "The quick brown fox";
foreach (Range range in Split (source))
{
  ReadOnlySpan<char> wordSpan = source [range];
  ...
}
This is an improvement, but it’s still imperfect. One of the reasons for using spans in the first place is to avoid memory allocations. But notice that our Split method creates a List<Range>, adds items to it, and then converts the list into an array. This incurs at least two memory allocations as well a memory-copy operation.

The solution to this is to eschew the list and array in favor of a forward-only enumerator. An enumerator is clumsier to work with, but it can be made allocation-free with the use of structs:

// We must define this as a ref struct, because _input is a ref struct.
public readonly ref struct CharSpanSplitter
{
  readonly ReadOnlySpan<char> _input;
  public CharSpanSplitter (ReadOnlySpan<char> input) => _input = input;
  public Enumerator GetEnumerator() => new Enumerator (_input);

  public ref struct Enumerator   // Forward-only enumerator
  {
    readonly ReadOnlySpan<char> _input;
    int _wordPos;
    public ReadOnlySpan<char> Current { get; private set; }

    public Rator (ReadOnlySpan<char> input)
    {
      _input = input;
      _wordPos = 0;
      Current = default;
    }

    public bool MoveNext()
    {
      for (int i = _wordPos; i <= _input.Length; i++)
        if (i == _input.Length || char.IsWhiteSpace (_input [i]))
        {
          Current = _input [_wordPos..i];
          _wordPos = i + 1;
          return true;
        }
      return false;
    }
  }
}

public static class CharSpanExtensions
{
  public static CharSpanSplitter Split (this ReadOnlySpan<char> input)
    => new CharSpanSplitter (input);

  public static CharSpanSplitter Split (this Span<char> input)
    => new CharSpanSplitter (input);
}
Here’s how you would call it:

var span = "the quick brown fox".AsSpan();
foreach (var word in span.Split())
{
  // word is a ReadOnlySpan<char>
}
By defining a Current property and a MoveNext method, our enumerator can work with C#’s foreach statement (see “Enumeration”). We don’t have to implement the IEnumerable<T>/IEnumerator<T> interfaces (in fact, we can’t; ref structs can’t implement interfaces). We’re sacrificing abstraction for micro-optimization.

Working with Stack-Allocated and Unmanaged Memory
Another effective micro-optimization technique is to reduce the load on the garbage collector by minimizing heap-based allocations. This means making greater use of stack-based memory—or even unmanaged memory.

Unfortunately, this normally requires that you rewrite code to use pointers. In the case of our previous example that summed elements in an array, we would need to write another version as follows:

unsafe int Sum (int* numbers, int length)
{
  int total = 0;
  for (int i = 0; i < length; i++) total += numbers [i];
  return total;
}
so that we could do this:

int* numbers = stackalloc int [1000];   // Allocate array on the stack
int total = Sum (numbers, 1000);
Spans solve this problem: you can construct a Span<T> or ReadOnlySpan<T> directly from a pointer:

int* numbers = stackalloc int [1000];
var span = new Span<int> (numbers, 1000);
Or in one step:

Span<int> numbers = stackalloc int [1000];
(Note that this doesn’t require the use of unsafe). Recall the Sum method that we wrote previously:

int Sum (ReadOnlySpan<int> numbers)
{
  int total = 0;
  int len = numbers.Length;
  for (int i = 0; i < len; i++) total += numbers [i];
  return total;
}
This method works equally well for a stack-allocated span. We have gained on three counts:

The same method works with both arrays and stack-allocated memory

We can use stack-allocated memory with minimal use of pointers

The span can be sliced

NOTE
The compiler is smart enough to prevent you from writing a method that allocates memory on the stack and returns it to the caller via a Span<T> or ReadOnlySpan<T>.

(In other scenarios, however, you can legally return a Span<T> or ReadOnlySpan<T>.)

You can also use spans to wrap memory that you allocate from the unmanaged heap. In the following example, we allocate unmanaged memory using the Marshal.AllocHGlobal function, wrap it in a Span<char>, and then copy a string into the unmanaged memory. Finally, we employ the CharSpanSplitter struct that we wrote in the preceding section to split the unmanaged string into words:

var source = "The quick brown fox".AsSpan();
var ptr = Marshal.AllocHGlobal (source.Length * sizeof (char));
try
{
  var unmanaged = new Span<char> ((char*)ptr, source.Length);
  source.CopyTo (unmanaged);
  foreach (var word in unmanaged.Split())
    Console.WriteLine (word.ToString());
}
finally { Marshal.FreeHGlobal (ptr); }
A nice bonus is that Span<T>’s indexer performs bounds-checking, preventing a buffer overrun. This protection applies if you correctly instantiate Span<T>: in our example, you would lose this protection if you wrongly obtained the span:

var span = new Span<char> ((char*)ptr, source.Length * 2);
There’s also no protection from the equivalent of a dangling pointer, so you must take care not to access the span after releasing its unmanaged memory with Marshal.FreeHGlobal.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


23. Span<T> and Memory<T>
24. Native and COM Interoperability
25. Regular Expressions
25h 47m remaining
Chapter 24. Native and COM Interoperability
This chapter describes how to integrate with native (unmanaged) Dynamic-Link Libraries (DLLs) and Component Object Model (COM) components. Unless otherwise stated, the types mentioned in this chapter exist in either the System or the System.Runtime.InteropServices namespace.

Calling into Native DLLs
P/Invoke, short for Platform Invocation Services, allows you to access functions, structs, and callbacks in unmanaged DLLs (shared libraries on Unix).

For example, consider the MessageBox function, defined in the Windows DLL user32.dll, as follows:

int MessageBox (HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption, UINT uType);
You can call this function directly by declaring a static method of the same name, applying the extern keyword, and adding the DllImport attribute:

using System;
using System.Runtime.InteropServices;

MessageBox (IntPtr.Zero,
            "Please do not press this again.", "Attention", 0);

[DllImport("user32.dll")]
static extern int MessageBox (IntPtr hWnd, string text, string caption,
                              int type);
The MessageBox classes in the System.Windows and System.Windows.Forms namespaces themselves call similar unmanaged methods.

Here’s a DllImport example for Ubuntu Linux:

Console.WriteLine ($"User ID: {getuid()}");

[DllImport("libc")]
static extern uint getuid();
The CLR includes a marshaler that knows how to convert parameters and return values between .NET types and unmanaged types. In the Windows example, the int parameters translate directly to four-byte integers that the function expects, and the string parameters are converted into null-terminated arrays of Unicode characters (encoded in UTF-16). IntPtr is a struct designed to encapsulate an unmanaged handle; it’s 32 bits wide on 32-bit platforms and 64 bits wide on 64-bit platforms. A similar translation happens on Unix. (From C# 9, you can also use the nint type, which maps to IntPtr.)

Type and Parameter Marshaling
Marshaling Common Types
On the unmanaged side, there can be more than one way to represent a given data type. A string, for instance, can contain single-byte ANSI characters or UTF-16 Unicode characters, and can be length prefixed, null terminated, or of fixed length. With the MarshalAs attribute, you can specify to the CLR marshaler the variation in use, so it can provide the correct translation. Here’s an example:

[DllImport("...")]
static extern int Foo ( [MarshalAs (UnmanagedType.LPStr)] string s );
The UnmanagedType enumeration includes all the Win32 and COM types that the marshaler understands. In this case, the marshaler was told to translate to LPStr, which is a null-terminated single-byte ANSI string.

On the .NET side, you also have some choice as to what data type to use. Unmanaged handles, for instance, can map to IntPtr, int, uint, long, or ulong.

NOTE
Most unmanaged handles encapsulate an address or pointer and so must be mapped to IntPtr for compatibility with both 32- and 64-bit operating systems. A typical example is HWND.

Quite often with Win32 and POSIX functions, you come across an integer parameter that accepts a set of constants, defined in a C++ header file such as WinUser.h. Rather than defining these as simple C# constants, you can define them within an enum instead. Using an enum can make for tidier code as well as increase static type safety. We provide an example in “Shared Memory”.

NOTE
When installing Microsoft Visual Studio, be sure to install the C++ header files—even if you choose nothing else in the C++ category. This is where all the native Win32 constants are defined. You can then locate all header files by searching for *.h in the Visual Studio program directory.

On Unix, the POSIX standard defines names of constants, but individual implementations of POSIX-compliant Unix systems may assign different numeric values to these constants. You must use the correct numeric value for your operating system of choice. Similarly, POSIX defines a standard for structs used in interop calls. The ordering of fields in the struct is not fixed by the standard, and a Unix implementation might add additional fields. C++ header files defining functions and types are often installed in /usr/include or /usr/local/include.

Receiving strings from unmanaged code back to .NET requires that some memory management take place. The marshaler automatically performs this work if you declare the external method with a StringBuilder rather than a string, as follows:

StringBuilder s = new StringBuilder (256);
GetWindowsDirectory (s, 256);
Console.WriteLine (s);

[DllImport("kernel32.dll")]
static extern int GetWindowsDirectory (StringBuilder sb, int maxChars);
On Unix, it works similarly. The following calls getcwd to return the current directory:

var sb = new StringBuilder (256);
Console.WriteLine (getcwd (sb, sb.Capacity));

[DllImport("libc")]
static extern string getcwd (StringBuilder buf, int size);
Although StringBuilder is convenient to use, it’s somewhat inefficient in that the CLR must perform additional memory allocations and copying. In performance hotspots, you can avoid this overhead by using char[] instead:

[DllImport ("kernel32.dll", CharSet = CharSet.Unicode)]
static extern int GetWindowsDirectory (char[] buffer, int maxChars);
Notice that you must specify a CharSet in the DllImport attribute. You must also trim the output string to length after calling the function. You can achieve this while minimizing memory allocations with the use of array pooling (see “Array Pooling”), as follows:

string GetWindowsDirectory()
{
  var array = ArrayPool<char>.Shared.Rent (256);
  try
  {
    int length = GetWindowsDirectory (array, 256);
    return new string (array, 0, length).ToString();
  }
  finally { ArrayPool<char>.Shared.Return (array); }
}
(Of course, this example is contrived in that you can obtain the Windows directory via the built-in Environment.GetFolderPath method.)

NOTE
If you are unsure how to call a particular Win32 or Unix method, you will usually find an example on the internet if you search for the method name and DllImport. For Windows, the site http://www.pinvoke.net is a wiki that aims to document all Win32 signatures.

Marshaling Classes and Structs
Sometimes, you need to pass a struct to an unmanaged method. For example, GetSystemTime in the Win32 API is defined as follows:

void GetSystemTime (LPSYSTEMTIME lpSystemTime);
LPSYSTEMTIME conforms to this C struct:

typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
To call GetSystemTime, we must define a .NET class or struct that matches this C struct:

using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
class SystemTime
{
   public ushort Year;
   public ushort Month;
   public ushort DayOfWeek;
   public ushort Day;
   public ushort Hour;
   public ushort Minute;
   public ushort Second;
   public ushort Milliseconds;
}
The StructLayout attribute instructs the marshaler how to map each field to its unmanaged counterpart. LayoutKind.Sequential means that we want the fields aligned sequentially on pack-size boundaries (you’ll see what this means shortly), just as they would be in a C struct. The field names here are irrelevant; it’s the ordering of fields that’s important.

Now we can call GetSystemTime:

SystemTime t = new SystemTime();
GetSystemTime (t);
Console.WriteLine (t.Year);

[DllImport("kernel32.dll")]
static extern void GetSystemTime (SystemTime t);
Similarly, on Unix:

Console.WriteLine (GetSystemTime());

static DateTime GetSystemTime()
{
  DateTime startOfUnixTime = 
    new DateTime(1970, 1, 1, 0, 0, 0, 0, System.DateTimeKind.Utc);

  Timespec tp = new Timespec();
  int success = clock_gettime (0, ref tp);
  if (success != 0) throw new Exception ("Error checking the time.");
  return startOfUnixTime.AddSeconds (tp.tv_sec).ToLocalTime();  
}

[DllImport("libc")]
static extern int clock_gettime (int clk_id, ref Timespec tp);

[StructLayout(LayoutKind.Sequential)]
struct Timespec
{
  public long tv_sec;   /* seconds */
  public long tv_nsec;  /* nanoseconds */
}
In both C and C#, fields in an object are located at n number of bytes from the address of that object. The difference is that in a C# program, the CLR finds this offset by looking it up using the field token; C field names are compiled directly into offsets. For instance, in C, wDay is just a token to represent whatever is at the address of a SystemTime instance plus 24 bytes.

For access speed, each field is placed at an offset that is a multiple of the field’s size. That multiplier, however, is restricted to a maximum of x bytes, where x is the pack size. In the current implementation, the default pack size is 8 bytes, so a struct comprising an sbyte followed by an (8-byte) long occupies 16 bytes, and the 7 bytes following the sbyte are wasted. You can lessen or eliminate this wastage by specifying a pack size via the Pack property of the StructLayout attribute: this makes the fields align to offsets that are multiples of the specified pack size. So, with a pack size of 1, the struct just described would occupy just 9 bytes. You can specify pack sizes of 1, 2, 4, 8, or 16 bytes.

The StructLayout attribute also lets you specify explicit field offsets (see “Simulating a C Union”).

In and Out Marshaling
In the previous example, we implemented SystemTime as a class. We could have instead chosen a struct—provided that GetSystemTime was declared with a ref or out parameter:

[DllImport("kernel32.dll")]
static extern void GetSystemTime (out SystemTime t);
In most cases, C#’s directional parameter semantics work the same with external methods. Pass-by-value parameters are copied in, C# ref parameters are copied in/out, and C# out parameters are copied out. However, there are some exceptions for types that have special conversions. For instance, array classes and the StringBuilder class require copying when coming out of a function, so they are in/out. It is occasionally useful to override this behavior, with the In and Out attributes. For example, if an array should be read-only, the in modifier indicates to copy only the array going into the function, not coming out of it:

static extern void Foo ( [In] int[] array);
Calling Conventions
Unmanaged methods receive arguments and return values via the stack and (optionally) CPU registers. Because there’s more than one way to accomplish this, a number of different protocols have emerged. These protocols are known as calling conventions.

The CLR currently supports three calling conventions: StdCall, Cdecl, and ThisCall.

By default, the CLR uses the platform default calling convention (the standard convention for that platform). On Windows, it’s StdCall, and on Linux x86, it’s Cdecl.

Should an unmanaged method not follow this default, you can explicitly state its calling convention as follows:

[DllImport ("MyLib.dll", CallingConvention=CallingConvention.Cdecl)]
static extern void SomeFunc (...)
The somewhat misleadingly named CallingConvention.WinApi refers to the platform default.

Callbacks from Unmanaged Code
C# also allows external functions to call C# code, via callbacks. There are two ways to accomplish callbacks:

Via function pointers

Via delegates

To illustrate, we will call the following Windows function in User32.dll, which enumerates all top-level window handles:

BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);
WNDENUMPROC is a callback that is fired with the handle of each window in sequence (or until the callback returns false). Here is its definition:

BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);
Callbacks with Function Pointers
From C# 9, the simplest and most performant option—when your callback is a static method—is to use a function pointer. In the case of the WNDENUMPROC callback, we can use the following function pointer:

delegate*<IntPtr, IntPtr, bool>
This denotes a function that accepts two IntPtr arguments and returns a bool. You can then use the & operator to feed it a static method:

using System;
using System.Runtime.InteropServices;

unsafe
{
  EnumWindows (&PrintWindow, IntPtr.Zero);

  [DllImport ("user32.dll")]
  static extern int EnumWindows (
    delegate*<IntPtr, IntPtr, bool> hWnd, IntPtr lParam);

  static bool PrintWindow (IntPtr hWnd, IntPtr lParam)
  {
    Console.WriteLine (hWnd.ToInt64());
    return true;
  }
}
With function pointers, the callback must be a static method (or a static local function, as in this example).

UnmanagedCallersOnly
You can improve performance by applying the unmanaged keyword to the function pointer declaration, and the [UnmanagedCallersOnly] attribute to the callback method:

using System;
using System.Runtime.CompilerServices;
using System.Runtime.InteropServices;

unsafe
{
  EnumWindows (&PrintWindow, IntPtr.Zero);

  [DllImport ("user32.dll")]
  static extern int EnumWindows (
    delegate* unmanaged <IntPtr, IntPtr, byte> hWnd, IntPtr lParam);

  [UnmanagedCallersOnly]
  static byte PrintWindow (IntPtr hWnd, IntPtr lParam)
  {
    Console.WriteLine (hWnd.ToInt64());
    return 1;
  }
}
This attribute flags the PrintWindow method such that it can be called only from unmanaged code, allowing the runtime to take shortcuts. Notice that we’ve also changed the method’s return type from bool to byte: this is because methods to which you apply [UnmanagedCallersOnly] can use only blittable value types in the signature. Blittable types are those that don’t require any special marshalling logic because they’re represented identically in the managed and unmanaged worlds. These include the primitive integral types, float, double, and structs that contain only blittable types. The char type is also blittable, if part of a struct with a StructLayout attribute specifying CharSet.Unicode:

[StructLayout (LayoutKind.Sequential, CharSet=CharSet.Unicode)]
Nondefault calling conventions
By default, the compiler assumes that the unmanaged callback follows the platform-default calling convention. Should this not be so, you can explicitly state its calling convention via the CallConvs parameter of the [UnmanagedCallersOnly] attribute:

[UnmanagedCallersOnly (CallConvs = new[] { typeof (CallConvStdcall) })]
static byte PrintWindow (IntPtr hWnd, IntPtr lParam) ...
You must also update the function pointer type by inserting a special modifier after the unmanaged keyword:

delegate* unmanaged[Stdcall] <IntPtr, IntPtr, byte> hWnd, IntPtr lParam);
NOTE
The compiler lets you put any identifier (such as XYZ) inside the square brackets, as long as there’s a .NET type called CallConvXYZ (that’s understood by the runtime and matches what you specified when applying the [UnmanagedCallersOnly] attribute). This makes it easier for Microsoft to add new calling conventions in the future.

In this case, we specified StdCall, which is the platform default for Windows (Cdecl is the default for Linux x86). Here are all the options that are currently supported:

Name	unmanaged modifier	Supporting type
Stdcall	unmanaged[Stdcall]	CallConvStdcall
Cdecl	unmanaged[Cdecl]	CallConvCdecl
ThisCall	unmanaged[Thiscall]	CallConvThiscall
Callbacks with Delegates
Unmanaged callbacks can also be accomplished with delegates. This approach works in all versions of C#, and allows for callbacks that reference instance methods.

To proceed, first declare a delegate type with a signature that matches the callback. Then you can pass a delegate instance to the external method:

class CallbackFun
{
  delegate bool EnumWindowsCallback (IntPtr hWnd, IntPtr lParam);

  [DllImport("user32.dll")]
  static extern int EnumWindows (EnumWindowsCallback hWnd, IntPtr lParam);

  static bool PrintWindow (IntPtr hWnd, IntPtr lParam)
  {
    Console.WriteLine (hWnd.ToInt64());
    return true;
  }
  static readonly EnumWindowsCallback printWindowFunc = PrintWindow;

  static void Main() => EnumWindows (printWindowFunc, IntPtr.Zero);
}
Using delegates for unmanaged callbacks is ironically unsafe, because it’s easy to fall into the trap of allowing a callback to occur after the delegate instance falls out of scope (at which point the delegate becomes eligible for garbage collection). This can result in the worst kind of runtime exception—one with no useful stack trace. In the case of static method callbacks, you can avoid this by assigning the delegate instance to a read-only static field (as we did in this example). With instance method callbacks, this pattern won’t help, so you must code carefully to ensure that you maintain at least one reference to the delegate instance for the duration of any potential callback. Even then, if there’s a bug on the unmanaged side—whereby it invokes a callback after you’ve told it not to—you may still have to deal with an untraceable exception. A workaround is to define a unique delegate type per unmanaged function: this helps diagnostically because the delegate type is reported in the exception.

You can change the callback’s calling convention from the platform default by applying the [UnmanagedFunctionPointer] attribute to the delegate:

[UnmanagedFunctionPointer (CallingConvention.Cdecl)]
delegate void MyCallback (int foo, short bar);
Simulating a C Union
Each field in a struct is given enough room to store its data. Consider a struct containing one int and one char. The int is likely to start at an offset of 0 and is guaranteed at least four bytes. So, the char would start at an offset of at least 4. If, for some reason, the char started at an offset of 2, you’d change the value of the int if you assigned a value to the char. Sounds like mayhem, doesn’t it? Strangely enough, the C language supports a variation on a struct called a union that does exactly this. You can simulate this in C# by using LayoutKind.Explicit and the FieldOffset attribute.

It might be challenging to think of a case in which this would be useful. However, suppose that you want to play a note on an external synthesizer. The Windows Multimedia API provides a function for doing just this via the MIDI protocol:

[DllImport ("winmm.dll")]
public static extern uint midiOutShortMsg (IntPtr handle, uint message);
The second argument, message, describes what note to play. The problem is in constructing this 32-bit unsigned integer: it’s divided internally into bytes, representing a MIDI channel, note, and velocity at which to strike. One solution is to shift and mask via the bitwise <<, >>, &, and | operators to convert these bytes to and from the 32-bit “packed” message. Far simpler, though, is to define a struct with explicit layout:

[StructLayout (LayoutKind.Explicit)]
public struct NoteMessage
{
  [FieldOffset(0)] public uint PackedMsg;    // 4 bytes long

  [FieldOffset(0)] public byte Channel;      // FieldOffset also at 0
  [FieldOffset(1)] public byte Note;
  [FieldOffset(2)] public byte Velocity;
}
The Channel, Note, and Velocity fields deliberately overlap with the 32-bit packed message. This allows you to read and write using either. No calculations are required to keep other fields in sync:

NoteMessage n = new NoteMessage();
Console.WriteLine (n.PackedMsg);    // 0

n.Channel = 10;
n.Note = 100;
n.Velocity = 50;
Console.WriteLine (n.PackedMsg);    // 3302410

n.PackedMsg = 3328010;
Console.WriteLine (n.Note);         // 200
Shared Memory
Memory-mapped files, or shared memory, is a feature in Windows that allows multiple processes on the same computer to share data. Shared memory is extremely fast and, unlike pipes, offers random access to the shared data. We saw in Chapter 15 how you can use the MemoryMappedFile class to access memory-mapped files; bypassing this and calling the Win32 methods directly is a good way to demonstrate P/Invoke.

The Win32 CreateFileMapping function allocates shared memory. You tell it how many bytes you need and the name with which to identify the share. Another application can then subscribe to this memory by calling OpenFileMapping with the same name. Both methods return a handle, which you can convert to a pointer by calling MapViewOfFile.

Here’s a class that encapsulates access to shared memory:

using System;
using System.Runtime.InteropServices;
using System.ComponentModel;

public sealed class SharedMem : IDisposable
{
  // Here we're using enums because they're safer than constants

  enum FileProtection : uint      // constants from winnt.h
  {
    ReadOnly = 2,
    ReadWrite = 4
  }

  enum FileRights : uint          // constants from WinBASE.h
  {
    Read = 4,
    Write = 2,
    ReadWrite = Read + Write
  }

  static readonly IntPtr NoFileHandle = new IntPtr (-1);

  [DllImport ("kernel32.dll", SetLastError = true)]
  static extern IntPtr CreateFileMapping (IntPtr hFile,
                                          int lpAttributes,
                                          FileProtection flProtect,
                                          uint dwMaximumSizeHigh,
                                          uint dwMaximumSizeLow,
                                          string lpName);

  [DllImport ("kernel32.dll", SetLastError=true)]
  static extern IntPtr OpenFileMapping (FileRights dwDesiredAccess,
                                        bool bInheritHandle,
                                        string lpName);

  [DllImport ("kernel32.dll", SetLastError = true)]
  static extern IntPtr MapViewOfFile (IntPtr hFileMappingObject,
                                      FileRights dwDesiredAccess,
                                      uint dwFileOffsetHigh,
                                      uint dwFileOffsetLow,
                                      uint dwNumberOfBytesToMap);

  [DllImport ("Kernel32.dll", SetLastError = true)]
  static extern bool UnmapViewOfFile (IntPtr map);

  [DllImport ("kernel32.dll", SetLastError = true)]
  static extern int CloseHandle (IntPtr hObject);

  IntPtr fileHandle, fileMap;

  public IntPtr Root => fileMap;

  public SharedMem (string name, bool existing, uint sizeInBytes)
  {
    if (existing)
      fileHandle = OpenFileMapping (FileRights.ReadWrite, false, name);
    else
      fileHandle = CreateFileMapping (NoFileHandle, 0,
                                      FileProtection.ReadWrite,
                                      0, sizeInBytes, name);
    if (fileHandle == IntPtr.Zero)
      throw new Win32Exception();

    // Obtain a read/write map for the entire file
    fileMap = MapViewOfFile (fileHandle, FileRights.ReadWrite, 0, 0, 0);

    if (fileMap == IntPtr.Zero)
      throw new Win32Exception();
  }

  public void Dispose()
  {
    if (fileMap != IntPtr.Zero) UnmapViewOfFile (fileMap);
    if (fileHandle != IntPtr.Zero) CloseHandle (fileHandle);
    fileMap = fileHandle = IntPtr.Zero;
  }
}
In this example, we set SetLastError=true on the DllImport methods that use the SetLastError protocol for emitting error codes. This ensures that the Win32Exception is populated with details of the error when that exception is thrown. (It also allows you to query the error explicitly by calling Marshal.GetLastWin32Error.)

To demonstrate this class, we need to run two applications. The first one creates the shared memory, as follows:

using (SharedMem sm = new SharedMem ("MyShare", false, 1000))
{
  IntPtr root = sm.Root;
  // I have shared memory!

  Console.ReadLine();         // Here's where we start a second app...
}
The second application subscribes to the shared memory by constructing a SharedMem object of the same name, with the existing argument true:

using (SharedMem sm = new SharedMem ("MyShare", true, 1000))
{
  IntPtr root = sm.Root;
  // I have the same shared memory!
  // ...
}
The net result is that each program has an IntPtr—a pointer to the same unmanaged memory. The two applications now need somehow to read and write to memory via this common pointer. One approach is to write a class that encapsulates all the shared data and then serialize (and deserialize) the data to the unmanaged memory using an UnmanagedMemoryStream. This is inefficient, however, if there’s a lot of data. Imagine if the shared memory class had a megabyte of data, and just one integer needed to be updated. A better approach is to define the shared data construct as a struct and then map it directly into shared memory. We discuss this in the following section.

Mapping a Struct to Unmanaged Memory
You can directly map a struct with a StructLayout of Sequential or Explicit into unmanaged memory. Consider the following struct:

[StructLayout (LayoutKind.Sequential)]
unsafe struct MySharedData
{
  public int Value;
  public char Letter;
  public fixed float Numbers [50];
}
The fixed directive allows us to define fixed-length value-type arrays inline, and it is what takes us into the unsafe realm. Space in this struct is allocated inline for 50 floating-point numbers. Unlike with standard C# arrays, Numbers is not a reference to an array—it is the array. If we run the following:

static unsafe void Main() => Console.WriteLine (sizeof (MySharedData));
the result is 208: 50 four-byte floats, plus the four bytes for the Value integer, plus two bytes for the Letter character. The total, 206, is rounded to 208 due to the floats being aligned on four-byte boundaries (four bytes being the size of a float).

We can demonstrate MySharedData in an unsafe context, most simply, with stack-allocated memory:

MySharedData d;
MySharedData* data = &d;       // Get the address of d

data->Value = 123;
data->Letter = 'X';
data->Numbers[10] = 1.45f;

or:

// Allocate the array on the stack:
MySharedData* data = stackalloc MySharedData[1];

data->Value = 123;
data->Letter = 'X';
data->Numbers[10] = 1.45f;
Of course, we’re not demonstrating anything that couldn’t otherwise be achieved in a managed context. Suppose, however, that we want to store an instance of MySharedData on the unmanaged heap, outside the realm of the CLR’s garbage collector. This is where pointers become really useful:

MySharedData* data = (MySharedData*)
  Marshal.AllocHGlobal (sizeof (MySharedData)).ToPointer();

data->Value = 123;
data->Letter = 'X';
data->Numbers[10] = 1.45f;
Marshal.AllocHGlobal allocates memory on the unmanaged heap. Here’s how to later free the same memory:

Marshal.FreeHGlobal (new IntPtr (data));
(The result of forgetting to free the memory is a good old-fashioned memory leak.)

NOTE
From .NET 6, you can instead use the NativeMemory class for allocating and freeing unmanaged memory. NativeMemory uses a newer (and better) underlying API than AllocHGlobal and also includes methods for performing aligned allocations.

In keeping with its name, here we use MySharedData in conjunction with the SharedMem class we wrote in the preceding section. The following program allocates a block of shared memory, and then maps the MySharedData struct into that memory:

static unsafe void Main()
{
  using (SharedMem sm = new SharedMem ("MyShare", false, 
                          (uint) sizeof (MySharedData)))
  {
    void* root = sm.Root.ToPointer();
    MySharedData* data = (MySharedData*) root;

    data->Value = 123;
    data->Letter = 'X';
    data->Numbers[10] = 1.45f;
    Console.WriteLine ("Written to shared memory");

    Console.ReadLine();

    Console.WriteLine ("Value is " + data->Value);
    Console.WriteLine ("Letter is " + data->Letter);
    Console.WriteLine ("11th Number is " + data->Numbers[10]);
    Console.ReadLine();
  }
}
NOTE
You can use the built-in MemoryMappedFile class instead of SharedMem, as follows:

using (MemoryMappedFile mmFile =
       MemoryMappedFile.CreateNew ("MyShare", 1000))
using (MemoryMappedViewAccessor accessor =
       mmFile.CreateViewAccessor())
{
  byte* pointer = null;
  accessor.SafeMemoryMappedViewHandle.AcquirePointer
   (ref pointer);
  void* root = pointer;
  ...
}
Here’s a second program that attaches to the same shared memory, reading the values written by the first program (it must be run while the first program is waiting on the ReadLine statement because the shared memory object is disposed upon leaving its using statement):

static unsafe void Main()
{
  using (SharedMem sm = new SharedMem ("MyShare", true, 
                          (uint) sizeof (MySharedData)))  
  {
    void* root = sm.Root.ToPointer();
    MySharedData* data = (MySharedData*) root;

    Console.WriteLine ("Value is " + data->Value);
    Console.WriteLine ("Letter is " + data->Letter);
    Console.WriteLine ("11th Number is " + data->Numbers[10]);

    // Our turn to update values in shared memory!
    data->Value++;
    data->Letter = '!';
    data->Numbers[10] = 987.5f;
    Console.WriteLine ("Updated shared memory");
    Console.ReadLine();
  }
}
The output from each of these programs is as follows:

// First program:

Written to shared memory
Value is 124
Letter is !
11th Number is 987.5

// Second program:

Value is 123
Letter is X
11th Number is 1.45
Updated shared memory
Don’t be put off by the pointers: C++ programmers use them throughout whole applications and are able to get everything working. At least most of the time! This sort of usage is fairly simple by comparison.

As it happens, our example is unsafe—quite literally—for another reason. We’ve not considered the thread-safety (or more precisely, process-safety) issues that arise with two programs accessing the same memory at once. To use this in a production application, we’d need to add the volatile keyword to the Value and Letter fields in the MySharedData struct to prevent fields from being cached by the Just-in-Time (JIT) compiler (or by the hardware in CPU registers). Furthermore, as our interaction with the fields grew beyond the trivial, we would most likely need to protect their access via a cross-process Mutex, just as we would use lock statements to protect access to fields in a multithreaded program. We discussed thread safety in detail in Chapter 21.

fixed and fixed {...}
One limitation of mapping structs directly into memory is that the struct can contain only unmanaged types. If you need to share string data, for instance, you must use a fixed-character array instead. This means manual conversion to and from the string type. Here’s how to do it:

[StructLayout (LayoutKind.Sequential)]
unsafe struct MySharedData
{
  ...
  // Allocate space for 200 chars (i.e., 400 bytes).
  const int MessageSize = 200;
  fixed char message [MessageSize];

  // One would most likely put this code into a helper class:
  public string Message
  {
    get { fixed (char* cp = message) return new string (cp); }
    set
    {
      fixed (char* cp = message)
      {
        int i = 0;
        for (; i < value.Length && i < MessageSize - 1; i++)
          cp [i] = value [i];

        // Add the null terminator
        cp [i] = '\0';
      }
    }
  }
}
NOTE
There’s no such thing as a reference to a fixed array; instead, you get a pointer. When you index into a fixed array, you’re actually performing pointer arithmetic!

With the first use of the fixed keyword, we allocate space, inline, for 200 characters in the struct. The same keyword (somewhat confusingly) has a different meaning when used later in the property definition. It instructs the CLR to pin an object so that should it decide to perform a garbage collection inside the fixed block, it will not move the underlying struct about on the memory heap (because its contents are being iterated via direct memory pointers). Looking at our program, you might wonder how MySharedData could ever shift in memory, given that it resides not on the heap but in the unmanaged world, where the garbage collector has no jurisdiction. The compiler doesn’t know this, however, and is concerned that we might use MySharedData in a managed context, so it insists that we add the fixed keyword to make our unsafe code safe in managed contexts. And the compiler does have a point—here’s all it would take to put MySharedData on the heap:

object obj = new MySharedData();
This results in a boxed MySharedData—on the heap and eligible for transit during garbage collection.

This example illustrates how a string can be represented in a struct mapped to unmanaged memory. For more complex types, you also have the option of using existing serialization code. The one proviso is that the serialized data must never exceed, in length, its allocation of space in the struct; otherwise, the result is an unintended union with subsequent fields.

COM Interoperability
The .NET runtime provides special support for COM, enabling COM objects to be used from .NET, and vice versa. COM is available only on Windows.

The Purpose of COM
COM is an acronym for Component Object Model, a binary standard for interfacing with libraries, released by Microsoft in 1993. The motivation for inventing COM was to enable components to communicate with each other in a language-independent and version-tolerant manner. Before COM, the approach in Windows was to publish DLLs that declared structures and functions using the C programming language. Not only is this approach language specific, but it’s also brittle. The specification of a type in such a library is inseparable from its implementation: even updating a structure with a new field means breaking its specification.

The beauty of COM was to separate the specification of a type from its underlying implementation through a construct known as a COM interface. COM also allowed for the calling of methods on stateful objects—rather than being limited to simple procedure calls.

NOTE
In a way, the .NET programming model is an evolution of the principles of COM programming: the .NET platform also facilitates cross-language development and allows binary components to evolve without breaking applications that depend on them.

The Basics of the COM Type System
The COM type system revolves around interfaces. A COM interface is rather like a .NET interface, but it’s more prevalent because a COM type exposes its functionality only through an interface. In the .NET world, for instance, we could declare a type simply, as follows:

public class Foo
{
  public string Test() => "Hello, world";
}
Consumers of that type can use Foo directly. And if we later changed the implementation of Test(), calling assemblies would not require recompilation. In this respect, .NET separates interface from implementation—without requiring interfaces. We could even add an overload without breaking callers:

  public string Test (string s) => $"Hello, world {s}";
In the COM world, Foo exposes its functionality through an interface to achieve this same decoupling. So, in Foo’s type library, an interface such as this would exist:

public interface IFoo { string Test(); }
(We’ve illustrated this by showing a C# interface—not a COM interface. The principle, however, is the same—although the plumbing is different.)

Callers would then interact with IFoo rather than Foo.

When it comes to adding the overloaded version of Test, life is more complicated with COM than with .NET. First, we would avoid modifying the IFoo interface because this would break binary compatibility with the previous version (one of the principles of COM is that interfaces, once published, are immutable). Second, COM doesn’t allow method overloading. The solution is to instead have Foo implement a second interface:

public interface IFoo2 { string Test (string s); }
(Again, we’ve transliterated this into a .NET interface for familiarity.)

Supporting multiple interfaces is of key importance in making COM libraries versionable.

IUnknown and IDispatch
All COM interfaces are identified with a Globally Unique Identifier (GUID).

The root interface in COM is IUnknown—all COM objects must implement it. This interface has three methods:

AddRef

Release

QueryInterface

AddRef and Release are for lifetime management given that COM uses reference counting rather than automatic garbage collection (COM was designed to work with unmanaged code, where automatic garbage collection isn’t feasible). The Quer⁠yInterface method returns an object reference that supports that interface, if it can do so.

To enable dynamic programming (e.g., scripting and automation), a COM object can also implement IDispatch. This enables dynamic languages to call COM objects in a late-bound manner—rather like dynamic in C# (although only for simple invocations).

Calling a COM Component from C#
The CLR’s built-in support for COM means that you don’t work directly with IUnknown and IDispatch. Instead, you work with CLR objects, and the runtime marshals your calls to the COM world via Runtime-Callable Wrappers (RCWs). The runtime also handles lifetime management by calling AddRef and Release (when the .NET object is finalized) and takes care of the primitive type conversions between the two worlds. Type conversion ensures that each side sees, for example, the integer and string types in their familiar forms.

Additionally, there needs to be some way to access RCWs in a statically typed fashion. This is the job of COM interop types. COM interop types are automatically generated proxy types that expose a .NET member for each COM member. The type library importer tool (tlbimp.exe) generates COM interop types from the command line, based on a COM library that you choose, and compiles them into a COM interop assembly.

NOTE
If a COM component implements multiple interfaces, the tlbimp.exe tool generates a single type that contains a union of members from all interfaces.

You can create a COM interop assembly in Visual Studio by going to the Add Reference dialog box and choosing a library from the COM tab. For example, if you have Microsoft Excel installed, adding a reference to the Microsoft Excel Object Library allows you to interoperate with Excel’s COM classes. Here’s the C# code to create and show a workbook, and then populate a cell in that workbook:

using System;
using Excel = Microsoft.Office.Interop.Excel;

var excel = new Excel.Application();
excel.Visible = true;
excel.WindowState = Excel.XlWindowState.xlMaximized;
Excel.Workbook workBook = excel.Workbooks.Add();
((Excel.Range)excel.Cells[1, 1]).Font.FontStyle = "Bold";
((Excel.Range)excel.Cells[1, 1]).Value2 = "Hello World";
workBook.SaveAs (@"d:\temp.xlsx");
NOTE
It is currently necessary to embed interop types in your application (otherwise, the runtime won’t locate them at runtime). Either click the COM reference in Visual Studio’s Solution Explorer and set the Embed Interop Types property to true in the Properties window, or open your .csproj file and add the following line (in boldface):

<ItemGroup>
  <COMReference Include="Microsoft.Office.Excel.dll">
    ...
    <EmbedInteropTypes>true</EmbedInteropTypes>
  </COMReference>
</ItemGroup>
The Excel.Application class is a COM interop type whose runtime type is an RCW. When we access the Workbooks and Cells properties, we get back more interop types.

Optional Parameters and Named Arguments
Because COM APIs don’t support function overloading, it’s very common to have functions with numerous parameters, many of which are optional. For instance, here’s how you might call an Excel workbook’s Save method:

var missing = System.Reflection.Missing.Value;

workBook.SaveAs (@"d:\temp.xlsx", missing, missing, missing, missing,
  missing, Excel.XlSaveAsAccessMode.xlNoChange, missing, missing,
  missing, missing, missing);
The good news is that the C#’s support for optional parameters is COM-aware, so we can just do this:

workBook.SaveAs (@"d:\temp.xlsx");
(As we stated in Chapter 3, optional parameters are “expanded” by the compiler into the full verbose form.)

Named arguments allow you to specify additional arguments, regardless of their position:

workBook.SaveAs (@"d:\test.xlsx", Password:"foo");
Implicit ref Parameters
Some COM APIs (Microsoft Word, in particular) expose functions that declare every parameter as pass-by-reference—whether or not the function modifies the parameter value. This is because of the perceived performance gain from not copying argument values (the real performance gain is negligible).

Historically, calling such methods from C# has been clumsy because you must specify the ref keyword with every argument, and this prevents the use of optional parameters. For instance, to open a Word document, we used to have to do this:

object filename = "foo.doc";
object notUsed1 = Missing.Value;
object notUsed2 = Missing.Value;
object notUsed3 = Missing.Value;
...
Open (ref filename, ref notUsed1, ref notUsed2, ref notUsed3, ...);
Thanks to implicit ref parameters, you can omit the ref modifier on COM function calls, allowing the use of optional parameters:

word.Open ("foo.doc");
The caveat is that you will get neither a compile-time nor a runtime error if the COM method you’re calling actually does mutate an argument value.

Indexers
The ability to omit the ref modifier has another benefit: it makes COM indexers with ref parameters accessible via ordinary C# indexer syntax. This would otherwise be forbidden because ref/out parameters are not supported with C# indexers.

You can also call COM properties that accept arguments. In the following example, Foo is a property that accepts an integer argument:

myComObject.Foo [123] = "Hello";
Writing such properties yourself in C# is still prohibited: a type can expose an indexer only on itself (the “default” indexer). Therefore, if you wanted to write code in C# that would make the preceding statement legal, Foo would need to return another type that exposed a (default) indexer.

Dynamic Binding
There are two ways that dynamic binding can help when calling COM components.

The first way is in allowing access to a COM component without a COM interop type. To do this, call Type.GetTypeFromProgID with the COM component name to obtain a COM instance, and then use dynamic binding to call members from then on. Of course, there’s no IntelliSense, and compile-time checks are impossible:

Type excelAppType = Type.GetTypeFromProgID ("Excel.Application", true);
dynamic excel = Activator.CreateInstance (excelAppType);
excel.Visible = true;
dynamic wb = excel.Workbooks.Add();
excel.Cells [1, 1].Value2 = "foo";
(The same thing can be achieved, much more clumsily, with reflection instead of dynamic binding.)

NOTE
A variation of this theme is calling a COM component that supports only IDispatch. Such components are quite rare, however.

Dynamic binding can also be useful (to a lesser extent) in dealing with the COM variant type. For reasons due more to poor design than necessity, COM API functions are often peppered with this type, which is roughly equivalent to object in .NET. If you enable “Embed Interop Types” in your project (more on this soon), the runtime will map variant to dynamic, instead of mapping variant to object, avoiding the need for casts. For instance, you could legally do

excel.Cells [1, 1].Font.FontStyle = "Bold";
instead of:

var range = (Excel.Range) excel.Cells [1, 1];
range.Font.FontStyle = "Bold";
The disadvantage of working in this way is that you lose autocompletion, so you must know that a property called Font happens to exist. For this reason, it’s usually easier to dynamically assign the result to its known interop type:

Excel.Range range = excel.Cells [1, 1];
range.Font.FontStyle = "Bold";
As you can see, this saves only five characters over the old-fashioned approach!

The mapping of variant to dynamic is the default, and is a function of enabling Embed Interop Types on a reference.

Embedding Interop Types
We said previously that C# ordinarily calls COM components via interop types that are generated by calling the tlbimp.exe tool (directly or via Visual Studio).

Historically, your only option was to reference interop assemblies just as you would with any other assembly. This could be troublesome because interop assemblies can get quite large with complex COM components. A tiny add-in for Microsoft Word, for instance, requires an interop assembly that is orders of magnitude larger than itself.

Rather than referencing an interop assembly, you have the option of embedding the portions that you use. The compiler analyzes the assembly to work out precisely the types and members that your application requires, and embeds definitions for (just) those types and members directly in your application. This avoids bloat as well as the need to ship an additional file.

To enable this feature, either select the COM reference in Visual Studio’s Solution Explorer and then set Embed Interop Types to true in the Properties window, or edit your .csproj file as we described earlier (see “Calling a COM Component from C#”).

Type Equivalence
The CLR supports type equivalence for linked interop types. This means that if two assemblies each link to an interop type, those types will be considered equivalent if they wrap the same COM type. This holds true even if the interop assemblies to which they linked were generated independently.

NOTE
Type equivalence relies on the TypeIdentifierAttribute attribute in the System.Runtime.InteropServices namespace. The compiler automatically applies this attribute when you link to interop assemblies. COM types are then considered equivalent if they have the same GUID.

Exposing C# Objects to COM
It’s also possible to write classes in C# that can be consumed in the COM world. The CLR makes this possible through a proxy called a COM-Callable Wrapper (CCW). A CCW marshals types between the two worlds (as with an RCW) and implements IUnknown (and optionally IDispatch) as required by the COM protocol. A CCW is lifetime-controlled from the COM side via reference counting (rather than through the CLR’s garbage collector).

You can expose any public class to COM (as an “in-proc” server). To do so, first create an interface, assign it a unique GUID (in Visual Studio, you can use Tools > Create GUID), declare it visible to COM, and then set the interface type:

namespace MyCom
{
  [ComVisible(true)]
  [Guid ("226E5561-C68E-4B2B-BD28-25103ABCA3B1")]  // Change this GUID
  [InterfaceType (ComInterfaceType.InterfaceIsIUnknown)]
  public interface IServer
  {
    int Fibonacci();
  }
}
Next, provide an implementation of your interface, assigning a unique GUID to that implementation:

namespace MyCom
{
  [ComVisible(true)]
  [Guid ("09E01FCD-9970-4DB3-B537-0EC555967DD9")]  // Change this GUID
  public class Server
  {
    public ulong Fibonacci (ulong whichTerm)
    {
      if (whichTerm < 1) throw new ArgumentException ("...");
      ulong a = 0;
      ulong b = 1;
      for (ulong i = 0; i < whichTerm; i++)
      {
        ulong tmp = a;
        a = b;
        b = tmp + b;
      }
      return a;
    }
  }
}
Edit your .csproj file, adding the following line:

<PropertyGroup>
  <EnableComHosting>true</EnableComHosting>
</PropertyGroup>
Now, when you build your project, an additional file is generated, MyCom.com⁠host.dll, which can be registered for COM interop. (Keep in mind that the file will always be 32 bit or 64 bit depending on your project configuration: there’s no such thing as “Any CPU” in this scenario.) From an elevated command prompt, switch to the directory holding your DLL and run regsvr32 MyCom.comhost.dll.

You can then consume your COM component from most COM-capable languages. For example, you can create this Visual Basic Script in a text editor and run it by double-clicking the file in Windows Explorer, or by starting it from a command prompt as you would a program:

REM Save file as ComClient.vbs
Dim obj
Set obj = CreateObject("MyCom.Server")

result = obj.Fibonacci(12)
Wscript.Echo result
Note that .NET Framework cannot be loaded into the same process as .NET 5+ or .NET Core. Therefore, a .NET 5+ COM server cannot be loaded into a .NET Framework COM client process, or vice versa.

Enabling Registry-Free COM
Traditionally, COM adds type information to the registry. Registry-free COM uses a manifest file instead of the registry to control object activation. To enable this feature, add the following line (in boldface) to your .csproj file:

<PropertyGroup>
  <TargetFramework>netcoreapp3.0</TargetFramework>
  <EnableComHosting>true</EnableComHosting>
  <EnableRegFreeCom>true</EnableRegFreeCom>
</PropertyGroup>
Your build will then generate MyCom.X.manifest.

NOTE
There is no support in .NET 5+ for generating a COM type library (*.tlb). You can manually write an IDL (Interface Definition Language) file or C++ header for the native declarations in your interface.


Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


24. Native and COM Interoperability
25. Regular Expressions
Index
25h 47m remaining
Chapter 25. Regular Expressions
The regular expressions language identifies character patterns. The .NET types supporting regular expressions are based on Perl 5 regular expressions and support both search and search/replace functionality.

Regular expressions are used for tasks such as:

Validating text input such as passwords and phone numbers

Parsing textual data into more structured forms (e.g., a NuGet version string)

Replacing patterns of text in a document (e.g., whole words only)

This chapter is split into both conceptual sections teaching the basics of regular expressions in .NET, and reference sections describing the regular expressions language.

All regular expression types are defined in System.Text.RegularExpressions.

NOTE
The samples in this chapter are all preloaded into LINQPad, which also includes an interactive RegEx tool (press Ctrl+Shift+F1). An online tool is available at http://regexstorm.net/tester.

Regular Expression Basics
One of the most common regular expression operators is a quantifier. ? is a quantifier that matches the preceding item 0 or 1 time. In other words, ? means optional. An item is either a single character or a complex structure of characters in square brackets. For example, the regular expression "colou?r" matches color and colour, but not colouur:


Console.WriteLine (Regex.Match ("color",   @"colou?r").Success);  // True
Console.WriteLine (Regex.Match ("colour",  @"colou?r").Success);  // True
Console.WriteLine (Regex.Match ("colouur", @"colou?r").Success);  // False
Regex.Match searches within a larger string. The object that it returns has properties for the Index and Length of the match as well as the actual Value matched:


Match m = Regex.Match ("any colour you like", @"colou?r");

Console.WriteLine (m.Success);     // True
Console.WriteLine (m.Index);       // 4
Console.WriteLine (m.Length);      // 6
Console.WriteLine (m.Value);       // colour
Console.WriteLine (m.ToString());  // colour
You can think of Regex.Match as a more powerful version of the string’s IndexOf method. The difference is that it searches for a pattern rather than a literal string.

The IsMatch method is a shortcut for calling Match and then testing the Success property.

The regular expressions engine works from left to right by default, so only the leftmost match is returned. You can use the NextMatch method to return more matches:


Match m1 = Regex.Match ("One color? There are two colours in my head!",
                        @"colou?rs?");
Match m2 = m1.NextMatch();
Console.WriteLine (m1);         // color
Console.WriteLine (m2);         // colours
The Matches method returns all matches in an array. We can rewrite the preceding example, as follows:


foreach (Match m in Regex.Matches
          ("One color? There are two colours in my head!", @"colou?rs?"))
  Console.WriteLine (m);
Another common regular expressions operator is the alternator, expressed with a vertical bar, |. An alternator expresses alternatives. The following matches “Jen”, “Jenny”, and “Jennifer”:


Console.WriteLine (Regex.IsMatch ("Jenny", "Jen(ny|nifer)?"));  // True
The brackets around an alternator separate the alternatives from the rest of the expression.

NOTE
You can specify a timeout when matching regular expressions. If a match operation takes longer than the specified TimeSpan, a RegexMatchTimeoutException is thrown. This can be useful if your program processes user-supplied regular expressions because it prevents malformed regular expressions from infinitely spinning.

Compiled Regular Expressions
In some of the preceding examples, we called a static RegEx method repeatedly with the same pattern. An alternative approach in these cases is to instantiate a Regex object with the pattern and RegexOptions.Compiled and then call instance methods:


Regex r = new Regex (@"sausages?", RegexOptions.Compiled);
Console.WriteLine (r.Match ("sausage"));   // sausage
Console.WriteLine (r.Match ("sausages"));  // sausages
RegexOptions.Compiled instructs the RegEx instance to use lightweight code generation (DynamicMethod in Reflection.Emit) to dynamically build and compile code tailored to that particular regular expression. This results in faster matching, at the expense of an initial compilation cost.

You can also instantiate a Regex object without using RegexOptions.Compiled. A Regex instance is immutable.

NOTE
The regular expressions engine is fast. Even without compilation, a simple match typically takes less than a microsecond.

RegexOptions
The RegexOptions flags enum lets you tweak matching behavior. A common use for RegexOptions is to perform a case-insensitive search:


Console.WriteLine (Regex.Match ("a", "A", RegexOptions.IgnoreCase)); // a
This applies the current culture’s rules for case equivalence. The CultureInvariant flag lets you request the invariant culture instead:


Console.WriteLine (Regex.Match ("a", "A", RegexOptions.IgnoreCase
                                        | RegexOptions.CultureInvariant));
You can activate most of the RegexOptions flags within a regular expression itself, using a single-letter code, as follows:


Console.WriteLine (Regex.Match ("a", @"(?i)A"));                     // a
You can turn options on and off throughout an expression:


Console.WriteLine (Regex.Match ("AAAa", @"(?i)a(?-i)a"));            // Aa
Another useful option is IgnorePatternWhitespace or (?x). This allows you to insert whitespace to make a regular expression more readable—without the whitespace being taken literally.

The NonBacktracking option (from .NET 7) instructs the regex engine to use a forwards-only matching algorithm. This usually results in slower performance and disables some advanced features such as lookahead or lookbehind. However, it also prevents malformed or maliciously constructed expressions from taking near-infinite time, mitigating a potential denial-of-service attack when processing user-supplied regular expressions (a ReDOS attack). Specifying a timeout is also useful in this scenario.

Table 25-1 lists all RegExOptions values along with their single-letter codes.

Table 25-1. Regular expression options
Enum value	Regular expressions code	Description
None	 	 
IgnoreCase	i	Ignores case (by default, regular expressions are case sensitive)
Multiline	m	Changes ^ and $ so that they match the start/end of a line instead of start/end of the string
ExplicitCapture	n	Captures only explicitly named or explicitly numbered groups (see “Groups”)
Compiled	 	Forces compilation to IL (see “Compiled Regular Expressions”)
Singleline	s	Makes . match every character (instead of matching every character except \n)
IgnorePatternWhitespace	x	Eliminates unescaped whitespace from the pattern
RightToLeft	r	Searches from right to left; can’t be specified midstream
ECMAScript	 	Forces ECMA compliance (by default, the implementation is not ECMA compliant)
CultureInvariant	 	Turns off culture-specific behavior for string comparisons
NonBacktracking	 	Disables backtracking to ensure predictable (albeit slower) performance
Character Escapes
Regular expressions have the following metacharacters, which have a special rather than literal meaning:

\ * + ? | { [ () ^ $ . #

To use a metacharacter literally, you must prefix, or escape, the character with a backslash. In the following example, we escape the ? character to match the string "what?":


Console.WriteLine (Regex.Match ("what?", @"what\?")); // what? (correct)
Console.WriteLine (Regex.Match ("what?", @"what?"));  // what  (incorrect)
NOTE
If the character is inside a set (square brackets), this rule does not apply, and the metacharacters are interpreted literally. We discuss sets in the following section.

The Regex’s Escape and Unescape methods convert a string containing regular expression metacharacters by replacing them with escaped equivalents, and vice versa:


Console.WriteLine (Regex.Escape   (@"?"));     // \?
Console.WriteLine (Regex.Unescape (@"\?"));    // ?>
All the regular expression strings in this chapter are expressed with the C# @ literal. This is to bypass C#’s escape mechanism, which also uses the backslash. Without the @, a literal backslash would require four backslashes:


Console.WriteLine (Regex.Match ("\\", "\\\\"));    // \
Unless you include the (?x) option, spaces are treated literally in regular expressions:


Console.Write (Regex.IsMatch ("hello world", @"hello world"));  // True
Character Sets
Character sets act as wildcards for a particular set of characters.

Expression	Meaning	Inverse (“not”)
[abcdef]	Matches a single character in the list.	[^abcdef]
[a-f]	Matches a single character in a range.	[^a-f]
\d	Matches anything in the Unicode digits category. In ECMAScript mode, [0-9].	\D
\w	Matches a word character (by default, varies according to CultureInfo.CurrentCulture; for example, in English, same as [a-zA-Z_0-9]).	\W
\s	Matches a whitespace character; that is, anything for which char.IsWhiteSpace returns true (including Unicode spaces). In ECMAScript mode, [\n\r\t\f\v ].	\S
\p{category}	Matches a character in a specified category.	\P
.	(Default mode) Matches any character except \n.	\n
.	(SingleLine mode) Matches any character.	\n
To match exactly one of a set of characters, put the character set in square brackets:


Console.Write (Regex.Matches ("That is that.", "[Tt]hat").Count);   // 2
To match any character except those in a set, put the set in square brackets with a ^ symbol before the first character:


Console.Write (Regex.Match ("quiz qwerty", "q[^aeiou]").Index);    // 5
You can specify a range of characters by using a hyphen. The following regular expression matches a chess move:


Console.Write (Regex.Match ("b1-c4", @"[a-h]\d-[a-h]\d").Success);  // True
\d indicates a digit character, so \d will match any digit. \D matches any nondigit character.

\w indicates a word character, which includes letters, numbers, and the underscore. \W matches any nonword character. These work as expected for non-English letters, too, such as Cyrillic.

. matches any character except \n (but allows \r).

\p matches a character in a specified category, such as {Lu} for uppercase letter or {P} for punctuation (we list the categories in the reference section later in the chapter):


Console.Write (Regex.IsMatch ("Yes, please", @"\p{P}"));   // True
We will find more uses for \d, \w, and . when we combine them with quantifiers.

Quantifiers
Quantifiers match an item a specified number of times.

Quantifier	Meaning
*	Zero or more matches
+	One or more matches
?	Zero or one match
{n}	Exactly n matches
{n,}	At least n matches
{n,m}	Between n and m matches
The * quantifier matches the preceding character or group zero or more times. The following matches cv.docx, along with any numbered versions of the same file (e.g., cv2.docx, cv15.docx):


Console.Write (Regex.Match ("cv15.docx", @"cv\d*\.docx").Success);  // True
Notice that we must escape the period in the file extension using a backslash.

The following allows anything between cv and .docx and is equivalent to dir cv*.docx:


Console.Write (Regex.Match ("cvjoint.docx", @"cv.*\.docx").Success); // True
The + quantifier matches the preceding character or group one or more times. For example:


Console.Write (Regex.Matches ("slow! yeah slooow!", "slo+w").Count);  // 2
The {} quantifier matches a specified number (or range) of repetitions. The following matches a blood pressure reading:


Regex bp = new Regex (@"\d{2,3}/\d{2,3}");
Console.WriteLine (bp.Match ("It used to be 160/110"));  // 160/110
Console.WriteLine (bp.Match ("Now it's only 115/75"));   // 115/75
Greedy Versus Lazy Quantifiers
By default, quantifiers are greedy, as opposed to lazy. A greedy quantifier repeats as many times as it can before advancing. A lazy quantifier repeats as few times as it can before advancing. You can make any quantifier lazy by suffixing it with the ? symbol. To illustrate the difference, consider the following HTML fragment:


string html = "<i>By default</i> quantifiers are <i>greedy</i> creatures";
Suppose that we want to extract the two phrases in italics. If we execute the following


foreach (Match m in Regex.Matches (html, @"<i>.*</i>"))
  Console.WriteLine (m);
the result is not two matches, but a single match:


<i>By default</i> quantifiers are <i>greedy</i>
The problem is that our * quantifier greedily repeats as many times as it can before matching </i>. So, it passes right by the first </i>, stopping only at the final </i> (the last point at which the rest of the expression can still match).

If we make the quantifier lazy, the * bails out at the first point at which the rest of the expression can match:


foreach (Match m in Regex.Matches (html, @"<i>.*?</i>"))
  Console.WriteLine (m);
Here’s the result:


<i>By default</i>
<i>greedy</i>
Zero-Width Assertions
The regular expressions language lets you place conditions on what should occur before or after a match, through lookbehind, lookahead, anchors, and word boundaries. These are called zero-width assertions because they don’t increase the width (or length) of the match itself.

Lookahead and Lookbehind
The (?=expr) construct checks whether the text that follows matches expr, without including expr in the result. This is called positive lookahead. In the following example, we look for a number followed by the word “miles”:


Console.WriteLine (Regex.Match ("say 25 miles more", @"\d+\s(?=miles)"));

OUTPUT: 25
Notice that the word “miles” was not returned in the result, even though it was required to satisfy the match.

After a successful lookahead, matching continues as though the sneak preview never took place. So, if we append .* to our expression like this:


Console.WriteLine (Regex.Match ("say 25 miles more", @"\d+\s(?=miles).*"));
the result is 25 miles more.

Lookahead can be useful in enforcing rules for a strong password. Suppose that a password must be at least six characters and contain at least one digit. With a lookup, we could achieve this, as follows:


string password = "...";
bool ok = Regex.IsMatch (password, @"(?=.*\d).{6,}");
This first performs a lookahead to ensure that a digit occurs somewhere in the string. If satisfied, it returns to its position before the sneak preview began and matches six or more characters. (In “Cookbook Regular Expressions”, we include a more substantial password validation example.)

The opposite is the negative lookahead construct, (?!expr). This requires that the match not be followed by expr. The following expression matches “good”—unless “however” or “but” appears later in the string:


string regex = "(?i)good(?!.*(however|but))";
Console.WriteLine (Regex.IsMatch ("Good work! But...",  regex));  // False
Console.WriteLine (Regex.IsMatch ("Good work! Thanks!", regex));  // True
The (?<=expr) construct denotes positive lookbehind and requires that a match be preceded by a specified expression. The opposite construct, (?<!expr), denotes negative lookbehind and requires that a match not be preceded by a specified expression. For example, the following matches “good”—unless “however” appears earlier in the string:


string regex = "(?i)(?<!however.*)good";
Console.WriteLine (Regex.IsMatch ("However good, we...", regex)); // False
Console.WriteLine (Regex.IsMatch ("Very good, thanks!", regex));  // True
We could improve these examples by adding word boundary assertions, which we introduce shortly.

Anchors
The anchors ^ and $ match a particular position. By default:

^
Matches the start of the string
$
Matches the end of the string
NOTE
^ has two context-dependent meanings: an anchor and a character class negator.

$ has two context-dependent meanings: an anchor and a replacement group denoter.

For example:


Console.WriteLine (Regex.Match ("Not now", "^[Nn]o"));   // No
Console.WriteLine (Regex.Match ("f = 0.2F", "[Ff]$"));   // F
When you specify RegexOptions.Multiline or include (?m) in the expression:

^ matches the start of the string or line (directly after a \n).

$ matches the end of the string or line (directly before a \n).

There’s a catch to using $ in multiline mode: a new line in Windows is nearly always denoted with \r\n rather than just \n. This means that for $ to be useful for Windows files, you must usually match the \r, as well, with a positive lookahead:


(?=\r?$)
The positive lookahead ensures that \r doesn’t become part of the result. The following matches lines that end in ".txt":


string fileNames = "a.txt" + "\r\n" + "b.docx" + "\r\n" + "c.txt";
string r = @".+\.txt(?=\r?$)";
foreach (Match m in Regex.Matches (fileNames, r, RegexOptions.Multiline))
  Console.Write (m + " ");

OUTPUT: a.txt c.txt
The following matches all empty lines in string s:


MatchCollection emptyLines = Regex.Matches (s, "^(?=\r?$)",
                                            RegexOptions.Multiline);
The following matches all lines that are either empty or contain only whitespace:


MatchCollection blankLines = Regex.Matches (s, "^[ \t]*(?=\r?$)",
                                            RegexOptions.Multiline);
NOTE
Because an anchor matches a position rather than a character, specifying an anchor on its own matches an empty string:


Console.WriteLine (Regex.Match ("x", "$").Length);   // 0
Word Boundaries
The word boundary assertion \b matches where word characters (\w) adjoin either:

Nonword characters (\W)

The beginning/end of the string (^ and $)

\b is often used to match whole words:


foreach (Match m in Regex.Matches ("Wedding in Sarajevo", @"\b\w+\b"))
  Console.WriteLine (m);

Wedding
in
Sarajevo
The following statements highlight the effect of a word boundary:


int one = Regex.Matches ("Wedding in Sarajevo", @"\bin\b").Count; // 1
int two = Regex.Matches ("Wedding in Sarajevo", @"in").Count;     // 2
The next query uses positive lookahead to return words followed by “(sic)”:


string text = "Don't loose (sic) your cool";
Console.Write (Regex.Match (text, @"\b\w+\b\s(?=\(sic\))"));  // loose
Groups
Sometimes, it’s useful to separate a regular expression into a series of subexpressions, or groups. For instance, consider the following regular expression that represents a US phone number such as 206-465-1918:


\d{3}-\d{3}-\d{4}
Suppose that we want to separate this into two groups: area code and local number. We can achieve this by using parentheses to capture each group:


(\d{3})-(\d{3}-\d{4})
We then retrieve the groups programmatically:


Match m = Regex.Match ("206-465-1918", @"(\d{3})-(\d{3}-\d{4})");

Console.WriteLine (m.Groups[1]);   // 206
Console.WriteLine (m.Groups[2]);   // 465-1918
The zeroth group represents the entire match. In other words, it has the same value as the match’s Value:


Console.WriteLine (m.Groups[0]);   // 206-465-1918
Console.WriteLine (m);             // 206-465-1918
Groups are part of the regular expressions language itself. This means that you can refer to a group within a regular expression. The \n syntax lets you index the group by group number n within the expression. For example, the expression (\w)ee\1 matches deed and peep. In the following example, we find all words in a string starting and ending in the same letter:


foreach (Match m in Regex.Matches ("pop pope peep", @"\b(\w)\w+\1\b"))
  Console.Write (m + " ");  // pop peep
The brackets around the \w instruct the regular expressions engine to store the submatch in a group (in this case, a single letter) so that it can be used later. We refer to that group later using \1, meaning the first group in the expression.

Named Groups
In a long or complex expression, it can be easier to work with groups by name rather than index. Here’s a rewrite of the previous example, using a group that we name 'letter':


string regEx =
  @"\b"             +  // word boundary
  @"(?'letter'\w)"  +  // match first letter, and name it 'letter'
  @"\w+"            +  // match middle letters
  @"\k'letter'"     +  // match last letter, denoted by 'letter'
  @"\b";               // word boundary

foreach (Match m in Regex.Matches ("bob pope peep", regEx))
  Console.Write (m + " ");  // bob peep
Here’s how to name a captured group:


(?'group-name'group-expr)  or  (?<group-name>group-expr)
And here’s how to refer to a group:


\k'group-name'  or  \k<group-name>
The following example matches a simple (non-nested) XML/HTML element by looking for start and end nodes with a matching name:


string regFind =
  @"<(?'tag'\w+?).*>" +  // lazy-match first tag, and name it 'tag'
  @"(?'text'.*?)"     +  // lazy-match text content, name it 'text'
  @"</\k'tag'>";         // match last tag, denoted by 'tag'

Match m = Regex.Match ("<h1>hello</h1>", regFind);
Console.WriteLine (m.Groups ["tag"]);          // h1
Console.WriteLine (m.Groups ["text"]);         // hello
Allowing for all possible variations in XML structure, such as nested elements, is more complex. The .NET regular expressions engine has a sophisticated extension called “matched balanced constructs” that can assist with nested tags—information on this is available on the internet and in Mastering Regular Expressions (O’Reilly) by Jeffrey E. F. Friedl.

Replacing and Splitting Text
The RegEx.Replace method works like string.Replace except that it uses a regular expression.

The following replaces “cat” with “dog”. Unlike with string.Replace, “catapult” won’t change into “dogapult”, because we match on word boundaries:


string find = @"\bcat\b";
string replace = "dog";
Console.WriteLine (Regex.Replace ("catapult the cat", find, replace));

OUTPUT: catapult the dog
The replacement string can reference the original match with the $0 substitution construct. The following example wraps numbers within a string in angle brackets:


string text = "10 plus 20 makes 30";
Console.WriteLine (Regex.Replace (text, @"\d+", @"<$0>"));

OUTPUT: <10> plus <20> makes <30>
You can access any captured groups with $1, $2, $3, and so on, or ${name} for a named group. To illustrate how this can be useful, consider the regular expression in the previous section that matched a simple XML element. By rearranging the groups, we can form a replacement expression that moves the element’s content into an XML attribute:


string regFind =
  @"<(?'tag'\w+?).*>" +  // lazy-match first tag, and name it 'tag'
  @"(?'text'.*?)"     +  // lazy-match text content, name it 'text'
  @"</\k'tag'>";         // match last tag, denoted by 'tag'

string regReplace =
  @"<${tag}"         +  // <tag
  @"value="""        +  // value="
  @"${text}"         +  // text
  @"""/>";              // "/>

Console.Write (Regex.Replace ("<msg>hello</msg>", regFind, regReplace));
Here’s the result:


<msg value="hello"/>
MatchEvaluator Delegate
Replace has an overload that takes a MatchEvaluator delegate, which is invoked per match. This allows you to delegate the content of the replacement string to C# code when the regular expressions language isn’t expressive enough:


Console.WriteLine (Regex.Replace ("5 is less than 10", @"\d+",
                   m => (int.Parse (m.Value) * 10).ToString()) );

OUTPUT: 50 is less than 100
In “Cookbook Regular Expressions”, we show how to use a MatchEva⁠luator to escape Unicode characters appropriately for HTML.

Splitting Text
The static Regex.Split method is a more powerful version of the string.Split method, with a regular expression denoting the separator pattern. In this example, we split a string, where any digit counts as a separator:


foreach (string s in Regex.Split ("a5b7c", @"\d"))
  Console.Write (s + " ");     // a b c
The result, here, doesn’t include the separators themselves. You can include the separators, however, by wrapping the expression in a positive lookahead. The following splits a camel-case string into separate words:


foreach (string s in Regex.Split ("oneTwoThree", @"(?=[A-Z])"))
  Console.Write (s + " ");    // one Two Three
Cookbook Regular Expressions
Recipes
Matching US Social Security number/phone number

string ssNum = @"\d{3}-\d{2}-\d{4}";

Console.WriteLine (Regex.IsMatch ("123-45-6789", ssNum));      // True

string phone = @"(?x)
  ( \d{3}[-\s] | \(\d{3}\)\s? )
    \d{3}[-\s]?
    \d{4}";

Console.WriteLine (Regex.IsMatch ("123-456-7890",   phone));   // True
Console.WriteLine (Regex.IsMatch ("(123) 456-7890", phone));   // True
Extracting “name = value” pairs (one per line)
Note that this starts with the multiline directive (?m):


string r = @"(?m)^\s*(?'name'\w+)\s*=\s*(?'value'.*)\s*(?=\r?$)";

string text =
  @"id = 3
    secure = true
    timeout = 30";

foreach (Match m in Regex.Matches (text, r))
  Console.WriteLine (m.Groups["name"] + " is " + m.Groups["value"]);
id is 3 secure is true timeout is 30
Strong password validation
The following checks whether a password has at least six characters and whether it contains a digit, symbol, or punctuation mark:


string r = @"(?x)^(?=.* ( \d | \p{P} | \p{S} )).{6,}";

Console.WriteLine (Regex.IsMatch ("abc12", r));     // False
Console.WriteLine (Regex.IsMatch ("abcdef", r));    // False
Console.WriteLine (Regex.IsMatch ("ab88yz", r));    // True
Lines of at least 80 characters

string r = @"(?m)^.{80,}(?=\r?$)";

string fifty = new string ('x', 50);
string eighty = new string ('x', 80);

string text = eighty + "\r\n" + fifty + "\r\n" + eighty;

Console.WriteLine (Regex.Matches (text, r).Count);   // 2
Parsing dates/times (N/N/N H:M:S AM/PM)
This expression handles a variety of numeric date formats—and works whether the year comes first or last. The (?x) directive improves readability by allowing whitespace; the (?i) switches off case sensitivity (for the optional AM/PM designator). You can then access each component of the match through the Groups collection:


string r = @"(?x)(?i)
 (\d{1,4}) [./-]
 (\d{1,2}) [./-]
 (\d{1,4}) [\sT]
 (\d+):(\d+):(\d+) \s? (A\.?M\.?|P\.?M\.?)?";

string text = "01/02/2008 5:20:50 PM";

foreach (Group g in Regex.Match (text, r).Groups)
  Console.WriteLine (g.Value + " ");
01/02/2008 5:20:50 PM 01 02 2008 5 20 50 PM
(Of course, this doesn’t verify that the date/time is correct.)

Matching Roman numerals

string r =
  @"(?i)\bm*"         +
  @"(d?c{0,3}|c[dm])" +
  @"(l?x{0,3}|x[lc])" +
  @"(v?i{0,3}|i[vx])" +
  @"\b";

Console.WriteLine (Regex.IsMatch ("MCMLXXXIV", r));   // True
Removing repeated words
Here, we capture a named group called dupe:


string r = @"(?'dupe'\w+)\W\k'dupe'";

string text = "In the the beginning...";
Console.WriteLine (Regex.Replace (text, r, "${dupe}"));

In the beginning
Word count

string r = @"\b(\w|[-'])+\b";

string text = "It's all mumbo-jumbo to me";
Console.WriteLine (Regex.Matches (text, r).Count);   // 5
Matching a GUID

string r =
  @"(?i)\b"           +
  @"[0-9a-fA-F]{8}\-" +
  @"[0-9a-fA-F]{4}\-" +
  @"[0-9a-fA-F]{4}\-" +
  @"[0-9a-fA-F]{4}\-" +
  @"[0-9a-fA-F]{12}"  +
  @"\b";

string text = "Its key is {3F2504E0-4F89-11D3-9A0C-0305E82C3301}.";
Console.WriteLine (Regex.Match (text, r).Index);                    // 12
Parsing an XML/HTML tag
Regex is useful for parsing HTML fragments—particularly when the document might be imperfectly formed:


string r =
  @"<(?'tag'\w+?).*>"  +  // lazy-match first tag, and name it 'tag'
  @"(?'text'.*?)"      +  // lazy-match text content, name it 'textd'
  @"</\k'tag'>";          // match last tag, denoted by 'tag'

string text = "<h1>hello</h1>";

Match m = Regex.Match (text, r);

Console.WriteLine (m.Groups ["tag"]);       // h1
Console.WriteLine (m.Groups ["text"]);      // hello
Splitting a camel-cased word
This requires a positive lookahead to include the uppercase separators:


string r = @"(?=[A-Z])";

foreach (string s in Regex.Split ("oneTwoThree", r))
  Console.Write (s + " ");    // one Two Three
Obtaining a legal filename

string input = "My \"good\" <recipes>.txt";

char[] invalidChars = System.IO.Path.GetInvalidFileNameChars();
string invalidString = Regex.Escape (new string (invalidChars));

string valid = Regex.Replace (input, "[" + invalidString + "]", "");
Console.WriteLine (valid);

My good recipes.txt
Escaping Unicode characters for HTML

string htmlFragment = "© 2007";

string result = Regex.Replace (htmlFragment, @"[\u0080-\uFFFF]",
                m => @"&#" + ((int)m.Value[0]).ToString() + ";");

Console.WriteLine (result);        // &#169; 2007
Unescaping characters in an HTTP query string

string sample = "C%23 rocks";

string result = Regex.Replace (
    sample,
    @"%[0-9a-f][0-9a-f]", 
    m => ((char) Convert.ToByte (m.Value.Substring (1), 16)).ToString(),
    RegexOptions.IgnoreCase
);

Console.WriteLine (result);   // C# rocks
Parsing Google search terms from a web stats log
You should use this in conjunction with the previous example to unescape characters in the query string:


string sample = 
  "http://google.com/search?hl=en&q=greedy+quantifiers+regex&btnG=Search";

Match m = Regex.Match (sample, @"(?<=google\..+search\?.*q=).+?(?=(&|$))");

string[] keywords = m.Value.Split (
  new[] { '+' }, StringSplitOptions.RemoveEmptyEntries);

foreach (string keyword in keywords)
  Console.Write (keyword + " ");       // greedy quantifiers regex
Regular Expressions Language Reference
Tables 25-2 through 25-12 summarize the regular expressions grammar and syntax supported in the .NET implementation.

Table 25-2. Character escapes
Escape code sequence	Meaning	Hexadecimal equivalent
\a	Bell	\u0007
\b	Backspace	\u0008
\t	Tab	\u0009
\r	Carriage return	\u000A
\v	Vertical tab	\u000B
\f	Form feed	\u000C
\n	Newline	\u000D
\e	Escape	\u001B
\nnn	ASCII character nnn as octal (e.g., \n052)	 
\xnn	ASCII character nn as hex (e.g., \x3F)	 
\cl	ASCII control character l (e.g., \cG for Ctrl-G)	 
\unnnn	Unicode character nnnn as hex (e.g., \u07DE)	 
\symbol	A nonescaped symbol	 
Special case: within a regular expression, \b means word boundary, except in a [ ] set, in which \b means the backspace character.

Table 25-3. Character sets
Expression	Meaning	Inverse (“not”)
[abcdef]	Matches a single character in the list	[^abcdef]
[a-f]	Matches a single character in a range	[^a-f]
\d	Matches a decimal digit
Same as [0-9]	\D
\w	Matches a word character (by default, varies according to CultureInfo.CurrentCulture; for example, in English, same as [a-zA-Z_0-9])	\W
\s	Matches a whitespace character
Same as [\n\r\t\f\v ]	\S
\p{category}	Matches a character in a specified category (see Table 25-4)	\P
.	(Default mode) Matches any character except \n	\n
.	(SingleLine mode) Matches any character	\n
Table 25-4. Character categories
Quantifier	Meaning
\p{L}	Letters
\p{Lu}	Uppercase letters
\p{Ll}	Lowercase letters
\p{N}	Numbers
\p{P}	Punctuation
\p{M}	Diacritic marks
\p{S}	Symbols
\p{Z}	Separators
\p{C}	Control characters
Table 25-5. Quantifiers
Quantifier	Meaning
*	Zero or more matches
+	One or more matches
?	Zero or one match
{n}	Exactly n matches
{n,}	At least n matches
{n,m}	Between n and m matches
The ? suffix can be applied to any of the quantifiers to make them lazy rather than greedy.

Table 25-6. Substitutions
Expression	Meaning
$0	Substitutes the matched text
$group-number	Substitutes an indexed group-number within the matched text
${group-name}	Substitutes a text group-name within the matched text
Substitutions are specified only within a replacement pattern.

Table 25-7. Zero-width assertions
Expression	Meaning
^	Start of string (or line in multiline mode)
$	End of string (or line in multiline mode)
\A	Start of string (ignores multiline mode)
\z	End of string (ignores multiline mode)
\Z	End of line or string
\G	Where search started
\b	On a word boundary
\B	Not on a word boundary
(?=expr)	Continue matching only if expression expr matches on right (positive lookahead)
(?!expr)	Continue matching only if expression expr doesn’t match on right (negative lookahead)
(?<=expr)	Continue matching only if expression expr matches on left (positive lookbehind)
(?<!expr)	Continue matching only if expression expr doesn’t match on left (negative lookbehind)
(?>expr)	Subexpression expr is matched once and not backtracked
Table 25-8. Grouping constructs
Syntax	Meaning
(expr)	Capture matched expression expr into indexed group
(?number)	Capture matched substring into a specified group number
(?'name')	Capture matched substring into group name
(?'name1-name2')	Undefine name2 and store interval and current group into name1; if name2 is undefined, matching backtracks
(?:expr)	Noncapturing group
Table 25-9. Back references
Parameter syntax	Meaning
\index	Reference a previously captured group by index
\k<name>	Reference a previously captured group by name
Table 25-10. Alternation
Expression syntax	Meaning
|	Logical or
(?(expr)yes|no)	Matches yes if expression matches; otherwise, matches no (no is optional)
(?(name)yes|no)	Matches yes if named group has a match; otherwise, matches no (no is optional)
Table 25-11. Miscellaneous constructs
Expression syntax	Meaning
(?#comment)	Inline comment
#comment	Comment to end of line (works only in IgnorePatternWhitespace mode)
Table 25-12. Regular expression options
Option	Meaning
(?i)	Case-insensitive match (“ignore” case)
(?m)	Multiline mode; changes ^ and $ so that they match beginning and end of any line
(?n)	Captures only explicitly named or numbered groups
(?c)	Compiles to Intermediate Language
(?s)	Single-line mode; changes meaning of “.” so that it matches every character
(?x)	Eliminates unescaped whitespace from the pattern
(?r)	Searches from right to left; can’t be specified midstream

Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue
Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


25. Regular Expressions
Index
About the Author
25h 47m remaining
Index
Symbols
! (logical negation operator), Equality and Comparison Operators, Conditional Compilation
! (null-forgiving operator), The Null-Forgiving Operator
!= (inequality operator), Equality and Comparison Operators, Equality operators (== and !=), == and !=, Overloading == and !=
# (hash), Preprocessor Directives, Conditional Compilation
$ (dollar sign)
in regular expressions, Anchors
preceding interpolated strings, String interpolation, String.Format and composite format strings
% (remainder operator), Arithmetic Operators
& (ampersand)
address-of operator, Pointer Basics
bitwise AND operator, Bitwise operators, Flags Enums
bool? with & operator, bool? with & and | Operators
in parameter type names, ref and out parameter type names
&& (conditional and operator), Conditional Operators, Conditional Compilation
' (quote, single)
enclosing char literals, Strings and Characters
following generic type names, Generic type names
() (parentheses), Literals, Punctuators, and Operators, Primary Expressions
(?x) IgnorePatternWhitespace, RegexOptions
* (asterisk)
as deference operator, Pointer Basics
as multiplication operator, A First C# Program, Literals, Punctuators, and Operators, Arithmetic Operators
in regular expressions, Quantifiers
+ (plus sign)
addition operator, Arithmetic Operators
combining delegate instances, Multicast Delegates
in nested type names, Nested type names
in regular expressions, Quantifiers
string concatenation operator, String concatenation
++ (increment operator), Increment and Decrement Operators
+= (add to self) operator
combining delegate instances, Multicast Delegates
delegate variable assignment, Multicast Delegates
event accessors, Event Accessors
subscribing to events, Events
+∞(positive infinity), Special Float and Double Values
, (comma), Rectangular arrays
- (hyphen), Character Sets
- (minus sign)
negative infinity (−∞), Special Float and Double Values
negative zero (−0), Special Float and Double Values
removing delegate instances, Multicast Delegates
subtraction operator, Arithmetic Operators
- (pointer-to-member operator), Pointer Basics, The Pointer-to-Member Operator
-- (decrement operator), Increment and Decrement Operators
-= operator
event accessors, Event Accessors
removing delegate instances, Multicast Delegates
unsubscribing from events, Events
. (period), Literals, Punctuators, and Operators, Primary Expressions
/ (forward slash)
as division operator, Arithmetic Operators
trailing in URIs, URIs
/* */ (multiline comments), Comments, XML Documentation
// (forward slash, double), A First C# Program, Comments
/// (documentation comments), XML Documentation
: (colon), in named arguments, Named arguments
:: (namespace alias qualification), Namespace alias qualifiers
; (semicolon), A First C# Program, Literals, Punctuators, and Operators
< (comparison operator), Order Comparison, < and >
<< (shift left operator), Bitwise operators
= (equal sign), as assignment operator, Literals, Punctuators, and Operators, Assignment Expressions
= (expression-bodied members), Operator Functions
== (equality operator), Literals, Punctuators, and Operators, == and !=
Boolean values and, Equality and Comparison Operators
Equals method versus, When Equals and == are not equal
NaN value and, Special Float and Double Values
operator lifting and, Equality operators (== and !=)
overloading, Overloading Equality and Comparison Operators, Overloading == and !=
records and, Records and Equality Comparison
string equality comparison, String comparisons, Comparing Strings
=> (expression-bodied members), Instance Constructors, Expression-bodied properties, Finalizers
=> (fat arrow notation), Instance Constructors, Expression-bodied properties
=> (lambda operator), Lambda Expressions
> (comparison operator), Order Comparison, < and >
>> (shift right operator), Bitwise operators
? (question mark)
in nullable types, Nullable Value Types
in regular expressions, Regular Expression Basics, Greedy Versus Lazy Quantifiers
?. (null-conditional operator), Null-Conditional Operator, Standard Event Pattern, Nullable Value Types and Null Operators
?? (null-coalescing operator), Null-Coalescing Operator, Nullable Value Types and Null Operators
[] (square brackets)
array declaration, Defining a Main method, Arrays, Jagged arrays
in collection expressions, Arrays
in list patterns, List Patterns
in regular expressions, Character Escapes
\ (backslash)
in regular expressions, Character Escapes
preceding escape sequences, Strings and Characters
^ (caret)
bitwise exclusive OR operator, Bitwise operators
in regular expressions, Anchors, Anchors
_ (discard symbol), Out variables and discards
{} (braces)
enclosing expressions in interpolated strings, String.Format and composite format strings
enclosing statement blocks, A First C# Program, Statements
in if statements, Changing the flow of execution with braces
in regular expressions, Quantifiers
| (vertical bar)
bitwise OR operator, Bitwise operators, Flags Enums
bool? with | operator, bool? with & and | Operators
in regular expressions, Regular Expression Basics
|| (conditional or operator), Conditional Operators, Conditional Compilation
~ (complement operator), Bitwise operators
~ (finalizer), Finalizers
calling Dispose from, Calling Dispose from a Finalizer
GC and, Finalizers-GC.ReRegisterForFinalize
GC.ReRegisterForFinalize, GC.ReRegisterForFinalize
resurrection, Resurrection-GC.ReRegisterForFinalize
A
abstract classes, Abstract Classes and Abstract Members
abstract members, Abstract Classes and Abstract Members
access control lists (ACLs), Running in a Standard User Account
access modifiers, Access Modifiers-Restrictions on Access Modifiers
accessibility capping, Accessibility Capping
friend assemblies, Friend Assemblies
restrictions on, Restrictions on Access Modifiers
accessors, Properties, Event Accessors
ACLs (access control lists), Running in a Standard User Account
Action delegate, The Func and Action Delegates
add to self (+=) operator
combining delegate instances, Multicast Delegates
delegate variable assignment, Multicast Delegates
event accessors, Event Accessors
subscribing to events, Events
addressing systems, network, Addresses and Ports
administrative elevation, Administrative Elevation and Virtualization
Aes class, Symmetric Encryption-Disposing Encryption Objects
Aggregate operator, Aggregate-Traps with unseeded aggregations, Optimizing custom aggregations
AggregateException class, Exceptions, Continuations, WhenAny, Working with AggregateException-Handle
Flatten method, Flatten
Handle method, Handle
parallel programming, Working with AggregateException-Handle
aggregation methods, Aggregation Methods-Traps with unseeded aggregations
aggregation operators, Other Operators
ALC (see assembly load context)
aliasing
any type, Alias any type (C# 12)
namespace alias qualifiers, Namespace alias qualifiers
tuples, Aliasing Tuples (C# 12)
types within namespaces, Aliasing Types and Namespaces
All method, All and SequenceEqual
alternator (|), Regular Expression Basics
Amazon Web Services (AWS), Key Management
ambient property, Scenarios for Nullable Value Types
Amdahl's law, When to Use PFX
ampersand (&)
address-of operator, Pointer Basics
bitwise AND operator, Bitwise operators, Flags Enums
bool? with & operator, bool? with & and | Operators
in parameter type names, ref and out parameter type names
anchors, Anchors
annotations, LINQ to XML, Annotations
anonymous disposal, Anonymous Disposal-Anonymous Disposal
anonymous methods, Anonymous Methods
anonymous pipes, PipeStream, Anonymous pipes-Anonymous pipes
anonymous types, Anonymous Types, Anonymous Types
Any method, Contains and Any
APM (Asynchronous Programming Model), Asynchronous Programming Model
AppContext, AppContext
AppDomain.CurrentDomain.BaseDirectory, Specifying a filename, Special Folders
application base directory, Specifying a filename
application layer, Network Architecture
application manifest, Administrative Elevation and Virtualization, The Application Manifest (Windows)
application servers, Thread Safety in Application Servers
Application.DispatcherUnhandledException, Centralized exception handling, Exception posting
Application.ThreadException, Centralized exception handling
ApplicationData directory, Special Folders
arguments
implications of passing by reference, Implications of passing by reference
named, Named arguments
pass-by-value versus pass-by-reference, Passing arguments by value
passing to a Dynamic Method, Passing Arguments to a Dynamic Method
arithmetic operators, Arithmetic Operators
Array class, The Array Class-Converting and Resizing
basics, The Array Class-The Array Class
construction and indexing, Construction and Indexing-Construction and Indexing
converting/resizing, Converting and Resizing
copying, Copying
enumeration, Enumeration
length and rank, Length and Rank
reversing elements, Reversing Elements
searching, Searching
sorting, Sorting
array initialization expressions, Arrays, Simplified Array Initialization Expressions
array pooling, Array Pooling
array types, obtaining, Obtaining array types
Array...
Array.ConvertAll method, Converting and Resizing
Array.Sort, Sorting
ArrayList, List<T> and ArrayList-List<T> and ArrayList
arrays, Arrays-Bounds Checking
array initialization expressions, Arrays, Simplified Array Initialization Expressions
bounds checking, Bounds Checking
covariance, Arrays
default element initialization, Default Element Initialization
indices and ranges, Indices and Ranges
jagged, Jagged arrays
multidimensional, Multidimensional Arrays
rectangular, Rectangular arrays
simplified initialization expressions, Simplified Array Initialization Expressions
type names, Array and pointer type names
value types versus reference types, Value types versus reference types
as operator, The as operator
ASCII character set, Text Encodings and Unicode
AsEnumerable operator, AsEnumerable, AsEnumerable and AsQueryable
AsParallel operator, PLINQ-PLINQ Limitations
.ASP.NET Core, ASP.NET Core
AsQueryable operator, AsQueryable, AsEnumerable and AsQueryable
assemblies, Compilation, Assemblies-Adding dependencies
application manifest, The Application Manifest (Windows)
applying attributes to, Applying Attributes to Assemblies and Backing Fields
Assembly class, The Assembly Class
assembly manifest, The Assembly Manifest
AssemblyName class, The AssemblyName Class
Authenticode signing, Authenticode Signing-Verifying that a program has been signed
components, What’s in an Assembly-The Assembly Class
defined, Common Language Runtime
emitting assemblies and types, Emitting Assemblies and Types-Attaching Attributes
fully qualified names, Fully Qualified Names
informational/file versions, Assembly Informational and File Versions
loading/resolving/isolating, Loading, Resolving, and Isolating Assemblies-Adding dependencies
modules, Modules
names, Assembly Names-Assembly Informational and File Versions
reflecting, Reflecting Assemblies
resources, Resources and Satellite Assemblies-Cultures and Subcultures
satellite assemblies, Satellite Assemblies-Visual Studio designer support
specifying attributes, Specifying assembly attributes
strong names and assembly signing, Strong Names and Assembly Signing
assembly load context (ALC), Assembly Load Contexts-Adding dependencies
Assembly.Load and contextual ALCs, Assembly.Load and Contextual ALCs-EnterContextualReflection
AssemblyDependencyResolver, AssemblyDependencyResolver
current ALC, The “Current” ALC
default ALC, The Default ALC
default probing, Default probing
EnterContextualReflection, EnterContextualReflection-EnterContextualReflection
legacy loading methods, The Legacy Loading Methods-LoadFile and Load(byte[])
LoadFile and Load(byte[]), LoadFile and Load(byte[])
LoadFrom method, LoadFrom
LoadFromAssemblyName, LoadFromAssemblyName
loading assemblies, Loading assemblies
loading/resolving unmanaged libraries, Loading and Resolving Unmanaged Libraries
resolving assemblies, Resolving assemblies-Resolving assemblies
unloading, Unloading ALCs
writing a plug-in system, Writing a Plug-In System-Adding dependencies
assembly resolution, Loading, Resolving, and Isolating Assemblies, Resolving assemblies-Resolving assemblies
Assembly...
Assembly class, The Assembly Class
Assembly.GetType, Obtaining a Type
Assembly.Load, Loading, Resolving, and Isolating Assemblies, Assembly.Load and Contextual ALCs-EnterContextualReflection
AssemblyBuilder, Emitting Assemblies and Types
AssemblyDependencyResolver, AssemblyDependencyResolver
AssemblyFileVersion, Assembly Informational and File Versions
AssemblyInformationalVersion, Assembly Informational and File Versions
AssemblyLoadContext, Loading, Resolving, and Isolating Assemblies
AssemblyName, The AssemblyName Class
AssemblyQualifiedName, Type Names
Assert method, Fail and Assert
assignment expressions, Assignment Expressions
assignment operators, Right-associative operators
associativity, operator, Operator Precedence and Associativity
asterisk (*)
as deference operator, Pointer Basics
as multiplication operator, A First C# Program, Literals, Punctuators, and Operators, Arithmetic Operators
in regular expressions, Quantifiers
asynchronous call graph, What Is Asynchronous Programming?
asynchronous functions, Asynchronous Functions in C#-Avoiding excessive bouncing
asynchronous call graph execution, Asynchronous call graph execution
asynchronous lambda expressions, Asynchronous Lambda Expressions
asynchronous methods in WinRT, Asynchronous Methods in WinRT
asynchronous streams, Asynchronous Streams-IAsyncEnumerable<T> in ASP.Net Core
asynchrony and synchronization contexts, Asynchrony and Synchronization Contexts
avoiding excessive bouncing, Avoiding excessive bouncing
awaiting, Awaiting-Comparison to coarse-grained concurrency
defined, Awaiting
optimizations, Completing synchronously-Completing synchronously
parallelism, Parallelism
precautions when using ValueTask<T>, Precautions when using ValueTask<T>
returning Task<TResult>, Returning Task<TResult>
synchronous completion, Completing synchronously-Avoiding excessive bouncing
ValueTask<T> and, Precautions when using ValueTask<T>
writing, Writing Asynchronous Functions-Parallelism
asynchronous lambda expressions, Asynchronous Lambda Expressions
asynchronous patterns, Cancellation-Asynchronous Locking
Asynchronous Programming Model (APM), Asynchronous Programming Model
BackgroundWorker class, BackgroundWorker
cancellation, Cancellation-Cancellation
Event-Based Asynchronous Pattern, Event-Based Asynchronous Pattern
obsolete patterns, Obsolete Patterns-BackgroundWorker
progress reporting, Progress Reporting-IProgress<T> and Progress<T>
task combinators, Task Combinators-Custom combinators
task-based patterns, The Task-Based Asynchronous Pattern
asynchronous programming
continuations and, Asynchronous Programming and Continuations
principles, What Is Asynchronous Programming?
Asynchronous Programming Model (APM), Asynchronous Programming Model
asynchronous streams, Asynchronous Streams-IAsyncEnumerable<T> in ASP.Net Core
IAsyncEnumerable<T> in ASP.Net Core, IAsyncEnumerable<T> in ASP.Net Core
querying IAsyncEnumerable<T>, Querying IAsyncEnumerable<T>
asynchrony, Principles of Asynchrony-Why Language Support Is Important
asynchronous functions in C#, Asynchronous Functions in C#-Avoiding excessive bouncing
asynchronous lambda expressions, Asynchronous Lambda Expressions
asynchronous patterns, Cancellation-Asynchronous Locking
asynchronous programming principles, What Is Asynchronous Programming?
coarse-grained concurrency versus, Comparison to coarse-grained concurrency
language support and, Why Language Support Is Important-Why Language Support Is Important
principles of, Principles of Asynchrony-Why Language Support Is Important
synchronous versus asynchronous operations, Synchronous Versus Asynchronous Operations
AsyncLocal<T>, AsyncLocal<T>
atomicity, locking and, Locking and Atomicity
attributes, Attributes-Caller Info Attributes
applying to assemblies and backing fields, Applying Attributes to Assemblies and Backing Fields
applying to lambda expressions (C# 10), Applying Attributes to Lambda Expressions
attaching custom attributes to dynamic construct, Attaching Attributes
attribute classes, Attribute Classes
AttributeUsage, The AttributeUsage Attribute
basics, Attribute Basics
caller info attributes, Caller Info Attributes
defining your own, Defining Your Own Attribute
named/positional parameters, Named and Positional Attribute Parameters
namespaces and, Attributes
reading, Reading Attributes
reflection, Working with Attributes-Retrieving Attributes at Runtime
retrieving at runtime, Retrieving Attributes at Runtime
specifying multiple attributes, Specifying Multiple Attributes
writing, Writing Attributes
AttributeUsage attribute, The AttributeUsage Attribute
authentication
client-side classes, Authentication-Authenticating via headers
CredentialCache and, CredentialCache
via headers with HttpClient, Authenticating via headers
Authenticode, Authenticode Signing-Verifying that a program has been signed
assembly signing, Authenticode Signing-Verifying that a program has been signed
code-signing certificate, Obtaining and installing a certificate
signing with, Obtaining and installing a certificate
signing with signtool.exe, Signing with signtool.exe
time stamping, Time stamping
automatic garbage collection, Automatic Garbage Collection-Roots
automatic properties, Automatic properties
autonomous tasks, Exceptions and autonomous tasks
AutoResetEvent, AutoResetEvent-Two-way signaling
Avalonia, MAUI
Average operator, Sum and Average
AVL tree, Immutable Collections and Performance
await expressions, Awaiting-Comparison to coarse-grained concurrency
awaiting in a UI, Awaiting in a UI-Awaiting in a UI
capturing local state, Capturing local state
locking and, Asynchronous semaphores and locks
AWS (Amazon Web Services), Key Management
B
b (word boundary assertion), Word Boundaries
background garbage collection, Background collection
background threads, Foreground Versus Background Threads
BackgroundWorker class, BackgroundWorker
backing fields, Applying Attributes to Assemblies and Backing Fields
backing store streams, Backing Store Streams
backslash (\)
in regular expressions, Character Escapes
preceding escape sequences, Strings and Characters
banker's rounding, Rounding real to integral conversions
Barrier class, The Barrier Class-The Barrier Class
base class library (BCL), Base Class Library
base constructors, Calling base constructors
base keyword, The base Keyword
base types and interfaces, Base Types and Interfaces
base-class constraint, Generic Constraints
BaseType property, Base Types and Interfaces
Basic Multilingual Plane (BMP), UTF-16 and surrogate pairs
BCL (base class library), Base Class Library
BigInteger struct, BigInteger
binary adapters, Binary Adapters
binary operators, Left-associative operators
BinaryReader, Using TCP
BinaryWriter, Using TCP
binding
dynamic binding, Dynamic Binding-Uncallable Functions
static versus dynamic, Static Binding Versus Dynamic Binding
BindingFlags enum, The BindingFlags enum
bit-mapped attributes, Attribute Basics
BitArray class, BitArray
BitConverter, BitConverter
BitOperations, BitOperations
bitwise operators, Bitwise operators
blocking
spinning versus, Blocking versus spinning
threads, Blocking
BlockingCollection<T>, BlockingCollection<T>-Using Tasks
using tasks, Using Tasks-Using Tasks
writing a producer/consumer queue, Writing a Producer/Consumer Queue-Using Tasks
BMP (Basic Multilingual Plane), UTF-16 and surrogate pairs
bool (Boolean) type and operators, Predefined Type Examples, Boolean Type and Operators-Conditional operator (ternary operator)
conditional operators, Conditional Operators
equality and comparison operators, Equality and Comparison Operators
bounds checking, Bounds Checking
boxing
copying semantics, Copying semantics of boxing and unboxing
defined, Boxing and Unboxing
interfaces and, Interfaces and Boxing
nullable values, Boxing and Unboxing Nullable Values
braces ({})
enclosing expressions in interpolated strings, String.Format and composite format strings
enclosing statement blocks, A First C# Program, Statements
in if statements, Changing the flow of execution with braces
in regular expressions, Quantifiers
branching, Branching
break statement, The break statement
broadcaster type, Events
BrotliStream, Compression Streams
BufferedStream class, BufferedStream
builder class, Builders
built-in types, Predefined Type Examples
byte arrays, Encoding to byte arrays
byte type, 8- and 16-Bit Integral Types
C
C# (generally)
brief history of features introduced from C# 2.0 through C# 9.0, A Brief History of C#-What’s New in C# 2.0
language basics, C# Language Basics-Namespace alias qualifiers
memory management, Memory Management, Common Language Runtime
(see also garbage collection[GC])
niche runtimes, Niche Runtimes
object orientation, Object Orientation
platform support, Platform Support
simple program, A First C# Program-Compilation
syntax, Syntax-Comments
type safety, Type Safety
C# 8
array ranges and indices, Indices and Ranges
asynchronous streams, Asynchronous Streams-IAsyncEnumerable<T> in ASP.Net Core
default interface members, Default Interface Members
new features, What’s New in C# 8.0-Asynchronous streams
null-coalescing assignment operators, Null-Coalescing Assignment Operator
nullable reference types, Nullable Reference Types-Treating Nullable Warnings as Errors
property patterns, Property Patterns
static local methods, Static local methods
switch expressions, Switch expressions
using declarations, using declarations
using indices and ranges with indexers, Using indices and ranges with indexers
C# 9
callbacks with function pointers, Callbacks with Function Pointers
function pointers, Callbacks with Function Pointers
init-only properties, Init-only properties
init-only setters, Init-only setters
new features, What’s New in C# 9.0-Other new features
pattern combinators, Pattern Combinators
records (see records)
relational patterns, Relational Patterns
target-typed new expressions, Target-Typed new Expressions
top-level statements, Defining a Main method, Local methods and top-level statements
C# 10
applying attributes to lambda expressions, Applying Attributes to Lambda Expressions
CallerArgumentExpression, CallerArgumentExpression
file-scoped namespaces, File-Scoped Namespaces
global using directive, The global using Directive
new features, What’s New in C# 10-Other new features
C# 11
checked operators, Checked operators
list patterns, List Patterns
new features, What’s New in C# 11-Other new features
raw string literals, Raw string literals (C# 11)-Raw string literals (C# 11)
required members for constructors, Required members (C# 11)
UTF-8 string literals, UTF-8 Strings
C# 12
aliasing any type, Alias any type (C# 12)
collection expressions, Arrays, Collection Initializers and Collection Expressions, CopyTo and TryCopyTo
default lambda parameters, Default Lambda Parameters (C# 12)
new features, What’s New in C# 12-Other new features
CA (Certificate Authority), Obtaining and installing a certificate
caching, Weak References and Caching
calculated fields, Calculated Fields and Lazy Evaluation-Calculated Fields and Lazy Evaluation
calculated properties, Read-only and calculated properties
call graph, What Is Asynchronous Programming?, Asynchronous call graph execution
call sites, The Dynamic Language Runtime
call-site caching, The Dynamic Language Runtime
caller info attributes, Caller Info Attributes
CallerArgumentExpression, CallerArgumentExpression
calling conventions, Calling Conventions, Nondefault calling conventions
calling site, Object Initializers
CallSite<>, The Dynamic Language Runtime
canceling a PLINQ query, Cancellation
cancellation tokens, Semaphore, Cancellation
Capitalizer (plug-in), Capitalizer (plug-in)
captured variables, Captured Variables, Lambda expressions and captured variables
caret (^)
bitwise exclusive OR operator, Bitwise operators
in regular expressions, Anchors, Anchors
cartesian product, Thinking in query syntax
Cast operator, OfType and Cast
casting, Casting and Reference Conversions-Introducing a pattern variable
as operator, The as operator
downcasting, Downcasting
introducing a pattern variable, Introducing a pattern variable
is operator and, The is operator
upcasting, Upcasting
catch clause, The catch Clause-Exception filters, Iterators and try/catch/finally blocks
CCW (COM-Callable Wrapper), Exposing C# Objects to COM
centralized exception handling, Centralized exception handling
Certificate Authority (CA), Obtaining and installing a certificate
chaining
encryption streams, Chaining Encryption Streams
extension methods, Extension Method Chaining
ChangeType method, Dynamic conversions
char type, Char Conversions, Char
character sets, Character Sets
characters, accessing within strings, Accessing characters within a string
checked operators, Overflow check operators, Checked operators
child tasks, Child tasks, Continuations and child tasks
chunk partitioning, Input-side optimization
circular dependencies, Circular Dependencies
class constraint, Generic Constraints
classes, Classes-The nameof operator
abstract, Abstract Classes and Abstract Members
anonymous types, Anonymous Types
constants, Constants-Constants
constructors and inheritance, Constructors and Inheritance-Inheritance with primary constructors
deconstructors, Deconstructors-Deconstructors
fields, Fields
finalizers, Finalizers
inheritance (see inheritance)
instance constructors, Instance Constructors
methods, Methods-Overloading methods
nameof operator, The nameof operator
object initializers, Object Initializers
partial types/methods, Partial Types and Methods
primary constructors and subclassing, Inheritance with primary constructors
properties, Properties-CLR property implementation
sealing functions and classes, Sealing Functions and Classes
static classes, Static Classes
static constructors, Static Constructors
this reference, The this Reference
writing a class versus an interface, Static virtual/abstract interface members
client-side classes
authentication, Authentication-Authenticating via headers
HttpClient, HttpClient-Cookies
proxies, Proxies
Clone method, The Array Class, Copying
cloning, Automatic Deep Cloning
Close method, Close and Stop
closed generic types, Uncreated Closed Generics
closures, Capturing Outer Variables
CLR (Common Language Runtime), Common Language Runtime
C# members versus CLR members, C# Members Versus CLR Members
calling conventions, Calling Conventions
deadlocks and, Deadlocks
indexer implementation, CLR indexer implementation
property implementation, CLR property implementation
type equivalence, Type Equivalence
coarse-grained concurrency, Comparison to coarse-grained concurrency
code point, Text Encodings and Unicode
collection expressions, Arrays, Collection Initializers and Collection Expressions, CopyTo and TryCopyTo
Collection<T>, Collection<T> and CollectionBase-CollectionBase
CollectionBase, CollectionBase
collections, Collections-IStructuralEquatable and IStructuralComparable
Array class, The Array Class-Converting and Resizing
customizable collections and proxies, Customizable Collections and Proxies-ReadOnlyCollection<T>
enumeration, Enumeration-Implementing the Enumeration Interfaces
frozen collections, Frozen Collections
ICollection and IList interfaces, The ICollection and IList Interfaces-IReadOnlyCollection<T> and IReadOnlyList<T>
IEqualityComparer and EqualityComparer, IEqualityComparer and EqualityComparer-ReferenceEqualityComparer.Instance (.NET 5+)
immutable collections, Immutable Collections-Immutable Collections and Performance
IStructuralEquatable and IStructuralComparable, IStructuralEquatable and IStructuralComparable
lists, queues, stacks, and sets, Lists, Queues, Stacks, and Sets-HashSet<T> and SortedSet<T>
plugging in equality and order, Plugging in Equality and Order-IStructuralEquatable and IStructuralComparable
StringComparer, StringComparer
collision, Hash Algorithms in .NET
colon (:), in named arguments, Named arguments
COM (Component Object Model), COM Interoperability-Enabling Registry-Free COM
calling a COM component from C#, Calling a COM Component from C#-Type Equivalence
dynamic binding, Dynamic Binding
embedding interop types, Embedding Interop Types
enabling registry-free COM, Enabling Registry-Free COM
exposing C# objects to, Exposing C# Objects to COM-Enabling Registry-Free COM
implicit ref parameters, Implicit ref Parameters
indexers, Indexers
IUnknown and IDispatch, IUnknown and IDispatch
optional parameters and named arguments, Optional Parameters and Named Arguments
purpose of, The Purpose of COM
type equivalence, Type Equivalence
type system basics, The Basics of the COM Type System
COM interop types, Calling a COM Component from C#
COM-Callable Wrapper (CCW), Exposing C# Objects to COM
comma (,), Rectangular arrays
comments, Comments
Common Language Runtime (see CLR)
CommonApplicationData, Special Folders
Compare method, Comparing Strings
CompareOrdinal method, Comparing Strings
CompareTo, Comparing Strings, < and > string comparisons in EF Core
CompareTo method, String comparisons
comparison operators, Equality and Comparison Operators, Overloading Equality and Comparison Operators, Order Comparison
comparisons
ordinal versus culture comparison, Ordinal versus culture comparison
string equality comparisons, String comparisons, Comparing Strings
string order comparison, String order comparison
string types, Comparing Strings-String order comparison
compilation, Compilation
complement operator (~), Bitwise operators
Complex struct, Complex
Component Object Model (see COM)
composite format string, String.Format and composite format strings
composite formatting, Composite formatting
Compressed file attribute, Compression and encryption attributes
compression streams, Compression Streams-Unix gzip File Compression
compressing in memory, Compressing in Memory
Concat operator, Splitting and joining strings, Concat, Union, UnionBy
concatenation, String concatenation
concurrency and asynchrony, Concurrency and Asynchrony-BackgroundWorker
common concurrency scenarios, Introduction
principles of asynchrony, Principles of Asynchrony-Why Language Support Is Important
tasks, Tasks-Task.Delay
threading, Threading-Hygiene in the thread pool
concurrent collections, Concurrent Collections-ConcurrentBag<T>
ConcurrentBag<T>, ConcurrentBag<T>
IProducerConsumerCollection<T>, IProducerConsumerCollection<T>
concurrent garbage collection, Background collection
concurrent operations, canceling, Cancellation-Cancellation
ConcurrentBag<T>, ConcurrentBag<T>
ConcurrentQueue<T>, Resurrection
conditional (ternary) operator, Conditional operator (ternary operator)
conditional and operator (&&), Conditional Operators, Conditional Compilation
Conditional attribute, Conditional Attributes, The Conditional Attribute-Alternatives to the Conditional attribute
conditional compilation, Conditional Compilation-Alternatives to the Conditional attribute
Conditional attribute, The Conditional Attribute-Alternatives to the Conditional attribute
static variable flags versus, Conditional Compilation Versus Static Variable Flags
conditional continuations, Conditional continuations
conditional or operator (||), Conditional Operators, Conditional Compilation
ConfigureAwait, Avoiding excessive bouncing
Console class, Composite formatting, Console
constant pattern, Constant Pattern
constants, Constants-Constants
ConstrainedCopy method, Copying
constraints, Generic Constraints-Generic Constraints
constructors, Constructors and instantiation
deconstructors and, Deconstructors-Deconstructors
emitting, Emitting Constructors
field initialization order, Constructor and field initialization order
implicit calling of the parameterless base-class constructor, Implicit calling of the parameterless base-class constructor
implicit parameterless, Implicit parameterless constructors
inheritance and, Constructors and Inheritance-Inheritance with primary constructors
instance constructor and field initialization order, Constructor and field initialization order
instance constructors, Instance Constructors
nonpublic constructors, Nonpublic constructors
overloading, Overloading constructors
primary, Primary Constructors-Primary Constructors
required members (C# 11), Required members (C# 11)
static, Static Constructors
Contains method, Contains and Any
contextual keywords, Contextual keywords
continuations
asynchronous programming and, Asynchronous Programming and Continuations
child tasks and, Continuations and child tasks
conditional, Conditional continuations
event wait handles and, Wait Handles and Continuations
exceptions and, Continuations and exceptions
multiple antecedents with, Continuations with multiple antecedents
multiple continuations on a single antecedent, Multiple continuations on a single antecedent
task parallelism, Continuations-Multiple continuations on a single antecedent
Task<TResult> and, Continuations and Task<TResult>
tasks and, Continuations-Continuations
continue statement, The continue statement
ContinueWith method, Continuations-Multiple continuations on a single antecedent
contravariance, Contravariance, Parameter compatibility
conversions, Types and Conversions
enums, Enum Conversions, Enum Conversions-String conversions
generic types, Type Parameters and Conversions
implicit/explicit, Types and Conversions
implicit/explicit nullable conversions, Implicit and Explicit Nullable Conversions
LINQ methods, Conversion Methods-AsEnumerable and AsQueryable
numeric types, Types and Conversions, Conversions
operator overloading and, Custom Implicit and Explicit Conversions
Convert class, Convert-Base-64 conversions
banker's rounding, Rounding real to integral conversions
base-64 conversions, Base-64 conversions
dynamic conversions, Dynamic conversions
parsing numbers in base 2, 8, and 16, Parsing numbers in base 2, 8, and 16
rounding real to integral conversions, Rounding real to integral conversions
ConvertTime method, TimeZoneInfo
cookies, Cookies
Coordinated Universal Time (UTC), DateTime and DateTimeOffset, DateTimeOffset and Time Zones
copy constructor, Nondestructive Mutation
Copy method, Copying
CopyTo method, Copying, CopyTo and TryCopyTo
core dump, dotnet-dump
correlated subquery, Select subqueries and object hierarchies
Count operator, Count and LongCount
CountdownEvent, CountdownEvent
covariance, Covariance-Declaring a covariant type parameter, Return type compatibility
covariant return types, Covariant return types
CreateRandom method, Static Polymorphism
CreateViewAccessor method, Working with View Accessors
CredentialCache, CredentialCache
CredentialCache.DefaultNetworkCredentials, Proxies, CredentialCache
cross join, Thinking in query syntax
cross-process EventWaitHandle, Creating a Cross-Process EventWaitHandle
cryptography and encryption, Cryptography-Digital Signing
hashing, Hashing-Hashing Passwords
options in .NET, Overview
public-key encryption/signing, Public-Key Encryption and Signing-Digital Signing
symmetric encryption, Symmetric Encryption-Key Management
Windows Data Protection, Windows Data Protection
CryptoStream, Symmetric Encryption
.csproj file, XML Documentation
culture sensitive string comparison, Ordinal versus culture comparison
CultureInfo, String order comparison, Format providers and CultureInfo
CultureInfo.CurrentCulture, Format Providers
CultureInfo.CurrentUICulture, Satellite Assemblies
cultures and subcultures, Cultures and Subcultures
custom attributes, Attribute Basics
custom binding, Custom Binding
custom conversion, Type Parameters and Conversions
custom types, Custom Types-Defining a Main method
constructors and instantiation, Constructors and instantiation
equality and, Equality and Custom Types-Pluggable equality comparers
instance versus static members, Instance versus static members
members of a type, Members of a type
public keyword, The public keyword
symmetry of predefined/custom types, Symmetry of predefined types and custom types
customizable collections and proxies, Customizable Collections and Proxies-ReadOnlyCollection<T>
Collection<T> and CollectionBase, Collection<T> and CollectionBase-CollectionBase
KeyedCollection<TKey,TItem> and DictionaryBase, KeyedCollection<TKey,TItem> and DictionaryBase-DictionaryBase
ReadOnlyCollection<T>, ReadOnlyCollection<T>
D
data members, Members of a type
data parallelism, PFX Concepts
data transfer object (DTO), Projecting into concrete types
dates and times, Dates and Times-Daylight Saving Time and DateTime
dates and time zones, Dates and Time Zones-Daylight Saving Time and DateTime
DateTime and DateTimeOffset, DateTime and DateTimeOffset-Null DateTime and DateTimeOffset values
parsing with regular expressions, Parsing dates/times (N/N/N H:M:S AM/PM)
TimeSpan, TimeSpan
DateTime, DateTime and DateTimeOffset-Null DateTime and DateTimeOffset values
constructing, Constructing a DateTime
DateTimeOffset versus, DateTime and DateTimeOffset
daylight saving time and, Daylight Saving Time and DateTime
format strings, Date/Time Format Strings-Parsing and misparsing DateTimes
formatting/parsing datetimes, Formatting and parsing datetimes
null values, Null DateTime and DateTimeOffset values
parsing/misparsing, Parsing and misparsing DateTimes
returning current date/time with, The current DateTime/DateTimeOffset
time zones and, DateTime and Time Zones
working with dates and times, Working with dates and times
DateTime.MinValue, Null DateTime and DateTimeOffset values
DateTimeFormatInfo, Using NumberFormatInfo or DateTimeFormatInfo
DateTimeOffset, DateTime and DateTimeOffset-Null DateTime and DateTimeOffset values, Value Versus Referential Equality
constructing, Constructing a DateTimeOffset
DateTime versus, DateTime and DateTimeOffset
format strings, Date/Time Format Strings-Parsing and misparsing DateTimes
formatting/parsing datetimes, Null DateTime and DateTimeOffset values
null values, Null DateTime and DateTimeOffset values
returning current date/time with, The current DateTime/DateTimeOffset
time zones and, DateTimeOffset and Time Zones
working with dates and times, Working with dates and times
DateTimeStyles, DateTimeStyles
daylight saving time, Daylight Saving Time and DateTime
DbContext, DbContext-Object Tracking
change tracking, Change Tracking
configuring the connection, Configuring the connection
configuring the model, Configuring the model
creating the database, Creating the database
disposing, Object Tracking
object tracking, Object Tracking
using, Using DbContext
Debug and Trace classes, Debug and Trace Classes-Flushing and Closing Listeners
Fail and Assert methods, Fail and Assert
flushing and closing listeners, Flushing and Closing Listeners
TraceListener, TraceListener
Debugger class, Debugger Integration
attaching and breaking, Attaching and Breaking
attributes, Debugger Attributes
DebuggerHidden attribute, Debugger Attributes
DebuggerStepThrough attribute, Debugger Attributes
decimal conversions, Decimal conversions
declaration statements, Declaration Statements
declarative parallelism, PFX Components
Deconstruct method, Deconstructors, Tuple and Positional Patterns
deconstructing assignment, Deconstructors
deconstructors, Deconstructors-Deconstructors
decorator sequence, How Deferred Execution Works
decrement operator (--), Increment and Decrement Operators
deep cloning, Automatic Deep Cloning
default keyword, Default Values, The default Generic Value
default lambda parameters (C# 12), Default Lambda Parameters (C# 12)
default scheduler, Task Schedulers
DefaultIfEmpty operator, DefaultIfEmpty
deferred execution
captured variables, Captured Variables
chaining decorators, Chaining Decorators
EF Core queries, Deferred Execution
how queries are executed, How Queries Are Executed
LINQ queries, Deferred Execution-How Queries Are Executed
mechanism of operation, How Deferred Execution Works
reevaluation, Reevaluation
subqueries and, Subqueries and Deferred Execution
deferred loading, Streaming a Projection
#define directive, Conditional Compilation
DefineMethodOverride, Overriding methods
definite assignment policy, Definite Assignment
DeflateStream, Compression Streams-Compressing in Memory
delegate type, Delegates
Delegate.CreateDelegate, Instantiating Types
delegates, Delegates-Generic delegate type parameter variance
callbacks with, Callbacks with Delegates
calling dynamically instantiated delegates, Using Delegates for Performance
compatibility, Type compatibility-Generic delegate type parameter variance
dynamically instantiating, Instantiating Types
Func and Action delegates, The Func and Action Delegates
generic delegate type parameter variance, Generic delegate type parameter variance
generic delegate types, Generic Delegate Types
instance/static method targets, Instance and Static Method Targets
interfaces versus, Delegates Versus Interfaces
multicast, Multicast Delegates
parameter compatibility, Parameter compatibility
return type compatibility, Return type compatibility
type compatibility, Type compatibility
writing plug-in methods with, Writing Plug-in Methods with Delegates
DelegatingHandler, Chaining handlers with DelegatingHandler
DescendantNodes method, Retrieving descendants
Descendants method, Retrieving descendants
diagnostics, Diagnostics-dotnet-dump
conditional compilation, Conditional Compilation-Alternatives to the Conditional attribute
cross-platform tools, Cross-Platform Diagnostic Tools
Debug and Trace classes, Debug and Trace Classes-Flushing and Closing Listeners
debugger integration, Debugger Integration
performance counters, Performance Counters-Creating Counters and Writing Performance Data
processes and process threads, Processes and Process Threads
StackTrace and StackFrame, StackTrace and StackFrame-StackTrace and StackFrame
Stopwatch class, The Stopwatch Class
Windows event logs, Windows Event Logs-Monitoring the Event Log
dictionaries, Dictionaries-Sorted Dictionaries
Dictionary<TKey,TValue> and Hashtable, Dictionary<TKey,TValue> and Hashtable-Dictionary<TKey,TValue> and Hashtable
IDictionary, IDictionary
IDictionary<TKey,TValue>, IDictionary<TKey,TValue>
ListDictionary and HybridDictionary, ListDictionary and HybridDictionary
OrderedDictionary, OrderedDictionary
sorted, Sorted Dictionaries
dictionary attack, Hashing Passwords
Dictionary<TKey,TValue>, Dictionary<TKey,TValue> and Hashtable-Dictionary<TKey,TValue> and Hashtable
DictionaryBase, DictionaryBase
digital signing, Digital Signing
Directory class, The Directory Class
DirectoryInfo class, FileInfo and DirectoryInfo
disassembler, Parsing IL-Writing a Disassembler
discard symbol (_), Out variables and discards
discards, Out variables and discards
disposal
anonymous, Anonymous Disposal-Anonymous Disposal
calling Dispose from a finalizer, Calling Dispose from a Finalizer
clearing fields, Clearing Fields in Disposal
defined, Disposal and Garbage Collection
encryption objects, Disposing Encryption Objects
IDisposable, Dispose, and Close, IDisposable, Dispose, and Close-Anonymous Disposal
standard disposal semantics, Standard Disposal Semantics
wait handles, AutoResetEvent
when to dispose, When to Dispose
Dispose method, IDisposable, Dispose, and Close-Anonymous Disposal, Calling Dispose from a Finalizer
Distinct operator, Distinct and DistinctBy
division, Division
DLL (Dynamic Link Library)
callbacks from unmanaged code, Callbacks from Unmanaged Code
calling into native DLLs, Calling into Native DLLs
mapping structs to unmanaged memory, Mapping a Struct to Unmanaged Memory-fixed and fixed {...}
simulating C unions, Simulating a C Union
type and parameter marshaling, Marshaling Common Types-Calling Conventions
.dll files, Compilation
DLR (Dynamic Language Runtime), Custom Binding, The Dynamic Language Runtime
DNS (Domain Name Service), Using DNS
Dns class, Using DNS
do-while loops, while and do-while loops
document object model (see DOM)
documentation comments (///), XML Documentation
dollar sign ($)
in regular expressions, Anchors
preceding interpolated strings, String interpolation, String.Format and composite format strings
DOM (document object model)
basics, Architectural Overview
expression DOM, The Expression DOM
Domain Name Service (DNS), Using DNS
dotnet tool, Compilation
dotnet-counters tool, dotnet-counters
dotnet-dump tool, dotnet-dump
dotnet-trace tool, dotnet-trace
double type, double Versus decimal
double-checked locking, Lazy<T>
downcasting, Downcasting
DownloadDataTaskAsync, Awaiting in a UI
DPAPI (Windows Data Protection API), Windows Data Protection
DriveInfo class, Querying Volume Information
DTO (data transfer object), Projecting into concrete types
dump, dotnet-dump
dynamic binding, Dynamic Binding-Uncallable Functions
conversions, Dynamic Conversions
custom binding, Custom Binding
dynamic calls without dynamic receivers, Dynamic Calls Without Dynamic Receivers
dynamic expressions, Dynamic Expressions
language binding, Language Binding
on COM types, Dynamic Binding
runtime representation of dynamic, Runtime Representation of Dynamic
RuntimeBinderException, RuntimeBinderException
static binding versus, Static Binding Versus Dynamic Binding
static types in dynamic expressions, Static Types in Dynamic Expressions
uncallable functions, Uncallable Functions
var versus dynamic types, var Versus dynamic
dynamic calls, Dynamic Calls Without Dynamic Receivers
dynamic code generation, Dynamic Code Generation-Exception Handling
branching, Branching
exception handling, Exception Handling
generating IL with DynamicMethod, Generating IL with DynamicMethod-Generating IL with DynamicMethod
generating local variables, Generating Local Variables
instantiating objects and calling instance methods, Instantiating Objects and Calling Instance Methods
passing arguments to a Dynamic Method, Passing Arguments to a Dynamic Method
dynamic construct, Attaching Attributes
dynamic conversions, Dynamic conversions
dynamic expressions, Dynamic Expressions
Dynamic Language Runtime (DLR), Custom Binding, The Dynamic Language Runtime
dynamic languages, Interoperating with Dynamic Languages-Passing State Between C# and a Script
Dynamic Link Library (DLL) (see DLL)
dynamic objects, Implementing Dynamic Objects-ExpandoObject
dynamic programming, Dynamic Programming-Passing State Between C# and a Script
Dynamic Language Runtime (DLR), The Dynamic Language Runtime
dynamic member overload resolution, Dynamic Member Overload Resolution-Anonymously Calling Members of a Generic Type
implementing dynamic objects, Implementing Dynamic Objects-ExpandoObject
interoperating with dynamic languages, Interoperating with Dynamic Languages-Passing State Between C# and a Script
dynamic receivers, dynamic calls without, Dynamic Expressions
dynamic type, var Versus dynamic
DynamicMethod
generating IL with, Generating IL with DynamicMethod-Generating IL with DynamicMethod
passing arguments to, Passing Arguments to a Dynamic Method
DynamicObject, DynamicObject-DynamicObject
DynamicVisit method, Simplifying the Visitor Pattern
E
EAP (Event-Based Asynchronous Pattern), Event-Based Asynchronous Pattern
EF Core, EF Core-Deferred Execution
adding and removing entities from navigation collections, Adding and removing entities from navigation collections
change tracking, Change Tracking
DbContext, DbContext-Object Tracking
deferred execution, Deferred Execution
entity classes, EF Core Entity Classes
GroupBy in, GroupBy in EF Core
loading navigation properties, Loading navigation properties
navigation properties, Navigation Properties-Lazy loading
object tracking, Object Tracking
SelectMany in, SelectMany in EF Core
SQL LIKE comparisons, SQL LIKE comparisons in EF Core
string comparisons in, < and > string comparisons in EF Core
subqueries and joins in, Subqueries and joins in EF Core
WHERE x IN (…,…,…), WHERE x IN (…, …, …) in EF Core
8- and 16-bit integral types, 8- and 16-Bit Integral Types
Element method, Retrieving elements
element operators, Other Operators, Element Operators-DefaultIfEmpty
element typing, Lambda expressions and element typing
ElementAt operator, ElementAt
elements, Getting Started
#elif directive, Conditional Compilation
#elif statement, Conditional Compilation
else clause, The else clause
#else directive, Conditional Compilation
#else statement, Conditional Compilation
"Elvis" (null-conditional) operator (see null-conditional operator)
email
receiving POP3 mail with TCP, Receiving POP3 Mail with TCP-Receiving POP3 Mail with TCP
sending mail with SmtpClient, Sending Mail with SmtpClient
embarrassingly parallel problems, When to Use PFX
Empty operator, Empty
empty strings, Null and empty strings
Encoding object, Obtaining an Encoding object
Encoding.GetEncoding, Obtaining an Encoding object
Encrypted file attribute, Compression and encryption attributes
encryption (see cryptography and encryption)
#endif directive, Conditional Compilation
EndsWith method, Searching within strings
EnterAsync extension method, Writing an EnterAsync extension method
EnterContextualReflection, EnterContextualReflection-EnterContextualReflection
Enum...
Enum.GetNames, Enumerating Enum Values
Enum.GetValues, Enumerating Enum Values
Enum.Parse, String conversions
Enum.ToObject, Integral to enum conversions
Enumerable...
Enumerable.AsEnumerable operator, AsEnumerable
Enumerable.ElementAt, ElementAt
Enumerable.Except, Intersect, Intersect By, Except, and ExceptBy
Enumerable.Join, Enumerable implementations
Enumerable.Where, Enumerable.Where implementation
enumeration, Enumeration, Enumeration-Implementing the Enumeration Interfaces
Array class, Enumeration
collection initializers and collection expressions, Collection Initializers and Collection Expressions
collections, Enumeration-Implementing the Enumeration Interfaces
IEnumerable and IEnumerator, IEnumerable and IEnumerator
IEnumerable<T> and IEnumerator<T>, IEnumerable<T> and IEnumerator<T>-IEnumerable<T> and IDisposable
implementing the enumeration interfaces, Implementing the Enumeration Interfaces-Implementing the Enumeration Interfaces
enumerators, Enumeration, Forward-Only Enumerators-Forward-Only Enumerators
enums, Enums-Type-Safety Issues, Enums-How Enums Work
conversions, Enum Conversions, Enum Conversions-String conversions
defined, Enums
enum to integral conversions, Enum to integral conversions
enumerating enum values, Enumerating Enum Values
Flags attribute, Flags Enums
format strings, Enum Format Strings
integral to enum conversions, Integral to enum conversions
operators that work with, Enum Operators
semantics of, How Enums Work
string conversions, String conversions
type-safety issues, Type-Safety Issues
Environment.SpecialFolder, Special Folders
equal sign (=), as assignment operator, Literals, Punctuators, and Operators, Assignment Expressions
equality comparison, Comparing Strings, Equality Comparison-Pluggable equality comparers
changing the meaning of equality, Changing the meaning of equality
equality and custom types, Equality and Custom Types-Pluggable equality comparers
implementing IEquatable<T>, Implementing IEquatable<T>
overloading == and !=, Overloading == and !=
overriding equality semantics, How to override equality semantics
overriding Equals, Overriding Equals
overriding GetHashCode, Overriding GetHashCode
pluggable equality operators, Pluggable equality comparers
records and, Records and Equality Comparison
speeding up with structs, Speeding up equality comparisons with structs
standard equality protocols, Standard Equality Protocols-When Equals and == are not equal
value equality versus referential equality, Value Versus Referential Equality
equality operator (==), Literals, Punctuators, and Operators, == and !=
Boolean values and, Equality and Comparison Operators
Equals method versus, When Equals and == are not equal
NaN value and, Special Float and Double Values
operator lifting and, Equality operators (== and !=)
overloading, Overloading Equality and Comparison Operators, Overloading == and !=
records and, Records and Equality Comparison
string equality comparison, String comparisons, Comparing Strings
EqualityComparer, IEqualityComparer and EqualityComparer-ReferenceEqualityComparer.Instance (.NET 5+)
EqualityComparer<T>, The static object.Equals method
EqualityComparer<T>.Default, EqualityComparer<T>.Default
Equals method
equality operator (==) versus, When Equals and == are not equal
IComparable versus, IComparable versus Equals
#error preprocessor directive, Preprocessor Directives
escape sequences, Strings and Characters, Character Escapes
evaluation stack, The Evaluation Stack
event accessors, Events
event wait handles, Signaling with Event Wait Handles-Alternatives to WaitAll and SignalAndWait
AutoResetEvent, AutoResetEvent-Two-way signaling
continuations and, Wait Handles and Continuations
CountdownEvent, CountdownEvent
cross-process, Creating a Cross-Process EventWaitHandle
disposal, AutoResetEvent
ManualResetEvent, ManualResetEvent
signaling with, Signaling with Event Wait Handles-Alternatives to WaitAll and SignalAndWait
WaitAny, WaitAll, and SignalAndWait, WaitAny, WaitAll, and SignalAndWait
Event-Based Asynchronous Pattern (EAP), Event-Based Asynchronous Pattern
EventLog class, Windows Event Logs-Monitoring the Event Log
events
accessors, Event Accessors
mechanism of operation, Events
modifiers, Event Modifiers
standard event pattern, Standard Event Pattern-Standard Event Pattern
weak references and, Weak References and Events-Weak References and Events
Except operator, Intersect, Intersect By, Except, and ExceptBy
exception filter, Exception filters
exception handling
centralized, Centralized exception handling
dynamic code generation, Exception Handling
threading and, Exception Handling
exception posting, Exception posting
exceptions, Throwing Exceptions-Rethrowing an exception
(see also try statements and exceptions)
autonomous tasks and, Exceptions and autonomous tasks
continuations and, Continuations and exceptions
tasks and, Exceptions
throwing, Throwing Exceptions-Rethrowing an exception
exclusive locking, Exclusive Locking-Mutex
choosing the synchronization object, Choosing the Synchronization Object
deadlocks, Deadlocks
lock statement, The lock Statement
locking and atomicity, Locking and Atomicity
lockTaken overloads, The lockTaken overloads
Monitor.Enter and Monitor.Exit, Monitor.Enter and Monitor.Exit
Mutex, Mutex
nested locking, Nested Locking
performance, Performance
TryEnter method, TryEnter
when to lock, When to Lock
.exe files, Compilation
ExpandoObject, ExpandoObject
explicit conversions, Types and Conversions
explicit loading, Loading navigation properties
expression DOM, The Expression DOM
expression statements, Expression Statements
expression trees, Expression Trees-The Expression DOM
compiling, Compiling expression trees
delegates versus, Delegates Versus Expression Trees-AsQueryable
lambda expressions and, Lambda Expressions
expression-bodied members (=), Operator Functions
expression-bodied members (=>), Instance Constructors, Expression-bodied properties, Finalizers
expression-bodied methods, Expression-bodied methods
expression-bodied properties, Expression-bodied properties
expressions, Expressions and Operators-Operator Table
assignment expressions, Assignment Expressions
primary expressions, Primary Expressions
switch expressions, Switch expressions
void expressions, Void Expressions
extended partial methods, Extended partial methods
Extensible Application Markup Language (XAML) files, Type Converters, Creating a pack URI resource in Visual Studio
extension methods, Extension Methods-Demoting an extension method, Why extension methods are important
ambiguity and resolution, Namespaces
chaining, Extension Method Chaining
demoting, Demoting an extension method
disambiguating two methods with same signature, Extension methods versus extension methods
EnterAsync, Writing an EnterAsync extension method
instance methods versus, Extension methods versus instance methods
namespaces, Namespaces
precedence among, Extension methods versus instance methods
extern aliases, Extern
F
Fail method, Fail and Assert
fat arrow notation (=>), Instance Constructors, Expression-bodied properties
fields, Fields
clearing in disposal, Clearing Fields in Disposal
constructor and field initialization order, Constructor and field initialization order
constructors and field initialization order, Constructor and field initialization order
declaring multiple fields together, Declaring multiple fields together
emitting, Emitting Fields and Properties-Emitting Fields and Properties
initialization, Field initialization
properties versus, Properties
readonly modifier, The readonly modifier
static constructors and field initialization order, Static constructors and field initialization order
file access modifier, Access Modifiers
file and directory operations, File and Directory Operations-Catching Filesystem Events
catching filesystem events, Catching Filesystem Events
Directory class, The Directory Class
File class, The File Class-Unix file security
FileInfo and DirectoryInfo, FileInfo and DirectoryInfo
Path class, Path-Path
querying volume information, Querying Volume Information
special folders, Special Folders
File class
compression and encryption attributes, Compression and encryption attributes
shortcut methods, Constructing a FileStream
Unix file security, Unix file security
Windows file security, Windows file security
file compression, Unix gzip File Compression
file-scoped namespaces, File-Scoped Namespaces
FileInfo class, FileInfo and DirectoryInfo
FileMode, Specifying a FileMode
filenames, specifying, Specifying a filename
FileSecurity class, Windows file security
FileStream, FileStream-Advanced FileStream features
advanced features, Advanced FileStream features
constructing, Constructing a FileStream
specifying a FileMode, Specifying a FileMode
specifying a filename, Specifying a filename
FileSystemWatcher class, Catching Filesystem Events
filtering, Filtering-Distinct and DistinctBy
< and > string comparisons in EF Core, < and > string comparisons in EF Core
Distinct operator, Distinct and DistinctBy
SQL LIKE comparisons in EF Core, SQL LIKE comparisons in EF Core
Take and Skip, Take, TakeLast, Skip, SkipLast
TakeWhile and SkipWhile, TakeWhile and SkipWhile
Where, Filtering-Distinct and DistinctBy
WHERE x IN (…,…,…) in EF Core, WHERE x IN (…, …, …) in EF Core
finalizer (~), Finalizers
calling Dispose from, Calling Dispose from a Finalizer
GC and, Finalizers-GC.ReRegisterForFinalize
GC.ReRegisterForFinalize, GC.ReRegisterForFinalize
resurrection, Resurrection-GC.ReRegisterForFinalize
finally blocks, The finally Block, Iterators and try/catch/finally blocks
fine-grained concurrency, What Is Asynchronous Programming?
First operator, First, Last, and Single
FirstNode function, FirstNode, LastNode, and Nodes
FirstOrDefault operator, First, Last, and Single
fixed keyword, fixed and fixed {...}
fixed statement, The fixed Statement
fixed-size buffers, Fixed-Size Buffers
Flags attribute, Flags Enums
Flatten method, Flatten
floating-point types, Numeric Types
conversions, Converting between floating-point and integral types
special float and double values, Special Float and Double Values
fluent syntax, Fluent Syntax-Other Operators
chaining query operators, Chaining Query Operators-Why extension methods are important
composing lambda expressions, Composing Lambda Expressions-Lambda expressions and element typing
importance of extension methods, Why extension methods are important
joining in, Joining in fluent syntax
mixed-syntax queries, Mixed-Syntax Queries
natural ordering, Natural Ordering
query syntax versus, Query Syntax Versus Fluent Syntax
for loops, for loops
foreach loops, foreach loops
foreground threads, Foreground Versus Background Threads
form data, uploading, Uploading Form Data
format item, String.Format and composite format strings
formatting and parsing, Formatting and Parsing-DateTimeStyles
BitConverter, BitConverter
composite formatting, Composite formatting
Convert class, Convert-Base-64 conversions
custom numeric format strings, Numeric Format Strings
Date/Time format strings, Date/Time Format Strings-Parsing and misparsing DateTimes
DateTimeFormatInfo, Using NumberFormatInfo or DateTimeFormatInfo
DateTimeStyles, DateTimeStyles
enum format strings, Enum Format Strings
enums, Enums-How Enums Work
equality comparison, Equality Comparison-Pluggable equality comparers
format providers, Format Providers-IFormatProvider and ICustomFormatter
format providers and CultureInfo, Format providers and CultureInfo
format string, String.Format and composite format strings
globalization, Globalization
Guid struct, The Guid Struct
IFormatProvider and ICustomFormatter, IFormatProvider and ICustomFormatter
NumberFormatInfo, Using NumberFormatInfo or DateTimeFormatInfo
NumberStyles, NumberStyles
numeric format strings, Numeric Format Strings
parsing with format providers, Parsing with format providers
standard format strings and parsing flags, Standard Format Strings and Parsing Flags-Enum Format Strings
ToString and Parse methods, ToString and Parse
type converters, Type Converters
working with numbers, Conversions-Random
XmlConvert, XmlConvert
FormatTransitionTime, TimeZoneInfo
forward slash (/)
as division operator, Arithmetic Operators
trailing in URIs, URIs
forward slash, double (//), A First C# Program, Comments
forward-only enumerators, Forward-Only Enumerators-Forward-Only Enumerators
frameworks, Runtimes
(see also runtimes)
friend assemblies, Friend Assemblies
frozen collections, Frozen Collections
fully qualified names, Fully Qualified Names
Func delegate, The Func and Action Delegates, Lambda expressions and Func signatures
function pointers, Function Pointers, Callbacks with Function Pointers
functional construction, Functional Construction
functional programming, Immutable Collections
G
garbage collection (GC), Automatic Garbage Collection-Roots
array pooling, Array Pooling
automatic, Automatic Garbage Collection-Roots
background collection, Background collection
defined, Disposal and Garbage Collection
finalizers, Finalizers-GC.ReRegisterForFinalize
forcing, Forcing Garbage Collection
generational collection, Generational collection
Large Object Heap, The Large Object Heap
managed memory leaks, Managed Memory Leaks-Diagnosing Memory Leaks
memory consumption and, Automatic Garbage Collection
memory pressure, Memory Pressure
notifications, GC notifications
optimization, Optimization Techniques-Forcing Garbage Collection
process of, How the GC Works-Array Pooling
resurrection, Resurrection-GC.ReRegisterForFinalize
roots, Roots
tuning at runtime, Tuning Garbage Collection at Runtime
weak references, Weak References-Weak References and Events
workstation versus server collection, Workstation versus server collection
GC...
GC.AddMemoryPressure, Memory Pressure
GC.Collect, Forcing Garbage Collection
GC.EndNoGCRegion, Tuning Garbage Collection at Runtime
GC.RegisterForFullGCNotification, GC notifications
GC.RemoveMemoryPressure, Memory Pressure
GC.ReRegisterForFinalize, GC.ReRegisterForFinalize
GC.SuppressFinalize, Calling Dispose from a Finalizer
GC.TryStartNoGCRegion, Tuning Garbage Collection at Runtime
GC.WaitForFullGCApproach, GC notifications
GC.WaitForFullGCComplete, GC notifications
GCNotificationStatus, GC notifications
GCSettings.LatencyMode, Tuning Garbage Collection at Runtime
generational garbage collection, Generational collection
generic interface, Anonymously Calling Members of a Generic Interface
generic math, Generic Math-Generic Math
generic methods, Generic Methods
defining, Defining Generic Methods
emitting, Emitting Generic Methods and Types-Defining Generic Types
retrieving/invoking, Retrieving and invoking generic methods
generic types
anonymously calling members of, Anonymously Calling Members of a Generic Type-Anonymously Calling Members of a Generic Type
C++ templates versus, C# Generics Versus C++ Templates
defining, Defining Generic Types
delegate types, Generic Delegate Types, Generic delegate type parameter variance
emitting, Emitting Generic Methods and Types-Defining Generic Types
obtaining member metadata, Generic Type Members
reflection, Generic Types
type names, Generic type names
generics, Generics-C# Generics Versus C++ Templates
C# generics versus C++ templates, C# Generics Versus C++ Templates
constraints, Generic Constraints-Generic Constraints
contravariance, Contravariance
covariance, Covariance-Declaring a covariant type parameter
declaring type parameters, Declaring Type Parameters
default generic value, The default Generic Value
generic methods, Generic Methods
generic types, Generic Types
purpose of, Why Generics Exist
self-referencing generic declarations, Self-Referencing Generic Declarations
static data, Static Data
subclassing generic types, Subclassing Generic Types
type parameters and conversion, Type Parameters and Conversions
typeof operator, typeof and Unbound Generic Types
unbound generic type, typeof and Unbound Generic Types
get accessor, get and set accessibility
Get...
GetAsync method, GetAsync and Response Messages
GetBytes method, Encoding to byte arrays
GetData method, GetData and SetData
GetEncodings method, Obtaining an Encoding object
GetEnumerator method, Enumeration, Implementing the Enumeration Interfaces
GetHashCode, Overriding GetHashCode
GetInterfaceMap method, Calling Static Virtual/Abstract Interface Members
GetMembers method, Reflecting and Invoking Members-Reflecting and Invoking Members
GetString method, Encoding to byte arrays
GetType method, Static and Runtime Type Checking
GetUnicodeCategory method, Char
GetValue method, Construction and Indexing
global keyword, Namespace alias qualifiers
global using directive (C# 10), The global using Directive
globalization, Globalization
checklist, Globalization Checklist
defined, Globalization
testing against different cultures, Testing
goto statement, The goto statement
greedy quantifiers, Greedy Versus Lazy Quantifiers
GroupBy operator, GroupBy-Custom equality comparers
grouping (LINQ), GroupBy-Custom equality comparers
GroupJoin operator (LINQ), GroupJoin-Enumerable implementations
enumerable implementations, Enumerable implementations
flat outer joins, Flat outer joins
joining with lookups, Joining with lookups
groups
named groups, Named Groups
regular expressions, Groups-Named Groups
Guid struct, The Guid Struct
Guid.NewGuid, The Guid Struct
gzip file compression, Unix gzip File Compression
GZipStream, Compression Streams
H
Half struct, Half
Handle method, Handle
hash (#), Preprocessor Directives, Conditional Compilation
hash partitioning, Input-side optimization
hashcode, Overriding GetHashCode, Hashing
hashing, Hashing-Hashing Passwords
hash algorithms in .NET, Hash Algorithms in .NET
passwords, Hashing Passwords
hashing algorithm, Hashing
HashSet<T>, HashSet<T> and SortedSet<T>
Hashtable class, Dictionary<TKey,TValue> and Hashtable-Dictionary<TKey,TValue> and Hashtable
hashtables, Overriding GetHashCode
headers, Headers
heap, Heap
HideBySig, HideBySig
hiding inherited members, Hiding Inherited Members
HTTP (Hypertext Transfer Protocol)
cookies, Cookies
headers, Headers
query strings, Query Strings
uploading form data, Uploading Form Data
writing an HTTP server, Writing an HTTP Server-Writing an HTTP Server
HttpClient, HttpClient-Cookies
authentication via headers with, Authenticating via headers
chaining handlers with DelegatingHandler, Chaining handlers with DelegatingHandler
cookies, Cookies
custom headers, Headers
GetAsync and response messages, GetAsync and Response Messages
HttpMessageHandler, HttpMessageHandler
proxies with, Proxies
SendAsync and request messages, SendAsync and Request Messages
unit testing and mocking, Unit testing and mocking
uploading data and HttpContent, Uploading Data and HttpContent
HttpClientHandler, HttpClient, Proxies, Cookies
HttpContent, Uploading Data and HttpContent
HttpListener, Writing an HTTP Server-Writing an HTTP Server
HttpMessageHandler, HttpMessageHandler
HttpRequestMessage, SendAsync and Request Messages
HttpResponseMessage, GetAsync and Response Messages
HybridDictionary, ListDictionary and HybridDictionary
Hypertext Transfer Protocol (see HTTP)
hyphen (-), Character Sets
I
IANA (Internet Assigned Numbers Authority) Character Set, Obtaining an Encoding object
IAsyncAction, IProgress<T> and Progress<T>
IAsyncDisposable, Asynchronous Streams
IAsyncEnumerable<T>, Asynchronous Streams
in ASP.Net Core, IAsyncEnumerable<T> in ASP.Net Core
querying, Querying IAsyncEnumerable<T>
IAsyncOperation<TResult>, IProgress<T> and Progress<T>
IAsyncOperationWithProgress<TResult>, IProgress<T> and Progress<T>
IAsyncResult, Asynchronous Programming Model
ICollection, The ICollection and IList Interfaces-IReadOnlyCollection<T> and IReadOnlyList<T>
ICollection<T>, The ICollection and IList Interfaces-IReadOnlyCollection<T> and IReadOnlyList<T>
IComparable interface, IComparable, Comparers and collations
Equals versus, IComparable versus Equals
implementing, Implementing the IComparable Interfaces
IComparer, Order Comparison
IConvertible, Convert
ICustomFormatter, IFormatProvider and ICustomFormatter
IDbConnection, Close and Stop
identifiers, Identifiers and Keywords-Contextual keywords
IDictionary, IDictionary
IDictionary<TKey,TValue>, IDictionary<TKey,TValue>
IDispatch interface, Dynamic Binding
IDisposable, IDisposable, Dispose, and Close-Anonymous Disposal
anonymous disposal and, Anonymous Disposal-Anonymous Disposal
IEnumerable<T> and, IEnumerable<T> and IDisposable
IDynamicMetaObjectProvider (IDMOP), Custom Binding, Implementing Dynamic Objects
IEnumerable, IEnumerable and IEnumerator, Implementing the Enumeration Interfaces-Implementing the Enumeration Interfaces
IEnumerable<char>, Accessing characters within a string
IEnumerable<T>, Iterators, IEnumerable<T> and IEnumerator<T>-IEnumerable<T> and IDisposable
IDisposable and, IEnumerable<T> and IDisposable
implementing the enumeration interfaces, Implementing the Enumeration Interfaces-Implementing the Enumeration Interfaces
LINQ conversion methods and, Conversion Methods-AsEnumerable and AsQueryable
IEnumerator, IEnumerable and IEnumerator
IEnumerator<T>, Iterators, IEnumerable<T> and IEnumerator<T>-IEnumerable<T> and IDisposable
IEqualityComparer, Pluggable equality comparers, IEqualityComparer and EqualityComparer-ReferenceEqualityComparer.Instance (.NET 5+)
IEquatable<T>, The IEquatable<T> interface, Implementing IEquatable<T>
#if directive, Conditional Compilation
if statement, The if statement
IFormatProvider, IFormatProvider and ICustomFormatter
IFormattable, Format Providers
IgnorePatternWhitespace (?x), RegexOptions
IL (intermediate language)
CLR and, Common Language Runtime
dynamic code generation, Dynamic Code Generation-Exception Handling
evaluation stack, The Evaluation Stack
exception handling, Exception Handling
generating with DynamicMethod, Generating IL with DynamicMethod-Generating IL with DynamicMethod
instantiating objects and calling instance methods, Instantiating Objects and Calling Instance Methods
parsing, Parsing IL-Writing a Disassembler
writing a disassembler, Writing a Disassembler-Writing a Disassembler
ildasm tool, Common Language Runtime
IList, The ICollection and IList Interfaces-IReadOnlyCollection<T> and IReadOnlyList<T>
IList<T>, The ICollection and IList Interfaces, IList<T> and IList
immutable collections, Immutable Collections-Immutable Collections and Performance
builders, Builders
creating, Creating Immutable Collections
manipulating, Manipulating Immutable Collections
performance, Immutable Collections and Performance
immutable objects, Immutable Objects
ImmutableArray<T>, Immutable Collections and Performance
ImmutableList<T>, Immutable Collections and Performance
imperative parallelism, PFX Components
implicit conversions, Types and Conversions, Converting between integral types
implicit global using directives, Implicit global usings
implicit ref parameters, Implicit ref Parameters
implicit typing, var—Implicitly Typed Local Variables
in parameter, The in modifier
increment operator (++), Increment and Decrement Operators
indexed filtering, Indexed filtering
indexers, Indexers-Using indices and ranges with indexers
CLR indexer implementation, CLR indexer implementation
implementing, Implementing an indexer
using indices and ranges with, Using indices and ranges with indexers
IndexOfAny method, Searching within strings
indices
arrays and, Indices
bounds checking, Bounds Checking
inequality operator (!=), Equality and Comparison Operators, Equality operators (== and !=), == and !=, Overloading == and !=
inheritance, Inheritance-Overloading and Resolution
abstract classes/abstract members, Abstract Classes and Abstract Members
base keyword, The base Keyword
casting and reference conversions, Casting and Reference Conversions-Introducing a pattern variable
constructors and, Constructors and Inheritance-Inheritance with primary constructors
hiding inherited members, Hiding Inherited Members
overloading and resolution, Overloading and Resolution
polymorphism, Polymorphism
sealing functions and classes, Sealing Functions and Classes
virtual function members, Virtual Function Members
init-only properties (C# 9), Init-only properties
init-only setters, Init-only setters
initialization
fields, Field initialization
instance constructor and field initialization order, Constructor and field initialization order
lazy (see lazy initialization)
object initializers, Object Initializers
property initializer, Property initializers
static constructor and field initialization order, Static constructors and field initialization order
Initialization Vector (IV), Symmetric Encryption
INotifyPropertyChanged interface, Change Tracking
INotifyPropertyChanging interface, Change Tracking
instance constructors, Instance Constructors
constructor and field initialization order, Constructor and field initialization order
implicit parameterless, Implicit parameterless constructors
nonpublic constructors, Nonpublic constructors
overloading, Overloading constructors
instance fields, ThreadLocal<T> and, ThreadLocal<T> and instance fields
instance methods
delegates and, Instance and Static Method Targets
extension methods versus, Extension methods versus instance methods
generating, Generating instance methods
instance, static members versus, Instance versus static members
instantiating a type, Constructors and instantiation, Instantiating Types-Instantiating Types
instruction atomicity, Locking and Atomicity
int type, Type Basics
integral types
8- and 16-bit integral types, 8- and 16-Bit Integral Types
conversions, Converting between integral types
enum conversions, Enum to integral conversions
native-sized integers, Native-Sized Integers-Runtime handling when targeting .NET 6 or below
specialized operations on, Specialized Operations on Integral Types
integral-type literals, Numeric Literals
interface, Interfaces-Static virtual/abstract interface members
alternatives to reimplementation, Alternatives to interface reimplementation
boxing and, Interfaces and Boxing
default implementation, Default Interface Members
defined, Object Orientation
delegates versus, Delegates Versus Interfaces
explicit implementation, Explicit Interface Implementation
extending, Extending an Interface
reimplementing in a subclass, Reimplementing an Interface in a Subclass-Alternatives to interface reimplementation
static interface members, Static Interface Members-Static virtual/abstract interface members
virtual implementation, Implementing Interface Members Virtually
when to use nongeneric interfaces, IEnumerable<T> and IDisposable
writing a class versus an interface, Static virtual/abstract interface members
interface constraint, Generic Constraints
intermediate language (see IL)
internal access modifier, Access Modifiers
internationalization, Globalization
Internet Assigned Numbers Authority (IANA) Character Set, Obtaining an Encoding object
interoperability, Native and COM Interoperability-Enabling Registry-Free COM
mapping structs to unmanaged memory, Mapping a Struct to Unmanaged Memory-fixed and fixed {...}
shared memory, Shared Memory-Shared Memory
simulating C unions, Simulating a C Union
interpolated string, String interpolation
interpolation, String interpolation
interpreted queries, Interpreted Queries-AsEnumerable
AsEnumerable operator, AsEnumerable
combining local queries with, Combining Interpreted and Local Queries
execution, Execution
mechanism of operation, How Interpreted Queries Work
interprocess communication (IPC), PipeStream
Intersect operator, Intersect, Intersect By, Except, and ExceptBy
into keyword, The into Keyword
INumber<TSelf> interface, Generic Math
IOrderedEnumerable, IOrderedEnumerable and IOrderedQueryable
IOrderedQueryable, IOrderedEnumerable and IOrderedQueryable
IPAddress class, Addresses and Ports
IPC (interprocess communication), PipeStream
IPEndPoint class, Addresses and Ports
IProducerConsumerCollection<T>, IProducerConsumerCollection<T>
IProgress<T>, IProgress<T> and Progress<T>
IPv4/IPv6 addresses, Addresses and Ports
IQueryable<T>, Interpreted Queries-Execution
IReadOnlyCollection<T>, IReadOnlyCollection<T> and IReadOnlyList<T>
IReadOnlyList<T>, IReadOnlyCollection<T> and IReadOnlyList<T>
is operator, The is operator
IStructuralComparable, IStructuralEquatable and IStructuralComparable
IStructuralEquatable, IStructuralEquatable and IStructuralComparable
iteration statements, Iteration Statements-foreach loops
for loops, for loops
foreach loops, foreach loops
while and do-while loops, while and do-while loops
iteration variables, Capturing iteration variables
iterators, Iterators-Iterators, Implementing the Enumeration Interfaces
composing sequences, Composing Sequences
semantics, Iterator Semantics-Iterators and try/catch/finally blocks
try/catch/finally blocks, Iterators and try/catch/finally blocks
yield break statement, yield break
IUnknown interface, Exposing C# Objects to COM
IV (Initialization Vector), Symmetric Encryption
J
jagged arrays, Jagged arrays
JIT (Just-in-Time) compilation, Common Language Runtime
Join method (strings), Splitting and joining strings
Join method (threading), Join and Sleep
Join operator (LINQ), Join and GroupJoin-The Zip Operator
basics, Overview
joining in fluent syntax, Joining in fluent syntax
joining on multiple keys, Joining on multiple keys
joining, Join and GroupJoin-The Zip Operator
SelectMany, Joining with SelectMany
strings, Splitting and joining strings
JSON, Working with JSON-Making updates with a JSON writer
JsonDocument, JsonDocument-Making updates with a JSON writer
Utf8JsonReader, Utf8JsonReader-JsonReaderOptions
JsonCommentHandling, JsonReaderOptions
JsonDocument, JsonDocument-Making updates with a JSON writer
LINQ and, JsonDocument and LINQ
making updates with a JSON writer, Making updates with a JSON writer
reading JSON arrays, Reading JSON arrays
reading JSON objects, Reading JSON objects
reading simple values, Reading simple values
JsonNode, JsonNode-Constructing a JsonNode DOM programmatically
constructing a JsonNode DOM programmatically, Constructing a JsonNode DOM programmatically
fluent traversal and LINQ, Fluent traversal and LINQ
making updates with, Making updates with JsonNode
reading JSON arrays, Reading JSON arrays
reading JSON objects, Reading JSON objects
reading simple values, Reading simple values
JsonReaderOptions, JsonReaderOptions
JsonWriterOptions, Utf8JsonWriter
jump statements, Jump Statements-The throw statement
break statement, The break statement
continue statement, The continue statement
goto statement, The goto statement
return statement, The return statement
throw statement, The throw statement
Just-in-Time (JIT) compilation, Common Language Runtime
K
key management, Key Management
keywords, Identifiers and Keywords-Contextual keywords
L
lambda expressions, Lambda Expressions-Lambda Expressions Versus Local Methods
anonymous methods versus, Anonymous Methods
applying attributes to (C# 10), Applying Attributes to Lambda Expressions
asynchronous, Asynchronous Lambda Expressions
captured variables and, Lambda expressions and captured variables
capturing iteration variables, Capturing iteration variables
capturing outer variables, Capturing Outer Variables-Capturing iteration variables
composing, Composing Lambda Expressions-Lambda expressions and element typing
default lambda parameters (C# 12), Default Lambda Parameters (C# 12)
element typing and, Lambda expressions and element typing
explicitly specifying parameter/return types, Explicitly Specifying Lambda Parameter and Return Types
Func signatures and, Lambda expressions and Func signatures
local methods versus, Lambda Expressions Versus Local Methods
static lambdas (C# 9), Static lambdas
subqueries, Subqueries-Subqueries and Deferred Execution
lambda operator (=>), Lambda Expressions
language binding, Language Binding
Language-Integrated Query (LINQ) (see LINQ entries)
Large Object Heap (LOH), The Large Object Heap
Last operator, First, Last, and Single
Last-In First-Out (LIFO), Stack<T> and Stack
LastIndexOf method, Searching within strings
LastNode function, FirstNode, LastNode, and Nodes
late binding, Dynamically Invoking a Member
lazy evaluation, Calculated Fields and Lazy Evaluation-Calculated Fields and Lazy Evaluation
lazy execution (see deferred execution)
lazy initialization, Lazy Initialization-LazyInitializer
Lazy<T> class, Lazy<T>
LazyInitializer class, LazyInitializer
lazy quantifiers, Greedy Versus Lazy Quantifiers
Lazy<T> class, Lazy<T>
LazyInitializer class, LazyInitializer
left-associative operators, Left-associative operators
let keyword, The let Keyword
LIFO (Last-In First-Out), Stack<T> and Stack
LIKE operator, SQL LIKE comparisons in EF Core
LinkedList<T>, LinkedList<T>
LINQ operators, LINQ Operators-Range and Repeat
aggregation methods, Aggregation Methods-Traps with unseeded aggregations
conversion methods, Conversion Methods-AsEnumerable and AsQueryable
element operators, Element Operators-DefaultIfEmpty
filtering, Filtering-Distinct and DistinctBy
generation methods, Generation Methods
grouping, GroupBy-Custom equality comparers
joining, Join and GroupJoin-The Zip Operator
ordering, Ordering-IOrderedEnumerable and IOrderedQueryable
overview, Overview-Generation methods
projecting, Projecting-Outer joins with SelectMany
quantifiers, Quantifiers
sequence to element or value, Sequence→Element or Value
sequence to sequence, Sequence→Sequence-Conversion methods: Export
set operators, Set Operators
void to sequence, Void→Sequence
Zip operator, The Zip Operator
LINQ queries, LINQ Queries-The Expression DOM
anonymous types, Anonymous Types
basics, Getting Started-Getting Started
composition strategies, Composition Strategies-Wrapping Queries
deferred execution, Deferred Execution-How Queries Are Executed
fluent syntax, Fluent Syntax-Other Operators
interpreted queries, Interpreted Queries-AsEnumerable
into keyword, The into Keyword
JsonDocument and, JsonDocument and LINQ
let keyword, The let Keyword
object initializers, Object Initializers
progressive query building, Progressive Query Building-Progressive Query Building
projecting into an X-DOM, Projecting into an X-DOM-Streaming a Projection
projection strategies, Object Initializers-The let Keyword
query expressions, Query Expressions-Mixed-Syntax Queries
subqueries, Subqueries-Subqueries and Deferred Execution
wrapping queries, Wrapping Queries
LINQ to XML, LINQ to XML-Streaming a Projection
annotations, Annotations
architectural overview, Architectural Overview
documents and declarations, XDocument-XDocument
LINQ to XML DOM, The LINQ to XML DOM
names and namespaces, Names and Namespaces-Prefixes
X-DOM (see XML DOM)
XML declarations, XML Declarations
LINQ, JsonDocument and, JsonDocument and LINQ
LINQ-to-objects queries, Getting Started
list patterns, List Patterns
list-like collections, Lists, Queues, Stacks, and Sets-HashSet<T> and SortedSet<T>
BitArray, BitArray
HashSet<T> and SortedSet<T>, HashSet<T> and SortedSet<T>
LinkedList<T>, LinkedList<T>
List<T> and ArrayList, List<T> and ArrayList-List<T> and ArrayList
Queue<T> and Queue, Queue<T> and Queue
Stack<T> and Stack, Stack<T> and Stack
List<T> class, IList<T> and IList, List<T> and ArrayList-List<T> and ArrayList
ListDictionary, ListDictionary and HybridDictionary
Listeners, TraceListener-Flushing and Closing Listeners
literals, Literals, Punctuators, and Operators
Load...
Load(byte[]) method, LoadFile and Load(byte[])
LoadFile method, LoadFile and Load(byte[])
LoadFrom method, LoadFrom
LoadFromAssemblyName method, LoadFromAssemblyName
local methods, Local methods
lambda expressions versus, Lambda Expressions Versus Local Methods
static local methods, Static local methods
top-level statements and, Local methods and top-level statements
local queries, Combining Interpreted and Local Queries
local sequences, Getting Started
local variables
dynamic code generation, Generating Local Variables
scope of, Local variables
var keyword, var—Implicitly Typed Local Variables
LocalApplicationData, Special Folders
localization, Globalization
lock statement, Miscellaneous Statements, The lock Statement
locking
exclusive (see exclusive locking)
immutable objects, Immutable Objects
locking around thread-safe objects, Locking around thread-safe objects
nonexclusive (see nonexclusive locking)
read-only thread safety, Read-only thread safety
static members, Static members
thread safety and, Locking and Thread Safety, Locking and Thread Safety-Immutable Objects
thread safety and .NET Core types, Thread Safety and .NET Types-Read-only thread safety
thread safety in application servers, Thread Safety in Application Servers
lockTaken overloads, The lockTaken overloads
logical negation operator (!), Equality and Comparison Operators, Conditional Compilation
LOH (Large Object Heap), The Large Object Heap
LongCount operator, Count and LongCount
loop iteration index, Indexed Parallel.ForEach
M
Main method, Compilation, Defining a Main method
man-in-the-middle attack, Public-Key Encryption and Signing
managed memory leaks, Managed Memory Leaks-Diagnosing Memory Leaks
ManualResetEvent, ManualResetEvent
ManualResetEventSlim, ManualResetEvent
MARS (MultipleActiveResultSets), Deferred Execution
MatchEvaluator delegate, MatchEvaluator Delegate
Math class, Math
MAUI, MAUI, MAUI
Max operator, Min and Max
member overload resolution, Dynamic Member Overload Resolution-Anonymously Calling Members of a Generic Type
member types, Member Types
MemberInfo subclass, Member Types
memory barrier, When to Lock
memory leaks
diagnosing, Diagnosing Memory Leaks
managed memory leaks, Managed Memory Leaks-Diagnosing Memory Leaks
timers and, Timers
memory management, Common Language Runtime
mapping structs to unmanaged memory, Mapping a Struct to Unmanaged Memory-fixed and fixed {...}
shared memory, Shared Memory-Shared Memory
memory, stack-allocated/unmanaged, Working with Stack-Allocated and Unmanaged Memory
memory-mapped files, Memory-Mapped Files-Working with View Accessors
cross-platform interprocess shared memory, Cross-Platform Interprocess Shared Memory
random file I/O and, Memory-Mapped Files and Random File I/O
shared memory (Windows), Memory-Mapped Files and Shared Memory (Windows)
working with view accessors, Working with View Accessors
Memory<T>, Memory<T>-Memory<T>
MemoryStream, MemoryStream, Encrypting in Memory
metacharacters, Character Escapes
method group, Delegates
method overloading, Overloading and Resolution
method parameters, Method Parameters-Retrieving and invoking generic methods
CallerArgumentExpression and, CallerArgumentExpression
MethodAttributes.HideBySig, HideBySig
methods, Methods-Overloading methods
emitting, Emitting Methods-HideBySig
expression-bodied, Expression-bodied methods
generic, Generic Methods
local methods, Local methods
overloading, Overloading methods
overriding, Overriding methods
purpose of, A First C# Program
Microsoft Azure, Key Management
Microsoft Dataflow, Parallel Programming
Min operator, Min and Max
minus sign (-)
negative infinity (-∞), Special Float and Double Values
negative zero (-0), Special Float and Double Values
removing delegate instances, Multicast Delegates
subtraction operator, Arithmetic Operators
mocking handler, Unit testing and mocking
module initializers, Static Constructors
modules, assembly, Modules, Modules
Monitor.Enter, Monitor.Enter and Monitor.Exit
Monitor.Exit, Monitor.Enter and Monitor.Exit
MoveNext method, Iterators
multicast delegates, Multicast Delegates
multidimensional arrays, Multidimensional Arrays
multiline comments (/* */), Comments, XML Documentation
multiple dispatch, Anonymously Calling Members of a Generic Type
MultipleActiveResultSets (MARS), Deferred Execution
multithreaded program, Threading
multithreaded timers, Multithreaded Timers-Multithreaded Timers
multithreading (see parallel programming)
Mutex, Mutex
N
naked type constraint, Generic Constraints
name hiding, Name hiding
name scoping, Name scoping
named arguments, Named arguments
named groups, Named Groups
named pipes, Named pipes-Named pipes
nameof operator, The nameof operator
namespace alias qualification (::), Namespace alias qualifiers
namespaces, A First C# Program, Namespaces-Namespace alias qualifiers
advanced features, Extern-Namespace alias qualifiers
alias qualifiers, Namespace alias qualifiers
aliasing types and, Aliasing Types and Namespaces
attributes, Attributes
defining, Defining namespaces
extension methods and, Namespaces
extern aliases, Extern
file-scoped, File-Scoped Namespaces
name hiding, Name hiding
name scoping, Name scoping
nested using directives withing, Nested using directives
prefixes, Prefixes
repeated, Repeated namespaces
rules within, Name scoping-Nested using directives
using directive and, The using Directive
using static directive and, using static
X-DOM, Specifying Namespaces in the X-DOM-The X-DOM and Default Namespaces
XML, Names and Namespaces-Prefixes
XmlReader and, Namespaces and Prefixes
XmlWriter and, Namespaces and Prefixes
native-sized integers, Native-Sized Integers-Runtime handling when targeting .NET 6 or below
runtime handling when targeting .NET 6 or below, Runtime handling when targeting .NET 6 or below
runtime handling when targeting .NET 7+, Runtime handling when targeting .NET 7+
navigation properties, Navigation Properties-Lazy loading
adding and removing entities from navigation collections, Adding and removing entities from navigation collections
lazy loading, Lazy loading
loading, Loading navigation properties
negative lookahead, Lookahead and Lookbehind
negative lookbehind, Lookahead and Lookbehind
nested locking, Nested Locking
nested types, Nested Types-Nested Types
obtaining, Obtaining nested types
type names, Nested type names
.NET
fundamentals, .NET Fundamentals-AppContext
overview, .NET Overview-MAUI
runtime targets and TFMs, Runtime Targets and TFMs
standard disposal semantics, Standard Disposal Semantics
.NET Core
CLR and BCL, The CLR and BCL-The Roslyn Compiler
collections (see collections)
.NET Framework
about, .NET Framework
application layers, Application Layers-MAUI
compilation, Compilation
.NET Micro Framework, Niche Runtimes
.NET Standard, .NET Standard-.NET Framework and .NET 8 Compatibility
C# language versions and, Runtime and C# Language Versions
.NET Framework and .NET 8 compatibility, .NET Framework and .NET 8 Compatibility
.NET Standard 2.0, .NET Standard 2.0
.NET Standard 2.1, Other .NET Standards
older .NET Standards, Other .NET Standards
reference assemblies, Reference Assemblies
networking, Networking-Receiving POP3 Mail with TCP
addresses and ports, Addresses and Ports
architecture, Network Architecture
concurrency with TCP, Concurrency with TCP
receiving POP3 mail with TCP, Receiving POP3 Mail with TCP-Receiving POP3 Mail with TCP
sending mail with SmtpClient, Sending Mail with SmtpClient
URIs, URIs-URIs
using DNS, Using DNS
using TCP, Using TCP-Concurrency with TCP
writing an HTTP server, Writing an HTTP Server-Writing an HTTP Server
new keyword, Hiding Inherited Members
niche runtimes, Niche Runtimes
Nodes function, FirstNode, LastNode, and Nodes
nondestructive mutation, Nondestructive Mutation
nonexclusive locking, Nonexclusive Locking-Lock recursion
lock recursion, Lock recursion
reader/writer locks, Reader/Writer Locks-Lock recursion
semaphore, Semaphore-Writing an EnterAsync extension method
upgradeable locks, Upgradeable locks-Lock recursion
nongeneric interfaces, IEnumerable<T> and IDisposable
nonpublic constructors, Nonpublic constructors
nonpublic members, Accessing Nonpublic Members
null operators, Null Operators-Null-Conditional Operator, Nullable Value Types and Null Operators
null reference, Null
null strings, Null and empty strings
null value, literal for, Null
null-coalescing assignment operators, Null-Coalescing Assignment Operator
null-coalescing operator (??), Null-Coalescing Operator, Nullable Value Types and Null Operators
null-conditional operator (?.), Null-Conditional Operator, Standard Event Pattern, Nullable Value Types and Null Operators
null-forgiving operator (!), The Null-Forgiving Operator
#nullable enable directive, Separating the Annotation and Warning Contexts
nullable annotation context, Separating the Annotation and Warning Contexts
nullable reference types, Nullable Reference Types-Treating Nullable Warnings as Errors
null-forgiving operator, The Null-Forgiving Operator
separating annotation and warning contexts, Separating the Annotation and Warning Contexts
treating nullable warnings as errors, Treating Nullable Warnings as Errors
nullable types, Null
nullable value types, Nullable Value Types-Alternatives to Nullable Value Types
alternatives to, Alternatives to Nullable Value Types
bool? with & and | operators, bool? with & and | Operators
boxing/unboxing nullable values, Boxing and Unboxing Nullable Values
implicit/explicit nullable conversions, Implicit and Explicit Nullable Conversions
null operators and, Nullable Value Types and Null Operators
Nullable<T> struct, Nullable<T> Struct
operator lifting, Operator Lifting
scenarios for, Scenarios for Nullable Value Types
Nullable<T> struct, Nullable<T> Struct
NullReferenceException, Common Exception Types, Nullable Reference Types
NumberFormatInfo, Using NumberFormatInfo or DateTimeFormatInfo
NumberStyles, Parsing with format providers, NumberStyles
numeric format strings, Numeric Format Strings
numeric literals, Numeric Literals
numeric suffixes, Numeric suffixes
type inference, Numeric literal type inference
numeric suffixes, Numeric suffixes
numeric types, Numeric Types-Real Number Rounding Errors, Conversions-Random
8- and 16-bit integral types, 8- and 16-Bit Integral Types
arithmetic operators, Arithmetic Operators
BigInteger struct, BigInteger
char type conversions, Char Conversions
Complex struct, Complex
conversions, Converting between integral types, Conversions
double versus decimal, double Versus decimal
increment and decrement operators, Increment and Decrement Operators
Math class, Math
numeric literals, Numeric Literals
Random class, Random
real number rounding errors, Real Number Rounding Errors
special float and double values, Special Float and Double Values
specialized operations on integral types, Specialized Operations on Integral Types
O
object initializers, Object Initializers
LINQ queries and, Object Initializers
optional parameters versus, Object Initializers
object instantiation, Constructor and field initialization order
object tracking, Object Tracking
object type, The object Type-Object Member Listing
boxing and unboxing, Boxing and Unboxing
GetType method and typeof operator, The GetType Method and typeof Operator
object member listing, Object Member Listing
static/runtime type checking, Static and Runtime Type Checking
ToString method, The ToString Method
Object...
Object.Equals method, The virtual Object.Equals method-The static object.Equals method
object.Equals static method, The static object.Equals method, Overriding Equals
object.Equals virtual method, The virtual Object.Equals method
object.ReferenceEquals method, The static object.ReferenceEquals method
object.System.Object class, The object Type
objects
heap and, Heap
implementing dynamic objects, Implementing Dynamic Objects-ExpandoObject
OfType operator, OfType and Cast
OperationCanceledException, Canceling Tasks
OperationCompleted method, OperationStarted and OperationCompleted
OperationStarted method, OperationStarted and OperationCompleted
operator lifting
equality operators (== and !=), Equality operators (== and !=)
mixing nullable and non-nullable operators, Mixing nullable and non-nullable types
nullable value types, Operator Lifting
relational operators, Relational operators (<, <=, >=, >)
operator overloading, Operator Overloading-Overloading true and false
checked operators, Checked operators
custom implicit/explicit conversions, Custom Implicit and Explicit Conversions
operator functions, Operator Functions
overloading equality/comparison operators, Overloading Equality and Comparison Operators
true/false operators, Overloading true and false
operator, defined, Literals, Punctuators, and Operators
optional parameters, Optional parameters
named arguments and, Optional Parameters and Named Arguments
object initializers versus, Object Initializers
order comparison, Comparing Strings, Order Comparison-Implementing the IComparable Interfaces
<and>, < and >
IComparable interface, IComparable
implementing IComparable interfaces, Implementing the IComparable Interfaces
OrderBy operator, Overview
OrderByDescending operator, Overview
OrderedDictionary, OrderedDictionary
ordering
comparers and collations, Comparers and collations
IOrderedEnumerable and IOrderedQueryable, IOrderedEnumerable and IOrderedQueryable
LINQ operators and, Ordering-IOrderedEnumerable and IOrderedQueryable
OrderBy and OrderByDescending arguments, Overview
PLINQ and, PLINQ and Ordering
ordinal case-sensitive comparison, String equality comparison
ordinal string comparison, Ordinal versus culture comparison
OS security, OS Security-Administrative Elevation and Virtualization
administrative elevation and virtualization, Administrative Elevation and Virtualization
running in a standard user account, Running in a Standard User Account
out parameter
passing, Dealing with ref and out parameters
type names, ref and out parameter type names
out parameter modifier, The out modifier
out variables, Out variables and discards
outer joins
GroupJoin, Flat outer joins
SelectMany, Outer joins with SelectMany
outer variables, Capturing Outer Variables-Capturing iteration variables
overflow, Overflow
overflow check operators
for constant expressions, Overflow checking for constant expressions
integral types and, Overflow check operators
overloading
equality operator (==), Overloading Equality and Comparison Operators, Overloading == and !=
instance constructors, Overloading constructors
lockTaken overloads, The lockTaken overloads
operator (see operator overloading)
overloading methods, Overloading methods
resolution and, Overloading and Resolution, Dynamic Member Overload Resolution-Anonymously Calling Members of a Generic Type
override modifier, Virtual Function Members, new versus override
oversubscription, Hygiene in the thread pool
P
Parallel class, The Parallel Class-Optimization with local values
Parallel.For and Parallel.ForEach, Parallel.For and Parallel.ForEach-Optimization with local values
Parallel.Invoke, Parallel.Invoke
Parallel Framework (PFX), Parallel Programming-When to Use PFX
benefits of, Why PFX?-When to Use PFX
components, PFX Components-PFX Components
concepts, PFX Concepts
when to use, When to Use PFX
Parallel LINQ (see PLINQ)
parallel programming, Parallel Programming-Using Tasks
AggregateException and, Working with AggregateException-Handle
BlockingCollection<T>, BlockingCollection<T>-Using Tasks
concurrent collections, Concurrent Collections-ConcurrentBag<T>
Parallel class, The Parallel Class-Optimization with local values
PFX benefits, Why PFX?-When to Use PFX
PLINQ (see PLINQ)
task parallelism, Task Parallelism-Creating your own task factories
Parallel.For, Parallel.For and Parallel.ForEach-Optimization with local values
optimization with local values, Optimization with local values-Optimization with local values
ParallelLoopState, ParallelLoopState: breaking early out of loops
Parallel.ForEach, Parallel.For and Parallel.ForEach-Optimization with local values
indexed, Indexed Parallel.ForEach
optimization with local values, Optimization with local values-Optimization with local values
outer versus inner loops, Outer versus inner loops
ParallelLoopState, ParallelLoopState: breaking early out of loops
Parallel.Invoke, Parallel.Invoke
ParallelLoopState, ParallelLoopState: breaking early out of loops
parameter lists, Parameter lists, Parameter lists
parameter marshaling, Marshaling Common Types-Calling Conventions
parameterless constructor, Implicit calling of the parameterless base-class constructor
parameterless constructor constraint, Generic Constraints
parameters, Parameters-Target-Typed new Expressions
implications of passing arguments by reference, Implications of passing by reference
in modifier, The in modifier
named arguments and, Named arguments
optional parameters, Optional parameters
out modifier, The out modifier
out variables and discards, Out variables and discards
params modifier, The params modifier
passing arguments by value, Passing arguments by value
ref modifier, The ref modifier
params modifier, The params modifier
parentheses (), Literals, Punctuators, and Operators, Primary Expressions
Parse method, TimeSpan, ToString and Parse
partial methods, Partial Types and Methods, Extended partial methods
partial types, Partial Types and Methods
passing by reference
implications of, Implications of passing by reference
ref modifier, The ref modifier
passwords
hashing, Hashing Passwords
validation, Strong password validation
Path class, Path-Path
pattern combinators, Pattern Combinators
pattern variable, Introducing a pattern variable
patterns, Patterns-List Patterns
constant pattern, Constant Pattern
pattern combinators (C# 9), Pattern Combinators
positional patterns, Named and Positional Attribute Parameters
property patterns, Property Patterns
relational patterns (C# 9), Relational Patterns
tuple and positional patterns, Tuple and Positional Patterns
var pattern, var Pattern
PE (portable executable) assembly, Assemblies
performance counters, Performance Counters-Creating Counters and Writing Performance Data
creating counters and writing performance data, Creating Counters and Writing Performance Data
enumerating the available counters, Enumerating the Available Counters
reading data from, Reading Performance Counter Data
period (.), Literals, Punctuators, and Operators, Primary Expressions
PFX (see Parallel Framework)
PipeStream class, PipeStream-Anonymous pipes
anonymous pipes, Anonymous pipes-Anonymous pipes
named pipes, Named pipes-Named pipes
PLINQ (Parallel LINQ), PLINQ-Optimizing custom aggregations
canceling a query, Cancellation
custom aggregation optimization, Optimizing custom aggregations-Optimizing custom aggregations
functional purity, Functional Purity
functionality, PFX Components
input-side optimization, Input-side optimization-Input-side optimization
limitations, PLINQ Limitations
optimizing, Output-side optimization-Optimizing custom aggregations
ordering, PLINQ and Ordering
output-side optimization, Output-side optimization
parallel execution ballistics, Parallel Execution Ballistics
parallel spellchecker example, Example: Parallel Spellchecker-Using ThreadLocal<T>
setting the degree of parallelism, Setting the Degree of Parallelism
when to use, Using ThreadLocal<T>
plug-in methods, writing with delegates, Writing Plug-in Methods with Delegates
Plugin.Common, Plugin.Common
Plugin.Host, Plugin.Host-Plugin.Host
plus sign (+)
addition operator, Arithmetic Operators
combining delegate instances, Multicast Delegates
in nested type names, Nested type names
in regular expressions, Quantifiers
string concatenation operator, String concatenation
pointer-to-member operator (-), Pointer Basics, The Pointer-to-Member Operator
pointers, Unsafe Code and Pointers-[SkipLocalsInit]
basics, Pointer Basics
fixed statement and, The fixed Statement
fixed-size buffers and, Fixed-Size Buffers
function pointers (C# 9), Function Pointers
native-sized integers and, Native-Sized Integers
stackalloc keyword and, The stackalloc Keyword
type names, Array and pointer type names
void pointer (void*), void*
polymorphic operators, Polymorphic Operators-Polymorphic Operators
polymorphism, Polymorphism
POP3 mail, Receiving POP3 Mail with TCP-Receiving POP3 Mail with TCP
portable executable (PE) assembly, Assemblies
ports, TCP/UDP protocols, Addresses and Ports
positional patterns, Tuple and Positional Patterns, Named and Positional Attribute Parameters
positive infinity (+∞), Special Float and Double Values
positive lookahead, Lookahead and Lookbehind
positive lookbehind, Lookahead and Lookbehind
post-phase action, The Barrier Class
#pragma warning directive, Pragma Warning
precedence, operator, Operator Precedence and Associativity
predefined types, Predefined Type Examples, Predefined Type Taxonomy, Default Values
(see also specific types)
predicate, Composing Lambda Expressions
preempted thread, Creating a Thread
prefixes
namespaces and, Prefixes
X-DOM, Prefixes
preprocessor directives, Preprocessor Directives-Pragma Warning
Conditional attribute, Conditional Attributes
pragma warning, Pragma Warning
primary constructors, Inheritance with primary constructors, Primary Constructors-Primary Constructors
primary expressions, Primary Expressions
primitive types, Predefined Type Taxonomy
Priority property, Thread Priority
private access modifier, Access Modifiers
private key, Public-Key Encryption and Signing
private protected access modifier, Access Modifiers
Process, Process-UseShellExecute, Processes and Process Threads
examining running processes, Examining Running Processes
examining threads in a process, Examining Threads in a Process
redirecting output and error streams, Redirecting output and error streams
Process class, Thread Priority
Process.Threads property, Examining Threads in a Process
producer/consumer collection, IProducerConsumerCollection<T>
producer/consumer queue, Writing a Producer/Consumer Queue-Using Tasks
Progress<T>, IProgress<T> and Progress<T>
projecting
into an X-DOM, Projecting into an X-DOM-Streaming a Projection
LINQ operators, Projecting-Outer joins with SelectMany
Select method, Overview-Projecting into concrete types
SelectMany, Overview-Outer joins with SelectMany
properties
automatic, Automatic properties
calculated properties, Read-only and calculated properties
CLR property implementation, CLR property implementation
emitting, Emitting Fields and Properties-Emitting Fields and Properties
expression-bodied, Expression-bodied properties
get and set accessors, get and set accessibility
property initializers, Property initializers
read-only, Read-only and calculated properties
property initializer, Property initializers
property patterns, Property Patterns
property validation, Property Validation
protected access modifier, Access Modifiers
protected internal access modifier, Access Modifiers
proxy servers, Proxies
pseudocustom attributes, Attribute Basics
public access modifier, Access Modifiers
public key, Public-Key Encryption and Signing
public keyword, The public keyword
public-key encryption/signing, Public-Key Encryption and Signing-Digital Signing
digital signing, Digital Signing
RSA class, The RSA Class
punctuators, Literals, Punctuators, and Operators
Q
quantifiers, Other Operators, Quantifiers
greedy versus lazy, Greedy Versus Lazy Quantifiers
LINQ, Quantifiers, Quantifiers
regular expressions, Regular Expression Basics, Quantifiers
query continuation, The into Keyword
query expressions
about, Query Expressions-Query Expressions
building, Building Query Expressions-The Expression DOM
delegates versus expression trees, Delegates Versus Expression Trees-AsQueryable
expression DOM, The Expression DOM
expression trees, Expression Trees-The Expression DOM
mixed-syntax queries, Mixed-Syntax Queries
query syntax versus fluent syntax, Query Syntax Versus Fluent Syntax
query syntax versus SQL syntax, Query Syntax Versus SQL Syntax
range variables, Range Variables
X-DOM, Navigating and Querying-Attribute Navigation
query operators
chaining, Chaining Query Operators-Why extension methods are important
LINQ, Getting Started
query strings, Query Strings
question mark (?)
in nullable types, Nullable Value Types
in regular expressions, Regular Expression Basics, Greedy Versus Lazy Quantifiers
Queue, Queue<T> and Queue
Queue<T>, Queue<T> and Queue
quote, single (')
enclosing char literals, Strings and Characters
following generic type names, Generic type names
R
rainbow tables, Hashing Passwords
Random class, Random
Range operator, Range and Repeat
range partitioning, Input-side optimization-Input-side optimization, Optimization with local values
range variables, Range Variables
ranges
arrays and, Ranges
using indices and ranges with indexers, Using indices and ranges with indexers
raw string literals (C# 11), Raw string literals (C# 11)-Raw string literals (C# 11)
RCWs (Runtime-Callable Wrappers), Calling a COM Component from C#
Reactive Extensions, Parallel Programming
read locks, Reader/Writer Locks-Lock recursion
read-only properties, Read-only and calculated properties
read-only structs, Read-Only Structs and Functions
ReaderWriterLockSlim, Reader/Writer Locks-Lock recursion
readonly modifier, The readonly modifier, Read-Only Structs and Functions
ReadOnlyCollection<T>, ReadOnlyCollection<T>
ReadOnlySpan<char>, Forward-Only Enumerators-Forward-Only Enumerators
real literals, Numeric Literals
record structs, Parameter lists
records, Records-Records and Equality Comparison
background, Background
calculated fields and lazy evaluation, Calculated Fields and Lazy Evaluation-Calculated Fields and Lazy Evaluation
defining a record, Defining a Record-Parameter lists
equality comparison and, Records and Equality Comparison
mutability with record structs, Parameter lists
nondestructive mutation, Nondestructive Mutation
parameter lists, Parameter lists
primary constructors, Primary Constructors-Primary Constructors
property validation, Property Validation
rectangular arrays, Rectangular arrays
recursive locking, Lock recursion
reentrancy, Awaiting in a UI
ref locals, Ref Locals
ref parameter
implicit, Implicit ref Parameters
passing, Dealing with ref and out parameters
type names, ref and out parameter type names
ref parameter modifier, The ref modifier
ref returns, Ref Returns
ref structs, Ref Structs
refactoring, A First C# Program
reference assemblies, Reference Assemblies
reference conversions, Casting and Reference Conversions-Introducing a pattern variable, Contravariance
reference types, Value Types Versus Reference Types, Reference types
ReferenceEqualityComparer.Instance, ReferenceEqualityComparer.Instance (.NET 5+)
referential equality, Value Versus Referential Equality, == and !=
reflection, Reflection and Metadata-Writing a Disassembler
anonymously calling members of generic interface, Anonymously Calling Members of a Generic Interface
awkward emission targets, Awkward Emission Targets-Circular Dependencies
base types and interfaces, Base Types and Interfaces
dynamic code generation, Dynamic Code Generation-Exception Handling
emitting assemblies and types, Emitting Assemblies and Types-The Reflection.Emit Object Model
emitting constructors, Emitting Constructors
emitting fields and properties, Emitting Fields and Properties-Emitting Fields and Properties
emitting generic methods and types, Emitting Generic Methods and Types-Defining Generic Types
emitting type members, Emitting Type Members-Attaching Attributes
obtaining a type, Obtaining a Type-Obtaining nested types
parsing IL, Parsing IL-Writing a Disassembler
reflecting and activating types, Reflecting and Activating Types-Generic Types
reflecting and invoking members of a type, Reflecting and Invoking Members-Calling Static Virtual/Abstract Interface Members
reflecting assemblies, Reflecting Assemblies
type names, Type Names
working with attributes, Working with Attributes-Retrieving Attributes at Runtime
Reflection.Emit object model, The Reflection.Emit Object Model
Regex...
Regex object, Compiled Regular Expressions
Regex.Match, Regular Expression Basics
RegEx.Replace, Replacing and Splitting Text
Regex.Split, Splitting Text
RegexMatchTimeoutException, Regular Expression Basics
RegexOptions, RegexOptions
RegexOptions.Compiled, Compiled Regular Expressions
RegexOptions.Multiline, Anchors
RegisterWaitForSingleObject, Wait Handles and Continuations
regular expressions (Regex), Regular Expressions-Regular Expressions Language Reference
basics, Regular Expression Basics-Character Sets
character escapes, Character Escapes
character sets, Character Sets
compiled regular expressions, Compiled Regular Expressions
cookbook regular expressions, Extracting “name = value” pairs (one per line)-Parsing Google search terms from a web stats log
groups, Groups-Named Groups
language reference, Regular Expressions Language Reference-Regular Expressions Language Reference
MatchEvaluator delegate, MatchEvaluator Delegate
named groups, Named Groups
quantifiers, Quantifiers
RegexOptions, RegexOptions
replacing and splitting text, Replacing and Splitting Text
zero-width assertions, Zero-Width Assertions-Word Boundaries
reimplementing interfaces, Reimplementing an Interface in a Subclass-Alternatives to interface reimplementation
relational operators, Relational operators (<, <=, >=, >)
relational patterns, Relational Patterns
remainder operator (%), Arithmetic Operators
Repeat operator, Range and Repeat
Replace method, Manipulating strings
required members, Required members (C# 11)
reserved keywords, Identifiers and Keywords
Resize method, Converting and Resizing
ResourceManager class, Reading .resources files-Reading .resources files
.resources files, .resources Files-Cultures and Subcultures
resources, in assemblies, Resources and Satellite Assemblies-Cultures and Subcultures
creating a pack URI resource in Visual Studio, Creating a pack URI resource in Visual Studio
directly embedding, Directly Embedding Resources
.resources files, .resources Files-Reading .resources files
.resx files, .resx Files
resurrection, Resurrection-GC.ReRegisterForFinalize
.resx files, .resx Files
return statement, The return statement
return types, A First C# Program, Methods
covariant return types (C# 9), Covariant return types
explicitly specifying lambda parameter and return types, Explicitly Specifying Lambda Parameter and Return Types
rich-client applications
application layers, Application Layers
threading in, Threading in Rich Client Applications-Threading in Rich Client Applications
right-associative operators, Right-associative operators
Rijndael class, Symmetric Encryption, Disposing Encryption Objects
roots, garbage collection and, Roots
Round method, Math
rounding errors, Real Number Rounding Errors
rounding, real to integral conversions, Rounding real to integral conversions
RSA encryption algorithm, The RSA Class
runtime type checking, Static and Runtime Type Checking
Runtime-Callable Wrappers (RCWs), Calling a COM Component from C#
RuntimeBinderException, RuntimeBinderException, Dynamic Conversions
runtimes
defined, Runtimes
niche, Niche Runtimes
runtime targets and TFMs, Runtime Targets and TFMs
S
satellite assemblies, Satellite Assemblies-Visual Studio designer support
building, Building satellite assemblies
cultures and subcultures, Cultures and Subcultures
testing, Testing satellite assemblies
Visual Studio designer support, Visual Studio designer support
sbyte (numeric type), 8- and 16-Bit Integral Types
sealed modifier, Sealing Functions and Classes, Alternatives to interface reimplementation
searching
within an array, Searching
within spans, Searching in Spans
within strings, Searching within strings
security (see cryptography and encryption)
seed factory function, Optimizing custom aggregations
seed value, Optimizing custom aggregations
Select method, Overview-Projecting into concrete types
indexed projection, Indexed projection
projecting into concrete types, Projecting into concrete types
select subqueries and object hierarchies, Select subqueries and object hierarchies
subqueries and joins in EF Core, Subqueries and joins in EF Core
selection statements, Selection Statements
changing the flow of execution with braces, Changing the flow of execution with braces
else clause and, The else clause
if statement, The if statement
switch expressions, Switch expressions
switch statements, The switch statement-The switch statement
switching on types, Switching on types
SelectMany, Overview-Outer joins with SelectMany
in EF Core, SelectMany in EF Core
joining with, Joining with SelectMany
multiple range variables, Multiple range variables
outer joins with, Outer joins with SelectMany
thinking in query syntax, Thinking in query syntax
self-referencing type constraints, Polymorphic Operators
semaphore, Semaphore-Writing an EnterAsync extension method
asynchronous semaphores and locks, Asynchronous semaphores and locks
writing an EnterAsync extension method, Writing an EnterAsync extension method
semicolon (;), A First C# Program, Literals, Punctuators, and Operators
SendAsync method, SendAsync and Request Messages
SequenceEqual method, All and SequenceEqual
sequences, Getting Started
serialization, defined, Native-Sized Integers
set accessor, get and set accessibility
set operators (LINQ), Set Operators
Concat and Union, Concat, Union, UnionBy
Intersect and Except, Intersect, Intersect By, Except, and ExceptBy
SetData method, GetData and SetData
SetValue method, Construction and Indexing, Setting Values
shallow copy, Background
shared memory, Shared Memory-Shared Memory
shared state, Threading
shared writable state, Local Versus Shared State
shift left operator (<<), Bitwise operators
shift right operator (>>), Bitwise operators
SignalAndWait method, WaitAny, WaitAll, and SignalAndWait
signaling
constructs/performance, ManualResetEvent
event wait handles for, Signaling with Event Wait Handles-Alternatives to WaitAll and SignalAndWait
threading, Signaling
two-way, Two-way signaling
signature, Methods
signing, digital, Digital Signing
signtool.exe, Signing with signtool.exe
single dispatch, Anonymously Calling Members of a Generic Type
Single operator, First, Last, and Single
single-line comments, Comments
single-threaded program, Threading
single-threaded timers, Single-Threaded Timers
Skip operator, Take, TakeLast, Skip, SkipLast
[SkipLocalsInit] attribute, [SkipLocalsInit]
SkipWhile operator, TakeWhile and SkipWhile
slicing
defined, Span<T> and Memory<T>
list patterns and, List Patterns
spans and, Spans and Slicing-Working with Text
SmtpClient, Sending Mail with SmtpClient
SortedDictionary<TKey,TValue>, Sorted Dictionaries
SortedSet<T>, HashSet<T> and SortedSet<T>
Span<T> struct, Span<T> and Memory<T>-Working with Stack-Allocated and Unmanaged Memory
spans
CopyTo and TryCopyTo, CopyTo and TryCopyTo
forward-only enumerators, Forward-Only Enumerators-Forward-Only Enumerators
searching in, Searching in Spans
slicing and, Spans and Slicing-Working with Text
stack-allocated/unmanaged memory, Working with Stack-Allocated and Unmanaged Memory
working with text, Working with Text
spinning, blocking versus, Blocking versus spinning
Split method, Splitting and joining strings
splitting strings, Splitting and joining strings
SQL Server, Niche Runtimes
square brackets ([])
array declaration, Defining a Main method, Arrays, Jagged arrays
in collection expressions, Arrays
in list patterns, List Patterns
in regular expressions, Character Escapes
stack, The Stack and the Heap
Stack (data structure), Stack<T> and Stack
stack-allocated memory, Working with Stack-Allocated and Unmanaged Memory
Stack<T>, Stack<T> and Stack
stackalloc keyword, The stackalloc Keyword
StackFrame class, StackTrace and StackFrame-StackTrace and StackFrame
StackTrace class, StackTrace and StackFrame-StackTrace and StackFrame
StartsWith method, Searching within strings
state, Passing State Between C# and a Script
statement block, A First C# Program, Statements, Lambda Expressions
statements, A First C# Program, Statements-Miscellaneous Statements
declaration statements, Declaration Statements
expression statements, Expression Statements
iteration statements, Iteration Statements-foreach loops
jump statements, Jump Statements-The throw statement
selection statements, Selection Statements
switch statements, The switch statement-The switch statement
static abstract members, Static virtual/abstract interface members, Calling Static Virtual/Abstract Interface Members-Calling Static Virtual/Abstract Interface Members
static binding, Static Binding Versus Dynamic Binding
static classes, Static Classes, Extension Methods-Demoting an extension method
static constructors, Static Constructors
static interface members, Static Interface Members-Static virtual/abstract interface members
static nonvirtual members, Static nonvirtual interface members
static virtual/abstract members, Static virtual/abstract interface members, Calling Static Virtual/Abstract Interface Members-Calling Static Virtual/Abstract Interface Members
static keyword, Static lambdas
static lambda expressions, Static lambdas
static local methods, Static local methods
static members
instance versus, Instance versus static members
locking, Static members
static methods, Instance and Static Method Targets, Extension Methods-Demoting an extension method
static polymorphism, Static Polymorphism-Generic Math
generic math, Generic Math-Generic Math
polymorphic operators, Polymorphic Operators-Polymorphic Operators
static virtual/abstract members and, Static virtual/abstract interface members
static readonly field, Constants
static type checking, Static and Runtime Type Checking
static types, Static Types in Dynamic Expressions
static typing, Type Safety
static variable flags, Conditional Compilation Versus Static Variable Flags
static virtual members, Static virtual/abstract interface members, Calling Static Virtual/Abstract Interface Members-Calling Static Virtual/Abstract Interface Members
Stop method, Close and Stop
Stopwatch class, The Stopwatch Class
stream adapters, Stream Adapters-Closing and Disposing Stream Adapters
binary adapters, Binary Adapters
closing and disposing, Closing and Disposing Stream Adapters, Closing and Disposing Stream Adapters
text adapters, Text Adapters-StringReader and StringWriter
Stream...
Stream class, Stream Architecture
StreamReader, StreamReader and StreamWriter, Using TCP
StreamWriter, StreamReader and StreamWriter, Using TCP
streams and I/O, Streams and I/O-Working with View Accessors
backing store streams, Backing Store Streams
BufferedStream, BufferedStream
closing and flushing, Closing and Flushing
compression streams, Compression Streams-Unix gzip File Compression
file and directory operations, File and Directory Operations-Catching Filesystem Events
FileStream, FileStream-Advanced FileStream features
memory-mapped files, Memory-Mapped Files-Working with View Accessors
MemoryStream, MemoryStream
OS security, OS Security-Administrative Elevation and Virtualization
PipeStream class, PipeStream-Anonymous pipes
reading and writing, Reading and Writing
seeking, Seeking
stream adapters, Stream Adapters-Closing and Disposing Stream Adapters
stream architecture, Stream Architecture-Stream Architecture
.tar files, Working with Tar Files
thread safety, Thread Safety
timeouts, Timeouts
using streams, Using Streams-BufferedStream
ZIP files, Working with ZIP Files
string type, Predefined Type Examples, Strings and Characters-String interpolation, String-UTF-16 and surrogate pairs
accessing characters within, Accessing characters within a string
comparing, String comparisons, Comparing Strings-String order comparison
constructing strings, Constructing strings
enum conversions, String conversions
manipulating, Manipulating strings
null/empty, Null and empty strings
ordinal versus culture comparison, Ordinal versus culture comparison
searching within strings, Searching within strings
spans and, Working with Text
splitting/joining, Splitting and joining strings
string equality comparisons, String equality comparison
string order comparison, String order comparison
String.format and composite format strings, String.Format and composite format strings
StringBuilder class, StringBuilder
text encodings and Unicode, Text Encodings and Unicode-UTF-16 and surrogate pairs
UTF-8 string literals, UTF-8 Strings
writing a declaration to, Writing a declaration to a string
String...
string.Format, String.Format and composite format strings, Composite formatting
string.IsNullOrEmpty, Null and empty strings
StringBuilder class, StringBuilder
StringComparer, StringComparer
StringComparison enum, String equality comparison
StringInfo class, UTF-16 and surrogate pairs
StringReader, StringReader and StringWriter
StringSplitOptions enum, Splitting and joining strings
StringWriter, StringReader and StringWriter
strongly named assemblies, Strong Names and Assembly Signing
struct constraint, Generic Constraints
structs, Structs-Ref Structs
construction semantics, Struct Construction Semantics
mapping to unmanaged memory, Mapping a Struct to Unmanaged Memory-fixed and fixed {...}
mapping to unmanaged method, Marshaling Classes and Structs-Marshaling Classes and Structs
mutability with record structs, Parameter lists
read-only structs/functions, Read-Only Structs and Functions
ref structs, Ref Structs
speeding up equality comparison with, Speeding up equality comparisons with structs
structural comparison, IStructuralEquatable and IStructuralComparable
structural equality, Value Versus Referential Equality
structured parallelism, PFX Concepts
subclass
inheritance with primary constructors, Inheritance with primary constructors
reimplementing an interface in, Reimplementing an Interface in a Subclass-Alternatives to interface reimplementation
subclassing generic types, Subclassing Generic Types
subcultures, Cultures and Subcultures
subqueries, Subqueries-Subqueries and Deferred Execution
deferred execution and, Subqueries and Deferred Execution
select subqueries and object hierarchies, Select subqueries and object hierarchies
subqueries and joins in EF Core, Subqueries and joins in EF Core
subscribers, Events
Substring method, Manipulating strings
Sum operator, Sum and Average
surrogate pairs, UTF-16 and surrogate pairs
switch expressions, Switch expressions
switch statements, The switch statement-The switch statement
symmetric encryption, Symmetric Encryption-Key Management
chaining encryption streams, Chaining Encryption Streams
disposing encryption objects, Disposing Encryption Objects
encrypting in memory, Encrypting in Memory
key management, Key Management
synchronization context scheduler, Task Schedulers
synchronization object, Choosing the Synchronization Object
SynchronizationContext class, Synchronization Contexts
synchronous call graph, Asynchronous Programming and Continuations
synchronous completion, Completing synchronously-Completing synchronously
syntax, C#, Syntax-Comments
comments, Comments
identifiers and keywords, Identifiers and Keywords-Contextual keywords
literals, punctuators, and operators, Literals, Punctuators, and Operators
System...
System.AppContext, AppContext
System.ArgumentException, Common Exception Types
System.ArgumentNullException, Common Exception Types
System.ArgumentOutOfRangeException, Common Exception Types
System.Attribute, Named and Positional Attribute Parameters, Attribute Basics, Defining Your Own Attribute
System.Buffers, Array Pooling
System.Buffers.MemoryPool<T>, Memory<T>
System.Buffers.Text, Working with Text
System.Char, Char
System.Collections.Concurrent, Resurrection, Concurrent Collections
System.Collections.Frozen, Frozen Collections
System.Collections.Generic, Collection Initializers and Collection Expressions
System.Collections.Generic.IEnumerable<T>, Enumeration
System.Collections.Generic.IEnumerator<T>, Enumeration
System.Collections.IEnumerable, Enumeration, Collection Initializers and Collection Expressions
System.Collections.IEnumerator, Enumeration
System.Collections.Immutable, Immutable Collections
System.ComponentModel, Synchronization Contexts, BackgroundWorker
System.Core.dll, The Dynamic Language Runtime
System.Data, When to Dispose
System.Data.IDataRecord, DynamicObject
System.Data.SqlTypes.SqlBoolean, Overloading true and false
System.Delegate, Multicast Delegates
System.Diagnostics, Process-UseShellExecute, Attaching and Breaking, Thread Priority
System.Diagnostics.PerformanceCounter, Performance Counters
System.Drawing, When to Dispose
System.Dynamic, Dynamic Programming
System.Enum, Enums
System.Environment class, Environment
System.EventArgs, Standard Event Pattern
System.EventHandler<>, Standard Event Pattern
System.Exception, The catch Clause, Key Properties of System.Exception
System.GC.Collect, How the GC Works
System.Globalization, UTF-16 and surrogate pairs, Constructing a DateTime
System.Globalization.CultureInfo, Cultures and Subcultures
System.IDisposable, The using statement
System.InvalidOperationException, Common Exception Types
System.IO, When to Dispose, File and Directory Operations
System.IO.Compression, Compression Streams, Working with ZIP Files
System.Linq.Enumerable class, Retrieving and invoking generic methods
System.Management, Compression and encryption attributes
System.MulticastDelegate, Multicast Delegates
System.Net, Awaiting in a UI, Addresses and Ports
System.Net.Mail, Sending Mail with SmtpClient
System.NotImplementedException, Common Exception Types
System.NotSupportedException, Common Exception Types
System.Nullable<T>, Nullable<T> Struct
System.Numerics.BitOperations, BitOperations
System.Object, The object Type, Overriding GetHashCode
System.ObjectDisposedException, Common Exception Types
System.Reflection, The Assembly Class
System.Reflection.Emit, Reflection and Metadata, Dynamic Code Generation, The Reflection.Emit Object Model
System.Runtime, dotnet-counters
System.Runtime.CompilerServices, Dynamic Programming
System.Runtime.InteropServices, Type Equivalence
System.Runtime.Loader, Loading, Resolving, and Isolating Assemblies
System.Security.AccessControl, Running in a Standard User Account
System.Security.Cryptography, Random
System.Security.Cryptography.X509Certificates, Overview, Digital Signing
System.Security.Cryptography.Xml, Overview
System.String, String, IComparable versus Equals
System.Text, Obtaining an Encoding object
System.Text.Json.JsonDocument, JsonDocument
System.Text.Json.Utf8JsonReader, Utf8JsonReader-JsonReaderOptions
System.Text.Json.Utf8JsonWriter, Utf8JsonWriter
System.Text.RegularExpressions, Regular Expressions
System.Threading, Timers
System.Threading.Channels.Channel, Parallel Programming
System.Threading.Tasks, Starting a Task
System.Threading.Timer, Multithreaded Timers
System.Timers, Timers, Multithreaded Timers
System.Timers.Timer, Forcing Garbage Collection
System.Tuple, The System.Tuple classes
System.Type, The GetType Method and typeof Operator, Obtaining a Type
System.Uri class, Property Patterns
System.WeakReference class, Weak References
System.Windows.Forms.Timer, Timers
System.Windows.Threading.DispatcherTimer, Timers
System.Xml.Linq, Removing a sequence of nodes or attributes
System.Xml.Serialization, Named and Positional Attribute Parameters
T
Take operator, Take, TakeLast, Skip, SkipLast
TakeWhile operator, TakeWhile and SkipWhile
TAP (Task-Based Asynchronous Pattern), The Task-Based Asynchronous Pattern
.tar files, Working with Tar Files
Target Framework Moniker (TFM), Runtime Targets and TFMs
target typing, Target-Typed new Expressions, Collection Initializers and Collection Expressions
task combinators, Task Combinators-Custom combinators
custom combinators, Custom combinators
WhenAll, WhenAll
WhenAny, WhenAny
task parallelism, Task Parallelism-Creating your own task factories
canceling tasks, Canceling Tasks
child tasks, Child tasks
continuations, Continuations-Multiple continuations on a single antecedent
creating and starting tasks, Creating and Starting Tasks
defined, PFX Concepts
specifying a state object, Specifying a state object
task schedulers, Task Schedulers
TaskCreationOptions, TaskCreationOptions
TaskFactory, TaskFactory
waiting on multiple tasks, Waiting on Multiple Tasks
task schedulers, Task Schedulers
Task-Based Asynchronous Pattern (TAP), The Task-Based Asynchronous Pattern
Task...
Task class, Tasks
Task.Delay, Task.Delay
Task.Factory, TaskFactory
Task.Factory.StartNew, TaskCompletionSource, Specifying a state object
Task.Run, Starting a Task, Asynchronous Programming and Continuations, Creating and Starting Tasks
Task.WaitAll, Waiting on Multiple Tasks
Task.WaitAny, Waiting on Multiple Tasks
Task.WhenAll, WhenAll
Task.WhenAny, WhenAny
Task<T>, ValueTask<T>
Task<TResult>, Returning Values, Returning Task<TResult>, Continuations and Task<TResult>
TaskCanceledException, Canceling Tasks
TaskCompletionSource, TaskCompletionSource-TaskCompletionSource, Why Language Support Is Important, Writing Asynchronous Functions, Returning Task<TResult>
TaskCreationOptions, TaskCreationOptions
TaskCreationOptions.LongRunning, Long-running tasks, TaskCompletionSource
TaskFactory object, TaskFactory
TaskScheduler.UnobservedTaskException, Exceptions and autonomous tasks
tasks, Tasks-Task.Delay
asynchronous programming and, Asynchronous Programming and Continuations
continuations, Continuations-Continuations
exceptions, Exceptions
exceptions and autonomous tasks, Exceptions and autonomous tasks
long-running, Long-running tasks
returning values, Returning Values
starting a task, Starting a Task-Long-running tasks
TaskCompletionSource, TaskCompletionSource-TaskCompletionSource
Wait method, Wait
TCP (Transmission and Control Protocol)
basics, Using TCP-Concurrency with TCP
concurrency with, Concurrency with TCP
receiving POP3 mail with, Receiving POP3 Mail with TCP-Receiving POP3 Mail with TCP
TcpClient, Using TCP-Concurrency with TCP
TcpListener, Using TCP-Concurrency with TCP
ternary (conditional) operator, Conditional operator (ternary operator)
text
MatchEvaluator delegate, MatchEvaluator Delegate
replacing and splitting with regular expressions, Replacing and Splitting Text
spans and, Working with Text
text adapters, Text Adapters-StringReader and StringWriter
character encodings, Character encodings
StreamReader and StreamWriter, StreamReader and StreamWriter
StringReader and StringWriter, StringReader and StringWriter
text encoding, Text Encodings and Unicode-UTF-16 and surrogate pairs
encoding to byte arrays, Encoding to byte arrays
file and stream I/O, Encoding for file and stream I/O
obtaining an Encoding object, Obtaining an Encoding object
UTF-16 and surrogate pairs, UTF-16 and surrogate pairs
text handling, Char-UTF-16 and surrogate pairs
char type, Char
text encodings and Unicode, Text Encodings and Unicode-UTF-16 and surrogate pairs
ThenBy operator, Overview
ThenByDescending operator, Overview
thin-client applications, Application Layers
this keyword, Overloading constructors
this reference, The this Reference
thread execution barrier, The Barrier Class
thread pool, The Thread Pool
entering, Entering the thread pool
hygiene in, Hygiene in the thread pool
thread safety, Thread Safety
thread-local storage, Thread-Local Storage-AsyncLocal<T>
AsyncLocal<T>, AsyncLocal<T>
GetData and SetData, GetData and SetData
ThreadLocal<T>, ThreadLocal<T>
ThreadStatic attribute, [ThreadStatic]
thread-safe code, Locking and Thread Safety
thread-safe objects, Locking around thread-safe objects
thread-unsafe operations, Functional Purity
Thread...
Thread object, Creating a Thread
Thread.Sleep, Join and Sleep
ThreadLocal<T>, ThreadLocal<T>, Using ThreadLocal<T>
ThreadPool.RegisterWaitForSingleObject, Wait Handles and Continuations
ThreadStart delegate, Creating a Thread
ThreadStatic attribute, [ThreadStatic]
threading, Threading-Hygiene in the thread pool, Advanced Threading-Single-Threaded Timers
advanced topics, Advanced Threading-Single-Threaded Timers
Barrier class, The Barrier Class-The Barrier Class
blocking, Blocking
blocking versus spinning, Blocking versus spinning
creating a thread, Creating a Thread-Creating a Thread
exception handling, Exception Handling
exclusive locking, Exclusive Locking-Mutex
foreground versus background threads, Foreground Versus Background Threads
I/O bound versus compute-bound operations, I/O-bound versus compute-bound
in rich-client applications, Threading in Rich Client Applications-Threading in Rich Client Applications
join and sleep, Join and Sleep
lambda expressions and captured variables, Lambda expressions and captured variables
lazy initialization, Lazy Initialization-LazyInitializer
limitations of, Tasks
local versus shared state, Local Versus Shared State-Local Versus Shared State
locking and thread safety, Locking and Thread Safety, Locking and Thread Safety-Immutable Objects
multiple UI threads, Threading in Rich Client Applications
nonexclusive locking, Nonexclusive Locking-Lock recursion
passing data to a thread, Passing Data to a Thread-Lambda expressions and captured variables
Priority property, Thread Priority
signaling, Signaling
signaling with event wait handles, Signaling with Event Wait Handles-Alternatives to WaitAll and SignalAndWait
synchronization contexts, Synchronization Contexts
synchronization overview, Synchronization Overview
thread pool, The Thread Pool
thread-local storage, Thread-Local Storage-AsyncLocal<T>
timers, Timers-Single-Threaded Timers
threads
defined, Threading
examining threads in a process, Examining Threads in a Process
throw expressions, throw expressions
throw statement, The throw statement
throwing exceptions, Throwing Exceptions-Rethrowing an exception
rethrowing exceptions, Rethrowing an exception
throw expressions, throw expressions
time zones, Dates and Time Zones-Daylight Saving Time and DateTime
DateTime and, DateTime and Time Zones
DateTimeOffset and, DateTimeOffset and Time Zones
Daylight Saving Time and DateTime, Daylight Saving Time and DateTime
TimeZoneInfo, TimeZoneInfo-TimeZoneInfo
time-stamping server, Time stamping
timeouts, Timeouts
timers, Timers-Single-Threaded Timers
memory leaks and, Timers
multithreaded, Multithreaded Timers-Multithreaded Timers
single-threaded, Single-Threaded Timers
TimeSpan, TimeSpan
TimeZone.CurrentTimeZone method, TimeZone
TimeZoneInfo, TimeZoneInfo-TimeZoneInfo
To...
ToArray operator, ToArray, ToList, ToDictionary, ToHashSet, ToLookup
ToDictionary operator, ToArray, ToList, ToDictionary, ToHashSet, ToLookup
ToHashSet operator, ToArray, ToList, ToDictionary, ToHashSet, ToLookup
ToList operator, ToArray, ToList, ToDictionary, ToHashSet, ToLookup
ToLocalTime, DateTime and Time Zones
ToLongDateString method, Formatting and parsing datetimes
ToLookup operator, ToArray, ToList, ToDictionary, ToHashSet, ToLookup
ToLower, Char, Manipulating strings
ToShortDateString method, Formatting and parsing datetimes
ToString method, The ToString Method, StringBuilder, Formatting and parsing datetimes, ToString and Parse, Saving and Serializing
ToUniversalTime, DateTime and Time Zones, Daylight Saving Time and DateTime
ToUpper, Char, Manipulating strings
top-level statements
elements of, Defining a Main method
local methods and, Local methods and top-level statements
Trace class (see Debug and Trace classes)
TraceFilter, TraceListener
TraceListener, TraceListener
traces, dotnet-trace
Transmission and Control Protcol (see TCP)
transport layer, Network Architecture
try statements and exceptions, try Statements and Exceptions-Alternatives to Exceptions
alternatives to exceptions, Alternatives to Exceptions
catch clause, The catch Clause-Exception filters
common exception types, Common Exception Types
finally block, The using statement
key properties of System.Exception, Key Properties of System.Exception
throwing exceptions, Throwing Exceptions-Rethrowing an exception
try/catch/finally blocks, Iterators and try/catch/finally blocks
TryXXX method pattern, The TryXXX Method Pattern
using declarations, using declarations
using statement, The using statement
TryCopyTo method, CopyTo and TryCopyTo
TryEnter method, TryEnter
TryParse, TimeSpan, ToString and Parse
TryXXX method pattern, The TryXXX Method Pattern
tuple literal, Tuples
tuple patterns, Tuple and Positional Patterns
tuple types, Tuples
TupleElementNamesAttribute, Type erasure
tuples, Tuples-The System.Tuple classes
aliasing (C# 12), Aliasing Tuples (C# 12)
deconstructing, Deconstructing Tuples
equality comparison, Equality Comparison
naming tuple elements, Naming Tuple Elements
System.Tuple classes, The System.Tuple classes
type erasure, Type erasure
ValueTuple.Create, Naming Tuple Elements
type arguments, Generic Types
type checking, Static and Runtime Type Checking
type converters, Type Converters
type equivalence, Type Equivalence
type library importer, Calling a COM Component from C#
type marshaling, Marshaling Common Types-Marshaling Common Types
calling conventions, Calling Conventions
in and out marshaling, In and Out Marshaling
marshaling classes and structs, Marshaling Classes and Structs-Marshaling Classes and Structs
marshaling common types, Marshaling Common Types-Calling Conventions
type members, emitting, Emitting Type Members-Attaching Attributes
type parameters
covariance, Declaring a covariant type parameter
declaring, Declaring Type Parameters
generic types and, Generic Types
type safety, Type Safety
enums and, Type-Safety Issues
type system, C#
access modifiers, Access Modifiers-Restrictions on Access Modifiers
anonymous types, Anonymous Types
basics, Type Basics-Predefined Type Taxonomy
Boolean type and operators, Boolean Type and Operators-Conditional operator (ternary operator)
C# members versus CLR members, C# Members Versus CLR Members
converting types, Types and Conversions
creating types, Creating Types in C#-C# Generics Versus C++ Templates
custom type examples, Custom Types-Defining a Main method
dynamically invoking a member, Dynamically Invoking a Member
emitting assemblies and types, Emitting Assemblies and Types-The Reflection.Emit Object Model
enums, Enums-Type-Safety Issues
extension methods, Extension Methods-Demoting an extension method
generics, Generics-C# Generics Versus C++ Templates
inheritance (see inheritance)
instantiating a type, Instantiating Types-Instantiating Types
interfaces, Interfaces-Static virtual/abstract interface members
nested types, Nested Types-Nested Types
numeric types, Numeric Types-Real Number Rounding Errors
object type, The object Type-Object Member Listing
predefined type examples, Predefined Type Examples
strings and characters, Strings and Characters-String interpolation
structs, Structs-Ref Structs
value types versus reference types, Value Types Versus Reference Types-Storage overhead
type unification, The object Type, Enums
Type...
TypeAttributes, Emitting Assemblies and Types
TypeBuilder, Emitting Assemblies and Types-The Reflection.Emit Object Model, Overriding methods
TypeIdentifierAttribute, Type Equivalence
TypeInfo class, TypeInfo, Reflecting and Invoking Members
typeof operator, The GetType Method and typeof Operator, typeof and Unbound Generic Types
types
aliasing any type (C# 12), Alias any type (C# 12)
aliasing within namespaces, Aliasing Types and Namespaces
base types and interfaces, Base Types and Interfaces
partial types/methods, Partial Types and Methods
reflecting and activating, Reflecting and Activating Types-Generic Types
reflecting and invoking members of, Reflecting and Invoking Members-Calling Static Virtual/Abstract Interface Members
U
UAC (User Account Control), OS Security
UI (user interface)
awaiting in, Awaiting in a UI-Awaiting in a UI
multiple UI threads, Threading in Rich Client Applications
unbound generic type, typeof and Unbound Generic Types
unboxing, Boxing and Unboxing
is operator and, The is operator
nullable values, Boxing and Unboxing Nullable Values
#undef directive, Conditional Compilation
Unicode, Text Encodings and Unicode-UTF-16 and surrogate pairs
UTF-16 and surrogate pairs, UTF-16 and surrogate pairs
XmlWriter and, XML Declarations
UnicodeCategory enum, Char
union, Simulating a C Union
Union operator, Concat, Union, UnionBy
Unity, Niche Runtimes
Universal Windows Platform (UWP) (see UWP)
Unix
file security, Unix file security
gzip file compression, Unix gzip File Compression
Unix gzip file compression, Unix gzip File Compression
Unix, OS security, OS Security
unmanaged code
callbacks from, Callbacks from Unmanaged Code
callbacks with delegates, Callbacks with Delegates
callbacks with function pointers (C# 9), Callbacks with Function Pointers
unmanaged constraint, Generic Constraints
unmanaged heap, Mapping a Struct to Unmanaged Memory
unmanaged memory, Working with Stack-Allocated and Unmanaged Memory, Mapping a Struct to Unmanaged Memory-fixed and fixed {...}
[UnmanagedCallersOnly] attribute, UnmanagedCallersOnly
UnmanagedType, Marshaling Common Types
unnamed methods, Asynchronous Lambda Expressions
unsafe code, Unsafe Code and Pointers-[SkipLocalsInit], Unsafe Code
unseeded aggregations, Unseeded aggregations
upcasting, Upcasting
upgradeable locks, Upgradeable locks
UploadValues method, Uploading Form Data
Uri class, URIs-URIs
URIs, URIs-URIs
User Account Control (UAC), OS Security
user interface (UI)
awaiting in, Awaiting in a UI-Awaiting in a UI
multiple UI threads, Threading in Rich Client Applications
UseShellExecute, UseShellExecute
ushort (numeric type), Numeric Types
using declarations, using declarations
using directive, The using Directive, Nested using directives, Aliasing Tuples (C# 12)
using statement, Miscellaneous Statements
using static directive, using static
UTC (Coordinated Universal Time), DateTime and DateTimeOffset, DateTimeOffset and Time Zones
UTF-8 string literals, UTF-8 Strings
Utf8JsonReader, Utf8JsonReader-JsonReaderOptions
Utf8JsonWriter, Utf8JsonWriter
utility classes, Console-AppContext
AppContext, AppContext
Console, Console
Environment, Environment
Process, Process-UseShellExecute
UWP (Universal Windows Platform), UWP and WinUI 3
about, Niche Runtimes
V
value equality, Value Versus Referential Equality
value types, Value Types Versus Reference Types
ValueTask<T>, ValueTask<T>
ValueTuple.Create, Naming Tuple Elements, ValueTuple.Create
ValueTuple<string,int>, Type erasure
var keyword, var—Implicitly Typed Local Variables
var pattern, var Pattern
var type, dynamic type versus, var Versus dynamic
variables, Type Basics, Variables and Parameters-Default Values
(see also parameters)
default values, Default Values
definite assignment and, Definite Assignment
heap, The Stack and the Heap
purpose of, Type Basics
ref locals, Ref Locals
ref returns, Ref Returns
stack and, The Stack and the Heap
var keyword, var—Implicitly Typed Local Variables
verbatim string literals, String Type
vertical bar (|)
bitwise OR operator, Bitwise operators, Flags Enums
bool? with | operator, bool? with & and | Operators
in regular expressions, Regular Expression Basics
view accessors, Working with View Accessors
virtual function members, Virtual Function Members
virtualization, Administrative Elevation and Virtualization
Visitor pattern, Simplifying the Visitor Pattern-Variations
void expressions, Void Expressions
void pointer (void*), void*
volume information, querying, Querying Volume Information
W
wait handles (see event wait handles)
Wait method, Wait
WaitAll method, WaitAny, WaitAll, and SignalAndWait
WaitAny method, WaitAny, WaitAll, and SignalAndWait
#warning preprocessor directive, Preprocessor Directives
weak references
caching and, Weak References and Caching
events and, Weak References and Events-Weak References and Events
GC and, Weak References-Weak References and Events
Where clause, Filtering-Distinct and DistinctBy
Enumerable.Where implementation, Enumerable.Where implementation
indexed filtering, Indexed filtering
WHERE x IN (…,…,…), WHERE x IN (…, …, …) in EF Core
while loops, while and do-while loops
wildcards (character sets), Character Sets
Windows
application manifest, The Application Manifest (Windows)
file security, Windows file security
memory-mapped files and shared memory, Memory-Mapped Files and Shared Memory (Windows)
OS security, OS Security
Windows Data Protection API (DPAPI), Windows Data Protection
Windows Desktop application layer, Windows Desktop and WinUI 3, Windows Desktop
Windows event logs, Windows Event Logs-Monitoring the Event Log
monitoring, Monitoring the Event Log
reading, Reading the Event Log
writing to, Writing to the Event Log
Windows Forms, Windows Forms
Windows Management Instrumentation (WMI) API, Compression and encryption attributes
Windows Presentation Foundation (WPF), WPF
Windows Runtime (WinRT)
asynchronous methods in, Asynchronous Methods in WinRT
WinUI 3, Windows Desktop and WinUI 3
WithDegreeOfParallelism, Setting the Degree of Parallelism
WithMergeOptions, Parallel Execution Ballistics
WMI (Windows Management Instrumentation) API, Compression and encryption attributes
word boundary assertions, Word Boundaries
WPF (Windows Presentation Foundation), WPF
write locks, Reader/Writer Locks-Lock recursion
X
x++ (incrementing), Locking and Thread Safety
X-DOM (see XML DOM)
XAML (Extensible Application Markup Language) files, Type Converters, Creating a pack URI resource in Visual Studio
XAttribute, X-DOM Overview
XContainer, X-DOM Overview
XDeclaration object, XDocument
XDocument, X-DOM Overview, XDocument-Writing a declaration to a string
XElement, X-DOM Overview-Saving and Serializing
using XmlReader with, Using XmlReader with XElement
using XmlWriter with, Using XmlWriter with XElement
XML declarations, XML Declarations
XML documentation, XML Documentation-Type or Member Cross-References
standard tags, Standard XML Documentation Tags-Standard XML Documentation Tags
type or member cross-references, Type or Member Cross-References
user-defined tags, User-Defined Tags
XML DOM (X-DOM), The LINQ to XML DOM
attribute navigation, Attribute Navigation
automatic deep cloning, Automatic Deep Cloning
automatic XText concatenation, Automatic XText Concatenation
child node navigation, Child Node Navigation
content specification, Specifying Content
default namespaces, The X-DOM and Default Namespaces
functional construction, Functional Construction
getting values, Getting Values
instantiating, Instantiating an X-DOM-Automatic Deep Cloning
loading and parsing, Loading and Parsing
mixing XmlReader/XmlWriter with, Mixing XmlReader/XmlWriter with an X-DOM
namespace specification, Specifying Namespaces in the X-DOM
navigating and querying, Navigating and Querying-Attribute Navigation
overview, X-DOM Overview-Saving and Serializing
parent navigation, Parent Navigation
peer node navigation, Peer Node Navigation
prefixes, Prefixes
projecting into, Projecting into an X-DOM-Streaming a Projection
removing a sequence of nodes or attributes, Removing a sequence of nodes or attributes
retrieving a single element, Retrieving a single element
retrieving descendants, Retrieving descendants
retrieving elements, Retrieving elements
saving and serializing, Saving and Serializing
setting values, Setting Values
simple value updates, Simple Value Updates
updating, Updating an X-DOM-Removing a sequence of nodes or attributes
updating child nodes and attributes, Updating Child Nodes and Attributes
updating through the parent, Updating Through the Parent
values and mixed content nodes, Values and Mixed Content Nodes
working with values, Working with Values-Automatic XText Concatenation
XmlConvert, XmlConvert
XmlReader, XmlReader-Namespaces and Prefixes
mixing with an X-DOM, Mixing XmlReader/XmlWriter with an X-DOM
namespaces and prefixes, Namespaces and Prefixes
patterns for using, Working with Hierarchical Data-Using XmlWriter with XElement
reading attributes, Reading Attributes
reading elements, Reading Elements-Other ReadXXX methods
reading nodes, Reading Nodes
using with XElement, Using XmlReader with XElement
working with hierarchical data, Working with Hierarchical Data-Working with Hierarchical Data
XmlWriter, XmlWriter
mixing with an X-DOM, Mixing XmlReader/XmlWriter with an X-DOM
patterns for using, Working with Hierarchical Data-Using XmlWriter with XElement
using with XElement, Using XmlWriter with XElement
working with hierarchical data, Working with Hierarchical Data-Working with Hierarchical Data
writing a declaration to a string, Writing a declaration to a string
XNode, X-DOM Overview
XObject, X-DOM Overview, Annotations
XStreamingElement, Streaming a Projection
XText, Automatic XText Concatenation
Y
yield break statement, yield break
Z
zero-width assertions, Zero-Width Assertions-Word Boundaries
anchors, Anchors
defined, Zero-Width Assertions
lookahead and lookbehind, Lookahead and Lookbehind
word boundaries, Word Boundaries
ZIP files, Working with ZIP Files
Zip operator, The Zip Operator
ZipArchive class, Working with ZIP Files
ZipFile class, Working with ZIP Files

Copy
copy

Highlight
highlight

Add Note
note

Get Link
link
table of contents
search
Settings
queue

