# The simple and satisfiying art of executing a java file from the command line.

Having the next java source

```java
public class Salad {
	
	public static void main(String[] args) {
		System.out.println("I'm the best salad in this neighberhood!");
	}
}
```

Run the command below, inside the folder source with `java` command:

```bash
java Salad.java
#it prints
I'm the best salad in this neighberhood!
```

Now let’s create another Java file in the same folder.

```java
public class Watermelon {
	
	public void talk() {
		System.out.println("I'm the best fruit!");
	}
}
```

and call its method `talk` in **Salad class** contained in **Salad file**.

```java
public class Salad {
	
	public static Watermelon watermelon = new Watermelon();
	
	public static void main(String[] args) {
		watermelon.talk();//here
		System.out.println("I'm the best salad in this neighberhood!");
	}
}
```

Let’s run the previous command once again.

```bash
java Salad.java
#it prints
Salad.java:3: error: cannot find symbol
        public static Watermelon watermelon = new Watermelon();
                      ^
  symbol:   class Watermelon
  location: class Salad
.\Salad.java:3: error: cannot find symbol
        public static Watermelon watermelon = new Watermelon();
                                                  ^
  symbol:   class Watermelon
  location: class Salad
2 errors
error: compilation failed
```

Because our **Salad class** doesn’t know any about the **Watermelon class**, thought the **Watermelon class** contained inside the **Watermelon file** knows how to talk, so let’s add some watermelon to our salad.

At first, is neccesary to process our **Watermelon file**  into our **processedFruits folder** with the `javac` command and `-d` option to indicate folder location name.

```bash
javac -d processedFruits Watermelon.java
```

And finally, let’s add our **processedFruits folder** to the original run command adding the `-cp` option to indicate where are compiled our java source of **Watermelon file.**

```bash
java -cp "processedFruits\" Salad.java
#it prints
I'm the best fruit!
I'm the best salad in this neighberhood!
```

That’s it, simple but effective:

- Run a standalone java file.
- Run a standalone java file adding compiled sources as need it.

### Command and options dictionary:

- `java` run .class and .java files.
- `javac`compile .java files and creates .class files.
- `-d`indicate output folder.
- `-cp`indicate compiled folders directory(classpath).

### Tech stack

- Java 11.
- Windows 10.
