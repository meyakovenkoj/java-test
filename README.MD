# Test project in Java

It is a extremly easy first project in Java, just to understand how to compile this shit.

## Usage

### Requirements

- You should be running Linux / Mac OS
- You should install JDK from oracle.com

## Developing
  
### Structure

* **src** - source files in java (in style of com/package/name/Class.java)
* **classes** - folder for binary files. It will contain your *.class files
* **lib** - folder for your/external lib's (in *.jar format)
* **Manifest.txt** - internal of this file will be included in META-INF/MANIFEST.MF of executable *.jar file

### How to run

```bash
javac -d classes src/MyOne/Test.java
cd classes
jar cfm ../lib/Test.jar ../Manifest.txt MyOne/*.class
cd ../lib
java -jar Test.jar
```

to be continued... 
