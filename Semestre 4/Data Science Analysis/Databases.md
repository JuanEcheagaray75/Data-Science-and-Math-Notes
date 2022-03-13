# Databases

---

- A database is a set of _stored and organized_ data with the end goal of making them easy to access and recover via a computer
- A database is a series of organized data that is **related** to one another.

---

## Traditional schema of a database

Traditional databases are organized by _fields_, _registries_ and _files_:

1. **Field**: Similar to a column in a table.
	1. Think of it as one of the properties of an object. It's not the particular value of that attribute, but rather the attribute in gener
3. **Registry**: Similar to a row in a table.
	1. In statistical terms, it is a sample (just 1 element), and in more data science terms, it's a data-point. A registry contains the all the information (all the fields) of a particular object
4. **File**: Set of all registries.
	1. The _entire_ database

![[Pasted image 20220312183959.png]]

---

## General properties of databases

- Ease of access to the data
- They allow us to store massive amounts of data
- **Redundancy control**
	- Option 1: Redundancy means having multiple copies of the same database (where you put them is up to you)
	- Option 2: Storing the same information in different parts of the database
- **Concurrency control**
	- Process of managing independent operations of the database that are simultaneous and considered _transactions_ in DBMS terms (read, write)
	- In simpler words, making the database available for multiple users, but guaranteeing that the operations performed on the database by one user **do not** affect those done by another user. 
- Safety measures: users, roles, passwords, and so on

### More convoluted properties

- Static vs dynamic
	- Static: data can only be read, not modified
	- Dynamic: can handle data reading and writing
- Centralized vs de-centralized
	- Centralized: the entire database is stored into a single server
	- Decentralized: the database is stored across multiple servers

---

## Types of databases

---

### RDB (Relational databases)

Composed of several tables called relations
- These tables are then connected to one another through a key.
	- The primary key is stored on the main database
	- The foreign key has the exact same values as the primary key, but it's located on the other databases that the users wants to relate to the original database to

![[Pasted image 20220312201629.png]]

---

### NonSQL

---

### APIs

---
