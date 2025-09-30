---
content_type: page
description: Related resources for 6.825 Java.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Related Resources
uid: e081a1e5-8ef8-3815-c311-14cb201a8a70
video_files:
  video_thumbnail_file: null
video_metadata:
  youtube_id: null
---
## 6.825: Java® Resources

## Web Sites

- The {{% resource_link "6dd3f08a-6d09-433e-969d-ffa82271bf42" "Java Programmer's FAQ" %}} is a great resource with lots of practical information
- {{% resource_link "64e36dcc-df57-4fc8-bf18-d75aada19168" "IAQ: Infrequently Answered Questions" %}} on Java, written by Peter Norvig
- {{% resource_link "94597e8e-e5fc-4065-a542-c7cfd3aba5bc" "Java 2 SDK Version 1.3 Documentation" %}} (a.k.a. JDK 1.3)
- {{% resource_link "737ec06a-525d-4211-88fa-4f8feacc8ffc" "Java 2 SDK Version 1.2.2 Documentation" %}} (a.k.a. JDK 1.2.2)
- {{% resource_link "ef3d7daf-14a0-445c-ac6c-96643a1e248e" "Java 1.1 JDK Documentation" %}}

## Books

Several people have asked which books are best for learning Java. The answer depends on prior programming experience and personal inclination.

Professor Kaelbling recommends the following two books:

Budd, Timothy. *Understanding Object-Oriented Programming With Java*. 1st ed. Reading, MA: Addison Wesley, 1999. ISBN: 0201612739.

Arnold, Ken, James Gosling, and David Holmes. *The Java Programming Language*. 3rd ed. Reading, MA: Addison Wesley, 2000. ISBN: 0201704331.

Mike recommends Flangan, David. *Java In A Nutshell*. 4th ed. O' Reilly Publications, 2002. ISBN: 0596002831. but admits that it is only helpful if you are already familiar with object-oriented programming from C++. In addition, the newest edition splits all the information about AWT and Swing (the graphics display classes) into a separate book,

Flangan, David. *Java Foundation Classes In A Nutshell*. 1st ed. O'Reilly Media, Inc., December 15, 1999. ISBN: 1565924886.

Juan Velasquez recommends Eckel, Bruce. *Thinking In Java*. 3rd ed. Upper Saddle River, NJ: Prentice Hall, 2002. ISBN: 0131002872.

## Free Tools

If you shudder at the thought of developing in Emacs or Vi, there are several free Java IDEs that you can check out. Sun's Forte and Borland's JBuilder 4 Foundation will work on Solaris, Linux, or Windows. For the purpose of class assignments, however, Emacs, Vi, Notepad, or some other text editor will be perfectly adequate.

## Beanshell

Even if you are an experienced Java programmer, you may not have heard of {{% resource_link "dbf70937-eef9-480e-b9e1-a723adbd8258" "Beanshell" %}}. Beanshell provides an interactive text-shell environment for evaluating Java expressions and interacting with a running JVM. This is a very useful debugging tool, as it allows you to instatiate and call methods on objects without recompiling (though you do need to restart the shell if you want to change a compiled class).

To install beanshell,

1. Download the {{% resource_link "ca8d45c3-993f-4f92-a746-a80175ac1a8b" "JAR file" %}}
2. Add it to your classpath, by:
    - Placing it in the lib/ext directory of your JVM, or
    - Placing it in ~/Library/Java/Extensions on MacOS X, or
    - Adding it to your UNIX/Windows environment variable
3. Run it by:
    - Double-clicking the jarfile (MacOS X, Windows + Sun JDK), or
    - Typing "java bsh.Interpreter" from the command-line, or
    - Typing "java bsh.Console" to run a GUI version

{{% resource_link "1756b2df-36cd-4887-be25-dcdedee4fe27" "More documentation" %}} is available on the Beanshell Web site.

## Assorted Tips

- **If you are a C++ programmer with little or no Java experience**, do not make the mistake of thinking that "Java is C++ without pointers," or "Java is C++ with everything as a class," etc. Many of these simplifications are wrong and will lead you astray. The first statement, "Java is C++ without pointers," is especially hazardous to your health. In Java unlike C++, all objects and arrays are created on the heap and are not in the stack. The stack only contains primitive types and references to objects. When you declare Bozo x = new Bozo();, you are creating an object on the heap and declaring that x is a reference to it. When you pass x around, assigning it to different variables and passing it to functions, it is passed by value. So if I say Bozo y = x;, y refers to the same Bozo as x does. But the following method has no effect:   
      
    public void swap(Bozo x, Bozo y) {   
    Bozo temp;   
    temp = x;   
    x = y;   
    y = temp;   
    }
- If you want to copy arrays quickly, use System.arraycopy().
- Lists can save a lot of the bookkeeping hassle required to use arrays correctly, and they are very efficient.
- Some Java classes support the clone() method, but you must be careful before using it. A clone() usually creates a shallow copy of an object. So, if you clone() a Vector, you get two different Vectors with independent internal data structures (i.e. you can delete elements from one Vector and they will remain in the other Vector), but the objects the Vectors contain are not duplicated - they both refer (at least initially) to the same set of objects.