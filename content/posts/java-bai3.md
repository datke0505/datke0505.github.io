---
title: "Java Bài 3 - Mảng (Arrays) | My New Hugo Site"
date: 2025-10-05
draft: false
categories: ["Java"]
tags: ["java", "arrays", "data-structures"]
description: "Học cách sử dụng mảng trong Java - cấu trúc dữ liệu cơ bản"
---

# Java Bài 3 - Mảng (Arrays)

Mảng (Array) là cấu trúc dữ liệu lưu trữ nhiều giá trị cùng kiểu trong một biến duy nhất.

## 1. Khai báo và khởi tạo mảng

### Cách 1: Khai báo rồi khởi tạo
```java
public class ArrayBasic {
    public static void main(String[] args) {
        // Khai báo mảng
        int[] numbers;
        
        // Khởi tạo với kích thước
        numbers = new int[5];
        
        // Gán giá trị
        numbers[0] = 10;
        numbers[1] = 20;
        numbers[2] = 30;
        numbers[3] = 40;
        numbers[4] = 50;
        
        System.out.println("Phần tử đầu tiên: " + numbers[0]);
    }
}
```

### Cách 2: Khai báo và khởi tạo cùng lúc
```java
public class ArrayInit {
    public static void main(String[] args) {
        // Khởi tạo với giá trị
        int[] scores = {85, 90, 78, 92, 88};
        
        // Hoặc
        String[] names = new String[]{"An", "Bình", "Chi"};
        
        System.out.println("Số phần tử: " + scores.length);
    }
}
```

## 2. Truy cập và thay đổi phần tử

```java
public class ArrayAccess {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        
        // Truy cập phần tử
        System.out.println("Phần tử thứ 3: " + numbers[2]); // 30
        
        // Thay đổi giá trị
        numbers[2] = 100;
        System.out.println("Sau khi thay đổi: " + numbers[2]); // 100
        
        // Độ dài mảng
        System.out.println("Độ dài: " + numbers.length);
    }
}
```

## 3. Duyệt mảng

### Dùng vòng lặp for thường
```java
public class ArrayLoop {
    public static void main(String[] args) {
        int[] numbers = {5, 10, 15, 20, 25};
        
        System.out.println("Các phần tử trong mảng:");
        for (int i = 0; i < numbers.length; i++) {
            System.out.println("numbers[" + i + "] = " + numbers[i]);
        }
    }
}
```

### Dùng for-each loop
```java
public class ArrayForEach {
    public static void main(String[] args) {
        String[] fruits = {"Táo", "Cam", "Chuối", "Xoài"};
        
        System.out.println("Danh sách trái cây:");
        for (String fruit : fruits) {
            System.out.println("- " + fruit);
        }
    }
}
```

## 4. Các thao tác với mảng

### Tìm giá trị lớn nhất/nhỏ nhất
```java
public class FindMinMax {
    public static void main(String[] args) {
        int[] numbers = {45, 23, 67, 12, 89, 34};
        
        int max = numbers[0];
        int min = numbers[0];
        
        for (int num : numbers) {
            if (num > max) max = num;
            if (num < min) min = num;
        }
        
        System.out.println("Giá trị lớn nhất: " + max);
        System.out.println("Giá trị nhỏ nhất: " + min);
    }
}
```

### Tính tổng và trung bình
```java
public class ArraySum {
    public static void main(String[] args) {
        double[] scores = {8.5, 9.0, 7.5, 8.0, 9.5};
        
        double sum = 0;
        for (double score : scores) {
            sum += score;
        }
        
        double average = sum / scores.length;
        
        System.out.println("Tổng điểm: " + sum);
        System.out.printf("Điểm trung bình: %.2f\n", average);
    }
}
```

### Tìm kiếm phần tử
```java
public class ArraySearch {
    public static void main(String[] args) {
        int[] numbers = {10, 25, 30, 45, 50};
        int target = 30;
        boolean found = false;
        int position = -1;
        
        for (int i = 0; i < numbers.length; i++) {
            if (numbers[i] == target) {
                found = true;
                position = i;
                break;
            }
        }
        
        if (found) {
            System.out.println("Tìm thấy " + target + " tại vị trí " + position);
        } else {
            System.out.println("Không tìm thấy " + target);
        }
    }
}
```

### Đếm phần tử thỏa điều kiện
```java
public class CountElements {
    public static void main(String[] args) {
        int[] numbers = {12, 25, 33, 48, 51, 60, 75};
        int count = 0;
        
        // Đếm số chẵn
        for (int num : numbers) {
            if (num % 2 == 0) {
                count++;
            }
        }
        
        System.out.println("Số lượng số chẵn: " + count);
    }
}
```

## 5. Sắp xếp mảng

### Sắp xếp tăng dần (Bubble Sort)
```java
public class BubbleSort {
    public static void main(String[] args) {
        int[] numbers = {64, 34, 25, 12, 22, 11, 90};
        
        System.out.println("Mảng trước khi sắp xếp:");
        printArray(numbers);
        
        // Bubble Sort
        for (int i = 0; i < numbers.length - 1; i++) {
            for (int j = 0; j < numbers.length - i - 1; j++) {
                if (numbers[j] > numbers[j + 1]) {
                    // Hoán đổi
                    int temp = numbers[j];
                    numbers[j] = numbers[j + 1];
                    numbers[j + 1] = temp;
                }
            }
        }
        
        System.out.println("\nMảng sau khi sắp xếp:");
        printArray(numbers);
    }
    
    static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

### Sử dụng Arrays.sort()
```java
import java.util.Arrays;

public class ArraysSort {
    public static void main(String[] args) {
        int[] numbers = {64, 34, 25, 12, 22, 11, 90};
        
        System.out.println("Trước: " + Arrays.toString(numbers));
        
        Arrays.sort(numbers);
        
        System.out.println("Sau: " + Arrays.toString(numbers));
    }
}
```

## 6. Mảng nhiều chiều

### Mảng 2 chiều (Ma trận)
```java
public class TwoDimensionalArray {
    public static void main(String[] args) {
        // Khai báo ma trận 3x3
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        System.out.println("Ma trận:");
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
        
        // Tính tổng các phần tử
        int sum = 0;
        for (int[] row : matrix) {
            for (int value : row) {
                sum += value;
            }
        }
        System.out.println("Tổng các phần tử: " + sum);
    }
}
```

## 7. Class Arrays - Các phương thức hữu ích

```java
import java.util.Arrays;

public class ArraysUtility {
    public static void main(String[] args) {
        int[] numbers = {5, 2, 8, 1, 9};
        
        // In mảng
        System.out.println("Mảng: " + Arrays.toString(numbers));
        
        // Sắp xếp
        Arrays.sort(numbers);
        System.out.println("Sau sắp xếp: " + Arrays.toString(numbers));
        
        // Tìm kiếm nhị phân (mảng phải đã sắp xếp)
        int index = Arrays.binarySearch(numbers, 8);
        System.out.println("Vị trí của 8: " + index);
        
        // So sánh hai mảng
        int[] numbers2 = {1, 2, 5, 8, 9};
        boolean isEqual = Arrays.equals(numbers, numbers2);
        System.out.println("Hai mảng bằng nhau: " + isEqual);
        
        // Điền giá trị
        int[] arr = new int[5];
        Arrays.fill(arr, 100);
        System.out.println("Mảng sau fill: " + Arrays.toString(arr));
        
        // Sao chép mảng
        int[] copy = Arrays.copyOf(numbers, numbers.length);
        System.out.println("Mảng copy: " + Arrays.toString(copy));
    }
}
```

## 8. Bài tập thực hành

### Bài 1: Nhập và xuất mảng
```java
import java.util.Scanner;

public class InputArray {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập số phần tử: ");
        int n = sc.nextInt();
        
        int[] arr = new int[n];
        
        System.out.println("Nhập các phần tử:");
        for (int i = 0; i < n; i++) {
            System.out.print("arr[" + i + "] = ");
            arr[i] = sc.nextInt();
        }
        
        System.out.println("\nMảng vừa nhập:");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        
        sc.close();
    }
}
```

### Bài 2: Đảo ngược mảng
```java
public class ReverseArray {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        
        System.out.println("Mảng ban đầu:");
        printArray(numbers);
        
        // Đảo ngược
        int left = 0;
        int right = numbers.length - 1;
        
        while (left < right) {
            int temp = numbers[left];
            numbers[left] = numbers[right];
            numbers[right] = temp;
            left++;
            right--;
        }
        
        System.out.println("Mảng sau đảo ngược:");
        printArray(numbers);
    }
    
    static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

### Bài 3: Tính tổng các số nguyên tố trong mảng
```java
public class SumPrimes {
    public static void main(String[] args) {
        int[] numbers = {2, 4, 7, 10, 11, 15, 17, 20};
        int sum = 0;
        
        for (int num : numbers) {
            if (isPrime(num)) {
                System.out.println(num + " là số nguyên tố");
                sum += num;
            }
        }
        
        System.out.println("Tổng các số nguyên tố: " + sum);
    }
    
    static boolean isPrime(int n) {
        if (n < 2) return false;
        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (n % i == 0) return false;
        }
        return true;
    }
}
```

## Tổng kết

Trong bài học này, bạn đã học được:
- ✅ Khai báo và khởi tạo mảng
- ✅ Truy cập và duyệt mảng
- ✅ Các thao tác: tìm kiếm, sắp xếp, đếm
- ✅ Mảng nhiều chiều
- ✅ Class Arrays và các phương thức hữu ích

**Bài trước:** [Java Bài 2 - Vòng lặp](/posts/java-bai2/)  
**Bài tiếp theo:** [Java Bài 4 - Hàm/Phương thức](/posts/java-bai4/)

---

💡 **Lưu ý:** Mảng trong Java có kích thước cố định. Nếu cần linh hoạt hơn, sử dụng ArrayList!