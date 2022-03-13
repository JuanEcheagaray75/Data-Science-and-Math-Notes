# Databases

---

1. [[#Traditional schema of a database|Traditional schema of a database]]
1. [[#General properties of databases|General properties of databases]]
	1. [[#More convoluted properties|More convoluted properties]]
1. [[#Types of databases|Types of databases]]
	1. [[#RDB (Relational databases)|RDB (Relational databases)]]
	1. [[#NonSQL|NonSQL]]
		1. [[#Key Value|Key Value]]
		1. [[#Document|Document]]
		1. [[#Columnar|Columnar]]
		1. [[#Graph|Graph]]
1. [[#API (Application Programming Interface)|API (Application Programming Interface)]]
	1. [[#Types of APIs|Types of APIs]]

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

Non-relational databases, they tailored made for specific data models, they possess flexible schemes to create modern apps.

#### Key Value

A hash table on steroids (to put it _mildly_). Each data-point receives a key, and the database uses this key to store the data using a hashing function.

- Most Key/Value databases just support query, insert and delete operations
	- To modify a value, a different application must overwrite the existing data
- Key/Value databases are optimized for performing simple lookups with keys.
- They are not that optimal when the user needs to query across different tables

![[Pasted image 20220312231024.png]]

#### Document

A document data store manages a set of named string fields and object values in an entity that's referred to as a document, typically in the form of **JSON** documents.

- Each field value can be a scalar (string, integer, ...) or a compound element, such as a list.
- A document contains the entire data for an entity (in most cases)
- Documents are queried by their unique key, but data can also be queried based on the values of the fields

![[Pasted image 20220312205559.png]]

#### Columnar

Stores data into columns and rows, seems pretty similar to a relational database, but the underlying structure is pretty distinct

- It has a de-normalized approach of storing sparse data
- Information is stored into **column families**. Each column family holds a set of logically related columns, that are usually manipulated together.
	- Within a column family new columns can be added dynamically, and the rows can be sparse!
- Data is stored by key order (Notice that the data for a single entity has the same key for different column families).
- Different column families are stored in different files

![[Pasted image 20220312210212.png]]

#### Graph

It manages 2 types of information, _nodes_ and _edges_. Nodes represent entities, and edges the relationships between them.

- Edges can have a direction encoding the nature of the relationship
- Graph databases shine the most when an application needs to traverse a network of nodes and edges

![[Pasted image 20220312231254.png]]

Take this example, with a graph database it would be pretty straightforward to perform queries such as "Find all employees that report to Sarah"

---
## API (Application Programming Interface)

Set of defined rules that explain how computers or applications communicate with each other. APIs sit between an application and the web server.

General procedure:
1. A **client initiates an API call** to retrieve information, this is known in the business as a **request**
2. After **receiving a valid request**, the API calls the external program or server
3. The **server sends a response** to the API with the requested information
4. The **API transfers the data** to the initial requesting application

### Types of APIs

- Open APIs
	- Open source APIs than can be accessed through the HTTP protocol, they are also known as _public APIs_, they have defined API endpoints, request and response formats 
- Partner APIs
	- They are exposed to or by strategic business partners
	- Developers can access these APIs in self-service mode through a public API developer portal (Just like on the activity in class)
	- They need to complete an onboarding process to get login credentials
- Internal APIs
	- They remain hidden from external users
	- Just meant to be used by the company
	- Designed to boost productivity and communication across different development teams
- Composite APIs
	- Combination of multiple APIs
	- Allow devs to access several endpoints through a single call
	- Useful where performing a single task may require information from several sources

For more info on APIs see https://www.ibm.com/cloud/learn/api

---

For more info on NoSQL databases see:
https://docs.microsoft.com/en-us/azure/architecture/data-guide/big-data/non-relational-data