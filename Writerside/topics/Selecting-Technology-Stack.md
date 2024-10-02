# Selecting Technology Stack

This **decision** is one of the **most important** in the whole process

It is **irreversible**, despite there are architectures that allow some flexibility like microservices

The **emotional attachment** to a technology stack **can lead to a bad decision**

The decision **must be**:

- **Done with clear mind**
- **Heavily documented**
- **Group decision, not only yours**

## Considerations for the technology stack

Some considerations must be taken into account to **ensure the best platform** for the system

- **Can perform the required tasks**, because if the technology stack is not able to perform the required tasks, the system will fail
- **Community support**, because it is easier to find help
- **Popularity**, because it is easier to find developers

## Front end

When talking about front end, we are talking about the **client side of Web Apps, Desktop Apps and Mobile Apps**, the part of the system that the user views with his own eyes

**Web Apps** have a front end component, **JavaScript based**, that runs in the browser

| Technology | Founder  | Content              | Community | Performance | Learning Curve | Future |
|------------|----------|----------------------|-----------|-------------|----------------|--------|
| Angular    | Google   | Full-blown Framework | Large     | Great       | Long           | Bright |
| React      | Facebook | UI-centered Library  | Large     | Great       | Medium         | Bright |
| Vue        | Evan You | UI-centered Library  | Medium    | Great       | Medium         | Bright |

**Mobile Apps have three approaches (Native, Hybrid and Cross-platform)** that represent a trade of **between performance and development time**, and **the selection should be based on these factors**

|                            | Native                         | Hybrid                | Cross-platform                  |
|----------------------------|--------------------------------|-----------------------|---------------------------------|
| Development Language & IDE | Java/Kotlin, Swift/Objective-C | HTML, CSS, JavaScript | Xamarin (C#), React Native (JS) |
| Access to Phone's Features | Full control, no limits        | Very limited          | Limited                         |
| User Experience            | Exceptional                    | Inferior              | Good, with limitations          |

**Desktop Apps** have two approaches (Native and Web-based)

## Back end

When talking about back end, we are talking about the **server side of Web Apps and Web APIs**, while also **including Console and Service applications**

| Technology   | Founder               | App Types                          | Type System | Cross Platform | Community | Performance | Learning Curve | Future  |
|--------------|-----------------------|------------------------------------|-------------|----------------|-----------|-------------|----------------|---------|
| .NET Classic | 2001 Microsoft        | All                                | Static      | No             | Large     | OK          | Long           | Blurred |
| .NET Core    | 2016 Microsoft        | Web App, Web API, Console, Service | Static      | Yes            | Medium    | Great       | Long           | Bright  |
| Java         | 1995 Sun Microsystems | All                                | Static      | Yes            | Huge      | OK          | Long           | Stable  |
| Node.js      | 2009 Ryan Dahl        | Web App, Web API                   | Dynamic     | Yes            | Large     | Great       | Medium         | Bright  |
| PHP          | 1995 Rasmus Lerdorf   | Web App, Web API                   | Dynamic     | Yes            | Large     | OK -        | Medium         | Fading  |
| Python       | 1991 Guido van Rossum | All                                | Dynamic     | Yes            | Huge      | OK -        | Short          | Bright  |

## Data store

Selecting the data store technology is one of the most important decisions in the whole process

There are two types of data store:

- **SQL**: Not Huge, Structured data
- **NoSQL**: Huge, Unstructured data

### SQL

Also known as **relational** databases

**Stores data in tables**, each one with a concrete **set of columns**, each one with a **specific type**

The tables can have relationships with other tables, hence the name **relational**

Another characteristic is the **transactions**, that represent an **atomic set of actions that either executes all the actions or none of them**

The transactions are **ACID compliant**:

- **Atomicity**: All or nothing
- **Consistency**: The data is always in a consistent state
- **Isolation**: The transactions are isolated from each other
- **Durability**: Once a transaction is committed, it is permanent

Another characteristic is the **querying language**, **SQL** (Structured Query Language)

### NoSQL

NoSQL databases try to be the **opposite of SQL databases**

Since **relational databases maintains schema for each record**, and the **performance decreases as the data grows**

NoSQL **emphasizes scalability and performance**

Most of them are **schema-less**, do not force any schema, can store different entities with different fields in the same table

The **data** usually is stored in **json format**

Most NoSQL databases support eventual consistency, that means that the data will be consistent, but not immediately

NoSQL databases are **not ACID compliant**, each database select its own version of transaction support

In NoSQL, there is not an universal query language to access the data in all databases, each one has its own query language

