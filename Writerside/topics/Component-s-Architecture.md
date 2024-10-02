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

**Interfaces** are the **contracts** that **define the methods** that a **class must implement**

## DI

## SOLID

## Naming Conventions

## Exceptions Handling

## Logging
