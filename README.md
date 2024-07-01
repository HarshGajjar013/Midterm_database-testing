# Midterm Assignment - Database Testing
#### SENG8071

## Team Member Details
- Harshil Patel - 8881398 
- Manpreet Kaur - 8974681
- Harsh Gajjar - 8968603

## Team Member Duties
- **Manpreet**: Database schema design.
- **Harshil and Manpreet**: SQL query development.
- **Harshil and Harsh**: TypeScript interface creation.
- **Harsh and Harshil**: Testing and validation.
- **Manpreet**: Documentation.

## Database Schema

### Authors Table
| Attribute     | Type        |
| ------------- | ----------- |
| author_id     | SERIAL      |
| name          | VARCHAR(100)|
| biography     | TEXT        |
| date_of_birth | DATE        |

### Publishers Table
| Attribute     | Type        |
| ------------- | ----------- |
| publisher_id  | SERIAL      |
| name          | VARCHAR(100)|
| address       | TEXT        |

### Books Table
| Attribute         | Type               |
| ----------------- | ------------------ |
| book_id           | SERIAL             |
| title             | VARCHAR(255)       |
| genre             | VARCHAR(50)        |
| author_id         | INT                |
| publisher_id      | INT                |
| publication_date  | DATE               |
| type              | VARCHAR(10)        |
| price             | DECIMAL(10, 2)     |

### Customers Table
| Attribute        | Type               |
| ---------------- | ------------------ |
| customer_id      | SERIAL             |
| name             | VARCHAR(100)       |
| email            | VARCHAR(100)       |
| password         | VARCHAR(255)       |
| registration_date| DATE               |
| total_spent      | DECIMAL(10, 2)     |

### Reviews Table
| Attribute   | Type          |
| ----------- | ------------- |
| review_id   | SERIAL        |
| book_id     | INT           |
| customer_id | INT           |
| rating      | INT           |
| comment     | TEXT          |
| review_date | DATE          |

### Sales Table
| Attribute   | Type          |
| ----------- | ------------- |
| sale_id     | SERIAL        |
| book_id     | INT           |
| customer_id | INT           |
| sale_date   | DATE          |
| amount      | DECIMAL(10, 2)|

## SQL DDL

```sql
CREATE TABLE Authors (
    author_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    biography TEXT,
    date_of_birth DATE
);

CREATE TABLE Publishers (
    publisher_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    address TEXT
);

CREATE TABLE Books (
    book_id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    genre VARCHAR(50),
    author_id INT,
    publisher_id INT,
    publication_date DATE,
    type VARCHAR(10) CHECK (type IN ('Physical', 'Ebook', 'Audiobook')),
    price DECIMAL(10, 2),
    FOREIGN KEY (author_id) REFERENCES Authors(author_id),
    FOREIGN KEY (publisher_id) REFERENCES Publishers(publisher_id)
);

CREATE TABLE Customers (
    customer_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    registration_date DATE,
    total_spent DECIMAL(10, 2) DEFAULT 0.00
);

CREATE TABLE Reviews (
    review_id SERIAL PRIMARY KEY,
    book_id INT,
    customer_id INT,
    rating INT CHECK (rating BETWEEN 1 AND 5),
    comment TEXT,
    review_date DATE,
    FOREIGN KEY (book_id) REFERENCES Books(book_id),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

CREATE TABLE Sales (
    sale_id SERIAL PRIMARY KEY,
    book_id INT,
    customer_id INT,
    sale_date DATE,
    amount DECIMAL(10, 2),
    FOREIGN KEY (book_id) REFERENCES Books(book_id),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

```
