# CGPA Calculator (PHP + MySQL via XAMPP)

## 📌 Overview

The **CGPA Calculator** is a web-based application developed using **PHP, MySQL, and XAMPP**. It helps students manage their semester grades, calculate GPA/CGPA, and view results semester-wise. The system is designed with a simple UI, clean database structure, and modular PHP scripts.

---

## ⚙️ Tech Stack

* **Frontend:** HTML5, CSS3 (custom styles), PHP embedded
* **Backend:** PHP (Core PHP)
* **Database:** MySQL (via XAMPP phpMyAdmin)
* **Server:** Apache (XAMPP)

---

## 📂 Project Structure

```plaintext
cgpa-calculator/
├── assets/                
    ├── styles.css         # CSS/images
├── db/
    ├── cgpa-db            # Database-related files
├── add_grades.php         # Form to add student grades
├── calculate_cgpa.php     # Logic for GPA/CGPA calculation
├── index.php              # Home page / entry point
├── view_gpa.php           # View calculated GPA
├── view_semesters.php     # List semesters and courses
└── cgpa-db.sql            # Database schema & seed data
```

---

## 🗄️ Database Schema

Defined in [`cgpa-db.sql`](sql/cgpa-db.sql).

### 1️⃣ `semesters`

Stores semester details.

```sql
semester_id INT AUTO_INCREMENT PRIMARY KEY,
semester_number INT NOT NULL,
description VARCHAR(50)
```

### 2️⃣ `courses`

Stores courses for each semester with credits.

```sql
course_id INT AUTO_INCREMENT PRIMARY KEY,
semester_id INT,
course_name VARCHAR(100) NOT NULL,
credits INT NOT NULL,
FOREIGN KEY (semester_id) REFERENCES semesters(semester_id)
```

### 3️⃣ `grades`

Stores grades for students.

```sql
grade_id INT AUTO_INCREMENT PRIMARY KEY,
student_id INT NOT NULL,
course_id INT,
grade CHAR(2),
FOREIGN KEY (course_id) REFERENCES courses(course_id)
```

### 4️⃣ `grade_scores`

Maps letter grades to numeric values.

```sql
grade CHAR(2) PRIMARY KEY,
score INT NOT NULL
```

---

## 🚀 Features

* 🎓 **Add Grades** – Input grades for each course with credit hours.
* 📊 **Calculate GPA & CGPA** – Compute results dynamically based on grade weights.
* 📑 **View Semester Results** – Organized view of GPA semester by semester.
* 📈 **Cumulative Report** – Track overall academic performance.
* 🎨 **Responsive UI** – Styled with `styles.css`.

---

## 🔧 Setup Instructions

### 1️⃣ Install XAMPP

* Download from [Apache Friends](https://www.apachefriends.org/).
* Install and start **Apache** + **MySQL** from Control Panel.

### 2️⃣ Project Setup

* Copy project folder into:

```plaintext
C:\xampp\htdocs\cgpa-calculator
```

### 3️⃣ Database Setup

1. Open phpMyAdmin → [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
2. Create a database:

```sql
CREATE DATABASE CGPA_Calculator;
```

3. Import `cgpa-db.sql` to create tables and insert default data.

### 4️⃣ Run Project

Open in browser:

```plaintext
http://localhost/cgpa-calculator/
```

---

## 📖 Core Workflows

### Add Grades

* `add_grades.php` – Give input grades for each course.

### Calculate CGPA

* `calculate_cgpa.php` – Processes grades, multiplies by credit weights, and computes CGPA.

### View CGPA Results

* `view_cgpa.php` – Displays calculated results.

### View Semesters & Courses

* `view_semesters.php` – Lists all semesters with their respective subjects and credits.

---

## 🛠️ Troubleshooting

* **Apache not starting** → Port conflict → Change Apache port in `httpd.conf`.
* **MySQL not starting** → Ensure no other MySQL instance is running.
* **Blank page** → Enable error reporting in PHP: `error_reporting(E_ALL); ini_set('display_errors', 1);`
* **Styles not loading** → Check path to `assets/styles.css`.

---

## 📌 Roadmap
Planned enhancements for future versions of the system:
*  User authentication to track multiple students
*  Import/export grades via Excel
*  Responsive design for mobile
*  Graphical representation of GPA trends

---

✅ This project is ideal for **students** to practice PHP & MySQL while solving a real academic need: tracking CGPA across semesters.
