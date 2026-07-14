# Hotel Booking System (C++)

A console-based **Hotel Booking Management System** developed in **C++** using Object-Oriented Programming concepts such as **inheritance, polymorphism, encapsulation, and abstraction**. The system allows users to register, book rooms, cancel bookings, and enables administrators to manage hotel operations.

---

## Features

### User

* Register with email, phone number, and Aadhaar validation
* Login using username and password
* View available rooms
* Book a room
* Cancel a booking

### Admin

* View customer details
* View all bookings
* Check room occupancy
* View room booking statistics
* Checkout booked rooms

### System

* Automatically creates hotel rooms on the first run
* Saves customer, room, and booking information in text files
* Loads saved data when the program starts

---

## Room Types

| Room Type | Price |
| --------- | ----: |
| Standard  | ₹3000 |
| Deluxe    | ₹5000 |
| Suite     | ₹8000 |

---

## Project Files

```
hotel/
│── hotel.cpp
│── README.md
│── customers.txt
│── rooms.txt
└── bookings.txt
```

The text files are created automatically when the program runs.

---

## How to Build

Compile using any C++17 compiler.

```bash
g++ -std=c++17 hotel.cpp -o hotel
```

Run the program:

```bash
./hotel
```

---

## OOP Concepts Used

* Classes and Objects
* Inheritance
* Polymorphism
* Encapsulation
* Abstract Classes
* File Handling
* Exception Handling

---

## Limitations

* Passwords are stored as plain text.
* Admin username and password are fixed in the code.
* Payment feature is not implemented.
* Booking dates are not included.
