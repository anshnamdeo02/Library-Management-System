# Library Management System

A robust, Java-based Library Management System with a Swing UI designed in NetBeans and backed by a MySQL database.

---

## Prerequisites

* **Java Development Kit**: JDK 22 or higher
* **IDE**: NetBeans IDE 17 or above (with GUI Builder)
* **Database**: MySQL Server 8.x
* **Database Client**: MySQL Workbench or CLI
* **JDBC Driver**: MySQL Connector/J 8.x

---

## Repository Structure

```
Library-Management-System/
├── src/
│   └── library/
│       ├── ClerkMenuUI.java
│       ├── LibrarianMenu.java
│       ├── LoginUI.java
│       ├── StudentMenuUI.java
│       ├── dbConnectivity.java
│       └── *.form
├── sql/
│   └── schema.sql
├── .gitignore
└── README.md
```

* `src/library/`: Java source files and NetBeans form definitions
* `sql/schema.sql`: SQL script to create database and tables

---

## Environment Configuration

1. **Set JAVA\_HOME** (Windows):

   ```batch
   setx JAVA_HOME "C:\Program Files\Java\jdk-22"
   setx PATH "%JAVA_HOME%\bin;%PATH%"
   ```

2. **Verify JDK**:

   ```bash
   java -version
   javac -version
   ```

3. **Install MySQL**: Use MySQL Installer for Windows. Include:

   * MySQL Server 8.x
   * MySQL Workbench
   * MySQL Connector/J

4. **Configure MySQL**:

   * Start MySQL Server
   * Optionally configure to start automatically

---

## Database Setup

1. **Create schema and user** by executing `sql/schema.sql` in MySQL Workbench or CLI:

   ```sql
   -- schema.sql
   CREATE DATABASE IF NOT EXISTS Library;
   USE Library;

   CREATE TABLE IF NOT EXISTS Users (
     id INT AUTO_INCREMENT PRIMARY KEY,
     username VARCHAR(50) NOT NULL UNIQUE,
     password VARCHAR(100) NOT NULL,
     role ENUM('librarian','clerk','student') NOT NULL,
     created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   CREATE TABLE IF NOT EXISTS Books (
     id INT AUTO_INCREMENT PRIMARY KEY,
     title VARCHAR(200) NOT NULL,
     author VARCHAR(100),
     isbn VARCHAR(20) UNIQUE,
     available BOOLEAN DEFAULT TRUE,
     created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );

   CREATE USER IF NOT EXISTS 'new_user'@'localhost' IDENTIFIED BY '123';
   GRANT ALL PRIVILEGES ON Library.* TO 'new_user'@'localhost';
   FLUSH PRIVILEGES;
   ```

2. **Verify tables**:

   ```sql
   SHOW TABLES IN Library;
   SELECT * FROM Users;
   SELECT * FROM Books;
   ```

---

## Building & Running

1. **Open NetBeans** → `File` → `Open Project` → select `Library-Management-System`
2. **Add JDBC Driver**:

   * Right-click project → `Properties` → `Libraries` → `Compile` tab
   * Click `Add JAR/Folder` → choose `mysql-connector-j-8.x.x.jar`
3. **Configure DB connection** in `dbConnectivity.java`:

   ```java
   String url = "jdbc:mysql://localhost:3306/Library?useSSL=false&serverTimezone=UTC";
   con = DriverManager.getConnection(url, "new_user", "123");
   ```
4. **Build project**: `Run` → `Clean and Build Project` (or Ctrl+F11)
5. **Run Login UI**:

   * Right-click `LoginUI.java` → `Run File`

---

## Testing

* **Test user login**:

  * Use credentials created in schema.sql
  * Validate role-based menu launches
* **CRUD operations**:

  * Add, remove, search books via UI
  * Check MySQL Workbench to confirm data changes

---

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/YourFeature`
3. Commit changes: `git commit -m "Add YourFeature description"`
4. Push: `git push origin feature/YourFeature`
5. Open a Pull Request

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 👤 Author

**Ansh Namdeo** — [GitHub Profile](https://github.com/anshnamdeo02)
