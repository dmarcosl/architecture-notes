# Component's Architecture

**Software components** are the services, **pieces of code that runs in a single process**

**Modern systems are** usually **distributed** (like microservices), meaning they are **composed of independent software components** deployed on separate processes, and often on separate containers or servers, that **communicate between them using** some kind of **protocol**

When talking about **Software Architecture**, we are talking about **two levels of architecture**:

- **Component's Architecture**, the architecture of **individual components**, the **interaction between them**, and how to **make it fast and easy to maintain**
- **System's Architecture**, deals with the **bigger picture**, making sure the **system** is **scalable, reliable, fast and easy to maintain**

## Layers

The **layers in a software component** represent **horizontal functionality**

Software components usually perform **three basic actions**:

- **Expose** the software **functionality** through an interface or an API
- **Execute logic** on the data received
- Save / retrieve data to the **data store**

**Each action** is usually implemented in a **separate layer**

- **User Interface** or **Service Interface** layer (UI / SI)
  - Expose API
  - Auth
  - Mapping request to objects
- **Business Logic** layer (BL)
  - Validation
  - Enrichment
  - Computation
- **Data Access layer** (DAL)
  - Connection
  - Querying
  - Transaction

Why separate the code in different layers?

- It forces you to write **code** that is **well-formed and focused**, it is a **bad idea to write a method to performs multiple tasks**
- **Layers are modular**, making easy to substitute them, for example to **change the database only have to change the DAL**

### Code Flow

**A layer can only call a layer that is directly benefit in the code**, and **a layer can never call another layer above it**

- A UI layer can call the BL layer, but not the DAL layer
- The DAL layer cannot call the BL or UI layers

### Loose Coupling

We need the **layers** to **communicate with each other** in a way that we will have the **minimum impact when there is a change**

The **loose coupling** is achieved by **using interfaces** to communicate between layers, so to **change the implementation of a layer**, we only have to **change the implementation of the interface**

### Exceptions Handling between Layers

The exception handling concept states that **each layer should hide its inner exceptions** and **return a generic exception** to the layer above

For example, **if there is an exception in the DAL layer**, **instead of returning a specific** `MySQLException` to the BL layer, **it should analyze** the exception, **log** it, and **return a generic** `DataAccessException`

## Interfaces

**Interfaces are common concepts** in **Java or C#** programming languages, but in other languages are other similar concepts like **abstract classes in Python**

Interfaces are the **contracts** that **define the methods** that a **class must implement**

```C#
interface Calculator
{
    dou Add(int a, int b);
    int Subtract(int a, int b);
}
```

```C#
class MyCalculator : Calculator
{
    public dou Add(int a, int b)
    {
        return a + b;
    }

    public int Subtract(int a, int b)
    {
        return a - b;
    }
}
```

Using interfaces **allows us** to make our **code loosely coupled**, and to **change the implementation of a class without changing the code** that uses it, only the **dependency injection**

**Without** using **interfaces**, we would have to **change the code that uses the class**

## Dependency Injection (DI)

Dependency Injection is a **design pattern** that **allows us to inject the dependencies of a class** from the outside, it **complements the use of interfaces**

Without DI, the class would have to **create the dependencies** inside the class, making it **hard to test** and **hard to change the implementation**

```java
public static void main(String[] args) {
    MyCalculator calculator = new MyCalculator();
    calculator.add(1, 2);
    calculator.subtract(2, 1);
}
```

With DI, we can **inject the dependencies** from the outside, making the class **easier to test and to change** the implementation

```java
@AutoWired
@Qualifier("myCalculator")
Calculator calculator1;

@AutoWired
@Qualifier("myAnotherCalculator")
Calculator calculator2;

public static void main(String[] args) {
    calculator1.add(1, 2);
    calculator2.subtract(2, 1);
}
```

## SOLID

### Single Responsibility Principle (SRP)

Each class, module or method should have a **single** well-defined **responsibility**, **fully encapsulated** by the class, module or method

For example, a method that reads a file should not also parse the file, it should only read the file

```java
public class FileReader {
    public OutputStream read(String path) {
        // read the file
    }
    
    public String parse(OutputStream stream) {
        // parse the content
    }
}
```

### Open/Closed Principle (OCP)

A software component should be **open for extension**, but **closed for modification**, to make the code as flexible as possible and enable us to make changes quickly without modifying the existing code

For example, if we have a class that performs a calculation, we should be able to extend the class to add new calculations, but we should not be able to modify the original class to add new calculations

```java
public class Calculator {
    public double add(int a, int b) {
        return a + b;
    }
}

public class AdvancedCalculator extends Calculator {
    public double subtract(int a, int b) {
        return a - b;
    }
}
```

### Liskov Substitution Principle (LSP)

If a class is a subclass of another class, it should be able to **substitute** the first class with the second **without changing the behavior** of the program

For example, if we have a class that write logs to a file, we should be able to substitute the class with another class that writes logs to a database without changing the behavior of the program

```java
var logger = new FileLogger();
logger.log(message);

var logger = new DatabaseLogger();
logger.log(message);
```

### Interface Segregation Principle (ISP)

**Many client-specific interfaces are better than one general-purpose interface**

A class should not be forced to implement an interface that it does not use, and it should not depend on methods that it does not use

Instead of bloating a single interface with many methods, we should create multiple interfaces with fewer methods

```java
public interface DataUtil {
    String readData();
    void writeData(String data);
    String decode(String data);
    String encode(String data);
}
```

```java
public interface DataHandler {
    String readData();
    void writeData(String data);
}

public interface DataEncoder {
    String decode(String data);
    String encode(String data);
}
```

### Dependency Inversion Principle (DIP)

**High-level modules**, which contain complex business logic, **should not** directly **depend on low-level modules**, such as utility classes or frameworks; instead, **both should rely on** abstract **interfaces** or contracts, **ensuring flexibility** and easier **maintenance** when changes are needed in low-level implementations

Same as **Dependency Injection**

## Naming Conventions

Naming conventions are a set of rules that define how to name variables, classes, methods, and other elements of a program

They are to make the code more readable and easy to understand, are not enforced by the compiler, but a code without them becomes messy

Usually there are two types of rules:

- **Structure**: casing, underscores, etc
- **Content**: what kind of words to use

### Structure

#### Camel Case

The first letter of the first word is lowercase

There are two types:

- Upper Camel Case: `CamelCase`, the first letter of the first word is capitalized
- Lower Camel Case: `camelCase`, the first letter of the first word is not capitalized

It is popular en Java, C#, JavaScript, Swift, and recommended for class names in Python, Ruby

#### Lowercase separated by underscores

The name contains only lowercase letters and the words are separated by underscores

`lowercase_separated_by_underscores`

Popular in Python and Ruby for variable names

#### Uppercase separated by underscores

The name contains only uppercase letters and the words are separated by underscores

`UPPERCASE_SEPARATED_BY_UNDERSCORES`

Popular in Java, Python and Ruby for constants

#### Hungarian Notation

The name contains a prefix that indicates the type of the variable

`strName`, `intAge`, `boolIsEnabled`

Popular in C, C++, and C#

### Content

- Class Names: Nouns (`DataRetriever`, `Car`, `Network`
- Methods Names: Imperative Verb (`RetrieveData`, `Drive`, `SendPacket`)

## Exceptions Handling

Exception handling is a **part of the layer pattern**, but there are some good practices to follow

- **Only catch exceptions if you have something to do with it**
  - Do not catch an exception only to log it, because that can be done with a more general exception to cover multiple ones
- **Catch only specific exceptions**
  - For example SQLException, along with the generic Exception, to handle the db related in a different way
- **Use try-catch on the smallest code fragment possible**
  - Do not wrap the entire method in a try-catch block, only the code that can throw an exception

## Logging

No matter how simple the code is or how urgent is the system, **logging is a must**

A good system uses logging for **two purposes**

- **Track errors**
  - If there are any exceptions during the execution of the code, the system will write them to the log, complete with full error message, stack trace, inner exceptions, etc.
  - This way, when an exception happens, you will have a good starting point to investigate the error
- **Gather data**
  - The system can write to the log some data that can be useful for debugging, like the parameters of a method, the result of a calculation, etc.
  - This way, you can see the data that the system is working with, and you can understand better what is happening
