# ios-application-in-objective-c-playtime
This is my playground for building iOS apps in objective C.

##Requirements
1. A Mac running OS X 10.9.4 or later.
2. Xcode
3. iOS SDK (included with Xcode)

##Resources
1. [Beginning Arc](http://www.raywenderlich.com/5677/beginning-arc-in-ios-5-part-1)
2. [Apple's Beginner Tutotiral](https://developer.apple.com/library/ios/referencelibrary/GettingStarted/RoadMapiOS/FirstTutorial.html#//apple_ref/doc/uid/TP40011343-CH3-SW1)

## Things to Know

- Once you start the Xcode Editor, you can choose which language you want to develop in: Swift or Objective C. You can also choose from a number of templates. For this app, choose the Single View Application template. The Xcode interface has four main areas: The main editing section, the utility section to the right, the navigation section to the left and the toolbar on top.

- On the toolbar, select iPhone 6 and click the play button to run your app. When you do this, the UIApplicaitonMain function takes over, creating an application object that sets up the infrustructure for your app to work. This function is written in the main.m file under the Supporting Files folder of your app.

  ### A note on compilers and interpreters.
  - When Yukihiro Matsumoto developed Ruby, he also made a Ruby Interpreter. This is the standard for most Ruby implementations (there are a few exceptions). What that means is that when people write in ruby code, they usually use Matz's Ruby Interpreter. This is the default. When you download Ruby, the MRI comes with it. WHen you are in the IRB and type ruby [some fucntion or file], the word "ruby" signals that the following text should be run through the ruby interpreter.

  - An interpreter goes through each line of code, translating it into machine language (0's and 1') until it either hits the end of the file or runs into an error. This is different than a compiler. A compiler goes through the whole document, translates all of it into machine code, and then if there are errors, send backs all the errors at once. If there are no errors, then it passes that translated file on to the computer. Objective-C uses a compiler.


## The Main.m File
- In the main file there is the main function and some import statements. Let's take a look at it and then disect it. It looks like this:

  ```Objective-C
     #import <UIKit/UIKit.h>
     #import "AppDelegate.h"

     int main(int argc, char * argv[]) {
       @autoreleasepool {
          return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
       }
     }
  ```
  ### Some notes before we dive into it:
  - In Objective-C, every variable and argument must be named - meaning that its type must be declared. Hence all the ints and chars.

  - Objective-C is built upon the C language, which means that Objective-C uses a lot of C's keywords. To distinguish Objectice-C keywords from C's keywords, the @ symbol is placed in front of a word to indicate that are idiomatic to Objective-C. Why does this matter? Because if you are using an existing C compiler, then it needs to know when to switch to "Objective-C mode." *Back to the explanation...*

- The curly braces open the main function. By default, Objective-C does not implement or import any functions, which is why there are also those two import statements that will provide the usable methods in the file. The UIKit framework provides the UIApplication class and its methods.

- The @autoreleasepool is a way to manage memory and is a part of automatic reference counting (ARC) in C. ARC makes the compiler keep track of the amount of objects that memory needs to be allocated for. Here's my best understanding of it so far. The compiler goes through a file of code and when it sees an object, allocates memory for it. The issue memory has to deal with is to determine how long to allocate space for a particular piece of code. It could store everything forever - allocate memory for each object or block of code and keep that memory allocated until the program is done running. But there is a more efficient way that is best explained by an example.

Imagine that there is a string. A variable points to that string, and another variable points to the same string, and a third variable points to the same string. That string is thus referenced three times. By default, the three variables "own" that string. All that means is that, even if the string is changed, those variables will still point to it. Now let's say that the compiler is going through the code. The compiler allocates memory to store that string, but let's say that it has gone through all three references to the string. At this point, it now has now translated the three references to that code to machine language, and this memory is no longer needed to save the string. So what ARC does is it counts the amount of times that particular code is referenced and then gets rid of it once its count is done - its usefulness is over. @autoreleasepool is a way of signlaing that this reference counting should be done.

- ```UIApplicationMain``` is our application object. This object manages and coordinated all the high level app behaviors.

- ```AppDelegate``` The app delegate can be thought of the main controller for our application. It creates the window where the app's content is drawn and it is responsible for responding to the user and the ipone. Our application object calls AppDelegate as way to say, "Run the program."

##AppDelegate

###The AppDelegate.h File
- The AppDelegate class is defined in two files - the AppDelegate.m (implemenation file) and the AppDelegate.h (the interface file). This is standard for class definitions. The interface file describes a class's public methods - methods you as a programmer use to make it do cool stuff. In the AppDelegate.h file the following lines of code are written.

  ```Objective-C
    #import <UIKit/UIKit.h>

    @interface AppDelegate : UIResponder <UIApplicationDelegate>

    @property (strong, nonatomic) UIWindow *window;

    @end

  ```
- The @interface opens up the public interface for the AppDelegate, in which has only one property: window. @property declares that the text to follow is going to be a property of the public interface. (strong, nonatomic) are property attributes. Strong means that the variable pointing to the place in memory where its value is stored will always point to that place, even if the value being stored changes. UIWindow means that the window variable is an instantnce of the UIWindow class.

###The AppDelegate.m File
- This file contains all the inner workings of the method - it manages data storage and retrieval.

##How to Get Shit To The Screen
1. Download Xcode.
2. Open up a single view project.
3. Navigate to the Main.storyboard file.
4. In the utility panel (right hand side), open the object library, which is in the panel on the lower right hand side of the screen:

![Object Library Screencap](screencap.png)

5. Type in "text" and select textfield (or whatever you want).
6. Drag and drop to the screen and position it as necessary.
7. Select auto AuoConstraints (so what you want to place is sized properly)

![AuoConstraints Screencap](autoconstraints.png)

8. Click the play button.
