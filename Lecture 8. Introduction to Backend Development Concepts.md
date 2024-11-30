### Installations
1. [Spring Tools Suite For Eclipse](https://spring.io/tools)
2. [MySQL Server and Workbench](https://dev.mysql.com/downloads/installer/)
	1. [Video tutorial](https://youtu.be/uj4OYk5nKCg?si=suxNqY5_HFHh86eg)
3. [Postman](https://www.postman.com/downloads/)
Before diving into **Spring Boot** or any other backend framework, it’s important to understand some foundational concepts that will help you grasp how the backend works. This includes understanding how applications interact, how data is exchanged, and the structure of web services. Let's explore these key topics in backend development.

---

## **What is Backend Development?**

In a web application, the **backend** is the part of the system that is responsible for:

1. **Storing data** (e.g., in databases).
2. **Processing logic** (e.g., calculating user scores).
3. **Communicating with external systems** (e.g., calling third-party APIs).
4. **Handling requests** (e.g., when a user submits a form).

While the **frontend** (user interface) is what the user sees and interacts with, the **backend** runs on a server and does the actual processing behind the scenes.

---

## **Web Servers and APIs**

### **1. What is a Web Server?**

A **web server** is a software that handles HTTP requests. It listens for incoming requests (e.g., from a browser or mobile app), processes them, and sends back a response. Think of it as the "postman" who receives messages and sends them to the correct address.

---

### **2. What is an API?**

- **API (Application Programming Interface)** is a set of rules that allow one piece of software to talk to another. It defines the **endpoints**, **requests**, and **responses**.
- **RESTful APIs** are the most common way to communicate between systems.

### **What is REST?**

- **REST (Representational State Transfer)** is an architectural style for designing networked applications. It relies on a stateless, client-server model where requests are made using standard HTTP methods.
- REST APIs use **URLs** to define resources, and HTTP methods to define actions on those resources.

---

## **HTTP Methods**

When you interact with a web service, you’ll use different **HTTP methods** to send requests. Here are the most commonly used ones:

### **1. GET**

- **Purpose**: Retrieve data from the server.
- **Example**: Get a list of users or a single user's profile.
- **Usage**: Safe and idempotent (it doesn't change the state of the server).
- **Example URL**: `GET /users/1` (Get the details of user with ID 1).

### **2. POST**

- **Purpose**: Send data to the server to create a new resource.
- **Example**: Creating a new user or adding a new item to a shopping cart.
- **Usage**: Non-idempotent (it can change the server's state).
- **Example URL**: `POST /users` (Create a new user).

### **3. PUT**

- **Purpose**: Update or replace a resource on the server.
- **Example**: Updating a user's profile information.
- **Usage**: Idempotent (calling it multiple times has the same effect as calling it once).
- **Example URL**: `PUT /users/1` (Update the details of user with ID 1).

### **4. DELETE**

- **Purpose**: Remove a resource from the server.
- **Example**: Deleting a user or item.
- **Usage**: Idempotent (deleting a resource multiple times has the same effect as once).
- **Example URL**: `DELETE /users/1` (Delete the user with ID 1).

### **5. PATCH**

- **Purpose**: Partially update a resource on the server.
- **Example**: Updating a single field of a user's profile (e.g., changing email address).
- **Usage**: Non-idempotent.
- **Example URL**: `PATCH /users/1` (Partially update user 1's information).

---

## **Response Codes (HTTP Status Codes)**

When a server sends a response to a request, it includes an **HTTP status code** to indicate the result of the request. Here are some important response codes:

### **1. 2xx (Success)**

- **200 OK**: The request was successful.
    - Example: `GET /users` → Returns a list of users.
- **201 Created**: The request was successful, and a new resource was created.
    - Example: `POST /users` → Creates a new user.

### **2. 4xx (Client Errors)**

- **400 Bad Request**: The request was malformed or invalid.
    - Example: `POST /users` with missing required fields.
- **401 Unauthorized**: The user is not authenticated (e.g., missing or invalid credentials).
    - Example: Trying to access user data without logging in.
- **404 Not Found**: The requested resource could not be found.
    - Example: `GET /users/12345` → No user found with ID 12345.
- **405 Method Not Allowed**: The HTTP method is not allowed for the resource.
    - Example: `DELETE /users` on a read-only API.

### **3. 5xx (Server Errors)**

- **500 Internal Server Error**: Something went wrong on the server.
    - Example: A bug in the server-side code or database issues.
- **502 Bad Gateway**: The server received an invalid response from an upstream server.
- **503 Service Unavailable**: The server is temporarily unavailable, usually due to being overloaded or under maintenance.

---

## **Request and Response Flow**

1. **Client sends a request**: A user interacts with the frontend (e.g., clicks a button), which sends an HTTP request to the backend (e.g., API call).
    
2. **Backend processes the request**: The backend server receives the request, performs necessary logic (e.g., retrieves data from the database), and prepares a response.
    
3. **Backend sends a response**: The server sends a response back to the client with the appropriate status code and data (if applicable).
    
4. **Client displays the response**: The frontend interprets the response (e.g., showing the data on the webpage or displaying an error message).
    

---

## **Serverless Architecture**

- **Serverless** doesn’t mean there are no servers. It means you don't have to manage the servers. The cloud provider automatically manages the infrastructure for you.
- **AWS Lambda** is a popular serverless option. You can write functions (e.g., process payment, send email) and deploy them without worrying about the underlying server.

### **Advantages of Serverless**:

1. **Scalability**: Automatically scales based on demand.
2. **Cost-Effective**: You only pay for the execution time of the functions.
3. **No Infrastructure Management**: No need to worry about servers or maintenance.

---

## **Understanding Web Frameworks**

- **Web frameworks** like **Spring Boot**, **Express.js**, or **Django** help in creating web applications quickly. These frameworks provide predefined templates and tools, saving you from writing a lot of boilerplate code.
    
    - **Spring Boot**: A Java-based framework that helps you build backend services.
    - **Express.js**: A minimal and flexible Node.js framework for building APIs.
    - **Django**: A Python framework that promotes rapid development.

---

## **Building APIs and Databases**

Backend systems often need to interact with databases to store and retrieve data. Some popular databases include:

### **1. Relational Databases (SQL)**

- **Examples**: MySQL, PostgreSQL, SQLite
- **Use**: Structured data, tables, and relationships between tables (e.g., users and orders).

### **2. NoSQL Databases**

- **Examples**: MongoDB, Redis, Cassandra
- **Use**: Unstructured or semi-structured data, fast access, and flexible schemas.

---

## **Security in Backend Development**

Security is a critical aspect of backend development. Some common practices include:

- **Authentication**: Verifying the identity of a user (e.g., JWT, OAuth).
- **Authorization**: Ensuring a user has permission to access a resource (e.g., checking roles like admin or user).
- **Data Validation**: Ensuring incoming data is valid and safe before processing it (e.g., using input sanitization to prevent SQL injection).

---

