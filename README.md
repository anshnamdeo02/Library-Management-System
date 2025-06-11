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


---

## 👤 Author

**Ansh Namdeo** — [GitHub Profile](https://github.com/anshnamdeo02)
