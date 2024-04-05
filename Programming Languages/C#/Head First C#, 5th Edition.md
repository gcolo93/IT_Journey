Skip to Content
Topics
Start Learning
Featured
Search 50,000+ courses, events, titles, and more


Head First C#, 5th Edition
1. Start Building apps with C#: Build Something Great…Fast!
2. Variables, Statements, and Methods: Dive into C# code
12h 51m remaining
Chapter 1. Start Building apps with C#: Build Something Great…Fast!
A NOTE FOR EARLY RELEASE READERS
With Early Release ebooks, you get books in their earliest form—the authors’ raw and unedited content as they write—so you can take advantage of these technologies long before the official release of these titles.

This will be the 1st chapter of the final book. Please note that the GitHub repo will be made active later on.

If you have comments about how we might improve the content and/or examples in this book, or if you notice missing material within this chapter, please reach out to the editor at mcronin@oreilly.com.


Want to build great apps…right now?

With C#, you’ve got a modern programming language and a valuable tool at your fingertips. And with Visual Studio, you’ve got an amazing development environment with highly intuitive features that make coding as easy as possible. Not only is Visual Studio a great tool for writing code, it’s also a really effective learning tool for exploring C#. Sound appealing? Let’s get coding!

Why you should learn C#
C# is a simple, modern language that lets you do incredible things. When you learn C#, you’re learning more than just a language. C# unlocks the whole world of .NET, an incredibly powerful open source platform for building all sorts of applications.

So why should you learn C#? There are so many reasons! Here are just a few of them:

 C# is really popular... and for good reason. Microsoft released the first version of C# over 20 years ago, and the C# team been working on it since then—and it shows! They’ve kept it up to date and added lots of new features, which is why it’s one of the most flexible and powerful programming languages in the world.

 You can build many, many, many kinds of apps in C#. C# is really versatile. You can use it to build everything from games to financial and accounting systems to websites to… well, you name it, C# can do it.

 .NET—the framework that powers most C# apps—is cross-platform and open source. In fact, all of the apps that you’ll build in this book will run on Windows and macOS, and many of the apps can even be deployed to Android and iOS mobile devices.

 C# skills are in demand. Are you looking to land a programming job? C# is one of the most in-demand programming languages around, because companies all over the world use C# to build their desktop applications and websites.


Write code and explore C# with Visual Studio
The best way to get started with C# is to write lots of code.

This book uses pictures, puzzles, quizzes, stories, and games to help you learn C# in a way that suits your brain. Every one of those elements is built to help you with a single goal: to keep things interesting while we help you get C# concepts, ideas, and skills into your brain.

This book is also full of C# projects that are specifically designed to give you lots of different ways to explore C# and learn about important ideas and concepts that will help you become a great developer. We designed those projects to be engaging, fun, and interactive to give you lots of opportunities to put those concepts, ideas, and skills into practice.


Visual Studio is your gateway to C#
Learning C# is all about exploring and growing your skills at your own pace—and that’s where Visual Studio comes in. It’s amazing tool built by Microsoft. At its heart, it’s an editor for your C# code and projects, but it’s much more than that. It’s a creative tool that helps you with every aspect of C# development. We’ll use Visual Studio throughout this book as an important tool to to help you learn and explore C#.

Visual Studio is an IDE—that’s short for integrated development environment—is a text editor, visual designer, file manager, debugger…it’s like a multitool for everything you need to write code.

Here are just a few of the things that Visual Studio helps you do:

 It’s a file and project manager. C# projects are often made up of a lot of files. Visual Studio makes it easy to see exactly where they are, and integrates with version control systems like Git to make sure you never lose a line of code.

 It helps you edit and manage your code. Visual Studio has many intuitive features to help you edit your code and C# projects, including powerful AI-driven tools like IntelliSense pop-ups and IntellICode code completion that gives you great suggestions to help keep you in the flow.

 It’s a debugger that lets you see your code in action. When you debug your apps in Visual Studio, you can see exactly what your code is doing while it runs—which is a great way to really understand how C# code works.

IDE TIPS
We’ll often refer to Visual Studio as “the IDE” throughout this book. Keep an eye out for handy IDE tips that help you become a more efficient coder.

Visual Studio is an powerful development environment, and it’s an amazing learning tool to help you explore C#.

Install Visual Studio Community Edition
Open https://visualstudio.microsoft.com/ and download Visual Studio Community Edition. It’s available for both Windows and macOS. The installers look a little different depending on which platform you’re using. Make sue you install the .NET desktop development tools and .NET Multi-platform App UI (or .NET MAUI) development toolols. We’ll be doing 3D game development with Unity, so make sure you check that option on Windows (it’s installed automatically for Mac).



WATCH IT!

Make sure you’re installing Visual Studio, not Visual Studio Code.

Visual Studio Code is an amazing open source, cross-platform code editor, but it’s not tailored to .NET development the way Visual Studio is. That’s why we can use Visual Studio throughout this book as a tool for learning and exploration.

Run Visual Studio
We’re going to jump right into code! So once the installer finishes, run Visual Studio.


RELAX

Grab a cup of coffee—it can take some time for Visual Studio to install.

Don’t worry if it takes a few minutes (or more!) to finish installing Visual Studio. And while we’re on the subject, here’s something else that you don’t have to worry about.

All of the screenshots in this book were taken with Visual Studio 2022 Community Edition, the latest version available while we’re writing it. If Microsoft released a newer version of Visual Studio since we took these screenshots, feel free to try it! The code and ideas that we teach should still work just fine. But if you want the screenshots to match, Microsoft makes older versions of Visual Studio available for download—and you can always install different versions of Visual Studio on the same computer: https://visualstudio.microsoft.com/vs/older-downloads/

If you run into trouble installing Visual Studio, head to our YouTube channel to see videos of the entire installation process: https://www.youtube.com/@headfirstcsharp

NOTE
Keep an eye out for these “relax” boxes—they point out some common issues that a lot of readers run into, so you know they’re coming and don’t have to worry about them.

Create your first project in Visual Studio – Windows edition

The best way to learn C# is to start writing code, so you’re going to write a lot of code—and create a lot of apps!—throughout this book. Each app will get its own project, or a folder that Visual Studio creates with special files to organize all of the code.

 Tell Visual Studio to create a new project.

When you launch Visual Studio, the first thing you’ll see is a “Get started” window with four options. Click “Create a new project” to create a new project.


When you create a new project, Visual Studio will ask you which of its project templates you want to use. Every C# project consists of a set of folders and files. Visual Studio has many built-in templates that it can use to generate different kinds of projects. In this book, you’ll use Visual Studio’s templates to create two kinds of projects, Console App projects and .NET MAUI projects. (You’ll also create Unity projects, but you won’t use Visual Studio to create them.)

GEEK NOTE

You’ll be writing a lot of code throughout this book, which means you’ll be creating a lot of projects. Most of those projects will be Console App projects, just like the one you’re creating now—so you can follow these directions any time you need to create a new Console App project. Just make sure you choose a different project name each time, so that Visual Studio creates the project in a new folder (don’t worry—it will warn you if that name already exists).

NOTE
This applies to both Windows  and Mac  projects! We’ll show you how to create and run an app in Visual Studio for Mac, too.

 Choose a project template for Visual Studio to use.

Visual Studio creates new projects using a template that determines what files to create. Choose the Console App template and click Next.


 Enter a name for your project and click Next.

Your project’s name is important—it determines file and folder names, and you’ll see it inside some of the code that Visual Studio generates for you. If we ask you to pick a specific name, make sure you do, otherwise the code in your project may not match screenshots in the book.


 Make sure you’re using the current version of .NET.

The current version of .NET at the time we’re writing this is 7.0 – make sure the version that you’re using is 7.0 or later. Then click the Create button to create your project.


Once Visual Studio creates your project, it will open a file called Program.cs with this code:


 Run your app.

The app Visual Studio created for you is ready to run. At the top of the Visual Studio IDE, find the button with a green triangle and your app’s name and click it:


 Look at your app’s output.

When you run your program, the Microsoft Visual Studio Debug Console window will pop up and show you the output of the program:


At the top of the window is the output of the program:

Hello World!
Then there’s a line break, followed by some additional text:

C:\path-to-your-project-folder\MyFirstConsoleApp\MyFirstConsoleApp\bin\Debug\net7.0\MyFirstConsoleApp.exe (process ####) exited with code 0.
To automatically close the console when debugging stops, enable Tools->Options->Debugging->Automatically close the console when debugging stops.
Press any key to close this window . . .
You’ll see the same message at the bottom of every Debug Console window. Your program printed a single line of text (Hello World!) and then exited. Visual Studio is keeping the output window open until you press a key to close it so you can see the output before the window disappears.

Press a key to close the window. Then run your program again. This is how you’ll run all of the .NET Core Console App projects that you’ll build throughout the book.

THERE ARE NO DUMB QUESTIONS
Q: So if Visual Studio writes all this code for me, is learning C# just a matter of learning how to use it?

A: No. The IDE is great at automatically generating some code for you, but it can only do so much. There are some things it’s really good at, like setting up good starting points for you, and automatically changing properties of controls in your UI. The most important part of programming—figuring out what your program needs to do and making it do it—is something that no IDE can do for you. Even though the Visual Studio IDE is one of the most advanced development environments out there, it can only go so far. It’s you—not the IDE—who writes the code that actually does the work.

Q: What if the IDE creates code I don’t want in my project?

A: You can change or delete it. The IDE is set up to create code based on the way the element you dragged or added is most commonly used, but sometimes that’s not exactly what you wanted. Everything the IDE does for you—every line of code it creates, every file it adds—can be changed, either manually by editing the files directly or through an easy-to-use interface in the IDE.

Q: Why did you ask me to install Visual Studio Community edition? Are you sure that I don’t need to use one of the versions of Visual Studio that isn’t free in order to do everything in this book?

A: There’s nothing in this book that you can’t do with the free version of Visual Studio (which you can download from Microsoft’s website). The main differences between Community and the other editions aren’t going to stop you from writing C# and creating fully functional, complete applications.

Q: My screen doesn’t look like yours! It’s missing some of the windows, and others are in the wrong place. Did I do something wrong? How can I reset it?

A: If you click on the Reset Window Layout command under the Window menu, the IDE will restore the default window layout for you. Then use the View>>Other Windows menu to open the any windows that are missing. That will make your screen look like the ones in this chapter and throughout the book.

NOTE
Some windows collapse by default. Use the pushpin button in the upper-right corner of the window to make it stay open.

NOTE
Keep an eye out for these Q&A sections. They often answer your most pressing questions, and point out questions other readers are thinking of. In fact, a lot of them are real questions from readers of previous editions of this book!

Visual Studio will generate code you can use as a starting point for your applications. Making sure the app does what it’s supposed to do is entirely up to you.

Create your first project in Visual Studio – Mac edition

The best way to learn C# is to start writing code, so you’re going to write a lot of code—and create a lot of apps!—throughout this book. Each app will get its own project, or a folder that Visual Studio creates with special files to organize all of the code. Follow these steps to create the Console App projects in this book.

 Start creating a new project a new project.

Start up Visual Studio for Mac. When it first starts up, it shows you a window with big buttons to open an existing project or create a new one. Click + New to start creating a new project.


 Choose a project template for Visual Studio to use.

Visual Studio creates new projects using a template that determines what files to create. Click “App” in the “Web and Console” list and choose the Console App template and click Continue.


 Make sure you’re using the current version of .NET.

The current version of .NET at the time we’re writing this is 7.0 – make sure the version that you’re using is 7.0 or later. Click the Continue button.


If Visual Studio gives you an error about Xcode when you try to run your MAUI app, open the Xcode app on your Mac, choose Settings (,) from the Xcode menu, click Locations, and select the highest option from the Command Line Tools dropdown. If it’s blank, open Terminal and run this command: xcode-select --install

 Enter a name for your project and click Create.

Your project’s name is important—it determines file and folder names, and you’ll see it inside some of the code that Visual Studio generates for you. If we ask you to pick a specific name, make sure you do, otherwise the code in your project may not match screenshots in the book.


Once Visual Studio creates your project, open a file called Program.cs that has the code for your new app. You can press the run button  to run the app and view the results in the Terminal window.


Let’s build a game!
You’ve built your first C# app, and that’s great! Now that you’ve done that, let’s build something a little more complex. We’re going to build an animal matching game, where a player is shown 8 pairs of animals and needs to click on them in pairs to make them disappear.

NOTE
The game displays sixteen buttons with eight pairs of matching animals in a random order. You play by clicking animals in pairs: first click one animal, then click its match. Match all eight animals and you win the game!




GAME DESIGN

What is a game?

It may seem obvious what a game is. But think about it for a minute--it’s not as simple as it seems.

* Do all games have a winner? Do they always end? Not necessarily. What about a flight simulator? A game where you design an amusement park? What about a game like The Sims?

* Are games always fun? Not for everyone. Some players like a “grind” where they do the same thing over and over again; others find that miserable.

* Is there always decicion making, conflict, or problem solving? Not in all games. Walking simulators are games where the player just explores in an environment, and there are often no puzzles or conflicts at all.

* It’s actually pretty hard to pin down exactly what a game is. If you read textbooks on game desgin, you’ll find all sorts of compelling definitions. So for our purposes, let’s define the meaning of “game” like this:

A game is a program that lets you play with it in a way that (hopefully) is as entertaining to play as it is to make.

NOTE
Keep an eye out for these “Game design…and beyond” elements scattered throughout the book. We’ll use game design principles as a way to learn and explore important programming concepts and ideas that apply to any kind of project, not just video games.

Break up large projects into smaller parts
Our goal in this book is to help you to learn C#, but we also help you become a great developer, and one of the most important skills great developers work on is tackling large projects. You’ll build a lot of projects throughout this book. They’ll be smaller starting with the next chapter, but they’ll get bigger as you go further. As the projects get bigger, we’ll show you how to break them up into smaller parts that you can work on one after another. This project is no exception—it’s a larger project, like the ones you’ll do later in the book—so you’ll do it in five parts.


If you run into any trouble with this project, you can watch a full video walkthrough on our YouTube channel. https://www.youtube.com/@headfirstcsharp

You can download all of the code and a PDF of this chapter from our GitHub page: https://github.com/head-first-csharp/fifth-edition

RELAX

This chapter is all about learning the basics, getting used to creating projects, editing code, and building your game.

Don’t worry if there are things that you don’t understand yet. By the end of the book, you’ll understand everything that’s going on in this game. For now, just follow the step-by-step instructions to get your game up and running. This will give you a solid foundation to build on later.

Here’s how you’ll build your game
The rest of this chapter will walk you through building your animal matching game. You’ll build it using .NET MAUI (which stands for .NET Multi-platform App UI, or just MAUI). MAUI is a technology that you can use to create apps in C# that run natively as desktop apps on Windows and macOS, or as mobile apps on your Android or iOS mobile devices.

The rest of this chapter will walk you through building your animal matching game, and you’ll be doing it in a series of separate parts:

NOTE
This project can take anywhere from 20 minutes to over an hour, depending on how quickly you type. We learn better when we don’t feel rushed, so give yourself plenty of time.


 First you’ll create a new .NET MAUI project in Visual Studio.

You just created a new console aplication. Now you’ll create a new MAUI app.


 Then you’ll use XAML to design the page.

Individual screens in MAUI apps are called pages. You’ll design them using XAML, a design language you’ll use to define how those pages work.

 You’ll write C# code to add random animal emoji to the page.

When your app first loads, it will run that code to display sixteen buttons with eight pairs of animal emoji in a random order.


 You’ll make the gameplay work.

The game needs to detect when the user clicks on pairs of emoji, keep track of the pairs, and end the game when they’ve found all of the matches. You’ll write that code too.


 Finally, you’ll make the game more exciting by adding a timer.

Your timer will start when the player starts the game, and keep track of how long it takes the player to find all eight pairs of animals.


Create a .NET MAUI project in Visual Studio – Windows edition

You can create a .NET MAUI app in Visual Studio just like you did with the console app at the beginning of the chapter. Open up Visual Studio or choose New >> Project (Ctrl+Shift+N) from the File menu to bring up the “Create a new project” window.


Choose the .NET MAUI App project template and click Next. Visual Studio will prompt you for a project name, just like it did when you created a Console App project.

Enter AnimalMatchingGame as the project name and click Next.


Finally, Visual Studio will ask you to choose a version of .NET – choose the latest version, just like you did when you created the Console App project. Then click the Create button to create your new .NET MAUI project.

Create a .NET MAUI project in Visual Studio – Mac edition

If you’re using Visual Studio for Mac, creating a .NET MAUI App project is really similar to creating the Console App project, just like you did at the beginning of the chapter. Start Visual Studio and click + New – or choose New Project... (N) from the File menu – to bring up the New Project window.


Visual Studio will ask you for the version of .NET, like it did when you created a console app. Choose the latest version and click Continue.


Make sure you enter AnimalMatchingGame as the project name, otherwise your code won’t match the screenshots in the book.

Finally, Visual Studio will ask you for a project name. Enter AnimalMatchingGame, then click the Create button to create your new .NET MAUI project.

Run your new .NET MAUI app
Go ahead and run your new .NET MAUI app. You can click the Run button in the toolbar:


Or you can choose Start Debugging (F5 or ) from the Debug menu.

Visual Studio will build your code, which means converting it to an executable program that your operating system can run. Then it will start your app:


Stop your MAUI app
You can stop your app by closing the app window. You can also choose Stop Debugging (Shift+F5 or ) from the Debug menu, or click the square Stop button in the Visual Studio toolbar.

You can start or stop your app at any time. If there are syntax errors (like typos or invalid keywords) in the C# or XAML code, Visual Studio won’t be able to run the app.

MAUI apps work on all of your devices
MAUI is a cross-platform framework for building visual apps, which means the apps that you build can run on your Android and iOS devices. If you have an Android phone or tablet, for example, you can set it to developer mode, plug it into your computer, and tell Visual Studio to deploy the app straight to your phone. You can do the same thing with your iPhone or iPad, but Apple requires you to join the Apple Developer Program before you can do that—at the time we’re writing this costs USD $99 (although nonprofits, government agencies, and students can get a fee waiver).


You can run MAUI apps on an Android device right from Visual Studio. This page shows you how to set up an Android device so you can connect it to your computer run your MAUI apps on it: https://learn.microsoft.com/en-us/dotnet/maui/android/device/setup

You can also run MAUI apps on your iOS device, but it requires a little more setup—and it costs money, because you need to join the Apple Developer Program. This page walks you through the whole process: https://learn.microsoft.com/en-us/dotnet/maui/ios/device-provisioning/


Many of the chapters in this book include .NET MAUI projects, so you can learn to build interactive apps that can run on computers running Windows or macOS, and mobile devices running Android or iOS.


Here’s the page that you’ll build
When you start a project, the first thing you always want to do is take a few minutes to understand the big picture. What are you going to create? How will it work? Let’s take a look at the page you’re about to build.

When you open an app built with .NET MAUI, the first thing it shows you is a page that you interact with. That page uses controls, or visual widgets like buttons and labels, to create a user interface (or UI) that you can interact with. Here’s the page that you’re going to design:


Start editing your XAML code
When you create your project, Visual Studio opens two tabs to edit code files. One page lets you edit MainPage.xaml, which contains your XAML code. The other lets you edit MainPage.xaml.cs, which has the C# code for your game. Here’s what you’ll see if you’re using Visual Studio for Windows:


Visual Studio for Mac looks a little different, but works exactly the same way.


Add the XAML for a Button and a Label
The first thing we’ll do is Design the page for the game. It will have sixteen buttons to display the animal emoji, plus a “Play again?” button to restart the game when the player wins.


 Delete everything between the opening and closing VerticalStackLayout tags.

XAML is a tag-based markup language. That means your XAML code uses tags to define everything that appears in your app. Here’s an example of a tag—you can find it on line 6 of MainPage.xaml:

<ScrollView>
That’s an opening tag. You can find its matching closing tag on line 39: </ScrollView>

This is a ScrollView. If your app is in a window that’s smaller than its contents, everything between the opening and closing tag can be scrolled up and down.

Find the opening VerticalStackLayout tag. It’s on lines 7 through 10, and it looks like this:

<VerticalStackLayout
     Spacing="25"
     Padding="30,0"
     VerticalOptions="Center">
Next, find the closing VerticalStackLayout tag on line 38:

</VerticalStackLayout>
Now carefully delete all of the lines between those two two tags. The XAML code in your MainPage.xaml file should now look like this:


 Delete the C# code that goes with the XAML that you just deleted.

If you try to run your app right now, Visual Studio will give you an error message and refuse to run it, because the C# code depends on some things that you just deleted. First, find this code on line 12:

private void OnCounterClicked(object sender, EventArgs e)
Delete it, and the next 10 lines of code, up to and including the closing curly brace } on line 22. Be careful not to delete the final closing } on line 24. Then delete the line of code on line 5: int count = 0;

Your C# code should now look like this:

namespace AnimalMatchingGame;

public partial class MainPage : ContentPage
{
      public MainPage()
      {
             InitializeComponent();
      }
}
 Use the Toolbox to add the “Play Again?” button.

You’ll be editing the XAML code again, so switch back to the MainPage.xaml tab. If you don’t see the Toolbox panel, expand it by clicking the tab on the side of the window. Add a few extra blank lines where you deleted the code between the opening and closing VerticalStackLayout tags. Then drag the Button out of the Toolbox and drop it onto tone of the lines that you added.


You should now see a new Button tag between the VerticalStackLayout tags—it’s okay if the spacing or indenting is a little different, because extra spaces or lines don’t matter in XAML:


 Add Properties to the XAML tag for the “Play again?” button.

XAML tags have properties that let you set options to customize how they’re displayed on the page. The Properties window in Visual Studio makes it easier to edit them.

Click on the code for the Button tag in MainPage.xaml, so your cursor is somewhere between the opening < and closing > angle brackets. Then look at the Properties window—it’s usually docked in the lower right corner of Visual Studio. If you don’t see it, choose Properties or Properties Window from the View menu. Make sure it says “Type Button” at the top, so you know that you’re editing the Button.

Find the Text property and set it to Play again?

Then find the FontSize property and set it to Large



When you’re done editing the button, the XAML for it should look like this:

<Button Text="Play again?" FontSize="Large" />
The Button tag now has Text and FontSize properties.

 Edit the XAML code by hand for your button to give it a name.

You can also edit XAML code by hand—for example, if you ran into trouble with the Properties window, you could type the XAML directly into the editor. You need to make sure that you copy all of the brackets, quotes, etc., exactly, otherwise your code won’t run!

In the next part of the project, you’ll write C# code to make your “Play again?” button visible when the game is over, and invisible while the game is running. You’ll give it a name that the C# code can use to tell it to show or hide itself.

Use the editor to add an x:Name property to give your Button a name. It should look like this:

<Button x:Name="PlayAgainButton" Text="Play again?" FontSize="Large" />
XAML tags have properties that let you set options to customize how they’re displayed on the page.

 Add an event handler so your button does something.

When you click a button, it executes C# code called an event handler. Visual Studio makes it easy to add one. Place your mouse cursor just before the /> at the end of the Button tag and start typing Clicked. Visual Studio will pop up an IntelliSense window:


Choose Clicked from the list and either click on it or press Enter. Visual Studio will then show you this:


Press Enter to add a new event handler. Your XAML tag should now look like this:


Switch to the MainPage.xaml.cs tab. You can see the code that Visual Studio added, which looks like this:

private void PlayAgainButton_Clicked(object sender, EventArgs e)
{

}
EXERCISE

Add a Label control to your XAML page.

Go back to the screenshot of the game that shows the “Play again?” button. Notice how it also has text above the button that displays the time elapsed? That’s a Label. It’s up to you to add a tag for it. Here’s what you’ll do:

Switch to the MainPage.xaml tab.

Open the Toolbox and drag a Label into your XAML code. Make sure it gets added directly below the Button, just like you did in Step 3 when you were adding the Button.

Use the Properties window to set the Text button to “Time Elapsed: 0.0 seconds” and the FontSize to “Large” just like you did in Step 4 when you were adding the Button.

Edit the XAML code by hand and set the x:Name to “TimeElapsed” just like you did in Step 5 when you were adding the Button.

NOTE
When you see an Exercise, that’s your chance to get some practice on your own. Make sure you do every exercise—they’re an important part of the book. If an exercise is part of a project, then the project won’t work until you get it right. But don’t worry—we’ll always give you the solution. And if you get stuck, it’s always okay to peek at the solution!

EXERCISE SOLUTION

Add a Label control to your XAML page.

If you followed the steps in the Exercise correctly, your XAML code in MainPage.xaml should now look like this:


The C# code in MainPage.xaml.cs didn’t get modified as part of the Exercise, so it should still look like this:

namespace AnimalMatchingGame;

public partial class MainPage : ContentPage
{
    public MainPage()
    {
        InitializeComponent();
    }

    private void PlayAgainButton_Clicked(object sender, EventArgs e)
    {

    }
}
Make sure that your XAML and C# code matches and your app looks like this screenshot before moving on.

If you run your app now, it should look like this


THERE ARE NO DUMB QUESTIONS
Q: What exactly is a “page” in a MAUI app?

A: A .NET MAUI app is usually built out of one or more pages, or individual screens that different layouts and contain controls like labels and buttons. Some MAUI apps have mutliple pages that let you navigate between them. Your Animal Matching Game app will just have a single page with sixteen animal buttons, a “Play again?” button, and a label to show the elapsed time.

Q: So those buttons and labels are controls?

A: Yes. Everything you see on a MAUI page is a control—including the page itself, which is a ContentPage control. Some controls are dedicated to making your page look a certain way, like the VerticalStackLayout control that causes other controls to be stacked one on top of another. Others, like the Button and Label controls, are there to display some kind of widget that the user can see and interact with. We’ll talk more about controls in the next chapter.

Q: It looks like some controls contain others, like the VerticalStackLayout in my app contains Button and a Label. What’s going on there?

A: When you include layout control like VerticalStackLayout on your page, you can’t actually see it. Its whole purpose is to cause the other controls on the page to be displayed a certain way—in this case, to be stacked on top of each other. You need a way to tell MAUI which other controls on the page you want it to stack. To do that, you nest those other controls inside the VerticalStackLayout by including their tags between its opening <VerticalStackLayout> tag and its closing </VerticalStackLayout> tag.

Q: Why do some tags like <ScrollView> have a closing </ScrollView> tag, but others like <Button> don’t have one?

A: A Button control doesn’t need to have any other controls nested inside of it, so there’s no need for it to have a closing tag—instead, you can just end the tag with /> to make it self-closing.

BRAIN POWER

Your app is looking good so far, but now you need to add some buttons. How do you think you’ll do that? What do you think you’ll have to add to the XAML to get sixteen buttons to be displayed in a layout with four rows of four buttons?

NOTE
These Brain Power boxes are here to give you something to think about. When you see one, don’t just go on to the next section. Take a few minutes and actually think about what you’re being asked. That will really help you get this material into your brain faster!

Use a FlexLayout to make a grid of animal buttons
The XAML for your page currently has three tags that determine its layout: there’s a ContentPage tag on the outside that displays the whole view. It contains a ScrollView—everything nested between its start and end tags will scroll if it goes off the bottom of the page. Inside it is a VerticalStackLayout, which causes everything between its start and end tags to be stacked on top of each other in the order that they appear. Inside all of those tags are self-closing Buton and Label tags.

Now you add a FlexLayout, which arranges anything inside of it in rows, wrapping them to the next row so they all fit inside its total width. You’ll add sixteen Button tags inside the FlexLayout. You’ll get them to display in a 4x4 grid by setting the width of each button to 100 and the width of the FlexLayout to 400, so exactly four buttons will fit on each row.


WARNING! At the time we’re writing this, there’s a bug in the macOS version of .NET MAUI where the FlexLayout’s MaximumWidthRequest property does not work, so you won’t see a nice 4x4 grid like this. 

EXERCISE

This looks like a big exercise! But don’t worry, just take it step by step. We know you can do it! And remember, it’s not cheating to look at the solution… in fact, seeing the solution is a great way to help you learn.

It’s time to finish designing your page. In this exercise, you’ll add a FlexLayout underneath the Label that you added in the last Exercise. Next, you’ll set its properties. Then you’ll add a button. And finally, you’ll copy the XAML for that button and paste it fifteen more times, so you have a total of sixteen buttons on your page.

Add extra space for your FlexLayout control

Take a careful look at the screenshot that we just showed you. It shows you how the whole page works. Now go back to Visual Studio and look at the XAML for your page, and figure out exactly where the FlexLayout should go—just below the <Label ... /> tag.

Now put your cursor at that location and press enter a few times to give yourself space to drag the FlexLayout.

Add the FlexLayout control just below the Label

Open the Toolbox and drag a FlexLayout into your XAML code. Make sure it gets added directly below the Label, into the extra space you just added. It will look like this: <FlexLayout></FlexLayout>

Position your cursor between the > and < in the middle of the XAML you just added and add several extra spaces between the opening and closing tags (you’ll drag a button into that space later in the exercise).

Place your cursor directly on the opening <FlexLayout> tag. Make sure the Properties window shows that the type is FlexLayout.

Use the Properties window to set the Wrap property to Wrap and the MaximumWidthRequest property to 400.

Edit the XAML code by hand and set the x:Name to “AnimalButtons” just like you did in the last Exercise.

Add the first Button inside the FlexLayout

Open the Toolbox and drag a Buton into your XAML code. Make sure it gets added in the space that you addefd between the opening and closing tags of the FlexLayout. It will look like this: <Button Text="" />

Place your cursor inside the Button tag. Make sure the Properties window shows that the type is Button.

Use the Properties window to set the Button’s HeightRequest property to 100, the WidthRequest property to 100, and the FontSize property to 60. The dropdown in the Properties window won’t have numbers—you can either type 60 into the window, or choose Caption from the dropdown list to set the font size.

Edit the XAML for the button and delete the Text property by selecting it in the code editor and pressing delete. Your cursor should now be inside the Button control.

Keep the cursor where it is and edit the XAML code by hand to set the BackgroundColor property to LightBlue and the the BorderColor property to Black. Visual Studio’s IntelliSense pop-up will help you match the colors.

Add a Clicked event handler, just like you did with PlayAgainButton. Choose <New Event Handler> from the dropdown, so it creates a new event handler method in the C# code. Use the default name Button_Clicked.

Add the rest of the Buttons

Copy the <Button ... /> tag that you just added. Then paste 15 identical tags below it. You should now have a total of 16 identical Button tags inside a FlexLayout just below the Label. Run your app—it should match our screenshot.

EXERCISE SOLUTION

It’s time to finish designing your page. In this exercise, you’ll add a FlexLayout underneath the Label that you added in the last Exercise. Next, you’ll set its properties. Then you’ll add a button. And finally, you’ll copy the XAML for that button and paste it fifteen more times, so you have a total of sixteen buttons on your page.

If you followed the steps in the Exercise correctly, your XAML code in MainPage.xaml should now look like this:


It looks like there is a lot of XAML code here! But most of the XAML that you added is the same <Button ... /> tag copied and pasted sixteen times.



That’s right!

Try resizing the window. And make sure that the x:Name properties match the ones in our solution exactly—the C# code you write will use them.



Write C# code to add the animals to the buttons
You started this book to learn C#. You’ve done all the preparation: creating the project, designing the page for your app. Now it’s time to get started writing C# code.

We’ll give you all of the code for this project, and show you exactly where it goes. But the goal is to get you started learning C#, so we’ll also work with you to help you understand how it all works—and that will provide you with a solid foundation to start writing code on your own.

You’ll add code that’s run every time the “Play again?” button is clicked. Here’s what it will do:


Start editing the PlayAgainButton event handler method
When you were writing the XAML code for the “Play again?” button, you added an event handler:


When you did this, Visaul Studio added Clicked="PlayAgainButton_Clicked" to the XAML tag for the button. It also added this C# code to MainPage.xaml.cs:

private void PlayAgainButton_Clicked(object sender, EventArgs e)
{

}
That’s a method. C# code is made up of statements, or specific tasks that you’re telling your app to execute. Those statements are bundled into methods. Methods have a name—this method is named PlayAgainButton_Clicked.

Visual Studio generated that method for you automatically when you added the Clicked event handler to your XAML code to give you a place to add the statements that will tell it what to do when the “Play again?” button is clicked.


Add a C# statement to the event handler method
Place your cursor on the line between the opening { curly bracket and closing } curly bracket of the method. Then start typing the following line of code to make the animal buttons visible:

AnimalButtons.IsVisible = true;

As you’re typing, you’ll see some of Visual Studio’s really powerful tools that help you write code:


Add more statements to your event handler
When the player clicks the “Play again?” button, the app will display the animal buttons, hide the “Play again?” button, and then fill the animal buttons eight pairs of animal emoji in a random order. You’re going to add statements to the PlayAgainButton_Clicked event handler method to do all that.

 Add a statement to make the “Play again?” button invisible.


Do you remember how you used the x:Name property in your XAML code to give names to the “Play again?” button and the FlexLayout that contains the sixteen animal buttons? Take a minute and go back to that XAML code—you’ll you gave the FlexLayout the name AnimalButtons, and you just added a line of code which used that name.

You also used an x:Name to give the “Play again?” button the name PlayAgainButton. Now add a second line of code to your event handler method:


That statement turns the “Play again?” button invisible.

 Make the animal buttons invisible when the app starts.

Take a closer look at the first statement that you added to your event handler method. It turns the FlexLayout that contains the animal buttons visible. But wait a minute—it’s already visible! You saw it when you ran your app. Let’s do something about that.

Go to top of your MainPage.xaml.cs file and find a method that starts public MainPage(). This is a special method that gets executed once while your page is loading. It has a statement in it – InitializeComponent(); – that initializes the page.

Add a statement right after that one to make the animal buttons invisible:


Now your app will make the animal buttons invisible when it starts up. As soon as the player clicks the “Play again?” button to start the game, it will show the animal buttons and hide the “Play again?” button.

 Run your app and make sure it works so far.

When you’re writing code, you don’t just write a complete app from beginning to end, then run it to see if it works. That’s not how it works at all! Writing code is a creative process. There are many, many ways to make your code do a specific thing, and in a lot of cases, the only way you can really be sure you’re happy with it is to try writing it one way—and if you don’t like it, change it.

Plus, it’s easy to make syntax errors in your code. A syntax error means that you wrote something that isn’t valid C# code, like using a keyword or symbol incorrectly, or using a name that doesn’t exist. For example, if you enter an extra } closing curly brace at the end of a method and then try to run it, Visual Studio will give you an error telling you that it can’t build your code (which is what it does to turn your C# code into something that your computer can actually execute).

What does all that mean?

It means that you’ll run your apps all the time, over and over again. And that’s perfectly fine! It’s absolutely okay to run your app after even a tiny change, just to see what that change did. The more comfortable you are running your app, the more you’ll feel like you can experiment and make changes—and the more fun you’ll have with it.

So go ahead and run your app now. Make sure it starts out with the “Play again?” button visible and the animal buttons invisible. Click the “Play again?” button and make sure it hides itself and shows the animal buttons. When you’re done, close the app (or stop it from inside Visual Studio).



WATCH IT!

When you enter your C# code, even tiny errors can make a big difference.

Some people say that you truly become a developer after the first time you’ve spent hours tracking down a misplaced period. Case matters: AnimalButtons is different from animalButtons. Extra commas, semicolons, parentheses, etc. can break your code—or, worse, change your code so that it still builds but does something different than what you want it to do. The IDE’s AI-assisted IntelliSense and IntelliCode features can help you avoid those problems…but it can’t do everything for you. It’s up to you to make sure your code is right—and that it does what you expect it to do.

Add animals to your buttons
This game won’t be much fun without animals to click on. Let’s update the “Play again?” button’s event handler method to set up the buttons with eight pairs of emojis positioned randomly on the buttons.

 Start creating a List of animal emoji.

Your event handler method needs to start with eight pairs of emoji, so you’re going to write a statement that creates them and stores them in something called a List (you’ll learn a lot more about that in Chapter 8).

Start typing this line of code right after the statements that you just added—but don’t end it with a semicolon, because that’s not the end of the statement yet:

List<string> animalEmoji = new List<string>()
While you’re typing, you’ll see IntelliSense windows pop up to help you enter that code. You might even get an IntelliCode suggestion that matches that code exactly, except with a semicolon at the end like this:


You should use the IntelliSense and IntelliCode suggestions if they make sense. In this case, if you get do get a matching suggestion and take it, make sure you delete the semicolon at the end of the line.

Your PlayAgainButton_Clicked event handler method should now look like this:


 Add a pair of animal emoji to your list.

NOTE
Some people think the plural emoji is emoji, others think it’s emojis. We went with emoji—but both ways are fine!

Your C# statement isn’t done yet. Make sure your cursor is placed just after the ) at the end of the line, then type an opening curly bracket {—the IDE will add the closing one for you, and your cursor will be positioned between the two brackets. Press Enter—the IDE will add line breaks for you automatically:


Now let’s add 8 pairs of animal emoji. You can find emoji by going to your favorite emoji website (for example, https://emojipedia.org/nature) and copying a individual emoji characters. Alternately…

If you’re using Windows, use the Windows emoji panel (press Windows logo key + period). If you’re using a Mac, use the Character Viewer panel (choose “Show Emoji & Symbols” from the Input menu).

Go back to your code add a double quote " then paste the character—we used an octopus—followed by another " and a comma, a space, another ", the same character again, and one more " and comma:


HOW TO ENTER EMOJI
If you’re using Windows, use the emoji panel by pressing Windows logo key  + period. Use the search box to search for a specific animal. When you find the emoji you want to enter, click on it to enter it as if you’d typed it.


If you’re using a Mac, use the Character Viewer panel, which you can view by choosing “Show Emoji & Symbols” from the Input menu in the menu bar . Use the search box to search for a specific animal. When you find the emoji you want to enter, click on it to enter it as if you’d typed it.


 Add the rest of the animal emoji pairs to your list.

Then do the same thing for seven more emoji so you end up with eight pairs of animal emoji between the brackets. We added a blowfish, elephant, whale, camel, brontosaurus, kangaroo, and porcupine—but you can add whatever animals (or other emoji!) that you want.

Add a ; after the closing curly bracket. This is what your statement should look like now:


 Finish the method.

Add the rest of the code to add random animal emoji to the buttons:


Before you run your app, read through the code that you just added. It’s okay if you don’t understand everything that’s going on with it yet. An important part of learning C# is starting to make the code make sense, and reading through it is a great way to do that.

Reading through C# code – even if yon don’t understand all of it yet – is a great way to make it all start to make sense.

 Make sure your code matches ours.

Here’s all of the C# code that you’ve added so far. We gave the parts that Visual Studio generated for you automatically a lighter color so you can see the code that you entered yourself.


Run your app!
Run your app again. The first thing you’ll see is the “Play again?” button. Click the button—you should now see eight pairs of animals in random positions:


Stop it and run it again a few times. The animals should get reshuffled in a different order every time you click the “Play again?” button.


You’ve set the stage for the next part that you’ll add.

When you build a new game, you’re not just writing code. You’re also running a project. A really effective way to run a project is to build it in small increments, taking stock along the way to make sure things are going in a good direction. That way you have plenty of opportunities to change course.

WHO DOES WHAT?

NOTE
This is a pencil-and-paper exercise. We included a lot of of games and puzzles like this throughout the book. You should do all of them, because there’s neuroscience evidence that writing things down is an effective way to get important concepts into your brain faster.

WHO DOES WHAT? SOLUTION

SHARPEN YOUR PENCIL

Here’s a pencil-and-paper exercise that will help you really start to understand your C# code.

Take a piece of paper and turn it on its side so it’s in landscape orientation, and draw a vertical line down the middle.

Write out the entire SetUpGame method by hand on the left side of the paper, leaving space between each statement. (You don’t need to be accurate with the emoji.)

On the right side of the paper, write each of the “what it does” answers above next to the statement that it’s connected to. Read down both sides—it should all start to make sense.

NOTE
Here’s another pencil-and paper exercise. Take a few minutes to do it!


Working on your code comprehension skills will make you a better developer.

The pencil-and-paper exercises are not optional. They give your brain a different way to absorb the information. But they do something even more important: they give you opportunities to make mistakes. Making mistakes is a part of learning, and we’ve all made plenty of mistkaes (you may even find one or two typos in this book!). Nobody writes perfect code the first time—really good programmers always assume that the code that they write today will probably need to change tomorrow. In fact, later in the book you’ll learn about refactoring, or programming techniques that are all about improving your code after you’ve written it.

NOTE
We’re serious—take the time to do the pencil-and-paper exercises. They’re carefully designed to reinforce important concepts, and they’re the fastest way to get the ideas in this book into your brain.

BULLET POINTS
Visual Studio is Microsoft’s IDE—or integrated development environment—that simplifies and assists in editing and managing your C# code files.

.Console apps are cross-platform apps that use text for input and output.

.NET MAUI (or .NET Multi-platform App UI) is a cross-platform framework for building visual apps in C#.

MAUI user interfaces are designed in XAML (eXtensible Application Markup Language), an XML-based markup language that uses tags and properties to define controls in a user interface.

MAUI apps are made up of pages that show controls.

The FlexLayout control contains other controls and wraps them so they display on the page.

The IDE’s Properties window makes it easy to edit the properties of your controls like the text or font size.

C# is made up of statements grouped into methods.

An event handler method gets executed when specific events—like button clicks—happen.

Visual Studio’s AI-assisted IntelliSense and IntelliCode help you enter code more quickly.

NOTE
We’ll add bullet points like this to give a quick summary of many of the ideas and tools that you’ve seen so far.


You can use Git to save all of your code, and Visual Studio will help make it easy.

You’re going to write a lot of code in this book! Wouldn’t it be great if there was a convenient place to put that code so you can always go back to it?

We bet that you’ll write some apps that you really like, and you’ll want to share them with your friends so they can see the great things you’ve built.

Do you have a desktop and a laptop? A computer at home and at an office? Wouldn’t it be great if you could start a project on one computer, then finish it on another one?

Imagine you’re working on a project. You’ve spent hours getting the code right, and you’re really happy with it. Then you make a few changes, and... oh no! Something went completely wrong, your code is broken, and you don’t remember exactly what you changed. It would be great if you see a history of all the changes you made, right?

Git can help you do all of those things!

Here are just a few things Git can do for you
 It can save your files somewhere that you can access them form anywhere, any time

 It lets you save snapshots of your work so you can go back and see exactly what changed

 It lets you share your code with anyone (or keep it private!)

 It lets a group of people collaborate on a project together—so if you’re learning C# with your friends, you can all work on code together

Visual Studio makes it easy to use Git
Git is a really powerful and flexible tool that can help you save, manage, and share your the code and files for all of your projects. It can also be complex and confusing at times! Luckily, Visual Studio has built-in Git suupport that takes care of the complexity. It helps you with Git, so you can concentrate on your code.


We recommend that you create a GitHub account and use it save the code for each of the projects in this book. That will make it easy for you to go back and revisit past projects any time!

Our free Head First C# Guide to Git PDF gives you a simple, step-by-step guide to saving your code in Git with Visual Studio. Download it from https://github.com/head-first-csharp/fifth-edition/



Add C# code to handle mouse clicks
You’ve got buttons with random animal emoji. Now you need them to do something when the player clicks them. Here’s how it will work:


SHARPEN YOUR PENCIL

When you added the Clicked event handler to your animal button, Visual Studio automatically added a method called Button_Clicked to MainPage.xaml.cs. Here’s the code that will go into that method. Before you add this code to your app, read through it and try to figure out what it does.

We’ve asked you a few questions about what the code does. Try writing down the answeres. It’s okay if you’re not 100% right! The goal is to start training your brain to recognize C# as something you can read and make sense of.


SHARPEN YOUR PENCIL SOLUTION

When you added the Clicked event handler to your animal button, Visual Studio automatically added a method called Button_Clicked to MainPage.xaml.cs. Here’s the code that will go into that method. Before you add this code to your app, read through it and try to figure out what it does.

We’ve asked you a few questions about what the code does. Try writing down the answeres. It’s okay if you’re not 100% right! The goal is to start training your brain to recognize C# as something you can read and make sense of.


Enter the code for the event handler
Did you do the “Sharpen your pencil” exercise? If not, take a few minutes and do it—you may not understand 100% of the code in the Button_Clicked event handler method yet, but you should at least have a basic sense of what’s going on. And, more importantly, you’ve had a chance to look at it closely enough so that it should be familiar.

That familiarity will make it easier to use Visual Studio to type the code into the method. Stop your app if it’s running, then MainPage.xaml.cs, find the Button_Clicked event handler method that Visual Studio added for you, and click on the line between its opening { and closing } curly brackets.

Now start typing the code line by line. If you haven’t used an IDE like Visual Studio to write code before, it may be a little weird seeing its IntelliSense and IntelliCode suggestions pop up. Use them if you can—the more you get used to them, the faster and easier it will be to write code later on in the book.

You need to be really careful when you’re entering code, because if your opening parentheses or brackets don’t have matches, or if you miss a semicolon at the end of a statement, your code won’t build. Luckily, Visual Studio have a lot of features to help you write code that builds:

 When you enter “if” it automatically adds the opening and closing parentheses () so you don’t accidentally leave them out.

 If you put your cursor in front of an opening parentehse or bracket, it will highlight the closing one so you can easily see its match.

 A lot of the time, when you enter code that has problems—like writing matchesFnd instead of matchesFound, for example—it will often point out the error by drawing a red squiggly line underneath it.

IDE TIP: THE ERROR LIST
An operating system like Windows, macOS, Android, or iOS can’t run C# code. That’s why Visual Studio has to build your code, or turn it into a binary (a file that the operating system can run). Let’s do an experiment and break your code.

Go to the first line of code in your Button_Clicked method. Press Enter twice, then add this on its own line: Xyz

Check the bottom of the code editor again—you’ll see an icon that looks like this:  or . If you don’t see the icon, choose Build Solution from the Build menu to tell Visual Studio to try to build your code.

Click the icon (or choose Error List from the View menu) to open the Error List window. You’ll see two errors in the window (if you’re using a Mac it’s called Errors and not Error List, and it looks a little different, but it displays the same information):


Visual Studio displayed these errors because Xyz is not valid C# code, and the errors prevent it from building your app. Your code won’t run with those errors, so go ahead and delete the Xyz line that you added and build your app again.

If there are no other errors in your code, the Error List should be empty, and you’ll see an icon that looks like this at the bottom of the Visual Studio window:  or  – that tells you that your app builds.

Run your app and find all the pairs
Try running your app. If you entered all of the code correctly, it should start up and show you the “Play again?” button. Click the button to see a random list of animals. Then click each pair of animals one by one—each pair will disappear after you click it. Once you click the last pair of animals, the buttons will disappear and you’ll see the “Play again?” button again.


If your game doesn’t work the way it should or you don’t see the bug on this page, go back and check the code you entered against the code in the book. It’s really easy to overlook a typo. Finding those issues is a good use of your time, because spotting errors in your code is a really good developer skill to work on.

Try experimenting with your app. Click mismatched pairs. Click in the window but outside hte buttons. Click on the “Time elapsed” label. Click an empty button. Is your app working?

Uh-oh – there’s a bug in your code
If you typed in all of the code correctly, you may have noticed a problem. Start your app, click the “Play again?” button to show the random animals, and click on a pair to make the animals disappear from their buttons. Now click the blank button seven times. Wait, what happened? Did the animal buttons disappear and the “Play again?” button appeared, as if you’d wont he game? That’s not supposed to happen! Your game has a bug.

Don’t worry, this bug is not your fault!

We left that bug in your code on purpose. You’re going to be writing a lot of code throughout this book. Every chapter has several projects for you to work on… and there are opportunities for bugs in every one of those projects. Finding and fixing bugs is a normal and healthy part of writing code—and a really valuable skill for you to practice.

Every bug is caused by a problem in the code, so the first step in fixing a bug is figuring out what’s causing it.

When you find a bug, you need to sleuth it out
Every bug is different. Code can break in many different ways. But there’s one thing all bugs have common: every one of them is caused by a problem in the code. So when there’s a bug, your job is to figure out what’s causing it, because you can’t fix the problem until you know why it’s happening.

If you’ve ever read a mystery novel or watched a detecive show, you know to solve a mystery: you need to find the culprit. So let’s do that right now. It’s time to put on your Sherlock Holmes cap, grab your magnifying glass, and sleuth out what’s causing the bug.


SLEUTH IT OUT

The Case of the Unexpected Match

You’ve probably heard the word “bug” before.

You might have even said something like this to your friends at some point in the past: “That game is really buggy, it has so many glitches.” Every bug has an explanation, and everything in your program happens for a reason… but not every bug is easy to track down. That’s why we’ll include tips for sleuthing out bugs throught the book, starting with this “Sleuth it out” section.

Every bug has a culprit

Bugs are weird. They’re what happens when your code does something you didn’t expect it to do.

But bugs are also normal. Every developer spends time finding and fixing bugs. It’s a normal part of writing code. You’re going to write code that doesn’t do what you expect it to. And when you do, the first thing you need to do is figure out what’s causing the bug.

The first step in finding a bug is thinking about what might have caused it


Sherlock Holmes once said, “Crime is common. Logic is rare. Therefore it is upon the logic rather than upon the crime that you should dwell.” That’s great advice for figuring out what caused the bug. Don’t get frustrated because your app doesn’t do what you want (that’s dwelling on the crime!). Instead, think about the logic of the situation. So let’s look at the code and figure out what’s going on.

Read the code carefully and search for clues

We know that all of the code for handling mouse clicks is in the Button_Clicked event handler that you just added. So let’s go back to the code and see if we can find clues about what went wrong.

Luckily, you did that “Sharpen your pencil” exercise. You looked closely at the code in the Button_Clicked event handler method to understand it. (If you haven’t done that exercise yet, go back and do it now!)

Based on what we found in the “Sharpen your pencil” exercise, we already know a few things about the code:

The event handler uses matchesFound to keep track of the number of pairs of animals the player found, so the game can end when they found all 8 pairs.

There a part of the event handler that checks if the animals on the two buttons that the player clicked on match each other. If they do match, it adds one to matchesFound and blanks out both buttons.

If matchesFound equals 8, the player found all 8 pairs of animals.There’s code at the end of the event handler that checks to see if matchesFound is equal to 8, and if that’s true is it resets the game.

Those are the important clues that will help us find and fix the bug. Before you go on, can you sleuth out what’s causing the game to end early if you keep clicking a button that’s already been cleared?

Why did the bug happen?

Let’s think about those three clues for a minute. Here’s what we know.

The game uses matchesFound to keep track of the number of pairs of animals the player found.

If the player clicks on a pair, the game increases matchesFound by 1 and blanks out the buttons the player clicked on.

When matchesFound reaches 8, the game resets itself.

So what are these clues telling us? There’s one conclusion that we can draw from these clues:

Somehow matchesFound is being increased by 1 when the player clicks on a button that’s already blanked out.

Which means we have a starting point: the code that increases matchesFound by 1.

Go back to the scene of the crime

Here’s the part of the code that increases matchesFound – the specific line that does that is in boldface:


The first line of code in the statements that we just showed you is an if statement, which checks if something and executes statements if it’s true. In this case, if the player clicked a different button than the first one in the pair (that’s what “buttonClicked != lastClicked” checks for) and if the animals on those two buttons match (“buttonClicked.Text == lastClicked.Text”), it increases matchesFound by 1 and blanks out both buttons.

This is where things went wrong—which means it’s also where we can fix the bug. We just need to find a way to keep matchesFound from getting increased by 1 if the player clicked a button that’s already blank.v

We found the culprit, so now we can fix the bug

Position your cursor between the last two closing parentheses )) in the if statement and press enter to add a line. Then enter the following code: && (buttonClicked.Text != "")

Here’s what your code should now look like:


Once you’ve edited the if statement, run your app again. Now the bug should be fixed.

NOTE
Finding and fixing bugs is one part typing, nine parts thinking... and 100% guaranteed to make you a better developer. That’s what these “Sleuth it Out” sections are all about.


Finish the game by adding a timer
Our animal match game will be more exciting if players can try to beat their best time. We’ll add a timer that “ticks” after a fixed interval by repeatedly calling a method.



Timers “tick” every time interval by calling methods over and over again. You’ll use a timer that starts when the player starts the game and ends when the last animal is matched.

Add a timer to your game’s code
In this last part of your project, you’ll add a timer to your game to make it more exciting. It will keep track of the time elapsed (in tenths of seconds), starting when the player clicks the “Play again?” button and stopping when they find the last match.


 Add a line of code to the end of the PlayAgainButton_Clicked event handler to start a timer.

Go to the very end of the PlayAgainButton_Clicked event handler. There are two closing curly brackets } at the end of the method on separate lines. Add three lines between the brackets, then add the following line of code into that space that you created:

   foreach (var button in AnimalButtons.Children.OfType<Button>())
   {
       int index = Random.Shared.Next(animalEmoji.Count);
       string nextEmoji = animalEmoji[index];
       button.Text = nextEmoji;
       animalEmoji.RemoveAt(index);
   }
   Dispatcher.StartTimer(TimeSpan.FromSeconds(.1), TimerTick);
}
The line of code that you just added causes your app to start a timer that executes a method called TimerTick every .1 a second.

 Examine the error and click on “TimerTick” in the code you just added.

You just added a line of code to start a timer that “ticks” every tenth of a second. Every time it ticks, it calls a method called TimerTick. But hold on—your C# code doesn’t have a TimerTick method. If you try to build your code, you’ll see an error in the Error List window:


And there will be a red squiggly line underneath TimerTick in the line of code that you added. Click on “TimerTick” in the C# code—when you click on it, Visual Studio will display an icon shaped like a light bulb in the left margin.


 Use Visual Studio to generate a new TimerTick method.

The code that you added has an error because it refers to a method called TimerTick that doesn’t exist. When you clicked on it, a light bulb icon showed up in the left-hand margin. If you hover over it, you can see an error message and light bulb icon directly underneath it as well:


Clicking the light bulb icon to brings up the Quick Actions menu, which gives you some suggested potential fixes for the error. You can also press Alt+Enter or Ctrl+. on Windows or +Return on a Mac to bring up the menu:


The first option in the Quick Actions menu should be “Generate method ‘TimerTick’” – and if you select that option, you’ll see a preview to the right. Choose that option.

Visual Studio will generate the TimerTick method for you. Look through your C# code in MainPage.xaml.cs and find the TimerTick method that Visual Studio added:

private bool TimerTick()
{
    throw new NotImplementedException();
}
When your C# code has errors, Visual Studio sometimes has suggestions for potential fixes that can generate code to fix the error.

Finish the code for your game
In this last part of your project, you’ll add a timer to your game to make it more exciting. It will keep track of the time elapsed (in tenths of seconds), starting when the player clicks the “Play again?” button and stopping when they find the last match.

Add a field to hold the time elapsed

Find the first line of the TimerTick method that you just generated. Place your mouse cursor at the beginning of the line, then press enter twice to add two spaces above it.

Add this line of code:


Finish your TimerTick method
Now you have everything you need to finish the TimerTick method. Here’s the code for it:


Run your game. Now the timer works!


YOUR TIMERTICK METHOD UP CLOSE

Let’s take a closer look at your TimerTick method to see how it, well, ticks. It has a total of seven statements, and each of them is important.


Even better ifs…
Your game is pretty good. Nice work! Every game—in fact, pretty much every program—can be improved. Here are a few things that we thought of that could make the game better:

 Add different kinds of animals so the same ones don’t show up each time.

 Keep track of the player’s best time so they can try to beat it.

 Make the timer count down instead of counting up so the player has a limited amount of time.


SHARPEN YOUR PENCIL

Can you think of your own “even better if” improvements for the game? This is a great exercise—take a few minutes and write down at least three improvements to the animal matching game.

NOTE
We’re serious—take a few minutes and do this. Stepping back and thinking about the project you just finished is a great way to seal the lessons you learned into your brain.

Did you save your code Git?

If you did, this is a great time to commit all of your changes and push it to the repository!

And if you still haven’t, take a few minutes and check out our free Head First C# Guide to Git PDF. It gives you step-by-step instructions for keeping your code safe in Git.

Download it today from our own GitHub page: https://github.com/head-first-csharp/fifth-edition

BULLET POINTS
An event handler is a method that your application calls when a specific event like a mouse click happens.

Visual Studio makes it easy to add and manage your event handler methods.

The IDE’s Error List window shows any errors that prevent your code from building.

A timer calls a method over and over again on a specified interval.

foreach is a kind of loop that iterates through a collection of items.

When you have a bug in your code, the first thing to do is try to figure out what’s causing it.

Bugs are normal, and sleuthing out bugs is an important developer skill that you’ll work on throughout this book.

Visual Studio makes it really easy to use source control to back up your code and keep track of all changes that you’ve made.

You can commit your code to a remote Git repository. We use GitHub for the repository with the source code for all of the projects in this book.


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


1. Start Building apps with C#: Build Something Great…Fast!
2. Variables, Statements, and Methods: Dive into C# code
3. Namespaces and Classes: Organizing your code
12h 51m remaining
Chapter 2. Variables, Statements, and Methods: Dive into C# code
A NOTE FOR EARLY RELEASE READERS
With Early Release ebooks, you get books in their earliest form—the authors’ raw and unedited content as they write—so you can take advantage of these technologies long before the official release of these titles.

This will be the 2nd chapter of the final book. Please note that the GitHub repo will be made active later on.

If you have comments about how we might improve the content and/or examples in this book, or if you notice missing material within this chapter, please reach out to the editor at mcronin@oreilly.com.


You’re not just an IDE user. You’re a developer.

You can get a lot of work done using the IDE, but there’s only so far it can take you. Visual Studio is one of the most advanced software development tools ever made, but a powerful IDE is only the beginning. It’s time to dive in to C# code: how it’s structured, how it works, and how you can take control of it…because there’s no limit to what you can get your apps to do.

Take a closer look at the files in your console app
In the last chapter, you created a new C# Console App project and named it MyFirstConsoleApp. When you did that, Visual Studio created two folders and three files.


Let’s take a closer look at the Program.cs file that it created. Open it up in Visual Studio:


A statement performs one single action
A console app is an app with a text-only user interface. All its input and output goes to a console, like the Windows command prompt or MacOS Terminal.

Your app has two lines:

The first line is a comment. Comments start with two forward slashes // and everything after those slashes is ignored. You can can use comments to write notes about the code.

The second line is a statement. In this case, it’s a Console.WriteLine statement, which writes a line of text. Statements are what actually make your code do things.

When you run your app, it starts with the first statement, and keeps executing statements until it runs out, and since it’s a console app you’ll see its output in a console window. Once it executes the last statements, the app exits.


The IDE helps you build your code right.

A long, long, LONG time ago, programmers had to use simple text editors like Windows Notepad or macOS TextEdit to edit their code. In fact, some their features would have been cutting-edge (like search and replace, or Notepad’s Ctrl+G for “go to line number”). We had to use a lot of complex command-line applications to build, run, debug, and deploy our code.

Over the years, Microsoft (and, let’s be fair, a lot of other companies, and a lot of individual developers!) figured out how to add many helpful things like error highlighting, IntelliSense, WYSIWYG click-and-drag window UI editing, automatic code generation, and many other features.

After years of evolution, Visual Studio is now one of the most advanced code-editing tools ever built. And lucky for you, it’s also a great tool for learning and exploring C# and app development.

THERE ARE NO DUMB QUESTIONS
Q: I understand what Program.cs does—that’s where the code for my program lives. But does my program need the other two files and folders?

A: When you created a new project in Visual Studio, it created a solution for you. A solution is just a container for your project. The solution file ends in .sln and contains a list of the projects that are in the solution, with a small amount of additional information (like the version of Visual Studio used to create it). The project lives in a folder inside the solution folder. It gets a separate folder because some solutions can contain multiple projects—but yours only contains one, and it happens to have the same name as the solution (MyFirstConsoleApp). The project folder for your app contains two files: a file called Program.cs that contains the code, and a project file called MyFirstConsoleApp.csproj that has all of the information Visual Studio needs to build the code, or turn it into a something your computer can run. You’ll eventually see two more folders underneath your project folder: the bin/ folder will have the executable files built from your C# code, and the obj folder will have the temporary files used to build it.

Statements are the building blocks for your apps
Your app is made up of classes, and those classes contain methods, and those methods contain statements. A statement is a line of code that does something.

NOTE
A statement can actually span multiple lines, which you’ll see later in this book. But for now, you can just think of “statement” and “line of code” as the same thing.

So if we want to build apps that do a lot of things, we’ll need a few different kinds of statements to make them work. You’ve already seen one kind of statement:

Console.WriteLine("Hello World!");
This is a statement that calls a method—specifically, the Console.WriteLine method, which prints a line of text to the console. We’ll also use a few other kinds of statements in this chapter and throughout the book. For example:


Statements live inside of methods
You wrote a method in Chapter 1 to set up your animal matching game. But what, exactly, is a method?

Methods do something
The Console.WriteLine method is part of .NET. It’s not hard to guess that a method that starts with “Console.” has something to do with reading or writing text in a console app. In this case, it writes a line of text to the console. It’s a really useful method, and you’ll use it—and a lot of other .NET methods (it has thousands of them!)—throughout this book.

You’re going to write your own methods, and you’re going to write code that calls those methods. To call a method, you write a statement that consists of the name of that method followed by parentheses and a semicolon. You can pass information to that method by putting it inside those parentheses—like passing “Hello, World!” when your code called the Console.WriteLine method.

Methods help you organize your code
Every method is made up of statements, and one method can contain many statements. Code tends to naturally organize into blocks, or lines of code which, taken together, do a specific thing. Methods are your way to take those code blocks, give them names, and make them easy to call.

When your program calls a method, it executes the first statement in that method, then the next, then the next, etc. When the method runs out of statements—or hits a return statement—it ends, and the program execution resumes after the statement that originally called the method.

Do you really need a method? You could copy the code in a method and paste it over the statement that called that method, and the app would still work. Putting the code into a method and giving it a name makes it a lot easier to understand what that code does.

BRAIN POWER

You’ll use methods over and over again throughout this book to organize your code. Why do you think your code needs organizing?

When you’re writing your code, you can take a block of code and turn it into a single method, multiple methods, or not use methods at all. How do you decide where to break up your code into methods?

The Console.WriteLine method writes a line to the console. Does that name make sense to you? Can you think of why it’s useful for methods to have sensible names?

Your methods use variables to work with data
Every program, no matter how big or how small, works with data. Sometimes the data is in the form of a document, or an image in a video game, or a social media update—but it’s all just data. That’s where variables come in. A variable is what your program uses to store data.


Declare your variables
Whenever you declare a variable, you tell your program its type and its name. Once C# knows your variable’s type, it will generate errors that stop your program from building if you try to do something that doesn’t make sense, like subtract "Fido" from 48353. Here’s how to declare variables:


Whenever your program needs to work with numbers, text, true/false values, or any other kind of data, you’ll use variables to keep track of them. The variable’s type defines what kind of data it can hold.

Variables vary
A variable is equal to different values at different times while your program runs. In other words, a variable’s value varies. (Which is why “variable” is such a good name.) This is really important, because that idea is at the core of every program you’ll write. Say your program sets the variable myHeight equal to 63:

int myHeight = 63;
Any time myHeight appears in the code, C# will replace it with its value, 63. Then, later on, if you change its value to 12:

myHeight = 12;
C# will replace myHeight with 12 from that point onwards (until it gets set again)—but the variable is still called myHeight.

You need to assign values to variables before you use them
Try typing these statements just below the “Hello World” statement in your new console app:


Go ahead, try it right now. You’ll get an error, and the IDE will refuse to build your code. That’s because it checks each variable to make sure that you’ve assigned it a value before you use it. The easiest way to make sure you don’t forget to assign your variables values is to combine the statement that declares a variable with a statement that assigns its value:


If you write code that uses a variable that hasn’t been assigned a value, your code won’t build. It’s easy to avoid that error by combining your variable declaration and assignment into a single statement.

NOTE
Once you’ve assigned a value to your variable, that value can change. So there’s no disadvantage to assigning a variable an initial value when you declare it.

A few useful types
Every variable has a type that tells C# what kind of data it can hold. We’ll go into a lot of detail about the many different types in C# in Chapter 4. In the meantime, we’ll concentrate on the three most popular types. int holds integers (or whole numbers), string holds text, and bool holds Boolean true/false values.


Generate a new method to work with variables
In the last chapter, you learned that Visual Studio will generate code for you. This is quite useful when you’re writing code—and it’s also a really valuable learning tool. Let’s build on what you learned and take a closer look at generating methods.


 Add a method to your new MyFirstConsoleApp project.

Open the Console App project that you created in the last chapter. The Program.cs file has these lines:

// See https://aka.ms/new-console-template for more information
Console.WriteLine("Hello World!");
Replace those two lines with a statement that calls a method:


 Let Visual Studio tell you what’s wrong.

As soon as you finish replacing the statement, Visual Studio will draw a red squiggly underline beneath your method call. Hover your mouse cursor over it. The IDE will display a pop-up window:


Visual Studio is telling you two things: that there’s a problem—you’re trying to call a method that doesn’t exist (which will prevent your code from building)—and that it has a potential fix.

 Generate the OperatorExamples method.

On Windows, the pop-up window tells you to press Alt+Enter or Ctrl+. to see the potential fixes. On macOS, it has a “Show potential fixes” link—press ⌥+Return to see the potential fixes. So go ahead and press either of those key combinations (or click on the dropdown to the left of the pop-up).


The IDE has a solution: it will generate a method called OperatorExamples in your top-level statements. Click “Preview changes” to display a window that has the IDE’s potential fix, adding a new method. Then click Apply to add the method to your code.

Add code that uses operators to your method

Once you’ve got some data stored in a variable, what can you do with it? Well, if it’s a number, you might want to add or multiply it. If it’s a string, you might join it together with other strings. That’s where operators come in. Here’s the method body for your new OperatorExamples method. Add this code to your program, and read the comments to learn about the operators it uses.


SHARPEN YOUR PENCIL

The statements you just added to your code will write three lines to the console: each Console.WriteLine statement prints a separate line. Before you run your code, figure out what they’ll be and write them down. And don’t bother looking for a solution, because we didn’t include one! Just run the code to check your answers.

Here’s a hint: converting a bool to a string results in either False or True.

Line 1: ________________________________________________________________________

Line 2: ________________________________________________________________________

Line 3: ________________________________________________________________________

Use the debugger to watch your variables change
When you ran your program earlier, it was executing in the debugger—and that’s an incredibly useful tool for understanding how your programs work. You can use breakpoints to pause your program when it hits certain statements and add watches to look at the value of your variables. Let’s use the debugger to see your code in action. We’ll use these three features of the debugger, which you’ll find in the toolbar:


If you end up in a state you don’t expect, just use the Restart button () to restart the debugger.


 Add a breakpoint and run your program.

Click on the first line of your program and choose Toggle Breakpoint (F9 or ⌘/) from the Debug menu. The line should now look like this—the line should be highlighted in red with a dot in the left margin:


Then press the  button to run your program in the debugger, just like you did earlier.

 Step into the method.

Your debugger is stopped at the breakpoint on the statement that calls the OperatorExamples method.


Press Step Into (F11)—the debugger will jump into the method and pause before it runs the first statement.

 Examine the value of the width variable.

When you’re stepping through your code, the debugger pauses after each statement that it executes. This gives you the opportunity to examine the values of your variables. Hover over the width variable.


The IDE displays a pop-up that shows the current value of the variable—it’s currently 0. Now press Step Over (F10 on Windows or ⇧⌘O on macOS)—it goes past the comment to the first statement, which is now highlighted. Now press Step Over again, then hover over width again. It now has a value of 3.

 The Locals window shows the values of your variables.

The variables that you declared are local to your OperatorExamples method—which just means that they exist only inside that method, and can only be used by statements in the method. Visual Studio displays their values in the Locals window at the bottom of the IDE when it’s debugging.


 Add a watch for the height variable.

A really useful feature of the debugger is the Watch window, which is typically in the same panel as the Locals window at the bottom of the IDE. When you hover over a variable, you can add a watch by right-clicking on the variable name in the pop-up window and choosing Add Watch. Hover over the height variable, then right-click and choose Add Watch from the menu.


Now you can see the height variable in the Watch window.


The debugger is one of the most important features in Visual Studio, and it’s a great tool for understanding how your programs work.

 Step through the rest of the method.

Step over each statement in OperatorExamples. As you step through the method, keep an eye on the Locals or Watch window and watch the values as they change. On Windows, press Alt+Tab before and after the Console.WriteLine statements to switch back and forth to the Debug Console to see the output. On macOS, you’ll see the output in the Terminal window so you don’t need to switch windows.

Use operators to work with variables
Once you have data in a variable, what do you do with it? Well, most of the time you’ll want your code to do something based on the value. That’s where equality operators, relational operators, and logical operators become important:

Equality Operators

The == operator compares two things and is true if they’re equal.

The != operator works a lot like ==, except it’s true if the two things you’re comparing are not equal.

Relational Operators

Use > and < to compare numbers and see if a number in one variable is bigger or smaller than another.

You can also use >= to check if one value is greater than or equal to another, and <= to check if it’s less than or equal.

Logical Operators

You can combine individual conditional tests into one long test using the && operator for and and the || operator for or.

Here’s how you’d check if i equals 3 or j is less than 5: (i == 3) || (j < 5)

WATCH IT!

Don’t confuse the two equals sign operators!

You use one equals sign (=) to set a variable’s value, but two equals signs (==) to compare two variables. You won’t believe how many bugs in programs—even ones made by experienced programmers!—are caused by using = instead of ==. If you see the IDE complain that you “cannot implicitly convert type ‘int’ to ‘bool’,” that’s probably what happened.

USE OPERATORS TO COMPARE TWO INT VARIABLES
You can do simple tests by checking the value of a variable using a comparison operator. Here’s how you compare two ints, x and y:

x < y (less than)
x > y (greater than)
x == y (equals - and yes, with two equals signs)
These are the ones you’ll use most often.

“if” statements make decisions
Use if statements to tell your program to do certain things only when the conditions you set up are (or aren’t) true. The if statement tests the condition and executes code if the test passed. A lot of if statements check if two things are equal. That’s when you use the == operator. That’s different from the single equals sign (=) operator, which you use to set a value.



if/else statements also do something if a condition isn’t true
if/else statements are just what they sound like: if a condition is true they do one thing or else they do the other. An if/else statement is an if statement followed by the else keyword followed by a second set of statements to execute. If the test is true, the program executes the statements between the first set of brackets. Otherwise, it executes the statements between the second set.


Loops perform an action over and over
Here’s a peculiar thing about most programs (especially games!): they almost always involve doing certain things over and over again. That’s what loops are for—they tell your program to keep executing a certain set of statements as long as some condition is true or false.


while loops keep looping statements while a condition is true
In a while loop, all of the statements inside the curly brackets get executed as long as the condition in the parentheses is true.


do/while loops run the statements then check the condition
A do/while loop is just like a while loop, with one difference. The while loop does its test first, then runs its statements only if that test is true. The do/while loop runs the statements first, then runs the test. So if you need to make sure your loop always runs at least once, a do/while loop is a good choice.


for loops run a statement after each loop
A for loop runs a statement after each time it executes a loop.


NOTE
The parts of the for statement are called the initializer (int i = 0), the conditional test (i < 8), and the iterator (i = i + 2). Each time through a for loop (or any loop) is called an iteration.

The conditional test always runs at the beginning of each iteration, and the iterator always runs at the end of the iteration.

FOR LOOPS UP CLOSE

A for loop is a little more complex—and more versatile—than a simple while loop or do loop. The most common type of for loop just counts up to a length. The for code snippet causes the IDE to create an example of that kind of for loop:


A for loop has four sections—an initializer, a condition, an iterator, and a body:

for (initializer; condition; iterator) {
    body
}
Most of the time you’ll use the initializer to declare a new variable—for example, the initializer int i = 0 in the for code snippet above declares a variable called i that can only be used inside the for loop. The loop will then execute the body—which can either be one statement or a block of statements inside curly braces—as long as the condition is true. At the end of each iteration the for loop executes the iterator. So this loop:

for (int i = 0; i < 10; i++) {
    Console.WriteLine(“Iteration #” + i);
}
will iterate 10 times, printing Iteration #0, Iteration #1, ..., Iteration #9 to the console.

SHARPEN YOUR PENCIL

Here are a few loops. Write down if each loop will repeat forever or eventually end. If it’s going to end, how many times will it loop? Also, answer the questions in the comments in loops #2 and #3.


SHARPEN YOUR PENCIL SOLUTION

Here are a few loops. Write down if each loop will repeat forever or eventually end. If it’s going to end, how many times will it loop? Also, answer the questions in the comments in loops #2 and #3.


NOTE
When we give you pencil-and-paper exercises, we’ll usually give you the solution on the next page.

NOTE
Take the time to really figure out how loop #3 works. Here’s a perfect opportunity to try out the debugger on your own! Set a breakpoint on q = p – q; and use the Locals window to watch how the values of p and q change as you step through the loop.

Use code snippets to help write loops

You’ll be writing a lot of loops throughout this book, and Visual Studio can help speed things up for you with snippets, or simple templates that you can use to add code. Let’s use snippets to add a few loops to your OperatorExamples method.

If your code is still running, choose Stop Debugging (Shift+F5) from the Debug menu (or press the square Stop button  in the toolbar). Then find the line Console.WriteLine(area); in your OperatorExamples method. Click at the end of that line so your cursor is after the semicolon, then press Enter a few times to add some extra space. Now start your snippet. Type while and press the Tab key twice. The IDE will add a template for a while loop to your code, with the conditional test highlighted:


IDE TIP: BRACKETS
If your brackets (or braces, either name will do) don’t match up, your program won’t build, which leads to frustrating bugs. Luckily, the IDE can help with this! Put your cursor on a bracket, and the IDE highlights its match.

Type area < 50—the IDE will replace true with the text. Press Enter to finish the snippet. Then add two statements between the brackets:

while (area < 50)
{
    height++;
    area = width * height;
}
Next, use the do/while loop snippet to add another loop immediately after the while loop you just added. Type do and press Tab twice. The IDE will add this snippet:


Type area > 25 and press Enter to finish the snippet. Then add two statements between the brackets:

do
{
    width--;
    area = width * height;
} while (area > 25);
Now use the debugger to really get a good sense of how these loops work:

Click on the line just above the first loop and choose Toggle Breakpoint (F9) from the Debug menu to add a breakpoint. Then run your code and press F5 to skip to the new breakpoint.

Use Step Over (F10) to step through the two loops. Watch the Locals window as the values for height, width, and area change.

Stop the program, then change the while loop test to area < 20 so both loops have conditions that are false. Debug the program again. The while checks the condition first and skips the loop, but the do/while executes it once and then checks the condition.

SHARPEN YOUR PENCIL

Let’s get some practice working with conditionals and loops. Update the code in your Program.file to matche the new code below, including TryAnIf, TryAnIfElse, and TrySomeLoops methods. Before you run your code, read it carefully and try to answer the questions based on how you think it will run. Then run your code and see if you got them right.

TryAnIf();
TrySomeLoops();
TryAnIfElse();

private static void TryAnIf()
{
    int someValue = 4;
    string name = "Bobbo Jr.";
    if ((someValue == 3) && (name == "Joe"))
    {
        Console.WriteLine("x is 3 and the name is Joe");
    }
    Console.WriteLine("this line runs no matter what");
}

private static void TryAnIfElse()
{
    int x = 5;
    if (x == 10)
    {
        Console.WriteLine("x must be 10");
    }
    else
    {
        Console.WriteLine("x isn’t 10");
    }
}

private static void TrySomeLoops()
{
    int count = 0;

    while (count < 10)
    {
        count = count + 1;
    }
    for (int i = 0; i < 5; i++)
    {
        count = count - 1;
    }
    Console.WriteLine("The answer is " + count);
}
What does the TryAnIf method write to the console?

.............................................................................

.............................................................................

What does the TryAnIfElse method write to the console?

.............................................................................

What does the TrySomeLoops method write to the console?

.............................................................................

We didn’t include answers for this exercise in the book. After you write down the answer, run the code check the the console output to see if your answer is correct.

Some useful things to keep in mind about C# code
 Don’t forget that all your statements need to end in a semicolon.

name = "Joe";
 Add comments to your code by starting a line with two slashes.

// this text is ignored
 Use /* and */ to start and end comments that can include line breaks.

/* this comment
* spans multiple lines */
 Variables are declared with a type followed by a name.

int weight;
// the variable's type is int and its name is weight
 Most of the time, extra whitespace is fine.

So this:          int            j        =          1234       ;
Is exactly the same as this: int j = 1234;
 If/else, while, do, and for are all about testing conditions.

Every loop we’ve seen so far keeps running as long as a condition is true.


Then your loop runs forever.

Every time your program runs a conditional test, the result is either true or false. If it’s true, then your program goes through the loop one more time. Every loop should have code that, if it’s run enough times, should cause the conditional test to eventually return false. If it doesn’t, then the loop will keep running until you kill the program or turn the computer off!

NOTE
This is sometimes called an infinite loop, and there are definitely times when you’ll want to use one in your code.

BRAIN POWER

Can you think of a reason that you’d want to write a loop that never stops running?

GAME DESIGN

Mechanics

The mechanics of a game are the aspects of the game that make up the actual gameplay: its rules, the actions that the player can take, and the way the game behaves in response to them.

Let’s start with a classic video game. The mechanics of Pac Man include how the joystick controls the player on the screen, the number of points for dots and power pellets, how ghosts move, how long they turn blue and how their behavior changes after the player eats a power pellet, when the player gets extra lives, how the ghosts slow down as they go through the tunnel—all of the rules that drive the game.

When game designers talk about a mechanic (in the singular), they’re often referring to a single mode of interaction or control, like a double jump in a platformer or shields that can only take a certain number of hits in a shooter. It’s often useful to isolate a single mechanic for testing and improvement.

Tabletop games give us a really good way to understand the concept of mechanics. Random number generators like dice, spinners, and cards are great examples of specific mechanics.

You’ve already seen a great example of a mechanic: the timer that you added to your animal matching game changed the entire experience. Timers, obstacles, enemies, maps, races, points…these are all mechanics.

Different mechanics combine in different ways, and that can have a big impact on how the players experience the game. Monopoly is a great example of a game that combines two different random number generators—dice and cards—to make a more interesting and subtle game.

Game mechanics also include the way the data is structured and the design of the code that handles that data—even if the mechanic is unintentional! Pac Man’s legendary level 256 glitch, where a bug in the code fills half the screen with garbage and makes the game unplayable, is part of the mechanics of the game.

So when we talk about mechanics of a C# game, that includes the classes and the code, because they drive the way that the game works.

NOTE
Here’s another one of those “Game design... and beyond” sections. This one is all about mechanics, an important part of video game design. If you’re not interested in writing video games, read these sections anyway! They have important concepts that we’ll build on throughout the book.


Definitely! Every program has its own kind of mechanics.

There are mechanics at every level of software design. They’re easier to talk about and understand in the context of video games. We’ll take advantage of that to help give you a deeper understanding of mechanics, which is valuable for designing and building any kind of project.

Here’s an example. The mechanics of a game determine how hard or easy it is to play. Make Pac Man faster or the ghosts slower and the game gets easier. That doesn’t necessarily make it better or worse—just different. And guess what? The same exact idea applies to how you design your classes! You can think of how you design your methods and fields as the mechanics of the class. The choices you make about how to break up your code into methods or when to use fields make them easier or more difficult to use.

BULLET POINTS
Methods are made up of statements. Calling a method executes its statements in order.

Putting statements into a method and giving it a name helps make your code easier to read.

When a method runs out of statements or executes a return statement, execution resumes after the statement that originally called the method.

A variable’s type determines what kind of data—like whole or decimal numbers, text, or true/false values—that it can hold

You need to assign values to variables before you can use them.

Operators like +, -, *, and / perform manipulations on the data stored in variables. The = operator assigns a value, while the == operator compares two values.

if statements tell your program to do certain things only when the conditions you set up are (or aren’t) true.

Loops execute a set of statements over and over again until a condition is met. for, while, and do/while loops all iterate over statements multiple times, but they work differently from each other.

Visual Studio’s code snippets feature helps you write if statements and loops.

Controls drive the mechanics of your user interfaces
In the last chapter, you built a game using Button and Label controls. There are a lot of different ways that you can use controls, and the choices you make about what controls to use can really change your app. Does that sound weird? It’s actually really similar to the way we make choices about mechanics in game design. If you’re designing a tabletop game that needs a random number generator, you can choose to use dice, a spinner, or cards. If you’re designing a platformer, you can choose to have your player jump, double jump, wall jump, or fly (or do different things at different times). The same goes for apps: if you’re designing an app where the user needs to enter a number, you can choose from different controls to let them do that… and that choice affects how your user experiences the app.

Meet some of the controls you’ll use in this book
Most of the chapters in this book feature a .NET MAUI projcet. We included them so you can go beyond console apps and start learning how to build visual apps. In those projects, you’ll use many different controls to build each app’s the user interface (or UI)—or the way the window is laid out so the user can interact with it—of each app.

Here are the controls you’ve seen so far.


The user interface, or UI, is the part of the app that your user interacts with. In a console app, the UI is made up of text, and the user uses the keyboard to interact with it. In a .NET MAUI app, the UI is built using controls.

Other controls you’ll use in this book
Controls are common user interface components, and they serve as the building blocks of your UI. The choices you make about what controls to use change the mechanics of your app.

Most of the chapters in this book contain a .NET MAUI project. You’ll use various controls to build the UI for each of those apps. Here are a few of the ones that you’ll use.

NOTE
We can borrow the idea of mechanics from video games to understand our options, so we can make great choices for any of our own apps—not just games.







Build a .NET MAUI app to experiment with controls
You’ve probably seen most the controls we just showed you (even if you didn’t know all of their official names). Now let’s create a .NET MAUI app to get some practice using some of them. The app will be really simple—the user will use controls to enter values, and the app will display those values.


RELAX

Don’t worry about memorizing the XAML in this project. You’ll pick it up throughout the book.

This Do this! and these exercises are all about getting some practice using XAML to build a UI with controls. You can always refer back to it when we use these controls in projects later in the book.

Create a new app to experiment with controls

Go back to Visual Studio and create a new .NET MAUI project, just like you did in Chapter 1. Name your project ExperimentWithControls. Run your new .NET MAUI app. It will pop up a window with a picture of a cute robot, text that says Hello, World!, and smaller text that says Welcome to .NET Multiplatform APP UI, and finally a button with the label Click me.


Now go back to Visual Studio and double-click the file MainPage.xaml to open it. Use the buttons in the left margin that look like a minus sign in a square to collapse the <Image>, <Label>, and <Button> tags. Each of those tags corresponds to one of the controls in your app.


Explore your new MAUI app and figure out how it works
When you created your new .NET MAUI app, Visual Studio used a template to create the files for your app, substituting the name that you specified(ExperimentWithControls) in various lines in the files. Let’s dig in to the project that you created.


 Create a new .NET MAUI project called ExperimentWithControls.

Go back to Visual Studio and create a new .NET MAUI project, just like you did in Chapter 1. Name your project ExperimentWithControls.

 Run your app and click on the button.

When you run the app, you’ll see the app window—it should look like this:


You know you want to click the “Click me” button. Go ahead! Lhe label on the button will change from “Click me” to “Clicked 1 time” and increment (or add one) every time you click the button.


 Investigate how the counter on the button works.

Go to the Solution Explorer, expand MainPage.xaml, and open MainPage.xaml.cs. Find the line that has the statement count++; and place a breakpoint on it.


Before you go to the next step, read the code.
Can you figure out how the button works?

 Click on the button and step through the code.

Add a watch for the count variable, just like you did earlier in the chapter. Then use “Step Over” to step through the code. Here’s waht the OnCounterClicked event handler method does:

 First it executes count++ to increment (or add one to) the count variable.

 Next it uses an if statement to check if the count variable equals 1. If it does, then it sets the button’s text to “Clicked 1 time”.

 If it doesn’t equal 1, it sets the button’s text to “Clicked {count} times” – you’ll learn more about exactly what that the $ dollar sign and {brackets} do in Chapter 5 (it’s called string interpolation).

 Click on the button and step through the code.

The program should pause on the breakpoint, just like you saw earlier in the chapter:


Add a watch for the count variable, just like you did earlier with the OperatorExamples console app. It should start out with the value 0. Step over to the


Keep stepping through the code. The if statement checks whether the count value is equal to 1. If it is, it executes this statement:

CounterBtn.Text = $"Clicked {count} time";
That sets the text Go back to the window with the XAML code. Find this line:


Every control can have a name. The x:Name property sets the name of the control—in this case, the button is named CounterBtn—and your C# code can use that name to make the control do things.

THE XAML FOR YOUR BUTTON UP CLOSE

You’ve been editing the the XAML code in your MainPage.xaml file—are you starting to get comfortable with it? This is a great time to take a closer look at the part of your XAML that displays the button.

Here’s the Button tag. Take a look at each of its five properties. Can you figure out what all do?

<Button
    x:Name="CounterBtn"
    Text="Click me"
    SemanticProperties.Hint="Counts the number of times you click"
    Clicked="OnCounterClicked"
    HorizontalOptions="Center" />
The x:Name property gives your control a name you can use in your code

The first property is x:Name, which sets the name of the control so you can use it in your C# code:

x:Name="CounterBtn"
You just saw a control name in action. When you clicked the button, the event handler method executed this statement to set the button’s text, using the name CounterBtn set by the x:Name property:

CounterBtn.Text = $"Clicked {count} time";
This line uses the CounterBtn name to update the text displayed on the button.

The x:Name property gives your control a name you can use in your code

The next property determines what text is displayed n the button:

Text="Click me"
The button displays “Click me” when you first run the app. That line of code in the method changes the text to “Clicked 1 time” the first time you click it, then “Clicked 2 times” when you click it again. That line of code starts with the name of the control (CounterBtn), followed by a period, followed by Text, the name of the property.

SemanticProperties help you make your apps accessible

When we create our apps, we want everyone to be able to use them—and that includes people with disabilities.

A screen reader is a tool that lets people who are blind, visually impaired, or have learning disabilities or other conditions that interfere with their ability to read use our visual apps. Semantic properties help your app work with a screen reader.


Use a screen reader to experiment with the SemanticProperites.Hint property

The best way to make your apps accessible is to use them the way someone with accessibility issues would—in this case, using a screen reader built into your operating system.

In Windows, start the Narrator app. You can run it from the Start menu, or use Windows logo key + Ctrl + Enter to turn Narrator on or off, and Windows logo key + Ctrl + N to bring up Narrator settings. Narrator will display a window with an overview of how Narrator works. It will also start to read the contents of that window, displaying a box around the section of the window that it’s readingh. You can go back to that window to turn of Narrator.

In MacOS, start the VoiceOver utility. It lives in the Applications/Utilities folder, but if your keyboard has Touch ID, the easiest way to turn it on or off is to press and hold the Command key while you quickly press Touch ID three times. By default the VoiceOver utility displays a welcome dialog—press the V key or click the “Use Voiceover” button to start VoiceOver.

Once you have Narrator or VoiceOver running, switch to your app window. You’ll hear a voice telling you details about what’s on the screen. People with visual impairments often have trouble using a mouse, so they use the keyboard to interact with apps—and you’ll do the same thing. Press the tab key to navigate to the “Click Here” button. The screen reader will announce that you are on a button. Listen closely—you’ll hear it speak the SemanticProperties.Hint value: “Counts the number of times you click”

Press Enter to click the button. Your app will execute code that includes this statement:

SemanticScreenReader.Announce(CounterBtn.Text);
When it does, the screen reader will announce the contents of the button (“Clicked 1 time”).

The Clicked property tells your app what event handler method to run when the button is clicked

Take a look at the next property in the button’s XAML code:

Clicked="OnCounterClicked"
When you clicked the button, your app used that property to figure out which method to run. You saw this in action when you placed a breakpoint on the first line of that method.

The HorizontalOptions property centers your button

When you run your app, the “Click Me” button is centered in the middle of the window. Go back to the code editor, select the word Center in that line of XAML code, and type C. Visual Studio will display an IntelliSense pop-up with all of the different options. Try selecting Start or End, then ren your app again—now the button will be displayed on the left or right side of the window. Experiment with all of the different horizontal options for Button control.


Add an Entry control to your app
And Entry control gives your user a box where they can enter text. You’ll add one your app—and you’ll use a really useful tool in Visual Studio to do it: the Toolbox window. The The Toolbox is a feature of Visual Studio that makes it easy to add controls to your app.

Stop your app, then open the MainPage.xaml editor window in Visual Studio.

Place your mouse cursor just after the closing /> bracket at the end of your Button control tag, then press enter three times to add three blank lines. Click on the second line that you just added, so there’s a blank line above your mouse cursor and another blank line below it.

Open the Toolbox window in Visual Studio (if it isn’t already open) by choosing “Toolbox” from the View menu.

Double-click Entry in the Toolbox window. Visual Studio will automatically add an <Entry> tag at your cursor location, on that middle blank line you added.


Here’s what you should see in your XAML code:


Now run your app. Congratulations, you just added a control for entering text!


Add properties to your Entry control
Let’s make your Entry control a little more usable by adding placeholder text, or text that appears in a lighter color to help the user understand what they’re supposed to enter.

Edit the XAML code for your Entry control to add a Placeholder property. And since we always want our apps to be accessible to people who use screen readers, add a SemanticProperties.Hint property too. Notice that when you add the properties, they show up in Visual Studio’s typeahead pop-up window, making it easier for you to add them.

Your Entry tag should look like this:

<Entry 
    Placeholder="Enter some text" 
    SemanticProperties.Hint="Lets you enter some text" />
Now run your app – you’ll see a new Entry control at the bottom. The placeholder text will appear as (“Enter some text” in a lighter color, and will disappear as soon as you you type text into it.



THERE ARE NO DUMB QUESTIONS
Q: Why did the Entry control get added to the bottom of my app? How did it know where in the window to display?

A: When you created a new .NET MAUI app, Visual Studio used a template that generated the XAML code for the main page in the MainPage.xaml file. This file contains a set of nested tags, or tags that contain other tags—so one tag’s start and end appear after the start and before the end of another tag. Each of these tags creates a specific kind of control that determines how the page is displayed.

The outermost tag in your app’s XAML is a <ContentPage> opening tag, which defines a single view that contains the rest of the page. If you scroll down to the bottom of the file, you’ll see the closing </ContentPage> tag. Right inside that <ContentPage> is a <ScrollView> tag—everything between the opening <ScrollView> and closing </ScrollView> tags defines contents that will automatically display a scrollbar that lets you scroll up and down if it’s too long for the page. The <ScrollView> tag contains a <VerticalStackLayout> tag, with a matching </VerticalStackLayout> closing tag at the bottom. A VerticalStackLayout can contain a series of controls, one after another. Each of those controls will be displayed on the page in a vertical stack, in the order that they appear in the file.

So since the Entry control is at the bottom of the file just above the closing </VerticalStackLayout> tag, it will appear at the bottom of the page. And because it’s nested inside the <ScrollView>...</ScrollView> tags, if you make your window shorter than the height of the page, you’ll be able to scroll down to it.

Make your Entry control update a Label
Your app already has two Label controls. Let’s add a third one and make it display everything the Entry does, so when you enter or update text in the Entry it automatically updates the Label.

 Use the Toolbox to add a new Label control to the bottom of your page.

When you drag the label out of the Toolbox, it will have an empty Text property:

<Label Text="" />
Change the Text property to make it display text. Then give it a SemanticProperties.Description property. This is what will get read aloud if your user is using a screen reader:


 Use the Toolbox to add a second Label control under the one you just added.

Every time the user changes the text in your Entry control, the app will update this new Label to show the text that they typed. Drag a new Label control out of the Toolbox and drop it in your XAML code between the Label control that you just added and the closing </VerticalStackLayout> tag. Then set its properties:

 You’ll be writing code to set the label text, so delete the Text property.

 Since you’re going to write code that updates the Label, you’ll need to give it a name. Use an x:Name property to name it EntryOutput: x:Name="EnteredText"

 Keep making your app acceessible by adding a description for people using a screen reader: SemanticProperties.Description="The text that the user entered"

Your new Label should look like this:

<Label x:Name="EnteredText"
     SemanticProperties.Description="The text that the user entered" />
 Give your label a background color.

Add a BackgroundColor property. When you start typing, Visual Studio will pop up a IntelliSense window. Choose Gold for the background color.


 Use the Properties window to add a bottom margin.

So far you’ve been adding properties by writing XAML code by hand. Luckily, Visual Studio has some useful tools to help you edit your XAML. The Properties window gives you an easy way to edit the properties on your controls.

Click the XAML for your Label control so the cursor is somewhere between the tags. Go to the Properties window (if you don’t see it, use the View menu to display it) and find Margin. Enter 20 for the lower margin to give it a 20 pixel magin (where a pixel is 1/96th of an inch on an unscaled screen).


Your property should now look like this:

<Label x:Name="EnteredText"
    SemanticProperties.Description="The text that the user entered" 
    BackgroundColor="Gold" Margin="0,0,0,20"/>
 Add an event handler method.

Back in Chapter 1 you used event handler methods so your Animal Matching Game could respond to mouse clicks and timer ticks. Now you know more about C# methods—this is a good chance to apply that knowledge by creating a new event handler method to update the EnteredText control ever time the user types in the Entry control. Add a TextChanged property to your Entry control. When it comes time to enter the value, Visual Studio will suggest the value <New Event Handler>:


Press return or use the mouse to accept the suggestion—this will cause Visual Studio to add a new event handler method called Entry_TextChanged automatically. You probably also noticed that it also displayed this message when you were adding the event handler:


Right-click on Entry_TextChanged and choose Go To Definition. This will open up MainPage.xaml.cs and jump directly to the method that Visual Studio added. Add this line of code to the method:

private void Entry_TextChanged(object sender, TextChangedEventArgs e)
{
      EnteredText.Text = e.NewTextValue;
}
Now run your app. You should see a label that says “Here’s what you typed:” followed by a gold-colored label. Click on the Entry control and type some text—it will appear in the gold-colored label immediately.


NOTE
One of our big goals with this book is to help you learn important skills that will help you become an all-around great developer. Understanding your users is a really important skill, and paying attention to accessibility is a great way to get better at it!

When you pay attention to accessibility, it makes your app—and your code!—better.

When you’re building apps, it’s always a great idea to create them so as many people can use them as possible, including people with disabilities—and not just because it’s the right thing to do. Building accessibility into your apps actually helps you become a better developer. Really!

Obviously, if you want to be a great developer, you need to get practice writing code: writing code is a skill, and the more code you write, the better you get at it. But there’s more to being a developer than “just” coding.

One of the biggest challenges that really experienced developers face is deciding exactly what they want to build. In fact, a lot of programmers will talk about the challenges of “building the software right and building the right software.” One of the most common problems in software engineering is building a great product that doesn’t do what your users need.

That’s where accessibility can help you. Building accessible code well means taking the time to really understand how people with disabilities will use your app. Taking the time to understand and empathize with them will help you build your app better—and it’s great practice for skills that will help you build the right software.

MAKE IT STICK

Here’s an great way to get accessibility ideas to stick in your brain—especially if you don’t have a disability. Turn on your screen reader, then leave it on while you code or do other work. Once you’re used to it, close your eyes and keep working. Can you work using just the screen reader?

NOTE
Using a screen reader is an effective way to really understandhow accessibility works.

EXERCISE

You added Entry and Label controls to your app—and Visual Studio’s Toolbox window, Properties window, and IntelliSense helped you. Can you add six more controls to your app to let your user enter numeric values?


Use the Toolbox window, Properties window, and Visual Studio editor to add a Stepper control, two Label controls, a Slider control, and two more Label controls to your app.

The two Label controls that display the values should have the BackgroundColor property set to LightBlue. Name them StepperValue and SliderValue. Make sure you add SematicProperties.Description properties.

You want your app to automatically update those the StepperValue control every time the the stepper value changes, so add a ValueChanged event handler to the Stepper control. Add this line of code to the event handler:

StepperValue.Text = e.NewValue.ToString();
Then add a ValueChanged event handler to the Slider control. It should be identical, except that it updates the SliderValue label instead of the StepperValue label.

Don’t forget to add SemanticDescription.Hint properties to your Stepper and Slider controls.

EXERCISE SOLUTION

Here’s the XAML to add the six controls to MainPage.xaml:


Here are the event handler methods to add to MainPage.xaml.cs:


 
In the exercise instructions, we gave you this line of code:

SliderValue.Text = e.NewValue.ToString();
What do you think .ToString() does?

NOTE
Here’s a hint: Stepper and Slider controls can only provide numeric values, but labels can only display text.

Combine horizontal and vertical stack layouts
In this last part of the exercise you’ll add a Picker control, which displays a list of items that you can pick from. You’ll also use a Label control to display the values that were picked. Here’s what it will look like:


Notice how the Label and Picker controls are next to each other? You’ll get that layout by using a HorizontalStackLayout control. It works just like the VerticalStackLayout control causes all of the controls you’ve added to your app so far to be stacked on top of each other, except instead they get stacked next to each other.

You’ll nest one Layout inside another
We’ll use nesting—where one layout control lives inside another one—to create a more complex layout.

Here’s how it will work:



Add a Picker control to display a list of choices
A Picker control displays a list of items in a dropdown so the user can pick one of them. Let’s add one to your app.

 Add the XAML for a Picker control and a Label for it to update.

You’ve already seen how a VerticalStackLayout control lets you stack controls on top of each other. You can also stack controls horizontally by adding a HorizontalStackLayout control.

Go ahead and add this XAML code just above the closing </VerticalStackLayout> tag. You can type it all or use the Toolbox. When you add Clicked event for the button, press Tab to let Visual Studio generate an event handler method for you, just like you did earlier..


 Initialize the Picker with a list of birds.

Open the MainPage.xaml.cs file and find the MainPage method at the top. This method gets run every time the page loads. Insert two lines after InitializeComponent(); and add this code.


 Fill in the event handler for the Button control.

When you added the XAML for the Button control, you used Visual Studio’s IntellliSense pop-up to help you add a new event handler to the C# code:


Since you used the x:Name property to name your Picker control AddBird, Visual Studio created an empty event handler method called AddBird_Clicked:

private void AddBird_Clicked(object sender, EventArgs e)
{

}
Add this line of code to the AddBird_Clicked method:

private void AddBird_Clicked(object sender, EventArgs e)
{
    Birds.Text = Birds.Text + Environment.NewLine + BirdPicker.SelectedItem;
}
Take a closer look at the line of code—let’s break down exactly what it does.

The line starts with Birds.Text = ... which means it’s setting the text in the Bird label.

The text is being set to Birds.Text + followed by additional things—this means it’s going to take whatever is in the Label and append text to it, or add additional text to the end.

The first thing that gets appended is Environment.NewLine, which adds a line break. The Label control will display multi-line text, adding a line break every time it sees a line break.

After the line break, it appends BirdPicker.SelectedItem—this is the item that’s currently selected in the Picker control.

 Run your app and use your new Picker control.

Scroll to the bottom of the app, choose a bird from the Picker, and click the Add a bird button—it will get added to the Label that contains the birds. Select a few more birds and add them.



You’re right! The app doesn’t match the screenshot.

Take a look at the screenshot we showed you earlier:


Run your app and try adding those same birds. When you get to the first owl, you’ll see extra space at the top of the Label:


Looks like we’ve got a bug. Time to put on your Sherlock Holmes cap. Let’s sleuth out this bug!

SLEUTH IT OUT

The Case of the Extraneous Space

Understanding a bug is the first step in fixing it.

In the last chapter, we looked at the code carefully and found several clues to help us solve the Case of the Unexpected Match. But as you keep going through this book, your apps will get longer and longer, and while looking at the code is a good start, it may not always be the best way to figure out what’s causing a bug.

Luckily, the Visual Studio debugger is a great tool for that. (That’s why it’s called a debugger: it’s a tool that helps you get rid of bugs!)

Reproduce the bug

It’s obvious that there’s a problem! But as Sherlock Holmes once said, “There is nothing more deceptive than an obvious fact.” When you’re sleuthing out bugs, can’t just rely on what’s obvious. You need to confirm for yourself exactly what’s going on. The way to do that is to reproduce the bug.

Stop your app. Make sure it’s not running, so you’ve got a fresh start. Then do this:

Start your app again

Pick Duck and click the “Add a bird” button

Pick Ostrich and click the “Add a bird” button

Pick Pigeon and click the “Add a bird” button

Pick Duck and click the “Add a bird” button

Pick Owl and click the “Add a bird” button

Your app should now look exactly like the screenshot:


“There is nothing more deceptive than an obvious fact.”

— Sherlock Holmes

Now restart your app, then try it again with different birds. You should still see extra space at the top of the Label. You can make the bug happen over and over again, at will. That means the problem is reproducible: you can follow a set of stpes to make it happen. Reproducing a bug is a great first step to fixing it.

Before you go on, can you sleuth out what’s causing the extra space to get added?

Every good investigation starts by identifying a list of suspects

When you’re tracking down a bug, what’s the first thing you should do? You could start placing breakpoints in the code… but where? The first step in debugging is thinking. Look at your code, think about how it works, and try to imagine where the bug might be. That will help you figure out where to put your breakpoints.

So let’s think through the code. It starts with a button—and the button calls a method:

<Button x:Name=”AddBird” Clicked=”AddBird_Clicked” Text=”Add a bird”
        Margin=”0,0,0,20” SemanticProperties.Hint=”Adds a bird”/>
All of the code to add the bird to the Label is in that AddBird_Clicked method. Now we have a suspect!

IDE TIP: USING THE DEBUGGER
You’re going to be using the debugger a lot in this book! We’ve walked you through it a few times, but you’re as you get further in the book and write more and more code, you should feel comfortable using the debugger on your own.

Let’s start with a few tips to help you get comfortable debugging your code.

 Think before you debug. Read through your code. Understand how it works (and not just how you think it works).

 Use the Watch window, Locals window, and hovering over variables to keep track of their values. They all do the same thing—show you the value of a variable—so you can decide which one you feel most comfortable with.

 Don’t be afraid to restart your app. Stop and start your code frequently—every time you run your code, you’re running an experiment. Run it as many times as it takes to understand what’s going on.

Here’s a handly list of the debugger commands. They may feel strange at first, but they’ll be second nature soon.

 When you press the triangle Run button in the toolbar or choose Start Debugging (F5 or ⌘↵), Visual Studio starts running your code in the debugger. You can place a breakpoint whether or not the debugger is running.

 To place a breakpoint, click on a line of code and choose Toggle Breakpoint (F9 or ⌘/) form the Debug menu.

 When your code hits a breakpoint, it stops running so you can inspect variables.

 When Visual Studio breaks on a breakpoint, the toolbar shows you the commands you can use to keep executing. Debugging code can be a little weird to get used to if you haven’t done it before, so try sticking to just these four commands—here’s where you’ll find them in the toolbar (for Windows or macOS) and using keyboard shortcuts:



Add a breakpoint and start debugging the code

Now that we have a suspect, let’s catch it in the act. Add a breakpoint to the line in the AddBird_Clicked method:


Now run your code. Pick a bird, then click the “Add a bird” button. The debugger stops on your breakpoint. Next, add a watch for Birds.Text, just like you did earlier in the chapter. The value should be null.


Then step over that line of code (F10 on Windows or ⇧⌘O on macOS) to run it. You should see this value:


The value of Birds.Text is a string: \r\n followed by the bird you picked. What do you think \r\n does?

NOTE: If you’re using macOS, you’ll see \n instead of \r\n.

Continue debugging (F5 or ⌘↵) to start your app running again. Pick a different bird and step over the line of code. Now have a look at the Birds.Text watch:


Repeat the process a few more times: continue debugging, pick a bird, click the button, step over, check the watch. Eventually your Birds.Text value will look something like this (you’ll see \n instead of \r\n on macOS):

"\r\nPenguin\r\nOstrich\r\nPigeon\r\nDuck\r\nOwl\r\nPigeon\r\nDuck\r\nOwl"
You’ve probably figured out by now that the \r\n or \n is the line break. The first time the AddBird_Clicked method is called, the Label text is empty (that’s what the null value means), so when the app adds the current value (empty) plus a line break plus the bird, it adds an extra line break to at the start of the string.

Now that we’ve found the culprit, we can fix the app. Replace the AddBird_Clicked method with this code, which uses a special method, String.IsNullOrEmpty, which checks if a string is empty:


Run your app again and add a few birds to the Label—there’s no more empty space above it. Your app is fixed!


There are no unexplainable mysteries in your code. Every bug has an explanation, even if it takes work to figure out what’s going on and fix it.

Bugs can be weird! If you’ve been playing video games for a long time, you’ve probably experienced a few glitches, and some of them can be extremely odd. If you haven’t seend any yourself, try searching the web for videos of game glitches—even the most polished game has bugs.

Every bug you see is code behaving in a way you don’t expect. That’s why bugs need sleuthing out. Bugs can be confusing, mysterious, and sometimes extremely frustrating. It’s even tempting to think that something is fundamentally wrong, and the code will never work. Always remember that every bug has an explanation. Every bug is strange, but even a bug that appears to be a weird mystery is caused by something in your code—so you can fix it. Because like Sherlock Holmes once said, “It is a mistake to confound strangeness with mystery.”

BULLET POINTS
You’ll use many different controls to build your app’s user interface (or UI). The UI is the part of the application that your user interacts with.

The C# code for a page in a MAUI app is called code-behind. The XAML code and the C# code in the code-behind file work together to make the page work.

The x:Name property gives your control a name you can use in your code.

When you pay attention to accessibility, it makes your app—and your code!—better. Semantic properties help you make your apps accessible by providing descriptions and hints for people who use screen readers.

In XAML you can have nested controls, or tags that contain other controls, so one control’s start and end tag appear after the start tag and before the end of another tag.

You can use nested HorizontalStackLayout and VerticalStackLayout controls to create more complex layouts.

The first step in debugging is thinking: look at your code, think about how it works, and try to imagine where the bug might be.

Reproducing a bug is an important tool that helps you fix it. When you’re debugging, you’re running an experiment every time you run your code. Run it as many times as it takes to understand what’s going on.


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


2. Variables, Statements, and Methods: Dive into C# code
3. Namespaces and Classes: Organizing your code
4. Data, Types, Objects, and References: Managing your App’s Data
12h 51m remaining
Chapter 3. Namespaces and Classes: Organizing your code
A NOTE FOR EARLY RELEASE READERS
With Early Release ebooks, you get books in their earliest form—the authors’ raw and unedited content as they write—so you can take advantage of these technologies long before the official release of these titles.

This will be the 3rd chapter of the final book. Please note that the GitHub repo will be made active later on.

If you have comments about how we might improve the content and/or examples in this book, or if you notice missing material within this chapter, please reach out to the editor at mcronin@oreilly.com.


Great developers keep their code and data organized. What’s the first thing you do when you’re creating an app? You think about what it’s supposed to do, whether you’re solving a problem, creating a game, or just having fun. But it’s not always obvious how individual statements fit into your app’s bigger picture… and that’s where classes come in. They let you organize your code around the features you’re creating and the problems the app needs to solve. Classes can help you organize your data too, by using them to create objects that represent any “thing” your app needs to know about—and the classes that you design serve as “blueprints” for the objects used in your app.

Classes help you organize your code
Let’s be honest… you’re going to write a lot of code throughout this book. And as you keep going through the chapters, your projects will get bigger and bigger. This is a good thing!

Bigger apps present an interesting challenge. The app you built at the end of Chapter 2 had just a few methods. If you create a console app with the same number of methods, there’s no reason not to put them all in Program.cs.

By the time you get to the end of the book, you’ll be creating apps with dozens of methods. If you put all of those methods into one big Program.cs file, you’ll have a hard time remembering which ones do what—and you’ll drive yourself crazy trying to sleuth out bugs!

Luckily, C# has an answer for this organizational challenge. Your C# code is organized into classes, or units of code that contain methods. You could still put all of your methods into one big class, and many small apps could have just one class. But when you have a lot of code, it makes sense to organize your classes based on what they do. When your classes are organized in a way that’s intuitive, it helps you figure out where to add new methods —and it makes sleuthing out bugs a lot easier.

ANATOMY OF A C# APP


Every C# program’s code is structured in exactly the same way. All programs use namespaces, classes, and methods to make your code easier to manage.


If code is useful, classes can help you reuse it
Developers have been reusing code since the earliest days of programming, and it’s not hard to see why. If you’ve written a class for one program, and you have another program that needs code that does exactly the same thing, then it makes sense to reuse the same class in your new program. So if we were going to build an app called PetManager, we might organize the code using classes called Dog and Cat.


Some methods take parameters and return a value
You’ve seen methods that do things, like the SetUpGame method in Chapter 1 that sets up your game. Methods can do more than that: they can use parameters to get input, do something with that input, and then generate output with a return value that can be used by the statement that called the method.


Parameters are values that the method uses as input. They’re declared as variables that are included in the method declaration (between the parentheses). The return value is a value that’s calculated or generated inside the method, and sent back to the statement that called that method. The type of the return value (like string or int) is called the return type. If a method has a return type, then it must use a return statement.

Here’s an example of a method with two int parameters and an int return type:


The method takes two parameters called factor1 and factor2. It uses the multiplication operator * to calculate the result, which it returns using the return keyword.

This code calls the Multiply method and stores the result in a variable called area:


A method’s parameters let you give it information that it can use, and its return value lets you use the result of the method in the statement that called it.

Visual Studio helps you explore parameters and return values
In the next app, you’ll be using a .NET method called Console.ReadLine to get a line that the user types into the console. Once you add the line to your app, you can hover over it to see more about it:


The IDE will pop up a box telling you what the method does. The very first thing in the box is its return type—in this case, it’s a string? value that holds text. We’ll learn a lot more about how strings work in the next chapter. In the meantime, what you need to know is that you call the method like this:

string? line = Console.ReadLine();
This calls the method to read a line of input, and stores the text the user typed in a variable called line.

You’ll also use a method called int.TryParse(), which you’ll use in an if statement like this:


The IDE is telling you that it takes two parameters, a string? value and an out int value. (We’ll learn a lot more about the out keywords later in the book—for now, we’ll give you the code to use.).

DO THIS!


Since you’re about to create methods that return values, right now is a perfect time to write some code and use the debugger to really dig into how the return statement works.

* What happens when a method is done executing all of its statements? See for yourself—open up one of the programs you’ve written so far, place a breakpoint inside a method, then keep stepping through it.

* When the method runs out of statements, it returns to the statement that called it and continues executing the next statement after that.

* A method can also include a return statement, which causes it to immediately exit without executing any of its other statements. Try adding a return statement in the middle of a method, then stepping over it.

Let’s build an app that picks random cards
In the first project in this chapter, you’re going to build a console app called PickRandomCards that lets you pick random playing cards.

Let’s use it as a way to start using classes. Here’s what its structure will look like:




You’ll use an array to store the cards
Your PickSomeCards method will use string values to represent playing cards. Let’s say you want to use your CardPicker class to pick five random cards and store them in a variable called cards. Here’s how you would do that:

string[] cards = CardPicker.PickSomeCards(5);
There’s a lot going on in that line of code, so let’s break it down. The PickSomeCards method is in the CardPicker class, but we’re calling it from a top-level statement, so we need to use the class name to call it:

string[] cards = CardPicker.PickSomeCards(5);
We just learned about how methods can take parameters. The PickSomeCards method takes an int parameter, and we’re passing the method the value 5 to tell it to pick five cards:

string[] cards = CardPicker.PickSomeCards(5);
The first part of the statement declares the cards variable. We just learned about return values—so the method will return a value that gets stored in the cards variable. But something looks different about it:

string[] cards = CardPicker.PickSomeCards(5);
The cards variable has a type that you haven’t seen yet. Look closely at the type:

string[] cards = CardPicker.PickSomeCards(5);
The square brackets [] mean that it’s an array of strings. Arrays let you use a single variable to store multiple values—in this case, strings with playing cards—which will get stored in the cards variable.

You can use a collection expression to create an array of values by comma-separated values between two square brackets []. Here’s an example of a string array that the PickSomeCards method might return:


After your array is generated, you can use a foreach loop to write each of the cards to the console:

foreach (string card in cards) {
    Console.WriteLine(card);
}
For the array above, running that foreach loop will generate this output:

10 of Diamonds
6 of Clubs
7 of Spades
Ace of Diamonds
Ace of Hearts

Create an app with a Main method
When you created console apps in the first two chapters, the IDE generated a two-line Program.cs file:

// See https://aka.ms/new-console-template for more information
Console.WriteLine("Hello, World!");
You may not have realized it at the time, but you were taking advantage of a very useful feature of C# called top-level statements that lets you start creating a console app with a simple file that contains a set of statements that get executed in order.

Top-level statements are really convenient! A good way to understand what they do for you and how they work is to create a C# app that doesn’t use top-level statements.

Create your PickRandomCards app without top-level statements

Use Visual Studio to create a new console app called PickRandomCards. But unlike previous chapters, when you’re going through the steps to create the app keep an eye out for a checkbox like this and make sure that it’s checked:


When you create your new app, your Program.cs file should look like this:


When the IDE created your app and generated the Program.cs file, it added a class called Program. This program was generated with one method called Main. The code inside the Main method is the familiar statement that prints “Hello, World!” to the console.

Run your app—it should look very familiar. Your new app does exactly the same thing as the “Hello, World!” app you created in Chapter 1. But instead of starting at the first statement in the Program.cs file, the first thing your app does is execute the Main method.

Your app can only have one entry point. If you add another class with a Main method, your code won’t build.

WATCH IT!

Visual Studio remembers your checkbox choices.

The next time you create a Console App project in Visual Studio, it may remember that you checked the “Do not use top-level statements” box and check it again for you. Make sure it’s unchecked the next time you create a console app.

TOP-LEVEL STATEMENTS BEHIND THE SCENES

Here’s what happens when you use top-level statements

Here’s the very first app that you created in Chapter 1:

// See https://aka.ms/new-console-template for more information
Console.WriteLine("Hello, World!");
The first line is a comment, so there’s actually only one statement in this app. When you build the app, the compiler—the part of Visual Studio that turns your C# code into something that your operating system can execute—reads all of the lines in the top-level statement and adds them to a class. It creates a class that looks like the one that you just saw in your PickRandomCards app:

internal class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello, World!");
    }
}
That looks a lot like the Program class that Visual Studio just created in your PickRandomCards app. But there’s one difference—can you spot it?

Here’s the Program class from your PickRandomCards app without top-level statements—we’ve made text that’s the same a lighter color so you can see the difference:


In an app with top-level statements, the code in your Program.cs file is not in a namespace. Every method in a C# program must be inside a class, but it’s okay for classes to be outside of namespaces.

We’ll learn more about how to work with namespaces work later in this chapter.

The rest of the console apps in this book will use top-level statements, so when you create the next one make sure to uncheck the “Do not use top-level statements” checkbox.


At the time we’re writing this, VSCode does not have the option to create a console app that does not use top-level statements. Just create your console app just like you did in Chapters 1 and 2, then replace the contents of Program.cs with the code we just showed you.

Add a class called CardPicker to your app
The next thing you’ll do is add a class called CardPicker to your app. Here’s a class diagram that shows information about the class you’ll build, including the methods that you’ll add to your CardPicker class:


Luckily, both Visual Studio and VSCode will help you add a new class to your project.

For Visual Studio: Right-click on the PickRandomCards project in the Solution Explorer—it’s the second row, underneath the solution (which has the same name). When the right-mouse menu pops up, choose Add >> Class… (Shift-Alt-C). (If you don’t want to do all that clicking, you can also choose Add Class... from the Project menu instead of right-clicking on the project name to jump straight to the filename prompt.) Enter CardPicker.cs when you’re asked for a filename. You should now see a new file called CardPicker.cs file in your Solution Explorer.


For VSCode: Right-click on the PickRandomCards project in the Solution Explorer—it’s the second row, underneath the solution (which has the same name. When the right-mouse menu pops up, choose Add New File... VSCode will display a list of templates at the top of the window and ask you to choose one. Choose Class. VSCode will then display a prompt at the top of the window asking you for a filename. Enter CardPicker.cs. You should now see a new file called CardPicker.cs file in your Solution Explorer.


SHARPEN YOUR PENCIL

Double-click on CardPicker.cs in the Solution Explorer to open it. The code in the file will look slightly different depending on whether you used Visual Studio or VSCode.

Here’s what your file will look like if you’re using Visual Studio:


Here’s what it will look like if you’re using VSCode:


Compare the code in these two screenshots. You should be able to spot three important differences. Write them down:


SHARPEN YOUR PENCIL SOLUTION

We asked you to compare the code in two screenshots. Here’s the screenshot from Visual Studio:


Did you spot these three differences?


Use Quick Actions to remove unnecessary ‘using’ lines
If you’re using Visual Studio, you’ll see five lines at the top of your CardPicker.cs file that start with using. These are using directives, and you’ll learn about them later in the book. But for now, they’re not needed.

Luckily, Visual Studio makes it easy to remove those unnecessary using directives from your file, which is good for us because we want to keep things simple and easy to read. Click anywhere in the top five lines. Visual Studio will display the Quick Actions light bulb icon to indicate that there’s a quick action available: 

Choose the Remove Unnecessary Usings quick action. Visual Studio will remove the five using lines.


Convert between namespace styles
Let’s compare the Visual Studio and VSCode versions of the CardPicker.cs file again, this time with the unnecessary using directives at the top of the Visual Studio version removed.

If you’re using Visual Studio, your CardPicker.cs file uses a block-scoped namespace. The namespace keyword is followed by the name of the namespace (PickRandomCards), which is followed by a block of code inside { brackets } and everything between those brackets is in the PickRandomCards namespace.

namespace PickRandomCards
{
    internal class CardPicker
    {
    }
}
If you’re using Visual Studio, your CardPicker.cs file uses a file-scoped namespace. The namespace keyword is followed by the name of the namespace (PickRandomCards) and a semicolon. Everything in the entire file is in the PickRandomCards namespace

namespace PickRandomCards;

public class CardPicker
{

}
This is the second difference you spotted in the ‘Sharpen your pencil’ exercise. Both ways to define a namespace are valid. They’re two different ways to say the same thing: the CardPicker class is inside the PickRandomCards namespace.

Click on the namespace line in your file. You’ll see a lightbulb icon  indicating that there’s a quick action available (the icon looks a little different in VSCode). Click the icon (or press Ctrl+. or .) to bring up the Quick Actions menu:

* If your file has a block-scoped namespace, you’ll see a Convert to file-scoped namespace quick action.

* If your file has a file-scoped namespace, you’ll see a Convert to block-scoped namespace quick action.

Choose the quick action to convert to the other namespace style. Then do the same thing and convert it back. Choose the style you like the best—they both work exactly the same way. You can switch namespace styles at any time.

RELAX

We’ll usually use file-scoped namespaces in the code in this book

Your code will behave exactly the same whether you use block-scoped or file-scoped namespaces. We’ll usually use file-scoped namespaces when we’re showing the code in this book, especially in Console App projects, because it takes up less room on the page: file-scoped namespaces don’t need the extra lines for the opening and closing brackets, and the code doesn’t need to be indented as much.

Also—we didn’t talk about the third difference from the ‘Sharpen your pencil’ exercise. The code generated by Visual Studio has the internal keyword, while the code generated by VSCode has the public keyword. Those are called access modifiers. We’ll talk more about them later in the book.

Use the new keyword to create an array of strings

Let’s say you want to create an array of 5 strings and store it in a variable called myStrings. You can use the new keyword to create a new array of strings. You can create your array of 5 strings like this:

string myStrings = new string[5];
You can also use a variable, field, or method parameter instead of a number. Your PickSomeCards method has a parameter called numberOfCards—you’ll use that parameter in your new statement: new string[numberOfCards];

The PickSomeCards method will pick five random cards. Each of the cards will have a random value and a random suit, so the class will also have two more methods that generate the value and suit for each card.

 Add a new PickSomeCards method to your CardPicker class.

Put your cursor between the curly brackets, press enter to add a space, and carefully type in this method:


 Create a new array of strings and store it in a variable called pickedCards.

We saw earlier that the PickSomeCards method will return an array of strings, so the first thing we’ll need is an array of strings to return. Add this line of code to your method:


Now the method has a string array to work with.

 Add a foreach loop to set the value of each card in the array.

Your method has an array of strings. Now it needs to set them. Add this foreach loop—it will call two methods called RandomValue and RandomSuit. Those methods don’t exist yet, but that’s okay.


 Finish the method by adding a return statement.

Add a return statement to send the pickedCards array back to the statement that called the method.


 Generate the RandomValue and RandomSuit methods.

In the last chapter, you generated a method called OperatorExamples. Follow exactly the same steps to generate a method in the CardPicker class called RandomSuit. Then do exactly the same thing to generate a method called RandomValue.

A method can have more than one return statement, and when it executes one of those statements it immediately returns, and does not execute any more statements in the method.

 Implement the RandomSuit method.

Every card has a suit: Hearts, Clubs, Spades, or Diamonds. The RandomSuit method will pick a suit at random, store it in a string, and return it. It will use the same random number generator, Random.Shared, that you used in Chapter 1 to pick emoji from a list. The random number generator’s Next method can take two parameters: random.Next(1, 5) returns a number that’s at least 1 but less than 5—in other words, calling Random.Shared.Next(1, 5) returns a random number from 1 to 4.

Let’s add code to your RandomSuit method that takes advantage of return statements to stop executing the method as soon as it finds a match—we added a comment to each line to explain how it works:


The return statement causes your method to stop immediately and go back to the statement that called it.

 Implement the RandomValue method.

Every playing card can have one of 13 values—Ace, 2 through 10, Jack, Queen, or King. Here’s the RandomValue method that generates a random value. Look closely at it. Can you figure out how it works?


Here’s the code for your finished CardPicker class
Your CardPicker class is in the PickRandomCards namespace and has the methods that we just added:


It’s okay if your methods are in a different order.

EXERCISE

Now that your CardPicker class has a method to pick random cards, you’ve got everything you need to finish your console app by filling in the Main method. You just need a few useful methods to make your console app read a line of input from the user and use it to pick a number of cards.

Useful method #1: Console.Write

You’ve already seen the Console.WriteLine method. Here’s its cousin, Console.Write, which writes text to the console but doesn’t add a new line at the end. You’ll use it to display a message to the user:

Console.Write("Enter the number of cards to pick: ");
Useful method #2: Console.ReadLine

The Console.ReadLine method reads a line of text from the input and returns a string. You’ll use it to let the user tell you how many cards to pick:


Useful method #3: int.TryParse

Your CardPicker.PickSomeCards method takes an int parameter. The line of input you get from the user is a string, so you’ll need a way to convert it to an int. You’ll use the int.TryParse method for that:


Put it all together

Your job is to take these three new pieces and put them together in a brand-new Main method for your console app. Modify your Program.cs file and replace the “Hello World!” line in the Main method with code that does this:

* Use Console.Write to ask the user for the number of cards to pick.

* Use Console.ReadLine to read a line of input into a string variable called line.

* Use int.TryParse to try to convert it to an int variable called numberOfCards.

* If the user input could be converted to an int value, use your CardPicker class to pick the number of cards that the user specified: CardPicker.PickSomeCards(numberOfCards). Use a string[] variable to save the results, then use a foreach loop to call Console.WriteLine on each card in the array. Flip back to Chapter 1 to see an example of a foreach loop—you’ll use it to loop through every element of the array. Here’s the first line of the loop: foreach (string card in CardPicker.PickSomeCards(numberOfCards))

* If the user input could not be converted, use Console.WriteLine to write a message to the user indicating that the number was not valid.

EXERCISE SOLUTION

Here’s the Main method for your console app. It replaces the one that Visual Studio created for you that prints “Hello, World!” This method prompts the user for the number of cards to pick, attempts to convert it to an int, and then uses the PickSomeCards method in the CardPicker class to pick that number of cards. PickSomeCards returns each of the picked cards in an array of strings, so it uses a foreach loop to write each of them to the console.


Here’s what it looks like when you run your console app:


Take the time to really understand how this program works–this is a great opportunity to use the Visual Studio debugger to help you explore your code. Place a breakpoint on the first line of the Main method, then use Step Into to step through the entire program. Add a watch for the value variable, and keep your eye on it as you step through the RandomSuit and RandomValue methods.

Ana’s working on her next game

Meet Ana. She’s an indie game developer. Her last game sold thousands of copies, and now she’s getting started on her next one.


Ana’s started working on some prototypes. She’s been working on the code for the alien enemies that the player has to avoid in one exciting part of the game, where the player needs to escape from their hideout while the aliens search for them. Ana’s written several methods that define the enemy behavior: searching the last location where the player was spotted, giving up the search after a while if the player wasn’t found, and capturing the player if the enemy gets too close.


Ana’s game is evolving…
The humans versus aliens idea is pretty good, but Ana’s not 100% sure that’s the direction she wants to go in. She’s also thinking about a nautical game where the player has to evade pirates. Or maybe it’s a zombie survival game set on a creepy farm. In all three of those ideas, she thinks the enemies will have different graphics, but their behavior can be driven by the same methods.




…so how can Ana make things easier for herself?
Ana’s not sure which direction the game should go in, so she wants to make a few different prototypes—and she wants them all to have the same code for the enemies, with the SearchForPlayer, StopSearching, SpottedPlayer, CommunicatePlayerLocation, and CapturePlayer methods. She’s got her work cut out for her.

BRAIN POWER

Can you think of a good way for Ana to use the same methods for enemies in different prototypes?


GAME DESIGN... AND BEYOND

Prototypes

A prototype is an early version of your game that you can play, test, learn from, and improve. A prototype can be a really valuable tool to help you make changes early. Prototypes are especially useful because they let you rapidly experiment with a lot of different ideas before you’ve made permanent decisions.

The first prototype is often a paper prototype, where you lay out the core elements of the game on paper. For example, you can learn a lot about your game by using sticky notes or index cards for the different elements of the game, and drawing out levels or play areas on large pieces of paper to move them around.

One good thing about building prototypes is that they help you get from an idea to a working, playable game very quickly. You learn the most about a game (or any kind of program) when you get working software into the hands of your players (or users).

Most games will go through many prototypes. This is your chance to try out lots of different things and learn from them. If something doesn’t go well, think of it as an experiment, not a mistake.

Prototyping is a skill, and just like any other skill, you get better at it with practice. Luckily, building prototypes is also fun, and a great way to get better at writing C# code.

Prototypes aren’t just used for games! When you need to build any kind of app, it’s often a great idea to build a prototype first to experiment with different ideas.

Build a paper prototype for a classic game
Paper prototypes are really useful for helping you figure out how a game will work before you start building it, which can save you a lot of time. There’s a fast way to get started building them—all you need is some paper and a pen or pencil. Start by choosing your favorite classic game. Platform games work especially well, so we chose one of the most popular, most recognizable classic video games ever made... but you can choose any game you’d like! Here’s what to do next.


 Draw the background on a piece of paper. Start your prototype by creating the background. In our prototype, the ground, bricks, and pipe don’t move, so we drew them on the paper. We also added the score, time, and other text at the top.

 Tear small scraps of paper and draw the moving parts. In our prototype, we drew the characters, the piranha plant, the mushroom, the fire flower, and the coins on separate scraps. If you’re not an artist, that’s absolutely fine! Just draw stick figures and rough shapes. Nobody else ever has to see this!

 “Play” the game. This is the fun part! Try to simulate player movement. Drag the player around the page. Make the non-player characters move too. It helps to spend a few minutes playing the game, then go back to your prototype and see if you can reproduce the motion as closely as possible. (It will feel a little weird at first, but that’s OK!)



NOTE
All of the tools and ideas in “Game Design... and Beyond” sections are important skills that go way beyond just game development—but we’ve found that they’re easier to learn when you try them with games first.

Yes! A paper prototype is a great first step for any project.

If you’re building a desktop app, a mobile app, or any other project that has a user interface, building a paper prototype is a great way to get started. Sometimes you need to create a few paper prototypes before you get the hang of it. That’s why we started with a paper prototype for a classic game…because that’s a great way to learn how to build paper prototypes. Prototyping is a really valuable skill for any kind of developer, not just a game developer.

SHARPEN YOUR PENCIL

In the next project, you’ll create a MAUI app that uses your CardPicker class to generate a set of random cards. In this paper-and-pencil exercise, you’ll build a paper prototype of your app to try out various design options.

Start by drawing the window frame on a large piece of paper and a label on a smaller scrap of paper.



Next, draw a bunch of different types of controls on more small scraps of paper. Drag them around the window and experiment with ways to fit them together. What design do you think works best? There’s no single right answer— there are lots of ways to design any app.


Build a MAUI version of your random card app
All of the code for picking random cards is conveniently organized into a class called CardPicker. Now you’ll reuse that class in a .NET MAUI app.

Here’s how the app will work.


Make your app accessible!
Accessibility is really important—and paying attention to accessibility is a great way to focus on important skills, like understanding your users and their needs.

* The Label and Entry controls each have a SemanticProperties. Description property so the screen reader will read it out loud.

* The Button control has a SemanticProperties.Hint property because the screen reader will read the contents of the button but we still want to give people who use accessibilty tools additional context for the control.

EXERCISE

You already have the tools you need to create the XAML for the MAUI card picker app! In this exercise, you’ll use what you learned about XAML in the first two chapters to create the main page for your app. You may need to go back to the XAML code you wrote in Chapter 2 to see how you added controls to your page.

Create a new .NET MAUI app called PickRandomCardsMAUI. Edit the MainPage.xaml.cs file to delete the controls inside the VerticalStackLayout (just like you did in Chapter 2), then add the controls for your card picker app.

Bonus: Edit the AppShell.xaml file to set the page title! We haven’t shown you how to do that yet—can you figure it out?


Peeking at the solution is not cheating! It’s actually a great way to get these ideas to stick in your brain.

EXERCISE SOLUTION

Your MainPage.xaml.cs file should have a public MainPage() method that calls InitializeComponent and an empty Clicked event handler method and nothing else.

Here’s the XAML for the contents of MainPage.xaml (we didn’t include the outer <ContentPage> tag):


We made this change to AppShell.xaml to set the title of the page to “Pick a card!”:


Make your MAUI app pick random cards
You’ve got an app that looks like it’s supposed to, and that’s a great start! In the second part of this project, you’ll make it work, so when the user enters a number and clicks the button it picks random cards. That’s where your CardPicker class comes in. You’ve already created a class that picks random cards. Now you just need to copy that class into your new APP. Once it’s copied, you’ll be able to make your button’s event handler method call the PickSomeCards method in the CardPicker class.

When your MAUI app builds, the code in the XAML file and the C# code in the code-behind file are combined together to create a new class that makes the page work.


Once you have code organized into a class, you can use that same class in two projects.

Reuse your the CardPicker class
You took the time to put all of the random card picking code into a convenient class. Now it’s time to take advantage of that class by reusing it in your new MAUI app.


 Choose ‘Add Existing Item’ or ‘Add Existing Files’ in Visual Studio. You created a file called CardPicker.cs in your PickRandomCards console app. Now you’ll tell Visual Studio to add that class file to your MAUI project, which will cause it to copy the file into your MAUI app’s project folder.

* In Visual Studio, right-click on the project in the Solution Explorer window and choose Add >> Existing Item... (Shift+Alt+A), or choose Add Existing Item from the Project menu.

* In VSCode, you’ll need to manually copy the file into the folder. Right-click on the project in the Solution Explorer and choose Reveal in File Explorer (or Reveal in Finder if you’re using a Mac). Use your operating system to copy the file into your project folder that VSCode opened. Once the file is copied, it will automatically appear in the Solution Explorer.

 Find your CardPicker.cs file and add it to your project.

Visual Studio will pop up a folder explorer window. Navigate to the folder with your PickACard console app and double-click on CardPicker.cs. You should now see CardPicker in the Solution Explorer.

 Try to use your CardPicker class in the MainPage.xaml.cs code.

Open MainPage.xaml.cs. Edit the PickCardsButton_Clicked event handler method and try adding a statement that calls your CardPicker.PickSomeCards method.


Add a using directive to use code in another namespace
You used either a file-scoped namespace or block-scoped namespace to put your CardPicker class in the PickRandomCards namespace. Compare the namespace declaration in your CardPicker class to the code at the top of your MainPage.xaml.cs file in your MAUI app:

namespace PickRandomCardsMAUI;

public partial class MainPage : ContentPage
{
  ... your MAUI app’s code is in the PickRandomCardsMAUI namespace ...
}
The reason your MainPage class can’t access the methods in your CardPicker class is because they’re in different namespaces.

Luckily, C# has an easy way to deal with this. You’ll add a using directive in your code that calls the methods in CardPicker—that’s a special line that you put at the top of a class file to tell it to use code in another namespace.


Add this line to the top of your MainPage.xaml.file.

If you chose a different name for your console app, replace PickRandomCards with then namespace in your CardPicker.cs file.


Now go back to the event handler method for your button. Start typing CardPicker. like you did before. Now Visual Studio will pop up its IntelliSense window, just like you’d expect it to.

EXERCISE

Here’s a C# coding challenge for you! Now that you added the using directive to the top of your MainPage.xaml.cs file, code in that file can use the CardPicker class. Can you finish your event handler method to make your app work?

To do this, you’ll need to add statements to the PickCardsButton_Clicked event handler method. Here’s what to do:

The first thing the method does is call int.TryParse to convert NumberOfCards.Text to a number.

If the number is valid, it calls CardPicker.PickSomeCards just like in your console app. If it isn’t, it makes the PickedCards label display a message: PickedCards.Text = "Please enter a valid number.";

Instead of writing to the console, it sets PickedCards.Text to a string value to make text appear in the PickedCards Label control. You can clear the text in PickedCards like this: PickedCards.Text = String.Empty;

After it clears the PickedCards label, it uses a foreach loop that works just like the one in your console app.

Add this statement after the foreach loop to tell the user how many cards they picked: PickedCards.Text += Environment.NewLine + "You picked " + numberOfCards + " cards.";

EXERCISE SOLUTION

Here’s the finished event handler method.


BULLET POINTS
Classes have methods that contain statements that perform actions. Well-designed classes have sensible method names.

Some methods have a return type. You set a method’s return type in its declaration. A method with a declaration that starts with the int keyword returns an int value. Here’s a statement that returns an int value: return 37;

When a method has a return type, it must have a return statement that returns a value that matches a return type. So if a method declaration has the string return type then you need a return statement that returns a string.

As soon as a return statement in a method executes, your program jumps back to the statement that called the method.

Not all methods have a return type. A method with a declaration that starts public void doesn’t return anything at all. You can still use a return statement to exit a void method, as in this example: if (finishedEarly) { return; }

Developers often reuse the same code in multiple programs. Classes can help you make your code more reusable.

When you select a control in the XAML code editor, you can edit its properties in the Properties window.

The XAML code combines with the C# code in the code-behind file to create a new class.

You can create an array of values using a collection expression by putting the values between a pair of square brackets [ ] and separating them with commas.

Ana’s prototypes look great…
Ana found out that whether her player was being chased by an alien, a pirate, a zombie, or an evil killer clown, she could use the same methods from her Enemy class to make them work. Her game is starting to shape up.


…but what if she wants more than one enemy?
And that’s great…until Ana wants more than one enemy, which is all there was in each of her early prototypes. What should she do to add a second or third enemy to her game?

Ana could copy the Enemy class code and paste it into two more class files. Then her program could use methods to control three different enemies at once. Technically, we’re reusing the code…right?

Hey Ana, what do you think of that idea?


Maintaining three copies of the same code is really messy.

A lot of problems you have to solve need a way to represent one thing a bunch of different times. In this case, it’s an enemy in a game, but it could be songs in a music player app, or contacts in a social media app. Those all have one thing in common: they always need to treat the same kind of thing in the same way, no matter how many of that thing they’re dealing with. Let’s see if we can find a better solution.

Ana can use objects to solve her problem
Objects are C#’s tool that you use to work with a bunch of similar things. Ana can use objects to program her Enemy class just once, and use it as many times as she wants in a program.



You use a class to build an object
A class is like a blueprint for an object. If you wanted to build five identical houses in a suburban housing development, you wouldn’t ask an architect to draw up five identical sets of blueprints. You’d just use one blueprint to build five houses.


A class defines its members, just like a blueprint defines the layout of the house. You can use one blueprint to make any number of houses, and you can use one class to make any number of objects.

An object gets its methods from its class
Once you build a class, you can create as many objects as you want from it using the new statement. When you do this, every method in your class becomes part of the object.


When you create a new object from a class, it’s called an instance of that class
You use the new keyword to create an object. All you need is a variable to use with it. Use the class as the variable type to declare the variable, so instead of int or bool, you’ll use a class like House or Enemy.



Yes! You’ve already created instances in your own code.

Go back to your animal matching program and look for this line of code:

Random random = new Random();
You created an instance of the Random class, and then you called its Next method. Now look at your CardPicker class and find the new statement. You’ve been using objects this whole time!

A better solution for Ana…brought to you by objects
Ana used objects to reuse the code in the Enemy class without all that messy copying that would’ve left duplicate code all over her project. Here’s how she did it.

 Ana created a Level class that stored the enemies in an Enemy array called enemyArray, just like you used string arrays to store cards and animal emoji.


 She used a loop that called new statements to create new instances of the Enemy class for the level and add them to an array of enemies.



 She called methods of each Enemy instance during every frame update to implement the enemy behavior.


When you create a new instance of a class, it’s called instantiating that class.


That’s right, we didn’t.

Some game prototypes are really simple, while others are much more complicated—but complicated programs follow the same patterns as simple ones. Ana’s game program is an example of how someone would use objects in real life. And this doesn’t just apply to game development! No matter what kind of program you’re building, you’ll use objects in exactly the same way that Ana did in her game. Ana’s example is just the starting point for getting this concept into your brain. We’ll give you lots more examples over the rest of the chapter—and this concept is so important that we’ll revisit it in future chapters, too.

Theory and practice
Speaking of patterns, here’s a pattern that you’ll see over and over again throughout the book. We’ll introduce a concept or idea (like objects) over the course of a few pages, using pictures and short code excerpts to demonstrate the idea. This is your opportunity to take a step back and try to understand what’s going on without having to worry about getting a program to work.


SHARPEN YOUR PENCIL

Now that you’ve got a better idea of how objects work, it’s a great time to go back to your CardPicker class and get to know the Random class that you’re using.

1. Open any Console App project that uses top-level statements (or create a new one). Press Enter to start a new statement, then type Random.Shared.—as soon as you type the second period, Visual Studio will pop up an IntelliSense window that shows its methods. Each method is marked with a cube icon (). We filled in some of the methods. Finish filling in the class diagram for the Random class.


2. Write code to create a new array of Doubles called randomDoubles, then use a for loop to add 20 double values to that array. Use the IntelliSense pop-up to help you choose the right method from the Random class to use in your code—make sure you’re calling the method that returns a random floating-point number that is greater than or equal to 0.0, and less than 1.0. (We’ll talk about what “floating point” means in the next chapter.)


SHARPEN YOUR PENCIL SOLUTION

Now that you’ve got a better idea of how objects work, it’s a great time to go back to your CardPicker class and get to know the Random class that you’re using.

1. Open any Console App project that uses top-level statements (or create a new one). Press Enter to start a new statement, then type Random.Shared.—as soon as you type the second period, Visual Studio will pop up an IntelliSense window that shows its methods. Each method is marked with a cube icon (). We filled in some of the methods. Finish filling in the class diagram for the Random class.


2. Write code to create a new array of Doubles called randomDoubles, then use a for loop to add 20 double values to that array. Use the IntelliSense pop-up to help you choose the right method from the Random class to use in your code—make sure you’re calling the method that returns a random floating-point number that is greater than or equal to 0.0, and less than 1.0. (We’ll talk about what “floating point” means in the next chapter.)


An instance uses fields to keep track of things
You’ve seen how classes can contain fields as well as methods. We just saw how you used the static keyword to declare a field in your CardPicker class:

static Random random = new Random();
What happens if you take away that static keyword? Then the field becomes an instance field, and every time you instantiate the class, the new instance that was created gets its own copy of that field.

NOTE
Sometimes people think the word “instantiate” sounds a little weird, but it makes sense when you think about what it means: creating a new instance of a class.

When we want to include fields in a class diagram, we’ll draw a horizontal line in the box. The fields go above the line, and methods go below the line.


Class diagrams typically list all of the fields and methods in the class. We call them the class members.

Methods are what an object does. Fields are what the object knows.
When Ana’s prototype created three instances of her Enemy class, each of those objects was used to keep track of a different enemy in the game. Every instance keeps separate copies of the same data: setting a field on the enemy2 instance won’t have any effect on the enemy1 or enemy3 instances.


An object’s behavior is defined by its methods, and it uses fields to keep track of its state.


Yes! That’s why you used the static keyword in your declarations.

Take another look at the method declarations in your CardPicker class:

public static string[] PickSomeCards(int numberOfCards)

private static string RandomValue()

private static string RandomSuit()
When you use the static keyword to declare a field or method in a class, you don’t need an instance of that class to access it. You just called your method like this:

CardPicker.PickSomeCards(numberOfCards)
That’s how you call static methods. If you take away the static keyword from the PickSomeCards method declaration, then you’ll have to create an instance of CardPicker in to call the method. Other than that distinction, static methods are just like object methods: they can take arguments, they can return values, and they live in classes.

When a field is static there’s only one copy of it, and it’s shared by all instances. So if you created multiple instances of CardPicker, they would all share the same random field. You can even mark your whole class as static, and then all of its members must be static too. If you try to add a nonstatic method to a static class, your program won’t build.

THERE ARE NO DUMB QUESTIONS
Q: When I think of something that’s “static” I think of something that doesn’t change. Does that mean nonstatic methods can change, but static methods don’t? Do they behave differently?

A: No, both static and nonstatic methods act exactly the same. The only difference is that static methods don’t require an instance, while nonstatic methods do.

Q: So I can’t use my class until I create an instance of an object?

A: You can use its static methods, but if you have methods that aren’t static, then you need an instance before you can use them.

Q: Then why would I want a method that needs an instance? Why wouldn’t I make all my methods static?

A: Because if you have an object that’s keeping track of certain data—like Ana’s instances of her Enemy class that each kept track of different enemies in her game— then you can use each instance’s methods to work with that data. So when Ana’s game calls the StopSearching method on the enemy2 instance, it only causes that one enemy to stop searching for the player. It doesn’t affect the enemy1 or enemy3 objects, and they can keep searching. That’s how Ana can create game prototypes with any number of enemies, and her programs can keep track of all of them at once.

When a field is static, there’s only one copy of it shared by all instances.

SHARPEN YOUR PENCIL

Here’s a console app that uses top-level statements and writes several lines to the console. It includes a class called Clown that has two fields, Name and Height, and a method called WhoAreYou that uses those fields to write a line to the console. Your job is to read the code and write down the lines that are printed to the console.

Here’s the class diagram and code for the Clown class:


Here are the contents of the Program.cs file. There are comments next to each of the calls to the WhoAreYou method, which prints a line to the console. Your job is to fill in the blanks in the comments so they match the output.

Clown oneClown = new Clown();
oneClown.Name = "Boffo";
oneClown.Height = 14;
oneClown.WhoAreYou();     // My name is ------- and I’m ---- inches tall.

Clown anotherClown = new Clown();
anotherClown.Name = "Biff";
anotherClown.Height = 16;
anotherClown.WhoAreYou();  // My name is ------- and I’m ---- inches tall.

Clown clown3 = new Clown();
clown3.Name = anotherClown.Name;
clown3.Height = oneClown.Height - 3;
clown3.WhoAreYou();        // My name is ------- and I’m ---- inches tall.

anotherClown.Height *= 2;
anotherClown.WhoAreYou();  // My name is ------- and I’m ---- inches tall.
NOTE
The *= operator tells C# to take whatever’s on the left of the operator and multiply it by whatever’s on the right, so this will update the Height field.


Thanks for the memory
When your program creates an object, it lives in a part of the computer’s memory called the heap. When your code creates an object with a new statement, C# immediately reserves space in the heap so it can store the data for that object.


When your program creates a new object, it gets added to the heap.

SHARPEN YOUR PENCIL SOLUTION

Here’s what the program prints to the console. It’s worth taking a few minutes to create a new console app—make sure it uses top-level statements—add the Clown class, and make its Program.cs method the code below, Then step through it with the debugger so you can see exactly how it works.


What’s on your app’s mind
Let’s take a closer look at the program in the “Sharpen your pencil” exercise, starting with the first line of the app. It’s actually two statements combined into one:


Next, let’s look closely at what the heap looks like after each group of statements is executed:


Sometimes code can be difficult to read
You may not realize it, but you’re constantly making choices about how to structure your code. Do you use one method to do something? Do you split it into more than one? Do you even need a new method at all? The choices you make about methods can make your code much more intuitive—or if you’re not careful, much more convoluted.

Here’s a nice, compact chunk of code from a control program that runs a machine that makes candy bars:

int t = m.chkTemp();
if (t > 160) {
   T tb = new T();
   tb.clsTrpV(2);
   ics.Fill();
   ics.Vent();
   m.airsyschk();
}
Extremely compact code can be especially problematic
Take a second and look at that code. Can you figure out what it does? Don’t feel bad if you can’t—it’s very difficult to read! Here are a few reasons why:

* We can see a few variable names: tb, ics, m. These are terrible names! We have no idea what they do. And what’s that T class for?

* The chkTemp method returns an integer…but what does it do? We can guess maybe it has something to do with checking the temperature of…something?

* The clsTrpV method has one parameter. Do we know what that parameter is supposed to be? Why is it 2? What is that 160 number for?


C# and .NET are everywhere…and we mean everywhere.

Have you ever played with a Raspberry PI? It’s a low-cost computer on a single board, and computers like it can be found inside all sorts of machinery. Thanks to Windows IoT (or Internet of Things), your C# code can run on them.

You can learn more about .NET IoT apps here: https://dotnet.microsoft.com/apps/iot

Microsoft even has a free Raspberry PI simulator that you can use to get started:

https://learn.microsoft.com/en-us/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started

Most code doesn’t come with a manual
Those statements don’t give you any hints about why the code’s doing what it’s doing. In this case, the programmer was happy with the results because she was able to get it all into one method. But making your code as compact as possible isn’t really useful! Let’s break it up into methods to make it easier to read, and make sure the classes are given names that make sense.

We’ll start by figuring out what the code is supposed to do. Luckily, we happen to know that this code is part of an embedded system, or a controller that’s part of a larger electrical or mechanical system. And we happen to have documentation for this code—specifically, the manual that the programmers used when they originally built the system.


We can compare the code with the manual that tells us what the code is supposed to do. Adding comments can definitely help us understand what it’s supposed to do:

/* This code runs every 3 minutes to check the temperature.
 * If it exceeds 160C we need to vent the cooling system.
 */
int t = m.chkTemp();
if (t > 160) {
   // Get the controller system for the turbines
   T tb = new T();

   // Close throttle valve on turbine #2
   tb.clsTrpV(2);

   // Fill and vent the isolation cooling system
   ics.Fill();
   ics.Vent();

   // Initiate the air system check
   m.airsyschk();
}
NOTE
Adding extra line breaks to your code in some places can make it easier to read.

BRAIN POWER

Code comments are a good start. Can you think of a way to make this code even easier to understand?

Use intuitive class and method names
That page from the manual made it a lot easier to understand the code. It also gave us some great hints about how to make our code easier to understand. Let’s take a look at the first two lines:

/* This code runs every 3 minutes to check the temperature.
 * If it exceeds 160C we need to vent the cooling system.
 */
int t = m.chkTemp();
if (t > 160) {
The comment we added explains a lot. Now we know why the conditional test checks the variable t against 160—the manual says that any temperature above 160°C means the nougat is too hot. It turns out that m is a class that controls the candy maker, with static methods to check the nougat temperature and check the air system.

So let’s put the temperature check into a method, and choose names for the class and the methods that make their purpose obvious. We’ll move these first two lines into their own method that returns a Boolean value, true if the nougat is too hot or false if it’s OK:


Did you notice the special /// comments above the method? That’s called an XML Documentation Comment (or XMLDoc) The IDE uses those comments to show you documentation for methods—like the documentation you saw when you used the IntelliSense window to figure out which method from the Random class to use.

IDE TIP: XML DOCUMENTATION FOR METHODS AND FIELDS

Visual Studio helps you add XML documentation. Put your cursor in the line above any method and type three slashes, and it will add an empty template for your documentation. If your method has parameters and a return type, it will add <param> and <returns> tags for them as well. Try going back to your CardPicker class and typing /// in the line above the PickSomeCards method—the IDE will add blank XML documentation. Fill it in and watch it show up in IntelliSense.

/// <summary>
/// Picks a number of cards and returns them.
/// </summary>
/// <param name="numberOfCards">The number of cards to pick.</param>
/// <returns>An array of strings that contain the card names.</returns>
You can create XML documentation for your fields, too. Try it out by going to the line just above any field and typing three slashes in the IDE. Anything you put after <summary> will show up in the IntelliSense window for the field.

What does the manual say to do if the nougat is too hot? It tells us to perform the candy isolation cooling system (or CICS) vent procedure. So let’s make another method, and choose an obvious name for the T class (which turns out to control the turbine) and the ics class (which controls the isolation cooling system, and has two static methods to fill and vent the system), and cap it all off with some brief XML documentation:


Now that we have the IsNougatTooHot and DoCICSVentProcedure methods, we can rewrite the original confusing code as a single method—and we can give it a name that makes clear exactly what it does:

/// <summary>
/// This code runs every 3 minutes to check the temperature.
/// If it exceeds 160C we need to vent the cooling system.
/// </summary>
public void ThreeMinuteCheck() {
   if (IsNougatTooHot() == true) {
      DoCICSVentProcedure();
   }
}
Now the code is a lot more intuitive! Even if you don’t know that the CICS vent procedure needs to be run if the nougat is too hot, it’s a lot more obvious what this code is doing.



That’s right. When you change the structure of your code without altering its behavior, it’s called refactoring.

Great developers write code that’s as easy as possible to understand, even after they haven’t looked at it for a long time. Comments can help, but nothing beats choosing intuitive names for your methods, classes, variables, and fields.

You can make your code easier to read and write by thinking about the problem your code was built to solve. If you choose names for your methods that make sense to someone who understands that problem, then your code will be a lot easier to decipher and develop. No matter how well we plan our code, we almost never get things exactly right the first time.

That’s why great developers constantly refactor their code. They’ll move code into methods and give them names that make sense. They’ll rename variables. Any time they see code that isn’t 100% obvious, they’ll take a few minutes to refactor it. They know it’s worth taking the time to do it now, because it will make it easier to add more code in an hour (or a day, a month, or a year!).

SHARPEN YOUR PENCIL

Each of these classes has a serious design flaw. Write down what you think is wrong with each class, and how you’d fix it.


This class is part of the candy manufacturing system from earlier.



These two classes are part of a system that a pizza parlor uses to track the pizza orders that are out for delivery.



The CashRegister class is part of a program that’s used by an automated convenience store checkout system.


SHARPEN YOUR PENCIL SOLUTION

Here’s how we improved the classes. We show just one possible way to fix the problems—but there are plenty of other ways you could design these classes depending on how they’ll be used.

This class is part of the candy manufacturing system from earlier.


These two classes are part of a system that a pizza parlor uses to track the pizza orders that are out for delivery.


The CashRegister class is part of a program that’s used by an automated convenience store checkout system.


CODE TIP: A FEW IDEAS FOR DESIGNING INTUITIVE CLASSES

We’re about to jump back into writing code. You’ll be writing code for the rest of this chapter, and a LOT of code throughout the book. That means you’ll be creating a lot of classes. Here are a few things to keep in mind when you make choices about how to design them:

* You’re building your program to solve a problem.

Spend some time thinking about that problem. Does it break down into pieces easily? How would you explain that problem to someone else? These are good things to think about when designing your classes.

* What real-world things will your program use?

A program to help a zookeeper track her animals’ feeding schedules might have classes for different kinds of food and types of animals.

* Use descriptive names for classes and methods.

Someone should be able to figure out what your classes and methods do just by looking at their names.

* Look for similarities between classes.

Sometimes two classes can be combined into one if they’re really similar. The candy manufacturing system might have three or four turbines, but there’s only one method for closing the trip valve that takes the turbine number as a parameter.

RELAX

It’s OK if you get stuck when you’re writing code. In fact, getting stuck can be a good thing!

Writing code is all about solving problems—and some of them can be tricky! But if you keep a few things in mind, it’ll make the code exercises go more smoothly:

* It’s easy to get caught up in syntax problems, like missing parentheses or quotes. One missing bracket can cause many build errors.

* It’s much better to look at the solution than to get frustrated with a problem. When you’re frustrated, your brain doesn’t like to learn.

* All of the code in this book is tested and definitely works! But it’s easy to accidentally type things wrong (like typing a one instead of a lowercase L, or missing a comma or semicolon).

* If your solution just won’t build, try downloading it from the GitHub repository for the book—it has working code for everything in the book: https://github.com/head-first-csharp/fifth-edition

You can learn a lot from reading code. So if you run into a problem with a coding exercise, don’t be afraid to peek at the solution. It’s not cheating!

Build a class to work with some guys
Joe and Bob lend each other money all the time. Let’s create a class to keep track of how much cash they each have. We’ll start with an overview of what we’ll build.

 We’ll create two instances of a “Guy” class.

We’ll use two Guy variables called joe and bob to keep track of each of our instances. Here’s what the heap will look like after they’re created:


 We’ll set each Guy object’s Cash and Name fields.

The two objects represent different guys, each with his own name and a different amount of cash in his pocket. Each guy has a Name field that keeps track of his name, and a Cash field that has the number of bucks in his pocket.



 We’ll add methods to give and receive cash.

We’ll make a guy give cash from his pocket (and reduce his Cash field) by calling his GiveCash method, which will return the amount of cash he gave. We’ll make him receive cash and add it to his pocket (increasing his Cash field) by calling his ReceiveCash method.



Compare the comments in this code to the class diagrams and illustrations of the Guy objects. If something doesn’t make sense at first, take the time to really understand it.

There’s an easier way to initialize objects with C#
Almost every object that you create needs to be initialized in some way. The Guy object is no exception—it’s useless until you set its Name and Cash fields. It’s so common to have to initialize fields that C# gives you a shortcut for doing, it called an object initializer. The IDE’s IntelliSense will help you do it.

You’re about to do an exercise where you create two Guy objects. You could use one new statement and two more statements to set its fields:

Object initializers save you time and make your code more compact and easier to read…and the IDE helps you write them.

joe = new Guy();
joe.Name = "Joe";
joe.Cash = 50;
Instead, type this: Guy joe = new Guy() {

As soon as you add the left curly bracket, the IDE will pop up an IntelliSense window that shows all of the fields that you can initialize:


Choose the Cash field, set it to 50, and add a comma:

Guy joe = new Guy() { Cash = 50,
Now type a space—another IntelliSense window will pop up with the remaining field to set:


Set the Name field and add the semicolon. You now have a single statement that initializes your object:


EXERCISE

This is part 1 of a two-part exercise.

Here are the top-level statements for a console app that makes Guy objects give cash to each other.

Step 1: Create a new console app that uses top-level statements. Name it Guys.

Step 2: Add a new class to your app called Guy. Since your project is called Guys, your new class will be in the namespace Guys. Carefully add all of the code from the Guy class that we just showed you.

Step 3: Here’s the code that goes into your app’s Program.cs file. Carefully enter it, then replace the comments in with code—read each comment and write code that does exactly what it says. When you’re done, you’ll have a program that looks like the screenshot on the previous page.


EXERCISE SOLUTION

Here are the top-level statements for your console app. It uses an infinite loop to keep asking the user how much cash to move between the Guy objects. If the user enters a blank line for an amount, the method executes a return statement, which causes Main to exit and the program to end.


Don’t move on to the next part of the exercise until you have the first part working and you understand what’s going on. It’s worth taking a few minutes to use the debugger to step through the program and make sure you really get it.

EXERCISE

Here’s the second part of the two-part exercise.

Now that you have your Guy class working, let’s see if you can reuse it in a betting game. Look closely at this screenshot to see how it works and what it prints to the console.


Create a new console app that uses top-level statements, then add the Guy class from your Guys project. Make sure you add a using statement to the top of your Program.cs file so you can use the Guy class.

In your Program.cs, declare two variables:

A double variable called odds that stores the odds to beat set to .75

A Guy variable called player for an instance of Guy named “The player” with 100 bucks.

Your app should write a line to the console welcoming the player and printing the odds. Then it should run this loop:

Call the Guy object’s WriteMyInfo method to write the amount of cash the player has to the console.

Write a line to the console asking the player how much money to bet.

Read the line from the console into a string variable called howMuch.

Try to parse it into an int variable called amount.

If it parses, the player gives the amount to an int variable called pot. Only do steps 6 through 9 if pot is greater than zero.

Multiply pot by two, because it’s a double-or-nothing bet.

Use Random.Shared to pick a random double value between 0 and 1.

If the random value is greater than odds, the player receives the pot.

If not, the player loses the amount they bet.

The program keeps running while the player has cash.

The loop ends when the player runs out of money, then the app prints a message: “The house always wins.”

In step 5, you’ll call the Guy object’s GiveCash method to give the amount to bet. The GiveCash method won’t give more cash than the guy has, so you don’t need to check if the player has enough money. The Guy class will write a message to the console if it doesn’t have enough cash to place the bet, so your app doesn’t have to. Checking if the pot variable is greater than zero makes sure the bet is valid and the player has enough cash.

EXERCISE SOLUTION

Here’s the working code for the top-level statements in the betting game. Can you think of ways to make it more fun? See if you can figure out how to add additional players, or give different options for odds, or maybe you can think of something more clever. This is a chance to get creative!

NOTE
...and to get some practice. Getting practice writing code is the best way to become a great developer.

using Guys;

double odds = .75;
Random random = new Random();

Guy player = new Guy() { Cash = 100, Name = "The player" };

Console.WriteLine("Welcome to the casino. The odds are " + odds);
while (player.Cash > 0)
{
    player.WriteMyInfo();
    Console.Write("How much do you want to bet: ");
    string? howMuch = Console.ReadLine();
    if (int.TryParse(howMuch, out int amount))
    {
        int pot = player.GiveCash(amount) * 2;
        if (pot > 0)
        {
            if (Random.Shared.NextDouble() > odds)
            {
                int winnings = pot;
                Console.WriteLine("You win " + winnings);
                player.ReceiveCash(winnings);
            } else
            {
                Console.WriteLine("Bad luck, you lose.");
            }
       }
   } else
   {
       Console.WriteLine("Please enter a valid number.");
   }
}
Console.WriteLine("The house always wins.");
Was your code a little different than ours? If it still works and produces the right output, that’s OK! There are many different ways to write the same program.

NOTE
...and as you get further along in the book and the exercise solutions get longer, your code will look more and more different from ours. Remember, it’s always OK to look at our solution when you’re working on an exercise!

BRAIN POWER

Is Guy really the best name for the class? Why or why not? Can you think of a better name for it?

SHARPEN YOUR PENCIL

Here’s an app that writes three lines to the console. Your job is to figure out what it writes, without using a computer. Start at the first line of the Main method and keep track of the values of each of the fields in the objects as it runs.

Pizzazz foxtrot = new Pizzazz() { Zippo = 2 };
foxtrot.Bamboo(foxtrot.Zippo);

Pizzazz november = new Pizzazz() { Zippo = 3 };
Abracadabra tango = new Abracadabra() { Vavavoom = 4 };

while (tango.Lala(november.Zippo))
{
    november.Zippo *= -1;
    november.Bamboo(tango.Vavavoom);
    foxtrot.Bamboo(november.Zippo);
    tango.Vavavoom -= foxtrot.Zippo;
}

Console.WriteLine("november.Zippo = " + november.Zippo);
Console.WriteLine("foxtrot.Zippo = " + foxtrot.Zippo);
Console.WriteLine("tango.Vavavoom = " + tango.Vavavoom);
class Pizzazz
{
    public int Zippo; 
 
    public void Bamboo(int eek)
    {
        Zippo += eek;
    }
}

class Abracadabra
{
    public int Vavavoom;

    public bool Lala(int floq)
    {
        if (floq < Vavavoom)
        {
            Vavavoom += floq;
            return true;
        }
        return false;
    }
}
WHAT DOES THIS PROGRAM WRITE TO THE CONSOLE?
november.Zippo = ..............................

foxtrot.Zippo = ..............................

tango.Vavavoom = ..............................

To find the solution, enter the program into Visual Studio and run it. If you didn’t get the answer right, step through the code line by line and add watches for each of the objects’ fields.

If you don’t want to type the whole thing in, you can download it from GitHub: https://github.com/head-first-csharp/fifth-edition.

SENS-AI
Ask an AI chatbot to do the exercise to write the betting game code for you

AI chatbots like Copilot, ChatGPT, and Bard can do more than answer questions. They can draw pictures, search for information, and even generate code for you. Let’s use the betting game to explore how this works.

Step 1: Download the PDF of the first four chapters of this book

We made the first four chapters of this book available as a free PDF. Download it from our GitHub page:

https://github.com/head-first-csharp/fifth-edition

Step 2: Use the complete text of Part 1 of the exercise as a prompt

Open the PDF and find Part 1 of the two-part exercise in this chapter. Part 1 starts with this sentence:

Here are the top-level statements for a console app that makes Guy objects give cash to each other.

Select all of the text for part 1—including all of the code—starting with “Here are the top-level statements” and ending with the closing bracket } at the bottom.

Open Copilot (https://copilot.microsoft.com), ChatGPT (https://chat.openai.com), Bard (https://bard.google.com), or any other AI chatbot. Paste in all of the text that you copied as a prompt. The chatbot should generate code for a Guy class, and code for the top-level statements that use it.

Step 3: Create a new Console App project and paste the generated code into it

Create a new project to test out the code that the AI chatbot generated for you. Make sure you use

Copy the code that the AI generated for its Guy class. Create a Guy class in your project and paste the code into it.

Copy the code that the AI generated for its top-level statements into your Program.cs.

Step 4: Use the AI safely − trust but verify

Before you run your app, look at the code. Does it look right?

When we did this ourselves, all three AI chatbots generated working code that did exactly what we asked it to do. However, one of the chatbots ignored our instruction to generate top-level statements and created a console app with a Main method. The app still worked, though!

Also, two of the chatbots used object initializers, while one of them set the fields directly. Our instructions didn’t tell it exactly what to do, and either of those choices will work just fine.

Step 5: Finish the betting game

Find Part 2 of the exercise in the PDF, copy all of the text, and paste it into the chatbot as a follow-up prompt (so don’t start a new chat). Copy the code that it generates and paste it into your Program.cs file. Before you run your app, carefully read all of the code. Does it look like it works? Did the AI do things differently than you did?

When we pasted our Part 2 prompt, the betting game worked perfectly. All three chatbots were even smart enough to ignore the instruction in Part 2 to look closely at the screenshot to see how the game works and what it prints to the console, even though we didn’t actually include the contents of the screenshot in our prompt.

Did the AI generate code that behaves the same way as the code you wrote for the exercise, but is structured differently? Compare its code to yours—that might give you ideas about how you can refactor your code.


It’s often easier to write the code that you want than it is to engineer a prompt to generate that code.

Creating a prompt isn’t always easy. In fact, there’s an entire growing field of study called prompt engineering that’s all about designing prompts to get an AI to do what you want it to do.

Creating a great prompt can include many steps. You need to test the specific language that you’re using, examine the output, then refine it to get the AI to give you the output that you’re looking for. Prompt engineering can be a difficult and often tedious process, because a very small change in a prompt can make a huge difference in the output that the AI generates.

We know this because every coding exercise in this book is a prompt. The only difference is that instead of building those prompts for an artificial intelligence, we built built them to be used by a real, smart, human intelligence—namely, you!

Every single exercise in this book went through a painstaking process to make sure you have all of the information that you need to do it. When we’re building an exercise, we start by writing the code for the solution. Believe it or not, that’s the quickest part of creating the exercise. Then we go through a process of creating instructions. We usually have to go through many versions of each exercise before we end up with the version that you see. It’s a time-consuming and painstaking process—and sometimes we don’t get it right. We got feedback from readers of the first four editions of this book (especially the early editions) who had trouble doing exercises because our instructions were unclear, difficult to follow, and on a few occasions even missed some steps.

NOTE
In this edition, we tested our exercises by pasting them into different AI chatbots to make sure we didn’t accidentally leave out any instructions. If the AI can generate code for a correct solution, it means we included everything you need to do it too.

In every single case, writing the code for each exercise was much easier than the prompt engineering that we had to do to craft the finished exercise.

EXERCISE

Decide for yourself if prompt engineering is harder than writing code. We gave you this method earlier in the chapter:

int Multiply(int factor1, int factor2)
{
   int product = factor1 * factor2;
   return product;
}
NOTE
On our first try, we had to ask four follow-up questions before we could get ChatGPT to give us exactly this output.

Start a new session with an AI chatbot and give it a prompt to create exactly this method. Make sure it doesn’t include comments or any additional code. Ask it follow-up questions until it gives you exactly this ouput.

Repeat the same exercise with the loop from the Sens-AI element in Chapter 2. Can you get the AI to generate it?

Use the C# Interactive window or csi to run C# code
If you just want to run some C# code, you don’t always need to create a new project in Visual Studio. Any C# code entered into the C# Interactive window is run immediately. You can open it by choosing View >> Other Windows >> C# Interactive. Try it now, and paste in the code from the exercise solution to see the output. You can call methods and enter other statements too.


You can also run an interactive C# session from the command line. On Windows, search the Start menu for developer command prompt, start it, and then type csi. On macOS or Linux, run csi from the Terminal. You can paste the Pizzazz, Abracadabra, and Program classes from the previous exercise directly into the prompt, then paste in the code that you want to run.

BULLET POINTS
Use the new keyword to create instances of a class. A program can have many instances of the same class.

Each instance has all of the methods from the class and gets its own copies of each of the fields.

When you included new Random(); in your code, you were creating an instance of the Random class.

Use the static keyword to declare a field or method in a class as static. You don’t need an instance of that class to access static methods or fields.

When a field is static, there’s only one copy of it shared by all instances. When you include the static keyword in a class declaration, all of its members must be static.

Fields and methods of a class are called its members.

If you remove the static keyword from a static field, it becomes an instance field.

When your program creates an object, it lives in a part of the computer’s memory called the heap.

Visual Studio helps you add XML documentation (or XMLDoc) to your fields and methods, and displays it in its IntelliSense window.

Class diagrams help you plan out your classes and make them easier to work with.

When you change the structure of your code without altering its behavior, it’s called refactoring. Advanced developers constantly refactor their code.

Object initializers save you time and make your code more compact and easier to read.


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


3. Namespaces and Classes: Organizing your code
4. Data, Types, Objects, and References: Managing your App’s Data
5. Encapsulation: How Objects Keep their Secrets
12h 51m remaining
Chapter 4. Data, Types, Objects, and References: Managing your App’s Data
A NOTE FOR EARLY RELEASE READERS
With Early Release ebooks, you get books in their earliest form—the authors’ raw and unedited content as they write—so you can take advantage of these technologies long before the official release of these titles.

This will be the 4th chapter of the final book. Please note that the GitHub repo will be made active later on.

If you have comments about how we might improve the content and/or examples in this book, or if you notice missing material within this chapter, please reach out to the editor at mcronin@oreilly.com.


Data and objects are the building blocks of your apps. What would your apps be without data? Think about it for a minute. Without data, your programs are...well, it’s actually hard to imagine writing code without data. You need information from your users, and you use that to look up or produce new information to give back to them. In fact, almost everything you do in programming involves working with data in one way or another. In this chapter, you’ll learn the ins and outs of C#’s data types and references, see how to work with data in your program, and even learn a few more things about objects (guess what...objects are data, too!).

Owen could use our help!
Owen is a game master—a really good one. He hosts a group that meets at his place every week to play different role-playing games (or RPGs), and like any good game master, he works hard to keep things interesting for the players.



Storytelling, fantasy, and mechanics
Owen is a particularly good storyteller. Over the last few months, he’s created an intricate fantasy world for his party, but he’s not so happy with the mechanics of the game that they’ve been playing.

Can we find a way to help Owen improve his RPG?


Character sheets store different types of data on paper
If you’ve ever played an RPG, you’ve seen character sheets: a page with details, statistics, background information, and any other notes you might see about a character. If you wanted to make a class to hold a character sheet, what types would you use for the fields?



BRAIN POWER

Look at the fields in the CharacterSheet class diagram. What type would you use for each field?

A variable’s type determines what kind of data it can store
There are many types built into C#, and you’ll use them to store many different kinds of data. You’ve already seen some of the most common ones, like int, string, bool, and float. There are a few others that you haven’t seen, and they can really come in handy, too.

Here are some types you’ll use a lot.


 int can store any integer from -2,147,483,648 to 2,147,483,647. Integers don’t have decimal points.


 float can store real numbers from ±1.5 x 10-45 to ±3.4 × 1038 with up to 8 significant digits.


 string can hold text of any length (including the empty string ””).


 bool is a Boolean value—it’s either true or false. You’ll use it to represent anything that only has two options: it can either be one thing or another, but nothing else.


 double can store real numbers from ±5.0 × 10-324 to ±1.7 × 10308 with up to 16 significant digits. It’s a really common type when you’re working with XAML properties.

BRAIN POWER

Why do you think C# has more than one type for storing numbers that have a decimal point?

C# has several types for storing integers
C# has several different types for integers, as well as int. This may seem a little odd (pun intended). Why have so many types for numbers without decimals? For most of the programs in this book, it won’t matter if you use an int or a long. If you’re writing a program that has to keep track of millions and millions of integer values, then choosing a smaller integer type like byte instead of a bigger type like long can save you a lot of memory.

 byte can store any integer between 0 and 255.

 sbyte can store any integer from –128 to 127.

 short can store any integer from –32,768 to 32,767.

 long can store any integer from –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.

NOTE
Notice how we’re saying “integer” and not “whole number”? We’re trying to be really careful—our high school math teachers always told us that integers are any numbers that can be written without a fraction, while whole numbers are integers starting at 0, and do not include negative numbers.


Did you notice that byte only stores positive numbers, while sbyte stores negative numbers? They both have 256 possible values. The difference is that, like short and long, sbyte can have a negative sign—which is why those are called signed types, (the “s” in sbyte stands for signed). Just like byte is the unsigned version of sbyte, there are unsigned versions of short, int, and long that start with “u”:

 ushort can store any whole number from 0 to 65,535.

 uint can store any whole number from 0 to 4,294,967,295.

 ulong can store any whole number from 0 to 18,446,744,073,709,551,615.


Types for storing really HUGE and really tiny numbers
Sometimes float just isn’t precise enough. Believe it or not, sometimes 1038 isn’t big enough and 10–45 isn’t small enough. A lot of programs written for finance or scientific research run into these problems all the time, so C# gives us different floating-point types to handle huge and tiny values:

 float can store any number from ±1.5 × 10–45 to ±3.4 × 1038 with 6–9 significant digits.

 double can store any number from ±5.0 × 10–324 to ±1.7 × 10308 with 15–17 significant digits.

 decimal can store any number from ±1.0 × 10–28 to ±7.9 × 1028 with 28–29 significant digits. When your program needs to deal with money or currency, you always want to use a decimal to store the number.

NOTE
The decimal type has a lot more precision (way more significant digits) which is why it’s appropriate for financial calculations.

FLOATING POINT NUMBERS UP CLOSE

The float and double types are called “floating-point” because the decimal point can move (as opposed to a “fixed-point” number, which always has the same number of decimal places). That—and, in fact, a lot stuff that has to do with floating-point numbers, especially precision—may seem a little weird, so let’s dig into the explanation.

“Significant digits” represents the precision of the number: 1,048,415, 104.8415, and .0000001048415 all have 7 significant digits. So when we say a float can store real numbers as big as 3.4 × 1038 or as small as –1.5 × 10-45, that means it can store numbers as big as 8 digits followed by 30 zeros, or as small as 37 zeros followed by 8 digits.

NOTE
If it’s been a while since you’ve used exponents, 3.4×1038 means 34 followed by 37 zeros, and -1.5×10-45 is -.00...(40 more zeros)...0015.

The float and double types can also have special values, including both positive and negative zero, positive and negative infinity, and a special value called NaN (not-a-number) that represents, well, a value that isn’t a number at all. They also have static methods that let you test for those special values. Try running this loop:

for (float f = 10; !float.IsInfinity(f); f *= f)
{
    Console.WriteLine(f);
}
Now try that same loop with double:

for (double d = 10; !double.IsInfinity(d); d *= d)
{
    Console.WriteLine(d);
}
Let’s talk about strings
You’ve written code that works with strings. So what, exactly, is a string?

In any .NET app, a string is an object. Its full class name is System.String—in other words, the class name is String and it’s in the System namespace (just like the Random class you used earlier). When you use the C# string keyword, you’re working with System.String objects. In fact, you can replace string with System. String in any of the code you’ve written so far and it will still work! (The string keyword is called an alias— as far as your C# code is concerned, string and System.String mean the same thing.)

There are also two special values for strings: an empty string, “” (or a string with no characters), and a null string, or a string that isn’t set to anything at all. We’ll talk more about null later in the chapter.

Strings are made up of characters—specifically, Unicode characters (which you’ll learn a lot more about later in the book). Sometimes you need to store a single character like Q or j or $, and when you do you’ll use the char type. Literal values for char are always inside single quotes (’x’, ’3’). You can include escape sequences in the quotes, too (’\n’ is a line break, ’\t’ is a tab). You can write an escape sequence in your C# code using two characters, but your program stores each escape sequence as a single character in memory.

And finally, there’s one more important type: object. If a variable has object as its type, you can assign any value to it. The object keyword is also an alias—it’s the same as System.Object.

SHARPEN YOUR PENCIL

Sometimes you declare a variable and set its value in a single statement like this: int i = 37;—but you already know that you don’t have to set a value. What happens if you use the variable without assigning a value? Let’s find out! Use the C# Interactive window (or the csi if you’re using Mac/Linux) to declare a variable and check its value.


A literal is a value written directly into your code
A literal is a number, string, or other fixed value that you include in your code. You’ve already used plenty of literals—here are some examples of numbers, strings, and other literals that you’ve used:


So when you type int i = 5;, the 5 is a literal.

Use suffixes to give your literals types
Go back to the first loop you wrote in the “Up Close” section and change 10 to 10D:

for (float f = 10D; float.IsFinite(f); f *= f)
Now your program won’t build—you’ll get an error that mentions a literal of type double. That’s because literals have types. Every literal is automatically assigned a type, and C# has rules about how you can combine different types. You can see for yourself how that works. Add this line to any C# program:

int wholeNumber = 14.7;
When you try to build your program, the IDE will show you this error in the Error List:


The IDE is telling you is that the literal 14.7 has a type—it’s a double. You can use a suffix to change its type—try changing it to a float by sticking an F on the end (14.7F) or a decimal by adding M (14.7M—the M actually stands for “money”). The error message now says it can’t convert float or decimal.

C# assumes that an integer literal without a suffix (like 371) is an int, and one with a decimal point (like 27.4) is a double.

SHARPEN YOUR PENCIL SOLUTION


SHARPEN YOUR PENCIL

C# has dozens of reserved words called keywords. They’re words reserved by the C# compiler that you can’t use for variable names. You’ve already learned many of them—here’s a little review to help seal them into your brain. Write down what you think each of these keywords does in C#.


NOTE
If you really want to use a reserved keyword as a variable name, put @ in front of it, but that’s as close as the compiler will let you get to the reserved word. You can also do that with nonreserved names, if you want to.

SHARPEN YOUR PENCIL SOLUTION

C# has dozens of reserved words called keywords. They’re words reserved by the C# compiler that you can’t use for variable names. You’ve already learned many of them—here’s a little review to help seal them into your brain. Write down what you think each of these keywords does in C#.


A variable is like a data to-go cup
All of your data takes up space in memory. (Remember the heap from the last chapter?) So part of your job is to think about how much space you’re going to need whenever you use a string or a number in your program. That’s one of the reasons you use variables. They let you set aside enough space in memory to store your data.

NOTE
Not all data ends up on the heap. Value types usually keep their data in another part of memory called the stack. You’ll learn all about that later in the book.

Think of a variable like a cup that you keep your data in. C# uses a bunch of different kinds of cups to hold different kinds of data. Just like the different sizes of cups at a coffee shop, there are different sizes of variables, too.


Use the Convert class to explore bits and bytes

You’ve always heard that programming is about 1s and 0s. .NET has a static Convert class that converts between different numeric data types. Let’s use it to see an example of how bits and bytes work.

A bit is a single 1 or 0. A byte is 8 bits, so a byte variable holds an 8-bit number, which means it’s a number that can be represented with up to 8 bits. What does that look like? Let’s use the Convert class to convert some binary numbers to bytes:


Bytes can hold numbers between 0 and 255 because they use 8 bits of memory—an 8-bit number is a binary number between 0 and 11111111 binary (or 0 and 255 decimal).

A short is a 16-bit value. Let’s use Convert.ToInt16 to convert the binary value 111111111111111 (15 1s) to a short. An int is a 32-bit value, so we’ll use Convert.ToInt32 to convert the 31 1s to an int:

Convert.ToInt16("111111111111111", 2);                 // returns 32767
Convert.ToInt32("1111111111111111111111111111111", 2); // returns 2147483647
Other types come in different sizes, too
Numbers that have decimal places are stored differently than integers, and the different floating-point types take up different amounts of memory. You can handle most of your numbers that have decimal places using float, the smallest data type that stores decimals. If you need to be more precise, use a double. If you’re writing a financial application where you’ll be storing currency values, you’ll always want to use the decimal type.

Oh, and one more thing: don’t use double for money or currency, only use decimal.


We’ve talked about strings, so you know that the C# compiler also can handle characters and non-numeric types. The char type holds one character, and string is used for lots of characters “strung” together. There’s no set size for a string object—it expands to hold as much data as you need to store in it. The bool data type is used to store true or false values, like the ones you’ve used for your if statements.


The different floating-point types take up different amounts of memory: float is smallest, and decimal is largest.

10 pounds of data in a 5-pound bag
When you declare your variable as one type, the C# compiler allocates (or reserves) all of the memory it would need to store the maximum value of that type. Even if the value is nowhere near the upper boundary of the type you’ve declared, the compiler will see the cup it’s in, not the number inside. So this won’t work:

int leaguesUnderTheSea = 20000;
short smallerLeagues = leaguesUnderTheSea;

20,000 would fit into a short, no problem. But because leaguesUnderTheSea is declared as an int, C# sees it as int-sized and considers it too big to put in a short container. The compiler won’t make those translations for you on the fly. You need to make sure that you’re using the right type for the data you’re working with.


SHARPEN YOUR PENCIL

Three of these statements won’t build, either because they’re trying to cram too much data into a small variable or because they’re putting the wrong type of data in. Circle them and write a brief explanation of what’s wrong


Casting lets you copy values that C# can’t automatically convert to another type
Let’s see what happens when you try to assign a decimal value to an int variable.


 Create a new Console App project and add this code to your Program.cs:

float myFloatValue = 10;
int myIntValue = myFloatValue;
Console.WriteLine("myIntValue is " + myIntValue);
NOTE
Implicit conversion means C# has a way to automatically convert a value to another type without losing information.

 Try building your program. You should get the same CS0266 error you saw earlier:


Look closely at the last few words of the error message: “are you missing a cast?”

That’s the C# compiler giving you a really useful hint about how to fix the problem.

 Make the error go away by casting the decimal to an int. You do this by adding the type that you want to convert to in parentheses: (int). Once you change the second line so it looks like this, your program will compile and run:


NOTE
When you cast a floating-point value to an int, it rounds the value down to the nearest integer.

So what happened?
The C# compiler won’t let you assign a value to a variable if it’s the wrong type—even if that variable can hold the value just fine! It turns out that a LOT of bugs are caused by type problems, and the compiler is helping by nudging you in the right direction. When you use casting, you’re essentially saying to the compiler that you know the types are different, and promising that in this particular instance it’s OK for C# to cram the data into the new variable.

SHARPEN YOUR PENCIL SOLUTION

Three of these statements won’t build, either because they’re trying to cram too much data into a small variable or because they’re putting the wrong type of data in. Circle them and write a brief explanation of what’s wrong


When you cast a value that’s too big, C# adjusts it to fit its new container
You’ve already seen that a float can be cast to an int. It turns out that any number can be cast to any other number. That doesn’t mean the value stays intact through the casting, though. Say you have an int variable set to 365. If you cast it to a byte variable (max value 255), instead of giving you an error, the value will just wrap around. 256 cast to a byte will have a value of 0, 257 will be converted to 1, 258 to 2, etc., up to 365, which will end up being 109. Once you get back to 255 again, the conversion value “wraps” back to zero.

If you use + (or *, /, or -) with two different numeric types, the operator automatically converts the smaller type to the bigger one. Here’s an example:

int myInt = 36;
float myFloat = 16.4F;
myFloat = myInt + myFloat;
Since an int can fit into a float but a float can’t fit into an int, the + operator converts myInt to a float before adding it to myFloat.

SHARPEN YOUR PENCIL

You can’t always cast any type to any other type.

Create a new Console App project and type these statements into its top-level statements. Then build your program—it will give lots of errors. Cross out the ones that give errors. This is a great way to help you figure out which types can be cast, and which can’t.

int myInt = 10;
byte myByte = (byte)myInt;
double myDouble = (double)myByte;
bool myBool = (bool)myDouble;
string myString = "false";
myBool = (bool)myString;
myString = (string)myInt;
myString = myInt.ToString();
myBool = (bool)myByte;
myByte = (byte)myBool;
short myShort = (short)myInt;
char myChar = ’x’;
myString = (string)myChar;
long myLong = (long)myInt;
decimal myDecimal = (decimal)myLong;
myString = myString + myInt + myByte +
myDouble + myChar;
NOTE
You can read a lot more about the different C# value types here—it’s worth taking a look: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/value-types


Yes! When you concatenate strings, C# converts values.

When you use the + operator to combine a string with another value, it’s called concatenation. When you concatenate a string with an int, bool, float, or another value type, it automatically converts the value. This kind of conversion is different from casting, because under the hood it’s really calling the ToString method for the value...and one thing that .NET guarantees is that every object has a ToString method that converts it to a string (but it’s up to the individual class to determine if that string makes sense).

WRAP IT YOURSELF!
There’s no mystery to how casting “wraps” the numbers—you can do it yourself. Just open up any calculator app that has a Mod button (which does a modulus calculation—sometimes in a Scientific mode), and calculate 365 Mod 256.

SHARPEN YOUR PENCIL SOLUTION

You can’t always cast any type to any other type. Create a new Console App project and type these statements into its top-level statements. Then build your program—it will give lots of errors. Cross out the ones that give errors. This is a great way to help you figure out which types can be cast, and which can’t.


C# does some conversions automatically
There are two important conversions that don’t require you to do casting. The first is the automatic conversion that happens any time you use arithmetic operators, like in this example:


The other way C# converts types for you automatically is when you use the + operator to concatenate strings (which just means sticking one string on the end of another, like you’ve been doing with message boxes). When you use + to concatenate a string with something that’s another type, it automatically converts the numbers to strings for you. Here’s an example—try adding these lines to any C# program. The first two lines are fine, but the third one won’t compile:

long number = 139401930;
string text = "Player score: " + number;
text = number;
The C# compiler gives you this error on the third line:


ScoreText.text is a string field, so when you used the + operator to concatenate a string it assigned the value just fine. But when you try to assign x to it directly, it doesn’t have a way to automatically convert the long value to a string. You can convert it to a string by calling its ToString method.

THERE ARE NO DUMB QUESTIONS
Q: You used the Convert.ToByte, Convert.ToInt32, and Convert.ToInt64 methods to convert strings with binary numbers into integer values. Can you convert integer values back to binary?

A: Yes. The Convert class has a Convert.ToString method that converts many different types of values to strings. The IntelliSense pop-up shows you how it works:


So Convert.ToString(255, 2) returns the string "11111111", and Convert.ToString(8675309, 2) returns the string “100001000101111111101101”—try experimenting with it to get a feel for how binary numbers work.

When you call a method, the arguments need to be compatible with the types of the parameters
In the last chapter, you used the Random class to choose a random number from 1 up to (but not including) 5, which you used to pick a suit for a playing card:

int value = Random.Shared.Next(1, 5);
Try changing the first argument from 1 to 1.0:

int value = Random.Shared.Next(1.0, 5);
You’re passing a double literal to a method that’s expecting an int value. So it shouldn’t surprise you that the compiler won’t build your program—instead, it shows an error:


Sometimes C# can do the conversion automatically. It doesn’t know how to convert a double to an int (like converting 1.0 to 1), but it does know how to convert an int to a double (like converting 1 to 1.0). More specifically:

 The C# compiler knows how convert an integer to a floating-point type.

 And it knows how to convert an integer type to another integer type, or a floating-point type to another floating-point type.

 But it can only do those conversions if the type it’s converting from is the same size as or smaller than the type it’s converting to. So, it can convert an int to a long or a float to a double, but it can’t convert a long to an int or a double to a float.

But Random.Shared.Next isn’t the only method that will give you compiler errors if you try to pass it a variable whose type doesn’t match the parameter. All methods will do that, even the ones you write yourself. Add this method to a console app:

public int MyMethod(bool add3) {
   int value = 12;

   if (add3)
      value += 3;
   else
      value -= 2;

   return value;
}
When the compiler gives you an “invalid argument” error, it means that you tried to call a method with variables whose types didn’t match the method’s parameters.

Try passing it a string or long—you’ll get one of those CS1503 errors telling you it can’t convert the argument to a bool. Some folks have trouble remembering the difference between a parameter and an argument. So just to be clear:

A parameter is what you define in your method. An argument is what you pass to it. You can pass a byte argument to a method with an int parameter.

THERE ARE NO DUMB QUESTIONS
Q: That last if statement only said if (add3). Is that the same thing as if (add3 == true)?

A: Yes. Let’s take another look at that if/else statement:

if (add3)
   value += 3;
else
   value -= 2;
An if statement always checks if something’s true. So because the type of the add3 variable is bool, it evaluates to either true or false, which means we didn’t have to explicitly include == true.

You can also check if something’s false using ! (an exclamation point, or the NOT operator). Writing if (!add3) is the same thing as writing if (add3 == false).

In our code examples from now on, if we’re using the conditional test to check a Boolean variable, you’ll usually just see us write if (add3) or if (!add3), and not use == to explicitly check to see if the Boolean is true or false.

Q: You didn’t include curly braces in the if or else blocks, either. Does that mean they’re optional?

A: Yes—but only if there’s a single statement in the if or else block. We could leave out the { curly braces } because there was just one statement in the if block (return 45;) and one statement in the else block (return 61;). If we wanted to add another statement to one of those blocks, we’d have to use curly braces for it:

if (add3)
   value += 3;
else {
   Console.WriteLine("Subtracting 2");
   value -= 2;
}
Be careful when you leave out curly braces because it’s easy to accidentally write code that doesn’t do what you want it to do. It never hurts to add curly braces, but it’s also good to get used to seeing if statements both with and without them.

BULLET POINTS
There are value types for variables that hold different sizes of numbers. The biggest numbers should be of type long and the smallest ones (up to 255) can be declared as bytes.

Every value type has a size, and you can’t put a value of a bigger type into a smaller variable, no matter what the actual size of the data is.

When you’re using literal values, use the F suffix to indicate a float (15.6F) and M for a decimal (36.12M).

Use the decimal type for money and currency. Floating-point precision is...well, it’s a little weird.

There are a few types that C# knows how to convert automatically (an implicit conversion), like short to int, int to double, or float to double.

When the compiler won’t let you set a variable equal to a value of a different type, that’s when you need to cast it. To cast a value (an explicit conversion) to another type, put the target type in parentheses in front of the value.

Some keywords are reserved by the language and you can’t name your variables with them. They’re words (like for, while, using, new, and others) that do specific things in the language.

A parameter is what you define in your method. An argument is what you pass to it.

When you build your code in the IDE, it uses the C# compiler to turn it into an executable program.

You can use methods on the static Convert class to convert values between different types.

Owen is constantly improving his game...
Good game masters are dedicated to creating the best experience they can for their players. Owen’s players are about to embark on a new campaign with a brand-new set of characters, and he thinks a few tweaks to the formula that they use for their ability scores could make things more interesting.



...but the trial and error can be time-consuming
Owen’s been experimenting with ways to tweak the ability score calculation. He’s pretty sure that he has the formula mostly right—but he’d really like to tweak the numbers.


Owen likes the overall formula: 4d6 roll, divide, subtract, round down, use a minimum value...but he’s not sure that the actual numbers are right.


BRAIN POWER

What can we do to help Owen find the best combination of values for an updated ability score formula?

Let’s help Owen experiment with ability scores
In this next project, you’ll build a .NET Core console app that Owen can use to test his ability score formula with different values to see how they affect the resulting score. The formula has four inputs: the starting 4d6 roll, the divide by value that the roll result is divided by, the add amount value to add to the result of that division, and the minimum to use if the result is too small.

Owen will enter each of the four inputs into the app, and it will calculate the ability score using those inputs. He’ll probably want to test a bunch of different values, so we’ll make the app easier by to use by asking for new values over and over again until he quits the app, keeping track of the values he used in each iteration and using those previous inputs as default values for the next iteration.

This is what it looks like when Owen runs the app:


This project is a little larger than the previous console apps that you’ve built, so we’ll tackle it in a few steps. First you’ll Sharpen your Pencil to understand the code to calculate the ability score. Then you’ll do an Exercise to write the rest of the code for the app. And finally, you’ll Sleuth out a bug in the code. Let’s get started!

SHARPEN YOUR PENCIL

We’ve built a class to help Owen calculate ability scores. To use it, you’ll set its RollResult, DivideBy, AddAmount, and Minimum fields—or just leave the values set in their declarations—and call its CalculateAbilityScore method.

Create a new Console App project called AbilityScore and add a class called AbilityScoreCalculator. Enter all of the code into the class file. Uh-oh! There’s one line of code that has a problem. Circle the line of code that causes a compiler error. Then write down what you think you’ll need to do to fix it.


Fix the compiler error by adding a cast
If you entered the code correctly, you should see a C# compiler error on this line of code:



Any time the C# compiler gives you an error, read it carefully. It often has a hint that can help you track down the problem. This error tells us exactly what went wrong: it can’t convert a double to an int without a cast. The divided variable is declared as a double, but C# won’t allow you to add it to an int field like AddAmount because it doesn’t know how to convert it. So here’s the answer to the Sharpen Your Pencil question:


When the C# compiler asks “are you missing a cast?” it’s giving you a huge hint that you need to cast the double variable divided before you can add it to the int field AddAmount.

Add a cast to get the AbilityScoreCalculator class to compile...
Now that you know what the problem is, you can add a cast to fix the problematic line of code in AbilityScoreCalculator. The line that caused the error because AddAmount += divided returns a double value. When you try to store a double value in an int variable like added you’ll get a “Cannot implicity convert type” error.

You can fix it by casting divided to an int, so adding it to AddAmount returns another int. Modify that line of code to change divided to (int)divided:


Adding that cast also addresses an important part of Owen’s ability score formula:

* ROUND DOWN TO THE NEAREST WHOLE NUMBER

When you cast a double to an int C# rounds it down—so for example (int)19.7431D gives us 19. By adding that cast, you’re making sure the score is rounded down, like Owen’s formula asks for.

...but there’s still a bug!
We’re not quite done yet! You fixed the compiler error, so now the project builds. But even though the C# compiler will accept it, there’s still a bug in the code. So let’s go ahead and fix it! In the next exercise, you’ll use the AbilityScoreCalculator class as is, then you’ll use it to sleuth out the bug.

EXERCISE

Finish building the console app that uses the AbilityScoreCalculator class. In this exercise, we’ll give you the top-level statements for the console app. Your job is to write code for two methods: a method called ReadInt that reads user input and converts it to an int using int.TryParse, and a method called ReadDouble that does exactly the same thing except it parses doubles instead of int values.

Step 1: In this first step, you’ll add top-level statements to your Program.cs file. Almost everything was used in previous projects. There’s only one new thing—it calls the Console.ReadKey method:

char keyChar = Console.ReadKey(true).KeyChar;
Console.ReadKey reads a single key from the console. When you pass the argument true it intercepts the input so that it doesn’t get printed to the console. Adding .KeyChar causes it to return the key pressed as a char.

Delete the “Hello, World!” line from your Program.cs file and add these top-level statements:

using AbilityScore;

AbilityScoreCalculator calculator = new AbilityScoreCalculator();
while (true)
{
    calculator.RollResult = ReadInt(calculator.RollResult, "Starting 4d6 roll");
    calculator.DivideBy = ReadDouble(calculator.DivideBy, "Divide by");
    calculator.AddAmount = ReadInt(calculator.AddAmount, "Add amount");
    calculator.Minimum = ReadInt(calculator.Minimum, "Minimum");
    calculator.CalculateAbilityScore();
    Console.WriteLine("Calculated ability score: " + calculator.Score);
    Console.WriteLine("Press Q to quit, any other key to continue");
    char keyChar = Console.ReadKey(true).KeyChar;
    if ((keyChar == ’Q’) || (keyChar == ’q’)) return;
}
Step 2: The code you wrote calls a method called ReadInt, so add a static ReadInt method. The ReadInt method takes two parameters: a string called prompt to display to the user, and an int called defaultValue. It writes the prompt to the console, followed by the default value in square brackets. Then it reads a line from the console and attempts to parse it with int.TryParse. If that returns true, return that value; otherwise, return the default value.

Here’s the declaration:

static int ReadInt(int defaultValue, string prompt)
Calling ReadInt("37", "What’s the magic number?") will cause the following prompt to be printed:

What’s the magic number? [37]
There’s a space at the end of that prompt. The user then types in a value and presses enter. The method reads that line from the console and calls int.TryParse to try to parse it. If int.TryParse returns true, the method returns the result. If it returns false, the method returns defaultValue—in this case, 37.

Step 3: Generate and implement the ReadDouble method. ReadDouble is exactly like ReadInt, except that it uses double.TryParse instead of int.TryParse. The double.TryParse method works exactly like int.TryParse, except its out variable needs to be a double, not an int.

static double ReadDouble(double defaultValue, string prompt)
EXERCISE SOLUTION

Here are the ReadInt and ReadDouble methods that display a prompt that includes the default value, read a line from the console, try to convert it to an int or a double, and either use the converted value or the default value, writing a message to the console with the value returned.

static int ReadInt(int defaultValue, string prompt)
{
    Console.Write(prompt + " [" + defaultValue + "]: ");
    string? line = Console.ReadLine();
    if (int.TryParse(line, out int value))
    {
        Console.WriteLine(" using value " + value);
        return value;
    } else
    {
        Console.WriteLine(" using default value " + defaultValue);
        return defaultValue;
    }
}

static double ReadDouble(double defaultValue, string prompt)
{
    Console.Write(prompt + " [" + defaultValue + "]: ");
    string? line = Console.ReadLine();
    if (double.TryParse(line, out double value))
    {
        Console.WriteLine(" using value " + value);
        return value;
    }
    else
    {
        Console.WriteLine(" using default value " + defaultValue);
        return defaultValue;
    }
}
NOTE
Really take some time to understand how each iteration of the while loop in the top-level statements uses fields to save the values that the user entered, then uses them for the default values in the next iteration.


 Did you get a “cannot read keys when either application does not have a console” error in VSCode? If you did, go back to Chapter 1 and follow the instructions to change the C# debug console setting so your console app runs in the Terminal and not the Debug Console.

NOTE
Try changing the csharp.debug.console setting to the externalTerminal to run your app in an external terminal window. You might prefer debugging your apps that way!


You’re right, Owen. There’s a bug in the code.

Owen wants to try out different values to use in his ability score formula, so we used a loop to make the app ask for those values over and over again.

To make it easier for Owen to just change one value at a time, we included a feature in the app that remembers the last values he entered and presents them as default options. We implemented that feature by keeping an instance of the AbilityScoreCalculator class in memory, and updating its fields in each iteration of the while loop.

But something’s gone wrong with the app. It remembers most of the values just fine, but it remembers the wrong number for the “add amount” default value. In the first iteration Owen entered 5, but it gave him 10 as a default option. Then he entered 7, but it gave a default of 12. What’s going on?

BRAIN POWER

What steps can you take to track down the bug in the ability score calculator app?

SLEUTH IT OUT: THE CASE OF THE OPERATOR ODDITY

The debugger is like a detective’s magnifying glass. It helps you spot even the smallest clues.

Let’s do an investigation and see if we can apprehend the culprit, Sherlock Holmes style. Something is causing the bug, so let’s use the debugger to identify suspects and retrace their steps.

The problem seems to be isolated to the “add amount” value, so let’s start by looking for any line of code that touches the AddAmount field. Here’s the line that uses the AddAmount field—put a breakpoint on it:


Here’s another one in the AbilityScoreCalculator.CalculateAbilityScore method—breakpoint that suspect, too:


The trap is set. Let’s see who springs it.

Now run your program. When your code hits the breakpoint, select calculator.AddAmount and add a watch (if you just right-click on AddAmount and choose “Add Watch” from the menu, it will only add a watch for AddAmount and not calculator.AddAmount). Does anything look weird there? We’re not seeing anything unusual. It seems to read the value and update it just fine—that’s probably not the issue. You can delete that breakpoint.

Continue running your program. When the breakpoint in AbilityScoreCalculator.CalculateAbilityScore is hit, add a watch for AddAmount. According to Owen’s formula, this line of code is supposed to add AddAmount to the result of dividing the roll result. Now step over the statement and...


Wait, what?! AddAmount changed. But...but that’s not supposed to happen—it’s impossible! Right? As Sherlock Holmes said, “When you have eliminated the impossible, whatever remains, however improbable, must be the truth.”

It looks like we’ve sleuthed out the source of the problem. That statement is supposed to cast divided to an int to round it down to an integer, then add it to AddAmount and store the result in added. It also has an unexpected side effect: it’s updating AddAmount with the sum because the statement uses the += operator, which returns the sum but assigns the sum to AddAmount.

Now we can finally fix Owen’s bug—and get the REAL “Sharpen” answer
Now that you know what’s happening, you can fix the bug—and it turns out to be a pretty small change. You just need to change the statement to use + instead of =:


And we can finally have the real answer to the “Sharpen Your Pencil” question in the first part of this project.

NOTE
After you circle the line of code that has problems, look at the error and write down what you need to do to fix it.


THERE ARE NO DUMB QUESTIONS
Q: I’m still not clear on the difference between the + operator and the += operator. How do they work, and why would I use one and not the other?

A: There are several operators that you can combine with an equals sign. They include += for adding, -= for subtracting, /= for dividing, *= for multiplying, and %= for remainder. Operators like + that combine two values are called binary operators. Some people find this name a little confusing, but “binary” refers to the fact that the operator combines two values— “binary” means “involving two things”—not that it somehow operates only on binary numbers.

With binary operators, you can do something called compound assignment, which means instead of this:


and it means the same thing. The compound assignment x op= y is equivalent to x = x op y (that’s the technical way of explaining it). They do exactly the same thing.

Operators like += or *= that combine a binary operator with an equals sign are called compound assignment operators.

Q: But then how did the added variable get updated?

A: What caused confusion in the score calculator is that the assignment operator = also returns a value. You can do this:

int q = (a = b + c)
which will calculate a = b + c as usual. The = operator returns a value, so it will update q with the result as well. So:

int added = AddAmount += divided;
is just like doing this:

int added = (AddAmount = AddAmount + divided);
which causes AddAmount to be increased by divided, but stores that result in added as well.

Q: Wait, what? The equals operator returns a value?

A: Yes, = returns the value being set. So in this code:

int first;
int second = (first = 4);
both first and second will end up equal to 4. Open up a console app and use the debugger to test this. It really works!

SHARPEN YOUR PENCIL

We learned about XML Documentation Comments (or XMLDoc) in Chapter 3. We added XMLDoc to the ReadInt method from your Ability Score Calculator app—but we left a lot of blanks for you to fill in. Go back to the section in Chapter 3 where we talked about XMLDoc and try filling in the missing parts of the XMLDoc.


We aren’t giving you a solution for this “Sharpen” pencil-and-paper exercise. Instead, use the responses that the AI chatbots give you in the next “Sens-AI” section—compare them against your answers to see how you did.

We asked you to fill in six blanks for three pairs of opening and closing tags. Did you get them right?

We gave you four blanks to describe what the method does, its parameters, and return values. Compare your responses with the ones the chatbots generated. Do you agree with their descriptions? Remember—AIs don’t always get everything right. You wrote this code, so your descriptions might be more accurate than the AI’s.

SENS-AI

Ask an AI chatbot to add comments to your code

Adding comments to your code is a great habit to get into. We’ve used comments throughout the first few chapters of this book to help you understand the code we’ve written. Comments are really valuable, for a few reasons:

Every developer knows what it feels like to look at code they wrote a long time ago and have absolutely no idea what it does or how it works. This happens a lot when working on a larger app (like the ones you’ll write later in the book). Comments help us remember what we were thinking when we wrote code.

Sometimes you’ve got a particularly complex bit of code, like the event handler method for the buttons in the Animal Matching Game from Chapter 1. Comments can make it easier for you to figure out what’s going on in that code—which can be really valuable if you’re trying to sleuth out a bug.

Developers will often leave themselves comments like this:

//TODO: Finish this piece of code
as a reminder that there’s still work left to do in one part of an app.

These are three really good reasons that developers use comments, but there are many other ways—so many that there’s no way we could possibly include them all in this book. Here’s an opportunity to learn more on your own.

NOTE
This is a great use of an AI chatbot as a learning tool. We’ve given you a lot of information about comments. Now you can use AI to learn more on your own.

Open an AI chatbot and give it this prompt: Why do developers use comments?

Create a prompt to add comments to your code

NOTE
There are many answers to this question, because there are lots of reasons that developers use comments. Try giving this prompt to more than one AI chatbot, or asking it multiple times.

Start a new session with an AI chatbot and give it the following prompt:

Add comments to the code for this C# console application.

Here are the contents of Program.cs:

<paste in the contents of your Program.cs file>

Here are the contents of AbilityScoreCalculator.cs:

<paste in the contents of the file with the AbilityScoreCalculator class>
Use AI chatbots to learn more about XML Documentation

In Chapter 3 we learned about XML Documentation (or XMLDoc), special comments with three slashes that you can use to document your methods, fields, and other class members. AI chatbots are really good at generating XMLDoc.

Start a new AI chatbot session, and give it exactly the same prompt you just gave it for the comments, except replace the first sentence of the prompt with this one, which asks it to generate XMLDoc where it’s needed.

Add comments to the code for this C# console application, using XMLDoc
for the classes, methods, and fields.
Compare the response from the AI against your answers to the “Sharpen” exercise. Which descriptions are better?



Try adding this if/else statement to a console app and build the solution:

if (0.1M + 0.2M == 0.3M) Console.WriteLine("They’re equal");
else Console.WriteLine("They aren’t equal");
You’ll see a green squiggle under the second Console—it’s an Unreachable code detected warning. The C# compiler knows that 0.1 + 0.2 is always equal to 0.3, so the code will never reach the else part of the statement. Run the code—it prints They’re equal to the console.

Next, change the float literals to doubles (remember, literals like 0.1 default to double):

if (0.1 + 0.2 == 0.3) Console.WriteLine("They’re equal");
else Console.WriteLine("They aren’t equal");
That’s really strange. The warning moved to the first line of the if statement. Try running the program. Hold on, that can’t be right! It printed They aren’t equal to the console. How is 0.1 + 0.2 not equal to 0.3?

Now do one more thing. Change 0.3 to 0.30000000000000004 (with 15 zeros between the 3 and 4). Now it prints They’re equal again. So apparently 0.1D plus 0.2D equals 0.30000000000000004D.

NOTE
Wait, what?!


Exactly. Decimal has a lot more precision than double or float, so it avoids the 0.30000000000000004 problem.

Some floating-point types—not just in C#, but in most programming languages!—can give you rare weird errors. This is so strange! How can 0.1 + 0.2 be 0.30000000000000004?

It turns out that some numbers can’t be exactly represented as a double—it has to do with how they’re stored as binary data (0s and 1s in memory). For example, .1D is not exactly .1. Try multiplying .1D * .1D—you get 0.010000000000000002, not 0.01. But .1M * .1M gives you the right answer. That’s why floats and doubles are really useful for a lot of things (like positioning a GameObject in Unity). If you need more rigid precision— like for a financial app that deals with money—decimal is the way to go.

THERE ARE NO DUMB QUESTIONS
Q: I’m still not clear on the difference between conversion and casting. Can you explain it a little more clearly?

A: Conversion is a general, all-purpose term for converting data from one type to another. Casting is a much more specific operation, with explicit rules about which types can be cast to other types, and what to do when the data for the value from one doesn’t quite match the type it’s being cast to. You just saw an example of one of those rules—when a floating-point number is cast to an int, it’s rounded down by dropping any decimal value. You saw another rule earlier about wrapping for integer types, where a number that’s too big to fit into the type it’s being cast to is wrapped using the remainder operator.

Q: Hold on a minute. Earlier you had me “wrap” numbers myself using the mod function on my calculator app. Now you’re talking about remainders. What’s the difference?

A: Mod and remainder are very similar operations. For positive numbers they’re exactly the same: A % B is the remainder when you divide B into A, so: 5 % 2 is the remainder of 5 ÷ 2, or 1. (If you’re trying to remember how long division works, that just means that 5 ÷ 2 is equal to 2 × 2 + 1, so the rounded quotient is 2 and the remainder is 1.) But when you start dealing with negative numbers, there’s a difference between mod (or modulus) and remainder. You can see for yourself: your calculator will tell you that –397 mod 17 = 11, but if you use the C# remainder operator you’ll get –397 % 17 = –6.

Q: Owen’s formula had me dividing two values and then rounding the result down to the nearest integer. How does that fit in with casting?

A: Let’s say you have some floating-point values:

float f1 = 185.26F;
double d2 = .0000316D;
decimal m3 = 37.26M;
and you want to cast them to int values so you can assign them to int variables i1, i2, and i3. We know that those int variables can only hold integers, so your program needs to do something to the decimal part of the number.

So C# has a consistent rule: it drops the decimal and rounds down: f1 becomes 185, d2 becomes 0, and m3 becomes 37. But don’t take our word for it—write your own C# code that casts those three floating-point values to int to see what happens.


NOTE
The 0.1D + 0.2D != 0.3D example is an edge case, or a problem or situation that only happens under certain rare conditions, usually when a parameter is at one of its extremes (like a very big or very small number). If you want to learn more about it, there’s a great article by Jon Skeet about how floating-point numbers are stored in memory in .NET. You can read it here: https://csharpindepth.com/Articles/FloatingPoint.

NOTE
Jon gave us some amazing technical review feedback for the very first edition of this book, and that made a huge difference for us. Thanks so much, Jon!

Use reference variables to access your objects
When you create a new object, you use a new statement to instantiate it, like new Guy() in your program at the end of the last chapter—the new statement created a new Guy object on the heap. You still needed a way to access that object, and that’s where a variable like joe came in: Guy joe = new Guy(). Let’s dig a little deeper into exactly what’s going on there.

The new statement creates the instance, but just creating that instance isn’t enough. You need a reference to the object. So you created a reference variable: a variable of type Guy with a name, like joe. So joe is a reference to the new Guy object you created. Any time you want to use that particular Guy, you can reference it with the reference variable called joe.

When you have a variable that’s an object type, it’s a reference variable: a reference to a particular object. Let’s just make sure we get the terminology right since we’ll be using it a lot. We’ll use the first two lines of the “Joe and Bob” program from the last chapter:


References are like sticky notes for your objects
In your kitchen, you probably have containers of salt and sugar. If you switched their labels, it would make for a pretty disgusting meal— even though you changed the labels, the contents of the containers stayed the same. References are like labels. You can move labels around and point them at different things, but it’s the object that dictates what methods and data are available, not the reference itself—and you can copy references just like you copy values.


A reference is like a label that your code uses to talk about a specific object. You use it to access fields and call methods on an object that it points to.

We stuck a lot of sticky notes on that object! In this particular case, there are a lot of different references to this same Guy object—because a lot of different methods use it for different things. Each reference has a different name that makes sense in its context.

That’s why it can be really useful to have multiple references pointing to the same instance. So you could say Guy dad = joe, and then call dad.GiveCash() (that’s what Joe’s kid does every day). If you want to write code that works with an object, you need a reference to that object. If you don’t have that reference, you have no way to access the object.

If there aren’t any more references, your object gets garbage-collected
If all of the labels come off of an object, programs can no longer access that object. That means C# can mark the object for garbage collection. That’s when C# gets rid of any unreferenced objects and reclaims the memory those objects took up for your program’s use.

 Here’s some code that creates an object.

Just to recap what we’ve been talking about: when you use the new statement, you’re telling C# to create an object. When you take a reference variable like joe and assign it to that object, it’s like you’re slapping a new sticky note on it.

Guy joe = new Guy() { Cash = 50, Name = "Joe" };

 Now let’s create our second object.

Once we do this we’ll have two Guy object instances and two reference variables: one variable (joe) for the first Guy object, and another variable (bob) for the second.

Guy bob = new Guy() { Cash = 100, Name = "Bob" };

 Let’s take the reference to the first Guy object and change it to point to the second Guy object.

Take a really close look at what you’re doing when you create a new Guy object. You’re taking a variable and using the = assignment operator to set it—in this case, to a reference that’s returned by the new statement. That assignment works because you can copy a reference just like you copy a value.

So let’s go ahead and copy that value:

joe = bob;
That tells C# to make joe point to the same object that bob does. Now the joe and bob variables both point to the same object.


 There’s no longer a reference to the first Guy object...so it gets garbage-collected.

Now that joe is pointing to the same object as bob, there’s no longer a reference to the Guy object it used to point to. So what happens? C# marks the object for garbage collection, and eventually trashes it. Poof—it’s gone!


For an object to stay in the heap, it has to be referenced. Some time after the last reference to the object disappears, so does the object.

Multiple references and their side effects
You’ve got to be careful when you start moving reference variables around. Lots of times, it might seem like you’re simply pointing a variable to a different object. You could end up removing all references to another object in the process. That’s not a bad thing, but it may not be what you intended. Take a look:


SHARPEN YOUR PENCIL

Now it’s your turn. Here’s one long block of code. Figure out how many objects and references there are at each stage. On the right-hand side, draw a picture of the objects and sticky notes in the heap.

 Dog rover = new Dog();

rover.Breed = "Greyhound";

Dog rinTinTin = new Dog();

Dog fido = new Dog();

Dog bear = fido;

Objects:______

References:_____

 Dog spot = new Dog();

spot.Breed = "Dachshund";

spot = rover;

Objects:______

References:_____

 Dog lucky = new Dog();

lucky.Breed = "Beagle";

Dog charlie = fido;

fido = rover;

Objects:______

References:_____

 rinTinTin = lucky;

Dog laverne = new Dog();

laverne.Breed = "pug";

Objects:______

References:_____

 charlie = laverne;

lucky = rinTinTin;

Objects:______

References:_____

SHARPEN YOUR PENCIL SOLUTION


GARBAGE COLLECTION EXPOSED

This week’s interview: The .NET Common Language Runtime

Head First: So, we understand that you do a pretty important job for us. Can you tell us a little more about what you do?

Common Language Runtime (CLR): In a lot of ways, it’s pretty simple. I run your code. Any time you’re using a .NET app, I’m making it work.

Head First: What do you mean by making it work?

CLR: I take care of the low-level “stuff ” for you by doing a sort of “translation” between your program and the computer running it. When you talk about instantiating objects or doing garbage collection, I’m the one that’s managing all of those things.

Head First: So how does that work, exactly?

CLR: Well, when you run a program on Windows, macOS, Linux, or most other operating systems, the OS loads machine language from a binary.

Head First: I’m going to stop you right there. Can you back up and tell us what machine language is?

CLR: Sure. A program written in machine language is made up of code that’s executed directly by the CPU— and it’s a whole lot less readable than C#.

Head First: If the CPU is executing the actual machine code, what does the OS do?

CLR: The OS makes sure each program gets its own process, respects the security rules, and provides APIs.

Head First: And for our readers who don’t know what an API is?

CLR: An API—or application programming interface—is a set of methods provided by an OS, library, or program. OS APIs help you do things like work with the filesystem and interact with hardware. But they’re often pretty difficult to use—especially for memory management—and they vary from OS to OS.

Head First: So back to your job. You mentioned a binary. What exactly is that?

CLR: A binary is a file that’s (usually) created by a compiler, a program whose job it is to convert high-level language into low-level code like machine code. Windows binaries usually end with .exe or .dll.

Head First: But I’m guessing that there’s a twist here. You said “low-level code like machine code”—does that mean there are other kinds of low-level code?

CLR: Exactly. I don’t run the same machine language as the CPU. When you build your C# code, Visual Studio asks the C# compiler to create Common Intermediate Language (CIL). That’s what I run. C# code is turned into CIL, which I read and execute.

Head First: You talked about Windows binaries. But you also work on macOS. How does that work?

CLR: If you look in the folders created for your Visual Studio for Mac projects, you’ll see lots of files that end with .dll. These are managed .NET DLL files, and they contain CIL code for the app. You can run those apps from the command line anywhere I’m installed! Try it out yourself. Open a console window, go to the folder with the PickRandomCards project from Chapter 3, find the folder under bin/ that has files that end with .dll, and run this: dotnet PickRandomCards.dll

Head First: You mentioned managing memory. Is that where garbage collection fits into all of this?

CLR: Yes! One useful thing that I do for you is manage your computer’s memory by figuring out when your app is done with certain objects. When it is, I get rid of them for you to free up that memory. That’s something programmers used to have to do themselves—but thanks to me, it’s something that you don’t have to be bothered with. You might not have known it at the time, but I’ve been making your job of learning C# a whole lot easier.

NOTE
You can run your console apps from the command line. Find the DLL file underneath the bin/ folder and run it like this: dotnet ProjectName.dll – and this will work on any OS you can install .NET on—even Linux!

EXERCISE

Create a program with an Elephant class. Instantiate two Elephant instances and then swap the reference values that point to them, without getting any Elephant instances garbage-collected. Here’s what it will look like when your program runs.

You’re going to build a new console app that has a class called Elephant.

Here’s an example of the output of the program:


NOTE
The CLR garbage-collects any object with no references to it. So here’s a hint for this exercise: if you want to pour a cup of coffee into another cup that’s currently full of tea, you’ll need a third glass to pour the tea into...

EXERCISE

Your job is to create a .NET Core console app with an Elephant class that matches the class diagram and uses its fields and methods to generate output that matches the example output.

 Create a new .NET Core console app and add the Elephant class.

Add an Elephant class to the project. Have a look at the Elephant class diagram—you’ll need an int field called EarSize and a string field called Name. Add them, and make sure both are public. Then add a method called WhoAmI that writes two lines to the console to tell you the name and ear size of the elephant. Look at the example output to see exactly what it’s supposed to print.

 Create two Elephant instances and a reference.

Use object initializers to instantiate two Elephant objects:

Elephant lucinda = new Elephant() { Name = "Lucinda", EarSize = 33 };
Elephant lloyd = new Elephant() { Name = "Lloyd", EarSize = 40 };
 Call their WhoAmI methods.

When the user presses 1, call lloyd.WhoAmI. When the user presses 2, call lucinda.WhoAmI. Make sure that the output matches the example.

 Now for the fun part: swap the references.

Here’s the interesting part of this exercise. When the user presses 3, make the app execute code that exchanges the two references. You’ll need to write that method. After you swap references, pressing 1 should write Lucinda’s message to the console, and pressing 2 should write Lloyd’s message. If you swap the references again, everything should go back to normal.


EXERCISE SOLUTION

Create a program with an Elephant class. Instantiate two Elephant instances and then swap the reference values that point to them, without getting any Elephant instances garbage-collected.

Here’s the Elephant class:


Here are the top-level statements for your Program.cs file:


Two references mean TWO variables that can change the same object’s data
Besides losing all the references to an object, when you have multiple references to an object, you can unintentionally change the object. In other words, one reference to an object may change that object, while another reference to that object has no idea that something has changed. Let’s see how that works.

Add one more “else if ” block to your top-level statements. Can you guess what will happen once it runs?


Now go ahead and run your program. Here’s what you’ll see:

You pressed 4 My
name is Lucinda
My ears are 4321 inches tall.


You pressed 1
Calling lloyd.WhoAmI()
My name is Lucinda
My ears are 4321 inches tall.


You pressed 2
Calling lucinda.WhoAmI()
My name is Lucinda
My ears are 4321 inches tall.
NOTE
The program acts normally... until you press 4. Once you do that, pressing either 1 or 2 prints the same output— and pressing 3 to swap the references doesn’t do anything anymore.

After you press 4 and run the new code that you added, both the lloyd and lucinda variables contain the same reference to the second Elephant object. Pressing 1 to call lloyd.WhoAmI prints exactly the same message as pressing 2 to call lucinda.WhoAmI. Swapping them makes no difference because you’re swapping two identical references.

Objects use references to talk to each other
So far, you’ve seen forms talk to objects by using reference variables to call their methods and check their fields. Objects can call one another’s methods using references, too. In fact, there’s nothing that a form can do that your objects can’t do, because your form is just another object. When objects talk to each other, one useful keyword that they have is this. Any time an object uses the this keyword, it’s referring to itself— it’s a reference that points to the object that calls it. Let’s see what that looks like by modifying the Elephant class so instances can call each other’s methods.


 Add a method that lets an Elephant hear a message.

Let’s add a method to the Elephant class. Its first parameter is a message from another Elephant object. Its second parameter is the Elephant object that sent the message:


Here’s what it looks like when it’s called:

lloyd.HearMessage("Hi", lucinda);
We called lloyd’s HearMessage method, and passed it two parameters: the string "Hi" and a reference to Lucinda’s object. The method uses its whoSaidIt parameter to access the Name field of whatever elephant was passed in.

 Add a method that lets an Elephant send a message.

Now let’s add a SpeakTo method to the Elephant class. It uses a special keyword: this. That’s a reference that lets an object get a reference to itself.


Let’s take a closer look at what’s going on.

When we call the Lucinda object’s SpeakTo method:

lucinda.SpeakTo(lloyd, "Hi, Lloyd!");
It calls the Lloyd object’s HearMessage method like this:


 Call the new methods.

Add one more else if block to the top-level statements to make the Lucinda object send a message to the Lloyd object:

else if (input == ’4’)
{
    lloyd = lucinda;
    lloyd.EarSize = 4321;
    lloyd.WhoAmI();
}
else if (input == ’5’)
{
    lucinda.SpeakTo(lloyd, "Hi, Lloyd!");
}
else
{
    return;
}
The “this” keyword lets an object get a reference to itself.

Now run your program and press 5. You should see this output:

You pressed 5
Lloyd heard a message
Lucinda said this: Hi, Lloyd!
 Use the debugger to understand what’s going on.

Place a breakpoint on the statement that you just added:


Run your program and press 5.

When it hits the breakpoint, use Debug >> Step Into (F11) to step into the SpeakTo method.

Add a watch for Name to show you which Elephant object you’re inside. You’re currently inside the Lucinda object—which makes sense because the the app just called lucinda.SpeakTo.

Hover over the this keyword at the end of the line and expand it. It’s a reference to the Lucinda object.


Hover over whoToTalkTo and expand it—it’s a reference to the Lloyd object.

The SpeakTo method has one statement—it calls whoToTalkTo.HearMessage. Step into it.

You should now be inside the HearMessage method. Check your watch again—now the value of the Name field is “Lloyd”—the Lucinda object called the Lloyd object’s HearMessage method.

Hover over whoSaidIt and expand it. It’s a reference to the Lucinda object.

Finish stepping through the code. Take a few minutes to really understand what’s going on.

Arrays hold multiple values
NOTE
Strings and arrays are different from the other data types you’ve seen in this chapter because they’re the only ones without a set size (think about that for a bit).

If you have to keep track of a lot of data of the same type, like a list of prices or a group of dogs, you can do it in an array. What makes an array special is that it’s a group of variables that’s treated as one object. An array gives you a way of storing and changing more than one piece of data without having to keep track of each variable individually. When you create an array, you declare it just like any other variable, with a name and a type—except the type is followed by square brackets:

NOTE
We saw arrays of strings in Chapter 3. Now let’s take a deeper dive into how arrays work.

bool[] myArray;
Use the new keyword to create an array. Let’s create an array with 15 bool elements:

myArray = new bool[15];
Use square brackets to set one of the values in the array. This statement sets the value of the fifth element of myArray to false by using square brackets and specifying the index 4. It’s the fifth one because the first is myArray[0], the second is myArray[1], etc.:

myArray[4] = false;
NOTE
You use the new keyword to create an array because it’s an object—so an array variable is a kind of reference variable. In C#, arrays are zero-based, which means the first element has index 0.

Use each element in an array like it’s a normal variable
When you use an array, first you need to declare a reference variable that points to the array. Then you need to create the array object using the new statement, specifying how big you want the array to be. Then you can set the elements in the array. Here’s an example of code that declares and fills up an array—and what’s happening in the heap when you do it. The first element in the array has an index of 0.


Arrays can contain reference variables
You can create an array of object references just like you create an array of numbers or strings. Arrays don’t care what type of variable they store; it’s up to you. So you can have an array of ints, or an array of Duck objects, with no problem.

Here’s code that creates an array of seven Dog variables. The line that initializes the array only creates reference variables. Since there are only two new Dog() lines, only two actual instances of the Dog class are created.

When you set or retrieve an element from an array, the number inside the brackets is called the index. The first element in the array has an index of 0.


THERE ARE NO DUMB QUESTIONS
Q: I’m still not sure I get how references work.

A: References are the way you use all of the methods and fields in an object. If you create a reference to a Dog object, you can then use that reference to access any methods you’ve created for the Dog object. If the Dog class has (nonstatic) methods called Bark and Fetch, you can create a reference called spot, and then you can use that to call spot.Bark() or spot.Fetch(). You can also change information in the fields for the object using the reference (so you could change a Breed field using spot.Breed).

Q: Then doesn’t that mean that every time I change a value through a reference I’m changing it for all of the other references to that object, too?

A: Yes. If the rover variable contains a reference to the same object as spot, changing rover.Breed to “beagle” would make it so that spot.Breed was “beagle”.

Q: Remind me again—what does this do?

A: this is a special variable that you can only use inside an object. When you’re inside a class, you use this to refer to any field or method of that particular instance. It’s especially useful when you’re working with a class whose methods call other classes. One object can use it to send a reference to itself to another object. So if spot calls one of rover’s methods passing this as a parameter, he’s giving rover a reference to the spot object.

Q: You keep talking about garbage-collecting, but what’s actually doing the collecting?

A: Every .NET app runs inside the Common Language Runtime. The CLR does a lot of stuff, but there are two really important things the CLR does that we’re concerned about right now. First, it executes your code—specifically, the output produced by the C# compiler. Second, it manages the memory that your program uses. That means it keeps track of all of your objects, figures out when the last reference to an object disappears, and frees up the memory that it was using. The folks on the .NET team at Microsoft have done an enormous amount of work making sure that it’s fast and efficient.

Q: I still don’t get that stuff about different types holding different-sized values. Can you go over that one more time?

A: Sure. The thing about variables is they assign a size to your number no matter how big its value is. So if you name a variable and give it a long type even though the number is really small (like, say, 5), the CLR sets aside enough memory for it to get really big. When you think about it, that’s really useful. After all, they’re called variables because they change all the time.

The CLR assumes you know what you’re doing and you’re not going to give a variable a type bigger than it needs. So even though the number might not be big now, there’s a chance that after some math happens, it’ll change. The CLR gives it enough memory to handle the largest value that type can accommodate.

Any time you’ve got code in an object that’s going to be instantiated, the instance can use the special this variable that has a reference to itself.

SHARPEN YOUR PENCIL

Here’s an array of Elephant objects and a loop that will go through it and find the one with the biggest ears. What’s the value of biggestEars.EarSize after each iteration of the for loop?


SHARPEN YOUR PENCIL SOLUTION

Here’s an array of Elephant objects and a loop that will go through it and find the one with the biggest ears. What’s the value of biggestEars.EarSize after each iteration of the for loop?

NOTE
The for loop starts with the second Elephant and compares it to whatever Elephant biggestEars points to. If its ears are bigger, it points biggestEars at that Elephant instead. Then it moves to the next one, then the next one…by the end of the loop, biggestEars points to the one with the biggest ears.


null means a reference points to nothing
There’s another important keyword that you’ll use with objects. When you create a new reference and don’t set it to anything, it has a value. It starts off set to null, which means it’s not pointing to any object at all. Let’s have a closer look at this:



Yes. The null keyword can be useful.

There are a few ways you see null used in typical programs. The most common way is making sure a reference points to an object:

if (lloyd == null) {
That test will return true if the lloyd reference is set to null.

Another way you’ll see the null keyword used is when you want your object to get garbage-collected. If you’ve got a reference to an object and you’re finished with the object, setting the reference to null will immediately mark it for collection (unless there’s another reference to it somewhere).


Yes! Console.ReadLine can return a null value.

Back at the beginning of Chapter 3, you hovered over Console. ReadLine so you could learn more about it from the description that the IntelliSense quick info pop-up. Let’s take another look at it:


Console.ReadLine returns a null when there are no lines available
You’ve been running your apps in Visual Studio and typing input using the keyboard. But you can also run them from the command line. In Windows, there’s an executable in the bin\Debug folder. You can use this command to run your app from the project folder:

C:\Users\Public\source\repos\ConsoleApp1\ConsoleApp1>dotnet run
Hello, World!
NOTE
Make sure you run from inside the project folder that has the .csproj file, not the solution folder that contains it.

You can also use your operating system’s pipe commands like << or < or | to send input to your app from a file or the output of another console app. When you do this, Console.ReadLine needs a way to tell your app that it hit the end of the file—and that’s when it returns null.

But there’s still one issue: what does your app do when Console.ReadLine returns null?

Use the string? type when a string might be null
You’ve been using two different (but related!) types to hold text values. First, there’s the string type, like you used for the Name field in the Elephant class:

public string Name = "";
Then there’s the string? type, like the type returned by Console.ReadLine or which int.TryParse takes as its first parameter, like you used in Owen’s ability score calculator app:

string? line = Console.ReadLine();
if (int.TryParse(line, out int value))
The difference is that in the Elephant class the Name field is never null. That’s why we asked you to initialize the Name field in your Elephant class.

What do you think would happen if you didn’t initialize the Name field in the Elephant class?


Change the field declaration in the Elephant class so it doesn’t initialize it to an empty string:


Visual Studio gives you a warning that has to do with null values, and asks you to consider declaring the field as nullable. That’s what the string? type is—a nullable string.

You can make the error disappear by changing the Name field to a nullable string? instead of a string:

public string? Name;
Now your app builds again, and runs exactly the same way as it did before.

NOTE
Use the debugger to step through the app, and add a watch for the holder variable. Its value is null until it runs this statement: holder = lloyd;

int.TryParse takes a string? parameter
So what does your app do if Console.ReadLine returns null?

Luckily, int.TryParse also takes a string? value, so if your app gets to the end of the input and Console.ReadLine returns null, int.TryParse will just return false—so the app will work just fine, and when it gets a null value it will treat it the way it treats any other value that can’t be parsed.

Visual Studio is smart enough to check for possible places where a value can be null. You can avoid that problem by making sure all of your reference variables are initialized.

GAME DESIGN... AND BEYOND

Tabletop Games

There’s a rich history to tabletop games—and, as it turns out, a long history of tabletop games influencing video games, at least as early as the very first commercial role-playing game.

The first edition of Dungeons and Dragons (D&D) was released in 1974, and that same year games with names like “dungeon” and “dnd” started popping up on university mainframe computers.

You’ve used the Random class to create numbers. The idea of games based on random numbers has a long history—for example, tabletop games that use dice, cards, spinners, and other sources of randomness.

We saw in the last chapter how a paper prototype can be a valuable first step in designing a video game. Paper prototypes have a strong resemblance to tabletop games. In fact, you can often turn the paper prototype of a video game into a playable tabletop game, and use it to test some game mechanics.

You can use tabletop games—especially card games and board games—as learning tools to understand the more general concept of game mechanics. Dealing, shuffling, dice rolling, rules for moving pieces around the board, use of a sand timer, and rules for cooperative play are all examples of mechanics.

The mechanics of Go Fish include dealing cards, asking another player for a card, saying “Go Fish” when asked for a card you don’t have, determining the winner, etc. We’re going to actually build a Go Fish game later in the book, so take a minute and read the rules here: https://en.wikipedia.org/wiki/Go_Fish#The_game.


NOTE
If you’ve never played Go Fish, take a few minutes and read the rules. We’ll use them later in the book!


Even if we’re not writing code for video games, there’s a lot we can learn from tabletop games.

A lot of our programs depend on random numbers. For example, you’ve already used the Random class to create random numbers for several of your apps. Most of us don’t actually have a lot of real-world experience with genuine random numbers... except when we play games. Rolling dice, shuffling cards, spinning spinners, flipping coins...these are all great examples of random number generators. The Random class is .NET’s random number generator—you’ll use it in many of your programs, and your experience using random numbers when playing tabletop games will make it a lot easier for you to understand what it does.



A RANDOM TEST DRIVE

You’ll be using the Random class throughout the book, so let’s get to know it better by kicking its tires and taking it for a spin. Fire up Visual Studio and follow along—and make sure you run your code multiple times, since you’ll get different random numbers each time.

 Create a new console app—all of this code will go in the top-level statements. Random.Shared returns an instance of the Random class. Start by using it to generate a random int:

int randomInt = Random.Shared.Next();
Console.WriteLine(randomInt);
Specify a maximum value to get random numbers from 0 up to—but not including—the maximum value. A maximum of 10 generates random numbers from 0 to 9:

int zeroToNine = Random.Shared.Next(10);
Console.WriteLine(zeroToNine);
 Now simulate the roll of a die. You can specify a minimum and maximum value. A minimum of 1 and maximum of 7 generates random numbers from 1 to 6:

int dieRoll = Random.Shared.Next(1, 7);
Console.WriteLine(dieRoll);

 The NextDouble method generates random double values. Hover over the method name to see a tooltip—it generates a floating-point number from 0.0 up to 1.0:

double randomDouble = Random.Shared.NextDouble();

You can multiply a random double to generate much larger random double values. So if you want a random double value from 1 to 100, multiply the random double by 100:

Console.WriteLine(randomDouble * 100);
Use casting to convert the random double to other types. Try running this code a bunch of times—you’ll see tiny precision differences in the float and decimal values.

Console.WriteLine((float)randomDouble * 100F);
Console.WriteLine((decimal)randomDouble * 100M);
 Use a maximum value of 2 to simulate a coin toss. That generates a random value of either 0 or 1. Use the Convert class, which has a static ToBoolean method that will convert it to a Boolean value:

int zeroOrOne = Random.Shared.Next(2);
bool coinFlip = Convert.ToBoolean(zeroOrOne);
Console.WriteLine(coinFlip);
BRAIN POWER

How would you use Random to choose a random string from an array of strings?

Welcome to Sloppy Joe’s Budget House o’ Discount Sandwiches!

Sloppy Joe has a pile of meat, a whole lotta bread, and more condiments than you can shake a stick at. What he doesn’t have is a menu! Can you build a program that makes a new random menu for him every day? You definitely can...with a new MAUI app, some arrays, your handy random number generator, and a couple of new, useful tools. Let’s get started!

Here’s the app you’ll build. It creates a menu with six random sandwiches. Each sandwich has a protein, a condiment, and a bread, all chosen at random from a list. Every sandwich is given a random price, and there’s a special random price at the bottom to add guacamole on the side.


Sloppy Joe’s menu app uses a Grid layout
A Grid control contains other controls, and defines a set of rows and columns to lay out those controls.

You’ve used other layout controls: you’ve used VerticalStackLayout controls to stack Button, Label, and other controls in your apps on top of each other. You used a HorizontalStackLayout control in Chapter 2 for your bird picker. And in the Animal Matching Game project your VerticalStackLayout contained a FlexLayout that arranged the buttons so they stacked horizontally, flowing into rows if as the window size changed.


WATCH IT!

A Grid control is for layouts, not data.

When most of us see something that contains “rows” and “columns” we think of tables of data, like spreadsheets or HTML tables. That’s not what a Grid control is all about.

The Grid control is for laying out content. Its job is to contain other controls, and give you a way to design more interesting or intricate layouts than you get with stack panels, in a way that works well with different window sizes or on mobile devices.

Grid controls
The Grid control contains other controls, and works just like the other layout controls to contain child controls (the other controls nested inside it). There’s an opening <Grid> tag and a closing </Grid> tag, and the tags for all of the child controls are between them.

Cells in a grid are invisible—their only purpose is to determine where the child controls are displayed on the page. We used Border controls to make the grid visible. A Border control draws a border around a child control nested inside it:

<Border>
    <Label Text="I have a border!"/>
</Border>
A Border can only contain one child control. In the app below we didn’t nest any controls inside the Borders—we just took advantage of the fact that each Border fills up the entire cell. We used the Border control’s BackgroundColor property to make some of the cells in the grid darker.

Use Grid properties to put a control in a cell
The rows and columns in a Grid are numbered starting with 0. To put a child control in a specific row and column, use the Grid.Row and Grid.Column properties. For example, putting <Border Grid.Row="1" Grid.Column="2" /> between Grid tags will make the Grid place the border in the second row and third column. You can also make a control span multiple rows or columns using the Grid.RowSpan and Grid.ColumnSpan properties.


Define the rows and columns for a Grid
The Grid control XAML has sections to define rows and columns. Each row or column can either have proportional sizes—for example, column 3 is twice as wide as column 2 and three times as wide as column 1—or absolute sizes in device-independent pixels.

The row and column definitions are in special sections inside the <Grid> tag. The row definitions are inside a <Grid.RowDefinitions> section, and the column definitions are inside a <Grid.ColumnDefinitions> section.

Here’s the complete XAML for the app that we’ve been showing you. Create a .NET MAUI app called GridExample and add this XAML code (and delete the OnCounterClicked method in MainPage.xaml.cs).


Create the Sloppy Joe’s menu app and set up the grid
Create a new .NET MAUI app and name it SloppyJoe. The first thing you’ll do is create the XAML for the app. Here’s how it will work:


We’ll give you all of the XAML for the app. But before we do, try editing the MainPage.xaml file and creating the XAML for the page on your own. Can you use the app we just gave you as an example to create the row and column definitions yourself?

See how far you can get, then compare it with our XAML.

Here’s the XAML for the app.
Take your time and go through it line by line to make sure you understand how its grid works.


The C# code for the main page
Here’s the C# code for the main page of your Sloppy Joe app. We’re about to give you an exercise to build a class called MenuItem that generates random sandwiches and prices. As soon as the page loads, it calls a method called MakeTheMenu that uses an array of MenuItem objects to fill in all of the prices, and one last MenuItem object to get the price for the guacamole.


EXERCISE

Create the MenuItem class for your menu app.

Start bhy looking closely at the class diagram. It has five fields: three arrays to hold the various sandwich parts, a description, and a price. The array fields use collection expressions that let you create an array by putting comma-separated values between [ square brackets ].

Add the MenuItem class to your project. Here’s the code for the fields:



NOTE
The Generate method uses Random.Shared to choose random prices between 5.00 and 14.99 by creating a random decimal value out of two ints. We gave you the last line of code for the method:

Price = price.ToString("c");
The parameter to the ToString method is a format. In this case, the "c" format tells ToString to format the value with the local currency: if you’re in the United States you’ll see a $; in the UK you’ll get a £, in the EU you’ll see €, etc. If the values don’t make sense in your currency, choose different random numbers!

Your job is to fill in the Generate method. It does the following:

Picks a random protein from the Proteins array

Picks a random condiment from the Condiments array

Picks a random bread from the Breads array

Sets the description field like this: protein + " with " + condiment + " on " + bread

Sets the Price field to a random price that’s at least 5.00 and less than 15.00. Pick a random int that’s at least 5 and less than 15. Then pick a second random in that’s at least 0 and less than 100. Multiply the second number by .01M to get a decimal value that’s at least .00 and less than 1.00, and add it to the first value, and store it in a variable called price. Then set the Price field like this: Price = price.ToString("c");


Sharpen your pencil

Can you write a single line of code that sets Price to a random value between 5.00 and 14.99? Here’s a hint: if the NextDouble method returns a value between 0 and 1. Try multiplying it by 10. What do you get?

........................................................

EXERCISE SOLUTION

public void Generate()
{
    string protein = Proteins[Random.Shared.Next(Proteins.Length)];
    string condiment = Condiments[Random.Shared.Next(Condiments.Length)];
    string bread = Breads[Random.Shared.Next(Breads.Length)];
    Description = protein + " with " + condiment + " on " + bread;


    int bucks = Random.Shared.Next(5, 15);
    int cents = Random.Shared.Next(0, 100);
    decimal price = bucks + (cents * .01M);
    Price = price.ToString("c");
}
Can you write a single line of code that sets Price to a random value between 5.00 and 14.99? Here’s a hint: if the NextDouble method returns a value between 0 and 1. Try multiplying it by 10. What do you get?



You’re right! This is a great time to improve accessibility.

Sloppy Joe has a wheelchair ramp and braille versions of all of his menus, because he wants to make sure everyone has a chance to eat his discount budget-friendly sandwiches. So let’s make sure our menu app is accessible, too!

Start your operating system’s screen reader and read the menu page.


Can we make the app more accessible?
When a screen reader narrates a window, it navigates from item to item, reading each item aloud and drawing a rectangle around it. What did you hear when you listened to the screen reader narrate your app? What did you see? Try having it read the menu while you have your eyes closed. Did you still understand everything that you needed to? It’s pretty good! But accessibility is all about making things better for all of our users. Can we make it better?

Set the main header so the screen reader narrates it
You may have noticed that the first thing it said was “Home” – and if you watched carefully, you saw that was narrating the title bar. Modify AppShell.xaml to change “Home” to “Sloppy Joe’s menu” and have the screen reader narrate the page again. When you’re

It would be great to have the narrator tell the user that they’re looking at items on a menu. Let’s try adding a SemanticProperties.Description to the <Grid> tag:

<Grid Margin="10"
      SemanticProperties.Description="Here are the items on the menu.">
Now try using the screen reader to narrate the window. It sounds fine in Windows, but if you’re using macOS there’s a problem: the screen reader won’t read the items or prices. That’s because if you set the SemanticProperties.Description on a that has children, the screen reader can’t reach those children anymore. This is important even if you’re building software for Windows, because your MAUI apps are cross-platform, and you want your app to be accessible anywhere.

Try setting the item1 label’s SemanticProperties.Description instead
Ok, let’s try something else. Remove the SemanticProperties.Description property from the <Grid> tag. Then try setting the SemanticProperties.Description on the first label:

<Label x:Name="item1" FontSize="18" Text="item #1"
       SemanticProperties.Description="Here are the items on the menu.">
Try using the screen reader again. It’s still not right! When you have a Label, you always want the screen reader to read the contents of the label. Setting the SemanticProperties.Description causes the screen reader to read that description instead of the label text.

Go ahead and delete the SemanticDescription property from the item1 Label control (and also from the Grid, if you haven’t done it already).

BRAIN POWER

What do you think you’ll do to make the screen reader say “Here are the items on the menu” followed by the randomly generated sandwich in the item1 Label control’s Text property?

Use the SetValue method to change a control’s semantic properties
Let’s find a different way to make the screen reader say “Here are the items on the menu.” before it reads the menu items. We’ll still use the SemanticProperties.Description for the first menu item, but instead of using a XAML tag, we’ll use C# to make sure it preserves the text.

Add this line of code to the end of your MainPage method:


This code sets the SemanticProperties.Description property—in this case, it’s setting it to the text “Here are the items on the menu” followed by the random sandwich generated by MenuItem. Try the screen reader one more time—now the page includes that text, and works on all operating systems.

BULLET POINTS
The new keyword returns a reference to an object that you can store in a reference variable.

You can have multiple references to the same object.

You can change an object with one reference and access the results of that change with another.

For an object to stay in the heap, it has to be referenced. Once the last reference to an object disappears, it eventually gets garbage-collected and the memory it used is reclaimed.

Your .NET apps run in the Common Language

Runtime (CLR), a “layer” between the OS and your program. The C# compiler builds your code into Common Intermediate Language (CIL), which the CLR executes.

Declare array variables by putting square brackets after the type in the variable declaration (like bool[] trueFalseValues or Dog[] kennel).

Use the new keyword to create a new array, specifying the array length in square brackets (like new bool[15] or new Dog[3]). The this keyword lets an object get a reference to itself.

An AI chatbot can read your code and add comments, including XML documentation (XMLDoc) comments.

Use the Length method on an array to get its length (like kennel.Length).

Access an array value using its index in square brackets (like bool[3] or Dog[0]). Array indexes start at 0.

null means a reference points to nothing. The compiler will warn you when a variable can potentially be null.

Use the string? type to hold a string that’s allowed to be null. Console.ReadLine can return null strings.

You can use Random.NextDouble to create a random double value between 0 and 1. Multiply a random double to generate much larger random double values

Use collection expressions to initialize an array field by setting the field equal to a value starting with a square bracket, followed by a comma-delimited list of values, and ending with a square bracket.

You can pass a format parameter to an object or value’s ToString method. If you’re calling a numeric type’s ToString method, passing it a value of “c” formats the value as a local currency.

Use a control’s SetValue method to set its semantic properties in code, so the screen reader can include text that’s generated when the app runs.


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


4. Data, Types, Objects, and References: Managing your App’s Data
5. Encapsulation: How Objects Keep their Secrets
6. Inheritance: Your Object’s Family Tree
12h 51m remaining
Chapter 5. Encapsulation: How Objects Keep their Secrets
A NOTE FOR EARLY RELEASE READERS
With Early Release ebooks, you get books in their earliest form—the authors’ raw and unedited content as they write—so you can take advantage of these technologies long before the official release of these titles.

This will be the 5th chapter of the final book. Please note that the GitHub repo will be made active later on.

If you have comments about how we might improve the content and/or examples in this book, or if you notice missing material within this chapter, please reach out to the editor at mcronin@oreilly.com.


Ever wished for a little more privacy?

Sometimes your objects feel the same way. Just like you don’t want anybody you don’t trust reading your journal or paging through your bank statements, good objects don’t let other objects go poking around their fields. In this chapter, you’re going to learn about the power of encapsulation, a way of programming that helps you make code that’s flexible, easy to use, and difficult to misuse. You’ll make your objects’ data private, and add properties to protect how that data is accessed—and you’ll keep your object’s important data from leaking out to other objects so they don’t accidentally misuse it.

Let’s help Owen roll for damage
Owen was so happy with his ability score calculator that he wanted to create more C# programs he can use for his games, and you’re going to help him. In the game he’s currently running, any time there’s a sword attack he rolls dice and uses a formula that calculates the damage. Owen wrote down how the sword damage formula works in his game master notebook.

Here’s a class called SwordDamage that does the calculation. Read through the code carefully—you’re about to create an app that uses it.



Create a console app to calculate damage

Let’s build a console app for Owen that uses the SwordDamage class. It will print a prompt to the console asking the user to specify whether the sword is magic and/or flaming, then it will do the calculation. Here’s an example of the output of the app:


EXERCISE

Draw a class diagram for the SwordDamage class. Then create a new console app and add the SwordDamage class. While you’re carefully entering the code, take a really close look at how the SetMagic and SetFlaming methods work, and how they work a little differently from each other. Once you’re confident you understand it, you can build out the top-level statements. Here’s what they’ll do:

Create a new instance of the SwordDamage class.

Write the prompt to the console and read the key. Call Console.ReadKey(false) so the key that the user typed is printed to the console. If the key isn’t 0, 1, 2, or 3, return to end the program.

Roll 3d6 by calling Random.Shared.Next(1, 7) three times and adding the results together, and set the Roll field.

If the user pressed 1 or 3 call SetMagic(true): otherwise call SetMagic(false). You don’t need an if statement to do this: key == '1' returns true, so you can use || to check the key directly inside the argument.

If the user pressed 2 or 3, call SetFlaming(true); otherwise call SetFlaming(false). Again, you can do this in a single statement using == and ||.

Write the results to the console. Look carefully at the output and use \n to insert line breaks where needed.

EXERCISE SOLUTION

This console app rolls for damage by creating a new instance of the SwordDamage class that we gave you and generating output that matches the example.


SwordDamage swordDamage = new SwordDamage();
while (true)
{
    Console.Write("0 for no magic/flaming, 1 for magic, 2 for
flaming, " +
                   "3 for both, anything else to quit: ");
    char key = Console.ReadKey().KeyChar;
    if (key != '0' && key != '1' && key != '2' && key != '3') return;
    int roll = Random.Shared.Next(1, 7) + Random.Shared.Next(1, 7)
        + Random.Shared.Next(1, 7);
    swordDamage.Roll = roll;
    swordDamage.SetMagic(key == '1' || key == '3');
    swordDamage.SetFlaming(key == '2' || key == '3');
    Console.WriteLine("\nRolled " + roll + " for " + swordDamage.Damage + " HP\n");
}

Yes! We can build a MAUI app that uses the same class. Let’s find a way to reuse the SwordDamage class in a MAUI app. The first challenge for us is how to provide an intuitive user interface. A sword can be magic, flaming, both, or none, so we need to figure out how we want to handle that in the UI—and there are a lot of options.

One way to design it would be to use a picker with four options, like this:


But that’s a little... weird? There’s got to be a better way to design the app, right?

Design a MAUI version of the damage calculator app
Let’s build a .NET MAUI damage calculator app for Owen. We’ll give you the code-behind C# code for it. Your job will be to create the XAML that works with the C# code.

In this project, you’ll be working with two new things that you haven’t used yet:

 Your app will use two checkboxes. A checkbox is a control that should be very familiar to you—it’s a box that displays a check when you click it, and is empty when you click it again. In MAUI, the Checkbox control has a Boolean value that’s true if the box is checked and false if the box is not unchecked.

 The C# code in your app will use string interpolation to build a string to display to the user. You’ve been using the + operator to build strings by concatenating values together. String interpolation does the same thing, but in a way that’s easier to read.

How your damage calculator app will work
Here’s the main page for the damage calculator. It has two Checkbox controls to turn flaming and magic on and off, a Button to roll for damage, and a Label to display the results.

 When you click the button, it generates three random numbers to do a 3d6 roll (just like the console app did), then uses the SwordDamage class to display the damage.

 Clicking on a checkbox causes the label to update automatically. When you check or uncheck either of the checkboxes, it updates the SwordDamage fields, recalculates the damage, and updates the label.


EXERCISE


NOTE
We didn’t forget about accessibility! We wanted to concentrate on giving you practice laying out a grid on your own. You’ll add semantic properties to the app later in the chapter. But this is a great time to add them on your own if you want to.

Get the C# code ready for the SwordDamageCalculator app.

Add the SwordDamage class to your app.

Add the code-behind C# code we gave you to MainPage.xaml.cs file.

Modify AppShell.xaml to change the title to "Damage Calculator".

Write the XAML for the SwordDamageCalculator app’s main page.

The main page uses a grid:


Add two Label controls and two Checkbox controls to the top row (Grid.Row="0”), a Button control to the middle row (Grid.Row="1”), and a Label to the bottom row (Grid.Row="2”) and set their properties so they match the screenshot:

The Flaming and Magic labels have these properties: FontSize="Medium" VerticalOptions="Center" HorizontalOptions="End" – this causes them to be centered vertically but moved to the right of the cell.

Give the Checkbox controls x:Name values of “Flaming” and “Magic” and have CheckChanged events call the event handler methods that we gave you. Set these properties to move them to the left of the cell: VerticalOptions="Center" HorizontalOptions="Start" Margin="20,0,0,0"

We gave the Button control a 2-pixel black border using its BorderColor and BorderWidth properties and set its font size to Medium. It spans all 4 columns in the row. Make it call the Clicked event handler that we gave you.

The Label at the bottom has these properties: x:Name="Damage" Margin="0,20,0,0" BackgroundColor="Black" TextColor="White" FontSize="Large" VerticalTextAlignment="Center" HorizontalTextAlignment="Center"

EXERCISE SOLUTION


Tabletop talk (or maybe... dice discussion?)
It’s game night! Owen’s entire gaming party is over, and he’s about to unveil his brand-new sword damage calculator. Let’s see how that goes.

NOTE
We told you there was a bug in the code! How do you think you’ll fix it?


Jayden: Owen, what are you talking about?

Owen: I’m talking about this new app that will calculate sword damage...automatically.

Matthew: Because rolling dice is so very, very hard.

Jayden: Come on, people, no need for sarcasm. Let’s give it a chance.

Owen: Thank you, Jayden. This is a perfect time, too, because Brittany just attacked the rampaging were-cow with her flaming magic sword. Go ahead, B. Give it a shot.

Brittany: Okay. We just started the app. I checked the Magic box. Looks like it’s got an old roll in there, let me click roll to do it again, and...

Jayden: Wait, that’s not right. Now you rolled 14, but it still says 3 HP. Click it again. Rolled 11 for 3 HP. Click it some more. 9, 10, 5, all give 3 HP. Owen, what’s the deal?

Brittany: Hey, it sort of works. If you click roll, then check the boxes a few times, eventually it gives the right answer. Looks like I rolled 10 for 22 HP.

Jayden: You’re right. We just have to click things in a really specific order. First we click roll, then we check the right boxes, and just to be sure we check the Flaming box twice.

Owen: You’re right. If we do things in exactly that order, the program works. But if we do it in any other order, it breaks. OK, we can work with this.

Matthew: Or...maybe we can just do things the normal way, with real dice?


Let’s try to fix that bug
When you run the program, what’s the first thing that it does? Let’s take a closer look at this method at the very top of the MainPage class in the code-behind for the page in MainPage.xaml.cs:


When a class has a constructor, it’s the very first thing that gets run when a new instance of that class is created. When your app starts up and creates an instance of MainPage, first it initializes the fields—including creating a new SwordDamage object—and then it calls the constructor.

The program calls RollDice just before showing you the window, and we see the problem every time we click roll, so maybe we can fix this by guessing what’s wrong, and trying out a possible solution to the problem?

Make these changes to the RollDice method so it sets the SwordDamage fields just like the constructor does:


Now test your code. Run your program and click the button a few times. So far so good—the numbers look correct. Now check the Magic box and click the button a few more times. OK, it looks like our fix worked! There’s just one more thing to test. Check the Flaming box and click the button and...

Oops! It’s still not working
It’s still not working. When you click the button, it does the 1.75 magic multiplier, but it doesn’t add the extra 3 HP for flaming. You still need to check and uncheck the Flaming checkbox to get the right number. So the app is still broken.


Use Debug.WriteLine to print diagnostic information
In the last few chapters you used the debugger to track down bugs, but that’s not the only way developers find problems in their code. In fact, when professional developers are trying to track down bugs in their code, one of the most common things they’ll do first is to add statements that print lines of output, and that’s exactly what we’ll do to track down this bug.

Open the Output window in Visual Studio by choosing Output (Ctrl+W O) from the View menu in Windows, or Application Output from the View >> Other Windows menu on a Mac.

Luckily, .NET gives us a really useful method for this: Debug.WriteLine. Any time you want to print output lines just for debugging purposes, call that method. The Debug class is in the System.Diagnostics namespace, so start by adding a using line to the top of your SwordDamage class file:

using System.Diagnostics;
Next, add a Debug.WriteLine statement to the end of the CalculateDamage method:

public void CalculateDamage()
{
    Damage = (int)(Roll * MagicMultiplier) + BASE_DAMAGE + FlamingDamage;
    Debug.WriteLine($"CalculateDamage set Damage to {Damage} (roll: {Roll})");
}
Now add another Debug.WriteLine statement to the end of the SetMagic method, and one more to the end of the SetFlaming method. They should be identical to the one in CalculateDamage, except that they print “SetMagic” or “SetFlaming” instead of “CalculateDamage” to the output:

public void SetMagic(bool isMagic)
{
    // the rest of the SetMagic method stays the same
    Debug.WriteLine($"SetMagic finished: Damage = {Damage} (roll: {Roll})");
}

public void SetFlaming(bool isFlaming)
{
    // the rest of the SetFlaming method stays the same
    Debug.WriteLine($"SetFlaming finished: Damage = {Damage} (roll: {Roll})");
}
Run your app again. Now you’ll see debug messages in the application output window.

Open the Output window to see the debug messages. If you’re on a Mac, check the bottom of the Visual Studio window for an “Application Output” tab.

Always think about what caused a bug before you try to fix it.

When something goes wrong in your code, it’s really tempting to jump right in and immediately start writing more code to try to fix it. It may feel like you’re taking action quickly, but it’s way too easy to just add more buggy code. It’s always safer to take the time to figure out what really caused the bug, rather than just try to stick in a quick fix. Diagnostic tools like Debug.WriteLine are there to help you think through the problems.

SLEUTH IT OUT


NOTE
You can sleuth out this bug without setting any breakpoints. Developers do this all the time. Now you can do it too!

A Scandal at the Gaming Table

Let’s use the Output window to debug the app. You can always press the Clear All ( or ) button to clear it.

Run your program and watch the output. As it loads, you’ll see a bunch of lines with messages about the CLR loading various DLLs (that’s normal, just ignore them for now). Then you’ll see this output:


That gives us a clue about the first mystery—why does the app always show 3 HP when it starts up, no matter what the roll is? It’s because it’s using 0 for the roll. It must not be setting the SwordDamage.Roll property.

Let’s keep looking for more clues. Check the Flaming box. When we did it, our was 14, so this is what it printed:


19 is the correct answer for that roll: 14 plus base damage of 3 plus 2 for a flaming sword. So far so good.

Thanks to the debug messages, you can see what methods are being called. The SetFlaming method called CalculateDamage, which calculated 17 and then executed the first Debug.WriteLine statement. It then added FLAME_DAMAGE (2) to get the value up to 19, and finally executed the second Debug.WriteLine statement.

Now press the button to roll again. The program should write four more lines to the Output window:


We rolled a 12, so it should calculate 17 HP. But it didn’t—it calculated 15. What does the debug output tell us?

First the RollDice method called SetFlaming, which calculated 17 just like before.

But then it called the CalculateDamage method, which overwrote the Damage field and set it back to 15.

The problem is that SetFlaming was called before CalculateDamage, so even though it added the flame damage correctly, calling CalculateDamage afterward undid that. So the real reason that the program doesn’t work is that the fields and methods in the SwordDamage class need to be used in a very specific order:

Set the Roll field to the 3d6 roll.

Call the SetMagic method.

Call the SetFlaming method.

Do not call the CalculateDamage method. SetFlaming does that for you.

NOTE
Debug.WriteLine is one of the most basic (and useful!) debugging tools in your developer toolbox. Sometimes the quickest way to sleuth out a bug in your code is to strategically add Debug.WriteLine statements to give you important clues that help you crack the case.

And that’s why the console app worked, but the MAUI version didn’t. The console app used the SwordDamage class in the specific way that it works. The MAUI app called them in the wrong order, so it got incorrect results.

Now we know what caused the bug! But we won’t fix this project yet. We’ll return to fix the project after learning more about encapsulation.


People won’t always use your classes in exactly the way you expect.

And most of the time those “people” who are using your classes are you! You might be writing a class today that you’ll be using tomorrow, or next month. Luckily, C# gives you a powerful technique to make sure your program always works correctly—even when people do things you never thought of. It’s called encapsulation and it’s really helpful for working with objects. The goal of encapsulation is to restrict access to the “guts” of your classes so that all of the class members are safe to use and difficult to misuse. This lets you design classes that are much more difficult to use incorrectly—and that’s a great way to prevent bugs like the one you sleuthed out in your sword damage calculator.

THERE ARE NO DUMB QUESTIONS
Q: What’s the difference between Console.WriteLine and Debug.WriteLine?

A: The Console class is used by console apps to get input from and send output to the user. It uses the three standard streams provided by your operating system: standard input (stdin), standard output (stdout), and standard error (stderr). Standard input is the text that goes into the program, and standard output is what it prints. (If you’ve ever piped input or output in a shell or command prompt using <, >, |, <<, >>, or || you’ve used stdin and stdout.) The Debug class is in the System.Diagnostics namespace, which gives you a hint about its use: it’s for helping diagnose problems by tracking down and fixing them. Debug. WriteLine sends its output to trace listeners, or special classes that monitor diagnostic output from your program and write them to the console, log files, or a diagnostic tool that collects data from your program for analysis.

Q: Can I use constructors in my own code?

A: Absolutely. A constructor is a method that the CLR calls when it first creates a new instance of an object. It’s just an ordinary method—there’s nothing weird or special about it. You can add a constructor to any class by declaring a method without a return type (so no void, int, or other type at the beginning) that has the same name as the class. Any time the CLR sees a method like that in a class, it recognizes it as a constructor and calls it any time it creates a new object and puts it on the heap.

RELAX

We’re not done with constructors.

We’ll do a lot more work with constructors later in the chapter. For now, just think of a constructor as a special method that you can use to initialize an object.

It’s easy to accidentally misuse your objects
Owen’s app ran into problems because we assumed that the CalculateDamage method would, well, calculate the damage. It turned out that it wasn’t safe to call that method directly because it replaced the Damage value and erased any calculations that were already done. Instead, we needed to let the SetFlaming method call CalculateDamage for us—but even that wasn’t enough, because we also had to make sure that SetMagic was always called first. So even though the SwordDamage class technically works, it causes problems when code calls it in an unexpected way.

How the SwordDamage class expected to be used

The SwordDamage class gave the app a good method to calculate the total damage for a sword. All it had to do was set the roll, then call the SetMagic method, and finally call the SetFlaming method. If things are done in that order, the Damage field is updated with the calculated damage. But that’s not what the app did.


How the SwordDamage class was actually used

Instead, it set the Roll field, then it called SetFlaming, which added the extra damage for the flaming sword to the Damage field. Then it called SetMagic, and finally it called CalculateDamage, which reset the Damage field and discarded the extra flaming damage.


Encapsulation means keeping some data in a class private
There’s a way to avoid the problem of misusing your objects: make sure that there’s only one way to use your class. C# helps you do that by letting you declare some of your fields as private. So far, you’ve only seen public fields. If you’ve got an object with a public field, any other object can read or change that field. If you make it a private field, then that field can only be accessed from inside that object (or by another instance of the same class).

When in doubt, make it private
Worried about trying to figure out which fields and methods to make private? Start by making every member private, and change them to public only if you need to. In this case, laziness can work to your advantage. If you leave off the “private” or “public” declaration, then C# will just assume that your field or method is private.


By making the CalculateDamage method private, we prevent the app from accidentally calling it and resetting the Damage field. Changing the fields involved in the calculation to make them private keeps an app from interfering with the calculation. When you make some data private and then write code to use that data, it’s called encapsulation. When a class protects its data and provides members that are safe to use and difficult to misuse, we say that it’s well-encapsulated.

Use encapsulation to control access to your class’s methods and fields
When you make all of your fields and methods public, any other class can access them. Everything your class does and knows about becomes an open book for every other class in your program...and you just saw how that can cause your program to behave in ways you never expected.

That’s why the public and private keywords are called access modifiers: they modify access to class members. Encapsulation lets you control what you share and what you keep private inside your class. Let’s see how this works.

 Super-spy Herb Jones is a secret agent object in a spy game set in the 1960s defending life, liberty, and the pursuit of happiness as a U.S. secret agent undercover in the Soviet Union. His object is an instance of the SecretAgent class.



 Agent Jones has a plan to help him evade the enemy agent object. He added an AgentGreeting method that takes a password as its parameter. If he doesn’t get the right password, he’ll only reveal his alias, Dash Martin.


 Seems like a foolproof way to protect the agent’s identity, right? As long as the agent object that calls it doesn’t have the right password, the agent’s name is safe.


But is the RealName field REALLY protected?
So as long as the enemy doesn’t know any SecretAgent object passwords, the agents’ real names are safe. Right? But that doesn’t do any good if that data’s kept in public fields.


What can Agent Jones do? He can use private fields to keep his identity secret from enemy spy objects. Once he declares the realName field as private, the only way to get to it is by calling methods that have access to the private parts of the class. So the enemy agent is foiled!

NOTE
The KgbAgent object can’t access the SecretAgent’s private fields because they’re instances of different classes.

NOTE
Just replace public with private, and now the field is hidden from any object that isn’t an instance of the same class. Keeping the right fields and methods private makes sure no outside code is going to change values you’re using when you don’t expect it. We renamed the fields to start with lowercase letters to make our code more readable.

private string
realName;
private string
password;
BRAIN POWER

Making the methods and fields in the damage calculator app private prevents bugs by keeping the app from using them directly. But there’s still a problem! We’ll still get the wrong answer if SetMagic is called before SetFlaming. Can the private keyword help you prevent that?

Private fields and methods can only be accessed from instances of the same class
There’s only one way that an object can get at the data stored inside another object’s private fields: by using the public fields and methods that return the data. EnemyAgent and AlliedAgent agents need to use the AgentGreeting method, but friendly spies that are also SecretAgent instances can see everything...because any class can see private fields in other instances of the same class.


The only way that one object can get to data stored in a private field inside another object of a different class is by using public methods that return the data.

THERE ARE NO DUMB QUESTIONS
Q: Why would I ever want a field in an object that another object can’t read or write?

A: Sometimes a class needs to keep track of information that is necessary for it to operate, but that no other object really needs to see—and you already saw an example of this. In the last chapter you saw that the Random class used special seed values to initialize the pseudo-random number generator. Under the hood, it turns out that every instance of the Random class actually contains an array of several dozen numbers that it uses to make sure that the Next method always gives you a random number. But that array is private—when you create an instance of Random you can’t access that array. If you had access to it, you might be able to put values in it that would cause it to give nonrandom values. So the seeds have been completely encapsulated from you.

Q: OK, so I need to access private data through public methods. What happens if the class with the private field doesn’t give me a way to get at that data, but my object needs to use it?

A: Then you can’t access the data from outside the object. When you’re writing a class, you should always make sure that you give other objects some way to get at the data they need. Private fields are a very important part of encapsulation, but they’re only part of the story. Writing a class with good encapsulation means giving a sensible, easy-to-use way for other objects to get the data they need, without giving them access to hijack data your class depends on.

Q: Hey, I just noticed that when I use “Generate method” in the IDE it uses the private keyword. Why does it do that?

A: Because it’s the safest thing for the IDE to do. Not only are the methods created with “Generate method” private, but when you double-click on a control to add an event handler the IDE creates a private method for that, too. The reason is that it’s safest to make a field or method private to prevent the kinds of bugs that we saw in the damage calculator. You can always make your class members public later if you need another class to access the data.

EXERCISE

Let’s get a little practice using the private keyword by creating a small Hi-Lo game. The game starts with a pot of 10 bucks, and it picks a random number from 1 to 10. The player will guess if the next number will be higher or lower. If the player guesses right they win a buck, otherwise they lose a buck. Then the next number becomes the current number, and the game continues.

Go ahead and create a new console app for the game. Here are the top-level statements:

Console.WriteLine("Welcome to HiLo.");
Console.WriteLine($"Guess numbers between 1 and {HiLoGame.MAXIMUM}.");
HiLoGame.Hint();
while (HiLoGame.GetPot() > 0)
{
    Console.WriteLine("Press h for higher, l for lower, ? to buy a hint,");
    Console.WriteLine($"or any other key to quit with {HiLoGame.GetPot()}.");
    char key = Console.ReadKey(true).KeyChar;
    if (key == 'h') HiLoGame.Guess(true);
    else if (key == 'l') HiLoGame.Guess(false);
    else if (key == '?') HiLoGame.Hint();
    else return;
}
Console.WriteLine("The pot is empty. Bye!");
Next, add a static class called HiLoGame and add the following members. Since this is a static class, all of the members need to be static. Make sure to include either public or private in the declaration for each member:

A constant integer MAXIMUM that defaults to 10. Remember, you can’t use the static keyword with constants.

Two int fields called currentNumber and nextNumber that are both initialized to random numbers.

An integer field called pot with the number of bucks in the pot. Make this field private.

NOTE
We made pot private because we don’t want other classes to be able to add money, but the top-level statements still need to be able to print the size of the pot to the console. Look carefully at the top-level statements—can you figure out how the top-level statements get the value of the pot field without making the field writeable?

A method called Guess with a bool parameter called higher that does the following (look closely at the top-level statements to see how it’s called):

If the player guessed higher and the next number is >= the current number OR if the player guessed lower and the next number is <= the current number, write “You guessed right!” to the console and increment the value in the pot.

Otherwise, it writes “Bad luck, you guessed wrong.” to the console and decrements the pot.

It sets currentNumber to nextNumber, then sets nextNumber to a new random number for the player to guess.

It writes “The current number is {currentNumber}” to the console.

A Hint method that finds half the maximum and writes either “The current number is {currentNumber}, the next is at least {half}” or “The current number is {currentNumber}, the next is at most {half}” then decrements the pot.

EXERCISE SOLUTION

Here’s the rest of the code for the Hi-Lo game. The game starts with a pot of 10 bucks, and it picks a random number from 1 to 10. The player will guess if the next number will be higher or lower. If the player guesses right they win a buck, otherwise they lose a buck. Then the next number becomes the current number, and the game continues.

Here’s the code for the HiLoGame class:



Because sometimes you want your class to hide information from the rest of the program.

A lot of people find encapsulation a little odd the first time they come across it because the idea of hiding one class’s fields, properties, or methods from another class is a little counterintuitive. There are some very good reasons that you’ll want to think about what information should be exposed to the rest of the program.

Encapsulation means having one class hide information from another. It helps you prevent bugs in your programs.

WATCH IT!

Encapsulation is not the same as security. Private fields are not secure.

If you’re building a game with 1960s spies, encapsulation is a great way to prevent bugs. If you’re building a program for real spies, encapsulation is a terrible way to protect their data. For example, go back to your Hi-Lo game. Place a breakpoint on the first line of Program.cs, add a watch for Random.Shared, and debug the program. If you expand Static Members >> Non-Public Members >> LocalRandom >> Non-Public Members you can see the internals of the class, including its seed array (an array of long values that it uses to generate its pseudo-random numbers).

It’s not just the IDE that can see your objects’ privates. .NET has a tool called reflection that lets you write code to access objects in memory and look at their contents, even private fields. Here’s a quick example of how it works. Create a new console app and add a class called HasASecret:

class HasASecret
{
    // This class has a secret field. Does the private keyword make it secure?
    private string secret = "xyzzy";
}
The reflection classes are in the System.Reflection namespace, so add this using statement to Program.cs, just above the top-level statements:

using System.Reflection;
Here are the top-level statements for Program.cs—they create a new instance of HasASecret, and then use reflection to read its secret field. It calls the GetType method, which is a method that you can call from any object to get information about its type:

using System.Reflection;

HasASecret keeper = new HasASecret();

// Uncommenting this Console.WriteLine statement causes a compiler error:
// 'HasASecret.secret' is inaccessible due to its protection level
// Console.WriteLine(keeper.secret);

// But we can still use reflection to get the value of the secret field
FieldInfo[] fields = keeper.GetType().GetFields(
                BindingFlags.NonPublic | BindingFlags.Instance);

// This foreach loop will cause "xyzzy" to be printed to the console
foreach (FieldInfo field in fields)
{
    Console.WriteLine(field.GetValue(keeper));
}
Why encapsulation? Think of an object as an opaque box...
Sometimes you’ll hear a developer refer to an object as an opaque box, and that’s a pretty good way of thinking about objects in general. When we say something is an opaque box, we’re saying that we can see how it behaves, but we have no way of knowing how it actually works.

When you call an object’s method, you don’t really care how that method works—at least, not right now. All you care about is that it takes the inputs you gave it and does the right thing.


You could include a lot more controls, like a window that shows you what’s going on inside the box, and knobs and dials that let you muck with its internals. But if they don’t actually do anything that your system needs, then they don’t do you any good and can only cause problems.

Encapsulation makes your classes...
 Easier to use

You already know that classes use fields to keep track of their state. Many of them use methods to keep those fields up to date—methods that no other class will ever call. It’s pretty common to have a class that has fields, methods, and properties that will never be called by any other class. If you make those members private, then they won’t show up in the IntelliSense window later when you need to use that class. Less clutter in the IDE will make your class easier to use.

 Less prone to bugs

That bug in Owen’s program happened because the app accessed a method directly rather than letting the other methods in the class call it. If that method had been private, we could have avoided that bug.

 Flexible

A lot of times, you’ll want to go back and add features to a program you wrote a while ago. If your classes are well-encapsulated, then you’ll know exactly how to use them and add on to them later.

BRAIN POWER

How could building a poorly encapsulated class now make your programs harder to modify later?

A few ideas for encapsulating classes
 Is everything in your class public?

If your class has nothing but public fields and methods, you probably need to spend a little more time thinking about encapsulation.

 Think about ways fields and methods can be misused.

What can go wrong if they’re not set or called properly?

 What fields require some processing or calculation to happen when they’re set?

Those are prime candidates for encapsulation. If someone writes a method later that changes the value in any one of them, it could cause problems for the work your program is trying to do.


 Only make fields and methods public if you need to.

If you don’t have a reason to declare something public, don’t—you could make things really messy for yourself by making all of the fields in your program public. But don’t just go making everything private, either. Spending a little time up front thinking about which fields really need to be public and which don’t can save you a lot of time later.


Exactly! The difference is that the well-encapsulated one is built in a way that prevents bugs and is easier to use.

It’s easy to take a well-encapsulated class and turn it into a poorly encapsulated class: do a search and replace to change every occurrence of private to public.

And that’s a funny thing about the private keyword: you can generally take any program and do that search and replace, and it will still compile and work in exactly the same way. That’s one reason that encapsulation can be a little difficult for some programmers to really “get” when they first see it.

When you come back to code that you haven’t looked at in a long time, it’s easy to forget how you intended it to be used. That’s where encapsulation can make your life a lot easier!

This book so far has been about making programs do things—perform certain behaviors. Encapsulation is a little different. It doesn’t change the way your program behaves. It’s more about the “chess game” side of programming: by hiding certain information in your classes when you design and build them, you set up a strategy for how they’ll interact later. The better the strategy, the more flexible and maintainable your programs will be, and the more bugs you’ll avoid.

NOTE
And just like chess, there are an almost unlimited number of possible encapsulation strategies!

If you encapsulate your classes well today, that makes them a lot easier to reuse tomorrow.

BULLET POINTS
Always think about what caused a bug before you try to fix it. Take the time to really understand what’s going on.

Adding statements that print lines of output can be an effective debugging tool. Use Debug.WriteLine when you add statements to print diagnostic information.

A constructor is a method that the CLR calls when it first creates a new instance of an object.

String interpolation makes string concatenation more readable. Use it by adding a $ in front of a string and including values in {curly brackets}.

The System.Console class writes its output to standard streams that provide the input and output for console apps.

The System.Diagnostics.Debug class writes its output to trace listeners—special classes that perform specific actions with diagnostic output—including one that writes that output to the IDE’s Output (Windows) or Application Output (macOS) window.

People won’t always use your classes in exactly the way you expect. Encapsulation is a technique for making your class members flexible and difficult to misuse.

Encapsulation usually involves using the private keyword to keep some of the fields or methods in a class private so they can’t be misused by other classes.

When a class protects its data and provides members that are safe to use and difficult to misuse, we say that it’s well-encapsulated.



Let’s use encapsulation to improve the SwordDamage class
We just covered some great ideas for encapsulating classes. Let’s see if we can start to apply those ideas to the SwordDamage class to keep it from being confused, misused, and abused by any app that we include it in.

Is every member of the SwordDamage class public?
Yes, indeed. The four fields (Roll, MagicMultiplier, FlamingDamage, and Damage) are public, and so are the three methods (CalculateDamage, SetMagic, and SetFlaming). We could stand to think about encapsulation.

Making members of a class private can prevent bugs caused by other classes calling its public methods or updating its public fields in unexpected ways.

Are fields or methods being misused?
Absolutely. In the first version of the damage calculator app, we called CalculateDamage when we should have just let the SetFlaming method call it. Even our attempt to fix it failed because we misused the methods by calling them in the wrong order.

Is there calculation required after setting a field?
Certainly. After setting the Roll field, we really want the instance to calculate damage immediately.

So what fields and methods really need to be public?
That’s a great question. Take some time to think about the answer. We’ll tackle it at the end of the chapter.

BRAIN POWER

Think about those questions, then take another look at how the SwordDamage class works. What would you do to fix the SwordDamage class?

Encapsulation keeps your data safe
We’ve seen how the private keyword protects class members from being accessed directly, and how that can prevent bugs caused by other classes calling methods or updating fields in ways we didn’t expect—like how your GetPot method in the Hi-Lo game gave read-only access to the private pot field, and only the Guess or Hint methods could modify it. This next class works in exactly the same way.

Let’s use encapsulation in a class
Let’s build a PaintballGun class for a paintball arena video game. The player can pick up magazines of paintballs and reload at any time, so we want the class to keep track of the total number of balls the player has and the number of balls currently loaded. We’ll add a method to check if the gun is empty and needs to be reloaded. We also want it to keep track of the magazine size. Any time the player gets more ammo we want the gun to automatically reload a full magazine, so we’ll make sure that always happens by providing a method to set the number of balls that calls the Reload method.


Does the IsEmpty method make code that calls this class easier to read? Or is it redundant? There’s no right or wrong answer—you could argue either side.

Write a console app to test the PaintballGun class
NOTE
 Do this!

Let’s try out our new PaintballGun class. Create a new console app callde Paintball and add the PaintballGun class to it. Here are the top-level statements—it uses a loop to call the various methods in the class:


Our class is well-encapsulated, but...
The class works, and we encapsulated it pretty well. The balls field is protected: it doesn’t let you set a negative number of balls, and it stays in sync with the ballsLoaded field. The Reload and Shoot methods work as expected, and there don’t seem to be any obvious ways we could accidentally misuse this class.

But have a closer look at this line from the top-level statements:

else if (key == '+') gun.SetBalls(gun.GetBalls() + PaintballGun.MAGAZINE_SIZE);
Let’s be honest—that’s a downgrade from a field. If we still had a field, we could use the += operator to increase it by the magazine size. Encapsulation is great, but we don’t want it to make our class annoying or difficult to use.

Is there a way to keep the balls field protected but still get the convenience of +=?


Properties make encapsulation easier
So far you’ve learned about two kinds of class members, methods and fields. There’s a third kind of class member that helps you encapsulate your classes: the property. A property is a class member that looks like a field when it’s used, but it acts like a method when it runs.

A property is declared just like a field, with a type and a name, except instead of ending with a semicolon it’s followed by curly brackets. Inside those brackets are property accessors, or methods that either return or set the property value. There are two types of accessors:

 A get property accessor, usually just referred to as a get accessor or getter, that returns the value of the property. It starts with the get keyword, followed by a method inside curly brackets. The method must return a value that matches the type in the property declaration.

 A set property accessor, usually just referred to as a set accessor or setter, that sets the value of the property. It starts with the set keyword, followed by a method inside curly brackets. Inside the method, the value keyword is a read-only variable that contains the value being set.

It is very common for a property to get or set a backing field, which is what we call a private field that’s encapsulated by restricting access to it through a property.

Replace the GetBalls and SetBalls methods with a property
NOTE
 Replace this!

Here are the GetBalls and SetBalls methods from your PaintballGun class:

public int GetBalls() { return balls; }

public void SetBalls(int numberOfBalls)
{
    if (numberOfBalls > 0)
        balls = numberOfBalls;
    Reload();
}
This is refactoring. You’re modifying the PaintbalGun class so it behaves the same way but is structured differently.

Let’s replace them with a property. Delete both methods.

Then add this Balls property:


Modify your top-level statements to use the Balls property
Now that you’ve replaced the GetBalls and SetBalls methods with a single property called Balls, your code won’t build anymore. You need to update the top-level statements to use the Balls property instead of the old methods.

The GetBalls method was called in this Console.WriteLine statement:

NOTE
 Update this!

Console.WriteLine($"{gun.GetBalls()} balls, {gun.GetBallsLoaded()} loaded");
You can fix that by replacing GetBalls() with Balls—when you do this, the statement will work just like before. Let’s have a look at the other place where GetBalls and SetBalls were used:

else if (key == '+') gun.SetBalls(gun.GetBalls() + PaintballGun.MAGAZINE_SIZE);
This was that messy line of code that looked ugly and clunky. Properties are really useful because they work like methods but you use them like fields. So let’s use the Balls property like a field—replace that line with this statement that uses the += operator exactly like it would if Balls were a field:

else if (key == '+') gun.Balls += PaintballGun.MAGAZINE_SIZE;
NOTE
If Balls were a field, this is how you would use the += operator to update it. You use properties exactly the same way.

Here are the updated top-level statements:

PaintballGun gun = new PaintballGun();
while (true)
{
    Console.WriteLine($"{gun.Balls} balls, {gun.GetBallsLoaded()} loaded");
    if (gun.IsEmpty()) Console.WriteLine("WARNING: You're out of ammo");
    Console.WriteLine("Space to shoot, r to reload, + to add ammo, q to quit");
    char key = Console.ReadKey(true).KeyChar;
    if (key == ' ') Console.WriteLine($"Shooting returned {gun.Shoot()}");
    else if (key == 'r') gun.Reload();
    else if (key == '+') gun.Balls += PaintballGun.MAGAZINE_SIZE;
    else if (key == 'q') return;
}
Debug your PaintballGun class to understand how the property works
Use the debugger to really get a good sense of how your new Ball property works:

 Place a breakpoint inside the curly brackets of the get accessor (return balls;).

 Place another breakpoint on the first line of the set accessor (if (value > 0)).

 Place a breakpoint at the top of Program.cs and start debugging. Step over each statement.

 When you step over Console.WriteLine, the debugger will hit the breakpoint in the getter.

 Keep stepping over methods. When you execute the += statement, the debugger will hit the breakpoint in the setter. Add a watch for the backing field balls and the value keyword.

Auto-implemented properties simplify your code
NOTE
 Add this!

A very common way to use a property is to create a backing field and provide get and set accessors for it. Let’s create a new BallsLoaded property that uses the existing ballsLoaded field as a backing field:


Now you can delete the GetBallsLoaded method and modify your top-level statements to use the property:

Console.WriteLine($"{gun.Balls} balls, {gun.BallsLoaded} loaded");
Run your program again. It should still work exactly the same way.

Use the prop snippet to create an auto-implemented property
NOTE
VSCode doesn’t support snippets yet, so if you’re using VSCode just type in the whole property.

An auto-implemented property—sometimes called an automatic property or auto-property—is a property that has a getter that returns the value of the backing field, and a setter that updates it. In other words, it works just like the BallsLoaded property that you just created. There’s one important difference: when you create an automatic property you don’t define the backing field. Instead, the C# compiler creates the backing field for you, and the only way to update it is to use the get and set accessors.

Visual Studio gives you a really useful tool for creating automatic properties: a code snippet, or a small, reusable block of code that the IDE inserts automatically. Let’s use it to create a BallsLoaded auto-property.

 Remove the BallsLoaded property and backing field.

Delete the BallsLoaded property you added, because we’re going to replace it with an auto-implemented property. Then delete the ballsLoaded backing field (private int ballsLoaded;) too, because any time you create an automatic property the C# compiler generates a hidden backing field for you.

 Tell the IDE to start the prop snippet.

Put your cursor where the field used to be, and then type prop and press the Tab key twice to tell the IDE to start a snippet. It will add this line to your code:


The snippet is a template that lets you edit parts of it—the prop snippet lets you edit the type and the property name. Press the Tab key once to switch to the property name, then change the name to BallsLoaded and press Enter to finalize the snippet


 Fix the rest of the class.

Since you removed the ballsLoaded field, your PaintballGun class doesn’t compile anymore. That has a quick fix—the ballsLoaded field appears five times in the code (once in the IsEmpty method, and twice in the Reload and Shoot methods). Change them to BallsLoaded—now your app works again.

Use a private setter to create a read-only property
Let’s take another look at the auto-implemented property that you just created:

public int BallsLoaded { get; set; }
This is definitely a great replacement for a property with get and set accessors that just update a backing field. It’s more readable and has less code than the ballsLoaded field and GetBallsLoaded method. So that’s an improvement, right?

But there’s one problem: we’ve broken the encapsulation. The whole point of the private field and public method was to make the number of balls loaded read-only. The top-level statements could easily set the BallsLoaded property. We made the field private and created a public method to get the value so that it could only be modified from inside the PaintballGun class.

Make the BallsLoaded setter private
Luckily, there’s a quick way to make our PaintballGun class well-encapsulated again. When you use a property, you can put an access modifier in front of the get or set keyword.

You can make a read-only property that can’t be set by another class by making its set accessor private. In fact, you can leave out the set accessor entirely for normal properties—but not automatic properties, which must have a set accessor or your code won’t compile.

So let’s make the set accessor private:

public int BallsLoaded { get; private set; }
NOTE
You can make your automatic property read-only by making its setter private.

Now the BallsLoaded field is a read-only property. It can be read anywhere, but it can only be updated from inside the PaintballGun class. The PaintballGun class is well-encapsulated again.


Exactly. Making a set accessor private is a great way to improve encapsulation for a class.

Think about how a paintball gun would work in a paintball arena game. Usually, there are only two things that affect the ammo loaded in the gun: the player loading or firing it. If we design the app so that only the PaintballGun class can modify its BallsLoaded property, it means we won’t accidentally update it from any other class in the system. That’s a great way to prevent bugs.

What if we want to change the magazine size?
Right now the PaintballGun class uses a const for the magazine size:

public const int MAGAZINE_SIZE = 16;
NOTE
 Replace this!

What if we want the game to set the magazine size when it instantiates the gun? Let’s replace it with a property.

 Remove the MAGAZINE_SIZE constant and replace it with a read-only property.

public int MagazineSize { get; private set; }
 Modify the Reload method to use the new property.

if (balls > MagazineSize)
     BallsLoaded = MagazineSize;
 Fix the line in the top-level statements that adds the ammo.

else if (key == '+') gun.Balls += gun.MagazineSize;
But there’s a problem...how do we initialize MagazineSize?
The MAGAZINE_SIZE constant used to be set to 16. Now we’ve replaced it with an auto-property, and if we want, we can initialize it to 16 just like a field by adding a field initializer to the end of the declaration:

NOTE
It’s called a field initializer, even if you’re using it to initialize a property.

public int MagazineSize { get; private set; } = 16;
Now the MagazineSize property will be initialized to 16 as soon as the game starts. We can even change this line to use Random.Shared.Next to initialize the magazine with a random number of paintballs:

public int MagazineSize { get; private set; } = Random.Shared.Next(8, 17);
But let’s say we wanted to do something a little different—like initialize it to the value of the BallsLoaded property:

public int MagazineSize { get; private set; } = BallsLoaded;

Now you get a compiler error. You can only use a literal, constant, or static field, method, or property in a field initializer. Random.Shared is a static property so you’re allowed to use it in your field initializer. But you can’t use the BallsLoaded property, because it’s not static.

Go ahead and remove the field initializer:

public int MagazineSize { get; private set; };
What if you want the game to decide how many balls to load in a new gun depending on the current level? How would you initialize the MagazineSize property if that data isn’t available in a static field or property?

Use a constructor with parameters to initialize properties
You saw earlier in the chapter that you can initialize an object with a constructor, or a special method that’s called when the object is first instantiated. Constructors are just like any other method—which means they can have parameters. We’ll use a constructor with parameters to initialize the properties.

The constructor you just created in the Q&A answer looks like this: public ConstructorTest(). That’s a parameterless constructor, so just like any other method without parameters, the declaration ends with (). Now let’s add a constructor with parameters to the PaintballGun class. Here’s the constructor to add:


Uh-oh—there’s a problem. As soon as you add the constructor, the IDE will tell you that there’s an error:


What do you think we need to do to fix this error?

WATCH IT!

When a parameter has the same name as a field, it masks the field.

The constructor’s balls parameter has the same name as the field called balls. Since they have the same name, the parameter takes precedence inside the body of the constructor. That’s called masking—when a parameter or a variable in a method has the same name as a field, using that name in the method refers to the parameter or variable, not the field. That’s why we need to use the this keyword in the PaintballGun constructor:

this.balls = balls;
When we just use balls it refers to the parameter. We want to set the field, and since it has the same name, we need to use this.balls to refer to the field.

And by the way, this doesn’t just apply to constructors. It’s true for any method.

Specify arguments when you use the “new” keyword
When you added the constructor, the IDE told you that the top-level statements have an error on the new statement (PaintballGun gun = new PaintballGun()). Here’s what that error looks like:


Read the text of the error—it’s telling you exactly what’s wrong. Your constructor now takes arguments, so it needs parameters. Start typing the new statement again, and the IDE will tell you exactly what you need to add:


You’ve been using new to create instances of classes. So far, all of your classes have had parameterless constructors, so you never needed to provide any arguments.

Now you have a constructor with parameters, and like any method with parameters, it requires you to specify arguments with types that match those parameters.

Let’s modify your top-level statements to pass parameters to the PaintballGun constructor.

NOTE
 Modify this!

 Add the ReadInt method that you wrote for Owen’s ability score calculator in Chapter 4.

You need to get the arguments for the constructor from somewhere. You already have a perfectly good method that prompts the user for int values, so it makes sense to reuse it here.

 Add code to read values from the console input.

Now that you’ve added the ReadInt method from Chapter 4, you can use it to get two int values. Add these four lines of code to the top of your top-level statements:


 Update the new statement to add arguments.

Now that you have values in variables with types that match the parameters in the constructor, you can update the new statement to pass them to the constructor as arguments:

PaintballGun gun = new PaintballGun(numberOfBalls, magazineSize, isLoaded);
 Run your program.

Now run your program. It will prompt you for the number of balls, the magazine size, and whether or not the gun is loaded. Then it will create a new instance of PaintballGun, passing arguments to its constructor that match your choices.

SHARPEN YOUR PENCIL

Here’s the final version of the PaintballGun class. You did a lot of refactoring, and now it looks really different than the original version. Go back through all of the steps that you followed, compare the original code for the PaintballGun class with the final version, and write down everything that changed.


SHARPEN YOUR PENCIL SOLUTION

Sens-AI


To get the solution to this “Sharpen your pencil” exercise, use AI to analyze the original and refactored versions of the classes and tell you what was refactored. Open ChatGPT, Copilot, Bard, or another AI chatbot and give it this prompt:

The PaintballGun class was refactored. Describe the changes.
Here's the code for the original version of the Paintball Class:
(paste the original code that we gave you here)
Here's the code for the refactored version of the Paintball Class:
(copy the refactored code from your IDE and paste it here)
Give this same prompt to multiple AI chatbots and compare their answers with yours. Did they all agree?


THERE ARE NO DUMB QUESTIONS
Q: We replaced methods with properties earlier. Is there a difference between how a method works and how a getter or setter works?

A: No. Get and set accessors are a special kind of method—they look just like a field to other objects, and are called whenever that “field” is set. Getters always return a value that’s the same type as the field. A setter works just like a method with one parameter called value whose type is the same as the field.

Q: So you can have ANY kind of statement in a property?

A: Absolutely. Anything you can do in a method, you can do in a property—you can even include complicated logic that does anything you can do in a normal method. A property can call other methods, access other fields, and even create instances of objects. Just remember that they only get called when a property gets accessed, so they should only include statements that have to do with getting or setting the property.

Q: Why would I need complicated logic in a get or set accessor? Isn’t it just a way of modifying fields?

A: Sometimes you know that every time you set a field, you’ll have to do some calculation or perform some action. Think about Owen’s problem—he ran into trouble because the app didn’t call the SwordDamage methods in the right order after setting the Roll field. If we replaced all of the methods with properties, then we could make sure the setters do the damage calculation correctly. (In fact, you’re about to do exactly that at the end of the chapter!)

Q: I’m pretty sure I get constructors, but can you explain them one more time just so I’m sure?

A: A constructor is a special method that’s called automatically when a new instance of a class is created with the new keyword. If the constructor takes parameters, then can pass arguments when you create the new instance. You just modified the PaintballGun constructor to take three parameters – int balls, int magazineSize, bool loaded – and when you did that you had to modify the code that instantiated the class to add three arguments between the parentheses after the class name.

Q: How do I know which method in a class is its constructor?

A: A constructor is declared as a method with no return type, and the method name matches the class name. If you see a method in a class that has no return type and its function name matches the class name, it’s the constructor.

Q: Can a class have more than one constructor?

A: Yes. A class can have multiple constructors, as long as they take different parameters. Your app can figures out which constructor to call based on the arguments used in the new statement that instantiates the class.

EXERCISE

Use the debugger to really understand how the constructor works. Create a new console app and add this class with a constructor and a public field called i: (There’s no answer to this exercise, it’s just about exploring constructors).


Add one breakpoint on the field declaration and two inside the constructor. Replace the top-level statements with a single statement to instantiate the class: new ConstructorTest(2); – then run your app and watch the value of i.

SENS-AI

Use AI to help you learn about refactoring and encapsulation

One reason C# is such a flexible and useful programming language is that there are many different ways to do the same thing. And since there are so many ways to write a specific piece of code, you can choose the one that makes it easiest to understand. That’s why refactoring—or modifying the structure of code without changing its behavior—is such a powerful tool. AI chatbots can help you refactor your code.

Ask an AI chatbot to refactor your code

Here’s the AbilityScoreCalculator class that you worked on in Chapter 4:

internal class AbilityScoreCalculator
{
    public int RollResult = 14;
    public double DivideBy = 1.75;
    public int AddAmount = 2;
    public int Minimum = 3;
    public int Score;

    public void CalculateAbilityScore()
    {
        // Divide the roll result by the DivideBy field
        double divided = RollResult / DivideBy;

        // Add AddAmount to the result and round down
        int added = AddAmount + (int)divided;

        // If the result is too small, use Minimum
        if (added < Minimum)
            Score = Minimum;
        else
            Score = added;
    }
}
Read through it again, but now think about what you’ve learned about properties, constructors, and encapsulation. Do you see opportunities to refactor it? There are definitely ways to do that.

Go to your favorite AI chatbot and give it this prompt:

Refactor the following C# class to encapsulate Score by using a property
instead of a public field.

(paste the entire AbilityScoreCalculator class into the chat)
Compare the code that the chatbot generated carefully against the code that you gave it. What did it change? Did it change Score into a property? Is it protected from being accidentally modified by another class?

Make Minimum property. Set its value using a constructor, and make sure
that it can't be modified after the class is created.
Now compare the new code that the chatbot gave you. Did it do what you expected it to do? Open your project from Chapter 4 and replace AbilityScoreCalculator with this new code. Does it still work the same way?

WATCH IT!

Read all code written by an AI before you use it.

AI can be a really powerful tool for generating code. It can be especially valuable for learning, so take the time to read and understand the code that the AI chatbot generated. We also learned an important lesson in Chapter 1: AIs sometimes make mistakes. Read every line of code generated by an AI before you use it in a project. If you don’t read all of the code, your app might do something you don’t want it to do.

Pool Puzzle

Your job is to take code snippets from the pool and place them into the blank lines in the code. You may use the same snippet more than once, and you won’t need to use all the snippets. Your goal is to make classes that will compile and run and produce output that matches the sample.

This program is a math quiz game that asks a series of random multiplication or addition questions and checks the answer. Here’s what it looks like when you play it:



Pool Puzzle Solution

Your job is to take code snippets from the pool and place them into the blank lines in the code. You may use the same snippet more than once, and you won’t need to use all the snippets. Your goal is to make classes that will compile and run and produce output that matches the sample.

This program is a math quiz game that asks a series of random multiplication or addition questions and checks the answer. Here’s what it looks like when you play it:


Initialize fields and properties inline or in the constructor
We just saw in the Pool Puzzle that you can include classes in your Program.cs—they just need to be declared below the top-level statements. Let’s take advantage of that to explore a little more about how the constructor works. Create a new Console Application project and add this code to Program.cs:

new MessageWriter().WriteMessage();

class MessageWriter
{
    public string Message { get; set; }

    public void WriteMessage()
    {
        Console.WriteLine($"The message is: {Message}");
    }

}
The compiler will give you the warning about null values that we learned about in the last chapter.


Take another look at that warning—it’s telling you that the Message property must be set to a non-null value when it exits the constructor. Now that you’ve used constructors, that should make more sense.

Try giving the Message property a default value by adding an inline assignment:

public string Message { get; set; } = "This is a message";
The warning should disappear. That’s because that assignment happens before the constructor is executed. Try experimenting with this by adding a constructor, then putting breakpoints in it and on the property assignment.


NOTE
This is a really good time to talk about aesthetics in video games. If you think about it, encapsulation doesn’t really give you a way to do anything that you couldn’t before. You could still write the same programs without properties, constructors, and private methods—but they would sure look really different. That’s because not everything in programming is about making your code do something different. Often, it’s about making your code do the same thing but in a better way. Think about that when you read about aesthetics. They don’t change the way your game behaves, they change the way the player thinks and feels about the game.

GAME DESIGN... AND BEYOND

Aesthetics

How did you feel the last time you played a game? Was it fun? Did you feel a thrill, a rush of adrenaline? Did it give you a sense of discovery or accomplishment? Did you get a feeling of competition or cooperation with other players? Was there an engaging story? Was it funny? Sad? Games bring out emotional responses in us, and that’s the idea behind aesthetics.

Does it seem weird to talk about feelings and video games? It shouldn’t—emotions and feelings have always played an important part in game design, and the most successful games have an important aesthetic aspect to them. Think about that satisfying feeling you get when you drop a long piece in Tetris and it clears four rows of blocks. Or that rush in Pac-Man when Blinky (the red ghost) is just pixels behind you when you swallow the power pellet.

It’s obvious how art and visuals, music and sound, or story writing can influence aesthetics, but aesthetics is more than the artistic elements of a game. Aesthetics can come from the way the game is structured.

You can find aesthetics in tabletop games. Poker is known for its emotional highs and lows, the feeling of pulling off a great bluff. Even a simple card game like Go Fish! has its own aesthetics: the growing back and forth, as players figure out each other’s hands; the crescendo toward a winner, as players put each new book on the table; the thrill of drawing that card you need; just saying “Go fish!” when asked for the wrong card.

When a game provides a challenge it gives players obstacles to get past, creating a feeling of accomplishment and personal victory.

The pure tactile sensation of a game—the beat of a rhythm game, the satisfying “gulp” of eating a power pellet, the “vroom” and blur of an accelerating car—provides pleasure.

Playing a cooperative or multiplayer game brings a sense of fellowship with others.

A game’s narrative draws the player into the drama of a story. A game that provides fantasy not only transports a player to another world, but lets that player be another person (or non-person!) entirely.

Games with expression give the player self-discovery, a way to learn more about themselves.

Believe it or not, we can use these ideas behind aesthetics to learn a larger lesson about development that applies to any kind of program or app, not just a game. Let these ideas sink in for now—we’ll return to this in the next chapter.

NOTE
Some developers are really skeptical when they read about aesthetics because they assume that only the mechanics of the game matter. Here’s a quick thought experiment to show how important aesthetics can be. Say you have two games with identical mechanics. There’s just one very tiny difference between them. In one game you’re kicking boulders out of the way to save a village. In the other game, you’re kicking puppies and kittens because you are a horrible person. Even if every other aspect of those games is identical, those are two very different games. That’s the power of aesthetics.

SHARPEN YOUR PENCIL

This code has problems. It’s supposed to be code for a simple gumball vending machine: you put in a coin and it dispenses gum. We’ve identified four specific problems that will cause bugs. Use the lines provided to write down what you think is wrong with the lines the arrows are pointing to.


SHARPEN YOUR PENCIL SOLUTION

This code has problems. We pointed out four specific lines that will cause bugs. Here’s what’s wrong with them.


THERE ARE NO DUMB QUESTIONS
Q: If my constructor is a method, why doesn’t it have a return type?

A: Your constructor doesn’t have a return type because every constructor is always void—which makes sense, because there’s no way for it to return a value. It would be redundant to make you type void at the beginning of each constructor.

Q: Can I have a getter without a setter?

A: Yes! When you have a get accessor but no set, you create a read-only property. For example, the SecretAgent class might have a public read-only field with a backing field for the name:

string spyNumber = "007";
public string SpyNumber {
   get { return spyNumber; }
}
Q: And I bet I can have a setter without a getter, right?

A: Yes—unless it’s an auto-property, in which case you’ll get an error (“Auto-implemented properties must have get accessors”). If you create a property with a setter but no getter, then your property can only be written. The SecretAgent class could use that for a property that other spies could write to, but not see:

public string DeadDrop {
  set {
    StoreSecret(value);
  }
}
Both of those techniques—set without get, or vice versa—can come in really handy when you’re doing encapsulation.

EXERCISE

Use what you’ve learned about encapsulation to fix Owen’s sword damage calculator. First, modify the SwordDamage class to replace the fields with properties and add a constructor. Once that’s done, update the console app to use it. Finally, fix the MAUI app. (This exercise will go more easily if you create a new console app for the first two parts and a new MAUI app for the third.)

Part 1: Modify SwordDamage so it’s a well-encapsulated class

Delete the Roll field and replace it with a property named Roll and a backing field named roll. The getter returns the value of the backing field. The setter updates the backing field, and then calls the CalculateDamage method.

Delete the SetFlaming method and replace it with a property named Flaming and a backing field named flaming. It works like the Roll property—the getter returns the backing field, the setter updates it and calls CalculateDamage.

Delete the SetMagic method and replace it with a property named Magic and a backing field named magic that works exactly like the Flaming and Roll properties.

Create an auto-implemented property named Damage with a public get accessor and private set accessor.

Delete the MagicMultiplier and FlamingDamage fields. Modify the CalculateDamage method so it checks the property values for the Roll, Magic, and Flaming properties and does the entire calculation inside the method.

Add a constructor that takes the initial roll as its parameter. Now that the CalculateDamage method is only called from the property set accessors and constructor, there’s no need for another class to call it. Make it private.

Add XML code documentation to all of the public class members.

Part 2: Modify the console app to use the well-encapsulated SwordDamage class

Add a method to Program.cs called RollDice that returns the results of a 3d6 roll.

Use the new RollDice method for the SwordDamage constructor argument and to set the Roll property.

Change the code that calls SetMagic and SetFlaming to set the Magic and Flaming properties instead.

Part 3: Modify the MAUI app to use the well-encapsulated SwordDamage class

Copy the code from Part 1 into a new MAUI app. Copy the XAML from the project earlier in the chapter.

Create a RollDice method that sets swordDamage.Roll to the results of a 3d6 roll, then calls DisplayDamage.

Make the Button_Clicked event handler call the RollDice method (and do nothing else).

Your SwordDamage class now has a constructor that takes one argument. Change the declaration so it looks like this (it doesn’t matter what number you use, because the app will do a new random roll in the constructor):

SwordDamage swordDamage = new SwordDamage(3);
In the MainPage constructor, set the SwordDamage object’s Flaming and Magic properties so they match the checkboxes. Then call the RollDice method to roll and display the damage.

Change the CheckedChanged event handlers for both checkboxes to use the Magic and Flaming properties instead of the old SetMagic and SetFlaming methods, then call DisplayDamage.

Make your app more accessible. Add SemanticProperties.Description properties to the checkbox labels and SemanticProperties.Hint properties to the checkboxes and buttons. Use the screen reader to test it.

NOTE
Test everything. Use the debugger or Debug.WriteLine statements to make sure that it all REALLY works.

EXERCISE SOLUTION

Now Owen finally has a class for calculating damage that’s much easier to use without running into bugs. Each property recalculates the damage, so it doesn’t matter what order you call them in. Here’s the code for the well-encapsulated SwordDamage class:



Here’s the code for the top-level statements in Program.cs for the console app:


EXERCISE SOLUTION

Here’s the code-behind in the MainPage.xaml.cs file.


BRAIN POWER

We had you pass 3 to the SwordDamage constructor because the MainPage constructor will call RollDice and set the Roll property to a new value. This is a little messy! Can you think of a better, more readable way to handle this?

Make the screen reader announce each roll
NOTE
 Do this!

Turn on the app, start the screen reader, and close your eyes. With the semantic properties, it should be pretty easy to use. Announcements can make a big difference for people who depend on a screen reader. Wouldn’t it be great if it always announced the result every time you clicked the button to roll for damage?

Luckily, it’s easy to do that! The SemanticScreenReader.Default.Announce method tells the screen reader to announce text. Add it to your DisplayDamage method to announce the roll, then use your operating system’s screen reader to test it out.

private void DisplayDamage()
{
    Damage.Text = $"Rolled {swordDamage.Roll} for {swordDamage.Damage} HP";
    SemanticScreenReader.Default.Announce(Damage.Text);
}
NOTE
Accessibility is important! You don’t need to wait for us to tell you to add semantic properties or test your app with a screen reader. Thinking about accessibility early is a great way to improve your overall coding skills!

EXERCISE SOLUTION

Here are the semantic properties we asked you to add to make the app more accessible:

<Label Text="Flaming"
        FontSize="Medium" VerticalOptions="Center" HorizontalOptions="End"/>

<CheckBox x:Name="Flaming" Grid.Column="1"
            VerticalOptions="Center" HorizontalOptions="Start"
            SemanticProperties.Description="Determines if the sword is flaming"
            CheckedChanged="Flaming_CheckedChanged" Margin="20,0,0,0" />

<Label Text="Magic" Grid.Column="2"
        FontSize="Medium" VerticalOptions="Center" HorizontalOptions="End"/>

<CheckBox x:Name="Magic" Grid.Column="3"
            VerticalOptions="Center" HorizontalOptions="Start"
            SemanticProperties.Description="Determines if the sword is flaming"
            CheckedChanged="Magic_CheckedChanged" Margin="20,0,0,0" />

<Button Grid.Row="1" Grid.ColumnSpan="4" Margin="0,20,0,0"
        BorderColor="Black" BorderWidth="2"
        SemanticProperties.Hint="Throws a 3d6 roll for damage"
        Text="Roll for damage" FontSize="Medium" Clicked="Button_Clicked"/>

<Label x:Name="Damage" Grid.Row="2" Grid.ColumnSpan="4" Margin="0,20,0,0"
        BackgroundColor="Black" TextColor="White" FontSize="Large"
        SemanticProperties.Hint="The results of the damage roll "
        VerticalTextAlignment="Center" HorizontalTextAlignment="Center" />
A few useful facts about methods and properties
 Every method in your class has a unique signature.

The first line of a method, which contains the access modifier, return value, name, and parameters is called the method’s signature. Properties have signatures, too—they consist of the access modifier, type, and name.

 You can initialize properties in an object initializer.

You used object initializers before:

Guy joe = new Guy() { Cash = 50, Name = "Joe" };
You can also specify properties in an object initializer. If you do, the constructor is run first, then the properties are set. And you can only initialize public fields and properties in the object initializer.

 Every class has a constructor, even if you didn’t add one yourself.

The CLR needs a constructor to instantiate an object—it’s part of the behind-the-scenes mechanics of how .NET works. So if you don’t add a constructor to your class, the C# compiler automatically adds a parameterless constructor for you.

 You can keep a class from being instantiated by other classes by adding a private constructor.

Sometimes you need to have really careful control over how your objects are created. One way to do that is to make your constructor private—then it can only be called from inside the class. Take a minute and try it out:

class NoNew {
  private NoNew() { Console.WriteLine("I'm alive!"); }
  public static NoNew CreateInstance() { return new NoNew(); }
}
Add that NoNew class to a console app. If you try to add new NoNew(); to your top-level statements, the C# compiler gives you an error ('NoNew.NoNew()' is inaccessible due to its protection level), but the NoNew.CreateInstance method creates a new instance just fine.

Objectcross

Take a break, sit back, and give your brain something to do. It’s your standard crossword; all of the solution words are from the first five chapters of the book.


Across

1. What (int) is doing in this line of code: x = (int) y;

4. Looks like a field but acts like a method

7. What kind of sequence is \n or \r?

9. If you want to create instances of a class, don’t put this keyword in the declaration

12. A variable that points to an object

14. What an object is an instance of

15. The four whole-number types that only hold positive numbers

18. You can assign any value to a variable of this type

21. What you’re doing when you use $ and curly braces to include values in a string

23. Draw one of these for your class before you start writing code

26. How you start a variable declaration

27. The numeric type that holds the biggest numbers

28. What you use to pass information into a method

29. If you want to store a currency value, use this type

Down

2. Every object has this method that converts it to a string

3. An object’s fields keep track of its __________

5. namespace, for, while, using, and new are examples of _________ keywords

6. These define the behavior of a class

8. The kind of collection that happens when the last reference to an object goes away

10. To _________ two strings, use the + operator

11. How a method tells you what to pass to it

13. += and -= are _________ assignment operators

16. The second part of a variable declaration

17. Where objects live

19. A variable declared directly in a class that all its members can access

20. What floats in a float

22. Tells a method to stop immediately, possibly sending a value back to the statement that called it

24. The statement you use to create an object

25. If a method’s return type is _________, it doesn’t return anything

BULLET POINTS
Encapsulation keeps your code safe by preventing classes from modifying it unexpectedly or otherwise misusing other classes’ members.

Fields that require some processing or calculation to happen when they’re set are prime candidates for encapsulation.

Think about ways fields and methods can be misused. Only make fields and methods public if you need to.

Using consistent case when choosing names for fields, properties, variables, and methods makes code easier to read. Many developers use camelCase for private fields and PascalCase for public ones.

A property is a class member that looks like a field when it’s used, but acts like a method when it runs.

A get accessor (or getter) is defined by the get keyword followed by a method that returns the value of the property.

A set accessor (or setter) is defined by the set keyword and followed by a method that sets the value of the property. Inside the method, the value keyword is a read-only variable that contains the value being set.

Properties often get or set a backing field, or a private field that’s encapsulated by restricting access to it through a property.

An auto-implemented property—sometimes called an automatic property or auto-property—is a property that has a getter that returns the value of the backing field, and a setter that updates it.

Use the prop snippet in Visual Studio to create an auto-implemented property by typing “prop” followed by two tabs.

Use the private keyword to restrict access to a get or set accessor. A read-only property has a private set accessor.

When an object is created, the CLR first sets all of the fields that have values set in their declarations and then executes the constructor, before returning to the new statement that created the object.

Use a constructor with parameters to initialize properties. Specify arguments to pass to the constructor when you use the new keyword.

A parameter with the same name as a field masks that field. Use the this keyword to access the field.

If you don’t add a constructor to your class, the C# compiler automatically adds a parameterless constructor for you.

You can keep a class from being instantiated by other classes by adding a private constructor.

OBJECTCROSS SOLUTION



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


5. Encapsulation: How Objects Keep their Secrets
6. Inheritance: Your Object’s Family Tree
7. Interfaces, Casting, and “is”: Making Classes keep their Promises
12h 51m remaining
Chapter 6. Inheritance: Your Object’s Family Tree
A NOTE FOR EARLY RELEASE READERS
With Early Release ebooks, you get books in their earliest form—the authors’ raw and unedited content as they write—so you can take advantage of these technologies long before the official release of these titles.

This will be the 6th chapter of the final book. Please note that the GitHub repo will be made active later on.

If you have comments about how we might improve the content and/or examples in this book, or if you notice missing material within this chapter, please reach out to the editor at mcronin@oreilly.com.


Sometimes you DO want to be just like your parents.

Ever run across a class that almost does exactly what you want your class to do? Found yourself thinking that if you could just change a few things, that class would be perfect? With inheritance, you can extend an existing class so your new class gets all of its behavior—with the flexibility to make changes to that behavior so you can tailor it however you want. Inheritance is one of the most powerful concepts and techniques in the C# language: with it, you can avoid duplicate code, model the real world more closely, and end up with apps that are easier to maintain and less prone to bugs.

Calculate damage for MORE weapons
NOTE
 Do this!

The updated sword damage calculator was huge a hit on game night! Now Owen wants calculators for all of the weapons. Let’s start with the damage calculation for an arrow, which uses a 1d6 roll. Let’s create a new ArrowDamage class to calculate the arrow damage using the arrow formula in Owen’s game master notebook. 


Most of the code in ArrowDamage will be identical to the code in the SwordDamage class. Here’s what we need to do to get started building the new app.

 Create a new .NET Console App project. We want it to do both sword and arrow calculations, so add the SwordDamage class to the project. The constants aren’t used anywhere else in the app, so make them private.

 Create an ArrowDamage class that’s an exact copy of SwordDamage. Create a new class called ArrowDamage, then copy all of the code from SwordDamage and paste it into the new ArrowDamage class. Then change the constructor name to ArrowDamage so the program builds.


 Refactor the constants. The arrow damage formula has different values for the base and flame damage, so let’s rename the BASE_DAMAGE constant to BASE_MULTIPLIER and update the constant values. We think these constants make the code easier to read, so add a MAGIC_MULTIPLIER constant too:


 Modify the CalculateDamage method. Now all you need to do to make your new ArrowDamage class work is to update the CalculateDamage method so it does the correct calculation:


BRAIN POWER

There are many different ways to write code that does the same thing. Can you think of another way to write the code to calculate arrow damage?

Use a switch statement to match several candidates
Let’s update our console app to prompt the user whether to calculate damage from an arrow or a sword. We’ll ask for a key, and use the static Char.ToUpper method to convert it to uppercase:

Console.Write("\nS for sword, A for arrow, anything else to quit: ");
char weaponKey = Char.ToUpper(Console.ReadKey().KeyChar);
NOTE
The Char.ToUpper method converts ‘s’ and ‘a’ to ‘S’ and ‘A’

We could use if/else statements for this:

if (weaponKey == 'S') { /* calculate sword damage */ }
else if (weaponKey == 'A') { /* calculate arrow damage */ }
else return;
That’s how we’ve handled input so far. Comparing one variable against many different values is a really common pattern that you’ll see over and over again. It’s so common that C# has a special kind of statement designed specifically for this situation. A switch statement lets you compare one variable against many values in a way that’s compact and easy to read. Here’s a switch statement that does exactly the same thing as the if/else statements above:


EXERCISE

Update the top-level statements to use a switch statement to let the user choose the type of weapon. Start by copying the top-level statements from the exercise solution at the end of the last chapter.

Create an instance of ArrowDamage at the top of the method, just after you create the SwordDamage instance.

Modify the RollDice method to take an int parameter called numberOfRolls so you can call RollDice(3) to roll 3d6 (so it calls Random.Shared.Next(1, 7) three times and adds the results), or RollDice(1) to roll 1d6.

Add the two lines of code exactly like they appear above that write the sword or arrow prompt to the console, read the input using Console.ReadKey, use Char.ToUpper to convert the key to uppercase, and store it in weaponKey.

Add the switch statement. It will be exactly the same as the switch statement above, except you’ll replace each of the /* comments */ with code that calculates damage and writes a line of output to the console.

EXERCISE SOLUTION

We just gave you a totally new piece of C# syntax—the switch statement—and asked you to use it in a program. The C# team at Microsoft is constantly improving the language, and being able to incorporate new language elements into your code is a really valuable C# skill. This exercise is designed to help give you some practice with it.


One more thing...can we calculate damage for a dagger? and a mace? and a staff? and...
We’ve made two classes for sword and arrow damage. But what happens if there are three other weapons? Or four? Or 12? And what if you had to maintain that code and make more changes later? What if you had to make the same exact change to five or six closely related classes? What if you had to keep making changes? It’s inevitable that bugs would slip through—it’s way too easy to update five classes but forget to change the sixth.



You’re right! Having the same code repeated in different classes is inefficient and error-prone.

Lucky for us, C# gives us a better way to build classes that are related to each other and share behavior: inheritance.

When your classes use inheritance, you only need to write your code once
It’s no coincidence that your SwordDamage and ArrowDamage classes have a lot of the same code. When you write C# programs, you often create classes that represent things in the real world, and those things are usually related to each other. Your classes have similar code because the things they represent in the real world—two similar calculations from the same role-playing game—have similar behaviors.


When you have two classes that are specific cases of something more general, you can set them up to inherit from the same class. When you do that, each of them is a subclass of the same base class.


Build up your class model by starting general and getting more specific
When you build a set of classes that represent things (especially things in the real world), you’re building a class model. Real-world things are often in a hierarchy that goes from more general to more specific, and your programs have their own class hierarchy that does the same thing. In your class model, classes further down in the hierarchy inherit from those above them.


How would you design a zoo simulator?
Lions and tigers and bears...oh my! Also, hippos, wolves, and the occasional dog. Your job is to design an app that simulates a zoo. (Don’t get too excited—we’re not going to actually build the code, just design the classes to represent the animals. We bet you’re already thinking about how you’d do this in Unity!)

We’ve been given a list of some of the animals that will be in the program, but not all of them. We know that each animal will be represented by an object, and that the objects will move around in the simulator, doing whatever it is that each particular animal is programmed to do.

More importantly, we want the program to be easy for other programmers to maintain, which means they’ll need to be able to add their own classes later on if they want to add new animals to the simulator.

The terms parent, superclass, and base class are often used interchangeably. Also, the terms extend and inherit from mean the same thing. The terms child and subclass are also synonymous, but subclass can also be used as a verb.

NOTE
Some people use the term “base class” to specifically mean the class at the top of the inheritance tree...but not the VERY top, because every class inherits from Object or a subclass of Object.

Let’s start by building a class model for the animals we know about.

So what’s the first step? Well, before we can talk about specific animals, we need to figure out the general things they have in common—the abstract characteristics that all animals have. Then we can build those characteristics into a base class that all animal classes can inherit from.

 Look for things the animals have in common.

Take a look at these six animals. What do a lion, a hippo, a tiger, a bobcat, a wolf, and a dog have in common? How are they related? You’ll need to figure out their relationships so you can come up with a class model that includes all of them.


 Build a base class to give the animals everything they have in common.

The fields, properties, and methods in the base class will give all of the animals that inherit from it a common state and behavior. They’re all animals, so it makes sense to call the base class Animal.

You already know that we should avoid duplicate code: it’s hard to maintain, and always leads to headaches down the road. So let’s choose fields and methods for an Animal base class that you only have to write once, and each of the animal subclasses can inherit them. Let’s start with the public properties:

 Picture: a path to an image file.

 Food: the type of food this animal eats. Right now, there can be only two values: meat and grass.

 Hunger: an int representing the hunger level of the animal. It changes depending on when (and how much) the animal eats.

 Boundaries: a reference to a class that stores the height, width, and location of the pen that the animal will roam around in.

 Location: the X and Y coordinates where the animal is standing.

In addition, the Animal class has four methods the animals can inherit:

 MakeNoise: a method to let the animal make a sound.

 Eat: behavior for when the animal encounters its preferred food.

 Sleep: a method to make the animal lie down and take a nap.

 Roam: a method to make animals wander around their pens.


Different animals have different behaviors
Lions roar, dogs bark, and as far as we know hippos don’t make any sound at all. All of the classes that inherit from Animal will have a MakeNoise method, but each of those methods will work a different way and will have different code. When a subclass changes the behavior of one of the methods that it inherited, we say that it overrides the method.

 Figure out what each animal does that the Animal class does differently—or not at all.

NOTE
Just because a property or a method is in the Animal base class, that doesn’t mean every subclass has to use it the same way...or at all!

Every animal needs to eat, but a dog might take small bites of meat while a hippo eats huge mouthfuls of grass. What would the code for that behavior look like? Both the dog and the hippo would override the Eat method. The hippo’s method would have it consume, say, 20 pounds of hay each time it was called. The dog’s Eat method, on the other hand, would reduce the zoo’s food supply by one 12-ounce can of dog food.

NOTE
So when you’ve got a subclass that inherits from a base class, it must inherit all of the base class’s behaviors... but you can modify them in the subclass so they’re not performed exactly the same way. That’s what overriding is all about.



BRAIN POWER

We already know that some animals will override the MakeNoise and Eat methods. Which animals will override Sleep or Roam? Will any of them?

 Look for classes that have a lot in common.

Don’t dogs and wolves seem pretty similar? They’re both canines, and it’s a good bet that if you look at their behavior they have a lot in common. They probably eat the same food and sleep the same way. What about bobcats, tigers, and lions? It turns out all three of them move around their habitats in exactly the same way. It’s a good bet that you’ll be able to have a general Feline class that lives between Animal and those three feline classes that can help prevent duplicate code between them.


 Finish your class hierarchy.

Now that you know how you’ll organize the animals, you can add the Feline and Canine classes.

When you create your classes so that there’s a base class at the top with subclasses below it, and those subclasses have their own subclasses that inherit from them, what you’ve built is called a class hierarchy. This is about more than just avoiding duplicate code, although that is certainly a great benefit of a sensible hierarchy. One benefit of this is code that’s a lot easier to understand and maintain. When you’re looking at the zoo simulator code and you see a method or property defined in the Feline class, then you immediately know that you’re looking at something that all of the cats share. Your hierarchy becomes a map that helps you find your way through your program.


Every subclass extends its base class
You’re not limited to the methods that a subclass inherits from its base class...but you already know that! After all, you’ve been building your own classes all along. When you modify a class to make it inherit members—and we’ll see that in C# code soon!—what you’re doing is taking the class you’ve already built and extending it by adding all of the fields, properties, and methods in the base class. So if you want to add a Fetch method to Dog, that’s perfectly normal. It won’t inherit or override anything—only the Dog class will have that method, and it won’t end up in Wolf, Canine, Animal, Hippo, or any other class.


C# always calls the most specific method
If you tell your Dog object to roam, there’s only one method that can be called—the one in the Animal class. What about telling your Dog to make noise? Which MakeNoise is called?

Well, it’s not too hard to figure it out. A method in the Dog class tells you how dogs make noise. If it’s in the Canine class, it’s telling you how all canines do it. If it’s in Animal, then it’s a description of that behavior that’s so general that it applies to every single animal. So if you ask your Dog to make a noise, first C# will look inside the Dog class to find the behavior that applies specifically to dogs. If Dog didn’t have a MakeNoise method it’d check Canine, and after that it’d check Animal.

Any place where you can use a base class, you can use one of its subclasses instead
One of the most useful things you can do with inheritance is to extend a class. So if your method takes a Bird object, then you can pass an instance of Woodpecker. All that method knows is that it has a bird. It doesn’t know what kind of bird it has, so it can only ask it to do things that all birds do: it can ask the bird to Walk and LayEggs, but it can’t ask it to HitWoodWithBeak, because only Woodpeckers have that behavior—and the method doesn’t know that it’s specifically a Woodpecker, just that it’s a more general Bird. It only has access to the fields, properties, and other methods that are part of the class it knows about.


Let’s see how this works in code. Here’s a method that takes a Bird reference:


If you want to incubate some Woodpecker eggs, you can pass a Woodpecker reference to the IncubateEggs method, because a Woodpecker is a kind of Bird—which is why it inherits from the Bird class:

public void GetWoodpeckerEggs()
{
    Woodpecker woody = new Woodpecker();
    IncubateEggs(woody);
    woody.HitWoodWithBeak();
}
You can replace a superclass with a subclass, but you can’t replace a subclass with its superclass. You can pass a Woodpecker to method that takes a Bird reference, but not vice versa:

NOTE
This should make intuitive sense. If someone asks you for a bird and you hand them a woodpecker, they’ll be happy. But if they ask you for a woodpecker and you hand them a pigeon, they’ll be confused.


SHARPEN YOUR PENCIL

The code below is from a program that uses the class model that includes Animal, Hippo, Canine, Wolf, and Dog. Draw a line through each statement that won’t compile, and write an explanation for the problem next to it.


SHARPEN YOUR PENCIL SOLUTION

The code below is from a program that uses the class model that includes Animal, Hippo, Canine, Wolf, and Dog. Draw a line through each statement that won’t compile, and write an explanation for the problem next to it.



BRAIN POWER

Owen asked a really good question. Go back to the app you built for Owen that calculates sword and arrow damage. How would you use inheritance and subclasses to improve the code? (Spoiler alert: you’ll be doing that later in the chapter!)

BULLET POINTS
A switch statement lets you compare one variable against many values. Each case executes code if its value matches. The default block runs if no cases match.

Inheritance lets you build classes that are related to each other and share behavior. Use arrows to show inheritance in a class diagram.

When you have two classes that are specific cases of something more general, you can set them up to inherit from the same general class. When you do that, each of them is a subclass of the same general base class.

When you build a set of classes that represent things, it’s called a class model. It can include classes that form a hierarchy of subclasses and base class.

The terms parent, superclass, and base class are often used interchangeably. Also, the terms extend and inherit from mean the same thing.

The terms child and subclass mean the same thing. We say that a subclass extends its base class. (The word subclass can also be used as a verb.)

When a subclass changes the behavior of one of the methods that it inherited, we say that it overrides the method.

C# always calls the most specific method. If a method in the base class uses a method or property that the subclass overrides, it will call the overridden version in the subclass.

You can use a subclass reference in place of a base class. If a method takes an Animal parameter and Dog extends Animal, you can pass it a Dog argument.

You can always use a subclass in place of the base class it inherits from, but you can’t always use a base class in place of a subclass that extends it.

Use a colon to extend a base class
When you’re writing a class, you use a colon (:) to have it inherit from a base class. That makes it a subclass, and gives it all of the fields, properties, and methods of the class it inherits from. This Bird class is a subclass of Vertebrate:

When a subclass extends a base class, it inherits its members: all of the fields, properties, and methods in the base class. They’re automatically added to the subclass.


We know that inheritance adds the base class fields, properties, and methods to the subclass...
We’ve seen inheritance when a subclass needs to inherit all of the base class’s methods, properties, and fields.


...but some birds don’t fly!
What do you do if your base class has a method that your subclass needs to modify?


Oops—we’ve got a problem. Penguins are birds, and the Bird class has a Fly method, but we don’t want our penguins to fly. It would be great if we could display a warning if a penguin tries to fly.

class Bird {
   public void Fly() {
       /* code to make birds fly */
   }
   public void LayEggs() { ... };
   public void PreenFeathers() { ... };
}

class Pigeon : Bird {
   public void Coo() { ... }
}

public void SimulatePigeon() {
   Pigeon Harriet = new Pigeon();

   // Since Pigeon is a subclass of Bird,
   // we can call methods from either class.
   Harriet.Walk();
   Harriet.LayEggs();
   Harriet.Coo();
   Harriet.Fly();
}

class Penguin : Bird {
   public void Swim() { ... }
}

public void SimulatePenguin() {
    Penguin Izzy = new Penguin();
    Izzy.Walk();
    Izzy.LayEggs();
    Izzy.Swim();
    Izzy.Fly();
}
NOTE
This code will compile because Penguin extends Bird. Is there a way to change the Penguin class so it displays a warning if a penguin tries to fly?

BRAIN POWER

If these classes were in your zoo simulator, what would you do about flying penguins?

A subclass can override methods to change or replace members it inherited
Sometimes you’ve got a subclass that you’d like to inherit most of the behaviors from the base class, but not all of them. When you want to change the behaviors that a class has inherited, you can override methods or properties, replacing them with new members with the same name.

NOTE
o-ver-ride, verb.

to use authority to replace, reject, or cancel. Once she became president of Dynamco, she could override poor management decisions.

When you override a method, your new method needs to have exactly the same signature as the method in the base class it’s overriding. In the case of the penguin, that means it needs to be called Fly, return void, and have no parameters.

 Add the virtual keyword to the method in the base class.

A subclass can only override a method if it’s marked with the virtual keyword. Adding virtual to the Fly method declaration tells C# that a subclass of the Bird class is allowed to override the Fly method.


 Add the override keyword to a method with the same name in the subclass.

The subclass’s method will need to have exactly the same signature—the same return type and parameters—and you’ll need to use the override keyword in the declaration. Now a Penguin object prints a warning when its Fly method is called.


EXERCISE

A short C# program is listed below. One block of the program is missing! Your challenge is to match the candidate block of code (on the left) with the output—what’s in the message box that the program pops up—that you’d see if the block were inserted. Not all the lines of output will be used, and some of the lines of output might be used more than once. Draw lines connecting the candidate blocks of code with their matching output.


EXERCISE SOLUTION

You can always substitute a reference to a subclass in place of a base class because you’re using something more specific in place of something more general. So this line:

A a2 = new C();
means that you’re instantiating a new C object, and then creating an A reference called a2 and pointing it at that object. Names like these make for a good puzzle, but they’re pretty hard to understand. Here are a few lines that follow the same pattern, but have names that are more obvious:

Canine fido = new Dog();
Bird pidge = new Pigen();
Feline rex = new Lion();

THERE ARE NO DUMB QUESTIONS
Q: A switch statement does exactly the same thing as a series of if/else statements, right? Isn’t that redundant?

A: Not at all. There are many situations where switch statements are much more readable than if/else statements. For example, let’s say you’re displaying a menu in a console app, and the user can press a key to choose one of 10 different options. What would 10 if/else if statements in a row look like? We think a switch statement would be cleaner and easier to read. You could see at a glance exactly what’s being compared, where each option is handled, and what happens in the default case if the user chooses an unsupported option. Also, it’s surprisingly easy to accidentally leave off an else. If you miss an else in the middle of a long string of if/else statements, you end up with a really annoying bug that’s surprisingly difficult to track down. There are some times when a switch statement is easier to read, and other times when if/else statements are easier. It’s up to you to write code in the way that you think is easiest to understand.

Q: Why does the arrow point up, from the subclass to the base class? Wouldn’t the diagram look better with the arrow pointing down instead?

A: It might seem more intuitive, but it wouldn’t be as accurate. When you set up a class to inherit from another one, you build that relationship into the subclass—the base class remains the same. Its behavior is completely unchanged when you add a class that inherits from it. The base class isn’t even aware of this new class. Its methods, fields, and properties remain entirely intact—but the subclass definitely changes its behavior. Every instance of the subclass automatically gets all of the properties, fields, and methods from the base class, and it all happens just by adding a colon. That’s why you draw the arrow on your diagram so that it points from the subclass to the base class that it inherits from.

EXERCISE

Let’s get some practice extending a base class. We’ll give you the top-level statements for a program that tracks birds laying eggs. Your job is to implement two subclasses of the Bird class.

Here are the top-level statements. The app prompts the user for the type of bird and number of eggs to lay:

while (true)
{
    Bird bird;
    Console.Write("\nPress P for pigeon, O for ostrich: ");
    char key = Char.ToUpper(Console.ReadKey().KeyChar);
    if (key == 'P') bird = new Pigeon();
    else if (key == 'O') bird = new Ostrich();
    else return;
    Console.Write("\nHow many eggs should it lay? ");
    if (!int.TryParse(Console.ReadLine(), out int numberOfEggs)) return;
    Egg[] eggs = bird.LayEggs(numberOfEggs);
    foreach (Egg egg in eggs)
    {
        Console.WriteLine(egg.Description);
    }
}
NOTE
Here’s what the program output looks like:

Press P for pigeon, O for ostrich: P
How many eggs should it lay? 4
A 2.40cm white egg
A 1.82cm white egg
A 2.88cm white egg
A 2.28cm white egg

Press P for pigeon, O for ostrich: O
How many eggs should it lay? 3
A 12.48cm speckled egg
A 12.12cm speckled egg
A 12.13cm speckled egg
Add this Egg class—the constructor sets the size and color:

class Egg
{
    public double Size { get; private set; }
    public string Color { get; private set; }
    public Egg(double size, string color)
    {
        Size = size;
        Color = color;
    }
    public string Description {
        get { return $"A {Size:0.00}cm {Color} egg"; }
    }
}
NOTE
Rounding in interpolation

You can round a number to a number of decimal places in string interpolation. We included {Size:0.00} to tell it to round the Size value to 2 decimal places.

This is the Bird class that you’ll extend:

class Bird
{
    public virtual Egg[] LayEggs(int numberOfEggs)
    {
        Console.Error.WriteLine("Bird.LayEggs should never get called");
        return new Egg[0];
    }
}
Create the Pigeon class that extends Bird. Override the LayEggs method and have it lay eggs with the color “white” and a size between 1 and 3 centimeters.

Create the Ostrich class that also extends Bird. Override the LayEggs method and have it lay eggs with the color “speckled” and a size between 12 and 13 centimeters.

EXERCISE SOLUTION

Here are the Pigeon and Ostrich classes. They each have their own version of the LayEggs method that uses the override keyword in the method declaration. The override keyword causes the method in the subclass to replace the one that it inherited.

Pigeon is a subclass of Bird, so if you override the LayEggs method, when you create a new Pigeon object and assign it to a Bird variable called bird, calling bird.LayEggs will call the LayEggs method you defined in Pigeon.

class Pigeon : Bird
{
    public override Egg[] LayEggs(int numberOfEggs)
    {
        Egg[] eggs = new Egg[numberOfEggs];
        for (int i = 0; i < numberOfEggs; i++)
        {
            eggs[i] = new Egg(Random.Shared.NextDouble() * 2 + 1, "white");
        }
        return eggs;
    }
}
The Ostrich subclass works the same way as Pigeon. In both classes, the override keyword in the LayEggs method declaration means that this new method will replace the LayEggs that it inherited from Bird. So all we need to do is have it create a set of eggs that are the right size and color.

class Ostrich : Bird
{
    public override Egg[] LayEggs(int numberOfEggs)
    {
        Egg[] eggs = new Egg[numberOfEggs];
        for (int i = 0; i < numberOfEggs; i++)
        {
            eggs[i] = new Egg(Random.Shared.NextDouble() + 12, "speckled");
        }
        return eggs;
    }
}

Some members are only implemented in a subclass
All the code we’ve seen so far that works with subclasses has accessed the members from outside the object—like how the top-level statements in the last exercise call LayEggs. Inheritance really shines when the base class uses a method or property that’s implemented in the subclass. Here’s an example. Our zoo simulator has vending machines that let patrons buy soda, candy, and feed to give to the animals in the petting zoo area.


VendingMachine is the base class for all vending machines. It has code to dispense items, but those items aren’t defined. The method to check if the patron put in the right amount always returns false. Why? Because they will be implemented in the subclass. Here’s a subclass for dispensing animal feed in the petting zoo:


Use the debugger to understand how overriding works
Let’s use the debugger to see exactly what happens when we create an instance of AnimalFeedVendingMachine and ask it to dispense some feed. Create a new Console App project, then do this.

 Add the top-level statements. Here’s the code:

VendingMachine vendingMachine = new AnimalFeedVendingMachine();
Console.WriteLine(vendingMachine.Dispense(2.00M));
NOTE
 Debug this!

 Add the VendingMachine and AnimalFeedVendingMachine classes. Once they’re added, try adding this line of code to the top-level statements:

vendingMachine.CheckAmount(1F);
You’ll get a compiler error because of the protected keyword, because only the VendingMachine class or subclasses of it can access its protected methods.


Delete the line so your code builds.

 Put a breakpoint on the first line of the top-level statements. Run your program. When it hits the breakpoint, use Step Into (F10 / I) to execute every line of code one at a time. Here’s what happens:

 It creates an instance of AnimalFeedVendingMachine and calls its Dispense method.

 That method is only defined in the base class, so it calls VendingMachine.Dispense.

 The first line of VendingMachine.Dispense calls the protected CheckAmount method.

 CheckAmount is overridden in the AnimalFeedVendingMachine subclass, which causes VendingMachine.Dispense to call the CheckAmount method defined in AnimalFeedVendingMachine.

 This version of CheckAmount returns true, so Dispense returns the Item property. AnimalFeedVendingMachine also overrides this property, it returns “a handful of animal feed.”

NOTE
You’ve been using the debugger to sleuth out bugs in your code. It’s also a great tool for learning and exploring C#, like in this “Debug this!” where you can explore how overriding works. Can you think of more ways to experiment with overriding subclasses?


There’s an important reason for virtual and override!

The virtual and override keywords aren’t just for decoration. They make a real difference in how your program works. The virtual keyword tells C# that a member (like a method, property, or field) can be extended—without it, you can’t override it at all. The override keyword tells C# that you’re extending the member. If you leave out the override keyword in a subclass, you’re creating a completely unrelated method that just happens to have the same name.

That sounds a little weird, right? But it actually makes sense—and the best way to really understand how virtual and override work is by writing code. So let’s build a real example to experiment with them.

When a subclass overrides a method in its base class, the more specific version defined in the subclass is always called—even when it’s being called by a method in the base class.

Build an app to explore virtual and override
A really important part of inheritance in C# is extending class members. That’s how a subclass can inherit some of its behavior from its base class, but override certain members where it needs to—and that’s where the virtual and override keywords come in. The virtual keyword determines which class members can be extended. When you want to extend a member, you must use the override keyword. Let’s create some classes to experiment with virtual and override. You’re going to create a class that represents a safe containing valuable jewels—you’ll build a class for some sneaky thieves to steal the jewels.


 Create a new console app and add the Safe class.

Here’s the code for the Safe class:

NOTE
 Do this!


Add a class for the person who owns the safe.

The safe owner is forgetful and occasionally forgets their extremely secure safe password. Add a SafeOwner class to represent them:

class SafeOwner
{
    private string valuables = "";
    public void ReceiveContents(string safeContents)
    {
        valuables = safeContents;
        Console.WriteLine($"Thank you for returning my {valuables}!");
    }
}
 Add Locksmith class that can pick the lock.

If a safe owner hires a professional locksmith to open their safe, they expect that locksmith to return the contents safe and sound. That’s exactly what the Locksmith.OpenSafe method does:


 Add a JewelThief class that wants to steal the valuables.

Uh-oh. Looks like there’s a burglar—and the worst kind, one who’s also a highly skilled locksmith able to open safes. Add this JewelThief class that extends Locksmith:


 Add top-level statements that make the JewelThief steal the jewels.

It’s time for the big heist! In this code, the JewelThief sneaks into the house and uses its inherited Locksmith. OpenSafe method to get the safe combination. What do you think will happen when it runs?


A subclass can hide methods in the base class

Go ahead and run the JewelThief program. Here’s what you should see:

Thank you for returning my precious jewels!
Did you expect the program’s output to be different? Maybe something like this:

I'm stealing the jewels! I stole: precious jewels
NOTE
C# is supposed to call the most specific method, right? Then why didn’t it call JewelThief.ReturnContents?

It looks like the JewelThief object acted just like a Locksmith object! So what happened?

Hiding methods versus overriding methods
The reason the JewelThief object acted like a Locksmith object when its ReturnContents method was called was because of the way the JewelThief class declared its ReturnContents method. There’s a big hint in that warning message you got when you compiled your program:


Since the JewelThief class inherits from Locksmith and replaces the ReturnContents method with its own method, it looks like JewelThief is overriding Locksmith’s ReturnContents method—but that’s not actually what’s happening. You probably expected JewelThief to override the method (which we’ll talk about in a minute), but instead JewelThief is hiding it.


There’s a big difference. When a subclass hides a method, it replaces (technically, it redeclares) a method in its base class that has the same name. So now our subclass really has two different methods that share a name: one that it inherits from its base class, and another brand-new one that’s defined in that class.

Use the new keyword when you’re hiding methods
Take a close look at that warning message. Sure, we know we should read our warnings, but sometimes we don’t...right? This time, actually read what it says: Use the new keyword if hiding was intended.

So go back to your program and add the new keyword:

new public void ReturnContents(Jewels safeContents, Owner owner)
As soon as you add new to your JewelThief class’s ReturnContents method declaration, that warning message will go away—but your code still won’t act the way you expect it to!

It still calls the ReturnContents method defined in the Locksmith class. Why? Because the ReturnContents method is being called from a method defined by the Locksmith class—specifically, from inside Locksmith.OpenSafe—even though it’s being initiated by a JewelThief object. If JewelThief only hides Locksmith’s ReturnContents method, its own ReturnContents method will never be called.

If a subclass just adds a method with the same name as a method in its base class, it only hides the base class method instead of overriding it.

Use different references to call hidden methods
Now we know that JewelThief only hides the ReturnContents method (as opposed to overriding it). That causes it to act like a Locksmith object whenever it’s called like a Locksmith object. JewelThief inherits one version of ReturnContents from Locksmith, and it defines a second version of it, which means that there are two different methods with the same name. That means your class needs two different ways to call it.

There are two different ways to call the ReturnContents method. If you’ve got an instance of JewelThief, you can use a JewelThief reference variable to call the new ReturnContents method. If you use a Locksmith reference variable to call it, it will call the hidden Locksmith ReturnContents method.

Here’s how that works:


Can you figure out how to get JewelThief to override the ReturnContents method instead of just hiding it? See if you can do it before reading the next section!

THERE ARE NO DUMB QUESTIONS
Q: I still don’t get why they’re called “virtual” methods—they seem real to me. What’s virtual about them?

A: The name “virtual” has to do with how .NET handles the virtual methods behind the scenes. It uses something called a virtual method table (or vtable). That’s a table that .NET uses to keep track of which methods are inherited and which ones have been overridden. Don’t worry—you don’t need to know how it works to use virtual methods.

Q: You talked about replacing a superclass with a reference to a subclass. Can you go over that one more time?

A: When you’ve got a diagram with one class that’s above another one, the class that’s higher up is more abstract than the one that’s lower down. More specific or concrete classes (like Shirt or Car) inherit from more abstract ones (like Clothing or Vehicle). If all you need is a vehicle, a car or van or motorcycle will do. If you need a car, a motorcycle won’t be useful to you.

Inheritance works exactly the same way. If you have a method with Vehicle as a parameter, and if the Motorcycle class inherits from the Vehicle class, then you can pass an instance of Motorcycle to the method. If the method takes Motorcycle as a parameter, you can’t pass any Vehicle object, because it may be a Van instance. Then C# won’t know what to do when the method tries to access the Handlebars property.

Use the override and virtual keywords to inherit behavior
We really want our JewelThief class to always use its own ReturnContents method, no matter how it’s called. This is the way we expect inheritance to work most of the time: a subclass can override a method in the base class so the method in the subclass is called instead. Start by using the override keyword when you declare the ReturnContents method:

class JewelThief {
    protected override void ReturnContents
          (string safeContents, SafeOwner owner)
But that’s not everything you need to do. If you just add the override keyword to the class declaration, you’ll get a compiler error:


Again, take a really close look and read what the error says. JewelThief can’t override the inherited member ReturnContents because it’s not marked virtual, abstract, or override in Locksmith. Well, that’s an error we can fix with a quick change. Mark Locksmith’s ReturnContents with the virtual keyword:

class Locksmith {
    protected virtual void ReturnContents
          (string safeContents, SafeOwner owner)
Now run your program again. Here’s the output we’ve been looking for:

I'm stealing the jewels! I stole: precious jewels
SHARPEN YOUR PENCIL

Draw a line from each of the following descriptions to the keyword it describes.

A method that can only be accessed by an instance of the same class

A method that a subclass can replace with a method of the same name

A method that can be accessed by an instance of any other class

A method that hides another method in the superclass with the same name

A method that replaces a method in the superclass

A method that can only be accessed by a member of the class or its subclass

virtual
new
override
protected
private
public
1. private 2. virtual 3. public 4. new 5. override 6. protected


Exactly. Most of the time you want to override methods, but hiding them is an option.

When you’re working with a subclass that extends a base class, you’re much more likely to use overriding than you are to use hiding. So when you see that compiler warning about hiding a method, pay attention to it! Make sure you really want to hide the method, and didn’t just forget to use the virtual and override keywords. If you always use the virtual, override, and new keywords correctly, you’ll never run into a problem like this again!

If you want to override a method in a base class, always mark it with the virtual keyword, and always use the override keyword any time you want to override the method in a subclass. If you don’t, you’ll end up accidentally hiding methods instead.

A subclass can access its base class using the base keyword
Even when you override a method or property in your base class, sometimes you’ll still want to access it. Luckily, we can use base, which lets us access any member of the base class.


 All animals eat, so the Vertebrate class has an Eat method that takes a Food object as its parameter.

class Vertebrate {
   public virtual void Eat(Food morsel) {
      Swallow(morsel);
      Digest();
   }
}

 Chameleons eat by catching food with their tongues. So the Chameleon class inherits from Vertebrate but overrides Eat.


 Instead of duplicating the code, we can use the base keyword to call the method that was overridden. Now we have access to both the old and the new version of Eat.


When a base class has a constructor, your subclass needs to call it
Let’s go back to the code you wrote with the Bird, Pigeon, Ostrich, and Egg classes. We want to add a BrokenEgg class that extends Egg, and make 25% of the eggs that the Pigeon lays broken. Replace the new statement in Pigeon.LayEgg with this if/else that creates a new instance of either Egg or BrokenEgg:

if (Random.Shared.Next(4) == 0)
    eggs[i] = new BrokenEgg(Random.Shared.NextDouble() * 2 + 1, "white");
else
    eggs[i] = new Egg(Random.Shared.NextDouble() * 2 + 1, "white");
NOTE
 Add this!

Now we just need a BrokenEgg class that extends Egg. Let’s make it identical to the Egg class, except that it has a constructor that writes a message to the console letting us know that an egg is broken:

class BrokenEgg : Egg
{
    public BrokenEgg()
    {
        Console.WriteLine("A bird laid a broken egg");
    }
}
Go ahead and make those two changes to your Egg program.

Uh-oh—looks like those new lines of code caused compiler errors:

 The first error is on the line where you create a new BrokenEgg: CS1729 – ’BrokenEgg’ does not contain a constructor that takes 2 arguments

 The second error is in the BrokenEgg constructor: CS7036 – There is no argument given that corresponds to the required formal parameter ’size’ of ’Egg.Egg(double, string)’

This is another great opportunity to read those errors and figure out what went wrong. The first error is pretty clear: the statement that creates a BrokenEgg instance is trying to pass two arguments to the constructor, but the BrokenEgg class has a parameterless constructor. So go ahead and add parameters to the constructor:

public BrokenEgg(double size, string color)
That takes care of the first error. What about the other error?

Let’s break down what that error says:

 It’s complaining about Egg.Egg(double, string)—this refers to the Egg class constructor.

 It says something about parameter ’size’, which the Egg class needs in order to set its Size property.

 But there is no argument given, because it’s not enough to just modify the BrokenEgg constructor to take arguments that match the parameter. It also needs to call that base class constructor.

Modify the BrokenEgg class to use the base keyword to call the base class constructor:

public BrokenEgg(double size, string color) : base(size, color)
Now your code compiles. Try running it—now when a Pigeon lays an egg, about a quarter of them will print a message about being broken when they’re instantiated (but after that, the rest of the output is the same as before).

A subclass and base class can have different constructors
When we modified BrokenEgg to call the base class constructor, we made its constructor match the one in the Egg base class. What if we want all broken eggs to have a size of zero and a color that starts with the word “broken”? Modify the statement that instantiates BrokenEgg so it only takes the color argument:

if (Random.Shared.Next(4) == 0)
     eggs[i] = new BrokenEgg("white");
else
     eggs[i] = new Egg(Random.Shared.NextDouble() * 2 + 1, "white");
NOTE
 Modify this!

When you make that change you’ll get the “required formal parameter” compiler error again—which makes sense because the BrokenEgg constructor has two parameters, but you’re only passing it one argument.

Fix your code by modifying the BrokenEgg constructor to take one parameter:


Now run your program again. The BrokenEgg constructor will still write its message to the console during the for loop in the Pigeon constructor, but now it will also cause the Egg to initialize its Size and Color fields. When the foreach loop in the top-level statements writes egg.Description to the console, it writes this message for each broken egg:


It’s time to finish the job for Owen
The first thing you did in this chapter was modify the damage calculator you built for Owen to roll for damage for either a sword or an arrow. It worked, and your SwordDamage and ArrowDamage classes were well-encapsulated. But aside from a few lines of code, those two classes were identical. You’ve learned that having code repeated in different classes is inefficient and error-prone, especially if you want to keep extending the program to add more classes for different kinds of weapons. Now you have a new tool to solve this problem: inheritance. So it’s time for you to finish the damage calculator app. You’ll do it in two steps: first you’ll design the new class model on paper, and then you’ll implement it in code.

Building your class model on paper before you write code helps you understand your problem better so you can solve it more effectively.


SHARPEN YOUR PENCIL

Great code starts in your head, not an IDE. So let’s design the class model on paper before we start writing code.

We’ve started you out by filling in the class names. Your job is to add the members to all three classes, and draw the arrows between the boxes.

For reference, we included diagrams for the SwordDamage and ArrowDamage classes that you built earlier. We included the private CalculateDamage method for each class. Make sure to include all public, private, and protected class members when you fill in the class diagram. Write the access modifier (public, private, or protected) next to each class member.



When your classes are well-encapsulated, it makes your code much easier to modify.

If you know a professional developer, ask them the most annoying thing they’ve had to do at work in the last year. There’s a pretty good chance that they’ll talk about having to make a change to a class, but to do that they had to change these two other classes, which required three other changes, and it was hard just to keep track of all the changes in their brains. Designing your classes with encapsulation in mind is a great way to avoid ending up in that situation.

SHARPEN YOUR PENCIL SOLUTION


EXERCISE

Now that you’ve designed the class model, you’re ready to write the code to implement it. That’s a great habit to get into—design your classes first, then turn them into code.

Here’s what you’ll do to finish the job for Owen. You can reopen the project that you created at the beginning of the chapter, or you can create an entirely new one and copy the relevant parts into it. If your code is very different from the exercise solution earlier in the chapter, you might want to start with the solution code. You can download the code from https://github.com/head-first-csharp/fifth-edition if you don’t want to type it in.

Don’t make any changes to the top-level statements. It will use the new SwordDamage and ArrowDamage classes exactly like it did at the beginning of the chapter.

Implement the WeaponDamage class. Add a new WeaponDamage class and make it match the class diagram in the “Sharpen your pencil” solution. Here are a few things to consider:

 The properties in WeaponDamage are almost identical to the properties in the SwordDamage and ArrowDamage classes at the beginning of the chapter. There’s just a single keyword that’s different.

 Don’t put any code in the CalculateDamage class (you can include a comment: /* the subclass overrides this */ ). It needs to be virtual, it can’t be private—otherwise you’ll get a compiler error:


 Add a constructor that sets the starting roll.

Implement the SwordDamage class. Here are a few things you need to think about:

 The constructor has a single parameter, which it passes to the base class constructor.

 C# always calls the most specific method. That means you’ll need to override CalculateDamage and make it do the sword damage calculation.

 It’s worth taking a minute to think about how CalculateDamage works. The Roll, Magic, or Flaming setters call CalculateDamage to make sure the Damage field is updated automatically. Since C# always calls the most specific method, they’ll call SwordDamage.CalculateDamage even though they’re part of the WeaponDamage superclass.

Implement the ArrowDamage class. It works exactly like SwordDamage, except that its CalculateDamage method does the arrow calculation and not the sword calculation.


EXERCISE SOLUTION

Here’s the code for the WeaponDamage class. The properties are almost identical to the properties in the old sword and arrow classes. It also has a constructor to set the starting roll, and a CalculateDamage method for the subclasses to override.



EXERCISE SOLUTION

The SwordDamage class extends WeaponDamage and overrides its CalculateDamage method to implement the sword damage calculation. Here’s the code:


And here’s the code for the ArrowDamage class. It works just like the SwordDamage class, except it does the calculation for arrows instead:

class ArrowDamage : WeaponDamage
{
    private const decimal BASE_MULTIPLIER = 0.35M;
    private const decimal MAGIC_MULTIPLIER = 2.5M;
    private const decimal FLAME_DAMAGE = 1.25M;

    public ArrowDamage(int startingRoll) : base(startingRoll) { }

    protected override void CalculateDamage()
    {
        decimal baseDamage = Roll * BASE_MULTIPLIER;
        if (Magic) baseDamage *= MAGIC_MULTIPLIER;
        if (Flaming) Damage = (int)Math.Ceiling(baseDamage + FLAME_DAMAGE);
        else Damage = (int)Math.Ceiling(baseDamage);
    }
}
Use the debugger to really understand how these classes work
NOTE
 Do this!

One of the most important ideas in this chapter is that when you extend a class, you can override its methods to make pretty significant changes to the way it behaves. Use the debugger to really understand how that works:

 Set breakpoints on the lines in the Roll, Magic, and Flaming setters that call CalculateDamage.

 Add a Console.WriteLine statement to WeaponDamage.CalculateDamage. This statement will never get called.

 Run your program. When it hits any of the breakpoints, use Step Into to enter the CalculateDamage method. It will step into the subclass—the WeaponDamage.CalculateDamage method is never called.

A class do should just one thing
When your classes overlap as little as possible, it’s called separation of concerns. That’s an important design principle—it means that each part of your code should focus on doing just one thing.

When you’re designing classes, separation of concerns is one of the first things you should think about. If one class seems to be doing two different things, try to figure out if you can split it into two classes (or more!).

Imagine if you had a dozen different classes to calculate damage for different weapons. What if you wanted to change Magic from a bool to an int, so you could have weapons with enchantment bonuses (like a +3 magic mace or +1 magic dagger)? With inheritance, you’d just have to change the Magic property in the superclass. Of course, you’d have to modify the CalculateDamage method for each class—but it would be a lot less work, and there’s no danger of accidentally forgetting to modify one of the classes. (That happens in professional software development all the time!)

This is an example of separation of concerns, because each class has only the code that concerns one specific part of the problem that your program solves. Code that only concerns swords goes into SwordDamage, code only for arrows goes into ArrowDamage, and code that’s shared between them goes into WeaponDamage.


Your code is easier to read when classes are small and do just one thing—and when that thing is in just one class.

If you design your classes well today, they’ll be easier to modify later. When you make classes small and simple, your code is easier to write, read, and change.

A lot of developers joke about how hard it is to look at code that you wrote six months ago, because almost every experienced developer has opened up old code and thought, “What was I thinking? How does this even work?”

Separation of concerns can help you avoid making code that’s hard to read and change, because we usually work on one class at a time, and it’s easier to understand a small class than a big one.

There’s another design principle that can help make your code easier to understand and change: don’t repeat yourself, or DRY, which means that any specific thing that your code does should only be in one place. For example, if you have two classes that do the same exact calculation, instead of pasting the same code in both of them, you can put that calculation in a single method and have them both extend the same base class, create an object that has that method, call a static method, or find another way to put it in just one place. That way, if you come back in a few months and need to find the code that does that calculation, you’ll know exactly where to find it.

SENS-AI
Use AI to help you research and explore separation of concerns and DRY

We just learned about two important design principles: separation of concerns and don’t repeat yourself (DRY). These are really valuable ideas that can help you become a better developer. Let’s use AI chatbots to explore them.

Do some research about separation of concerns and DRY

AI chatbots can be great research tools. Just don’t forget the lesson we learned back in Chapter 2: they aren’t perfect, and make mistakes—so when you’re using an AI as a learning and research tool, you really want to be careful to double-check all of the information that it gives you! Use clear, simple prompts, and ask follow-up questions. Some AI chatbots like Copilot also give you links with more information. Click on those links, too.

Try these prompts to start your research journey:

What is “separation of concerns” in programming?

What is “don’t repeat yourself” or “DRY” in programming?

Give me an example of “separation of concerns” and DRY in C#.

NOTE
Ask the AI who created DRY. These ideas were made by smart people—learn about the folks who came up with them.

Experiment with separation of concerns

In the last exercise, you created three classes: SwordDamage with the behavior that’s specific to the sword damage calculation, ArrowDamage with the behavior specific to arrow damage calculation, and WeaponDamage with the behavior that’s common to calculating damage for any weapon. What would it look like if you didn’t follow the principle of separation of concerns? Ask an AI to show you. Give an AI chatbot this prompt:

Combine the following three separate C# classes into a single class.

(paste the code for WeaponDamage class, SwordDamage class, and 
ArrowDamage class)
Examine the code closely. Do you think it works? Make assa copy of your damage calculator app. Delete the WeaponDamage, SwordDamage, and ArrowDamage classes and replace them with the code that the chatbot generated. Can you get your app to work with the AI’s code? Debug through it. Is it easier or harder to understand?

Experiment with separation of DRY

The classes from the last exercise are also a good example of the “don’t repeat yourself” principle—but just looking at the code, it’s not easy to see exactly why. An AI chatbot can help you with this, too. Give the AI this prompt:

Combine the following three separate C# classes into two classes that
include the code from the WeaponDamage class instead of extending it.

(paste the code for WeaponDamage class, SwordDamage class, and
ArrowDamage class)
Do the same thing you did with the previous code—copy the damage calculator app, delete the damage classes, and replace them with the code that the chatbot generated. Figure out how it works. Can you find the code that it duplicated? What would happen if you had to modify that code—would you remember to change it in both places?

NOTE
One of the AIs we tested the last prompt with didn’t do what we asked it to, and generated subclasses that still extended WeaponDamage. We gave it a follow-up prompt: “Rewrite that so SwordDamage and ArrowDamage do not extend WeaponDamage, but instead duplicate its code.”

GAME DESIGN... AND BEYOND

NOTE
We’re about to talk about an important element of game design: dynamics. It’s actually such an important concept that it goes beyond game design. In fact, you can find dynamics in almost any kind of app.

Dynamics

The dynamics of a game describe how the mechanics combine and cooperate to drive the gameplay. Any time you have game mechanics, they lead to dynamics. That’s not limited to video games—all games have mechanics, and dynamics arise out of those mechanics.

We’ve already seen a good example of mechanics: in Owen’s role-playing game, he uses formulas (the ones you built into your damage classes) to calculate damage for various weapons. That’s a good starting point to think about how a change in those mechanics would affect dynamics.

What happens if you change the mechanics of the arrow formula so that it multiplies the base damage by 10? That’s a small change in mechanics, but it leads to a huge change in the dynamics of the game. Suddenly, arrows are much more powerful than swords. Players will stop using swords and start shooting arrows, even at close range—that’s a change in dynamics.

Once the players start behaving differently, Owen will need to change his campaigns. For example, some battles designed to be difficult may suddenly be too easy for the players. That makes the players change again.

Take a minute to think about all of that. A tiny change to the rules leads to a huge change in the way the players behave. A small change in mechanics caused a very large change in dynamics. Owen didn’t make those changes to gameplay directly; they were follow-on effects from his small rule change. In technical terms, the change in dynamics emerged from the change in mechanics.

If you haven’t come across the idea of emergence before it may seem a little odd. Let’s look at a concrete example:

We’ll start with a classic video game. The mechanics of Space Invaders are simple. Aliens march back and forth and fire shots down; if a shot hits the player, they lose a life. The player moves the ship left and right and fires shots up. If a shot hits an alien, it’s destroyed. A mothership occasionally flies across the top of the screen for more points. Shields slowly get eaten away by shots. Different aliens add different scores. The aliens march faster as the game goes on. Take a few minutes and watch a gameplay video, or even better play the game.

The dynamics of Space Invaders are more complex. The game starts off very easy—most players can get through the first wave after a few tries—but it quickly gets harder and harder. The only thing that changes is the speed at which the invaders march and shoot. Somehow as the invaders get faster and faster, it changes the entire game. The tempo—how fast the game feels—drastically changes.

Some players try to shoot the aliens starting at the edge of the formation, because the gap at the side of the formation slows down their descent. That’s not written anywhere in the code, which just has simple rules for how the invaders march. That’s a dynamic, and it’s emergent because it’s a side effect of how the mechanics combine—specifically, the mechanics of how the player shots work combined with the rules for how the invaders march. None of that is programmed into the code of the game. It’s not part of the mechanics. It’s all dynamics.

NOTE
Have you ever heard a gamer complain about “balance” in a game—like the choice of weapons in a shooter? Any individual type of gun in a first-person shooter has specific behavior, but add a gun that’s too powerful and the entire game changes. That’s another example of emergence.

NOTE
Dynamics can feel like a really abstract concept at first! We’ll spend more time on it later in the chapter. For now, keep all of this stuff about dynamics in mind when you’re doing the next project. See if you can spot how dynamics come into play as you’re coding it.


Video games are serious business.

The video game industry is growing globally every year, and employs hundreds of thousands of people all over the world, and it’s a business that a talented game designer can break into! There’s an entire ecosystem of independent game developers who build and sell games, either as individuals or on small teams.

But you’re right—C# is a serious programming language, and it’s used for all sorts of serious, non-gaming applications. In fact, while C# is a favorite language among game developers, it’s also one of the most common languages found in businesses across many different industries.

So for this next project, let’s get some practice with inheritance by building a serious business application.

Build a beehive management system
The queen bee needs your help! Her hive is out of control, and she needs a program to help manage her honey production business. She’s got a beehive full of workers, and a whole bunch of jobs that need to be done around the hive, but somehow she’s lost control of which bee is doing what, and whether or not she’s got the beepower to do the jobs that need to be done. It’s up to you to build a beehive management system to help her keep track of her workers. Here’s how it’ll work.


 The queen assigns jobs to her workers.

There are three different jobs that the workers can do. Nectar collector bees fly out and bring nectar back to the hive. Honey manufacturer bees turn that nectar into honey, which bees eat to keep working. Finally, the queen is constantly laying eggs, and egg care bees make sure they become workers.

 When the jobs are all assigned, it’s time to work.

Once the queen’s done assigning the work, she’ll tell the bees to work the next shift. At the end of the shift she gets a shift report that tells her how many bees are assigned to each job and the status of the nectar and honey in the honey vault.

 Help the queen grow her hive.

Like all business leaders, the queen is focused on growth. The beehive business is hard work, and she measures her hive in the total number of workers. Can you help the queen keep adding workers? How big can she grow the hive before it runs out of honey and she has to file for bee-nkruptcy?


This is a bigger project than the ones in the last few chapters.

NOTE
This is a big project. You can do this!

The main goal of this book is to help you learn C#. But we’ll also teach important skills that can help you become a great developer. One way to do that is to help show you how to work on—and finish!—larger projects. When you did the Animal Matching Game project in Chapter 1, you broke it down into smaller pieces. You’ll do the same for the Beehive Management System project. First you’ll create the XAML for the main page, then you’ll do a “Sharpen Your Pencil” exercise to complete the code for several of the classes, and finally you’ll do an exercise to finish the rest of the code for the project.

How the Beehive Management System app works
When the app starts, the honey vault has 25 units of honey and 100 units of nectar, and the hive has three workers: a nectar collector bee, a honey manufacturer bee, and an egg care bee. The first shift report delivered is displayed on the right-hand side of the app.


The page uses a grid to lay out the controls for the UI
The Beehive Management System app is a .NET MAUI app. The main page uses a Grid control to lay out the Labels, Buttons, Picker, and other controls.

Take a closer look at it to see how it works:


The Grid has three properties:

 Margin="20" adds 20 pixels of space between the controls in the grid and the window frame.

 ColumnSpacing="20" adds 20 pixels of space between the two columns.

 MinimumHeightRequest="400" keeps the grid from getting smaller than 400 pixels high. If you resize the window smaller than that, the ScrollView will scroll the grid for you.

The Bee Jobs box uses a Border with a VerticalStackLayout
The middle row of the left column has a box that contains a picker and a button. You’ll use a Border to draw the box. You need to put two controls inside the Border, but Border controls can only contain one other control, so you’ll put a VerticalStackLayout inside it to contain the Picker and Button controls.


EXERCISE

Add the XAML for the main page to your MainPage.xaml.cs file. It uses a grid—here’s how it’s laid out:


The left column of the grid has the following controls:

The top row has a Label control. Its FontSize property is set to Large.

The middle row has a Border control. It contains a VerticalStackLayout, which contains a Picker and a Button. Use x:Name to name the Picker JobPicker and name the button AssignJobButton.

The Picker has a 20 pixel bottom margin. They both have FontSize set to Medium. Look at the screenshot to figure out the Picker’s Title and the Button’s Text properties. Add a SemanticProperties.Hint to each of them.

Modify the MainPage constructor in MainPage.xaml.cs to set JobPicker.ItemsSource to a new array that contains the following strings: "Nectar Collector", "Honey Manufacturer", "Egg Care"

The bottom row has a Button control. Use x:Name to name it WorkShiftButton. Its font size is large.

The bottom row has a second Button control. You can’t see it because it has the IsVisible="False" property. Set its BackgroundColor property to Red, its FontSize to Large, and use x:Name to name it OutOfHoneyButton. It should display the following text: "The hive is out of honey"

Add an event handler method for all three of the Button controls. Make sure they all have semantic hints.

The right column of the grid has the following controls:

The top row has a Label control. Its FontSize property is set to large.

The bottom two rows have another Label control with RowSpan="2” so it spans both rows. Its background color is set to black, and text color is set to yellow. It has the Padding="10” property to give space between the edge and the text, and VerticalOptions="FillAndExpand” so it fills the cell. Use x:Name to name it StatusReport.

EXERCISE SOLUTION

Here’s the XAML for the main page. Did yours come out a little different than ours? That’s okay! There are a lot of different ways to design this page—if it still works and you like the way it looks, then you got it right.


The beehive management system class model
Here are the classes that you’ll build for the beehive management system. There’s an inheritance model with a base class and four subclasses, a static class to manage the honey and nectar that drive the hive business, and the MainPage class with the code-behind for the main page.


All bees in the system extend the Bee class
This is the Bee class. It’s the superclass of all the other bee classes in the system. Each shift, every bee—the queen and every one of her wokers—consumes honey and does their job. The system does this by calling the WorkTheNextShift method, which consumes the honey from the vault using the CostPerShift property. The WorkTheNextShift method is marked virtual because each subclass will extend it to do its specific job.



All the constants are in their own static class
Each of the bees consumes honey and does a job. These constants determine how both of those things work.


The worker bees extend the Bee class
Workers can be assigned one of three jobs: nectar collectors add nectar to the honey vault, honey manufacturers convert the nectar into honey, and egg care bees turn eggs into workers who can be assigned to jobs. During each shift, the Queen lays eggs (just under two shifts per egg). The Queen updates her shift report at the end of the shift. It shows the honey vault status and the number of eggs, unassigned workers, and bees assigned to each job.

Here’s a closer look at how the NectarCollector, HoneyManufacturer, and EggCare classes work. They’re all subclasses of the Bee class. They all use constants defined in the static Constants class. Each bee does a different job, so they all have different WorkTheNextShift methods that override Bee.WorkTheNextShift to do their jobs.


SHARPEN YOUR PENCIL

Fill in the missing parts of the Bee subclasses based on what we’ve told you about how they work.


SHARPEN YOUR PENCIL SOLUTION

Fill in the missing parts of the Bee subclasses based on what we’ve told you about how they work.


The Queen class: how she manages the worker bees
When you press the button to work the next shift, the button’s event handler calls the Queen object’s WorkTheNextShift method, which is inherited from the Bee base class. Here’s what happens next:

 Bee.WorkTheNextShift calls HoneyVault.ConsumeHoney(HoneyConsumed), using the CostPerShift property (which each subclass overrides with a different value) to determine how much honey she needs.

 The Queen overrides overrides WorkTheNextShift so that each shift she adds 0.45 eggs to her private eggs field (using the EGGS_PER_SHIFT constant). The EggCare bee will call her ReportEggConversion method to tell the Queen to update the egg and worker counts. She’ll then decrease eggs and increase unassignedWorkers.

 Queen.WorkTheNextShift then uses a foreach loop to call each worker’s WorkTheNextShift method.

 It consumes honey for each unassigned worker. The HONEY_PER_UNASSIGNED_WORKER const tracks how much each one consumes per shift.

 Finally, it calls its UpdateStatusReport method, which takes a boolean argument telling it whether all the workers did their jobs. If they didn’t, it adds a warning.

When you press the button to assign a job to a bee, the event handler calls the Queen object’s AssignBee method, which takes a string with the job name (you’ll get that name from jobSelector.text). It uses a switch statement to create a new instance of the appropriate Bee subclass and pass it to AddWorker, so make sure you add the AddWorker method below to your Queen class.


Here’s the code-behind for MainPage.xaml.cs
This code will help you figure out how to write the code for the HoneyVault and Queen classes.


EXERCISE

NOTE
This is the biggest exercise we’ve given you so far. You can do this! Just take it one step at a time.

Add the Constants class we gave you earlier, then add a static class called HoneyVault to manage the honey

Look back at the “Sharpen Your Pencil” solution to see how the Bee subclasses call methods in HoneyVault.

Add two constants to the static Constants class (INITIAL_HONEY = 25f and INITIAL_NECTAR = 100f) and use them to initialize the two private fields called honey and nectar.

The ConsumeHoney method is how the bees use honey to do their jobs. It takes a parameter, amount. If honey is greater than or equal to amount, it subtracts amount from honey and returns true; otherwise it returns false.

The CollectNectar method is called by the NectarCollector bee each shift. It takes a parameter, amount. If amount is greater than zero, it adds it to the nectar field.

The ConvertNectarToHoney method converts nectar to honey. It takes a decimal parameter called amount, subtracts that amount from its nectar field, and adds amount × NECTAR_CONVERSION_RATIO to the honey field. (If the amount passed to the method is greater than the nectar left in the vault, it converts the remaining nectar.)

The StatusReport property only has a get accessor that returns a string with separate lines with the amount of honey and the amount of nectar in the vault. If the honey is below LOW_LEVEL_WARNING, it adds a warning ("LOW HONEY - ADD A HONEY MANUFACTURER"). It does the same for the nectar field. Then use the SemanticScreenReader.Default.Announce method to announce the warnings to improve accessibility.

Add the HoneyManufacturer, NectarCollector, and BeeCare classes, then create the Queen class

The “Sharpen Your Pencil” solution has the code for the first three Bee subclasses.

The Queen class is the other subclass of Bee. We showed you how the Queen class works (and gave you an AddWorker method that adds workers to an array of Bee objects). Also look carefully at the code-behind to see how it’s used. The Queen class has a private Bee[] field called workers. It starts off as an empty array. We gave you the AddWorker method to add to it—you’ll create the AssignBee method that instantiates Bee objects and calls it.

There are two private decimal fields called eggs and unassignedWorkers to keep track of the number of eggs (which she adds to each shift) and the number of workers waiting to be assigned.

The queen starts off with three unassigned workers (so set unassignedWorkers to 3) and zero eggs. The Queen’s constructor calls the AssignBee method three times to create three worker bees, one of each type.

The AssignBee method takes a parameter with a job name (like "Egg Care"). It has switch (job) with cases that call the AddWorker method that we gave you when we described the queen class. For example, if job is "Egg Care" then it calls AddWorker(new EggCare(this)).

Go back to the “Sharpen Your Pencil” solution and look at how the EggCare bees call the Queen’s ReportEggConversion method. The method takes a decimal parameter called eggsToConvert. It checks if the eggs field is >= eggsToConvert—if it is, it subtracts eggsToConvert from eggs and adds it to unassignedWorkers.

She overrides the WorkTheNextShift method to add eggs, tell the worker bees to work, and feed honey to the unassigned workers waiting for work. The EGGS_PER_SHIFT constant (set to 0.45f) is added to the eggs field. She uses a foreach loop to call each worker’s WorkTheNextShift method. Then she calls HoneyVault.ConsumeHoney, passing it the constant HONEY_PER_UNASSIGNED_WORKER (set to 0.5f) × unassignedWorkers. The loop keeps track of whether all of the workers did their jobs, and passes that to UpdateStatusReport.

Look carefully at the shift reports in the screenshots. The private UpdateStatusReport method generates it (using HoneyVault.StatusReport). She calls UpdateShiftReport at the end of her WorkTheNextShift and AssignBee methods. UpdateShiftReport calls a private WorkerStatus method with a string parameter called job (“Nectar Collector”) and returns a string with the number of workers doing that job (“3 Nectar Collector bees”). It also takes a bool parameter—if it’s true, it adds "WARNING: NOT ALL WORKERS DID THEIR JOBS" to the end of the report.

NOTE
If you get stuck, it’s not cheating to look at our solution. That’s a great way to learn, too!

EXERCISE SOLUTION

Here are the constants that were added to the static Constants class. They’re used to initialize and reset HoneyVault.

static class Constants
{
    /// <summary>
    /// The amount of honey the hive starts with
    /// </summary>
    public const decimal INITIAL_HONEY = 25m;

    /// <summary>
    /// The amount of nectar the hive starts with
    /// </summary>
    public const decimal INITIAL_NECTAR = 100m;
Here’s the Queen class, a Bee subclass that assigns workers, tells them to do their jobs, and makes status reports:


EXERCISE SOLUTION


EXERCISE SOLUTION



Okay, you got us. Yes, you’re right. This is a game.

Specifically, it’s a resource management game, or a game where the mechanics are focused on collecting, monitoring, and using resources. If you’ve played a simulation game like SimCity or a strategy game like Civilization, you’ll recognize resource management as a big part of the game, where you need resources like money, metal, fuel, wood, or water to run a city or build an empire.

Resource management games are a great way to experiment with the relationship between mechanics, dynamics, and aesthetics:

 The mechanics are simple: the player assigns workers and then initiates the next shift. Then each bee either adds nectar, reduces nectar/increases honey, or reduces eggs/increases workers. The egg count increases, and the report is displayed.

 The aesthetics are more complex. Players feel stress as the honey or nectar levels fall and the low-level warning is displayed. They feel excitement when they make a choice, and satisfaction when it affects the game—and then stress again, as the numbers stop increasing and start decreasing again.

 The game is driven by the dynamics. There’s nothing in the code that makes the honey or nectar scarce—they’re just consumed by the bees and eggs.

BRAIN POWER

A small change in HoneyVault.NECTAR_CONVERSION_RATIO can make the game much easier or much harder by making the honey drain slowly or quickly. What other numbers affect gameplay? What do you think is driving those relationships?

NOTE
Really take a minute and think about this, because it gets to the heart of what dynamics are about. Do you see any way to use some of these ideas in other kinds of programs, and not just games?

Feedback drives your Beehive Management game
Let’s take a few minutes and really understand how this game works. The nectar conversion ratio has a big impact on your game. If you change the constants, it can make really big differences in gameplay. If it takes just a little honey to convert an egg to a worker, the game gets really easy. If it takes a lot, the game gets much harder. But if you go through the classes, you won’t find a difficulty setting. There’s no Difficultly field on any of them. Your Queen doesn’t get special power-ups to help make the game easier, or tough enemies or boss battles to make it more difficult. In other words, there’s no code that explicitly creates a relationship between the number of eggs or workers and the difficulty of the game. So what’s going on?

You’ve probably played with feedback before. Start a video call between your phone and your computer. Hold the phone near the computer speaker and you’ll hear noisy echoes. Point the camera at the computer screen and you’ll see a picture of the screen inside the picture of the screen inside the picture of the screen, and it will turn into a crazy pattern if you tilt the phone. This is feedback: you’re taking the live video or audio output and feeding it right back into the input. There’s nothing in the code of the video call app that specifically generates those crazy sounds or images. Instead, they emerge from the feedback.


Workers and honey are in a feedback loop
Your Beehive Management game is based on a series of feedback loops: lots of little cycles where parts of the game interact with each other. For example, honey manufacturers add honey to the vault, which is consumed by honey manufacturers, who make more honey.


And that’s just one feedback loop. There are many different feedback loops in your game, and they make the whole game more complex, more interesting, and (hopefully!) more fun.


MECHANICS, AESTHETICS, AND DYNAMICS UP CLOSE

Feedback loops...equilibrium...making your code do something indirectly by creating a system...does all this have your head spinning a little? Here’s another opportunity to use game design to explore a larger programming concept.

You’ve learned about mechanics, dynamics, and aesthetics—now it’s time to bring them all together. The Mechanics-Dynamics-Aesthetics framework, or MDA framework, is a formal tool (“formal” just means it’s written down) that’s used by researchers and academics to analyze and understand games. It defines the relationship between mechanics, dynamics, and aesthetics, and gives us a way to talk about how they create feedback loops to influence each other.

The MDA framework was developed by Robin Hunicke, Marc LeBlanc, and Robert Zubek, and published in a 2004 paper called “MDA: A Formal Approach to Game Design and Game Research”—it’s quite readable, without a ton of academic jargon. (Remember back in Chapter 5, when we talked about how aesthetics includes challenge, narrative, sensation, fantasy, and expression? That came from this paper.) Take a few minutes and look through it, it’s actually a great read: http://bit.ly/mda-paper.

The goal of the MDA framework is to give us a formal way to think about and analyze video games. This may sound like something that’s only important in an academic setting, like a college course on game design. But it’s actually really valuable to us as everyday game developers, because it can help us understand how people perceive the games we create, and give us a deeper insight into what makes those games fun.

Game designers had been using the terms mechanics, dynamics, and aesthetics informally, but the paper really gave them a solid definition and established the relationship between them.


One thing that the MDA framework tackles is the difference in perspective between gamers and game designers. Players, first and foremost, want the game to be fun—but we’ve already seen how “fun” can differ wildly from player to player. Game designers, on the other hand, typically see a game through the lens of its mechanics, because they spend their time writing code, designing levels, creating graphics, and tinkering with the mechanical aspects of the game.

All developers (not just game developers!) can use the MDA framework to get a handle on feedback loops

Let’s use the MDA framework to analyze a classic game, Space Invaders, so we can better understand feedback loops.

Start with the mechanics of the game: the player’s ship moves left and right and fires shots up; the invaders march in formation and fire shots down; the shields block shots. The fewer enemies there are on screen, the faster they go.

Players figure out strategies: shoot where the invaders will be, pick off enemies on the sides of the formation, hide behind the shields. The code for the game doesn’t have an if/else or switch statement for these strategies; they emerge as the player figures out the game. Players learn the rules, then start to understand the system, which helps them better take advantage of the rules. In other words, the mechanics and dynamics form a feedback loop.

The invaders get faster, the marching sounds speed up, and the player gets a rush of adrenaline. The game gets more exciting—and in turn, the player has to make decisions more quickly, causing them to make mistakes, which makes them change strategy, and that has an effect on the system. The dynamics and aesthetics form another feedback loop.

None of this happened by accident. The speed of the invaders, the rate at which they increase, the sounds, the graphics... these were all carefully balanced by the game’s creator, Tomohiro Nishikado, who spent over a year designing it, drawing inspiration from earlier games, H. G. Wells, even his own dreams to create a classic game.

The Beehive Management System is turn-based... now let’s convert it to real-time
A turn-based game is a game where the flow is broken down into parts—in the case of the Beehive Management System, into shifts. The next shift doesn’t start until you click a button, so you can take all the time you want to assign workers. We can use a timer—like the one you used in Chapter 1—to convert it to a real-time game where time progresses continuously... and we can do it with just a few lines of code.

 Start a timer at the end of the MainPage constructor.

Add this line of code to the end of the MainPage constructor to start a timer:


 Generate the TimerTick method and call the Work Shift button event handler.

We want the timer to keep the game moving forward, so we can have it automatically trigger the next shift if the player hasn’t done it already. Use the IDE’s Generate Method feature to generate the TimerTick method—notice that it generates it with a bool return type.

Here’s the code for the method:


Now run your game. A new shift starts every 1.5 seconds, whether or not you click the button. This is a small change to the mechanics, but it dramatically changes the dynamics of the game, which leads to a huge difference in aesthetics. It’s up to you to decide if the game is better as a turn-based or real-time simulation.

Curious about that EventArgs class? Learn more about it in our downloadable chapter on events and delegates.


Yes! The timer changed the mechanics, which altered the dynamics, which in turn impacted the aesthetics.

Let’s take a minute and think about that feedback loop. The change in mechanics (a timer that automatically clicks the “Work the next shift” button every 1.5 seconds) creates a totally new dynamic: a window when players must make decisions, or else the game makes the decision for them. That increases the pressure, which gives some players a satisfying shot of adrenaline, but just causes stress in other players—the aesthetics changed, which makes the game more fun for some people but less fun for others.

NOTE
There’s a feedback loop here, too. As players feel more stress, they make worse decisions, changing the game... aesthetics feeds back into mechanics.

But you only added half a dozen lines of code to your game, and none of them included “make this decision or else” logic. That’s an example of behavior that emerged from how the timer and the button work together.


Feedback loops and emergence are important programming concepts.

We designed this project to give you practice with inheritance, but also to let you explore and experiment with emergent behavior. That’s behavior that comes not just from what your objects do individually, but also out of the way objects interact with each other. The constants in the game (like the nectar conversion ratio) are an important part of that emergent interaction. When we created this exercise, we started out by setting those constants to some initial values, then we tweaked them by making tiny adjustments until we ended up with a system that’s not quite in equilibrium—a state where everything is perfectly balanced—so the player needs to keep making decisions in order to make the game last as long as possible. That’s all driven by the feedback loops between the eggs, workers, nectar, honey, and queen.

NOTE
Try experimenting with these feedback loops. Add more eggs per shift or start the hive with more honey, for example, and the game gets easier. Go ahead, give it a try! You can change the entire feel of the game just by making small changes to a few constants.

Some classes should never be instantiated
Remember our zoo simulator class hierarchy? You’ll definitely end up instantiating a bunch of Hippos, Dogs, and Lions. What about the Canine and Feline classes? How about the Animal class? It turns out that there are some classes that just don’t need to be instantiated...and, in fact, don’t make any sense if they are.

Does that sound weird? Actually, it happens all the time—in fact, you created several classes earlier in the chapter that should never be instantiated.



BRAIN POWER

So what happens when you instantiate the Bird, WeaponDamage, or Bee classes? Does it ever make sense to do it? Do all of their methods even work?

An abstract class is an intentionally incomplete class
It’s really common to have a class with “placeholder” members that it expects the subclasses to implement. It could be at the top of the hierarchy (like your Bee, WeaponDamage, or Bird classes) or in the middle (like Feline or Canine in the zoo simulator class model). They take advantage of the fact that C# always calls the most specific method, like how WeaponDamage calls the CalculateDamage method that’s only implemented in SwordDamage or ArrowDamage, or how Bee.WorkTheNextShift depends on the subclasses to override it.

C# has a tool that’s built specifically for this: an abstract class. It’s a class that’s intentionally incomplete, with empty class members that serve as placeholders for the subclasses to implement. To make a class abstract, add the abstract keyword to the class declaration. Here’s what you need to know about abstract classes.

 An abstract class works just like a normal class.

You define an abstract class just like a normal one. It has fields and methods, and it can inherit from other classes, too, exactly like a normal class. There’s almost nothing new to learn.

 An abstract class can have incomplete “placeholder” members.

An abstract class can include declarations of properties and methods that must be implemented by inheriting classes. A method that has a declaration but no statements or method body is called an abstract method, and a property that only declares its accessors but doesn’t define them is called an abstract property. Subclasses that extend it must implement all abstract methods and properties unless they’re also abstract.

 Only abstract classes can have abstract members.

If you put an abstract method or property into a class, then you’ll have to mark that class abstract or your code won’t compile. You’ll learn more about how to mark a class abstract in a minute.

 An abstract class can’t be instantiated.

The opposite of abstract is concrete. A concrete method is one that has a body, and all the classes you’ve been working with so far are concrete classes. The biggest difference between an abstract class and a concrete class is that you can’t use new to create an instance of an abstract class. If you do, C# will give you an error when you try to compile your code.

Try it now! Create a new console app, add an empty abstract class, and try to instantiate it:

abstract class MyAbstractClass { }

MyAbstractClass myInstance = new MyAbstractClass();
The compiler will give you an error, and won’t let you build your code:



Because you want to provide some of the code, but still require that subclasses fill in the rest of the code.

Sometimes bad things happen when you create objects that should never be instantiated. The class at the top of your class diagram usually has some fields that it expects its subclasses to set. An Animal class may have a calculation that depends on a Boolean called HasTail or Vertebrate, but there’s no way for it to set that itself. Here’s a quick example of a class that’s problematic when instantiated...

Let’s plan a trip to another planet
Create a new console app, then add the PlanetMission class and its two subclasses, Mars and Venus.


Then add these top-level statements to instantiate each of the classes and call their MissionInfo methods:

Console.WriteLine(new Venus().MissionInfo());
Console.WriteLine(new Mars().MissionInfo());
Console.WriteLine(new PlanetMission().MissionInfo());
Before you run this code, can you figure out what it will print to the console?

Like we said, some classes should never be instantiated
Try running the PlanetMission console app. Did it do what you expected? It printed two lines to the console:

We'll burn 86509992 units of fuel in 1389 hours
We'll burn 159160000 units of fuel in 2486 hours
But then it threw an exception.

The problems all started when you created an instance of the PlanetMission class. Its FuelNeeded method expects the fields to be set by the subclass. When they aren’t, they get their default values—zero. And when C# tries to divide a number by zero, this happens...


Solution: use an abstract class
When you mark a class abstract, C# won’t let you write code to instantiate it. So how does that fix this problem? It’s like the old saying goes—prevention is better than cure. Add the abstract keyword to the PlanetMission class declaration:


As soon as you make the change, the compiler gives you an error:


Your code won’t compile at all—and no compiled code means no exception. This is really similar to the way you used the private keyword in Chapter 5, or virtual and override earlier in this chapter. Making some members private doesn’t change the behavior. It just prevents your code from building if you break the encapsulation. The abstract keyword works the same way: you’ll never get an exception instantiating an abstract class because the C# compiler won’t let you instantiate one in the first place.

When you add the abstract keyword to a class declaration, the compiler gives you an error any time you try to create an instance of that class.

An abstract method doesn’t have a body
The Bird class that you built was never meant to be instantiated. That’s why it uses Console.Error to write an error message if a program tries to instantiate it and call its LayEggs method:

class Bird
{
    public virtual Egg[] LayEggs(int numberOfEggs)
    {
        Console.Error.WriteLine
             ("Bird.LayEggs should never get called");
        return new Egg[0];
    }
}

Since we don’t ever want to instantiate the Bird class, let’s add the abstract keyword to its declaration. But that’s not enough—not only should this class never be instantiated, but we want to require that every subclass that extends Bird must override the LayEggs method.

That’s exactly what happens when you add the abstract keyword to a class member. An abstract method only has a class declaration but no method body—the body must be implemented by any subclass that extends the abstract class. The body of a method is the code between the curly braces after the declaration—and it’s something abstract methods can’t have.

Go back to your Bird project from earlier and replace the Bird class with this abstract class:


Your program still runs like it did before! But try adding this line to the top-level statements:

Bird abstractBird = new Bird();
and you’ll get a compiler error:


Try to add a body to the LayEggs method:

public abstract Egg[] LayEggs(int numberOfEggs)
{
    return new Egg[0];
}
and you’ll get a different compiler error:


If an abstract class has abstract members, every subclass must override all of those members.

Abstract properties work just like abstract methods
Let’s go back to the Bee class from our earlier example. We already know that we don’t want the class to be instantiated, so let’s modify it to turn it into an abstract class. We can do that just by adding the abstract modifier to the class declaration:

abstract class Bee
{
   /* the rest of the class stays the same */
}
But there’s one other virtual member—and it’s not a method. It’s the CostPerShift property, which the Bee.WorkTheNextShift method calls to figure out how much honey the bee will require this shift:

public virtual decimal CostPerShift { get; }
We learned in Chapter 5 that properties are really just methods that are called like fields. Use the abstract keyword to create an abstract property just like you do with a method:

public abstract decimal CostPerShift { get; }
Abstract properties can have a get accessor, a set accessor, or both get and set accessors. Setters and getters in abstract properties can’t have method bodies. Their declarations look just like automatic properties—but they’re not, because they don’t have any implementation at all. Like abstract methods, abstract properties are placeholders for properties that must be implemented by any subclass that extends their class.

Here’s the whole abstract Bee class, complete with abstract method and property (but not the comments):

abstract class Bee
{
    public abstract decimal CostPerShift { get; }

    public string Job { get; private set; }

    public Bee(string job)
    {
        Job = job;
    }

    public virtual bool WorkTheNextShift()
    {
        if (HoneyVault.ConsumeHoney(CostPerShift))
            return true;
        else
            return false;
    }
}
NOTE
 Replace this!

Replace the Bee class in your Beehive Management System app with this new abstract one. It will still work! But now if you try to instantiate the Bee class with new Bee(); you’ll get a compiler error. Even more importantly, you’ll get an error if you extend Bee but forget to implement CostPerShift.

EXERCISE

It’s time to get some practice with abstract classes—and you don’t have to look far to find good candidates for classes to make abstract.

Earlier in the chapter you modified your SwordDamage and ArrowDamage classes to extend a new class called WeaponDamage. Make the WeaponDamage class abstract. There’s a good candidate for an abstract method in WeaponDamage—make that abstract as well.

THERE ARE NO DUMB QUESTIONS
Q: When I mark a class abstract, does that change the way it behaves? Do the methods or properties work differently than they do in a concrete class?

A: No, abstract classes work exactly like any other kind of class. When you add the abstract keyword to the class declaration, it causes the C# compiler to do two things: prevent you from using the class in a new statement, and allow you to include abstract members.

Q: I’m confused about the way you’re using the word “implement” or “implementation.” What do you mean when you’re talking about implementing an abstract method?

A: When you use the abstract keyword to declare an abstract method or property, we say that you’re defining the abstract member. Later on, when you add a complete method or property with the same declaration to a concrete class, we say that you’re implementing the member. So you define abstract methods or properties in an abstract class, and implement them in concrete classes that extend it.

Q: I’m still having trouble with the idea that the abstract keyword keeps my code from compiling if I try to instantiate an instance of an abstract class. I already have trouble finding and fixing all of the compiler errors. Why do I want to make it even harder to get my code to build?

A: Sometimes when you’re first learning to code, those “CS” compiler errors can be a little frustrating. Everyone has spent time trying to track down a missing comma, period, or quotation mark to try to clear out the Errors List. So why would you ever use a keyword like abstract or private that puts even more restrictions on your code and makes those compiler errors even more common? It seems a little counterintuitive. If you never use the abstract keyword, you’ll never see a “Cannot create an instance of the abstract class” compiler error. So why ever use it?

The reason you use keywords like abstract or private that keep your code from building in certain cases is that it’s a lot easier to fix a “Cannot create an instance of the abstract class” compiler error than it is to track down the error that it prevents. If you have a class that should never be instantiated, it’s because the bug you get when you create an instance of it instead of a subclass can be subtle and difficult to find. Adding abstract to the base class causes your code to fail fast with an error that’s easier to fix.

Bugs caused by instantiating a base class that should never be instantiated can be subtle and hard to find. Making it abstract makes your code fail fast if you try to create an instance of it.

EXERCISE SOLUTION

The WeaponDamage class should never be instantiated—the only reason it exists is so that the SwordDamage and ArrowDamage classes can inherit its properties and methods. So it makes sense to mark this class abstract. Have a look at its CalculateDamage method:


protected virtual void CalculateDamage() {
  /* the subclass overrides this */
}
This method is a great candidate to convert to an abstract method, because it only exists so that subclasses will override it with their own implementations that update the Damage property. Here’s everything that you needed to change in the WeaponDamage class:

abstract class WeaponDamage
{
    /* the Damage, Roll, Flaming, and Magic properties
       stay the same */

    protected abstract void CalculateDamage();

    public WeaponDamage(int startingRoll)
    {
        roll = startingRoll;
        CalculateDamage();
    }
}
Was this the first time you’ve read through the code you wrote for previous exercises?

It may feel a little weird to go back to code you wrote before—but that’s actually something a lot of developers do, and it’s a habit you should get used to. Did you find things that you would do differently the second time around? Are there improvements or changes that you might make? It’s always a good idea to take the time to refactor your code. That’s exactly what you did in this exercise: you changed the structure of the code without modifying its behavior. That’s refactoring.


That sounds great! But there’s a problem.

If C# let you inherit from more than one base class, it would open up a whole can of worms. When a language lets one subclass inherit from two base classes, it’s called multiple inheritance. If C# supported multiple inheritance, you would end up in a big fat class conundrum called...

The Deadly Diamond of Death

What would happen in a CRAZY world where C# allowed multiple inheritance? Let’s play a little game of “what if” and find out.

NOTE
That’s its real name! Some developers just call it the “diamond problem.”

What if... you had a class called Appliance that had an abstract method called TurnOn?

And what if... it had two subclasses: Oven with a Temperature property, and Toaster with a SicesOfBread property?

And what if... you wanted to create a ToasterOven class that inherited both Temperature and SlicesOfBread?

And what if...C# supported multiple inheritance, so you could do that?

Then there’s only one more question...

Which TurnOn does ToasterOven inherit?

Does it get the version from Oven? Or does it get the version from Toaster?

There’s no way to know!

And that’s why C# doesn’t allow multiple inheritance.


BULLET POINTS
A subclass can override members it inherits, replacing them with new methods or properties with the same names.

To override a method or property, add the virtual keyword to the base class, then add the override keyword to the member with the same name in the subclass.

The protected keyword is an access modifier that makes a member public only to its subclasses, but private to every other class.

When a subclass overrides a method in its base class, the more specific version defined in the subclass is always called—even if the base class is calling it.

If a subclass just adds a method with the same name as a method in its base class, it only hides the base class method instead of overriding it. Use the new keyword when you’re hiding methods.

The dynamics of a game describe how the mechanics combine and cooperate to drive the gameplay.

A subclass can access its base class using the base keyword. When a base class has a constructor, your subclass needs to use the base keyword to call it.

A subclass and base class can have different constructors. The subclass can choose what values to pass to the base class constructor.

Build your class model on paper before you write code to help you understand and solve your problem.

When your classes overlap as little as possible, that’s an important design principle called separation of concerns.

Don’t repeat yourself (or DRY) is another design principle aimed at not repeating the code that does the same thing multiple places in an app’s code.

Emergent behavior occurs when objects interact with each other, beyond the logic directly coded into them.

Abstract classes are intentionally incomplete classes that cannot be instantiated.

Adding the abstract keyword to a method or property and leaving out the body makes it abstract. Any concrete subclass of the abstract class must implement it.

Refactoring means reading code you already wrote and making improvements without modifying its behavior.

C# does not allow for multiple inheritance because of the diamond problem: it can’t determine which version of a member inherited from two base classes to use.


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


6. Inheritance: Your Object’s Family Tree
7. Interfaces, Casting, and “is”: Making Classes keep their Promises
About the Authors
12h 51m remaining
Chapter 7. Interfaces, Casting, and “is”: Making Classes keep their Promises
A NOTE FOR EARLY RELEASE READERS
With Early Release ebooks, you get books in their earliest form—the authors’ raw and unedited content as they write—so you can take advantage of these technologies long before the official release of these titles.

This will be the 7th chapter of the final book. Please note that the GitHub repo will be made active later on.

If you have comments about how we might improve the content and/or examples in this book, or if you notice missing material within this chapter, please reach out to the editor at mcronin@oreilly.com.


Need an object to do a specific job? Use an interface.

Sometimes you need to group your objects together based on the things they can do rather than the classes they inherit from—and that’s where interfaces come in. You can use an interface to define a specific job. Any instance of a class that implements the interface is guaranteed to do that job, no matter what other classes it’s related to. To make it all work, any class that implements an interface must promise to fulfill all of its obligations…or the compiler will break its kneecaps, see?

The beehive is under attack!
An enemy hive is trying to take over the Queen’s territory and keeps sending enemy bees to attack her workers. She’s added a new elite Bee subclass called HiveDefender to help defend the hive.


HiveDefender needs a DefendHive method because enemies can attack at any time
We can add a HiveDefender subclass to the Bee class hierarchy by extending the Bee class, overriding its CostPerShift with the amount of honey each defender consumes every shift, and overriding the DoJob method to fly out to the enemy hive and attack the enemy bees.


But enemy bees can attack at any time. We want defenders to be able to defend the hive whether or not they’re currently doing their normal jobs.

So in addition to DoJob, we’ll add a DefendHive method to any Bee that can defend the hive—not just the elite HiveDefender workers, but any of their sisters who can take up arms and protect their Queen. The Queen will call her workers’ DefendHive methods any time she sees that her hive is under attack.

RELAX

We didn’t include the complete code for the HiveDefender class… and that’s okay!

This chapter is all about interfaces, which are really useful and very important! But they’re also a bit more abstract than other C# concepts we’ve covered so far. That’s why we’ve included lots of examples in this chapter—including ones like this that show an idea without getting bogged down into code details.

We could use casting to call the DefendHive method…
When you coded the Queen.DoJob method, you used a foreach loop to get each Bee reference in the workers array, then you used that reference to call worker.DoJob. If the hive is under attack, the Queen will want to call her defenders’ DefendHive methods. So we’ll give her a HiveUnderAttack method that gets called any time the hive is being attacked by enemy bees, and she’ll use a foreach loop to order her workers to defend the hive until all of the attackers are gone.

But there’s a problem. The Queen can use the Bee references to call DoJob because each subclass overrides Bee.DoJob, but she can’t use a Bee reference to call the DefendHive method, because that method isn’t part of the Bee class. So how does she call DefendHive?

Since DefendHive is only defined in each subclass, we’ll need to use casting to convert the Bee reference to the correct subclass in order to call its DefendHive method.

public void HiveUnderAttack() {
    foreach (Bee worker in workers) {
        if (EnemyHive.AttackingBees > 0) {
            if (worker.Job == "Hive Defender") {
                HiveDefender defender = (HiveDefender) worker;
                defender.DefendHive();
            } else if (worker.Job == "Nectar Defender") {
                NectarDefender defender = (NectarDefender) defender;
                defender.DefendHive();
            }
        }
    }
}
…but what if we add more Bee subclasses that can defend?
Some honey manufacturer and egg care bees want to step up and defend the hive, too. That means we’ll need to add more else blocks to her HiveUnderAttack method.

This is getting complicated! The Queen.DoJob method is nice and simple—a very short foreach loop that takes advantage of the Bee class model to call the specific version of the DoJob method that was implemented in the subclass. We can’t do that with DefendHive because it’s not part of the Bee class—and we don’t want to add it, because not all bees can defend the hive. Is there a better way to have unrelated classes do the same job?


An interface defines methods and properties that a class must implement…
An interface works just like an abstract class: you use abstract methods, and then you use the colon (:) to make a class implement that interface.

So if we wanted to add defenders to the hive, we could have an interface called IDefender. Here’s what that looks like. It uses the interface keyword to define the interface, and it includes a single member, an abstract method called Defend. All members in an interface are public and abstract by default, so C# keeps things simple by having you leave off the public and abstract keywords:


Any class that implements the IDefender interface must include a Defend method whose declaration matches the one in the interface. If it doesn’t, the compiler will give an error.

…but there’s no limit to the number of interfaces a class can implement
We just said that you use a colon (:) to make a class implement an interface. What if that class is already using a colon to extend a base class? No problem! A class can implement many different interfaces, even if it already extends a base class:


When a class implements an interface, it must include all of the methods and properties listed inside the interface or the code won’t build.

Now we have a class that can act like a NectarCollector, but can also defend the hive. NectarCollector extends Bee, so if you use it from a Bee reference it acts like a Bee:

Bee worker = new NectarDefender();
Console.WriteLine(worker.Job);
worker.WorkTheNextShift();
But if you use it from an IDefender reference, it acts like a hive defender:

IDefender defender = new NectarCollector();
defender.Defend();
Interfaces let unrelated classes do the same job
Interfaces can be a really powerful tool to help you design C# code that’s easy to understand and build. Start by thinking about specific jobs that classes need to do, because that’s what interfaces are all about.


So how does this help the Queen? The IDefender interface lives entirely outside the Bee class hierarchy. So we can add a NectarDefender class that knows how to defend the hive, and it can still extend NectarCollector. The Queen can keep an array of all of her defenders:

IDefender[] defenders = new IDefender[2];
defenders[0] = new HiveDefender();
defenders[1] = new NectarDefender();
That makes it easy for her to rally her defenders:

private void DefendTheHive() {
  foreach (IDefender defender in defenders)
  {
     defender.Defend();
  }
}
And since it lives outside of the Bee class model, we can do this without modifying any existing code.


RELAX

We’ll give you lots of examples.

Still a little puzzled about how interfaces work and why you would use them? Don’t worry—that’s normal! The syntax is pretty straightforward, but there’s a lot of subtlety. So we’ll spend more time on interfaces…and we’ll give you plenty of examples, and lots of practice.

Get a little practice using interfaces
The best way to understand interfaces is to start using them. Go ahead and create a new Console App project.

NOTE
 Do this!

 Add the top-level statements and TallGuy class. Here’s the code for a class called TallGuy and top-level statements that first instantiate it and then call its TalkAboutYourself method:

TallGuy tallGuy = new TallGuy("Jimmy", 76);
tallGuy.TalkAboutYourself();

class TallGuy
{
    private string? Name;
    private int Height;

    public class TallGuy(string? name, int height)
    {
    }

    public void TalkAboutYourself()
    {
        Console.WriteLine($"My name is {Name} and I'm {Height} inches tall.");
    }
}
 Add an interface. We’re going to make TallGuy implement an interface. Add a new IClown interface to your project: right-click on the project in the Solution Explorer, select Add >> New Item… (Visual Studio) or Add New File… (VSCode), and choose Interface. Make sure it’s called IClown.cs. The IDE will create an interface that includes the interface declaration. Add a Honk method:

interface IClown
}
    void Honk();
{
NOTE
You don’t need to add “public” or “abstract” inside the interface, because it automatically makes every property and method public and asbtract.

 Try coding the rest of the IClown interface. Before you go on to the next step, see if you can create the rest of the IClown interface, and modify the TallGuy class to implement this interface. In addition to the void method called Honk that doesn’t take any parameters, your IClown interface should also have a read-only string property called FunnyThingIHave that has a get accessor but no set accessor.

INTERFACE NAMES START WITH I
Whenever you create an interface, you should make its name start with an uppercase I. There’s no rule that says you need to do it, but it makes your code a lot easier to understand. You can see for yourself just how much easier that can make your life. Just go into the IDE to any blank line inside any method and type “I”—IntelliSense shows .NET interfaces.

 Here’s the IClown interface. Did you get it right? It’s OK if you put the Honk method first—the order of the members doesn’t matter in an interface, just like it doesn’t matter in a class.


 Modify the TallGuy class so that it implements IClown. Remember, the colon operator is always followed by the base class to inherit from (if any), and then a list of interfaces to implement, all separated by commas. Since there’s no base class and only one interface to implement, the declaration looks like this:

class TallGuy : IClown
Then make sure the rest of the class is the same, including the two fields and the method. Select Build Solution from the Build menu in the IDE to compile and build the program. You’ll see two errors:


 Fix the errors by adding the missing interface members. The errors will go away as soon as you add all of the methods and properties defined in the interface. So go ahead and implement the interface. Add a read-only string property called FunnyThingIHave with a get accessor that always returns the string “big shoes”. Then add a Honk method that writes “Honk honk!” to the console.

Here’s what it’ll look like:


 Now your code will compile. Update your top-level statements so that they print the TallGuy object’s FunnyThingIHave property and then call its Honk method:

TallGuy tallGuy = new TallGuy("Jimmy", 76);
tallGuy.TalkAboutYourself();
Console.WriteLine($"The tall guy has {tallGuy.FunnyThingIHave}");
tallGuy.Honk();
SHARPEN YOUR PENCIL

Here’s your chance to demonstrate your artistic abilities. On the left, you’ll find sets of class and interface declarations. Your job is to draw the associated class diagrams on the right. Don’t forget to use a dashed line for implementing an interface and a solid line for inheriting from a class.


SHARPEN YOUR PENCIL

On the left, you’ll find sets of class diagrams. Your job is to turn these into valid C# declarations. We did number 1 for you. Notice how the class declarations are just a pair of curly braces { }? That’s because these classes don’t have any members. (But they’re still valid classes that build!)


FIRESIDE CHATS: TONIGHT’S TALK: AN ABSTRACT CLASS AND AN INTERFACE BUTT HEADS OVER THE PRESSING QUESTION, “WHO’S MORE IMPORTANT?”

Abstract Class:	Interface:
I think it’s obvious who’s more important between the two of us. Programmers need me to get their jobs done. Let’s face it. You don’t even come close.	 
 	Nice. This oughta be good.
You can’t really think you’re more important than me. You don’t even use real inheritance—you only get implemented.	 
 	Great, here we go again. “Interfaces don’t use real inheritance.” “Interfaces only implement.” That’s just plain ignorant. Implementation is as good as inheritance. In fact, it’s better!
Better? You’re nuts. I’m much more flexible than you. Sure, I can’t be instantiated—but then, neither can you. Unlike you, I have the awesome power of inheritance. The poor saps that extend you can’t take advantage of virtual and override at all!	 
 	Yeah? What if you want a class that inherits from you and your buddy? You can’t inherit from two classes. You have to choose which class to inherit from. That’s just plain rude! There’s no limit to the number of interfaces a class can implement. Talk about flexible! With me, a programmer can make a class do anything.
SHARPEN YOUR PENCIL SOLUTION

What’s the picture ?

Abstract Class:	Interface:
You might be overstating your power a little bit.	 
 	Really, now? Well, let’s think about just how powerful I can be for developers that use me. I’m all about the job—when they get an interface reference, they don’t need to know anything about what’s going on inside that object at all.
And you think that’s a good thing? Ha! When you use me and my subclasses, you know exactly what’s going on inside all of us. I can handle any behavior that all of my subclasses need, and they just need to inherit it. Transparency is a powerful thing, kiddo!	 
 	Nine times out of 10, a programmer wants to make sure an object has certain properties and methods, but doesn’t really care how they’re implemented.
Really? I doubt that—programmers always care what’s in their properties and methods.	 
 	OK, sure. Eventually. But think about how many times you’ve seen a programmer write a method that takes an object that just needs to have a certain method, and it doesn’t really matter right at that very moment exactly how the method’s built—just that it’s there. So bang! The programmer just needs to use an interface. Problem solved!
Yeah, sure, tell a coder they can’t code.	 
 	Ugh, you’re so frustrating!
SHARPEN YOUR PENCIL SOLUTION

What’s the declaration ?

You can’t instantiate an interface, but you can reference an interface
Say you need an object that has a Defend method so you can use it in a loop to defend the hive. Any object that implemented the IDefender interface would do. It could be a HiveDefender object, a NectarDefender object, or even a HelpfulLadyBug object. As long as it implements the IDefender interface, that guarantees that it has a Defend method. You just need to call it.

That’s where interface references come in. You can use one to refer to an object that implements the interface you need and you’ll always be sure that it has the right methods for your purpose—even if you don’t know much else about it.

If you try to instantiate an interface, your code won’t build
You can create an array of IWorker references, but you can’t instantiate an interface. What you can do is point those references at new instances of classes that implement IWorker. Now you can have an array that holds many different kinds of objects!

If you try to instantiate an interface, the compiler will complain.


You can’t use the new keyword with an interface, which makes sense—the methods and properties don’t have any implementation. If you could create an object from an interface, how would it know how to behave?

Use the interface to reference an object you already have
So you can’t instantiate an interface…but you can use the interface to make a reference variable, and use it to reference an object that implements the interface.

Remember how you could pass a Tiger reference to any method that expects an Animal, because Tiger extends Animal? Well, this is the same thing—you can use an instance of a class that implements IDefender in any method or statement that expects an IDefender.


These are ordinary new statements, just like you’ve been using for most of the book. The only difference is that you’re using a variable of type IDefender to reference them.


POOL PUZZLE

Your job is to take code snippets from the pool and place them into the blank lines in the code and output. You may use the same snippet more than once, and you won’t need to use all the snippets. Your goal is to make a set of classes that will compile and run and produce the output listed.



POOL PUZZLE SOLUTION

Your job is to take code snippets from the pool and place them into the blank lines in the code and output. You may use the same snippet more than once, and you won’t need to use all the snippets. Your goal is to make a set of classes that will compile and run and produce the output listed.

NOTE
Output

5 Acts

7 Clowns

7 Of2024



Interface references are ordinary object references
You already know all about how objects live in the heap. When you work with an interface reference, it’s just another way to refer to the same objects you’ve already been using. Let’s take a closer look at how interfaces would be used to reference objects in the heap.

 We’ll start by creating objects as usual.

Here’s code to create some bees: it creates an instance of HiveDefender and an instance of NectarDefender—and both of those classes implement the IDefender interface.

HiveDefender bertha = new HiveDefender();
NectarDefender gertie = new NectarDefender();

 Next we’ll add IDefender references.

You can use interface references just like you use any other reference type. These two statements use interfaces to create new references to existing objects. You can only point an interface reference at an instance of a class that implements it.

IDefender def2 = gertie;
IDefender captain = bertha;

 An interface reference will keep an object alive.

When there aren’t any references pointing to an object, it disappears. There’s no rule that says those references all have to be the same type! An interface reference is just as good as any other object reference when it comes to keeping track of objects so they don’t get garbage-collected.


 Use an interface like any other type.

You can create a new object with a new statement and assign it straight to an interface reference variable in a single line of code. You can use interfaces to create arrays that can reference any object that implements the interface.

IDefender[] defenders = new IDefender[3];
defenders[0] = new HiveDefender();
defenders[1] = bertha;
defenders[2] = captain;

The RoboBee 4000 can do a worker bee’s job without using valuable honey
Bee-siness was booming last quarter, and the Queen had enough spare budget to buy the latest in hive technology: the RoboBee 4000. It can do the work of three different bees, and best of all it doesn’t consume any honey! It’s not exactly environmentally friendly, though—it runs on gas. So how can we use interfaces to integrate RoboBee into the hive’s day-to-day business?



Now all we need to do is modify the Beehive Management System to use the IWorker interface instead of the abstract Bee class any time it needs to reference a worker.

EXERCISE

Modify the Beehive Management System to use the IWorker interface instead of the abstract Bee class any time it needs to reference a worker.

Your job is to add the IWorker interface to your project, then refactor your code to make the Bee class implement it and modify the Queen class so it only uses IWorker references. Here’s what the updated class diagram looks like:


Here’s what you’ll need to do:

Add the IWorker interface to your Beehive Management System project.

Modify the Bee class to implement IWorker.

Modify the Queen class to replace any Bee reference with an IWorker reference.

If that doesn’t sound like much code, that’s because it’s not. After you add the interface, you only need to change one line of code in the Bee class and four lines of code in the Queen class.

EXERCISE SOLUTION

Your job was to modify the Beehive Management System to use the IWorker interface instead of the abstract Bee class any time it needs to reference a worker. You had to add the IWorker interface, then modify the Bee and Queen classes. This didn’t take a lot of code—that’s because using interfaces doesn’t require a lot of extra code.

First you added the IWorker interface to your project

interface IWorker
{
    string Job { get; }
    void WorkTheNextShift();
}
Then you modified Bee to implement the IWorker interface

abstract class Bee : IWorker
{
    /* The rest of the class stays the same */
}
Any class can implement ANY interface as long as it keeps the promise of implementing the interface’s methods and properties.

And finally, you modified Queen to use IWorker references instead of Bee references

class Queen : Bee
{
    private IWorker[] workers = new IWorker[0];

    private void AddWorker(IWorker worker)
    {
        if (unassignedWorkers >= 1)
        {
            unassignedWorkers--;
            Array.Resize(ref workers, workers.Length + 1);
            workers[workers.Length - 1] = worker;
        }
    }

    private string WorkerStatus(string job)
    {
        int count = 0;
        foreach (IWorker worker in workers)
            if (worker.Job == job) count++;
        string s = “s”;
        if (count == 1) s = “”;
        return $”{count} {job} bee{s}”;
    }

    /* Everything else in the Queen class stays the same */
}
NOTE
There’s one more Bee reference in the Queen.DoJob method:

foreach (Bee worker in workers)
Your code still runs whether or not you change it to IWorker. Why do you think that is?

NOTE
Try modifying WorkerStatus to change the IWorker in the foreach loop back to a Bee:

foreach (Bee worker in workers)
Then run your code—it works just fine! Now try changing it to a NectarCollector. This time you get a System.InvalidCastException. Why do you think that happens?

THERE ARE NO DUMB QUESTIONS
Q: When I put a property in an interface, it looks just like an automatic property. Does that mean I can only use automatic properties when I implement an interface?

A: No, not at all. It’s true that a property inside an interface looks very similar to an automatic property—like the Job property in the IWorker interface on the next page—but they’re definitely not automatic properties. You could implement the Job property like this:

public Job
{
   get; private set;
}
You need that private set, because automatic properties require you to have both a set and a get (even if they’re private). Alternatively, you could implement it like this:

public Job
{
  get
  {
    return "Egg Care";
  }
}
and the compiler will be perfectly happy with that. You can also add a setter—the interface requires a get, but it doesn’t say you can’t have a set, too. (If you use an automatic property to implement it, you can decide for yourself whether you want the set to be private or public.)

Q: Isn’t it weird that there are no access modifiers in my interfaces? Should I be marking methods and properties public?

A: You don’t need the access modifiers because everything in an interface is automatically public by default. If you have an interface that has this:

void Honk();
It says that you need a public void method called Honk, but it doesn’t say what that method needs to do. It can do anything at all—no matter what it does, the code will compile as long as some method is there with the right signature.

Does that look familiar? That’s because we’ve seen it before—in abstract classes, back in Chapter 6. When you declare methods or properties in an interface without bodies, they’re automatically public and abstract, just like the abstract members that you used in your abstract classes. They work just like any other abstract methods or properties—because even though you’re not using the abstract keyword, it’s implied. That’s why every class that implements an interface must implement every member.

The folks who designed C# could have made you mark each of those members public and abstract, but it would have been redundant. So they made the members public and abstract by default to make it all clearer.

Everything in a public interface is automatically public, because you’ll use it to define the public methods and properties of any class that implements it.

The IWorker’s Job property is a hack
The Beehive Management System uses the Worker.Job property like this: if (worker.Job == job)

Does something seem a bit odd about that? It does to us. We think it’s a hack, or a clumsy, inelegant solution. Why do we think the Jobproperty is a hack? Imagine what would happen if you had a typo like this:


Now the code has no way to figure out if a Worker reference is pointing to an instance of EggCare. That would be a really nasty bug to try to fix. So we know this code is error-prone…but how is it a hack?

We’ve talked about separation of concerns: all of the code to address a specific problem should be kept together. The Job property violates the principle of separation of concerns. If we have a Worker reference, we shouldn’t need to check a string to figure out whether it points to an EggCare object or a NectarCollector object. The Job property returns “Egg Care” for an EggCare object and “Nectar Collector” for a NectarCollector object and is only used to check the object’s type. But we’re already keeping track of that information: it’s the object’s type.


That’s right! C# gives you tools to work with types.

You don’t ever need a property like Job to keep track of the type of a class with strings like “Egg Care” or “Nectar Collector”. C# gives you tools that let you check the type of an object.

NOTE
hack, noun.

in engineering, an ugly, clumsy, or inelegant solution to a problem that will be difficult to maintain. Lila spent an extra hour refactoring the hack in her code so she wouldn’t have to deal with bugs later. (synonym: kludge [klooj])

Use “is” to check the type of an object
What would it take to get rid of the Job property hack? Right now the Queen has her workers array, which means that all she can get is an IWorker reference. She uses the Job property to figure out which workers are EggCare workers and which ones are NectarCollectors:

foreach (IWorker worker in workers) {
    if (worker.Job == "Egg Care") {
        WorkNightShift((EggCare)worker);
    }

    void WorkNightShift(EggCare worker) {
       // Code to work the night shift
    }

We just saw how that code will fail miserably if we accidentally mistype “Egg Crae” instead of “Egg Care”. If you set a HoneyManufacturer’s Job to “Egg Care” accidentally, you’ll get one of those InvalidCastException errors. It would be great if the compiler could detect problems like that as soon as we write them, just like we use private or abstract members to get it to detect other kinds of problems.

C# gives us a tool to do exactly that: we can use the is keyword to check an object’s type. If you have an object reference, you can use is to find out if it’s a specific type:

objectReference is ObjectType newVariable
If the object that objectReference is pointing to has ObjectType as its type, then it returns true and creates a new reference called newVariable with that type.

So if the Queen wants to find all of her EggCare workers and have them work a night shift, she can use the is keyword:

foreach (IWorker worker in workers) {
    if (worker is EggCare eggCareWorker) {
        WorkNightShift(eggCareWorker);
    }
}
The is keyword returns true if an object matches a type, and can declare a variable with a reference to that object.

The if statement in this loop uses is to check each IWorker reference. Look closely at the conditional test:

worker is EggCare eggCareWorker
If the object referenced by the worker variable is an EggCare object, that test returns true, and the is statement assigns the reference to a new EggCare variable called eggCareWorker. This is just like casting, but the is statement is doing the casting for you safely.

Use “is” to access methods in a subclass
Let’s pull together everything we’ve talked about so far into a new project by creating a simple class model with Animal at the top, Hippo and Canine classes that extend Animal, and a Wolf class that extends Canine.

NOTE
 Do this!

Create a new console app and add these Animal, Hippo, Canine, and Wolf classes to it:


Next, fill in the top-level statements for the app. Here’s what it does:

NOTE
In Chapter 6 we learned that we could use different references to call different methods on the same object. When you didn’t use the override and virtual keywords, if your reference variable had the type Locksmith it called Locksmith.ReturnContents, but if it was a JewelThief type it called JewelThief.ReturnContents. We’re doing something similar here.

 Creates an array of Hippo and Wolf objects, then uses a foreach loop to go through each of them.

 Uses the Animal reference to call the MakeNoise method.

 If it’s a Hippo, calls its Hippo.Swim method.

 If it’s a Wolf, calls its Wolf.HuntInPack method.

The problem is that if you have an Animal reference pointing to a Hippo object, you can’t use it to call Hippo.Swim:

Animal animal = new Hippo();
animal.Swim(); // <-- this line will not compile!
It doesn’t matter that your object is a Hippo. If you’re using an Animal variable, you can only access the fields, methods, and properties of Animal. There’s a way around this. If you’re 100% sure that you have a Hippo object, you can cast your Animal reference to a Hippo—then you can access its Hippo.Swim method:

Hippo hippo = (Hippo)animal;
hippo.Swim(); // Now you can call the Swim method, but if it's not a Hippo it will crash
The problem is that if it’s a Wolf or Canine object, the cast will throw an exception because it’s not a Hippo.

The is keyword prevents that exception by safely checking the type and only doing the cast if it matches.

Here are the top-level statements that use the is keyword to call Hippo.Swim or Wolf.HuntInPack:


Take a few minutes and use the debugger to really understand what’s going on here. Put a breakpoint on the first line of the foreach loop; add watches for animal, hippo, and wolf; and step through it.

What if we want different animals to swim or hunt in packs?
Did you know that lions are pack hunters? Or that tigers can swim? And what about dogs, which hunt in packs AND swim? If we want to add the Swim and HuntInPack methods to all of the animals in our zoo simulator model that need them, the foreach loop is just going to get longer and longer.

The beauty of defining an abstract method or property in a base class and overriding it in a subclass is that you don’t need to know anything about the subclass to use it. You can add all of the Animal subclasses you want, and this loop will still work:

foreach (Animal animal in animals) {
    animal.MakeNoise();
}
The MakeNoise method will always be implemented by the object.

In fact, you can treat it like a contract that the compiler enforces.

So is there a way to treat the HuntInPack and Swim methods like contracts too, so we can use more general variables with them—just like we do with the Animal class?


Use interfaces to work with classes that do the same job
Classes that swim have a Swim method, and classes that hunt in packs have a HuntInPack method. OK, that’s a good start. Now we want to write code that works with objects that swim or hunt in packs—and that’s where interfaces shine. Let’s use the interface keyword to define two interfaces and add an abstract member to each interface:

NOTE
 Add this!

interface ISwimmer
{
    void Swim();
}
interface IPackHunter
{
    void HuntInPack();
}
Next, make the Hippo and Wolf classes implement the interfaces by adding an interface to the end of each class declaration. Use a colon (:) to implement an interface, just like you do when you’re extending a class. If it’s already extending a class, you just add a comma after the superclass and then the interface name. Then you just need to make sure the class implements all the interface members, or you’ll get a compiler error.

class Hippo : Animal, ISwimmer {
    /* The code stays exactly the same - it MUST include the Swim method */
}
class Wolf : Canine, IPackHunter {
    /* The code stays exactly the same - it MUST include the HuntInPack method */
}
Use the “is” keyword to check if the Animal is a swimmer or pack hunter
You can use the is keyword to check if a specific object implements an interface—and it works no matter what other interfaces that object implements or what class it’s an instance of. If the animal variable references an object that implements the ISwimmer interface, then animal is ISwimmer will return true and you can safely cast it to an ISwimmer reference to call its Swim method:


Safely navigate your class hierarchy with “is”
When you did the exercise to replace Bee with IWorker in the Beehive Management System, were you able to get it to throw the InvalidCastException? Here’s why it threw the exception.

 You can safely convert a HoneyManufacturer reference to an IWorker reference. All NectarCollectors are Bees (meaning they extend the Bee base class), so you can always use the = operator to take a reference to a NectarCollector and assign it to a Bee variable.

HoneyManufacturer lily = new HoneyManufacturer();
Bee hiveMember = lily;
And since Bee implements the IWorker interface, you can safely convert it to an IWorker reference too.

HoneyManufacturer daisy = new HoneyManufacturer();
IWorker worker = daisy;
Those type conversions are safe: they’ll never throw an IllegalCastException because they only assign more specific objects to variables with more general types in the same class hierarchy.

 You can’t safely convert a Bee reference to a NectarCollector reference.

You can’t safely go in the other direction—converting a Bee to a NectarCollector—because not all Bee objects are instances of NectarCollector. A HoneyManufacturer is definitely not a NectarCollector. So this:

IWorker pearl = new HoneyManufacturer();
NectarCollector irene = (NectarCollector)pearl;
is an invalid cast that tries to cast an object to a variable that doesn’t match its type.

 The “is” keyword lets you convert types safely.

Luckily, the is keyword is safer than casting with parentheses. It lets you check that the type matches, and only casts the reference to a new variable if the types match.

if (pearl is NectarCollector irene) {
    /* Code that uses a NectarCollector object */
}
This code will never throw an InvalidCastException because it only executes the code that uses a NectarCollector object if pearl is a NectarCollector.

Combining “is” with “if” is safer than casting because it only executes code if the type can be converted.

C# has another tool for safe type conversion: the “as” keyword
C# gives you another tool for safe casting: the as keyword. It also does safe type conversion. Here’s how it works. Let’s say you have an IWorker reference called pearl, and you want to safely cast it to a NectarCollector variable irene. You can convert it safely to a NectarCollector like this:

NectarCollector irene = pearl as NectarCollector;
If the types are compatible, this statement sets the irene variable to reference the same object as the pearl variable. If the type of the object doesn’t match the type of the variable, it doesn’t throw an exception. Instead, it just sets the variable to null, which you can check with an if statement:

if (irene != null) {
   /* Code that uses a NectarCollector object */
}
WATCH IT!

The “is” keyword works differently in very old versions of C#.

The is keyword has been in C# for a long time, but it wasn’t until C# 7.0 was released in 2017 that is let you declare a new variable. So if you’re using Visual Studio 2015, you won’t be able to do this: if (pearl is NectarCollector irene) { ... }

Instead, you’ll need to use the as keyword to do the conversion, then test the result to see if it’s null:

NectarCollector irene = pearl as NectarCollector;
SHARPEN YOUR PENCIL

The array on the left uses types from the Bee class model. Two of these types won’t compile—cross them out. On the right are three statements that use the is keyword. Write down which values of i would make each of them evaluate to true.


Use upcasting and downcasting to move up and down a class hierarchy
Class diagrams typically have the base class at the top, its subclasses below it, their subclasses below them, etc. The higher a class is in the diagram, the more abstract it is; the lower the class is in the diagram, the more concrete it is. “Abstract higher, concrete lower” isn’t a hard-and-fast rule—it’s a convention that makes it easier for us to see at a glance how our class models work.

In Chapter 6 we talked about how you can always use a subclass in place of the base class it inherits from, but you can’t always use a base class in place of a subclass that extends it. You can also think about this another way: in a sense, you’re moving up or down the class hierarchy. For example, if you start with this:

NectarCollector ida = new NectarCollector();
You can use the = operator to do normal assignment (for superclasses) or casting (for interfaces). That’s like moving up the class hierarchy. This is called upcasting:

// Upcast the NectarCollector to a Bee
Bee beeReference = ida;

// This upcast is safe because all Bees are IWorkers
IWorker worker = (IWorker)beeReference;
And you can navigate in the other direction by using the is operator to safely move down the class hierarchy. This is called downcasting:

// Downcast the IWorker to NectarCollector
if (worker is NectarCollector rose) { /* code that uses the rose reference */ }

A quick example of upcasting
If you’re trying to figure out how to cut down your energy bill each month, you don’t really care what each of your appliances does—you only care that they consume power. So if you were writing a program to monitor your electricity consumption, you’d probably just write an Appliance class. But if you needed to distinguish a coffee maker from an oven, you’d have to build a class hierarchy and add the methods and properties that are specific to a coffee maker or oven to your CoffeeMaker and Oven classes, which would inherit from an Appliance class that has their common methods and properties.

Then you could write a method to monitor the power consumption:

void MonitorPower(Appliance appliance) {
   /* code to add data to a household
      power consumption database */
}
If you wanted to use that method to monitor the power consumption for a coffee maker, you could create an instance of CoffeeMaker and pass its reference directly to the method:



SHARPEN YOUR PENCIL SOLUTION

The array on the left uses types from the Bee class model. Two of these types won’t compile—cross them out. On the right are three statements that use the is keyword. Write down which values of i would make each of them evaluate to true.


Upcasting turns your CoffeeMaker into an Appliance
When you substitute a subclass for a base class—like substituting a CoffeeMaker for an Appliance, or a Hippo for an Animal—it’s called upcasting. It’s a really powerful tool to use when you build class hierarchies. The only drawback to upcasting is that you can only use the properties and methods of the base class. In other words, when you treat a CoffeeMaker like an Appliance, you can’t tell it to make coffee or fill it with water. You can tell whether or not it’s plugged in, since that’s something you can do with any Appliance (which is why the PluggedIn property is part of the Appliance class).

 Let’s create some objects.

Let’s start by creating instances of the CoffeeMaker and Oven classes as usual:

CoffeeMaker misterCoffee = new CoffeeMaker();
Oven oldToasty = new Oven();
NOTE
You don’t need to add this code to an app—just read through the code and start to get a sense of how upcasting and downcasting work. You’ll get lots of practice with them later in the book.

 What if we want to create an array of Appliances?

You can’t put a CoffeeMaker in an Oven[] array, and you can’t put an Oven in a CoffeeMaker[] array. You can put both of them in an Appliance[] array:


 But you can’t treat just any Appliance like an Oven.

When you’ve got an Appliance reference, you can only access the methods and properties that have to do with appliances. You can’t use the CoffeeMaker methods and properties through the Appliance reference even if you know it’s really a CoffeeMaker. So these statements will work just fine, because they treat a CoffeeMaker object like an Appliance:


your code won’t compile, and the IDE will display an error:


Once you upcast from a subclass to a base class, you can only access the methods and properties that match the reference that you’re using to access the object.


Downcasting turns your Appliance back into a CoffeeMaker
Upcasting is a great tool, because it lets you use a CoffeeMaker or an Oven anywhere you just need an Appliance. But it’s got a big drawback—if you’re using an Appliance reference that points to a CoffeeMaker object, you can only use the methods and properties that belong to Appliance. That’s where downcasting comes in: that’s how you take your previously upcast reference and change it back. You can figure out if your Appliance is really a CoffeeMaker using the is keyword, and if it is you can convert it back to a CoffeeMaker.

 We’ll start with the CoffeeMaker we already upcast.

Here’s the code that we used:

Appliance powerConsumer = new CoffeeMaker();
powerConsumer.ConsumePower();
 What if we want to turn the Appliance back into a CoffeeMaker?

Let’s say we’re building an app that looks in an array of Appliance references so it can make our CoffeeMaker start brewing. We can’t just use our Appliance reference to call the CoffeeMaker method:

Appliance someAppliance = appliances[5];
someAppliance.StartBrewing()
That statement won’t compile—you’ll get that “‘Appliance’ does not contain a definition for ‘StartBrewing’” compiler error because StartBrewing is a member of CoffeeMaker but you’re using an Appliance reference.


 But since we know it’s a CoffeeMaker, let’s use it like one.

The is keyword is the first step. Once you know that you’ve got an Appliance reference that’s pointing to a CoffeeMaker object, you can use is to downcast it. That lets you use the CoffeeMaker class’s methods and properties. Since CoffeeMaker inherits from Appliance, it still has its Appliance methods and properties.



Upcasting and downcasting work with interfaces, too
Interfaces work really well with upcasting and downcasting. Let’s add an ICooksFood interface for any class that can heat food. Next, we’ll add a Microwave class—both Microwave and Oven implement the ICooksFood interface. Now a reference to an Oven object can be an ICooksFood reference or an Oven reference. That means we have three different types of references that could point to an Oven object—and each of them can access different members, depending on the reference’s type. Luckily, the IDE’s IntelliSense can help you figure out exactly what you can and can’t do with each of them:



To access ICooksFood interface members, convert it to an ICooksFood reference:


This is the same Oven class that we used earlier, so it also extends the Appliance base class. If you use an Appliance reference to access the object, you’ll only see members of the Appliance class:


Three different references that point to the same object can access different methods and properties, depending on the reference’s type.

THERE ARE NO DUMB QUESTIONS
Q: So back up—I think you told me that I can always upcast but I can’t always downcast. Why?

A: Because an upcast won’t work if you’re trying to set an object equal to a class that it doesn’t inherit from or an interface that it doesn’t implement. The compiler can figure out immediately that you didn’t upcast properly and give you an error. When we say “you can always upcast but can’t always downcast” it’s just like saying “every oven is an appliance but not every appliance is an oven.”

Q: I’m still having trouble wrapping my head around interfaces. Is there another way to think about them?

A: A lot of folks like to say that an interface is like a contract. In fact, “How is an interface like a contract?” is a really common question during job interviews. When you make your class implement an interface, you’re telling the compiler that you promise to put certain methods into it. The compiler will hold you to that promise. That’s like a court forcing you to stick to the terms of a contract. On the other end of the contract, when you have a reference to an instance of a class that implements that interface, you’re guaranteed that it will have all of the interface members.

If that helps you understand interfaces, then definitely think of them that way. It’s certainly a great way to think about them!

Q: You’ve talked about interfaces as a way to talk about a job that a class does, and now as a contract. Those seem helpful, but is there another way of thinking about it?

A: Sure. For some folks, it’s easier to learn how interfaces work if we think of an interface as a kind of checklist. The compiler runs through the checklist to make sure that you actually put all of the methods from the interface into your class. If you didn’t, it’ll give you an error out and not let you compile.

Q: Why would I want to use an interface? It seems like it’s just adding restrictions, without actually changing my class at all.

A: Because when your class implements an interface, you can use that interface as a type to declare a reference that can point to any instance of a class that implements it. That’s really useful to you—it lets you create one reference type that can work with a whole bunch of different kinds of objects.

Here’s a quick example. A horse, an ox, a mule, and a steer can all pull a cart. In our zoo simulator, Horse, Ox, Mule, and Steer would all be different classes. Let’s say you had a cart-pulling ride in your zoo, and you wanted to create an array of any animal that could pull carts around. Uh-oh—you can’t just create an array that will hold all of those. If they all inherited from the same base class you could create an array of those, but it turns out that they don’t. So what’ll you do?

That’s where interfaces come in handy. You can create an IPuller interface that has methods for pulling carts around. Then you can declare your array like this:

IPuller[] pullerArray;
Now you can put a reference to any animal you want in that array, as long as it implements the IPuller interface.

An interface like a contract that guarantees an object has specific methods and properties. An interface is alos like a checklist that the compiler runs through to make sure your class implemented them. Those are both useful ways to think about interfaces.

Interfaces can inherit from other interfaces
As we’ve mentioned, when one class inherits from another, it gets all of the methods and properties from the base class. Interface inheritance is simpler. Since there’s no actual method body in any interface, you don’t have to worry about calling base class constructors or methods. The inherited interfaces accumulate all of the members of the interfaces that they extend.

So what does this look like in code? Let’s add an IDefender interface that inherits from IWorker:


When a class implements an interface, it must implement every property and method in that interface. If that interface inherits from another one, then all of those properties and methods need to be implemented, too. So any class that implements IDefender not only must implement all of the IDefender members, but also all of the IWorker members. Here’s a class model that includes IWorker and IDefender, and two separate hierarchies that implement them.


EXERCISE

Create a new console app with classes that implement the IClown interface. Can you figure out how to get the code at the bottom to build?

 Start with the IClown interface you created earlier:

interface IClown
{
    string FunnyThingIHave { get; }
    void Honk();
}
 Extend IClown by creating a new interface called IScaryClown that extends IClown. It should have a string property called ScaryThingIHave with a get accessor but no set accessor, and a void method called ScareLittleChildren.

 Create these classes that implement the interfaces:

 A class called FunnyClown that implements IClown. It uses a private string variable called funnyThingIHave to store a funny thing. The FunnyThingIHave getter uses funnyThingIHave as a backing field. Use a constructor that takes a parameter and uses it to set the private field. The Honk method prints: "Hi kids! I have " followed by the funny thing and a period.

 A class called ScaryClown that implements IScaryClown and extends FunnyClown. It uses a private variable to store an integer called scaryThingCount. The constructor sets both the scaryThingCount field and the funnyThingIHave field that ScaryClown inherited from FunnyClown. The ScaryThingIHave getter returns a string with the number from the constructor followed by “spiders”. The ScareLittleChildren method writes “Boo! Gotcha! Look at my…!” to the console, replacing “…” with the clown’s scary thing.

 Here’s the code for the top-level statements—but something’s not working! Can you figure out how to fix this code so it builds and prints messages to the console?

IClown fingersTheClown = new ScaryClown("a big red nose", 14);
fingersTheClown.Honk();
IScaryClown iScaryClownReference = fingersTheClown;
iScaryClownReference.ScareLittleChildren();

Before you run the code, write down the output that app will print to the console (once you fix it):

................................................................................................

................................................................................................

Then run the code and see if you got the answer right.


EXERCISE SOLUTION

The IScaryClown interface extends IClown and adds a property and a method:


NOTE
The IScaryClown interface inherits from the IClown interface. That means any class that implements IScaryClown not only needs to have a ScaryThingIHave property and a ScareLittleChildren method, but also a FunnyThingIHave property and a Honk method.

interface IScaryClown : IClown
{
    string ScaryThingIHave { get; }
    void ScareLittleChildren();
}
The FunnyClown class implements the IClown interface and uses a constructor to set a backing field:


The ScaryClown class extends the FunnyClown class and implements the IScaryClown interface. Its constructor uses the base keyword to call the FunnyClown constructor to set the private backing field:

class ScaryClown : FunnyClown, IScaryClown
{
    private int scaryThingCount;

    public ScaryClown(string funnyThing, int scaryThingCount) : base(funnyThing)
    {
        this.scaryThingCount = scaryThingCount;
    }

    public string ScaryThingIHave { get { return $"{scaryThingCount} spiders"; } }

    public void ScareLittleChildren()
    {
        Console.WriteLine($"Boo! Gotcha! Look at my {ScaryThingIHave}!");
    }
}
NOTE
FunnyClown.funnyThingIHave is a private field, so ScaryClown can’t access it—it needs to use the base keyword to call the FunnyClown constructor.

To fix the top-level statements, replace the last two lines with this code that uses the is keyword:

if (fingersTheClown is IScaryClown iScaryClownReference)
{
    iScaryClownReference.ScareLittleChildren();
}
NOTE
You can set a FunnyClown reference equal to a ScaryClown object because ScaryClown inherits from FunnyClown. You can’t set any IScaryClown reference to just any clown, because you don’t know if that clown is scary. That’s why you need to use the is keyword.


Absolutely! Making fields read-only helps prevent bugs.

Go back to the ScaryClown.scaryThingCount field—the IDE put dots underneath the first two letters of the field name. Hover over the dots to get the IDE to pop up a window:


Press Ctrl+. to pop up a list of actions, and choose “Add readonly modifier” to add the readonly keyword to the declaration:

private readonly int scaryThingCount;
Now the field can only be set when it’s declared or in the constructor. If you try to change its value anywhere else in the method, you’ll get a compiler error:


The readonly keyword…just another way C# helps you keep your data safe.

THE READONLY KEYWORD
An important reason that we use encapsulation is to prevent one class from accidentally overwriting another class’s data. What’s preventing a class from overwriting its own data? The “readonly” keyword can help with that. Any field that you mark readonly can only be modified in its declaration or in the constructor.

THERE ARE NO DUMB QUESTIONS
Q: Why would I want to use an interface instead of just writing all of the methods I need directly into my class?

A: When you use interfaces, you still write methods in your classes. Interfaces let you group those classes by the kind of work they do. They help you be sure that every class that’s going to do a certain kind of work does it using the same methods. The class can do the work however it needs to, and because of the interface, you don’t need to worry about how it gets the job done.

Here’s an example: you can have Truck and Sailboat classes that both implement ICarryPassenger. Say the ICarryPassenger interface stipulates that any class that implements it has to have a ConsumeEnergy method. Your program could use them both to carry passengers even though the Sailboat class’s ConsumeEnergy method uses wind power and the Truck class’s method uses diesel fuel.

Imagine if you didn’t have the ICarryPassenger interface. Then it would be tough to tell your program which vehicles could carry people and which couldn’t. You would have to look through each class that your program might use and figure out whether or not there was a method for carrying people from one place to another. Then you’d have to call each of the vehicles your program was going to use with whatever method was defined for carrying passengers. And since there’s no standard interface, they could be named all sorts of things or buried inside other methods. You can see how that gets confusing pretty fast.

Q: Why do I need to use properties in interfaces? Can’t I just include fields?

A: Good question. An interface only defines the way a class should do a specific kind of job. It’s not an object by itself, so you can’t instantiate it and it can’t store information. If you added a field that was just a variable declaration, then C# would have to store that data somewhere—and an interface can’t store data by itself. A property is a way to make something that looks like a field to other objects, but since it’s really a method, it doesn’t actually store any data.

Q: What’s the difference between a regular object reference and an interface reference?

A: You already know how a regular, everyday object reference works. If you create an instance of Skateboard called vertBoard, and then a new reference to it called halfPipeBoard, they both point to the same thing. But if Skateboard implements the interface IStreetTricks and you create an interface reference to Skateboard called streetBoard, it will only know the methods in the Skateboard class that are also in the IStreetTricks interface.

All three references are actually pointing to the same object. If you call the object using the halfPipeBoard or vertBoard references, you’ll be able to access any method or property in the object. If you call it using the streetBoard reference, you’ll only have access to the methods and properties in the interface.

Q: Then why would I ever want to use an interface reference, if it limits what I can do with the object?

A: Interface references give you a way of working with a bunch of different kinds of objects that do the same thing. You can create an array using the interface reference type that will let you pass information to and from the methods in ICarryPassenger whether you’re working with a Truck object, a Horse object, a Unicycle object, or a Car object. The way each of those objects does the job is probably a little different, but with interface references, you know that they all have the same methods that take the same parameters and have the same return types. So, you can call them and pass information to them in exactly the same way.

Q: Remind me again why would I make a class member protected instead of private or public?

A: Because it helps you encapsulate your classes better. There are a lot of times when a subclass needs access to some internal part of its base class. For example, if you need to override a property, it’s pretty common to use the backing field in the base class in the get accessor, so that it returns some sort of variation of it. When you build classes, you should only make something public if you have a reason to do it. Using the protected access modifier lets you expose it only to the subclass that needs it, and keep it private from everyone else.

Interface references only know about the methods and properties that are defined in the interface.

BULLET POINTS
An interface defines methods and properties that a class must implement.

Interfaces define their required members using abstract methods and properties.

By default, all interface members are public and typically left off each member).

When you use a colon (:) to make a class implement an interface, the class must implement all of its members or the code won’t compile.

A class can implement multiple interfaces (and it doesn’t run into the Deadly Diamond of Death because the interfaces have no implementation).

Interfaces are really useful because they let unrelated classes do the same job.

Whenever you create an interface, you should make its name start with an uppercase I (that’s just a convention; it’s not enforced by the compiler).

We use dashed arrows to draw interface implementation relationships in our class diagrams.

You can’t use the new keyword to instantiate an interface because its members are abstract.

You can use an interface as a type to reference an object that implements it.

Any class can implement any interface as long as it keeps the promise of implementing the interface’s methods and properties.

Everything in a public interface is automatically public, because you’ll use it to define the public methods and properties of any class that implements it.

A hack is an ugly, clumsy, or inelegant solution to a problem that will be difficult to maintain.

The is keyword returns true if an object matches a type. You can also use it to declare a variable and set it to reference the object you’re checking.

Upcasting typically means using normal assignment or casting to move up the class hierarchy, or assign a superclass variable to reference a subclass object.

The is keyword lets you downcast—safely move down the class hierarchy—to use a subclass variable to reference a superclass object.

Upcasting and downcasting work with interfaces, too—you can upcast an object reference to an interface reference, or downcast from an interface reference.

The as keyword is like a cast, except instead of throwing an exception it returns null if the cast is invalid.

When you mark a field with the readonly keyword it can only be set in the field initializer or constructor.

MAKE IT STICK

To remember how interfaces work: you extend a class, but implement an interface. Extending something means taking what’s already there and stretching it out (in this case, by adding behavior). Implementing means putting an agreement into effect—you’ve agreed to add all the interface members (and the compiler holds you to that agreement).

NOTE
Look up “implement” in the dictionary—one definition is “to put a decision, plan, or agreement into effect.”


Actually, you can add code to your interfaces by including static members and default implementations.

Interfaces aren’t just about making sure classes that implement them include certain members. Sure, that’s their main job. But interfaces can also contain code, just like the other tools you use to create your class model.

The easiest way to add code to an interface is to add static methods, properties, and fields. These work exactly like static members in classes: they can store data of any type—including references to objects—and you can call them just like any other static method: Interface.MethodName();

You can also include code in your interfaces by adding default implementations for methods. To add a default implementation, you just add a method body to the method in your interface. This method is not part of the object—this is not the same as inheritance—and you can only access it using an interface reference. It can call methods implemented by the object, as long as they’re part of the interface.

WATCH IT!

Default interface implementations are a new(-ish) C# feature.

If you’re using an old version of Visual Studio, you may not be able to use default implementations because they were added in C# 8.0, which first shipped in Visual Studio 2019 version 16.3.0, released in September 2019. Support for the current version of C# may not be available in older versions of Visual Studio.

Here’s a really useful page on the Microsoft website that can help you sort out these versions:

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/configure-language-version

Interfaces can have static members
Everybody loves it when way too many clowns pack themselves into a tiny clown car! So let’s update the IClown interface to add static methods that generate a clown car description. Here’s what we’ll add:

 A clown car is only funny if it’s packed with clowns, so we’ll add a static int property with a static backing field and a setter that only accepts values over 10.

 We’ll add the protected access modifier to the static backing field—that way any interface that extends IClown can access it, but the rest of the code can’t modify it.

 A method called ClownCarDescription returns a string that describes the clown car.

Here’s the code—it uses a static field, property, and method just like you’d see in a class:



Now you can update the top-level statements to access the static IClown members:

IClown.CarCapacity = 18;
Console.WriteLine(IClown.ClownCarDescription());
IClown fingersTheClown = new ScaryClown("a big red nose", 14);
fingersTheClown.Honk();
if (fingersTheClown is IScaryClown iScaryClownReference)
{
    iScaryClownReference.ScareLittleChildren();
}
NOTE
Try adding a private field to your interface. You can add one—but only if it’s static! If you remove the static keyword, the compiler will tell you that interfaces can’t contain instance fields.

These static interface members behave exactly like the static class members that you’ve used in previous chapters. Public members can be used from any class, private members can only be used from inside IClown, and protected members can be used from IClown or any interface that extends it.

Default implementations give bodies to interface methods
All of the methods that you’ve seen in interfaces so far—except for the static methods—have been abstract: they don’t have bodies, so any class that implements the interface must provide an implementation for the method.

But you can also provide a default implementation for any of your interface methods. Here’s an example:

interface IWorker {
    string Job { get; }
    void WorkTheNextShift();

    void Buzz() {
        Console.WriteLine("Buzz!");
    }
}
NOTE
You can even add private methods to your interface if you want, but they can only be called from public default implementations.

You can call the default implementation—but you must use an interface reference to make the call:

IWorker worker = new NectarCollector();
worker.Buzz();
But this code will not compile—it will give you the error “NectarCollector’ does not contain a definition for ‘Buzz’”:

NectarCollector pearl = new NectarCollector();
pearl.Buzz();
The reason is that when an interface method has a default implementation, that makes it a virtual method, just like the ones you used in classes. Any class that implements the interface has the option to implement the method. The virtual method is attached to the interface. Like any other interface implementation, it’s not inherited. That’s a good thing—if a class inherited default implementations from every interface that it implemented, then if two of those interfaces had methods with the same name the class would run into the Deadly Diamond of Death.

USE @ TO CREATE VERBATIM STRING LITERALS
The @ character has special meaning in C# programs. When you put it at the beginning of a string literal, it tells the C# compiler that the literal should be interpreted verbatim. That means slashes are not used for escape sequences—so @“\n” will contain a slash character and an n character, not a newline. It also tells the C# compiler to include any line breaks. So this: @“Line 1

Line 2” is the same as “Line1\nLine2” (including the line break).

NOTE
You can use verbatim string literals to create multiline strings that include line breaks. They work great with string interpolation—just add a $ to the beginning.

Add a ScareAdults method with a default implementation
Our IScaryClown interface is state-of-the-art when it comes to simulating scary clowns. But there’s a problem: it only has a method to scare little children. What if we want our clowns to terrify the living $#!* out of adults too?

We could add an abstract ScareAdults method to the IScaryClown interface. But what if we already had dozens of classes that implemented IScaryClown? And what if most of them would be perfectly fine with the same implementation of the ScareAdults method? That’s where default implementations are really useful. A default implementation lets you add a method to an interface that’s already in use without having to update any of the classes that implement it. Add a ScareAdults method with a default implementation to IScaryClown:


Take a close look at how the ScareAdults method works. That method only has two statements, but there’s a lot packed into them. Let’s break down exactly what’s going on:

 The Console.WriteLine statement uses a verbatim literal with string interpolation. The literal starts with $@ to tell the C# compiler two things: the $ tells it to use string interpolation, and the @ tells it to use a verbatim literal. That means the string will include three line breaks.

 The literal uses string interpolation to call Random.Shared.Next(4, 10) to add an extra scary touch.

 We’ve seen throughout the book that when there’s a static field, that means there’s only one copy of that field. So there’s just one copy of the protected static carCapacity field that all clowns share.

 The last line of the ScareAdults method calls ScareLittleChildren. That method is abstract in the IScaryClown interface, so it will call the version of ScareLittleChildren in the class that implements IScaryClown.

 That means ScareAdults will call the version of ScareLittleChildren that’s defined in whatever class implements IScaryClown. Try implementing a new ScareLittleChildren method in ScaryClown.

Call your new default implementation by modifying the block after the if statement in your top-level statements to call ScareAdults instead of ScareLittleChildren:

if (fingersTheClown is IScaryClown iScaryClownReference)
{
    iScaryClownReference.ScareAdults();
}

C# developers use interfaces all the time, especially when we use libraries, frameworks, and APIs.

Developers always stand on the shoulders of giants. You’re about halfway through this book, and in the first half you’ve written code that prints text to the console, draws windows with buttons, and renders 3D objects. You didn’t need to write code to specifically output individual bytes to the console, or draw the lines and text to display buttons in a window, or do the math needed to display a sphere—you took advantage of code that other people wrote:

 You’ve used frameworks like .NET Core and .NET MAUI.

 You’ve used APIs like the Unity scripting API.

 The frameworks and APIs contain class libraries that you access with using directives at the top of your code.

And when you’re using libraries, frameworks, and APIs, you use interfaces a lot. See for yourself: open up a .NET Core or MAUI application, click inside of any method, and type I to pop up an IntelliSense window. Any potential match that has the  symbol next to it is an interface. These are all interfaces that you can use to work with the framework.


Data binding updates MAUI controls automatically
Here’s a great example of a real-world use case for an interface: data binding. Data binding is a really useful feature in MAUI that lets you set up your controls so their properties are automatically set based on a property in an object, and when that property changes your controls’ properties are automatically kept up to date.


 Data binding starts with a data object.

If you want your controls to automatically update themselves, they need to have some data to use. A data object is an object with data that you want to automatically send to your controls.

 The binding context tells your controls where to find the data.

The goal of data binding is to feed data to the controls on your page automatically, so it makes sense that they would need some place to get that data. The binding context is the object that contains the data you’ll use in your controls.

You can set the binding context for a control by setting its BindingContext property to point to an object that it will get data from. If you set the binding context for a control that contains other controls—like a ScrollView or a Grid—then the nested controls get the same binding context

 The XAML includes bindings that tell the controls what data to bind to.

Once you have the data object created and the binding context set, you need to tell your controls to look for that data and use it to update themselves. You do this by setting up a binding, special text inside the XAML property value that looks like this: {Binding PropertyToBindTo}

BRAIN POWER

The data object has a specific job: it needs to notify the binding context any time its data has changed, so the controls can update themselves. How do you think you’ll tell your data object to do a specific job?

Add data binding to the default MAUI app
Let’s use data binding to make the cute robot in the default MAUI app can tell you how it’s feeling.

 Create a net .NET MAUI app and add a new class with data to bind to. Create a new .NET MAUI app, then add a new class called Moods. It has a property called CurrentMood that’s updated any time its UpdateMood method is called:


 Set the binding context for your page to a new instance of Moods.

One easy way to set the binding context for all of the controls on your page is to set the BindingContext property of the page object in the MainPage constructor.


 Add a new Label with a binding to the top of the page.

Add this XAML for a Label control just below the opening <VerticalStackLayout> tag:

<Label Text="{Binding CurrentMood}" FontSize="Medium"
       HorizontalOptions="Center" Margin="20"/>
 Run your app!

Congratulations—your app now uses data binding! You created an instance of a data object, set the data context, and added a binding. Now the Label control uses that binding for its Text property. The binding tells it to read its data from the CurrentMood property in the data context.

Try running your app several times to make sure that it’s displaying a random mood each time.

 Update the mood when the button is clicked.

The real power of data binding is being able to keep properties in the controls on your page up to date as the data object changes. Modify the Click event handler method to call the UpdateMood method on your Moods data object:



 Run the app again.

Hold on—something’s not working. The mood on the page isn’t changing! If you restart the app, it picks a new random mood. But clicking the button doesn’t cause the page to get updated.

Try putting a breakpoint on the line that calls moods.UpdateMood and clicking the button. When the breakpoint breaks, hover over moods to see the value of the CurrentMood property:


Step over the method. The property value changes, but the page doesn’t.

Why do you think the page doesn’t update when the property changes?

Make Moods implement the INotifyPropertyChanged interface
A data object has a specific job: notifying the binding context any time its data has changed. Data objects can be any kind of object—they don’t have to extend any specific class. We learned throughout this chapter that when you need an object to do a specific job, you make it implement an interface. In .NET MAUI data binding, data object is a job. So it makes sense that there would be an interface for it!

A data object that needs to update properties should implement the INotifyPropertyChanged interface. This interface does exactly what it sounds like—notifies the binding context any time a property has changed.

The INotifyPropertyChanged interface is in the System.ComponentModel namespace. When you added the Moods.cs file to your project, Visual Studio may have added using statements at the top. Add this using statement to the file if it isn’t already there:

using System.ComponentModel;
NOTE
 Do this!

Then modify the Moods class to implement the INotifyPropertyChanged interface. The interface is not implemented, so Visual Studio will warn you about a compiler error:


Use the Quick Actions menu to implement the interface. Press Alt+Enter or  to show potential fixes and choose “Implement interface” from the context menu.


As soon as you choose that action from the menu, Visual Studio should add this line of code to your Moods class:

public event PropertyChangedEventHandler PropertyChanged;
The INotifyPropertyChanged interface has a single member, an event called PropertyChanged.

We haven’t talked about events yet. We’ll give you all of the code that you need to use this event. You can learn more about events in our downloadable chapter on events and delegates: https://github.com/head-first-csharp/fifth-edition

Use the PropertyChanged event to make data binding work
This interface has a new keyword that we haven’t shown yet: event. An event is a way for an object to let other objects know that something happened. Buttons have a Clicked event, and you’ve written event handler methods for them: if you’ve hooked up an event handler method to a button, then when the user clicks the button, it invokes its Clicked event, which calls your event handler.

Now your Moods class has a PropertyChanged event, just like the Button class has a Clicked event.

Luckily, events are easy to use. Add this method to your Moods class:

NOTE
 Do this!

protected void OnPropertyChanged(string name)
{
    PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(name));
}
Now all you need to do to tell the binding context that the CurrentMood property has changed is to call this method and pass the string "CurrentMood" as an argument to invoke the PropertyChanged event.

Modify the Moods class to add this statement to the very end of the UpdateMood method:

OnPropertyChanged("CurrentMood");
Now run your app again. Click the button several times. It now works—the label text updates.

NOTE
You added an event to your class, and added a method that uses the ?. operator to invoke the event to tell the binding context that a property was updated. That’s all you need to know about events to finish the rest of the projects in this chapter!


Data binding can make your code-behind a lot simpler and easier to understand.

In Chapter 6 we talked about separation of concerns, and how you can make your code easier to read and work with if you separate behavior into different classes.

Data binding is a great way to use this idea to keep your code-behind simple, and to make it easier for you to write the code for your .NET MAUI apps—which can make a huge difference when you’re building an app that has many controls and displays a lot of data.

SHARPEN YOUR PENCIL

In the next exercise you’ll convert the Beehive Management System to use data binding. Here’s new code-behind for it. Compare it with the code in Chapter 6 and write down what we changed.


EXERCISE

Modify the Beehive Management System to use data binding, using the code in the example that we just gave you.

Modify the Queen class to implement INotifyPropertyChanged

Add the using System.ComponentModel directive to Queen.cs if it’s not already there.

Modify the Queen class declaration to add , INotifyPropertyChanged (including the comma) and use the Quick Action menu to implement the interface so it adds the PropertyChanged event.

Add the OnPropertyChanged method to your queen class (this is the same method that you added to Moods cs).

Add two new properties to Queen:

public bool HiveIsRunning { get; private set; } = true;
public bool OutOfHoney { get { return !HiveIsRunning; } }
Add code to the end of the UpdateStatusReport method to notify the binding context that properties have changed:

OnPropertyChanged("StatusReport");
OnPropertyChanged("CanAssignWorkers");
OnPropertyChanged("HiveIsRunning");
OnPropertyChanged("OutOfHoney");
Replace the last line of the WorkTheNext method with this code to update the HiveIsRunning property:

HiveIsRunning = base.WorkTheNextShift();
return HiveIsRunning;
Modify the XAML to bind property values to properties in the Queen class

Modify the XAML to bind AssignJobButton’s IsEnabled property, WorkShiftButton’s IsVisible property, OutOfHoneyButton’s IsVisible, and StatusReport’s Text property to StatusReport.


SHARPEN YOUR PENCIL SOLUTION


EXERCISE

We gave you all of the changes to the XAML. Here are the changes to the Queen class. It’s been modified to implement the INotifyPropertyChanged interface, and the OnPropertyChanged button was added.


Two new properties were added, which are used to bind to properties:


The UpdateStatusReport method was modified to call OnPropertyChanged every time the Queen updated the report:


The WorkTheNextShift method was modified to set the HiveIsRunning property before returning:


THERE ARE NO DUMB QUESTIONS
Q: I think I understand everything that we just did. Can you go over it again, just in case I missed something?

A: Absolutely. The Beehive Management System app you built in Chapter 6 updated its Label named StatusReport by setting its Text property in code like this:

StatusReport.Text = queen.StatusReport;
You modified that app to use data binding to automatically update the Label any time the Queen object updates its StatusReport property. You did this by making three changes. First, you modified the Queen class to implement the INotifyPropertyChanged interface so it could notify the UI of any changes to the property. Then you modified the XAML to create an instance of Queen and bind the Label.Text property to the Queen object’s StatusReport property. Finally, you modified the code-behind to use the instance created by the XAML and remove the lines that set statusReport.Text.

Q: And what exactly is the interface for?

A: The INotifyPropertyChanged interface gives you a way to tell a MAUI page that a property changed, so it can update any controls that bind to it. When you implement it, you’re building a class that can do a specific job: notifying MAUI apps of property changes. The interface has a single member, an event called PropertyChanged. When you use your class for data binding, MAUI checks to see if it implements INotifyPropertyChanged, and if it does, it attaches an event handler to your class’s PropertyChanged event, just like you attached event handlers to your Buttons’ click events.

Q: I still don’t quite get events. Can you explain them one more time?

A: Sure! You’ve been using event handler methods since the very first chapter in this book—for example, every time you used a button in a MAUI app, you added a Clicked event handler that looked like this:

private void Button_Clicked(object sender,
EventArgs e)
So what’s going on behind the scenes? Well, a Button is actually just another class. Try going to the MainPage.xaml.cs file in the Beehive Management System and typing in WorkShiftButton. Hover over it:


Visual Studio is showing you that this is really just a field, and its type is Button. Somewhere inside the code for that Button is an event that’s declared with the event keyword, and somewhere else there’s code to invoke the event, just like your OnPropertyChanged method invoked the PropertyChanged event.

The reason the method is called an event handler method is because it handles an event—which means that it executes every time that event is invoked. Your MAUI’s binding context does the same thing. It hooked up an event handler to the Queen’s PropertyChanged event, and every time the Queen calls OnPropertyChanged to invoke the event, it updates the specific binding that you told it to update.

WATCH IT!

Data binding works with properties, not fields.

You can only use data binding with public properties. If you try to bind a WPF control attribute to a public field instead, you won’t see any changes—but you won’t get an exception, either.

Polymorphism means that one object can take many different forms
Any time you use a RoboBee in place of an IWorker, or a Wolf in place of an Animal, or even an aged Vermont cheddar in a recipe that just calls for cheese, you’re using polymorphism. That’s what you’re doing any time you upcast or downcast. It’s taking an object and using it in a method or a statement that expects something else.

Keep your eyes open for polymorphism!
You’ve been using polymorphism throughout—we just didn’t use that word to describe it. While you’re writing code over the next few chapters, be on the lookout for the many different ways you use it.

Here’s a list of four typical ways that you’ll use polymorphism. We’re providing an example of each of them, though you won’t see these particular lines in the exercises. As soon as you write similar code in an exercise in later chapters in the book, come back to this page and check it off the following list:

You’re using polymorphism when you take an instance of one class and use it in a statement or a method that expects a different type, like a parent class or an interface that the class implements.



They’re all right. Thinking about interfaces in lots of different ways helps you get to that “a-ha!” moment.

We’ve described interfaces in a bunch of different ways. You can think about an interface like…

 …a type that you can use to reference any object that implements the interface.

 …a way to show that different classes do the same job.

 …a contract that guarantees that an object has certain members, no matter what its type is.

 …a checklist that the compiler uses to make sure that a has class all of the methods and properties in the interface.

These are all good ways to think about interfaces.


Exactly! The fastest way to get to that “a-ha!” moment is to write lots of code that users interfaces—and AI can help.

Interfaces are really useful, which is why there are so many different ways that C# developers use them. Ironically, that’s one reason that the interface is one of the more difficult concepts for folks learning C# to wrap their heads around… so even if you feel like you’ve got a pretty good handle on the mechanics—the “hows”—of using interfaces, don’t feel bad if you’re still a little unclear on the “whys.” Luckily, AI chatbots can be a great tool to help fill in your knowledge gaps and get you to that “a-ha!” moment when you really get interfaces.

SENS-AI

Use prompt engineering to learn more about interfaces

You’ve learned a lot about interfaces in this chapter! But even with the knowledge and practice you’ve had so far, you still have questions… right? Let’s use AI to help you reach that “a-ha!” moment where you “get” interfaces.

OpenAI—the company that makes ChatGPT—created this really useful prompt engineering guide to help you use AI chatbots more effectively: https://platform.openai.com/docs/guides/prompt-engineering

Let’s use some of the valuable advice in that guide to help get C# interfaces into your brain.

Prompt Engineering Strategy: Write clear instructions

The prompt engineering guide has strategies to help you get better results from an AI. You’ve already seen one of those strategies in action: write clear instructions. Back in Chapter 3, you used the Guy object exercise from this book as a prompt. If the AI generated code that worked, that meant the instructions were clear enough for it.

We created the first version of that exercise in 2007 when we were writing the first edition of this book, and we’ve been revising and improving it ever since. We work really hard on writing clear instructions for each exercise in this book—if they’re not clear, some readers have trouble with the exercise. Before AI, we had to test our instructions with real people (and we still do). Now we can test our instructions to see if they’re clear by pasting them into an AI chatbot: if the chatbot generates code that isn’t right, it means we didn’t make our instructions clear enough.


Asking an AI chatbot to adopt a persona means requesting that it change its responses to you in specific ways—like asking it to answer every prompt with a joke, or to talk like a pirate (“Ahoy, matey! Arrrr!”). Let’s take advantage of this tactic by first giving it a prompt telling it how you want it to answer future questions, and then asking it the questions that you want answered. Here’s a persona prompt that can help you when you’re doing research:

When I ask for help to learn about a specific feature of C#, give a
response that has at least one real-world example I would use it for, with
lots of analogies and C# code that demonstrates that example.
Try it out. Start a new session with your favorite AI chatbot. Give it that prompt. It might choose a C# topic and give you an example of a response—that’s okay. Once it finishes responding, ask it to help you learn about interfaces:

I want to learn more about C# interfaces. Can you help me understand how
an interface is like a contract?
Now it should include analogies and code examples in its response. Try asking it follow-up questions about interfaces, like how an interface is a type, or about how a class implements an interface to show that it does a specific job.


AI chatbots are good at following examples. If you want to see the code first, then an explanation, and then an analogy, try giving it this prompt:



You’re an object-oriented programmer.

There’s a name for what you’ve been doing. It’s called object-oriented programming, or OOP. Before languages like C# came along, people didn’t use objects and methods when writing their code. They just used functions (which is what they call methods in a non-OO program) that were all in one place—as if each program were just one big static class that only had static methods. It made it a lot harder to create programs that modeled the problems they were solving. Luckily, you’ll never have to write programs without OOP, because it’s a core part of C#.

NOTE
The idea that you could combine your data and your code into classes and objects was a revolutionary one when it was first introduced—but that’s how you’ve been building all your C# programs so far, so you can think of it as just plain programming.

The four core principles of object-oriented programming
When programmers talk about OOP, they’re referring to four important principles. They should seem very familiar to you by now because you’ve been working with every one of them. We just told you about polymorphism, and you’ll recognize the first three principles from Chapter 5 and Chapter 6: inheritance, abstraction, and encapsulation.


Separation of concerns and DRY (don’t repeat yourself) are also important ideas. for OOP.


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

