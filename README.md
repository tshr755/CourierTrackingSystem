# Courier Tracking System

## Overview
This project is a menu-based console application designed to simulate a courier tracking system. The application allows users to track parcels, manage delivery status, and update customer information. It demonstrates proficiency in Core Java, MySQL, and JDBC.

## Functionalities
1. **Parcel Tracking**:
   - Enter parcel tracking number to get status updates.
   - View detailed information about the parcel's journey.
   - Receive notifications for key status changes.

2. **Delivery Status Management**:
   - Update delivery status for parcels.
   - View delivery history for parcels.
   - Calculate estimated delivery times.

3. **Customer Information Management**:
   - Register new customers.
   - View customer details.
   - Update customer information.
   - Delete customer accounts.

## Database Schema
### Parcel Table
- `parcel_id` (Primary Key)
- `tracking_number`
- `sender_name`
- `sender_address`
- `recipient_name`
- `recipient_address`
- `current_status`
- `delivery_history`

### Customer Table
- `customer_id` (Primary Key)
- `customer_name`
- `email`
- `phone_number`

### CustomerParcels Table
- `customer_id` (Foreign Key references `customers.customer_id`)
- `parcel_id` (Foreign Key references `parcels.parcel_id`)

## Setup Instructions

### Prerequisites
- Java Development Kit (JDK) installed
- MySQL database installed and running
- MySQL JDBC driver added to your project's classpath

### Database Setup
1. Create a MySQL database named `courier_tracking`.
2. Run the following SQL script to create the necessary tables:

    ```sql
    -- Create the 'parcels' table
    CREATE TABLE parcels (
        parcel_id INT AUTO_INCREMENT PRIMARY KEY,
        tracking_number VARCHAR(50) NOT NULL,
        sender_name VARCHAR(100) NOT NULL,
        sender_address VARCHAR(255) NOT NULL,
        recipient_name VARCHAR(100) NOT NULL,
        recipient_address VARCHAR(255) NOT NULL,
        current_status VARCHAR(100) NOT NULL,
        delivery_history TEXT
    );

    -- Create the 'customers' table
    CREATE TABLE customers (
        customer_id INT AUTO_INCREMENT PRIMARY KEY,
        customer_name VARCHAR(100) NOT NULL,
        email VARCHAR(100) NOT NULL,
        phone_number VARCHAR(20) NOT NULL
    );

    -- Create the 'CustomerParcels' table
    CREATE TABLE CustomerParcels (
        customer_id INT,
        parcel_id INT,
        FOREIGN KEY (customer_id) REFERENCES customers(customer_id),
        FOREIGN KEY (parcel_id) REFERENCES parcels(parcel_id)
    );
    ```

### Application Setup
1. Clone the repository:
    ```bash
    git clone https://github.com/tshr755/courier-tracking-system.git
    cd courier-tracking-system
    ```

2. Compile the Java source files:
    ```bash
    javac -cp .:path_to_mysql_connector/mysql-connector-java-x.x.xx.jar Nus.java
    ```

3. Run the application:
    ```bash
    java -cp .:path_to_mysql_connector/mysql-connector-java-x.x.xx.jar Nus
    ```

### Configuration
- Update the `DB_URL`, `USER`, and `PASSWORD` constants in the `Nus` class with your MySQL database details.

## Usage
1. Run the application using the setup instructions.
2. Follow the on-screen menu options to interact with the system:
   - Track parcels
   - Manage delivery status
   - Manage customer information

## Error Handling
The application includes basic error handling to ensure user-friendly error messages. Exceptions related to database operations are caught and displayed appropriately.

## Contribution
Feel free to fork the repository and submit pull requests. Contributions are welcome!

## License
This project is licensed under the MIT License.

## Contact
For any questions or suggestions, please contact [tushar.slrn@gmail.com].
# CourierTrackingSystem
