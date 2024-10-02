# Quality-Attributes

**Attributes of the system** that describe a specific capabilities that are **not related to specific functional requirements** 

Are closely **related to the non-functional** requirements and **describe** what **technical capabilities** the system should have **in order to fulfill the non-functional** requirements

1. A **non-functional requirement define** what the system **should deal with** 
2. **Quality attributes map** those requirements **to technical capabilities** 
3. The **architecture describes how** those capabilities **will be designed and implemented**

## Scalability

**Ability** of the system to **support adding computational resources** in order **to handle additional load without interruption** of the service

This can be **easily done with a load balancer**, which will **distribute the load between the servers** while **adds or removes servers based on the load**

## Manageability

**Ability to manage the application**, to **known what is happening** inside it and to **be able to take actions** accordingly

If **the one to report** a problem **is the user**, the system **is not manageable**, while **if the system itself report problems**, **it becomes** more **manageable**

## Modularity

**Making an application modular** will **minimize the effort** needed **to maintain it** and **make it much more flexible** for changes

A **modular system** is **built from small, well-defined, building blocks**, that **can be changed** or replaced **without affecting the whole system**

## Extensibility

A system that implement extensibility is a **system that its functionality can be extended without modifying its existing code**

In the case we have an **endpoint that receive a `format` parameter** to return the data in `json` or `xml`, and we want to **implement a new format** `csv`

In a **non-extensible system**, we would have a **switch with 2 cases**, and to implement a new format, we would have to **modify the whole code**

```java
String formatQuery(String format, String data) {
    switch (format) {
        case "json":
            return new JsonFormatter().format(data);
        case "xml":
            return new XmlFormatter().format(data);
        case "csv":
            return new CsvFormatter().format(data);
    }
}
```

In an **extensible system**, the **switch would be replaced by a factory method** that would **return the correct formatter** based on the format

```java
String formatQuery(String format, String data) {
    Formatter formatter = getFormatter(format);
    return formatter.format(data);
}

Formatter getFormatter(String format) {
    switch (format) {
        case "json":
            return new JsonFormatter();
        case "xml":
            return new XmlFormatter();
        case "csv":
            return new CsvFormatter();
    }
}
```

## Testability

Testability **defines how easy is to test the system**

With **unit tests**, the system is tested in **small parts**, while with **integration tests**, **the system** is tested **as a whole**

In a **testable system is easy to test using both** tests, and have two characteristics:

- **Methods and modules are independent of each other**
- **Every method is responsible for a single action**
