# **1. Project Overview**

***Project Name: ProductManagement***

## Purpose:
The ProductManagement system helps you efficiently track and manage various products stored in a warehouse. It provides a simple interface to maintain product information and monitor stock levels.

## Key Features:

Keep track of products in the warehouse.

Perform basic CRUD (Create, Read, Update, Delete) operations on products.

Option to mark products as publicly visible or private.

# **2. Objectives**

Provide a user-friendly system to manage product inventory.

Allow users to securely store their credentials.

Enable real-time tracking and updates of product quantities.

Support visibility control for products (public/private).

# **3. Functional Requirements**

User Authentication: Users can register and log in using secure credentials.

Product Management (CRUD):

>**Create:** Add new products with quantity, type, and visibility.
>**Read:** View products owned by the user
>**Update:** Modify product details such as quantity or type.
>**Delete:** Remove products from the system.
>**Public Visibility:** Users can choose to display products publicly.

# **4. Database Architecture**

The system uses a relational database with two primary tables:

## 4.1 Users Table

Stores user authentication details.

| Column  | Name	| Type	| Description |
|:---|:---:|:---:|:---:|
| username	| VARCHAR| 	Unique | username for login |
| password	| VARCHAR	| Hashed | password for security |


## 4.2 Products Table

Stores product details associated with each user.

| Column Name      | Type      | Description                                  |
|-----------------|----------|----------------------------------------------|
| username        | VARCHAR  | The user who owns the product               |
| product         | VARCHAR  | Name of the product                          |
| quantity        | INT      | Quantity of the product                      |
| type            | VARCHAR  | Type or category of the product              |
| display_publicly| BOOLEAN  | Whether the product is visible publicly (Yes/No) |
| timestamp       | TIMESTAMP| Default timestamp of product creation       |


# **5. System Architecture**

## Overview:

The application uses a client-server architecture.

Users interact with a frontend interface (web or desktop) to perform CRUD operations.

The backend handles authentication, authorization, and database operations.

## Data Flow:

User logs in → backend validates credentials against the Users table.

Authenticated users perform CRUD operations on Products table.

System updates product records and timestamps automatically.

Public products are available for viewing depending on the display_publicly flag.

## Commands to run project
From the root project directory navigate to backend
```bash
cd backend
```

Run the project using the following commands:
```bash
npm install
npm install dependencies
npm run start
```

## Security details of the project
The application is using hashing before storing the passwords. As hashing is one-way funtion, even some attackers breached the database and get the credentials, they will be unable to login using them.

Also, the application uses **JWT** to provide security over unautharized users. This makes the application does not repond with apis with usernames anymore. It builds standard session  keys with expiration time to avoid unautharized access.
