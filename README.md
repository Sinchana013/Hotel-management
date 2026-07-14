# Hotel-Booking-management
OOP based project in c++


# Hotel Booking System (C++)

A console-based **Hotel Booking Management System** written in modern C++ (C++17). It demonstrates
object-oriented design (inheritance, polymorphism, encapsulation, abstract classes), STL containers,
smart pointers, regex input validation, custom exceptions, and file-based persistence.

> Note: The source file is named `Hotell_no_loyalty.cpp` — this is the **no-loyalty** variant
> (the loyalty-points feature has been removed).

---

## Features

### User
- Register with validated details (email regex, 10-digit phone, 12-digit Aadhaar)
- Secure-ish login (username + password)
- View available rooms grouped by floor
- Book a room
- Cancel an existing booking

### Admin (`admin` / `adminpass`)
- View all customer details
- View all current bookings
- Generate an **Occupancy Report** (total / booked / available / occupancy %)
- Generate a **Popular Room Types Report** (bookings per type, sorted)
- Checkout (free) any booked room

### System
- Auto-initializes **15 rooms** on first run: 5 floors × 3 types
  (`101 102 103 … 501 502 503`)
- Persists all data to text files and reloads it on the next run

| Room number pattern | Type     | Price (₹) |
|---------------------|----------|-----------|
| `x01`               | Standard | 3000      |
| `x02`               | Deluxe   | 5000      |
| `x03`               | Suite    | 8000      |

---

## Project Structure

```
hotel/
├── hotel.cpp        # entire application (single source file)
├── README.md        # this file
├── customers.txt    # generated at runtime: username,name,email,phone,adhaar,password
├── rooms.txt        # generated at runtime: number,isBooked,type
└── bookings.txt     # generated at runtime: roomNumber,username
```

The `.txt` files are created automatically the first time you run the program.

---

## Build

Requires a C++17-capable compiler (e.g. `g++` 9+).

```bash
g++ -std=c++17 -Wall -o hotel hotel.cpp
```

## Run

```bash
./hotel
```

---

## Usage

At each prompt, type a number/value and press Enter.

**Main menu:** `1` Admin Login · `2` User Login · `3` Register · `4` Exit

Example: register, log in, and book room 101:
```
3
myuser
mypass
My Name
me@mail.com
9876543210
123456789012
2
myuser
mypass
2
101
4
4
```

**Admin login:** username `admin`, password `adminpass`.

---

## Architecture Overview

- **`Room`** — abstract base class (`roomNumber`, `price`, `isBooked`) with pure-virtual
  `displayInfo()` and `getRoomType()`.
  - **`StandardRoom` / `DeluxeRoom` / `SuiteRoom`** — concrete subclasses (polymorphism).
- **`Customer`** — encapsulates name, email, phone, Aadhaar, password.
- **`Validator`** — static helpers for integer input and email/phone/Aadhaar validation.
- **`Hotel`** — central controller: owns `customers`, `rooms`, `bookings` maps; handles menus,
  booking logic, reporting, and file persistence (loads in constructor, saves in destructor).
- **`BookingException` / `PaymentException`** — custom exception types.

### C++ concepts demonstrated
Inheritance & runtime polymorphism · abstract classes / pure virtual functions ·
`std::shared_ptr` / `make_shared` · STL (`unordered_map`, `map`, `vector`, `deque`) ·
lambdas + `std::sort` · `std::regex` validation · file I/O (`fstream`, `stringstream`) ·
`iomanip` formatting · exception handling · robust `cin` error recovery.

---

## Known Limitations
- Passwords are stored in **plaintext**; admin credentials are **hardcoded**.
- No booking dates / duration / payment processing (the `PaymentException` class is unused).
- Occupancy report does not guard against zero total rooms.
