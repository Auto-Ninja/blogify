## Java Database Connectivity
JDBC (Java Database Connectivity) is a Java API that enables applications to interact with databases using SQL. It provides a standard way to connect, query, and manipulate data across various databases like MySQL, MS Access, and even Excel.

### 🧠 What Is JDBC and Why Use It?
JDBC is part of Java SE and allows Java programs to:
- Connect to databases
- Execute SQL queries
- Retrieve and update data

### ✅ Purpose of JDBC
- Database independence: Works with any relational database via drivers.
- Standardized access: Unified API for CRUD operations.
- Integration: Enables Java apps to persist and retrieve data.

### 🧩 JDBC Architecture & Components
🔧 Key Components
Component	Role
DriverManager	Manages database drivers and connections
Connection	Establishes a session with the database
Statement	Executes SQL queries
ResultSet	Holds data returned by queries
PreparedStatement	Executes parameterized queries
### 🏗️ Architecture Models
```plaintext
Two-Tier Architecture:
[Java Application] ↔ [Database via JDBC Driver]

Three-Tier Architecture:
[Java Application] ↔ [Middleware] ↔ [Database]
```
### 💻 JDBC Code Examples
#### 1️⃣ MySQL Connection
```java
import java.sql.*;

public class MySQLExample {
    public static void main(String[] args) throws Exception {
        Class.forName("com.mysql.cj.jdbc.Driver");
        Connection con = DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/ecommerce", "root", "password");

        Statement stmt = con.createStatement();
        ResultSet rs = stmt.executeQuery("SELECT * FROM products");

        while (rs.next()) {
            System.out.println(rs.getString("name"));
        }

        con.close();
    }
}
```
#### 2️⃣ MS Access Connection
```java
import java.sql.*;

public class AccessExample {
    public static void main(String[] args) throws Exception {
        Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
        Connection con = DriverManager.getConnection(
            "jdbc:ucanaccess://C:/data/ecommerce.accdb");

        Statement stmt = con.createStatement();
        ResultSet rs = stmt.executeQuery("SELECT * FROM orders");

        while (rs.next()) {
            System.out.println(rs.getInt("order_id"));
        }

        con.close();
    }
}
```
#### 3️⃣ Excel Connection (via JDBC-ODBC Bridge or Apache POI)
```java
import java.sql.*;
public class ExcelExample {
    public static void main(String[] args) throws Exception {
        Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
        Connection con = DriverManager.getConnection(
            "jdbc:odbc:Driver={Microsoft Excel Driver (*.xls)};DBQ=C:/data/sales.xls");

        Statement stmt = con.createStatement();
        ResultSet rs = stmt.executeQuery("SELECT * FROM [Sheet1$]");

        while (rs.next()) {
            System.out.println(rs.getString("Product"));
        }

        con.close();
    }
}
```
⚠️ Note: Excel JDBC access is deprecated; prefer Apache POI for modern Excel handling.

### 📦 General JDBC Dependencies
| **Requirement**           | **Description**                                                                 |
|---------------------------|----------------------------------------------------------------------------------|
| **JDK**                   | Java Development Kit installed (version 8+ recommended)                         |
| **JDBC Driver**           | A database-specific driver (JAR file) that enables Java to talk to the database |
| **Database**              | The actual database (MySQL server, Access file, Excel sheet)                    |
| **Classpath Configuration** | The JDBC driver JAR must be added to your project’s classpath                  |
| **Connection URL**        | A properly formatted JDBC URL for the target database        
### 🐬 MySQL JDBC Dependencies
## 🐬 MySQL JDBC Dependencies

| **Dependency**     | **Details**                                      |
|--------------------|--------------------------------------------------|
| **Driver**         | `mysql-connector-java-x.x.xx.jar`                |
| **Download**       | [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/) |
| **Connection URL** | `jdbc:mysql://localhost:3306/dbname`             |
Example
```java
Class.forName("com.mysql.cj.jdbc.Driver");
Connection con = DriverManager.getConnection(
  "jdbc:mysql://localhost:3306/ecommerce", "root", "password");
```
### 🗂️ MS Access JDBC Dependencies
| **Dependency**     | **Details**                                                                 |
|--------------------|------------------------------------------------------------------------------|
| **Driver**         | `ucanaccess-x.x.x.jar` (plus `jackcess`, `commons-lang`, etc.)               |
| **Download**       | [UCanAccess](http://ucanaccess.sourceforge.net/site.html)                   |
| **Connection URL** | `jdbc:ucanaccess://C:/path/to/database.accdb`                               |
Example
```java
Class.forName("net.ucanaccess.jdbc.UcanaccessDriver");
Connection con = DriverManager.getConnection(
  "jdbc:ucanaccess://C:/data/ecommerce.accdb");
```
### 📊 Excel JDBC Dependencies
## 📊 Excel JDBC Dependencies

| **Dependency**           | **Details**                                                                 |
|--------------------------|------------------------------------------------------------------------------|
| **Driver (Legacy)**      | JDBC-ODBC Bridge (deprecated in Java 8+)                                     |
| **Modern Alternative**   | Use Apache POI to read/write Excel files                                     |
| **Connection URL (ODBC)**| `jdbc:odbc:Driver={Microsoft Excel Driver (*.xls)};DBQ=C:/data/sales.xls`    |
| **Apache POI**           | [Apache POI Library](https://poi.apache.org/)                                |
Example (POI)
```java
FileInputStream fis = new FileInputStream("sales.xlsx");
Workbook workbook = new XSSFWorkbook(fis);
Sheet sheet = workbook.getSheetAt(0);
```
### ✅ How to Add Dependencies
#### 🔧 In Eclipse or IntelliJ:
- Right-click your project → Build Path → Add External JARs
- Add the JDBC driver JAR file

### 📦 In Maven:
```xml
<!-- MySQL -->
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <version>8.0.33</version>
</dependency>

<!-- UCanAccess -->
<dependency>
  <groupId>net.sf.ucanaccess</groupId>
  <artifactId>ucanaccess</artifactId>
  <version>5.0.1</version>
</dependency>

<!-- Apache POI for Excel -->
<dependency>
  <groupId>org.apache.poi</groupId>
  <artifactId>poi-ooxml</artifactId>
  <version>5.2.3</version>
</dependency>
```
### 🛒 Real-World E-Commerce Use Case
- Product Catalog: Stored in MySQL, accessed via JDBC.
- Order History: Archived in MS Access for legacy support.
- Sales Reports: Exported to Excel, read via JDBC or POI.

```plaintext
[Java App]
 ├── MySQL → Live product data
 ├── Access → Archived orders
 └── Excel → Sales analytics
```