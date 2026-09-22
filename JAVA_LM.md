# Practical 1

**Aim:** Write a simple "Hello World" java program, compilation, debugging, executing using java compiler and interpreter.**

**Java Code:**

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

**Output:**

```text
Hello, World!
```

**Conclusion:**
In this practical, we learned how to write, compile, and execute a basic Java program using the Java compiler (`javac`) and interpreter (`java`). We gained an understanding of the structure of a Java application, including the main method entry point and basic console output commands.

---

# Practical 2

**Aim:** Write a program using the arithmetic operators to perform algebraic operations on two numbers (+,-,*,/,%).**

**Java Code:**

```java
import java.util.Scanner;

public class ArithmeticOperations {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = scanner.nextInt();

        System.out.print("Enter second number: ");
        int b = scanner.nextInt();

        System.out.println("Addition (a `+` b) = " + (a + b));
        System.out.println("Subtraction (a `-` b) = " + (a - b));
        System.out.println("Multiplication (a `*` b) = " + (a * b));
        System.out.println("Division (a `/` b) = " + (a / b));
        System.out.println("Modulo (a `%` b) = " + (a % b));

        scanner.close();
    }
}
```

**Output:**

```text
Enter first number: 20
Enter second number: 6
Addition (a `+` b) = 26
Subtraction (a `-` b) = 14
Multiplication (a `*` b) = 120
Division (a `/` b) = 3
Modulo (a `%` b) = 2
```

**Conclusion:**
In this practical, we successfully implemented basic arithmetic operators (`+`, `-`, `*`, `/`, `%`) in Java to perform algebraic operations on user-provided inputs. We understood how integer division computes quotients while the modulo operator evaluates the remainder.

---

# Practical 3

**Aim:** Write a java program to print the value of x^n. Input: x=5 Input: n=3 Output: 125**

**Java Code:**

```java
import java.util.Scanner;

public class PowerCalculation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Input x: ");
        int x = scanner.nextInt();

        System.out.print("Input n: ");
        int n = scanner.nextInt();

        long result = 1;
        for (int i = 1; i <= n; i++) {
            result *= x;
        }

        System.out.println("Output: " + result);

        scanner.close();
    }
}
```

**Output:**

```text
Input x: 5
Input n: 3
Output: 125
```

**Conclusion:**
In this practical, we demonstrated power calculation (x^n) in Java using iterative control structures (`for` loop). We learned how to accumulate multiplicative results across iterations to compute exponential values efficiently.

---

# Practical 4

**Aim:** Write a program in Java to find a minimum of three numbers using a conditional operator.**

**Java Code:**

```java
import java.util.Scanner;

public class MinThreeNumbers {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = scanner.nextInt();

        System.out.print("Enter second number: ");
        int b = scanner.nextInt();

        System.out.print("Enter third number: ");
        int c = scanner.nextInt();

        int min = (a < b) ? ((a < c) ? a : c) : ((b < c) ? b : c);

        System.out.println("Minimum number is: " + min);

        scanner.close();
    }
}
```

**Output:**

```text
Enter first number: 15
Enter second number: 7
Enter third number: 12
Minimum number is: 7
```

**Conclusion:**
In this practical, we explored the usage of nested ternary (conditional) operators (`?:`) to find the minimum of three numbers. We understood how concise conditional expressions simplify decision-making logic without relying on verbose `if-else` blocks.

---

# Practical 5

**Aim:** Write a program to print even numbers up to 10 using a while loop.**

**Java Code:**

```java
public class EvenNumbers {
    public static void main(String[] args) {
        int i = 2;
        while (i <= 10) {
            System.out.println(i);
            i += 2;
        }
    }
}
```

**Output:**

```text
2
4
6
8
10
```

**Conclusion:**
In this practical, we learned how to utilize the `while` loop construct in Java to iterate and print even numbers sequentially up to 10. We understood loop initialization, condition evaluation, and increment operations.

---

# Practical 6

**Aim:** Write a Program to print Prime numbers between 1 to 100.**

**Java Code:**

```java
public class PrimeNumbers {
    public static void main(String[] args) {
        System.out.println("Prime numbers between 1 and 100:");
        for (int num = 2; num <= 100; num++) {
            boolean isPrime = true;
            for (int i = 2; i <= Math.sqrt(num); i++) {
                if (num % i == 0) {
                    isPrime = false;
                    break;
                }
            }
            if (isPrime) {
                System.out.print(num + " ");
            }
        }
    }
}
```

**Output:**

```text
Prime numbers between 1 and 100:
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 
```

**Conclusion:**
In this practical, we implemented nested loop logic and mathematical checks to identify prime numbers between 1 and 100. We learned how to optimize prime testing using `Math.sqrt()` and boolean flags.

---

# Practical 7

**Aim:** Write a JAVA program to sort the elements of an array in ascending order.**

**Java Code:**

```java
import java.util.Arrays;
import java.util.Scanner;

public class ArraySort {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter number of elements in array: ");
        int n = scanner.nextInt();
        int[] arr = new int[n];

        System.out.println("Enter " + n + " elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }

        System.out.println("Original Array: " + Arrays.toString(arr));

        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = 0; j < arr.length - 1 - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }

        System.out.println("Sorted Array: " + Arrays.toString(arr));

        scanner.close();
    }
}
```

**Output:**

```text
Enter number of elements in array: 5
Enter 5 elements:
45 12 85 32 10
Original Array: [45, 12, 85, 32, 10]
Sorted Array: [10, 12, 32, 45, 85]
```

**Conclusion:**
In this practical, we implemented the Bubble Sort algorithm in Java to arrange array elements in ascending order. We gained practical knowledge of array traversal, index comparisons, and value swapping techniques.

---

# Practical 8

**Aim:** Write a program in Java to multiply two matrixes. Declare a class Matrix where 2D array is declared as instance variable and array should be initialized, within class.**

**Java Code:**

```java
import java.util.Scanner;

class Matrix {
    int[][] data;
    int rows;
    int cols;

    public Matrix(int rows, int cols) {
        this.rows = rows;
        this.cols = cols;
        this.data = new int[rows][cols];
    }

    public void readMatrix(Scanner scanner) {
        System.out.println("Enter matrix elements (" + rows + "x" + cols + "):");
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                data[i][j] = scanner.nextInt();
            }
        }
    }

    public Matrix multiply(Matrix other) {
        Matrix result = new Matrix(this.rows, other.cols);
        for (int i = 0; i < this.rows; i++) {
            for (int j = 0; j < other.cols; j++) {
                for (int k = 0; k < this.cols; k++) {
                    result.data[i][j] += this.data[i][k] * other.data[k][j];
                }
            }
        }
        return result;
    }

    public void display() {
        for (int[] row : data) {
            for (int val : row) {
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}

public class MatrixMultiplication {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        Matrix m1 = new Matrix(2, 2);
        Matrix m2 = new Matrix(2, 2);

        System.out.println("--- Matrix 1 ---");
        m1.readMatrix(scanner);

        System.out.println("--- Matrix 2 ---");
        m2.readMatrix(scanner);

        Matrix result = m1.multiply(m2);

        System.out.println("Resultant Matrix:");
        result.display();

        scanner.close();
    }
}
```

**Output:**

```text
--- Matrix 1 ---
Enter matrix elements (2x2):
1 2
3 4
--- Matrix 2 ---
Enter matrix elements (2x2):
5 6
7 8
Resultant Matrix:
19 22 
43 50 
```

**Conclusion:**
In this practical, we developed an object-oriented Java program to perform 2D matrix multiplication. We learned object modeling, encapsulation of 2D arrays within classes, constructor initialization, and multi-dimensional loop indexing.

---

# Practical 9

**Aim:** Write a java program to check Armstrong number. Input: 153 Output: Armstrong number Input: 22 Output: not Armstrong number .**

**Java Code:**

```java
import java.util.Scanner;

public class ArmstrongCheck {
    public static void checkArmstrong(int num) {
        int original = num;
        int sum = 0;
        int digits = String.valueOf(num).length();

        int temp = num;
        while (temp > 0) {
            int digit = temp % 10;
            sum += Math.pow(digit, digits);
            temp /= 10;
        }

        if (sum == original) {
            System.out.println("Output: Armstrong number");
        } else {
            System.out.println("Output: not Armstrong number");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int number = scanner.nextInt();

        checkArmstrong(number);

        scanner.close();
    }
}
```

**Output:**

```text
Enter a number: 153
Output: Armstrong number
```

**Conclusion:**
In this practical, we created a program to verify whether a given integer is an Armstrong number. We understood digit extraction using modulus (`%`) and division (`/`) operators alongside power calculations with `Math.pow()`.

---

# Practical 10

**Aim:** Write programs in Java to use the Wrapper class of each primitive data type.**

**Java Code:**

```java
import java.util.Scanner;

public class WrapperClassesDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter an integer value: ");
        int primitiveInt = scanner.nextInt();

        System.out.print("Enter a double value: ");
        double primitiveDouble = scanner.nextDouble();

        // Autoboxing (Primitive to Wrapper Object)
        Integer intObj = primitiveInt;
        Double doubleObj = primitiveDouble;
        Boolean boolObj = true;
        Character charObj = 'J';

        System.out.println("\n--- Autoboxed Wrapper Objects ---");
        System.out.println("Integer Object: " + intObj);
        System.out.println("Double Object: " + doubleObj);
        System.out.println("Boolean Object: " + boolObj);
        System.out.println("Character Object: " + charObj);

        // Unboxing (Wrapper Object to Primitive)
        int unboxedInt = intObj;
        double unboxedDouble = doubleObj;

        System.out.println("\n--- Unboxed Primitives ---");
        System.out.println("Unboxed int: " + unboxedInt);
        System.out.println("Unboxed double: " + unboxedDouble);

        scanner.close();
    }
}
```

**Output:**

```text
Enter an integer value: 42
Enter a double value: 99.99

--- Autoboxed Wrapper Objects ---
Integer Object: 42
Double Object: 99.99
Boolean Object: true
Character Object: J

--- Unboxed Primitives ---
Unboxed int: 42
Unboxed double: 99.99
```

**Conclusion:**
In this practical, we demonstrated Java Wrapper classes (`Integer`, `Double`, `Boolean`, `Character`). We learned the mechanisms of Autoboxing (converting primitive types into objects) and Unboxing (extracting primitive values from wrapper objects).

---

# Practical 11

**Aim:** Write the program for method overloading.**

**Java Code:**

```java
class Calculator {
    // Overloaded method: 2 integer parameters
    public int add(int a, int b) {
        return a + b;
    }

    // Overloaded method: 3 integer parameters
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // Overloaded method: 2 double parameters
    public double add(double a, double b) {
        return a + b;
    }
}

public class MethodOverloadingDemo {
    public static void main(String[] args) {
        Calculator calc = new Calculator();

        System.out.println("Add 2 integers (10 `+` 20): " + calc.add(10, 20));
        System.out.println("Add 3 integers (10 `+` 20 `+` 30): " + calc.add(10, 20, 30));
        System.out.println("Add 2 doubles (5.5 `+` 4.3): " + calc.add(5.5, 4.3));
    }
}
```

**Output:**

```text
Add 2 integers (10 `+` 20): 30
Add 3 integers (10 `+` 20 `+` 30): 60
Add 2 doubles (5.5 `+` 4.3): 9.8
```

**Conclusion:**
In this practical, we explored method overloading in Java to achieve compile-time polymorphism. We demonstrated how multiple methods within the same class can share the same name provided their parameter types or counts differ.

---

# Practical 12

**Aim:** Consider an employee class, which contains fields such as name and Designation. And a subclass, which contains a field for salary. Write a program to inherit this relation .**

**Java Code:**

```java
import java.util.Scanner;

class Employee {
    String name;
    String designation;

    public Employee(String name, String designation) {
        this.name = name;
        this.designation = designation;
    }

    public void displayDetails() {
        System.out.println("Employee Name: " + name);
        System.out.println("Designation: " + designation);
    }
}

class SalaryEmployee extends Employee {
    double salary;

    public SalaryEmployee(String name, String designation, double salary) {
        super(name, designation);
        this.salary = salary;
    }

    public void displaySalaryEmployee() {
        displayDetails();
        System.out.println("Salary: $" + salary);
    }
}

public class InheritanceDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter Employee Name: ");
        String name = scanner.nextLine();

        System.out.print("Enter Designation: ");
        String designation = scanner.nextLine();

        System.out.print("Enter Salary: ");
        double salary = scanner.nextDouble();

        SalaryEmployee emp = new SalaryEmployee(name, designation, salary);

        System.out.println("\n--- Employee Details ---");
        emp.displaySalaryEmployee();

        scanner.close();
    }
}
```

**Output:**

```text
Enter Employee Name: Alice Smith
Enter Designation: Software Engineer
Enter Salary: 75000

--- Employee Details ---
Employee Name: Alice Smith
Designation: Software Engineer
Salary: $75000.0
```

**Conclusion:**
In this practical, we implemented single inheritance in Java using the `extends` keyword. We learned how a subclass inherits instance variables and methods from a superclass and utilizes `super()` to initialize parent class fields.

---

# Practical 13

**Aim:** Create a class "Rectangle" that would contain length and width as an instance variable. Define constructors [constructor overloading (default, parameterized and copy)] to initialize variables of objects. Define methods to find area and to display variables' value of objects which are created.**

**Java Code:**

```java
class Rectangle {
    double length;
    double width;

    // 1. Default Constructor
    public Rectangle() {
        this.length = 1.0;
        this.width = 1.0;
    }

    // 2. Parameterized Constructor
    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }

    // 3. Copy Constructor
    public Rectangle(Rectangle rect) {
        this.length = rect.length;
        this.width = rect.width;
    }

    public double calculateArea() {
        return length * width;
    }

    public void display() {
        System.out.println("Length: " + length + ", Width: " + width + ", Area: " + calculateArea());
    }
}

public class RectangleDemo {
    public static void main(String[] args) {
        Rectangle r1 = new Rectangle();                  // Default
        Rectangle r2 = new Rectangle(5.0, 3.0);          // Parameterized
        Rectangle r3 = new Rectangle(r2);                 // Copy

        System.out.println("--- Default Rectangle ---");
        r1.display();

        System.out.println("--- Parameterized Rectangle ---");
        r2.display();

        System.out.println("--- Copy Rectangle ---");
        r3.display();
    }
}
```

**Output:**

```text
--- Default Rectangle ---
Length: 1.0, Width: 1.0, Area: 1.0
--- Parameterized Rectangle ---
Length: 5.0, Width: 3.0, Area: 15.0
--- Copy Rectangle ---
Length: 5.0, Width: 3.0, Area: 15.0
```

**Conclusion:**
In this practical, we demonstrated constructor overloading including default, parameterized, and copy constructors in a `Rectangle` class. We learned how different constructor forms enable flexible object initialization and area calculations.

---

# Practical 14

**Aim:** Create a class "Vehicle" with instance variable vehicle_type. Inherit the class in a class called "Car" with instance model_type, company name etc. display the information of the vehicle by defining the display() in both super and sub class [Method Overriding]**

**Java Code:**

```java
class Vehicle {
    String vehicle_type;

    public Vehicle(String vehicle_type) {
        this.vehicle_type = vehicle_type;
    }

    public void display() {
        System.out.println("Vehicle Type: " + vehicle_type);
    }
}

class Car extends Vehicle {
    String model_type;
    String company_name;

    public Car(String vehicle_type, String model_type, String company_name) {
        super(vehicle_type);
        this.model_type = model_type;
        this.company_name = company_name;
    }

    @Override
    public void display() {
        super.display();
        System.out.println("Company Name: " + company_name);
        System.out.println("Model Type: " + model_type);
    }
}

public class MethodOverridingDemo {
    public static void main(String[] args) {
        Car car = new Car("Four-Wheeler", "Sedan", "Toyota");
        car.display();
    }
}
```

**Output:**

```text
Vehicle Type: Four-Wheeler
Company Name: Toyota
Model Type: Sedan
```

**Conclusion:**
In this practical, we demonstrated method overriding in Java to achieve runtime polymorphism between a `Vehicle` superclass and `Car` subclass. We learned how `@Override` allows a subclass to customize parent class methods while invoking base behavior via `super.display()`.

---

# Practical 15

**Aim:** Create a class "Account" containing accountNo, and balance as an instance variable. Derive the Account class into two classes named "Savings" and "Current". The "Savings" class should contain an instance variable named interest Rate, and the "Current" class should contain an instance variable called overdraft Limit. Define appropriate methods for all the classes to enable functionalities to check balance, deposit, and withdraw amounts in Savings and Current accounts. [Ensure that the Account class cannot be instantiated.]**

**Java Code:**

```java
abstract class Account {
    int accountNo;
    double balance;

    public Account(int accountNo, double balance) {
        this.accountNo = accountNo;
        this.balance = balance;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited $" + amount + ". New Balance: $" + balance);
    }

    public void checkBalance() {
        System.out.println("Account #" + accountNo + " Balance: $" + balance);
    }

    public abstract void withdraw(double amount);
}

class Savings extends Account {
    double interestRate;

    public Savings(int accountNo, double balance, double interestRate) {
        super(accountNo, balance);
        this.interestRate = interestRate;
    }

    @Override
    public void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
            System.out.println("Savings Account Withdrawn: $" + amount + ". Remaining Balance: $" + balance);
        } else {
            System.out.println("Insufficient funds in Savings Account!");
        }
    }
}

class Current extends Account {
    double overdraftLimit;

    public Current(int accountNo, double balance, double overdraftLimit) {
        super(accountNo, balance);
        this.overdraftLimit = overdraftLimit;
    }

    @Override
    public void withdraw(double amount) {
        if ((balance + overdraftLimit) >= amount) {
            balance -= amount;
            System.out.println("Current Account Withdrawn: $" + amount + ". Remaining Balance: $" + balance);
        } else {
            System.out.println("Exceeded Overdraft Limit in Current Account!");
        }
    }
}

public class AbstractAccountDemo {
    public static void main(String[] args) {
        Savings sa = new Savings(1001, 2000.0, 4.5);
        Current ca = new Current(2001, 1000.0, 500.0);

        System.out.println("--- Savings Account ---");
        sa.checkBalance();
        sa.deposit(500.0);
        sa.withdraw(1200.0);

        System.out.println("\n--- Current Account ---");
        ca.checkBalance();
        ca.withdraw(1300.0);
    }
}
```

**Output:**

```text
--- Savings Account ---
Account #1001 Balance: $2000.0
Deposited $500.0. New Balance: $2500.0
Savings Account Withdrawn: $1200.0. Remaining Balance: $1300.0

--- Current Account ---
Account #2001 Balance: $1000.0
Current Account Withdrawn: $1300.0. Remaining Balance: $-300.0
```

**Conclusion:**
In this practical, we implemented abstract classes and methods to model a banking `Account` structure with specialized `Savings` and `Current` subclasses. We learned how abstract classes prevent direct instantiation while enforcing concrete withdrawal behaviors.

---

# Practical 16

**Aim:** Write a program in Java in which a subclass constructor invokes the constructor of the super class and instantiate the values. [ refer class Account and sub classes savingAccount and CurrentAccount in Q 14 for this task]**

**Java Code:**

```java
class AccountBase {
    int accountNo;
    double balance;

    public AccountBase(int accountNo, double balance) {
        this.accountNo = accountNo;
        this.balance = balance;
        System.out.println("Superclass AccountBase Constructor Executed.");
    }

    public void displayAccountInfo() {
        System.out.println("Account Number: " + accountNo);
        System.out.println("Account Balance: $" + balance);
    }
}

class SavingsAccountSub extends AccountBase {
    double interestRate;

    public SavingsAccountSub(int accountNo, double balance, double interestRate) {
        super(accountNo, balance); // Invokes superclass constructor
        this.interestRate = interestRate;
        System.out.println("Subclass SavingsAccountSub Constructor Executed.");
    }

    public void displaySavingsInfo() {
        displayAccountInfo();
        System.out.println("Interest Rate: " + interestRate + "%");
    }
}

public class SuperConstructorDemo {
    public static void main(String[] args) {
        SavingsAccountSub acc = new SavingsAccountSub(5001, 4500.0, 5.0);
        System.out.println("\n--- Account Summary ---");
        acc.displaySavingsInfo();
    }
}
```

**Output:**

```text
Superclass AccountBase Constructor Executed.
Subclass SavingsAccountSub Constructor Executed.

--- Account Summary ---
Account Number: 5001
Account Balance: $4500.0
Interest Rate: 5.0%
```

**Conclusion:**
In this practical, we demonstrated how a subclass constructor invokes its superclass constructor using the `super()` keyword. We observed the constructor execution sequence where parent variables are initialized before subclass extensions are applied.

---

# Practical 17

**Aim:** Write a program in Java to demonstrate use of this keyword. Check whether this can access the Static variables of the class or not.**

**Java Code:**

```java
public class ThisKeywordDemo {
    int instanceVar;
    static int staticVar = 100;

    public ThisKeywordDemo(int instanceVar) {
        // 'this' resolves variable shadowing between parameter and instance field
        this.instanceVar = instanceVar;
    }

    public void testAccess() {
        System.out.println("Accessing Instance Variable using 'this': " + this.instanceVar);
        
        // Checking access to static variable using 'this'
        System.out.println("Accessing Static Variable using 'this': " + this.staticVar);
        System.out.println("Accessing Static Variable using Class Name: " + ThisKeywordDemo.staticVar);
    }

    public static void main(String[] args) {
        ThisKeywordDemo obj = new ThisKeywordDemo(50);
        obj.testAccess();
    }
}
```

**Output:**

```text
Accessing Instance Variable using 'this': 50
Accessing Static Variable using 'this': 100
Accessing Static Variable using Class Name: 100
```

**Conclusion:**
In this practical, we investigated the scope and usage of the `this` keyword in Java. We confirmed that `this` resolves field shadowing and can access both instance variables and static variables of the class.

---

# Practical 18

**Aim:** Write a program in Java to demonstrate the use of 'final' keyword in the field declaration. How it is accessed using the objects.**

**Java Code:**

```java
class FinalDemo {
    // Final field declaration (Constant)
    final int MAX_SPEED = 120;
    final String CODE;

    // Blank final field initialized in constructor
    public FinalDemo(String code) {
        this.CODE = code;
    }

    public void display() {
        System.out.println("Max Speed (Final field): " + MAX_SPEED);
        System.out.println("Product Code (Blank Final field): " + CODE);
    }
}

public class FinalKeywordDemo {
    public static void main(String[] args) {
        FinalDemo obj = new FinalDemo("PROD-99");
        obj.display();

        // Accessing final field directly via object
        System.out.println("Directly accessing final field: " + obj.MAX_SPEED);
    }
}
```

**Output:**

```text
Max Speed (Final field): 120
Product Code (Blank Final field): PROD-99
Directly accessing final field: 120
```

**Conclusion:**
In this practical, we demonstrated the `final` keyword for declaring constant fields and blank final fields initialized via constructors. We learned that final fields can be read via object references but cannot be modified once set.

---

# Practical 19

**Aim:** Describe abstract class called Shape which has three subclasses say Triangle, Rectangle, and Circle. Define one method area () in the abstract class and override this area () in these three subclasses to calculate for specific objects i.e. area () of Triangle subclass should calculate area of triangle etc. Same for Rectangle and Circle**

**Java Code:**

```java
abstract class Shape {
    public abstract double area();
}

class Triangle extends Shape {
    double base;
    double height;

    public Triangle(double base, double height) {
        this.base = base;
        this.height = height;
    }

    @Override
    public double area() {
        return 0.5 * base * height;
    }
}

class RectangleShape extends Shape {
    double length;
    double width;

    public RectangleShape(double length, double width) {
        this.length = length;
        this.width = width;
    }

    @Override
    public double area() {
        return length * width;
    }
}

class Circle extends Shape {
    double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}

public class AbstractShapeDemo {
    public static void main(String[] args) {
        Shape t = new Triangle(10.0, 5.0);
        Shape r = new RectangleShape(8.0, 4.0);
        Shape c = new Circle(7.0);

        System.out.println("Area of Triangle: " + t.area());
        System.out.println("Area of Rectangle: " + r.area());
        System.out.println("Area of Circle: " + c.area());
    }
}
```

**Output:**

```text
Area of Triangle: 25.0
Area of Rectangle: 32.0
Area of Circle: 153.93804002589985
```

**Conclusion:**
In this practical, we built an abstract `Shape` class with `Triangle`, `RectangleShape`, and `Circle` subclasses overriding the `area()` method. We observed dynamic method dispatch calculating distinct geometric areas through polymorphic references.

---

# Practical 20

**Aim:** Assume that there are two packages, student and exam. A student package contains Student class and the exam package contains Result class. Write a program that generates mark sheet for students.**

**Java Code:**

```java
// Package structure representation in Java

// File 1: student/Student.java
package student;

public class Student {
    public int rollNo;
    public String name;
    public int mark1, mark2, mark3;

    public Student(int rollNo, String name, int mark1, int mark2, int mark3) {
        this.rollNo = rollNo;
        this.name = name;
        this.mark1 = mark1;
        this.mark2 = mark2;
        this.mark3 = mark3;
    }
}

// File 2: exam/Result.java
package exam;

import student.Student;

public class Result {
    public static void generateMarkSheet(Student s) {
        int total = s.mark1 + s.mark2 + s.mark3;
        double percentage = total / 3.0;

        System.out.println("================ MARK SHEET ================");
        System.out.println("Roll No    : " + s.rollNo);
        System.out.println("Name       : " + s.name);
        System.out.println("Subject 1  : " + s.mark1);
        System.out.println("Subject 2  : " + s.mark2);
        System.out.println("Subject 3  : " + s.mark3);
        System.out.println("Total Marks: " + total);
        System.out.println("Percentage : " + percentage + "%");
        System.out.println("============================================");
    }

    public static void main(String[] args) {
        Student s = new Student(101, "John Doe", 85, 90, 78);
        generateMarkSheet(s);
    }
}
```

**Output:**

```text
================ MARK SHEET ================
Roll No    : 101
Name       : John Doe
Subject 1  : 85
Subject 2  : 90
Subject 3  : 78
Total Marks: 253
Percentage : 84.33333333333333%
============================================
```

**Conclusion:**
In this practical, we implemented cross-package class interaction between `student` and `exam` packages to generate student mark sheets. We learned how public visibility and package imports structure modular Java applications.

---

# Practical 21

**Aim:** Write a java program to accept strings to check whether it is in Upper or Lower case. After checking, the case will be reversed.**

**Java Code:**

```java
import java.util.Scanner;

public class CaseReverseDemo {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String input = scanner.nextLine();

        StringBuilder reversedString = new StringBuilder();

        for (int i = 0; i < input.length(); i++) {
            char ch = input.charAt(i);

            if (Character.isUpperCase(ch)) {
                reversedString.append(Character.toLowerCase(ch));
            } else if (Character.isLowerCase(ch)) {
                reversedString.append(Character.toUpperCase(ch));
            } else {
                reversedString.append(ch);
            }
        }

        System.out.println("Original String: " + input);
        System.out.println("Case Reversed String: " + reversedString.toString());

        scanner.close();
    }
}
```

**Output:**

```text
Enter a string: Hello World!
Original String: Hello World!
Case Reversed String: hELLO wORLD!
```

**Conclusion:**
In this practical, we developed a string manipulation program to inspect character casing and invert uppercase and lowercase letters. We gained experience using `Character` utility methods and `StringBuilder` for string construction.

---

# Practical 22

**Aim:** Write a program in Java to develop user defined exceptions for 'Divide by Zero' error.**

**Java Code:**

```java
import java.util.Scanner;

// User-Defined Exception Class
class DivideByZeroException extends Exception {
    public DivideByZeroException(String message) {
        super(message);
    }
}

public class CustomExceptionDemo {
    public static double divide(int numerator, int denominator) throws DivideByZeroException {
        if (denominator == 0) {
            throw new DivideByZeroException("Custom Error: Cannot divide number by zero!");
        }
        return (double) numerator / denominator;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter numerator: ");
        int num = scanner.nextInt();

        System.out.print("Enter denominator: ");
        int den = scanner.nextInt();

        try {
            double result = divide(num, den);
            System.out.println("Result: " + result);
        } catch (DivideByZeroException e) {
            System.out.println("Caught Custom Exception: " + e.getMessage());
        } finally {
            scanner.close();
        }
    }
}
```

**Output:**

```text
Enter numerator: 10
Enter denominator: 0
Caught Custom Exception: Custom Error: Cannot divide number by zero!
```

**Conclusion:**
In this practical, we created a custom user-defined exception (`DivideByZeroException`) extending the `Exception` class. We learned how to explicitly throw and catch custom exceptions to handle specific error conditions gracefully.

---

# Practical 23

**Aim:** Write a program in Java to demonstrate throw, throws, finally, multiple try block and multiple catch exception**

**Java Code:**

```java
import java.util.Scanner;

public class ExceptionKeywordsDemo {
    public static void checkAge(int age) throws ArithmeticException {
        if (age < 18) {
            throw new ArithmeticException("Age must be 18 or above to register!");
        } else {
            System.out.println("Age verification successful.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // First Try Block
        try {
            System.out.print("Enter your age: ");
            int age = scanner.nextInt();
            checkAge(age);
        } catch (ArithmeticException e) {
            System.out.println("Caught in Catch 1: " + e.getMessage());
        }

        // Second Try Block with Multiple Catch Blocks
        try {
            int[] numbers = {10, 20, 30};
            System.out.print("Enter array index to access (0-2): ");
            int idx = scanner.nextInt();
            
            System.out.println("Value at index " + idx + ": " + numbers[idx]);
            
            int divResult = numbers[idx] / idx; // may throw ArithmeticException if idx == 0
            System.out.println("Result of division: " + divResult);

        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Caught Catch 2A (Array Index): Invalid array index entered!");
        } catch (ArithmeticException e) {
            System.out.println("Caught Catch 2B (Arithmetic): Cannot divide array value by zero!");
        } catch (Exception e) {
            System.out.println("Caught Generic Exception: " + e.getMessage());
        } finally {
            System.out.println("Finally block executed regardless of exception occurrence.");
            scanner.close();
        }
    }
}
```

**Output:**

```text
Enter your age: 16
Caught in Catch 1: Age must be 18 or above to register!
Enter array index to access (0-2): 5
Caught Catch 2A (Array Index): Invalid array index entered!
Finally block executed regardless of exception occurrence.
```

**Conclusion:**
In this practical, we demonstrated key Java exception handling keywords (`try`, `catch`, `finally`, `throw`, and `throws`). We learned how multiple catch blocks handle distinct runtime exceptions while `finally` guarantees cleanup execution.

---

# Practical 24

**Aim:** Write a small application in Java to develop Banking Application in which the user deposits the amount Rs 1000.00 and then start withdrawing of Rs 400.00, Rs 300.00 and it throws exception "Not Sufficient Fund" when user withdraws Rs. 500 there after.**

**Java Code:**

```java
class NotSufficientFundException extends Exception {
    public NotSufficientFundException(String message) {
        super(message);
    }
}

class BankAccount {
    private double balance;

    public BankAccount(double initialDeposit) {
        this.balance = initialDeposit;
        System.out.println("Account opened with Initial Deposit: Rs " + balance);
    }

    public void withdraw(double amount) throws NotSufficientFundException {
        System.out.println("Attempting to withdraw: Rs " + amount);
        if (amount > balance) {
            throw new NotSufficientFundException("Not Sufficient Fund! Current Balance: Rs " + balance);
        }
        balance -= amount;
        System.out.println("Withdrawal successful. Remaining Balance: Rs " + balance);
    }
}

public class BankingApplication {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(1000.00);

        try {
            account.withdraw(400.00);
            account.withdraw(300.00);
            account.withdraw(500.00); // Triggers exception (Remaining balance is 300)
        } catch (NotSufficientFundException e) {
            System.out.println("Exception Caught: " + e.getMessage());
        }
    }
}
```

**Output:**

```text
Account opened with Initial Deposit: Rs 1000.0
Attempting to withdraw: Rs 400.0
Withdrawal successful. Remaining Balance: Rs 600.0
Attempting to withdraw: Rs 300.0
Withdrawal successful. Remaining Balance: Rs 300.0
Attempting to withdraw: Rs 500.0
Exception Caught: Not Sufficient Fund! Current Balance: Rs 300.0
```

**Conclusion:**
In this practical, we built a banking simulation program that enforces custom `NotSufficientFundException` checks during withdrawals. We observed how state tracking prevents overdrawing and raises handled exceptions when funds are insufficient.

---

# Practical 25

**Aim:** Write a java program to implement an interface called Exam with a method Pass (int mark) that returns a boolean. Write another interface called Classify with a method Division (int average) which returns a String. Write a class called Result which implements both Exam and Classify. The Pass method should return true if the mark is greater than or equal to 50 else false. The Division method must return "First" when the parameter average is 60 or more, "Second" when average is 50 or more but below 60, "No division" when average is less than 50.**

**Java Code:**

```java
interface Exam {
    boolean Pass(int mark);
}

interface Classify {
    String Division(int average);
}

class Result implements Exam, Classify {

    @Override
    public boolean Pass(int mark) {
        return mark >= 50;
    }

    @Override
    public String Division(int average) {
        if (average >= 60) {
            return "First";
        } else if (average >= 50) {
            return "Second";
        } else {
            return "No division";
        }
    }
}

public class InterfaceDemo {
    public static void main(String[] args) {
        Result res = new Result();

        int studentMark = 65;
        int studentAvg = 62;

        System.out.println("Mark: " + studentMark + " | Passed: " + res.Pass(studentMark));
        System.out.println("Average: " + studentAvg + " | Division: " + res.Division(studentAvg));

        int studentMark2 = 45;
        int studentAvg2 = 48;

        System.out.println("\nMark: " + studentMark2 + " | Passed: " + res.Pass(studentMark2));
        System.out.println("Average: " + studentAvg2 + " | Division: " + res.Division(studentAvg2));
    }
}
```

**Output:**

```text
Mark: 65 | Passed: true
Average: 62 | Division: First

Mark: 45 | Passed: false
Average: 48 | Division: No division
```

**Conclusion:**
In this practical, we implemented multiple inheritance in Java using the `Exam` and `Classify` interfaces within a `Result` class. We understood how interfaces define behavioral contracts for evaluating pass status and division classifications.

---

# Practical 26

**Aim:** Write a Java Program for Multithreading.**

**Java Code:**

```java
class NumberPrinter extends Thread {
    @Override
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println(Thread.currentThread().getName() + " - Count: " + i);
            try {
                Thread.sleep(500); // Sleep for 500 milliseconds
            } catch (InterruptedException e) {
                System.out.println("Thread interrupted!");
            }
        }
    }
}

public class MultithreadingDemo {
    public static void main(String[] args) {
        NumberPrinter thread1 = new NumberPrinter();
        NumberPrinter thread2 = new NumberPrinter();

        thread1.setName("Thread-Alpha");
        thread2.setName("Thread-Beta");

        System.out.println("Starting Concurrent Threads...");
        thread1.start(); // Starts execution of thread1
        thread2.start(); // Starts execution of thread2
    }
}
```

**Output:**

```text
Starting Concurrent Threads...
Thread-Alpha - Count: 1
Thread-Beta - Count: 1
Thread-Alpha - Count: 2
Thread-Beta - Count: 2
Thread-Alpha - Count: 3
Thread-Beta - Count: 3
Thread-Alpha - Count: 4
Thread-Beta - Count: 4
Thread-Alpha - Count: 5
Thread-Beta - Count: 5
```

**Conclusion:**
In this practical, we implemented multithreading in Java by extending the `Thread` class and overriding the `run()` method. We observed concurrent thread execution and managed thread timing using `Thread.sleep()`.

---

# Practical 27

**Aim:** Write a java program to implement Generic class Number_1 for both data type int and float in java.**

**Java Code:**

```java
class Number_1<T extends Number> {
    private T num;

    public Number_1(T num) {
        this.num = num;
    }

    public double getSquare() {
        return num.doubleValue() * num.doubleValue();
    }

    public void display() {
        System.out.println("Value: " + num + " | Square: " + getSquare());
    }
}

public class GenericNumberDemo {
    public static void main(String[] args) {
        // Integer instantiation
        Number_1<Integer> intObj = new Number_1<>(5);
        System.out.print("Integer Generic: ");
        intObj.display();

        // Float instantiation
        Number_1<Float> floatObj = new Number_1<>(4.5f);
        System.out.print("Float Generic: ");
        floatObj.display();
    }
}
```

**Output:**

```text
Integer Generic: Value: 5 | Square: 25.0
Float Generic: Value: 4.5 | Square: 20.25
```

**Conclusion:**
In this practical, we created a generic class (`Number_1<T extends Number>`) accepting both integer and floating-point data types. We learned how bounded type parameters deliver type-safe mathematical calculations across different numeric types.

---

# Practical 28

**Aim:** Write a Java program to implement a generic class that stores multiple elements of any data type using a Collection Framework (ArrayList). The program should allow adding elements, sorting them using Comparable, and then displaying them. Demonstrate the program with both String and Integer data types.**

**Java Code:**

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

class GenericContainer<T extends Comparable<T>> {
    private List<T> list = new ArrayList<>();

    public void addElement(T element) {
        list.add(element);
    }

    public void sortElements() {
        Collections.sort(list); // Uses Comparable natural ordering
    }

    public void display() {
        System.out.println(list);
    }
}

public class GenericArrayListDemo {
    public static void main(String[] args) {
        // Integer List
        GenericContainer<Integer> intContainer = new GenericContainer<>();
        intContainer.addElement(42);
        intContainer.addElement(15);
        intContainer.addElement(89);
        intContainer.addElement(7);

        System.out.println("Integer Container before sorting:");
        intContainer.display();
        intContainer.sortElements();
        System.out.println("Integer Container after sorting:");
        intContainer.display();

        // String List
        GenericContainer<String> stringContainer = new GenericContainer<>();
        stringContainer.addElement("Banana");
        stringContainer.addElement("Apple");
        stringContainer.addElement("Mango");
        stringContainer.addElement("Cherry");

        System.out.println("\nString Container before sorting:");
        stringContainer.display();
        stringContainer.sortElements();
        System.out.println("String Container after sorting:");
        stringContainer.display();
    }
}
```

**Output:**

```text
Integer Container before sorting:
[42, 15, 89, 7]
Integer Container after sorting:
[7, 15, 42, 89]

String Container before sorting:
[Banana, Apple, Mango, Cherry]
String Container after sorting:
[Apple, Banana, Cherry, Mango]
```

**Conclusion:**
In this practical, we utilized the Java Collection Framework's `ArrayList` within a generic class bounded by `Comparable<T>`. We demonstrated adding, storing, and sorting both `Integer` and `String` elements using `Collections.sort()`.

---

# Practical 29

**Aim:** Write a program for Java Generics class for Sorting operations: 1. Sorting a list according to natural ordering of elements 2. Reversing sort order 3. Sorting a list whose elements of a custom type 4. Sorting a list using a Comparator.**

**Java Code:**

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

// Custom Class implementing Comparable
class StudentItem implements Comparable<StudentItem> {
    String name;
    int marks;

    public StudentItem(String name, int marks) {
        this.name = name;
        this.marks = marks;
    }

    @Override
    public int compareTo(StudentItem other) {
        return Integer.compare(this.marks, other.marks); // Ascending by marks
    }

    @Override
    public String toString() {
        return name + " (" + marks + ")";
    }
}

public class SortingGenericsDemo {
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>();
        fruits.add("Orange");
        fruits.add("Apple");
        fruits.add("Banana");

        // 1. Natural Ordering
        Collections.sort(fruits);
        System.out.println("1. Natural Order: " + fruits);

        // 2. Reverse Order
        Collections.sort(fruits, Collections.reverseOrder());
        System.out.println("2. Reverse Order: " + fruits);

        // 3. Custom Type Sorting (Comparable)
        List<StudentItem> students = new ArrayList<>();
        students.add(new StudentItem("Bob", 85));
        students.add(new StudentItem("Alice", 92));
        students.add(new StudentItem("Charlie", 78));

        Collections.sort(students);
        System.out.println("3. Custom Type Sorted by Marks (Comparable): " + students);

        // 4. Comparator Sorting (Sort by Name)
        Collections.sort(students, new Comparator<StudentItem>() {
            @Override
            public int compare(StudentItem s1, StudentItem s2) {
                return s1.name.compareTo(s2.name);
            }
        });
        System.out.println("4. Custom Type Sorted by Name (Comparator): " + students);
    }
}
```

**Output:**

```text
1. Natural Order: [Apple, Banana, Orange]
2. Reverse Order: [Orange, Banana, Apple]
3. Custom Type Sorted by Marks (Comparable): [Charlie (78), Bob (85), Alice (92)]
4. Custom Type Sorted by Name (Comparator): [Alice (92), Bob (85), Charlie (78)]
```

**Conclusion:**
In this practical, we implemented various sorting operations using Java Generics, `Comparable`, and `Comparator` interfaces. We learned how to sort collections in natural order, reverse order, and according to custom class criteria.

---

# Practical 30

**Aim:** Write a Java program to demonstrate the use of Date and Calendar classes to extract the current date, year, month, and day. Format the date using the Formatter class with varargs .**

**Java Code:**

```java
import java.util.Calendar;
import java.util.Date;
import java.util.Formatter;

public class DateCalendarDemo {
    public static void formatDateString(String formatPattern, Object... args) {
        Formatter formatter = new Formatter();
        formatter.format(formatPattern, args);
        System.out.println("Formatted Date Output: " + formatter);
        formatter.close();
    }

    public static void main(String[] args) {
        // Date class
        Date currentDate = new Date();
        System.out.println("Current Date (Date Class): " + currentDate);

        // Calendar class
        Calendar calendar = Calendar.getInstance();
        int year = calendar.get(Calendar.YEAR);
        int month = calendar.get(Calendar.MONTH) + 1; // Month is 0-indexed
        int day = calendar.get(Calendar.DAY_OF_MONTH);
        int dayOfWeek = calendar.get(Calendar.DAY_OF_WEEK);

        System.out.println("Extracted Year: " + year);
        System.out.println("Extracted Month: " + month);
        System.out.println("Extracted Day: " + day);
        System.out.println("Extracted Day of Week: " + dayOfWeek);

        // Formatter with varargs
        formatDateString("Today's Date: %02d/%02d/%04d", day, month, year);
    }
}
```

**Output:**

```text
Current Date (Date Class): Sat Sep 19 17:45:00 IST 2026
Extracted Year: 2026
Extracted Month: 9
Extracted Day: 19
Extracted Day of Week: 7
Formatted Date Output: Today's Date: 19/09/2026
```

**Conclusion:**
In this practical, we worked with Java's `Date` and `Calendar` classes to extract date components such as year, month, and day. We also formatted date outputs using the `Formatter` class with variable arguments (`varargs`).
