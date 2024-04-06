Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


V. Metaprogramming
22. Dynamic Attributes and Properties
23. Attribute Descriptors
23h 31m remaining
Chapter 22. Dynamic Attributes and Properties
The crucial importance of properties is that their existence makes it perfectly safe and indeed advisable for you to expose public data attributes as part of your class’s public interface.

 Martelli, Ravenscroft, and Holden, “Why properties are important”1

Data attributes and methods are collectively known as attributes in Python. A method is an attribute that is callable. Dynamic attributes present the same interface as data attributes—i.e., obj.attr—but are computed on demand. This follows Bertrand Meyer’s Uniform Access Principle:

All services offered by a module should be available through a uniform notation, which does not betray whether they are implemented through storage or through computation.2

There are several ways to implement dynamic attributes in Python. This chapter covers the simplest ways: the @property decorator and the __getattr__ special method.

A user-defined class implementing __getattr__ can implement a variation of dynamic attributes that I call virtual attributes: attributes that are not explicitly declared anywhere in the source code of the class, and are not present in the instance __dict__, but may be retrieved elsewhere or computed on the fly whenever a user tries to read a nonexistent attribute like obj.no_such_attr.

Coding dynamic and virtual attributes is the kind of metaprogramming that framework authors do. However, in Python the basic techniques are straightforward, so we can use them in everyday data wrangling tasks. That’s how we’ll start this chapter.

What’s New in This Chapter
Most of the updates to this chapter were motivated by a discussion of @functools.cached_property (introduced in Python 3.8), as well as the combined use of @property with @functools.cache (new in 3.9). This affected the code for the Record and Event classes that appear in “Computed Properties”. I also added a refactoring to leverage the PEP 412—Key-Sharing Dictionary optimization.

To highlight more relevant features while keeping the examples readable, I removed some nonessential code—merging the old DbRecord class into Record, replacing shelve.Shelve with a dict, and deleting the logic to download the OSCON dataset—which the examples now read from a local file included in the Fluent Python code repository.

Data Wrangling with Dynamic Attributes
In the next few examples, we’ll leverage dynamic attributes to work with a JSON dataset published by O’Reilly for the OSCON 2014 conference. Example 22-1 shows four records from that dataset.3

Example 22-1. Sample records from osconfeed.json; some field contents abbreviated
{ "Schedule":
  { "conferences": [{"serial": 115 }],
    "events": [
      { "serial": 34505,
        "name": "Why Schools Don´t Use Open Source to Teach Programming",
        "event_type": "40-minute conference session",
        "time_start": "2014-07-23 11:30:00",
        "time_stop": "2014-07-23 12:10:00",
        "venue_serial": 1462,
        "description": "Aside from the fact that high school programming...",
        "website_url": "http://oscon.com/oscon2014/public/schedule/detail/34505",
        "speakers": [157509],
        "categories": ["Education"] }
    ],
    "speakers": [
      { "serial": 157509,
        "name": "Robert Lefkowitz",
        "photo": null,
        "url": "http://sharewave.com/",
        "position": "CTO",
        "affiliation": "Sharewave",
        "twitter": "sharewaveteam",
        "bio": "Robert ´r0ml´ Lefkowitz is the CTO at Sharewave, a startup..." }
    ],
    "venues": [
      { "serial": 1462,
        "name": "F151",
        "category": "Conference Venues" }
    ]
  }
}
Example 22-1 shows 4 of the 895 records in the JSON file. The entire dataset is a single JSON object with the key "Schedule", and its value is another mapping with four keys: "conferences", "events", "speakers", and "venues". Each of those four keys maps to a list of records. In the full dataset, the "events", "speakers", and "venues" lists have dozens or hundreds of records, while "conferences" has only that one record shown in Example 22-1. Every record has a "serial" field, which is a unique identifier for the record within the list.

I used Python’s console to explore the dataset, as shown in Example 22-2.

Example 22-2. Interactive exploration of osconfeed.json
>>> import json
>>> with open('data/osconfeed.json') as fp:
...     feed = json.load(fp)  
>>> sorted(feed['Schedule'].keys())  
['conferences', 'events', 'speakers', 'venues']
>>> for key, value in sorted(feed['Schedule'].items()):
...     print(f'{len(value):3} {key}')  
...
  1 conferences
484 events
357 speakers
 53 venues
>>> feed['Schedule']['speakers'][-1]['name']  
'Carina C. Zona'
>>> feed['Schedule']['speakers'][-1]['serial']  
141590
>>> feed['Schedule']['events'][40]['name']
'There *Will* Be Bugs'
>>> feed['Schedule']['events'][40]['speakers']  
[3471, 5199]

feed is a dict holding nested dicts and lists, with string and integer values.


List the four record collections inside "Schedule".


Display record counts for each collection.


Navigate through the nested dicts and lists to get the name of the last speaker.


Get the serial number of that same speaker.


Each event has a 'speakers' list with zero or more speaker serial numbers.

Exploring JSON-Like Data with Dynamic Attributes
Example 22-2 is simple enough, but the syntax feed['Schedule']['events'][40]['name'] is cumbersome. In JavaScript, you can get the same value by writing feed.Schedule.events[40].name. It’s easy to implement a dict-like class that does the same in Python—there are plenty of implementations on the web.4 I wrote FrozenJSON, which is simpler than most recipes because it supports reading only: it’s just for exploring the data. FrozenJSON is also recursive, dealing automatically with nested mappings and lists.

Example 22-3 is a demonstration of FrozenJSON, and the source code is shown in Example 22-4.

Example 22-3. FrozenJSON from Example 22-4 allows reading attributes like name, and calling methods like .keys() and .items()
    >>> import json
    >>> raw_feed = json.load(open('data/osconfeed.json'))
    >>> feed = FrozenJSON(raw_feed)  
    >>> len(feed.Schedule.speakers)  
    357
    >>> feed.keys()
    dict_keys(['Schedule'])
    >>> sorted(feed.Schedule.keys())  
    ['conferences', 'events', 'speakers', 'venues']
    >>> for key, value in sorted(feed.Schedule.items()): 
    ...     print(f'{len(value):3} {key}')
    ...
      1 conferences
    484 events
    357 speakers
     53 venues
    >>> feed.Schedule.speakers[-1].name  
    'Carina C. Zona'
    >>> talk = feed.Schedule.events[40]
    >>> type(talk)  
    <class 'explore0.FrozenJSON'>
    >>> talk.name
    'There *Will* Be Bugs'
    >>> talk.speakers  
    [3471, 5199]
    >>> talk.flavor  
    Traceback (most recent call last):
      ...
    KeyError: 'flavor'

Build a FrozenJSON instance from the raw_feed made of nested dicts and lists.


FrozenJSON allows traversing nested dicts by using attribute notation; here we show the length of the list of speakers.


Methods of the underlying dicts can also be accessed, like .keys(), to retrieve the record collection names.


Using items(), we can retrieve the record collection names and their contents, to display the len() of each of them.


A list, such as feed.Schedule.speakers, remains a list, but the items inside are converted to FrozenJSON if they are mappings.


Item 40 in the events list was a JSON object; now it’s a FrozenJSON instance.


Event records have a speakers list with speaker serial numbers.


Trying to read a missing attribute raises KeyError, instead of the usual AttributeError.

The keystone of the FrozenJSON class is the __getattr__ method, which we already used in the Vector example in “Vector Take #3: Dynamic Attribute Access”, to retrieve Vector components by letter: v.x, v.y, v.z, etc. It’s essential to recall that the __getattr__ special method is only invoked by the interpreter when the usual process fails to retrieve an attribute (i.e., when the named attribute cannot be found in the instance, nor in the class or in its superclasses).

The last line of Example 22-3 exposes a minor issue with my code: trying to read a missing attribute should raise AttributeError, and not KeyError as shown. When I implemented the error handling to do that, the __getattr__ method became twice as long, distracting from the most important logic I wanted to show. Given that users would know that a FrozenJSON is built from mappings and lists, I think the KeyError is not too confusing.

Example 22-4. explore0.py: turn a JSON dataset into a FrozenJSON holding nested FrozenJSON objects, lists, and simple types
from collections import abc


class FrozenJSON:
    """A read-only façade for navigating a JSON-like object
       using attribute notation
    """

    def __init__(self, mapping):
        self.__data = dict(mapping)  

    def __getattr__(self, name):  
        try:
            return getattr(self.__data, name)  
        except AttributeError:
            return FrozenJSON.build(self.__data[name])  

    def __dir__(self):  
        return self.__data.keys()

    @classmethod
    def build(cls, obj):  
        if isinstance(obj, abc.Mapping):  
            return cls(obj)
        elif isinstance(obj, abc.MutableSequence):  
            return [cls.build(item) for item in obj]
        else:  
            return obj

Build a dict from the mapping argument. This ensures we get a mapping or something that can be converted to one. The double-underscore prefix on __data makes it a private attribute.


__getattr__ is called only when there’s no attribute with that name.


If name matches an attribute of the instance __data dict, return that. This is how calls like feed.keys() are handled: the keys method is an attribute of the __data dict.


Otherwise, fetch the item with the key name from self.__data, and return the result of calling FrozenJSON.build() on that.5


Implementing __dir__ suports the dir() built-in, which in turns supports auto-completion in the standard Python console as well as IPython, Jupyter Notebook, etc. This simple code will enable recursive auto-completion based on the keys in self.__data, because __getattr__ builds FrozenJSON instances on the fly—useful for interactive exploration of the data.


This is an alternate constructor, a common use for the @classmethod decorator.


If obj is a mapping, build a FrozenJSON with it. This is an example of goose typing—see “Goose Typing” if you need a refresher.


If it is a MutableSequence, it must be a list,6 so we build a list by passing each item in obj recursively to .build().


If it’s not a dict or a list, return the item as it is.

A FrozenJSON instance has the __data private instance attribute stored under the name _FrozenJSON__data, as explained in “Private and ‘Protected’ Attributes in Python”. Attempts to retrieve attributes by other names will trigger __getattr__. This method will first look if the self.__data dict has an attribute (not a key!) by that name; this allows FrozenJSON instances to handle dict methods such as items, by delegating to self.__data.items(). If self.__data doesn’t have an attribute with the given name, __getattr__ uses name as a key to retrieve an item from self.__data, and passes that item to FrozenJSON.build. This allows navigating through nested structures in the JSON data, as each nested mapping is converted to another FrozenJSON instance by the build class method.

Note that FrozenJSON does not transform or cache the original dataset. As we traverse the data, __getattr__ creates FrozenJSON instances again and again. That’s OK for a dataset of this size, and for a script that will only be used to explore or convert the data.

Any script that generates or emulates dynamic attribute names from arbitrary sources must deal with one issue: the keys in the original data may not be suitable attribute names. The next section addresses this.

The Invalid Attribute Name Problem
The FrozenJSON code doesn’t handle attribute names that are Python keywords. For example, if you build an object like this:

>>> student = FrozenJSON({'name': 'Jim Bo', 'class': 1982})
You won’t be able to read student.class because class is a reserved keyword in Python:

>>> student.class
  File "<stdin>", line 1
    student.class
         ^
SyntaxError: invalid syntax
You can always do this, of course:

>>> getattr(student, 'class')
1982
But the idea of FrozenJSON is to provide convenient access to the data, so a better solution is checking whether a key in the mapping given to FrozenJSON.__init__ is a keyword, and if so, append an _ to it, so the attribute can be read like this:

>>> student.class_
1982
This can be achieved by replacing the one-liner __init__ from Example 22-4 with the version in Example 22-5.

Example 22-5. explore1.py: append an _ to attribute names that are Python keywords
    def __init__(self, mapping):
        self.__data = {}
        for key, value in mapping.items():
            if keyword.iskeyword(key):  
                key += '_'
            self.__data[key] = value

The keyword.iskeyword(…) function is exactly what we need; to use it, the keyword module must be imported, which is not shown in this snippet.

A similar problem may arise if a key in a JSON record is not a valid Python identifier:

>>> x = FrozenJSON({'2be':'or not'})
>>> x.2be
  File "<stdin>", line 1
    x.2be
      ^
SyntaxError: invalid syntax
Such problematic keys are easy to detect in Python 3 because the str class provides the s.isidentifier() method, which tells you whether s is a valid Python identifier according to the language grammar. But turning a key that is not a valid identifier into a valid attribute name is not trivial. One solution would be to implement __getitem__ to allow attribute access using notation like x['2be']. For the sake of simplicity, I will not worry about this issue.

After giving some thought to the dynamic attribute names, let’s turn to another essential feature of FrozenJSON: the logic of the build class method. Frozen.JSON.build is used by __getattr__ to return a different type of object depending on the value of the attribute being accessed: nested structures are converted to FrozenJSON instances or lists of FrozenJSON instances.

Instead of a class method, the same logic could be implemented as the __new__ special method, as we’ll see next.

Flexible Object Creation with __new__
We often refer to __init__ as the constructor method, but that’s because we adopted jargon from other languages. In Python, __init__ gets self as the first argument, therefore the object already exists when __init__ is called by the interpreter. Also, __init__ cannot return anything. So it’s really an initializer, not a constructor.

When a class is called to create an instance, the special method that Python calls on that class to construct an instance is __new__. It’s a class method, but gets special treatment, so the @classmethod decorator is not applied to it. Python takes the instance returned by __new__ and then passes it as the first argument self of __init__. We rarely need to code __new__, because the implementation inherited from object suffices for the vast majority of use cases.

If necessary, the __new__ method can also return an instance of a different class. When that happens, the interpreter does not call __init__. In other words, Python’s logic for building an object is similar to this pseudocode:

# pseudocode for object construction
def make(the_class, some_arg):
    new_object = the_class.__new__(some_arg)
    if isinstance(new_object, the_class):
        the_class.__init__(new_object, some_arg)
    return new_object

# the following statements are roughly equivalent
x = Foo('bar')
x = make(Foo, 'bar')
Example 22-6 shows a variation of FrozenJSON where the logic of the former build class method was moved to __new__.

Example 22-6. explore2.py: using __new__ instead of build to construct new objects that may or may not be instances of FrozenJSON
from collections import abc
import keyword

class FrozenJSON:
    """A read-only façade for navigating a JSON-like object
       using attribute notation
    """

    def __new__(cls, arg):  
        if isinstance(arg, abc.Mapping):
            return super().__new__(cls)  
        elif isinstance(arg, abc.MutableSequence):  
            return [cls(item) for item in arg]
        else:
            return arg

    def __init__(self, mapping):
        self.__data = {}
        for key, value in mapping.items():
            if keyword.iskeyword(key):
                key += '_'
            self.__data[key] = value

    def __getattr__(self, name):
        try:
            return getattr(self.__data, name)
        except AttributeError:
            return FrozenJSON(self.__data[name])  

    def __dir__(self):
        return self.__data.keys()

As a class method, the first argument __new__ gets is the class itself, and the remaining arguments are the same that __init__ gets, except for self.


The default behavior is to delegate to the __new__ of a superclass. In this case, we are calling __new__ from the object base class, passing FrozenJSON as the only argument.


The remaining lines of __new__ are exactly as in the old build method.


This was where FrozenJSON.build was called before; now we just call the FrozenJSON class, which Python handles by calling FrozenJSON.__new__.

The __new__ method gets the class as the first argument because, usually, the created object will be an instance of that class. So, in FrozenJSON.__new__, when the expression super().__new__(cls) effectively calls object.__new__(FrozenJSON), the instance built by the object class is actually an instance of FrozenJSON. The __class__ attribute of the new instance will hold a reference to FrozenJSON, even though the actual construction is performed by object.__new__, implemented in C, in the guts of the interpreter.

The OSCON JSON dataset is structured in a way that is not helpful for interactive exploration. For example, the event at index 40, titled 'There *Will* Be Bugs' has two speakers, 3471 and 5199. Finding the names of the speakers is awkward, because those are serial numbers and the Schedule.speakers list is not indexed by them. To get each speaker, we must iterate over that list until we find a record with a matching serial number. Our next task is restructuring the data to prepare for automatic retrieval of linked records.

Computed Properties
We first saw the @property decorator in Chapter 11, in the section, “A Hashable Vector2d”. In Example 11-7, I used two properties in Vector2d just to make the x and y attributes read-only. Here we will see properties that compute values, leading to a discussion of how to cache such values.

The records in the 'events' list of the OSCON JSON data contain integer serial numbers pointing to records in the 'speakers' and 'venues' lists. For example, this is the record for a conference talk (with an elided description):

{ "serial": 33950,
  "name": "There *Will* Be Bugs",
  "event_type": "40-minute conference session",
  "time_start": "2014-07-23 14:30:00",
  "time_stop": "2014-07-23 15:10:00",
  "venue_serial": 1449,
  "description": "If you're pushing the envelope of programming...",
  "website_url": "http://oscon.com/oscon2014/public/schedule/detail/33950",
  "speakers": [3471, 5199],
  "categories": ["Python"] }
We will implement an Event class with venue and speakers properties to return the linked data automatically—in other words, “dereferencing” the serial number. Given an Event instance, Example 22-7 shows the desired behavior.

Example 22-7. Reading venue and speakers returns Record objects
    >>> event  
    <Event 'There *Will* Be Bugs'>
    >>> event.venue  
    <Record serial=1449>
    >>> event.venue.name  
    'Portland 251'
    >>> for spkr in event.speakers:  
    ...     print(f'{spkr.serial}: {spkr.name}')
    ...
    3471: Anna Martelli Ravenscroft
    5199: Alex Martelli

Given an Event instance…


…reading event.venue returns a Record object instead of a serial number.


Now it’s easy to get the name of the venue.


The event.speakers property returns a list of Record instances.

As usual, we will build the code step-by-step, starting with the Record class and a function to read the JSON data and return a dict with Record instances.

Step 1: Data-Driven Attribute Creation
Example 22-8 shows the doctest to guide this first step.

Example 22-8. Test-driving schedule_v1.py (from Example 22-9)
    >>> records = load(JSON_PATH)  
    >>> speaker = records['speaker.3471']  
    >>> speaker  
    <Record serial=3471>
    >>> speaker.name, speaker.twitter  
    ('Anna Martelli Ravenscroft', 'annaraven')

load a dict with the JSON data.


The keys in records are strings built from the record type and serial number.


speaker is an instance of the Record class defined in Example 22-9.


Fields from the original JSON can be retrieved as Record instance attributes.

The code for schedule_v1.py is in Example 22-9.

Example 22-9. schedule_v1.py: reorganizing the OSCON schedule data
import json

JSON_PATH = 'data/osconfeed.json'

class Record:
    def __init__(self, **kwargs):
        self.__dict__.update(kwargs)  

    def __repr__(self):
        return f'<{self.__class__.__name__} serial={self.serial!r}>'  

def load(path=JSON_PATH):
    records = {}  
    with open(path) as fp:
        raw_data = json.load(fp)  
    for collection, raw_records in raw_data['Schedule'].items():  
        record_type = collection[:-1]  
        for raw_record in raw_records:
            key = f'{record_type}.{raw_record["serial"]}' 
            records[key] = Record(**raw_record)  
    return records

This is a common shortcut to build an instance with attributes created from keyword arguments (detailed explanation follows).


Use the serial field to build the custom Record representation shown in Example 22-8.


load will ultimately return a dict of Record instances.


Parse the JSON, returning native Python objects: lists, dicts, strings, numbers, etc.


Iterate over the four top-level lists named 'conferences', 'events', 'speakers', and 'venues'.


record_type is the list name without the last character, so speakers becomes speaker. In Python ≥ 3.9 we can do this more explicitly with collection.removesuffix('s')—see PEP 616—String methods to remove prefixes and suffixes.


Build the key in the format 'speaker.3471'.


Create a Record instance and save it in records with the key.

The Record.__init__ method illustrates an old Python hack. Recall that the __dict__ of an object is where its attributes are kept—unless __slots__ is declared in the class, as we saw in “Saving Memory with __slots__”. So, updating an instance __dict__ with a mapping is a quick way to create a bunch of attributes in that instance.7

NOTE
Depending on the application, the Record class may need to deal with keys that are not valid attribute names, as we saw in “The Invalid Attribute Name Problem”. Dealing with that issue would distract from the key idea of this example, and is not a problem in the dataset we are reading.

The definition of Record in Example 22-9 is so simple that you may be wondering why I did not use it before, instead of the more complicated FrozenJSON. There are two reasons. First, FrozenJSON works by recursively converting the nested mappings and lists; Record doesn’t need that because our converted dataset doesn’t have mappings nested in mappings or lists. The records contain only strings, integers, lists of strings, and lists of integers. Second reason: FrozenJSON provides access to the embedded __data dict attributes—which we used to invoke methods like .keys()—and now we don’t need that functionality either.

NOTE
The Python standard library provides classes similar to Record, where each instance has an arbitrary set of attributes built from keyword arguments given to __init__: types.SimpleNamespace, argparse.Namespace, and multiprocessing.managers.Namespace. I wrote the simpler Record class to highlight the essential idea: __init__ updating the instance __dict__.

After reorganizing the schedule dataset, we can enhance the Record class to automatically retrieve venue and speaker records referenced in an event record. We’ll use properties to do that in the next examples.

Step 2: Property to Retrieve a Linked Record
The goal of this next version is: given an event record, reading its venue property will return a Record. This is similar to what the Django ORM does when you access a ForeignKey field: instead of the key, you get the linked model object.

We’ll start with the venue property. See the partial interaction in Example 22-10 as an example.

Example 22-10. Extract from the doctests of schedule_v2.py
    >>> event = Record.fetch('event.33950')  
    >>> event  
    <Event 'There *Will* Be Bugs'>
    >>> event.venue  
    <Record serial=1449>
    >>> event.venue.name  
    'Portland 251'
    >>> event.venue_serial  
    1449

The Record.fetch static method gets a Record or an Event from the dataset.


Note that event is an instance of the Event class.


Accessing event.venue returns a Record instance.


Now it’s easy to find out the name of an event.venue.


The Event instance also has a venue_serial attribute, from the JSON data.

Event is a subclass of Record adding a venue to retrieve linked records, and a specialized __repr__ method.

The code for this section is in the schedule_v2.py module in the Fluent Python code repository. The example has nearly 60 lines, so I’ll present it in parts, starting with the enhanced Record class.

Example 22-11. schedule_v2.py: Record class with a new fetch method
import inspect  
import json

JSON_PATH = 'data/osconfeed.json'

class Record:

    __index = None  

    def __init__(self, **kwargs):
        self.__dict__.update(kwargs)

    def __repr__(self):
        return f'<{self.__class__.__name__} serial={self.serial!r}>'

    @staticmethod  
    def fetch(key):
        if Record.__index is None:  
            Record.__index = load()
        return Record.__index[key]  

inspect will be used in load, listed in Example 22-13.


The __index private class attribute will eventually hold a reference to the dict returned by load.


fetch is a staticmethod to make it explicit that its effect is not influenced by the instance or class on which it is called.


Populate the Record.__index, if needed.


Use it to retrieve the record with the given key.

TIP
This is one example where the use of staticmethod makes sense. The fetch method always acts on the Record.__index class attribute, even if invoked from a subclass, like Event.fetch()—which we’ll soon explore. It would be misleading to code it as a class method because the cls first argument would not be used.

Now we get to the use of a property in the Event class, listed in Example 22-12.

Example 22-12. schedule_v2.py: the Event class
class Event(Record):  

    def __repr__(self):
        try:
            return f'<{self.__class__.__name__} {self.name!r}>'  
        except AttributeError:
            return super().__repr__()

    @property
    def venue(self):
        key = f'venue.{self.venue_serial}'
        return self.__class__.fetch(key)  

Event extends Record.


If the instance has a name attribute, it is used to produce a custom representation. Otherwise, delegate to the __repr__ from Record.


The venue property builds a key from the venue_serial attribute, and passes it to the fetch class method, inherited from Record (the reason for using self.__class__ is explained shortly).

The second line of the venue method of Example 22-12 returns self​.__class__.fetch(key). Why not simply call self.fetch(key)? The simpler form works with the specific OSCON dataset because there is no event record with a 'fetch' key. But, if an event record had a key named 'fetch', then within that specific Event instance, the reference self.fetch would retrieve the value of that field, instead of the fetch class method that Event inherits from Record. This is a subtle bug, and it could easily sneak through testing because it depends on the dataset.

WARNING
When creating instance attribute names from data, there is always the risk of bugs due to shadowing of class attributes—such as methods—or data loss through accidental overwriting of existing instance attributes. These problems may explain why Python dicts are not like JavaScript objects in the first place.

If the Record class behaved more like a mapping, implementing a dynamic __getitem__ instead of a dynamic __getattr__, there would be no risk of bugs from overwriting or shadowing. A custom mapping is probably the Pythonic way to implement Record. But if I took that road, we’d not be studying the tricks and traps of dynamic attribute programming.

The final piece of this example is the revised load function in Example 22-13.

Example 22-13. schedule_v2.py: the load function
def load(path=JSON_PATH):
    records = {}
    with open(path) as fp:
        raw_data = json.load(fp)
    for collection, raw_records in raw_data['Schedule'].items():
        record_type = collection[:-1]  
        cls_name = record_type.capitalize()  
        cls = globals().get(cls_name, Record)  
        if inspect.isclass(cls) and issubclass(cls, Record):  
            factory = cls  
        else:
            factory = Record  
        for raw_record in raw_records:  
            key = f'{record_type}.{raw_record["serial"]}'
            records[key] = factory(**raw_record)  
    return records

So far, no changes from the load in schedule_v1.py (Example 22-9).


Capitalize the record_type to get a possible class name; e.g., 'event' becomes 'Event'.


Get an object by that name from the module global scope; get the Record class if there’s no such object.


If the object just retrieved is a class, and is a subclass of Record…


…bind the factory name to it. This means factory may be any subclass of Record, depending on the record_type.


Otherwise, bind the factory name to Record.


The for loop that creates the key and saves the records is the same as before, except that…


…the object stored in records is constructed by factory, which may be Record or a subclass like Event, selected according to the record_type.

Note that the only record_type that has a custom class is Event, but if classes named Speaker or Venue are coded, load will automatically use those classes when building and saving records, instead of the default Record class.

We’ll now apply the same idea to a new speakers property in the Events class.

Step 3: Property Overriding an Existing Attribute
The name of the venue property in Example 22-12 does not match a field name in records of the "events" collection. Its data comes from a venue_serial field name. In contrast, each record in the events collection has a speakers field with a list of serial numbers. We want to expose that information as a speakers property in Event instances, which returns a list of Record instances. This name clash requires some special attention, as Example 22-14 reveals.

Example 22-14. schedule_v3.py: the speakers property
    @property
    def speakers(self):
        spkr_serials = self.__dict__['speakers']  
        fetch = self.__class__.fetch
        return [fetch(f'speaker.{key}')
                for key in spkr_serials]  

The data we want is in a speakers attribute, but we must retrieve it directly from the instance __dict__ to avoid a recursive call to the speakers property.


Return a list of all records with keys corresponding to the numbers in spkr_serials.

Inside the speakers method, trying to read self.speakers will invoke the property itself, quickly raising a RecursionError. However, if we read the same data via self.__dict__['speakers'], Python’s usual algorithm for retrieving attributes is bypassed, the property is not called, and the recursion is avoided. For this reason, reading or writing data directly to an object’s __dict__ is a common Python metaprogramming trick.

WARNING
The interpreter evaluates obj.my_attr by first looking at the class of obj. If the class has a property with the my_attr name, that property shadows an instance attribute by the same name. Examples in “Properties Override Instance Attributes” will demonstrate this, and Chapter 23 will reveal that a property is implemented as a descriptor—a more powerful and general abstraction.

As I coded the list comprehension in Example 22-14, my programmer’s lizard brain thought: “This may be expensive.” Not really, because events in the OSCON dataset have few speakers, so coding anything more complicated would be premature optimization. However, caching a property is a common need—and there are caveats. So let’s see how to do that in the next examples.

Step 4: Bespoke Property Cache
Caching properties is a common need because there is an expectation that an expression like event.venue should be inexpensive.8 Some form of caching could become necessary if the Record.fetch method behind the Event properties needed to query a database or a web API.

In the first edition Fluent Python, I coded the custom caching logic for the speakers method, as shown in Example 22-15.

Example 22-15. Custom caching logic using hasattr disables key-sharing optimization
    @property
    def speakers(self):
        if not hasattr(self, '__speaker_objs'):  
            spkr_serials = self.__dict__['speakers']
            fetch = self.__class__.fetch
            self.__speaker_objs = [fetch(f'speaker.{key}')
                    for key in spkr_serials]
        return self.__speaker_objs  

If the instance doesn’t have an attribute named __speaker_objs, fetch the speaker objects and store them there.


Return self.__speaker_objs.

The handmade caching in Example 22-15 is straightforward, but creating an attribute after the instance is initialized defeats the PEP 412—Key-Sharing Dictionary optimization, as explained in “Practical Consequences of How dict Works”. Depending on the size of the dataset, the difference in memory usage may be important.

A similar hand-rolled solution that works well with the key-sharing optimization requires coding an __init__ for the Event class, to create the necessary __speaker_objs initialized to None, and then checking for that in the speakers method. See Example 22-16.

Example 22-16. Storage defined in __init__ to leverage key-sharing optimization
class Event(Record):

    def __init__(self, **kwargs):
        self.__speaker_objs = None
        super().__init__(**kwargs)

# 15 lines omitted...
    @property
    def speakers(self):
        if self.__speaker_objs is None:
            spkr_serials = self.__dict__['speakers']
            fetch = self.__class__.fetch
            self.__speaker_objs = [fetch(f'speaker.{key}')
                    for key in spkr_serials]
        return self.__speaker_objs
Examples 22-15 and 22-16 illustrate simple caching techniques that are fairly common in legacy Python codebases. However, in multithreaded programs, handmade caches like those introduce race conditions that may lead to corrupted data. If two threads are reading a property that was not previously cached, the first thread will need to compute the data for the cache attribute (__speaker_objs in the examples) and the second thread may read a cached value that is not yet complete.

Fortunately, Python 3.8 introduced the @functools.cached_property decorator, which is thread safe. Unfortunately, it comes with a couple of caveats, explained next.

Step 5: Caching Properties with functools
The functools module provides three decorators for caching. We saw @cache and @lru_cache in “Memoization with functools.cache” (Chapter 9). Python 3.8 introduced @cached_property.

The functools.cached_property decorator caches the result of the method in an instance attribute with the same name. For example, in Example 22-17, the value computed by the venue method is stored in a venue attribute in self. After that, when client code tries to read venue, the newly created venue instance attribute is used instead of the method.

Example 22-17. Simple use of a @cached_property
    @cached_property
    def venue(self):
        key = f'venue.{self.venue_serial}'
        return self.__class__.fetch(key)
In “Step 3: Property Overriding an Existing Attribute”, we saw that a property shadows an instance attribute by the same name. If that is true, how can @cached_property work? If the property overrides the instance attribute, the venue attribute will be ignored and the venue method will always be called, computing the key and running fetch every time!

The answer is a bit sad: cached_property is a misnomer. The @cached_property decorator does not create a full-fledged property, it creates a nonoverriding descriptor. A descriptor is an object that manages the access to an attribute in another class. We will dive into descriptors in Chapter 23. The property decorator is a high-level API to create an overriding descriptor. Chapter 23 will include a through explanation about overriding versus nonoverriding descriptors.

For now, let us set aside the underlying implementation and focus on the differences between cached_property and property from a user’s point of view. Raymond Hettinger explains them very well in the Python docs:

The mechanics of cached_property() are somewhat different from property(). A regular property blocks attribute writes unless a setter is defined. In contrast, a cached_property allows writes.

The cached_property decorator only runs on lookups and only when an attribute of the same name doesn’t exist. When it does run, the cached_property writes to the attribute with the same name. Subsequent attribute reads and writes take precedence over the cached_property method and it works like a normal attribute.

The cached value can be cleared by deleting the attribute. This allows the cached_property method to run again.9

Back to our Event class: the specific behavior of @cached_property makes it unsuitable to decorate speakers, because that method relies on an existing attribute also named speakers, containing the serial numbers of the event speakers.

WARNING
@cached_property has some important limitations:

It cannot be used as a drop-in replacement to @property if the decorated method already depends on an instance attribute with the same name.

It cannot be used in a class that defines __slots__.

It defeats the key-sharing optimization of the instance __dict__, because it creates an instance attribute after __init__.

Despite these limitations, @cached_property addresses a common need in a simple way, and it is thread safe. Its Python code is an example of using a reentrant lock.

The @cached_property documentation recommends an alternative solution that we can use with speakers: stacking @property and @cache decorators, as shown in Example 22-18.

Example 22-18. Stacking @property on @cache
    @property  
    @cache  
    def speakers(self):
        spkr_serials = self.__dict__['speakers']
        fetch = self.__class__.fetch
        return [fetch(f'speaker.{key}')
                for key in spkr_serials]

The order is important: @property goes on top…


…of @cache.

Recall from “Stacked Decorators” the meaning of that syntax. The top three lines of Example 22-18 are similar to:

speakers = property(cache(speakers))
The @cache is applied to speakers, returning a new function. That function then is decorated by @property, which replaces it with a newly constructed property.

This wraps up our discussion of read-only properties and caching decorators, exploring the OSCON dataset. In the next section, we start a new series of examples creating read/write properties.

Using a Property for Attribute Validation
Besides computing attribute values, properties are also used to enforce business rules by changing a public attribute into an attribute protected by a getter and setter without affecting client code. Let’s work through an extended example.

LineItem Take #1: Class for an Item in an Order
Imagine an app for a store that sells organic food in bulk, where customers can order nuts, dried fruit, or cereals by weight. In that system, each order would hold a sequence of line items, and each line item could be represented by an instance of a class, as in Example 22-19.

Example 22-19. bulkfood_v1.py: the simplest LineItem class
class LineItem:

    def __init__(self, description, weight, price):
        self.description = description
        self.weight = weight
        self.price = price

    def subtotal(self):
        return self.weight * self.price
That’s nice and simple. Perhaps too simple. Example 22-20 shows a problem.

Example 22-20. A negative weight results in a negative subtotal
    >>> raisins = LineItem('Golden raisins', 10, 6.95)
    >>> raisins.subtotal()
    69.5
    >>> raisins.weight = -20  # garbage in...
    >>> raisins.subtotal()    # garbage out...
    -139.0
This is a toy example, but not as fanciful as you may think. Here is a story from the early days of Amazon.com:

We found that customers could order a negative quantity of books! And we would credit their credit card with the price and, I assume, wait around for them to ship the books.

 Jeff Bezos, founder and CEO of Amazon.com10

How do we fix this? We could change the interface of LineItem to use a getter and a setter for the weight attribute. That would be the Java way, and it’s not wrong.

On the other hand, it’s natural to be able to set the weight of an item by just assigning to it; and perhaps the system is in production with other parts already accessing item.weight directly. In this case, the Python way would be to replace the data attribute with a property.

LineItem Take #2: A Validating Property
Implementing a property will allow us to use a getter and a setter, but the interface of LineItem will not change (i.e., setting the weight of a LineItem will still be written as raisins.weight = 12).

Example 22-21 lists the code for a read/write weight property.

Example 22-21. bulkfood_v2.py: a LineItem with a weight property
class LineItem:

    def __init__(self, description, weight, price):
        self.description = description
        self.weight = weight  
        self.price = price

    def subtotal(self):
        return self.weight * self.price

    @property  
    def weight(self):  
        return self.__weight  

    @weight.setter  
    def weight(self, value):
        if value > 0:
            self.__weight = value  
        else:
            raise ValueError('value must be > 0')  

Here the property setter is already in use, making sure that no instances with negative weight can be created.


@property decorates the getter method.


All the methods that implement a property share the name of the public attribute: weight.


The actual value is stored in a private attribute __weight.


The decorated getter has a .setter attribute, which is also a decorator; this ties the getter and setter together.


If the value is greater than zero, we set the private __weight.


Otherwise, ValueError is raised.

Note how a LineItem with an invalid weight cannot be created now:

>>> walnuts = LineItem('walnuts', 0, 10.00)
Traceback (most recent call last):
    ...
ValueError: value must be > 0
Now we have protected weight from users providing negative values. Although buyers usually can’t set the price of an item, a clerical error or a bug may create a LineItem with a negative price. To prevent that, we could also turn price into a property, but this would entail some repetition in our code.

Remember the Paul Graham quote from Chapter 17: “When I see patterns in my programs, I consider it a sign of trouble.” The cure for repetition is abstraction. There are two ways to abstract away property definitions: using a property factory or a descriptor class. The descriptor class approach is more flexible, and we’ll devote Chapter 23 to a full discussion of it. Properties are in fact implemented as descriptor classes themselves. But here we will continue our exploration of properties by implementing a property factory as a function.

But before we can implement a property factory, we need to have a deeper understanding of properties.

A Proper Look at Properties
Although often used as a decorator, the property built-in is actually a class. In Python, functions and classes are often interchangeable, because both are callable and there is no new operator for object instantiation, so invoking a constructor is no different from invoking a factory function. And both can be used as decorators, as long as they return a new callable that is a suitable replacement of the decorated callable.

This is the full signature of the property constructor:

property(fget=None, fset=None, fdel=None, doc=None)
All arguments are optional, and if a function is not provided for one of them, the corresponding operation is not allowed by the resulting property object.

The property type was added in Python 2.2, but the @ decorator syntax appeared only in Python 2.4, so for a few years, properties were defined by passing the accessor functions as the first two arguments.

The “classic” syntax for defining properties without decorators is illustrated in Example 22-22.

Example 22-22. bulkfood_v2b.py: same as Example 22-21, but without using decorators
class LineItem:

    def __init__(self, description, weight, price):
        self.description = description
        self.weight = weight
        self.price = price

    def subtotal(self):
        return self.weight * self.price

    def get_weight(self):  
        return self.__weight

    def set_weight(self, value):  
        if value > 0:
            self.__weight = value
        else:
            raise ValueError('value must be > 0')

    weight = property(get_weight, set_weight)  

A plain getter.


A plain setter.


Build the property and assign it to a public class attribute.

The classic form is better than the decorator syntax in some situations; the code of the property factory we’ll discuss shortly is one example. On the other hand, in a class body with many methods, the decorators make it explicit which are the getters and setters, without depending on the convention of using get and set prefixes in their names.

The presence of a property in a class affects how attributes in instances of that class can be found in a way that may be surprising at first. The next section explains.

Properties Override Instance Attributes
Properties are always class attributes, but they actually manage attribute access in the instances of the class.

In “Overriding Class Attributes” we saw that when an instance and its class both have a data attribute by the same name, the instance attribute overrides, or shadows, the class attribute—at least when read through that instance. Example 22-23 illustrates this point.

Example 22-23. Instance attribute shadows the class data attribute
>>> class Class:  
...     data = 'the class data attr'
...     @property
...     def prop(self):
...         return 'the prop value'
...
>>> obj = Class()
>>> vars(obj)  
{}
>>> obj.data  
'the class data attr'
>>> obj.data = 'bar' 
>>> vars(obj)  
{'data': 'bar'}
>>> obj.data  
'bar'
>>> Class.data  
'the class data attr'

Define Class with two class attributes: the data attribute and the prop property.


vars returns the __dict__ of obj, showing it has no instance attributes.


Reading from obj.data retrieves the value of Class.data.


Writing to obj.data creates an instance attribute.


Inspect the instance to see the instance attribute.


Now reading from obj.data retrieves the value of the instance attribute. When read from the obj instance, the instance data shadows the class data.


The Class.data attribute is intact.

Now, let’s try to override the prop attribute on the obj instance. Resuming the previous console session, we have Example 22-24.

Example 22-24. Instance attribute does not shadow the class property (continued from Example 22-23)
>>> Class.prop  
<property object at 0x1072b7408>
>>> obj.prop  
'the prop value'
>>> obj.prop = 'foo'  
Traceback (most recent call last):
  ...
AttributeError: can't set attribute
>>> obj.__dict__['prop'] = 'foo'  
>>> vars(obj)  
{'data': 'bar', 'prop': 'foo'}
>>> obj.prop  
'the prop value'
>>> Class.prop = 'baz'  
>>> obj.prop  
'foo'

Reading prop directly from Class retrieves the property object itself, without running its getter method.


Reading obj.prop executes the property getter.


Trying to set an instance prop attribute fails.


Putting 'prop' directly in the obj.__dict__ works.


We can see that obj now has two instance attributes: data and prop.


However, reading obj.prop still runs the property getter. The property is not shadowed by an instance attribute.


Overwriting Class.prop destroys the property object.


Now obj.prop retrieves the instance attribute. Class.prop is not a property anymore, so it no longer overrides obj.prop.

As a final demonstration, we’ll add a new property to Class, and see it overriding an instance attribute. Example 22-25 picks up where Example 22-24 left off.

Example 22-25. New class property shadows the existing instance attribute (continued from Example 22-24)
>>> obj.data  
'bar'
>>> Class.data  
'the class data attr'
>>> Class.data = property(lambda self: 'the "data" prop value')  
>>> obj.data  
'the "data" prop value'
>>> del Class.data  
>>> obj.data  
'bar'

obj.data retrieves the instance data attribute.


Class.data retrieves the class data attribute.


Overwrite Class.data with a new property.


obj.data is now shadowed by the Class.data property.


Delete the property.


obj.data now reads the instance data attribute again.

The main point of this section is that an expression like obj.data does not start the search for data in obj. The search actually starts at obj.__class__, and only if there is no property named data in the class, Python looks in the obj instance itself. This applies to overriding descriptors in general, of which properties are just one example. Further treatment of descriptors must wait for Chapter 23.

Now back to properties. Every Python code unit—modules, functions, classes, methods—can have a docstring. The next topic is how to attach documentation to properties.

Property Documentation
When tools such as the console help() function or IDEs need to display the documentation of a property, they extract the information from the __doc__ attribute of the property.

If used with the classic call syntax, property can get the documentation string as the doc argument:

    weight = property(get_weight, set_weight, doc='weight in kilograms')
The docstring of the getter method—the one with the @property decorator itself—is used as the documentation of the property as a whole. Figure 22-1 shows the help screens generated from the code in Example 22-26.


Figure 22-1. Screenshots of the Python console when issuing the commands help(Foo.bar) and help(Foo). Source code is in Example 22-26.
Example 22-26. Documentation for a property
class Foo:

    @property
    def bar(self):
        """The bar attribute"""
        return self.__dict__['bar']

    @bar.setter
    def bar(self, value):
        self.__dict__['bar'] = value
Now that we have these property essentials covered, let’s go back to the issue of protecting both the weight and price attributes of LineItem so they only accept values greater than zero—but without implementing two nearly identical pairs of getters/setters by hand.

Coding a Property Factory
We’ll create a factory to create quantity properties—so named because the managed attributes represent quantities that can’t be negative or zero in the application. Example 22-27 shows the clean look of the LineItem class using two instances of quantity properties: one for managing the weight attribute, the other for price.

Example 22-27. bulkfood_v2prop.py: the quantity property factory in use
class LineItem:
    weight = quantity('weight')  
    price = quantity('price')  

    def __init__(self, description, weight, price):
        self.description = description
        self.weight = weight  
        self.price = price

    def subtotal(self):
        return self.weight * self.price  

Use the factory to define the first custom property, weight, as a class attribute.


This second call builds another custom property, price.


Here the property is already active, making sure a negative or 0 weight is rejected.


The properties are also in use here, retrieving the values stored in the instance.

Recall that properties are class attributes. When building each quantity property, we need to pass the name of the LineItem attribute that will be managed by that specific property. Having to type the word weight twice in this line is unfortunate:

    weight = quantity('weight')
But avoiding that repetition is complicated because the property has no way of knowing which class attribute name will be bound to it. Remember: the righthand side of an assignment is evaluated first, so when quantity() is invoked, the weight class attribute doesn’t even exist.

NOTE
Improving the quantity property so that the user doesn’t need to retype the attribute name is a nontrivial metaprogramming problem. We’ll solve that problem in Chapter 23.

Example 22-28 lists the implementation of the quantity property factory.11

Example 22-28. bulkfood_v2prop.py: the quantity property factory
def quantity(storage_name):  

    def qty_getter(instance):  
        return instance.__dict__[storage_name]  

    def qty_setter(instance, value):  
        if value > 0:
            instance.__dict__[storage_name] = value  
        else:
            raise ValueError('value must be > 0')

    return property(qty_getter, qty_setter)  

The storage_name argument determines where the data for each property is stored; for the weight, the storage name will be 'weight'.


The first argument of the qty_getter could be named self, but that would be strange because this is not a class body; instance refers to the LineItem instance where the attribute will be stored.


qty_getter references storage_name, so it will be preserved in the closure of this function; the value is retrieved directly from the instance.__dict__ to bypass the property and avoid an infinite recursion.


qty_setter is defined, also taking instance as first argument.


The value is stored directly in the instance.__dict__, again bypassing the property.


Build a custom property object and return it.

The bits of Example 22-28 that deserve careful study revolve around the storage_name variable. When you code each property in the traditional way, the name of the attribute where you will store a value is hardcoded in the getter and setter methods. But here, the qty_getter and qty_setter functions are generic, and they depend on the storage_name variable to know where to get/set the managed attribute in the instance __dict__. Each time the quantity factory is called to build a property, the storage_name must be set to a unique value.

The functions qty_getter and qty_setter will be wrapped by the property object created in the last line of the factory function. Later, when called to perform their duties, these functions will read the storage_name from their closures to determine where to retrieve/store the managed attribute values.

In Example 22-29, I create and inspect a LineItem instance, exposing the storage attributes.

Example 22-29. bulkfood_v2prop.py: exploring properties and storage attributes
    >>> nutmeg = LineItem('Moluccan nutmeg', 8, 13.95)
    >>> nutmeg.weight, nutmeg.price  
    (8, 13.95)
    >>> nutmeg.__dict__  
    {'description': 'Moluccan nutmeg', 'weight': 8, 'price': 13.95}

Reading the weight and price through the properties shadowing the namesake instance attributes.


Using vars to inspect the nutmeg instance: here we see the actual instance attributes used to store the values.

Note how the properties built by our factory leverage the behavior described in “Properties Override Instance Attributes”: the weight property overrides the weight instance attribute so that every reference to self.weight or nutmeg.weight is handled by the property functions, and the only way to bypass the property logic is to access the instance __dict__ directly.

The code in Example 22-28 may be a bit tricky, but it’s concise: it’s identical in length to the decorated getter/setter pair defining just the weight property in Example 22-21. The LineItem definition in Example 22-27 looks much better without the noise of the getter/setters.

In a real system, that same kind of validation may appear in many fields, across several classes, and the quantity factory would be placed in a utility module to be used over and over again. Eventually that simple factory could be refactored into a more extensible descriptor class, with specialized subclasses performing different validations. We’ll do that in Chapter 23.

Now let us wrap up the discussion of properties with the issue of attribute deletion.

Handling Attribute Deletion
We can use the del statement to delete not only variables, but also attributes:

>>> class Demo:
...    pass
...
>>> d = Demo()
>>> d.color = 'green'
>>> d.color
'green'
>>> del d.color
>>> d.color
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Demo' object has no attribute 'color'
In practice, deleting attributes is not something we do every day in Python, and the requirement to handle it with a property is even more unusual. But it is supported, and I can think of a silly example to demonstrate it.

In a property definition, the @my_property.deleter decorator wraps the method in charge of deleting the attribute managed by the property. As promised, silly Example 22-30 is inspired by the scene with the Black Knight from Monty Python and the Holy Grail.12

Example 22-30. blackknight.py
class BlackKnight:

    def __init__(self):
        self.phrases = [
            ('an arm', "'Tis but a scratch."),
            ('another arm', "It's just a flesh wound."),
            ('a leg', "I'm invincible!"),
            ('another leg', "All right, we'll call it a draw.")
        ]

    @property
    def member(self):
        print('next member is:')
        return self.phrases[0][0]

    @member.deleter
    def member(self):
        member, text = self.phrases.pop(0)
        print(f'BLACK KNIGHT (loses {member}) -- {text}')
The doctests in blackknight.py are in Example 22-31.

Example 22-31. blackknight.py: doctests for Example 22-30 (the Black Knight never concedes defeat)
    >>> knight = BlackKnight()
    >>> knight.member
    next member is:
    'an arm'
    >>> del knight.member
    BLACK KNIGHT (loses an arm) -- 'Tis but a scratch.
    >>> del knight.member
    BLACK KNIGHT (loses another arm) -- It's just a flesh wound.
    >>> del knight.member
    BLACK KNIGHT (loses a leg) -- I'm invincible!
    >>> del knight.member
    BLACK KNIGHT (loses another leg) -- All right, we'll call it a draw.
Using the classic call syntax instead of decorators, the fdel argument configures the deleter function. For example, the member property would be coded like this in the body of the BlackKnight class:

    member = property(member_getter, fdel=member_deleter)
If you are not using a property, attribute deletion can also be handled by implementing the lower-level __delattr__ special method, presented in “Special Methods for Attribute Handling”. Coding a silly class with __delattr__ is left as an exercise to the procrastinating reader.

Properties are a powerful feature, but sometimes simpler or lower-level alternatives are preferable. In the final section of this chapter, we’ll review some of the core APIs that Python offers for dynamic attribute programming.

Essential Attributes and Functions for Attribute Handling
Throughout this chapter, and even before in the book, we’ve used some of the built-in functions and special methods Python provides for dealing with dynamic attributes. This section gives an overview of them in one place, because their documentation is scattered in the official docs.

Special Attributes that Affect Attribute Handling
The behavior of many of the functions and special methods listed in the following sections depend on three special attributes:

__class__
A reference to the object’s class (i.e., obj.__class__ is the same as type(obj)). Python looks for special methods such as __getattr__ only in an object’s class, and not in the instances themselves.

__dict__
A mapping that stores the writable attributes of an object or class. An object that has a __dict__ can have arbitrary new attributes set at any time. If a class has a __slots__ attribute, then its instances may not have a __dict__. See __slots__ (next).

__slots__
An attribute that may be defined in a class to save memory. __slots__ is a tuple of strings naming the allowed attributes.13 If the '__dict__' name is not in __slots__, then the instances of that class will not have a __dict__ of their own, and only the attributes listed in __slots__ will be allowed in those instances. Recall “Saving Memory with __slots__” for more.

Built-In Functions for Attribute Handling
These five built-in functions perform object attribute reading, writing, and introspection:

dir([object])
Lists most attributes of the object. The official docs say dir is intended for interactive use so it does not provide a comprehensive list of attributes, but an “interesting” set of names. dir can inspect objects implemented with or without a __dict__. The __dict__ attribute itself is not listed by dir, but the __dict__ keys are listed. Several special attributes of classes, such as __mro__, __bases__, and __name__, are not listed by dir either. You can customize the output of dir by implementing the __dir__ special method, as we saw in Example 22-4. If the optional object argument is not given, dir lists the names in the current scope.

getattr(object, name[, default])
Gets the attribute identified by the name string from the object. The main use case is to retrieve attributes (or methods) whose names we don’t know beforehand. This may fetch an attribute from the object’s class or from a superclass. If no such attribute exists, getattr raises AttributeError or returns the default value, if given. One great example of using gettatr is in the Cmd.onecmd method in the cmd package of the standard library, where it is used to get and execute a user-defined command.

hasattr(object, name)
Returns True if the named attribute exists in the object, or can be somehow fetched through it (by inheritance, for example). The documentation explains: “This is implemented by calling getattr(object, name) and seeing whether it raises an AttributeError or not.”

setattr(object, name, value)
Assigns the value to the named attribute of object, if the object allows it. This may create a new attribute or overwrite an existing one.

vars([object])
Returns the __dict__ of object; vars can’t deal with instances of classes that define __slots__ and don’t have a __dict__ (contrast with dir, which handles such instances). Without an argument, vars() does the same as locals(): returns a dict representing the local scope.

Special Methods for Attribute Handling
When implemented in a user-defined class, the special methods listed here handle attribute retrieval, setting, deletion, and listing.

Attribute access using either dot notation or the built-in functions getattr, hasattr, and setattr triggers the appropriate special methods listed here. Reading and writing attributes directly in the instance __dict__ does not trigger these special methods—and that’s the usual way to bypass them if needed.

Section “3.3.11. Special method lookup” of the “Data model” chapter warns:

For custom classes, implicit invocations of special methods are only guaranteed to work correctly if defined on an object’s type, not in the object’s instance dictionary.

In other words, assume that the special methods will be retrieved on the class itself, even when the target of the action is an instance. For this reason, special methods are not shadowed by instance attributes with the same name.

In the following examples, assume there is a class named Class, obj is an instance of Class, and attr is an attribute of obj.

For every one of these special methods, it doesn’t matter if the attribute access is done using dot notation or one of the built-in functions listed in “Built-In Functions for Attribute Handling”. For example, both obj.attr and getattr(obj, 'attr', 42) trigger Class.__getattribute__(obj, 'attr').

__delattr__(self, name)
Always called when there is an attempt to delete an attribute using the del statement; e.g., del obj.attr triggers Class.__delattr__(obj, 'attr'). If attr is a property, its deleter method is never called if the class implements __delattr__.

__dir__(self)
Called when dir is invoked on the object, to provide a listing of attributes; e.g., dir(obj) triggers Class.__dir__(obj). Also used by tab-completion in all modern Python consoles.

__getattr__(self, name)
Called only when an attempt to retrieve the named attribute fails, after the obj, Class, and its superclasses are searched. The expressions obj.no_such_attr, getattr(obj, 'no_such_attr'), and hasattr(obj, 'no_such_attr') may trigger Class.__getattr__(obj, 'no_such_attr'), but only if an attribute by that name cannot be found in obj or in Class and its superclasses.

__getattribute__(self, name)
Always called when there is an attempt to retrieve the named attribute directly from Python code (the interpreter may bypass this in some cases, for example, to get the __repr__ method). Dot notation and the getattr and hasattr built-ins trigger this method. __getattr__ is only invoked after __getattribute__, and only when __getattribute__ raises AttributeError. To retrieve attributes of the instance obj without triggering an infinite recursion, implementations of __getattribute__ should use super().__getattribute__(obj, name).

__setattr__(self, name, value)
Always called when there is an attempt to set the named attribute. Dot notation and the setattr built-in trigger this method; e.g., both obj.attr = 42 and setattr(obj, 'attr', 42) trigger Class.__setattr__(obj, 'attr', 42).

WARNING
In practice, because they are unconditionally called and affect practically every attribute access, the __getattribute__ and __setattr__ special methods are harder to use correctly than __getattr__, which only handles nonexisting attribute names. Using properties or descriptors is less error prone than defining these special methods.

This concludes our dive into properties, special methods, and other techniques for coding dynamic attributes.

Chapter Summary
We started our coverage of dynamic attributes by showing practical examples of simple classes to make it easier to deal with a JSON dataset. The first example was the FrozenJSON class that converted nested dicts and lists into nested FrozenJSON instances and lists of them. The FrozenJSON code demonstrated the use of the __getattr__ special method to convert data structures on the fly, whenever their attributes were read. The last version of FrozenJSON showcased the use of the __new__ constructor method to transform a class into a flexible factory of objects, not limited to instances of itself.

We then converted the JSON dataset to a dict storing instances of a Record class. The first rendition of Record was a few lines long and introduced the “bunch” idiom: using self.__dict__.update(**kwargs) to build arbitrary attributes from keyword arguments passed to __init__. The second iteration added the Event class, implementing automatic retrieval of linked records through properties. Computed property values sometimes require caching, and we covered a few ways of doing that.

After realizing that @functools.cached_property is not always applicable, we learned about an alternative: combining @property on top of @functools.cache, in that order.

Coverage of properties continued with the LineItem class, where a property was deployed to protect a weight attribute from negative or zero values that make no business sense. After a deeper look at property syntax and semantics, we created a property factory to enforce the same validation on weight and price, without coding multiple getters and setters. The property factory leveraged subtle concepts—such as closures, and instance attribute overriding by properties—to provide an elegant generic solution using the same number of lines as a single hand-coded property definition.

Finally, we had a brief look at handling attribute deletion with properties, followed by an overview of the key special attributes, built-in functions, and special methods that support attribute metaprogramming in the core Python language.

Further Reading
The official documentation for the attribute handling and introspection built-in functions is Chapter 2, “Built-in Functions” of The Python Standard Library. The related special methods and the __slots__ special attribute are documented in The Python Language Reference in “3.3.2. Customizing attribute access”. The semantics of how special methods are invoked bypassing instances is explained in “3.3.9. Special method lookup”. In Chapter 4, “Built-in Types,” of The Python Standard Library, “4.13. Special Attributes” covers __class__ and __dict__ attributes.

Python Cookbook, 3rd ed., by David Beazley and Brian K. Jones (O’Reilly) has several recipes covering the topics of this chapter, but I will highlight three that are outstanding: “Recipe 8.8. Extending a Property in a Subclass” addresses the thorny issue of overriding the methods inside a property inherited from a superclass; “Recipe 8.15. Delegating Attribute Access” implements a proxy class showcasing most special methods from “Special Methods for Attribute Handling” in this book; and the awesome “Recipe 9.21. Avoiding Repetitive Property Methods,” which was the basis for the property factory function presented in Example 22-28.

Python in a Nutshell, 3rd ed., by Alex Martelli, Anna Ravenscroft, and Steve Holden (O’Reilly) is rigorous and objective. They devote only three pages to properties, but that’s because the book follows an axiomatic presentation style: the preceding 15 pages or so provide a thorough description of the semantics of Python classes from the ground up, including descriptors, which are how properties are actually implemented under the hood. So by the time Martelli et al., get to properties, they pack a lot of insights in those three pages—including what I selected to open this chapter.

Bertrand Meyer—quoted in the Uniform Access Principle definition in this chapter opening—pioneered the Design by Contract methodology, designed the Eiffel language, and wrote the excellent Object-Oriented Software Construction, 2nd ed. (Pearson). The first six chapters provide one of the best conceptual introductions to OO analysis and design I’ve seen. Chapter 11 presents Design by Contract, and Chapter 35 offers Meyer’s assessments of some influential object-oriented languages: Simula, Smalltalk, CLOS (the Common Lisp Object System), Objective-C, C++, and Java, with brief comments on some others. Only in the last page of the book does he reveal that the highly readable “notation” he uses as pseudocode is Eiffel.

SOAPBOX
Meyer’s Uniform Access Principle is aesthetically appealing. As a programmer using an API, I shouldn’t have to care whether product.price simply fetches a data attribute or performs a computation. As a consumer and a citizen, I do care: in e-commerce today the value of product.price often depends on who is asking, so it’s certainly not a mere data attribute. In fact, it’s common practice that the price is lower if the query comes from outside the store—say, from a price-comparison engine. This effectively punishes loyal customers who like to browse within a particular store. But I digress.

The previous digression does raise a relevant point for programming: although the Uniform Access Principle makes perfect sense in an ideal world, in reality, users of an API may need to know whether reading product.price is potentially too expensive or time-consuming. That’s a problem with programming abstractions in general: they make it hard to reason about the runtime cost of evaluating an expression. On the other hand, abstractions let users accomplish more with less code. It’s a trade-off. As usual in matters of software engineering, Ward Cunningham’s original wiki hosts insightful arguments about the merits of the Uniform Access Principle.

In object-oriented programming languages, application or violations of the Uniform Access Principle often revolve around the syntax of reading public data attributes versus invoking getter/setter methods.

Smalltalk and Ruby address this issue in a simple and elegant way: they don’t support public data attributes at all. Every instance attribute in these languages is private, so every access to them must be through methods. But their syntax makes this painless: in Ruby, product.price invokes the price getter; in Smalltalk, it’s simply product price.

At the other end of the spectrum, the Java language allows the programmer to choose among four access-level modifiers—including the no-name default that the Java Tutorial calls “package-private.”

The general practice does not agree with the syntax established by the Java designers, though. Everybody in Java-land agrees that attributes should be private, and you must spell it out every time, because it’s not the default. When all attributes are private, all access to them from outside the class must go through accessors. Java IDEs include shortcuts for generating accessor methods automatically. Unfortunately, the IDE is not so helpful when you must read the code six months later. It’s up to you to wade through a sea of do-nothing accessors to find those that add value by implementing some business logic.

Alex Martelli speaks for the majority of the Python community when he calls accessors “goofy idioms” and then provides these examples that look very different but do the same thing:14

someInstance.widgetCounter += 1
# rather than...
someInstance.setWidgetCounter(someInstance.getWidgetCounter() + 1)
Sometimes when designing APIs, I’ve wondered whether every method that does not take an argument (besides self), returns a value (other than None), and is a pure function (i.e., has no side effects) should be replaced by a read-only property. In this chapter, the LineItem.subtotal method (as in Example 22-27) would be a good candidate to become a read-only property. Of course, this excludes methods that are designed to change the object, such as my_list.clear(). It would be a terrible idea to turn that into a property, so that merely accessing my_list.clear would delete the contents of the list!

In the Pingo GPIO library, which I coauthored (mentioned in “The __missing__ Method”), much of the user-level API is based on properties. For example, to read the current value of an analog pin, the user writes pin.value, and setting a digital pin mode is written as pin.mode = OUT. Behind the scenes, reading an analog pin value or setting a digital pin mode may involve a lot of code, depending on the specific board driver. We decided to use properties in Pingo because we want the API to be comfortable to use even in interactive environments like a Jupyter Notebook, and we feel pin.mode = OUT is easier on the eyes and on the fingers than pin.set_mode(OUT).

Although I find the Smalltalk and Ruby solution cleaner, I think the Python approach makes more sense than the Java one. We are allowed to start simple, coding data members as public attributes, because we know they can always be wrapped by properties (or descriptors, which we’ll talk about in the next chapter).

__new__ Is Better than new

Another example of the Uniform Access Principle (or a variation of it) is the fact that function calls and object instantiation use the same syntax in Python: my_obj = foo(), where foo may be a class or any other callable.

Other languages influenced by C++ syntax have a new operator that makes instantiation look different than a call. Most of the time, the user of an API doesn’t care whether foo is a function or a class. For years I was under the impression that property was a function. In normal usage, it makes no difference.

There are many good reasons for replacing constructors with factories.15 A popular motive is limiting the number of instances by returning previously built ones (as in the Singleton pattern). A related use is caching expensive object construction. Also, sometimes it’s convenient to return objects of different types, depending on the arguments given.

Coding a constructor is simpler; providing a factory adds flexibility at the expense of more code. In languages that have a new operator, the designer of an API must decide in advance whether to stick with a simple constructor or invest in a factory. If the initial choice is wrong, the correction may be costly—all because new is an operator.

Sometimes it may also be convenient to go the other way, and replace a simple function with a class.

In Python, classes and functions are interchangeable in many situations. Not only because there’s no new operator, but also because there is the __new__ special method, which can turn a class into a factory producing objects of different kinds (as we saw in “Flexible Object Creation with __new__”) or returning prebuilt instances instead of creating a new one every time.

This function-class duality would be easier to leverage if PEP 8 — Style Guide for Python Code did not recommend CamelCase for class names. On the other hand, dozens of classes in the standard library have lowercase names (e.g., property, str, defaultdict, etc.). So maybe the use of lowercase class names is a feature, and not a bug. But however we look at it, the inconsistent capitalization of classes in the Python standard library poses a usability problem.

Although calling a function is not different from calling a class, it’s good to know which is which because of another thing we can do with a class: subclassing. So I personally use CamelCase in every class that I code, and I wish all classes in the Python standard library used the same convention. I am looking at you, collections.OrderedDict and collections.defaultdict.

1 Alex Martelli, Anna Ravenscroft, and Steve Holden, Python in a Nutshell, 3rd ed. (O’Reilly), p. 123.

2 Bertrand Meyer, Object-Oriented Software Construction, 2nd ed. (Pearson), p. 57.

3 OSCON—O’Reilly Open Source Conference—was a casualty of the COVID-19 pandemic. The original 744 KB JSON file I used for these examples is no longer online as of January 10, 2021. You’ll find a copy of osconfeed.json in the example code repository.

4 Two examples are AttrDict and addict.

5 The expression self.__data[name] is where a KeyError exception may occur. Ideally, it should be handled and an AttributeError raised instead, because that’s what is expected from __getattr__. The diligent reader is invited to code the error handling as an exercise.

6 The source of the data is JSON, and the only collection types in JSON data are dict and list.

7 By the way, Bunch is the name of the class used by Alex Martelli to share this tip in a recipe from 2001 titled “The simple but handy ‘collector of a bunch of named stuff’ class”.

8 This is actually a downside of Meyer’s Uniform Access Principle, which I mentioned in the opening of this chapter. Read the optional “Soapbox” if you’re interested in this discussion.

9 Source: @functools.cached_property documentation. I know Raymond Hettinger authored this explanation because he wrote it as a response to an issue I filed: bpo42781—functools.cached_property docs should explain that it is non-overriding. Hettinger is a major contributor to the official Python docs and standard library. He also wrote the excellent “Descriptor HowTo Guide”, a key resource for Chapter 23.

10 Direct quote by Jeff Bezos in the Wall Street Journal story, “Birth of a Salesman” (October 15, 2011). Note that as of 2021, you need a subscription to read the article.

11 This code is adapted from “Recipe 9.21. Avoiding Repetitive Property Methods” from Python Cookbook, 3rd ed., by David Beazley and Brian K. Jones (O’Reilly).

12 The bloody scene is available on Youtube as I review this in October 2021.

13 Alex Martelli points out that, although __slots__ can be coded as a list, it’s better to be explicit and always use a tuple, because changing the list in the __slots__ after the class body is processed has no effect, so it would be misleading to use a mutable sequence there.

14 Alex Martelli, Python in a Nutshell, 2nd ed. (O’Reilly), p. 101.

15 The reasons I am about to mention are given in the Dr. Dobbs Journal article titled “Java’s new Considered Harmful”, by Jonathan Amsterdam and in “Consider static factory methods instead of constructors,” which is Item 1 of the award-winning book Effective Java, 3rd ed., by Joshua Bloch (Addison-Wesley).


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


22. Dynamic Attributes and Properties
23. Attribute Descriptors
24. Class Metaprogramming
23h 31m remaining
Chapter 23. Attribute Descriptors
Learning about descriptors not only provides access to a larger toolset, it creates a deeper understanding of how Python works and an appreciation for the elegance of its design.

 Raymond Hettinger, Python core developer and guru1

Descriptors are a way of reusing the same access logic in multiple attributes. For example, field types in ORMs, such as the Django ORM and SQLAlchemy, are descriptors, managing the flow of data from the fields in a database record to Python object attributes and vice versa.

A descriptor is a class that implements a dynamic protocol consisting of the __get__, __set__, and __delete__ methods. The property class implements the full descriptor protocol. As usual with dynamic protocols, partial implementations are OK. In fact, most descriptors we see in real code implement only __get__ and __set__, and many implement only one of these methods.

Descriptors are a distinguishing feature of Python, deployed not only at the application level but also in the language infrastructure. User-defined functions are descriptors. We’ll see how the descriptor protocol allows methods to operate as bound or unbound methods, depending on how they are called.

Understanding descriptors is key to Python mastery. This is what this chapter is about.

In this chapter we’ll refactor the bulk food example we first saw in “Using a Property for Attribute Validation”, replacing properties with descriptors. This will make it easier to reuse the attribute validation logic across different classes. We’ll tackle the concepts of overriding and nonoverriding descriptors, and realize that Python functions are descriptors. Finally we’ll see some tips about implementing descriptors.

What’s New in This Chapter
The Quantity descriptor example in “LineItem Take #4: Automatic Naming of Storage Attributes” was dramatically simplified thanks to the __set_name__ special method added to the descriptor protocol in Python 3.6.

I removed the property factory example formerly in “LineItem Take #4: Automatic Naming of Storage Attributes” because it became irrelevant: the point was to show an alternative way of solving the Quantity problem, but with the addition of __set_name__, the descriptor solution becomes much simpler.

The AutoStorage class that used to appear in “LineItem Take #5: A New Descriptor Type” is also gone because __set_name__ made it obsolete.

Descriptor Example: Attribute Validation
As we saw in “Coding a Property Factory”, a property factory is a way to avoid repetitive coding of getters and setters by applying functional programming patterns. A property factory is a higher-order function that creates a parameterized set of accessor functions and builds a custom property instance from them, with closures to hold settings like the storage_name. The object-oriented way of solving the same problem is a descriptor class.

We’ll continue the series of LineItem examples where we left off, in “Coding a Property Factory”, by refactoring the quantity property factory into a Quantity descriptor class. This will make it easier to use.

LineItem Take #3: A Simple Descriptor
As we said in the introduction, a class implementing a __get__, a __set__, or a __delete__ method is a descriptor. You use a descriptor by declaring instances of it as class attributes of another class.

We’ll create a Quantity descriptor, and the LineItem class will use two instances of Quantity: one for managing the weight attribute, the other for price. A diagram helps, so take a look at Figure 23-1.


Figure 23-1. UML class diagram for LineItem using a descriptor class named Quantity. Underlined attributes in UML are class attributes. Note that weight and price are instances of Quantity attached to the LineItem class, but LineItem instances also have their own weight and price attributes where those values are stored.
Note that the word weight appears twice in Figure 23-1, because there are really two distinct attributes named weight: one is a class attribute of LineItem, the other is an instance attribute that will exist in each LineItem object. This also applies to price.

Terms to understand descriptors
Implementing and using descriptors involves several components, and it is useful to be precise when naming those components. I will use the following terms and definitions as I describe the examples in this chapter. They will be easier to understand once you see the code, but I wanted to put the definitions up front so you can refer back to them when needed.

Descriptor class
A class implementing the descriptor protocol. That’s Quantity in Figure 23-1.

Managed class
The class where the descriptor instances are declared as class attributes. In Figure 23-1, LineItem is the managed class.

Descriptor instance
Each instance of a descriptor class, declared as a class attribute of the managed class. In Figure 23-1, each descriptor instance is represented by a composition arrow with an underlined name (the underline means class attribute in UML). The black diamonds touch the LineItem class, which contains the descriptor instances.

Managed instance
One instance of the managed class. In this example, LineItem instances are the managed instances (they are not shown in the class diagram).

Storage attribute
An attribute of the managed instance that holds the value of a managed attribute for that particular instance. In Figure 23-1, the LineItem instance attributes weight and price are the storage attributes. They are distinct from the descriptor instances, which are always class attributes.

Managed attribute
A public attribute in the managed class that is handled by a descriptor instance, with values stored in storage attributes. In other words, a descriptor instance and a storage attribute provide the infrastructure for a managed attribute.

It’s important to realize that Quantity instances are class attributes of LineItem. This crucial point is highlighted by the mills and gizmos in Figure 23-2.


Figure 23-2. UML class diagram annotated with MGN (Mills & Gizmos Notation): classes are mills that produce gizmos—the instances. The Quantity mill produces two gizmos with round heads, which are attached to the LineItem mill: weight and price. The LineItem mill produces rectangular gizmos that have their own weight and price attributes where those values are stored.
INTRODUCING MILLS & GIZMOS NOTATION
After explaining descriptors many times, I realized UML is not very good at showing relationships involving classes and instances, like the relationship between a managed class and the descriptor instances.2 So I invented my own “language,” the Mills & Gizmos Notation (MGN), which I use to annotate UML diagrams.

MGN is designed to make very clear the distinction between classes and instances. See Figure 23-3. In MGN, a class is drawn as a “mill,” a complicated machine that produces gizmos. Classes/mills are always machines with levers and dials. The gizmos are the instances, and they look much simpler. When this book is rendered in color, gizmos have the same color as the mill that made it.


Figure 23-3. MGN sketch showing the LineItem class making three instances, and Quantity making two. One instance of Quantity is retrieving a value stored in a LineItem instance.
For this example, I drew LineItem instances as rows in a tabular invoice, with three cells representing the three attributes (description, weight, and price). Because Quantity instances are descriptors, they have a magnifying glass to __get__ values, and a claw to __set__ values. When we get to metaclasses, you’ll thank me for these doodles.

Enough doodling for now. Here is the code: Example 23-1 shows the Quantity descriptor class, and Example 23-2 lists a new LineItem class using two instances of Quantity.

Example 23-1. bulkfood_v3.py: Quantity descriptor does not accept negative values
class Quantity:  

    def __init__(self, storage_name):
        self.storage_name = storage_name  

    def __set__(self, instance, value):  
        if value > 0:
            instance.__dict__[self.storage_name] = value  
        else:
            msg = f'{self.storage_name} must be > 0'
            raise ValueError(msg)

    def __get__(self, instance, owner):  
        return instance.__dict__[self.storage_name]

Descriptor is a protocol-based feature; no subclassing is needed to implement one.


Each Quantity instance will have a storage_name attribute: that’s the name of the storage attribute to hold the value in the managed instances.


__set__ is called when there is an attempt to assign to the managed attribute. Here, self is the descriptor instance (i.e., LineItem.weight or LineItem.price), instance is the managed instance (a LineItem instance), and value is the value being assigned.


We must store the attribute value directly into __dict__; calling set​attr​(instance, self.storage_name) would trigger the __set__ method again, leading to infinite recursion.


We need to implement __get__ because the name of the managed attribute may not be the same as the storage_name. The owner argument will be explained shortly.

Implementing __get__ is necessary because a user could write something like this:

class House:
    rooms = Quantity('number_of_rooms')
In the House class, the managed attribute is rooms, but the storage attribute is number_of_rooms. Given a House instance named chaos_manor, reading and writing chaos_manor.rooms goes through the Quantity descriptor instance attached to rooms, but reading and writing chaos_manor.number_of_rooms bypasses the descriptor.

Note that __get__ receives three arguments: self, instance, and owner. The owner argument is a reference to the managed class (e.g., LineItem), and it’s useful if you want the descriptor to support retrieving a class attribute—perhaps to emulate Python’s default behavior of retrieving a class attribute when the name is not found in the instance.

If a managed attribute, such as weight, is retrieved via the class like Line​Item.weight, the descriptor __get__ method receives None as the value for the instance argument.

To support introspection and other metaprogramming tricks by the user, it’s a good practice to make __get__ return the descriptor instance when the managed attribute is accessed through the class. To do that, we’d code __get__ like this:

    def __get__(self, instance, owner):
        if instance is None:
            return self
        else:
            return instance.__dict__[self.storage_name]
Example 23-2 demonstrates the use of Quantity in LineItem.

Example 23-2. bulkfood_v3.py: Quantity descriptors manage attributes in LineItem
class LineItem:
    weight = Quantity('weight')  
    price = Quantity('price')  

    def __init__(self, description, weight, price):  
        self.description = description
        self.weight = weight
        self.price = price

    def subtotal(self):
        return self.weight * self.price

The first descriptor instance will manage the weight attribute.


The second descriptor instance will manage the price attribute.


The rest of the class body is as simple and clean as the original code in bulkfood_v1.py (Example 22-19).

The code in Example 23-2 works as intended, preventing the sale of truffles for $0:3

>>> truffle = LineItem('White truffle', 100, 0)
Traceback (most recent call last):
    ...
ValueError: value must be > 0
WARNING
When coding descriptor __get__ and __set__ methods, keep in mind what the self and instance arguments mean: self is the descriptor instance, and instance is the managed instance. Descriptors managing instance attributes should store values in the managed instances. That’s why Python provides the instance argument to the descriptor methods.

It may be tempting, but wrong, to store the value of each managed attribute in the descriptor instance itself. In other words, in the __set__ method, instead of coding:

    instance.__dict__[self.storage_name] = value
the tempting, but bad, alternative would be:

    self.__dict__[self.storage_name] = value
To understand why this would be wrong, think about the meaning of the first two arguments to __set__: self and instance. Here, self is the descriptor instance, which is actually a class attribute of the managed class. You may have thousands of LineItem instances in memory at one time, but you’ll only have two instances of the descriptors: the class attributes LineItem.weight and LineItem.price. So anything you store in the descriptor instances themselves is actually part of a LineItem class attribute, and therefore is shared among all LineItem instances.

A drawback of Example 23-2 is the need to repeat the names of the attributes when the descriptors are instantiated in the managed class body. It would be nice if the LineItem class could be declared like this:

class LineItem:
    weight = Quantity()
    price = Quantity()

    # remaining methods as before
As it stands, Example 23-2 requires naming each Quantity explicitly, which is not only inconvenient but dangerous. If a programmer copying and pasting code forgets to edit both names and writes something like price = Quantity('weight'), the program will misbehave badly, clobbering the value of weight whenever the price is set.

The problem is that—as we saw in Chapter 6—the righthand side of an assignment is executed before the variable exists. The expression Quantity() is evaluated to create a descriptor instance, and there is no way the code in the Quantity class can guess the name of the variable to which the descriptor will be bound (e.g., weight or price).

Thankfully, the descriptor protocol now supports the aptly named __set_name__ special method. We’ll see how to use it next.

NOTE
Automatic naming of a descriptor storage attribute used to be a thorny issue. In the first edition of Fluent Python, I devoted several pages and lines of code in this chapter and the next to presenting different solutions, including the use of a class decorator, and then metaclasses in Chapter 24. This was greatly simplified in Python 3.6.

LineItem Take #4: Automatic Naming of Storage Attributes
To avoid retyping the attribute name in the descriptor instances, we’ll implement __set_name__ to set the storage_name of each Quantity instance. The __set_name__ special method was added to the descriptor protocol in Python 3.6. The interpreter calls __set_name__ on each descriptor it finds in a class body—if the descriptor implements it.4

In Example 23-3, the LineItem descriptor class doesn’t need an __init__. Instead, __set_item__ saves the name of the storage attribute.

Example 23-3. bulkfood_v4.py: __set_name__ sets the name for each Quantity descriptor instance
class Quantity:

    def __set_name__(self, owner, name):  
        self.storage_name = name          

    def __set__(self, instance, value):   
        if value > 0:
            instance.__dict__[self.storage_name] = value
        else:
            msg = f'{self.storage_name} must be > 0'
            raise ValueError(msg)

    # no __get__ needed  

class LineItem:
    weight = Quantity()  
    price = Quantity()

    def __init__(self, description, weight, price):
        self.description = description
        self.weight = weight
        self.price = price

    def subtotal(self):
        return self.weight * self.price

self is the descriptor instance (not the managed instance), owner is the managed class, and name is the name of the attribute of owner to which this descriptor instance was assigned in the class body of owner.


This is what the __init__ did in Example 23-1.


The __set__ method here is exactly the same as in Example 23-1.


Implementing __get__ is not necessary because the name of the storage attribute matches the name of the managed attribute. The expression product.price gets the price attribute directly from the LineItem instance.


Now we don’t need to pass the managed attribute name to the Quantity constructor. That was the goal for this version.

Looking at Example 23-3, you may think that’s a lot of code just for managing a couple of attributes, but it’s important to realize that the descriptor logic is now abstracted into a separate code unit: the Quantity class. Usually we do not define a descriptor in the same module where it’s used, but in a separate utility module designed to be used across the application—even in many applications, if you are developing a library or framework.

With this in mind, Example 23-4 better represents the typical usage of a descriptor.

Example 23-4. bulkfood_v4c.py: LineItem definition uncluttered; the Quantity descriptor class now resides in the imported model_v4c module
import model_v4c as model  


class LineItem:
    weight = model.Quantity()  
    price = model.Quantity()

    def __init__(self, description, weight, price):
        self.description = description
        self.weight = weight
        self.price = price

    def subtotal(self):
        return self.weight * self.price

Import the model_v4c module where Quantity is implemented.


Put model.Quantity to use.

Django users will notice that Example 23-4 looks a lot like a model definition. It’s no coincidence: Django model fields are descriptors.

Because descriptors are implemented as classes, we can leverage inheritance to reuse some of the code we have for new descriptors. That’s what we’ll do in the following section.

LineItem Take #5: A New Descriptor Type
The imaginary organic food store hits a snag: somehow a line item instance was created with a blank description, and the order could not be fulfilled. To prevent that, we’ll create a new descriptor, NonBlank. As we design NonBlank, we realize it will be very much like the Quantity descriptor, except for the validation logic.

This prompts a refactoring, producing Validated, an abstract class that overrides the __set__ method, calling a validate method that must be implemented by subclasses.

We’ll then rewrite Quantity, and implement NonBlank by inheriting from Validated and just coding the validate methods.

The relationship among Validated, Quantity, and NonBlank is an application of the template method as described in the Design Patterns classic:

A template method defines an algorithm in terms of abstract operations that subclasses override to provide concrete behavior.5

In Example 23-5, Validated.__set__ is the template method and self.validate is the abstract operation.

Example 23-5. model_v5.py: the Validated ABC
import abc

class Validated(abc.ABC):

    def __set_name__(self, owner, name):
        self.storage_name = name

    def __set__(self, instance, value):
        value = self.validate(self.storage_name, value)  
        instance.__dict__[self.storage_name] = value  

    @abc.abstractmethod
    def validate(self, name, value):  
        """return validated value or raise ValueError"""

__set__ delegates validation to the validate method…


…then uses the returned value to update the stored value.


validate is an abstract method; this is the template method.

Alex Martelli prefers to call this design pattern Self-Delegation, and I agree it’s a more descriptive name: the first line of __set__ self-delegates to validate.6

The concrete Validated subclasses in this example are Quantity and NonBlank, shown in Example 23-6.

Example 23-6. model_v5.py: Quantity and NonBlank, concrete Validated subclasses
class Quantity(Validated):
    """a number greater than zero"""

    def validate(self, name, value):  
        if value <= 0:
            raise ValueError(f'{name} must be > 0')
        return value


class NonBlank(Validated):
    """a string with at least one non-space character"""

    def validate(self, name, value):
        value = value.strip()
        if not value:  
            raise ValueError(f'{name} cannot be blank')
        return value  

Implementation of the template method required by the Validated.validate abstract method.


If nothing is left after leading and trailing blanks are stripped, reject the value.


Requiring the concrete validate methods to return the validated value gives them an opportunity to clean up, convert, or normalize the data received. In this case, value is returned without leading or trailing blanks.

Users of model_v5.py don’t need to know all these details. What matters is that they get to use Quantity and NonBlank to automate the validation of instance attributes. See the latest LineItem class in Example 23-7.

Example 23-7. bulkfood_v5.py: LineItem using Quantity and NonBlank descriptors
import model_v5 as model  

class LineItem:
    description = model.NonBlank()  
    weight = model.Quantity()
    price = model.Quantity()

    def __init__(self, description, weight, price):
        self.description = description
        self.weight = weight
        self.price = price

    def subtotal(self):
        return self.weight * self.price

Import the model_v5 module, giving it a friendlier name.


Put model.NonBlank to use. The rest of the code is unchanged.

The LineItem examples we’ve seen in this chapter demonstrate a typical use of descriptors to manage data attributes. Descriptors like Quantity are called overriding descriptors because its __set__ method overrides (i.e., intercepts and overrules) the setting of an instance attribute by the same name in the managed instance. However, there are also nonoverriding descriptors. We’ll explore this distinction in detail in the next section.

Overriding Versus Nonoverriding Descriptors
Recall that there is an important asymmetry in the way Python handles attributes. Reading an attribute through an instance normally returns the attribute defined in the instance, but if there is no such attribute in the instance, a class attribute will be retrieved. On the other hand, assigning to an attribute in an instance normally creates the attribute in the instance, without affecting the class at all.

This asymmetry also affects descriptors, in effect creating two broad categories of descriptors, depending on whether the __set__ method is implemented. If __set__ is present, the class is an overriding descriptor; otherwise, it is a nonoverriding descriptor. These terms will make sense as we study descriptor behaviors in the next examples.

Observing the different descriptor categories requires a few classes, so we’ll use the code in Example 23-8 as our test bed for the following sections.

TIP
Every __get__ and __set__ method in Example 23-8 calls print_args so their invocations are displayed in a readable way. Understanding print_args and the auxiliary functions cls_name and display is not important, so don’t get distracted by them.

Example 23-8. descriptorkinds.py: simple classes for studying descriptor overriding behaviors
### auxiliary functions for display only ###

def cls_name(obj_or_cls):
    cls = type(obj_or_cls)
    if cls is type:
        cls = obj_or_cls
    return cls.__name__.split('.')[-1]

def display(obj):
    cls = type(obj)
    if cls is type:
        return f'<class {obj.__name__}>'
    elif cls in [type(None), int]:
        return repr(obj)
    else:
        return f'<{cls_name(obj)} object>'

def print_args(name, *args):
    pseudo_args = ', '.join(display(x) for x in args)
    print(f'-> {cls_name(args[0])}.__{name}__({pseudo_args})')


### essential classes for this example ###

class Overriding:  
    """a.k.a. data descriptor or enforced descriptor"""

    def __get__(self, instance, owner):
        print_args('get', self, instance, owner)  

    def __set__(self, instance, value):
        print_args('set', self, instance, value)


class OverridingNoGet:  
    """an overriding descriptor without ``__get__``"""

    def __set__(self, instance, value):
        print_args('set', self, instance, value)


class NonOverriding:  
    """a.k.a. non-data or shadowable descriptor"""

    def __get__(self, instance, owner):
        print_args('get', self, instance, owner)


class Managed:  
    over = Overriding()
    over_no_get = OverridingNoGet()
    non_over = NonOverriding()

    def spam(self):  
        print(f'-> Managed.spam({display(self)})')

An overriding descriptor class with __get__ and __set__.


The print_args function is called by every descriptor method in this example.


An overriding descriptor without a __get__ method.


No __set__ method here, so this is a nonoverriding descriptor.


The managed class, using one instance of each of the descriptor classes.


The spam method is here for comparison, because methods are also descriptors.

In the following sections, we will examine the behavior of attribute reads and writes on the Managed class, and one instance of it, going through each of the different descriptors defined.

Overriding Descriptors
A descriptor that implements the __set__ method is an overriding descriptor, because although it is a class attribute, a descriptor implementing __set__ will override attempts to assign to instance attributes. This is how Example 23-3 was implemented. Properties are also overriding descriptors: if you don’t provide a setter function, the default __set__ from the property class will raise AttributeError to signal that the attribute is read-only. Given the code in Example 23-8, experiments with an overriding descriptor can be seen in Example 23-9.

WARNING
Python contributors and authors use different terms when discussing these concepts. I adopted “overriding descriptor” from the book Python in a Nutshell. The official Python documentation uses “data descriptor,” but “overriding descriptor” highlights the special behavior. Overriding descriptors are also called “enforced descriptors.” Synonyms for nonoverriding descriptors include “nondata descriptors” or “shadowable descriptors.”

Example 23-9. Behavior of an overriding descriptor
>>> obj = Managed()  
>>> obj.over  
-> Overriding.__get__(<Overriding object>, <Managed object>, <class Managed>)
>>> Managed.over  
-> Overriding.__get__(<Overriding object>, None, <class Managed>)
>>> obj.over = 7  
-> Overriding.__set__(<Overriding object>, <Managed object>, 7)
>>> obj.over  
-> Overriding.__get__(<Overriding object>, <Managed object>, <class Managed>)
>>> obj.__dict__['over'] = 8  
>>> vars(obj)  
{'over': 8}
>>> obj.over  
-> Overriding.__get__(<Overriding object>, <Managed object>, <class Managed>)

Create Managed object for testing.


obj.over triggers the descriptor __get__ method, passing the managed instance obj as the second argument.


Managed.over triggers the descriptor __get__ method, passing None as the second argument (instance).


Assigning to obj.over triggers the descriptor __set__ method, passing the value 7 as the last argument.


Reading obj.over still invokes the descriptor __get__ method.


Bypassing the descriptor, setting a value directly to the obj.__dict__.


Verify that the value is in the obj.__dict__, under the over key.


However, even with an instance attribute named over, the Managed.over descriptor still overrides attempts to read obj.over.

Overriding Descriptor Without __get__
Properties and other overriding descriptors, such as Django model fields, implement both __set__ and __get__, but it’s also possible to implement only __set__, as we saw in Example 23-2. In this case, only writing is handled by the descriptor. Reading the descriptor through an instance will return the descriptor object itself because there is no __get__ to handle that access. If a namesake instance attribute is created with a new value via direct access to the instance __dict__, the __set__ method will still override further attempts to set that attribute, but reading that attribute will simply return the new value from the instance, instead of returning the descriptor object. In other words, the instance attribute will shadow the descriptor, but only when reading. See Example 23-10.

Example 23-10. Overriding descriptor without __get__
>>> obj.over_no_get  
<__main__.OverridingNoGet object at 0x665bcc>
>>> Managed.over_no_get  
<__main__.OverridingNoGet object at 0x665bcc>
>>> obj.over_no_get = 7  
-> OverridingNoGet.__set__(<OverridingNoGet object>, <Managed object>, 7)
>>> obj.over_no_get  
<__main__.OverridingNoGet object at 0x665bcc>
>>> obj.__dict__['over_no_get'] = 9  
>>> obj.over_no_get  
9
>>> obj.over_no_get = 7  
-> OverridingNoGet.__set__(<OverridingNoGet object>, <Managed object>, 7)
>>> obj.over_no_get  
9

This overriding descriptor doesn’t have a __get__ method, so reading obj.over_no_get retrieves the descriptor instance from the class.


The same thing happens if we retrieve the descriptor instance directly from the managed class.


Trying to set a value to obj.over_no_get invokes the __set__ descriptor method.


Because our __set__ doesn’t make changes, reading obj.over_no_get again retrieves the descriptor instance from the managed class.


Going through the instance __dict__ to set an instance attribute named over_no_get.


Now that over_no_get instance attribute shadows the descriptor, but only for reading.


Trying to assign a value to obj.over_no_get still goes through the descriptor set.


But for reading, that descriptor is shadowed as long as there is a namesake instance attribute.

Nonoverriding Descriptor
A descriptor that does not implement __set__ is a nonoverriding descriptor. Setting an instance attribute with the same name will shadow the descriptor, rendering it ineffective for handling that attribute in that specific instance. Methods and @functools.cached_property are implemented as nonoverriding descriptors. Example 23-11 shows the operation of a nonoverriding descriptor.

Example 23-11. Behavior of a nonoverriding descriptor
>>> obj = Managed()
>>> obj.non_over  
-> NonOverriding.__get__(<NonOverriding object>, <Managed object>, <class Managed>)
>>> obj.non_over = 7  
>>> obj.non_over  
7
>>> Managed.non_over  
-> NonOverriding.__get__(<NonOverriding object>, None, <class Managed>)
>>> del obj.non_over  
>>> obj.non_over  
-> NonOverriding.__get__(<NonOverriding object>, <Managed object>, <class Managed>)

obj.non_over triggers the descriptor __get__ method, passing obj as the second argument.


Managed.non_over is a nonoverriding descriptor, so there is no __set__ to interfere with this assignment.


The obj now has an instance attribute named non_over, which shadows the namesake descriptor attribute in the Managed class.


The Managed.non_over descriptor is still there, and catches this access via the class.


If the non_over instance attribute is deleted…


…then reading obj.non_over hits the __get__ method of the descriptor in the class, but note that the second argument is the managed instance.

In the previous examples, we saw several assignments to an instance attribute with the same name as a descriptor, and different results according to the presence of a __set__ method in the descriptor.

The setting of attributes in the class cannot be controlled by descriptors attached to the same class. In particular, this means that the descriptor attributes themselves can be clobbered by assigning to the class, as the next section explains.

Overwriting a Descriptor in the Class
Regardless of whether a descriptor is overriding or not, it can be overwritten by assignment to the class. This is a monkey-patching technique, but in Example 23-12 the descriptors are replaced by integers, which would effectively break any class that depended on the descriptors for proper operation.

Example 23-12. Any descriptor can be overwritten on the class itself
>>> obj = Managed()  
>>> Managed.over = 1  
>>> Managed.over_no_get = 2
>>> Managed.non_over = 3
>>> obj.over, obj.over_no_get, obj.non_over  
(1, 2, 3)

Create a new instance for later testing.


Overwrite the descriptor attributes in the class.


The descriptors are really gone.

Example 23-12 reveals another asymmetry regarding reading and writing attributes: although the reading of a class attribute can be controlled by a descriptor with __get__ attached to the managed class, the writing of a class attribute cannot be handled by a descriptor with __set__ attached to the same class.

TIP
In order to control the setting of attributes in a class, you have to attach descriptors to the class of the class—in other words, the metaclass. By default, the metaclass of user-defined classes is type, and you cannot add attributes to type. But in Chapter 24, we’ll create our own metaclasses.

Let’s now focus on how descriptors are used to implement methods in Python.

Methods Are Descriptors
A function within a class becomes a bound method when invoked on an instance because all user-defined functions have a __get__ method, therefore they operate as descriptors when attached to a class. Example 23-13 demonstrates reading the spam method from the Managed class introduced in Example 23-8.

Example 23-13. A method is a nonoverriding descriptor
>>> obj = Managed()
>>> obj.spam  
<bound method Managed.spam of <descriptorkinds.Managed object at 0x74c80c>>
>>> Managed.spam  
<function Managed.spam at 0x734734>
>>> obj.spam = 7  
>>> obj.spam
7

Reading from obj.spam retrieves a bound method object.


But reading from Managed.spam retrieves a function.


Assigning a value to obj.spam shadows the class attribute, rendering the spam method inaccessible from the obj instance.

Functions do not implement __set__, therefore they are nonoverriding descriptors, as the last line of Example 23-13 shows.

The other key takeaway from Example 23-13 is that obj.spam and Managed.spam retrieve different objects. As usual with descriptors, the __get__ of a function returns a reference to itself when the access happens through the managed class. But when the access goes through an instance, the __get__ of the function returns a bound method object: a callable that wraps the function and binds the managed instance (e.g., obj) to the first argument of the function (i.e., self), like the functools.partial function does (as seen in “Freezing Arguments with functools.partial”). For a deeper understanding of this mechanism, take a look at Example 23-14.

Example 23-14. method_is_descriptor.py: a Text class, derived from UserString
import collections


class Text(collections.UserString):

    def __repr__(self):
        return 'Text({!r})'.format(self.data)

    def reverse(self):
        return self[::-1]
Now let’s investigate the Text.reverse method. See Example 23-15.

Example 23-15. Experiments with a method
    >>> word = Text('forward')
    >>> word  
    Text('forward')
    >>> word.reverse()  
    Text('drawrof')
    >>> Text.reverse(Text('backward'))  
    Text('drawkcab')
    >>> type(Text.reverse), type(word.reverse)  
    (<class 'function'>, <class 'method'>)
    >>> list(map(Text.reverse, ['repaid', (10, 20, 30), Text('stressed')]))  
    ['diaper', (30, 20, 10), Text('desserts')]
    >>> Text.reverse.__get__(word)  
    <bound method Text.reverse of Text('forward')>
    >>> Text.reverse.__get__(None, Text)  
    <function Text.reverse at 0x101244e18>
    >>> word.reverse  
    <bound method Text.reverse of Text('forward')>
    >>> word.reverse.__self__  
    Text('forward')
    >>> word.reverse.__func__ is Text.reverse  
    True

The repr of a Text instance looks like a Text constructor call that would make an equal instance.


The reverse method returns the text spelled backward.


A method called on the class works as a function.


Note the different types: a function and a method.


Text.reverse operates as a function, even working with objects that are not instances of Text.


Any function is a nonoverriding descriptor. Calling its __get__ with an instance retrieves a method bound to that instance.


Calling the function’s __get__ with None as the instance argument retrieves the function itself.


The expression word.reverse actually invokes Text.reverse.__get__(word), returning the bound method.


The bound method object has a __self__ attribute holding a reference to the instance on which the method was called.


The __func__ attribute of the bound method is a reference to the original function attached to the managed class.

The bound method object also has a __call__ method, which handles the actual invocation. This method calls the original function referenced in __func__, passing the __self__ attribute of the method as the first argument. That’s how the implicit binding of the conventional self argument works.

The way functions are turned into bound methods is a prime example of how descriptors are used as infrastructure in the language.

After this deep dive into how descriptors and methods work, let’s go through some practical advice about their use.

Descriptor Usage Tips
The following list addresses some practical consequences of the descriptor characteristics just described:

Use property to keep it simple
The property built-in creates overriding descriptors implementing __set__ and __get__ even if you do not define a setter method.7 The default __set__ of a property raises AttributeError: can't set attribute, so a property is the easiest way to create a read-only attribute, avoiding the issue described next.

Read-only descriptors require __set__
If you use a descriptor class to implement a read-only attribute, you must remember to code both __get__ and __set__, otherwise setting a namesake attribute on an instance will shadow the descriptor. The __set__ method of a read-only attribute should just raise AttributeError with a suitable message.8

Validation descriptors can work with __set__ only
In a descriptor designed only for validation, the __set__ method should check the value argument it gets, and if valid, set it directly in the instance __dict__ using the descriptor instance name as key. That way, reading the attribute with the same name from the instance will be as fast as possible, because it will not require a __get__. See the code for Example 23-3.

Caching can be done efficiently with __get__ only
If you code just the __get__ method, you have a nonoverriding descriptor. These are useful to make some expensive computation and then cache the result by setting an attribute by the same name on the instance.9 The namesake instance attribute will shadow the descriptor, so subsequent access to that attribute will fetch it directly from the instance __dict__ and not trigger the descriptor __get__ anymore. The @functools.cached_property decorator actually produces a nonoverriding descriptor.

Nonspecial methods can be shadowed by instance attributes
Because functions and methods only implement __get__, they are nonoverriding descriptors. A simple assignment like my_obj.the_method = 7 means that further access to the_method through that instance will retrieve the number 7—without affecting the class or other instances. However, this issue does not interfere with special methods. The interpreter only looks for special methods in the class itself, in other words, repr(x) is executed as x.__class__.__repr__(x), so a __repr__ attribute defined in x has no effect on repr(x). For the same reason, the existence of an attribute named __getattr__ in an instance will not subvert the usual attribute access algorithm.

The fact that nonspecial methods can be overridden so easily in instances may sound fragile and error prone, but I personally have never been bitten by this in more than 20 years of Python coding. On the other hand, if you are doing a lot of dynamic attribute creation, where the attribute names come from data you don’t control (as we did in the earlier parts of this chapter), then you should be aware of this and perhaps implement some filtering or escaping of the dynamic attribute names to preserve your sanity.

NOTE
The FrozenJSON class in Example 22-5 is safe from instance attribute shadowing methods because its only methods are special methods and the build class method. Class methods are safe as long as they are always accessed through the class, as I did with FrozenJSON.build in Example 22-5—later replaced by __new__ in Example 22-6. The Record and Event classes presented in “Computed Properties” are also safe: they implement only special methods, static methods, and properties. Properties are overriding descriptors, so they are not shadowed by instance attributes.

To close this chapter, we’ll cover two features we saw with properties that we have not addressed in the context of descriptors: documentation and handling attempts to delete a managed attribute.

Descriptor Docstring and Overriding Deletion
The docstring of a descriptor class is used to document every instance of the descriptor in the managed class. Figure 23-4 shows the help displays for the LineItem class with the Quantity and NonBlank descriptors from Examples 23-6 and 23-7.

That is somewhat unsatisfactory. In the case of LineItem, it would be good to add, for example, the information that weight must be in kilograms. That would be trivial with properties, because each property handles a specific managed attribute. But with descriptors, the same Quantity descriptor class is used for weight and price.10

The second detail we discussed with properties, but have not addressed with descriptors, is handling attempts to delete a managed attribute. That can be done by implementing a __delete__ method alongside or instead of the usual __get__ and/or __set__ in the descriptor class. I deliberately omitted coverage of __delete__ because I believe real-world usage is rare. If you need this, please see the “Implementing Descriptors” section of the Python Data Model documentation. Coding a silly descriptor class with __delete__ is left as an exercise to the leisurely reader.


Figure 23-4. Screenshots of the Python console when issuing the commands help(LineItem.weight) and help(LineItem).
Chapter Summary
The first example of this chapter was a continuation of the LineItem examples from Chapter 22. In Example 23-2, we replaced properties with descriptors. We saw that a descriptor is a class that provides instances that are deployed as attributes in the managed class. Discussing this mechanism required special terminology, introducing terms such as managed instance and storage attribute.

In “LineItem Take #4: Automatic Naming of Storage Attributes”, we removed the requirement that Quantity descriptors were declared with an explicit storage_name, which was redundant and error prone. The solution was to implement the __set_name__ special method in Quantity, to save the name of the managed property as self.storage_name.

“LineItem Take #5: A New Descriptor Type” showed how to subclass an abstract descriptor class to share code while building specialized descriptors with some common functionality.

We then looked at the different behaviors of descriptors providing or omitting the __set__ method, making the crucial distinction between overriding and nonoverriding descriptors, a.k.a. data and nondata descriptors. Through detailed testing we uncovered when descriptors are in control and when they are shadowed, bypassed, or overwritten.

Following that, we studied a particular category of nonoverriding descriptors: methods. Console experiments revealed how a function attached to a class becomes a method when accessed through an instance, by leveraging the descriptor protocol.

To conclude the chapter, “Descriptor Usage Tips” presented practical tips, and “Descriptor Docstring and Overriding Deletion” provided a brief look at how to document descriptors.

NOTE
As noted in “What’s New in This Chapter”, several examples in this chapter became much simpler thanks to the __set_name__ special method of the descriptor protocol, added in Python 3.6. That’s language evolution!

Further Reading
Besides the obligatory reference to the “Data Model” chapter, Raymond Hettinger’s “Descriptor HowTo Guide” is a valuable resource—part of the HowTo collection in the official Python documentation.

As usual with Python object model subjects, Martelli, Ravenscroft, and Holden’s Python in a Nutshell, 3rd ed. (O’Reilly) is authoritative and objective. Martelli also has a presentation titled “Python’s Object Model,” which covers properties and descriptors in depth (see the slides and video).

WARNING
Beware that any coverage of descriptors written or recorded before PEP 487 was adopted in 2016 is likely to contain examples that are needlessly complicated today, because __set_name__ was not supported in Python versions prior to 3.6.

For more practical examples, Python Cookbook, 3rd ed., by David Beazley and Brian K. Jones (O’Reilly), has many recipes illustrating descriptors, of which I want to highlight “6.12. Reading Nested and Variable-Sized Binary Structures,” “8.10. Using Lazily Computed Properties,” “8.13. Implementing a Data Model or Type System,” and “9.9. Defining Decorators As Classes.” The last recipe of which addresses deep issues with the interaction of function decorators, descriptors, and methods, explaining how a function decorator implemented as a class with __call__ also needs to implement __get__ if it wants to work with decorating methods as well as functions.

PEP 487—Simpler customization of class creation introduced the __set_name__ special method, and includes an example of a validating descriptor.

SOAPBOX
The Design of self

The requirement to explicitly declare self as a first argument in methods is a controversial design decision in Python. After 23 years using the language, I am used to it. I think that decision is an example of “worse is better”: a design philosophy described by computer scientist Richard P. Gabriel in “The Rise of Worse is Better”. The first priority of this philosophy is “simplicity,” which Gabriel presents as:

The design must be simple, both in implementation and interface. It is more important for the implementation to be simple than the interface. Simplicity is the most important consideration in a design.

Python’s explicit self embodies that design philosophy. The implementation is simple—elegant even—at the expense of the user interface: a method signature like def zfill(self, width): doesn’t visually match the invocation label.zfill(8).

Modula-3 introduced that convention with the same identifier self. But there is a key difference: in Modula-3, interfaces are declared separately from their implementation, and in the interface declaration the self argument is omitted, so from the user’s perspective, a method appears in an interface declaration with the same explicit parameters used to call it.

Over time, Python’s error messages related to method arguments became clearer. For a user-defined method with one argument besides self, if the user invokes obj.meth(), Python 2.7 raised:

TypeError: meth() takes exactly 2 arguments (1 given)
In Python 3, the confusing argument count is not mentioned, and the missing argument is named:

TypeError: meth() missing 1 required positional argument: 'x'
Besides the use of self as an explicit argument, the requirement to qualify every access to instance attributes with self is also criticized. See, for example, A. M. Kuchling’s famous “Python Warts” post (archived); Kuchling himself is not so bothered by the self qualifier, but he mentions it—probably echoing opinions from the comp.lang.python group. I personally don’t mind typing the self qualifier: it’s good to distinguish local variables from attributes. My issue is with the use of self in the def statement.

Anyone who is unhappy about the explicit self in Python can feel a lot better by considering the baffling semantics of the implicit this in JavaScript. Guido had some good reasons to make self work as it does, and he wrote about them in “Adding Support for User-Defined Classes”, a post on his blog, The History of Python.

1 Raymond Hettinger, Descriptor HowTo Guide.

2 Classes and instances are drawn as rectangles in UML class diagrams. There are visual differences, but instances are rarely shown in class diagrams, so developers may not recognize them as such.

3 White truffles cost thousands of dollars per pound. Disallowing the sale of truffles for $0.01 is left as an exercise for the enterprising reader. I know a person who actually bought an $1,800 encyclopedia of statistics for $18 because of an error in an online store (not Amazon.com in this case).

4 More precisely, __set_name__ is called by type.__new__—the constructor of objects representing classes. The type built-in is actually a metaclass, the default class of user-defined classes. This is hard to grasp at first, but rest assured: Chapter 24 is devoted to the dynamic configuration of classes, including the concept of metaclasses.

5 Gamma et al., Design Patterns: Elements of Reusable Object-Oriented Software, p. 326.

6 Slide #50 of Alex Martelli’s “Python Design Patterns” talk. Highly recommended.

7 A __delete__ method is also provided by the property decorator, even if no deleter method is defined by you.

8 Python is not consistent in such messages. Trying to change the c.real attribute of a complex number gets AttributeError: readonly attribute, but an attempt to change c.conjugate (a method of complex), results in AttributeError: 'complex' object attribute 'conjugate' is read-only. Even the spelling of “read-only” is different.

9 However, recall that creating instance attributes after the __init__ method runs defeats the key-sharing memory optimization, as discussed in from “Practical Consequences of How dict Works”.

10 Customizing the help text for each descriptor instance is surprisingly hard. One solution requires dynamically building a wrapper class for each descriptor instance.


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


23. Attribute Descriptors
24. Class Metaprogramming
Afterword
23h 31m remaining
Chapter 24. Class Metaprogramming
Everyone knows that debugging is twice as hard as writing a program in the first place. So if you’re as clever as you can be when you write it, how will you ever debug it?

Brian W. Kernighan and P. J. Plauger, The Elements of Programming Style1

Class metaprogramming is the art of creating or customizing classes at runtime. Classes are first-class objects in Python, so a function can be used to create a new class at any time, without using the class keyword. Class decorators are also functions, but designed to inspect, change, and even replace the decorated class with another class. Finally, metaclasses are the most advanced tool for class metaprogramming: they let you create whole new categories of classes with special traits, such as the abstract base classes we’ve already seen.

Metaclasses are powerful, but hard to justify and even harder to get right. Class decorators solve many of the same problems and are easier to understand. Furthermore, Python 3.6 implemented PEP 487—Simpler customization of class creation, providing special methods supporting tasks that previously required metaclasses or class decorators.2

This chapter presents the class metaprogramming techniques in ascending order of complexity.

WARNING
This is an exciting topic, and it’s easy to get carried away. So I must offer this advice.

For the sake of readability and maintainability, you should probably avoid the techniques described in this chapter in application code.

On the other hand, these are the tools of the trade if you want to write the next great Python framework.

What’s New in This Chapter
All the code in the “Class Metaprogramming” chapter of the first edition of Fluent Python still runs correctly. However, some of the previous examples no longer represent the simplest solutions in light of new features added since Python 3.6.

I replaced those examples with different ones, highlighting Python’s new metaprogramming features or adding further requirements to justify the use of the more advanced techniques. Some of the new examples leverage type hints to provide class builders similar to the @dataclass decorator and typing.NamedTuple.

“Metaclasses in the Real World” is a new section with some high-level considerations about the applicability of metaclasses.

TIP
Some of the best refactorings are removing code made redundant by newer and simpler ways of solving the same problems. This applies to production code as well as books.

We’ll get started by reviewing attributes and methods defined in the Python Data Model for all classes.

Classes as Objects
Like most program entities in Python, classes are also objects. Every class has a number of attributes defined in the Python Data Model, documented in “4.13. Special Attributes” of the “Built-in Types” chapter in The Python Standard Library. Three of those attributes appeared several times in this book already: __class__, __name__, and __mro__. Other class standard attributes are:

cls.__bases__
The tuple of base classes of the class.

cls.__qualname__
The qualified name of a class or function, which is a dotted path from the global scope of the module to the class definition. This is relevant when the class is defined inside another class. For example, in a Django model class such as Ox, there is an inner class called Meta. The __qualname__ of Meta is Ox.Meta, but its __name__ is just Meta. The specification for this attribute is PEP 3155—Qualified name for classes and functions.

cls.__subclasses__()
This method returns a list of the immediate subclasses of the class. The implementation uses weak references to avoid circular references between the superclass and its subclasses—which hold a strong reference to the superclasses in their __bases__ attribute. The method lists subclasses currently in memory. Subclasses in modules not yet imported will not appear in the result.

cls.mro()
The interpreter calls this method when building a class to obtain the tuple of superclasses stored in the __mro__ attribute of the class. A metaclass can override this method to customize the method resolution order of the class under construction.

TIP
None of the attributes mentioned in this section are listed by the dir(…) function.

Now, if a class is an object, what is the class of a class?

type: The Built-In Class Factory
We usually think of type as a function that returns the class of an object, because that’s what type(my_object) does: it returns my_object.__class__.

However, type is a class that creates a new class when invoked with three arguments.

Consider this simple class:

class MyClass(MySuperClass, MyMixin):
    x = 42

    def x2(self):
        return self.x * 2
Using the type constructor, you can create MyClass at runtime with this code:

MyClass = type('MyClass',
               (MySuperClass, MyMixin),
               {'x': 42, 'x2': lambda self: self.x * 2},
          )
That type call is functionally equivalent to the previous class MyClass… block statement.

When Python reads a class statement, it calls type to build the class object with these parameters:

name
The identifier that appears after the class keyword, e.g., MyClass.

bases
The tuple of superclasses given in parentheses after the class identifier, or (object,) if superclasses are not mentioned in the class statement.

dict
A mapping of attribute names to values. Callables become methods, as we saw in “Methods Are Descriptors”. Other values become class attributes.

NOTE
The type constructor accepts optional keyword arguments, which are ignored by type itself, but are passed untouched into __init_subclass__, which must consume them. We’ll study that special method in “Introducing __init_subclass__”, but I won’t cover the use of keyword arguments. For more, please read PEP 487—Simpler customization of class creation.

The type class is a metaclass: a class that builds classes. In other words, instances of the type class are classes. The standard library provides a few other metaclasses, but type is the default:

>>> type(7)
<class 'int'>
>>> type(int)
<class 'type'>
>>> type(OSError)
<class 'type'>
>>> class Whatever:
...     pass
...
>>> type(Whatever)
<class 'type'>
We’ll build custom metaclasses in “Metaclasses 101”.

Next, we’ll use the type built-in to make a function that builds classes.

A Class Factory Function
The standard library has a class factory function that appears several times in this book: collections.namedtuple. In Chapter 5 we also saw typing.NamedTuple and @dataclass. All of these class builders leverage techniques covered in this chapter.

We’ll start with a super simple factory for classes of mutable objects—the simplest possible replacement for @dataclass.

Suppose I’m writing a pet shop application and I want to store data for dogs as simple records. But I don’t want to write boilerplate like this:

class Dog:
    def __init__(self, name, weight, owner):
        self.name = name
        self.weight = weight
        self.owner = owner
Boring…each field name appears three times, and that boilerplate doesn’t even buy us a nice repr:

>>> rex = Dog('Rex', 30, 'Bob')
>>> rex
<__main__.Dog object at 0x2865bac>
Taking a hint from collections.namedtuple, let’s create a record_factory that creates simple classes like Dog on the fly. Example 24-1 shows how it should work.

Example 24-1. Testing record_factory, a simple class factory
    >>> Dog = record_factory('Dog', 'name weight owner')  
    >>> rex = Dog('Rex', 30, 'Bob')
    >>> rex  
    Dog(name='Rex', weight=30, owner='Bob')
    >>> name, weight, _ = rex  
    >>> name, weight
    ('Rex', 30)
    >>> "{2}'s dog weighs {1}kg".format(*rex)  
    "Bob's dog weighs 30kg"
    >>> rex.weight = 32  
    >>> rex
    Dog(name='Rex', weight=32, owner='Bob')
    >>> Dog.__mro__  
    (<class 'factories.Dog'>, <class 'object'>)

Factory can be called like namedtuple: class name, followed by attribute names separated by spaces in a single string.


Nice repr.


Instances are iterable, so they can be conveniently unpacked on assignment…


…or when passing to functions like format.


A record instance is mutable.


The newly created class inherits from object—no relationship to our factory.

The code for record_factory is in Example 24-2.3

Example 24-2. record_factory.py: a simple class factory
from typing import Union, Any
from collections.abc import Iterable, Iterator

FieldNames = Union[str, Iterable[str]]  

def record_factory(cls_name: str, field_names: FieldNames) -> type[tuple]:  

    slots = parse_identifiers(field_names)  

    def __init__(self, *args, **kwargs) -> None:  
        attrs = dict(zip(self.__slots__, args))
        attrs.update(kwargs)
        for name, value in attrs.items():
            setattr(self, name, value)

    def __iter__(self) -> Iterator[Any]:  
        for name in self.__slots__:
            yield getattr(self, name)

    def __repr__(self):  
        values = ', '.join(f'{name}={value!r}'
            for name, value in zip(self.__slots__, self))
        cls_name = self.__class__.__name__
        return f'{cls_name}({values})'

    cls_attrs = dict(  
        __slots__=slots,
        __init__=__init__,
        __iter__=__iter__,
        __repr__=__repr__,
    )

    return type(cls_name, (object,), cls_attrs)  


def parse_identifiers(names: FieldNames) -> tuple[str, ...]:
    if isinstance(names, str):
        names = names.replace(',', ' ').split()  
    if not all(s.isidentifier() for s in names):
        raise ValueError('names must all be valid identifiers')
    return tuple(names)

User can provide field names as a single string or an iterable of strings.


Accept arguments like the first two of collections.namedtuple; return a type—i.e., a class that behaves like a tuple.


Build a tuple of attribute names; this will be the __slots__ attribute of the new class.


This function will become the __init__ method in the new class. It accepts positional and/or keyword arguments.4


Yield the field values in the order given by __slots__.


Produce the nice repr, iterating over __slots__ and self.


Assemble a dictionary of class attributes.


Build and return the new class, calling the type constructor.


Convert names separated by spaces or commas to list of str.

Example 24-2 is the first time we’ve seen type in a type hint. If the annotation was just -> type, that would mean that record_factory returns a class—and it would be correct. But the annotation -> type[tuple] is more precise: it says the returned class will be a subclass of tuple.

The last line of record_factory in Example 24-2 builds a class named by the value of cls_name, with object as its single immediate base class, and with a namespace loaded with __slots__, __init__, __iter__, and __repr__, of which the last three are instance methods.

We could have named the __slots__ class attribute anything else, but then we’d have to implement __setattr__ to validate the names of attributes being assigned, because for our record-like classes we want the set of attributes to be always the same and in the same order. However, recall that the main feature of __slots__ is saving memory when you are dealing with millions of instances, and using __slots__ has some drawbacks, discussed in “Saving Memory with __slots__”.

WARNING
Instances of classes created by record_factory are not serializable—that is, they can’t be exported with the dump function from the pickle module. Solving this problem is beyond the scope of this example, which aims to show the type class in action in a simple use case. For the full solution, study the source code for collections.namedtuple; search for the word “pickling.”

Now let’s see how to emulate more modern class builders like typing.NamedTuple, which takes a user-defined class written as a class statement, and automatically enhances it with more functionality.

Introducing __init_subclass__
Both __init_subclass__ and __set_name__ were proposed in PEP 487—Simpler customization of class creation. We saw the __set_name__ special method for descriptors for the first time in “LineItem Take #4: Automatic Naming of Storage Attributes”. Now let’s study __init_subclass__.

In Chapter 5, we saw that typing.NamedTuple and @dataclass let programmers use the class statement to specify attributes for a new class, which is then enhanced by the class builder with the automatic addition of essential methods like __init__, __repr__, __eq__, etc.

Both of these class builders read type hints in the user’s class statement to enhance the class. Those type hints also allow static type checkers to validate code that sets or gets those attributes. However, NamedTuple and @dataclass do not take advantage of the type hints for attribute validation at runtime. The Checked class in the next example does.

NOTE
It is not possible to support every conceivable static type hint for runtime type checking, which is probably why typing.NamedTuple and @dataclass don’t even try it. However, some types that are also concrete classes can be used with Checked. This includes simple types often used for field contents, such as str, int, float, and bool, as well as lists of those types.

Example 24-3 shows how to use Checked to build a Movie class.

Example 24-3. initsub/checkedlib.py: doctest for creating a Movie subclass of Checked
    >>> class Movie(Checked):  
    ...     title: str  
    ...     year: int
    ...     box_office: float
    ...
    >>> movie = Movie(title='The Godfather', year=1972, box_office=137)  
    >>> movie.title
    'The Godfather'
    >>> movie  
    Movie(title='The Godfather', year=1972, box_office=137.0)

Movie inherits from Checked—which we’ll define later in Example 24-5.


Each attribute is annotated with a constructor. Here I used built-in types.


Movie instances must be created using keyword arguments.


In return, you get a nice __repr__.

The constructors used as the attribute type hints may be any callable that takes zero or one argument and returns a value suitable for the intended field type, or rejects the argument by raising TypeError or ValueError.

Using built-in types for the annotations in Example 24-3 means the values must be acceptable by the constructor of the type. For int, this means any x such that int(x) returns an int. For str, anything goes at runtime, because str(x) works with any x in Python.5

When called with no arguments, the constructor should return a default value of its type.6

This is standard behavior for Python’s built-in constructors:

>>> int(), float(), bool(), str(), list(), dict(), set()
(0, 0.0, False, '', [], {}, set())
In a Checked subclass like Movie, missing parameters create instances with default values returned by the field constructors. For example:

    >>> Movie(title='Life of Brian')
    Movie(title='Life of Brian', year=0, box_office=0.0)
The constructors are used for validation during instantiation and when an attribute is set directly on an instance:

    >>> blockbuster = Movie(title='Avatar', year=2009, box_office='billions')
    Traceback (most recent call last):
      ...
    TypeError: 'billions' is not compatible with box_office:float
    >>> movie.year = 'MCMLXXII'
    Traceback (most recent call last):
      ...
    TypeError: 'MCMLXXII' is not compatible with year:int
CHECKED SUBCLASSES AND STATIC TYPE CHECKING
In a .py source file with a movie instance of Movie, as defined in Example 24-3, Mypy flags this assignment as a type error:

movie.year = 'MCMLXXII'
However, Mypy can’t detect type errors in this constructor call:

blockbuster = Movie(title='Avatar', year='MMIX')
That’s because Movie inherits Checked.__init__, and the signature of that method must accept any keyword arguments to support arbitrary user-defined classes.

On the other hand, if you declare a Checked subclass field with the type hint list[float], Mypy can flag assignments of lists with incompatible contents, but Checked will ignore the type parameter and treat that the same as list.

Now let’s look at the implementation of checkedlib.py. The first class is the Field descriptor, as shown in Example 24-4.

Example 24-4. initsub/checkedlib.py: the Field descriptor class
from collections.abc import Callable  
from typing import Any, NoReturn, get_type_hints


class Field:
    def __init__(self, name: str, constructor: Callable) -> None:  
        if not callable(constructor) or constructor is type(None):  
            raise TypeError(f'{name!r} type hint must be callable')
        self.name = name
        self.constructor = constructor

    def __set__(self, instance: Any, value: Any) -> None:
        if value is ...:  
            value = self.constructor()
        else:
            try:
                value = self.constructor(value)  
            except (TypeError, ValueError) as e:  
                type_name = self.constructor.__name__
                msg = f'{value!r} is not compatible with {self.name}:{type_name}'
                raise TypeError(msg) from e
        instance.__dict__[self.name] = value  

Recall that since Python 3.9, the Callable type for annotations is the ABC in collections.abc, and not the deprecated typing.Callable.


This is a minimal Callable type hint; the parameter type and return type for constructor are both implicitly Any.


For runtime checking, we use the callable built-in.7 The test against type(None) is necessary because Python reads None in a type as NoneType, the class of None (therefore callable), but a useless constructor that only returns None.


If Checked.__init__ sets the value as ... (the Ellipsis built-in object), we call the constructor with no arguments.


Otherwise, call the constructor with the given value.


If constructor raises either of these exceptions, we raise TypeError with a helpful message including the names of the field and constructor; e.g., 'MMIX' is not compatible with year:int.


If no exceptions were raised, the value is stored in the instance.__dict__.

In __set__, we need to catch TypeError and ValueError because built-in constructors may raise either of them, depending on the argument. For example, float(None) raises TypeError, but float('A') raises ValueError. On the other hand, float('8') raises no error and returns 8.0. I hereby declare that this is a feature and not a bug of this toy example.

TIP
In “LineItem Take #4: Automatic Naming of Storage Attributes”, we saw the handy __set_name__ special method for descriptors. We don’t need it in the Field class because the descriptors are not instantiated in client source code; the user declares types that are constructors, as we saw in the Movie class (Example 24-3). Instead, the Field descriptor instances are created at runtime by the Checked.__init_subclass__ method, which we’ll see in Example 24-5.

Now let’s focus on the Checked class. I split it in two listings. Example 24-5 shows the top of the class, which includes the most important methods in this example. The remaining methods are in Example 24-6.

Example 24-5. initsub/checkedlib.py: the most important methods of the Checked class
class Checked:
    @classmethod
    def _fields(cls) -> dict[str, type]:  
        return get_type_hints(cls)

    def __init_subclass__(subclass) -> None:  
        super().__init_subclass__()           
        for name, constructor in subclass._fields().items():   
            setattr(subclass, name, Field(name, constructor))  

    def __init__(self, **kwargs: Any) -> None:
        for name in self._fields():             
            value = kwargs.pop(name, ...)       
            setattr(self, name, value)          
        if kwargs:                              
            self.__flag_unknown_attrs(*kwargs)  

I wrote this class method to hide the call to typing.get_type_hints from the rest of the class. If I need to support Python ≥ 3.10 only, I’d call inspect.get_annotations instead. Review “Problems with Annotations at Runtime” for the issues with those functions.


__init_subclass__ is called when a subclass of the current class is defined. It gets that new subclass as its first argument—which is why I named the argument subclass instead of the usual cls. For more on this, see “__init_subclass__ Is Not a Typical Class Method”.


super().__init_subclass__() is not strictly necessary, but should be invoked to play nice with other classes that might implement .__init_subclass__() in the same inheritance graph. See “Multiple Inheritance and Method Resolution Order”.


Iterate over each field name and constructor…


…creating an attribute on subclass with that name bound to a Field descriptor parameterized with name and constructor.


For each name in the class fields…


…get the corresponding value from kwargs and remove it from kwargs. Using ... (the Ellipsis object) as default allows us to distinguish between arguments given the value None from arguments that were not given.8


This setattr call triggers Checked.__setattr__, shown in Example 24-6.


If there are remaining items in kwargs, their names do not match any of the declared fields, and __init__ will fail.


The error is reported by __flag_unknown_attrs, listed in Example 24-6. It takes a *names argument with the unknown attribute names. I used a single asterisk in *kwargs to pass its keys as a sequence of arguments.

__INIT_SUBCLASS__ IS NOT A TYPICAL CLASS METHOD
The @classmethod decorator is never used with __init_subclass__, but that doesn’t mean much, because the __new__ special method behaves as a class method even without @classmethod. The first argument that Python passes to __init_subclass__ is a class. However, it is never the class where __init_subclass__ is implemented: it is a newly defined subclass of that class. That’s unlike __new__ and every other class method that I know about. Therefore, I think __init_subclass__ is not a class method in the usual sense, and it is misleading to name the first argument cls. The __init_suclass__ documentation names the argument cls but explains: “…called whenever the containing class is subclassed. cls is then the new subclass.”

Now let’s see the remaining methods of the Checked class, continuing from Example 24-5. Note that I prepended _ to the _fields and _asdict method names for the same reason the collections.namedtuple API does: to reduce the chance of name clashes with user-defined field names.

Example 24-6. initsub/checkedlib.py: remaining methods of the Checked class
    def __setattr__(self, name: str, value: Any) -> None:  
        if name in self._fields():              
            cls = self.__class__
            descriptor = getattr(cls, name)
            descriptor.__set__(self, value)     
        else:                                   
            self.__flag_unknown_attrs(name)

    def __flag_unknown_attrs(self, *names: str) -> NoReturn:  
        plural = 's' if len(names) > 1 else ''
        extra = ', '.join(f'{name!r}' for name in names)
        cls_name = repr(self.__class__.__name__)
        raise AttributeError(f'{cls_name} object has no attribute{plural} {extra}')

    def _asdict(self) -> dict[str, Any]:  
        return {
            name: getattr(self, name)
            for name, attr in self.__class__.__dict__.items()
            if isinstance(attr, Field)
        }

    def __repr__(self) -> str:  
        kwargs = ', '.join(
            f'{key}={value!r}' for key, value in self._asdict().items()
        )
        return f'{self.__class__.__name__}({kwargs})'

Intercept all attempts to set an instance attribute. This is needed to prevent setting an unknown attribute.


If the attribute name is known, fetch the corresponding descriptor.


Usually we don’t need to call the descriptor __set__ explicitly. It was necessary in this case because __setattr__ intercepts all attempts to set an attribute on the instance, including in the presence of an overriding descriptor such as Field.9


Otherwise, the attribute name is unknown, and an exception will be raised by __flag_unknown_attrs.


Build a helpful error message listing all unexpected arguments, and raise AttributeError. This is a rare example of the NoReturn special type, covered in “NoReturn”.


Create a dict from the attributes of a Movie object. I’d call this method _as_dict, but I followed the convention started by the _asdict method in collections.namedtuple.


Implementing a nice __repr__ is the main reason for having _asdict in this example.

The Checked example illustrates how to handle overriding descriptors when implementing __setattr__ to block arbitrary attribute setting after instantiation. It is debatable whether implementing __setattr__ is worthwhile in this example. Without it, setting movie.director = 'Greta Gerwig' would succeed, but the director attribute would not be checked in any way, and would not appear in the __repr__ nor would it be included in the dict returned by _asdict—both defined in Example 24-6.

In record_factory.py (Example 24-2) I solved this issue using the __slots__ class attribute. However, this simpler solution is not viable in this case, as explained next.

Why __init_subclass__ Cannot Configure __slots__
The __slots__ attribute is only effective if it is one of the entries in the class namespace passed to type.__new__. Adding __slots__ to an existing class has no effect. Python invokes __init_subclass__ only after the class is built—by then it’s too late to configure __slots__. A class decorator can’t configure __slots__ either, because it is applied even later than __init_subclass__. We’ll explore these timing issues in “What Happens When: Import Time Versus Runtime”.

To configure __slots__ at runtime, your own code must build the class namespace passed as the last argument of type.__new__. To do that, you can write a class factory function, like record_factory.py, or you can take the nuclear option and implement a metaclass. We will see how to dynamically configure __slots__ in “Metaclasses 101”.

Before PEP 487 simplified the customization of class creation with __init_subclass__ in Python 3.7, similar functionality had to be implemented using a class decorator. That’s the focus of the next section.

Enhancing Classes with a Class Decorator
A class decorator is a callable that behaves similarly to a function decorator: it gets the decorated class as an argument, and should return a class to replace the decorated class. Class decorators often return the decorated class itself, after injecting more methods in it via attribute assignment.

Probably the most common reason to choose a class decorator over the simpler __init_subclass__ is to avoid interfering with other class features, such as inheritance and metaclasses.10

In this section, we’ll study checkeddeco.py, which provides the same service as checkedlib.py, but using a class decorator. As usual, we’ll start by looking at a usage example, extracted from the doctests in checkeddeco.py (Example 24-7).

Example 24-7. checkeddeco.py: creating a Movie class decorated with @checked
    >>> @checked
    ... class Movie:
    ...     title: str
    ...     year: int
    ...     box_office: float
    ...
    >>> movie = Movie(title='The Godfather', year=1972, box_office=137)
    >>> movie.title
    'The Godfather'
    >>> movie
    Movie(title='The Godfather', year=1972, box_office=137.0)
The only difference between Example 24-7 and Example 24-3 is the way the Movie class is declared: it is decorated with @checked instead of subclassing Checked. Otherwise, the external behavior is the same, including the type validation and default value assignments shown after Example 24-3 in “Introducing __init_subclass__”.

Now let’s look at the implementation of checkeddeco.py. The imports and Field class are the same as in checkedlib.py, listed in Example 24-4. There is no other class, only functions in checkeddeco.py.

The logic previously implemented in __init_subclass__ is now part of the checked function—the class decorator listed in Example 24-8.

Example 24-8. checkeddeco.py: the class decorator
def checked(cls: type) -> type:  
    for name, constructor in _fields(cls).items():    
        setattr(cls, name, Field(name, constructor))  

    cls._fields = classmethod(_fields)  # type: ignore  

    instance_methods = (  
        __init__,
        __repr__,
        __setattr__,
        _asdict,
        __flag_unknown_attrs,
    )
    for method in instance_methods:  
        setattr(cls, method.__name__, method)

    return cls  

Recall that classes are instances of type. These type hints strongly suggest this is a class decorator: it takes a class and returns a class.


_fields is a top-level function defined later in the module (in Example 24-9).


Replacing each attribute returned by _fields with a Field descriptor instance is what __init_subclass__ did in Example 24-5. Here there is more work to do…


Build a class method from _fields, and add it to the decorated class. The type: ignore comment is needed because Mypy complains that type has no _fields attribute.


Module-level functions that will become instance methods of the decorated class.


Add each of the instance_methods to cls.


Return the decorated cls, fulfilling the essential contract of a class decorator.

Every top-level function in checkeddeco.py is prefixed with an underscore, except the checked decorator. This naming convention makes sense for a couple of reasons:

checked is part of the public interface of the checkeddeco.py module, but the other functions are not.

The functions in Example 24-9 will be injected in the decorated class, and the leading _ reduces the chance of naming conflicts with user-defined attributes and methods of the decorated class.

The rest of checkeddeco.py is listed in Example 24-9. Those module-level functions have the same code as the corresponding methods of the Checked class of checkedlib.py. They were explained in Examples 24-5 and 24-6.

Note that the _fields function does double duty in checkeddeco.py. It is used as a regular function in the first line of the checked decorator, and it will also be injected as a class method of the decorated class.

Example 24-9. checkeddeco.py: the methods to be injected in the decorated class
def _fields(cls: type) -> dict[str, type]:
    return get_type_hints(cls)

def __init__(self: Any, **kwargs: Any) -> None:
    for name in self._fields():
        value = kwargs.pop(name, ...)
        setattr(self, name, value)
    if kwargs:
        self.__flag_unknown_attrs(*kwargs)

def __setattr__(self: Any, name: str, value: Any) -> None:
    if name in self._fields():
        cls = self.__class__
        descriptor = getattr(cls, name)
        descriptor.__set__(self, value)
    else:
        self.__flag_unknown_attrs(name)

def __flag_unknown_attrs(self: Any, *names: str) -> NoReturn:
    plural = 's' if len(names) > 1 else ''
    extra = ', '.join(f'{name!r}' for name in names)
    cls_name = repr(self.__class__.__name__)
    raise AttributeError(f'{cls_name} has no attribute{plural} {extra}')

def _asdict(self: Any) -> dict[str, Any]:
    return {
        name: getattr(self, name)
        for name, attr in self.__class__.__dict__.items()
        if isinstance(attr, Field)
    }

def __repr__(self: Any) -> str:
    kwargs = ', '.join(
        f'{key}={value!r}' for key, value in self._asdict().items()
    )
    return f'{self.__class__.__name__}({kwargs})'
The checkeddeco.py module implements a simple but usable class decorator. Python’s @dataclass does a lot more. It supports many configuration options, adds more methods to the decorated class, handles or warns about conflicts with user-defined methods in the decorated class, and even traverses the __mro__ to collect user-defined attributes declared in the superclasses of the decorated class. The source code of the dataclasses package in Python 3.9 is more than 1,200 lines long.

For metaprogramming classes, we must be aware of when the Python interpreter evaluates each block of code during the construction of a class. This is covered next.

What Happens When: Import Time Versus Runtime
Python programmers talk about “import time” versus “runtime,” but the terms are not strictly defined and there is a gray area between them.

At import time, the interpreter:

Parses the source code of a .py module in one pass from top to bottom. This is when a SyntaxError may occur.

Compiles the bytecode to be executed.

Executes the top-level code of the compiled module.

If there is an up-to-date .pyc file available in the local __pycache__, parsing and compiling are skipped because the bytecode is ready to run.

Although parsing and compiling are definitely “import time” activities, other things may happen at that time, because almost every statement in Python is executable in the sense that they can potentially run user code and may change the state of the user program.

In particular, the import statement is not merely a declaration,11 but it actually runs all the top-level code of a module when it is imported for the first time in the process. Further imports of the same module will use a cache, and then the only effect will be binding the imported objects to names in the client module. That top-level code may do anything, including actions typical of “runtime,” such as writing to a log or connecting to a database.12 That’s why the border between “import time” and “runtime” is fuzzy: the import statement can trigger all sorts of “runtime” behavior. Conversely, “import time” can also happen deep inside runtime, because the import statement and the __import__() built-in can be used inside any regular function.

This is all rather abstract and subtle, so let’s do some experiments to see what happens when.

Evaluation Time Experiments
Consider an evaldemo.py script that uses a class decorator, a descriptor, and a class builder based on __init_subclass__, all defined in a builderlib.py module. The modules have several print calls to show what happens under the covers. Otherwise, they don’t perform anything useful. The goal of these experiments is to observe the order in which these print calls happen.

WARNING
Applying a class decorator and a class builder with __init_subclass__ together in single class is likely a sign of overengineering or desperation. This unusual combination is useful in these experiments to show the timing of the changes that a class decorator and __init_subclass__ can apply to a class.

Let’s start by checking out builderlib.py, split into two parts: Example 24-10 and Example 24-11.

Example 24-10. builderlib.py: top of the module
print('@ builderlib module start')

class Builder:  
    print('@ Builder body')

    def __init_subclass__(cls):  
        print(f'@ Builder.__init_subclass__({cls!r})')

        def inner_0(self):  
            print(f'@ SuperA.__init_subclass__:inner_0({self!r})')

        cls.method_a = inner_0

    def __init__(self):
        super().__init__()
        print(f'@ Builder.__init__({self!r})')


def deco(cls):  
    print(f'@ deco({cls!r})')

    def inner_1(self):  
        print(f'@ deco:inner_1({self!r})')

    cls.method_b = inner_1
    return cls  

This is a class builder to implement…


…an __init_subclass__ method.


Define a function to be added to the subclass in the assignment below.


A class decorator.


Function to be added to the decorated class.


Return the class received as an argument.

Continuing with builderlib.py in Example 24-11…

Example 24-11. builderlib.py: bottom of the module
class Descriptor:  
    print('@ Descriptor body')

    def __init__(self):  
        print(f'@ Descriptor.__init__({self!r})')

    def __set_name__(self, owner, name):  
        args = (self, owner, name)
        print(f'@ Descriptor.__set_name__{args!r}')

    def __set__(self, instance, value):  
        args = (self, instance, value)
        print(f'@ Descriptor.__set__{args!r}')

    def __repr__(self):
        return '<Descriptor instance>'


print('@ builderlib module end')

A descriptor class to demonstrate when…


…a descriptor instance is created, and when…


…__set_name__ will be invoked during the owner class construction.


Like the other methods, this __set__ doesn’t do anything except display its arguments.

If you import builderlib.py in the Python console, this is what you get:

>>> import builderlib
@ builderlib module start
@ Builder body
@ Descriptor body
@ builderlib module end
Note that the lines printed by builderlib.py are prefixed with @.

Now let’s turn to evaldemo.py, which will trigger special methods in builderlib.py (Example 24-12).

Example 24-12. evaldemo.py: script to experiment with builderlib.py
#!/usr/bin/env python3

from builderlib import Builder, deco, Descriptor

print('# evaldemo module start')

@deco  
class Klass(Builder):  
    print('# Klass body')

    attr = Descriptor()  

    def __init__(self):
        super().__init__()
        print(f'# Klass.__init__({self!r})')

    def __repr__(self):
        return '<Klass instance>'


def main():  
    obj = Klass()
    obj.method_a()
    obj.method_b()
    obj.attr = 999

if __name__ == '__main__':
    main()

print('# evaldemo module end')

Apply a decorator.


Subclass Builder to trigger its __init_subclass__.


Instantiate the descriptor.


This will only be called if the module is run as the main program.

The print calls in evaldemo.py show a # prefix. If you open the console again and import evaldemo.py, Example 24-13 is the output.

Example 24-13. Console experiment with evaldemo.py
>>> import evaldemo
@ builderlib module start  
@ Builder body
@ Descriptor body
@ builderlib module end
# evaldemo module start
# Klass body  
@ Descriptor.__init__(<Descriptor instance>)  
@ Descriptor.__set_name__(<Descriptor instance>,
      <class 'evaldemo.Klass'>, 'attr')                
@ Builder.__init_subclass__(<class 'evaldemo.Klass'>)  
@ deco(<class 'evaldemo.Klass'>)  
# evaldemo module end

The top four lines are the result of from builderlib import… . They will not appear if you didn’t close the console after the previous experiment, because builderlib.py is already loaded.


This signals that Python started reading the body of Klass. At this point, the class object does not exist yet.


The descriptor instance is created and bound to attr in the namespace that Python will pass to the default class object constructor: type.__new__.


At this point, Python’s built-in type.__new__ has created the Klass object and calls __set_name__ on each descriptor instance of descriptor classes that provide that method, passing Klass as the owner argument.


type.__new__ then calls __init_subclass__ on the superclass of Klass, passing Klass as the single argument.


When type.__new__ returns the class object, Python applies the decorator. In this example, the class returned by deco is bound to Klass in the module namespace.

The implementation of type.__new__ is written in C. The behavior I just described is documented in the “Creating the class object” section of Python’s “Data Model” reference.

Note that the main() function of evaldemo.py (Example 24-12) was not executed in the console session (Example 24-13), therefore no instance of Klass was created. All the action we saw was triggered by “import time” operations: importing builderlib and defining Klass.

If you run evaldemo.py as a script, you will see the same output as Example 24-13 with extra lines right before the end. The extra lines are the result of running main() (Example 24-14).

Example 24-14. Running evaldemo.py as a program
$ ./evaldemo.py
[... 9 lines omitted ...]
@ deco(<class '__main__.Klass'>)  
@ Builder.__init__(<Klass instance>)  
# Klass.__init__(<Klass instance>)
@ SuperA.__init_subclass__:inner_0(<Klass instance>)  
@ deco:inner_1(<Klass instance>)  
@ Descriptor.__set__(<Descriptor instance>, <Klass instance>, 999)  
# evaldemo module end

The top 10 lines—including this one—are the same as shown in Example 24-13.


Triggered by super().__init__() in Klass.__init__.


Triggered by obj.method_a() in main; method_a was injected by SuperA.__init_subclass__.


Triggered by obj.method_b() in main; method_b was injected by deco.


Triggered by obj.attr = 999 in main.

A base class with __init_subclass__ and a class decorator are powerful tools, but they are limited to working with a class already built by type.__new__ under the covers. In the rare occasions when you need to adjust the arguments passed to type.__new__, you need a metaclass. That’s the final destination of this chapter—and this book.

Metaclasses 101
[Metaclasses] are deeper magic than 99% of users should ever worry about. If you wonder whether you need them, you don’t (the people who actually need them know with certainty that they need them, and don’t need an explanation about why).

Tim Peters, inventor of the Timsort algorithm and prolific Python contributor13

A metaclass is a class factory. In contrast with record_factory from Example 24-2, a metaclass is written as a class. In other words, a metaclass is a class whose instances are classes. Figure 24-1 depicts a metaclass using the Mills & Gizmos Notation: a mill producing another mill.


Figure 24-1. A metaclass is a class that builds classes.
Consider the Python object model: classes are objects, therefore each class must be an instance of some other class. By default, Python classes are instances of type. In other words, type is the metaclass for most built-in and user-defined classes:

>>> str.__class__
<class 'type'>
>>> from bulkfood_v5 import LineItem
>>> LineItem.__class__
<class 'type'>
>>> type.__class__
<class 'type'>
To avoid infinite regress, the class of type is type, as the last line shows.

Note that I am not saying that str or LineItem are subclasses of type. What I am saying is that str and LineItem are instances of type. They all are subclasses of object. Figure 24-2 may help you confront this strange reality.


Figure 24-2. Both diagrams are true. The left one emphasizes that str, type, and LineItem are subclasses of object. The right one makes it clear that str, object, and LineItem are instances type, because they are all classes.
NOTE
The classes object and type have a unique relationship: object is an instance of type, and type is a subclass of object. This relationship is “magic”: it cannot be expressed in Python because either class would have to exist before the other could be defined. The fact that type is an instance of itself is also magical.

The next snippet shows that the class of collections.Iterable is abc.ABCMeta. Note that Iterable is an abstract class, but ABCMeta is a concrete class—after all, Iterable is an instance of ABCMeta:

>>> from collections.abc import Iterable
>>> Iterable.__class__
<class 'abc.ABCMeta'>
>>> import abc
>>> from abc import ABCMeta
>>> ABCMeta.__class__
<class 'type'>
Ultimately, the class of ABCMeta is also type. Every class is an instance of type, directly or indirectly, but only metaclasses are also subclasses of type. That’s the most important relationship to understand metaclasses: a metaclass, such as ABCMeta, inherits from type the power to construct classes. Figure 24-3 illustrates this crucial relationship.


Figure 24-3. Iterable is a subclass of object and an instance of ABCMeta. Both object and ABCMeta are instances of type, but the key relationship here is that ABCMeta is also a subclass of type, because ABCMeta is a metaclass. In this diagram, Iterable is the only abstract class.
The important takeaway here is that metaclasses are subclasses of type, and that’s what makes them work as class factories. A metaclass can customize its instances by implementing special methods, as the next sections demonstrate.

How a Metaclass Customizes a Class
To use a metaclass, it’s critical to understand how __new__ works on any class. This was discussed in “Flexible Object Creation with __new__”.

The same mechanics happen at a “meta” level when a metaclass is about to create a new instance, which is a class. Consider this declaration:

class Klass(SuperKlass, metaclass=MetaKlass):
    x = 42
    def __init__(self, y):
        self.y = y
To process that class statement, Python calls MetaKlass.__new__ with these arguments:

meta_cls
The metaclass itself (MetaKlass), because __new__ works as class method.

cls_name
The string Klass.

bases
The single-element tuple (SuperKlass,), with more elements in the case of multiple inheritance.

cls_dict
A mapping like:

{x: 42, `__init__`: <function __init__ at 0x1009c4040>}
When you implement MetaKlass.__new__, you can inspect and change those arguments before passing them to super().__new__, which will eventually call type.__new__ to create the new class object.

After super().__new__ returns, you can also apply further processing to the newly created class before returning it to Python. Python then calls SuperKlass.__init_subclass__, passing the class you created, and then applies a class decorator to it, if one is present. Finally, Python binds the class object to its name in the surrounding namespace—usually the global namespace of a module, if the class statement was a top-level statement.

The most common processing made in a metaclass __new__ is to add or replace items in the cls_dict—the mapping that represents the namespace of the class under construction. For instance, before calling super().__new__, you can inject methods in the class under construction by adding functions to cls_dict. However, note that adding methods can also be done after the class is built, which is why we were able to do it using __init_subclass__ or a class decorator.

One attribute that you must add to the cls_dict before type.__new__ runs is __slots__, as discussed in “Why __init_subclass__ Cannot Configure __slots__”. The __new__ method of a metaclass is the ideal place to configure __slots__. The next section shows how to do that.

A Nice Metaclass Example
The MetaBunch metaclass presented here is a variation of the last example in Chapter 4 of Python in a Nutshell, 3rd ed., by Alex Martelli, Anna Ravenscroft, and Steve Holden, written to run on Python 2.7 and 3.5.14 Assuming Python 3.6 or later, I was able to further simplify the code.

First, let’s see what the Bunch base class provides:

    >>> class Point(Bunch):
    ...     x = 0.0
    ...     y = 0.0
    ...     color = 'gray'
    ...
    >>> Point(x=1.2, y=3, color='green')
    Point(x=1.2, y=3, color='green')
    >>> p = Point()
    >>> p.x, p.y, p.color
    (0.0, 0.0, 'gray')
    >>> p
    Point()
Remember that Checked assigns names to the Field descriptors in subclasses based on class variable type hints, which do not actually become attributes on the class since they don’t have values.

Bunch subclasses, on the other hand, use actual class attributes with values, which then become the default values of the instance attributes. The generated __repr__ omits the arguments for attributes that are equal to the defaults.

MetaBunch—the metaclass of Bunch—generates __slots__ for the new class from the class attributes declared in the user’s class. This blocks the instantiation and later assignment of undeclared attributes:

    >>> Point(x=1, y=2, z=3)
    Traceback (most recent call last):
      ...
    AttributeError: No slots left for: 'z'
    >>> p = Point(x=21)
    >>> p.y = 42
    >>> p
    Point(x=21, y=42)
    >>> p.flavor = 'banana'
    Traceback (most recent call last):
      ...
    AttributeError: 'Point' object has no attribute 'flavor'
Now let’s dive into the elegant code of MetaBunch in Example 24-15.

Example 24-15. metabunch/from3.6/bunch.py: MetaBunch metaclass and Bunch class
class MetaBunch(type):  
    def __new__(meta_cls, cls_name, bases, cls_dict):  

        defaults = {}  

        def __init__(self, **kwargs):  
            for name, default in defaults.items():  
                setattr(self, name, kwargs.pop(name, default))
            if kwargs:  
                extra = ', '.join(kwargs)
                raise AttributeError(f'No slots left for: {extra!r}')

        def __repr__(self):  
            rep = ', '.join(f'{name}={value!r}'
                            for name, default in defaults.items()
                            if (value := getattr(self, name)) != default)
            return f'{cls_name}({rep})'

        new_dict = dict(__slots__=[], __init__=__init__, __repr__=__repr__)  

        for name, value in cls_dict.items():  
            if name.startswith('__') and name.endswith('__'):  
                if name in new_dict:
                    raise AttributeError(f"Can't set {name!r} in {cls_name!r}")
                new_dict[name] = value
            else:  
                new_dict['__slots__'].append(name)
                defaults[name] = value
        return super().__new__(meta_cls, cls_name, bases, new_dict)  


class Bunch(metaclass=MetaBunch):  
    pass

To create a new metaclass, inherit from type.


__new__ works as a class method, but the class is a metaclass, so I like to name the first argument meta_cls (mcs is a common alternative). The remaining three arguments are the same as the three-argument signature for calling type() directly to create a class.


defaults will hold a mapping of attribute names and their default values.


This will be injected into the new class.


Read the defaults and set the corresponding instance attribute with a value popped from kwargs or a default.


If there is still any item in kwargs, it means there are no slots left where we can place them. We believe in failing fast as best practice, so we don’t want to silently ignore extra items. A quick and effective solution is to pop one item from kwargs and try to set it on the instance, triggering an AttributeError on purpose.


__repr__ returns a string that looks like a constructor call—e.g., Point(x=3), omitting the keyword arguments with default values.


Initialize namespace for the new class.


Iterate over the namespace of the user’s class.


If a dunder name is found, copy the item to the new class namespace, unless it’s already there. This prevents users from overwriting __init__, __repr__, and other attributes set by Python, such as __qualname__ and __module__.


If not a dunder name, append to __slots__ and save its value in defaults.


Build and return the new class.


Provide a base class, so users don’t need to see MetaBunch.

MetaBunch works because it is able to configure __slots__ before calling super().__new__ to build the final class. As usual when metaprogramming, understanding the sequence of actions is key. Let’s do another evaluation time experiment, now with a metaclass.

Metaclass Evaluation Time Experiment
This is a variation of “Evaluation Time Experiments”, adding a metaclass to the mix. The builderlib.py module is the same as before, but the main script is now evaldemo_meta.py, listed in Example 24-16.

Example 24-16. evaldemo_meta.py: experimenting with a metaclass
#!/usr/bin/env python3

from builderlib import Builder, deco, Descriptor
from metalib import MetaKlass  

print('# evaldemo_meta module start')

@deco
class Klass(Builder, metaclass=MetaKlass):  
    print('# Klass body')

    attr = Descriptor()

    def __init__(self):
        super().__init__()
        print(f'# Klass.__init__({self!r})')

    def __repr__(self):
        return '<Klass instance>'


def main():
    obj = Klass()
    obj.method_a()
    obj.method_b()
    obj.method_c()  
    obj.attr = 999


if __name__ == '__main__':
    main()

print('# evaldemo_meta module end')

Import MetaKlass from metalib.py, which we’ll see in Example 24-18.


Declare Klass as a subclass of Builder and an instance of MetaKlass.


This method is injected by MetaKlass.__new__, as we’ll see.

WARNING
In the interest of science, Example 24-16 defies all reason and applies three different metaprogramming techniques together on Klass: a decorator, a base class using __init_subclass__, and a custom metaclass. If you do this in production code, please don’t blame me. Again, the goal is to observe the order in which the three techniques interfere in the class construction process.

As in the previous evaluation time experiment, this example does nothing but print messages revealing the flow of execution. Example 24-17 shows the code for the top part of metalib.py—the rest is in Example 24-18.

Example 24-17. metalib.py: the NosyDict class
print('% metalib module start')

import collections

class NosyDict(collections.UserDict):
    def __setitem__(self, key, value):
        args = (self, key, value)
        print(f'% NosyDict.__setitem__{args!r}')
        super().__setitem__(key, value)

    def __repr__(self):
        return '<NosyDict instance>'
I wrote the NosyDict class to override __setitem__ to display each key and value as they are set. The metaclass will use a NosyDict instance to hold the namespace of the class under construction, revealing more of Python’s inner workings.

The main attraction of metalib.py is the metaclass in Example 24-18. It implements the __prepare__ special method, a class method that Python only invokes on metaclasses. The __prepare__ method provides the earliest opportunity to influence the process of creating a new class.

TIP
When coding a metaclass, I find it useful to adopt this naming convention for special method arguments:

Use cls instead of self for instance methods, because the instance is a class.

Use meta_cls instead of cls for class methods, because the class is a metaclass. Recall that __new__ behaves as a class method even without the @classmethod decorator.

Example 24-18. metalib.py: the MetaKlass
class MetaKlass(type):
    print('% MetaKlass body')

    @classmethod  
    def __prepare__(meta_cls, cls_name, bases):  
        args = (meta_cls, cls_name, bases)
        print(f'% MetaKlass.__prepare__{args!r}')
        return NosyDict()  

    def __new__(meta_cls, cls_name, bases, cls_dict):  
        args = (meta_cls, cls_name, bases, cls_dict)
        print(f'% MetaKlass.__new__{args!r}')
        def inner_2(self):
            print(f'% MetaKlass.__new__:inner_2({self!r})')

        cls = super().__new__(meta_cls, cls_name, bases, cls_dict.data)  

        cls.method_c = inner_2  

        return cls  

    def __repr__(cls):  
        cls_name = cls.__name__
        return f"<class {cls_name!r} built by MetaKlass>"

print('% metalib module end')

__prepare__ should be declared as a class method. It is not an instance method because the class under construction does not exist yet when Python calls __prepare__.


Python calls __prepare__ on a metaclass to obtain a mapping to hold the namespace of the class under construction.


Return NosyDict instance to be used as the namespace.


cls_dict is a NosyDict instance returned by __prepare__.


type.__new__ requires a real dict as the last argument, so I give it the data attribute of NosyDict, inherited from UserDict.


Inject a method in the newly created class.


As usual, __new__ must return the object just created—in this case, the new class.


Defining __repr__ on a metaclass allows customizing the repr() of class objects.

The main use case for __prepare__ before Python 3.6 was to provide an OrderedDict to hold the attributes of the class under construction, so that the metaclass __new__ could process those attributes in the order in which they appear in the source code of the user’s class definition. Now that dict preserves the insertion order, __prepare__ is rarely needed. You will see a creative use for it in “A Metaclass Hack with __prepare__”.

Importing metalib.py in the Python console is not very exciting. Note the use of % to prefix the lines output by this module:

>>> import metalib
% metalib module start
% MetaKlass body
% metalib module end
Lots of things happen if you import evaldemo_meta.py, as you can see in Example 24-19.

Example 24-19. Console experiment with evaldemo_meta.py
>>> import evaldemo_meta
@ builderlib module start
@ Builder body
@ Descriptor body
@ builderlib module end
% metalib module start
% MetaKlass body
% metalib module end
# evaldemo_meta module start  
% MetaKlass.__prepare__(<class 'metalib.MetaKlass'>, 'Klass',  
                        (<class 'builderlib.Builder'>,))
% NosyDict.__setitem__(<NosyDict instance>, '__module__', 'evaldemo_meta')  
% NosyDict.__setitem__(<NosyDict instance>, '__qualname__', 'Klass')
# Klass body
@ Descriptor.__init__(<Descriptor instance>)  
% NosyDict.__setitem__(<NosyDict instance>, 'attr', <Descriptor instance>)  
% NosyDict.__setitem__(<NosyDict instance>, '__init__',
                       <function Klass.__init__ at …>)  
% NosyDict.__setitem__(<NosyDict instance>, '__repr__',
                       <function Klass.__repr__ at …>)
% NosyDict.__setitem__(<NosyDict instance>, '__classcell__', <cell at …: empty>)
% MetaKlass.__new__(<class 'metalib.MetaKlass'>, 'Klass',
                    (<class 'builderlib.Builder'>,), <NosyDict instance>)  
@ Descriptor.__set_name__(<Descriptor instance>,
                          <class 'Klass' built by MetaKlass>, 'attr')  
@ Builder.__init_subclass__(<class 'Klass' built by MetaKlass>)
@ deco(<class 'Klass' built by MetaKlass>)
# evaldemo_meta module end

The lines before this are the result of importing builderlib.py and metalib.py.


Python invokes __prepare__ to start processing a class statement.


Before parsing the class body, Python adds the __module__ and __qualname__ entries to the namespace of the class under construction.


The descriptor instance is created…


…and bound to attr in the class namespace.


__init__ and __repr__ methods are defined and added to the namespace.


Once Python finishes processing the class body, it calls MetaKlass.__new__.


__set_name__, __init_subclass__, and the decorator are invoked in this order, after the __new__ method of the metaclass returns the newly constructed class.

If you run evaldemo_meta.py as script, main() is called, and a few more things happen (Example 24-20).

Example 24-20. Running evaldemo_meta.py as a program
$ ./evaldemo_meta.py
[... 20 lines omitted ...]
@ deco(<class 'Klass' built by MetaKlass>)  
@ Builder.__init__(<Klass instance>)
# Klass.__init__(<Klass instance>)
@ SuperA.__init_subclass__:inner_0(<Klass instance>)
@ deco:inner_1(<Klass instance>)
% MetaKlass.__new__:inner_2(<Klass instance>)  
@ Descriptor.__set__(<Descriptor instance>, <Klass instance>, 999)
# evaldemo_meta module end

The top 21 lines—including this one—are the same shown in Example 24-19.


Triggered by obj.method_c() in main; method_c was injected by MetaKlass.__new__.

Let’s now go back to the idea of the Checked class with the Field descriptors implementing runtime type validation, and see how it can be done with a metaclass.

A Metaclass Solution for Checked
I don’t want to encourage premature optimization and overengineering, so here is a make-believe scenario to justify rewriting checkedlib.py with __slots__, which requires the application of a metaclass. Feel free to skip it.

A BIT OF STORYTELLING
Our checkedlib.py using __init_subclass__ is a company-wide success, and our production servers have millions of instances of Checked subclasses in memory at any one time.

Profiling a proof-of-concept, we discover that using __slots__ will reduce the cloud hosting bill for two reasons:

Lower memory usage, as Checked instances don’t need their own __dict__

Higher performance, by removing __setattr__, which was created just to block unexpected attributes, but is triggered at instantiation and for all attribute setting before Field.__set__ is called to do its job

The metaclass/checkedlib.py module we’ll study next is a drop-in replacement for initsub/checkedlib.py. The doctests embedded in them are identical, as well as the checkedlib_test.py files for pytest.

The complexity in checkedlib.py is abstracted away from the user. Here is the source code of a script using the package:

from checkedlib import Checked

class Movie(Checked):
    title: str
    year: int
    box_office: float

if __name__ == '__main__':
    movie = Movie(title='The Godfather', year=1972, box_office=137)
    print(movie)
    print(movie.title)
That concise Movie class definition leverages three instances of the Field validating descriptor, a __slots__ configuration, five methods inherited from Checked, and a metaclass to put it all together. The only visible part of checkedlib is the Checked base class.

Consider Figure 24-4. The Mills & Gizmos Notation complements the UML class diagram by making the relationship between classes and instances more visible.

For example, a Movie class using the new checkedlib.py is an instance of CheckedMeta, and a subclass of Checked. Also, the title, year, and box_office class attributes of Movie are three separate instances of Field. Each Movie instance has its own _title, _year, and _box_office attributes, to store the values of the corresponding fields.

Now let’s study the code, starting with the Field class, shown in Example 24-21.

The Field descriptor class is now a bit different. In the previous examples, each Field descriptor instance stored its value in the managed instance using an attribute of the same name. For example, in the Movie class, the title descriptor stored the field value in a title attribute in the managed instance. This made it unnecessary for Field to provide a __get__ method.

However, when a class like Movie uses __slots__, it cannot have class attributes and instance attributes with the same name. Each descriptor instance is a class attribute, and now we need separate per-instance storage attributes. The code uses the descriptor name prefixed with a single _. Therefore Field instances have separate name and storage_name attributes, and we implement Field.__get__.


Figure 24-4. UML class diagram annotated with MGN: the CheckedMeta meta-mill builds the Movie mill. The Field mill builds the title, year, and box_office descriptors, which are class attributes of Movie. The per-instance data for the fields is stored in the _title, _year, and _box_office instance attributes of Movie. Note the package boundary of checkedlib. The developer of Movie doesn’t need to grok all the machinery inside checkedlib.py.
Example 24-21 shows the source code for Field, with callouts describing only the changes in this version.

Example 24-21. metaclass/checkedlib.py: the Field descriptor with storage_name and __get__
class Field:
    def __init__(self, name: str, constructor: Callable) -> None:
        if not callable(constructor) or constructor is type(None):
            raise TypeError(f'{name!r} type hint must be callable')
        self.name = name
        self.storage_name = '_' + name  
        self.constructor = constructor

    def __get__(self, instance, owner=None):
        if instance is None:  
            return self
        return getattr(instance, self.storage_name)  

    def __set__(self, instance: Any, value: Any) -> None:
        if value is ...:
            value = self.constructor()
        else:
            try:
                value = self.constructor(value)
            except (TypeError, ValueError) as e:
                type_name = self.constructor.__name__
                msg = f'{value!r} is not compatible with {self.name}:{type_name}'
                raise TypeError(msg) from e
        setattr(instance, self.storage_name, value)  

Compute storage_name from the name argument.


If __get__ gets None as the instance argument, the descriptor is being read from the managed class itself, not a managed instance. So we return the descriptor.


Otherwise, return the value stored in the attribute named storage_name.


__set__ now uses setattr to set or update the managed attribute.

Example 24-22 shows the code for the metaclass that drives this example.

Example 24-22. metaclass/checkedlib.py: the CheckedMeta metaclass
class CheckedMeta(type):

    def __new__(meta_cls, cls_name, bases, cls_dict):  
        if '__slots__' not in cls_dict:  
            slots = []
            type_hints = cls_dict.get('__annotations__', {})  
            for name, constructor in type_hints.items():   
                field = Field(name, constructor)  
                cls_dict[name] = field  
                slots.append(field.storage_name)  

            cls_dict['__slots__'] = slots  

        return super().__new__(
                meta_cls, cls_name, bases, cls_dict)  

__new__ is the only method implemented in CheckedMeta.


Only enhance the class if its cls_dict doesn’t include __slots__. If __slots__ is already present, assume it is the Checked base class and not a user-defined subclass, and build the class as is.


To get the type hints in prior examples, we used typing.get_type_hints, but that requires an existing class as the first argument. At this point, the class we are configuring does not exist yet, so we need to retrieve the __annotations__ directly from the cls_dict—the namespace of the class under construction, which Python passes as the last argument to the metaclass __new__.


Iterate over type_hints to…


…build a Field for each annotated attribute…


…overwrite the corresponding entry in cls_dict with the Field instance…


…and append the storage_name of the field in the list we’ll use to…


…populate the __slots__ entry in cls_dict—the namespace of the class under construction.


Finally, we call super().__new__.

The last part of metaclass/checkedlib.py is the Checked base class that users of this library will subclass to enhance their classes, like Movie.

The code for this version of Checked is the same as Checked in initsub/checkedlib.py (listed in Example 24-5 and Example 24-6), with three changes:

Added an empty __slots__ to signal to CheckedMeta.__new__ that this class doesn’t require special processing.

Removed __init_subclass__. Its job is now done by CheckedMeta.__new__.

Removed __setattr__. It became redundant because adding __slots__ to the user-defined class prevents setting undeclared attributes.

Example 24-23 is a complete listing of the final version of Checked.

Example 24-23. metaclass/checkedlib.py: the Checked base class
class Checked(metaclass=CheckedMeta):
    __slots__ = ()  # skip CheckedMeta.__new__ processing

    @classmethod
    def _fields(cls) -> dict[str, type]:
        return get_type_hints(cls)

    def __init__(self, **kwargs: Any) -> None:
        for name in self._fields():
            value = kwargs.pop(name, ...)
            setattr(self, name, value)
        if kwargs:
            self.__flag_unknown_attrs(*kwargs)

    def __flag_unknown_attrs(self, *names: str) -> NoReturn:
        plural = 's' if len(names) > 1 else ''
        extra = ', '.join(f'{name!r}' for name in names)
        cls_name = repr(self.__class__.__name__)
        raise AttributeError(f'{cls_name} object has no attribute{plural} {extra}')

    def _asdict(self) -> dict[str, Any]:
        return {
            name: getattr(self, name)
            for name, attr in self.__class__.__dict__.items()
            if isinstance(attr, Field)
        }

    def __repr__(self) -> str:
        kwargs = ', '.join(
            f'{key}={value!r}' for key, value in self._asdict().items()
        )
        return f'{self.__class__.__name__}({kwargs})'
This concludes the third rendering of a class builder with validated descriptors.

The next section covers some general issues related to metaclasses.

Metaclasses in the Real World
Metaclasses are powerful, but tricky. Before deciding to implement a metaclass, consider the following points.

Modern Features Simplify or Replace Metaclasses
Over time, several common use cases of metaclasses were made redundant by new language features:

Class decorators
Simpler to understand than metaclasses, and less likely to cause conflicts with base classes and metaclasses.

__set_name__
Avoids the need for custom metaclass logic to automatically set the name of a descriptor.15

__init_subclass__
Provides a way to customize class creation that is transparent to the end user and even simpler than a decorator—but may introduce conflicts in a complex class hierarchy.

Built-in dict preserving key insertion order
Eliminated the #1 reason to use __prepare__: to provide an OrderedDict to store the namespace of the class under construction. Python only calls __prepare__ on metaclasses, so if you needed to process the class namespace in the order it appears in the source code, you had to use a metaclass before Python 3.6.

As of 2021, every actively maintained version of CPython supports all the features just listed.

I keep advocating these features because I see too much unnecessary complexity in our profession, and metaclasses are a gateway to complexity.

Metaclasses Are Stable Language Features
Metaclasses were introduced in Python 2.2 in 2002, together with so-called “new-style classes,” descriptors, and properties.

It is remarkable that the MetaBunch example, first posted by Alex Martelli in July 2002, still works in Python 3.9—the only change being the way to specify the metaclass to use, which in Python 3 is done with the syntax class Bunch(metaclass=MetaBunch):.

None of the additions I mentioned in “Modern Features Simplify or Replace Metaclasses” broke existing code using metaclasses. But legacy code using metaclasses can often be simplified by leveraging those features, especially if you can drop support to Python versions before 3.6—which are no longer maintained.

A Class Can Only Have One Metaclass
If your class declaration involves two or more metaclasses, you will see this puzzling error message:

TypeError: metaclass conflict: the metaclass of a derived class
must be a (non-strict) subclass of the metaclasses of all its bases
This may happen even without multiple inheritance. For example, a declaration like this could trigger that TypeError:

class Record(abc.ABC, metaclass=PersistentMeta):
    pass
We saw that abc.ABC is an instance of the abc.ABCMeta metaclass. If that Persistent metaclass is not itself a subclass of abc.ABCMeta, you get a metaclass conflict.

There are two ways of dealing with that error:

Find some other way of doing what you need to do, while avoiding at least one of the metaclasses involved.

Write your own PersistentABCMeta metaclass as a subclass of both abc.ABCMeta and PersistentMeta, using multiple inheritance, and use that as the only metaclass for Record.16

TIP
I can imagine the solution of the metaclass with two base metaclasses implemented to meet a deadline. In my experience, metaclass programming always takes longer than anticipated, which makes this approach risky before a hard deadline. If you do it and make the deadline, the code may contain subtle bugs. Even in the absence of known bugs, you should consider this approach as technical debt simply because it is hard to understand and maintain.

Metaclasses Should Be Implementation Details
Besides type, there are only six metaclasses in the entire Python 3.9 standard library. The better known metaclasses are probably abc.ABCMeta, typing.NamedTupleMeta, and enum.EnumMeta. None of them are intended to appear explicitly in user code. We may consider them implementation details.

Although you can do some really wacky metaprogramming with metaclasses, it’s best to heed the principle of least astonishment so that most users can indeed regard metaclasses as implementation details.17

In recent years, some metaclasses in the Python standard library were replaced by other mechanisms, without breaking the public API of their packages. The simplest way to future-proof such APIs is to offer a regular class that users subclass to access the functionality provided by the metaclass, as we’ve done in our examples.

To wrap up our coverage of class metaprogramming, I will share with you the coolest, small example of metaclass I found as I researched this chapter.

A Metaclass Hack with __prepare__
When I updated this chapter for the second edition, I needed to find simple but illuminating examples to replace the bulkfood LineItem code that no longer require metaclasses since Python 3.6.

The simplest and most interesting metaclass idea was given to me by João S. O. Bueno—better known as JS in the Brazilian Python community. One application of his idea is to create a class that autogenerates numeric constants:

    >>> class Flavor(AutoConst):
    ...     banana
    ...     coconut
    ...     vanilla
    ...
    >>> Flavor.vanilla
    2
    >>> Flavor.banana, Flavor.coconut
    (0, 1)
Yes, that code works as shown! That’s actually a doctest in autoconst_demo.py.

Here is the user-friendly AutoConst base class and the metaclass behind it, implemented in autoconst.py:

class AutoConstMeta(type):
    def __prepare__(name, bases, **kwargs):
        return WilyDict()

class AutoConst(metaclass=AutoConstMeta):
    pass
That’s it.

Clearly the trick is in WilyDict.

When Python processes the namespace of the user’s class and reads banana, it looks up that name in the mapping provided by __prepare__: an instance of WilyDict. WilyDict implements __missing__, covered in “The __missing__ Method”. The WilyDict instance initially has no 'banana' key, so the __missing__ method is triggered. It makes an item on the fly with the key 'banana' and the value 0, returning that value. Python is happy with that, then tries to retrieve 'coconut'. WilyDict promptly adds that entry with the value 1, returning it. The same happens with 'vanilla', which is then mapped to 2.

We’ve seen __prepare__ and __missing__ before. The real innovation is how JS put them together.

Here is the source code for WilyDict, also from autoconst.py:

class WilyDict(dict):
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.__next_value = 0

    def __missing__(self, key):
        if key.startswith('__') and key.endswith('__'):
            raise KeyError(key)
        self[key] = value = self.__next_value
        self.__next_value += 1
        return value
While experimenting, I found that Python looked up __name__ in the namespace of the class under construction, causing WilyDict to add a __name__ entry, and increment __next_value. So I added that if statement in __missing__ to raise KeyError for keys that look like dunder attributes.

The autoconst.py package both requires and illustrates mastery of Python’s dynamic class building machinery.

I had a great time adding more functionality to AutoConstMeta and AutoConst, but instead of sharing my experiments, I will let you have fun playing with JS’s ingenious hack.

Here are some ideas:

Make it possible to retrieve the constant name if you have the value. For example, Flavor[2] could return 'vanilla'. You can to this by implementing __getitem__ in AutoConstMeta. Since Python 3.9, you can implement __class_getitem__ in AutoConst itself.

Support iteration over the class, by implementing __iter__ on the metaclass. I would make the __iter__ yield the constants as (name, value) pairs.

Implement a new Enum variant. This would be a major undertaking, because the enum package is full of tricks, including the EnumMeta metaclass with hundreds of lines of code and a nontrivial __prepare__ method.

Enjoy!

NOTE
The __class_getitem__ special method was added in Python 3.9 to support generic types, as part of PEP 585—Type Hinting Generics In Standard Collections. Thanks to __class_getitem__, Python’s core developers did not have to write a new metaclass for the built-in types to implement __getitem__ so that we could write generic type hints like list[int]. This is a narrow feature, but representative of a wider use case for metaclasses: implementing operators and other special methods to work at the class level, such as making the class itself iterable, just like Enum subclasses.

Wrapping Up
Metaclasses, as well as class decorators and __init_subclass__ are useful for:

Subclass registration

Subclass structural validation

Applying decorators to many methods at once

Object serialization

Object-relational mapping

Object-based persistence

Implementing special methods at the class level

Implementing class features found in other languages, such as traits and aspect-oriented programming

Class metaprogramming can also help with performance issues in some cases, by performing tasks at import time that otherwise would execute repeatedly at runtime.

To wrap up, let’s recall Alex Martelli’s final advice from his essay “Waterfowl and ABCs”:

And, don’t define custom ABCs (or metaclasses) in production code… if you feel the urge to do so, I’d bet it’s likely to be a case of “all problems look like a nail”-syndrome for somebody who just got a shiny new hammer—you (and future maintainers of your code) will be much happier sticking with straightforward and simple code, eschewing such depths.

I believe Martelli’s advice applies not only to ABCs and metaclasses, but also to class hierarchies, operator overloading, function decorators, descriptors, class decorators, and class builders using __init_subclass__.

Those powerful tools exist primarily to support library and framework development. Applications naturally should use those tools, as provided by the Python standard library or external packages. But implementing them in application code is often premature abstraction.

Good frameworks are extracted, not invented.18

David Heinemeier Hansson, creator of Ruby on Rails

Chapter Summary
This chapter started with an overview of attributes found in class objects, such as __qualname__ and the __subclasses__() method. Next, we saw how the type built-in can be used to construct classes at runtime.

The __init_subclass__ special method was introduced, with the first iteration of a Checked base class designed to replace attribute type hints in user-defined subclasses with Field instances that apply constructors to enforce the type of those attributes at runtime.

The same idea was implemented with a @checked class decorator that adds features to user-defined classes, similar to what __init_subclass__ allows. We saw that neither __init_subclass__ nor a class decorator can dynamically configure __slots__, because they operate only after a class is created.

The concepts of “import time” and “runtime” were clarified with experiments showing the order in which Python code is executed when modules, descriptors, class decorators, and __init_subclass__ is involved.

Our coverage of metaclasses began with an overall explanation of type as a metaclass, and how user-defined metaclasses can implement __new__ to customize the classes it builds. We then saw our first custom metaclass, the classic MetaBunch example using __slots__. Next, another evaluation time experiment demonstrated how the __prepare__ and __new__ methods of a metaclass are invoked earlier than __init_subclass__ and class decorators, providing opportunities for deeper class customization.

The third iteration of a Checked class builder with Field descriptors and custom __slots__ configuration was presented, followed by some general considerations about metaclass usage in practice.

Finally, we saw the AutoConst hack invented by João S. O. Bueno, based on the cunning idea of a metaclass with __prepare__ returning a mapping that implements __missing__. In less than 20 lines of code, autoconst.py showcases the power of combining Python metaprogramming techniques

I haven’t yet found a language that manages to be easy for beginners, practical for professionals, and exciting for hackers in the way that Python is. Thanks, Guido van Rossum and everybody else who makes it so.

Further Reading
Caleb Hattingh—a technical reviewer of this book—wrote the autoslot package, providing a metaclass to automatically create a __slots__ attribute in a user-defined class by inspecting the bytecode of __init__ and finding all assignments to attributes of self. It’s useful and also an excellent example to study: only 74 lines of code in autoslot.py, including 20 lines of comments explaining the most difficult parts.

The essential references for this chapter in the Python documentation are “3.3.3. Customizing class creation” in the “Data Model” chapter of The Python Language Reference, which covers __init_subclass__ and metaclasses. The type class documentation in the “Built-in Functions” page, and “4.13. Special Attributes” of the “Built-in Types” chapter in the The Python Standard Library are also essential reading.

In the The Python Standard Library, the types module documentation covers two functions added in Python 3.3 that simplify class metaprogramming: types.new_class and types.prepare_class.

Class decorators were formalized in PEP 3129—Class Decorators, written by Collin Winter, with the reference implementation authored by Jack Diederich. The PyCon 2009 talk “Class Decorators: Radically Simple” (video), also by Jack Diederich, is a quick introduction to the feature. Besides @dataclass, an interesting—and much simpler—example of a class decorator in Python’s standard library is functools.total_ordering that generates special methods for object comparison.

For metaclasses, the main reference in Python’s documentation is PEP 3115—Metaclasses in Python 3000, in which the __prepare__ special method was introduced.

Python in a Nutshell, 3rd ed., by Alex Martelli, Anna Ravenscroft, and Steve Holden, is authoritative, but was written before PEP 487—Simpler customization of class creation came out. The main metaclass example in that book—MetaBunch—is still valid, because it can’t be written with simpler mechanisms. Brett Slatkin’s Effective Python, 2nd ed. (Addison-Wesley) has several up-to-date examples of class building techniques, including metaclasses.

To learn about the origins of class metaprogramming in Python, I recommend Guido van Rossum’s paper from 2003, “Unifying types and classes in Python 2.2”. The text applies to modern Python as well, as it covers what were then called the “new-style” class semantics—the default semantics in Python 3—including descriptors and metaclasses. One of the references cited by Guido is Putting Metaclasses to Work: a New Dimension in Object-Oriented Programming, by Ira R. Forman and Scott H. Danforth (Addison-Wesley), a book to which he gave five stars on Amazon.com, adding the following review:

This book contributed to the design for metaclasses in Python 2.2

Too bad this is out of print; I keep referring to it as the best tutorial I know for the difficult subject of cooperative multiple inheritance, supported by Python via the super() function.19

If you are keen on metaprogramming, you may wish Python had the ultimate metaprogramming feature: syntactic macros, as offered in the Lisp family of languages and—more recently—by Elixir and Rust. Syntactic macros are more powerful and less error prone than the primitive code substitution macros in the C language. They are special functions that rewrite source code using custom syntax into standard code before the compilation step, enabling developers to introduce new language constructs without changing the compiler. Like operator overloading, syntactic macros can be abused. But as long as the community understands and manages the downsides, they support powerful and user-friendly abstractions, like DSLs (Domain-Specific Languages). In September 2020, Python core developer Mark Shannon posted PEP 638—Syntactic Macros, advocating just that. A year after it was initially published, PEP 638 was still in draft and there were no ongoing discussions about it. Clearly it’s not a top priority for the Python core developers. I would like to see PEP 638 further discussed and eventually approved. Syntactic macros would allow the Python community to experiment with controversial new features, such as the walrus operator (PEP 572), pattern matching (PEP 634), and alternative rules for evaluating type hints (PEPs 563 and 649) before making permanent changes to the core language. Meanwhile, you can get a taste of syntactic macros with the MacroPy package.

SOAPBOX
I will start the last soapbox in the book with a long quote from Brian Harvey and Matthew Wright, two computer science professors from the University of California (Berkeley and Santa Barbara). In their book, Simply Scheme: Introducing Computer Science (MIT Press), Harvey and Wright wrote:

There are two schools of thought about teaching computer science. We might caricature the two views this way:

The conservative view: Computer programs have become too large and complex to encompass in a human mind. Therefore, the job of computer science education is to teach people how to discipline their work in such a way that 500 mediocre programmers can join together and produce a program that correctly meets its specification.

The radical view: Computer programs have become too large and complex to encompass in a human mind. Therefore, the job of computer science education is to teach people how to expand their minds so that the programs can fit, by learning to think in a vocabulary of larger, more powerful, more flexible ideas than the obvious ones. Each unit of programming thought must have a big payoff in the capabilities of the program.

Brian Harvey and Matthew Wright, preface to Simply Scheme20

Harvey and Wright’s exaggerated descriptions are about teaching computer science, but they also apply to programming language design. By now, you should have guessed that I subscribe to the “radical” view, and I believe Python was designed in that spirit.

The property idea is a great step forward compared to the accessors-from-the-start approach practically demanded by Java and supported by Java IDEs generating getters/setters with a keyboard shortcut. The main advantage of properties is to let us start our programs simply exposing attributes as public—in the spirit of KISS—knowing a public attribute can become a property at any time without much pain. But the descriptor idea goes way beyond that, providing a framework for abstracting away repetitive accessor logic. That framework is so effective that essential Python constructs use it behind the scenes.

Another powerful idea is functions as first-class objects, paving the way to higher-order functions. Turns out the combination of descriptors and higher-order functions enable the unification of functions and methods. A function’s __get__ produces a method object on the fly by binding the instance to the self argument. This is elegant.21

Finally, we have the idea of classes as first-class objects. It’s an outstanding feat of design that a beginner-friendly language provides powerful abstractions such as class builders, class decorators, and full-fledged, user-defined metaclasses. Best of all, the advanced features are integrated in a way that does not complicate Python’s suitability for casual programming (they actually help it, under the covers). The convenience and success of frameworks such as Django and SQLAlchemy owe much to metaclasses. Over the years, class metaprogramming in Python is becoming simpler and simpler, at least for common use cases. The best language features are those that benefit everyone, even if some Python users are not aware of them. But they can always learn and create the next great library.

I look forward to learning about your contributions to the Python community and ecosystem!

1 Quote from Chapter 2, “Expression” of The Elements of Programming Style, 2nd ed. (McGraw-Hill), page 10.

2 That doesn’t mean PEP 487 broke code that used those features. It just means that some code that used class decorators or metaclasses prior to Python 3.6 can now be refactored to use plain classes, resulting in simpler and possibly more efficient code.

3 Thanks to my friend J. S. O. Bueno for contributing to this example.

4 I did not add type hints to the arguments because the actual types are Any. I put the return type hint because otherwise Mypy will not check inside the method.

5 That’s true for any object, except when its class overrides the __str__ or __repr__ methods inherited from object with broken implementations.

6 This solution avoids using None as a default. Avoiding null values is a good idea. They are hard to avoid in general, but easy in some cases. In Python as well as SQL, I prefer to represent missing data in a text field with an empty string instead of None or NULL. Learning Go reinforced this idea: variables and struct fields of primitive types in Go are initialized by default with a “zero value.” See “Zero values” in the online Tour of Go if you are curious.

7 I believe that callable should be made suitable for type hinting. As of May 6, 2021, this is an open issue.

8 As mentioned in “Loops, Sentinels, and Poison Pills”, the Ellipsis object is a convenient and safe sentinel value. It has been around for a long time, but recently people are finding more uses for it, as we see in type hints and NumPy.

9 The subtle concept of an overriding descriptor was explained in “Overriding Descriptors”.

10 This rationale appears in the abstract of PEP 557–Data Classes to explain why it was implemented as a class decorator.

11 Contrast with the import statement in Java, which is just a declaration to let the compiler know that certain packages are required.

12 I’m not saying opening a database connection just because a module is imported is a good idea, only pointing out it can be done.

13 Message to comp.lang.python, subject: “Acrimony in c.l.p.”. This is another part of the same message from December 23, 2002, quoted in the Preface. The TimBot was inspired that day.

14 The authors kindly gave me permission to use their example. MetaBunch first appeared in a message posted by Martelli in the comp.lang.python group on July 7, 2002, with the subject line “a nice metaclass example (was Re: structs in python)”, following a discussion about record-like data structures in Python. Martelli’s original code for Python 2.2 still runs after a single change: to use a metaclass in Python 3, you must use the metaclass keyword argument in the class declaration, e.g., Bunch(metaclass=MetaBunch), instead of the older convention of adding a __metaclass__ class-level attribute.

15 In the first edition of Fluent Python, the more advanced versions of the LineItem class used a metaclass just to set the storage name of the attributes. See the code in the metaclasses of bulkfood in the first edition code repository.

16 If you just got dizzy considering the implications of multiple inheritance with metaclasses, good for you. I’d stay way from this solution as well.

17 I made a living writing Django code for a few years before I decided to study how Django’s model fields were implemented. Only then I learned about descriptors and metaclasses.

18 The phrase is widely quoted. I found an early direct quote in a post in DHH’s blog from 2005.

19 I bought a used copy and found it a very challenging read.

20 See p. xvii. Full text available at Berkeley.edu.

21 Machine Beauty: Elegance and the Heart of Technology by David Gelernter (Basic Books) opens with an intriguing discussion of elegance and aesthetics in works of engineering, from bridges to software. The later chapters are not great, but the opening is worth the price.


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


Afterword
Index
About the Author
23h 31m remaining
Index
Symbols
!= (not equal to) operator, Rich Comparison Operators
!r conversion field, String Representation
% (modulo) operator, What’s New in This Chapter, String Representation
%r placeholder, String Representation
* (star) operator, Emulating Numeric Types, Using * to Grab Excess Items-Unpacking with * in Function Calls and Sequence Literals, Using + and * with Sequences-A += Assignment Puzzler, From Positional to Keyword-Only Parameters, Overloading * for Scalar Multiplication-Overloading * for Scalar Multiplication
** (double star) operator, Unpacking Mappings, From Positional to Keyword-Only Parameters
*= (star equals) operator, Augmented Assignment with Sequences-A += Assignment Puzzler, Augmented Assignment Operators-Augmented Assignment Operators
*_ symbol, Pattern Matching with Sequences
*_new*_, Flexible Object Creation with __new__-Flexible Object Creation with __new__
+ operator, Emulating Numeric Types, Using + and * with Sequences-A += Assignment Puzzler, Overloading + for Vector Addition-Overloading + for Vector Addition
+= (addition assignment) operator, Augmented Assignment with Sequences-A += Assignment Puzzler, Augmented Assignment Operators-Augmented Assignment Operators
+ELLIPSIS directive, A Pythonic Card Deck
:= (Walrus operator), List Comprehensions and Readability
< (less than) operator, Rich Comparison Operators
<= (less than or equal to) operator, Rich Comparison Operators
== (equality) operator, Identity, Equality, and Aliases, Further Reading, Rich Comparison Operators
> (greater than) operator, Rich Comparison Operators
>= (greater than or equal to) operator, Rich Comparison Operators
@ sign, Using @ as an Infix Operator-Using @ as an Infix Operator
@asyncio.coroutine decorator, A Few Definitions
@cached_property, Step 5: Caching Properties with functools
@contextmanager decorator, Using @contextmanager-Using @contextmanager
@dataclass
default settings, More About @dataclass
example using, @dataclass Example: Dublin Core Resource Record-@dataclass Example: Dublin Core Resource Record
field options, Field Options-Field Options
init-only variables, Initialization Variables That Are Not Fields
keyword parameters accepted by, More About @dataclass
post-init processing, Post-init Processing-Post-init Processing
typed class attributes, Typed Class Attributes
__hash__ method, More About @dataclass
@typing.overload decorator, Overloaded Signatures-Takeaways from Overloading max
[] (square brackets), A Pythonic Card Deck, List Comprehensions and Readability, Unpacking Sequences and Iterables, Multidimensional Slicing and Ellipsis
\ (backslash), List Comprehensions and Readability
\ line continuation escape, List Comprehensions and Readability
\N{} (Unicode literals escape notation), Beware of Encoding Defaults
_ symbol, Pattern Matching with Sequences
__ (double underscore), The Python Data Model
__abs__, Emulating Numeric Types
__add__, Emulating Numeric Types
__bool__, Boolean Value of a Custom Type
__bytes__, Object Representations
__call__, Further Reading
__class__, Special Attributes that Affect Attribute Handling, Classes as Objects
__contains__, A Pythonic Card Deck, The __missing__ Method
__delattr__, Special Methods for Attribute Handling
__delete__, Attribute Descriptors
__del__, del and Garbage Collection
__dict__, Special Attributes that Affect Attribute Handling
__dir__, Special Methods for Attribute Handling
__enter__, Context Managers and with Blocks
__eq__, Vector Take #4: Hashing and a Faster ==-Vector Take #4: Hashing and a Faster ==
__exit__, Context Managers and with Blocks
__format__, Object Representations, Formatted Displays, Vector Take #5: Formatting-Vector Take #5: Formatting, Further Reading
__getattribute__, Special Methods for Attribute Handling
__getattr__, Vector Take #3: Dynamic Attribute Access-Vector Take #3: Dynamic Attribute Access, Special Methods for Attribute Handling
__getitem__, A Pythonic Card Deck-A Pythonic Card Deck, Multidimensional Slicing and Ellipsis, Vector Take #2: A Sliceable Sequence-A Slice-Aware __getitem__
__get__, Attribute Descriptors
__hash__, More About @dataclass, Vector Take #4: Hashing and a Faster ==-Vector Take #4: Hashing and a Faster ==
__iadd__, Augmented Assignment with Sequences
__init_subclass__, Introducing __init_subclass__-Why __init_subclass__ Cannot Configure __slots__
__init__, How Special Methods Are Used, Post-init Processing, Vector Take #1: Vector2d Compatible
__invert__, Unary Operators
__iter__, Sentence Classes with __iter__-How a Generator Works
__len__, A Pythonic Card Deck-A Pythonic Card Deck, Why len Is Not a Method, Vector Take #2: A Sliceable Sequence-A Slice-Aware __getitem__
__missing__, The __missing__ Method-Inconsistent Usage of __missing__ in the Standard Library
__mro__, Classes as Objects
__mul__, Emulating Numeric Types
__name__, Classes as Objects
__neg__, Unary Operators
__post_init__, Post-init Processing
__pos__, Unary Operators
__prepare__, A Metaclass Hack with __prepare__-A Metaclass Hack with __prepare__
__repr__, Emulating Numeric Types-String Representation, Object Representations, Vector Take #1: Vector2d Compatible
__setattr__, Special Methods for Attribute Handling
__setitem__, Multidimensional Slicing and Ellipsis
__set__, Attribute Descriptors
__slots__, Saving Memory with __slots__-Summarizing the Issues with __slots__, Vector Take #3: Dynamic Attribute Access, Special Attributes that Affect Attribute Handling, Why __init_subclass__ Cannot Configure __slots__
__str__, String Representation, Object Representations
{} (curly brackets), List Comprehensions and Readability
ǀ (pipe) operator, Merging Mappings with |, Using OR-patterns
ǀ= (pipe equals) operator, Merging Mappings with |
… (ellipsis), A Pythonic Card Deck, Multidimensional Slicing and Ellipsis
A
abc.ABC class, ABCs in the Standard Library
abc.Iterable, abc.Iterable versus abc.Sequence
abc.Sequence, abc.Iterable versus abc.Sequence
ABCs (abstract base classes)
ABC syntax details, ABC Syntax Details
defining and using ABCs, Defining and Using an ABC-Defining and Using an ABC
further reading on, Further Reading
goose typing and, Goose Typing-Goose Typing
overview of, Chapter Summary
in Python standard library, ABCs in the Standard Library-ABCs in the Standard Library
Soapbox discussion, Further Reading-Further Reading
structural typing with, Structural Typing with ABCs-Structural Typing with ABCs
subclassing ABCs, Subclassing an ABC-Subclassing an ABC, Subclassing an ABC-Subclassing an ABC
type hints (type annotations), Abstract Base Classes-The fall of the numeric tower
UML class diagrams, Collection API-Collection API
usage of register, Usage of register in Practice
virtual subclasses of ABCs, A Virtual Subclass of an ABC-A Virtual Subclass of an ABC
abs built-in function, Emulating Numeric Types
actual type parameters, Basic Jargon for Generic Types
addition assignment (+=) operator, Augmented Assignment with Sequences-A += Assignment Puzzler, Augmented Assignment Operators-Augmented Assignment Operators
aliasing, Identity, Equality, and Aliases-The Relative Immutability of Tuples
anonymous functions, Anonymous Functions, Further Reading, Closures
Any type, The Any Type-Subtype-of versus consistent-with
AnyStr, The AnyStr predefined type variable
.append method, Deques and Other Queues
apply function, Higher-Order Functions-Modern Replacements for map, filter, and reduce
arguments
freezing with functools.partial, Freezing Arguments with functools.partial
key argument, Further Reading
keyword-only arguments, From Positional to Keyword-Only Parameters
arrays, Overview of Built-In Sequences, Arrays-Arrays
as keyword, Pattern Matching with Sequences
assignment expression (:=), List Comprehensions and Readability
asynchronous generators, The Nine Flavors of Callable Objects, A Few Definitions
asynchronous programming
asynchronous context managers, Asynchronous Context Managers-Asynchronous Context Managers
asyncio script example, An asyncio Example: Probing Domains-Guido’s Trick to Read Asynchronous Code
avoiding CPU-bound traps, Avoiding CPU-Bound Traps
awaitables, New Concept: Awaitable
benefits of, Running Circles Around Blocking Calls
Curio project, async Beyond asyncio: Curio-async Beyond asyncio: Curio
delegating tasks to executors, Delegating Tasks to Executors-Delegating Tasks to Executors
enhancing asyncio downloader, Enhancing the asyncio Downloader-Making Multiple Requests for Each Download
further reading on, Further Reading
iteration and iterables, Asynchronous Iteration and Asynchronous Iterables-Asynchronous comprehensions
myth of I/O-bound systems, The Myth of I/O-Bound Systems
overview of, Chapter Summary
relevant terminology, A Few Definitions
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
topics covered, Asynchronous Programming
type hinting asynchronous objects, Type Hinting Asynchronous Objects
writing asyncio servers, Writing asyncio Servers-An asyncio TCP Server
Asynchronous Server Gateway Interface (ASGI), WSGI Application Servers
asyncio package
achieving peak performance with, The All-or-Nothing Problem
documentation, Asynchronous Programming
downloading with, Downloading with asyncio and HTTPX-The All-or-Nothing Problem
enhancing asyncio downloader, Enhancing the asyncio Downloader-Making Multiple Requests for Each Download
example script, An asyncio Example: Probing Domains-Guido’s Trick to Read Asynchronous Code
queue implementation by, Deques and Other Queues
writing asyncio servers, Writing asyncio Servers-An asyncio TCP Server
asyncpg, Asynchronous Context Managers
attribute descriptors (see also attributes; dynamic attributes and properties)
attribute validation, Descriptor Example: Attribute Validation-LineItem Take #5: A New Descriptor Type
descriptor docstring and overriding deletion, Descriptor Docstring and Overriding Deletion
descriptor usage tips, Descriptor Usage Tips-Descriptor Usage Tips
further reading on, Further Reading
methods as descriptors, Methods Are Descriptors-Methods Are Descriptors
overriding versus nonoverriding, Step 5: Caching Properties with functools, Overriding Versus Nonoverriding Descriptors-Overwriting a Descriptor in the Class
overview of, Chapter Summary
purpose of, Attribute Descriptors
relevant terminology, Terms to understand descriptors
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
topics covered, Attribute Descriptors
attributes (see also attribute descriptors; dynamic attributes and properties)
dynamic attribute access, Vector Take #3: Dynamic Attribute Access-Vector Take #3: Dynamic Attribute Access
handling attribute deletion, Handling Attribute Deletion
overriding class attributes, Overriding Class Attributes-Overriding Class Attributes
private and protected, Private and “Protected” Attributes in Python-Private and “Protected” Attributes in Python
properties and up-front costs, Further Reading
safety versus security in private, Further Reading
using attribute descriptors for validation, Descriptor Example: Attribute Validation-LineItem Take #5: A New Descriptor Type
using properties for attribute validation, Using a Property for Attribute Validation-LineItem Take #2: A Validating Property
virtual attributes, Dynamic Attributes and Properties
augmented assignment operators, Augmented Assignment with Sequences-A += Assignment Puzzler, Augmented Assignment Operators-Augmented Assignment Operators
averages, computing, Example: Coroutine to Compute a Running Average-Example: Coroutine to Compute a Running Average
await keyword, New Concept: Awaitable
B
backslash (\), List Comprehensions and Readability
behavioral subtyping, Subtype-of versus consistent-with
binary records, parsing with struct, What’s New in This Chapter
binary sequences, Byte Essentials (see also Unicode text versus bytes)
bisect module, list.sort Versus the sorted Built-In
blue tool, A Default Parameter Value
BOMs (byte-order marks), BOM: A Useful Gremlin
bool type, Boolean Value of a Custom Type
Boolean values, custom types and, Boolean Value of a Custom Type
built-in functions, The Nine Flavors of Callable Objects
byte sequences, How to Discover the Encoding of a Byte Sequence (see also Unicode text versus bytes)
bytecode, disassembling, Variable Scope Rules
C
call by sharing, Function Parameters as References
callable objects
nine types of, The Nine Flavors of Callable Objects-The Nine Flavors of Callable Objects
user-defined, User-Defined Callable Types
using iter() with, Using iter with a Callable-Using iter with a Callable
Callable type, Callable
card deck example, A Pythonic Card Deck-A Pythonic Card Deck
Cartesian products, Cartesian Products-Cartesian Products
case folding, Case Folding
chain generator, Reinventing chain
ChainMap, collections.ChainMap
characters
finding Unicode by name, Finding Characters by Name-Finding Characters by Name
numeric meaning of, Numeric Meaning of Characters-Numeric Meaning of Characters
Chardet library, How to Discover the Encoding of a Byte Sequence
cladistics, Goose Typing
class metaprogramming
benefits and drawbacks of, Class Metaprogramming
built-in class factory, type: The Built-In Class Factory
class factory function, A Class Factory Function-A Class Factory Function
classes as objects, Classes as Objects
enhancing classes with class decorators, Enhancing Classes with a Class Decorator-Enhancing Classes with a Class Decorator
further reading on, Further Reading
import time versus runtime, What Happens When: Import Time Versus Runtime-Evaluation Time Experiments
__init_subclass__, Introducing __init_subclass__-Why __init_subclass__ Cannot Configure __slots__
metaclass basics, Metaclasses 101-Metaclass Evaluation Time Experiment
metaclass issues, Metaclasses in the Real World-Metaclasses Should Be Implementation Details
metaclass solution for checkedlib.py, A Metaclass Solution for Checked-A Metaclass Solution for Checked
overview of, Chapter Summary
__prepare__ method, A Metaclass Hack with __prepare__-A Metaclass Hack with __prepare__
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
useful applications of metaclasses, Wrapping Up
classes (see also protocols)
as callable objects, The Nine Flavors of Callable Objects
implementing generic classes, Implementing a Generic Class-Basic Jargon for Generic Types
topics covered, How the Book Is Organized
undocumented classes, Further Reading
classic refactoring strategy, Classic Strategy-Classic Strategy
classmethod decorator, classmethod Versus staticmethod
client codes, Subgenerators with yield from
clock decorators
class-based, A Class-Based Clock Decorator
parameterized, The Parameterized Clock Decorator-The Parameterized Clock Decorator
closures (see decorators and closures)
cls.mro(), Classes as Objects
cls.__bases__, Classes as Objects
cls.__qualname__, Classes as Objects
cls.__subclasses__(), Classes as Objects
code examples, obtaining and using, Using Code Examples
code points, Character Issues, Further Reading
code smells, Data Class Builders, Data Class as a Code Smell-Data Class as Intermediate Representation, Goose Typing
codecs, Basic Encoders/Decoders
Collection API, Collection API-Collection API
collections.abc module
abstract base classes defined in, ABCs in the Standard Library
ChainMap, collections.ChainMap
Counter, collections.Counter
defaultdict and OrderedDict, Overview of Common Mapping Methods, collections.OrderedDict
Mapping and MutableMapping ABCs, Standard API of Mapping Types
multiple inheritance in, ABCs Are Mixins Too
UserDict, Subclassing UserDict Instead of dict
collections.deque class, Deques and Other Queues-Deques and Other Queues
collections.namedtuple, A Pythonic Card Deck, Classic Named Tuples-Classic Named Tuples
Command pattern, The Command Pattern-The Command Pattern
comments and questions, How to Contact Us
comparison operators, Identity, Equality, and Aliases, Rich Comparison Operators-Rich Comparison Operators
computed properties
caching properties with functools, Step 5: Caching Properties with functools-Step 5: Caching Properties with functools
data-driven attribute creation, Step 1: Data-Driven Attribute Creation-Step 1: Data-Driven Attribute Creation
properties that compute values, Computed Properties
property caching, Step 4: Bespoke Property Cache-Step 4: Bespoke Property Cache
property overriding existing attributes, Step 3: Property Overriding an Existing Attribute
property to retrieve linked records, Step 2: Property to Retrieve a Linked Record-Step 2: Property to Retrieve a Linked Record
concatenation, Using + and * with Sequences-A += Assignment Puzzler
concurrency models
basics of concurrency, The Big Picture
benefits of concurrency, Concurrency Models in Python
further reading on, Further Reading-Concurrency and Scalability Beyond Python
Global Interpreter Lock impact, The Real Impact of the GIL-3. Answer for asyncio
Hello World example, A Concurrent Hello World-Supervisors Side-by-Side
indefinite loops and sentinels, Code for the Multicore Prime Checker
multicore processors and, Python in the Multicore World-Distributed Task Queues
overview of, Chapter Summary
process pools, A Homegrown Process Pool-Thread-Based Nonsolution
Python programming concepts, Processes, Threads, and Python’s Infamous GIL-Processes, Threads, and Python’s Infamous GIL
relevant terminology, A Bit of Jargon-A Bit of Jargon
significant changes to, What’s New in This Chapter
Soapbox discussion, Concurrency and Scalability Beyond Python-Concurrency and Scalability Beyond Python
structured concurrency, async Beyond asyncio: Curio
topics covered, Concurrency Models in Python
concurrent executors
concurrent web downloads, Concurrent Web Downloads-Where Are the Futures?
downloads with progress display and error handling, Downloads with Progress Display and Error Handling-Using futures.as_completed
Executor.map, Experimenting with Executor.map-Experimenting with Executor.map
further reading on, Further Reading
launching processes with concurrent.futures, Launching Processes with concurrent.futures-Multicore Prime Checker Redux
overview of, Chapter Summary
purpose of, Concurrent Executors
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
concurrent.futures
downloading with, Downloading with concurrent.futures-Downloading with concurrent.futures
launching processes with, Launching Processes with concurrent.futures-Multicore Prime Checker Redux
consistent-with relationships, Subtype-of versus consistent-with
Container interface, Collection API
container sequences, Overview of Built-In Sequences, Further Reading
contention, A Bit of Jargon
context managers
@contextmanager decorator, Using @contextmanager-Using @contextmanager
asynchronous, Asynchronous Context Managers-Asynchronous Context Managers
asynchronous generators as, Asynchronous generators as context managers
contextlib utilities, The contextlib Utilities
creative uses for, Context Managers and with Blocks
demonstrations of, Context Managers and with Blocks-Context Managers and with Blocks
methods included in interface, Context Managers and with Blocks
parenthesized in Python 3.10, Context Managers and with Blocks
purpose of, Context Managers and with Blocks
contravariance (see variance)
control flow, How the Book Is Organized (see also asynchronous programming; concurrent executors; concurrency models; iterators; generators; with, match, and else blocks)
cooperative multiple inheritance, Multiple Inheritance and Method Resolution Order
copies
deep, Deep and Shallow Copies of Arbitrary Objects-Deep and Shallow Copies of Arbitrary Objects
shallow, Copies Are Shallow by Default-Copies Are Shallow by Default
coroutine objects, Classic Coroutines
coroutines
computing running averages, Example: Coroutine to Compute a Running Average-Example: Coroutine to Compute a Running Average
definition of term, A Bit of Jargon
further reading on, Further Reading
generator-based, A Few Definitions
generic type hints for, Generic Type Hints for Classic Coroutines
Global Interpreter Lock impact, 3. Answer for asyncio
overview of, Chapter Summary
returning values from, Returning a Value from a Coroutine-Returning a Value from a Coroutine
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
spinners (loading indicators) using, Spinner with Coroutines-Experiment: Break the spinner for an insight
topics covered, Iterators, Generators, and Classic Coroutines
types of, A Few Definitions
understanding classic, Classic Coroutines
Counter, collections.Counter
covariance (see variance)
CPU-bound systems, Avoiding CPU-Bound Traps
Curio project, async Beyond asyncio: Curio-async Beyond asyncio: Curio
curly brackets ({}), List Comprehensions and Readability
D
Dask, Data Science
data attributes (see attributes)
data class builders
@dataclass, More About @dataclass-@dataclass Example: Dublin Core Resource Record
classic named tuples, Classic Named Tuples-Classic Named Tuples
data class as code smell, Data Class as a Code Smell-Data Class as Intermediate Representation
further reading on, Further Reading
main features, Main Features-New class at runtime
overview of, Overview of Data Class Builders-Overview of Data Class Builders, Chapter Summary
pattern matching class instances, Pattern Matching Class Instances-Positional Class Patterns
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
topics covered, Data Class Builders
type hints, Type Hints 101-Inspecting a class decorated with dataclass
typed named tuples, Typed Named Tuples
data descriptors (see overriding descriptors)
data model (see Python Data Model)
data science, Data Science
data structures, How the Book Is Organized (see also data class builders; dictionaries and sets; object references; sequences; Unicode text versus bytes)
data wrangling
with dynamic attributes, Data Wrangling with Dynamic Attributes-Data Wrangling with Dynamic Attributes
flexible object creation, Flexible Object Creation with __new__-Flexible Object Creation with __new__
invalid attribute name problem, The Invalid Attribute Name Problem
JSON-like data, Exploring JSON-Like Data with Dynamic Attributes-Exploring JSON-Like Data with Dynamic Attributes
decimal.Decimal class, Unary Operators
decoding (see also Unicode text versus bytes)
basics of, Basic Encoders/Decoders-Basic Encoders/Decoders
definition of, Character Issues
understanding encode/decode problems, Understanding Encode/Decode Problems-BOM: A Useful Gremlin
decorator-enhanced strategy pattern, Decorator-Enhanced Strategy Pattern-Decorator-Enhanced Strategy Pattern
decorators and closures
classmethod versus staticmethod, classmethod Versus staticmethod
closure basics, Closures-Closures
closures in lis.py, Procedure: A Class Implementing a Closure
decorator basics, Decorators 101-Decorators 101
decorator execution, When Python Executes Decorators
decorator implementation, Implementing a Simple Decorator-How It Works
decorators in Python standard library, Decorators in the Standard Library-Memoization with functools.cache
enhancing classes with class decorators, Enhancing Classes with a Class Decorator-Enhancing Classes with a Class Decorator
further reading on, Further Reading
nonlocal declarations, The nonlocal Declaration-Variable Lookup Logic
overview of, Chapter Summary
parameterized decorators, Parameterized Decorators-A Class-Based Clock Decorator
purpose of, Decorators and Closures
registration decorators, Registration Decorators
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
topics covered, Decorators and Closures
variable scope rules, Variable Scope Rules-Variable Scope Rules
deep copies, Deep and Shallow Copies of Arbitrary Objects-Deep and Shallow Copies of Arbitrary Objects
defaultdict, Overview of Common Mapping Methods, defaultdict: Another Take on Missing Keys
defensive programming, Inserting or Updating Mutable Values, Defensive Programming and “Fail Fast”-Defensive Programming and “Fail Fast”
del statement, del and Garbage Collection-del and Garbage Collection, Handling Attribute Deletion
delegating generators, Subgenerators with yield from
deprecated collection types, Generic Collections
deque (double-ended queue), When a List Is Not the Answer, Deques and Other Queues-Deques and Other Queues
descriptor classes, Terms to understand descriptors
descriptor instances, Terms to understand descriptors
descriptors, Inspecting a typing.NamedTuple, Attribute Descriptors (see also attribute descriptors)
design patterns (see functions, design patterns with first-class)
destructuring, Pattern Matching with Sequences
diacritics, normalization and, Extreme “Normalization”: Taking Out Diacritics-Extreme “Normalization”: Taking Out Diacritics
dictcomps (dict comprehensions), dict Comprehensions
dictionaries and sets
automatic handling of missing keys, Automatic Handling of Missing Keys-Inconsistent Usage of __missing__ in the Standard Library
consequences of how dict works, Practical Consequences of How dict Works
consequences of how set works, Practical Consequences of How Sets Work
dictionary views, Dictionary Views-Dictionary Views
further reading on, Further Reading
immutable mappings, Immutable Mappings
internals of, What’s New in This Chapter
modern dict syntax, Modern dict Syntax-Merging Mappings with |
overview of, Chapter Summary
pattern matching with mappings, Pattern Matching with Mappings-Pattern Matching with Mappings
set operations, Set Operations-Set Operations
set operations on dict views, Set Operations on dict Views
set theory, Set Theory-Set Comprehensions
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
standard API of mapping types, Standard API of Mapping Types-Inserting or Updating Mutable Values
topics covered, Dictionaries and Sets
variations of dict, Variations of dict-Subclassing UserDict Instead of dict
dir([object]) function, Built-In Functions for Attribute Handling
dis module, Variable Scope Rules
displays, formatting, Formatted Displays-Formatted Displays
distributed task queues, Distributed Task Queues
Django generic views mixins, Django Generic Views Mixins-Django Generic Views Mixins
doctest package
documentation, Hands-On Approach
ellipsis in, A Pythonic Card Deck
double star (**) operator, Unpacking Mappings, From Positional to Keyword-Only Parameters
double underscore (__), The Python Data Model
double() function, The Typed double Function-The Typed double Function
Dublin Core Schema, @dataclass Example: Dublin Core Resource Record
duck typing, Overview of Common Mapping Methods, Types Are Defined by Supported Operations, Further Reading, Protocols and Duck Typing, Further Reading, Interfaces, Protocols, and ABCs, Runtime Checkable Static Protocols
dunder methods, The Python Data Model
dynamic attributes and properties
coding property factories, Coding a Property Factory-Coding a Property Factory
computed properties, Computed Properties-Step 5: Caching Properties with functools
data wrangling with dynamic attributes, Data Wrangling with Dynamic Attributes-Flexible Object Creation with __new__
dynamic versus virtual attributes, Dynamic Attributes and Properties
essential attributes and functions for attribute handling, Essential Attributes and Functions for Attribute Handling-Special Methods for Attribute Handling
further reading on, Further Reading
handling attribute deletion, Handling Attribute Deletion
overview of, Chapter Summary
property class, A Proper Look at Properties-Property Documentation
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
using properties for attribute validation, Using a Property for Attribute Validation-LineItem Take #2: A Validating Property
dynamic protocols, Protocols and Duck Typing, Two Kinds of Protocols
dynamic type, The Any Type-Subtype-of versus consistent-with
E
ellipsis (…), A Pythonic Card Deck, Multidimensional Slicing and Ellipsis
else blocks, Do This, Then That: else Blocks Beyond if-Do This, Then That: else Blocks Beyond if
emojis
building, What’s New in This Chapter
console font and, Beware of Encoding Defaults
finding characters by name, Finding Characters by Name-Finding Characters by Name
in the Museum of Modern Art, Further Reading
increasing issues with, Further Reading
UCS-2 versus UTF-16 encoding, Basic Encoders/Decoders
varied support for, Finding Characters by Name
encoding (see also Unicode text versus bytes)
basics of, Basic Encoders/Decoders-Basic Encoders/Decoders
definition of, Character Issues
encoding defaults, Beware of Encoding Defaults-Beware of Encoding Defaults
understanding encode/decode problems, Understanding Encode/Decode Problems-BOM: A Useful Gremlin
equality (==) operator, Identity, Equality, and Aliases, Further Reading, Rich Comparison Operators
error handling, in network I/O, Downloads with Progress Display and Error Handling-Using futures.as_completed
execution units, A Bit of Jargon
Executor.map, Experimenting with Executor.map-Experimenting with Executor.map
executors, delegating tasks to, Delegating Tasks to Executors-Delegating Tasks to Executors (see also concurrent executors)
explicit self argument, Further Reading
F
f-string syntax
benefits of, What’s New in This Chapter
delegation of formatting by, Formatted Displays
string representation using special methods, String Representation
fail-fast philosophy, Inserting or Updating Mutable Values, Vector Take #4: Hashing and a Faster ==, Defensive Programming and “Fail Fast”-Defensive Programming and “Fail Fast”
FastAPI framework, A FastAPI Web Service-A FastAPI Web Service
FIFO (first in, first out), When a List Is Not the Answer, Deques and Other Queues
filter function, Listcomps Versus map and filter, Higher-Order Functions-Modern Replacements for map, filter, and reduce
filtering generator functions, Generator Functions in the Standard Library
first-class functions (see functions, as first-class objects)
first-class objects, Functions as First-Class Objects
flake8 tool, A Default Parameter Value
flat sequences, Overview of Built-In Sequences, Further Reading
flawed typing, Imperfect Typing and Strong Testing
fluentpython.com, Companion Website: fluentpython.com
ForkingMixIn, ThreadingMixIn and ForkingMixIn
formal type parameters, Basic Jargon for Generic Types
format() function, Formatted Displays
forward reference problem, Problems with Annotations at Runtime
free variables, Closures, Procedure: A Class Implementing a Closure
frozenset, Set Theory (see also dictionaries and sets)
function decorators (see decorators and closures)
function parameters, introspection of, What’s New in This Chapter
function-class duality, Further Reading
function-oriented refactoring strategy, Function-Oriented Strategy-Function-Oriented Strategy
functional programming
packages for, Packages for Functional Programming-Freezing Arguments with functools.partial
with Python, Further Reading
functions
abs built-in function, Emulating Numeric Types
dir([object]) function, Built-In Functions for Attribute Handling
disassembling bytecode of, Variable Scope Rules
double() function, The Typed double Function
filter, map, and reduce functions, Listcomps Versus map and filter, Higher-Order Functions
format() function, Formatted Displays
getattr function, Special Methods for Attribute Handling
getattr(object, name[, default]) function, Built-In Functions for Attribute Handling
globals() function, Finding Strategies in a Module
hasattr function, Special Methods for Attribute Handling
higher-order functions, Higher-Order Functions-Modern Replacements for map, filter, and reduce
id() function, Identity, Equality, and Aliases
iter() function, Why Sequences Are Iterable: The iter Function
len() function, A Pythonic Card Deck
map function, Listcomps Versus map and filter
max() function, Max Overload
repr() function, Object Representations
setattr funcion, Special Methods for Attribute Handling
setattr(object, name, value) function, Built-In Functions for Attribute Handling, Built-In Functions for Attribute Handling
single dispatch generic functions, Single Dispatch Generic Functions-Function singledispatch
str() function, String Representation, Object Representations
super() function, Vector Take #3: Dynamic Attribute Access, The super() Function
zip() function, Vector Take #4: Hashing and a Faster ==
functions, as first-class objects (see also decorators and closures)
anonymous functions, Anonymous Functions
callable objects, The Nine Flavors of Callable Objects-The Nine Flavors of Callable Objects
definition of term, Functions as First-Class Objects
flexible parameter handling and, From Positional to Keyword-Only Parameters-Positional-Only Parameters
further reading on, Further Reading
higher-order functions, Higher-Order Functions-Modern Replacements for map, filter, and reduce
overview of, Chapter Summary
packages for functional programming, Packages for Functional Programming-Freezing Arguments with functools.partial
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
topics covered, How the Book Is Organized
treating functions like objects, Treating a Function Like an Object-Treating a Function Like an Object
user-defined callable types, User-Defined Callable Types
functions, design patterns with first-class
Command pattern, The Command Pattern-The Command Pattern
decorator-enhanced strategy pattern, Decorator-Enhanced Strategy Pattern-Decorator-Enhanced Strategy Pattern
dynamic languages and, Design Patterns with First-Class Functions
further reading on, Further Reading
overview of, Chapter Summary
refactoring strategies, Case Study: Refactoring Strategy-Finding Strategies in a Module
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
functions, type hints in
annotating positional only and variadic parameters, Annotating Positional Only and Variadic Parameters
benefits and drawbacks of, Type Hints in Functions
flawed typing and strong testing, Imperfect Typing and Strong Testing
further reading on, Further Reading
gradual typing, About Gradual Typing-Using None as a Default
overview of, Chapter Summary
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
supported operations and, Types Are Defined by Supported Operations-Types Are Defined by Supported Operations
topics covered, Type Hints in Functions
types usable in annotations, Types Usable in Annotations-NoReturn
functools module
caching properties with, Step 5: Caching Properties with functools-Step 5: Caching Properties with functools
freezing arguments with, Freezing Arguments with functools.partial-Freezing Arguments with functools.partial
functools.cache decorator, Memoization with functools.cache-Memoization with functools.cache
functools.lru_cache function, Using lru_cache
functools.singledispatch decorator, Function singledispatch-Function singledispatch
futures
basics of, Where Are the Futures?-Where Are the Futures?
definition of term, Concurrent Executors
futures.as_completed, Using futures.as_completed-Using futures.as_completed
G
garbage collection, del and Garbage Collection-del and Garbage Collection, Further Reading
generator expressions (genexps), List Comprehensions and Readability, Generator Expressions, Modern Replacements for map, filter, and reduce, When to Use Generator Expressions, Async Comprehensions and Async Generator Expressions-Asynchronous comprehensions
generators
arithmetic progression generators, An Arithmetic Progression Generator-Arithmetic Progression with itertools
asynchronous generator functions, Asynchronous Generator Functions-Asynchronous generators versus native coroutines
examples of, How a Generator Works-How a Generator Works
further reading on, Further Reading
generator functions in Python standard library, The Nine Flavors of Callable Objects, Generator Functions in the Standard Library-Generator Functions in the Standard Library
generator-based coroutines, A Few Definitions
generic iterable types, Generic Iterable Types
humble generators, The Secret of Native Coroutines: Humble Generators
iterable reducing functions, Iterable Reducing Functions-Iterable Reducing Functions
versus iterators, When to Use Generator Expressions
lazy generators, Lazy Sentences-Sentence Take #5: Lazy Generator Expression
overview of, Chapter Summary
Sentence classes with, Sentence Take #3: A Generator Function
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
subgenerators with yield from expression, Subgenerators with yield from-Traversing a Tree
topics covered, Iterators, Generators, and Classic Coroutines
when to use generator expressions, When to Use Generator Expressions
yield keyword, How a Generator Works
generic classes, implementing, Implementing a Generic Class-Basic Jargon for Generic Types
generic collections
parameterized generics and TypeVar, Parameterized Generics and TypeVar-The AnyStr predefined type variable
Soapbox discussion, Further Reading
type annotations and, Generic Collections-Generic Collections
generic functions, single dispatch, Single Dispatch Generic Functions-Function singledispatch
generic mapping types, Generic Mappings
generic static protocols, Implementing a Generic Static Protocol-Implementing a Generic Static Protocol
getattr function, Special Methods for Attribute Handling
getattr(object, name[, default]) function, Built-In Functions for Attribute Handling
gevent library, Experiment: Break the spinner for an insight
Global Interpreter Lock (GIL), NumPy, Processes, Threads, and Python’s Infamous GIL, The Real Impact of the GIL-3. Answer for asyncio, Python in the Multicore World, The GIL
globals() function, Finding Strategies in a Module
goose typing
ABC syntax details, ABC Syntax Details
ABCs in Python standard library, ABCs in the Standard Library-ABCs in the Standard Library
abstract base classes (ABCs), Goose Typing-Goose Typing
defining and using ABCs, Defining and Using an ABC-Defining and Using an ABC
definition of term, Interfaces, Protocols, and ABCs
overview of, Goose Typing
structural typing with ABCs, Structural Typing with ABCs-Structural Typing with ABCs
subclassing ABCs, Subclassing an ABC-Subclassing an ABC, Subclassing an ABC-Subclassing an ABC
usage of register, Usage of register in Practice
virtual subclasses of ABCs, A Virtual Subclass of an ABC-A Virtual Subclass of an ABC
gradual type system (see also type hints (type annotations))
abstract base classes, Abstract Base Classes-The fall of the numeric tower
Any type, The Any Type-The Any Type
basics of, About Gradual Typing
Callable type, Callable
further reading on, Further Reading
generic collections, Generic Collections-Generic Collections
generic mappings, Generic Mappings
implementing generic classes, Implementing a Generic Class-Basic Jargon for Generic Types
implementing generic static protocols, Implementing a Generic Static Protocol-Implementing a Generic Static Protocol
in practice, Gradual Typing in Practice-Using None as a Default
Iterable, Iterable-abc.Iterable versus abc.Sequence
legacy support and deprecated collection types, Generic Collections
NoReturn type, NoReturn
Optional and Union types, Optional and Union Types
overloaded signatures, Overloaded Signatures-Takeaways from Overloading max
overview of, Chapter Summary
parameterized generics and TypeVar, Parameterized Generics and TypeVar-The AnyStr predefined type variable
reading hints at runtime, Reading Type Hints at Runtime-Dealing with the Problem
significant changes to, What’s New in This Chapter
simple types and classes, Simple Types and Classes
Soapbox discussion, Further Reading
static protocols, Static Protocols-Static Protocols
subtype-of versus consistent-with relationships, Subtype-of versus consistent-with-Subtype-of versus consistent-with
topics covered, More About Type Hints
tuple types, Tuple Types-Tuples as immutable sequences
type casting, Type Casting-Type Casting
TypedDict, TypedDict
variance and, Variance-Variance rules of thumb
greater than (>) operator, Rich Comparison Operators
greater than or equal to (>=) operator, Rich Comparison Operators
greenlet package, Experiment: Break the spinner for an insight
H
hasattr function, Special Methods for Attribute Handling
hash code, versus hash value, What Is Hashable
hash tables, Dictionaries and Sets
hashable, definition of, What Is Hashable
heapq package, Deques and Other Queues
higher-order functions, Higher-Order Functions-Modern Replacements for map, filter, and reduce
HTTPServer class, ThreadingMixIn and ForkingMixIn
HTTPX library, Downloading with asyncio and HTTPX-The All-or-Nothing Problem
humble generators, The Secret of Native Coroutines: Humble Generators
I
I/O (input/output) (see network I/O)
id() function, Identity, Equality, and Aliases
immutable mappings, Immutable Mappings
immutable sequences, Overview of Built-In Sequences
implicit conversion, Unicode Text Versus Bytes
import time versus runtime, When Python Executes Decorators, What Happens When: Import Time Versus Runtime
indefinite loops, Code for the Multicore Prime Checker
infix operators, Operator Overloading, Using @ as an Infix Operator-Wrapping-Up Arithmetic Operators
inheritance and subclassing
best practices, Coping with Inheritance-Tkinter: The Good, the Bad, and the Ugly
further reading on, Further Reading
mixin classes, Mixin Classes-Case-Insensitive Mappings
multiple inheritance and method resolution order, Multiple Inheritance and Method Resolution Order-Multiple Inheritance and Method Resolution Order
overview of, Chapter Summary
real-world examples of, Multiple Inheritance in the Real World-Multiple Inheritance in Tkinter
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
subclassing ABCs, Subclassing an ABC-Subclassing an ABC, Subclassing an ABC-Subclassing an ABC
subclassing built-in types, Subclassing Built-In Types Is Tricky-Subclassing Built-In Types Is Tricky
super() function, The super() Function-The super() Function
topics covered, Inheritance: For Better or for Worse
virtual subclasses of ABCs, A Virtual Subclass of an ABC-A Virtual Subclass of an ABC
input expanding generator functions, Generator Functions in the Standard Library
interfaces (see also goose typing; protocols)
Container interface, Collection API
further reading on, Further Reading
Iterable interface, Collection API, Iterable, Programming Ducks
overview of, Chapter Summary
protocols as informal, Further Reading
role in object-oriented programming, Interfaces, Protocols, and ABCs
significant changes to, What’s New in This Chapter
Sized interface, Collection API
Soapbox discussion, Further Reading-Further Reading
topics covered, The Typing Map
typing map, The Typing Map
ways of defining and using, Interfaces, Protocols, and ABCs
interning, Tricks Python Plays with Immutables
invalid attribute name problem, The Invalid Attribute Name Problem
inverted indexes, Writing asyncio Servers
is operator, Choosing Between == and is, Tricks Python Plays with Immutables
.items method, Set Operations on dict Views
iter() function, Why Sequences Are Iterable: The iter Function-Using iter with a Callable
Iterable interface, Collection API, Iterable-abc.Iterable versus abc.Sequence, Programming Ducks-Python Digs Sequences
iterables
asynchronous, Asynchronous Iteration and Asynchronous Iterables-Asynchronous comprehensions
iterable reducing functions, Iterable Reducing Functions-Iterable Reducing Functions
versus iterators, Iterables Versus Iterators-Iterables Versus Iterators
unpacking, Unpacking Sequences and Iterables-Nested Unpacking
iterators
asynchronous, Asynchronous Iteration and Asynchronous Iterables-Asynchronous comprehensions
further reading on, Further Reading
versus generators, When to Use Generator Expressions
generic iterable types, Generic Iterable Types
iter() function, Why Sequences Are Iterable: The iter Function-Using iter with a Callable
versus iterables, Iterables Versus Iterators-Iterables Versus Iterators
lazy sentences, Lazy Sentences-Sentence Take #5: Lazy Generator Expression
overview of, Chapter Summary
role of, Iterators, Generators, and Classic Coroutines
Sentence classes with __iter__, Sentence Classes with __iter__-How a Generator Works
sequence protocol, A Sequence of Words-A Sequence of Words
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
topics covered, Iterators, Generators, and Classic Coroutines
itertools module, Arithmetic Progression with itertools
J
JSON-like data, Exploring JSON-Like Data with Dynamic Attributes-Exploring JSON-Like Data with Dynamic Attributes
K
key argument, Further Reading
keys
automatic handling of missing, Automatic Handling of Missing Keys-Inconsistent Usage of __missing__ in the Standard Library
converting nonstring keys to str, Subclassing UserDict Instead of dict
hashability, Standard API of Mapping Types
persistent storage for mapping, shelve.Shelf
practical consequences of using dict, Practical Consequences of How dict Works
preserving key insertion order, Collection API, Modern Features Simplify or Replace Metaclasses
sorting multiple, The operator Module
.keys method, Set Operations on dict Views
keyword class patterns, Keyword Class Patterns
keyword-only arguments, From Positional to Keyword-Only Parameters
keywords
as keyword, Pattern Matching with Sequences
await keyword, New Concept: Awaitable
lambda keyword, Anonymous Functions
nonlocal keyword, The nonlocal Declaration-Variable Lookup Logic, (set! …)
reserved keywords, (quote …)
yield keyword, The Nine Flavors of Callable Objects, Don’t Make the Iterable an Iterator for Itself-How a Generator Works, When to Use Generator Expressions, Classic Coroutines, Example: Coroutine to Compute a Running Average, Using @contextmanager
KISS principle, Further Reading, Further Reading, Concurrency and Scalability Beyond Python
L
lambda keyword, Anonymous Functions
lazy sentences, Lazy Sentences-Sentence Take #5: Lazy Generator Expression
Least Recently Used (LRU), Using lru_cache
len() function, A Pythonic Card Deck
less than (<) operator, Rich Comparison Operators
less than or equal to (<=) operator, Rich Comparison Operators
line breaks, List Comprehensions and Readability
lis.py interpreter
Environment class, The Environment
evaluate function, The Evaluator-Catch syntax errors
imports and types, Imports and Types
OR-patterns, Using OR-patterns
parser, The Parser-The Parser
pattern matching in, Pattern Matching Sequences in an Interpreter-Shortcut syntax for function definition
Procedure class, Procedure: A Class Implementing a Closure-Procedure: A Class Implementing a Closure
REPL (read-eval-print-loop), The REPL
Scheme syntax, Scheme Syntax-Scheme Syntax
topics covered, Pattern Matching in lis.py: A Case Study
list comprehensions (listcomps)
asynchronous, Async Comprehensions and Async Generator Expressions-Asynchronous comprehensions
building lists from cartesian products, Cartesian Products
building sequences with, List Comprehensions and Generator Expressions
versus generator expressions, Generator Expressions
local scope within, List Comprehensions and Readability
readability and, List Comprehensions and Readability
syntax tip, List Comprehensions and Readability
versus map and filter functions, Listcomps Versus map and filter, Modern Replacements for map, filter, and reduce
lists
alternatives to, When a List Is Not the Answer-Deques and Other Queues
building lists of lists, Building Lists of Lists
list.sort versus sorted built-in, list.sort Versus the sorted Built-In-list.sort Versus the sorted Built-In
mixed-bag, Further Reading
multiline, List Comprehensions and Readability
shallow copies of, Copies Are Shallow by Default-Copies Are Shallow by Default
versus tuples, Comparing Tuple and List Methods
using tuples as immutable, Tuples as Immutable Lists-Tuples as Immutable Lists
locks, definition of term, A Bit of Jargon
LRU (see Least Recently Used)
M
magic methods, The Python Data Model, Further Reading
managed attributes, Terms to understand descriptors
managed classes, Terms to understand descriptors
managed instances, Terms to understand descriptors
map function, Listcomps Versus map and filter, Higher-Order Functions-Modern Replacements for map, filter, and reduce
mappings
automatic handling of missing keys, Automatic Handling of Missing Keys-Inconsistent Usage of __missing__ in the Standard Library
case-insensitive, Case-Insensitive Mappings-Case-Insensitive Mappings
immutable mappings, Immutable Mappings
mapping generator functions, Generator Functions in the Standard Library
merging, Merging Mappings with |
pattern matching with, Pattern Matching with Mappings-Pattern Matching with Mappings
standard API of mapping types, Standard API of Mapping Types-Inserting or Updating Mutable Values
unpacking, Unpacking Mappings
match blocks (see with, match, and else blocks)
match/case statement, Pattern Matching with Sequences, Pattern Matching with Mappings
mathematical vector operations, Overloading + for Vector Addition
max() function, Max Overload-Takeaways from Overloading max
memoization, Memoization with functools.cache-Memoization with functools.cache
memory, saving with __slots__, Saving Memory with __slots__-Summarizing the Issues with __slots__
memoryview class, Memory Views-Memory Views
metaclasses
basics of, Metaclasses 101-Metaclasses 101
considerations for use, Metaclasses in the Real World-Metaclasses Should Be Implementation Details
customizing classes, How a Metaclass Customizes a Class
definition of term, type: The Built-In Class Factory
example metaclass, A Nice Metaclass Example-A Nice Metaclass Example
metaclass evaluation time experiment, Metaclass Evaluation Time Experiment-Metaclass Evaluation Time Experiment
metaclass solution for checkedlib.py, A Metaclass Solution for Checked-A Metaclass Solution for Checked
useful applications of, Wrapping Up
metaobjects, Further Reading
metaprogramming, How the Book Is Organized (see also attribute descriptors; class metaprogramming; dynamic attributes and properties)
method resolution order (MRO), Multiple Inheritance and Method Resolution Order-Multiple Inheritance and Method Resolution Order
methods, as callable objects, The Nine Flavors of Callable Objects (see also sequences, special methods for; special methods)
Meyer's Uniform Access Principle, Further Reading-Further Reading
Mills & Gizmos Notation (MGN), Terms to understand descriptors
mixin classes, Mixin Classes-Case-Insensitive Mappings
mixin methods, ABCs Are Mixins Too
modulo (%) operator, What’s New in This Chapter, String Representation
monkey-patching, Monkey Patching: Implementing a Protocol at Runtime-Monkey Patching: Implementing a Protocol at Runtime, Further Reading, Overwriting a Descriptor in the Class
MRO (see method resolution order)
multicore processing
data science, Data Science
distributed task queues, Distributed Task Queues
increased availability of, Python in the Multicore World
server-side web/mobile development, Server-Side Web/Mobile Development
system administration, System Administration
WSGI application servers, WSGI Application Servers
multiline lists, List Comprehensions and Readability
multiple inheritance (see also inheritance and subclassing)
method resolution order and, Multiple Inheritance and Method Resolution Order-Multiple Inheritance and Method Resolution Order
real-world examples of, Multiple Inheritance in the Real World-Multiple Inheritance in Tkinter
multiplication, scalar, Emulating Numeric Types, Overloading * for Scalar Multiplication-Overloading * for Scalar Multiplication
multiprocessing package, Deques and Other Queues, Spinner with Processes
mutable objects, Further Reading (see also object references)
mutable parameters, Mutable Types as Parameter Defaults: Bad Idea-Defensive Programming with Mutable Parameters
mutable sequences, Overview of Built-In Sequences
mutable values, inserting or updating, Inserting or Updating Mutable Values-Inserting or Updating Mutable Values
MutableMapping ABC, Standard API of Mapping Types
Mypy type checker, Gradual Typing in Practice-Using None as a Default
my_fmt.format() method, What’s New in This Chapter
N
name mangling, Private and “Protected” Attributes in Python
namedtuple, Classic Named Tuples-Classic Named Tuples
native coroutines
versus asynchronous generators, Asynchronous generators versus native coroutines
definition of term, A Few Definitions
functions defined with async def, The Nine Flavors of Callable Objects
humble generators and, The Secret of Native Coroutines: Humble Generators
network I/O
downloading with asyncio, Downloading with asyncio and HTTPX-The All-or-Nothing Problem
downloading with concurrent.futures, Downloading with concurrent.futures-Downloading with concurrent.futures
downloads with progress display and error handling, Downloads with Progress Display and Error Handling-Using futures.as_completed
enhancing asyncio downloader, Enhancing the asyncio Downloader-Making Multiple Requests for Each Download
essential role of concurrency in, Concurrent Web Downloads-Concurrent Web Downloads
myth of I/O-bound systems, The Myth of I/O-Bound Systems
role of futures, Where Are the Futures?-Where Are the Futures?
sequential download script, A Sequential Download Script-A Sequential Download Script
NFC (see Normalization Form C)
nominal typing, Types Are Defined by Supported Operations
nonlocal keyword, The nonlocal Declaration-Variable Lookup Logic, (set! …)
nonoverriding descriptors, Step 5: Caching Properties with functools, Overriding Versus Nonoverriding Descriptors-Overwriting a Descriptor in the Class
NoReturn type, NoReturn
Normalization Form C (NFC), Normalizing Unicode for Reliable Comparisons
normalized text matching, Utility Functions for Normalized Text Matching-Extreme “Normalization”: Taking Out Diacritics
not equal to (!=) operator, Rich Comparison Operators
numbers ABCs, The numbers ABCs and Numeric Protocols-The numbers ABCs and Numeric Protocols
numbers package, The fall of the numeric tower
numeric protocols, The numbers ABCs and Numeric Protocols-The numbers ABCs and Numeric Protocols
numeric tower, The fall of the numeric tower
numeric types
checking for convertibility, Runtime Checkable Static Protocols, The numbers ABCs and Numeric Protocols
emulating using special methods, Emulating Numeric Types-Emulating Numeric Types
hashability of, What Is Hashable
support for, The numbers ABCs and Numeric Protocols
NumPy, NumPy-NumPy
O
object references
aliasing, Identity, Equality, and Aliases-The Relative Immutability of Tuples
deep copies, Deep and Shallow Copies of Arbitrary Objects-Deep and Shallow Copies of Arbitrary Objects
del and garbage collection, del and Garbage Collection-del and Garbage Collection
distinction between objects and their names, Object References, Mutability, and Recycling
function parameters as references, Function Parameters as References-Defensive Programming with Mutable Parameters
further reading on, Further Reading
immutability and, Tricks Python Plays with Immutables
overview of, Chapter Summary
shallow copies, Copies Are Shallow by Default-Copies Are Shallow by Default
Soapbox discussion, Further Reading
variables as labels versus boxes, Variables Are Not Boxes-Variables Are Not Boxes
objects
callable objects, The Nine Flavors of Callable Objects-The Nine Flavors of Callable Objects, Using iter with a Callable-Using iter with a Callable
first-class, Functions as First-Class Objects
flexible object creation, Flexible Object Creation with __new__-Flexible Object Creation with __new__
mutable, Further Reading
treating functions like, Treating a Function Like an Object-Treating a Function Like an Object
user-defined callable objects, User-Defined Callable Types
operator module, The operator Module-The operator Module
operator overloading
augmented assignment operators, Augmented Assignment Operators-Augmented Assignment Operators
basics of, Operator Overloading 101
further reading on, Further Reading
infix operator method names, Wrapping-Up Arithmetic Operators
infix operators, Operator Overloading
overloading * for scalar multiplication, Overloading * for Scalar Multiplication-Overloading * for Scalar Multiplication
overloading + for vector addition, Overloading + for Vector Addition-Overloading + for Vector Addition
overview of, Chapter Summary
rich comparison operators, Rich Comparison Operators-Rich Comparison Operators
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
topics covered, Operator Overloading
unary operators, Unary Operators-Unary Operators
using @ as infix operator, Using @ as an Infix Operator-Using @ as an Infix Operator
Optional type, Optional and Union Types
OR-patterns, Using OR-patterns
OrderedDict, Overview of Common Mapping Methods, collections.OrderedDict
os functions, str versus bytes in, str Versus bytes in os Functions
overloaded signatures, Overloaded Signatures-Takeaways from Overloading max
overriding descriptors, Step 5: Caching Properties with functools, Properties Override Instance Attributes, Overriding Versus Nonoverriding Descriptors-Overwriting a Descriptor in the Class
P
parallelism, Concurrency Models in Python, A Bit of Jargon
parameterized decorators, Parameterized Decorators-A Class-Based Clock Decorator
parameterized types, Basic Jargon for Generic Types
parameters
annotating positional only and variadic parameters, Annotating Positional Only and Variadic Parameters
introspection of function parameters, What’s New in This Chapter
keyword-only, From Positional to Keyword-Only Parameters
mutable, Mutable Types as Parameter Defaults: Bad Idea-Defensive Programming with Mutable Parameters
parameter passing, Function Parameters as References
positional, From Positional to Keyword-Only Parameters-Positional-Only Parameters
pattern matching
*_ symbol, Pattern Matching with Sequences
destructuring, Pattern Matching with Sequences
in lis.py interpreter, Pattern Matching Sequences in an Interpreter-Shortcut syntax for function definition, Pattern Matching in lis.py: A Case Study-Using OR-patterns
with mappings, Pattern Matching with Mappings-Pattern Matching with Mappings
match/case statement, Pattern Matching with Sequences
pattern matching class instances, Pattern Matching Class Instances-Positional Class Patterns
tuples and lists, Pattern Matching with Sequences
type information, Pattern Matching with Sequences
_ symbol, Pattern Matching with Sequences
patterns (see functions, design patterns with first-class; pattern matching)
pickle module, shelve.Shelf
Pingo library, Immutable Mappings
pipe (ǀ) operator, Merging Mappings with |, Using OR-patterns
pipe equals (ǀ=) operator, Merging Mappings with |
plain text, How to Discover the Encoding of a Byte Sequence, Further Reading
.pop method, Deques and Other Queues
positional class patterns, Positional Class Patterns
positional parameters, From Positional to Keyword-Only Parameters-Positional-Only Parameters
positional patterns, Supporting Positional Pattern Matching
process pools
code for multicore prime checker, Code for the Multicore Prime Checker-Code for the Multicore Prime Checker
example problem, A Homegrown Process Pool
process-based solution, Process-Based Solution
thread-based nonsolution, Thread-Based Nonsolution
understanding elapsed times, Understanding the Elapsed Times
varying process numbers, Experimenting with More or Fewer Processes
processes
definition of term, A Bit of Jargon
launching with concurrent.futures, Launching Processes with concurrent.futures-Multicore Prime Checker Redux
progress displays, Downloads with Progress Display and Error Handling-Using futures.as_completed
Project Jupyter, Data Science
proper tail calls (PTC), Further Reading-Further Reading
properties (see computed properties; dynamic attributes and properties)
property class, A Proper Look at Properties-Property Documentation
protocol classes, Protocols and Duck Typing
Protocol type, Static Protocols-Static Protocols
protocols (see also interfaces)
defensive programming, Defensive Programming and “Fail Fast”-Defensive Programming and “Fail Fast”
duck typing and, Protocols and Duck Typing
further reading on, Further Reading
implementing at runtime, Monkey Patching: Implementing a Protocol at Runtime-Monkey Patching: Implementing a Protocol at Runtime
implementing generic static protocols, Implementing a Generic Static Protocol-Implementing a Generic Static Protocol
as informal interfaces, Further Reading
meanings of protocol, Two Kinds of Protocols
numeric, The numbers ABCs and Numeric Protocols-The numbers ABCs and Numeric Protocols
overview of, Chapter Summary
sequence and iterable protocols, Programming Ducks-Python Digs Sequences
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
static protocols, Protocols and Duck Typing, Static Protocols-The numbers ABCs and Numeric Protocols
topics covered, The Typing Map
PSF (see Python Software Foundation)
PUG (see Python Users Group)
PyICU, Sorting with the Unicode Collation Algorithm
PyLadies, Afterword
pytest package, Hands-On Approach
Python
appreciating language-specific features, Preface
approach to learning, Five Books in One-Hands-On Approach
community support for, Afterword
fluentpython.com, Companion Website: fluentpython.com
functional programming with, Further Reading
functioning with multicore processors, Python in the Multicore World-Distributed Task Queues
further reading on, Further Reading
prerequisites to learning, Who This Book Is For
target audience, Who This Book Is Not For
versions featured, Who This Book Is For
Python Data Model
further reading on, Further Reading
__getitem__ and __len__, A Pythonic Card Deck-A Pythonic Card Deck
making len work with custom objects, Why len Is Not a Method
overview of, The Python Data Model, Chapter Summary
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
special methods overview, Overview of Special Methods-Overview of Special Methods
using special methods, How Special Methods Are Used-Collection API
Python Software Foundation (PSF), Afterword
Python type checkers, Gradual Typing in Practice
Python Users Group (PUG), Afterword
python-tulip list, Afterword
Pythonic Card Deck example, A Pythonic Card Deck-A Pythonic Card Deck
Pythonic objects (see also objects)
alternative constructor for, An Alternative Constructor
building user-defined classes, A Pythonic Object
classmethod versus staticmethod, classmethod Versus staticmethod
formatted displays, Formatted Displays-Formatted Displays
further reading on, Further Reading
hashable Vector2d, A Hashable Vector2d-A Hashable Vector2d
object representations, Object Representations
overriding class attributes, Overriding Class Attributes-Overriding Class Attributes
overview of, Chapter Summary
private and protected attributes, Private and “Protected” Attributes in Python-Private and “Protected” Attributes in Python
saving memory with __slots__, Saving Memory with __slots__-Summarizing the Issues with __slots__
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
supporting positional patterns, Supporting Positional Pattern Matching
topics covered, A Pythonic Object
Vector2d class example, Vector Class Redux-Vector Class Redux
Vector2d full listing, Complete Listing of Vector2d, Version 3-Complete Listing of Vector2d, Version 3
Pythonic sums, Further Reading-Further Reading
pyuca library, Sorting Unicode Text, Chapter Summary
Q
quantity properties, Coding a Property Factory-Coding a Property Factory
questions and comments, How to Contact Us
queues
definition of term, A Bit of Jargon
deque (double-ended queue), When a List Is Not the Answer, Deques and Other Queues
distributed task queues, Distributed Task Queues
implementing, Deques and Other Queues
R
race conditions, Code for the Multicore Prime Checker
random.choice function, A Pythonic Card Deck
recycling (see garbage collection)
reduce function, Higher-Order Functions-Modern Replacements for map, filter, and reduce
reducing functions, Vector Take #4: Hashing and a Faster ==, Iterable Reducing Functions-Iterable Reducing Functions
refactoring strategies
choosing the best, Choosing the Best Strategy: Simple Approach
classic, Classic Strategy-Classic Strategy
Command pattern, The Command Pattern-The Command Pattern
decorator-enhanced pattern, Decorator-Enhanced Strategy Pattern-Decorator-Enhanced Strategy Pattern
finding strategies in modules, Finding Strategies in a Module-Finding Strategies in a Module
function-oriented, Function-Oriented Strategy-Function-Oriented Strategy
reference counting, del and Garbage Collection
registration decorators, Registration Decorators, A Parameterized Registration Decorator-A Parameterized Registration Decorator
regular expressions, str versus bytes in, str Versus bytes in Regular Expressions
repr() function, Object Representations
reserved keywords, (quote …)
rich comparison operators, Rich Comparison Operators-Rich Comparison Operators
running averages, computing, Example: Coroutine to Compute a Running Average-Example: Coroutine to Compute a Running Average
S
S-expression, Scheme Syntax
salts, What Is Hashable
Scheme language, Pattern Matching Sequences in an Interpreter-Shortcut syntax for function definition, Scheme Syntax-Scheme Syntax
SciPy, NumPy-NumPy
scope
dynamic scope versus lexical scope, Further Reading-Further Reading
function local scope, Variable Scope Rules
module global scope, Variable Scope Rules
variable scope rules, Variable Scope Rules-Variable Scope Rules
within comprehensions and generator expressions, List Comprehensions and Readability
semaphores, Throttling Requests with a Semaphore-Throttling Requests with a Semaphore
Sentence classes, Sentence Classes with __iter__-How a Generator Works
sentinels, Code for the Multicore Prime Checker
sequence protocol, Programming Ducks-Python Digs Sequences, A Sequence of Words-A Sequence of Words
sequences
alternatives to lists, When a List Is Not the Answer-Deques and Other Queues
further reading on, Further Reading
list comprehensions and generator expressions, List Comprehensions and Generator Expressions-Tuples Are Not Just Immutable Lists
list.sort versus sorted built-in, list.sort Versus the sorted Built-In-list.sort Versus the sorted Built-In
overview of, Chapter Summary
overview of built-in, Overview of Built-In Sequences-Overview of Built-In Sequences
pattern matching with, Pattern Matching with Sequences-Shortcut syntax for function definition
significant changes to, What’s New in This Chapter
slicing, Slicing-Assigning to Slices
Soapbox discussion, Further Reading-Further Reading
topics covered, An Array of Sequences
tuples, Tuples Are Not Just Immutable Lists-Comparing Tuple and List Methods
uniform handling of, An Array of Sequences
unpacking sequences and iterables, Unpacking Sequences and Iterables-Nested Unpacking
using + and * with, Using + and * with Sequences-A += Assignment Puzzler
sequences, special methods for
applications beyond three dimensions, Vector: A User-Defined Sequence Type
dynamic attribute access, Vector Take #3: Dynamic Attribute Access-Vector Take #3: Dynamic Attribute Access
__format__, Vector Take #5: Formatting-Vector Take #5: Formatting
further reading on, Further Reading
__hash__ and __eq__, Vector Take #4: Hashing and a Faster ==-Vector Take #4: Hashing and a Faster ==
overview of, Chapter Summary
protocols and duck typing, Protocols and Duck Typing
significant changes to, What’s New in This Chapter
sliceable sequences, Vector Take #2: A Sliceable Sequence-A Slice-Aware __getitem__
Soapbox discussion, Further Reading-Further Reading
topics covered, Special Methods for Sequences
Vector implementation strategy, Vector: A User-Defined Sequence Type
Vector2d compatibility, Vector Take #1: Vector2d Compatible-Vector Take #1: Vector2d Compatible
sequential.py program, A Homegrown Process Pool
server-side web/mobile development, Server-Side Web/Mobile Development
servers
Asynchronous Server Gateway Interface (ASGI), WSGI Application Servers
HTTPServer class, ThreadingMixIn and ForkingMixIn
TCP servers, An asyncio TCP Server-An asyncio TCP Server
test servers, Downloads with Progress Display and Error Handling
ThreadingHTTPServer class, ThreadingMixIn and ForkingMixIn
Web Server Gateway Interface (WSGI), WSGI Application Servers
writing asyncio servers, Writing asyncio Servers-An asyncio TCP Server
setattr function, Special Methods for Attribute Handling
sets (see also dictionaries and sets)
consequences of how set works, Practical Consequences of How Sets Work
set comprehensions, Set Comprehensions
set literals, Set Literals
set operations, Set Operations-Set Operations
set operations on dict views, Set Operations on dict Views
set theory, Set Theory-Set Theory
shallow copies, Copies Are Shallow by Default-Copies Are Shallow by Default
shelve module, shelve.Shelf
simple class patterns, Simple Class Patterns
single dispatch generic functions, Single Dispatch Generic Functions-Function singledispatch
Sized interface, Collection API
slicing
assigning to slices, Assigning to Slices
excluding last item in, Why Slices and Ranges Exclude the Last Item
multidimensional slicing and ellipses, Multidimensional Slicing and Ellipsis
slice objects, Slice Objects
sliceable sequences, Vector Take #2: A Sliceable Sequence-A Slice-Aware __getitem__
Soapbox sidebars
@dataclass, Further Reading
anonymous functions, Further Reading
__call__, Further Reading
code points, Further Reading
data model versus object model, Further Reading
design patterns, Further Reading
duck typing, Further Reading, Further Reading
dynamic scope versus lexical scope, Further Reading-Further Reading
equality (==) operator, Further Reading
explicit self argument, Further Reading
flat versus container sequences, Further Reading
__format__, Further Reading
function-class duality, Further Reading
functional programming with Python, Further Reading
generic collections, Further Reading
inheritance across languages, Further Reading
interfaces, Further Reading
key argument, Further Reading
lis.py and evaluate function, Further Reading
magic methods, Further Reading
metaobjects, Further Reading
minimalistic iterator interface, Further Reading
mixed-bag lists, Further Reading
monkey-patching, Further Reading
multilevel class hierarchies, Further Reading
mutability, Further Reading
non-ASCII names in source code, Further Reading
object destruction and garbage collection, Further Reading
operator overloading, Further Reading
Oracle, Google, and the Timbot, Further Reading
plain text, Further Reading
pluggable generators, Further Reading-Further Reading
programming language design, Further Reading
proper tail calls (PTC), Further Reading-Further Reading
properties and up-front costs, Further Reading
protocols as informal interfaces, Further Reading
Python decorators and decorator design pattern, Further Reading
Pythonic sums, Further Reading-Further Reading
safety versus security in private attributes, Further Reading
static typing, Further Reading
syntactic sugar, Further Reading
thread avoidance, Further Reading
threads-and-locks versus actor-style programming, Concurrency and Scalability Beyond Python-Concurrency and Scalability Beyond Python
trade-offs of built-ins, Further Reading
tuples, Further Reading
Twisted library, Further Reading
type hints (type annotations), Further Reading-Further Reading
typing map, Further Reading
undocumented classes, Further Reading
Uniform Access Principle, Further Reading-Further Reading
uvloop, Further Reading
variance notation in other classes, Further Reading
with statements, Further Reading
sorted function, list.sort Versus the sorted Built-In-list.sort Versus the sorted Built-In
special methods (see also sequences, special methods for)
advantages of using, A Pythonic Card Deck
Boolean values of custom types, Boolean Value of a Custom Type
calling, How Special Methods Are Used
Collection API, Collection API-Collection API
emulating numeric types, Emulating Numeric Types-Emulating Numeric Types
__getitem__ and __len__, A Pythonic Card Deck-A Pythonic Card Deck
naming conventions, The Python Data Model
purpose of, The Python Data Model
special method names (operators excluded), Overview of Special Methods
special method names and symbols for operators, Overview of Special Methods
string representation, String Representation
spinners (loading indicators) (see also network I/O)
comparing supervisor functions, Supervisors Side-by-Side
created using coroutines, Spinner with Coroutines-Experiment: Break the spinner for an insight
created with multiprocessing package, Spinner with Processes
created with threading, Spinner with Threads-Spinner with Threads
Global Interpreter Lock impact, The Real Impact of the GIL-3. Answer for asyncio
keeping alive, 3. Answer for asyncio
square brackets ([]), A Pythonic Card Deck, List Comprehensions and Readability, Unpacking Sequences and Iterables, Multidimensional Slicing and Ellipsis
stacked decorators, Memoization with functools.cache
star (*) operator, Emulating Numeric Types, Using * to Grab Excess Items-Unpacking with * in Function Calls and Sequence Literals, Using + and * with Sequences-A += Assignment Puzzler, From Positional to Keyword-Only Parameters, Overloading * for Scalar Multiplication-Overloading * for Scalar Multiplication
star equals (*=) operator, Augmented Assignment Operators-Augmented Assignment Operators
static duck typing, Static Protocols, Interfaces, Protocols, and ABCs, Chapter Summary
static protocols
best practices for protocol design, Best Practices for Protocol Design
definition of, Two Kinds of Protocols
designing, Designing a Static Protocol-Designing a Static Protocol
versus dynamic protocols, Protocols and Duck Typing
extending, Extending a Protocol
implementing generic static protocols, Implementing a Generic Static Protocol-Implementing a Generic Static Protocol
limitations of runtime protocol checks, Limitations of Runtime Protocol Checks
numbers ABCS and numeric protocols, The numbers ABCs and Numeric Protocols-The numbers ABCs and Numeric Protocols
runtime checkable, Runtime Checkable Static Protocols-Runtime Checkable Static Protocols
Soapbox discussion, Further Reading
supporting, Supporting a Static Protocol-Supporting a Static Protocol
type hints (type annotations), Static Protocols-Static Protocols
typed double function, The Typed double Function-The Typed double Function
static typing, Interfaces, Protocols, and ABCs
staticmethod decorator, classmethod Versus staticmethod
storage attributes, Terms to understand descriptors
str() function, String Representation, Object Representations
str.format() method, What’s New in This Chapter, Formatted Displays
Strategy pattern, Classic Strategy-Classic Strategy
strings
default sorting of, list.sort Versus the sorted Built-In
dual-mode str and bytes APIs, Dual-Mode str and bytes APIs-str Versus bytes in os Functions
normalizing Unicode for reliable comparisons, Normalizing Unicode for Reliable Comparisons-Extreme “Normalization”: Taking Out Diacritics
representation using special methods, String Representation
strong testing, Imperfect Typing and Strong Testing
struct module, What’s New in This Chapter
structural typing, Structural Typing with ABCs-Structural Typing with ABCs
structured concurrency, async Beyond asyncio: Curio
subclassing (see inheritance and subclassing)
subgenerators, Subgenerators with yield from
subtype-of relationships, Subtype-of versus consistent-with
super() function, Vector Take #3: Dynamic Attribute Access, The super() Function-The super() Function
syntactic sugar, Further Reading
SyntaxError, SyntaxError When Loading Modules with Unexpected Encoding
system administration, System Administration
T
tail call optimization (TCO), Further Reading-Further Reading
TCP servers, An asyncio TCP Server-An asyncio TCP Server
TensorFlow, Data Science
test servers, Downloads with Progress Display and Error Handling
text files, handling, Handling Text Files-Beware of Encoding Defaults (see also Unicode text versus bytes)
ThreadingHTTPServer class, ThreadingMixIn and ForkingMixIn
ThreadingMixIn class, ThreadingMixIn and ForkingMixIn
threads
definition of term, A Bit of Jargon
enhancing asyncio downloader, Using asyncio.as_completed and a Thread-Making Multiple Requests for Each Download
further reading on, Concurrency with Threads and Processes
Global Interpreter Lock impact, 2. Answer for threading
spinners (loading indicators) using, Spinner with Threads-Spinner with Threads
thread avoidance, Further Reading
thread-based process pools, Thread-Based Nonsolution
throttling, Throttling Requests with a Semaphore-Throttling Requests with a Semaphore
Timsort algorithm, Further Reading
Tkinter GUI toolkit
benefits and drawbacks of, Tkinter: The Good, the Bad, and the Ugly
multiple inheritance in, Multiple Inheritance in Tkinter-Multiple Inheritance in Tkinter
tree structures, traversing, Traversing a Tree-Traversing a Tree
tuples
classic named tuples, Classic Named Tuples-Classic Named Tuples
immutability and, Tricks Python Plays with Immutables
as immutable lists, Tuples as Immutable Lists-Tuples as Immutable Lists
versus lists, Comparing Tuple and List Methods
nature of, Further Reading
as records, Tuples as Records-Tuples as Records
relative immutability of, The Relative Immutability of Tuples
simplified memory diagram for, Overview of Built-In Sequences
tuple unpacking, Tuples as Records
type hints (type annotations), Tuple Types-Tuples as immutable sequences
typing.NamedTuple, Typed Named Tuples
Twisted library, Further Reading
type casting, Type Casting-Type Casting
type hints (type annotations)
annotating positional only and variadic parameters, Annotating Positional Only and Variadic Parameters
for asynchronous objects, Type Hinting Asynchronous Objects
basics of, Type Hints 101-Inspecting a class decorated with dataclass
benefits and drawbacks of, Type Hints in Functions
flawed typing and strong testing, Imperfect Typing and Strong Testing
further reading on, Further Reading
generic type hints for coroutines, Generic Type Hints for Classic Coroutines
gradual typing, About Gradual Typing-Using None as a Default (see also gradual type system)
overview of, Chapter Summary
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
supported operations and, Types Are Defined by Supported Operations-Types Are Defined by Supported Operations
topics covered, Type Hints in Functions
types usable in, Types Usable in Annotations-NoReturn
typed double function, The Typed double Function-The Typed double Function
TypedDict, Data Class Builders, TypedDict-TypedDict
Typeshed project, Iterable
TypeVar, Parameterized Generics and TypeVar-The AnyStr predefined type variable
typing map, The Typing Map, Further Reading (see also type hints (type annotations))
typing module, Types Usable in Annotations
typing.NamedTuple, Typed Named Tuples
U
UCA (see Unicode Collation Algorithm)
UCS-2 encoding, Basic Encoders/Decoders
UML class diagrams
ABCs in collections.abc, ABCs in the Standard Library
annotated with MGN, Terms to understand descriptors, A Metaclass Solution for Checked
Command design pattern, The Command Pattern
django.views.generic.base module, Django Generic Views Mixins
django.views.generic.list module, Django Generic Views Mixins
fundamental collection types, Collection API
managed and descriptor classes, LineItem Take #3: A Simple Descriptor
MutableSequence ABC and superclasses, Subclassing an ABC
Sequence ABC and abstract classes, Python Digs Sequences
simplified for collections.abc, Overview of Built-In Sequences
simplified for MutableMapping and superclasses, Standard API of Mapping Types
simplified for MutableSet and superclasses, Set Operations
Strategy design pattern, Classic Strategy
Tkinter Text widget class and superclasses, Multiple Inheritance and Method Resolution Order
TomboList, A Virtual Subclass of an ABC
unary operators, Unary Operators-Unary Operators
undocumented classes, Further Reading
Unicode Collation Algorithm (UCA), Sorting with the Unicode Collation Algorithm
Unicode literals escape notation (\N{}), Beware of Encoding Defaults
Unicode sandwich, Handling Text Files
Unicode text versus bytes
basic encoders/decoders, Basic Encoders/Decoders-Basic Encoders/Decoders
byte essentials, Byte Essentials-Byte Essentials
characters and Unicode standard, Character Issues-Character Issues
dual-mode str and bytes APIs, Dual-Mode str and bytes APIs-str Versus bytes in os Functions
further reading on, Further Reading
handling text files, Handling Text Files-Beware of Encoding Defaults
normalizing Unicode for reliable comparisons, Normalizing Unicode for Reliable Comparisons-Extreme “Normalization”: Taking Out Diacritics
overview of, Chapter Summary
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading
sorting Unicode text, Sorting Unicode Text-Sorting with the Unicode Collation Algorithm
topics covered, Unicode Text Versus Bytes
understanding encode/decode problems, Understanding Encode/Decode Problems-BOM: A Useful Gremlin
Unicode database, The Unicode Database-Numeric Meaning of Characters
UnicodeDecodeError, Coping with UnicodeDecodeError
UnicodeEncodeError, Coping with UnicodeEncodeError
Uniform Access Principle, Further Reading-Further Reading
Union type, Optional and Union Types
unittest module, Hands-On Approach
unpacking
iterables and mappings, From Positional to Keyword-Only Parameters
mapping unpackings, Unpacking Mappings
nested, Nested Unpacking
sequences and iterables, Unpacking Sequences and Iterables
using * to grab excess items, Using * to Grab Excess Items
with * in function calls and sequence literals, Unpacking with * in Function Calls and Sequence Literals
user-defined functions, The Nine Flavors of Callable Objects
UserDict, Subclassing UserDict Instead of dict-Subclassing UserDict Instead of dict
UTF-8 decoding, How to Discover the Encoding of a Byte Sequence
UTF-8-SIG encoding, BOM: A Useful Gremlin
uvloop, Further Reading
V
variable annotations
meaning of, The Meaning of Variable Annotations-Inspecting a class decorated with dataclass
syntax of, Variable Annotation Syntax
variable scope rules, Variable Scope Rules-Variable Scope Rules
variables
free, Closures
init-only variables, Initialization Variables That Are Not Fields
as labels versus boxes, Variables Are Not Boxes-Variables Are Not Boxes
lookup logic, Variable Lookup Logic
variadic parameters, Annotating Positional Only and Variadic Parameters
variance
contravariant types, A Contravariant Trash Can
covariant types, A Covariant Dispenser
in callable types, Variance in Callable types
invariant types, An Invariant Dispenser
overview of, Variance Review
relevance of, Variance
rules of thumb, Variance rules of thumb
variance notation in other classes, Further Reading
vars([object]) function, Built-In Functions for Attribute Handling
Vector class, multidimensional
applications beyond three dimensions, Vector: A User-Defined Sequence Type
dynamic attribute access, Vector Take #3: Dynamic Attribute Access-Vector Take #3: Dynamic Attribute Access
__format__, Vector Take #5: Formatting-Vector Take #5: Formatting
further reading on, Further Reading
__hash__ and __eq__, Vector Take #4: Hashing and a Faster ==-Vector Take #4: Hashing and a Faster ==
implementation strategy, Vector: A User-Defined Sequence Type
overview of, Chapter Summary
protocols and duck typing, Protocols and Duck Typing
sliceable sequences, Vector Take #2: A Sliceable Sequence-A Slice-Aware __getitem__
topics covered, Special Methods for Sequences
Vector2d compatibility, Vector Take #1: Vector2d Compatible-Vector Take #1: Vector2d Compatible
Vector2d
class example, Vector Class Redux-Vector Class Redux
full listing, Complete Listing of Vector2d, Version 3-Complete Listing of Vector2d, Version 3
hashable, A Hashable Vector2d
vectors
overloading + for vector addition, Overloading + for Vector Addition-Overloading + for Vector Addition
representing two-dimensional, Emulating Numeric Types-Emulating Numeric Types
virtual attributes, Dynamic Attributes and Properties
virtual subclasses, A Virtual Subclass of an ABC-A Virtual Subclass of an ABC
W
Walrus operator (:=), List Comprehensions and Readability
weak references, del and Garbage Collection
Web Server Gateway Interface (WSGI), WSGI Application Servers
web/mobile development, Server-Side Web/Mobile Development
with, match, and else blocks
context managers and with blocks, Context Managers and with Blocks-Using @contextmanager
else clause, Do This, Then That: else Blocks Beyond if-Do This, Then That: else Blocks Beyond if
further reading on, Further Reading
overview of, Chapter Summary
pattern matching in lis.py, Pattern Matching in lis.py: A Case Study-Using OR-patterns
purpose of with statements, Context Managers and with Blocks
significant changes to, What’s New in This Chapter
Soapbox discussion, Further Reading-Further Reading
topics covered, with, match, and else Blocks
Y
yield from expression, Subgenerators with yield from-Traversing a Tree
yield keyword, The Nine Flavors of Callable Objects, Don’t Make the Iterable an Iterator for Itself-How a Generator Works, When to Use Generator Expressions, Classic Coroutines, Example: Coroutine to Compute a Running Average, Using @contextmanager
Z
zero-based indexing, Slicing
zip() function, Vector Take #4: Hashing and a Faster ==

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

