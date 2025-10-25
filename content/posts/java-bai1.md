---
title: "Java Bài 1 - Cơ bản | My New Hugo Site"
date: 2025-10-03
draft: false
categories: ["Java"]
tags: ["java", "basic", "beginner"]
description: "Trong bài này, chúng ta sẽ học cách viết chương trình Java đầu tiên: Hello World!"
---

# Java Bài 1 - Cơ bản

Chào mừng bạn đến với bài học đầu tiên về Java! Trong bài này, chúng ta sẽ tìm hiểu những kiến thức cơ bản nhất để bắt đầu với Java.

## 1. Cấu trúc chương trình Java

Một chương trình Java cơ bản bao gồm các thành phần sau:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

### Giải thích:
- **`public class HelloWorld`**: Khai báo một class công khai tên là HelloWorld
- **`public static void main(String[] args)`**: Phương thức main - điểm khởi đầu của chương trình
- **`System.out.println()`**: In ra màn hình console

## 2. Biến và Kiểu dữ liệu

### Kiểu dữ liệu nguyên thủy (Primitive Types)

```java
public class DataTypes {
    public static void main(String[] args) {
        // Số nguyên
        int age = 25;
        long population = 7800000000L;
        
        // Số thực
        float price = 99.99f;
        double distance = 384400.5;
        
        // Ký tự
        char grade = 'A';
        
        // Boolean
        boolean isStudent = true;
        
        // Byte và Short
        byte smallNumber = 127;
        short mediumNumber = 32000;
        
        // In ra
        System.out.println("Tuổi: " + age);
        System.out.println("Dân số: " + population);
        System.out.println("Giá: " + price);
        System.out.println("Là sinh viên: " + isStudent);
    }
}
```

### Bảng kiểu dữ liệu:

| Kiểu    | Kích thước | Giá trị                                    |
|---------|------------|--------------------------------------------|
| byte    | 1 byte     | -128 đến 127                              |
| short   | 2 bytes    | -32,768 đến 32,767                        |
| int     | 4 bytes    | -2³¹ đến 2³¹-1                            |
| long    | 8 bytes    | -2⁶³ đến 2⁶³-1                            |
| float   | 4 bytes    | 6-7 chữ số thập phân                      |
| double  | 8 bytes    | 15 chữ số thập phân                       |
| boolean | 1 bit      | true hoặc false                           |
| char    | 2 bytes    | Ký tự Unicode (0 đến 65,535)              |

## 3. Khai báo và Khởi tạo biến

```java
// Khai báo
int number;

// Khởi tạo
number = 10;

// Khai báo và khởi tạo cùng lúc
int count = 0;

// Khai báo nhiều biến cùng kiểu
int x = 5, y = 10, z = 15;

// Hằng số (constant)
final double PI = 3.14159;
final int MAX_SIZE = 100;
```

## 4. Toán tử cơ bản

### Toán tử số học:
```java
int a = 10, b = 3;

System.out.println("Cộng: " + (a + b));      // 13
System.out.println("Trừ: " + (a - b));       // 7
System.out.println("Nhân: " + (a * b));      // 30
System.out.println("Chia: " + (a / b));      // 3 (chia nguyên)
System.out.println("Chia lấy dư: " + (a % b)); // 1
```

### Toán tử so sánh:
```java
int x = 5, y = 10;

System.out.println(x == y);  // false (bằng)
System.out.println(x != y);  // true (khác)
System.out.println(x < y);   // true (nhỏ hơn)
System.out.println(x > y);   // false (lớn hơn)
System.out.println(x <= y);  // true (nhỏ hơn hoặc bằng)
System.out.println(x >= y);  // false (lớn hơn hoặc bằng)
```

### Toán tử logic:
```java
boolean t = true, f = false;

System.out.println(t && f);  // false (AND - và)
System.out.println(t || f);  // true (OR - hoặc)
System.out.println(!t);      // false (NOT - phủ định)
```

## 5. Nhập xuất dữ liệu

### Xuất dữ liệu:
```java
System.out.println("In và xuống dòng");
System.out.print("In không xuống dòng ");
System.out.printf("Số nguyên: %d, Số thực: %.2f", 10, 3.14);
```

### Nhập dữ liệu:
```java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập tên của bạn: ");
        String name = sc.nextLine();
        
        System.out.print("Nhập tuổi: ");
        int age = sc.nextInt();
        
        System.out.print("Nhập điểm: ");
        double score = sc.nextDouble();
        
        System.out.println("\n=== THÔNG TIN ===");
        System.out.println("Tên: " + name);
        System.out.println("Tuổi: " + age);
        System.out.println("Điểm: " + score);
        
        sc.close();
    }
}
```

## 6. Bài tập thực hành

### Bài 1: Tính tổng hai số
```java
import java.util.Scanner;

public class SumTwoNumbers {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập số thứ nhất: ");
        int num1 = sc.nextInt();
        
        System.out.print("Nhập số thứ hai: ");
        int num2 = sc.nextInt();
        
        int sum = num1 + num2;
        System.out.println("Tổng: " + sum);
        
        sc.close();
    }
}
```

### Bài 2: Tính diện tích hình chữ nhật
```java
import java.util.Scanner;

public class RectangleArea {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập chiều dài: ");
        double length = sc.nextDouble();
        
        System.out.print("Nhập chiều rộng: ");
        double width = sc.nextDouble();
        
        double area = length * width;
        double perimeter = 2 * (length + width);
        
        System.out.println("Diện tích: " + area);
        System.out.println("Chu vi: " + perimeter);
        
        sc.close();
    }
}
```

### Bài 3: Chuyển đổi nhiệt độ
```java
import java.util.Scanner;

public class TemperatureConverter {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập nhiệt độ Celsius: ");
        double celsius = sc.nextDouble();
        
        double fahrenheit = (celsius * 9/5) + 32;
        double kelvin = celsius + 273.15;
        
        System.out.printf("%.2f°C = %.2f°F\n", celsius, fahrenheit);
        System.out.printf("%.2f°C = %.2fK\n", celsius, kelvin);
        
        sc.close();
    }
}
```

## Tổng kết

Trong bài học này, bạn đã học được:
- ✅ Cấu trúc cơ bản của chương trình Java
- ✅ Các kiểu dữ liệu nguyên thủy
- ✅ Cách khai báo và sử dụng biến
- ✅ Các toán tử cơ bản
- ✅ Nhập xuất dữ liệu với Scanner

**Bài tiếp theo:** [Java Bài 2 - Vòng lặp](/posts/java-bai2/)

---

💡 **Lưu ý:** Hãy thực hành nhiều để nắm vững kiến thức!