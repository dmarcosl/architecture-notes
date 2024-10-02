# Types of Applications

## Web Apps

They are based on the **Request-Response model**

It **serves html, css, js, images**, and more, and **renders the page on the client side**

Web Apps are best suited for systems that required:

- User interaction
- User input
- Large scale
- Short and focused actions

## Web API

**Similar to Web Apps**, based on the **Request-Response model**, but the **clients are not users**, are other systems like a JS code

It serves **json, xml, csv**, etc

There are **multiple implementations**, like REST, SOAP, GraphQL

**REST** (Representational State Transfer)

- URL: `https://www.example.com/api`
- Parameters: `date=2020-01-01`
- Methods: `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `OPTIONS`, `HEAD`, `TRACE`, etc
- Input: `json`, `xml`, `csv`, etc
- Output: `json`, `xml`, `csv`, etc

**SOAP** (Simple Object Access Protocol)

- URL: `https://www.example.com/soap`
- Methods: `POST`
- Input: `xml`
- Output: `xml`

**GraphQL** (Graph Query Language)

- URL: `https://www.example.com/graphql`
- Methods: `POST`
- Input: `json`
- Output: `json`

Web APIs are best suited for systems that required:

- Data retrieval and store
- Client initiated actions
- Large scale
- Short and focused actions

## Mobile

**Apps run on mobile phones**

**Works with Web APIs** to retrieve and store data, log, etc

Mobile are best suited for systems that required:

- User interaction
- Front end for Web APIs
- Location services

## Console

Apps that **run inside the command line** of the operating system

These apps do **not have fancy ui**, just text

**Require some technical knowledge** to use, contrary to Web Apps where the user just clicks, in Console the user has to type commands with parameters

Usually have **limited interaction with the user**

Can trigger **long-running processes as well as short and focused actions**

Console are best suited for systems that required:

- Executing long-running processes
- Executing hort and focused actions
- Well-trained users

## Service

Services are **similar to Console**, but with two distinctions:

- Do **not have UI** at all, they **run in the background**
- Are **managed by a service manager**, like `systemd` in Linux

Services are best suited for systems that required:

- Long-running processes where no user interaction is needed

## Desktop

Desktop apps **run mainly on the pc**, usually with all its **resources on the client side**, but **can also work with Web APIs**

Are **targeted to end users**, so they have a **fancy UI**

Desktop are best suited for systems that required:

- User-centric actions (Microsoft Word)
- Gaming
