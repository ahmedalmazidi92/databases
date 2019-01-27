## 1. What data types do each of these values represent?
| Values               | Data Types |
| -------------------- | ---------- |
| "A Clockwork Orange" | String     |
| 42                   | Integer    |
| 09/02/1945           | Date       |
| 98.7                 | Float      |
| $15.99               | Float      |

## 2. Explain in your own words when a database might be used. Explain when a text file might be used.
- A database is typically used to store large amounts of datasets, in order to be easily retrieved or queried. An app that collects saves user's information is a common use for a database
- A text file can be used to store data in an unordered fashion, and without any restriction on data types for the data themselves. Github personal tokens are typically stored in text files

## 3. Describe one difference between SQL and other programming languages.
- SQL is a declarative language, which means that the user indicates to the language what the outcome should look like
- Other programming languages typically let the user define each step in the process without explicitly stating what the outcome is.

## 4. In your own words, explain how the pieces of a database system fit together at a high level.
- A database contains tables, which themselves have columns and rows. Within each column and row intersection is a value, which is defined by the column it is in and belongs to the row in it is.

## 5. Explain the meaning of table, row, column, and value.
- Table = Stores data. Contains rows and columns, in which data is stored. It also provides the context of the data stored within it
- Row = The single unit of a table. For example, each row in a table named 'users' would provide users for a particular application
- Column = Provides context of the data displayed. For example, the column named 'name' in the 'users' table, provides the names of the users in the table
- Value = A piece of information that is defined by the column it is in. For example, the value 'Bob' under the column 'name' in the 'users' table, is the name of the user.

## 6. List 3 data types that can be used in a table.
1. String
2. Integer
3. Float

## 7. Given this payments table, provide an English description of the following queries and include their results:
     ```sql
     SELECT date, amount
     FROM payments;
     ```      
- Display all payments but only display the values from the date and amount columns
- Results:

| date       | amount  |
| ---------- | ------- |
| 2016-05-01 | 1500.00 |
| 2016-05-10 | 37.00   |
| 2016-05-15 | 124.93  |
| 2016-05-23 | 54.72   |
     ```sql
     SELECT amount
     FROM payments
     WHERE amount > 500;
     ```
- Display payments whose amount value is strictly above 500 from the payments table, but only display the values from the amount column
- Results:

| amount  |
| ------- |
| 1500.00 |
     ```sql
     SELECT *
     FROM payments
     WHERE payee = 'Mega Foods';
     ```
- Display payments where the payee value is 'Mega Foods', and display all values from every column
- Results:

| date       | payee        | amount | memo        |
| ---------- | ------------ | ------ | ----------- |
| 2016-05-15 | 'Mega Foods' | 124.93 | 'Groceries' |

## 8. Given this users table, write SQL queries using the following criteria and include the output:

- The email and sign-up date for the user named DeAndre Data.
```sql
SELECT email, signup
FROM users
WHERE name = 'DeAndre Data';
```
Results:

| email               | signup     |
| ------------------- | ---------- |
| 'datad@comcast.net' | 2008-01-20 |

- The user ID for the user with email 'aleesia.algorithm@uw.edu'.
```sql
SELECT userid
FROM users
WHERE email = 'aleesia.algorithm@uw.edu';
```
Results:

| userid |
| ------ |
| 1      |

- All the columns for the user ID equal to 4.
```sql
SELECT *
FROM users
WHERE userid = 4;
```
Results:

| userid | name             | email               | signup       |
| ------ | ---------------- | ------------------- | ------------ |
| 4      | 'Brandy Boolean' | 'bboolean@nasa.gov' | '1999-10-15' |
