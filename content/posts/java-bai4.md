---
title: "Java Bài 4 - Hàm/Phương thức (Methods) | My New Hugo Site"
date: 2025-10-06
draft: false
categories: ["Java"]
tags: ["java", "methods", "functions"]
description: "Học cách tạo và sử dụng hàm/phương thức trong Java"
---

# Java Bài 4 - Hàm/Phương thức (Methods)

Phương thức (Method) hay còn gọi là hàm (Function) là một khối code thực hiện một nhiệm vụ cụ thể, giúp code dễ đọc, tái sử dụng và bảo trì.

## 1. Cú pháp khai báo phương thức

```java
[access_modifier] [static] return_type method_name(parameters) {
    // Thân phương thức
    return value; // nếu có return_type
}
```

**Ví dụ:**
```java
public class MethodExample {
    // Phương thức không trả về giá trị
    public static void sayHello() {
        System.out.println("Xin chào!");
    }
    
    // Phương thức có trả về giá trị
    public static int add(int a, int b) {
        return a + b;
    }
    
    public static void main(String[] args) {
        sayHello();
        int result = add(5, 3);
        System.out.println("Kết quả: " + result);
    }
}
```

## 2. Các loại phương thức

### Phương thức không tham số, không trả về
```java
public class NoParamNoReturn {
    static void greet() {
        System.out.println("Chào mừng bạn đến với Java!");
    }
    
    public static void main(String[] args) {
        greet();
    }
}
```

### Phương thức có tham số, không trả về
```java
public class WithParamNoReturn {
    static void greetUser(String name) {
        System.out.println("Xin chào, " + name + "!");
    }
    
    static void printSum(int a, int b) {
        System.out.println("Tổng: " + (a + b));
    }
    
    public static void main(String[] args) {
        greetUser("An");
        printSum(10, 20);
    }
}
```

### Phương thức không tham số, có trả về
```java
public class NoParamWithReturn {
    static int getRandomNumber() {
        return (int)(Math.random() * 100);
    }
    
    static String getCurrentDay() {
        return "Thứ Hai";
    }
    
    public static void main(String[] args) {
        int random = getRandomNumber();
        String day = getCurrentDay();
        
        System.out.println("Số ngẫu nhiên: " + random);
        System.out.println("Hôm nay là: " + day);
    }
}
```

### Phương thức có tham số, có trả về
```java
public class WithParamWithReturn {
    static int multiply(int a, int b) {
        return a * b;
    }
    
    static double calculateCircleArea(double radius) {
        return Math.PI * radius * radius;
    }
    
    static boolean isEven(int number) {
        return number % 2 == 0;
    }
    
    public static void main(String[] args) {
        int product = multiply(5, 4);
        double area = calculateCircleArea(5.0);
        boolean check = isEven(10);
        
        System.out.println("Tích: " + product);
        System.out.printf("Diện tích: %.2f\n", area);
        System.out.println("10 là số chẵn: " + check);
    }
}
```

## 3. Phạm vi truy cập (Access Modifiers)

```java
public class AccessModifiers {
    // public: Truy cập được từ mọi nơi
    public static void publicMethod() {
        System.out.println("Public method");
    }
    
    // private: Chỉ truy cập trong class hiện tại
    private static void privateMethod() {
        System.out.println("Private method");
    }
    
    // protected: Truy cập trong package và subclass
    protected static void protectedMethod() {
        System.out.println("Protected method");
    }
    
    // default: Truy cập trong cùng package
    static void defaultMethod() {
        System.out.println("Default method");
    }
}
```

## 4. Tham số và đối số

### Tham số cơ bản
```java
public class Parameters {
    static void printInfo(String name, int age, double height) {
        System.out.println("Tên: " + name);
        System.out.println("Tuổi: " + age);
        System.out.println("Chiều cao: " + height + "m");
    }
    
    public static void main(String[] args) {
        printInfo("Nguyễn Văn A", 20, 1.75);
    }
}
```

### Varargs - Số lượng tham số không xác định
```java
public class VarargsExample {
    static int sum(int... numbers) {
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        return total;
    }
    
    public static void main(String[] args) {
        System.out.println("Tổng 1: " + sum(1, 2, 3));
        System.out.println("Tổng 2: " + sum(5, 10, 15, 20, 25));
        System.out.println("Tổng 3: " + sum(100));
    }
}
```

## 5. Phương thức đệ quy (Recursion)

Phương thức đệ quy là phương thức tự gọi chính nó.

### Tính giai thừa
```java
public class Factorial {
    static long factorial(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        return n * factorial(n - 1);
    }
    
    public static void main(String[] args) {
        System.out.println("5! = " + factorial(5));  // 120
        System.out.println("10! = " + factorial(10)); // 3628800
    }
}
```

### Dãy Fibonacci
```java
public class FibonacciRecursion {
    static int fibonacci(int n) {
        if (n <= 1) {
            return n;
        }
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
    
    public static void main(String[] args) {
        System.out.println("10 số Fibonacci đầu tiên:");
        for (int i = 0; i < 10; i++) {
            System.out.print(fibonacci(i) + " ");
        }
    }
}
```

### Tính lũy thừa
```java
public class Power {
    static long power(int base, int exponent) {
        if (exponent == 0) {
            return 1;
        }
        return base * power(base, exponent - 1);
    }
    
    public static void main(String[] args) {
        System.out.println("2^10 = " + power(2, 10)); // 1024
        System.out.println("5^3 = " + power(5, 3));   // 125
    }
}
```

## 6. Nạp chồng phương thức (Method Overloading)

Nhiều phương thức có cùng tên nhưng khác tham số.

```java
public class MethodOverloading {
    // Cộng 2 số nguyên
    static int add(int a, int b) {
        return a + b;
    }
    
    // Cộng 3 số nguyên
    static int add(int a, int b, int c) {
        return a + b + c;
    }
    
    // Cộng 2 số thực
    static double add(double a, double b) {
        return a + b;
    }
    
    // Nối chuỗi
    static String add(String a, String b) {
        return a + b;
    }
    
    public static void main(String[] args) {
        System.out.println(add(5, 10));           // 15
        System.out.println(add(5, 10, 15));       // 30
        System.out.println(add(2.5, 3.7));        // 6.2
        System.out.println(add("Hello ", "World")); // Hello World
    }
}
```

## 7. Truyền tham chiếu vs Truyền giá trị

### Truyền giá trị (kiểu nguyên thủy)
```java
public class PassByValue {
    static void changeValue(int x) {
        x = 100;
        System.out.println("Trong method: " + x);
    }
    
    public static void main(String[] args) {
        int num = 10;
        System.out.println("Trước: " + num);
        changeValue(num);
        System.out.println("Sau: " + num); // Vẫn là 10
    }
}
```

### Truyền tham chiếu (mảng, object)
```java
public class PassByReference {
    static void changeArray(int[] arr) {
        arr[0] = 999;
    }
    
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3};
        System.out.println("Trước: " + numbers[0]);
        changeArray(numbers);
        System.out.println("Sau: " + numbers[0]); // Thay đổi thành 999
    }
}
```

## 8. Ví dụ thực tế

### Chương trình tính toán đơn giản
```java
import java.util.Scanner;

public class Calculator {
    static double add(double a, double b) {
        return a + b;
    }
    
    static double subtract(double a, double b) {
        return a - b;
    }
    
    static double multiply(double a, double b) {
        return a * b;
    }
    
    static double divide(double a, double b) {
        if (b == 0) {
            System.out.println("Lỗi: Không thể chia cho 0!");
            return 0;
        }
        return a / b;
    }
    
    static void showMenu() {
        System.out.println("\n=== CALCULATOR ===");
        System.out.println("1. Cộng");
        System.out.println("2. Trừ");
        System.out.println("3. Nhân");
        System.out.println("4. Chia");
        System.out.println("0. Thoát");
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int choice;
        
        do {
            showMenu();
            System.out.print("Chọn: ");
            choice = sc.nextInt();
            
            if (choice >= 1 && choice <= 4) {
                System.out.print("Nhập số thứ nhất: ");
                double num1 = sc.nextDouble();
                System.out.print("Nhập số thứ hai: ");
                double num2 = sc.nextDouble();
                
                double result = 0;
                switch (choice) {
                    case 1: result = add(num1, num2); break;
                    case 2: result = subtract(num1, num2); break;
                    case 3: result = multiply(num1, num2); break;
                    case 4: result = divide(num1, num2); break;
                }
                
                System.out.printf("Kết quả: %.2f\n", result);
            }
        } while (choice != 0);
        
        System.out.println("Cảm ơn bạn đã sử dụng!");
        sc.close();
    }
}
```

### Quản lý điểm sinh viên
```java
import java.util.Scanner;

public class StudentGrades {
    static double[] inputGrades(int n, Scanner sc) {
        double[] grades = new double[n];
        for (int i = 0; i < n; i++) {
            System.out.print("Điểm môn " + (i + 1) +