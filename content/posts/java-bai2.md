---
title: "Java Bài 2 - Vòng lặp | My New Hugo Site"
date: 2025-10-04
draft: false
categories: ["Java"]
tags: ["java", "loops", "for", "while"]
description: "Tìm hiểu về vòng lặp for, while, do-while trong Java"
---

# Java Bài 2 - Vòng lặp

Vòng lặp (Loop) là cấu trúc cho phép thực hiện một khối lệnh nhiều lần. Java hỗ trợ 3 loại vòng lặp chính: **for**, **while**, và **do-while**.

## 1. Vòng lặp FOR

Vòng lặp `for` được sử dụng khi biết trước số lần lặp.

### Cú pháp:
```java
for (khởi_tạo; điều_kiện; bước_nhảy) {
    // Khối lệnh thực thi
}
```

### Ví dụ cơ bản:
```java
public class ForLoop {
    public static void main(String[] args) {
        // In số từ 1 đến 5
        for (int i = 1; i <= 5; i++) {
            System.out.println("Số: " + i);
        }
    }
}
```

**Kết quả:**
```
Số: 1
Số: 2
Số: 3
Số: 4
Số: 5
```

### Ví dụ nâng cao:

#### Tính tổng từ 1 đến 100:
```java
public class SumNumbers {
    public static void main(String[] args) {
        int sum = 0;
        
        for (int i = 1; i <= 100; i++) {
            sum += i;
        }
        
        System.out.println("Tổng từ 1 đến 100: " + sum); // 5050
    }
}
```

#### In bảng cửu chương:
```java
public class MultiplicationTable {
    public static void main(String[] args) {
        int n = 7;
        
        System.out.println("Bảng cửu chương " + n + ":");
        for (int i = 1; i <= 10; i++) {
            System.out.println(n + " x " + i + " = " + (n * i));
        }
    }
}
```

## 2. Vòng lặp WHILE

Vòng lặp `while` kiểm tra điều kiện trước khi thực thi. Nếu điều kiện đúng thì thực thi, sai thì dừng.

### Cú pháp:
```java
while (điều_kiện) {
    // Khối lệnh thực thi
}
```

### Ví dụ:
```java
public class WhileLoop {
    public static void main(String[] args) {
        int count = 1;
        
        while (count <= 5) {
            System.out.println("Lần lặp thứ: " + count);
            count++;
        }
    }
}
```

### Ví dụ thực tế - Đoán số:
```java
import java.util.Scanner;
import java.util.Random;

public class GuessNumber {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Random rand = new Random();
        
        int secretNumber = rand.nextInt(100) + 1;
        int guess = 0;
        int attempts = 0;
        
        System.out.println("Tôi đã nghĩ một số từ 1 đến 100. Hãy đoán xem!");
        
        while (guess != secretNumber) {
            System.out.print("Nhập số của bạn: ");
            guess = sc.nextInt();
            attempts++;
            
            if (guess < secretNumber) {
                System.out.println("Số bạn đoán nhỏ hơn!");
            } else if (guess > secretNumber) {
                System.out.println("Số bạn đoán lớn hơn!");
            } else {
                System.out.println("🎉 Chúc mừng! Bạn đã đoán đúng!");
                System.out.println("Số lần đoán: " + attempts);
            }
        }
        
        sc.close();
    }
}
```

## 3. Vòng lặp DO-WHILE

Vòng lặp `do-while` thực thi ít nhất 1 lần, sau đó mới kiểm tra điều kiện.

### Cú pháp:
```java
do {
    // Khối lệnh thực thi
} while (điều_kiện);
```

### Ví dụ:
```java
public class DoWhileLoop {
    public static void main(String[] args) {
        int i = 1;
        
        do {
            System.out.println("Giá trị: " + i);
            i++;
        } while (i <= 5);
    }
}
```

### Ví dụ thực tế - Menu chương trình:
```java
import java.util.Scanner;

public class MenuProgram {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int choice;
        
        do {
            System.out.println("\n=== MENU ===");
            System.out.println("1. Tính tổng 2 số");
            System.out.println("2. Tính hiệu 2 số");
            System.out.println("3. Tính tích 2 số");
            System.out.println("4. Tính thương 2 số");
            System.out.println("0. Thoát");
            System.out.print("Chọn chức năng: ");
            choice = sc.nextInt();
            
            if (choice >= 1 && choice <= 4) {
                System.out.print("Nhập số thứ nhất: ");
                double a = sc.nextDouble();
                System.out.print("Nhập số thứ hai: ");
                double b = sc.nextDouble();
                
                switch (choice) {
                    case 1:
                        System.out.println("Kết quả: " + (a + b));
                        break;
                    case 2:
                        System.out.println("Kết quả: " + (a - b));
                        break;
                    case 3:
                        System.out.println("Kết quả: " + (a * b));
                        break;
                    case 4:
                        if (b != 0) {
                            System.out.println("Kết quả: " + (a / b));
                        } else {
                            System.out.println("Lỗi: Không thể chia cho 0!");
                        }
                        break;
                }
            } else if (choice != 0) {
                System.out.println("Lựa chọn không hợp lệ!");
            }
            
        } while (choice != 0);
        
        System.out.println("Cảm ơn bạn đã sử dụng chương trình!");
        sc.close();
    }
}
```

## 4. Vòng lặp lồng nhau (Nested Loop)

Vòng lặp lồng nhau là vòng lặp bên trong vòng lặp khác.

### In hình tam giác:
```java
public class Triangle {
    public static void main(String[] args) {
        int rows = 5;
        
        for (int i = 1; i <= rows; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

**Kết quả:**
```
* 
* * 
* * * 
* * * * 
* * * * * 
```

### In bảng cửu chương đầy đủ:
```java
public class FullMultiplicationTable {
    public static void main(String[] args) {
        System.out.println("BẢNG CỬU CHƯƠNG TỪ 2 ĐẾN 9\n");
        
        for (int i = 2; i <= 9; i++) {
            System.out.println("--- Bảng " + i + " ---");
            for (int j = 1; j <= 10; j++) {
                System.out.printf("%d x %d = %d\n", i, j, i * j);
            }
            System.out.println();
        }
    }
}
```

## 5. Lệnh break và continue

### Break - Thoát khỏi vòng lặp:
```java
public class BreakExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i == 6) {
                break; // Dừng vòng lặp khi i = 6
            }
            System.out.println(i);
        }
    }
}
```
**Kết quả:** 1 2 3 4 5

### Continue - Bỏ qua lần lặp hiện tại:
```java
public class ContinueExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i % 2 == 0) {
                continue; // Bỏ qua số chẵn
            }
            System.out.println(i);
        }
    }
}
```
**Kết quả:** 1 3 5 7 9

## 6. Enhanced For Loop (For-each)

Sử dụng để duyệt mảng hoặc collection.

```java
public class ForEachExample {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        
        for (int num : numbers) {
            System.out.println(num);
        }
    }
}
```

## 7. Bài tập thực hành

### Bài 1: Tính giai thừa
```java
import java.util.Scanner;

public class Factorial {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập số nguyên dương n: ");
        int n = sc.nextInt();
        
        long factorial = 1;
        for (int i = 1; i <= n; i++) {
            factorial *= i;
        }
        
        System.out.println(n + "! = " + factorial);
        sc.close();
    }
}
```

### Bài 2: Kiểm tra số nguyên tố
```java
import java.util.Scanner;

public class PrimeNumber {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập số cần kiểm tra: ");
        int n = sc.nextInt();
        
        boolean isPrime = true;
        
        if (n < 2) {
            isPrime = false;
        } else {
            for (int i = 2; i <= Math.sqrt(n); i++) {
                if (n % i == 0) {
                    isPrime = false;
                    break;
                }
            }
        }
        
        if (isPrime) {
            System.out.println(n + " là số nguyên tố");
        } else {
            System.out.println(n + " không là số nguyên tố");
        }
        
        sc.close();
    }
}
```

### Bài 3: In dãy Fibonacci
```java
import java.util.Scanner;

public class Fibonacci {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập số phần tử: ");
        int n = sc.nextInt();
        
        int a = 0, b = 1;
        
        System.out.println("Dãy Fibonacci:");
        for (int i = 1; i <= n; i++) {
            System.out.print(a + " ");
            int next = a + b;
            a = b;
            b = next;
        }
        
        sc.close();
    }
}
```

## So sánh các loại vòng lặp

| Loại vòng lặp | Khi nào sử dụng | Đặc điểm |
|---------------|-----------------|----------|
| **for** | Biết trước số lần lặp | Gọn gàng, dễ đọc |
| **while** | Không biết trước số lần lặp | Kiểm tra điều kiện trước |
| **do-while** | Cần thực thi ít nhất 1 lần | Kiểm tra điều kiện sau |
| **for-each** | Duyệt mảng/collection | Đơn giản, an toàn |

## Tổng kết

Trong bài học này, bạn đã học được:
- ✅ Vòng lặp for, while, do-while
- ✅ Vòng lặp lồng nhau
- ✅ Lệnh break và continue
- ✅ Enhanced for loop (for-each)
- ✅ Các bài tập thực hành

**Bài trước:** [Java Bài 1 - Cơ bản](/posts/java-bai1/)

---

💡 **Mẹo:** Lựa chọn loại vòng lặp phù hợp sẽ giúp code dễ đọc và hiệu quả hơn!