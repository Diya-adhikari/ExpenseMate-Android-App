 # ExpenseMate - Personal Expense Tracker (Android)

ExpenseMate is a native Android application designed to help users **record daily income and expenses**, organize transactions into categories, set **monthly or category-level budgets**, and view **financial summaries**.  
All data is stored locally using the **Room persistence library (SQLite abstraction)**, ensuring privacy and offline usability.

---

## Project Overview

- **Project Type:** Android Personal Expense Tracker  
- **Platform:** Android (Native)  
- **Primary Language:** Java  
- **UI Layer:** XML + Material Design  
- **Database:** Room (SQLite abstraction)  
- **Minimum SDK:** API 24 (Android 7.0 Nougat)  
- **Package Name:** `com.example.expensemate`
---
##  Objectives

1. Record income and expenses  
2. Manage transactions (add, edit, delete)  
3. Categorize every transaction  
4. Track account balance  
5. Monitor monthly spending  
6. Search and filter transactions  
7. Define and manage budgets  
8. View financial summaries (income, expense, savings, category breakdown)  
9. Maintain user-specific isolated data  

---

## Features

- **Authentication:** Registration, login, logout, session management  
- **Dashboard:** Balance, total income, total expense, recent transactions  
- **Transactions:** Add, edit, delete, view history  
- **Categories:** Fixed sets for income & expense (Food, Transport, Salary, Freelance, etc.)  
- **Search & Filtering:** Keyword search, filter by category/type/month, sorting  
- **Reports:** Monthly totals, savings, category-wise breakdown  
- **Budget:** Monthly & category-level budgets, warnings when exceeded  
- **Notifications:** Budget alerts, reminders to log transactions  
- **Profile Management:** View & edit user profile

---
## System Architecture

ExpenseMate follows a **layered architecture**:

- **UI Layer:** XML layouts (screens, buttons, RecyclerViews)  
- **Activity / Adapter Layer:** Handles user interactions & binds data to views  
- **Database Access Layer (DAO):** CRUD + query methods  
- **Room Database:** Stores entities (User, Transaction, Budget)  

---

## Database Design

### Entities
- **User:** `userId`, `name`, `email`, `passwordHash`, `phone`  
- **Transaction:** `transactionId`, `userId`, `type`, `amount`, `category`, `description`, `date`, `paymentMethod`  
- **Budget:** `budgetId`, `userId`, `category`, `amount`, `month`  

### Relationships
- One-to-many: **User → Transactions**  
- One-to-many: **User → Budgets**

---

---

##  Security

- Passwords stored as **hashed values** (not plain text)  
- All queries scoped to **logged-in userId**  
- No cross-user data access  

---

## User Roles

ExpenseMate currently supports a single application role: **Normal User**.  
No administrative role is implemented in the current version, since the app is designed as a **single-user, on-device finance tracker** rather than a multi-tenant managed system.

### Normal User Capabilities
A registered user can:
- Register a new account  
- Log in and log out  
- Manage their own profile  
- Add, edit, and delete their own transactions  
- View only their own transactions  
- Search and filter only within their own data  
- Create and manage their own budgets  
- View summaries computed from their own data  

>  **Data Isolation:**  
Every query in the data layer is scoped by the logged-in `userId`, ensuring that a user can **never read or modify another user’s records** through normal application flows.



