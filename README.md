# README.md

## Console Banking Application

### Admin Credentials
- **Username:** `admin`
- **Password:** `adminPass`

### Files
- **Account Requests:** `existingRequests.txt`
- **Existing Accounts & History:** `existingAccount.txt`
- **Deletion Requests:** `deletionRequests.txt`

### Overview

The application provides a simple banking system through console interaction. Users can register, log in, and manage their transactions. Admins can view and approve account creation/deletion requests and all existing users, along with their specific user information.

### Main Menu
```
——————————
Welcome to the best banking app!
(1) New user registration
(2) Existing user login
(3) Admin access
(4) Exit program
——————————
Choose an option:
```

### New User Registration
```
——————————
Please fill out the following form:

Username:
Password:
Name:
Initial deposit (minimum $100):
Age:
Credit score:
——————————
```

### Existing User Login
```
——————————
Welcome back!

Please enter your credentials:

Username:
Password:
——————————
```

### Admin Access
```
——————————
Welcome Admin!

Please enter your credentials:

Username:
Password:
——————————
```

### Incorrect Credentials Alert
```
——————————

User with uch credentials do not exist..

Redirecting you back to main menu….

——————————
```

### Existing User Menu
```
——————————
Welcome back!
(1) Withdraw
(2) Deposit
(3) View transaction history
(4) Display balance
(5) Request account deletion
(6) Exit and return to main menu
Choose an option:
——————————
```

### Admin Menu
```
——————————
Welcome back!
(1) View account requests for creation
(2) View account requests for deletion
(3) Display existing accounts
(4) Approve account creation requests
(5) Approve account deletion requests
(6) Exit and return to the main menu
Choose an option:
——————————
```

### Main Classes

#### 1. `MainApp`
* **Description:** Entry point for the application.
* **Responsibilities:**
    * Displays the main menu and handles navigation to user, admin, or exit based on the user’s choice.
    * Utilizes the `UserManager` and `AdminManager` for user and admin-related operations.
* **Methods:**
    * `main(String[] args)`: Initializes the application and loops through the main menu options.

#### 2. `UserManager`
* **Description:** Handles operations related to user accounts, including registration, login, and transaction management.
* **Responsibilities:**
    * Manages new user registration, login, and session management.
    * Manages individual user transactions like deposits and withdrawals.
* **Methods:**
    * `handleNewUser()`: Registers a new user and saves the account request for approval.
    * `handleExistingUser()`: Authenticates an existing user and redirects to the user menu.
    * `showUserMenu(String username)`: Provides the user menu options for transactions, balance, and history.

#### 3. `AdminManager`
* **Description:** Manages admin functions such as approving new accounts, deleting accounts, and viewing accounts and requests.
* **Responsibilities:**
    * Authenticates admin credentials and provides the admin menu.
    * Manages approval of account creation and deletion requests.
* **Methods:**
    * `handleAdmin()`: Authenticates an admin and redirects to the admin menu.
    * `approveAccountCreation()`: Approves a new account request.
    * `approveAccountDeletion()`: Approves a request for account deletion.
    * `showAdminMenu()`: Displays the admin menu with account-related options.

#### 4. `Account`
* **Description:** Represents a user account with attributes like username, password, name, age, credit score, and balance.
* **Responsibilities:**
    * Manages individual user transactions like deposits and withdrawals.
    * Keeps a transaction history and provides account information.
* **Methods:**
    * `displayBalance()`: Displays the current balance.
    * `withdraw(double amount)`: Withdraws a specified amount from the balance.
    * `deposit(double amount)`: Deposits a specified amount to the balance.
    * `showHistory()`: Displays the transaction history.
    * `requestDeletion()`: Requests the deletion of the account.
    * `addTransaction(Transaction transaction)`: Adds a transaction to the transaction history.

#### 5. `Transaction`
* **Description:** Represents a transaction with attributes like type (deposit, withdrawal), amount, and date.
* **Responsibilities:**
    * Captures the details of a financial transaction.
* **Methods:**
    * `getType()`, `getAmount()`, `getDate()`: Getters for the transaction attributes.
    * `toString()`: Returns a formatted string representation of the transaction.

### Utility and Storage Classes

#### 1. `FileHandler`
* **Description:** Handles reading and writing to files (accounts, transactions, requests for creation and deletion).
* **Responsibilities:**
    * Ensures the existence of required files and handles data serialization.
    * Manages account requests, existing accounts, and deletion requests.
* **Methods:**
    * `ensureFilesExist()`: Ensures the necessary files are created.
    * `saveAccountRequest(Account account)`: Saves a new account request for approval.
    * `isDuplicateAccountRequest(String username)`: Checks for duplicate account creation requests.
    * `displayAccountRequests()`: Displays all pending account requests.
    * `displayDeletionRequests()`: Displays all pending deletion requests.
    * `displayExistingAccounts()`: Displays all existing accounts.
    * `removeAccount(String username)`: Deletes an existing account.
    * `saveDeletionRequest(String username)`: Requests an account for deletion.
    * `updateAccountBalance(Account account)`: Updates the balance of an existing account.
    * `loadAccountRequest(String username)`: Loads an account request by username.
    * `loadAccount(String username)`: Loads an existing account by username.
    * `saveExistingAccount(Account account)`: Saves an approved account to the existing accounts file.

#### 2. `Authentication`
* **Description:** Manages login procedures for users and the admin.
* **Responsibilities:**
    * Verifies credentials against stored data.
* **Methods:**
    * `verifyUserCredentials(String username, String password)`: Verifies a user's credentials.
    * `verifyAdminCredentials(String username, String password)`: Verifies an admin's credentials.
    * `isPendingApproval(String username)`: Checks if a username has a pending account request.

#### 3. `PasswordUtils`
* **Description:** Provides utilities for password security.
* **Responsibilities:**
    * Hashes passwords using SHA-256.
* **Methods:**
    * `hashPassword(String password)`: Hashes a password and returns its Base64 representation.



