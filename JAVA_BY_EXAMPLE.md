# Java by Example — A Practical Guide

An example-first reference for modern Java (17+). Each section shows a minimal snippet you can paste into a `.java` file and run.

> How to run examples
>
> 1. Install a recent JDK (17 or later recommended):
>    ```bash
>    java -version
>    javac -version
>    ```
>
> 2. Save a snippet in `Example.java`, then compile and run:
>    ```bash
>    javac Example.java
>    java Example
>    ```
>
> 3. For third-party libraries, use a build tool like **Maven** or **Gradle**. Example with Maven:
>    ```bash
>    mvn archetype:generate
>    mvn compile exec:java
>    ```

---

## Table of Contents

1. [Hello, Java](#hello-java)  
2. [Numbers & Math](#numbers--math)  
3. [Strings & Formatting](#strings--formatting)  
4. [Collections (List/Set/Map)](#collections-listsetmap)  
5. [Control Flow (if/for/while/switch)](#control-flow-ifforwhileswitch)  
6. [Methods, Parameters, Generics](#methods-parameters-generics)  
7. [Streams & Lambdas](#streams--lambdas)  
8. [Packages & JARs](#packages--jars)  
9. [Files, Paths, JSON/CSV/ZIP](#files-paths-jsoncsvzip)  
10. [Errors & Exceptions](#errors--exceptions)  
11. [OOP: Classes, Records, Interfaces](#oop-classes-records-interfaces)  
12. [Concurrency: Threads, Executor, CompletableFuture](#concurrency-threads-executor-completablefuture)  
13. [HTTP: HttpClient & a tiny API (Spring Boot / Javalin)](#http-httpclient--a-tiny-api-spring-boot--javalin)  
14. [Command-line apps (args & picocli)](#commandline-apps-args--picocli)  
15. [ProcessBuilder & Subprocess](#processbuilder--subprocess)  
16. [Dates, Times & Timezones (java.time)](#dates-times--timezones-javatime)  
17. [Regex (javautilregex)](#regex-javautilregex)  
18. [Logging (javautillogging--slf4j)](#logging-javautillogging--slf4j)  
19. [Configuration via Env Vars & Properties](#configuration-via-env-vars--properties)  

---

## Hello, Java

```java
public class Example {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
````

---

## Numbers & Math

```java
public class Example {
    public static void main(String[] args) {
        int x = 10;
        double y = 3.5;
        System.out.println(x + y);      // 13.5
        System.out.println(Math.pow(2, 8));  // 256.0
        System.out.println(Math.sqrt(16));   // 4.0
    }
}
```

---

## Strings & Formatting

```java
public class Example {
    public static void main(String[] args) {
        String name = "Alice";
        int age = 30;

        System.out.println("Hello " + name + ", age " + age);
        System.out.println(String.format("Hello %s, age %d", name, age));

        String multi = """
            This is
            a multi-line
            string.
            """;
        System.out.println(multi.strip());
    }
}
```

---

## Collections (List/Set/Map)

```java
import java.util.*;

public class Example {
    public static void main(String[] args) {
        List<String> list = List.of("a", "b", "c");
        Set<Integer> set = new HashSet<>(List.of(1, 2, 2, 3));
        Map<String, Integer> map = Map.of("apple", 1, "banana", 2);

        System.out.println(list);
        System.out.println(set);
        System.out.println(map);
    }
}
```

---

## Control Flow (if/for/while/switch)

```java
public class Example {
    public static void main(String[] args) {
        int n = 3;

        if (n > 0) System.out.println("positive");
        else System.out.println("non-positive");

        for (int i = 0; i < 3; i++) System.out.println(i);

        int j = 0;
        while (j < 3) {
            System.out.println(j);
            j++;
        }

        switch (n) {
            case 1 -> System.out.println("one");
            case 2 -> System.out.println("two");
            default -> System.out.println("other");
        }
    }
}
```

---

## Methods, Parameters, Generics

```java
public class Example {
    public static <T> void printTwice(T item) {
        System.out.println(item);
        System.out.println(item);
    }

    public static void main(String[] args) {
        printTwice("hello");
        printTwice(42);
    }
}
```

---

## Streams & Lambdas

```java
import java.util.*;
import java.util.stream.*;

public class Example {
    public static void main(String[] args) {
        List<Integer> nums = List.of(1, 2, 3, 4, 5);

        int sumSquares = nums.stream()
                             .map(x -> x * x)
                             .filter(x -> x % 2 == 0)
                             .reduce(0, Integer::sum);

        System.out.println(sumSquares);  // 20
    }
}
```

---

## Packages & JARs

```java
// In file myapp/App.java
package myapp;

public class App {
    public static void main(String[] args) {
        System.out.println("Inside a package!");
    }
}
```

Compile & run:

```bash
javac myapp/App.java
java myapp.App
```

---

## Files, Paths, JSON/CSV/ZIP

```java
import java.nio.file.*;
import java.io.IOException;

public class Example {
    public static void main(String[] args) throws IOException {
        Path path = Path.of("hello.txt");
        Files.writeString(path, "Hello File!");
        String text = Files.readString(path);
        System.out.println(text);
    }
}
```

---

## Errors & Exceptions

```java
public class Example {
    public static void risky() throws Exception {
        throw new Exception("Oops!");
    }

    public static void main(String[] args) {
        try {
            risky();
        } catch (Exception e) {
            System.out.println("Caught: " + e.getMessage());
        }
    }
}
```

---

## OOP: Classes, Records, Interfaces

```java
record Point(int x, int y) {}

interface Greeter {
    void greet();
}

class Person implements Greeter {
    String name;
    Person(String name) { this.name = name; }
    public void greet() { System.out.println("Hello " + name); }
}

public class Example {
    public static void main(String[] args) {
        Point p = new Point(1, 2);
        System.out.println(p);

        Person alice = new Person("Alice");
        alice.greet();
    }
}
```

---

## Concurrency: Threads, Executor, CompletableFuture

```java
import java.util.concurrent.*;

public class Example {
    public static void main(String[] args) throws Exception {
        ExecutorService pool = Executors.newFixedThreadPool(2);

        CompletableFuture<String> future =
            CompletableFuture.supplyAsync(() -> "Hello from another thread!", pool);

        System.out.println(future.get());
        pool.shutdown();
    }
}
```

---

## HTTP: HttpClient & a tiny API (Spring Boot / Javalin)

```java
import java.net.http.*;
import java.net.*;
import java.io.*;

public class Example {
    public static void main(String[] args) throws Exception {
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest req = HttpRequest.newBuilder(new URI("https://httpbin.org/get"))
                                     .build();
        HttpResponse<String> res = client.send(req, HttpResponse.BodyHandlers.ofString());
        System.out.println(res.body());
    }
}
```

---

## Command-line apps (args & picocli)

```java
public class Example {
    public static void main(String[] args) {
        if (args.length > 0)
            System.out.println("First arg: " + args[0]);
        else
            System.out.println("No args");
    }
}
```

---

## ProcessBuilder & Subprocess

```java
import java.io.*;

public class Example {
    public static void main(String[] args) throws Exception {
        Process p = new ProcessBuilder("echo", "Hello").start();
        try (var reader = new BufferedReader(new InputStreamReader(p.getInputStream()))) {
            System.out.println(reader.readLine());
        }
    }
}
```

---

## Dates, Times & Timezones (java.time)

```java
import java.time.*;

public class Example {
    public static void main(String[] args) {
        LocalDate today = LocalDate.now();
        ZonedDateTime utc = ZonedDateTime.now(ZoneId.of("UTC"));
        System.out.println(today);
        System.out.println(utc);
    }
}
```

---

## Regex (java.util.regex)

```java
import java.util.regex.*;

public class Example {
    public static void main(String[] args) {
        String text = "abc123";
        Pattern p = Pattern.compile("\\d+");
        Matcher m = p.matcher(text);

        if (m.find()) {
            System.out.println("Found: " + m.group());
        }
    }
}
```

---

## Logging (java.util.logging & SLF4J)

```java
import java.util.logging.*;

public class Example {
    private static final Logger logger = Logger.getLogger("MyLog");

    public static void main(String[] args) {
        logger.info("Hello log!");
        logger.warning("Something might be wrong");
    }
}
```

---

## Configuration via Env Vars & Properties

```java
import java.util.*;

public class Example {
    public static void main(String[] args) {
        String path = System.getenv("PATH");
        System.out.println("PATH=" + path);

        Properties props = System.getProperties();
        System.out.println("Java version=" + props.getProperty("java.version"));
    }
}
```

