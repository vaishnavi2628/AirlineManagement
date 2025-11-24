✈️ Airline Management System (ASimulator)
Overview
The Airline Management System is a desktop application used for airline management. This system provides an interface for managing flight schedules, passenger bookings, cancellations, and journey details. Built with Java Swing for the GUI and MySQL for database management, it provides solution for airline administrative tasks.
Features
Core Functionality

Flight Management

Add, update, and view flight schedules
Manage flight routes and timings
Track flight availability and capacity


Passenger Management

Add new passenger details
View passenger information
Update passenger details
we can filter and search for passenger data


Booking System

Book flights for passengers
View booking history
Check seat availability
Generate booking confirmations


Cancellation Management

Cancel existing bookings
Process refunds
Update passenger records
View cancellation history


Journey Details

View complete journey information
Track flight status
Display route details
Show passenger itinerary



Additional Features

User-friendly GUI with intuitive navigation
Real-time data updates
Secure database connectivity
Date picker integration for easy date selection
Comprehensive error handling

Technologies/Tools Used
Programming Languages & Frameworks

Java 8 - Core programming language
Java Swing - GUI framework
JDBC - Database connectivity

Database

MySQL - Relational database management system

Development Tools

Eclipse IDE - Integrated Development Environment
Apache Ant - Build automation tool

External Libraries

JCalendar (v1.3.3-4) - Date picker component
MySQL Connector/J - MySQL JDBC driver

Steps to Install & Run the Project
Prerequisites

Java Development Kit (JDK) 8 or higher

Download from Oracle JDK
Verify installation: java -version


MySQL Server

Download from MySQL Community Server
Install and set up root password


NetBeans IDE (Optional but recommended)

Download from NetBeans Official Site



Installation Steps
1. Clone the Repository
bashgit clone https://github.com/vaishnavi2628/AirlineManagement.git
cd AirlineManagement
2. Set Up MySQL Database
sql-- Open MySQL Workbench or command line
-- Create database
CREATE DATABASE airline_management;

-- Use the database
USE airline_management;

-- Create necessary tables (example structure)
CREATE TABLE flight (
    flight_id VARCHAR(20) PRIMARY KEY,
    flight_name VARCHAR(50),
    source VARCHAR(50),
    destination VARCHAR(50),
    departure_time TIME,
    arrival_time TIME,
    capacity INT
);

CREATE TABLE passenger (
    passenger_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    nationality VARCHAR(50),
    phone VARCHAR(15),
    address VARCHAR(200),
    gender VARCHAR(10)
);

CREATE TABLE booking (
    booking_id INT AUTO_INCREMENT PRIMARY KEY,
    passenger_id INT,
    flight_id VARCHAR(20),
    booking_date DATE,
    seat_number VARCHAR(10),
    FOREIGN KEY (passenger_id) REFERENCES passenger(passenger_id),
    FOREIGN KEY (flight_id) REFERENCES flight(flight_id)
);

CREATE TABLE cancellation (
    cancellation_id INT AUTO_INCREMENT PRIMARY KEY,
    booking_id INT,
    cancellation_date DATE,
    reason VARCHAR(200),
    FOREIGN KEY (booking_id) REFERENCES booking(booking_id)
);

3. Configure Database Connection
Update the database connection details in your Java code (typically in a database utility class):
javaString url = "jdbc:mysql://localhost:3306/airline_management";
String username = "root";
String password = "your_mysql_password";
4. Add Required Libraries

Place jcalendar-tz-1.3.3-4.jar in the project's lib folder
Add MySQL Connector JAR to the project classpath

5. Build and Run
Using NetBeans:

Open the project in NetBeans
Right-click on the project → Properties → Libraries
Ensure all required JARs are added
Press F6 or click Run Project

Using Command Line:
bash# Navigate to project directory
cd AirlineManagementSystem-master

# Build the project
ant clean
ant build

# Run the project
java -jar dist/ASimulator.jar
Alternative (if main class is configured):
bashjava -cp "dist/ASimulator.jar:lib/*" asimulator.ASimulator
Instructions for Testing
Manual Testing Checklist
1. Flight Management Testing

 Add a new flight with valid details
 Try adding a flight with duplicate flight ID (should show error)
 View all flights
 Update flight information
 Verify date and time formats

2. Passenger Management Testing

 Add new passenger with all required fields
 Add passenger with missing fields (should validate)
 View passenger list
 Search for specific passenger
 Update passenger details

3. Booking System Testing

 Book a flight for an existing passenger
 Try booking when flight is full 
 View booking details
 Check if seat number is auto-assigned correctly
 Verify booking confirmation

4. Cancellation Testing

 Cancel an existing booking
 Try canceling a non-existent booking (should show error)
 Verify cancellation is recorded in database
 Check if cancelled seat becomes available again

5. Journey Details Testing

 View complete journey for a passenger
 Check if all flight details are displayed correctly
 Verify route information

Test Credentials
Database Host: localhost
Database Port: 3306
Database Name: airline_management
Username: root
Password: [your_mysql_password]
Sample Test Data
sql-- Insert sample flight
INSERT INTO flight VALUES 
('AI101', 'Air India', 'Mumbai', 'Delhi', '06:00:00', '08:30:00', 180),
('AI102', 'Air India', 'Delhi', 'Bangalore', '10:00:00', '12:30:00', 150);

-- Insert sample passenger
INSERT INTO passenger (name, nationality, phone, address, gender) VALUES 
('John Doe', 'Indian', '9876543210', 'Mumbai, Maharashtra', 'Male');
Project Structure
AirlineManagementSystem-master/
├── src/
│   └── asimulator/
│       ├── ASimulator.java          # Main application class
│       ├── AddFlight.java           # Flight management
│       ├── AddPassenger.java        # Passenger management
│       ├── BookFlight.java          # Booking system
│       ├── Cancel.java              # Cancellation handling
│       └── JourneyDetails.java      # Journey information
├── lib/
│   ├── jcalendar-tz-1.3.3-4.jar
│   └── mysql-connector-java.jar
├── nbproject/                        # Eclipse project files
├── build.xml                         # Ant build file
├── README.md
└── statement.md
Troubleshooting
Common Issues
1. Database Connection Error

Verify MySQL server is running
Check username and password
Ensure database airline_management exists

2. ClassNotFoundException for MySQL Driver

Add MySQL Connector JAR to classpath
In NetBeans: Right-click project → Properties → Libraries → Add JAR

3. JCalendar not found

Download JCalendar JAR from [official source]
Add to project libraries

4. Build Failed

Ensure JDK 8 or higher is installed
Check Ant is properly configured
Verify all dependencies are in place

Contributing
Contributions are welcome! Please feel free to submit a Pull Request.
License
This project is developed for educational purposes.
Contact
For queries or support, please contact:

GitHub: @vaishnavi2628


Note: This project is part of an academic assignment and demonstrates fundamental concepts of database-driven application development using Java Swing.
