---
title: "Bài 5: Mảng (Arrays) trong Java"
description: "Tìm hiểu về mảng, cách khai báo, khởi tạo và thao tác với mảng trong Java"
date: 2024-10-05
category: "Java"
tags: ["java", "arrays", "mảng", "cơ bản"]
---

## Giới thiệu về Mảng

Mảng là một cấu trúc dữ liệu lưu trữ nhiều giá trị cùng kiểu dữ liệu trong một biến duy nhất. Mảng trong Java có kích thước cố định và các phần tử được truy xuất thông qua chỉ số (index).

## Khai báo và Khởi tạo Mảng

### Cách 1: Khai báo rồi khởi tạo

```java
// Khai báo mảng
int[] numbers;

// Khởi tạo mảng với 5 phần tử
numbers = new int[5];

// Gán giá trị cho từng phần tử
numbers[0] = 10;
numbers[1] = 20;
numbers[2] = 30;
numbers[3] = 40;
numbers[4] = 50;
```

### Cách 2: Khai báo và khởi tạo cùng lúc

```java
// Khởi tạo mảng với giá trị ban đầu
int[] numbers = {10, 20, 30, 40, 50};

// Hoặc
String[] fruits = {"Táo", "Cam", "Chuối", "Xoài"};
```

## Truy xuất và Duyệt Mảng

### Truy xuất phần tử theo index

```java
int[] numbers = {10, 20, 30, 40, 50};

// Lấy phần tử đầu tiên
System.out.println(numbers[0]); // 10

// Lấy phần tử cuối cùng
System.out.println(numbers[numbers.length - 1]); // 50
```

### Duyệt mảng bằng vòng lặp for

```java
int[] numbers = {10, 20, 30, 40, 50};

// Duyệt bằng for thông thường
for (int i = 0; i < numbers.length; i++) {
    System.out.println("Phần tử thứ " + i + ": " + numbers[i]);
}

// Duyệt bằng for-each
for (int num : numbers) {
    System.out.println(num);
}
```

## Mảng Đa Chiều

### Mảng 2 chiều (Ma trận)

```java
// Khai báo mảng 2 chiều
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Truy xuất phần tử
System.out.println(matrix[1][2]); // 6

// Duyệt mảng 2 chiều
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```

## Các Thao Tác Thường Gặp

### Tìm giá trị lớn nhất, nhỏ nhất

```java
int[] numbers = {45, 23, 67, 12, 89, 34};

int max = numbers[0];
int min = numbers[0];

for (int num : numbers) {
    if (num > max) max = num;
    if (num < min) min = num;
}

System.out.println("Giá trị lớn nhất: " + max); // 89
System.out.println("Giá trị nhỏ nhất: " + min); // 12
```

### Tính tổng và trung bình

```java
int[] scores = {85, 90, 78, 92, 88};

int sum = 0;
for (int score : scores) {
    sum += score;
}

double average = (double) sum / scores.length;

System.out.println("Tổng điểm: " + sum);
System.out.println("Điểm trung bình: " + average);
```

## Sao chép Mảng

```java
int[] original = {1, 2, 3, 4, 5};

// Cách 1: Sử dụng vòng lặp
int[] copy1 = new int[original.length];
for (int i = 0; i < original.length; i++) {
    copy1[i] = original[i];
}

// Cách 2: Sử dụng Arrays.copyOf()
int[] copy2 = Arrays.copyOf(original, original.length);

// Cách 3: Sử dụng clone()
int[] copy3 = original.clone();
```

## Bài Tập Thực Hành

1. Viết chương trình nhập vào n số nguyên và tìm số lớn thứ hai
2. Tạo mảng chứa 10 số nguyên ngẫu nhiên và sắp xếp tăng dần
3. Viết chương trình đảo ngược một mảng
4. Tìm và in ra các số nguyên tố trong một mảng
5. Tạo ma trận đơn vị kích thước n x n

## Lưu Ý Quan Trọng

- Chỉ số mảng bắt đầu từ 0
- Truy xuất vượt quá kích thước mảng sẽ gây lỗi `ArrayIndexOutOfBoundsException`
- Mảng trong Java có kích thước cố định, không thể thay đổi sau khi khởi tạo
- Sử dụng `array.length` để lấy độ dài mảng