
# 🔟 IMPORTANT SPRING CORE INTERVIEW QUESTIONS & ANSWERS

---

## 1️⃣ What is Spring Framework?

### ✅ Answer:
Spring Framework is a **lightweight, open-source Java framework** that provides infrastructure support for developing **loosely coupled, maintainable, and testable enterprise applications**.

It mainly provides:
- Inversion of Control (IoC)
- Dependency Injection (DI)
- Modular architecture

👉 **In applications**, Spring manages objects and their dependencies so developers can focus on business logic.

---

## 2️⃣ What problem does Spring Core solve?

### ✅ Answer:
Spring Core solves:
- Tight coupling between classes
- Manual object creation using `new`
- Difficult unit testing
- Poor maintainability

By using **IoC and DI**, Spring removes object creation responsibility from application code.

---

## 3️⃣ What is Inversion of Control (IoC)?

### ✅ Answer:
Inversion of Control is a **design principle** where:
> The control of object creation and dependency management is shifted from the application code to the Spring container.

Instead of classes creating dependencies, Spring injects them.

---

## 4️⃣ What is Dependency Injection (DI)?

### ✅ Answer:
Dependency Injection is a **design pattern** used to implement IoC, where required dependencies are provided to a class from outside.

Spring supports DI using:
- Constructor Injection
- Setter Injection
- Field Injection

---

## 5️⃣ Difference between IoC and DI?

### ✅ Answer:

| Aspect | IoC | DI |
|-----|----|----|
| Type | Principle | Pattern |
| Purpose | Invert control | Inject dependencies |
| Who implements | Framework | Developer + Spring |
| Relation | Concept | Implementation |

👉 **Spring uses DI to achieve IoC**

---

## 6️⃣ What is Spring Container?

### ✅ Answer:
Spring Container is the **core component** of Spring that:
- Creates beans
- Injects dependencies
- Manages bean lifecycle

It acts as an **object factory and lifecycle manager**.

---

## 7️⃣ Difference between BeanFactory and ApplicationContext?

### ✅ Answer:

| Feature | BeanFactory | ApplicationContext |
|------|------------|-------------------|
| Loading | Lazy | Eager |
| Features | Basic | Advanced |
| Usage | Rare | Most common |
| AOP, Events | ❌ | ✅ |

👉 **ApplicationContext is preferred in real applications**

---

## 8️⃣ What is a Spring Bean?

### ✅ Answer:
A Spring Bean is an object that is:
- Created
- Managed
- Injected  
by the Spring container.

Beans usually represent:
- Controllers
- Services
- Repositories

---

## 9️⃣ What are the different types of Dependency Injection?

### ✅ Answer:

1. **Constructor Injection** (Recommended)
2. Setter Injection
3. Field Injection (Not recommended)

👉 Constructor injection is preferred for mandatory dependencies and immutability.

---

## 🔟 What is the default bean scope in Spring?

### ✅ Answer:
The default bean scope in Spring is **singleton**.

This means:
- Only one instance of the bean is created per Spring container
- Same object is shared across the application

---

## ❓ 11. Why is Spring considered lightweight?

### ✅ Answer:
Spring is lightweight because:
- It uses POJOs (Plain Old Java Objects)
- No need to extend framework classes
- Minimal resource usage
- Modular design (use only what you need)

---

## ❓ 12. Why is Constructor Injection recommended over Field Injection?

### ✅ Answer:
Constructor Injection:
- Makes dependencies explicit
- Ensures immutability
- Supports unit testing
- Avoids reflection issues

Field Injection hides dependencies and makes testing harder.

---

## ❓ 13. Why do we avoid using `new` keyword in Spring applications?

### ✅ Answer:
Using `new`:
- Creates tight coupling
- Bypasses Spring container
- Prevents DI and lifecycle management

Spring needs to create objects to manage dependencies and lifecycle.

---

## ❓ 14. Why is Spring preferred for enterprise applications?

### ✅ Answer:
Spring is preferred because it provides:
- Loose coupling
- Scalability
- Easy testing
- Integration with ORM, Security, Messaging
- Strong community support

---

## ❓ 15. Why is ApplicationContext preferred over BeanFactory?

### ✅ Answer:
ApplicationContext provides:
- Eager bean loading
- AOP support
- Event handling
- Internationalization
- Better enterprise features

BeanFactory is too basic for real-world applications.

---

#  QUICK INTERVIEW ONE-LINERS (BONUS)

- **Spring = IoC + DI**
- **IoC is the concept, DI is the implementation**
- **Spring Boot simplifies Spring Core**
- **Constructor Injection is best practice**
- **Spring manages application objects**

---

##  FINAL TIP FOR INTERVIEWS
Always explain Spring Core with **application layers**  
(Controller → Service → Repository)

---

