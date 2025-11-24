Airline Management System 


The Airline Management System will be used for airline management.
This system provides an interface for managing flight schedules, passenger bookings, cancellations, and journey details. Built with Java Swing for the GUI and MySQL for database management, it provides solution for airline administrative tasks.


Features
Core Functionality

Flight Management

Add, update, and look for flight schedules
Manage flight routes and timings
Track flight availability 


Passenger Management

Add new passenger details
View passenger details
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




Technologies used

Java 8 
Java Swing 
JDBC 

Database

MySQL - Relational database management system

Development Tools

Eclipse IDE - Integrated Development Environment


External Libraries

JCalendar 
MySQL Connector/J - MySQL JDBC driver

Steps to Install & Run the Project
Prerequisites

Java Development Kit (JDK)

Download from Oracle JDK


MySQL Server

Download from MySQL Community Server
Install and set up root password

Eclipse IDE 

-- Create database
CREATE DATABASE airline_management;


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



Place jcalendar-tz-1.3.3-4.jar 
Add MySQL Connector JAR to the project classpath

5. Build and Run
Using Eclipse:



# Run the project


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
├── build.xml                        
├── README.md
└── statement.md

2. ClassNotFoundException for MySQL Driver

Add MySQL Connector JAR to classpath
In NetBeans: Right-click project → Properties → Libraries → Add JAR


here in this project we have made it on the principles of
Inheritance
Abstraction
File Handling
Exception Handling
FrameWorks are used for providing GUI
Inheritance property have been used 

