## 1. List the commands for adding, updating, and deleting data
- Adding: INSERT INTO
- Updating: UPDATE
- Deleting: DELETE FROM

## 2. Explain the structure for each type of command.
- INSERT INTO requires the table, in which new rows will be inserted into. VALUES determines what the values of the new rows will be. Optionally, the columns can be explicitly stated and the values will be in the same order.
- UPDATE requires the table from which a row or rows will be updated. SET controls what the value of the selected column will be. WHERE determines which rows will be updated
- DELETE FROM requires the table from which a row(s) will be deleted from. WHERE determines which rows will be deleted, if it satisfies the conditions

## 3. What are some the data types that can be used in tables? Give a real world example of each.
- Text could be used to store the image reference for a product
- Timestamp is used for when a row was created at or last updated at
- Integer could be used for enums, such as roles for users on a system

## 4. Think through how to create a new table to hold a list of people invited to a wedding. This table needs to have first and last name, whether they sent in their RSVP, the number of guests they are bringing, and the number of meals (1 for adults and 1/2 for children).

### a. Which data type would you use to store each of the following pieces of information?
| column            | data type |
| ----------------- | --------- |
| First & last name | text      |
| RSVP              | boolean   |
| Guests            | float     |
| Meals             | integer   |

### b. Write a command that makes the table to track the wedding.

```sql
CREATE TABLE wedding_guests (
  first_name text,
  last_name text,
  rsvp boolean,
  guests float,
  meals integer
);
```
### c. Using the table we just created, write a command that adds a column to track whether they were sent a thank you card.

```sql
ALTER TABLE wedding_guests ADD COLUMN thank_you_card boolean;
```

### d. You have decided to move the data about the meals to another table, so write a command to remove the column storing the number meals from the wedding table.

```sql
ALTER TABLE wedding_guests DROP COLUMN meals boolean;
```

### e. The guests are going to need a place to sit at the reception, so write a command that adds a column for table number.

```sql
ALTER TABLE wedding_guests ADD COLUMN table_number integer;
```

### f. The wedding is over and we do not need to keep this information, so write a command that deletes the wedding table from the database.

```sql
DROP TABLE wedding_guests;
```

## 5. Write a command to make a new table to hold the books in a library with the columns ISBN, title, author, genre, publishing date, number of copies, and available copies.

```sql
CREATE TABLE books(
  isbn text,
  title text,
  author text,
  genre text,
  publishing_date date,
  number_of_copies integer,
  available_copies integer
);
```

### a. Find three books and add their information to the table.
```sql
INSERT INTO books (isbn, title, author, genre, publishing_date, number_of_copies, available_copies)
VALUES
('978-0241950432', 'The Catcher in the Rye', 'J. D. Salinger', 'Coming-of-age fiction', DATE '1951', 10, 10),
('978-1934356340', 'The Passionate Programmer', 'Chad Fowler', 'Computer Science', DATE '2009', 5, 5),
('978-1607747307', 'The Life Changing Magic of Tidying Up', 'Marie Kondō', 'Self-help', DATE '2014', 15, 3);
```

### b. Someone has just checked out one of the books. Change the available copies column to 1 fewer.

```sql
UPDATE books SET available_copies = 4 WHERE isbn = '978-1934356340';
```

### c. Now one of the books has been added to the banned books list. Remove it from the table.

```sql
DELETE FROM books WHERE title = 'The Catcher in the Rye';
```

## 6. Write a command to make a new table to hold spacecrafts. Information should include id, name, year launched, country of origin, a brief description of the mission, orbiting body, if it is currently operating, and approximate miles from Earth. In addition to the table creation, provide commands that perform the following operations:

```sql
CREATE TABLE spacecrafts (
  id integer,
  name text,
  year_launched date,
  country_of_origin text,
  description text,
  orbiting_body text,
  operational boolean,
  million_miles_from_earth float
);
```

### a. Add 3 non-Earth-orbiting satellites to the table.
```sql
INSERT INTO spacecrafts (id, name, year_launched, country_of_origin, description, orbiting_body, operational, million_miles_from_earth)
VALUES
(1, '2001 Mars Odyssey', DATE '2001', 'USA', 'Detect evidence of past or present water and ice', 'Mars', TRUE, 2),
(2, 'Luna 10', DATE '1966', 'Soviet Union', 'First artificial satellite of the moon', 'Moon', FALSE, 0.238),
(3, 'Akatsuki', DATE '2010', 'Japan', 'Study the atmosphere of Venus', 'Venus', TRUE, 162);
```

### b. Remove one of the satellites from the table since it has just been crashed into the planet.

```sql
DELETE FROM spacecrafts WHERE id = 2;
```

### c. Edit another satellite because it is no longer operating and change the value to reflect that.

```sql
UPDATE spacecrafts SET operational = FALSE WHERE id = 3;
```

## 7. Write a command to make a new table to hold the emails in your inbox. This table should include an id, the subject line, the sender, any additional recipients, the body of the email, the timestamp, whether or not it’s been read, and the id of the email chain it’s in. Also provide commands that perform the following operations:

```sql
CREATE TABLE emails (
  id integer,
  subject_line text,
  sender text,
  additional_recipients text,
  body text,
  timestamp timestamp,
  read boolean DEFAULT FALSE,
  email_chain_id integer
);
```

### a. Add 3 new emails to the inbox.

```sql
INSERT INTO emails (id, subject_line, sender, additional_recipients, body, timestamp, email_chain_id)
VALUES
(1, 'Urgent! Please Read Carefully', 'noreply@example.com', '', 'You have been selected to participate in the...', TIMESTAMP '2018-12-30 10:00:15', NULL),
(2, 'Have some fresh tasty spam', 'spam@not.spam', 'other@not.spam', 'By reading this email, you have made a great choice...', TIMESTAMP '2018-12-31 23:59:00', FALSE, NULL),
(3, 'Not Spam I swear', 'spam@not.spam', '', 'Try our new Spam!', TIMESTAMP '2019-1-1 00:00:01', FALSE, 2);
```

### b. You’ve just deleted one of the emails, so write a command to remove the row from the inbox table.

```sql
DELETE FROM emails WHERE id = 3;
```

### c. You started reading an email but just heard a crash in another room. Mark the email as unread before investigating, so you can come back to it later.

```sql
UPDATE emails SET read = FALSE WHERE id = 1;
```
