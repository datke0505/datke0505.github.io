---
title: "Java - Ngôn ngữ lập trình hướng đối tượng"
date: 2025-10-03
draft: false
categories: ["Java"]
tags: ["java", "programming", "oop"]
---

# Giới thiệu về Java

**Java** là một trong những ngôn ngữ lập trình phổ biến nhất thế giới, được phát triển bởi Sun Microsystems (nay thuộc Oracle) vào năm 1995.

## Đặc điểm nổi bật

### 1. Hướng đối tượng (OOP)
Java là ngôn ngữ lập trình hướng đối tượng thuần túy, giúp code dễ quản lý và tái sử dụng.

### 2. Độc lập nền tảng
Java tuân theo triết lý **"Write Once, Run Anywhere"** (Viết một lần, chạy mọi nơi). Code Java được biên dịch thành bytecode và chạy trên Java Virtual Machine (JVM).

### 3. Bảo mật cao
Java có nhiều cơ chế bảo mật tích hợp sẵn, giúp xây dựng ứng dụng an toàn.

### 4. Đa luồng (Multi-threading)
Java hỗ trợ lập trình đa luồng, cho phép thực thi nhiều tác vụ đồng thời.

## Ứng dụng của Java

- **Ứng dụng Desktop**: Sử dụng JavaFX, Swing
- **Ứng dụng Web**: Spring Boot, Jakarta EE
- **Ứng dụng Mobile**: Android (Kotlin/Java)
- **Game**: Minecraft được viết bằng Java
- **Big Data**: Hadoop, Apache Spark

## Cài đặt Java

### Windows:
1. Tải Java Development Kit (JDK) từ trang chủ Oracle
2. Cài đặt và thiết lập biến môi trường PATH
3. Kiểm tra bằng lệnh: `java -version`

### MacOS/Linux:
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install default-jdk

# MacOS (dùng Homebrew)
brew install openjdk
```

## Chương trình Java đầu tiên

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

Biên dịch và chạy:
```bash
javac HelloWorld.java
java HelloWorld
```

## Các bài học về Java

- [Java Bài 1 - Cơ bản](/posts/java-bai1/)
- [Java Bài 2 - Vòng lặp](/posts/java-bai2/)

---

**Tài liệu tham khảo:**
- [Oracle Java Documentation](https://docs.oracle.com/en/java/)
- [Java Tutorial - W3Schools](https://www.w3schools.com/java/)