---
title: "Bài 6: Kế Thừa (Inheritance) trong Java"
description: "Tìm hiểu về tính kế thừa, class con, class cha và cách sử dụng inheritance trong Java"
date: 2024-10-05
category: "Java"
tags: ["java", "oop", "inheritance", "kế thừa", "extends"]
---

## Giới thiệu về Kế Thừa

Kế thừa (Inheritance) là một trong bốn tính chất quan trọng của OOP, cho phép một class (class con) kế thừa các thuộc tính và phương thức từ một class khác (class cha), giúp tái sử dụng code và tạo mối quan hệ giữa các class.

## Cú pháp Kế Thừa

```java
// Class cha (Parent class / Super class / Base class)
public class Animal {
    String name;
    int age;
    
    public void eat() {
        System.out.println(name + " đang ăn");
    }
    
    public void sleep() {
        System.out.println(name + " đang ngủ");
    }
}

// Class con (Child class / Sub class / Derived class)
public class Dog extends Animal {
    String breed;
    
    public void bark() {
        System.out.println(name + " đang sủa: Gâu gâu!");
    }
}

// Sử dụng
public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.name = "Lục";
        myDog.age = 3;
        myDog.breed = "Golden Retriever";
        
        // Gọi phương thức từ class cha
        myDog.eat();
        myDog.sleep();
        
        // Gọi phương thức từ class con
        myDog.bark();
    }
}
```

## Ví dụ Thực Tế

### Ví dụ 1: Hệ thống quản lý nhân viên

```java
// Class cha
public class Employee {
    protected String name;
    protected String id;
    protected double baseSalary;
    
    public Employee(String name, String id, double baseSalary) {
        this.name = name;
        this.id = id;
        this.baseSalary = baseSalary;
    }
    
    public double calculateSalary() {
        return baseSalary;
    }
    
    public void displayInfo() {
        System.out.println("Tên: " + name);
        System.out.println("ID: " + id);
        System.out.println("Lương cơ bản: " + baseSalary);
    }
}

// Class con - Manager
public class Manager extends Employee {
    private double bonus;
    private int teamSize;
    
    public Manager(String name, String id, double baseSalary, double bonus, int teamSize) {
        super(name, id, baseSalary); // Gọi constructor của class cha
        this.bonus = bonus;
        this.teamSize = teamSize;
    }
    
    @Override
    public double calculateSalary() {
        return baseSalary + bonus;
    }
    
    @Override
    public void displayInfo() {
        super.displayInfo(); // Gọi phương thức của class cha
        System.out.println("Thưởng: " + bonus);
        System.out.println("Số nhân viên quản lý: " + teamSize);
        System.out.println("Tổng lương: " + calculateSalary());
    }
}

// Class con - Developer
public class Developer extends Employee {
    private String programmingLanguage;
    private int projectCount;
    
    public Developer(String name, String id, double baseSalary, String language) {
        super(name, id, baseSalary);
        this.programmingLanguage = language;
        this.projectCount = 0;
    }
    
    public void completeProject() {
        projectCount++;
        System.out.println(name + " đã hoàn thành project thứ " + projectCount);
    }
    
    @Override
    public double calculateSalary() {
        return baseSalary + (projectCount * 1000000); // Thưởng 1 triệu/project
    }
    
    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Ngôn ngữ: " + programmingLanguage);
        System.out.println("Số project: " + projectCount);
        System.out.println("Tổng lương: " + calculateSalary());
    }
}
```

## Từ khóa `super`

`super` được sử dụng để:
1. Gọi constructor của class cha
2. Truy cập thuộc tính của class cha
3. Gọi phương thức của class cha

```java
public class Vehicle {
    protected String brand;
    protected int year;
    
    public Vehicle(String brand, int year) {
        this.brand = brand;
        this.year = year;
    }
    
    public void displayInfo() {
        System.out.println("Thương hiệu: " + brand);
        System.out.println("Năm sản xuất: " + year);
    }
}

public class Car extends Vehicle {
    private int numberOfDoors;
    
    public Car(String brand, int year, int doors) {
        super(brand, year); // Gọi constructor của Vehicle
        this.numberOfDoors = doors;
    }
    
    @Override
    public void displayInfo() {
        super.displayInfo(); // Gọi phương thức displayInfo() của Vehicle
        System.out.println("Số cửa: " + numberOfDoors);
    }
    
    public void showBrand() {
        System.out.println("Xe của tôi là: " + super.brand); // Truy cập thuộc tính của Vehicle
    }
}
```

## Method Overriding (Ghi đè phương thức)

Method Overriding là việc class con định nghĩa lại phương thức đã có trong class cha.

```java
public class Shape {
    public double calculateArea() {
        return 0;
    }
    
    public void draw() {
        System.out.println("Vẽ hình");
    }
}

public class Rectangle extends Shape {
    private double width;
    private double height;
    
    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    
    @Override
    public double calculateArea() {
        return width * height;
    }
    
    @Override
    public void draw() {
        System.out.println("Vẽ hình chữ nhật " + width + "x" + height);
    }
}

public class Circle extends Shape {
    private double radius;
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
    
    @Override
    public void draw() {
        System.out.println("Vẽ hình tròn bán kính " + radius);
    }
}

// Sử dụng
public class Main {
    public static void main(String[] args) {
        Shape shape1 = new Rectangle(5, 3);
        Shape shape2 = new Circle(4);
        
        shape1.draw();
        System.out.println("Diện tích: " + shape1.calculateArea());
        
        shape2.draw();
        System.out.println("Diện tích: " + shape2.calculateArea());
    }
}
```

## Access Modifiers trong Kế Thừa

```java
public class Parent {
    public int publicVar = 1;        // Truy cập được ở mọi nơi
    protected int protectedVar = 2;   // Truy cập trong package và class con
    int defaultVar = 3;               // Truy cập trong cùng package
    private int privateVar = 4;       // Chỉ truy cập trong class này
    
    public void display() {
        System.out.println("Public: " + publicVar);
        System.out.println("Protected: " + protectedVar);
        System.out.println("Default: " + defaultVar);
        System.out.println("Private: " + privateVar);
    }
}

public class Child extends Parent {
    public void showInheritedVars() {
        System.out.println(publicVar);     // OK
        System.out.println(protectedVar);  // OK
        System.out.println(defaultVar);    // OK (nếu cùng package)
        // System.out.println(privateVar); // ERROR - không thể truy cập
    }
}
```

## Đa cấp Kế Thừa (Multilevel Inheritance)

```java
// Cấp 1
public class LivingBeing {
    public void breathe() {
        System.out.println("Đang hô hấp");
    }
}

// Cấp 2
public class Animal extends LivingBeing {
    public void move() {
        System.out.println("Đang di chuyển");
    }
}

// Cấp 3
public class Dog extends Animal {
    public void bark() {
        System.out.println("Gâu gâu!");
    }
}

// Sử dụng
public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.breathe(); // Từ LivingBeing
        dog.move();    // Từ Animal
        dog.bark();    // Từ Dog
    }
}
```

## Kế Thừa Phân Cấp (Hierarchical Inheritance)

```java
public class Vehicle {
    protected String brand;
    
    public void start() {
        System.out.println("Phương tiện khởi động");
    }
}

public class Car extends Vehicle {
    public void drive() {
        System.out.println("Ô tô đang chạy");
    }
}

public class Motorcycle extends Vehicle {
    public void ride() {
        System.out.println("Xe máy đang chạy");
    }
}

public class Truck extends Vehicle {
    public void transport() {
        System.out.println("Xe tải đang chở hàng");
    }
}
```

## Lưu Ý về Kế Thừa

### Java không hỗ trợ đa kế thừa

```java
// KHÔNG HỢP LỆ - Java không cho phép kế thừa nhiều class
// public class Child extends Parent1, Parent2 { }

// Thay vào đó, sử dụng Interface (sẽ học ở bài sau)
```

### Constructor không được kế thừa

```java
public class Parent {
    public Parent() {
        System.out.println("Constructor của Parent");
    }
}

public class Child extends Parent {
    public Child() {
        super(); // Tự động gọi constructor của Parent
        System.out.println("Constructor của Child");
    }
}

// Khi tạo object Child, cả 2 constructor đều được gọi:
// Constructor của Parent
// Constructor của Child
```

## Bài Tập Thực Hành

1. Tạo class `BankAccount` với các class con `SavingsAccount` và `CheckingAccount`, mỗi loại có cách tính lãi suất khác nhau
2. Tạo hệ thống quản lý `Person` với các class con `Student` và `Teacher`
3. Tạo class `Product` với các class con `Electronics`, `Clothing`, `Food` có phương thức tính giá khác nhau
4. Xây dựng hệ thống `Transport` với `Land`, `Water`, `Air` transport
5. Tạo game đơn giản với class `Character` và các class con `Warrior`, `Mage`, `Archer`

## Khi nào nên sử dụng Kế Thừa?

✅ **NÊN dùng khi:**
- Có mối quan hệ "IS-A" rõ ràng (Dog IS-A Animal)
- Muốn tái sử dụng code từ class có sẵn
- Các class con có chung hành vi cơ bản

❌ **KHÔNG NÊN dùng khi:**
- Chỉ muốn sử dụng một số phương thức (dùng Composition)
- Không có mối quan hệ logic giữa các class
- Tạo ra cấu trúc phức tạp không cần thiết

## Tổng Kết

- Kế thừa giúp tái sử dụng code và tạo cấu trúc phân cấp
- Sử dụng `extends` để kế thừa từ class cha
- `super` để truy cập members của class cha
- `@Override` để ghi đè phương thức
- Class con kế thừa tất cả members trừ private
- Java chỉ hỗ trợ đơn kế thừa (một class chỉ kế thừa từ một class cha)