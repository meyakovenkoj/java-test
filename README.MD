# How to compile and create jar
## Compile
Let's check the project structure:

    .
    ├── build
    ├── bin
    ├── lib
    |   ├── commons-io-2.6.jar
    |   └── commons-codec-1.4.jar
    └── src
        ├── com
        |   ├── interactive
        |   |   └── Interactive.java
        |   ├── manual
        |   |   └── Manual.java
        |   └── Process.java
        └── HashFunc.java

To build project we should create .class files at first.
Open terminal in project's folder
ls command will show you build, bin, lib, src folders
Create file with paths to all .java files
Call commmand:

```bash
find . -name '*.java' > source.txt
```

It will find all .java files in your project. A dot after find says computer to look up in your current directory.

Call:

```bash
cat source.txt
```

to see all paths

Then we should build .class files in build folder
Call:

```bash
javac -classpath ./lib/commons-io-2.6.jar:./lib/commons-codec-1.4.jar -d build @source.txt
```

* **-classpath** says java to add depedeces with external libs
* **-d** says what direction folder you want
* **@source.txt** says where we store paths to java-files


## Create jar file

Create Mainfest file:

```bash
vim MANIFEST.MD
```

It should contain information about your Main class and libs:

    Manifest-Version: 1.0
    Main-Class: HashFunc
    Class-Path: lib/commons-io-2.6.jar lib/commons-codec-1.4.jar

Don't forget to leave /n in the end of file!

Go to your build folder:

```bash
cd build
```

And now let's create our jar:

```bash
jar cvfm ../bin/HashFunc.jar ../MANIFEST.MF * ../lib
```

How does it work?

keys:
* **c** - creates jar file with your own name 
* **v** - shows all info about process
* **f** - tells what files you adding into jar archive
* **m** - tells the path to yor own Manifest file

options:
* **../bin/HashFunc.jar** - name of your jar file
* **../MANIFEST.MF** - name of your Manifest
* (star) - means 'everything inside current directory'
* **../lib** - path to external libs

And the last but not the least:
Because of java is interpretating lang so you should hold external jar near to your own one. It is easily solves with .exe programs in Windows. But it's not our case)
So you should copy full ./lib folder in ./bin

Result structure:

    .
    ├── build
    |   ├── com
    |   |   ├── interactive
    |   |   |   └── Interactive.class
    |   |   ├── manual
    |   |   |   └── Manual.class
    |   |   └── Process.class
    |   └── HashFunc.class
    ├── bin
    |   ├── lib
    |   |   ├── commons-io-2.6.jar
    |   |   └── commons-codec-1.4.jar
    |   └── HashFunc.jar
    ├── lib
    |   ├── commons-io-2.6.jar
    |   └── commons-codec-1.4.jar
    ├── src
    |   ├── com
    |   |   ├── interactive
    |   |   |   └── Interactive.java
    |   |   ├── manual
    |   |   |   └── Manual.java
    |   |   └── Process.java
    |   └── HashFunc.java
    ├── MANIFEST.MD
    └── source.txt

## Running

Open bin folder:

```bash
cd bin
```

Create test file:

```bash
vim iloveyou.txt  
```

Put some text:

    Darling, you are awesome!

Run your app:

```bash
java -jar HashFunc.jar -md5 -f iloveyou.txt
```

## Links
* http://qaru.site/questions/351623/how-to-compile-multiple-java-files-when-there-are-java-files-in-other-packages
* http://qaru.site/questions/139373/how-do-i-make-a-jar-from-a-java
* https://www.opennet.ru/docs/RUS/linux_base/node149.html
* https://stackoverflow.com/questions/6768188/how-can-i-add-a-jar-file-dependencies-when-building-it-with-the-command-line-to

