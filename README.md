# DLC Assured Advanced Diploma in AI & Data Science
## Object Oriented Programming - Final Practical Assessment
## Complete Solutions Document

---

## SECTION A – JAVA BASICS (30 Marks)

### Q1. Greatest Number Program (10 Marks)

**File: GreatestNumber.java**

```java
import java.util.Scanner;

public class GreatestNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        int num1, num2, num3;
        
        // Input with validation for first number
        do {
            System.out.print("Enter first positive integer: ");
            num1 = scanner.nextInt();
            if (num1 <= 0) {
                System.out.println("Error: Only positive numbers allowed!");
            }
        } while (num1 <= 0);
        
        // Input with validation for second number
        do {
            System.out.print("Enter second positive integer: ");
            num2 = scanner.nextInt();
            if (num2 <= 0) {
                System.out.println("Error: Only positive numbers allowed!");
            }
        } while (num2 <= 0);
        
        // Input with validation for third number
        do {
            System.out.print("Enter third positive integer: ");
            num3 = scanner.nextInt();
            if (num3 <= 0) {
                System.out.println("Error: Only positive numbers allowed!");
            }
        } while (num3 <= 0);
        
        // Find greatest number using if-else
        int greatest;
        
        if (num1 >= num2 && num1 >= num3) {
            greatest = num1;
        } else if (num2 >= num1 && num2 >= num3) {
            greatest = num2;
        } else {
            greatest = num3;
        }
        
        System.out.println("\nThe greatest number is: " + greatest);
        
        scanner.close();
    }
}
```

**Sample Input/Output:**
```
Test Case 1:
Enter first positive integer: 45
Enter second positive integer: 78
Enter third positive integer: 32
The greatest number is: 78

Test Case 2:
Enter first positive integer: -5
Error: Only positive numbers allowed!
Enter first positive integer: 15
Enter second positive integer: 22
Enter third positive integer: 19
The greatest number is: 22
```

---

### Q2. Grade Calculator Method (10 Marks)

**File: GradeCalculator.java**

```java
public class GradeCalculator {
    
    // Method to return grade based on marks
    public static String getGrade(int marks) {
        if (marks >= 75) {
            return "Distinction";
        } else if (marks >= 65 && marks <= 74) {
            return "Merit";
        } else if (marks >= 50 && marks <= 64) {
            return "Pass";
        } else {
            return "Fail";
        }
    }
    
    // Main method to test with different inputs
    public static void main(String[] args) {
        // Test Case 1
        int marks1 = 85;
        System.out.println("Marks: " + marks1 + " -> Grade: " + getGrade(marks1));
        
        // Test Case 2
        int marks2 = 68;
        System.out.println("Marks: " + marks2 + " -> Grade: " + getGrade(marks2));
        
        // Test Case 3
        int marks3 = 55;
        System.out.println("Marks: " + marks3 + " -> Grade: " + getGrade(marks3));
        
        // Test Case 4
        int marks4 = 42;
        System.out.println("Marks: " + marks4 + " -> Grade: " + getGrade(marks4));
        
        // Test Case 5
        int marks5 = 75;
        System.out.println("Marks: " + marks5 + " -> Grade: " + getGrade(marks5));
        
        // Test Case 6
        int marks6 = 50;
        System.out.println("Marks: " + marks6 + " -> Grade: " + getGrade(marks6));
    }
}
```

**Sample Output:**
```
Marks: 85 -> Grade: Distinction
Marks: 68 -> Grade: Merit
Marks: 55 -> Grade: Pass
Marks: 42 -> Grade: Fail
Marks: 75 -> Grade: Distinction
Marks: 50 -> Grade: Pass
```

---

### Q3. Day of Week Switch Statement (10 Marks)

**File: DayOfWeek.java**

```java
import java.util.Scanner;

public class DayOfWeek {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter a number (1-7): ");
        int day = scanner.nextInt();
        
        switch (day) {
            case 1:
                System.out.println("Monday");
                break;
            case 2:
                System.out.println("Tuesday");
                break;
            case 3:
                System.out.println("Wednesday");
                break;
            case 4:
                System.out.println("Thursday");
                break;
            case 5:
                System.out.println("Friday");
                break;
            case 6:
                System.out.println("Saturday");
                break;
            case 7:
                System.out.println("Sunday");
                break;
            default:
                System.out.println("Invalid input! Please enter a number between 1 and 7.");
        }
        
        scanner.close();
    }
}
```

**Sample Input/Output:**
```
Test Case 1:
Enter a number (1-7): 1
Monday

Test Case 2:
Enter a number (1-7): 4
Thursday

Test Case 3:
Enter a number (1-7): 7
Sunday

Test Case 4:
Enter a number (1-7): 9
Invalid input! Please enter a number between 1 and 7.
```

---

## SECTION B – JAVA SWING CRUD (30 Marks)

### Q4. StudentForm Design Explanation (15 Marks)

**Theory Answer:**

#### 1. Form Design Overview

The StudentForm will be designed as a JFrame-based GUI application with the following components:

**UI Components:**
- **JTextField txtStudentId** - For entering/displaying Student ID
- **JTextField txtName** - For entering/displaying Student Name
- **JTextField txtCourse** - For entering/displaying Course Name
- **JButton btnAdd** - To add new student records
- **JButton btnUpdate** - To update existing records
- **JButton btnDelete** - To delete student records
- **JButton btnView** - To view all student records
- **JTable tblStudents** - To display all student data
- **JScrollPane** - To make the table scrollable
- **JLabel** components - For field labels

#### 2. Database Connection Setup

**Database Configuration:**
```sql
Database Name: student_db
Table Name: students
Table Structure:
- id INT PRIMARY KEY
- name VARCHAR(100) NOT NULL
- course VARCHAR(100) NOT NULL
```

**JDBC Connection Details:**
- Driver: MySQL Connector/J (com.mysql.cj.jdbc.Driver)
- Connection URL: jdbc:mysql://localhost:3306/student_db
- Username: root
- Password: (your MySQL password)

#### 3. CRUD Operations Flow

**ADD Operation:**
1. User enters Student ID, Name, and Course in text fields
2. User clicks "Add" button
3. System validates that all fields are filled
4. Creates database connection using DriverManager.getConnection()
5. Prepares SQL INSERT statement with PreparedStatement
6. Sets parameters from text fields to prevent SQL injection
7. Executes the INSERT using executeUpdate()
8. Displays success message using JOptionPane
9. Clears all text fields
10. Calls refreshTable() method to update JTable
11. Closes database connection in finally block

**UPDATE Operation:**
1. User selects a row from JTable using mouse click
2. Selected row data populates the text fields automatically
3. User modifies the required fields
4. User clicks "Update" button
5. System validates the Student ID exists
6. Creates database connection
7. Prepares SQL UPDATE statement: UPDATE students SET name=?, course=? WHERE id=?
8. Sets new values from text fields as parameters
9. Executes the UPDATE statement
10. Shows success confirmation message
11. Clears text fields and refreshes JTable
12. Closes connection

**DELETE Operation:**
1. User selects a row from JTable or enters Student ID
2. User clicks "Delete" button
3. System shows confirmation dialog: "Are you sure you want to delete?"
4. If user confirms (Yes), proceed with deletion
5. Creates database connection
6. Prepares SQL DELETE statement: DELETE FROM students WHERE id=?
7. Sets Student ID as parameter
8. Executes the DELETE statement
9. Shows success message
10. Clears fields and refreshes JTable
11. Closes connection

**VIEW Operation:**
1. Triggered automatically on form load or when "View" button is clicked
2. Creates database connection
3. Creates Statement object
4. Executes SQL SELECT query: SELECT * FROM students ORDER BY id
5. Gets ResultSet containing all records
6. Creates DefaultTableModel with column names
7. Loops through ResultSet using rs.next()
8. For each row, extracts id, name, course
9. Adds row to DefaultTableModel using addRow()
10. Sets the model to JTable
11. Closes ResultSet, Statement, and Connection

#### 4. Key Classes and Methods

**JDBC Classes:**
- Class.forName() - Load MySQL driver
- DriverManager.getConnection() - Establish connection
- Connection.prepareStatement() - Create prepared statement
- PreparedStatement.setInt(), setString() - Set parameters
- PreparedStatement.executeUpdate() - For INSERT/UPDATE/DELETE
- PreparedStatement.executeQuery() - For SELECT queries
- ResultSet.next() - Iterate through results
- ResultSet.getInt(), getString() - Extract data

**Swing Classes:**
- JFrame - Main window
- JPanel - Container for components
- JTextField - Input fields
- JButton - Action buttons
- JTable - Data display
- DefaultTableModel - Table data model
- JScrollPane - Scrollable container
- JOptionPane - Dialogs and messages
- ActionListener - Button click events
- ListSelectionListener - Table row selection

#### 5. Error Handling

**Validation:**
- Check for empty fields before database operations
- Validate Student ID is numeric
- Check if record exists before UPDATE/DELETE

**Exception Handling:**
- Try-catch blocks for SQLException
- Try-catch for NumberFormatException
- Finally block to close connections
- Display user-friendly error messages

**Connection Management:**
- Always close connections in finally block
- Or use try-with-resources statement
- Prevent connection leaks

#### 6. Advantages of This Design

- **User-Friendly:** Intuitive GUI with clear buttons and table
- **Data Integrity:** PreparedStatement prevents SQL injection
- **Real-time Updates:** JTable refreshes after each operation
- **Error Prevention:** Validation and confirmations
- **Maintainable:** Separate methods for each operation
- **Scalable:** Can easily add more fields or operations

---

### Q5. Swing CRUD Insert and Refresh Code (15 Marks)

**File: StudentCRUD.java**

```java
import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.*;

public class StudentCRUD extends JFrame {
    
    // UI Components
    private JTextField txtId, txtName, txtCourse;
    private JTable tblStudents;
    private DefaultTableModel tableModel;
    private JButton btnInsert;
    
    // Database credentials
    private static final String DB_URL = "jdbc:mysql://localhost:3306/student_db";
    private static final String DB_USER = "root";
    private static final String DB_PASSWORD = "password";
    
    public StudentCRUD() {
        // Frame setup
        setTitle("Student Management System");
        setSize(700, 500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());
        
        // Create input panel
        JPanel inputPanel = new JPanel(new GridLayout(4, 2, 10, 10));
        inputPanel.setBorder(BorderFactory.createEmptyBorder(10, 10, 10, 10));
        
        inputPanel.add(new JLabel("Student ID:"));
        txtId = new JTextField();
        inputPanel.add(txtId);
        
        inputPanel.add(new JLabel("Name:"));
        txtName = new JTextField();
        inputPanel.add(txtName);
        
        inputPanel.add(new JLabel("Course:"));
        txtCourse = new JTextField();
        inputPanel.add(txtCourse);
        
        btnInsert = new JButton("Insert Student");
        inputPanel.add(new JLabel()); // Empty cell
        inputPanel.add(btnInsert);
        
        add(inputPanel, BorderLayout.NORTH);
        
        // Create table
        String[] columnNames = {"ID", "Name", "Course"};
        tableModel = new DefaultTableModel(columnNames, 0);
        tblStudents = new JTable(tableModel);
        JScrollPane scrollPane = new JScrollPane(tblStudents);
        add(scrollPane, BorderLayout.CENTER);
        
        // Add action listener to insert button
        btnInsert.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                insertStudent();
            }
        });
        
        // Load initial data
        refreshTable();
        
        setVisible(true);
    }
    
    // Method to insert a new student record
    private void insertStudent() {
        String id = txtId.getText().trim();
        String name = txtName.getText().trim();
        String course = txtCourse.getText().trim();
        
        // Validation
        if (id.isEmpty() || name.isEmpty() || course.isEmpty()) {
            JOptionPane.showMessageDialog(this, 
                "Please fill all fields!", 
                "Validation Error", 
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        // Database operation
        Connection conn = null;
        PreparedStatement pstmt = null;
        
        try {
            // Establish connection
            conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
            
            // Prepare SQL statement
            String sql = "INSERT INTO students (id, name, course) VALUES (?, ?, ?)";
            pstmt = conn.prepareStatement(sql);
            
            // Set parameters
            pstmt.setInt(1, Integer.parseInt(id));
            pstmt.setString(2, name);
            pstmt.setString(3, course);
            
            // Execute insert
            int rowsAffected = pstmt.executeUpdate();
            
            if (rowsAffected > 0) {
                JOptionPane.showMessageDialog(this, 
                    "Student record inserted successfully!", 
                    "Success", 
                    JOptionPane.INFORMATION_MESSAGE);
                
                // Clear text fields
                txtId.setText("");
                txtName.setText("");
                txtCourse.setText("");
                
                // Refresh the table
                refreshTable();
            }
            
        } catch (SQLException ex) {
            JOptionPane.showMessageDialog(this, 
                "Database Error: " + ex.getMessage(), 
                "Error", 
                JOptionPane.ERROR_MESSAGE);
            ex.printStackTrace();
        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(this, 
                "Student ID must be a number!", 
                "Validation Error", 
                JOptionPane.ERROR_MESSAGE);
        } finally {
            // Close resources
            try {
                if (pstmt != null) pstmt.close();
                if (conn != null) conn.close();
            } catch (SQLException ex) {
                ex.printStackTrace();
            }
        }
    }
    
    // Method to refresh JTable with all student records
    private void refreshTable() {
        Connection conn = null;
        Statement stmt = null;
        ResultSet rs = null;
        
        try {
            // Establish connection
            conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
            
            // Create statement
            stmt = conn.createStatement();
            
            // Execute query
            String sql = "SELECT * FROM students ORDER BY id";
            rs = stmt.executeQuery(sql);
            
            // Clear existing table data
            tableModel.setRowCount(0);
            
            // Populate table with results
            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                String course = rs.getString("course");
                
                // Add row to table model
                tableModel.addRow(new Object[]{id, name, course});
            }
            
        } catch (SQLException ex) {
            JOptionPane.showMessageDialog(this, 
                "Error loading data: " + ex.getMessage(), 
                "Database Error", 
                JOptionPane.ERROR_MESSAGE);
            ex.printStackTrace();
        } finally {
            // Close resources
            try {
                if (rs != null) rs.close();
                if (stmt != null) stmt.close();
                if (conn != null) conn.close();
            } catch (SQLException ex) {
                ex.printStackTrace();
            }
        }
    }
    
    public static void main(String[] args) {
        // Run on Event Dispatch Thread
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new StudentCRUD();
            }
        });
    }
}
```

**Database Setup:**
```sql
CREATE DATABASE IF NOT EXISTS student_db;
USE student_db;

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    course VARCHAR(100) NOT NULL
);
```

**Required Library:**
- MySQL Connector/J (mysql-connector-java-8.0.x.jar)

**Sample Test Steps:**
1. Run the program
2. Enter ID: 101, Name: John Doe, Course: Computer Science
3. Click "Insert Student"
4. Success message appears
5. Table automatically refreshes showing the new record
6. Fields are cleared for next entry

---

## SECTION C – OOP CONCEPTS (40 Marks)

### Q6. OOP Concepts with Examples (20 Marks)

**File: OOPDemo.java**

```java
// ==================== 1. ENCAPSULATION ====================
/*
Encapsulation is the mechanism of wrapping data (variables) and methods 
that operate on the data into a single unit (class). It hides the internal 
state of an object from the outside world and only exposes necessary 
operations through public methods.

Key Features:
- Data hiding using private access modifier
- Controlled access through getter and setter methods
- Protects data integrity
- Prevents unauthorized access
*/

class Student {
    // Private fields - data hiding
    private int studentId;
    private String name;
    private double gpa;
    
    // Public getter and setter methods - controlled access
    public int getStudentId() {
        return studentId;
    }
    
    public void setStudentId(int studentId) {
        if (studentId > 0) {
            this.studentId = studentId;
        } else {
            System.out.println("Invalid student ID");
        }
    }
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public double getGpa() {
        return gpa;
    }
    
    public void setGpa(double gpa) {
        if (gpa >= 0.0 && gpa <= 4.0) {
            this.gpa = gpa;
        } else {
            System.out.println("Invalid GPA. Must be between 0.0 and 4.0");
        }
    }
}

// ==================== 2. INHERITANCE ====================
/*
Inheritance is a mechanism where a new class (child/subclass) inherits 
properties and behaviors from an existing class (parent/superclass). 
It promotes code reusability and establishes an "IS-A" relationship.

Key Features:
- Reuses existing code
- Creates hierarchical relationships
- Uses 'extends' keyword
- Child class inherits all non-private members
*/

// Parent class
class Vehicle {
    protected String brand;
    protected int year;
    
    public Vehicle(String brand, int year) {
        this.brand = brand;
        this.year = year;
    }
    
    public void displayInfo() {
        System.out.println("Brand: " + brand + ", Year: " + year);
    }
    
    public void start() {
        System.out.println("Vehicle is starting...");
    }
}

// Child class inheriting from Vehicle
class Car extends Vehicle {
    private int numberOfDoors;
    
    public Car(String brand, int year, int numberOfDoors) {
        super(brand, year); // Call parent constructor
        this.numberOfDoors = numberOfDoors;
    }
    
    // Additional method specific to Car
    public void displayCarInfo() {
        displayInfo(); // Inherited method
        System.out.println("Number of Doors: " + numberOfDoors);
    }
    
    // Child can have its own methods
    public void honk() {
        System.out.println("Car is honking: Beep! Beep!");
    }
}

// ==================== 3. POLYMORPHISM ====================
/*
Polymorphism means "many forms". It allows objects of different classes 
to be treated as objects of a common parent class. The same method name 
can behave differently based on the object that invokes it.

Types:
1. Compile-time (Method Overloading)
2. Runtime (Method Overriding)

Key Features:
- One interface, multiple implementations
- Improves flexibility and maintainability
*/

// Parent class
class Animal {
    public void makeSound() {
        System.out.println("Animal makes a sound");
    }
    
    public void eat() {
        System.out.println("Animal is eating");
    }
}

// Child class 1
class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Dog barks: Woof! Woof!");
    }
    
    // Method overloading (compile-time polymorphism)
    public void play() {
        System.out.println("Dog plays with ball");
    }
    
    public void play(String toy) {
        System.out.println("Dog plays with " + toy);
    }
}

// Child class 2
class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Cat meows: Meow! Meow!");
    }
}

// Main class to demonstrate all concepts
class OOPDemo {
    public static void main(String[] args) {
        System.out.println("========== ENCAPSULATION DEMO ==========");
        Student student = new Student();
        student.setStudentId(101);
        student.setName("Alice");
        student.setGpa(3.8);
        
        System.out.println("Student ID: " + student.getStudentId());
        System.out.println("Name: " + student.getName());
        System.out.println("GPA: " + student.getGpa());
        
        // Trying to set invalid GPA
        student.setGpa(5.0); // Will show error message
        
        System.out.println("\n========== INHERITANCE DEMO ==========");
        Car myCar = new Car("Toyota", 2023, 4);
        myCar.displayCarInfo(); // Uses both parent and child methods
        myCar.start(); // Inherited method
        myCar.honk(); // Own method
        
        System.out.println("\n========== POLYMORPHISM DEMO ==========");
        // Runtime polymorphism (Method Overriding)
        Animal myAnimal = new Animal();
        Animal myDog = new Dog();
        Animal myCat = new Cat();
        
        myAnimal.makeSound(); // Output: Animal makes a sound
        myDog.makeSound();    // Output: Dog barks: Woof! Woof!
        myCat.makeSound();    // Output: Cat meows: Meow! Meow!
        
        // Compile-time polymorphism (Method Overloading)
        Dog realDog = new Dog();
        realDog.play();           // Output: Dog plays with ball
        realDog.play("frisbee");  // Output: Dog plays with frisbee
    }
}
```

**Expected Output:**
```
========== ENCAPSULATION DEMO ==========
Student ID: 101
Name: Alice
GPA: 3.8
Invalid GPA. Must be between 0.0 and 4.0

========== INHERITANCE DEMO ==========
Brand: Toyota, Year: 2023
Number of Doors: 4
Vehicle is starting...
Car is honking: Beep! Beep!

========== POLYMORPHISM DEMO ==========
Animal makes a sound
Dog barks: Woof! Woof!
Cat meows: Meow! Meow!
Dog plays with ball
Dog plays with frisbee
```

---

### Q7. Bank Account Inheritance System (20 Marks)

**File: BankAccountSystem.java**

```java
// Parent class - Base Account
class Account {
    protected String accountNumber;
    protected double balance;
    
    // Constructor
    public Account(String accountNumber, double initialBalance) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }
    
    // Method to deposit money
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount);
            System.out.println("New Balance: $" + balance);
        } else {
            System.out.println("Invalid deposit amount!");
        }
    }
    
    // Method to withdraw money
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: $" + amount);
            System.out.println("New Balance: $" + balance);
        } else {
            System.out.println("Insufficient balance or invalid amount!");
        }
    }
    
    // Method to display account details
    public void displayAccountInfo() {
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Balance: $" + balance);
    }
}

// Child class 1 - Savings Account
class SavingsAccount extends Account {
    private double interestRate;
    
    // Constructor
    public SavingsAccount(String accountNumber, double initialBalance, double interestRate) {
        super(accountNumber, initialBalance);
        this.interestRate = interestRate;
    }
    
    // Method to calculate and add interest
    public void addInterest() {
        double interest = balance * (interestRate / 100);
        balance += interest;
        System.out.println("Interest Added: $" + interest + " at " + interestRate + "%");
        System.out.println("New Balance: $" + balance);
    }
    
    // Override display method to include interest rate
    @Override
    public void displayAccountInfo() {
        System.out.println("=== Savings Account ===
Account Number: SA-12345
Balance: $5000.0
Interest Rate: 3.5%

--- Testing Savings Account Operations ---
Deposited: $1500.0
New Balance: $6500.0

Withdrawn: $2000.0
New Balance: $4500.0

Interest Added: $157.5 at 3.5%
New Balance: $4657.5

=== Savings Account ===
Account Number: SA-12345
Balance: $4657.5
Interest Rate: 3.5%


========================================

>>> Creating Checking Account <<<
=== Checking Account ===
Account Number: CA-67890
Balance: $3000.0
Overdraft Limit: $1000.0

--- Testing Checking Account Operations ---
Deposited: $500.0
New Balance: $3500.0

Withdrawn: $2500.0
New Balance: $1000.0

--- Testing Overdraft Feature ---
Withdrawn: $1200.0
New Balance: $-200.0
WARNING: Overdraft used. Amount: $200.0

=== Checking Account ===
Account Number: CA-67890
Balance: $-200.0
Overdraft Limit: $1000.0
Current Overdraft: $200.0

--- Attempting to Exceed Overdraft Limit ---
Withdrawal denied! Exceeds overdraft limit.
Available: $800.0

--- Recovering from Overdraft ---
Deposited: $1000.0
New Balance: $800.0

=== Checking Account ===
Account Number: CA-67890
Balance: $800.0
Overdraft Limit: $1000.0


========================================
*     DEMONSTRATION COMPLETED          *
========================================
```

**Key Features Demonstrated:**

1. **Inheritance:** 
   - Both SavingsAccount and CheckingAccount inherit from Account
   - Shared properties: accountNumber, balance
   - Shared methods: deposit(), withdraw(), displayAccountInfo()

2. **Code Reusability:**
   - deposit() method inherited and used by both child classes
   - Basic withdraw() inherited by SavingsAccount
   - displayAccountInfo() inherited and enhanced by both

3. **Method Overriding:**
   - CheckingAccount overrides withdraw() for overdraft functionality
   - Both child classes override displayAccountInfo() to add specific details

4. **Polymorphism:**
   - Same method names behave differently in different classes
   - displayAccountInfo() shows different output for each account type

5. **Encapsulation:**
   - Protected fields accessible to child classes
   - Private field (interestRate) specific to SavingsAccount
   - Public methods provide controlled access

6. **Additional Features:**
   - SavingsAccount: interestRate field and addInterest() method
   - CheckingAccount: OVERDRAFT_LIMIT constant and modified withdraw()

---

## SUBMISSION CHECKLIST

### Files to Create:

**Section A:**
- [ ] GreatestNumber.java
- [ ] GradeCalculator.java
- [ ] DayOfWeek.java

**Section B:**
- [ ] StudentCRUD.java
- [ ] Create MySQL database and table

**Section C:**
- [ ] OOPDemo.java
- [ ] BankAccountSystem.java

### Word Document Requirements:

Create a Word document with:

1. **Title Page:**
   - Course: DLC Assured Advanced Diploma in AI & Data Science
   - Subject: Object Oriented Programming
   - Student Name: [Your Name]
   - Student ID: [Your ID]
   - Date: 5th October 2025

2. **For Each Question Include:**
   - Question number and marks
   - Brief description of the program
   - Screenshot of the output with sample inputs
   - For Q4: Include the complete theory explanation
   - For Q6: Include explanations of each OOP concept

3. **Screenshots Required:**
   - Q1: Show valid input case and invalid input rejection
   - Q2: Show all grade categories (Distinction, Merit, Pass, Fail)
   - Q3: Show valid days and invalid input handling
   - Q4: No screenshot (theory only)
   - Q5: Show GUI with inserted records and refreshed table
   - Q6: Show output demonstrating all three OOP concepts
   - Q7: Show complete bank account operations output

### Final Steps:

1. **Test All Programs:**
   - Compile each Java file
   - Run and verify outputs
   - Take clear screenshots

2. **Create Word Document:**
   - Add all content as specified above
   - Format properly with headings
   - Insert all screenshots

3. **Save as PDF:**
   - Save Word document as PDF
   - Name it: YourName_OOP_Assessment.pdf

4. **Create Folder Structure:**
```
YourName_OOP_Assessment/
├── Section_A/
│   ├── GreatestNumber.java
│   ├── GradeCalculator.java
│   └── DayOfWeek.java
├── Section_B/
│   └── StudentCRUD.java
├── Section_C/
│   ├── OOPDemo.java
│   └── BankAccountSystem.java
└── YourName_OOP_Assessment.pdf
```

5. **Zip and Submit:**
   - Right-click folder → Send to → Compressed (zipped) folder
   - Upload to LMS
   - If size > 512MB, email with public access link

---

## IMPORTANT REMINDERS

⚠️ **Anti-Plagiarism:**
- All code must be written by you
- Understand every line of code
- Be prepared to explain during viva

⚠️ **Code Quality:**
- Use proper indentation (4 spaces)
- Add meaningful comments
- Follow Java naming conventions
- Handle exceptions properly

⚠️ **Database Setup for Q5:**
```sql
-- Run these commands in MySQL before running the program
CREATE DATABASE student_db;
USE student_db;
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    course VARCHAR(100) NOT NULL
);
```

⚠️ **Required Libraries:**
- MySQL Connector/J JAR file
- Add to project classpath in your IDE

⚠️ **Testing:**
- Test with multiple inputs
- Check edge cases
- Verify error handling

---

## MARKS DISTRIBUTION SUMMARY

| Section | Questions | Marks | Total |
|---------|-----------|-------|-------|
| A | Q1 + Q2 + Q3 | 10 + 10 + 10 | 30 |
| B | Q4 + Q5 | 15 + 15 | 30 |
| C | Q6 + Q7 | 20 + 20 | 40 |
| **TOTAL** | | | **100** |

---

## CONTACT FOR HELP

If you face any issues:
- Database connection errors: Check MySQL service is running
- JDBC errors: Verify mysql-connector-java.jar is in classpath
- Compilation errors: Check Java version (JDK 8+)
- Swing not displaying: Use SwingUtilities.invokeLater()

---

## GOOD LUCK! 🎓

Remember to:
✅ Test all programs thoroughly
✅ Take clear screenshots
✅ Write proper documentation
✅ Check plagiarism
✅ Submit before deadline

**All the best with your assessment!**");
        super.displayAccountInfo();
        System.out.println("Interest Rate: " + interestRate + "%");
    }
}

// Child class 2 - Checking Account
class CheckingAccount extends Account {
    private static final double OVERDRAFT_LIMIT = 1000.0;
    
    // Constructor
    public CheckingAccount(String accountNumber, double initialBalance) {
        super(accountNumber, initialBalance);
    }
    
    // Override withdraw method to allow overdraft
    @Override
    public void withdraw(double amount) {
        if (amount > 0) {
            double availableBalance = balance + OVERDRAFT_LIMIT;
            
            if (amount <= availableBalance) {
                balance -= amount;
                System.out.println("Withdrawn: $" + amount);
                System.out.println("New Balance: $" + balance);
                
                if (balance < 0) {
                    System.out.println("WARNING: Overdraft used. Amount: $" + Math.abs(balance));
                }
            } else {
                System.out.println("Withdrawal denied! Exceeds overdraft limit.");
                System.out.println("Available: $" + availableBalance);
            }
        } else {
            System.out.println("Invalid withdrawal amount!");
        }
    }
    
    // Override display method to show overdraft info
    @Override
    public void displayAccountInfo() {
        System.out.println("=== Checking Account ===");
        super.displayAccountInfo();
        System.out.println("Overdraft Limit: $" + OVERDRAFT_LIMIT);
        
        if (balance < 0) {
            System.out.println("Current Overdraft: $" + Math.abs(balance));
        }
    }
}

// Main class to demonstrate the bank account system
public class BankAccountSystem {
    public static void main(String[] args) {
        
        System.out.println("****************************************");
        System.out.println("*   BANK ACCOUNT MANAGEMENT SYSTEM    *");
        System.out.println("****************************************\n");
        
        // Creating a Savings Account
        System.out.println(">>> Creating Savings Account <<<");
        SavingsAccount savings = new SavingsAccount("SA-12345", 5000.0, 3.5);
        savings.displayAccountInfo();
        
        System.out.println("\n--- Testing Savings Account Operations ---");
        savings.deposit(1500.0);
        System.out.println();
        
        savings.withdraw(2000.0);
        System.out.println();
        
        savings.addInterest();
        System.out.println();
        
        savings.displayAccountInfo();
        
        System.out.println("\n\n========================================\n");
        
        // Creating a Checking Account
        System.out.println(">>> Creating Checking Account <<<");
        CheckingAccount checking = new CheckingAccount("CA-67890", 3000.0);
        checking.displayAccountInfo();
        
        System.out.println("\n--- Testing Checking Account Operations ---");
        checking.deposit(500.0);
        System.out.println();
        
        checking.withdraw(2500.0);
        System.out.println();
        
        // Testing overdraft functionality
        System.out.println("--- Testing Overdraft Feature ---");
        checking.withdraw(1200.0); // This will use overdraft
        System.out.println();
        
        checking.displayAccountInfo();
        System.out.println();
        
        // Trying to exceed overdraft limit
        System.out.println("--- Attempting to Exceed Overdraft Limit ---");
        checking.withdraw(500.0); // This should be denied
        System.out.println();
        
        // Deposit to recover from overdraft
        System.out.println("--- Recovering from Overdraft ---");
        checking.deposit(1000.0);
        System.out.println();
        
        checking.displayAccountInfo();
        
        System.out.println("\n\n========================================");
        System.out.println("*     DEMONSTRATION COMPLETED          *");
        System.out.println("========================================");
    }
}
```

**Expected Output:**
```
****************************************
*   BANK ACCOUNT MANAGEMENT SYSTEM    *
****************************************

>>> Creating Savings Account <<<
=== Savings Account ===
