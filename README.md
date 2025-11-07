# 🚌 Bus Reservation System

A simple Java (Maven-based) project for managing bus reservations.
This project helps users to book, cancel, and view bus tickets, while the admin can manage bus details and passenger information.

---

## 📌 Features

* 🔑 **User Features:**

  * Register / Login
  * Search buses by route
  * Book tickets
  * Cancel tickets
  * View booking history

* 🛠 **Admin Features:**

  * Add new buses
  * Update or remove buses
  * View all bookings
  * Manage passenger records

---

## ⚙️ Tech Stack

* **Language:** Java
* **Framework:** Spring Boot
* **Build Tool:** Maven
* **Database:** MySQL
* **Frontend:** Thymeleaf Templates (HTML + CSS)
* **IDE Support:** IntelliJ IDEA / Eclipse / VS Code

---

## 🚀 Installation & Setup

Clone this repository and navigate into the project directory:

```bash
git clone https://github.com/shreyr1/bus-reservation-system
cd bus-reservation-system
```

---

## 🧩 Database Setup

⚠️ Note: The project uses a hardcoded MySQL user (`root` / `root`) by default.
Make sure your local MySQL server is running and allows root login.
The app will automatically create the required tables at startup.

Expected tables for `bus_db`:

```
+------------------+
| Tables_in_bus_db |
+------------------+
| bookings         |
| buses            |
| schedules        |
| users            |
+------------------+
```

---

## 🧰 Build & Run

### ▶️ Using Maven

```bash
mvn clean install
mvn spring-boot:run
```

### ▶️ OR Run the JAR directly

After building, run:

```bash
java -jar target/bus-reservation-system-0.0.1-SNAPSHOT.jar
```

Then open your browser at 👉 [http://localhost:8080](http://localhost:8080)

---

## 🧑‍💻 Default Login (Demo Seed)

When the app starts for the first time (and the `users` table is empty),
the `DataLoader.java` class automatically creates demo users and sample data.

### 👥 Default Accounts

**Admin**

* Email: `admin@test.com`
* Password: `password`
* Role: `ROLE_ADMIN`

**User**

* Email: `user@test.com`
* Password: `password`
* Role: `ROLE_USER`

### 🚌 Demo Data

The following sample records are created:

**Buses**

| Name             | Number      | Seats |
| ---------------- | ----------- | ----- |
| Volvo AC Sleeper | UP85-AB1234 | 30    |
| Express Non-AC   | DL01-CD5678 | 45    |

**Schedule**

| Source  | Destination | Departure (approx) | Arrival (approx) | Price |
| ------- | ----------- | ------------------ | ---------------- | ----- |
| Mathura | Delhi       | +2 hours           | +5 hours         | ₹550  |

---

## 🧱 Project Structure

```
src/
├── main/
│   ├── java/com/busreservation/...   # Controllers, services, repositories, models
│   ├── resources/
│   │   ├── templates/                # Thymeleaf templates (HTML pages)
│   │   ├── static/                   # CSS, images, and other assets
│   │   └── application.properties    # App configuration
└── test/                             # Unit tests
```