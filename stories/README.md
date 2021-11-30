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
