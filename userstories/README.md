# Userstories

## Customer

### Login

As a customer, I want to be able to log into the website, so I can access my account. 

**Acceptance criteria:**
1. On entering the correct email and password, I should be redirected to my customer dashboard.
2. On entering an incorrect email or password, I should be alerted to the invalid information.

### Logout

As a customer, I want to be able to log out, so others can't access my account later.

**Acceptance criteria:**
1. On clicking log out, my session is terminated.

### View my accounts

As a customer, I want to view my accounts, so that I could select an account and see its info.

**Notes:**

Should include this info:
- Account IBAN
- Account balance

### View account information

As a customer, I want to view account information, so that I could check account balance and transfers.

**Notes:**

Should include this info:
- Account IBAN
- Account balance
- Account transfers

### Make a transfer

As a customer, I want to be able to make a transfer, so I can pay other people.

**Notes:**

The transfer should include:
- Receiver (see below)
- Description
- Amount

The receiver can be:
- Phone number (uses primary account)
- Email (uses primary account)
- IBAN (refers to specific account)

**Acceptance criteria:**
1. If I have more or equal money to the amount and the receiver is valid, if I click send, a new transfer will be made.
2. If I have don't have more or equal money to the amount or the receiver is invalid, if I click send, the application will alert me to the error.

### View my transfers

As a customer, I want to be able to view all my transfers, so I know where my money is going.

**Notes:**

Transfer list should include:
- Timestamp
- Receiver
- Status
- Description
- Amount

**Acceptance criteria:**
1. If I am logged in and on the transfers page, I should see all my transfers.

### Request transfer with QR code

As a customer, I want to be able to generate a QR code with transfer information, so the paying party can pay me as fast as possible with their mobile device.

**Notes:**

The QR code should include:
- Receiver
- Amount
- Description

Can be generated on desktop and mobile.

### Make a transfer with QR code

As a customer, I want to be able to make a transfer by scanning a QR code, so I can pay people easier. 

**Notes:**
- QR code should fill fields in the transfer form, but not immediately send it. 
- The customer needs to be able to verify the information. 

For mobile only.

### Request transfer

As a customer, I want to be able to request other people transfers, so I can remind them to pay me. 

**Notes:**

The transfer request should include:
- Requested sender
- Amount

**Acceptance criteria:**
1. If the amount is positive and the requested sender exists, a request for transfer will be sent to him.

## Admininstrator

### Login

As an administrator, I want to be able to log into the website, so I can manage customers.

**Acceptance criteria:**
1. On entering the correct email and password, I should be redirected to my admin dashboard.
2. On entering an incorrect email or password, I should be alerted to the invalid information.

### Logout

As an administrator, I want to be able to log out, so others can't access my account later.

**Acceptance criteria:**
1. On clicking log out, my session is terminated. 

### View all accounts

As an administrator, I want to view all customers accounts, so that I could select an account and view its info.

**Notes:**

Should include this info:
- Customer ID
- Customer Name and Surname
- Account ID
- Account name
- Account balance

**Acceptance criteria:**
1. By selecting a customer, it should display customers information.

### View account info

As an administrator, I want to view account info, so that I could check account balance and transactions.

**Notes:**

Should include this info:
- Account ID
- Account name
- Account open date
- Account balance
- Account's transactions

**Acceptance criteria:**
1. By selecting an account, it should display account information.

### Create a new account

As an administrator, I want to create new accounts so that other users can use the banking system.

**Notes:**
- This process also creates a new user that is assigned to the account (see below).
- It should create a unique ID for each user account.
- It should also save the account opening date.
- Newly created accounts balance should be 0.

User details:
- ID
- Email
- Password
- Name, Surname
- Phone number
- Primary account

**Acceptance criteria:**
1. By submitting account information, the account should exist in the database.

### Close account

As an administrator, I want to close an account so that I can clear up unused user accounts.

**Acceptance criteria:**
1. By initiating account deletion, it should ask for confirmation, and if the admin confirms it, then the user account should be marked as closed in the database.

### Add money to account

As an administrator, I want to add money to user accounts so that users can make new transactions and use the banking system.

**Acceptance criteria:**
1. If I am logged in as admin and I select an account I want to send money to, I insert the amount and click add, the money should be added to his account.

### View all transactions

As an administrator, I want to be able to view all transactions of the system so that I could perform operations with them.

**Acceptance criteria:**
1. Should display all existing transactions.

### View account's transactions

As an administrator, I want to be able to view account's transactions, so that I could perform operations with them.

**Notes:**

Should include this info:
- Transaction ID
- Debit account ID
- Credit account ID
- Transaction amount
- Status
  1. *empty*
  2. CORRECTION
  3. STORNED
  4. STORNO
- TimeStamp

Possible operations:
- Edit
- Storno

**Acceptance criteria:**
1. All transactions should be shown.
2. Deleted transactions should not be visible.

### Edit transaction

As an administrator, I want to be able to edit a transaction, so that I could manually fix some problems.

**Notes:**

Editable info:
- Timestamp
- Amount
Should trigger update for balances and transfers.

**Acceptance criteria:**
1. Should allow to edit only those fields mentioned in this requirement.
2. Immediately after edit changed info should be visible.
3. Customer should be able to see updated balance and transfer info.
4. If after edit, account balance becomes negative, the customer should not be able to transfer money. Error should be showed: "Not enough funds".

### Storno transaction

As an administrator, I want to be able to storno (revert) a transaction, so that I could manually fix some problems.

**Notes:**
- Should not allow to storno transaction with status STORNED or STORNO
- Should create new reverted transition with status STORNO. New transaction:
  + Transaction ID = *new
  + Debit account ID = storned transaction's Credit account ID
  + Credit account ID = storned transaction's Debit account ID
  + Transaction amount = storned transaction amount
  + Status = STORNO
  + Timestamp = *new
- Should set status to STORNED for current transaction.

**Acceptance criteria:**
1. After Storno operation, newly created Storno transaction should become visible.
2. After Storno operation, Storned transaction should get status STORNED.
3. Customer should be able to see updated balance and transfer info.
4. If after edit, account balance becomes negative, the customer should not be able to transfer money. Error should be displayed: "Not enough funds".
