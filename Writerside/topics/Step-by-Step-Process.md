# Step-by-Step Process

The first three steps are know as black-box design, where we focus on the system's API and sequence of events

The last two steps are known as white-box design, where we focus on the internal details of the system

## 1. Gathering Functional Requirements

Involves investigation and asking questions to understand

- **How** our system **behaves**
- **What** our system **needs and does not need to do**
- **What parts** of the system **are given** to us and what parts we **need to design**

## 2. Gathering Non-Functional Requirements

This step is critical to ensure that **the system**

- Has the **right qualities**
- **Produces the desired behaviour** for the **given workload**, not just in general

Main attributes to consider:

- **Scalability**
- **High availability**
- **Performance**

## 3. Defining System's API and Sequence of Events

Using a **sequence diagram**

- Will ensure that **all the use cases are covered**
- Naturally **present our System's API** through **interactions between users and the system**

## 4. Designing for Functional Requirements

Creating a **software architecture diagram** that matches the **system's API** and sequence of events

This **involves**:

- **Defining the architectural style** we are going to follow
- The **flow of network requests** from the clients to the relevant services
- All the **details of** what **data** we are going to store and **how** we want to **store it** (schema, db, etc.)

Mainly focus on the **system functionality**, while keeping the non-functional requirements in mind

## 5. Addressing Non-Functional Requirements

This step **involves**

- **Adding additional components**
- **Eliminating** potential single points of **failure or performance bottlenecks**
- **Optimizing critical parts** of the system using 
  - **Different data structures**
  - **Sharding or processing** techniques
  - **Software architecture patterns**

Ensure we handle user requests and store data in an efficient way