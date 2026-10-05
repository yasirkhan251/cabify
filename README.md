# 🚖 Cabify — Taxi & Ride Booking Management System

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python" alt="Python">
  <img src="https://img.shields.io/badge/Flask-Web%20Framework-black?style=for-the-badge&logo=flask" alt="Flask">
  <img src="https://img.shields.io/badge/MySQL-Database-orange?style=for-the-badge&logo=mysql" alt="MySQL">
  <img src="https://img.shields.io/badge/SQLite-Alternative-blue?style=for-the-badge&logo=sqlite" alt="SQLite">
  <img src="https://img.shields.io/badge/Bootstrap-UI-purple?style=for-the-badge&logo=bootstrap" alt="Bootstrap">
  <img src="https://img.shields.io/badge/Status-Prototype-success?style=for-the-badge" alt="Status">
</p>

<p align="center">
  <strong>A Flask-based taxi booking and ride-management platform with dedicated User, Driver, and Admin workflows.</strong>
</p>

<p align="center">
  <a href="https://github.com/yasirkhan251/cabify">View Repository</a>
</p>

---

## 🎯 What This Project Offers

**Cabify** is a web-based taxi and transportation management system built using **Python Flask**.

The application provides separate workflows for:

- 👤 Customers
- 🚗 Drivers
- 🛠️ Administrators

Customers can create different types of ride bookings, drivers can view and respond to available rides, and administrators can review and authorize driver accounts.

The project also contains both:

- 🗄️ **MySQL implementation** — `app.py`
- 🗄️ **SQLite implementation** — `app_sqlite_converted_2.py`

This makes the project useful as a full-stack Flask learning project demonstrating authentication, database operations, booking workflows, role-based sessions, file uploads, payment-related pages, and ride-status management.

---

## ✨ Highlighted Features

<table>
<tr>
<td width="50%">

### 👤 Customer Features

- User registration
- User login/logout
- Password hashing
- Customer dashboard
- Current ride booking
- Advance booking
- Shared taxi booking
- Private driver booking
- Vehicle selection
- Pickup/drop-off information
- Booking history
- Ride status pages
- Profile-related pages
- Feedback and contact pages
- Safety information

</td>

<td width="50%">

### 🚗 Driver Features

- Driver registration
- Driver login/logout
- Driver dashboard
- Driver profile
- Driver credential submission
- Driver photo upload
- Aadhaar document upload
- Driving licence upload
- Available ride requests
- Accept/reject ride requests
- Ride journey interface
- Driver settings
- Ride history interface
- Driver authorization workflow

</td>
</tr>

<tr>
<td>

### 🛠️ Admin Features

- Driver listing
- Driver authorization
- Driver approval/rejection states
- Driver credential review
- Driver management
- Booking visibility
- Driver status management

</td>

<td>

### 💳 Booking & Payment

- Multiple booking modes
- Vehicle selection
- Ride pricing fields
- Payment-related pages
- Cash payment page
- Debit/card-related UI
- UPI-related UI
- Payment success interface
- Booking confirmation pages

</td>
</tr>
</table>

---

## 🧠 How It Works

Cabify is structured around three main actors.

```text
                    ┌───────────────────────┐
                    │        CABIFY         │
                    │  Taxi Booking System  │
                    └───────────┬───────────┘
                                │
             ┌──────────────────┼──────────────────┐
             │                  │                  │
             ▼                  ▼                  ▼
       ┌───────────┐      ┌───────────┐      ┌───────────┐
       │   USER    │      │  DRIVER   │      │   ADMIN   │
       └─────┬─────┘      └─────┬─────┘      └─────┬─────┘
             │                  │                  │
             ▼                  ▼                  ▼
       Create Ride        View Requests       Review Drivers
       Select Vehicle    Accept / Reject      Authorize
       Track Journey     Manage Journey       Manage Status
       View Bookings     Profile / Docs       Driver Records
             │                  │                  │
             └──────────────────┼──────────────────┘
                                ▼
                     ┌────────────────────┐
                     │      DATABASE      │
                     │  MySQL / SQLite    │
                     └────────────────────┘
```

### 🔄 Typical Customer Flow

```text
Register
   ↓
Login
   ↓
Customer Dashboard
   ↓
Choose Booking Type
   ↓
Enter Pickup / Drop-off
   ↓
Select Vehicle
   ↓
Create Booking
   ↓
Driver Receives Request
   ↓
Driver Accepts
   ↓
Ride Journey
   ↓
Booking / Ride Status
```

### 🚗 Driver Flow

```text
Driver Registration
       ↓
Credential Submission
       ↓
Admin Review
       ↓
Driver Authorization
       ↓
Driver Dashboard
       ↓
View Available Rides
       ↓
Accept / Reject
       ↓
Start Journey
       ↓
Complete / Cancel Ride
```

---

# 🚕 Booking Types

Cabify implements several different transportation workflows.

## 1. ⚡ Current Booking

Designed for immediate/current taxi requirements.

Customers provide:

- Customer ID
- Pickup location
- Drop-off location
- Vehicle type
- Booking time

The booking is stored and made available through the driver workflow.

---

## 2. 📅 Advance Booking

Allows the customer to schedule a ride for a future date and time.

Information includes:

- Customer information
- Pickup location
- Drop-off location
- Vehicle type
- Pickup date
- Pickup time
- Booking time

---

## 3. 👥 Shared Taxi

Allows customers to request a shared taxi.

The booking records:

- Pickup
- Drop-off
- Number of passengers
- Vehicle type
- Customer information
- Booking time

---

## 4. 👨‍✈️ Private Driver

Customers can request a private driver for a specified duration.

The workflow collects:

- Name
- Phone
- Address
- State
- City
- Pincode
- Required duration
- Booking time

---

# 🚗 Vehicle Selection

The application includes dedicated pages for several vehicle types and their booking flows.

Examples include:

- 🚙 Maruti/compact vehicle options
- 🚗 Nano
- 🚗 Mini Cooper
- 🚘 Hyundai Santro
- 🚐 Toyota Innova
- 🚐 Tata Winger

The repository contains dedicated vehicle information and booking templates for these flows.

---

# 👤 User System

Cabify implements a session-based customer authentication system.

### Registration

Customers register with:

```text
Name
Username
Phone
Password
```

Passwords are hashed using:

```python
sha256_crypt
```

### Login

The application verifies the submitted credentials against the database and stores the logged-in state using Flask sessions.

Example session values include:

```python
session["ulogged_in"] = True
session["userId"] = user_id
```

### Protected Routes

A custom decorator is used to protect customer-only pages:

```python
@login_required
```

---

# 🚗 Driver Management

Drivers have their own authentication and dashboard.

### Driver Registration

Driver registration includes:

- Name
- Driver username
- Phone
- Password

After registration, the driver is redirected into the driver onboarding workflow.

### Driver Credentials

Drivers can submit:

- Driver photograph
- Aadhaar document
- Driving licence
- Gender
- Address
- Age
- Experience
- Licence information
- Aadhaar information

Uploaded files are stored under:

```text
dynamic/Image/
```

---

# 🛡️ Driver Authorization

Cabify includes an administrative authorization workflow.

The driver status system uses values representing states such as:

```text
Pending
Authorized
Rejected
```

The project maintains a separate `dst` table for driver authorization/status information.

The admin can review drivers and update their authorization state.

---

# 🧭 Ride Journey

After a ride request is accepted, the application provides dedicated journey pages.

Examples include:

```text
/advance/ridejourney
/current/ridejourney/
/sharetaxi/ridejourney
/driverjourney/active/
```

These pages display information such as:

- Ride/customer ID
- Pickup
- Drop-off
- Current ride status

---

# 📋 Booking Management

Cabify stores different booking categories separately.

```text
advance
current
share
private
```

The application can retrieve bookings belonging to a customer and display them through the booking-history interface.

The driver dashboard can also retrieve active ride requests.

---

# 💳 Payment Interface

The repository contains multiple payment-related templates, including:

```text
payment.html
paymentbackup.html
cash.html
debit.html
upi.html
paysuccess.html
```

These provide the user interface for different payment scenarios.

> ⚠️ The payment implementation should be treated as a prototype rather than a production payment gateway integration. A production deployment should use a verified payment provider and server-side transaction verification.

---

# 🛠️ Software & Technologies Used

<table>
<tr>
<th>Technology</th>
<th>Purpose</th>
</tr>

<tr>
<td>🐍 Python</td>
<td>Core programming language</td>
</tr>

<tr>
<td>🌐 Flask</td>
<td>Backend web framework</td>
</tr>

<tr>
<td>🗄️ MySQL</td>
<td>Primary database implementation</td>
</tr>

<tr>
<td>🗄️ SQLite</td>
<td>Alternative/local database implementation</td>
</tr>

<tr>
<td>🔐 Passlib</td>
<td>Password hashing</td>
</tr>

<tr>
<td>🎨 HTML</td>
<td>Frontend structure</td>
</tr>

<tr>
<td>🎨 CSS / SCSS</td>
<td>Interface styling</td>
</tr>

<tr>
<td>🅱️ Bootstrap</td>
<td>Responsive UI components</td>
</tr>

<tr>
<td>⚡ JavaScript</td>
<td>Frontend interactions</td>
</tr>

<tr>
<td>📁 Werkzeug</td>
<td>File upload handling</td>
</tr>

<tr>
<td>🔑 Flask Sessions</td>
<td>User/driver session management</td>
</tr>

</table>

---

# 💻 System Requirements

### Minimum

| Component | Requirement |
|---|---|
| OS | Windows / Linux / macOS |
| Python | Python 3.x |
| RAM | 4 GB |
| Storage | 500 MB+ |
| Database | MySQL or SQLite |
| Browser | Chrome / Edge / Firefox |

### Recommended

| Component | Recommendation |
|---|---|
| RAM | 8 GB+ |
| CPU | Modern dual/quad-core CPU |
| Python | Python 3.10+ |
| Database | MySQL |
| Browser | Latest Chrome/Edge |

---

# 📦 Installation & Setup

## 1. Clone the Repository

```bash
git clone https://github.com/yasirkhan251/cabify.git
```

Enter the project:

```bash
cd cabify
```

---

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3. Install Dependencies

The repository does not currently provide a root `requirements.txt`, so install the packages required by the Flask implementation.

For the MySQL version:

```bash
pip install flask flask-mysqldb mysql-connector-python passlib werkzeug
```

For the SQLite version:

```bash
pip install flask passlib werkzeug
```

---

# ⚙️ Configuration

## 🗄️ MySQL Version

The primary `app.py` implementation expects a local MySQL database.

Current configuration is structured around:

```python
app.config['MYSQL_HOST'] = 'localhost'
app.config['MYSQL_USER'] = 'root'
app.config['MYSQL_PASSWORD'] = ''
app.config['MYSQL_DB'] = 'tms'
```

Create the database:

```sql
CREATE DATABASE tms;
```

Then configure your local MySQL credentials before running the application.

---

## 🗄️ SQLite Version

The repository also includes:

```text
app_sqlite_converted_2.py
```

which uses:

```text
sqlite3.db
```

This version is useful when you want to run the application without configuring MySQL.

---

# ▶️ How to Run

## MySQL Version

```bash
python app.py
```

The application runs using Flask's development server.

Open:

```text
http://127.0.0.1:5000/
```

---

## SQLite Version

```bash
python app_sqlite_converted_2.py
```

Then open:

```text
http://127.0.0.1:5000/
```

---

# 🎮 How to Use

## 👤 Customer

1. Open the application.
2. Create a user account.
3. Login.
4. Open the customer dashboard.
5. Select a booking type.
6. Enter pickup and drop-off details.
7. Select a vehicle.
8. Submit the booking.
9. View booking/ride information.
10. Follow the ride journey interface.

---

## 🚗 Driver

1. Open the driver section.
2. Register as a driver.
3. Login.
4. Complete driver credentials.
5. Upload required documents.
6. Wait for administrative authorization.
7. Access the driver dashboard.
8. View available rides.
9. Accept or reject requests.
10. Open the ride journey.

---

## 🛠️ Admin

The administrative workflow can be used to:

- Review drivers
- View driver information
- Authorize drivers
- Reject drivers
- Manage driver authorization states
- Review booking-related information

---

# 📸 Screenshots

The repository contains a dedicated screenshot collection under:

```text
Website screenshots/
```

### 🏠 Application Screens

<p align="center">
  <img src="Website%20screenshots/Screenshot%202026-10-03%20030431.png" width="80%" alt="Cabify Screenshot 1">
</p>

<p align="center">
  <img src="Website%20screenshots/Screenshot%202026-10-03%20030458.png" width="80%" alt="Cabify Screenshot 2">
</p>

<p align="center">
  <img src="Website%20screenshots/Screenshot%202026-10-03%20030518.png" width="80%" alt="Cabify Screenshot 3">
</p>

<p align="center">
  <img src="Website%20screenshots/Screenshot%202026-10-03%20030526.png" width="80%" alt="Cabify Screenshot 4">
</p>

> The repository contains additional screenshots covering different application screens and workflows.

---

# 🎞️ GIF Demonstrations

You can add animated demonstrations under:

```text
docs/demo/
```

Recommended GIFs:

```text
docs/demo/user-booking.gif
docs/demo/driver-booking.gif
docs/demo/driver-authorization.gif
docs/demo/ride-journey.gif
```

Example:

```html
<p align="center">
  <img src="docs/demo/user-booking.gif" width="85%" alt="User Booking Demo">
</p>
```

> These GIF paths are documentation placeholders unless the files are added to the repository.

---

# 🎥 Video Demonstration

A project demonstration can be linked through YouTube or another hosted video platform.

Example:

```markdown
[![Cabify Demo](https://img.youtube.com/vi/YOUR_VIDEO_ID/maxresdefault.jpg)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)
```

Replace `YOUR_VIDEO_ID` with the actual demonstration video ID.

---

# 📁 Project Structure

```text
cabify/
│
├── app.py
├── app_sqlite_converted_2.py
├── test.py
├── tempCodeRunnerFile.py
├── sqlite3.db
│
├── dynamic/
│   └── Image/
│       ├── vehicle images
│       ├── uploaded driver images
│       └── document images
│
├── static/
│   ├── css/
│   │   ├── bootstrap.css
│   │   ├── style.css
│   │   ├── responsive.css
│   │   ├── driverhome.css
│   │   ├── driverlogin.css
│   │   └── ...
│   │
│   └── application images
│
├── templates/
│   ├── welcome.html
│   ├── login.html
│   ├── signup.html
│   ├── userlogin.html
│   ├── user-register.html
│   ├── userdb.html
│   ├── Userbookinglist.html
│   │
│   ├── driverindex.html
│   ├── driverlogin.html
│   ├── driversignup.html
│   ├── driverhomepage.html
│   ├── driverprofile.html
│   ├── driverform.html
│   │
│   ├── payment.html
│   ├── cash.html
│   ├── debit.html
│   ├── upi.html
│   ├── paysuccess.html
│   │
│   ├── advance booking pages
│   ├── current booking pages
│   ├── shared taxi pages
│   ├── private driver pages
│   ├── journey pages
│   ├── vehicle pages
│   └── admin pages
│
└── Website screenshots/
    └── application screenshots
```

---

# 🏗️ Application Architecture

```text
                 ┌──────────────────────┐
                 │      Browser UI      │
                 │ HTML / CSS / JS      │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │       Flask          │
                 │   Application Layer  │
                 └──────────┬───────────┘
                            │
            ┌───────────────┼────────────────┐
            │               │                │
            ▼               ▼                ▼
       User System     Driver System     Admin System
            │               │                │
            └───────────────┼────────────────┘
                            ▼
                 ┌──────────────────────┐
                 │    Booking System    │
                 ├──────────────────────┤
                 │ Current              │
                 │ Advance              │
                 │ Shared Taxi          │
                 │ Private Driver       │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │       Database       │
                 │   MySQL / SQLite     │
                 └──────────────────────┘
```

---

# 🔐 Authentication Architecture

Cabify maintains separate session states for different actors.

### Customer

```python
session["ulogged_in"]
session["userId"]
```

### Driver

```python
session["dlogged_in"]
session["driverId"]
```

### Admin

The application also contains an admin session mechanism:

```python
session["alogged_in"]
```

Custom decorators are used for access control:

```python
@login_required
@login_requireddriver
@login_requiredadmin
```

---

# 🗄️ Database Design

The application uses different tables for different business entities.

Important tables include:

```text
user
driver
driveract
dst

advance
current
share
private
```

### `user`

Stores customer account information.

```text
id
name
username
password
phone
```

### `driver`

Stores driver information and credentials.

```text
id
name
drivername
phone
password
gender
address
age
experience
driving_license
aadhar
driver image
document references
```

### Booking Tables

The booking system separates ride types:

```text
advance
current
share
private
```

This keeps the different booking workflows independent.

---

# 📊 Ride Status Concept

Cabify uses a ticket/status field to represent the state of ride requests.

Typical values include:

```text
active
accepted
expired
```

The driver can update ride requests through the driver workflow.

---

# ⚠️ Limitations

This project is best considered a **learning/prototype transportation management system**, rather than a production-ready ride-hailing platform.

### Current limitations include:

- ❌ No production-grade deployment configuration
- ❌ No real-time GPS tracking system
- ❌ No WebSocket-based live ride updates
- ❌ No production mapping/navigation integration
- ❌ Payment UI is not equivalent to a secure payment gateway
- ❌ No robust API architecture
- ❌ Limited validation/error handling
- ❌ Development Flask server configuration
- ❌ Credentials/configuration are embedded in source code
- ❌ Database tables are created dynamically in application routes
- ❌ No formal migration system
- ❌ No automated test suite covering the application
- ❌ Driver authorization requires stronger production security
- ❌ Uploaded identity documents require secure storage controls
- ❌ No production-grade logging/monitoring

---

# 🔒 Security Considerations

Before deploying this application publicly, several areas should be improved.

## Secret Key

The project currently contains a hard-coded Flask secret key.

Move it into an environment variable:

```python
import os

app.config["SECRET_KEY"] = os.environ.get("SECRET_KEY")
```

---

## Database Credentials

Do not store production database credentials directly inside:

```python
app.py
```

Use environment variables instead:

```text
MYSQL_HOST
MYSQL_USER
MYSQL_PASSWORD
MYSQL_DB
```

---

## Uploaded Documents

The application handles sensitive driver documents such as:

- Aadhaar
- Driving licence
- Driver photographs

These should never be publicly exposed through an unrestricted static directory in a production deployment.

Use:

- Secure storage
- Access controls
- Encryption where appropriate
- File-type validation
- File-size limits
- Private object storage

---

## Payment Security

Production payments should use a trusted payment gateway.

The server should verify:

```text
Payment request
      ↓
Payment provider
      ↓
Server-side verification
      ↓
Transaction status
      ↓
Booking confirmation
```

Never trust a client-side payment-success page alone.

---

# 🔮 Future Improvements / Roadmap

## 🚀 Phase 1 — Backend Improvements

- [ ] Add `requirements.txt`
- [ ] Move configuration to `.env`
- [ ] Add Flask application factory
- [ ] Separate routes into Blueprints
- [ ] Introduce database migrations
- [ ] Improve error handling
- [ ] Add structured logging
- [ ] Add automated tests

---

## 🗺️ Phase 2 — Real Ride-Hailing Features

- [ ] Google Maps / Mapbox integration
- [ ] GPS location capture
- [ ] Driver live location
- [ ] Route calculation
- [ ] Distance calculation
- [ ] Estimated fare
- [ ] ETA calculation
- [ ] Real-time driver matching

---

## 📱 Phase 3 — Modern User Experience

- [ ] Responsive mobile-first UI
- [ ] PWA support
- [ ] Driver mobile dashboard
- [ ] Customer mobile dashboard
- [ ] Push notifications
- [ ] SMS notifications
- [ ] Email notifications

---

## 💳 Phase 4 — Production Payments

- [ ] Razorpay integration
- [ ] Stripe integration
- [ ] UPI payment verification
- [ ] Payment webhooks
- [ ] Refund management
- [ ] Transaction history
- [ ] Invoice generation

---

## 🤖 Phase 5 — Intelligent Transportation

Future versions could introduce:

- 🤖 AI-based driver matching
- 📈 Demand prediction
- 💰 Dynamic pricing
- 🗺️ Route optimization
- 🚦 Traffic-aware ETA
- 📊 Driver performance analytics
- 🔍 Fraud detection

---

# 📸 Documentation Assets

The repository already contains a large collection of application screenshots.

Recommended documentation organization:

```text
docs/
│
├── images/
│   ├── home.png
│   ├── user-dashboard.png
│   ├── booking.png
│   ├── driver-dashboard.png
│   ├── admin.png
│   └── payment.png
│
└── demo/
    ├── user-booking.gif
    ├── driver-flow.gif
    └── ride-journey.gif
```

This structure can make the GitHub README much cleaner than linking every raw screenshot from the repository root.

---

# 🎓 What This Project Demonstrates

Cabify demonstrates practical experience with:

- 🐍 Python development
- 🌐 Flask web development
- 🗄️ Relational databases
- 🔐 Authentication
- 🔑 Session management
- 🔒 Password hashing
- 👤 Multi-role applications
- 🚗 Transportation workflows
- 📋 CRUD operations
- 📁 File uploads
- 💳 Payment interfaces
- 🎨 Responsive web UI
- 🧠 Application workflow design
- 🗃️ MySQL-to-SQLite adaptation

It is particularly useful as a portfolio project because it demonstrates more than a simple CRUD application: it contains **multiple user roles, booking workflows, driver management, authorization, documents, and ride-state handling**.

---

# 👨‍💻 Author

<p align="center">
  <strong>Yasir Khan</strong><br>
  Python / Flask / Django Developer<br>
  Web Developer • AI/ML Enthusiast
</p>

<p align="center">
  <a href="https://github.com/yasirkhan251">
    <img src="https://img.shields.io/badge/GitHub-yasirkhan251-black?style=for-the-badge&logo=github" alt="GitHub">
  </a>
</p>

---

## ⭐ Project

If this project helped you understand Flask-based transportation systems, feel free to explore the repository and its implementation.

<p align="center">
  <strong>🚖 Cabify — Connecting Customers, Drivers & Rides</strong>
</p>