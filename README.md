# 🧩 C1 – API Client Framework

> A foundational Core Python project focused on **classes, inheritance, and abstraction** through real-world API consumption.

This project is part of **Track 2: Core Python & OOP**, and is intentionally framework-free.  
The goal is not to build an API, but to **design a clean, reusable way to talk to APIs**.

---

## 🎯 Purpose

Most developers learn APIs by writing one-off request logic scattered across scripts or route handlers.

This project takes a different approach.

The purpose of this project is to learn how to:

- Separate **how APIs are contacted** from **what APIs represent**
- Encapsulate API documentation rules into reusable objects
- Hide multi-step workflows behind meaningful domain actions
- Practice inheritance and polymorphism in a context that mirrors real systems

This is **not** a FastAPI project.  
This is about **thinking clearly with classes**.

---

## 🧠 Core Idea

All APIs are different in *what they require*.  
Almost all APIs are the same in *how they are contacted*.

This project models that distinction explicitly.

---

## 🧱 High-Level Design

The project is built around two conceptual layers.

### 1️⃣ Base API Client (Communication Layer)

The base client represents **generic API communication**, independent of any specific service.

It is responsible for:

- Making HTTP requests
- Attaching headers and query parameters
- Handling failures and error responses
- Parsing JSON safely and consistently

It does **not** know:

- what weather is
- what a GitHub repository is
- what a coin price means
- what endpoints exist

It only knows **how to talk**.

---

### 2️⃣ Concrete API Clients (Domain Layer)

Each concrete client represents **one specific API domain**.

Examples include:

- Weather
- GitHub
- Cryptocurrency prices

These clients:

- inherit the ability to communicate from the base client
- encode rules learned from API documentation
- expose **domain-level actions**, not raw HTTP calls

For example:

- “Get weather for a city”
- “Get repository metadata”
- “Get current asset price”

How many HTTP calls are required to fulfill that action is an **internal concern**.

---

## 🔄 Why Inheritance Is Used Here

Inheritance is used **intentionally**, not automatically.

It is appropriate here because:

- All API clients share the same communication behavior
- Each API has different rules, endpoints, and workflows
- Subclasses should be usable interchangeably at the communication level
- Domain-specific behavior belongs in domain-specific clients

This mirrors real-world patterns such as:

- API adapters
- integration clients
- service wrappers

---

## 🌦️ Example: Multi-Step API Workflow (Conceptual)

Some APIs require **multiple dependent calls**.

For example:

- A weather service may require latitude and longitude
- A human provides a city name
- A geocoding call must occur before a weather call

In this project:

- That workflow lives **inside the Weather client**
- The base client remains unaware of it
- The caller simply asks for “weather for a city”

This keeps complexity contained and reusable.

---

## 🚫 What This Project Is Not

To avoid confusion, this project is **not**:

- A FastAPI service
- A REST API
- A request utility script
- A rate-limiting or retry framework
- A production-ready SDK

Those concerns belong elsewhere.

This project exists to build **mental models**, not deployables.

---

## 🧭 How This Fits Into the Larger Learning Plan

This project is intended to be completed **before** backend API service work.

Once this pattern is understood:

- FastAPI route handlers become thin adapters
- External integrations feel predictable
- Domain logic stays out of transport layers
- API documentation stops feeling overwhelming

This project feeds directly into Track 1 backend services.

---

## 🗂️ Suggested Folder Structure

The structure is intentionally minimal and behavior-focused.

- Core logic lives under `src/`
- Domain-specific clients are separated by concern
- Tests focus on **behavior**, not HTTP plumbing

The exact layout is less important than the **separation of responsibility**.

---

## 🧠 Key Takeaways

By completing this project, you should be able to confidently answer:

- Where does API documentation knowledge belong?
- What should a base class be responsible for?
- When is inheritance appropriate?
- How do you hide API quirks behind clean interfaces?
- How do real systems prevent API complexity from leaking everywhere?

If those answers feel clearer at the end, the project succeeded.

---

## 🧾 Status

Planned  
(To be implemented incrementally, starting with one simple API and expanding)

---

## 📌 Final Note

This project is intentionally uncomfortable at first.

That discomfort is not confusion — it is **abstraction forming**.

If this feels harder than writing a script that “just works,” that’s the point.
