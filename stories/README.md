# Stories

## Register a user

|Use Case UC-1: |Register a user|
|-------------|-------------|
|Initiating Actor:     |Admin |
|Actor’s Goal:         |Register a customer to use the bank      |
|Participating Actors: |Customer, bank |
|Preconditions:        |The bank has an admin; The admin is logged in |
|Postconditions:       |The user exists in the system database |

Flow of Events for Main Success Scenario:

| | | |
|-------------|-------------|-------------|
| →  | 1.  |The admin clicks "create a new account" button|
| ←  | 2.  |The new account view is displayed |
| →  | 3.  |The admin enters user information: ID, email, password, name, surname, phone number|
| →  | 4.  |The admin clicks "submit" button|
| ←  | 5.  |The user is persisted in the database|

Flow of Events for Extensions (Alternate Scenarios): What could go wrong? List the exceptions to the routine and describe how they are handled

| | | |
|-------------|-------------|-------------|
| → | 1a. |The admin leaves some fields blank |
| ← | 1b. |The system displays an error message|

## Open an account

|Use Case UC-2: |Open an account|
|-------------|-------------|
|Initiating Actor:     |Admin |
|Actor’s Goal:         |Create an account for a user|
|Participating Actors: |Customer, bank |
|Preconditions:        |The bank has an admin; The admin is logged in |
|Postconditions:       |The account exists in the system database; The user can access their account|

Flow of Events for Main Success Scenario:

| | | |
|-------------|-------------|-------------|
| →  | 1.  |The admin clicks "create a new account" button|
| ←  | 2.  |The new account view is displayed |
| →  | 3.  |The admin enters user information|
| →  | 4.  |The admin clicks "submit" button|
| ←  | 5.  |The account is persisted in the database with a new ID, IBAN, open date, balance (default: 0) and an empty list of transactions|

Flow of Events for Extensions (Alternate Scenarios): What could go wrong? List the exceptions to the routine and describe how they are handled

| | | |
|-------------|-------------|-------------|
| → | 1a. |The admin leaves some user information fields blank |
| ← | 1b. |The system displays an error message|

The arrows on the left indicate the direction of interaction: → Actor’s action; ← System’s reaction





## Make a transfer (same currency) as a customer

|Use Case UC-3: |Make a transfer|
|-------------|-------------|
|Initiating Actor:     |Customer |
|Actor’s Goal:         |Make a transfer from my account to another account|
|Participating Actors: |Bank |
|Preconditions:        |Customer has an account; Customer has logged in |
|Postconditions:       |The customer has successfully made a transfer. |

Flow of Events for Main Success Scenario:

| | | |
|-------------|-------------|-------------|
| →  | 1.  | Customer logs into the system using her email and password. |
| ←  | 2.  | The system opens the main page.|
| →  | 3.  | Customer clicks on a “make new transfer” button. |
| ←  | 4.  | The system opens the money transfer form. |
| →  | 5.  | Customer enters recipient information (either phone number, email, IBAN), amount to transfer, currency from, currency to, description. |
| →  | 6.  | Customer clicks on the “Transfer” button. |
| ←  | 7.  | The system alerts about a new successful transfer.|

Flow of Events for Extensions (Alternate Scenarios): What could go wrong? List the exceptions to the routine and describe how they are handled

| | | |
|-------------|-------------|-------------|
| → | 5a. |The system message that some required field is not filled.|
| → | 5b. |The receiver's phone number, email, IBAN does not exist, is incorrect or is unavailable|
| → | 5c. |There is not enough money on sender’s account. |
| ← | 5d. |The system displays an error message.|

The arrows on the left indicate the direction of interaction: → Actor’s action; ← System’s reaction



## Make a transfer (different currencies) as a customer

|Use Case UC-4: |Make a transfer|
|-------------|-------------|
|Initiating Actor:     |Customer |
|Actor’s Goal:         |Make a transfer from my account to another account|
|Participating Actors: |Bank |
|Preconditions:        |Customer has an account; Customer has logged in |
|Postconditions:       |The customer has successfully made a transfer to different currency. |

Flow of Events for Main Success Scenario:

| | | |
|-------------|-------------|-------------|
| →  | 1.  | Customer logs into the system using her email and password. |
| ←  | 2.  | The system opens the main page.|
| →  | 3.  | Customer clicks on a “make new transfer” button. |
| ←  | 4.  | The system opens the money transfer form. |
| →  | 5.  | Customer enters recipient information (either phone number, email, IBAN), amount to transfer, currency from, currency to, description. |
| →  | 6.  | Customer clicks on the “Transfer” button. |
| ←  | 7.  | The system converts the currency.|
| ←  | 8.  | The system alerts about a new successful transfer.|

Flow of Events for Extensions (Alternate Scenarios): What could go wrong? List the exceptions to the routine and describe how they are handled

| | | |
|-------------|-------------|-------------|
| → | 5a. |The system message that some required field is not filled.|
| → | 5b. |The receiver's phone number, email, IBAN does not exist, is incorrect or is unavailable|
| → | 5c. |There is not enough money on sender’s account. |
| → | 7a. |System does not have the possibility to convert this currency. |
| ← | 7b. |The system displays an error message.|

The arrows on the left indicate the direction of interaction: → Actor’s action; ← System’s reaction



## Player to player (p2p) payment (QR code transfer)

|Use Case number: | UC-5 |
|-------------|-------------|
|Initiating Actor:     |Customer |
|Actor’s Goal:         |Sender successfully transfers money to a receiver |
|Participating Actors: |bank |
|Preconditions:        | - Both a sender and a receiver is logged in. <br> - Both customers are using mobile app for this action|
|Postconditions:       | - A receiver receives money from a sender. <br> - Both customers receive notification after the transaction |

Flow of Events for Main Success Scenario:

| | |
|-------------|-------------|
| 1.  |As a reciever, I log in to my account on my mobile app|
| 2.  |As a sender, I log in to my account on my mobile app |
| 3.  |As a sender, I go to the page that I can make p2p payment |
| 4.  |As a sender, I fill the required information <br> - Amount of the money to send <br> - The account information about the receiver <br> - The title and description about the transaction |
| 5.  |As a sender, I see a QR code on my phone |
| 6.  |As a reciever, I scan the QR code with my phone through the QR code reader on the mobile app |
| 7.  |As a reciever and sender, there is a sign that the transaction was completed on our phones. |
| 8.  |As a reciever and sender, an invoice of its transaction is sent within 5 seconds. |

Alternative flow:

| | |
|-------------|-------------|
| 5a. |If there is enough money in the sender's balance, an error message is popped out and prevents the transaction|
| 5b. |If the typed receiver's information is not valid, an error message is popped out and prevents the transaction|



## Adding money to the account as an admin (trading customer cash)

|Use Case number: | UC-6 |
|-------------|-------------|
|Initiating Actor:     |Admin |
|Actor’s Goal:         |Admin adds money to a customer's account|
|Participating Actors: |Customer, bank |
|Preconditions:        | - The bank has an admin <br> - The admin is logged in |
|Postconditions:       | - A customer already created an account in the bank |

Flow of Events for Main Success Scenario:

| | |
|-------------|-------------|
| 1.  |As an Admin, I log in to my account on my mobile app|
| 2.  |As an Admin, I search an account the customer has by referencing the account number |
| 3.  |As an Admin, I found the account on my screen |
| 4.  |As an Admin, I type the amount of cash the customer gave me. |
| 5.  |As an Admin, I click th "submit" button to make the transaction. |
| 6.  |As an Admin, I click "check the balance" so that I can confirm the transaction was successfully conducted.

Alternative flow:

| | |
|-------------|-------------|
| 3a-1. |If a cutomer doesn't know his or her account number, as an Adminitraotr, I type "last name", "first name", "Date of birth" to get the customer account. |
| 3a-2. |As an administrator, I find the correct account that the customer wants to add the money. |
