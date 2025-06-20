# Complaint Management System (CMS) 

A web-based Complaint Management System developed as part of the Graduate Diploma in Software Engineering (GDSE) program at IJSE. This system allows users (employees and admins) to submit, manage, and track complaints efficiently.

---

## 🚀 Features

- 👤 User Registration (Admin/Employee)
- 🔐 Login Authentication with Role-based Access
- 📝 Complaint Submission by Employees
- 📋 Complaint Review & Management by Admins
- 🧾 Complaint Status Updates (PENDING, IN_PROGRESS, RESOLVED, REJECTED)
- 📅 Auto Timestamping on Complaint Creation/Updates
- 🔒 Secure Input Validation and Error Handling
- 🎨 Modern, Responsive UI with Bootstrap 5
- 💾 Data persistence using JDBC + MySQL
- ☕ Built with JSP + Servlets using MVC architecture

---

## 🛠️ Technologies Used

- Java (JDK 17+)
- JSP & Servlets (Jakarta EE)
- Apache Tomcat 10.x
- MySQL (v8.0+)
- Apache Commons DBCP for connection pooling
- Bootstrap 5 & Icons
- HTML, CSS, JavaScript

---

## 📂 Project Structure

Complaint-Management-System/
├── src/
│ ├── controller/
│ │ └── SignUpServlet.java, AuthServlet.java, ComplaintServlet.java
│ ├── dto/
│ │ └── UserDTO.java, ComplaintDTO.java
│ ├── model/
│ │ └── UserModel.java, ComplaintModel.java
├── web/
│ ├── pages/
│ │ └── index.jsp, signup.jsp, dashboard.jsp, complaints.jsp
│ ├── static/
│ │ └── css/, js/
│ └── WEB-INF/
│ └── web.xml



---

## ⚙️ How to Run the Project

1. **Clone this repository**  
   ```bash
   git clone https://github.com/yourusername/cms-project.git
   cd cms-project
Import the project into IntelliJ IDEA or Eclipse

Configure Tomcat Server

Version: Apache Tomcat 10.x

Deployment: Deploy war or web exploded version

Configure Database

Create a database named complaint_management

Run the following SQL to create tables:

CREATE TABLE users
(
    id         INT PRIMARY KEY AUTO_INCREMENT,
    username   VARCHAR(50) UNIQUE         NOT NULL,
    password   VARCHAR(255)               NOT NULL,
    full_name  VARCHAR(100)               NOT NULL,
    email      VARCHAR(100)               NOT NULL,
    role       ENUM ('EMPLOYEE', 'ADMIN') NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE complaints
(
    id            INT PRIMARY KEY AUTO_INCREMENT,
    title         VARCHAR(200) NOT NULL,
    description   TEXT         NOT NULL,
    category      VARCHAR(50)  NOT NULL,
    status        ENUM ('PENDING', 'IN_PROGRESS', 'RESOLVED', 'REJECTED') DEFAULT 'PENDING',
    priority      ENUM ('LOW', 'MEDIUM', 'HIGH')                          DEFAULT 'MEDIUM',
    submitted_by  INT          NOT NULL,
    assigned_to   INT          NULL,
    admin_remarks TEXT         NULL,
    created_at    TIMESTAMP                                               DEFAULT CURRENT_TIMESTAMP,
    updated_at    TIMESTAMP                                               DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (submitted_by) REFERENCES users (id),
    FOREIGN KEY (assigned_to) REFERENCES users (id)
);


Configure Database Connection Pool in DBCPContextListener


dataSource.setUrl("jdbc:mysql://localhost:3306/cms_db");
dataSource.setUsername("root");
dataSource.setPassword("yourpassword");
Start the server and open browser
Navigate to: http://localhost:8080/

