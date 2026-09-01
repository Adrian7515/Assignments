# Java Compilation, bytecode and the JVM
## JavaProcess.java file 

```java
public class JavaProcess {
    public static void main(String[] args) {
        System.out.println("I understand the Java compilation process.");
    }
}
    // 1. Java source file .java stored the source code the program I, the progammmer wrote down.
    // 2. javac, the compiler, translated the source code I wrote in the program into bytecode.
    // 3. The .class file has the bytecode that was created by the compiler.
    // 4. The role that the JVM plays is what takes the bytecode in the .class file and executes it in the program to produce an output.

## CompilationSteps.java file

public class CompilationSteps {
    public static void main(String[] args) {
        System.out.println("Step 1: Write Java source code.");
        System.out.println("Step 2: Compile the source code using javac.");
        System.out.println("Step 3: The compiler generates Java bytecode.");
        System.out.println("Step 4: The JVM Java Virtual Machine executes the bytecode.");
        /* After examining the files I can see I wrote JavaProcess.java and CompilationSteps.java.
        The compiler generated the files with bytecode which are JavaProcess.class and CompilationSteps.class
         */
    }
}
