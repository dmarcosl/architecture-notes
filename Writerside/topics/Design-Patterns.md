# Design Patterns

Design patterns are a **collection of general reusable solutions to common problems** in software design

They **are templates** that can be applied to solve a problem in a specific context

They **are not finished designs** that can be transformed directly into code

Using design patterns have these advantages:

- **Are already tested** by other developers, do not reinvent the wheel
- **Make your code more readable and easy to modify**, making the system more flexible

**Patterns have architectural aspects**, **each one** discusses a proposed architecture that **solves a given problem** (micro-architecture)

## Factory Pattern

It **allows creating objects without specifying the exact class** of the object

**Specifying the class** in the creation code **will tie the code to the class**

If later we need to use another class for implementing the same logic, we will have to modify all the code that creates the class, which can be scattered all across the application

In this example we specify the class in the creation code

```java
class EuropeWeather {
    public int getWeather(String city, String date) {
        ...
    }
}

class Main {
    public static void main(String[] args) {
        EuropeWeather weather = new EuropeWeather();
        int weather = weather.getWeather("London", "2021-09-01");
    }
}
```

If we need to change the class, we will have to modify all the code that creates the class

The factory pattern allows us to create objects without specifying the exact class of object that will be created

```java
pubic interface WeatherProvider {
    int getWeather(String city, String date);
}

public class EuropeWeather implements WeatherProvider {
    public int getWeather(String city, String date) {
        ...
    }
}

public class AsiaWeather implements WeatherProvider {
    public int getWeather(String city, String date) {
        ...
    }
}

public class Main {
    public static void main(String[] args) {
        WeatherProvider weatherProvider = getWeatherProvider("Europe");
        int weather = weatherProvider.getWeather("London", "2021-09-01");
    }
    
    private static WeatherProvider getWeatherProvider(String continent) {
        if (provider.equals("Europe")) {
            return new EuropeWeather();
        } else if (provider.equals("Asia")) {
            return new AsiaWeather();
        }
        return null;
    }
}
```

## Repository Pattern

The repository pattern is a **data access pattern** that provides a **separation between the domain model and the data access code**

It describes a **data obstruction** technique that should be used to **hide** the complexities of the **data access code**

For example, a bad practice would be to scatter the sql queries all across the application, making it difficult to maintain and modify, with the repository pattern we can centralize all the data access code in one place

The change from a database to another without this pattern would require to rewrite the whole application, while with this pattern we only need to modify the repository classes

## Facade Pattern

The facade pattern is a **structural design pattern** that provides a **simplified interface** to a complex system

Instead of put the whole code in a single class, we can create a facade class that will call the other classes

```java
// not facade
public void transferMoney(String accountA, String accountB, int amount) {
    if (accountRepository.getAccount(accountA) == null) {
        log.info("Account " + accountA + " does not exist");
        throw new Exception("Invalid operation");
    }
    if (accountRepository.getAccount(accountB) == null) {
        log.info("Account " + accountB + " does not exist");
        throw new Exception("Invalid operation");
    }
    if (balanceRepository.getAccountBalance(accountA) < amount) {
        log.info("Account " + accountA + " does not have enough money");
        throw new Exception("Invalid operation");
    }
    
    balanceRepository.withdrawMoney(accountA, amount);
    log.info("Money withdrawn from account " + accountA);
    balanceRepository.depositMoney(accountB, amount);
    log.info("Money deposited to account " + accountB);
}

// facade
public void transferMoney(String accountA, String accountB, int amount) {
    if (!accountExists(accountA) ||
        !accountExists(accountB) !!
        !hasEnoughMoney(accountA, amount)) {
        throw new Exception("Invalid operation");
    }
    
    withdrawMoney(accountA, amount);
    depositMoney(accountB, amount);
}
```

## Command Pattern

The command patterns is a **behavioral design pattern** that says that **all the information of an action should be encapsulated within an object**, and **this object will have a method that will execute the action**

The goal is the **complete separation** between the invocation of the **command** and its actual **function**

```java
public class Light {
    public void turnOn() {
        ...
    }
    
    public void turnOff() {
        ...
    }
}

// not command
public class Main {
    public static void main(String[] args) {
        Light light = new Light();
        light.turnOn();
        light.turnOff();
    }
}

// command
public interface Command {
    void execute();
}

public class TurnOnLightCommand implements Command {
    private Light light;
    
    public TurnOnLightCommand(Light light) {
        this.light = light;
    }
    
    public void execute() {
        light.turnOn();
    }
}

public class TurnOffLightCommand implements Command {
    private Light light;
    
    public TurnOffLightCommand(Light light) {
        this.light = light;
    }
    
    public void execute() {
        light.turnOff();
    }
}

public class Main {
    private Light light;
    private TurnOnLightCommand turnOnLightCommand;
    
    public static void main(String[] args) {
        setup();
        turnOnLightCommand.execute();
        turnOffLightCommand.execute();
    }
    
    private void setup() {
        light = new Light();
        turnOnLightCommand = new TurnOnLightCommand(light);
        turnOffLightCommand = new TurnOffLightCommand(light);
    }
}
```