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

