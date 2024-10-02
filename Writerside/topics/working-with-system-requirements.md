# Working with System Requirements

## Two types of requirements

The **functional requirements** answer the question **what the system should do**

We expect the functional requirements to deal with the questions

- What are the **business flows** of the system? Login, storing photos, etc
- What **business services** should the system have? User authentication service, data access service
- What does the **user interface** of the system looks like? The Look and feel general guidance, responsiveness and more

The **non-functional requirements** answer this other question, **what should the system deal with**

## The non-functional requirements

The non-functional requirements describe the expected environment for the system with emphasis on edge cases

The most common non-functional requirements are

- Performance
- Load
- Data volume
- Concurrent users
- Service Level Agreement (SLA)

### Performance

When talking about performance there are two main aspects to consider

- Always talk in numbers, **never in general terms**
- Latency and Throughput

The **rule of thumb** is that when is an **end user**, the waiting response should be **less than 1 second**, but when is a batch process, but when working in a **b2b environment**, we are talking **about 100ms**

**Latency** is the **time that the system takes to perform a single task** in the application, for example "how long it takes to read a row from the database?"

**Throughput** is the **number of tasks that the system can perform in a given time**, for example "how many rows can be read from the database in a second?"

If the read of a row takes about 1s, that is the latency, so in a good system the throughput, considering concurrency and a well optimized code, should be about 1000 rows per second, but if the throughput is 100 rows per second, that is a bad system

### Load

The load defines the **quantity of work the application have to withstand** without breaking

In an **API**, it will be the **number of concurrent requests**, **not the number of requests made in a specific time** unit

If the throughput is 1000 requests per second, the load should be around 5000 concurrent requests, **even if the response time increases, the system should be able to handle the load**

The **best practice is to always look at peak numbers**

### Data volume

The data volume defines **how much data** in gigabytes or terabytes **our system will accumulate** over time

This is important to:

- **Deciding on the database type**, since not all databases can handle large quantities of data equally
- **Determine what types of queries we are going to write**, because a query in a table of 100.000 rows will be different from a query in a table of 100.000.000 rows
- **Plan ahead the storage**

The data volume has two aspects:

- How much data is required on day one
- What is a forecasted data growth

### Concurrent users

This requirement defines **how many users will be using the system simultaneously**

Is **similar to the load**, but while the **load are actual requests**, the **users include dead times** between them

The **rule of thumb** says that **concurrent users are 10 times the load**

### Service Level Agreement (SLA)

The SLA describes the **required uptime** for the system **in a percentage**

This is one of the main competitions between cloud providers

The SLA has **great influence on the design of the system**, to more uptime, more sophisticated the system will be

**The client usually will ask for 100%** or 99.999% uptime, but **the cost** of such a system **is prohibitive**

