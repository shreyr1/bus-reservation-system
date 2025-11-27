# 🚌 Bus Reservation System

A simple Java (Maven-based) project for managing bus reservations.

---

## 📌 Features

### 🔑 User Features

* User registration & login
* Profile management (name, mobile, address, profile photo)
* Change password
* Search buses by source, destination, and date
* View bus schedules with available seats
* Book tickets (with payment simulation)
* View booking confirmation ticket
* Cancel bookings
* View booking history
* Loyalty points system
* User notifications (read/unread)
* Referral program with unique referral codes

---

### 🛠 Admin Features

* Admin dashboard with system overview
* Bus Management: add, edit, delete buses
* Schedule Management: add, edit, delete schedules, manage delays & compensation
* Staff Management: add staff, edit details, upload photos, activate/deactivate, delete
* View all bookings
* View schedule-wise bookings
* View user list
* Configure loyalty program settings
* Send notifications to users
* Manage global system settings

---

### ⚙️ System Features

* Role-based access control (Admin/User)
* Spring Security authentication + CSRF protection
* Global exception handling with custom error pages
* File uploads for user and staff profile photos
* Automatic database seeding (default admin, users, buses, schedules, staff)
* JPA/Hibernate ORM with MySQL/MariaDB
* Responsive UI with Thymeleaf
* Light/Dark theme toggle

---

## ⚙️ Tech Stack

* **Language:** Java 17
* **Framework:** Spring Boot (Spring MVC, Spring Security, Spring Data JPA)
* **Database:** MariaDB / MySQL
* **ORM:** Hibernate (JPA)
* **Build Tool:** Maven
* **Frontend:** Thymeleaf (HTML, CSS, JS)
* **Web Server:** NGINX (reverse proxy + SSL)
* **Deployment:** Google Cloud VM (Linux) with Systemd
* **IDE:** IntelliJ IDEA / VS Code / Eclipse

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
| feedback         |
| loyalty_points   |
| loyalty_settings |
| notifications    |
| passengers       |
| referrals        |
| schedules        |
| staff            |
| system_settings  |
| transactions     |
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

---

### 👥 Default Accounts

**Admin**

* Email: `admin@test.com`
* Password: `password`
* Role: `ROLE_ADMIN`

**User**

* Email: `user@test.com`
* Password: `password`
* Role: `ROLE_USER`

---

## 🚌 Demo Data

### **Buses**

| Name             | Number      | Seats |
| ---------------- | ----------- | ----- |
| Volvo AC Sleeper | UP85-AB1234 | 30    |
| Express Non-AC   | DL01-CD5678 | 45    |

---

### **Schedule**

| Source  | Destination | Departure (approx) | Arrival (approx) | Price |
| ------- | ----------- | ------------------ | ---------------- | ----- |
| Mathura | Delhi       | +2 hours           | +5 hours         | ₹550  |

---

## 👥 Staff Members

### **Drivers**

| Name         | Email                                       | Mobile     | License       | Status   |
| ------------ | ------------------------------------------- | ---------- | ------------- | -------- |
| Ramesh Kumar | [ramesh.k@bus.com](mailto:ramesh.k@bus.com) | 9876543210 | DL-2023-12345 | Active   |
| Suresh Singh | [suresh.s@bus.com](mailto:suresh.s@bus.com) | 9876543211 | DL-2022-67890 | On Leave |

### **Conductors**

| Name         | Email                                       | Mobile     | License | Status |
| ------------ | ------------------------------------------- | ---------- | ------- | ------ |
| Mahesh Yadav | [mahesh.y@bus.com](mailto:mahesh.y@bus.com) | 9876543212 | —       | Active |
| Rajesh Gupta | [rajesh.g@bus.com](mailto:rajesh.g@bus.com) | 9876543213 | —       | Active |

### **Manager**

| Name            | Email                                       | Mobile     | Status |
| --------------- | ------------------------------------------- | ---------- | ------ |
| Vikram Malhotra | [vikram.m@bus.com](mailto:vikram.m@bus.com) | 9876543214 | Active |

---

## 🧱 Project Structure

```
bus-reservation-system/                                          # Maven project configuration
├── fix_database.sql                                             # SQL patch for DB fixes
├── pom.xml                                                         
├── README.md                                                    # Project documentation
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── busreservation
│   │   │           ├── BusReservationSystemApplication.java     # Spring Boot entry point
│   │   │           ├── config
│   │   │           │   ├── DataLoader.java                      # Loads default users, buses, schedules, staff
│   │   │           │   └── SecurityConfig.java                  # Spring Security config
│   │   │           ├── controller                               # Handles web requests
│   │   │           │   ├── AdminController.java                 # Admin dashboard pages
│   │   │           │   ├── AdminPaymentController.java          # Admin-side payment logs
│   │   │           │   ├── AdminRestController.java             # Admin REST API
│   │   │           │   ├── BookingController.java               # Ticket booking & cancellation
│   │   │           │   ├── CarbonReportController.java          # Ticket booking & cancellation
│   │   │           │   ├── GoogleLoginController.java           # Google OAuth login
│   │   │           │   ├── LoyaltyController.java               # Loyalty program routes
│   │   │           │   ├── PublicController.java                # Public pages
│   │   │           │   └── UserController.java                  # User profile & account mgmt
│   │   │           ├── dto                                      # Data Transfer Objects
│   │   │           │   ├── BusDto.java
│   │   │           │   ├── LoyaltySettingDto.java
│   │   │           │   ├── PasswordChangeDto.java
│   │   │           │   ├── ScheduleDto.java
│   │   │           │   └── UserRegistrationDto.java
│   │   │           ├── exception                                # Global exception handling
│   │   │           │   ├── GlobalExceptionHandler.java
│   │   │           │   └── ResourceNotFoundException.java
│   │   │           ├── model                                    # JPA Entities → DB tables
│   │   │           │   ├── Booking.java
│   │   │           │   ├── Bus.java
│   │   │           │   ├── Feedback.java
│   │   │           │   ├── LoyaltyPoints.java
│   │   │           │   ├── LoyaltySetting.java
│   │   │           │   ├── Notification.java
│   │   │           │   ├── Passenger.java
│   │   │           │   ├── Referral.java
│   │   │           │   ├── Schedule.java
│   │   │           │   ├── Staff.java
│   │   │           │   ├── SystemSetting.java
│   │   │           │   ├── Transaction.java
│   │   │           │   └── User.java
│   │   │           ├── repository                               # DB Repositories (JPA)
│   │   │           │   ├── BookingRepository.java
│   │   │           │   ├── BusRepository.java
│   │   │           │   ├── FeedbackRepository.java
│   │   │           │   ├── LoyaltyPointsRepository.java
│   │   │           │   ├── LoyaltySettingRepository.java
│   │   │           │   ├── NotificationRepository.java
│   │   │           │   ├── PassengerRepository.java
│   │   │           │   ├── ReferralRepository.java
│   │   │           │   ├── ScheduleRepository.java
│   │   │           │   ├── StaffRepository.java
│   │   │           │   ├── SystemSettingRepository.java
│   │   │           │   ├── TransactionRepository.java
│   │   │           │   └── UserRepository.java
│   │   │           └── service                                  # Business Logic
│   │   │               ├── BookingServiceImpl.java
│   │   │               ├── BookingService.java
│   │   │               ├── BusServiceImpl.java
│   │   │               ├── BusService.java
│   │   │               ├── CarbonFootprintService.java
│   │   │               ├── CustomUserDetailsService.java        # Security: loads users
│   │   │               ├── FeedbackService.java
│   │   │               ├── FileStorageService.java              # Handles photo uploads
│   │   │               ├── GoogleAuthService.java
│   │   │               ├── LoyaltyService.java
│   │   │               ├── NotificationService.java
│   │   │               ├── PassengerService.java
│   │   │               ├── ScheduleServiceImpl.java
│   │   │               ├── ScheduleService.java
│   │   │               ├── StaffServiceImpl.java
│   │   │               ├── StaffService.java
│   │   │               ├── TransactionService.java
│   │   │               ├── UserServiceImpl.java
│   │   │               └── UserService.java
│   │   └── resources
│   │       ├── application-prod.properties
│   │       ├── application.properties                          # Main app & DB config
│   │       ├── static
│   │       │   ├── css
│   │       │   │   ├── admin-style.css
│   │       │   │   ├── enhancements.css
│   │       │   │   ├── style.css
│   │       │   │   ├── theme-toggle.css
│   │       │   │   └── visibility-fixes.css
│   │       │   ├── images
│   │       │   │   └── bus.png
│   │       │   ├── js
│   │       │   │   ├── loader.js
│   │       │   │   └── theme-toggle.js
│   │       │   └── uploads
│   │       └── templates                                      # Thymeleaf HTML pages
│   │           ├── about.html
│   │           ├── admin
│   │           │   ├── admin-dashboard.html
│   │           │   ├── admin-feedback.html
│   │           │   ├── carbon-report.html
│   │           │   ├── edit-bus.html
│   │           │   ├── edit-schedule.html
│   │           │   ├── edit-staff.html
│   │           │   ├── loyalty-program.html
│   │           │   ├── manage-buses.html
│   │           │   ├── manage-schedules.html
│   │           │   ├── manage-staff.html
│   │           │   ├── payments.html
│   │           │   ├── reports.html
│   │           │   ├── security-audit.html
│   │           │   ├── system-settings.html
│   │           │   ├── view-bookings.html
│   │           │   ├── view-schedule-bookings.html
│   │           │   └── view-users.html
│   │           ├── booking-page.html
│   │           ├── carbon-report.html
│   │           ├── contact.html
│   │           ├── error-page.html
│   │           ├── feedback.html
│   │           ├── fragments
│   │           │   ├── admin-sidebar.html
│   │           │   ├── footer.html
│   │           │   └── header.html
│   │           ├── help-center.html
│   │           ├── index.html
│   │           ├── login.html
│   │           ├── loyalty-dashboard.html
│   │           ├── my-bookings.html
│   │           ├── payment-simulation.html
│   │           ├── privacy-policy.html
│   │           ├── profile.html
│   │           ├── register.html
│   │           ├── search-results.html
│   │           ├── terms-of-service.html
│   │           └── ticket.html
│   └── test
│       └── java
│           └── com
│               └── busreservation
│                   └── service
│                       └── BusServiceImplTest.java
└── target
    ├── bus-reservation-system-0.0.1-SNAPSHOT.jar
    ├── bus-reservation-system-0.0.1-SNAPSHOT.jar.original
    ├── classes
    │   ├── application-prod.properties
    │   ├── application.properties
    │   ├── com
    │   │   └── busreservation
    │   │       ├── BusReservationSystemApplication.class
    │   │       ├── config
    │   │       │   ├── DataLoader.class
    │   │       │   └── SecurityConfig.class
    │   │       ├── controller
    │   │       │   ├── AdminController.class
    │   │       │   ├── AdminPaymentController.class
    │   │       │   ├── AdminRestController.class
    │   │       │   ├── BookingController.class
    │   │       │   ├── CarbonReportController.class
    │   │       │   ├── GoogleLoginController.class
    │   │       │   ├── LoyaltyController.class
    │   │       │   ├── PublicController.class
    │   │       │   └── UserController.class
    │   │       ├── dto
    │   │       │   ├── BusDto.class
    │   │       │   ├── LoyaltySettingDto.class
    │   │       │   ├── PasswordChangeDto.class
    │   │       │   ├── ScheduleDto.class
    │   │       │   └── UserRegistrationDto.class
    │   │       ├── exception
    │   │       │   ├── GlobalExceptionHandler.class
    │   │       │   └── ResourceNotFoundException.class
    │   │       ├── model
    │   │       │   ├── Booking.class
    │   │       │   ├── Bus.class
    │   │       │   ├── Feedback.class
    │   │       │   ├── LoyaltyPoints.class
    │   │       │   ├── LoyaltySetting.class
    │   │       │   ├── Notification.class
    │   │       │   ├── Passenger.class
    │   │       │   ├── Referral.class
    │   │       │   ├── Schedule.class
    │   │       │   ├── Staff.class
    │   │       │   ├── SystemSetting.class
    │   │       │   ├── Transaction.class
    │   │       │   └── User.class
    │   │       ├── repository
    │   │       │   ├── BookingRepository.class
    │   │       │   ├── BusRepository.class
    │   │       │   ├── FeedbackRepository.class
    │   │       │   ├── LoyaltyPointsRepository.class
    │   │       │   ├── LoyaltySettingRepository.class
    │   │       │   ├── NotificationRepository.class
    │   │       │   ├── PassengerRepository.class
    │   │       │   ├── ReferralRepository.class
    │   │       │   ├── ScheduleRepository.class
    │   │       │   ├── StaffRepository.class
    │   │       │   ├── SystemSettingRepository.class
    │   │       │   ├── TransactionRepository.class
    │   │       │   └── UserRepository.class
    │   │       └── service
    │   │           ├── BookingService.class
    │   │           ├── BookingServiceImpl.class
    │   │           ├── BusService.class
    │   │           ├── BusServiceImpl.class
    │   │           ├── CarbonFootprintService.class
    │   │           ├── CustomUserDetailsService.class
    │   │           ├── FeedbackService.class
    │   │           ├── FileStorageService.class
    │   │           ├── GoogleAuthService.class
    │   │           ├── LoyaltyService.class
    │   │           ├── NotificationService.class
    │   │           ├── PassengerService.class
    │   │           ├── ScheduleService.class
    │   │           ├── ScheduleServiceImpl.class
    │   │           ├── StaffService.class
    │   │           ├── StaffServiceImpl.class
    │   │           ├── TransactionService.class
    │   │           ├── UserService.class
    │   │           └── UserServiceImpl.class
    │   ├── static
    │   │   ├── css
    │   │   │   ├── admin-style.css
    │   │   │   ├── enhancements.css
    │   │   │   ├── style.css
    │   │   │   ├── theme-toggle.css
    │   │   │   └── visibility-fixes.css
    │   │   ├── images
    │   │   │   └── bus.png
    │   │   ├── js
    │   │   │   ├── loader.js
    │   │   │   └── theme-toggle.js
    │   │   └── uploads
    │   └── templates
    │       ├── about.html
    │       ├── admin
    │       │   ├── admin-dashboard.html
    │       │   ├── admin-feedback.html
    │       │   ├── carbon-report.html
    │       │   ├── edit-bus.html
    │       │   ├── edit-schedule.html
    │       │   ├── edit-staff.html
    │       │   ├── loyalty-program.html
    │       │   ├── manage-buses.html
    │       │   ├── manage-schedules.html
    │       │   ├── manage-staff.html
    │       │   ├── payments.html
    │       │   ├── reports.html
    │       │   ├── security-audit.html
    │       │   ├── system-settings.html
    │       │   ├── view-bookings.html
    │       │   ├── view-schedule-bookings.html
    │       │   └── view-users.html
    │       ├── booking-page.html
    │       ├── carbon-report.html
    │       ├── contact.html
    │       ├── error-page.html
    │       ├── feedback.html
    │       ├── fragments
    │       │   ├── admin-sidebar.html
    │       │   ├── footer.html
    │       │   └── header.html
    │       ├── help-center.html
    │       ├── index.html
    │       ├── login.html
    │       ├── loyalty-dashboard.html
    │       ├── my-bookings.html
    │       ├── payment-simulation.html
    │       ├── privacy-policy.html
    │       ├── profile.html
    │       ├── register.html
    │       ├── search-results.html
    │       ├── terms-of-service.html
    │       └── ticket.html
    ├── generated-sources
    │   └── annotations
    ├── generated-test-sources
    │   └── test-annotations
    ├── maven-archiver
    │   └── pom.properties
    ├── maven-status
    │   └── maven-compiler-plugin
    │       ├── compile
    │       │   └── default-compile
    │       │       ├── createdFiles.lst
    │       │       └── inputFiles.lst
    │       └── testCompile
    │           └── default-testCompile
    │               ├── createdFiles.lst
    │               └── inputFiles.lst
    ├── surefire-reports
    │   ├── com.busreservation.service.BusServiceImplTest.txt
    │   └── TEST-com.busreservation.service.BusServiceImplTest.xml
    └── test-classes
        └── com
            └── busreservation
                └── service
                    └── BusServiceImplTest.class

```
---

# 🚀 Deployment (Google Cloud VM + NGINX + SSL)

This project is deployed on a **Google Cloud Compute Engine VM** using:

* Ubuntu Linux 24.04 LTS
* NGINX (reverse proxy)
* Systemd service for the Spring Boot app
* SSL Certificates (Let's Encrypt)
* Custom domain (GoDaddy)

Follow the steps below to deploy your own instance. 

I chose an e2-small instance. 

---

## 1️⃣ **Install Required Packages on VM**

```bash
sudo apt update
sudo apt install -y openjdk-17-jdk nginx certbot python3-certbot-nginx vim
```

---

## 2️⃣ **Upload the JAR File to Your VM**

Just upload manually using the Google Cloud console as it is the easiest to do.

---

## 3️⃣ **Create a Systemd Service**

Create the service file:

```bash
sudo vim /etc/systemd/system/busapp.service
```

Paste this (update username + jar file name):

```
[Unit]
Description=Spring Boot Bus App
After=network.target

[Service]
User=YOUR_USERNAME
WorkingDirectory=/home/YOUR_USERNAME
ExecStart=/usr/bin/java -jar /home/YOUR_USERNAME/bus-reservation-system-0.0.1-SNAPSHOT.jar
SuccessExitStatus=143
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Save and enable this service using systemctl :

```bash
sudo systemctl daemon-reload
sudo systemctl start busapp
sudo systemctl enable busapp
sudo systemctl status busapp
```

---

## 4️⃣ **Configure NGINX Reverse Proxy**

Create an NGINX config:

```bash
sudo vim /etc/nginx/sites-available/[YOUR_DOMAIN_NAME]
```
Paste:
```bash
server {
    server_name [YOUR_DOMAIN_NAME].[TLD] www.[YOUR_DOMAIN_NAME].[TLD];

    location / {
        proxy_pass http://localhost:8080/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

Enable it:

```bash
sudo ln -s /etc/nginx/sites-available/tourntravels /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

---

## 5️⃣ **Point Your Domain (GoDaddy → Google Cloud IP)**

Set DNS records:

| Type | Name | Value      |
| ---- | ---- | ---------- |
| A    | @    | your VM IP |
| A    | www  | your VM IP |

Propagation can take from 5 minutes to 1 hour.

---

## 6️⃣ **Enable HTTPS Using Certbot (Let’s Encrypt)**

Run:

```bash
sudo certbot --nginx -d [YOUR_DOMAIN_NAME].[TLD] -d www.[YOUR_DOMAIN_NAME].[TLD]
```

Certbot will:

✔ Auto-configure SSL

✔ Redirect HTTP → HTTPS

✔ Create auto-renew cron jobs

You can test renewal:

```bash
sudo certbot renew --dry-run
```

---

## 7️⃣ **Check If Everything Is Running**

### Spring Boot app status:

```bash
sudo systemctl status busapp
```

### NGINX status:

```bash
sudo systemctl status nginx
```

### Check open ports:

```bash
sudo ss -tulnp
```

### Visit your website:

```
https://[YOUR_DOMAIN_NAME].[TLD]
```

---


