## 1️⃣ What is Hibernate?

### 🔹 Definition
Hibernate is an **ORM (Object Relational Mapping)** framework that:
- Converts **Java objects ↔ Database tables**
- Removes the need to write JDBC code manually

### 🔹 Problem Hibernate Solves
Without Hibernate:
- Write SQL queries
- Handle ResultSet
- Convert DB rows → Java objects

With Hibernate:
- Java class = Table
- Object = Row
- Fields = Columns

---

## 2️⃣ What is JPA?

### 🔹 Definition
**JPA (Java Persistence API)** is a **specification**
- Defines rules for ORM
- Does NOT provide implementation

### 🔹 JPA Providers
| Provider | Role |
|--------|------|
| Hibernate | Most popular JPA implementation |
| EclipseLink | JPA implementation |
| OpenJPA | JPA implementation |

👉 **Spring Data JPA uses Hibernate internally by default**

---

## 3️⃣ What is Spring Data JPA?

### 🔹 Definition
Spring Data JPA is a **Spring module** that:
- Simplifies JPA + Hibernate
- Removes boilerplate DAO code
- Provides CRUD methods automatically

### 🔹 Key Benefit
You **don’t write SQL or JPQL manually** for common operations.

---

## 4️⃣ Architecture Flow (Application-Level)

```

Controller
↓
Service
↓
Repository (Spring Data JPA)
↓
JPA (Specification)
↓
Hibernate (Implementation)
↓
Database

````

---

## 5️⃣ How Spring Data JPA Works Internally (Simple)

### Step-by-Step Flow

1. You create a **Repository interface**
2. Extend `JpaRepository`
3. At runtime:
   - Spring creates a **proxy class**
   - Proxy uses **EntityManager**
4. EntityManager delegates work to **Hibernate**
5. Hibernate generates SQL
6. SQL executes on DB
7. Result converts back to Java object

👉 **You never see SQL unless logging is enabled**

---

## 6️⃣ Core Interfaces in Spring Data JPA

| Interface | Purpose |
|---------|--------|
| CrudRepository | Basic CRUD |
| PagingAndSortingRepository | Pagination + Sorting |
| JpaRepository | Full JPA features |

### Example
```java
public interface UserRepository extends JpaRepository<User, Long> {
}
````

---

## 7️⃣ Entity & Mapping Annotations (VERY IMPORTANT)

### 🔹 Entity Level

| Annotation | Purpose                 |
| ---------- | ----------------------- |
| `@Entity`  | Marks class as DB table |
| `@Table`   | Customize table name    |

```java
@Entity
@Table(name = "users")
public class User {
}
```

---

### 🔹 Primary Key

| Annotation        | Purpose         |
| ----------------- | --------------- |
| `@Id`             | Primary key     |
| `@GeneratedValue` | Auto generation |

```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```

---

### 🔹 Column Mapping

| Annotation   | Purpose          |
| ------------ | ---------------- |
| `@Column`    | Column mapping   |
| `@Transient` | Not stored in DB |

---

## 8️⃣ Relationship Annotations

| Relationship | Annotation    |
| ------------ | ------------- |
| One to One   | `@OneToOne`   |
| One to Many  | `@OneToMany`  |
| Many to One  | `@ManyToOne`  |
| Many to Many | `@ManyToMany` |

### Example

```java
@ManyToOne
@JoinColumn(name = "dept_id")
private Department department;
```

---

## 9️⃣ Fetch Types (Interview Favorite)

| Type  | Meaning            |
| ----- | ------------------ |
| EAGER | Load immediately   |
| LAZY  | Load when required |

```java
@OneToMany(fetch = FetchType.LAZY)
```

---

## 🔟 Cascade Types

| Cascade | Purpose              |
| ------- | -------------------- |
| ALL     | Apply all operations |
| PERSIST | Save child           |
| REMOVE  | Delete child         |

```java
@OneToMany(cascade = CascadeType.ALL)
```

---

## 1️⃣1️⃣ Query Methods (Magic of Spring Data JPA)

### Method Name → Query

```java
findByName(String name)
findByAgeGreaterThan(int age)
findByEmailAndPassword(String e, String p)
```

👉 Spring converts method name → SQL automatically

---

## 1️⃣2️⃣ Custom Queries

### JPQL

```java
@Query("SELECT u FROM User u WHERE u.name = :name")
List<User> findUsers(@Param("name") String name);
```

### Native Query

```java
@Query(value = "SELECT * FROM users", nativeQuery = true)
```

---

## 1️⃣3️⃣ Transaction Management

### Annotation

```java
@Transactional
```

### What it Does

* Begins transaction
* Commits on success
* Rollback on exception

---

## 1️⃣4️⃣ Entity Lifecycle States (Hibernate Internals)

| State      | Meaning              |
| ---------- | -------------------- |
| Transient  | New object           |
| Persistent | Managed by Hibernate |
| Detached   | Session closed       |
| Removed    | Deleted              |

---

## 1️⃣5️⃣ Hibernate Session vs JPA EntityManager

| Hibernate | JPA           |
| --------- | ------------- |
| Session   | EntityManager |
| save()    | persist()     |
| get()     | find()        |

---

## 1️⃣6️⃣ Logging SQL (Very Useful)

```properties
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

---

## 1️⃣7️⃣ Advantages of Spring Data JPA

✔ No boilerplate code
✔ Clean architecture
✔ Easy pagination
✔ Transaction support
✔ Repository pattern

---

## 1️⃣8️⃣ Common Interview Questions (Quick View)

* How does Spring Data JPA create queries?
* Difference between JPA and Hibernate?
* What is EntityManager?
* What is proxy class in repository?
* How pagination works internally?
* Lazy vs Eager loading?
* N+1 problem?
* What is dirty checking?

---

## 1️⃣9️⃣ One-Line Summary (Memory Trick)

> **Spring Data JPA = Spring + JPA Spec + Hibernate + Repository Pattern**

---



