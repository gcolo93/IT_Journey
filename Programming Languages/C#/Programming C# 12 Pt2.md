Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


13. Reflection
14. Attributes
15. Files and Streams
24h 20m remaining
Chapter 14. Attributes
In .NET, you can annotate components, types, and their members with attributes. An attribute’s purpose is to control or modify the behavior of a framework, a tool, the compiler, or the CLR. For example, in Chapter 1, I showed a class annotated with the [TestClass] attribute. This told a unit testing framework that the annotated class contains some tests to be run as part of a test suite.

Attributes are passive containers of information that do nothing on their own. To draw an analogy with the physical world, if you print out a shipping label containing an address and tracking information and attach it to a package, that label will not in itself cause the package to make its way to a destination. Such a label is useful only once the package is in the hands of a shipping company. When the company picks up your parcel, it’ll expect to find the label and will use it to work out how to route your package. So the label is important, but ultimately, its only job is to provide information that some system requires. .NET attributes work the same way—they have an effect only if something goes looking for them. Some attributes are handled by the CLR or the compiler, but these are in the minority. The majority of attributes are consumed by frameworks, libraries, tools (such as a unit test runner), or your own code.

Applying Attributes
To avoid having to introduce an extra set of concepts into the type system, .NET models attributes as instances of .NET types. To be used as an attribute, a type must derive from the System.Attribute class, but it can otherwise be entirely ordinary. To apply an attribute, you put the type’s name in square brackets, and this usually goes directly before the attribute’s target. (Since C# mostly ignores whitespace, attributes don’t have to be on a separate line, but that is the convention when the target is a type or a member.) Example 14-1 shows some attributes from Microsoft’s test framework. I’ve applied one to the class to indicate that this contains tests I’d like to run, and I’ve also applied attributes to individual methods, telling the test framework which ones represent tests and which contain initialization code to be run before each test.

Example 14-1. Attributes in a unit test class

using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace ImageManagement.Tests;

[TestClass]
public class WhenPropertiesRetrieved
{
    private ImageMetadataReader? _reader;

    [TestInitialize]
    public void Initialize()
    {
        _reader = new ImageMetadataReader(TestFiles.GetImage());
    }

    [TestMethod]
    public void ReportsCameraMaker()
    {
        Assert.AreEqual(_reader!.CameraManufacturer, "Fabrikam");
    }

    [TestMethod]
    public void ReportsCameraModel()
    {
        Assert.AreEqual(_reader!.CameraModel, "Fabrikam F450D");
    }
}
If you look at the documentation for most attributes, you’ll find that their real name ends with Attribute. If there’s no class with the name you specify in the brackets, the C# compiler tries appending Attribute, so the [TestClass] attribute in Example 14-1 refers to the TestClassAttribute class. If you really want to, you can spell the class name out in full—for example, [TestClassAttribute]—but it’s more common to use the shorter version.

If you want to apply multiple attributes, you have two options. You can either provide multiple sets of brackets or put multiple attributes inside a single pair of brackets, separated by commas.

Some attribute types can take constructor arguments. For example, Microsoft’s test framework includes a TestCategoryAttribute. When running tests, you can choose to execute only those in a certain category. This attribute requires you to pass the category name as a constructor argument, because there would be no point in applying this attribute without specifying the name. As Example 14-2 shows, the syntax for specifying an attribute’s constructor arguments is unsurprising.

Example 14-2. Attribute with constructor argument

[TestCategory("Property Handling")]
[TestMethod]
public void ReportsCameraMaker()
{
    ...
You can also specify property or field values. Some attributes have features that can be controlled only through properties or fields, and not constructor arguments. (If an attribute has lots of optional settings, it’s usually easier to present these as properties or fields, instead of defining a constructor overload for every conceivable combination of settings.) The syntax for this is to write one or more PropertyOrFieldName=Value entries after the constructor arguments (or instead of them, if there are no constructor arguments). Example 14-3 shows another attribute used in unit testing, ExpectedExceptionAttribute, which allows you to specify that when your test runs, you expect it to throw a particular exception. The exception type is mandatory, so we pass that as a constructor argument, but this attribute also allows you to state whether the test runner should accept exceptions of a type derived from the one specified. (By default, it will accept only an exact match.) This is controlled with the AllowDerivedTypes property.

Example 14-3. Specifying optional attribute settings with properties

[ExpectedException(typeof(ArgumentException), AllowDerivedTypes = true)]
[TestMethod]
public void ThrowsWhenNameMalformed()
{
    ...
Applying an attribute will not cause it to be constructed. All you are doing when you apply an attribute is providing instructions on how the attribute should be created and initialized if something should ask to see it. (There is a common misconception that method attributes are instantiated when the method runs. Not so.) When the compiler builds the metadata for an assembly, it includes information about which attributes have been applied to which items, including a list of constructor arguments and property values, and the CLR will dig that information out and use it only if something asks for it. For example, when you tell Visual Studio to run your unit tests, it will load your test assembly, and then for each public type, it asks the CLR for any test-related attributes. That’s the point at which the attributes get constructed. If you were simply to load the assembly by, say, adding a reference to it from another project and then using some of the types it contains, the attributes would never come into existence—they would remain as nothing more than a set of building instructions frozen into your assembly’s metadata. In some cases they might not even make it that far. If you’re using Native AOT in conjunction with the JSON serialization mechanisms shown in Chapter 15, the relevant attributes are processed during compilation and get trimmed out of the final output.

Attribute Targets
Attributes can be applied to numerous different kinds of targets. You can put attributes on any of the features of the type system represented in the reflection API that I showed in Chapter 13. Specifically, you can apply attributes to assemblies, modules, types, methods, method parameters, constructors, fields, properties, events, and generic type parameters. In addition, you can supply attributes that target a method’s return value.

For most of these, you denote the target simply by putting the attribute in front of it. But that’s not an option for assemblies or modules, because there is no single feature that represents those in your source code—everything in your project goes into the assembly it produces, and modules are likewise an aggregate. So for these, we have to state the target explicitly at the start of the attribute. The specific assembly-level attribute shown in Example 14-4 will often be found in a GlobalSuppressions.cs file. Visual Studio sometimes makes suggestions for modifying your code, and if you want to suppress these, one option is to use assembly-level attributes.

Example 14-4. Assembly-level attributes
[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage(
    "Style",
    "IDE0060:Remove unused parameter",
    Justification = "This is just some example code from a book",
    Scope = "member",
    Target = "~M:Idg.Examples.SomeMethod")]
You can put assembly-level attributes in any file. The sole restriction is that they must appear before any namespace or type definitions. The only things that should come before assembly-level attributes are whichever using directives you need, comments, and whitespace (all of which are optional).

Module-level attributes follow the same pattern, although they are much less common, not least because multimodule assemblies are pretty rare and are not supported in the latest versions of .NET—they only work on .NET Framework. Example 14-5 shows how to configure the debuggability of a particular module, should you want one module in a multimodule assembly to be easily debuggable but the rest to be JIT-compiled with full optimizations. (This is a contrived scenario so that I can show the syntax. In practice, you’re unlikely ever to want to do this.) I’ll talk about the DebuggableAttribute later, in “JIT compilation”.

Example 14-5. Module-level attribute
using System.Diagnostics;

[module: Debuggable(DebuggableAttribute.DebuggingModes.DisableOptimizations)]
Another kind of target that needs qualification is a compiler-generated field. You get these with properties in which you do not supply code for the getter or setter, and also in event members without explicit add and remove implementations. The attributes in Example 14-6 apply to the fields that hold the property’s value and the delegate for the event; without the field: qualifiers, attributes in those positions would apply to the property or event itself.

Example 14-6. Attribute for compiler-generated property and event fields
[field: NonSerialized]
public int DynamicId { get; set; }

[field: NonSerialized]
public event EventHandler? Frazzled;
Methods’ return values can be annotated, and this also requires qualification, because return value attributes go in front of the method, the same place as attributes that apply to the method itself. (Attributes for parameters do not need qualification, because these appear inside the parentheses with the parameters.) Example 14-7 shows a method with attributes applied to both the method and the return type. (The attributes in this example are part of the interop services that enable .NET code to call external code, such as OS APIs. This example imports a function from a Win32 DLL, enabling you to use it from C#. There are several different representations for Boolean values in unmanaged code, so I’ve annotated the return type here with a MarshalAsAttribute to say which particular one the CLR should expect.)

Example 14-7. Method and return value attributes
[LibraryImport("User32.dll")]
[return: MarshalAs(UnmanagedType.Bool)]
internal static partial bool IsWindowVisible(IntPtr hWnd);
C# 11.0 added a new feature for attributes that target either return values or arguments. Sometimes, attributes describe relationships between multiple parameters, or a relationship between a method’s return value and a parameter. An attribute has just one target, so we refer to related arguments by name. Example 14-8 shows an example from the .NET runtime library: the string.Create method. (This method enables you to change localization and other format settings when using an interpolated string. You can write string.Create(CultureInfo.InvariantCulture, $"Value: {v}"), for example.) It uses the InterpolatedStringHandlerArgumentAttribute to tell the compiler that it wants to provide custom string interpolation handling, and that this will be managed by the DefaultInterpolatedStringHandler type. The compiler needs to know whether any of the method’s other arguments are involved with the string interpolation, and this method has indicated that the provider argument needs to be passed as a constructor argument to DefaultInterpolatedStringHandler.

Example 14-8. Referring to a method argument by name in an attribute before C# 11.0
public static string Create(
    IFormatProvider? provider,
    [InterpolatedStringHandlerArgument("provider")]
    ref DefaultInterpolatedStringHandler handler)
Referring to arguments by name in a string was always slightly unsatisfactory. It’s easy to mistype the name, and it is hard for refactoring tools to process these correctly—if you rename the argument, that string also needs to change. This is exactly the scenario that nameof is designed for, but you couldn’t use it here because parameters were in scope only inside the method’s body. C# 11.0 relaxed the scoping rules very slightly: nameof is now allowed to refer to argument names in attributes applied to the method’s arguments or return value, so if you look at the source for string.Create you’ll find it now looks like Example 14-9.

Example 14-9. Referring to a method argument by name in an attribute using nameof
public static string Create(
    IFormatProvider? provider,
    [InterpolatedStringHandlerArgument(nameof(provider))]
    ref DefaultInterpolatedStringHandler handler)
How are we to apply method attributes in cases where we don’t write the method declaration explicitly? As you saw in Chapter 9, the lambda syntax lets us write an expression whose value is a delegate. The compiler generates a normal method to hold the code (typically in a hidden class), and we might want to pass that method to a framework that uses attributes to control its functionality, such as the ASP.NET Core web framework. Example 14-10 shows how we can specify these attributes when using a lambda.

Example 14-10. Lambda with attributes
app.MapGet(
    "/items/{id}",
    [Authorize] ([FromRoute] int id) => $"Item {id} requested");
The MapGet method here tells the ASP.NET Core framework how our application should behave when it receives GET requests on URLs matching a particular pattern. The first argument specifies the pattern, and the second is a delegate that defines the behavior. I’ve used the lambda syntax here, and I’ve applied a couple of attributes.

The first attribute is [Authorize]. This appears before the parameter list, so its target is the whole method. (You can also use a return: attribute in this position.) This causes ASP.NET Core to block unauthenticated requests that match this URL pattern. The [FromRoute] attribute is inside the parameter list’s parentheses, so it applies to the id parameter, and it tells ASP.NET Core that we want that particular parameter’s value to be taken from the expression of the same name in the URL pattern. So if a request came in for https://myserver/items/42, ASP.NET Core would first check that the request meets the application’s configured requirements for authentication and authorization, and if so, it would then invoke my lambda passing 42 as the id argument.

NOTE
Example 9-23 in Chapter 9 showed that you can omit details in certain cases. The parentheses around the parameter list are normally optional for 1-argument lambdas. However, the parentheses must be present if you apply attributes to a lambda. To see why, imagine Example 14-10 without parentheses around the parameter list: it would be unclear whether the attributes were meant to apply to the method or the parameter.

Compiler-Handled Attributes
The C# compiler recognizes certain attribute types and handles them in special ways. For example, assembly names and versions are set via attributes and also some related information about your assembly. As Chapter 12 described, the build process generates a hidden source file containing these for you. If you’re curious, it usually ends up in the obj\Debug or obj\Release folder of your project, and it will be named something like YourProject.AssemblyInfo.cs. Example 14-11 shows a typical example.

Example 14-11. A typical generated file with assembly-level attributes
//------------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by a tool.
//     Runtime Version:4.0.30319.42000
//
//     Changes to this file may cause incorrect behavior and will be lost if
//     the code is regenerated.
// </auto-generated>
//------------------------------------------------------------------------------

using System;
using System.Reflection;

[assembly: System.Reflection.AssemblyCompanyAttribute("MyCompany")]
[assembly: System.Reflection.AssemblyConfigurationAttribute("Debug")]
[assembly: System.Reflection.AssemblyFileVersionAttribute("1.0.0.0")]
[assembly: System.Reflection.AssemblyInformationalVersionAttribute("1.0.0")]
[assembly: System.Reflection.AssemblyProductAttribute("MyApp")]
[assembly: System.Reflection.AssemblyTitleAttribute("MyApp")]
[assembly: System.Reflection.AssemblyVersionAttribute("1.0.0.0")]

// Generated by the MSBuild WriteCodeFragment class.
Old versions of the .NET Framework SDK did not generate this file at build time, so if you work on older projects, you will often find these attributes in a file called AssemblyInfo.cs. (By default Visual Studio hid this inside the project’s Properties node in Solution Explorer, but it was still just an ordinary source file.) The advantage of the file generation used in modern projects is that names are less likely to drift out of sync. For example, by default the assembly Product and Title will be the same as the project filename. If you rename the project file, the generated YourRenamedProject.AssemblyInfo.cs will change to match (unless you added <Product> and <AssemblyTitle> properties to your project file, in which case it will use those), whereas with the old AssemblyInfo.cs approach you could accidentally end up with mismatched names. Similarly, if you build a NuGet package from your project, certain properties end up in both the NuGet package and the compiled assembly. When these are all generated from information in the project file, it’s easier to keep things consistent.

Even though you only control these attributes indirectly, it’s useful to understand them since they affect the compiler output.

Names and versions
As you saw in Chapter 12, assemblies have a compound name. The simple name, which is typically the same as the filename but without the .exe or .dll extension, is configured as part of the project settings. The name also includes a version number, and this is controlled with an attribute, as Example 14-12 shows.

Example 14-12. Version attributes
[assembly: AssemblyVersion("1.0.0.0")]
[assembly: AssemblyFileVersion("1.0.0.0")]
As you may recall from Chapter 12, the first of these sets the version part of the assembly’s name. The second has nothing to do with .NET—the compiler uses this to generate a Win32-style version resource. This is the version number end users will see if they select your assembly in Windows Explorer and open the Properties window.

The culture is also part of the assembly name. This will often be set automatically if you’re using the satellite resource assembly mechanisms described in Chapter 12. You can set it explicitly with the AssemblyCulture attribute, but for nonresource assemblies, the culture should usually not be set. (The only culture-related assembly-level attribute you will normally specify explicitly is the Neu⁠tral⁠Res⁠our⁠ces⁠Lan⁠gua⁠ge​Att⁠rib⁠ute, which I showed in Chapter 12.)

Strongly named assemblies have an additional component in their name: the public key token. The easiest way to set up a strong name in Visual Studio is with the “Strong naming” section of your project’s properties page (which is inside the Build section). If you’re using VS Code or some other editor, you can just add two properties to your .csproj file: SignAssembly set to True, and AssemblyOriginatorKeyFile with the path to your key file. However, you can also manage strong naming from the source code, because the compiler recognizes some special attributes for this. AssemblyKeyFileAttribute takes the name of a file that contains a key. Alternatively, you can install a key in the computer’s key store (which is part of the Windows cryptography system). If you want to do that, you can use the AssemblyKeyNameAttribute instead. The presence of either of these attributes causes the compiler to embed the public key in the assembly and include a hash of that key as the public key token of the strong name. If the key file includes the private key, the compiler will sign your assembly too. If it does not, it will fail to compile, unless you also enable either delay signing or public signing. You can enable delay signing by applying the Ass⁠emb⁠ly​Del⁠ayS⁠ign⁠Att⁠rib⁠ute with a constructor argument of true. Alternatively, you can add either <DelaySign>true</DelaySign> or <PublicSign>true</PublicSign> to your .csproj file.

WARNING
Although the key-related attributes trigger special handling from the compiler, it still embeds them in the metadata as normal attributes. So, if you use the AssemblyKeyFileAttribute, the path to your key file will be visible in the final compiled output. This is not necessarily a problem, but you might prefer not to advertise these sorts of details, so it may be better to use the project-level configuration for strong names than the attribute-based approach.

Description and related resources
The version resource produced by the AssemblyFileVersion attribute is not the only information that the C# compiler can embed in Win32-style resources. There are several other attributes providing copyright information and other descriptive text. Example 14-13 shows a typical selection.

Example 14-13. Typical assembly description attributes
[assembly: AssemblyTitle("ExamplePlugin")]
[assembly: AssemblyDescription("An example plug-in DLL")]
[assembly: AssemblyConfiguration("Retail")]
[assembly: AssemblyCompany("Endjin Ltd.")]
[assembly: AssemblyProduct("ExamplePlugin")]
[assembly: AssemblyCopyright("Copyright © 2024 Endjin Ltd.")]
[assembly: AssemblyTrademark("")]
As with the file version, these are all visible in the Details tab of the Properties window that Windows Explorer can show for the file. And with all of these attributes, you can cause them to be generated by editing the project file.

Caller information attributes
There are some compiler-handled attributes designed for scenarios where your methods need information about the context from which they were invoked. This is useful for certain diagnostic logging or error handling scenarios, and it is also helpful when implementing a particular interface commonly used in UI code.

Example 14-14 illustrates how you can use these attributes in logging code. If you annotate method parameters with any of these three attributes, the compiler provides some special handling when callers omit the arguments. We can ask for the name of the member (method or property) that called the attributed method, the filename containing the code that called the method, or the line number from which the call was made. Example 14-14 asks for all three, but you can be more selective.

NOTE
These attributes are allowed only for optional parameters. Optional arguments are required to specify a default value, but C# will always substitute a different value when these attributes are present, so the default you specify will not be used if you invoke the method from C# (or F# or Visual Basic, which also support these attributes). Nonetheless, you must provide a default because without one, the parameter is not optional, so we normally use empty strings, null, or the number 0.

Example 14-14. Applying caller info attributes to method parameters
public static void Log(
    string message,
    [CallerMemberName] string callingMethod = "",
    [CallerFilePath] string callingFile = "",
    [CallerLineNumber] int callingLineNumber = 0)
{
    Console.WriteLine("Message {0}, called from {1} in file '{2}', line {3}",
        message, callingMethod, callingFile, callingLineNumber);
}
If you supply all arguments when invoking this method, nothing unusual happens. But if you omit any of the optional arguments, C# will generate code that provides information about the site from which the method was invoked. The default values for the three optional arguments in Example 14-14 will be the name of the method or property that called this Log method, the full path of the source code containing the code that made the call, and the line number from which Log was called.

The CallerMemberName attribute has a superficial resemblance to the nameof operator, which we saw in Chapter 8. Both cause the compiler to create a string containing the name of some feature of the code, but they work quite differently. With nameof, you always know exactly what string you’ll get, because it’s determined by the expression you supply. (E.g., if we were to write nameof(message) inside Log in Example 14-14, it would always evaluate to "message".) But CallerMemberName changes the way the compiler invokes the method to which they apply—cal⁠lin⁠g​Met⁠hod has that attribute, and its value is not fixed. It will depend on where this method is called from.

NOTE
You can discover the calling method another way: the StackTrace and StackFrame classes in the System.Diagnostics namespace can report information about methods above you in the call stack. However, these have a considerably higher runtime cost—the caller information attributes calculate the values at compile time, making the runtime overhead very low. (Likewise with nameof.) Also, StackFrame can determine the filename and line number only if debug symbols are available.

Although diagnostic logging is an obvious application for this, I also mentioned a certain scenario that most .NET UI developers will be familiar with. The runtime libraries define an interface called INotifyPropertyChanged. As Example 14-15 shows, this is a very simple interface with just one member, an event called PropertyChanged.

Example 14-15. INotifyPropertyChanged
public interface INotifyPropertyChanged
{
    event PropertyChangedEventHandler? PropertyChanged;
}
Types that implement this interface raise the PropertyChanged event every time one of their properties changes. The PropertyChangedEventArgument provides a string containing the name of the property that just changed. These change notifications are useful in UIs, because they enable an object to be used with databinding technologies (such as those provided by .NET’s WPF UI framework) that can automatically update the UI any time a property changes. Databinding can help you to achieve a clean separation between the code that deals directly with UI types and code that contains the logic that decides how the application should respond to user input.

Implementing INotifyPropertyChanged can be both tedious and error-prone. Because the PropertyChanged event indicates which property changed as a string, it is very easy to mistype the property name, or to accidentally use the wrong name if you copy and paste the implementation from one property to another. Also, if you rename a property, it’s easy to forget to change the text used for the event, meaning that code that was previously correct will now provide the wrong name when raising the PropertyChanged event. The nameof operator helps avoid mistyping, and helps with renames, but can’t always detect cut-and-paste errors. (It won’t notice if you fail to update the name when pasting code between properties of the same class, for example.)

Caller information attributes can help make implementing this interface much less error-prone. Example 14-16 shows a base class that implements INotifyPropertyChanged, supplying a helper for raising change notifications in a way that exploits one of these attributes. (It uses the null-conditional ?. operator to ensure that it only invokes the event’s delegate if it is non-null. By the way, when you use the operator this way, C# generates code that only evaluates the delegate’s Invoke method’s arguments if it is non-null. So not only does it skip the call to Invoke when the delegate is null, it will also avoid constructing the Pro⁠per⁠ty​Cha⁠nge⁠dEv⁠ent⁠Args that would have been passed as an argument.) This code also detects whether the value really has changed, only raising the event when that’s the case, and its return value indicates whether it changed, in case callers might find that useful.

Example 14-16. A reusable INotifyPropertyChanged implementation
public class NotifyPropertyChanged : INotifyPropertyChanged
{
    public event PropertyChangedEventHandler? PropertyChanged;

    protected bool SetProperty<T>(
        ref T field,
        T value,
        [CallerMemberName] string propertyName = "")
    {
        if (Equals(field, value))
        {
            return false;
        }

        field = value;

        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        return true;
    }
}
The presence of the [CallerMemberName] attribute means that a class deriving from this type does not need to specify the property name if it calls SetProperty from inside a property setter, as Example 14-17 shows.

Example 14-17. Raising a property changed event
public class MyViewModel : NotifyPropertyChanged
{
    private string? _name;

    public string? Name
    {
        get => _name;
        set => SetProperty(ref _name, value);
    }
}
Even with the new attribute, implementing INotifyPropertyChanged is clearly more effort than an automatic property, where you just write { get; set; } and let the compiler do the work for you. But it’s only a little more complex than an explicit implementation of a trivial field-backed property, and it’s simpler than would be possible without [CallerMemberName], because I’ve been able to omit the property name when asking the base class to raise the event. More importantly, it’s less error prone: I can now be confident that the right name will be used every time, even if I rename the property at some point in the future.

There’s a fourth caller information attribute, CallerArgumentExpression, that is a little different: instead of telling us where the call came from, it tells us something about what the call looked like. Example 14-18 shows an excerpt from the runtime libraries’ ArgumentNullException class. It declares a ThrowIfNull method that uses this attribute.

Example 14-18. The CallerArgumentExpressionAttribute in ArgumentNullException.ThrowIfNull
public class ArgumentNullException
{
    public static void ThrowIfNull(
        [NotNull] object? argument,
        [CallerArgumentExpression(nameof(argument))] string? paramName =  null)
    {
...
As you can see, the CallerArgumentExpression attribute takes a single string argument. This must be the name of another parameter in the same method—in this case there is only one other parameter, called argument, so it has to refer to that. The effect is that if you call this method without providing a value for the annotated paramName argument, the C# compiler will pass a string containing the exact expression you used for the argument that the attribute identified. Example 14-19 shows how this ThrowIfNull method is typically called.

Example 14-19. Calling a method that uses CallerArgumentExpressionAttribute
static void Greet(string greetingRecipient)
{
    ArgumentNullException.ThrowIfNull(greetingRecipient);
    Console.WriteLine($"Hello, {greetingRecipient}");
}

Greet("world");
Greet(null!);
The Greet method needs greetingRecipient not to be null, so it calls Arg⁠ume⁠nt​Nul⁠lEx⁠cep⁠tio⁠n.T⁠hro⁠wIf⁠Null, passing in greetingRecipient. Because this code does not provide a second argument to ThrowIfNull, the compiler will provide the full text of the expression we used for the first argument. In this case, that’s "gre⁠eti⁠ng​Rec⁠ipi⁠ent". So the effect is that when I run this program, it throws an Arg⁠ume⁠nt​Nul⁠lEx⁠cep⁠tion with this message:

Value cannot be null. (Parameter 'greetingRecipient')
One of the scenarios this attribute supports is to improve assertion messages. For example, unit test libraries typically provide mechanisms for asserting that certain conditions are true after exercising the code under test. The idea is that if your test contains code such as Assert.IsTrue(answer == 42); the test library could use [CallerArgumentExpression] to be able to report the exact expression (answer == 42) on failure.

You might expect the Debug.Assert method in the runtime libraries to use this for similar reasons, but it does not, because a single-argument overload of that method existed for years before this language feature was added. A two-argument overload using CallerArgumentExpressionAttribute on the second argument would be a viable candidate for code such as Debug.Assert(status == 42); but that also a matches the single-argument method. When a method call could resolve either to a method that is an exact match, or one where the the compiler has to generate code to supply missing optional arguments, it prefers the exact match. The only way to use CallerArgumentExpressionAttribute would be to remove the existing single-argument method, and this would not be a binary-compatible change. The .NET runtime libraries use this attribute only on exception helper methods. At the time of writing this, none of the widely used .NET testing frameworks use this on their assertion methods, nor do the popular assertion libraries, for similar backwards compatibility reasons. The language feature is still relatively new, so perhaps this will change before long.

CLR-Handled Attributes
Some attributes get special treatment at runtime from the CLR. There is no official comprehensive list of such attributes, so in the next few sections, I will just describe some of the most widely used examples.

InternalsVisibleToAttribute
You can apply the InternalsVisibleToAttribute to an assembly to declare that any internal types or members it defines should be visible to one or more other assemblies. A popular use for this is to enable unit testing of internal types. As Example 14-20 shows, you pass the name of the assembly as a constructor argument.

NOTE
Strong naming complicates matters. Strongly named assemblies cannot make their internals visible to assemblies that are not strongly named, and strongly-named assemblies can only reference other strongly-named assemblies. When a strongly named assembly makes its internals visible to another strongly named assembly, it must specify not just the simple name but also the public key of the assembly to which it is granting access. And this is not just the public key token I described in Chapter 12—it is the hexadecimal for the entire public key, which will be several hundred digits. You can discover an assembly’s full public key with the .NET SDK’s sn.exe utility, using the -Tp switch followed by the assembly’s path.

Example 14-20. InternalsVisibleToAttribute
[assembly:InternalsVisibleTo("ImageManagement.Tests")]
[assembly:InternalsVisibleTo("ImageServices.Tests")]
This shows that you can make the types visible to multiple assemblies by applying the attribute multiple times, with a different assembly name each time.

The CLR is responsible for enforcing accessibility rules. Normally, if you try to use an internal class from another assembly, you’ll get an error at runtime. (C# won’t even let you compile such code, but it’s possible to trick the compiler. Or you could write directly in IL. The IL assembler, ILASM, does what you tell it and imposes far fewer restrictions than C#. Once you get past the compile-time restrictions, then you’ll hit the runtime ones.) But when this attribute is present, the CLR relaxes its rules for the assemblies you list. The compiler also understands this attribute and lets code that tries to use externally defined internal types compile as long as the external library names your assembly in an InternalsVisibleToAttribute.

Besides being useful in unit test scenarios, this attribute can also be helpful if you want to split code across multiple assemblies. If you have written a large class library, you might not want to put it into one massive DLL. If it has several areas that your customers might want to use in isolation, it could make sense to split it up so that they can deploy just the parts that they need. However, although you may be able to partition your library’s public-facing API, the implementation might not be as easy to divide, particularly if your codebase performs a lot of reuse. You might have many classes that are not designed for public consumption but that you use throughout your code.

If it weren’t for the InternalsVisibleToAttribute, it would be awkward to reuse shared implementation details across assemblies. Either each assembly would need to contain its own copy of the relevant classes, or you’d need to make them public types in some common assembly. The problem with that second technique is that making types public effectively invites people to use them. Your documentation might state that the types are for the internal use of your framework and should not be used, but that won’t stop some people.

Fortunately, you don’t have to make them public. Any types that are just implementation details can remain internal, and you can make them available to all of your assemblies with the InternalsVisibleToAttribute while keeping them inaccessible to everyone else.

JIT compilation
There are a few attributes that influence how the JIT compiler generates code. You can apply the MethodImplAttribute to a method, passing values from the Met⁠hod​Imp⁠lOp⁠tions enumeration. Its NoInlining value ensures that whenever your method is called by another method, it will be a full method call. Without this, the JIT compiler will sometimes just copy a method’s code directly into the calling code.

In general, you’ll want to leave inlining enabled. The JIT compiler inlines only small methods, and it’s particularly important for tiny methods, such as property accessors. For simple field-based properties, invoking accessors with a normal function call often requires more code than inlining, so this optimization can produce code that’s smaller, as well as faster. (Even if the code is not smaller, it may still be faster, because function calls can be surprisingly expensive. Modern CPUs tend to handle long sequential streams of instructions more efficiently than code that leaps around from one location to another.) However, inlining is an optimization with observable side effects—an inlined method does not get its own stack frame. Earlier, I mentioned some diagnostic APIs you can use to inspect the stack, and inlining will change the number of reported stack frames. If you just want to ask the question “Which method is calling me?” the caller info attributes described earlier provide a more efficient way to discover this and will not be defeated by inlining, but if you have code that inspects the stack for any reason, it can sometimes be confused by inlining. So, just occasionally, it’s useful to disable it.

Conversely, you can specify AggressiveInlining, which encourages the JIT compiler to inline things it might otherwise leave as normal method calls. If you have identified a particular method as being highly performance sensitive, it might be worth trying this setting to see if it makes any difference, although be aware that it could make code either slower or faster—it will depend on the circumstances. Conversely, you can disable all optimizations with the NoOptimization option (although the documentation implies that this is more for the benefit of the CLR team at Microsoft than for consumers, because it is for “debugging possible code generation problems”).

Another attribute that has an impact on optimization is the DebuggableAttribute. The C# compiler automatically applies this to your assembly in Debug builds. The attribute tells the CLR to be less aggressive about certain optimizations, particularly ones that affect variable lifetime and ones that change the order in which code executes. Normally, the compiler is free to change such things as long as the final result of the code is the same, but this can cause confusion if you break into the middle of an optimized method with the debugger. This attribute ensures that variable values and the flow of execution are easy to follow in that scenario.

STAThread and MTAThread
Applications that run only on Windows and that present a UI (e.g., anything using .NET’s WPF or Windows Forms frameworks) typically have the [STAThread] attribute on their Main method (although you won’t always see it, because the entry point is often generated by the build system for these kinds of applications). This is an instruction to the CLR’s interop services for the Component Object Model (COM), but it has broader implications: you need this attribute on Main if you want your main thread to host UI elements.

Various Windows UI features rely on COM under the covers. The clipboard uses it, for example, as do certain kinds of controls. COM has several threading models, and only one of them is compatible with UI threads. One of the main reasons for this is that UI elements have thread affinity, so COM needs to ensure that it does certain work on the right thread. Also, if a UI thread doesn’t regularly check for messages and handle them, deadlock can ensue. If you don’t tell COM that a particular thread is a UI thread, it will omit these checks, and you will encounter problems.

NOTE
Even if you’re not writing UI code, some interop scenarios need the [STAThread] attribute, because certain COM components are incapable of working without it. However, UI work is the most common reason for seeing it.

Since COM is managed for you by the CLR, the CLR needs to know that it should tell COM that a particular thread needs to be handled as a UI thread. When you create a new thread explicitly using the techniques shown in Chapter 16, you can configure its COM threading mode, but the main thread is a special case—the CLR creates it for you when your application starts, and by the time your code runs, it’s too late to configure the thread. Placing the [STAThread] attribute on the Main method tells the CLR that your main thread should be initialized for UI-compatible COM behavior.

STA is short for single-threaded apartment. Threads that participate in COM always belong to either an STA or a multithreaded apartment (MTA). There are other kinds of apartments, but threads have only temporary membership in those; when a thread starts using COM, it must pick either STA or MTA mode. So there is, unsurprisingly, also an [MTAThread] attribute.

Debugging Attributes
Some attributes have no effect on normal execution of code, but can change behavior during debugging. If you annotate a method with the DebuggerStepThroughAttribute, then by default debuggers will allow that code to run without stopping when you single-step through your code. Some code generation tools will apply this attribute so that the code they generate does not distract you while you are debugging.

If you apply the DebuggerDisplayAttribute to a class or struct, it determines how debuggers display instances of that type. For example, if you have written a Coordinate type with X and Y properties, you could annotate it with [DebuggerDisplay("{X}, {Y}")]. This would tell the debugger that to show these property values any time it displays the value of a Coordinate.

Build-Time Attributes
Some attributes are handled as part of the build process. NuGet packages can extend the build process in various ways, and they may supply source generators that can add extra code into your project. These are often controlled by attributes. An advantage of this technique is that it works well with trimming because the attributes are processed entirely during the build, instead of using reflection at runtime.

JSON serialization without reflection
The JSON serialization mechanisms described in Chapter 15 use attributes to enable developers to control how .NET objects are represented in JSON. If you use these APIs in the most straightforward way, they will use reflection to discover these attributes at runtime. However, the .NET SDK includes a code generator which can remove any need to use reflection by processing the attributes and other type information at compile time, and generating code. Examples 15-17 and 15-18 in Chapter 15 show how to use this so I won’t repeat it here.

Regular expression source generation
The .NET runtime libraries have always offered regular expression support, but .NET 7 has introduced a new way to use these. As Example 14-21 shows, you can annotate a partial method with the GeneratedRegex attribute. This triggers a source generator built into the .NET SDK to generate C# code that evaluates the specified regular expression.

Example 14-21. Regular expression source generation
public partial class RegexSourceGeneration
{
    [GeneratedRegex(@"[-+]?\b\d+\b")]
    private static partial Regex IsSignedInteger();

    public static bool TextIsSignedInteger(string text)
        => IsSignedInteger().IsMatch(text);
}
This enables all the work of parsing the regular expression and determining how best to process it to be done at build time. This improves both startup time and throughput.

Interop
The CLR’s interop services define numerous attributes. Since the attributes make sense only in the context of the mechanisms they support, and because there are so many, I will not describe them in full, but Example 14-22 illustrates the kinds of things they can do.

Example 14-22. Interop attributes
[LibraryImport("advapi32.dll", EntryPoint = "LookupPrivilegeValueW",
    SetLastError = true, StringMarshalling = StringMarshalling.Utf16)]
[return: MarshalAs(UnmanagedType.Bool)]
internal static partial bool LookupPrivilegeValue(
    [MarshalAs(UnmanagedType.LPWStr)] string? lpSystemName,
    [MarshalAs(UnmanagedType.LPWStr)] string lpName,
    out LUID lpLuid);
This uses two interop attributes that we saw earlier in Example 14-7 but in a somewhat more complex way. This calls into a function exposed by advapi32.dll, part of the Win32 API. The first argument to the LibraryImport attribute tells us that, but unlike the earlier example, this goes on to provide the interop layer with additional information. The EntryPoint property deals with the fact that Win32 APIs taking strings sometimes come in two forms, working with either 8-bit or 16-bit characters (some old versions of Windows only supported 8-bit text, to conserve memory) and that we want to call the Wide form (hence the W suffix). This particular API uses a common Win32 idiom: it returns a Boolean value to indicate success or failure, but it also uses the Windows SetLastError API to provide more information in the failure case. The attribute’s SetLastError property tells the interop layer to retrieve that immediately after calling this API so that .NET code can inspect it if necessary. This API deals with strings, so interop needs to know which character representation is in use. It then uses MarshalAs on the two string arguments to tell the interop layer which of the many different string representations available in unmanaged code this particular API expects.

Prior to .NET 7, interop attributes were handled at runtime by the CLR (and that still happens if you use the older DllImport attribute instead of LibraryImport). However, that older approach relies on JIT compilation under the covers if any of the arguments or the return type need any kind of runtime processing, meaning it is unavailable if you’re using Native AOT. The .NET SDK includes a code generator that looks for the LibraryImport attribute, and which generates code to convert between .NET and unmanaged types, enabling you to call into unmanaged APIs even when using Native AOT. (In fact, this generated code still ends up using the DllImport attribute, but it defines the target methods in such a way that the mappings between .NET types and unmanaged types are trivial, removing any need for the CLR to do any conversions.)

Defining and Consuming Attributes
The vast majority of attributes you will come across are not intrinsic to the runtime or compiler. They are defined by class libraries and have an effect only if you are using the relevant libraries or frameworks. You are free to do exactly the same in your own code—you can define your own attribute types. Because attributes don’t do anything on their own—they don’t even get instantiated unless something asks to see them—it is normally useful to define an attribute type only if you’re writing some sort of framework, particularly one that is driven by reflection or compile-time code analysis.

For example, unit test frameworks often discover the test classes you write via reflection and enable you to control the test runner’s behavior with attributes. Another example is how Visual Studio uses reflection to discover the properties of editable objects on design surfaces (such as UI controls), and it will look for certain attributes that enable you to customize the editing behavior. Another application of attributes is to opt out of rules applied by the static code analysis tools. (The .NET SDK has built-in tools for detecting potential problems in your code. This is an extensible system, and NuGet packages can add analyzers that expand on this, potentially detecting common mistakes specific to a particular library.) Sometimes these tools make unhelpful suggestions, and you can suppress their warnings by annotating your code with attributes.

The common theme here is that some tool or framework examines your code and decides what to do based on what it finds. This is the kind of scenario in which attributes are a good fit. For example, attributes could be useful if you write an application that end users could extend. You might support loading of external assemblies that augment your application’s behavior—this is often known as a plug-in model. It might be useful to define an attribute that allows a plug-in to provide descriptive information about itself. It’s not strictly necessary to use attributes—you would probably define at least one interface that all plug-ins are required to implement, and you could have members in that interface for retrieving the necessary information. However, one advantage of using attributes is that you would not need to create an instance of the plug-in just to retrieve the description information. That would enable you to show the plug-in’s details to the user before loading it, which might be important if constructing the plug-in could have side effects that the user might not want.

Attribute Types
Example 14-23 shows how an attribute containing information about a plug-in might look.

Example 14-23. An attribute type
[AttributeUsage(AttributeTargets.Class)]
public class PluginInformationAttribute(string name, string author) : Attribute
{
    public string Name { get; } = name;

    public string Author { get; } = author;

    public string? Description { get; set; }
}
To act as an attribute, a type must derive from the Attribute base class. Although Attribute defines various static methods for discovering and retrieving attributes, it does not provide very much of interest for instances. We do not derive from it to get any particular functionality; we do so because the compiler will not let you use a type as an attribute unless it derives from Attribute.

Notice that my type’s name ends in the word Attribute. This is not an absolute requirement, but it is an extremely widely used convention. As you saw earlier, it’s even built into the compiler, which automatically adds the Attribute suffix if you leave it out when applying an attribute. So there’s usually no reason not to follow this convention.

I’ve annotated my attribute type with an attribute. Most attribute types are annotated with the AttributeUsageAttribute, indicating the targets to which the attribute can usefully be applied. The C# compiler will enforce this. Since my attribute in Example 14-23 states that it may be applied only to classes, the compiler will generate an error if you attempt to apply it to anything else.

NOTE
As you’ve seen, sometimes when we apply an attribute, we need to state its target. For example, an attribute appearing before a method targets that method unless you qualify it with the return: prefix. You might think you could leave out these prefixes with attributes that can target only certain members: if an attribute can be applied only to an assembly, do you really need the assembly: qualifier? However, C# doesn’t let you leave it off. It uses the AttributeUsageAttribute only to verify that an attribute has not been misapplied.

My attribute defines only one constructor, so any code that uses it will have to pass the arguments that the constructor requires, as Example 14-24 does.

Example 14-24. Applying an attribute
[PluginInformation("Reporting", "Endjin Ltd.")]
public class ReportingPlugin
{
    ...
}
Attribute classes are free to define multiple constructor overloads to support different sets of information. They can also define properties as a way to support optional pieces of information. My attribute defines a Description property, which is not required because the constructor does not demand a value for it, but which I can set using the syntax I described earlier in this chapter. Example 14-25 shows how that looks for my attribute.

Example 14-25. Providing an optional property value for an attribute

[PluginInformation("Reporting", "Endjin Ltd.",
    Description = "Automated report generation")]
public class ReportingPlugin
{
    ...
}
So far, nothing I’ve shown will cause an instance of my Plu⁠gin⁠Inf⁠orm⁠ation​Att⁠rib⁠ute type to be created. These annotations are simply instructions for how the attribute should be initialized if anything asks to see it. So, if this attribute is to be useful, I need to write some code that will look for it.

Retrieving Attributes
You can discover whether a particular kind of attribute has been applied using the reflection API, which can also instantiate the attribute for you. (You could also use Roslyn, the C# compiler API, but that’s beyond the scope of this book.) In Chapter 13, I showed all of the reflection types representing the various targets to which attributes can be applied—types such as MethodInfo, Type, and PropertyInfo. These all implement an interface called ICustomAttributeProvider, which is shown in Example 14-26.

Example 14-26. ICustomAttributeProvider
public interface ICustomAttributeProvider
{
    object[] GetCustomAttributes(bool inherit);
    object[] GetCustomAttributes(Type attributeType, bool inherit);
    bool IsDefined(Type attributeType, bool inherit);
}
The IsDefined method simply tells you whether or not a particular attribute type is present—it does not instantiate it. The two GetCustomAttributes overloads create attributes and return them. (This is the point at which attributes are constructed and also when any properties the annotations specify are set.) The first overload returns all attributes applied to the target, while the second lets you request only those attributes of a particular type.

All of these methods take a bool argument that lets you specify whether you want only attributes that were applied directly to the target you’re inspecting or also attributes applied to the base type or types.

This interface was introduced in .NET 1.0, so it does not use generics, meaning you need to cast the objects that come back. Fortunately, the Cus⁠tom⁠Att⁠rib⁠ute​Ext⁠ens⁠ions static class defines several extension methods that are more convenient to use. Instead of defining them for the ICustomAttributeProvider interface, it extends the reflection classes that offer attributes. For example, if you have a variable of type Type, you could call GetCustomAttribute<PluginInformationAttribute>() on it, which would construct and return the plug-in information attribute or return null if the attribute is not present. Example 14-27 uses this to show all of the plug-in information from all the DLLs in a particular folder.

Example 14-27. Showing plug-in information
static void ShowPluginInformation(string pluginFolder)
{
    var dir = new DirectoryInfo(pluginFolder);
    foreach (FileInfo file in dir.GetFiles("*.dll"))
    {
        Assembly pluginAssembly = Assembly.LoadFrom(file.FullName);
        var plugins =
             from type in pluginAssembly.ExportedTypes
             let info = type.GetCustomAttribute<PluginInformationAttribute>()
             where info != null
             select new { type, info };

        foreach (var plugin in plugins)
        {
            Console.WriteLine($"Plugin type: {plugin.type.Name}");
            Console.WriteLine(
                $"Name: {plugin.info.Name}, written by {plugin.info.Author}");
            Console.WriteLine($"Description: {plugin.info.Description}");
        }
    }
}
There’s one potential problem with this. I said that one benefit of attributes is that they can be retrieved without instantiating their target types. That’s true here—I’m not constructing any of the plug-ins in Example 14-27. However, I am loading the plug-in assemblies, and a possible side effect of enumerating the plug-ins would be to run static constructors in the plug-in DLLs. So, although I’m not deliberately running any code in those DLLs, I can’t guarantee that no code from those DLLs will run. If my goal is to present a list of plug-ins to the user, and to load and run only the ones explicitly selected, I’ve failed, because I’ve given plug-in code a chance to run. However, we can fix this.

Metadata-Only Load
You do not need to load an assembly fully in order to retrieve attribute information. As I discussed in Chapter 13, you can load an assembly for reflection purposes only with the MetadataLoadContext class. This prevents any of the code in the assembly from running but enables you to inspect the types it contains. However, this presents a challenge for attributes. The usual way to inspect an attribute’s properties is to instantiate it by calling GetCustomAttributes or a related extension method. Since that involves constructing the attribute—which means running some code—it is not supported for assemblies loaded by MetadataLoadContext (not even if the attribute type in question were defined in a different assembly that had been fully loaded in the normal way). If I modified Example 14-27 to load the assembly with Met⁠ada⁠ta​Loa⁠dCo⁠ntext, the call to Get⁠Cus⁠tom⁠Att⁠rib⁠ute⁠<Pl⁠ugi⁠nIn⁠for⁠mat⁠ion​Att⁠rib⁠ute> would throw an exception.

When loading for metadata only, you have to use the GetCustomAttributesData method. Instead of instantiating the attribute for you, this returns the information stored in the metadata—the instructions for creating the attribute. Example 14-28 shows a version of the relevant code from Example 14-27 modified to work this way. (It also includes the code required to initialize the MetadataLoadContext.)

Example 14-28. Retrieving attributes with the MetadataLoadContext

string[] runtimeAssemblies = Directory.GetFiles(
    RuntimeEnvironment.GetRuntimeDirectory(), "*.dll");
var paths = new List<string>(runtimeAssemblies);
paths.Add(file.FullName);

var resolver = new PathAssemblyResolver(paths);
var mlc = new MetadataLoadContext(resolver);

Assembly pluginAssembly = mlc.LoadFromAssemblyPath(file.FullName);
var plugins =
     from type in pluginAssembly.ExportedTypes
     let info = type.GetCustomAttributesData().SingleOrDefault(attrData =>
            attrData.AttributeType.FullName == pluginAttributeType.FullName)
     where info != null
     let description = info.NamedArguments
                           .SingleOrDefault(a => a.MemberName == "Description")
     select new
     {
         type,
         Name = (string) info.ConstructorArguments[0].Value,
         Author = (string) info.ConstructorArguments[1].Value,
         Description =
             description == null ? null : description.TypedValue.Value
     };

foreach (var plugin in plugins)
{
    Console.WriteLine($"Plugin type: {plugin.type.Name}");
    Console.WriteLine($"Name: {plugin.Name}, written by {plugin.Author}");
    Console.WriteLine($"Description: {plugin.Description}");
}
The code is rather more cumbersome because we don’t get back an instance of the attribute. GetCustomAttributesData returns a collection of CustomAttributeData objects. Example 14-28 uses LINQ’s SingleOrDefault operator to find the entry for the PluginInformationAttribute, and if that’s present, the info variable in the query will end up holding a reference to the relevant CustomAttributeData object. The code then picks through the constructor arguments and property values using the ConstructorArguments and NamedArguments properties, enabling it to retrieve the three descriptive text values embedded in the attribute.

As this demonstrates, the MetadataLoadContext adds complexity, so you should use it only if you need the benefits it offers. One benefit is the fact that it won’t run any of the assemblies you load. It can also load assemblies that might be rejected if they were loaded normally (e.g., because they target a specific processor architecture that doesn’t match your process). But if you don’t need the metadata-only option, accessing the attributes directly, as Example 14-27 does, is more convenient.

Generic Attribute Types
C# 11.0 and .NET 7.0 added support for defining generic attribute types. Example 14-29 shows such an attribute, and how to use it.

Example 14-29. A generic attribute type
[AttributeUsage(AttributeTargets.Class)]
public class PluginHelpProviderAttribute<TProvider> : Attribute
    where TProvider : IPluginHelpProvider
{
    public Type ProviderType => typeof(TProvider);
}

// Usage:
[PluginInformation("Reporting", "Endjin Ltd.")]
[PluginHelpProviderAttribute<ReportingPluginHelpProvider>]
public class ReportingPlugin
{
    ...
}
Since this is a fairly recent feature, it is not yet widely used. Most attribute types that need to refer to a particular type (like the ExpectedException attribute shown in Example 14-3) just take a Type object as a constructor argument. That works perfectly well, but generic attribute types have one advantage: they can define constraints for their type arguments. Example 14-29 requires that whatever type we plug into this PluginHelpProviderAttribute<TProvider>, it must be a type that implements a specific interface, IPluginHelpProvider. If we try to use this attribute with a type that does not implement that interface, the compiler will report an error. With the old approach of passing a Type object to the attribute’s constructor, you would either need to wait until the attribute is instantiated to detect the use of an inappropriate type, or write a code analyzer (which is a fairly complex task) to detect the problem at build time.

Summary
Attributes provide a way to embed custom data into an assembly’s metadata. You can apply attributes to a type, any member of a type, a parameter, a return value, or even a whole assembly or one of its modules. A handful of attributes get special handling from the CLR, and a few control compiler features, but most have no intrinsic behavior, acting merely as passive information containers. Attributes do not even get instantiated unless something asks to see them. All of this makes attributes most useful in systems with reflection-driven behavior—if you already have one of the reflection API objects such as ParameterInfo or Type, you can ask it directly for attributes. You therefore most often see attributes used in frameworks that inspect your code with reflection, such as unit test frameworks, serialization frameworks, data-driven UI elements like Visual Studio’s Properties panel, or plug-in frameworks. Sometimes frameworks of this kind can use the C# compiler API (Roslyn) to discover attributes at build time. This enables them to avoid relying on reflection, making them compatible with Native AOT. If you are using a framework of this kind, you will typically be able to configure its behavior by annotating your code with the attributes the framework recognizes. If you are writing this sort of framework, then it may make sense to define your own attribute types.


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


14. Attributes
15. Files and Streams
16. Multithreading
24h 20m remaining
Chapter 15. Files and Streams
Most of the techniques I’ve shown so far in this book revolve around the information that lives in objects and variables. This kind of state is stored in a particular process’s memory, but to be useful, a program must interact with a broader world. This might happen through UI frameworks, but there’s one particular abstraction that can be used for many kinds of interactions with the outside world: a stream.

Streams are so widely used in computing that you will no doubt already be familiar with them, and a .NET stream is much the same as in most other programming systems: it is simply a sequence of bytes. That makes a stream a useful abstraction for many commonly encountered features such as a file on disk or the body of an HTTP response. A console application uses streams to represent its input and output. If you run such a program interactively, the text that the user types at the keyboard becomes the program’s input stream, and anything the program writes to its output stream appears on screen. A program doesn’t necessarily know what kind of input or output it has, though—you can redirect these streams with console programs. For example, the input stream might actually provide the contents of a file on disk, or it could even be the output from some other program.

NOTE
Not all I/O APIs are stream-based. For example, in addition to the input stream, the Console class provides a ReadKey method that gives information about exactly which key was pressed, which works only if the input comes from the keyboard. So, although you can write programs that do not care whether their input comes interactively or from a file, some programs are pickier.

The stream APIs present you with raw byte data. However, it is possible to work at a different level. For example, there are text-oriented APIs that can wrap underlying streams, so you can work with characters or strings instead of raw bytes. There are also various serialization mechanisms that enable you to convert .NET objects into a stream representation, which you can turn back into objects later, making it possible to save an object’s state persistently or to send that state over the network. I’ll show these higher-level APIs later, but first, let’s look at the stream abstraction itself.

The Stream Class
The Stream class is defined in the System.IO namespace. It is an abstract base class, with concrete derived types such as FileStream or GZipStream representing particular kinds of streams. Example 15-1 shows three of the Stream class’s members. It has several other members, but these are at the heart of the abstraction. (As you’ll see later, there are also asynchronous versions of Read and Write. The latest .NET versions also provide overloads that take one of the span types described in Chapter 18 in place of an array. Everything I say in this section about these methods also applies to the asynchronous and span-based forms.)

Example 15-1. The members at the heart of Stream
public abstract int Read(byte[] buffer, int offset, int count);
public abstract void Write(byte[] buffer, int offset, int count);
public abstract long Position { get; set; }
Some streams are read-only. For example, when the input stream for a console application represents the keyboard or the output of some other program, there’s no meaningful way for the program to write to that stream. (And for consistency, even if you use input redirection to run a console application with a file as its input, the input stream will be read-only.) Some streams are write-only, such as the output stream of a console application. If you call Read on a write-only stream or Write on a read-only one, these methods throw a NotSupportedException.

TIP
The Stream class defines various bool properties that describe a stream’s capabilities, so you don’t have to wait until you get an exception to find out what sort of stream you’ve got. You can check the CanRead or CanWrite properties.

Both Read and Write take a byte[] array as their first argument, and these methods copy data into or out of that array, respectively. The offset and count arguments that follow indicate the array element at which to start and the number of bytes to read or write; you do not have to use the whole array. Notice that there are no arguments to specify the offset within the stream at which to read or write. This is managed by the Position property—this starts at zero, but each time you read or write, the position advances by the number of bytes processed.

Notice that the Read method returns an int. This tells you how many bytes were read from the stream—the method does not guarantee to provide the amount of data you requested. One obvious reason for this is that you could reach the end of the stream, so even though you may have asked to read 100 bytes into your array, there may have been only 30 bytes of data left between the current Position and the end of the stream. However, that’s not the only reason you might get less than you asked for, and this often catches people out, so for the benefit of people skim-reading this chapter, I’ll put this in a scary warning.

WARNING
If you ask for more than one byte at a time, a Stream is always free to return less data than you requested from Read for any reason. You should never presume that a call to Read returned as much data as it could, even if you have good reason to know that the amount you asked for will be available.

The reason Read is slightly tricky is that some streams are live, representing a source of information that produces data gradually as the program runs. For example, if a console application is running interactively, its input stream can provide data only as fast as the user types; a stream representing data being received over a network connection can provide data only as fast as it arrives. If you call Read and you ask for more data than is currently available, a stream might wait until it has as much as you’ve asked for, but it doesn’t have to—it may return whatever data it has immediately. (The only situation in which it is obliged to wait before returning is if it currently has no data at all but is not yet at the end of the stream. It has to return at least one byte, because a 0 return value indicates the end of the stream.) If you want to ensure that you read a specific number of bytes, you used to have to check whether Read returned fewer bytes than you wanted, and if necessary, keep calling it until you have what you need. (On .NET Framework, you still have to do this.) Fortunately, .NET 7.0 added a new method, ReadExactly, which takes the same arguments as Read, but won’t return until it either reaches the end of the stream, or is able to return as many bytes as you asked for. It also added a similar ReadAtLeast, which will never return fewer bytes than you asked for (unless it reaches the end of the stream) but can return more if the stream happens to have more available immediately.

Stream also offers a simpler way to read. The ReadByte method returns a single byte, unless you hit the end of the stream, at which point it returns a value of −1. (Its return type is int, enabling it to return any possible value for byte as well as negative values.) This avoids the problem of being handed back only some of the data you requested, because if you get anything back at all, you always get exactly one byte. However, it’s not especially convenient or efficient if you want to read larger chunks of data.

The Write method doesn’t have any of these issues. If it succeeds, it always accepts all of the data you provide. Of course, it might fail—it could throw an exception before it manages to write all of the data because of an error (e.g., running out of space on disk or losing a network connection).

Position and Seeking
Streams automatically update their current position each time you read or write. As you can see in Example 15-1, the Position property can be set, so you can attempt to move directly to a particular position. This is not guaranteed to work because it’s not always possible to support it. For example, a Stream that represents data being received over a TCP network connection could produce data indefinitely—as long as the connection remains open and the other end keeps sending data, the stream will continue to honor calls to Read. A connection could remain open for many days and might receive terabytes of data in that time. If such a stream let you set its Position property, enabling your code to go back and reread data received earlier, the stream would have to find somewhere to store every single byte it received just in case the code using the stream wants to see it again. Since that might involve storing more data than you have space for on disk, this is clearly not practical, so some streams will throw NotSupportedException when you try to set the Position property. (There’s a CanSeek property you can use to discover whether a particular stream supports changing the position, so just like with read-only and write-only streams, you don’t have to wait until you get an exception to find out whether it will work.)

As well as the Position property, Stream also defines a Seek method, whose signature is shown in Example 15-2. This lets you specify the position you require relative to the stream’s current position. (This also throws NotSupportedException on streams that don’t support seeking.)

Example 15-2. The Seek method
public abstract long Seek(long offset, SeekOrigin origin);
If you pass SeekOrigin.Current as the second argument, it will set the position by adding the first argument to the current position. You can pass a negative offset if you want to move backward. You can also pass SeekOrigin.End to set the position to be some specified number of bytes from the end of the stream. Passing Seek​Ori⁠gin.Begin has the same logical effect as just setting Position—it sets the position relative to the start of the stream.

Flushing
As with many stream APIs on other programming systems, writing data to a Stream does not necessarily cause the data to reach its destination immediately. When a call to Write returns, all you know is that it has copied your data somewhere; but that might be a buffer in memory, not the final target. For example, if you write a single byte to a stream representing a file on a storage device, the stream object will typically defer writing that to the drive until it has enough bytes to make it worth the effort. Storage devices are block-based, meaning that writes happen in fixed-size chunks, typically several kilobytes in size, so it generally makes sense to wait until there’s enough data to fill a block before writing anything out.

This buffering is usually a good thing—it improves write performance while enabling you to ignore the details of how the disk works. However, a downside is that if you write data only occasionally (e.g., when writing error messages to a logfile), you could easily end up with long delays between the program writing data to a stream and that data reaching the disk. This could be perplexing for someone trying to diagnose a problem by looking at the logfiles of a program that’s currently running. And more insidiously, if your program crashes, anything in a stream’s buffers that has not yet made it to the storage device will probably be lost.

The Stream class therefore offers a Flush method. This lets you tell the stream that you want it to do whatever work is required to ensure that any buffered data is written to its target, even if that means making suboptimal use of the buffer.

When using a FileStream, the Flush method does not necessarily guarantee that the data being flushed has made it to disk yet. It merely makes the stream pass the data to the OS. Before you call Flush, the OS might not even have seen the data, so if you were to terminate the process suddenly, the data would be lost. After Flush has returned, the OS has everything your code has written, so the process could be terminated without loss of data. However, the OS may perform additional buffering of its own, so if the power fails before the OS gets around to writing everything to disk, the data will still be lost. If you need to guarantee that data has been written persistently (rather than merely ensuring that you’ve handed it to the OS), you will also need to either use the WriteThrough flag, described in “FileStream Class”, or call the Flush overload that takes a bool, passing true to force flushing to the storage device.

A stream automatically flushes its contents when you call Dispose. You need to use Flush only when you want to keep a stream open after writing out buffered data. It is particularly important if there will be extended periods during which the stream is open but inactive. (If the stream represents a network connection, and if your application depends on prompt data delivery—this would be the case in an online chat application or game, for example—you would call Flush even if you expect only fairly brief periods of inactivity.)

Copying
Copying all of the data from one stream to another is occasionally useful. It wouldn’t be hard to write a loop to do this, but you don’t have to, because the Stream class’s CopyTo method (or the equivalent CopyToAsync) does it for you. There’s not much to say about it. The main reason I’m mentioning it is that it’s not uncommon for developers to write their own version of this method because they didn’t know the functionality was built into Stream.

Length
Some streams are able to report their length through the predictably named Length property. As with Position, this property’s type is long—Stream uses 64-bit numbers because streams often need to be larger than 2 GB, which would be the upper limit if sizes and positions were represented with int.

Stream also defines a SetLength method that lets you define the length of a stream (where supported). You might think about using this when writing a large quantity of data to a file, to ensure that there is enough space to contain all the data you wish to write—better to get an IOException before you start than wasting time on a doomed operation and potentially causing system-wide problems by using up all of the free space. However, many filesystems support sparse files, letting you create files far larger than the available free space, so in practice you might not see any error until you start writing nonzero data. Even so, if you specify a length that is longer than the filesystem supports, SetLength will throw an ArgumentException.

Not all streams support length operations. The Stream class documentation says that the Length property is available only on streams that support CanSeek. This is because streams that support seeking are typically ones where the whole content of the stream is known and accessible up front. Seeking is unavailable on streams where the content is produced at runtime (e.g., input streams representing user input or streams representing data received over the network), and in those cases the length is also very often not known in advance. As for SetLength, the documentation states that this is supported only on streams that support both writing and seeking. (As with all members representing optional features, Length and SetLength will throw a NotSupportedException if you try to use these members on streams that do not support them.)

Disposal
Some streams represent resources external to the .NET runtime. For example, FileStream provides stream access to the contents of a file, so it needs to obtain a file handle from the OS. It’s important to close handles when you’re done with them; otherwise you might prevent other applications from being able to use the file. Consequently, the Stream class implements the IDisposable interface (described in Chapter 7) so that it can know when to do that. And, as I mentioned earlier, buffering streams such as FileStream flush their buffers when you call Dispose, before closing handles.

Not all stream types depend on Dispose being called: MemoryStream works entirely in memory, so the GC would be able to take care of it. But in general, if you caused a stream to be created, you should call Dispose when you no longer need it.

NOTE
There are some situations in which you will be provided with a stream, but it is not your job to dispose it. For example, ASP.NET Core can provide streams to represent data in HTTP requests and responses. It creates these for you and then disposes them after you’ve used them, so you should not call Dispose on them.

Confusingly, the Stream class also has a Close method. This is an accident of history. The first public beta release of .NET 1.0 did not define IDisposable, and C# did not have using statements—the keyword was only for using directives, which bring namespaces into scope. The Stream class needed some way of knowing when to clean up its resources, and since there was not yet a standard way to do this, it invented its own idiom. It defined a Close method, which was consistent with the terminology used in many stream-based APIs in other programming systems. IDisposable was added before the final release of .NET 1.0, and the Stream class added support for this, but it left the Close method in place; removing it would have disrupted a lot of early adopters who had been using the betas. But Close is redundant, and the documentation actively advises against using it. It says you should call Dispose instead (through a using statement if that is convenient). There’s no harm in calling Close—there’s no practical difference between that and Dispose—but Dispose is the more common idiom and is therefore preferred.

Asynchronous Operation
The Stream class offers asynchronous versions of Read and Write. Be aware that there are two forms. Stream first appeared in .NET 1.0, so it supported what was then the standard asynchronous mechanism, the Asynchronous Programming Model (APM, described in Chapter 16) through the BeginRead, EndRead, BeginWrite, and EndWrite methods. This model is now deprecated, having been superseded by the newer Task-based Asynchronous Pattern (or TAP, also described in Chapter 16). Stream supports this through its ReadAsync and WriteAsync methods. There are two more operations that did not originally have any kind of asynchronous form that now have TAP versions: FlushAsync and CopyToAsync. (These support only TAP, because APM was already deprecated by the time Microsoft added these methods.)

WARNING
Avoid the old APM-based Begin/End forms of Read and Write. For a while they were only in .NET Framework. They were later added to .NET Standard 2.0 to make it easier to migrate existing code from .NET Framework to .NET, so they are supported only for legacy scenarios.

Some stream types implement asynchronous operations using very efficient techniques that correspond directly to the asynchronous capabilities of the underlying OS. (FileStream does this, as do the various streams .NET can provide to represent content from network connections.) You may come across libraries with custom stream types that do not do this, but even then, the asynchronous methods will be available, because the base Stream class can fall back to using multithreaded techniques instead.

One thing you need to be careful of when using asynchronous reads and writes is that a stream only has a single Position property. Reads and writes depend on the current Position and also update it when they are done, so in general you must avoid starting a new operation before one already in progress is complete. However, if you wish to perform multiple concurrent read or write operations from a particular file, FileStream has special handling for this. If you tell it that you will be using the file in asynchronous mode, operations use the value Position has at the start of the operation, and once an asynchronous read or write has started, you are allowed to change Position and start another operation without waiting for all the previous ones to complete. But this only applies to FileStream, and only when the file is opened in asynchronous mode. Alternatively, instead of using FileStream, you could use the RandomAccess class, which defines methods for performing read and write operations directly against a file handle. This class’s methods all require you pass an argument specifying the position explicitly for each read and write.

.NET offers IAsyncDisposable, an asynchronous form of Dispose. The Stream class implements this, because disposal often involves flushing, which is a potentially slow operation. (This is not available on .NET Framework.)

Concrete Stream Types
The Stream class is abstract, so to use a stream, you’ll need a concrete derived type. In some situations, this will be provided for you—the ASP.NET Core web framework supplies stream objects representing HTTP request and response bodies, for example, and the client-side HttpClient class will do something similar. But sometimes you’ll need to create a stream object yourself. This section describes a few of the more commonly used types that derive from Stream.

The FileStream class represents a file on the filesystem. I will describe this in “Files and Directories”.

MemoryStream lets you create a stream on top of a byte[] array. You can either take an existing byte[] and wrap it in a MemoryStream, or you can create a MemoryStream and then populate it with data by calling Write (or WriteAsync). You can retrieve the populated byte[] once you’re done by calling either ToArray or GetBuffer. (ToArray allocates a new array, with the size based on the number of bytes actually written. GetBuffer is more efficient because it returns the underlying array MemoryStream is using, but unless the writes happened to fill it completely, the array returned will typically be oversized, with some unused space at the end.) This class is useful when you are working with APIs that require a stream and you don’t have one for some reason. For example, most of the serialization APIs described later in this chapter work with streams, but you might end up wanting to use that in conjunction with some other API that works in terms of byte[]. MemoryStream lets you bridge between those two representations.

Both Windows and Unix define an interprocess communication (IPC) mechanism enabling you to connect two processes through a stream. Windows calls these named pipes. Unix also has a mechanism with that name, but it is completely different; it does, however, offer a mechanism similar to Windows named pipes: domain sockets. Although the precise details of Windows named pipes and Unix domain sockets differ, the various classes derived from PipeStream provide a common abstraction for both in .NET.

BufferedStream derives from Stream but also takes a Stream in its constructor. It adds a layer of buffering, which is useful if you want to perform small reads or writes on a stream that is designed to work best with larger operations. (You don’t need to use this with FileStream because that has its own built-in buffering mechanism.)

There are various stream types that transform the contents of other streams in some way. For example, DeflateStream, GZipStream, and BrotliStream implement three widely used compression algorithms. You can wrap these around other streams to compress the data written to the underlying stream or to decompress the data read from it. (These just provide the lowest-level compression service. If you want to work with the popular ZIP format for packages of compressed files, use the ZipArchive class. .NET 7.0 added a TarFile class for working with the tar archive used for similar purposes in Unix.) There’s also a class called CryptoStream, which can encrypt or decrypt the contents of other streams using any of the wide variety of encryption mechanisms supported in .NET.

One Type, Many Behaviors
As you’ve now seen, the abstract base class Stream gets used in a wide range of scenarios. It is arguably an abstraction that has been stretched a little too thin. The presence of properties such as CanSeek that tell you whether the particular Stream you have can be used in a certain way is arguably a symptom of an underlying problem, an example of something known as a code smell. .NET streams did not invent this particular one-size-fits-all approach—it was popularized by Unix and the C programming language’s standard library a long time ago. The problem is that when writing code that deals with a Stream, you might not know what sort of thing you are dealing with.

There are many different ways to use a Stream, but three usage styles come up a lot:

Sequential access of a sequence of bytes

Random access, with a presumption of efficient caching

Access to some underlying capability of a device or system

As you know, not all Stream implementations support all three models—if CanSeek returns false, that rules out the middle option. But what is less obvious is that even when these properties indicate that a capability is available, not all streams support all usage models equally efficiently.

For example, I worked on a project that used a library for accessing files in a cloud-hosted storage service that was able to represent those files with Stream objects. This looks convenient because you can pass those to any API that works with a Stream. However, it was designed very much for the third style of use in the preceding list: every single call to Read (or ReadAsync) would cause the library to make an HTTP request to the storage service. We had initially hoped to use this with another library that knew how to parse Parquet files (a binary tabular data storage format widely used in high-volume data processing). However, it turned out that the library was expecting a stream that supported the second type of access: it jumped back and forth through the file, making large numbers of fairly small reads. It worked perfectly well with the FileStream type I’ll be describing later, because that supports the first two modes of use well. (For the second style, it relies on the OS to do the caching.) But it would have been a performance disaster to plug a Stream from the storage service library directly into the Parquet parsing library.

It’s not always obvious when you have a mismatch of this kind. In this example, the properties reporting capabilities such as CanSeek gave no clue that there would be a problem. And applications that use Parquet files often use some sort of remote storage service, rather than the local filesystem, so there was no obvious reason to think that this library would presume that any Stream would offer local filesystem-like caching. It did technically work when we tried it: the storage library Stream worked hard to do everything asked of it, and the code worked correctly…eventually. But it was unusably slow. So whenever you use a Stream, it’s important to make sure you have fully understood what access patterns it will be subjected to and how efficiently it supports those patterns.

In some cases you might be able to bridge the gap. The BufferedStream class can often take a Stream designed only for the third usage style mentioned previously and adapt it for the first style of usage. However, there’s nothing in the runtime libraries that can add support for the second style of usage to a Stream that doesn’t already innately support it. (This is typically only available either with streams that represent something already fully in memory or that wrap some local API that does the caching for you, such as the OS filesystem APIs.) In these cases you will either need to rethink your design (e.g., make a local copy of the Stream contents), change the way that the Stream is consumed, or write some sort of custom caching adapter. (In the end, we wrote an adapter that augmented the capabilities of BufferedStream with just enough random access caching to solve the performance problems.)

Text-Oriented Types
Stream is byte oriented, but it’s common to work with files that contain text. If you want to process text stored in a file (or received over the network), it is cumbersome to use a byte-based API, because this forces you to deal explicitly with all of the variations that can occur. For example, there are multiple conventions for how to represent the end of a line—Windows typically uses two bytes with values of 13 and 10, as do many internet standards such as HTTP, but Unix-like systems often use just a single byte with the value 10.

There are also multiple character encodings in popular use. Some files use one byte per character, some use two, and some use a variable-length encoding. There are many different single-byte encodings too, so if you encounter a byte value of, say, 163 in a text file, you cannot know what that means unless you know which encoding is in use.

In a file using the single-byte Windows-1252 encoding, the value 163 represents a pound sign: £.1 But if the file is encoded with ISO/IEC 8859-5 (designed for regions that use Cyrillic alphabets), the exact same code represents the Cyrillic capital letter DJE: Ђ. And if the file uses the UTF-8 encoding, the value 163 would only be allowed as part of a multibyte sequence representing a single character.

Awareness of these issues is, of course, an essential part of any developer’s skill set, but that doesn’t mean you should have to handle every little detail any time you encounter text. So .NET defines specialized abstractions for working with text.

TextReader and TextWriter
The abstract TextReader and TextWriter classes present data as a sequence of char values. Logically speaking, these classes are similar to a stream, but each element in the sequence is a char instead of a byte. However, there are some differences in the details. For one thing, there are separate abstractions for reading and writing. Stream combines these, because it’s common to want read/write access to a single entity, particularly if the stream represents a file on disk. For byte-oriented random access, this makes sense, but it’s a problematic abstraction for text.

Variable-length encodings make it tricky to support random write access (i.e., the ability to change values at any point in the sequence). Consider what it would mean to take a 1 GB UTF-8 text file whose first character is a $ and replace that first character with a £. In UTF-8, the $ character takes only one byte, but £ requires two, so changing that first character would require an extra byte to be inserted at the start of the file. This would mean moving the remaining file contents—almost 1 GB of data—along by one byte.

Even read-only random access is relatively expensive. Finding the millionth character in a UTF-8 file requires you to read the first 999,999 characters, because without doing that, you have no way of knowing what mix of single-byte and multibyte characters there is. The millionth character might start at the millionth byte, but it could also start some 4 million bytes in, or anywhere in between. Since supporting random access with variable-length text encodings is expensive, particularly for writable data, these text-based types don’t offer it. Without random access, there’s no real benefit in merging readers and writers into one type. Also, separating reader and writer types removes the need to check the CanWrite property—you know that you can write because you’ve got a TextWriter.

TextReader offers several ways to read data. The simplest is the zero-argument overload of Read, which returns an int. This will return −1 if you’ve reached the end of the input and will otherwise return a character value. (You’ll need to cast it to a char once you’ve verified that it’s nonnegative.) Alternatively, there are two methods that look similar to the Stream class’s Read method, as Example 15-3 shows.

Example 15-3. TextReader chunk reading methods
public virtual int Read(char[] buffer, int index, int count) {...}
public virtual int ReadBlock(char[] buffer, int index, int count) {...}
Just like Stream.Read, these take an array, as well as an index into that array and a count, and will attempt to read the number of values specified. The most obvious difference from Stream is that these use char instead of byte. But what’s the difference between Read and ReadBlock? ReadBlock solves the same problem as ReadExactly does for streams: whereas Read may return fewer characters than you asked for, ReadBlock will not return until either as many characters as you asked for are available or it reaches the end of the content.

One of the challenges of handling text input is dealing with the various conventions for line endings, and TextReader can insulate you from that. Its ReadLine method reads an entire line of input and returns it as a string. This string will not include the end-of-line character or characters.

NOTE
TextReader does not presume one particular end-of-line convention. It accepts either a carriage return (character value 13, which we write as \r in string literals) or a line feed (10, or \n). And if both characters appear adjacently, the character pair is treated as being a single end of line, despite being two characters. This processing happens only when you use either ReadLine or Read​Li⁠neAsync. If you work directly at the character level by using Read or ReadBlock, you will see the end-of-line characters exactly as they are.

TextReader also offers ReadToEnd, which reads the input in its entirety and returns it as a single string. And finally, there’s Peek, which does the same thing as the single-argument Read method, except it does not change the state of the reader. It lets you look at the next character without consuming it, so the next time you call either Peek or Read, it will return the same character again.

As for TextWriter, it offers two overloaded methods for writing: Write and WriteLine. Each of these offers overloads for all of the built-in value types (bool, int, float, etc.). Functionally, the class could have gotten away with a single overload that takes an object, because that can just call ToString on its argument, but these specialized overloads make it possible to avoid boxing the argument. TextWriter also offers a Flush method for much the same reason that Stream does.

By default, a TextWriter will use the default end-of-line sequence for the OS you are running on. On Windows this is the \r\n sequence (13, then 10). On Linux or macOS you will just get a single \n at each line end. You can change this by setting the writer’s NewLine property.

Both of these abstract classes implement IDisposable because some of the concrete derived text reader and writer types are wrappers around other disposable resources.

As with Stream, these classes offer asynchronous methods for reading and writing (although StreamReader doesn’t implement IAsyncDisposable). Unlike with Stream, this was a fairly recent addition, so they support only the task-based pattern described in Chapter 16, which can be consumed with the await keyword described in Chapter 17.

Concrete Reader and Writer Types
As with Stream, various APIs in .NET will present you with TextReader and TextWriter objects. For example, the Console class defines In and Out properties that provide textual access to the process’s input and output streams. I’ve not described these before, but we have been using them implicitly—the Console.WriteLine method overloads are all just wrappers that call Out.WriteLine for you. Likewise, the Console class’s Read and ReadLine methods simply forward to In.Read and In.ReadLine. There’s also Error, another TextWriter for writing to the standard error output stream. However, there are some concrete classes that derive from TextReader or TextWriter that you might want to instantiate directly.

StreamReader and StreamWriter
Perhaps the most useful concrete text reader and writer types are StreamReader and StreamWriter, which wrap a Stream object. You can pass a Stream as a constructor argument, or you can just pass a string containing the path of a file, in which case they will automatically construct a FileStream for you and then wrap that. Example 15-4 uses this technique to write some text to a file.

Example 15-4. Writing text to a file with StreamWriter
using (var fw = new StreamWriter(@"c:\temp\out.txt"))
{
    fw.WriteLine($"Writing to a file at {DateTime.Now}");
}
There are various constructor overloads offering more fine-grained control. When passing a string in order to use a file with a StreamWriter (as opposed to some Stream you have already obtained), you can optionally pass a bool indicating whether to start from scratch or to append to an existing file if one exists. (A true value enables appending.) If you do not pass this argument, appending is not used, and writing will begin from the start. You can also specify an encoding. By default, StreamWriter will use UTF-8 with no byte order mark (BOM), but you can pass any type derived from the Encoding class, which is described in “Encoding”.

StreamReader is similar—you can construct it by passing either a Stream or a string containing the path of a file, and you can optionally specify an encoding. However, if you don’t specify an encoding, the behavior is subtly different from StreamWriter. Whereas StreamWriter just defaults to UTF-8, StreamReader will attempt to detect the encoding from the stream’s content. It looks at the first few bytes and will look for certain features that are typically a good sign that a particular encoding is in use. If the encoded text begins with a Unicode BOM, this makes it possible to determine with high confidence what the encoding is.

StringReader and StringWriter
The StringReader and StringWriter classes serve a similar purpose to MemoryStream: they are useful when you are working with an API that requires either a TextReader or TextWriter, but you want to work entirely in memory. Whereas MemoryStream presents a Stream API on top of a byte[] array, StringReader wraps a string as a TextReader, while StringWriter presents a TextWriter API on top of a StringBuilder.

One of the APIs .NET offers for working with XML, XmlReader, requires either a Stream or a TextReader. Suppose you have XML content in a string. If you pass a string when creating a new XmlReader, it will interpret that as a URI from which to fetch the content, rather than the content itself. The constructor for StringReader that takes a string just wraps that string as the content of the reader, and we can pass that to the XmlReader.Create overload that requires a TextReader, as Example 15-5 shows. (The line that does this is in bold—the code that follows just uses the XmlReader to read the content to show that it works as expected.)

Example 15-5. Wrapping a string in a StringReader

string xmlContent =
    "<message><text>Hello</text><recipient>world</recipient></message>";
var xmlReader = XmlReader.Create(new StringReader(xmlContent));
while (xmlReader.Read())
{
    if (xmlReader.NodeType == XmlNodeType.Text)
    {
        Console.WriteLine(xmlReader.Value);
    }
}
StringWriter is even simpler: you can just construct it with no arguments. Once you’ve finished writing to it, you can call either ToString or GetStringBuilder to extract all of the text that has been written.

Encoding
As I mentioned earlier, if you’re using the StreamReader or StreamWriter, these need to know which character encoding the underlying stream uses to be able to convert correctly between the bytes in the stream and .NET’s char or string types. To manage this, the System.Text namespace defines an abstract Encoding class, with various encoding-specific public concrete derived types, including ASCIIEncoding, UTF7Encoding, UTF8Encoding, UTF32Encoding, and UnicodeEncoding.

Most of those type names are self-explanatory, because they are named after the standard character encodings they represent, such as ASCII or UTF-8. The one that requires a little more explanation is UnicodeEncoding—after all, UTF-7, UTF-8, and UTF-32 are all Unicode encodings, so what’s this other one for? When Windows introduced support for Unicode back in the first version of Windows NT, it adopted a slightly unfortunate convention: in documentation and various API names, the term Unicode was used to refer to a 2-byte little-endian2 character encoding, which is just one of many possible encoding schemes, all of which could correctly be described as being “Unicode” of one form or another.

The UnicodeEncoding class is named to be consistent with this historical convention, although even then it’s still a bit confusing. The encoding referred to as “Unicode” in Win32 APIs is effectively UTF-16LE, but the UnicodeEncoding class is also capable of supporting the big-endian UTF-16BE.

The base Encoding class defines static properties that return instances of all the encoding types I’ve mentioned, so if you need an object representing a particular encoding, you would normally just write Encoding.ASCII or Encoding.UTF8, etc., instead of constructing a new object. There are two properties of type UnicodeEncoding: the Unicode property returns one configured for UTF-16LE, and BigEndianUnicode returns one for UTF-16BE.

For the various Unicode encodings, these properties will return encoding objects that will tell StreamWriter to generate a byte order mark at the start of the output. The main purpose of the BOM is to enable software that reads encoded text to detect automatically whether the encoding is big- or little-endian. (You can also use it to recognize UTF-8, because that encodes the BOM differently than other encodings.) If you know that you will be using an endian-specific encoding (e.g., UTF-16LE), the BOM is unnecessary, because you already know the order, but the Unicode specification defines adaptable formats in which the encoded bytes can advertise the order in use by starting with a BOM, a character with Unicode code point U+FEFF. The 16-bit version of this encoding is just called UTF-16, and you can tell whether any particular set of UTF-16-encoded bytes is big- or little-endian by seeing whether it begins with 0xFE, 0xFF or 0xFF, 0xFE.

WARNING
Although Unicode defines encoding schemes that allow the endianness to be detected, it is not possible to create an Encoding object that works that way—it will always have a specific endianness. So, although an Encoding specifies whether a BOM should be written when writing data, this does not influence the behavior when reading data—it will always presume the endianness specified when the Encoding was constructed. This means that the Encoding.UTF32 property is arguably misnamed—it always interprets data as little-endian even though the Unicode specification allows UTF-32 to use either big- or little-endian. Encoding.UTF32 is really UTF-32LE.

As mentioned earlier, if you do not specify an encoding when creating a StreamWriter, it defaults to UTF-8 with no BOM, which is different from Encoding.UTF8—that will generate a BOM. And recall that StreamReader is more interesting: if you do not specify an encoding, it will attempt to detect the encoding. So .NET is able to handle automatic detection of byte ordering as required by the Unicode specification for UTF-16 and UTF-32; it is just that the way to do it is not to specify any particular encoding when constructing a StreamReader. It will look for a BOM, and if it finds one present, it will use a suitable Unicode encoding; otherwise, it presumes UTF-8 encoding.

UTF-8 is a popular encoding. If your main language is English, it’s a particularly convenient representation, because if you happen to use only the characters available in ASCII, each character will occupy a single byte, and the encoded text will have the exact same byte values as it would with ASCII encoding. But unlike ASCII, you’re not limited to a 7-bit character set. All Unicode code points are available; you just have to use multibyte representations for anything outside of the ASCII range. However, although it’s very widely used, UTF-8 is not the only popular 8-bit encoding.

Code page encodings
Windows, like DOS before it, has long supported 8-bit encodings that extend ASCII. ASCII is a 7-bit encoding, meaning that with 8-bit bytes you have 128 “spare” values to use for other characters. This is nowhere near enough to cover every character for every locale, but within a particular country, it’s often enough to get by (although not always—many Far Eastern countries need more than 8 bits per character). But each country tends to want a different set of non-ASCII characters, depending on which accented characters are popular in that locale and whether a non-Roman alphabet is required. So various code pages exist for different locales. For example, code page 1253 uses values in the range 193–254 to define characters from the Greek alphabet (filling the remaining non-ASCII values with useful characters such as non-US currency symbols). Code page 1255 defines Hebrew characters instead, while 1256 defines Arabic characters in the upper range (and there is some common ground for these particular code pages, such as using 128 for the euro symbol, €, and 163 for the pound sign, £).

One of the most commonly encountered code pages is 1252, because that’s the Windows default for English-speaking locales. This does not define a non-Roman alphabet; instead it uses the upper character range for useful symbols and for various accented versions of the Roman alphabet that enable a wide range of Western European languages to be adequately represented.

You can create an encoding for a code page by calling the Encoding.GetEncoding method, passing in the code page number. (The concrete type of the object you get back is often not one of those I listed earlier. This method may return nonpublic types that derive from Encoding.) Example 15-6 uses this to write text containing a pound sign to a file using code page 1252.

Example 15-6. Writing with the Windows 1252 code page
using (var sw = new StreamWriter("Text.txt", false,
                                 Encoding.GetEncoding(1252)))
{
    sw.Write("£100");
}
This will encode the £ symbol as a single byte with the value 163. With the default UTF-8 encoding, it would have been encoded as two bytes, with values of 194 and 163, respectively.

Using encodings directly
TextReader and TextWriter are not the only way to use encodings. Objects representing encodings (such as Encoding.UTF8) define various members. The GetBytes method converts a string directly to a byte[] array, for example, and the GetString method converts back again.

You can also discover how much data these conversions will produce. GetByteCount tells you how large an array GetBytes would produce for a given string, while GetCharCount tells you how many characters decoding a particular array would generate. You can also find an upper limit for how much space will be required without knowing the exact text with GetMaxByteCount. Instead of a string, this takes a number, which it interprets as a string length; since .NET strings use UTF-16, this means that this API answers the question “If I have this many UTF-16 code units, what’s the largest number of code units that might be required to represent the same text in the target encoding?” This can produce a significant overestimate for variable-length encodings. For example, with UTF-8, GetMaxByteCount multiplies the length of the input string by three3 and adds an extra 3 bytes to deal with an edge case that can occur with surrogate characters. It produces a correct description of the worst possible case, but text containing any characters that don’t require 3 bytes in UTF-8 (i.e., any text in English or any other languages that use the Latin alphabet, and also any text using Greek, Cyrillic, Hebrew, or Arabic writing systems, for example) will require significantly less space than GetMaxByteCount predicts.

Some encodings can provide a preamble, a distinctive sequence of bytes that, if found at the start of some encoded text, indicates that you are likely to be looking at something using that encoding. This can be useful if you are trying to detect which encoding is in use when you don’t already know. The various Unicode encodings all return their encoding of the BOM as the preamble, which you can retrieve with the GetPreamble method.

The Encoding class defines instance properties offering information about the encoding. EncodingName returns a human-readable name for the encoding, but there are two more names available. The WebName property returns the standard name for the encoding registered with the Internet Assigned Numbers Authority (IANA), which manages standard names and numbers for things on the internet such as MIME types. Some protocols, such as HTTP, sometimes put encoding names into headers, and this is the text you should use in that situation. The other two names, BodyName and HeaderName, are somewhat more obscure and are used only for internet email—there are different conventions for how certain encodings are represented in the body and headers of email.

Files and Directories
The abstractions I’ve shown so far in this chapter are very general purpose in nature—you can write code that uses a Stream without needing to have any idea where the bytes it contains come from or are going to, and likewise, TextReader and TextWriter do not demand any particular origin or destination for their data. This is useful because it makes it possible to write code that can be applied in a variety of scenarios. For example, the stream-based GZipStream can compress or decompress data from a file, over a network connection, or from any other stream. However, there are occasions where you know you will be dealing with files and want access to file-specific features. This section describes the classes for working with files and the filesystem.

FileStream Class
The FileStream represents a file from the filesystem. I’ve used it a few times in passing already. It derives from Stream, so the preceding sections have already described most of what you need to know except for one aspect: when it comes to creating a FileStream, it offers several constructors offering a great deal of control.

We can supply various pieces of information when creating a new FileStream. Table 15-1 lists the various types you can supply to the constructor in addition to the path.4 The most flexible FileStream constructor takes the file path and a FileStreamOptions, which supports all possible settings. However, FileStream offers other constructor overloads taking various combinations of the types in that table, to simplify certain common scenarios.

Table 15-1. FileStream constructor argument types
Type	Purpose	Default
FileMode

Determines the behavior if the file already exists, or does not exist

Not applicable

FileAccess

Indicates whether we will we be reading, writing, or both

ReadWrite (Write if using FileMode.Append)

FileShare

Specifies our tolerance for other applications using the file at the same time

FileShare.Read

FileOptions

Various usage settings including async and cache write-through

FileOptions.None

FileStreamOptions

Combines all preceding settings and some less common ones

Not applicable

FileMode is normally5 non-optional, because FileStream needs to know whether you’re expecting to create a new file, or open an existing one. Table 15-2 shows the behaviors you can choose between.

Table 15-2. FileMode enumeration
Value	Behavior if file exists	Behavior if file does not exist
CreateNew

Throws IOException

Creates new file

Create

Replaces existing file

Creates new file

Open

Opens existing file

Throws FileNotFoundException

OpenOrCreate

Opens existing file

Creates new file

Truncate

Replaces existing file

Throws FileNotFoundException

Append

Opens existing file, setting Position to end of file

Creates new file

The FileAccess values of Read, Write, and ReadWrite are self-explanatory, but FileShare is more subtle. It doesn’t state how we intend to use the file, it states how other processes should be allowed to use the file while we have it open. For example, when using FileAccess.Write, we might specify FileShare.Read, indicating that we’re happy for other processes to read from the file, but we want to be the only ones writing. FileShare.None demands exclusive access.

The FileShare comes into play when we try to open the file—the constructor will throw an IOException if the file is already open elsewhere in a way that conflicts with our stated requirements. (There are two kinds of conflict: our specified FileShare may be incompatible with FileAccess with which the file is already open elsewhere—perhaps we’ve said FileShare.Read but some other process already has the file open with FileAccess.Write. Or our specified FileAccess may be incompatible with the FileShare with which the file is already open. Perhaps we’re asking for FileAccess.Read, but some other process has the file open with FileShare.None.) If we successfully open the file, then for as long as we keep it open, the FileAccess and FileShare we specified impose constraints on any other attempts to open the same file.

WARNING
Unix has fewer file-locking mechanisms than Windows, so these sharing semantics will often be mapped to something simpler on Linux and macOS. Also, file locks are advisory in Unix, meaning processes can simply ignore them if they want to.

While FileStream gives you control over the contents of the file, some operations you might wish to perform on files are either cumbersome or not supported at all with FileStream. For example, you can copy a file with this class, but it’s not as straightforward as it could be, and FileStream does not offer any way to delete a file. So the runtime libraries include a separate class for these kinds of operations.

File Class
The static File class provides methods for performing various operations on files. For example, the Delete method removes the named file from the filesystem. The Move method can either move or just rename a file. There are methods for retrieving information and attributes that the filesystem stores about each file, such as GetCreationTime, GetLastAccessTime, GetLastWriteTime,6 and GetAttributes. (The last of those returns a FileAttributes value, which is a flags enumeration type telling you whether the file is read only, a hidden file, a system file, and so on.) .NET 7.0 added Get/SetUnixFileMode methods to work with the mode flags present in Unix filesystems.

The Exists method lets you discover whether a file exists before you attempt to open it. You don’t strictly need this, because FileStream will throw a FileNotFound exception if you attempt to open a nonexistent file, but Exists is useful if you don’t need to do anything with the file other than determining whether it is there. If you are planning to open the file anyway, and are just trying to avoid an exception, you should be wary of this method; just because Exists returns true, that’s no guarantee that you won’t get a FileNotFound exception. It’s always possible that in between your checking for a file’s existence and attempting to open it, another process might delete the file. Alternatively, the file might be on a network share, and you might lose network connectivity. So you should always be prepared for exceptions with file access, even if you’ve attempted to avoid provoking them.

File offers many helper methods to simplify opening or creating files. The Create method simply constructs a FileStream for you, passing in suitable FileMode, FileAccess, and FileShare values. Example 15-7 shows how to use it and also shows what the equivalent code would look like without using the Create helper. The Create method provides overloads letting you specify the buffer size, FileOptions, and FileSecurity, but these still provide the other arguments for you.

Example 15-7. File.Create versus new FileStream
using (FileStream fs = File.Create("foo.bar"))
{
   ...
}

// Equivalent code without using File class
using (var fs = new FileStream("foo.bar", FileMode.Create,
                               FileAccess.ReadWrite, FileShare.None))
{
    ...
}
The File class’s OpenRead and OpenWrite methods provide similar decluttering for when you want to open an existing file for reading or open or create a file for writing. It also offers several text-oriented helpers, such as File.AppendAllText, which appends all of the text in a string to a file. This has the same effect as opening the file, wrapping it in a StreamWriter, writing the text, then closing the file again, but as Example 15-8 shows, it reduces all that to a single method call.

Example 15-8. Appending a single string to a file
File.AppendAllText(@"c:\temp\log.txt", message);
Be careful, though. This does not automatically add any end of line characters, so if you were to call AppendAllText multiple times, you’d end up with one long line in your output file, unless the strings you were using happened to contain end-of-line characters. If you want to work with lines, there’s an AppendAllLines method that takes a collection of strings and appends each as a new line to the end of a file. Example 15-9 uses this to append a full line with each call.

Example 15-9. Appending a single line to a file
static void Log(string message)
{
    File.AppendAllLines(@"c:\temp\log.txt", new[] { message });
}
Since AppendAllLines accepts an IEnumerable<string>, you can use it to append any number of lines. But it’s perfectly happy to append just one if that’s what you want. File also defines WriteAllText and WriteAllLines methods, which work in a very similar way, but if there is already a file at the specified path, these will replace it instead of appending to it.

There are also some related text-oriented methods for reading the contents of files. ReadAllText performs the equivalent of constructing a StreamReader and then calling its ReadToEnd method—it returns the entire content of the file as a single string. ReadAllBytes fetches the whole file into a byte[] array. ReadAllLines reads the whole file as a string[] array, with one element for each line in the file. ReadLines is superficially very similar. It provides access to the whole file as an IEnumerable<string> with one item for each line, but the difference is that it works lazily—unlike all the other methods I’ve described in this paragraph, it does not read the entire file into memory up front, so ReadLines would be a better choice for very large files. It not only consumes less memory, but it also enables your code to get started more quickly—you can begin to process data as soon as the first line can be read from disk, whereas none of the other methods return until they have read the whole file.

Directory Class
Just as File is a static class offering methods for performing operations with files, Directory is a static class offering methods for performing operations with directories. Some of the methods are very similar to those offered by File—there are methods to get and set the creation time, last access time, and last write time, for example, and we also get Move, Exists, and Delete methods. The latter has an overload taking a bool that, if true, will delete everything in the folder, recursively deleting any nested folders and the files they contain. Use that one carefully.

Of course, there are also directory-specific methods. GetFiles takes a directory path and returns a string[] array containing the full path of each file in that directory. Similarly, GetDirectories returns the directories inside the specified directory instead of the files. GetFileSystemEntries returns both files and folders. Each of these offers an overload that lets you specify a pattern by which to filter the results, and a third overload that takes a pattern and also a flag that lets you request recursive searching of all subfolders.

There are also methods called EnumerateFiles, EnumerateDirectories, and EnumerateFileSystemEntries, which do exactly the same thing as the three methods in the preceding paragraph, but they return IEnumerable<string>. This is a lazy enumeration, so you can start processing results immediately instead of waiting for all the results as one big array.

You can create new directories too. The CreateDirectory method takes a path and will attempt to create as many directories as are necessary to ensure that the path exists. So, if you pass C:\new\dir\here, and there is no C:\new directory, it will create three new directories: first it will create C:\new, then C:\new\dir, and then C:\new\dir\here. If the folder you ask for already exists, it doesn’t treat that as an error; it just returns without doing anything.

Path Class
The static Path class provides useful utilities for strings containing filenames. Some extract pieces from a file path, such as the containing folder name or the file extension. Some combine strings to produce new file paths. Most of these methods just perform specialized string processing and do not require the files or directories to which the paths refer to exist. However, there are a few that go beyond string manipulation. For example, Path.GetFullPath will take the current directory into account if you do not pass an absolute path as the argument. But only the methods that need to make use of real locations will do so.

The Path.Combine method deals with the fiddly issues around combining folder and filenames. If you have a folder name, C:\temp, and a filename, log.txt, passing both to Path.Combine returns C:\temp\log.txt. And it will also work if you pass C:\temp\ as the first argument, so one of the issues it deals with is working out whether it needs to supply an extra \ character. If the second path is absolute, it detects this and simply ignores the first path, so if you pass C:\temp and C:\logs\log.txt, the result will be C:\logs\log.txt. Although these may seem like trivial matters, it’s surprisingly easy to get the file path combination wrong if you try to do it yourself by concatenating strings, so you should always avoid the temptation to do that and just use Path.Combine.

Path has platform-specific behavior. On Unix-like systems, only the / character is used as a directory separator, so the various methods in Path that expect paths to contain directories will treat only / as a separator on these systems. Windows uses a \ as a separator, although it is common for / to be tolerated as a substitute, and Path follows suit. So Path​.Com⁠bine("/x/y", "/z.txt") will produce the same results on Windows and Linux, but Path.Combine(@"\x\y", @"\z.txt") will not. Also, on Windows, if a path begins with a drive letter, it is an absolute path, but Unix does not recognize drive letters. The examples in the preceding paragraph will produce strange-looking results on Linux or macOS because on those systems, all the paths will be treated as relative paths. If you remove the drive letters and replace \ with /, the results will be as you’d expect.

Serialization
The Stream, TextReader, and TextWriter types provide the ability to read and write data in files, networks, or anything else stream-like that provides a suitable concrete class. But these abstractions support only byte or text data. Suppose you have an object with several properties of various types, including some numeric types and perhaps also references to other objects, some of which might be collections. What if you wanted to write all the information in that object out to a file or over a network connection so that an object of the same type and with the same property values could be reconstituted at a later date, or on another computer at the other end of a connection?

You could do this with the abstractions shown in this chapter, but it would require a fair amount of work. You’d have to write code to read each property and write its value out to a Stream or TextWriter, and you’d need to convert the value to either binary or text. You’d also need to decide on your representation—would you just write values out in a fixed order, or would you come up with a scheme for writing name/value pairs so that you’re not stuck with an inflexible format if you need to add more properties later on? You’d also need to come up with ways to handle collections and references to other objects, and you’d need to decide what to do in the face of circular references—if two objects each refer to one another, naive code could end up getting stuck in an infinite loop.

.NET offers several solutions to this problem, each making varying trade-offs between the complexity of the scenarios they are able to support, how well they deal with versioning, and how suitable they are for interoperating with other platforms. These techniques all fall under the broad name of serialization (because they involve writing an object’s state into some form that stores data sequentially—serially—such as a Stream). Many different mechanisms have been introduced over the years in .NET, so I won’t cover all of them. I’ll just present the ones that best represent particular approaches to the problem.

BinaryReader, BinaryWriter, and BinaryPrimitives
No discussion of this area is complete without covering the BinaryReader and BinaryWriter classes, because they solve a fundamental problem that any attempt to serialize and deserialize objects must deal with: they can convert the CLR’s intrinsic types to and from streams of bytes. BinaryPrimitives does the same thing, but it is able to work with Span<byte> and related types, which are discussed in Chapter 18.

BinaryWriter is a wrapper around a writable Stream. It provides a Write method that has overloads for all of the intrinsic types except for object. So it can take a value of any of the numeric types, or the string, char, or bool types, and it writes a binary representation of that value into a Stream. It can also write arrays of type byte or char.

BinaryReader is a wrapper around a readable Stream, and it provides various methods for reading data, each corresponding to the overloads of Write provided by BinaryWriter. For example, you have ReadDouble, ReadInt32, and ReadString.

To use these types, you would create a BinaryWriter when you want to serialize some data, and write out each value you wish to store. When you later want to deserialize that data, you’d wrap a BinaryReader around a stream containing the data written with the writer, and call the relevant read methods in the exact same order that you wrote the data out in the first place.

BinaryPrimitives works slightly differently. It is designed for code that needs to minimize the number of heap allocations, so it’s not a wrapper type—it is a static class offering a wide range of methods, such as ReadInt32LittleEndian and WriteUInt16BigEndian. These take ReadOnlySpan<byte> and Span<byte> arguments, respectively, because it is designed to work directly with data wherever it may lie in memory (not necessarily wrapped in a Stream). However, the basic principle is the same: it converts between byte sequences and primitive .NET types. (Also, string handling is rather more complex: there’s no ReadString method because anything that returns a string will create a new string object on the heap, unless there’s a fixed set of possible strings that you can preallocate and hand out again and again. See Chapter 18 for more information about span types.)

These classes only solve the problem of how to represent various built-in types in binary. You are still left with the task of working out how to represent whole objects and what to do about more complex kinds of structures such as references between objects.

CLR Serialization
CLR serialization is, as the name suggests, built into the runtime itself—it is not simply a library feature. You should not use it. CLR serialization has been deprecated for a long time. Recent versions of .NET have disabled the functionality by default. (To be precise, certain types central to the operation of CLR serialization throw exceptions unless you add settings to re-enable them. This has the effect of preventing you from using CLR serialization by default, even though the underlying support mechanisms still exist in the CLR.) Microsoft has announced that it in NET 9.0 they will remove the settings that enabled you to switch it back on.

So why am I telling you about a feature that is deprecated, unavailable by default, and destined to be removed entirely? It’s because it offered a useful, distinctive capability. This meant it was widely used, and it can still be tempting to use it. (This will be possible even with .NET 9.0, because the plan is to provide a NuGet package that continues to make it available.) CLR serialization can seem like a good idea, so it’s important to know why not to use it.

The most interesting aspect of CLR serialization is that it deals directly with object references. If you serialize, say, a List<SomeType> where multiple entries in the list refer to the same object, CLR serialization will detect this, storing just one copy of that object, and when deserializing, it will re-create that one-object-many-references structure. This avoids duplication and also means circular references don’t cause problems. (Serialization systems based on the very widely used JSON format normally don’t preserve references, although the JsonSerializer described later does provide an option to do this.) Moreover, it supports cases where derived types are present—if your List<SomeType> contains a mixture of types all derived from SomeType, CLR reflection detects this. When it deserializes the list, it will create objects of the same type that were in the original list. It’s also simple to use: you just apply a single attribute ([Serializable]) to a type, and the CLR automatically handles the process of writing out all of your object’s fields during serialization, and reading them back in when deserializing.

This is powerful and easy to use. Why wouldn’t we want it?

It’s almost impossible to avoid security problems with this style of serialization. This is a consequence of the basic approach: the features I just described mean that a serialized stream describes the types of objects to create, and the values of all the fields in those objects. If you build a system that accepts serialized streams as inputs (e.g., over the network) you are enabling whoever generates those streams to create objects of any type and configuration inside your service. Security research has shown that this provides a springboard from which attackers can run whatever code they like, meaning you have effectively lost control of your system. (This is not unique to .NET by the way. Other platforms have had their own versions of this problem.) The documentation states that CLR serialization’s BinaryFormatter “is insecure and can’t be made secure,” and you will see deprecation warnings when you attempt to use it. So I’m only describing CLR serialization here because it still gets used despite Microsoft’s attempts to end it. (There’s also one technical curiosity that exists as a result of CLR serialiation. An assumption you might otherwise have made about object creation—specifically that a reference type can only be created through one of its constructors or via MemberwiseClone—turns out not be true, because objects can come into existence through deserialization without their constructors running.)

JSON
The JavaScript Object Notation, JSON, is a very widely used serialization format, and the .NET runtime libraries provide support for working with it in the System.Text.Json namespace.7 It provides three ways of working with JSON data.

The Utf8JsonReader and Utf8JsonWriter types are stream-like abstractions that represent the contents of JSON data as a sequence of elements. These can be useful if you need to process JSON documents that are too large to load into memory as a single object. They are built on the memory-efficient mechanisms described in Chapter 18, which includes a full example showing how to process JSON with these types. This is a very high-performance option, but it is not the easiest to use.

NOTE
As the names suggest, these types read and write JSON using UTF-8 encoding. This is by far the most widely used encoding for sending and storing JSON, so all of System.Text.Json is optimized for it. Because of this, performance-sensitive code should typically avoid ever obtaining a JSON document as a .NET string, because that uses UTF-16 encoding and will require conversion to UTF-8 before you can work with these APIs.

There’s also the JsonSerializer class, which converts between entire .NET objects and JSON. It requires you to define classes with a structure corresponding to the JSON.

Finally, System.Text.Json offers types that can provide a description of a JSON document’s structure. These are useful when you do not know at development time exactly what the structure of your JSON data will be, because they provide a flexible object model that can adapt to any shape of JSON data. In fact, there are two variations on this approach. We have JsonDocument, JsonElement, and related types, which provide a highly efficient read-only mechanism for inspecting a JSON document, and the more flexible but slightly less efficient JsonNode, which is writable, enabling you either to build up a description of JSON from scratch or to read in some JSON and then modify it.

JsonSerializer
JsonSerializer offers an attribute-driven serialization model in which you define one or more classes mirroring the structure of the JSON data you need to deal with, and can then convert JSON data to and from that model.

Example 15-10 shows a simple model suitable for use with JsonSerializer. As you can see, I’m not required to use any particular base class, and there are no mandatory attributes. This example uses the required keyword (new in C# 11.0) to indicate that we expect all of the properties to be set. JsonSerializer recognizes this, and will throw an exception if you try to deserialize JSON where a required property is missing.

Example 15-10. Simple JSON serialization model
public class SimpleData
{
    public required int Id { get; set; }
    public required IList<string> Names { get; set; }
    public required NestedData Location { get; set; }
    public required IDictionary<string, int> Map { get; set; }
}

public class NestedData
{
    public required string LocationName { get; set; }
    public required double Latitude { get; set; }
    public required double Longitude { get; set; }
}
Example 15-11 creates an instance of this model and then uses the JsonConvert class’s Serialize method to serialize it to a string. It also passes a second, optional, argument, a JsonSerializationOptions. I’ve used it here to indent the JSON to make it easier to read. (By default, JsonSerializer will use a more efficient layout with no unnecessary whitespace, but that is much harder to read.)

TIP
Example 15-11 puts the JsonSerializationOptions in a static field because it is inefficient to construct new options each time you deserialize. (A code analyzer built into the .NET SDK will warn you if you do that.) In applications that process JSON repeatedly, System.Text.Json caches information about the types being serialized to avoid repeating expensive work. It stores that inside the options object, which is why you should construct the settings just once and reuse them.

Example 15-11. Serializing data with JsonSerializer
private static readonly JsonSerializerOptions SerializeIndented =
    new() { WriteIndented = true };
public static string SerializeJson()
{
    var model = new SimpleData
    {
        Id = 42,
        Names = ["Bell", "Stacey", "her", "Jane"],
        Location = new NestedData
        {
            LocationName = "London",
            Latitude = 51.503209,
            Longitude = -0.119145
        },
        Map = new Dictionary<string, int>
            {
                { "Answer", 42 },
                { "FirstPrime", 2 }
            }
    };

    return JsonSerializer.Serialize(model, SerializeIndented);
}
The results look like this:

{
  "Id": 42,
  "Names": [
    "Bell",
    "Stacey",
    "her",
    "Jane"
  ],
  "Location": {
    "LocationName": "London",
    "Latitude": 51.503209,
    "Longitude": -0.119145
  },
  "Map": {
    "Answer": 42,
    "FirstPrime": 2
  }
}
As you can see, each .NET object has become a JSON object, where the name/value pairs correspond to properties in my model. Numbers and strings are represented exactly as you would expect. The IList<string> has become a JSON array, and the IDictionary<string, int> has become another JSON dictionary. I’ve used interfaces for these collections, but you can also use the concrete List<T> and Dictio⁠nary​<TKey,TValue> types. You can use ordinary arrays to represent lists if you prefer. I tend to prefer the interfaces because it leaves you free to use whatever collection types you want. (E.g., Example 15-11 initialized the Names property with a string array, but it could also have used List<string> without changing the model type.)

Converting serialized JSON back into the model is equally straightforward, as Example 15-12 shows.

Example 15-12. Deserializing data with JsonSerializer
var deserialized = JsonSerializer.Deserialize<SimpleData>(json);
Although a plain and simple model such as this will often suffice, sometimes you may need to take control over some aspects of serialization, particularly if you are working with an externally defined JSON format. For example, you might need to work with a JSON API that uses naming conventions that are different from .NET’s—camelCasing is popular but conflicts with the PascalCasing convention for .NET properties. One way to resolve this to use the JsonPropertyName attribute to specify the name to use in the JSON, as Example 15-13 shows.

Example 15-13. Controlling the JSON with JsonPropertyName attributes
public class NestedData
{
    [JsonPropertyName("locationName")]
    public required string LocationName { get; set; }

    [JsonPropertyName("latitude")]
    public required double Latitude { get; set; }

    [JsonPropertyName("longitude")]
    public required double Longitude { get; set; }
}
JsonSerializer will use the names specified in JsonPropertyName when serializing and will look for those names when deserializing. This approach gives us complete control over the .NET and JSON property names, but there is a simpler solution for this particular scenario. This kind of renaming that just changes the case of the first letter is so common that you can get JsonSerializer to do it for you. Example 15-14 constructs its JsonSerializationOptions by passing an optional argument of type JsonSerializerDefaults. By passing Json​Seri⁠ali⁠zerDefaults.Web, we get the camelCasing style without needing to use any attributes. You can achieve the same effect by setting the JsonSerializerOptions.PropertyNamingPolicy to JsonNamingPolicy.CamelCase. .NET 8.0 adds four new naming styles: KebabCaseLower (looks-like-this), KebabCaseUpper (LOOKS-LIKE-THIS), SnakeCaseLower (looks_like_this), and SnakeCaseUpper (LOOKS_LIKE_THIS).

Example 15-14. Using JsonSerializerDefaults to get camelCased property names
private static readonly JsonSerializerOptions camelCaseOptions =
    new(JsonSerializerDefaults.Web) { WriteIndented = true };
public static string AutoCamelCase(SimpleData model)
{
    return JsonSerializer.Serialize(model, camelCaseOptions);
}
The JsonSerializerOptions also provide a way to handle circular references. Suppose you want to serialize objects of type SelfRef, as shown in Example 15-15.

Example 15-15. A type supporting circular references
public class SelfRef
{
    public required string Name { get; set; }
    public SelfRef? Next { get; set; }
}
By default, if you attempt to serialize objects that refer to one another either directly or indirectly, you’ll get a JsonException reporting a possible cycle. It says “possible” because it doesn’t directly detect cycles by default—instead, JsonSerializer has a limit on the depth of any object graph that it will serialize. This is configurable through the JsonSerializerOptions.MaxDepth property, but by default the serializer will report an error if it has to go more than 64 objects deep. However, you can set the ReferenceHandler to change the behavior. Example 15-16 sets this to ReferenceHandler.Preserve, enabling it to serialize a pair of SelfRef instances that refer to each other.

Example 15-16. Serializing a type supporting circular references
private static readonly JsonSerializerOptions jsonWithRefs =
    new(JsonSerializerDefaults.Web)
    {
        WriteIndented = true,
        ReferenceHandler = ReferenceHandler.Preserve
    };
public static string SerializeWithCircularReferences()
{
    var circle = new SelfRef
    {
        Name = "Top",
        Next = new SelfRef
        {
            Name = "Bottom",
        }
    };
    circle.Next.Next = circle;
    string json = JsonSerializer.Serialize(circle, jsonWithRefs);

    return json;
}
To enable this, the JsonSerializer gives objects identifiers by adding an $id property:

{
  "$id": "1",
  "name": "Top",
  "next": {
    "$id": "2",
    "name": "Bottom",
    "next": {
      "$ref": "1"
    }
  }
}
This enables the serializer to avoid problems when it encounters a circular reference. Whenever it has to serialize a property, it checks to see whether that refers to some object that has already been written out (or is in the process of being written out). If it does, then instead of attempting to write out the object again (which in this example would cause an infinite loop, since it’ll just encounter the circular reference again and again), the serializer emits a JSON object containing a property with the special name $ref referring back to the relevant $id. This is not a universally supported form of JSON, which is why ID generation is not enabled by default.

You can control many other aspects of serialization with JsonSerializerOptions—you can define custom serialization mechanisms for data types, for example. (E.g., you might want to represent something as a DateTimeOffset in your C# code but have that become a string with a particular date-time format in the JSON.) The full details can be found in the System.Text.Json documentation.

In the examples shown so far, JsonSerializer discovers our types’ properties using the reflection API. This is convenient, but there are a couple of disadvantages to this. The first time a process uses reflection is relatively slow, so if your code runs in an environment where cold start performance (i.e. the time it takes to be able to do useful work after the process has just started) is significant, reflection can be a problem. Some cloud hosting environments don’t leave code running for very long on any single machine, so you can find that even a fairly busy service experiences a surprisingly large number of cold starts. Another problem with reflection is that it makes it harder for ahead-of-time compilation to be effective, because reflection-based serialization defers work until runtime—it can make it particularly difficult for trimming to remove unnecessary code from your build output, and might not work at all with Native AOT. For these reasons, the .NET SDK includes a code generator that can generate all of the type information required for serialization at compile time, removing any need to use reflection at runtime. Example 15-17 shows how to enable this code generation.

Example 15-17. Enabling JSON serializer code generation
[JsonSerializable(typeof(SimpleData))]
internal partial class CodeGenSerializationContext : JsonSerializerContext
{
}
Although this class appears to be empty, the partial keyword enables the code generator to supply an implementation. The generator looks for classes such as this that inherit from JsonSerializerContext, and which have at least one JsonSerializable attribute. It will emit code for each attribute, including a public property with a name matching the specified type. Example 15-18 shows how to use the property generated for SimpleData.

Example 15-18. Using JSON serializer code generation
SimpleData? data = JsonSerializer.Deserialize(
    json, CodeGenSerializationContext.Default.SimpleData);
For each JsonSerializable attribute, there will be a corresponding generated property on our serialization context class. When we pass this to JsonSerializer, it will use the type information that the code generator created, avoiding use of reflection, which can enable work to commence significantly more quickly the first time this code runs, and also making it possible to use Native AOT.

JSON DOM
Whereas JsonSerializer requires you to define one or more types representing the structure of the JSON you want to work with, System.Text.Json provides a fixed set of types that enable a more dynamic approach, and which can also support significantly more efficient JSON processing. You can build a Document Object Model (DOM) in which instances of types such as JsonElement or JsonNode represent the structure of the JSON.

System.Text.Json provides two ways to build a DOM. If you have data already in JSON form, you can use the JsonDocument class to obtain a read-only model of the JSON, in which each object, value, and array is represented as a JsonElement, and each property in an object is represented as a JsonProperty. Example 15-19 uses JsonDocument to discover all of the properties in the object at the root of the JSON by calling RootElement.EnumerateObject() on the JsonDocument. This returns a collection of JsonProperty structs.

Example 15-19. Dynamic JSON inspection with JsonDocument and JsonElement
using (JsonDocument document = JsonDocument.Parse(json))
{
    foreach (JsonProperty property in document.RootElement.EnumerateObject())
    {
        Console.WriteLine($"Property: {property.Name} ({property.Value.ValueKind})");
    }
}
Running this on the serialized document produced by earlier examples produces this output:

Property: id (Number)
Property: names (Array)
Property: location (Object)
Property: map (Object)
As this shows, we are able to discover at runtime what properties exist. The JsonProperty.Value returns a JsonElement struct, and we can inspect its ValueKind to discover which sort of JSON value it is. If it’s an array, we can enumerate its contents by calling EnumerateArray, and if it’s a string value, we can read its value by calling GetString. Example 15-20 uses these methods to show all the strings in the names property.

Example 15-20. Dynamic JSON array enumeration with JsonDocument and JsonElement
JsonElement namesElement = document.RootElement.GetProperty("names");
foreach (JsonElement name in namesElement.EnumerateArray())
{
    Console.WriteLine($"Name: {name.GetString()}");
}
As this example also shows, if you know in advance that a particular property will be present, you don’t need to use EnumerateObject to find it: you can call GetProperty. There’s also a TryGetProperty for when the property is optional. Example 15-21 uses both: this treats the root object’s location property as optional, but if it is present, it then requires the locationName, latitude, and longitude properties to be present.

Example 15-21. Reading JSON properties with JsonElement
if (root.TryGetProperty("location", out JsonElement locationElement))
{
    JsonElement nameElement = locationElement.GetProperty("locationName");
    JsonElement latitudeElement = locationElement.GetProperty("latitude");
    JsonElement longitudeElement = locationElement.GetProperty("longitude");
    string locationName = nameElement.GetString()!;
    double latitude = latitudeElement.GetDouble();
    double longitude = longitudeElement.GetDouble();
    Console.WriteLine($"Location: {locationName}: {latitude},{longitude}");
}
In addition to structural elements, objects and arrays, the data model in the JSON specification recognizes four basic data types: strings, numbers, Booleans, and null. As you’ve seen, you can discover which of these any particular JsonElement represents with its Kind property. If it’s one of the basic data types, you can use a suitable Get method. The last two examples both used GetString, and the second also used GetDouble. There are multiple methods you can use to retrieve a number: if you are expecting an integer, you can call GetSByte, GetInt16, GetInt32, or GetInt64 (and unsigned versions are also available) depending on what range of values you are expecting. There’s also GetDecimal. JsonElement also offers methods for reading string properties in particular formats: GetGuid, GetDateTime, GetDateTimeOffset, and GetBytesFromBase64.

All of the Get methods will throw an exception if the value is not in the required form, but it won’t always be the same exception. If the JSON has a type that can’t possibly contain a suitable value (e.g., you call GetGuid when the property’s value is false, or you all GetInt32 when the property is a string) it will throw InvalidOperationException. If the JSON type is appropriate but the value is not right (e.g, you called GetUInt32 but the number is negative, or is a floating point value, or you called GetDateTime and the JSON value is a string, but is not a valid ISO 8601 datetime) it will throw a FormatException instead.

Each of these Get methods is also available in a TryGet form, such as TryGetUInt32. These enable you to detect when the data cannot be parsed in the expected way without triggering an exception, although there’s a trap for the unwary: the TryGet forms will throw an InvalidOperationException in the same cases where the equivalent Get would—these only return false in cases where the equivalent Get method would have thrown a FormatException. If you want to avoid exceptions entirely, you should check the element’s ValueKind property, and only call the TryGet method if that indicates that the JSON type is what you expect.

These types attempt to minimize the amount of memory allocated. JsonElement and JsonProperty are both structs, so you can obtain these without causing additional heap allocations. The underlying data is held in UTF-8 format by the JsonDocument, and the JsonElement and JsonProperty instances just refer back to that, avoiding the need to allocate copies of the relevant data. This can make these types significantly more efficient than deserialization in some scenarios.

Obviously, the underlying data does need to live somewhere, and depending on exactly how you loaded the JSON into a JsonDocument, it may have to allocate some memory to hold it. (E.g., you can pass it a Stream, and since not all streams are rewindable, JsonDocument would need to make a copy of the stream’s contents.) JsonDocument uses the buffer pooling features available in the .NET runtime libraries to manage this data, meaning that if an application parses many JSON documents, it may be able to reuse memory, reducing pressure on the garbage collector (GC). But this means the JsonDocument needs to know when you’ve finished with the JSON so that it can return buffers to the pool. That’s why we use a using statement when working with a JsonDocument.

WARNING
Be aware that JsonElement.GetString is more expensive than all the other Get methods, because it has to create a new .NET string on the heap. The other Get methods all return value types, so they do not cause heap allocations.

I mentioned earlier that there are two ways of working with a JSON DOM. JsonDocument provides a read-only model that lets you inspect existing JSON. But there is also JsonNode, which is read/write. You can use this in a couple of ways that JsonDocument does not support. You can build up an object model from scratch to create a new JSON document. Alternatively, you can parse existing JSON into an object model just like with JsonDocument, but when you use JsonNode, the resulting model is modifiable. So you could use it to load some JSON and modify it, as Example 15-22 illustrates.

Example 15-22. Modifying JSON with JsonNode
JsonNode rootNode = JsonNode.Parse(json)!;
JsonNode mapNode = rootNode["map"]!;
mapNode["iceCream"] = 99;
This loads the JSON text in json into a JsonNode and then retrieves the map property. (This example expects to work with JSON in the same form as I’ve used in the preceding examples, with camelCased property names.) So far this doesn’t do anything we couldn’t do with JsonDocument. But the final line adds a new entry to the object in map. It’s this ability to modify the document that makes JsonNode more powerful. So why do we need JsonDocument if JsonNode is more powerful? The power comes at a price: JsonNode is less efficient, so if you don’t need the extra flexibility, you shouldn’t use it.

An advantage of using either the read-only JsonDocument and JsonElement or the writable JsonNode is that you don’t need to define any types to model the data. They also make it easier to write code whose behavior is driven by the structure of the data, because these APIs are able to describe what they find. The read-only form is typically more efficient than JsonSerializer, because it may enable you to cause fewer object allocations when reading data from a JSON document.

Summary
The Stream class is an abstraction representing data as a sequence of bytes. A stream can support reading, writing, or both, and may support seeking to arbitrary offsets as well as straightforward sequential access. TextReader and TextWriter provide strictly sequential reading and writing of character data, abstracting away the character encoding. These types may sit on top of a file, a network connection, or memory, or you could implement your own versions of these abstract classes. The FileStream class also provides some other filesystem access features, but for full control, we also have the File and Directory classes. When bytes and strings aren’t enough, .NET offers various serialization mechanisms that can automate the mapping between an object’s state in memory and a representation that can be written out to disk or sent over the network or any other stream-like target; this representation can later be turned back into an object of the same type and with equivalent state.

As you’ve seen, a few of the file and stream APIs offer asynchronous forms that can help improve performance, particularly in highly concurrent systems. The next chapter tackles concurrency, parallelism, and the task-based pattern that the asynchronous forms of these APIs use.

1 You might have thought that the pound sign was #, but if, like me, you’re British, that’s just not on. It would be like someone insisting on referring to @ as a dollar sign. Unicode’s canonical name for # is number sign, and it also allows my preferred option, hash, as well as octothorpe, crosshatch, and, regrettably, pound sign.

2 Just in case you’ve not come across the term, in little-endian representations, multibyte values start with the lower-order bytes, so the value 0x1234 in 16-bit little-endian would be 0x34, 0x12, whereas the big-endian version would be 0x12, 0x34. Little-endian looks reversed, but it’s the native format for Intel’s processors.

3 Some Unicode characters can take up to 4 bytes in UTF-8, so multiplying by three might seem like it could underestimate. However, all such characters require two code units in UTF-16. Any single char in .NET will never require more than 3 bytes in UTF-8.

4 Although FileStream normally opens the file, there are constructors that accept a file handle.

5 FileMode only comes into play at the instant when a file is opened, so you don’t need it with the constructors that accept a file handle.

6 These all return a DateTime that is relative to the computer’s current time zone. Each of these methods has an equivalent that returns the time relative to time zone zero (e.g., GetCreationTimeUtc).

7 To use this on .NET Framework, you will need to add a reference to the System.Text.Json NuGet package.


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


15. Files and Streams
16. Multithreading
17. Asynchronous Language Features
24h 20m remaining
Chapter 16. Multithreading
Multithreading enables an application to execute several pieces of code simultaneously. There are two common reasons for doing this. One is to exploit the computer’s parallel processing capabilities—multicore CPUs are now more or less ubiquitous, and to realize their full performance potential, you’ll need to provide the CPU with multiple streams of work to give all of the cores something useful to do. The other usual reason for writing multithreaded code is to prevent progress from grinding to a halt when you do something slow, such as reading from disk.

Multithreading is not the only way to solve that second problem—asynchronous techniques can be preferable. C# has features for supporting asynchronous work. Asynchronous execution doesn’t necessarily mean multithreading, but the two are often related in practice, and I will be describing some of the asynchronous programming models in this chapter. However, this chapter focuses on the threading foundations. I will describe the language-level support for asynchronous code in Chapter 17.

Threads
All the operating systems that .NET can run on allow each process to contain multiple threads (although if you build to Web Assembly and run code in the browser, that particular environment currently doesn’t support creation of new threads). Each thread has its own stack, and the OS presents the illusion that a thread gets a whole CPU hardware thread to itself. (See the sidebar, “Processors, Cores, and Hardware Threads”.) You can create far more OS threads than the number of hardware threads your computer provides, because the OS virtualizes the CPU, context switching from one thread to another. The computer I’m using as I write this has 16 hardware threads, which is a reasonably generous quantity but some way short of the 8,893 threads currently active across the various processes running on my machine.

PROCESSORS, CORES, AND HARDWARE THREADS
A hardware thread is one piece of hardware capable of executing code. Back in the early 2000s, one processor chip gave you one hardware thread, and you got multiple hardware threads only in computers that had multiple, physically separate CPUs plugged into separate sockets on the motherboard. However, two inventions have made the relationship between hardware and threads more complex: multicore CPUs and hyperthreading.

With a multicore CPU, you effectively get multiple processors on a single piece of silicon. This means that opening up your computer and counting the number of processor chips doesn’t necessarily tell you how many hardware threads you’ve got. But if you were to inspect the CPU’s silicon with a suitable microscope, you’d see two or more distinct processors next to each other on the chip.

Hyperthreading, also known as simultaneous multithreading (SMT), complicates matters further. A hyperthreaded core is a single processor that has two sets of certain parts. (It could be more than two, but doubling seems most common.) So, although there might be only a single part of the core capable of performing, say, floating-point division, there will be two sets of registers. Each set of registers includes an instruction pointer (IP) register that keeps track of where execution has reached. Registers also contain the immediate working state of the code, so by having two sets, a single core can run code from two places at once—in other words, hyperthreading enables a single core to provide two hardware threads. Since only certain parts of the CPU are doubled up, two execution contexts have to share some resources—they can’t both perform floating-point division operations simultaneously, because there’s only one piece of hardware in the core to do that. However, if one of the hardware threads wants to do some division while another multiplies two numbers together, they will typically be able to do so in parallel, because those operations are performed by different areas of the core. Hyperthreading enables more parts of a single CPU core to be kept busy simultaneously. It doesn’t give you quite the same throughput as two full cores (because if the two hardware threads both want to do the same kind of work at once, one of them will have to wait), but it can often provide better throughput from each core than would otherwise be possible.

In a hyperthreaded system, the total number of hardware threads available is the number of cores multiplied by the number of hyperthreaded execution units per core. For example, the Intel Core i9-9900K processor has 8 cores with two-way hyperthreading, giving a total of 16 hardware threads.

The CLR presents its own threading abstraction on top of OS threads. In .NET, there is always a direct relationship—each Thread object corresponds directly to some particular underlying OS thread. On .NET Framework, this relationship is not guaranteed to exist—applications that use the CLR’s unmanaged hosting API to customize the relationship between the CLR and its containing process can in theory cause a CLR thread to move between different OS threads. In practice, this capability is very rarely used, so even on .NET Framework, each CLR thread will usually correspond to one OS thread.

I will get to the Thread class shortly, but before writing multithreaded code, you need to understand the ground rules for managing state1 when using multiple threads.

Threads, Variables, and Shared State
Each CLR thread gets various thread-specific resources, such as the call stack (which holds method arguments and some local variables). Because each thread has its own stack, the local variables that end up there will be local to the thread. Each time you invoke a method, you get a new set of its local variables. Recursion relies on this, but it’s also important in multithreaded code, because data that is accessible to multiple threads requires much more care, particularly if that data changes. Coordinating access to shared data is complex. I’ll be describing some of the techniques for that in the section “Synchronization”, but it’s better to avoid the problem entirely where possible, and the thread-local nature of the stack can be a great help.

For example, consider a web-based application. Busy sites have to handle requests from multiple users simultaneously. ASP.NET Core uses multithreading to support this, so you’re likely to end up in a situation where a particular piece of code (e.g., the code for your site’s home page) is being executed simultaneously on several different threads. (Websites typically don’t just serve up the exact same content every time, because pages are often tailored to particular users, so if 1,000 users ask to see the home page, it will run the code that generates that page 1,000 times.) ASP.NET Core provides you with various objects that your code will need to use, but most of these are specific to a particular request. So, if your code is able to work entirely with those objects and with local variables, each thread can operate completely independently. If you need shared state (such as objects that are visible to multiple threads, perhaps through a static field or property), life will get more difficult, but local variables are usually straightforward.

Why only “usually”? Things get more complex if you use lambdas or anonymous functions, because they make it possible to declare a variable in a containing method and then use that in an inner method. This variable is now available to two or more methods, and with multithreading, it’s possible that these methods could execute concurrently. (As far as the CLR is concerned, it’s not really a local variable anymore—it’s a field in a compiler-generated class.) Sharing local variables across multiple methods removes the guarantee of complete locality, so you need to take the same sort of care with such variables as you would with more obviously shared items, like static properties and fields.

Another important point to remember in multithreaded environments is the distinction between a variable and the object it refers to. (This is an issue only with reference type variables.) Although a local variable is accessible only inside its declaring method, that variable may not be the only one that refers to a particular object. Sometimes it will be—if you create the object inside the method and never store it anywhere that would make it accessible to a wider audience, then you have nothing to worry about. The StringBuilder that Example 16-1 creates is only ever used within the method that creates it.

Example 16-1. Object visibility and methods
public static string FormatDictionary<TKey, TValue>(
    IDictionary<TKey, TValue> input)
{
    var sb = new StringBuilder();
    foreach ((TKey key, TValue value) in input)
    {
        sb.Append($"{key}: {value}");
        sb.AppendLine();
    }

    return sb.ToString();
}
This code does not need to worry about whether other threads might be trying to modify the StringBuilder. There are no nested methods here, so the sb variable is truly local, and that’s the only thing that contains a reference to the StringBuilder. (This relies on the fact that the StringBuilder doesn’t sneakily store copies of its this reference anywhere that other threads might be able to see.)

But what about the input argument? That’s also local to the method, but the object it refers to is not: the code that calls FormatDictionary gets to decide what input refers to. Looking at Example 16-1 in isolation, it’s not possible to say whether the dictionary object to which it refers is currently in use by other threads. The calling code could create a single dictionary and then create two threads, and have one modify the dictionary while the other calls this FormatDictionary method. This would cause a problem: most dictionary implementations do not support being modified on one thread at the same time as being used on some other thread. And even if you were working with a collection that was designed to cope with concurrent use, you’re often not allowed to modify a collection while an enumeration of its contents is in progress (e.g., a foreach loop).

You might think that any collection designed to be used from multiple threads simultaneously (a thread-safe collection, you might say) should allow one thread to iterate over its contents while another modifies the contents. If it disallows this, then in what sense is it thread safe? In fact, the main difference between a thread-safe and a non-thread-safe collection in this scenario is predictability: whereas a thread-safe collection might throw an exception when it detects that this has happened, a non-thread-safe collection does not guarantee to do anything in particular. It might crash, or you might start getting perplexing results from the iteration, such as a single entry appearing multiple times. It could do more or less anything because you’re using it in an unsupported way. Sometimes, thread safety just means that failure happens in a well-defined and predictable manner.

As it happens, the various collections in the System.Collection.Concurrent namespace do in fact support changes while enumeration is in progress without throwing exceptions. However, they often have a different API from the other collection classes specifically to support concurrency, so they are not always drop-in replacements.

There’s nothing Example 16-1 can do to ensure that it uses its input argument safely in multithreaded environments, because it is at the mercy of its callers. Concurrency hazards need to be dealt with at a higher level. In fact, the term thread safe is potentially misleading, because it suggests something that is not, in general, possible. Inexperienced developers often fall into the trap of thinking that they are absolved of all responsibility for thinking about threading issues in their code by just making sure that all the objects they’re using are thread safe. This usually doesn’t work, because while individual thread-safe objects will maintain their own integrity, that’s no guarantee that your application’s state as a whole will be coherent.

To illustrate this, Example 16-2 uses the ConcurrentDictionary<TKey, TValue> class from the System.Collections.Concurrent namespace. Every operation this class defines is thread safe in the sense that each will leave the object in a consistent state and will produce the expected result given the collection’s state prior to the call. However, this example contrives to use it in a non-thread-safe fashion.

Example 16-2. Non-thread-safe use of a thread-safe collection
static string UseDictionary(ConcurrentDictionary<int, string> cd)
{
    cd[1] = "One";
    return cd[1];
}
This seems like it could not fail. (It also seems pointless; that’s just to show how even a very simple piece of code can go wrong.) But if the dictionary instance is being used by multiple threads (which seems likely, given that we’ve chosen a type designed specifically for multithreaded use), it’s entirely possible that in between setting a value for key 1 and trying to retrieve it, some other thread will have removed that entry. If I put this code into a program that repeatedly runs this method on several threads, but that also has several other threads busily removing the very same entry, I eventually see a KeyNotFoundException.

Concurrent systems need a top-down strategy to ensure system-wide consistency. (This is why database management systems often group sets of operations together as transactions, atomic units of work that either succeed completely or have no effect at all.) Looking at Example 16-1, this means that it is the responsibility of code that calls FormatDictionary to ensure that the dictionary can be used freely for the duration of the method.

WARNING
Although calling code should guarantee that whatever objects it passes are safe to use for the duration of a method call, you cannot in general assume that it’s OK to hold on to references to your arguments for future use. Anonymous functions and delegates make it easy to do this accidentally—if a nested method refers to its containing method’s arguments, and if that nested method runs after the containing method returns, it may no longer be safe to assume that you’re allowed to access the objects to which the arguments refer. If you need to do this, you will need to document the assumptions you’re making about when you can use objects, and inspect any code that calls the method to make sure that these assumptions are valid.

Thread-Local Storage
Sometimes it can be useful to maintain thread-local state at a broader scope than a single method. Various parts of the runtime libraries do this. For example, the System.Transactions namespace defines an API for using transactions with databases, message queues, and any other resource managers that support them. It provides an implicit model where you can start an ambient transaction, and any operations that support this will enlist in it without you needing to pass any explicit transaction-related arguments. (It also supports an explicit model, should you prefer that.) The Transaction class’s static Current property returns the ambient transaction for the current thread, or it returns null if the thread currently has no ambient transaction in progress.

To support this sort of per-thread state, .NET offers the ThreadLocal<T> class. Example 16-3 uses this to provide a wrapper around a delegate that allows only a single call into the delegate to be in progress on any one thread at any time.

Example 16-3. Using ThreadLocal<T>
public class Notifier(Action callback)
{
    private readonly ThreadLocal<bool> _isCallbackInProgress = new();

    public void Notify()
    {
        if (_isCallbackInProgress.Value)
        {
            throw new InvalidOperationException(
                "Notification already in progress on this thread");
        }

        try
        {
            _isCallbackInProgress.Value = true;
            callback();
        }
        finally
        {
            _isCallbackInProgress.Value = false;
        }
    }
}
If the method that Notify calls back attempts to make another call to Notify, this will block that attempt at recursion by throwing an exception. However, because it uses a ThreadLocal<bool> to track whether a call is in progress, this will allow simultaneous calls as long as each call happens on a separate thread.

You get and set the value that ThreadLocal<T> holds for the current thread through the Value property. The constructor is overloaded, and you can pass a Func<T> that will be called back each time a new thread first tries to retrieve the value to create a default initial value. (The initialization is lazy—the callback won’t run every time a new thread starts. A ThreadLocal<T> invokes the callback only the first time a thread attempts to use the value.) There is no fixed limit to the number of ThreadLocal<T> objects you can create.

There’s one thing you need to be careful about with thread-local storage. If you create a new object for each thread, be aware that an application might create a large number of threads over its lifetime, especially if you use the thread pool (which is described in detail later). If the per-thread objects you create are expensive, this might cause problems. Furthermore, if there are any disposable per-thread resources, you will not necessarily know when a thread terminates; the thread pool regularly creates and destroys threads without telling you when it does so.

If you don’t need the automatic creation each time a new thread first uses thread-local storage, you can instead just annotate a static field with the [ThreadStatic] attribute. This is handled by the CLR: it effectively means that each thread that accesses this field gets its own distinct field. This can reduce the number of objects that need to be allocated. But be careful: it’s possible to define a field initializer for such fields, but that initializer will run only for the first thread to access the field. For other threads using the same [ThreadStatic], the field will initially contain the default zero-like value for the field’s type.

One last note of caution: be wary of thread-local storage (and any mechanism based on it) if you plan to use the asynchronous language features described in Chapter 17, because those make it possible for a single invocation of a method to use multiple different threads as it progresses. This would make it a bad idea for that sort of method to use ambient transactions, or anything else that relies on thread-local state. Many .NET features that you might think would use thread-local storage (e.g., the ASP.NET Core framework’s static HttpContext.Current property, which returns an object relating to the HTTP request that the current thread is handling) turn out to associate information with something called the execution context instead. An execution context is more flexible, because it can hop across threads when required. I’ll be describing it later.

For the issues I’ve just discussed to be relevant, we’ll need to have multiple threads. There are four main ways to use multithreading. In one, the code runs in a framework that creates multiple threads on your behalf, such as ASP.NET Core. Another is to use certain kinds of callback-based APIs. A few common patterns for this are described in “Tasks” and “Other Asynchronous Patterns”. But the two most direct ways to use threads are to create new threads explicitly or to use the .NET thread pool.

The Thread Class
As I mentioned earlier, the Thread class (defined in the System.Threading namespace) represents a CLR thread. You can obtain a reference to the Thread object representing the thread that’s executing your code with the Thread.CurrentThread property, but if you’re looking to introduce some multithreading, you can construct a new Thread object.

A new thread needs to know what code it should run when it starts, so you must provide a delegate, and the thread will invoke the method the delegate refers to when it starts. The thread will run until that method returns normally, or allows an exception to propagate all the way to the top of the stack (or the thread is forcibly terminated through any of the OS mechanisms for killing threads or their containing processes). Example 16-4 creates three threads to download the contents of three web pages simultaneously. It uses a single HttpClient instance to do this, which is OK because that type is designed to be used concurrently from multiple threads.

Example 16-4. Creating threads
internal static class Program
{
    private static readonly HttpClient http = new();

    private static void Main()
    {
        Thread t1 = new(MyThreadEntryPoint);
        Thread t2 = new(MyThreadEntryPoint);
        Thread t3 = new(MyThreadEntryPoint);

        t1.Start("https://endjin.com/");
        t2.Start("https://oreilly.com/");
        t3.Start("https://dotnet.microsoft.com/");
    }

    private static void MyThreadEntryPoint(object? arg)
    {
        string url = (string)arg!;

        Console.WriteLine($"Downloading {url}");
        var response = http.Send(new HttpRequestMessage(HttpMethod.Get, url));
        using StreamReader r = new(response.Content.ReadAsStream());
        string page = r.ReadToEnd();
        Console.WriteLine($"Downloaded {url}, length {page.Length}");
    }
}
The Thread constructor is overloaded and accepts two delegate types. The ThreadStart delegate requires a method that takes no arguments and returns no value, but in Example 16-4, the MyThreadEntryPoint method takes a single object argument, which matches the other delegate type, ParameterizedThreadStart. This provides a way to pass an argument to each thread, which is useful if you’re invoking the same method on several different threads, as this example does. The thread will not run until you call Start, and if you’re using the ParameterizedThreadStart delegate type, you must call the overload that takes a single object argument. I’m using this to make each thread download from a different URL.

There are two more overloads of the Thread constructor, each adding an int argument after the delegate argument. This int specifies the size of stack for the thread. Current .NET implementations require stacks to be contiguous in memory, making it necessary to preallocate address space for the stack. If a thread exhausts this space, the CLR throws a StackOverflowException. (You normally see those only when a bug causes infinite recursion.) Without this argument, the CLR will use the default stack size for the process. (This varies by OS; on Windows it will usually be 1 MB.) You can change it by setting the DOTNET_DefaultStackSize environment variable. Note that it interprets the value as a hexadecimal number. It’s rare to need to change this but not unheard of. If you have recursive code that produces very deep stacks, you might need to run it on a thread with a larger stack. Conversely, if you’re creating huge numbers of threads, you might want to reduce the stack size to conserve resources, because the default of 1 MB is usually considerably more than is really required. However, it’s usually not a great idea to create such a large number of threads. So, in most cases, you will create only a moderate number of threads and just use the constructors that use the default stack size.

Notice that the Main method in Example 16-4 returns immediately after starting the three threads. Despite this, the application continues to run—it will run until all the threads finish. The CLR keeps the process alive until there are no foreground threads running, where a foreground thread is defined to be any thread that hasn’t explicitly been designated as a background thread. If you want to prevent a particular thread from keeping the process running, set its IsBackground property to true. (This means that background threads may be terminated while they’re in the middle of doing something, so you need to be careful about what kind of work you do on these threads.)

Creating threads directly is not the only option. The thread pool provides a commonly used alternative.

The Thread Pool
On most operating systems, it is relatively expensive to create and shut down threads. If you need to perform a fairly short piece of work (such as serving up a web page or some similarly brief operation), it would be a bad idea to create a thread just for that job and to shut it down when the work completes. There are two serious problems with this strategy: first, you may end up expending more resources on the startup and shutdown costs than on useful work; second, if you keep creating new threads as more work comes in, the system may bog down under load—with heavy workloads, creating ever more threads will tend to reduce throughput. This is because, in addition to basic per-thread overheads such as the memory required for the stack, the OS needs to switch regularly between runnable threads to enable them all to make progress, and this switching has its own overheads.

To avoid these problems, .NET provides a thread pool. You can supply a delegate that the runtime will invoke on a thread from the pool. If necessary, it will create a new thread, but where possible, it will reuse one it created earlier, and it might make your work wait in a queue if all the threads created so far are busy. After your method runs, the CLR will not normally terminate the thread; instead, the thread will stay in the pool waiting for other work items, which amortizes the cost of creating the thread over multiple work items. It will create new threads if necessary, but it tries to keep the thread count at a level that results in the number of runnable threads matching the hardware thread count, to minimize switching costs.

WARNING
The thread pool always creates background threads, so if it has work in progress when the last foreground thread in your process exits, that work will not complete, because all background threads will be terminated at that point. If you need to ensure that work being done on the thread pool completes, you must wait for that to happen before allowing all foreground threads to finish.

Launching thread pool work with Task
The usual way to use the thread pool is through the Task class. This is part of the Task Parallel Library (discussed in more detail in “Tasks”), but its basic usage is pretty straightforward, as Example 16-5 shows.

Example 16-5. Running code on the thread pool with a Task
Task.Run(() => MyThreadEntryPoint("https://oreilly.com/"));
This queues the lambda for execution on the thread pool (which, when it runs, just calls the MyThreadEntryPoint method from Example 16-4). If a thread is available, it will start to run straightaway, but if not, it will wait in a queue until a thread becomes available (either because some other work item in progress completes or because the thread pool decides to add a new thread to the pool).

There are other ways to use the thread pool, the most obvious of which is through the ThreadPool class. Its QueueUserWorkItem method works in a similar way to Start—you pass it a delegate and it will queue the method for execution. This is a lower-level API—it does not provide any direct way to handle completion of the work, nor to chain operations together, so for most cases, the Task class is preferable.

Thread creation heuristics
The runtime adjusts the number of threads based on the workload you present. The heuristics it uses are not documented and have changed across releases of .NET, so you should not depend on the exact behavior I’m about to describe; however, it is useful to know roughly what to expect.

If you give the thread pool only CPU-bound work, in which every method you ask it to execute spends its entire time performing computations and never blocks waiting for I/O to complete, you might end up with one thread for each of the hardware threads in your system (although if the individual work items take long enough, the thread pool might decide to allocate more threads). For example, on the eight-core two-way hyperthreaded computer I’m using as I write this, queuing up a load of CPU-intensive work items initially causes the CLR to create 16 thread pool threads, and as long as the work items complete about once a second or faster, the number of threads mostly stays at that level. (It occasionally goes over that because the runtime will try adding an extra thread from time to time to see what effect this has on throughput, and then it drops back down again.) But if the rate at which the program gets through items drops, the CLR gradually increases the thread count.

If thread pool threads get blocked (e.g., because they’re waiting for data from disk or for a response over the network from a server), the CLR increases the number of pool threads more quickly. Again, it starts off with one per hardware thread, but when slow work items consume very little processor time, it will try adding threads to improve throughput.

In either case, the CLR will eventually stop adding threads. The exact default limit varies in 32-bit processes, depending on the version of .NET, although it’s typically on the order of 1,000 threads. In 64-bit mode, it appears to default to 32,767. You can change this limit—the ThreadPool class has a SetMaxThreads method that lets you configure different limits for your process. You may run into other limitations that place a lower practical limit. For example, each thread has its own stack that has to occupy a contiguous range of virtual address space. If each thread gets 1 MB of the process’s address space reserved for its stack, by the time you have 1,000 threads, you’ll be using 1 GB of address space for stacks alone. Thirty-two-bit processes have only 4 GB of address range, so you might not have space for the number of threads you request. In any case, 1,000 threads is usually more than is helpful, so if it gets that high, this may be a symptom of some underlying problem that you should investigate. For this reason, if you call SetMaxThreads, it will normally be to specify a lower limit—you may find that with some workloads, constraining the number of threads improves throughput by reducing the level of contention for system resources.

ThreadPool also has a SetMinThreads method. This lets you ensure that the number of threads does not drop below a certain number. This can be useful in applications that work most efficiently with some minimum number of threads and that want to be able to operate at maximum speed instantly, without waiting for the thread pool’s heuristics to adjust the thread count.

Thread Affinity and SynchronizationContext
Some objects demand that you use them only from certain threads. This is particularly common with UI code—the WPF, .NET MAUI, and Windows Forms UI frameworks require that UI objects be used from the thread on which they were created. This is called thread affinity, and although it is most often a UI concern, it can also crop up in interoperability scenarios—some COM objects have thread affinity.

Thread affinity can make life awkward if you want to write multithreaded code. Suppose you’ve carefully implemented a multithreaded algorithm that can exploit all of the hardware threads in an end user’s computer, significantly improving performance when running on a multicore CPU compared to a single-threaded algorithm. Once the algorithm completes, you may want to present the results to the end user. The thread affinity of UI objects requires you to perform that final step on a particular thread, but your multithreaded code may well produce its final results on some other thread. (In fact, you will probably have avoided the UI thread entirely for the CPU-intensive work, to make sure that the UI remained responsive while the work was in progress.) If you try to update the UI from some random worker thread, the UI framework will throw an exception complaining that you’ve violated its thread affinity requirements. Somehow, you’ll need to pass a message back to the UI thread so that it can display the results.

The runtime libraries provide the SynchronizationContext class to help in these scenarios. Its Current static property returns an instance of the Synchronization​Con⁠text class that represents the context in which your code is currently running. For example, in a WPF application, if you retrieve this property while running on a UI thread, it will return an object associated with that thread. You can store the object that Current returns and use it from any thread anytime you need to perform further work on the UI thread. Example 16-6 does this so that it can perform some potentially slow work on a thread pool thread and then update the UI back on the UI thread.

Example 16-6. Using the thread pool and then SynchronizationContext

private void findButton_Click(object sender, RoutedEventArgs e)
{
    SynchronizationContext uiContext = SynchronizationContext.Current!;

    Task.Run(() =>
    {
        string pictures =
            Environment.GetFolderPath(Environment.SpecialFolder.MyPictures);
        var folder = new DirectoryInfo(pictures);
        FileInfo[] allFiles =
            folder.GetFiles("*.jpg", SearchOption.AllDirectories);
        FileInfo? largest =
            allFiles.OrderByDescending(f => f.Length).FirstOrDefault();

        if (largest is not null)
        {
            uiContext.Post(_ =>
            {
                long sizeMB = largest.Length / (1024 * 1024);
                outputTextBox.Text =
                    $"Largest file ({sizeMB}MB) is {largest.FullName}";
            },
            null);
        }
    });
}
This code handles a Click event for a button. (It happens to be a WPF application, but SynchronizationContext works in exactly the same way in other client-side UI frameworks, such as .NET MAUI.) UI elements raise their events on the UI thread, so when the first line of the click handler retrieves the current SynchronizationContext, it will get the context for the UI thread. The code then runs some work on a thread pool thread via the Task class. The code looks at every picture in the user’s Pictures folder, searching for the largest file, so this could take a while. It’s a bad idea to perform slow work on a UI thread—UI elements that belong to that thread cannot respond to user input while the UI thread is busy doing something else. So pushing this into the thread pool is a good idea.

The problem with using the thread pool here is that once the work completes, we’re on the wrong thread to update the UI. This code updates the Text property of a text box, and we’d get an exception if we tried that from a thread pool thread. So, when the work completes, it uses the SynchronizationContext object it retrieved earlier and calls its Post method. That method accepts a delegate, and it will arrange to invoke that back on the UI thread. (Under the covers, it posts a custom message to the Windows message queue, and when the UI thread’s main message processing loop picks up that message, it will invoke the delegate.)

TIP
The Post method does not wait for the work to complete. There is a method that will wait, called Send, but you should avoid it. Making a worker thread block while it waits for the UI thread to do something can be risky, because if the UI thread is currently blocked waiting for the worker thread to do something, the application will deadlock. Post avoids this problem by enabling the worker thread to proceed concurrently with the UI thread.

Example 16-6 retrieves SynchronizationContext.Current while it’s still on the UI thread, before it starts the thread pool work. This is important because this static property is context sensitive—it returns the context for the UI thread only while you’re on the UI thread. (In fact, it’s possible for each window to have its own UI thread in WPF, so it wouldn’t be possible to have an API that returns the UI thread—there might be several.) If you read this property from a thread pool thread, the context object it returns will not post work to the UI thread.

The SynchronizationContext mechanism is extensible, so you can derive your own type from it if you want, and you can call its static SetSynchronizationContext method to make your context the current context for the thread. This can be useful in unit testing scenarios—it enables you to write tests to verify that objects interact with the SynchronizationContext correctly without needing to create a real UI.

ExecutionContext
The SynchronizationContext class has a cousin, ExecutionContext. This provides a similar service, allowing you to capture the current context and then use it to run a delegate sometime later in the same context, but it differs in two ways. First, it captures different things. Second, it uses a different approach for reestablishing the context. A SynchronizationContext will often run your work on some particular thread, whereas ExecutionContext will always use your thread, and it just makes sure that all of the contextual information it has captured is available on that thread. One way to think of the difference is that SynchronizationContext does the work in an existing context, whereas ExecutionContext brings the contextual information to you.

You retrieve the current context by calling the ExecutionContext.Capture method. The execution context does not capture thread-local storage, but it does include any information in the current logical call context. You can access this through the CallContext class, which provides LogicalSetData and LogicalGetData methods to store and retrieve name/value pairs, or through the higher-level wrapper Async​Lo⁠cal<T>. This information is usually associated with the current thread, but if you run code in a captured execution context, it will make information from the logical context available, even if that code runs on some other thread entirely.

.NET uses the ExecutionContext class internally whenever long-running work that starts on one thread later ends up continuing on a different thread (as happens with some of the asynchronous patterns described later in this chapter). You may want to use the execution context in a similar way if you write any code that accepts a callback that it will invoke later, perhaps from some other thread. To do this, you call Capture to grab the current context, which you can later pass to the Run method to invoke a delegate. Example 16-7 shows ExecutionContext at work.

Example 16-7. Using ExecutionContext
public class Defer(Action callback)
{
    private readonly ExecutionContext? _context = ExecutionContext.Capture()!;

    public void Run()
    {
        if (_context is null) { callback(); return; }
        // When ExecutionContext.Run invokes the lambda we supply as the 2nd
        // argument, it passes that lambda the value we supplied as the 3rd
        // argument to Run. Here we're passing callback, so the lambda has
        // access to the Action we want to invoke. It would have been simpler
        // to write "_ => callback()", but the lambda would then need to
        // capture 'this' to be able to access callback, and that capture
        // would cause an additional allocation. Using the static keyword
        // on the lambda tells the compiler that we intend to avoid capture,
        // so it would report an error if we accidentally used any locals.
        ExecutionContext.Run(
            _context,
            static (cb) => ((Action)cb!)(),
            callback);
    }
}
In .NET Framework, a single captured ExecutionContext cannot be used on multiple threads simultaneously. Sometimes you might need to invoke multiple different methods in a particular context, and in a multithreaded environment, you might not be able to guarantee that the previous method has returned before calling the next. For this scenario, ExecutionContext provides a CreateCopy method that generates a copy of the context, enabling you to make multiple simultaneous calls through equivalent contexts. In .NET, ExecutionContext is immutable, meaning this restriction no longer applies, and CreateCopy just returns its this reference.

Synchronization
Sometimes you will want to write multithreaded code in which multiple threads have access to the same state. For example, in Chapter 5, I suggested that a server could use a Dictionary<TKey, TValue> as part of a cache to avoid duplicating work when it receives multiple similar requests. While this sort of caching can offer significant performance benefits in some scenarios, it presents a challenge in a multithreaded environment. (And if you’re working on server code with demanding performance requirements, you will most likely need more than one thread to handle requests.) The Thread Safety section of the documentation for the Dictionary<TKey, TValue> class says this:

A Dictionary<TKey, TValue> can support multiple readers concurrently, as long as the collection is not modified. Even so, enumerating through a collection is intrinsically not a thread-safe procedure. In the rare case where an enumeration contends with write accesses, the collection must be locked during the entire enumeration. To allow the collection to be accessed by multiple threads for reading and writing, you must implement your own synchronization.

This is better than we might expect—the vast majority of types in the runtime libraries simply don’t support multithreaded use of instances at all. Most types support multithreaded use at the class level, but individual instances must be used one thread at a time. Dictionary<TKey, TValue> is more generous: it explicitly supports multiple concurrent readers, which sounds good for our caching scenario. However, when modifying a collection, not only must we ensure that we do not try to change it from multiple threads simultaneously, but also we must not have any read operations in progress while we do so.

The other generic collection classes make similar guarantees (unlike most other classes in the library). For example, List<T>, Queue<T>, Stack<T>, SortedDiction⁠ary​<TKey, TValue>, HashSet<T>, and SortedSet<T> all support concurrent read-only use. (Again, if you modify any instance of these collections, you must make sure that no other threads are either modifying or reading from the same instance at the same time.) Of course, you should always check the documentation before attempting multithreaded use of any type.2 Be aware that the generic collection interface types make no thread safety guarantees—although List<T> supports concurrent readers, not all implementations of IList<T> will. (For example, imagine an implementation that wraps something potentially slow, such as the contents of a file. It might make sense for this wrapper to cache data to make read operations faster. Reading an item from such a list could change its internal state, so reads could fail when performed simultaneously from multiple threads if the code did not take steps to protect itself.)

If you can arrange never to have to modify a data structure while it is in use from multithreaded code, the support for concurrent access offered by many of the collection classes may be all you need. But if some threads will need to modify shared state, you will need to coordinate access to that state. To enable this, .NET provides various synchronization mechanisms that you can use to ensure that your threads take it in turns to access shared objects when necessary. In this section, I’ll describe the most commonly used ones.

Monitors and the lock Keyword
The first option to consider for synchronizing multithreaded use of shared state is the Monitor class. This is popular because it is efficient, it offers a straightforward model, and C# provides direct language support, making it very easy to use. Example 16-8 shows a class that uses the lock keyword (which in turn uses the Monitor class) anytime it either reads or modifies its internal state. This ensures that only one thread will be accessing that state at any one time.

Example 16-8. Protecting state with lock
public class SaleLog
{
    private readonly object _sync = new();
    private decimal _total;
    private readonly List<string> _saleDetails = [];

    public decimal Total
    {
        get { lock (_sync) { return _total; } }
    }

    public void AddSale(string item, decimal price)
    {
        string details = $"{item} sold at {price}";
        lock (_sync)
        {
            _total += price;
            _saleDetails.Add(details);
        }
    }

    public string[] GetDetails(out decimal total)
    {
        lock (_sync)
        {
            total = _total;
            return _saleDetails.ToArray();
        }
    }
}
To use the lock keyword, you provide a reference to an object and a block of code. The C# compiler generates code that will cause the CLR to ensure that no more than one thread is inside a lock block for that object at any one time. Suppose you created a single instance of this SaleLog class, and on one thread you called the AddSale method, while on another thread you called GetDetails at the same time. Both threads will reach lock statements, passing in the same _sync field. Whichever thread happens to get there first will be allowed to run the block following the lock. The other thread will be made to wait—it won’t be allowed to enter its lock block until the first thread leaves its lock block.

The SaleLog class only ever uses any of its fields from inside a lock block using the _sync argument. This ensures that all access to fields is serialized (in the concurrency sense—that is, threads get to access fields one at a time, rather than all piling in simultaneously). When the GetDetails method reads from both the _total and _saleDetails fields, it can be confident that it’s getting a coherent view—the total will be consistent with the current contents of the list of sales details, because the code that modifies these two pieces of data does so within a single lock block. This means that updates will appear to be atomic from the point of view of any other lock block using _sync.

It may look excessive to use a lock block even for the get accessor that returns the total. However, decimal is a 128-bit value, so access to data of this type is not intrinsically atomic—without that lock, it would be possible for the returned value to be made up of a mixture of two or more values that _total had at different times. (For example, the bottom 64 bits might be from an older value than the top 64 bits.) This is often described as a torn read. The CLR guarantees atomic reads and writes only for data types whose size is no larger than 4 bytes, and also for references, even on a platform where those are larger than 4 bytes. (It guarantees this only for naturally aligned fields, but in C#, fields will always be aligned unless you have deliberately misaligned them for interop purposes.)

A subtle but important detail of Example 16-8 is that whenever it returns information about its internal state, it returns a copy. The Total property’s type is decimal, which is a value type, and values are always returned as copies. But when it comes to the list of entries, the GetDetails method calls ToArray, which will build a new array containing a copy of the list’s current contents. It would be a mistake to return the reference in _saleDetails directly, because that would enable code outside of the SalesLog class to access and modify the collection without using lock. We need to ensure that all access to that collection is synchronized, and we lose the ability to do that if our class hands out references to its internal state.

TIP
If you write code that performs some multithreaded work that eventually comes to a halt, it’s OK to share references to the state after the work has stopped. But if multithreaded modifications to an object are ongoing, you need to ensure that all use of that object’s state is protected.

The lock keyword accepts any object reference, so you might wonder why I’ve created an object specially—couldn’t I have passed this instead? That would have worked, but the problem is that your this reference is not private—it’s the same reference by which external code uses your object. Using a publicly visible feature of your object to synchronize access to private state is imprudent; some other code could decide that it’s convenient to use a reference to your object as the argument to some completely unrelated lock blocks. In this case, it probably wouldn’t cause a problem, but with more complex code, it could tie conceptually unrelated pieces of concurrent behavior together in a way that might cause performance problems or even deadlocks. Thus, it’s usually better to code defensively and use something that only your code has access to as the lock argument. Of course, I could have used the _saleDetails field because that refers to an object that only my class has access to. However, even if you code defensively, you should not assume that other developers will, so in general, it’s safer to avoid using an instance of a class you didn’t write as the argument for a lock, because you can never be certain that it isn’t using its this reference for its own locking purposes.

The fact that you can use any object reference is a bit of an oddity in any case. Most of .NET’s synchronization mechanisms use an instance of some distinct type as the point of reference for synchronization. (For example, if you want reader/writer locking semantics, you use an instance of the ReaderWriterLockSlim class, not just any old object.) The Monitor class (which is what lock uses) is an exception that dates back to an old requirement for a degree of compatibility with Java (which has a similar locking primitive). This is not relevant to modern .NET development, so this feature is now just a historical peculiarity. Using a distinct object whose only job is to act as a lock argument adds minimal overhead (compared to the costs of locking in the first place) and tends to make it easier to see how synchronization is being managed.

NOTE
You cannot use a value type as an argument for lock. C# prevents this, and with good reason. The compiler performs an implicit conversion to object on the lock argument, which for reference types doesn’t require the CLR to do anything at runtime. But when you convert a value type to a reference of type object, a box needs to be created. That box would be the argument to lock, and that would be a problem, because you get a new box every time you convert a value to an object reference. So, each time you ran a lock, it would get a different object, meaning there would be no synchronization in practice. This is why the compiler prevents you from trying.

How the lock keyword expands
Each lock block turns into code that does three things: first, it calls Monitor.Enter, passing the argument you provided to lock. Then it attempts to run the code in the block. Finally, it will usually call Monitor.Exit once the block finishes. But it’s not entirely straightforward, thanks to exceptions. The code will still call Monitor.Exit if the code you put in the block throws an exception, but it needs to handle the possibility that Monitor.Enter itself threw, which would mean that the thread does not own the lock and should therefore not call Monitor.Exit. Example 16-9 shows what the compiler makes of the lock block in the GetDetails method in Example 16-8.

Example 16-9. How lock blocks expand
bool lockWasTaken = false;
object temp = _sync;
try
{
    Monitor.Enter(temp, ref lockWasTaken);
    {
        total = _total;
        return _saleDetails.ToArray();
    }
}
finally
{
    if (lockWasTaken)
    {
        Monitor.Exit(temp);
    }
}
Monitor.Enter is the API that does the work of discovering whether some other thread already has the lock, and if so, making the current thread wait. If this returns at all, it normally succeeds. (It might deadlock, in which case it will never return.) There is a small possibility of failure caused by an exception, e.g., due to running out of memory. That would be unusual, but the generated code takes it into account nonetheless—this is the purpose of the slightly roundabout-looking code for the lockWasTaken variable. (In practice, the compiler will make that a hidden variable without an accessible name, by the way. I’ve named it to show what’s happening here.) The Monitor.Enter method guarantees that acquisition of the lock will be atomic with updating the flag indicating whether the lock was taken, ensuring that the finally block will attempt to call Exit if and only if the lock was acquired.

Monitor.Exit tells the CLR that we no longer need exclusive access to whatever resources we’re synchronizing access to, and if any other threads are waiting inside Monitor.Enter for the object in question, this will enable one of them to proceed. The compiler puts this inside a finally block to ensure that whether you exit from the block by running to the end, returning from the middle, or throwing an exception, the lock will be released.

The fact that the lock block calls Monitor.Exit on an exception is a double-edged sword. On the one hand, it reduces the chances of deadlock by ensuring that locks are released on failure. On the other hand, if an exception occurs while you’re in the middle of modifying some shared state, the system may be in an inconsistent state; releasing locks will allow other threads access to that state, possibly causing further problems. In some situations, it might have been better to leave locks locked in the case of an exception—a deadlocked process might do less damage than one that plows on with corrupt state. A more robust strategy is to write code that guarantees consistency in the face of exceptions, either by rolling back any changes it has made if an exception prevents a complete set of updates or by arranging to change state in an atomic way (e.g., by putting the new state into a whole new object and substituting that for the previous one only once the updated object is fully initialized). But that’s beyond what the compiler can automate for you.

Waiting and notification
The Monitor class can do more than just ensure that threads take it in turns. It provides a way for threads to sit and wait for a notification from some other thread. If a thread has acquired the monitor for a particular object, it can call Monitor.Wait, passing in that object. This has two effects: it releases the monitor and causes the thread to block. It will block until some other thread calls Monitor.Pulse or PulseAll for the same object; a thread must have the monitor to be able to call either of these methods. (Wait, Pulse, and PulseAll all throw an exception if you call them while not holding the relevant monitor.)

If a thread calls Pulse, this enables one thread waiting in Wait to wake up. Calling PulseAll enables all of the threads waiting on that object’s monitor to run. In either case, Monitor.Wait reacquires the monitor before returning, so even if you call PulseAll, the threads will wake up one at a time—a second thread cannot emerge from Wait until the first thread to do so relinquishes the monitor. In fact, no threads can return from Wait until the thread that called Pulse or PulseAll relinquishes the lock.

Example 16-10 uses Wait and Pulse to provide a wrapper around a Queue<T> that causes the thread that retrieves items from the queue to wait if the queue is empty. (This is for illustration only—if you want this sort of queue, you don’t have to write your own. Use the built-in BlockingCollection<T> or the types in System.Thread⁠ing​.Channels.)

Example 16-10. Wait and Pulse
public class MessageQueue<T>
{
    private readonly object _sync = new();

    private readonly Queue<T> _queue = new();

    public void Post(T message)
    {
        lock (_sync)
        {
            bool wasEmpty = _queue.Count == 0;
            _queue.Enqueue(message);
            if (wasEmpty)
            {
                Monitor.Pulse(_sync);
            }
        }
    }

    public T Get()
    {
        lock (_sync)
        {
            while (_queue.Count == 0)
            {
                Monitor.Wait(_sync);
            }
            return _queue.Dequeue();
        }
    }
}
This example uses the monitor in two ways. It uses it through the lock keyword to ensure that only one thread at a time uses the Queue<T> that holds queued items. But it also uses waiting and notification to enable the thread that consumes items to block efficiently when the queue is empty, and for any thread that adds new items to the queue to wake up the blocked reader thread.

Timeouts
Whether you are waiting for a notification or just attempting to acquire the lock, it’s possible to specify a timeout, indicating that if the operation doesn’t succeed within the specified time, you would like to give up. For lock acquisition, you use a different method, TryEnter, but when waiting for notification, you just use a different overload. (There’s no compiler support for this, so you won’t be able to use the lock keyword.) In both cases, you can pass either an int representing the maximum time to wait, in milliseconds, or a TimeSpan value. Both return a bool indicating whether the operation succeeded.

You could use this to avoid deadlocking the process, but if your code does fail to acquire a lock within the timeout, this leaves you with the problem of deciding what to do about that. If your application is unable to acquire a lock it needs, then it can’t just do whatever work it was going to do regardless. Termination of the process may be the only realistic option, because deadlock is usually a symptom of a bug, so if it occurs, your process may already be in a compromised state. That said, some developers take a less-than-rigorous approach to lock acquisition and may regard deadlock as being normal. In this case, it might be viable to abort whatever operation you were trying and either retry the work later or just log a failure, abandon this particular operation, and carry on with whatever else the process was doing. But that may be a risky strategy.

Other Synchronization Primitives
Although the lock keyword should be your default choice for protecting shared data in multithreaded scenarios, the .NET runtime libraries offer many specialized synchronization primitives that can be a better fit in certain cases. Table 16-1 describes the scenarios for which these are intended.

Table 16-1. Specialized synchronization types
Type	Usage
Barrier

Enables multiple threads to coordinate their work in phases.

CountdownEvent

Enables threads to wait until the CountDownEvent has been signaled some specific number of times.

ManualResetEvent, AutoResetEvent, and EventWaitHandle

Enables one thread to signal to other threads when something of interest has happened. Supports cross-process notifications on Windows.

ManualResetEventSlim

Alternative to ManualResetEvent that does not support cross-process notification, but which has lower overheads when wait times are likely to be very short.

Mutex

Exclusive access similar to Monitor. Higher overhead, but with cross-process support on all operating systems.

ReaderWriterLockSlim

Higher overhead than Monitor, but can be better if locks are held for a long time, and modifications are rare, because this allows concurrent readers, granting exclusive access only during writes.

SpinLock

Exclusive locking (just like lock and Monitor) that might enable lower memory usage; requires great care because subtle mistakes can make this more expensive than simpler solutions.

Semaphore

Enables a bounded level of concurrency—like a Monitor where you can configure the number of threads that are allowed to possess it simultaneously. Supports cross-process use on Windows.

SemaphoreSlim

Alternative to Semaphore that does not support cross-process notification, but which has lower overheads when wait times are likely to be very short.

Interlocked
The Interlocked class supports concurrent access to shared data, but it is not a synchronization primitive. Instead, it defines static methods that provide atomic forms of various simple operations.

For example, it provides Increment, Decrement, and Add methods, with overloads supporting int and long values. (These are all similar—incrementing or decrementing is just addition by 1 or −1.) Addition involves reading a value from some storage location, calculating a modified value, and storing that back in the same storage location, and if you use normal C# operators to do this, things can go wrong if multiple threads try to modify the same location simultaneously. If the value is initially 0, and two threads both read that value in quick succession, and if both then add 1 and store the result back, they will both end up writing back 1. Two threads attempted to increment the value, but it went up only by one. The Interlocked form of these operations prevents this sort of overlap.

Interlocked also offers various methods for swapping values. The Exchange method takes two arguments: a reference to a value and a value. This returns the value currently in the location referred to by the first argument and also overwrites that location with the value supplied as a second argument, and it performs these two steps as a single atomic operation. There are overloads supporting int, uint, long, ulong, object, float, double, nint, and nuint. There is also a generic Exchange<T>, where T can be any reference type. There is a variant called CompareExchange. As with Exchange, it takes a reference to some variable you wish to modify, and the value you want to replace it with, but it also takes a third argument: the value you think is already in the storage location. If the value in the storage location does not match the expected value, this method will not change the storage location. (It still returns whatever value was in that storage location, whether it modifies it or not.) This is often used to discover when some other thread has been using the variable at the same time as us, and to avoid concurrent modifications.

The simplest Interlocked operation is the Read method. This takes a ref long or ref ulong and reads the value atomically with respect to any other operations on the same variable that you perform through Interlocked. This enables you to read 64-bit values safely—in general, the CLR does not guarantee that 64-bit reads will be atomic. (In a 64-bit process, they will be unless you’ve taken deliberate steps to misalign data, which may sometimes be necessary to interoperate with unmanaged code. But 64-bit reads usually aren’t atomic on 32-bit architectures. You need to use Interlocked.Read to ensure atomicity.) There are no overloads for 32-bit values, because reading and writing those is always atomic.

The operations supported by Interlocked correspond to the atomic operations that most CPUs can support more or less directly. (Some CPU architectures support all the operations innately, while others support only the compare and exchange, building everything else up out of that. But in any case, these operations are at most a few instructions.) This means they are reasonably efficient. They are considerably more costly than performing equivalent noninterlocked operations with ordinary code, because atomic CPU instructions need to coordinate across all CPU cores (and across all CPU chips in computers that have multiple physically separate CPUs installed) to guarantee atomicity. Nonetheless, they incur a fraction of the cost you pay when a lock statement ends up blocking the thread at the OS level.

These sorts of operations are sometimes described as lock free. This is not entirely accurate—the computer does acquire locks very briefly at a fairly low level in the hardware. Atomic read-modify-write operations effectively acquire an exclusive lock on the computer’s memory for two bus cycles. However, no OS locks are acquired, the scheduler does not need to get involved, and the locks are held for an extremely short duration—often for just one machine code instruction. More significantly, the highly specialized and low-level form of locking used here does not permit holding onto one lock while waiting to acquire another—code can lock only one thing at a time. This means that this sort of operation will not deadlock. However, the simplicity that rules out deadlocks cuts both ways.

The downside of interlocked operations is that the atomicity applies only to extremely simple operations. It’s very hard to build more complex logic in a way that works correctly in a multithreaded environment using just Interlocked. It’s easier and considerably less risky to use the higher-level synchronization primitives, because those make it fairly easy to protect more complex operations rather than just individual calculations. You would typically use Interlocked only in extremely performance-sensitive work, and even then, you should measure carefully to verify that it’s having the effect you hope—sometimes clever use of Interlocked ends up costing you more than you expect.

One of the biggest challenges with writing correct code when using low-level atomic operations is that you may encounter problems caused by the way a CPU’s cache works. Work done by one thread may not become visible instantly to other threads, and in some cases, memory access may not necessarily occur in the order that your code specifies. Using higher-level synchronization primitives sidesteps these issues by enforcing certain ordering constraints, but if you decide instead to use Interlocked to build your own synchronization mechanisms, you will need to understand the memory model that .NET defines for when multiple threads access the same memory simultaneously, and you will typically need to use either the MemoryBarrier method defined by the Interlocked class or the various methods defined by the Volatile class to ensure correctness. This is beyond the scope of this book, and it’s also a really good way to write code that looks like it works but turns out to go wrong under heavy load (i.e., when it probably matters most), so these sorts of techniques are rarely worth the cost. Stick with the other mechanisms I’ve discussed in this chapter unless you really have no alternative.

Lazy Initialization
When you need an object to be accessible from multiple threads, if it’s possible for that object to be immutable (i.e., its fields never change after construction), you can often avoid the need for synchronization. It is always safe for multiple threads to read from the same location simultaneously—trouble sets in only if the data needs to change. However, there is one challenge: when and how do you initialize the shared object? One solution might be to store a reference to the object in a static field initialized from a static constructor or a field initializer—the CLR guarantees to run the static initialization for any class just once. However, this might cause the object to be created earlier than you want. If you perform too much work in static initialization, this can have an adverse effect on how long it takes your application to start running.

You might want to wait until the object is first needed before initializing it. This is called lazy initialization. This is not particularly hard to achieve—you can just check a field to see if it’s null and initialize it if not, using lock to ensure that only one thread gets to construct the value. However, this is an area in which developers seem to have a remarkable appetite for showing how clever they are, with the potentially undesirable corollary of demonstrating that they’re not as clever as they think they are.

The lock keyword works fairly efficiently, but it’s possible to do better by using Interlocked. However, the subtleties of memory access reordering on multiprocessor systems make it easy to write code that runs quickly, looks clever, and doesn’t always work. To avert this recurring problem, .NET provides two classes to perform lazy initialization without using lock or other potentially expensive synchronization primitives. The easiest to use is Lazy<T>.

Lazy<T>
The Lazy<T> class provides a Value property of type T, and it will not create the instance that Value returns until the first time something reads the property. By default, Lazy<T> will use the no-arguments constructor for T, but you can supply your own method for creating the instance.

Lazy<T> is able to handle race conditions for you. In fact, you can configure the level of multithreaded protection you require. Since lazy initialization can also be useful in single-threaded environments, you can disable multithreaded support entirely (by passing LazyThreadSafetyMode.None as a constructor argument). But for multithreaded environments, you can choose between the other two modes in the LazyThreadSafetyMode enumeration.

These determine what happens if multiple threads all try to read the Value property for the first time more or less simultaneously. PublicationOnly does not attempt to ensure that only one thread creates an object—it only applies any synchronization at the point at which a thread finishes creating an object. The first thread to complete construction or initialization gets to supply the object, and the ones produced by any other threads that had started initialization are all discarded. Once a value is available, all further attempts to read Value will just return that.

If you choose ExecutionAndPublication, only a single thread will be allowed to attempt construction. That may seem less wasteful, but PublicationOnly offers a potential advantage: because it avoids holding any locks during initialization, you are less likely to introduce deadlock bugs if the initialization code itself attempts to acquire any locks. PublicationOnly also handles errors differently. If the first initialization attempt throws an exception, other threads that had begun a construction attempt are given a chance to complete, whereas with ExecutionAndPublication, if the one and only attempt to initialize fails, the exception is retained and will be thrown each time any code reads Value.

LazyInitializer
The other class supporting lazy initialization is LazyInitializer. This is a static class, and you use it entirely through its static generic methods. It is marginally more complex to use than Lazy<T>, but it avoids the need to allocate an extra object in addition to the lazily allocated instance you require. Example 16-11 shows how to use it.

Example 16-11. Using LazyInitializer
public class Cache<T>
{
    private static Dictionary<string, T>? _d;

    public static IDictionary<string, T> Dictionary =>
        LazyInitializer.EnsureInitialized(ref _d);
}
If the field is null, the EnsureInitialized method constructs an instance of the argument type—Dictionary<string, T>, in this case. Otherwise, it will return the value already in the field. There are some other overloads. You can pass a callback, much as you can to Lazy<T>. You can also pass a ref bool argument, which it will inspect to discover whether initialization has already occurred (and it sets this to true when it performs initialization).

A static field initializer would have given us the same once-and-once-only initialization but might have ended up running far earlier in the process’s lifetime. In a more complex class with multiple fields, static initialization might even cause unnecessary work, because it happens for the entire class, so you might end up constructing objects that don’t get used. This could increase the amount of time it takes for an application to start up. LazyInitializer lets you initialize individual fields as and when they are first used, ensuring that you do only work that is needed.

Other Class Library Concurrency Support
The System.Collections.Concurrent namespace defines various collections that make more generous guarantees in the face of multithreading than the usual collections, meaning you may be able to use them without needing any other synchronization primitives. Take care, though—as always, even though individual operations may have well-defined behavior in a multithreaded world, that doesn’t necessarily help you if the operation you need to perform involves multiple steps. You may still need coordination at a broader scope to guarantee consistency. But in some situations, the concurrent collections may be all you need.

Unlike the nonconcurrent collections, ConcurrentDictionary, ConcurrentBag, ConcurrentStack, and ConcurrentQueue all support modification of their contents even while enumeration (e.g., with a foreach loop) of those contents is in progress. The dictionary provides a live enumerator, in the sense that if values are added or removed while you’re in the middle of enumerating, the enumerator might show you some of the added items and it might not show you the removed items. It makes no firm guarantees, not least because with multithreaded code, when two things happen on two different threads, it’s not always entirely clear which happened first—the laws of relativity mean that it may depend on your point of view.

This means that it’s possible for an enumerator to seem to return an item after that item was removed from the dictionary. The bag, stack, and queue take a different approach: their enumerators all take a snapshot and iterate over that, so a foreach loop will see a set of contents that is consistent with what was in the collection at some point in the past, even though it may since have changed.

As I already mentioned in Chapter 5, the concurrent collections present APIs that have similarities to their nonconcurrent counterparts but with some additional members to support atomic addition and removal of items. For example, Concurrent​Dic⁠tionary offers a GetOrAdd method that returns an existing entry if one exists and adds a new entry otherwise.

Another part of the runtime libraries that can help you deal with concurrency without needing to make explicit use of synchronization primitives is Rx (the subject of Chapter 11). It offers various operators that can combine multiple asynchronous streams together into a single stream. These manage concurrency issues for you—remember that any single observable will provide observers with items one at a time.

Rx takes the necessary steps to ensure that it stays within these rules even when it combines inputs from numerous individual streams that are all producing items concurrently. As long as all the sources stick to the rules, Rx will never ask an observer to deal with more than one thing at a time.

The System.Threading.Channels NuGet package offers types that support producer/consumer patterns, in which one or more threads generate data, while other threads consume that data. You can choose whether channels are buffered, enabling producers to get ahead of consumers, and if so, by how much. (The Blocking​Col⁠lection<T> in System.Collections.Concurrent also offers this kind of service. However, it is less flexible, and it does not support the await keyword described in Chapter 17.)

Finally, in multithreaded scenarios it is worth considering the immutable collection classes, which I described in Chapter 5. These support concurrent access from any number of threads, and because they are immutable, the question of how to handle concurrent write access never arises. Obviously, immutability imposes considerable constraints, but if you can find a way to work with these types (and remember, the built-in string type is immutable, so working with immutable data is common), they can be very useful in some concurrent scenarios.

Tasks
Earlier in this chapter, I showed how to use the Task class to launch work in the thread pool. This class is more than just a wrapper for the thread pool. Task and the related types that form the Task Parallel Library (TPL) can handle a wider range of scenarios. Tasks are particularly important because C#’s asynchronous language features (which are the topic of Chapter 17) are able to work with these directly. A great many APIs in the runtime libraries offer task-based asynchronous operation.

Although tasks are the preferred way to use the thread pool, they are not just about multithreading. The basic abstractions are more flexible than that.

The Task and Task<T> Classes
There are two classes at the heart of the TPL: Task and a class that derives from it, Task<T>. The Task base class represents some work that may take some time to complete. Task<T> extends this to represent work that produces a result (of type T) when it completes. (The nongeneric Task does not produce any result. It’s the asynchronous equivalent of a void return type.) Notice that these are not concepts that necessarily involve threads.

Most I/O operations can take a while to complete, and in most cases, the runtime libraries provide task-based APIs for them. Example 16-12 uses an asynchronous method to fetch the content of a web page as a string. Since the HttpClient class cannot return the string immediately—it might take a while to download the page—it returns a task instead.

Example 16-12. Task-based web download
var w = new HttpClient();
Task<string> webGetTask = w.GetStringAsync("https://endjin.com/");
NOTE
Most task-based APIs follow a naming convention in which they end in Async, and if there’s a corresponding synchronous API, it will have the same name but without the Async suffix. For example, the Stream class (see Chapter 15) has a Write method, and that method is synchronous (i.e., it waits until it finishes its work before returning). It also offers WriteAsync which, being asynchronous, returns without waiting for its work to complete. It returns a Task to represent the work; this convention is called the Task-based Asynchronous Pattern (TAP).

That GetStringAsync method does not wait for the download to complete, so it returns almost immediately. To perform the download, the computer has to send a message to the relevant server, and then it must wait for a response. Once the request is on its way, there’s no work for the CPU to do until the response comes in, meaning that this operation does not need to involve a thread for the majority of the time that the request is in progress. So this method does not wrap some underlying synchronous version of the API in a call to Task.Run. And with classes that offer I/O APIs in both forms, such as Stream, the synchronous versions are often wrappers around a fundamentally asynchronous implementation: when you call a blocking API to perform I/O, it will typically perform an asynchronous operation under the covers and then just block the calling thread until that work completes. And even in cases where it’s nonasynchronous all the way down to the OS—e.g., the FileStream can use nonasynchronous operating system file APIs to implement Read and Write—I/O in the OS kernel is typically asynchronous in nature.

So, although the Task and Task<T> classes make it very easy to produce tasks that work by running methods on thread pool threads, they are also able to represent fundamentally asynchronous operations that do not require the use of a thread for most of their duration. Although it’s not part of the official terminology, I describe this kind of operation as a threadless task, to distinguish it from tasks that run entirely on thread pool threads.

ValueTask and ValueTask<T>
Task and Task<T> are pretty flexible, and not just because they can represent both thread-based and threadless operations. As you’ll see, they offer several mechanisms for discovering when the work they represent completes, including the ability to combine multiple tasks into one. Multiple threads can all wait on the same task simultaneously. You can write caching mechanisms that repeatedly hand out the same task, even long after the task completes. This is all very convenient, but it means that these task types also have some overheads. For more constrained cases, .NET defines less flexible ValueTask and ValueTask<T> types that are more efficient in certain circumstances.

The most important difference between these types and their ordinary counterparts is that ValueTask and ValueTask<T> are value types. This is significant in performance-sensitive code because it can reduce the number of objects that code allocates, reducing the amount of time an application spends performing garbage collection work. You might be thinking that the context switching costs typically involved with concurrent work are likely to be high enough that the cost of an object allocation will be the least of your concerns when dealing with asynchronous operations. And while this is often true, there’s one very important scenario where the GC overhead of Task<T> can be problematic: operations that sometimes run slowly but usually don’t.

It is very common for I/O APIs to perform buffering to reduce the number of calls into the OS. If you write a few bytes into a Stream, it will typically put those into a buffer and wait until either you’ve written enough data to make it worth sending it to the OS or you’ve explicitly called Flush. And it’s also common for reads to be buffered—if you read a single byte from a file, the OS will typically have to read an entire sector from the drive (usually at least 4 KB), and that data usually gets saved somewhere in memory so that when you ask for the second byte, no more I/O needs to happen. The practical upshot is that if you write a loop that reads data from a file in relatively small chunks (e.g., one line of text at a time), the majority of read operations will complete straightaway because the data being read has already been fetched.

In these cases where the overwhelming majority of calls into asynchronous APIs complete immediately, the GC overheads of creating task objects can become significant. This is why ValueTask and ValueTask<T> were introduced. (These are built into .NET, and .NET Standard 2.1. On .NET Framework, you can get them via the System.Threading.Tasks.Extensions NuGet package.) These make it possible for potentially asynchronous operations to complete immediately without needing to allocate any objects. In cases where immediate completion is not possible, these types end up being wrappers for Task or Task<T> objects, at which point the overheads return, but in cases where only a small fraction of calls need to do that, these types can offer significant performance boosts, particularly in code that uses the low-allocation techniques described in Chapter 18.

The nongeneric ValueTask is rarely used, because asynchronous operations that produce no result can just return the Task.CompletedTask static property, which provides a reusable task that is already in the completed state, avoiding any GC overhead. But tasks that need to produce a result generally can’t reuse existing tasks. (There are some exceptions: the runtime libraries will often use cached precompleted tasks for Task<bool>, because there are only two possible outcomes. But for Task<int>, there’s no practical way to maintain a list of precompleted tasks for every possible result.)

These value task types have some constraints. They are single use: unlike Task and Task<T>, you must not store these types in a dictionary or a Lazy<T> to provide a cached asynchronous value. It is an error to attempt to retrieve the Result of a ValueTask<T> before it has completed. It is also an error to retrieve the Result more than once. In general, you should use a ValueTask or ValueTask<T> with exactly one await operation (as described in Chapter 17) and then never use it again. (Alternatively, if necessary, you can escape these restrictions by calling its AsTask method to obtain a full Task, or Task<T> with all the corresponding overheads, at which point you should not do anything more with the value task.)

Because the value type tasks were introduced many years after the TPL first appeared, class libraries often use Task<T> where you might expect to see a ValueTask<T>. For example, the Stream class’s ReadAsync methods are all prime candidates because buffering means these are likely to complete immediately a high proportion of the time. However, most of Stream’s asynchronous methods were defined long before ValueTask<T> existed, so they mostly return Task<T>. The recently added ReadAsync overload that accepts a Memory<byte> instead of a byte[] does return a ValueTask<T>, though, and more generally, where APIs have been augmented to add support for the new memory-efficient techniques described in Chapter 18, these will usually return ValueTask<T>. And if you’re in a performance-sensitive world where the GC overhead of a task is significant, you will likely want to be using those techniques in any case.

Task creation options
Instead of using Task.Run, you can get more control over certain aspects of a new thread-based task by creating it with the StartNew method of either Task.Factory or Task<T>.Factory, depending on whether your task needs to return a result. Some overloads of StartNew take an argument of the enum type TaskCreationOptions, which provides some control over how the TPL schedules the task.

The PreferFairness flag asks to run the task after any tasks that have already been scheduled. By default, the thread pool normally runs the most recently added tasks first (a last-in, first-out, or LIFO, policy) because this tends to make more efficient use of the CPU cache.

The LongRunning flag warns the TPL that the task may run for a long time. By default, the TPL’s scheduler optimizes for relatively short work items—anything up to a few seconds. This flag indicates that the work might take longer than that, in which case the TPL may modify its scheduling. If there are too many long-running tasks, they might use up all the threads, and even though some of the queued work items might be for much shorter pieces of work, those will still take a long time to finish, because they’ll have to wait in line behind the slow work before they can even start. But if the TPL knows which items are likely to run quickly and which are likely to be slower, it can prioritize them differently to avoid such problems.

The other TaskCreationOptions settings relate to parent/child task relationships and schedulers, which I’ll describe later.

Task status
A task goes through a number of states in its lifetime, and you can use the Task class’s Status property to discover where it has gotten to. This returns a value of the enum type TaskStatus. If a task completes successfully, the property will return the enumeration’s RanToCompletion value. If the task fails, it will be Faulted. If you cancel a task using the technique shown in “Cancellation”, the status will then be Canceled.

There are several variations on a theme of “in progress,” of which Running is the most obvious—it means that some thread is currently executing the task. A task representing I/O doesn’t typically require a thread while it is in progress, so it never enters that state—it starts in the WaitingForActivation state and then typically transitions directly to one of the three final states (RanToCompletion, Faulted, or Canceled). A thread-based task can also be in this WaitingForActivation state but only if something is preventing it from running, which would typically happen if you set it up to run only when some other task completes (which I’ll show how to do shortly). A thread-based task may also be in the WaitingToRun state, which means that it’s in a queue waiting for a thread pool thread to become available. It’s possible to establish parent/child relationships between tasks, and a parent that has already finished but that created some child tasks that are not yet complete will be in the WaitingForChildrenToComplete state.

Finally, there’s the Created state. You don’t see this very often, because it represents a thread-based task that you have created but have not yet asked to run. You’ll never see this with a task created using the task factory’s StartNew method, or with Task.Run, but you will see this if you construct a new Task directly.

The level of detail in the TaskStatus property may be too much most of the time, so the Task class defines various simpler bool properties. If you want to know only whether the task has no more work to do (and don’t care whether it succeeded, failed, or was canceled), there’s the IsCompleted property. IsCompletedSuccessfully tells you whether it completed without failure or cancellation. If you want to check specifically for failure or cancellation, use IsFaulted or IsCanceled.

Retrieving the result
Suppose you’ve got a Task<T>, either from an API that provides one or by creating a thread-based task that returns a value. If the task completes successfully, you are likely to want to retrieve its result, which you can get from the Result property. So the task created by Example 16-12 makes the web page content available in webGetTask.Result.

If you try to read the Result property before the task completes, it will block your thread until the result is available. (If you have a plain Task, which does not return a result, and you would like to wait for that to finish, you can just call Wait instead.) If the operation then fails, Result throws an exception (as does Wait), although that is not as straightforward as you might expect, as I will discuss in “Error Handling”.

WARNING
You should avoid using Result on an uncompleted task. In some scenarios, it risks deadlock, as does Wait. This is particularly common in desktop applications, because certain work needs to happen on particular threads, and if you block a thread by reading the Result of an incomplete task, you might prevent the task from completing. Even if you don’t deadlock, blocking on Result can cause performance issues by hogging thread pool threads that might otherwise have been able to get on with useful work. And reading the Result of an uncompleted ValueTask<T> is not permitted.

In most cases, it is far better to use C#’s asynchronous language features to retrieve the result. These are the subject of the next chapter, but as a preview, Example 16-13 shows how you could use this to get the result of the task that fetches a web page. (You’ll need to apply the async keyword in front of the method declaration to be able to use the await keyword.)

Example 16-13. Getting a task’s results with await
string pageContent = await webGetTask;
This may not look like an exciting improvement on simply writing webGetTask.Result, but as I’ll show in Chapter 17, this code is not quite what it seems—the C# compiler restructures this statement into a callback-driven state machine that enables you to get the result without blocking the calling thread. (If the operation hasn’t finished, the thread returns to the caller, and the remainder of the method runs later when the operation completes.)

But how are the asynchronous language features able to make this work—how can code discover when a task has completed? Result or Wait let you just sit and wait for that to happen, blocking the thread, but that rather defeats the purpose of using an asynchronous API in the first place. You will normally want to be notified when the task completes, and you can do this with a continuation.

Continuations
Tasks provide various overloads of a method called ContinueWith. This creates a new thread-based task that will execute when the task on which you called Contin⁠ue​With finishes (whether it does so successfully or with failure or cancellation). Example 16-14 uses this on the task created in Example 16-12.

Example 16-14. A continuation
webGetTask.ContinueWith(static t =>
{
    string webContent = t.Result;
    Console.WriteLine($"Web page length: {webContent.Length}");
});
A continuation task is always a thread-based task (regardless of whether its antecedent task was thread-based, I/O-based, or something else). The task gets created as soon as you call ContinueWith but does not become runnable until its antecedent task completes. (It starts out in the WaitingForActivation state.)

NOTE
A continuation is a task in its own right—ContinueWith returns either a Task<T> or Task, depending on whether the delegate you supply returns a result. You can set up a continuation for a continuation if you want to chain together a sequence of operations.

The method you provide for the continuation (such as the lambda in Example 16-14) receives the antecedent task as its argument, and I’ve used this to retrieve the result. I could also have used the webGetTask variable, which is in scope from the containing method, as it refers to the same task. However, by using the argument, the lambda in Example 16-14 doesn’t use any variables from its containing method, which enables the compiler to produce slightly more efficient code—it doesn’t need to create an object to hold shared variables, and it can reuse the delegate instance it creates because it doesn’t have to create a context-specific one for each call. (I put the static method on the lambda to tell the compiler that this was my intention. It would still generate the more efficient code even without that keyword, but this way if I accidentally tried to capture a variable, I’d get a compiler error instead of the compiler silently generating less efficient code.) This means I could also easily separate this out into an ordinary noninline method, if I felt that would make the code easier to read.

You might be thinking that there’s a possible problem in Example 16-14: What if the download completes extremely quickly so that webGetTask has already completed before the code manages to attach the continuation? In fact, that doesn’t matter—if you call ContinueWith on a task that has already completed, it will still run the continuation. It just schedules it immediately. You can attach as many continuations as you like. All the continuations you attach before the task completes will be scheduled for execution when it does complete. And any that you attach after the task has completed will be scheduled immediately.

By default, a continuation task will be scheduled for execution on the thread pool like any other task. However, there are some things you can do to change how it runs. Some overloads of ContinueWith take an argument of the enum type Task​Conti⁠nua⁠tionOptions, which controls how (and whether) your task is scheduled. This includes all of the same options that are available with TaskCreationOptions but adds some others specific to continuations.

You can specify that the continuation should run only in certain circumstances. For example, the OnlyOnRanToCompletion flag will ensure that the continuation runs only if the antecedent task succeeds. There are similar OnlyOnFaulted and OnlyOn​Can⁠celed flags. Alternatively, you can specify NotOnRanToCompletion, which means that the continuation will run only if the task either faults or is canceled.

NOTE
You can create multiple continuations for a single task. So you could set up one to handle the success case and another one to handle failures.

You can also specify ExecuteSynchronously. This indicates that the continuation should not be scheduled as a separate work item. Normally, when a task completes, any continuations for that task will be scheduled for execution and will have to wait for the normal thread pool mechanisms pick the work items out of the queue and execute them. (This won’t take long if you use the default options. Unless you specify PreferFairness, the LIFO operation the thread pool uses for tasks means that the most recently scheduled items run first.) However, if your completion does only the tiniest amount of work, the overhead of scheduling it as a completely separate item may be overkill. So ExecuteSynchronously lets you piggyback the completion task on the same thread pool work item that ran the antecedent. The TPL will run this kind of continuation immediately after the antecedent finishes before returning the thread to the pool. You should use this option only if the continuation will run quickly.

The LazyCancellation option handles a tricky situation that can occur if you make tasks cancelable (as described later in “Cancellation”) and you are using continuations. If you cancel a task, any continuations will, by default, become runnable instantly. If the task being canceled was itself set up as a continuation for another task that hadn’t yet finished, and if it has a continuation of its own, as in Example 16-15, this can have a mildly surprising effect.

Example 16-15. Cancellation and chained continuations
private static void ShowContinuations()
{
    Task op = Task.Run(DoSomething);
    var cs = new CancellationTokenSource();
    Task onDone = op.ContinueWith(
        _ => Console.WriteLine("Never runs"),
        cs.Token);
    Task andAnotherThing = onDone.ContinueWith(
        _ => Console.WriteLine("Continuation's continuation"));
    cs.Cancel();
}

static void DoSomething()
{
    Thread.Sleep(1000);
    Console.WriteLine("Initial task finishing");
}
This creates a task that will call DoSomething, followed by a cancelable continuation for that task (the Task in onDone), and then a final task (andAnotherThing) that is a continuation for the first continuation. This code cancels the first continuation almost immediately, which is almost certain to happen before the first task completes. The effect of this is that the final task runs before the first completes. The final andAnotherThing task becomes runnable when onDone completes, even if that completion was due to onDone being canceled. Since there was a chain here—andAnotherThing is a continuation for onDone, which is a continuation for op—it is a bit odd that andAnotherThing ends up running before op has finished. LazyCancellation changes the behavior so that the first continuation will not be deemed to have completed until its antecedent completes, meaning that the final continuation will run only after the first task has finished.

There’s another mechanism for controlling how tasks execute: you can specify a scheduler.

Schedulers
All thread-based tasks are executed by a TaskScheduler. By default, you’ll get the TPL-supplied scheduler that runs work items via the thread pool. However, there are other kinds of schedulers, and you can even write your own.

The most common reason for selecting a nondefault scheduler is to handle thread affinity requirements. The TaskScheduler class’s static FromCurrentSynchroniza⁠tion​Context method returns a scheduler based on the current synchronization context for whichever thread you call the method from. This scheduler will execute all work via that synchronization context. So, if you call FromCurrentSynchronizationContext from a UI thread, the resulting scheduler can be used to run tasks that can safely update the UI. You would typically use this for a continuation—you can run some task-based asynchronous work and then hook up a continuation that updates the UI when that work is complete. Example 16-16 shows this technique in use in the codebehind file for a window in a WPF application.

Example 16-16. Scheduling a continuation on the UI thread

public partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();
    }

    private static readonly HttpClient w = new();
    private readonly TaskScheduler _uiScheduler =
        TaskScheduler.FromCurrentSynchronizationContext();

    private void FetchButtonClicked(object sender, RoutedEventArgs e)
    {
        Task<string> webGetTask = w.GetStringAsync("https://endjin.com/");

        webGetTask.ContinueWith(t =>
        {
            string webContent = t.Result;
            outputTextBox.Text = webContent;
        },
        _uiScheduler);
    }
}
This uses a field initializer to obtain the scheduler—the constructor for a UI element runs on the UI thread, so this will get a scheduler for the synchronization context for the UI thread. A click handler then downloads a web page using the HttpClient class’s GetStringAsync. This runs asynchronously, so it won’t block the UI thread, meaning that the application will remain responsive while the download is in progress. The method sets up a continuation for the task using an overload of ContinueWith that takes a TaskScheduler. This ensures that when the task that gets the content completes, the lambda passed to ContinueWith runs on the UI thread, so it’s safe for it to access UI elements.

TIP
While this works perfectly well, the await keyword described in the next chapter provides a more straightforward solution to this particular problem.

The runtime libraries provide three built-in kinds of schedulers. There’s the default one that uses the thread pool, and the one I just showed that uses a synchronization context. The third is provided by a class called ConcurrentExclusiveSchedulerPair, and as the name suggests, this provides two schedulers, which it makes available through properties. The ConcurrentScheduler property returns a scheduler that will run tasks concurrently much like the default scheduler. The ExclusiveScheduler property returns a scheduler that can be used to run tasks one at a time, and it will temporarily suspend the other scheduler while it does so. (This is reminiscent of ReaderWriterLockSlim—it allows exclusivity when required but concurrency the rest of the time.)

Error Handling
A Task object indicates when its work has failed by entering the Faulted state. There will always be at least one exception associated with failure, but the TPL allows composite tasks—tasks that contain a number of subtasks. This makes it possible for multiple failures to occur, and the root task will report them all. Task defines an Exception property, and its type is AggregateException. You may recall from Chapter 8 that as well as inheriting the InnerException property from the base Exception type, AggregateException defines an InnerExceptions property that returns a collection of exceptions. This is where you will find the complete set of exceptions that caused the task to fault. (If the task was not a composite task, there will usually be just one.)

If you attempt to get the Result property or call Wait on a faulted task, it will throw the same AggregateException as it would return from the Exception property. A faulted task remembers whether you have used at least one of these members, and if you have not yet done so, it considers the exception to be unobserved. The TPL uses finalization to track faulted tasks with unobserved exceptions, and if you allow such a task to become unreachable, the TaskScheduler will raise its static UnobservedTaskException event. This gives you one last chance to do something about the exception, after which it will be lost.

Custom Threadless Tasks
Many I/O-based APIs return threadless tasks. You can do the same if you want. The TaskCompletionSource<T> class provides a way to create a Task<T> that does not have an associated method to run on the thread pool and instead completes when you tell it to. There’s also a nongeneric TaskCompletionSource for creating a non-generic Task. (.NET Framework doesn’t have the non-generic one, but since Task<T> derives from Task, you can just use TaskCompletionSource<object?> instead.)

Suppose you’re using a class that does not provide a task-based API, and you’d like to add a task-based wrapper. The runtime libraries provide an SmtpClient class for sending emails, and it supports an older event-based asynchronous pattern but not the task-based one. Example 16-17 uses that API in conjunction with TaskCompletionSource<object?> to provide a task-based wrapper. (And, yes, there are two spellings of Canceled/​Cancelled in there. The TPL consistently uses Canceled, but older APIs exhibit more variety.)

Example 16-17. Using TaskCompletionSource<T>
public static class SmtpAsyncExtensions
{
    public static Task SendTaskAsync(this SmtpClient mailClient, string from,
        string recipients, string subject, string body)
    {
        var tcs = new TaskCompletionSource<object?>();

        void CompletionHandler(object s, AsyncCompletedEventArgs e)
        {
            // Check this is the notification for our SendAsync.
            if (!object.ReferenceEquals(e.UserState, tcs)) { return; }
            mailClient.SendCompleted -= CompletionHandler;
            if (e.Canceled)
            {
                tcs.SetCanceled();
            }
            else if (e.Error != null)
            {
                tcs.SetException(e.Error);
            }
            else
            {
                tcs.SetResult(null);
            }
        };

        mailClient.SendCompleted += CompletionHandler;
        mailClient.SendAsync(from, recipients, subject, body, tcs);

        return tcs.Task;
    }
}
The SmtpClient notifies us that the operation is complete by raising an event. The handler for this event first checks that the event corresponds to our call to SendAsync and not some other operation that may have already been in progress. It then detaches itself (so that it doesn’t run a second time if something uses that same SmtpClient for further work). Then it detects whether the operation succeeded, was canceled, or failed, and calls the SetResult, SetCanceled, or SetException method, respectively, on the TaskCompletionSource<object>. This will cause the task to transition into the relevant state and will also take care of running any continuations attached to that task. The completion source makes the threadless Task object it creates available through its Task property, which this method returns.

Parent/Child Relationships
If a thread-based task’s method creates a new thread-based task, then by default, there will be no particular relationship between those tasks. However, one of the Task​Crea⁠tionOptions flags is AttachedToParent, and if you set this, the newly created task will be a child of the task currently executing. The significance of this is that the parent task won’t report completion until all its children have completed. (Its own method also needs to complete, of course.) If any children fault, the parent task will fault, and it will include all the children’s exceptions in its own AggregateException.

You can also specify the AttachedToParent flag for a continuation. Be aware that this does not make it a child of its antecedent task. It will be a child of whichever task was running when ContinueWith was called to create the continuation.

NOTE
Threadless tasks (e.g., most tasks representing I/O) often cannot be made children of another task. If you create one yourself with a TaskCompletionSource<T>, you can do it because that class has a constructor overload that accepts a TaskCreation​Op⁠tions. However, the majority of .NET APIs that return tasks do not provide a way to request that the task be a child.

Parent/child relationships are not the only way of creating a task whose outcome is based on multiple other items.

Composite Tasks
The Task class has static WhenAll and WhenAny methods. Each of these has overloads that accept either a collection of Task objects or a collection of Task<T> objects as the only argument. The WhenAll method returns either a Task or a Task<T[]> that completes only when all of the tasks provided in the argument have completed (and in the latter case, the composite task produces an array containing each of the individual tasks’ results). The WhenAny method returns a Task<Task> or Task<Task<T>> that completes as soon as the first task completes, providing that task as the result.

As with a parent task, if any of the tasks that make up a task produced with WhenAll fail, the exceptions from all of the failed tasks will be available in the composite task’s AggregateException. (WhenAny does not report errors. It completes as soon as the first task completes, and you must inspect that to discover if it failed.)

You can attach a continuation to these tasks, but there’s a slightly more direct route. Instead of creating a composite task with WhenAll or WhenAny and then calling ContinueWith on the result, you can just call the ContinueWhenAll or Continue​WhenAny method of a task factory. Again, these take a collection of Task or Task<T>, but they also take a method to invoke as the continuation.

Other Asynchronous Patterns
Although the TPL provides the preferred mechanism for exposing asynchronous APIs, .NET had been around for almost a decade before it was added, so you will come across older approaches. The longest established form is the Asynchronous Programming Model (APM). This was introduced in .NET 1.0, so it is widely implemented, but its use is now discouraged. With this pattern, methods come in pairs: one to start the work and a second to collect the results when it is complete. Example 16-18 shows just such a pair from the Stream class in the System.IO namespace, and it also shows the corresponding synchronous method. (Code written today should use a task-based WriteAsync instead.)

Example 16-18. An APM pair and the corresponding synchronous method
public virtual IAsyncResult BeginWrite(byte[] buffer, int offset, int count,
    AsyncCallback callback, object state)...
public virtual void EndWrite(IAsyncResult asyncResult)...

public abstract void Write(byte[] buffer, int offset, int count)...
Notice that the first three arguments of the BeginWrite method are identical to those of the Write method. In the APM, the BeginXxx method takes all of the inputs (i.e., any normal arguments and any ref arguments but not out arguments, should any be present). The EndXxx method provides any outputs, which means the return value, any ref arguments (because those can pass information either in or out), and any out arguments.

The BeginXxx method also takes two additional arguments: a delegate of type AsyncCallback, which will be invoked when the operation completes, and an argument of type object that accepts any object you would like to associate with the operation (or null if you have no use for this). This method also returns an IAsync​Re⁠sult, which represents the asynchronous operation.

When your completion callback gets invoked, you can call the EndXxx method, passing in the same IAsyncResult object returned by the BeginXxx method, and this will provide the return value if there is one. If the operation failed, the EndXxx method will throw an exception.

You can wrap APIs that use the APM with a Task. The TaskFactory objects provided by Task and Task<T> provide FromAsync methods to which you can pass a pair of delegates for the BeginXxx and EndXxx methods, and you also pass any arguments that the BeginXxx method requires. This will return a Task or Task<T> that represents the operation.

Another common older pattern is the Event-based Asynchronous Pattern (EAP). You’ve seen an example in this chapter—it’s what the SmtpClient uses. With this pattern, a class provides a method that starts the operation and a corresponding event that it raises when the operation completes. The method and event usually have related names, such as SendAsync and SendCompleted. An important feature of this pattern is that the method captures the synchronization context and uses that to raise the event, meaning that if you use an object that supports this pattern in UI code, it effectively presents a single-threaded asynchronous model. This makes it much easier to use than the APM, because you don’t need to write any extra code to get back onto the UI thread when asynchronous work completes.

There’s no automated mechanism for wrapping the EAP in a task, but as I showed in Example 16-17, it’s not particularly hard to do.

There’s one more common pattern used in asynchronous code: the awaitable pattern supported by the C# asynchronous language features (the async and await keywords). As I showed in Example 16-13, you can consume a TPL task directly with these features, but the language does not recognize Task directly, and it’s possible to await things other than tasks. You can use the await keyword with anything that implements a particular pattern. I will show this in Chapter 17.

Cancellation
.NET defines a standard mechanism for canceling slow operations. Cancelable operations take an argument of the type CancellationToken, and if you set this into a canceled state, the operation will stop early if possible instead of running to completion.

The CancellationToken type itself does not offer any methods to initiate cancellation—the API is designed so that you can tell operations when you want them to be canceled without giving them power to cancel whatever other operations you have associated with the same CancellationToken. The act of cancellation is managed through a separate object, CancellationTokenSource. As the name suggests, you can use this to get hold of any number of CancellationToken instances. If you call the CancellationTokenSource object’s Cancel method, that sets all of the associated CancellationToken instances into a canceled state.

Some of the synchronization mechanisms I described earlier can be passed a CancellationToken. (Monitor does not support cancellation, but many newer APIs do.) It’s also common for task-based APIs to take a cancellation token, and the TPL itself also offers overloads of the StartNew and ContinueWith methods that take them. If the task has already started to run, there’s nothing the TPL can do to cancel it, but if you cancel a task before it begins to run, the TPL will take it out of the scheduled task queue for you. If you want to be able to cancel your task after it starts running, you’ll need to write code in the body of your task that inspects the CancellationToken and abandons the work if its IsCancellationRequested property is true.

Cancellation support is not ubiquitous, because it’s not always possible. Some operations simply cannot be canceled. For example, once a message has been sent out over the network, you can’t unsend it. Some operations allow work to be canceled up until some point of no return has been reached. (If a message is queued up to be sent but hasn’t actually been sent, then it might not be too late to cancel, for example.) This means that even when cancellation is offered, it might not do anything. So, when you use cancellation, you need to be prepared for it not to work.

Parallelism
The runtime libraries include some classes that can work with collections of data concurrently on multiple threads. There are three ways to do this: the Parallel class, Parallel LINQ, and TPL Dataflow.

The Parallel Class
The Parallel class offers five static methods: For, ForAsync, ForEach, ForEachAsync, and Invoke. The last of those takes an array of delegates and executes all of them, potentially in parallel. (Whether it decides to use parallelism depends on various factors such as the number of hardware threads the computer has, how heavily loaded the system is, and how many items you want it to process.) The For and ForEach methods mimic the C# loop constructs of the same names, but they will also potentially execute iterations in parallel. ForAsync (new in .NET 8.0) and ForEachAsync also mimic these loop types, but they provide better support for asynchronous operation. Both accept a delegate that returns a task, enabling each iteration to perform asynchronous operations (equivalent to using await in the body of a foreach loop). ForEachAsync can work with IAsyncEnumerable<T> (like await foreach).

Example 16-19 illustrates the use of Parallel.For in code that performs a convolution of two sets of samples. This is a highly repetitive operation commonly used in signal processing. (In practice, a fast Fourier transform offers a more efficient way to perform this work unless the convolution kernel is small, but the complexity of that code would have obscured the main subject here, the Parallel class.) It produces one output sample for each input sample. Each output sample is produced by calculating the sum of a series of pairs of values from the two inputs, multiplied together. For large data sets, this can be time consuming, so it is the sort of work you might want to speed up by spreading it across multiple processors. Each individual output sample’s value can be calculated independently of all the others, so it is a good candidate for parallelization.

Example 16-19. Parallel convolution
static float[] ParallelConvolution(float[] input, float[] kernel)
{
    float[] output = new float[input.Length];
    Parallel.For(0, input.Length, i =>
    {
        float total = 0;
        for (int k = 0; k < Math.Min(kernel.Length, i + 1); ++k)
        {
            total += input[i - k] * kernel[k];
        }
        output[i] = total;
    });

    return output;
}
The basic structure of this code is very similar to a pair of nested for loops. I’ve simply replaced the outer for loop with a call to Parallel.For. (I’ve not attempted to parallelize the inner loop—if you make each individual step trivial, Parallel.For will spend more of its time in housekeeping work than it does running your code.)

The first argument, 0, sets the initial value of the loop counter, and the second sets the upper limit. The final argument is a delegate that will be invoked once for each value of the loop counter, and the calls will occur concurrently if the Parallel class’s heuristics tell it that this is likely to produce a speedup as a result of the work running in parallel. Running this method with large data sets on a multicore machine causes all of the available hardware threads to be used to full capacity.

It may be possible to get better performance by partitioning the work in more cache-friendly ways—naive parallelization can give the impression of high performance by maxing out all your CPU cores while delivering suboptimal throughput. However, there is a trade-off between complexity and performance, and the simplicity of the Parallel class can often provide worthwhile wins for relatively little effort.

Parallel LINQ
Parallel LINQ is a LINQ provider that works with in-memory information, much like LINQ to Objects. The System.Linq namespace makes this available as an extension method called AsParallel defined for any IEnumerable<T> (by the Parallel​Enumera⁠ble class). This returns a ParallelQuery<T>, which supports the usual LINQ operators.

Any LINQ query built this way provides a ForAll method, which takes a delegate. When you call this, it invokes the delegate for all of the items that the query produces, and it will do so in parallel on multiple threads where possible.

TPL Dataflow
TPL Dataflow is a runtime library feature that lets you construct a graph of objects that perform some kind of processing on information that flows through them. You can tell the TPL which of these nodes needs to process information sequentially and which are happy to work on multiple blocks of data simultaneously. You push data into the graph, and the TPL will then manage the process of providing each node with blocks to process, and it will attempt to optimize the level of parallelism to match the resources available on your computer.

The dataflow API is in the System.Threading.Tasks.Dataflow namespace. (It’s built into .NET; on .NET Framework you’ll need to add a reference to a NuGet package, also called System.Threading.Tasks.Dataflow.) It is large and complex and could have a whole chapter to itself. Sadly, this makes it beyond the scope of this book. I mention it because it’s worth being aware of for certain kinds of work.

Summary
Threads provide the ability to execute multiple pieces of code simultaneously. On a computer with multiple CPU execution units (i.e., multiple hardware threads), you can exploit this potential for parallelism by using multiple software threads. You can create new software threads explicitly with the Thread class, or you can use either the thread pool or a parallelization mechanism, such as the Parallel class or Parallel LINQ, to determine automatically how many threads to use to run the work your application supplies. If multiple threads need to use and modify shared data structures, you will need to use the synchronization mechanisms offered by .NET to ensure that the threads can coordinate their work correctly.

Threads can also provide a way to execute multiple concurrent operations that do not need the CPU the whole time (e.g., waiting for a response from an external service), but it is often more efficient to perform such work with asynchronous APIs (where available). The Task Parallel Library (TPL) provides abstractions that are useful for both kinds of concurrency. It can manage multiple work items in the thread pool, with support for combining multiple operations and handling potentially complex error scenarios, and its Task abstraction can also represent inherently asynchronous operations. The next chapter describes C# language features that greatly simplify working with tasks.

1 I’m using the word state here broadly. I just mean information stored in variables and objects.

2 At the time of this writing, the documentation does not offer read-only thread safety guarantees for HashSet<T> and SortedSet<T>. Nonetheless, I have been assured by Microsoft that these also support concurrent reads.


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


16. Multithreading
17. Asynchronous Language Features
18. Memory Efficiency
24h 20m remaining
Chapter 17. Asynchronous Language Features
C# provides language-level support for using and implementing asynchronous methods. Asynchronous APIs are often the most efficient way to use certain services. For example, most I/O is handled asynchronously inside the OS kernel, because most peripherals, such as disk controllers or network adapters, are able to do the majority of their work autonomously. They need the CPU to be involved only at the start and end of each operation.

Although many of the services offered by operating systems are intrinsically asynchronous, developers often choose to use them through synchronous APIs (i.e., ones that do not return until the work is complete). This can waste resources, because they block the thread until the I/O completes. Threads have overheads, and if you’re aiming to get the best performance in a highly concurrent application (e.g., a web app serving large numbers of users), it’s usually best to have a relatively small number of OS threads. Ideally, your application would have no more OS threads than you have hardware threads, but that’s optimal only if you can ensure that threads only ever block when there’s no outstanding work for them to do. (Chapter 16 described the difference between OS threads and hardware threads.) The more threads that get blocked inside synchronous API calls, the more threads you’ll need to handle your workload, reducing efficiency. In performance-sensitive code, asynchronous APIs are useful, because instead of wasting resources by forcing a thread to sit and wait for I/O to complete, a thread can kick off the work and then do something else productive in the meantime.

The problem with asynchronous APIs is that they can be significantly more complex to use than synchronous ones, particularly if you need to coordinate multiple related operations and deal with errors. This was often why developers chose the less efficient synchronous alternatives back in the days before any mainstream programming languages provided built-in support. In 2012, C# and Visual Basic brought language-level support out of the research labs, and since then many other popular languages have added analogous features (most notably JavaScript, which acquired a very similar-looking syntax in 2016). The asynchronous features in C# make it possible to write code that uses efficient asynchronous APIs while retaining most of the simplicity of code that uses simpler synchronous APIs.

These language features are also useful in some scenarios in which maximizing throughput is not the primary performance goal. With client-side code, it’s important to avoid blocking the UI thread to maintain responsiveness, and asynchronous APIs provide one way to do that. The language support for asynchronous code can handle thread affinity issues, which greatly simplifies the job of writing highly responsive UI code.

Asynchronous Keywords: async and await
C# presents its support for asynchronous code through two keywords: async and await. Neither of these is not meant to be used on its own. You put the async keyword in a method’s declaration, and this tells the compiler that you intend to use asynchronous features in the method. If this keyword is not present, you are not allowed to use the await keyword.

This is arguably redundant—the compiler produces an error if you attempt to use await without async. If it knows when a method’s body is trying to use asynchronous features, why do we need to tell it explicitly? There are two reasons. First, as you’ll see, these features radically change the behavior of the code the compiler generates, so it’s useful for anyone reading the code to see a clear indication that the method behaves asynchronously. Second, await wasn’t always a keyword in C#, so developers were once free to use it as an identifier. Perhaps Microsoft could have designed the grammar for await so that it acts as a keyword only in very specific contexts, enabling you to continue to use it as an identifier in all other scenarios, but the C# team decided to take a slightly more coarse-grained approach: you cannot use await as an identifier inside an async method, but it’s a valid identifier anywhere else.

NOTE
The async keyword does not change the signature of the method. It determines how the method is compiled, not how it is used.

The program entry point is a special case. If you use top-level statements to avoid having to declare Main explicitly, there’s no place to put the async keyword or a return type, so this is the one case where the compiler deduces whether a method is asynchronous from whether you use await.

So the async keyword simply declares your intention to use the await keyword. (While you mustn’t use await without async anywhere other than in top-level statements, it’s not an error to apply the async keyword to a method that doesn’t use await. However, it would serve no purpose, so the compiler will generate a warning if you do this.) Example 17-1 shows a fairly typical example. This uses the HttpClient class to request just the headers for a particular resource (using the standard HEAD verb that the HTTP protocol defines for this purpose). It then displays the results in a UI control—this method is part of the codebehind for a UI that includes a TextBox named headerListTextBox.

Example 17-1. Using async and await when fetching HTTP headers

// Note: as you'll see later, async methods usually should not be void
private async void FetchAndShowHeaders(string url, IHttpClientFactory cf)
{
    using (HttpClient w = cf.CreateClient())
    {
        var req = new HttpRequestMessage(HttpMethod.Head, url);
        HttpResponseMessage response =
            await w.SendAsync(req, HttpCompletionOption.ResponseHeadersRead);

        headerListTextBox.Text = response.Headers.ToString();
    }
}
This code contains a single await expression, shown in bold. You use the await keyword in an expression that may take some time to produce a result, and it indicates that the remainder of the method should not execute until that operation is complete. This sounds a lot like what a blocking, synchronous API does, but the difference is that an await expression does not block the thread. This code is not quite what it seems.

The HttpClient class’s SendAsync method returns a Task<HttpResponseMessage>, and you might be wondering why we wouldn’t just use its Result property. As you saw in Chapter 16, if the task is not complete, this property blocks the thread until the result is available (or the task fails, in which case it will throw an exception instead). However, this is a dangerous thing to do in a UI application: if you block the UI thread by trying to read the Result of an incomplete task, you will prevent progress of any operations that need to run on that thread. Since a lot of the work that UI applications do needs to happen on the UI thread, blocking that thread in this way more or less guarantees that deadlock will occur sooner or later, causing the application to freeze. So don’t do that!

Although the await expression in Example 17-1 does something that is logically similar to reading Result, it works very differently. If the task’s result is not available immediately, the await keyword does not make the thread wait, despite what its name suggests. Instead, it causes the containing method to return. You can use a debugger to verify that FetchAndShowHeaders returns immediately. For example, if I call that method from the button click event handler shown in Example 17-2, I can put a breakpoint on the Debug.WriteLine call in that handler and another breakpoint on the code in Example 17-1 that will update the headerListTextBox.Text property.

Example 17-2. Calling the asynchronous method
private void fetchHeadersButton_Click(object sender, RoutedEventArgs e)
{
    FetchAndShowHeaders("https://endjin.com/", this.clientFactory);
    Debug.WriteLine("Method returned");
}
Running this in the debugger, I find that the code hits the breakpoint on the last statement of Example 17-2 before it hits the breakpoint on the final statement of Example 17-1. In other words, the section of Example 17-1 that follows the await expression runs after the method has returned to its caller. Evidently, the compiler is somehow arranging for the remainder of the method to be run via a callback that occurs once the asynchronous operation completes.

NOTE
Visual Studio’s debugger plays some tricks when you debug asynchronous methods to enable you to step through them as though they were normal methods. This is usually helpful, but it can sometimes conceal the true nature of execution. The debugging steps I just described were contrived to defeat Visual Studio’s attempts to be clever and instead to reveal what is really happening.

Notice that the code in Example 17-1 expects to run on the UI thread because it modifies the text box’s Text property toward the end. Asynchronous APIs do not necessarily guarantee to notify you of completion on the same thread on which you started the work—in fact, most won’t. Despite this, Example 17-1 works as intended, so as well as converting half of the method to a callback, the await keyword is handling thread affinity issues for us.

The C# compiler evidently performs some major surgery on your code each time you use the await keyword. In older versions of C#, if you wanted to use this asynchronous API and then update the UI, you would need to have written something like Example 17-3. This uses a technique I showed in Chapter 16: it sets up a continuation for the task returned by SendAsync, using a TaskScheduler to ensure that the continuation’s body runs on the UI thread.

Example 17-3. Manual asynchronous coding
private void OldSchoolFetchHeaders(string url, IHttpClientFactory cf)
{
    HttpClient w = cf.CreateClient();
    var req = new HttpRequestMessage(HttpMethod.Head, url);

    var uiScheduler = TaskScheduler.FromCurrentSynchronizationContext();
    w.SendAsync(req, HttpCompletionOption.ResponseHeadersRead)
        .ContinueWith(sendTask =>
        {
            try
            {
                HttpResponseMessage response = sendTask.Result;
                headerListTextBox.Text = response.Headers.ToString();
            }
            finally
            {
                w.Dispose();
            }
        },
        uiScheduler);
}
This is a reasonable way to use the TPL directly, and it has a similar effect to Example 17-1, although it’s not an exact representation of how the C# compiler transforms the code. As I’ll show later, await uses a pattern that is supported by, but does not require, Task or Task<T>. It also generates code that handles early completion (where the task has already finished by the time you’re ready to wait for it) far more efficiently than Example 17-3. But before I show the details of what the compiler does, I want to illustrate some of the problems it solves for you, which is best done by showing the kind of code you might have written back before this language feature existed.

My current example is pretty simple, because it involves only one asynchronous operation, but aside from the two steps I’ve already discussed—setting up some kind of completion callback and ensuring that it runs on the correct thread—I’ve also had to deal with the using statement that was in Example 17-1. Example 17-3 can’t use the using keyword, because we want to dispose the HttpClient object only after we’ve finished with it.1 Calling Dispose shortly before the outer method returns would not work, because we need to be able to use the object when the continuation runs, and that will typically happen a fair bit later. So I need to create the object in one method (the outer one) and then dispose of it in a different method (the nested one). And because I’m calling Dispose by hand, it’s now my problem to deal with exceptions, so I’ve had to wrap all of the code I moved into the callback with a try block and call Dispose in a finally block. (In fact, I’ve not even done a comprehensive job. In the unlikely event that either the HttpRequestMessage constructor or the call that retrieves the task scheduler were to throw an exception, the HttpClient would not get disposed. I’m handling only the case where the HTTP operation itself fails.)

Example 17-3 has used a task scheduler to arrange for the continuation to run via the SynchronizationContext that was current when the work started. This ensures that the callback occurs on the correct thread to update the UI. The await keyword can take care of that for us.

Execution and Synchronization Contexts
When your program’s execution reaches an await expression for an operation that doesn’t complete immediately, the code generated for that await will ensure that the current execution context has been captured. (It might not have to do much—if this is not the first await to block in this method, and if the context hasn’t changed since, it will have been captured already.) When the asynchronous operation completes, the remainder of your method will be executed through the execution context.2

As I described in Chapter 16, the execution context handles certain contextual information that needs to flow when one method invokes another (even when it does so indirectly). But there’s another kind of context that we may be interested in, particularly when writing UI code: the synchronization context (which was also described in Chapter 16).

While all await expressions capture the execution context, the decision of whether to flow synchronization context as well is controlled by the type being awaited. If you await for a Task, the synchronization context will also be captured by default. Tasks are not the only thing you can await, and I’ll describe how types can support await in the section “The await Pattern”.

Sometimes, you might want to avoid getting the synchronization context involved. If you want to perform asynchronous work starting from a UI thread, but you have no particular need to remain on that thread, scheduling every continuation through the synchronization context is unnecessary overhead. If the asynchronous operation is a Task or Task<T> (or the equivalent value types, ValueTask or ValueTask<T>), you can declare that you don’t want this by calling the ConfigureAwait method passing false. This returns a different representation of the asynchronous operation, and if you await that instead of the original task, it will ignore the current Syn⁠chr⁠oni⁠zat⁠ion​Con⁠text if there is one. (There’s no equivalent mechanism for opting out of the execution context.) Example 17-4 shows how to use this.

Example 17-4. ConfigureAwait

private async void OnFetchButtonClick(object sender, RoutedEventArgs e)
{
    using (HttpClient w = this.clientFactory.CreateClient())
    using (Stream f = File.Create(fileTextBox.Text))
    {
        Task<Stream> getStreamTask = w.GetStreamAsync(urlTextBox.Text);
        Stream getStream = await getStreamTask.ConfigureAwait(false);

        Task copyTask = getStream.CopyToAsync(f);
        await copyTask.ConfigureAwait(ConfigureAwaitOptions.None);
    }
}
This code is a click handler for a button, so it initially runs on a UI thread. It retrieves the Text property from a couple of text boxes. Then it kicks off some asynchronous work—fetching the content for a URL and copying the data into a file. It does not use any UI elements after fetching those two Text properties, so it doesn’t matter if the remainder of the method runs on some separate thread. By passing false to ConfigureAwait and waiting on the value it returns, we are telling the TPL that we are happy for it to use whatever thread is convenient to notify us of completion, which in this case will most likely be a thread pool thread. This will enable the work to complete more efficiently and more quickly, because it avoids getting the UI thread involved unnecessarily after each await.

You might have spotted that the final call to ConfigureAwait in Example 17-4 doesn’t pass false. .NET 8.0 added a new overload taking a ConfigureAwaitOptions. This enumeration type’s None and ContinueOnCapturedContext members provide the same behavior as false and true, and it also provides access to two new capabilities. We’ll look at one of these, SuppressThrowing, in “Error Handling”. The other, ForceYielding disables an optimization. Normally, in cases where the task has already completed (described in more detail in “The await Pattern”), await just allows the rest of the method to proceed immediately, but ForceYielding causes it to act as through the task had not completed. This typically causes the remainder of the method to run on a thread pool thread when it would otherwise have run on the caller’s thread. This might be useful if you know that after the await, you will be going on to perform CPU intensive work, or to call some slow API that does not offer an asynchronous form, and you don’t want that to tie up the caller’s thread. ConfigureAwaitOptions is a flags-style enumeration (with None having the value 0) so you can ask for combinations of these behaviors.

Not all asynchronous APIs return Task or Task<T>. For example, various asynchronous APIs introduced to Windows as part of UWP (an API for building desktop and tablet applications) return an IAsyncOperation<T> instead of Task<T>. This is because UWP is not .NET-specific, and it has its own runtime-independent representation for asynchronous operations that can also be used from C++ and JavaScript. This interface is conceptually similar to TPL tasks, and it supports the await pattern, meaning you can use await with these APIs. However, it does not provide Con⁠fig⁠ure​Awa⁠it. If you want to do something similar to Example 17-4 with one of these APIs, you can use the AsTask extension method that wraps an IAsyncOperation<T> as a Task<T>, and you can call ConfigureAwait on that task instead.

TIP
If you are writing libraries, then in most cases you should call ConfigureAwait(false) anywhere you use await. This is because continuing via the synchronization context can be expensive, and in some cases it can introduce the possibility of deadlock occurring. The only exceptions are when you are doing something that positively requires the synchronization context to be preserved, or you know for certain that your library will only ever be used in application frameworks that do not set up a synchronization context. (E.g., ASP.NET Core applications do not use synchronization contexts, so it generally doesn’t matter whether or not you call ConfigureAwait(false) in those.)

Example 17-1 contained just one await expression, and even that turned out to be fairly complex to reproduce with classic TPL programming. Example 17-4 contains two, and achieving equivalent behavior without the aid of the await keyword would require rather more code, because exceptions could occur before the first await, after the second, or between, and we’d need to call Dispose on the HttpClient and Stream in any of those cases (as well as in the case where no exception is thrown). However, things can get considerably more complex than that once flow control gets involved.

Multiple Operations and Loops
Suppose that instead of fetching headers, or just copying the HTTP response body to a file, I wanted to process the data in the body. If the body is large, retrieving it is an operation that could require multiple, slow steps. Example 17-5 fetches a web page gradually.

Example 17-5. Multiple asynchronous operations

private async void FetchAndShowBody(string url, IHttpClientFactory cf)
{
    using (HttpClient w = cf.CreateClient())
    {
        Stream body = await w.GetStreamAsync(url);
        using (var bodyTextReader = new StreamReader(body))
        {
            while (!bodyTextReader.EndOfStream)
            {
                string? line = await bodyTextReader.ReadLineAsync();
                bodyTextBox.AppendText(line);
                bodyTextBox.AppendText(Environment.NewLine);
                await Task.Delay(TimeSpan.FromMilliseconds(10));
            }
        }
    }
}
This now contains three await expressions. The first kicks off an HTTP GET request, and that operation will complete when we get the first part of the response, but the response might not be complete yet—there may be several megabytes of content to come. This code presumes that the content will be text, so it wraps the Stream object that comes back in a StreamReader, which presents the bytes in a stream as text.3 It then uses that wrapper’s asynchronous ReadLineAsync method to read text a line at a time from the response. Reading the first line may take a while because it will need to wait for the response to arrive over the network from the server, but the next few calls to this method will probably complete immediately, because each network packet we receive will typically contain multiple lines. But if the code can read faster than data arrives over the network, eventually it will have consumed all the lines that appeared in the first packet, and it will then take a while before the next line becomes available. So the calls to ReadLineAsync will return some tasks that are slow and some that complete immediately. The third asynchronous operation is a call to Task.Delay. I’ve added this to slow things down so that I can see the data arriving gradually in the UI. Task.Delay returns a Task that completes after the specified delay, so this provides an asynchronous equivalent to Thread.Sleep. (Thread.Sleep blocks the calling thread, but await Task.Delay introduces a delay without blocking the thread.)

NOTE
I’ve put each await expression in a separate statement, but this is not a requirement. It’s perfectly legal to write expressions of the form (await t1) + (await t2). (You can omit the parentheses if you like, because await has higher precedence than addition; I prefer the visual emphasis they provide here.)

I’m not going to show you the complete pre-async equivalent of Example 17-5, because it would be enormous, but I’ll describe some of the problems. First, we’ve got a loop with a body that contains two await blocks. To produce something equivalent with Task and callbacks means building your own loop constructs, because the code for the loop ends up being split across three methods: the one that starts the loop running (which would be the nested method acting as the continuation callback for GetStreamAsync) and the two callbacks that handle the completion of ReadLineAsync and Task.Delay. You can solve this by having a local method that starts a new iteration and calling that from two places: the point at which you want to start the loop and again in the Task.Delay continuation to kick off the next iteration. Example 17-6 shows this technique, but it illustrates just one aspect of what we’re expecting the compiler to do for us; it is not a complete alternative to Example 17-5.

Example 17-6. An incomplete manual asynchronous loop
private void IncompleteOldSchoolFetchAndShowBody(
    string url, IHttpClientFactory cf)
{
    HttpClient w = cf.CreateClient();
    var uiScheduler = TaskScheduler.FromCurrentSynchronizationContext();
    w.GetStreamAsync(url).ContinueWith(getStreamTask =>
    {
        Stream body = getStreamTask.Result;
        var bodyTextReader = new StreamReader(body);

        StartNextIteration();

        void StartNextIteration()
        {
            if (!bodyTextReader.EndOfStream)
            {
                bodyTextReader.ReadLineAsync().ContinueWith(readLineTask =>
                {
                    string? line = readLineTask.Result;

                    bodyTextBox.AppendText(line);
                    bodyTextBox.AppendText(Environment.NewLine);

                    Task.Delay(TimeSpan.FromMilliseconds(10))
                        .ContinueWith(
                            _ => StartNextIteration(), uiScheduler);
                },
                uiScheduler);
            }
        };
    },
    uiScheduler);
}
This code works after a fashion, but it doesn’t even attempt to dispose any of the resources it uses. There are several places in which failure could occur, so we can’t just put a single using block or try/finally pair in to clean things up. And even without that additional complication, the code is barely recognizable—it’s not obvious that this is attempting to perform the same basic operations as Example 17-5. With proper error handling, it would be completely unreadable. In practice, it would probably be easier to take a different approach entirely, writing a class that implements a state machine to keep track of where the work has gotten to. That will probably make it easier to produce code that operates correctly, but it’s not going to make it any easier for someone reading your code to understand that what they’re looking at is really little more than a loop at heart.

No wonder so many developers used to prefer synchronous APIs. But C# lets us write asynchronous code that has almost exactly the same structure as the synchronous equivalent, giving us all of the performance and responsiveness benefits of asynchronous code without the pain. That’s the main benefit of async and await in a nutshell.

Consuming and producing asynchronous sequences
Example 17-5 showed a while loop, and as you’d expect, you’re free to use other kinds of loops such as for and foreach in async methods. However, foreach can introduce a subtle problem: What happens if the collection you iterate over needs to perform slow operations? This doesn’t arise for collection types such as arrays or HashSet<T>, where all the collection’s items are already in memory, but what about the IEnumerable<string> returned by File.ReadLines? That’s an obvious candidate for asynchronous operation, but in practice, it will just block your thread each time it needs to wait for more data to arrive from storage. And that’s because the pattern expected by foreach doesn’t support asynchronous operation. The heart of the problem is the method foreach will call to move to the next item—it expects the enumerator (often, but not always an implementation of IEnumerator<T>) to provide a MoveNext method with a signature like the one shown in Example 17-7.

Example 17-7. The non-async-friendly IEnumerator.MoveNext
bool MoveNext();
If more items are forthcoming but are not yet available, collections have no choice but to block the thread, not returning from MoveNext until the data arrives. Fortunately, C# recognizes a variation on this pattern. The runtime libraries define a pair of types,4 shown in Example 17-8 (first introduced in Chapter 5), that embody this newer pattern. As with the synchronous IEnumerable<T>, foreach doesn’t strictly require these exact types. Anything offering members of the same signature will work.

Example 17-8. IAsyncEnumerable<T> and IAsyncEnumerator<T>
public interface IAsyncEnumerable<out T>
{
    IAsyncEnumerator<T> GetAsyncEnumerator(
        CancellationToken cancellationToken = default);
}

public interface IAsyncEnumerator<out T> : IAsyncDisposable
{
    T Current { get; }

    ValueTask<bool> MoveNextAsync();
}
Conceptually this is identical to the synchronous pattern: an asynchronous foreach will ask the collection object for an enumerator and will repeatedly ask it to advance to the next item, executing the loop body with the value returned by Current each time until the enumerator indicates that there are no more items. The main difference is that the synchronous MoveNext has been replaced by MoveNextAsync, which returns an awaitable ValueTask<T>. (The IAsyncEnumerable<T> interface also provides support for passing in a cancellation token. An asynchronous foreach won’t use that itself directly, but you can use this indirectly through the WithCancellation extension method for IAsyncEnumerable<T>.)

To consume an enumerable source that implements this pattern, you must put the await keyword in front of the foreach. C# can also help you to implement this pattern: Chapter 5 showed how you can use the yield keyword in an iterator method to implement IEnumerable<T>, but you can also return an IAs⁠ync​Enu⁠mer⁠abl⁠e<T>. Example 17-9 shows both implementation and consumption of IAsyncEnumerable<T> in action.

Example 17-9. Consuming and producing asynchronous enumerables
await foreach (string line in ReadLinesAsync(args[0]))
{
    Console.WriteLine(line);
}

static async IAsyncEnumerable<string> ReadLinesAsync(string path)
{
    using (var bodyTextReader = new StreamReader(path))
    {
        while (!bodyTextReader.EndOfStream)
        {
            string? line = await bodyTextReader.ReadLineAsync();
            if (line is not null) { yield return line; }
        }
    }
}
Since this language support makes creating and using IAsyncEnumerable<T> very similar to working with IEnumerable<T>, you might be wondering whether there are asynchronous versions of the various LINQ operators described in Chapter 10. Unlike LINQ to Objects, IAsyncEnumerable<T> implementations are not in the parts of the runtime libraries built into .NET or .NET Standard, but a suitable NuGet package is available. If you add a reference to the System.Linq.Async package, the usual using System.Linq; declaration will make all the LINQ operators available on IAsyncEnumerable<T> expressions.

While we’re looking at asynchronous equivalents of widely implemented types, we should look at IAsyncDisposable.

Asynchronous disposal
As Chapter 7 described, the IDisposable interface is implemented by types that need to perform some sort of cleanup promptly, such as closing an open handle, and there is language support in the form of using statements. But what if the cleanup involves potentially slow work, such as flushing data out to disk? .NET and .NET Standard 2.1 provide the IAsyncDisposable interface for this scenario. As Example 17-10 shows, you can put the await keyword in front of a using statement to consume an asynchronously disposable resource. (You can also put await in front of a using declaration.)

Example 17-10. Consuming and implementing IAsyncDisposable
await using (DiagnosticWriter w = new(@"c:\temp\log.txt"))
{
    await w.LogAsync("Test");
}

class DiagnosticWriter : IAsyncDisposable
{
    private StreamWriter? _sw;

    public DiagnosticWriter(string path)
    {
        _sw = new StreamWriter(path);
    }

    public Task LogAsync(string message)
    {
        ObjectDisposedException.ThrowIf(_sw is null, nameof(DiagnosticWriter));
        return _sw.WriteLineAsync(message);
    }

    public async ValueTask DisposeAsync()
    {
        if (_sw is not null)
        {
            await LogAsync("Done");
            await _sw.DisposeAsync();
            _sw = null;
        }
    }
}
NOTE
Although the await keyword appears in front of the using statement, the potentially slow operation that it awaits happens when execution leaves the using statement’s block. This is unavoidable since using statements and declarations effectively hide the call to Dispose.

Example 17-10 also shows how to implement IAsyncDisposable. Whereas the synchronous IDisposable defines a single Dispose method, its asynchronous counterpart defines a single DisposeAsync method that returns a ValueTask. This enables us to annotate the method with async. An await using statement will ensure that the task returned by DisposeAsync completes at the end of its block before execution continues. You may have noticed that we’ve used a few different return types for async methods. Iterators are a special case, just as they are in synchronous code, but what about these methods that return various task types?

Returning a Task
Any method that uses await could itself run slowly, so as well as being able to call asynchronous APIs, you will usually also want to present an asynchronous public face. The C# compiler enables methods marked with the async keyword to return an object that represents the asynchronous work in progress. Instead of returning void, you can return a Task, or you can return a Task<T>, where T is any type. This enables callers to discover the status of the work your method performs, it provides the opportunity to attach continuations, and if you use Task<T>, it offers a way to get the result. Alternatively, you can return the value type equivalents, ValueTask and ValueTask<T>. Returning any of these means that if your method is called from another async method, it can use await to wait for your method to complete and, if applicable, to collect its result.

Returning a task is almost always preferable to void when using async because with a void return type, there’s no way for callers to know when your method has really finished, or to discover when it throws an exception. (Asynchronous methods can continue to run after returning—in fact, that’s the whole point—so by the time you throw an exception, the original caller will probably not be on the stack.) By returning a task object, you provide the compiler with a way to make exceptions available and, where applicable, a way to provide a result.

Returning a task is so trivially easy that there’s very little reason not to. To modify the method in Example 17-5 to return a task, I only need to make a single change. I make the return type Task instead of void, as shown in Example 17-11, and the rest of the code can remain exactly the same.

Example 17-11. Returning a Task
private async Task FetchAndShowBody(string url, IHttpClientFactory cf)
// ...as before
The compiler automatically generates the code required to produce a Task object (or a ValueTask, if you use that as your return type) and set it into a completed or faulted state when the method either returns or throws an exception. A return type of Task is the asynchronous equivalent of void, since the Task produces no result when it completes (which is why we don’t need to add a return statement to this method even though it now has a return type of Task). And if you want to return a result from your task, that’s also easy. Make the return type Task<T> or ValueTask<T>, where T is your result type, and then you can use the return keyword as though your method were a normal, non-async method, as Example 17-12 shows.

Example 17-12. Returning a Task<T>

public static async Task<string?> GetServerHeaderAsync(
    string url, IHttpClientFactory cf)
{
    using (HttpClient w = cf.CreateClient())
    {
        var request = new HttpRequestMessage(HttpMethod.Head, url);
        HttpResponseMessage response = await w.SendAsync(
            request, HttpCompletionOption.ResponseHeadersRead);

        string? result = null;
        IEnumerable<string>? values;
        if (response.Headers.TryGetValues("Server", out values))
        {
            result = values.FirstOrDefault();
        }
        return result;
    }
}
This fetches HTTP headers asynchronously in the same way as Example 17-1, but instead of displaying the results, this picks out the value of the first Server: header and makes that the result of the Task<string?> that this method returns. (It needs to be a nullable string because the header might not be present.) As you can see, the return statement just returns a string?, even though the method’s return type is Task<string?>. The compiler generates code that completes the task and arranges for that string to be the result. With either a Task or Task<T> return type, the generated code produces a task similar to the kind you would get using Task​Com⁠ple⁠tio⁠nSo⁠urc⁠e<T>, as described in Chapter 16.

NOTE
Just as the await keyword can use any asynchronous method that fits a particular pattern (described later), C# offers the same flexibility when it comes to implementing an asynchronous method. You are not limited to Task, Task<T>, ValueTask, and ValueTask<T>. You can return any type that meets two conditions: it must be annotated with the AsyncMethodBuilder attribute, identifying a class that the compiler can use to manage the progress and completion of the task, and it must also offer a GetAwaiter method that returns a type implementing the INotifyCompletion interface.

There’s very little downside to returning one of the built-in task types. Callers are not obliged to do anything with it, so your method will be just as easy to use as a void method but with the added advantage that a task is available to callers that want one. About the only reason for returning void would be if some external constraint forces your method to have a particular signature. For example, most event handlers are required to have a return type of void—that’s why some of my earlier examples did it. But unless you are forced to use it, void is not a recommended return type for an asynchronous method.

The program entry point (typically called Main) is a special case. The .NET runtime doesn’t support asynchronous entry points, and it expects this method to return either void or int. Despite this, C# lets Main return either Task or Task<int>, in which case the C# compiler will generate a hidden method that acts as the real entry point. This calls your asynchronous Main and then blocks until the task it returns completes. This makes it possible for Main to be async (although the compiler will generate the wrapper when you use these return types even if you don’t make the method async). If you use top-level statements, there will be no explicit declaration of Main, but if you use await in these statements, the compiler will choose a return type of Task, or, if you use a return statement to produce an exit code, Task<int>.

Applying async to Nested Methods
In the examples shown so far, I have applied the async keyword to ordinary methods. You can also use it on anonymous functions (either anonymous methods or lambdas) and local functions. For example, if you’re writing a program that creates UI elements programmatically, you may find it convenient to attach event handlers written as lambdas, and you might want to make some of those asynchronous, as Example 17-13 does.

Example 17-13. An asynchronous lambda
okButton.Click += async (s, e) =>
{
    using (HttpClient w = this.clientFactory.CreateClient())
    {
        infoTextBlock.Text = await w.GetStringAsync(uriTextBox.Text);
    }
};
The await Pattern
The majority of the asynchronous APIs that support the await keyword will return a TPL task of some kind. However, C# does not absolutely require this. It will await anything that implements a particular pattern. Moreover, although Task supports this pattern, the way it works means that the compiler uses tasks in a slightly different way than you would when using the TPL directly—this is partly why I said earlier that the code showing task-based asynchronous equivalents to await-based code did not represent exactly what the compiler does. In this section, I’m going to show how the compiler uses tasks and other types that support await to better illustrate how it really works.

I’ll create a custom implementation of the await pattern to show what the C# compiler expects. Example 17-14 shows an asynchronous method, UseCustomAsync, that uses this custom implementation. It assigns the result of the await expression into a string, so it clearly expects the asynchronous operation to produce a string as its output. It calls a method, CustomAsync, which returns our implementation of the pattern (which will be shown later in Example 17-15). As you can see, this is not a Task<string>.

Example 17-14. Calling a custom awaitable implementation
static async Task UseCustomAsync()
{
    string result = await CustomAsync();
    Console.WriteLine(result);
}

public static MyAwaitableType CustomAsync()
{
    return new MyAwaitableType();
}
The compiler expects the await keyword’s operand to be a type that provides a method called GetAwaiter. This can be an ordinary instance member or an extension method. (So it is possible to make await work with a type that does not support it innately by defining a suitable extension method.) This method must return an object or value, known as an awaiter, that does three things.

First, the awaiter must provide a bool property called IsCompleted. The code that the compiler generates for the await uses this to discover whether the operation has already finished. In situations where no slow work needs to be done (e.g., when a call to ReadAsync on a Stream can be handled immediately with data that the stream already has in a buffer), it would be a waste to set up a callback. So await avoids creating an unnecessary delegate if the IsCompleted property returns true, and it will just continue straight on with the remainder of the method. (Passing ConfigureAwaitOptions.ForceYielding to ConfigureAwait defeats this optimization by supplying an awaiter where IsCompleted initially returns false even when the underlying task has in fact completed.)

The compiler also requires a way to get the result once the work is complete, so the awaiter must have a GetResult method. Its return type defines the result type of the operation—it will be the type of the await expression. (If there is no result, the return type is void. GetResult still needs to be present, because it is responsible for throwing exceptions if the operation fails.) Since Example 17-14 assigns the result of the await into a variable of type string, the GetResult method of the awaiter returned by the MyAwaitableType class’s GetAwaiter must be string (or some type implicitly convertible to string).

Finally, the compiler needs to be able to supply a callback. If IsCompleted returns false, indicating that the operation is not yet complete, the code generated for the await expression will create a delegate that will run the rest of the method. It needs to be able to pass that to the awaiter. (This is similar to passing a delegate to a task’s ContinueWith method.) For this, the compiler requires not just a method but also an interface. You are required to implement INotifyCompletion, and there’s an optional interface that it’s recommended you also implement where possible called ICriticalNotifyCompletion. These do similar things: each defines a single method (OnCompleted and UnsafeOnCompleted, respectively) that takes a single Action delegate, and the awaiter must invoke this delegate once the operation completes. The distinction between these two interfaces and their corresponding methods is that the first requires the awaiter to flow the current execution context to the target method, whereas the latter does not. The .NET runtime libraries features that the C# compiler uses to help build asynchronous methods always flow the execution context for you, so the generated code typically calls UnsafeOnCompleted where available to avoid flowing it twice. (If the compiler used OnCompleted, the awaiter would flow context too.) However, on .NET Framework, you’ll find that security constraints may prevent the use of UnsafeOnCompleted. (.NET Framework had a concept of untrusted code. Code from potentially untrustworthy origins—perhaps because it was downloaded from the internet—would be subject to various constraints. This concept was dropped in .NET, but various vestiges remain, such as this design detail of asynchronous operations.) Because UnsafeOnCompleted does not flow execution context, untrusted code must not be allowed to call it, because that would provide a way to bypass certain security mechanisms. .NET Framework implementations of UnsafeOnCompleted provided for the various task types are marked with the SecurityCriticalAttribute, which means that only fully trusted code can call it. We need OnCompleted so that partially trusted code is able to use the awaiter.

Example 17-15 shows the minimum viable implementation of the awaiter pattern. This is oversimplified, because it always completes synchronously, so its OnCompleted method doesn’t do anything. If you use the await keyword on an instance of My​Awa⁠ita⁠ble⁠Type, the code that the C# compiler generates will never call OnCompleted. The await pattern requires that OnCompleted is only called if IsCompleted returns false, and, in this example, IsCompleted always returns true. This is why I’ve made OnCompleted throw an exception. However, although this example is unrealistically simple, it will serve to illustrate what await does.

Example 17-15. An excessively simple await pattern implementation
public class MyAwaitableType
{
    public MinimalAwaiter GetAwaiter()
    {
        return new MinimalAwaiter();
    }

    public class MinimalAwaiter : INotifyCompletion
    {
        public bool IsCompleted => true;

        public string GetResult() => "This is a result";

        public void OnCompleted(Action continuation)
        {
            throw new NotImplementedException();
        }
    }
}
With this code in place, we can see what Example 17-14 will do. It will call Get​Awai⁠ter on the MyAwaitableType instance returned by the CustomAsync method. Then it will test the awaiter’s IsCompleted property, and if it’s true (which it will be), it will run the rest of the method immediately. The compiler doesn’t know IsCompleted will always be true in this case, so it generates code to handle the false case. This will create a delegate that, when invoked, will run the rest of the method and pass that delegate to the waiter’s OnCompleted method. (I’ve not provided UnsafeOnCompleted here, so it is forced to use OnCompleted.) Example 17-16 shows code that does all of this.

Example 17-16. A very rough approximation of what await does
static void ManualUseCustomAsync()
{
    var awaiter = CustomAsync().GetAwaiter();
    if (awaiter.IsCompleted)
    {
        TheRest(awaiter);
    }
    else
    {
        awaiter.OnCompleted(() => TheRest(awaiter));
    }
}

private static void TheRest(MyAwaitableType.MinimalAwaiter awaiter)
{
    string result = awaiter.GetResult();
    Console.WriteLine(result);
}
I’ve split the method into two pieces, because the C# compiler avoids creating a delegate in the case where IsCompleted is true, and I wanted to do the same. However, this is not quite what the C# compiler does—it also manages to avoid creating an extra method for each await statement, but this means it has to create considerably more complex code. In fact, for methods that just contain a single await, it introduces rather more overhead than Example 17-16. However, once the number of await expressions starts to increase, the complexity pays off, because the compiler does not need to add any further methods. Example 17-17 shows something closer to what the compiler does.

Example 17-17. A slightly closer approximation to how await works
private class ManualUseCustomAsyncState
{
    private int state;
    private MyAwaitableType.MinimalAwaiter? awaiter;

    public void MoveNext()
    {
        if (state == 0)
        {
            awaiter = CustomAsync().GetAwaiter();
            if (!awaiter.IsCompleted)
            {
                state = 1;
                awaiter.OnCompleted(MoveNext);
                return;
            }
        }
        string result = awaiter!.GetResult();
        Console.WriteLine(result);
    }
}

static void ManualUseCustomAsync()
{
    var s = new ManualUseCustomAsyncState();
    s.MoveNext();
}
This is still simpler than the real code, but it shows the basic strategy: the compiler generates a nested type that acts as a state machine. This has a field (state) that keeps track of where the method has got to so far, and it also contains fields corresponding to the method’s local variables (just the awaiter variable in this example). When an asynchronous operation does not block (i.e., its IsCompleted returns true immediately), the method can just continue to the next part, but once it encounters an operation that needs some time, it updates the state variable to remember where it is and then uses the relevant awaiter’s OnCompleted method. Notice that the method it asks to be called on completion is the same one that is already running: MoveNext. And this continues to be the case no matter how many awaits you need to perform—every completion callback invokes the same method; the class simply remembers how far it had already gotten, and the method picks up from there. That way, no matter how many times an await blocks, it never needs to create more than one delegate.

I won’t show the real generated code. It is borderline unreadable, because it contains a lot of unspeakable identifiers. (Remember from Chapter 3 that when the C# compiler needs to generate items with identifiers that must not collide with or be directly visible to our code, it creates a name that the runtime considers legal but that is not legal in C#; this is called an unspeakable name.) Moreover, the compiler-generated code uses various helper classes from the System.Runtime.CompilerServices namespace that are intended for use only from asynchronous methods to manage things like determining which of the completion interfaces the awaiter supports and handling the related execution context flow. Also, if the method returns a task, there are additional helpers to create and update that. But when it comes to understanding the nature of the relationship between an awaitable type and the code the compiler produces for an await expression, Example 17-17 gives a fair impression.

Error Handling
The await keyword deals with exceptions much as you’d hope it would: if an asynchronous operation fails, the exception emerges from the await expression that was consuming that operation. The general principle that asynchronous code can be structured in the same way as ordinary synchronous code continues to apply in the face of exceptions, and the compiler does whatever work is required to make that possible.

Example 17-18 contains two asynchronous operations, one of which occurs in a loop. This is similar to Example 17-5. It does something a bit different with the content it fetches, but most importantly, it returns a task. This provides a place for an error to go if any of the operations should fail.

Example 17-18. Multiple potential points of failure
private static async Task<string> FindLongestLineAsync(
    string url, IHttpClientFactory cf)
{
    using (HttpClient w = cf.CreateClient())
    {
        Stream body = await w.GetStreamAsync(url);
        using (var bodyTextReader = new StreamReader(body))
        {
            string longestLine = string.Empty;
            while (!bodyTextReader.EndOfStream)
            {
                string? line = await bodyTextReader.ReadLineAsync();
                if (line is not null && line.Length > longestLine.Length)
                {
                    longestLine = line;
                }
            }
            return longestLine;
        }
    }
}
Exceptions are potentially challenging with asynchronous operations because by the time a failure occurs, the method call that originally started the work is likely to have returned. The FindLongestLineAsync method in this example will usually return as soon as it executes the first await expression. (It’s possible that it won’t—if HTTP caching is in use, or if the IHttpClientFactory returns a client configured as a fake that never makes any real requests, this operation could succeed immediately. But typically, that operation will take some time, causing the method to return.) Suppose this operation succeeds and the rest of the method starts to run, but partway through the loop that retrieves the body of the response, the computer loses network connectivity. This will cause one of the operations started by ReadLineAsync to fail.

An exception will emerge from the await for that operation. There is no exception handling in this method, so what should happen next? Normally, you’d expect the exception to start working its way up the stack, but what’s above this method on the stack? It almost certainly won’t be the code that originally called it—remember, the method will usually return as soon as it hits the first await, so at this stage, we’re running as a result of being called back by the awaiter for the task returned by ReadLineAsync. Chances are, we’ll be running on some thread from the thread pool, and the code directly above us in the stack will be part of the task awaiter. This won’t know what to do with our exception.

But the exception does not propagate up the stack. When an exception goes unhandled in an async method that returns a task, the compiler-generated code catches it and puts the task returned by that method into a faulted state (which will in turn mean that anything that was waiting for that task can now continue). If the code that called FindLongestLineAsync is working directly with the TPL, it will be able to see the exception by detecting that faulted state and retrieving the task’s Exception property. Alternatively, it can either call Wait or fetch the task’s Result property, and in either case, the task will throw an AggregateException containing the original exception. But if the code calling FindLongestLineAsync uses await on the task we return, the exception gets rethrown from that. From the calling code’s point of view, it looks just like the exception emerged as it would normally, as Example 17-19 shows.

Example 17-19. Handling exceptions from await
try
{
    string longest = await FindLongestLineAsync(
        "http://192.168.22.1/", this.clientFactory);
    Console.WriteLine($"Longest line: {longest}");
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"Error fetching page: {ex.Message}");
}
This is almost deceptively simple. Remember that the compiler performs substantial restructuring of the code around each await, and the execution of what looks like a single method may involve multiple calls in practice. So preserving the semantics of even a simple exception handling block like this (or related constructs, such as a using statement) is nontrivial. If you have ever attempted to write equivalent error handling for asynchronous work without the help of the compiler, you’ll appreciate how much C# is doing for you here.

NOTE
The await does not rethrow the AggregateException provided by the task’s Exception property. It rethrows the original exception. This enables async methods to handle the error in the same way synchronous code would.

Validating Arguments
There’s one potentially surprising aspect of the way C# automatically reports exceptions through the task your asynchronous method returns. It means that code such as that in Example 17-20 doesn’t do what you might expect.

Example 17-20. Potentially surprising argument validation
public async Task<string> FindLongestLineAsync(string url)
{
    ArgumentNullException.ThrowIfNull(url);
    ...
Inside an async method, the compiler treats all exceptions in the same way: none are allowed to pass up the stack as they would with a normal method, and they will always be reported by faulting the returned task. This is true even of exceptions thrown before the first await. In this example, the argument validation happens before the method does anything else, so at that stage, we will still be running on the original caller’s thread. You might have thought that an argument exception thrown by this part of the code would propagate directly back to the caller. In fact, the caller will see a nonexceptional return, producing a task that is in a faulted state.

If the calling method immediately calls await on the return task, this won’t matter much—it will see the exception in any case. But some code may choose not to wait immediately, in which case it won’t see the argument exception until later. For simple argument validation exceptions where the caller has clearly made a programming error, you might expect code to throw an exception immediately, but this code doesn’t do that.

NOTE
If it’s not possible to determine whether a particular argument is valid without performing slow work, you will not be able to throw immediately if you want a truly asynchronous method. In that case, you would need to decide whether you would rather have the method block until it can validate all arguments or have argument exceptions be reported via the returned task instead of being thrown immediately.

Most async methods work this way, but suppose you want to throw this kind of exception straightaway (e.g., because it’s being called from code that does not immediately await the result, and you’d like to discover the problem as soon as possible). The usual technique is to write a normal method that validates the arguments before calling an async method that does the work, and to make that second method either private or local. (You would have to do something similar to perform immediate argument validation with iterators too, incidentally. Iterators were described in Chapter 5.) Example 17-21 shows such a public wrapper method and the start of the method it calls to do the real work.

Example 17-21. Validating arguments for async methods
public static Task<string> FindLongestLineAsync(string url)
{
    ArgumentNullException.ThrowIfNull(url);
    return FindLongestLineCore(url);

    static async Task<string> FindLongestLineCore(string url)
    {
        ...
    }
}
Because the public method is not marked with async, any exceptions it throws will propagate directly to the caller. But any failures that occur once the work is underway in the local method will be reported through the task.

I’ve chosen to forward the url argument to the local method. I didn’t have to, because a local method can access its containing method’s variables. However, relying on that causes the compiler to create a type to hold the locals to share them across the methods. Where possible, it will make this a value type, passing it by reference to the inner type, but in cases where the inner method’s scope might outlive the outer method, it can’t do that. And since the local method here is async, it is likely to continue to run long after the outer method’s stack frame no longer exists, so this would cause the compiler to create a reference type just to hold that url argument. By passing the argument in, we avoid this (and I’ve marked the method as static to indicate that this is my intent—this means the compiler will produce an error if I inadvertently use anything from the outer method in the local one). The compiler will probably still have to generate code that creates an object to hold on to local variables in the inner method during asynchronous execution, but at least we’ve avoided creating more objects than necessary.

Singular and Multiple Exceptions
As Chapter 16 showed, the TPL defines a model for reporting multiple errors—a task’s Exception property returns an AggregateException. Even if there is only a single failure, you still have to extract it from its containing AggregateException. However, if you use the await keyword, it does this for you—as you saw in Example 17-19, it retrieves the first exception in the InnerExceptions and rethrows that.

This is handy when the operation can produce only a single failure—it saves you from having to write additional code to handle the aggregate exception and then dig out the contents. (If you’re using a task returned by an async method, it will never contain more than one exception.) However, it does present a problem if you’re working with composite tasks that can fail in multiple ways simultaneously. For example, Task.WhenAll takes a collection of tasks and returns a single task that completes only when all its constituent tasks complete. If some of them complete by failing, you’ll get an AggregateException that contains multiple errors. If you use await with such an operation, it will throw only the first of those exceptions back to you.

The usual TPL mechanisms—the Wait method or the Result property—provide the complete set of errors (by throwing the AggregateException itself instead of its first inner exception), but they both block the thread if the task is not yet complete. What if you want the efficient asynchronous operation of await, which uses threads only when there’s something for them to do, but you still want to see all the errors? Example 17-22 shows one approach.

Example 17-22. Throwless awaiting followed by Wait
static async Task CatchAll(Task[] ts)
{
    try
    {
        var t = Task.WhenAll(ts);
        await t.ConfigureAwait(ConfigureAwaitOptions.SuppressThrowing);
        t.Wait();
    }
    catch (AggregateException all)
    {
        Console.WriteLine(all);
    }
}
This uses await to take advantage of the efficient nature of asynchronous C# methods, but it uses a new feature of .NET 8.0 to indicate that if the task faults, we don’t want an exception to be thrown. The call to Wait will throw an AggregateException if anything failed, enabling the catch block to see all of the exceptions. And because we call Wait only after the await completes, we know the task is already finished, so the call will not block. (Alternatively, we could have not called Wait at all. After the await we could check t.IsFaulted to see if it failed, and get the exception with t.Exception if it did.)

Concurrent Operations and Missed Exceptions
The most straightforward way to use await is to do one thing after another, just as you would with synchronous code. Although doing work strictly sequentially may not sound like it takes full advantage of the potential of asynchronous code, it does make much more efficient use of the available threads than the synchronous equivalent, and it also works well in client-side UI code, leaving the UI thread free to respond to input even while work is then in progress. However, you might want to go further.

It is possible to kick off multiple pieces of work simultaneously. You can call an asynchronous API, and instead of using await immediately, you can store the result in a variable and then start another piece of work before waiting for both. Although this is a viable technique, and might reduce the overall execution time of your operations, there’s a trap for the unwary, shown in Example 17-23.

Example 17-23. How not to run multiple concurrent operations
static async Task GetSeveral(IHttpClientFactory cf)
{
    using (HttpClient w = cf.CreateClient())
    {
        w.MaxResponseContentBufferSize = 2_000_000;

        Task<string> g1 = w.GetStringAsync("https://endjin.com/");
        Task<string> g2 = w.GetStringAsync("https://oreilly.com");

        // BAD!
        Console.WriteLine((await g1).Length);
        Console.WriteLine((await g2).Length);
    }
}
This fetches content from two URLs concurrently. Having started both pieces of work, it uses two await expressions to collect the results of each and to display the lengths of the resulting strings. If the operations succeed, this will work, but it doesn’t handle errors well. If the first operation fails, the code will never get as far as executing the second await. This means that if the second operation also fails, nothing will look at the exception it throws. Eventually, the TPL will detect that the exception has gone unobserved, which will result in the UnobservedTaskException event being raised. (Chapter 16 discussed the TPL’s unobserved exception handling.) The problem is that this will happen only very occasionally—it requires both operations to fail in quick succession—so it’s something that would be very easy to miss in testing.

You could avoid this with careful exception handling—you could catch any exceptions that emerge from the first await before going on to execute the second, for example. Alternatively, you could use Task.WhenAll to wait for all the tasks as a single operation—this will produce a faulted task with an AggregateException if anything fails, enabling you to see all errors. Of course, as you saw in the preceding section, multiple failures of this kind are awkward to deal with when you’re using await. But if you want to launch multiple asynchronous operations and have them all in flight simultaneously, you’re going to need more complex code to coordinate the results than you would do when performing work sequentially. Even so, the await and async keywords still make life much easier.

Summary
Asynchronous operations do not block the thread from which they are invoked. This can make them more efficient than synchronous APIs, which is particularly important on heavily loaded machines. It also makes them suitable for use on the client side, because they enable you to perform long-running work without causing the UI to become unresponsive. Without language support, asynchronous operations can be complex to use correctly, particularly when handling errors across multiple related operations. C#’s await keyword enables you to write asynchronous code in a style that looks just like normal synchronous code. It gets a little more complex if you want a single method to manage multiple concurrent operations, but even if you write an asynchronous method that does things strictly in order, you will get the benefits of making much more efficient use of threads in a server application—it will be able to support more simultaneous users, because each individual operation uses fewer resources—and on the client side, you’ll get the benefit of a more responsive UI.

Methods that use await must be marked with the async keyword and should usually return one of Task, Task<T>, ValueTask, or ValueTask<T>. (C# allows a void return type, but you would normally use this only when you have no choice.) The compiler will arrange for this task to complete successfully once your method returns, or to complete with a fault if your method fails at any point in its execution. Because await can consume any Task or Task<T>, this makes it easy to split asynchronous logic across multiple methods, because a high-level method can await a lower-level async method. Usually, the work eventually ends up being performed by some task-based API, but it doesn’t have to be, because await only demands a certain pattern—it will accept any expression on which you can invoke a GetWaiter method to obtain a suitable type.

1 This example is a bit contrived so that I can illustrate how using works in async methods. Disposing an HttpClient obtained from an IHttpClientFactory is normally optional, and in cases where you new up an HttpClient directly, it’s better to hang on to it and reuse it, as discussed in “Optional Disposal”.

2 As it happens, Example 17-3 does this too, because the TPL captures the execution context for us.

3 Strictly speaking, I should inspect the HTTP response headers to discover the encoding, and configure the StreamReader with that. Instead, I’m letting it detect the encoding, which will work well enough for demonstration purposes.

4 These are available in .NET and .NET Standard 2.1. With .NET Framework, you will need to use the Microsoft.Bcl.AsyncInterfaces NuGet package.


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


17. Asynchronous Language Features
18. Memory Efficiency
About the Author
24h 20m remaining
Chapter 18. Memory Efficiency
As Chapter 7 described, the CLR is able to perform automatic memory management thanks to its garbage collector (GC). This comes at a price: when a CPU spends time on garbage collection, that stops it from getting on with more productive work. On laptops and phones, GC work drains power from the battery. In a cloud computing environment where you may be paying for CPU time based on consumption, extra work for the CPU corresponds directly to increased costs. More subtly, on a computer with many cores, spending too much time in the GC can significantly reduce throughput, because many of the cores may end up blocked, waiting for the GC to complete before they can proceed.

In many cases, these effects will be small enough not to cause visible problems. However, when certain kinds of programs experience heavy load, GC costs can come to dominate the overall execution time. In particular, if you write code that performs relatively simple but highly repetitive processing, GC overhead can have a substantial impact on throughput.

To give you an example of the kinds of improvements that can sometimes be possible, early versions of Microsoft’s ASP.NET Core web server framework frequently ran into hard limits due to GC overhead. To enable .NET applications to break through these barriers, C# introduced various features that can enable dramatic reductions in the number of allocations. Fewer allocations means fewer blocks of memory for the GC to recover, so this translates directly to lower GC overhead. When ASP.NET Core first started making extensive use of these features, performance improved across the board, but for the simplest performance benchmark, known as plaintext (part of the TechEmpower suite of web performance tests), this release improved the request handling rate by over 25%.

In some specialized scenarios, the differences can be even greater. I worked on a project that processed diagnostic information from a broadband provider’s networking equipment (in the form of RADIUS packets). Adopting the techniques described in this chapter boosted the rate at which a single CPU core in our system could process the messages from around 300,000/s to about 7 million/s.

There is a price to pay, of course: these GC-efficient techniques can add significant complication to your code. And the payoff won’t always be so large—although the first ASP.NET Core release to be able to use these features improved over the previous version on all benchmarks, only the simplest saw a 25% boost, and most improved more modestly. The practical improvement will really depend on the nature of your workload, and for some applications you might find that applying these techniques delivers no measurable improvement. So before you even consider using them, you should use performance monitoring tools to find out how much time your code spends in the GC. If it’s only a few percent, then you might not be able to realize order-of-magnitude improvements. But if testing suggests that there’s room for significant improvement, the next step is to ask whether the techniques in this chapter are likely to help. So let’s start by exploring exactly how these techniques can help you reduce GC overhead.

(Don’t) Copy That
The way to reduce GC overhead is to allocate less memory on the heap. And the most important technique for minimizing allocations is to avoid making copies of data. For example, consider the URL http://example.com/books/1323?edition=6&format=pdf. There are several elements of interest in here, such as the protocol (http), the hostname (example.com), or the query string. The latter has its own structure: it is a sequence of name/value pairs. The obvious way to work with a URL in .NET is to use the System.Uri type, as Example 18-1 shows.

Example 18-1. Deconstructing a URL
var uri = new Uri("http://example.com/books/1323?edition=6&format=pdf");
Console.WriteLine(uri.Scheme);
Console.WriteLine(uri.Host);
Console.WriteLine(uri.AbsolutePath);
Console.WriteLine(uri.Query);
It produces the following output:

http
example.com
/books/1323
?edition=6&format=pdf
This is convenient, but by getting the values of these four properties, we have forced the Uri to provide four string objects in addition to the original one. You could imagine a smart implementation of Uri that recognized certain standard values for Scheme, such as http, and that always returned the same string instance for these instead of allocating new ones, but for all the other parts, it’s likely to have to allocate new strings on the heap.

There is another way. Instead of creating new string objects for each section, we could take advantage of the fact that all of the information we want was already in the string containing the whole URL. There’s no need to copy each section into a new string, when instead we can just keep track of the position and lengths of the relevant sections within the string. Instead of creating a string for each section, we would need just two numbers. And since we can represent numbers using value types (e.g., int or, for very long strings, long), we don’t need any additional objects on the heap beyond the single string with the full URL. For example, the scheme (http) is at position 0 and has length 4. Figure 18-1 shows each of the elements by their offset and position within the string.


Figure 18-1. URL substrings
This works, but already we can see the first problem with working this way: it is somewhat awkward. Instead of representing, say, the Host with a convenient string object, which is easily understood and readily inspected in the debugger, we now have a pair of numbers, and as developers, we now have to remember which string they point into. It’s not rocket science, but it makes it slightly harder to understand our code, and easier to introduce bugs. But there’s a payoff: instead of five strings (the original URL and the four properties), we just have one. And if you’re trying to process millions of events each second, that could easily be worth the effort.

Obviously this technique would work for a more fine-grained structure too. The offset and position (25, 4) locates the text 1323 in this URL. We might want to parse that as an int. But at this point we run into the second problem with this style of working: it is not widely supported in .NET libraries. The usual way to parse text into an int is to use the int type’s static Parse or TryParse methods. Unfortunately, these do not provide overloads that accept a position or offset within a string. They require a string containing only the number to be parsed. This means you end up writing code such as Example 18-2.

Example 18-2. Defeating the point of the exercise by using Substring
string uriString = "http://example.com/books/1323?edition=6&format=pdf";
int id = int.Parse(uriString.Substring(25, 4));
This works, but by using Substring to go from our (offset, length) representation back to the plain string that int.Parse wants, we’ve allocated a new string. The whole point of this exercise was to reduce allocations, so this doesn’t seem like progress. One solution might be for Microsoft to go through the entire .NET API surface area, adding overloads that accept offset and length parameters in any situation where we might want to work with something in the middle of something else (either a substring, as in this example, or perhaps a subrange of an array). In fact, there are examples of this already: the Stream API for working with byte streams has various methods that accept a byte[] array, and also offset and length arguments to indicate exactly which part of the array you want to work with.

However, there’s one more problem with this technique: it is inflexible about the type of container that the data lives in. Microsoft could add an overload to int.Parse that takes a string, an offset, and a length, but it would only be able to parse data inside a string. What if the data happens to be in a char[]? In that case, you’d have to convert it to a string first, at which point we’re back to additional allocations. Alternatively, every API that wants to support this approach would need multiple overloads to support all the containers that anyone might want to use, each potentially requiring a different implementation of the same basic method.

More subtly, what if the data you have is currently in memory that’s not on the CLR’s heap? This is a particularly important question when it comes to the performance of servers that accept requests over the network (e.g., a web server). Sometimes, data received by a network interface won’t be delivered directly into memory on .NET’s heap. Also, some forms of interprocess communication involve arranging for the OS to map a particular region of memory into two different processes’ address spaces. The .NET heap is local to the process and cannot use such memory.

C# has always supported use of external memory through unsafe code, which supports raw unmanaged pointers that work in a similar way to pointers in the C and C++ languages. However, there are a couple of problems with these. First, they would add yet another entry to the list of overloads that everything would need to support in a world where we can parse data in place. Second, code using pointers cannot pass .NET’s type safety verification rules. This means it becomes possible to make certain kinds of programming errors that are normally impossible in C#. It may also mean that the code will not be allowed to run in certain scenarios, since the loss of type safety would enable unsafe code to bypass certain security constraints.

To summarize, it has always been possible to reduce allocations and copying in .NET by working with offsets and lengths and either a reference to a containing string or array or an unmanaged pointer to memory, but there was considerable room for improvement on these fronts:

Convenience

Wide support across .NET APIs

Unified, safe handling of the following:

Strings

Arrays

Unmanaged memory

.NET offers a type that addresses all of these points: Span<T>. (See the sidebar, “Support Across Language and Runtime Versions”, for more information on how the features described in this chapter relate to C# language and .NET runtime versions.)

SUPPORT ACROSS LANGUAGE AND RUNTIME VERSIONS
Span<T> is built into .NET and is available to any library that targets .NET Standard 2.1. You can also use it on .NET Framework via a NuGet package, System.Memory, but be aware that this package has some limitations.

First, although this NuGet package adds Span<T> and related types, it cannot modify existing libraries. To fulfill the “wide support across .NET APIs” requirement, Microsoft added numerous methods to the .NET runtime libraries. For example, new overloads of int.TryParse accept ReadOnlySpan<char> as an alternative to string. The System.Memory NuGet package can’t add new static methods to int, so these new methods are not available in .NET Framework.

Second, this package provides a slightly different implementation than the one you will get when running the exact same code on .NET. These newer runtimes enable a more efficient implementation of Span<T> and related types, and provide related optimizations. This is critical to the high performance offered by the features discussed in this chapter. The latest version of the .NET Framework at the time of writing (version 4.8.1) lacks the Span<T> optimizations, and Microsoft has no plans to add them in future versions because .NET supersedes the .NET Framework. Code using these techniques works correctly on .NET Framework, but if you want to reap the full performance benefits of these techniques, you’ll need to run on .NET.

Representing Sequential Elements with Span<T>
The System.Span<T> value type represents a sequence of elements of type T stored contiguously in memory. Those elements can live inside an array, a string, a managed block of memory allocated in a stack frame, or unmanaged memory. Starting with .NET 7.0 and C# 11.0, it is also possible to create a single-element span that refers to an individual field or variable without needing to use unsafe code. Let’s look at how Span<T> addresses each of the requirements enumerated in the preceding section.

A Span<T> encapsulates both a pointer to the start of the data in memory, and its length. To access the contents of a span, you use it much as you would an array, as Example 18-3 shows. This makes it much more convenient to use than ad hoc techniques in which you define a couple of int variables and have to remember what they refer to.

Example 18-3. Iterating over a Span<int>
static int SumSpan(ReadOnlySpan<int> span)
{
    int sum = 0;
    for (int i = 0; i < span.Length; ++i)
    {
        sum += span[i];
    }
    return sum;
}
Since a Span<T> knows its own length, its indexer checks that the index is in range, just as the built-in array type does. The performance is very similar to using a built-in array. This includes the optimizations that detect certain loop patterns—for example, the CLR will recognize Example 18-3 as a loop that iterates over the entire contents, enabling it to generate code that doesn’t need to check that the index is in range each time around the loop. (On .NET Framework, Span<T> is a little slower than an array, because its CLR does not include the optimizations for Span<T>.)

You may have noticed that the method in Example 18-3 takes a ReadOnlySpan<T>. This is a close relative of Span<T>, and there is an implicit conversion enabling you to pass any Span<T> to a method that takes a ReadOnlySpan<T>. The read-only form enables a method to declare clearly that it will only read from the span, and not write to it. (This is enforced by the fact that the read-only form’s indexer offers just a get accessor, and no set.)

TIP
Whenever you write a method that works with a span and that does not mean to modify the span’s data, you should use ReadOnlySpan<T>.

Span<T> defines an explicit conversion from arrays. Similarly, ReadOnlySpan<T> is implicitly convertible from arrays and also strings. This enables Example 18-4 to pass an array to the SumSpan method. Of course, we’ve gone and allocated an array on the heap there, so this particular example defeats the main point of using spans, but if you already have an array on hand, this is a useful technique.

Example 18-4. Passing an int[] as a ReadOnlySpan<int>
int[] numberArray = [1, 2, 3];
Console.WriteLine(SumSpan(numberArray));
Although Example 18-4 constructs an array, you may be surprised to discover that Example 18-5 does not, despite appearing to construct an array explicitly.

Example 18-5. Array syntax implicitly creating a ReadOnlySpan<int> directly
Console.WriteLine(SumSpan(new int[] { 1, 2, 3 }));
When you use this array initialization syntax in a place where a ReadOnlySpan<T> is required, then as long as the initializer values are all constants, the compiler can perform an optimization: it does not create a real .NET array. Instead, it embeds the initializer values directly into the compiled output as a block of binary data and generates code that obtains a ReadOnlySpan<T> that points directly to that data. This optimization relies on a couple of facts. First, spans provide no way to get hold of the underlying container. This means our code can’t tell whether there really is an array behind the span, so it doesn’t actually matter if no array gets created. Second, this relies on the data being read-only—since methods might run multiple times, it needs to be possible to create an identical span every time, and if we were using a writable span, it would not be possible to share the same underlying block of memory every time.

Example 18-6 shows a couple of examples in which creating a span with the same array initializer syntax really will create an array. In the first case, not all of the values are constant, so the optimization just described can’t be applied. And in the second case, we assign the array into a Span<int> (even though SumSpan needs only an ReadOnlySpan<int>) so the compiler generates code that creates an array to enable the data to be modified. If the only thing we’re doing with this data is passing it to SumSpan (which is allowed because Span<T> is implicitly convertible to ReadOnlySpan<T>) that’s a waste, because the array will never be modified in practice.

Example 18-6. Array syntax examples that defeat the no-array optimization
// Creates an array because one of the initializer values is not constant.
Console.WriteLine(SumSpan(new int[] { 1, 2, DateTime.Now.Hour }));

// Creates an array because we asked for a Span<int> (not readonly).
Span<int> numberSpan = new int[] { 1, 2, 3 };
Console.WriteLine(SumSpan(numberSpan));
It is possible to avoid creating a real array even in these scenarios because Span<T> also works with stack-allocated arrays, as Example 18-7 shows.

Example 18-7. Passing a stack-allocated array as a ReadOnlySpan<int>
ReadOnlySpan<int> nonConstReadOnly = stackalloc int[] { 1, 2, DateTime.Now.Hour };
Console.WriteLine(SumSpan(nonConstReadOnly));

Span<int> constWriteable = stackalloc int[] { 1, 2, 3 };
Console.WriteLine(SumSpan(constWriteable));
C# disallows most uses of stackalloc outside of code marked as unsafe. This allocates memory on the current method’s stack frame, so this array won’t have the usual .NET object headers that an ordinary array on the GC heap would have—it’s just the raw values. This means that a stackalloc expression produces a pointer type, int* in this example. You can normally only use pointer types directly in unsafe code blocks. However, the compiler makes an exception to this rule if you assign the pointer produced by a stackalloc expression directly into a span. This is permitted because spans impose bounds checking, preventing undetected out-of-range access errors of the kind that normally make pointers unsafe. Also, Span<T> and ReadOnlySpan<T> are both defined as ref struct types, and as “Stack Only” describes, this means they cannot outlive their containing stack frame. This guarantees that the stack frame on which the stack-allocated memory lives will not vanish while there are still outstanding references to it. (.NET’s type safety verification rules include special handling for ref-like types such as spans.)

As you saw in earlier chapters, C# 12.0 adds collection expressions, a new syntax for creating and initializing collections. These work with spans, as Example 18-8 shows. The first two collection expressions compile into code that puts the relevant data on the stack. The final one passes a collection made entirely of constant values to a method taking a ReadOnlySpan<int>, so in this case the compiler uses the same trick we saw with array initializers: it just embeds the constant values as a block of binary data in the compiled output, and creates a span pointing directly to that.

Example 18-8. Using collection expressions with spans
// Lives on stack (because one of the values is not constant).
Console.WriteLine(SumSpan([1, 2, DateTime.Now.Hour]));

// Lives on stack (because using Span<int> means this must be writable).
Span<int> numbersCollectionExpression = [1, 2, DateTime.Now.Hour];
Console.WriteLine(SumSpan(numbersCollectionExpression));

// Pointer to constant data embedded in DLL.
Console.WriteLine(SumSpan([1, 2, 3]));
If a collection expression uses the spread syntax (..) to incorporate a copy of some other collection, the size of the resulting span is not fixed at compile time—it will be determined by however large that other collection is. In these cases the compiler falls back to generating code that puts the relevant collection on the heap to avoid risking a stack overflow. If you need a span that incorporates some data from other collections and you want to avoid heap allocation, you would use stackalloc directly, and not the collection expression syntax. If you do this, you should inspect the size of that incoming data because you it’s generally a bad idea to put more than a few hundred bytes of data on the stack. The default stack size is not the same on all platforms, and can be changed by configuration, but it’s common for the stack to be 1.5 MB in size, and if you use async and await it can be hard to predict exactly how deep call stacks will get at runtime. It is wise to choose a fairly conservative upper size limit when using stackalloc, and you should either reject data that is too large, or fall back to a heap-based code path.

Earlier I mentioned that spans can refer to strings as well as arrays. However, we can’t pass a string to our SumSpan method for the simple reason that it requires a span with an element type of int, whereas a string is a sequence of char values. int and char have different sizes—they take 4 and 2 bytes each, respectively. Although an implicit conversion exists between the two (meaning you can assign a char value into an int variable, giving you the Unicode value of the char), that does not make a ReadOnlySpan<char> implicitly compatible with a ReadOnlySpan<int>.1 Remember, the entire point of spans is that they provide a view into a block of data without needing to copy or modify that data; since int and char have different sizes, converting a char[] to an int[] array would double its size. However, if we were to write a method accepting a ReadOnlySpan<char>, we would be able to pass it a string, a char[] array, or a stackalloc char[], or could explicitly construct a ReadOnlySpan<char> from an unmanaged pointer of type char* (because the in-memory representation of a particular span of characters within each of these is the same).

NOTE
Since strings are immutable in .NET, you cannot convert a string to a Span<char>. You can only convert it to a ReadOnlySpan<char>.

We’ve examined two of our requirements from the preceding section: Span<T> is easier to use than ad hoc storing of an offset and length, and it makes it possible to write a single method that can work with data in arrays, strings, the stack, or unmanaged memory. This leaves our final requirement: widespread support throughout .NET’s runtime libraries. As Example 18-9 shows, it is now supported in int.Parse, enabling us to fix the problem shown in Example 18-2. The generic math feature added in .NET 7.0 defines this and a span-based TryParse in its ISpanParsable<T> interface, and since INumberBase<T> inherits from ISpanParsable<T>, span-based parsing is available for all numeric types.

Example 18-9. Parsing integers in a string using Span<char>
string uriString = "http://example.com/books/1323?edition=6&format=pdf";
int id = int.Parse(uriString.AsSpan(25, 4));
Span<T> is a relatively new type (it was introduced in 2018; .NET has been around since 2002), so although the .NET runtime libraries now support it widely, many third-party libraries do not yet support it, and perhaps never will. However, it has become increasingly well supported since being introduced, and that situation will only improve.

Utility Methods
In addition to the array-like indexer and Length properties, Span<T> offers a few useful methods. The Clear and Fill methods provide convenient ways to initialize all the elements in a span either to the default value for the element type or a specific value. Obviously, these are not available on ReadOnlySpan<T>.

You may sometimes encounter situations in which you have a span and you need to pass its contents to a method that requires an array. Obviously there’s no avoiding an allocation in this case, but if you need to do it, you can use the ToArray method.

Spans (both normal and read-only) also offer a TryCopyTo method, which takes as its argument a (non-read-only) span of the same element type. This allows you to copy data between spans. This method handles scenarios where the source and target spans refer to overlapping ranges within the same container. As the Try suggests, it’s possible for this method to fail: if the target span is too small, this method returns false.

Collection Expressions and Spans
I’ve already shown how you can use C# 12.0’s new collection expression feature to initialize a span, but there’s a more subtle way that these two language features interact: spans can become involved when you initialize certain other collection types with collection expressions. Some collection types define a special create method that C# will use if you initialize those types with a collection expression. Example 18-10 will use the ImmutableList.Create method, for example.

Example 18-10. Using a collection builder
using System.Collections.Immutable;

ImmutableList<int> numbers = [1, 2, 3, 4, 5];
Collection types can advertise a create method with the [CollectionBuilder] attribute. This method is required to accept a ReadOnlySpan<T> where T is the element type of the collection being initialized. As of .NET 8.0, only the immutable collection types define this. These types were previously quite awkward to initialize, and the simplest ways of creating them were not the highest-performing. But now, using a collection expression creates the most efficient possible initialization code.

Although not all collection types implement this, some types, such as List<T>, are known to the compiler, enabling it to generate tailored initialization code for those. But if you write your own collection type, and if its implementation details mean that you can perform initialization more efficiently if you can see all the elements up front instead of them being added one at a time, you can also implement a create method that accepts a ReadOnlySpan<T>, and declare that it is your creation method with the [CollectionBuilder] attribute.

Pattern matching
Spans can be used with certain kinds of patterns. Chapter 2 described list patterns, a new feature in C# 11.0, and as Example 18-11 shows, you can use a span as the input to a list pattern.

Example 18-11. Using a span with a list pattern
static void CheckStart(ReadOnlySpan<char> chars)
{
    if (chars is ['H', .. ReadOnlySpan<char> theRest])
    {
        Console.WriteLine(theRest.Length);
    }
}
This pattern includes the .. syntax, denoting a slice, which matches any elements in the source not explicitly specified in the pattern. This example has a declaration pattern to capture the elements matched by the slice into a new variable called theRest. As you can see, the captured slice is also a span. Spans are particularly well suited to list patterns that capture slices, because there’s no need to make a copy of the relevant subsequence. If we had used string here instead of ReadOnlySpan<char>, the compiler would need to generate code that called chars.Substring(1) to obtain a suitable value for theRest, causing a new string to be allocated. This code avoids that, and yet we can still pass this CheckStart method a string, because string is implicitly convertible to ReadOnlySpan<char>.

Since C# 11.0, it has also been possible to use a ReadOnlySpan<char> (or a Span<char>) as the input to a string constant pattern, as Example 18-12 shows. The compiler generates the code required to compare the span’s contents with the string’s contents.

Example 18-12. Span as input to a string constant pattern
static void RespondToGreeting(ReadOnlySpan<char> message)
{
    switch (message)
    {
        case "Hello":
            Console.WriteLine("Hello to you too");
            break;

        case "How do you do":
            Console.WriteLine("How do you do");
            break;
    }
}
Stack Only
The Span<T> and ReadOnlySpan<T> types are both declared as ref struct. This means that not only are they value types, they are value types that can live only on the stack. So you cannot have fields with span types in a class, or in any struct that is not also a ref struct. This also imposes some potentially more surprising restrictions. For example, it means you cannot use a span in a variable in an async method. These store all their variables as fields in a hidden type, enabling them to live on the heap, because asynchronous methods often need to outlive their original stack frame. In fact, these methods can even switch to a completely different stack altogether, because asynchronous methods can end up running on different threads as their execution progresses. For similar reasons, there are restrictions on using spans in anonymous functions and in iterator methods. You can use them in local methods, and you can even declare a ref struct variable in the outer method and use it from the nested one, but with one restriction: you must not create a delegate that refers to that local method, because this would cause the compiler to move shared variables into an object that lives on the heap. (See Chapter 9 for details.)

This restriction is necessary for .NET to be able to offer the combination of array-like performance, type safety, and the flexibility to work with multiple different containers. “Representing Sequential Elements with Memory<T>” will show what we can do instead in scenarios where this stack-only limitation is problematic.

Using ref With Fields
Before C# 11.0, the Span<T> and ReadOnlySpan<T> types were only able to exist thanks to special support in the compiler and runtime—you couldn’t write your own types that contained a ref-style reference. This restriction no longer exists. The basic capability that makes spans possible—the ability for a type to have a field that is effectively a ref to some other value—is no longer a special power available only to the span types. C# 11.0 made it possible to write your own ref-like type as Example 18-13 shows.

Example 18-13. Type with a ref field
public readonly ref struct RefLike<T>(ref T rv)
{
    public readonly ref T Ref = ref rv;
}
Example 18-14 shows this type in use. The ri variable’s Ref field is a ref int referring to the local variable i (because the code passes ref i as the constructor argument). When it modifies ri.Ref it is really modifying the i variable, so the final line displays the value 42.

Example 18-14. Using a type with a ref field
int i = 21;
RefLike<int> ri = new(ref i);
ri.Ref *= 2;
Console.WriteLine(i);
Only ref struct types may contain ref fields, for exactly the same reason that only ref struct types may contain other ref struct types such as spans: types of this kind absolutely must live on the stack, because it would otherwise be possible for a ref to some variable in a stack frame to end up in an object or boxed struct on the heap. That would allow the ref to survive after the stack frame containing the variable to which it refers no longer exists, which would mean ref fields were unsafe. Without this restriction, they’d be no different from pointers, and we’ve been able to declare pointer-typed fields since C# 1.0. But pointers are inherently unsafe. The whole point of ref fields is that they preserve type safety, which is why restrictions on their use exist.

Although the ability to put a ref in a field may seem like a relatively simple new feature, the need to ensure type safety meant that the addition of this feature had consequences. In particular, it undermines a simple assumption that used to be true before C# 11.0: if you pass some method a ref as an argument, it used to be safe to assume that the method was unable to retain that ref after it returned. But the availability of ref fields means that when a public method of a ref struct type takes an argument of some ref type, the caller now has to assume that the ref struct might store that ref in some ref field. This changes the rules about what it is safe to pass in as a ref or via a ref-like type such as Span<T> or the RefLike<T> type shown here.

For example, it’s normally just fine to pass a reference to a local variable as an argument to a method (either directly as a ref, or via a ref-like such as Span<int>). This is, in general, safe because the method won’t be able to store that reference—it will not be able to use it after it returns. But if the method is a member of a ref struct, it can stash a reference passed in arguments in a field. The ChangeTarget method in Example 18-15 does exactly this. (As it happens, this example doesn’t do anything with the stored ref, but we could add other members that do.)

Example 18-15. A method that captures a ref
public ref struct RefSmuggler<T>
{
    private ref T _ref;

    public void ChangeTarget(RefLike<T> rv)
    {
        _ref = ref rv.Ref;
    }
}
Because it’s now possible to write code that holds onto a ref, the compiler has to apply more conservative rules. Example 18-16 tries to use the RefSmuggler<T> type to pass a reference to a local variable back out to its caller. It calls ChangeTarget to set the _ref field to refer to the local variable, but it does this on a RefSmuggler<T> passed in by ref, which means that RefSmuggler<T> will be available to whatever code calls Bad after Bad returns. This is trying to create a dangling reference—it’s trying to give its caller a reference to the local variable on its own stack frame, a stack frame that will no longer exist.

Example 18-16. Attempting to enable a ref to outlive its target’s stack frame
static void Bad(ref RefSmuggler<int> rs)
{
    int local = 123;
    RefLike<int> rli = new(ref local);
    rs.ChangeTarget(rli); // Won't compile
}
The compiler does not allow this, which is good, but this creates a problem. What if we had a method takes ref-like arguments, but which didn’t hold onto any reference, such as Example 18-17?

Example 18-17. A method that doesn’t capture a ref but which is handled as if it did
public readonly ref struct NoRefCapture<T>
{
    public void UseRef(RefLike<T> rv1, RefLike<T> rv2)
    {
        rv1.Ref = rv2.Ref;
    }
}
This doesn’t capture a ref from either of its arguments. That means that code like Example 18-18 would be safe.

Example 18-18. Code C# thinks might be attempting to enable a ref to outlive its target’s stack frame
void LooksBad(ref NoRefCapture<int> r)
{
    int local1 = 123;
    int local2 = 456;
    RefLike<int> rli1 = new(ref local1);
    RefLike<int> rli2 = new(ref local2);
    r.UseRef(rli1, rli2); // Won't compile
}
Unfortunately the C# compiler won’t allow this. It applies exactly the same rules as it did in Example 18-16. We know that in this particular case there isn’t really a problem because UseRef only makes immediate use of the references passed in, and it doesn’t hold onto them after it returns. But the problem is that the C# compiler can’t know that in general. If the NoRefCapture<T> type is defined in a library, the compiler can’t know what’s inside the UseRef method. (Arguably, it could inspect the IL during compilation, but that would be a bad idea because a future version of the library could change the implementation.) It can only go on the public signature of the method, and from that perspective, there’s no real difference between RefSmuggler<T>.ChangeTarget and NoRefCapture<T>.UseRef. These are both members of ref struct types, so either could capture references from their inputs. That’s why both examples fail to compile.

This is vexing if the method in question will never have any reason to capture its inputs. It’s particularly frustrating if you wrote a library before C# 11.0 came out that includes a method of this kind, because it used to be legal: back when it simply wasn’t possible to capture a ref there was no problem with this sort of method.

Fortunately, there’s a solution. Our method can declare that it will never capture references from specific arguments by marking them with the scoped keyword. This is part of the method’s public signature, which has two effects. First, the compiler will keep us honest: if we annotated a parameter as scoped it will prevent us from attempting to capture a reference obtained through that parameter. Second, code such as Example 18-18 would not cause an error if it used this type. The compiler would know that the references passed in through these arguments won’t be captured, so there will be no violation of the type safety rules.

Example 18-19. Declaring non-capture of a ref
public readonly ref struct NoRefCaptureWithScoped<T>
{
    public void UseRef(scoped RefLike<T> rv1, scoped RefLike<T> rv2)
    {
        rv1.Ref = rv2.Ref;
    }
}
Before C# 11.0 it wasn’t possible for methods of this form to capture references. It’s only the addition of ref fields that makes it possible. Code such as Example 18-18 never used to cause compiler errors because it used to be safe. Now it’s only safe if the target method declares the argument as scoped. But what does that mean if you’re using a mixture of old and new code? Your C# 11.0 or 12.0 project might use a library written in C# 10.0 that contains a method similar to Example 18-19. Since the library was written in a version of C# that didn’t support ref fields, that method can’t capture references, but it has parameters which, on current versions of C#, would make it possible to capture references. There was no scoped keyword in C# 10.0, so a method such as UseRef could only have a signature like the one in Example 18-17. Does that mean that such methods become unusable once you move to C# 11.0 or later?

As you’d probably expect, that’s not what happens. If you’re using an old library that contains code such as Example 18-17, you’ll be able to call it in the way that Example 18-18 does without errors. This works because the compiler now adds attributes to the component to indicate that it was built with a version of the language in which ref fields are available. Older libraries (or any library where the project configuration specifies a version of C# older than 11.0) will not have this attribute, so if you’re consuming such a library from a new project, the compiler will know that the older rules around ref handling apply. In effect, all ref-like arguments of methods of ref struct types defined in older libraries will be handled as though they were scoped.

Representing Sequential Elements with Memory<T>
The runtime libraries define the Memory<T> type and its counterpart, ReadOnlyMemory<T>, representing the same basic concept as Span<T> and ReadOnlySpan<T>. These types provide a uniform view over a contiguous sequence of elements of type T that could reside in an array, unmanaged memory, or, if the element type is char, a string. But unlike spans, these are not ref struct types, so they can be used anywhere. The downside is that this means they cannot offer the same high performance as spans. (It also means you cannot create a Memory<T> that refers to stackalloc memory.2)

You can convert a Memory<T> to a Span<T>, and likewise a ReadOnlyMemory<T> to a ReadOnlySpan<T>, as long as you’re in a context where spans are allowed (e.g., in an ordinary method but not an asynchronous one). The conversion to a span has a cost. It is not massive, but it is significantly higher than the cost of accessing an individual element in a span. (In particular, many of the optimizations that make spans attractive only become effective with repeated use of the same span.) So if you are going to read or write elements in a Memory<T> in a loop, you should perform the conversion to Span<T> just once, outside of the loop, rather than doing it each time around. If you can work entirely with spans, you should do so since they offer the best performance. (And if you are not concerned with performance, then this is not the chapter for you!)

ReadOnlySequence<T>
The types we’ve looked at so far in this chapter all represent contiguous blocks of memory. Unfortunately, data doesn’t always neatly present itself to us in the most convenient possible form. For example, on a busy server that is handling many concurrent requests, the network messages for requests in progress often become interleaved—if a particular request is large enough to need to be split across two network packets, it’s entirely possible that after receiving the first but before receiving the second of these, one or more packets for other, unrelated requests could arrive. So by the time we come to process the contents of the request, it might be split across two different chunks of memory. Since span and memory values can each represent only a contiguous range of elements, .NET provides another type, ReadOnlySequence, to represent data that is conceptually a single sequence but that has been split into multiple ranges.

NOTE
There is no corresponding Sequence<T>. Unlike spans and memory, this particular abstraction is available only in read-only form. That’s because it’s common to need to deal with fragmented data as a reader, where you don’t control where the data lives, but if you are producing data, you are more likely to be in a position to control where it goes.

Now that we’ve seen the main types for working with data while minimizing the number of allocations, let’s look at how these can all work together to handle high volumes of data. To coordinate this kind of processing, we need to look at one more feature: pipelines.

Processing Data Streams with Pipelines
Everything we’re looking at in this chapter is designed to enable safe, efficient processing of large volumes of data. The types we’ve seen so far all represent information that is already in memory. We also need to think about how that data is going to get into memory in the first place. The preceding section hinted at the fact that this can be somewhat messy. The data will very often be split into chunks, and not in a way designed for the convenience of the code processing the data, because it will likely be arriving either over a network or from a disk. If we’re to realize the performance benefits made possible by Span<T> and its related types, we need to pay close attention to the job of getting data into memory in the first place and the way in which this data fetching process cooperates with the code that processes the data. Even if you are only going to be writing code that consumes data—perhaps you are relying on a framework such as ASP.NET Core to get the data into memory for you—it is important to understand how this process works.

The System.Io.Pipelines NuGet package defines a set of types in a namespace of the same name that provide a high-performance system for loading data from some source that tends to split data into inconveniently sized chunks, and passing that data over to code that wants to be able to process it in situ using spans. Figure 18-2 shows the main participants in a pipeline-based process.

At the heart of this is the Pipe class. It offers two properties: Writer and Reader. The first returns a PipeWriter, which is used by the code that loads the data into memory. (This often doesn’t need to be application-specific. For example, in a web application, you can let ASP.NET Core control the writer on your behalf.) The Reader property’s type is, predictably, PipeReader, and this is most likely to be the part your code interacts with.


Figure 18-2. Pipeline overview
The basic process for reading data from a pipe is as follows. First, you call Pipe​Rea⁠der.⁠Rea⁠dAs⁠ync. This returns a task,3 because if no data is available yet, you will need to wait until the data source supplies the writer with some data. Once data is available, the task will provide a ReadResult object. This supplies a ReadOnlySequence<T>, which presents the available data as one or more ReadOnlySpan<T> values. The number of spans will depend on how fragmented the data is. If it’s all conveniently in one place in memory, there will be just one span, but code using a reader needs to be able to cope with more. Your code should then process as much of the available data as it can. Once it has done this, it calls the reader’s AdvanceTo to tell it how much of the data your code has been able to process. Then, if the ReadResult.IsComplete property is false, we will repeat these steps again from the call to ReadAsync.

An important detail of this is that we are allowed to tell the PipeReader that we couldn’t process everything it gave us. This would normally be because the information got sliced into pieces, and we need to see some of the next chunk before we can fully process everything in the current one. For example, a JSON message large enough to need to be split across several network packets will probably end up with splits in inconvenient places. So you might find that the first chunk looks like this:

{"property1":"value1","prope
And the second like this:

rty2":42}
In practice the chunks would be bigger, but this illustrates the basic problem: the chunks that a PipeReader returns are likely to slice across the middle of important features. With most .NET APIs, you never have to deal with this kind of mess because everything has been cleaned up and reassembled by the time you see it, but the price you pay for that is the allocation of new strings to hold the recombined results. If you want to avoid those allocations, you have to handle these challenges.

There are a couple of ways to deal with this. One is for code reading data to maintain enough state to be able to stop and later restart at any point in the sequence. So code processing this JSON might choose to remember that it is partway through an object and that it’s in the middle of processing a property whose name starts with prope. But PipeReader offers an alternative. Code processing these examples could report with its call to AdvanceTo that it has consumed everything up to the first comma. If you do that, the Pipe will remember that we’re not yet finished with this first block, and when the next call to ReadAsync completes, the ReadOnlySequence<T> in ReadResult.Buffer will now include at least two spans: the first span will point into the same block of memory as last time, but now its offset will be set to where we got to last time—that first span will refer to the "prope text at the end of the first block. And then the second span will refer to the text in the second chunk.

The advantage of this second approach is that the code processing the data doesn’t need to remember as much between calls to ReadAsync, because it knows it’ll be able to go back and look at the previously unprocessed data again once the next chunk arrives, at which point it should now be able to make sense of it.

In practice, this particular example is fairly easy to cope with because there’s a type in the runtime libraries called Utf8JsonReader that can handle all the awkward details around chunk boundaries for us. Let’s look at an example.

Processing JSON in ASP.NET Core
Suppose you are developing a web service that needs to handle HTTP requests containing JSON. This is a pretty common scenario. Example 18-20 shows a common way to do this in ASP.NET Core. This is reasonably straightforward, but it does not use any of the low-allocation mechanisms discussed in this chapter, so this forces ASP.NET Core to allocate multiple objects for each request.

Example 18-20. Handling JSON in HTTP requests
[HttpPost]
[Route("/jobs/create")]
public void CreateJob([FromBody] JobDescription requestBody)
{
    switch (requestBody.JobCategory)
    {
        case "arduous":
            CreateArduousJob(requestBody.DepartmentId);
            break;

        case "tedious":
            CreateTediousJob(requestBody.DepartmentId);
            break;
    }
}

public record JobDescription(int DepartmentId, string JobCategory);
Before we look at how to change it, for readers not familiar with ASP.NET Core, I will quickly explain what’s happening in this example. The CreateJob method is annotated with attributes telling ASP.NET Core that this will handle HTTP POST requests where the URL path is /jobs/create. The [FromBody] attribute on the method’s argument indicates that we expect the body of the request to contain data in the form described by the JobDescription type. ASP.NET Core can be configured to handle various data formats, but if you go with the defaults, it will expect JSON.

This example is therefore telling ASP.NET Core that for each POST request to /jobs/create, it should construct a JobDescription object, populating its Dep⁠art⁠ment​Id and JobCategory from properties of the same names in JSON in the incoming request body.

In other words, we’re asking ASP.NET Core to allocate two objects—a Job​Des⁠cri⁠pti⁠on and a string—for each request, each of which will contain copies of information that was in the body of the incoming request. (The other property, DepartmentId, is an int, and since that’s a value type, it lives inside the Job​Des⁠crip⁠tion object.) And for most applications that will be fine—a couple of allocations is not normally anything to worry about in the course of handling a single web request. However, in more realistic examples with more complex requests, we might then be looking at a much larger number of properties, and if you need to handle a very high volume of requests, the copying of data into a string for each property can start to cause enough extra work for the GC that it becomes a performance problem.

Example 18-21 shows how we can avoid these allocations using the various features described in the preceding sections of this chapter. It makes the code a good deal more complex, demonstrating why you should only apply these kinds of techniques in cases where you have established that GC overhead is high enough that the extra development effort is justified by the performance improvements.

Example 18-21. Handling JSON without allocations
[HttpPost]
[Route("/jobs/create")]
public async ValueTask CreateJobFrugalAsync()
{
    bool inDepartmentIdProperty = false;
    bool inJobCategoryProperty = false;
    int? departmentId = null;
    bool? isArduous = null;

    PipeReader reader = this.Request.BodyReader;
    JsonReaderState jsonState = default;
    while (true)
    {
        ReadResult result = await reader.ReadAsync().ConfigureAwait(false);
        jsonState = ProcessBuffer(
            result,
            jsonState,
            out SequencePosition position);

        if (departmentId.HasValue && isArduous.HasValue)
        {
            if (isArduous.Value)
            {
                CreateArduousJob(departmentId.Value);
            }
            else
            {
                CreateTediousJob(departmentId.Value);
            }

            return;
        }

        reader.AdvanceTo(position);

        if (result.IsCompleted)
        {
            break;
        }
    }

    JsonReaderState ProcessBuffer(
        in ReadResult result,
        in JsonReaderState jsonState,
        out SequencePosition position)
    {
        // This is a ref struct, so this has no GC overhead
        var r = new Utf8JsonReader(result.Buffer, result.IsCompleted, jsonState);

        while (r.Read())
        {
            if (inDepartmentIdProperty)
            {
                if (r.TokenType == JsonTokenType.Number)
                {
                    if (r.TryGetInt32(out int v))
                    {
                        departmentId = v;
                    }
                }
            }
            else if (inJobCategoryProperty)
            {
                if (r.TokenType == JsonTokenType.String)
                {
                    if (r.ValueSpan.SequenceEqual("arduous"u8))
                    {
                        isArduous = true;
                    }
                    else if (r.ValueSpan.SequenceEqual("tedious"u8))
                    {
                        isArduous = false;
                    }
                }
            }

            inDepartmentIdProperty = false;
            inJobCategoryProperty = false;

            if (r.TokenType == JsonTokenType.PropertyName)
            {
                if (r.ValueSpan.SequenceEqual("JobCategory"u8))
                {
                    inJobCategoryProperty = true;
                }
                else if (r.ValueSpan.SequenceEqual("DepartmentId"u8))
                {
                    inDepartmentIdProperty = true;
                }
            }
        }

        position = r.Position;
        return r.CurrentState;
    }
}
Instead of defining an argument with a [FromBody] attribute, this method works directly with the this.Request.BodyReader property. (Inside an ASP.NET Core MVC controller class, this.Request returns an object representing the request being handled.) This property’s type is PipeReader, the consumer side of a Pipe. ASP.NET Core creates the pipe, and it manages the data production side, feeding data from incoming requests into the associated PipeWriter.

As the property name suggests, this particular PipeReader enables us to read the contents of the HTTP request’s body. By reading the data this way, we make it possible for ASP.NET Core to present the request body to us in situ: our code will be able to read the data directly from wherever it happened to end up in memory once the computer’s network card received it. (In other words, no copies, and no additional GC overhead.)

The while loop in CreateJobFrugalAsync performs a process common to any code that reads data from a PipeReader: it calls ReadAsync, processes the data that returns, and calls AdvanceTo to let the PipeReader know how much of that data it was able to process. We then check the IsComplete property of the ReadResult returned by ReadAsync, and if that is false, then we go round one more time.

Example 18-21 uses the Utf8JsonReader type to process the data. As the name suggests, this works directly with text in UTF-8 encoding. JSON messages are commonly sent with this encoding, but .NET strings use UTF-16. So one of the jobs that the simpler Example 18-20 forced ASP.NET to do was convert any strings from UTF-8 to UTF-16. Avoiding this conversion can provide a significant performance improvement, although it does lose some flexibility. The simpler, slower approach has the benefit of being able to adapt to incoming requests in more formats: if a client chose to send its request in something other than UTF-8—perhaps UTF-16 or UCS-32, or even a non-Unicode encoding such as ISO-8859-1—our first handler could cope with any of them, because ASP.NET Core can do the string conversions for us. But since Example 18-21 works directly with the data in the form the client transmitted, using a type that only understands UTF-8, we have traded off that flexibility in exchange for higher performance.

Utf8JsonReader is able to handle the tricky chunking issues for us—if an incoming request ends up being split across multiple buffers in memory because it was too large to fit in a single network packet, Utf8JsonReader is able to cope. In the event of an unhelpfully placed split, it will process what it can, and then the JsonReaderState value it returns through its CurrentState will report a Position indicating the first unprocessed character. We pass this to PipeReader.AdvanceTo. The next call to PipeReader.ReadAsync will return only when there is more data, but its ReadResult.Buffer will also include the previously unconsumed data.

Like the ReadOnlySpan<T> type it uses internally when reading data, Utf8JsonReader is a ref struct type, meaning that it cannot live on the heap. This means it cannot be used in an async method, because async methods store all of their local variables on the heap. That is why this example has a separate method, ProcessBuffer. The outer CreateJobFrugalAsync method has to be async because the streaming nature of the PipeReader type means that its ReadAsync method requires us to use await. But the Utf8JsonReader cannot be used in an async method, so we end up having to split our logic across two methods.

When splitting your pipeline processing into an outer async reader loop and an inner method that avoids async in order to use ref struct types, it can be convenient to make the inner method a local method, as Example 18-21 does. This enables it to access variables declared in the outer method. You might be wondering whether this causes a hidden extra allocation—to enable sharing of variables in this way, the compiler generates a type, storing shared variables in fields in that type and not as conventional stack-based variables. With lambdas and other anonymous methods, this type will indeed cause an additional allocation, because it needs to be a heap-based type so that it can outlive the parent method. However, with local methods, the compiler uses a struct to hold the shared variables, which it passes by reference to the inner method, thus avoiding any extra allocation. This is possible because the compiler can determine that all calls to the local method will return before the outer method returns.

When using Utf8JsonReader, our code has to be prepared to receive the content in whatever order it happens to arrive. We can’t write code that tries to read the properties in an order that is convenient for us, because that would rely on something holding those properties and their values in memory. (If you tried to rely on going back to the underlying data to retrieve particular properties on demand, you might find that the property you wanted was in an earlier chunk that’s no longer available.) This defeats the whole goal of minimizing allocations. If you want to avoid allocations, your code needs to be flexible enough to handle the properties in whatever order they appear.

So the ProcessBuffer code in Example 18-21 just looks at each JSON element as it comes and works out whether it’s of interest. This means that when looking for particular property values, we have to notice the PropertyName element, and then remember that this was the last thing we saw, so that we know how to handle the Number or String element that follows, containing the value.

One strikingly odd feature of this code is the way it checks for particular strings. It needs to recognize properties of interest (JobCategory and DepartmentId in this example) but it doesn’t just use normal string comparison. While it’s possible to retrieve property names and string values as .NET strings, doing so defeats the main purpose of using Utf8JsonReader: if you obtain a string, the CLR has to allocate space for that string on the heap and will eventually have to garbage collect the memory. (In this example, every acceptable incoming string is known in advance. In some scenarios there will be strings in the incoming data whose values you will need to perform further processing on, and in those cases, you may just need to accept the costs of allocating an actual string.) So instead we end up performing binary comparisons by calling r.ValueSpan.SequenceEqual. Notice that we’re working entirely in UTF-8 encoding, and not the UTF-16 encoding used by .NET’s string type. (The various strings passed to SequenceEqual use the UTF8 string literal syntax introduced in C# 11.0—they all have a u8 suffix. As you saw in “UTF-8 String Literals” this means that instead of producing string objects, the compiler embeds the UTF-8 representation of these strings directly into the compiled component, and creates ReadOnlySpan<byte> values pointing to the data.) That’s because all of this code works directly against the request’s payload in the form in which it arrived over the network, in order to avoid unnecessary copying.

Summary
APIs that break data down into the constituent components can be very convenient to use, but this convenience comes at a price. Each time we want some subelement represented either as a string or a child object, we cause another object to be allocated on the GC heap. The cumulative cost of these allocations (and the corresponding work to recover the memory once they are no longer in use) can be damaging in some very performance-sensitive applications. They can also be significant in cloud applications or high-volume data processing, where you might be paying for the amount of processing work you do—reducing CPU or memory usage can have a nontrivial effect on cost.

The Span<T> type and the related types discussed in this chapter make it possible to work with data wherever it already resides in memory. This typically requires rather more complex code, but in cases where the payoff justifies the work, these features make it possible for C# to tackle whole classes of problems for which it would previously have been too slow.

Thank you for reading this book, and congratulations for making it to the end. I hope you enjoy using C#, and I wish you every success with your future projects.

1 That said, it is possible to perform this kind of conversion explicitly—the MemoryMarshal class offers methods that can take a span of one type and return another span that provides a view over the same underlying memory, interpreted as containing a different element type. But it is unlikely to be useful in this case: converting a ReadOnlySpan<char> to a ReadOnlySpan<int> would produce a span with half the number of elements, where each int contained pairs of adjacent char values.

2 Technically you could write a custom MemoryManager to do this, but the compiler and runtime would be unable to enforce safety if you did that.

3 It is a ValueTask<ReadResult> because the purpose of this exercise is to minimize allocations. ValueTask<T> was described in Chapter 16.


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

