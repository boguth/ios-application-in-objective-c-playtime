# ios-application-in-objective-c-playtime
This is my playground for building iOS apps in objective C.

##Requirements
1. A Mac running OS X 10.9.4 or later.
2. Xcode
3. iOS SDK (included with Xcode)


## Things to Know

- Once you start the Xcode Editor, you can choose which language you want to develop in: Swift or Objective C. You can also choose from a number of templates. For this app, choose the Single View Application template. The Xcode interface has four main areas: The main editing section, the utility section to the right, the navigation section to the left and the toolbar on top.

- On the toolbar, select iPhone 6 and click the play button to run your app. When you do this, the UIApplicaitonMain function takes over, creating an application object that sets up the infrustructure for your app to work. This function is written in the main.m file under the Supporting Files folder of your app.

  ### A note on compilers and interpreters.
  - When Yukihiro Matsumoto developed Ruby, he also made a Ruby Interpreter. This is the standard for most Ruby implementations (there are a few exceptions). What that means is that when people write in ruby code, they usually use Matz's Ruby Interpreter. This is the default. When you download Ruby, the MRI comes with it. WHen you are in the IRB and type ruby [some fucntion or file], the word "ruby" signals that the following text should be run through the ruby interpreter.

  - An interpreter goes through each line of code, translating it into machine language (0's and 1') until it either hits the end of the file or runs into an error. This is different than a compiler. A compiler goes through the whole document, translates all of it into machine code, and then if there are errors, send backs all the errors at once. If there are no errors, then it passes that translated file on to the computer. Objective-C uses a compiler.

## The Main.m File
- In the main file there is the main function and some import statements. It looks like this:

  ```Objective-C
     #import <UIKit/UIKit.h>
     #import "AppDelegate.h"

     int main(int argc, char * argv[]) {
       @autoreleasepool {
          return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
       }
     }
  ```
  In Objective-C, every variable and argument must be named - meaning that its type must be declared. Hence all the ints and chars. The curly braces open the main function. By default, Objective-C does not implement or import any functions, which is why there are also those two import statements that will provide the usable methods in the file.

  Objective-C is built upon the C language, which means that Objective-C uses a lot of C's keywords. To distinguish Objectice-C keywords from C's keywords, the @ symbol is placed in front of a word to indicate that are idiomatic to Objective-C. Why does this matter? Because if you are using an existing C compiler, then it needs to know when to switch to "Objective-C mode."

