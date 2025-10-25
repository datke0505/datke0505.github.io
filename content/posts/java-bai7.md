---
title: "Bài 7: Exception Handling - Xử Lý Ngoại Lệ"
description: "Tìm hiểu về try-catch, throw, throws và cách xử lý lỗi trong Java"
date: 2024-10-05
category: "Java"
tags: ["java", "exception", "error handling", "try-catch", "xử lý lỗi"]
---

## Giới thiệu về Exception

Exception (ngoại lệ) là một sự kiện bất thường xảy ra trong quá trình thực thi chương trình, làm gián đoạn luồng thực thi bình thường. Java cung cấp cơ chế xử lý exception để chương trình không bị crash.

## Phân loại Exception

```
Throwable
├── Error (Lỗi hệ thống, không nên xử lý)
│   ├── OutOfMemoryError
│   └── StackOverflowError
│
└── Exception (Có thể xử lý)
    ├── IOException (Checked Exception)
    ├── SQLException (Checked Exception)
    └── RuntimeException (Unchecked Exception)
        ├── NullPointerException
        ├── ArrayIndexOutOfBoundsException
        └── ArithmeticException
```

### Checked Exception vs Unchecked Exception

**Checked Exception**: Compiler bắt buộc phải xử lý (try-catch hoặc throws)
- IOException, SQLException, FileNotFoundException...

**Unchecked Exception**: Không bắt buộc phải xử lý
- NullPointerException, ArrayIndexOutOfBoundsException, ArithmeticException...

## Try-Catch Block

### Cú pháp cơ bản

```java
public class ExceptionDemo {
    public static void main(String[] args) {
        try {
            // Code có thể gây ra exception
            int result = 10 / 0; // ArithmeticException
            System.out.println(result);
        } catch (ArithmeticException e) {
            // Xử lý exception
            System.out.println("Lỗi: Không thể chia cho 0!");
            System.out.println("Chi tiết: " + e.getMessage());
        }
        
        System.out.println("Chương trình tiếp tục chạy...");
    }
}
```

### Multiple Catch Blocks

```java
public class MultipleCatchDemo {
    public static void main(String[] args) {
        try {
            int[] numbers = {1, 2, 3};
            System.out.println(numbers[5]); // ArrayIndexOutOfBoundsException
            
            int result = 10 / 0; // ArithmeticException
            
            String text = null;
            System.out.println(text.length()); // NullPointerException
            
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Lỗi: Truy cập index không hợp lệ!");
        } catch (ArithmeticException e) {
            System.out.println("Lỗi: Phép toán không hợp lệ!");
        } catch (NullPointerException e) {
            System.out.println("Lỗi: Đối tượng null!");
        }
    }
}
```

### Multi-catch Block (Java 7+)

```java
public class MultiCatchDemo {
    public static void main(String[] args) {
        try {
            // Code có thể gây ra nhiều loại exception
            int[] arr = {1, 2, 3};
            System.out.println(arr[10]);
        } catch (ArrayIndexOutOfBoundsException | ArithmeticException e) {
            System.out.println("Lỗi mảng hoặc phép toán: " + e.getMessage());
        }
    }
}
```

## Finally Block

Finally block luôn được thực thi dù có exception hay không.

```java
public class FinallyDemo {
    public static void main(String[] args) {
        try {
            System.out.println("Bắt đầu try block");
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Xử lý exception");
        } finally {
            System.out.println("Finally block luôn chạy");
            // Thường dùng để đóng file, database connection...
        }
    }
}
```

### Ví dụ thực tế với File

```java
import java.io.*;

public class FileHandlingDemo {
    public static void main(String[] args) {
        BufferedReader reader = null;
        
        try {
            reader = new BufferedReader(new FileReader("data.txt"));
            String line = reader.readLine();
            System.out.println(line);
        } catch (FileNotFoundException e) {
            System.out.println("Không tìm thấy file!");
        } catch (IOException e) {
            System.out.println("Lỗi đọc file!");
        } finally {
            // Đảm bảo đóng file dù có lỗi hay không
            try {
                if (reader != null) {
                    reader.close();
                }
            } catch (IOException e) {
                System.out.println("Lỗi đóng file!");
            }
        }
    }
}
```

## Try-with-Resources (Java 7+)

Tự động đóng resources, code ngắn gọn hơn.

```java
import java.io.*;

public class TryWithResourcesDemo {
    public static void main(String[] args) {
        // Tự động đóng BufferedReader
        try (BufferedReader reader = new BufferedReader(new FileReader("data.txt"))) {
            String line = reader.readLine();
            System.out.println(line);
        } catch (FileNotFoundException e) {
            System.out.println("Không tìm thấy file!");
        } catch (IOException e) {
            System.out.println("Lỗi đọc file!");
        }
        // Không cần finally để đóng file
    }
}
```

## Throw - Ném Exception

Sử dụng `throw` để tạo và ném exception.

```java
public class ThrowDemo {
    public static void checkAge(int age) {
        if (age < 18) {
            throw new ArithmeticException("Tuổi phải >= 18");
        } else {
            System.out.println("Tuổi hợp lệ: " + age);
        }
    }
    
    public static void main(String[] args) {
        try {
            checkAge(15);
        } catch (ArithmeticException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
    }
}
```

## Throws - Khai báo Exception

Sử dụng `throws` để khai báo phương thức có thể ném exception.

```java
import java.io.*;

public class ThrowsDemo {
    // Khai báo phương thức có thể ném IOException
    public static void readFile(String filename) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filename));
        String line = reader.readLine();
        System.out.println(line);
        reader.close();
    }
    
    public static void main(String[] args) {
        try {
            readFile("data.txt");
        } catch (IOException e) {
            System.out.println("Lỗi đọc file: " + e.getMessage());
        }
    }
}
```

## Custom Exception

Tạo exception tùy chỉnh bằng cách kế thừa từ Exception.

```java
// Tạo custom exception
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

class AgeValidator {
    public static void validateAge(int age) throws InvalidAgeException {
        if (age < 0) {
            throw new InvalidAgeException("Tuổi không thể âm!");
        } else if (age > 150) {
            throw new InvalidAgeException("Tuổi không hợp lý!");
        } else if (age < 18) {
            throw new InvalidAgeException("Phải đủ 18 tuổi!");
        }
        System.out.println("Tuổi hợp lệ: " + age);
    }
}

public class CustomExceptionDemo {
    public static void main(String[] args) {
        try {
            AgeValidator.validateAge(-5);
        } catch (InvalidAgeException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
        
        try {
            AgeValidator.validateAge(15);
        } catch (InvalidAgeException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
        
        try {
            AgeValidator.validateAge(25);
        } catch (InvalidAgeException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
    }
}
```

## Ví dụ Thực Tế: ATM System

```java
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

class InvalidAmountException extends Exception {
    public InvalidAmountException(String message) {
        super(message);
    }
}

class BankAccount {
    private String accountNumber;
    private double balance;
    
    public BankAccount(String accountNumber, double initialBalance) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }
    
    public void withdraw(double amount) throws InsufficientFundsException, InvalidAmountException {
        if (amount <= 0) {
            throw new InvalidAmountException("Số tiền phải lớn hơn 0!");
        }
        
        if (amount > balance) {
            throw new InsufficientFundsException(
                "Số dư không đủ! Số dư hiện tại: " + balance
            );
        }
        
        balance -= amount;
        System.out.println("Rút thành công: " + amount);
        System.out.println("Số dư còn lại: " + balance);
    }
    
    public void deposit(double amount) throws InvalidAmountException {
        if (amount <= 0) {
            throw new InvalidAmountException("Số tiền phải lớn hơn 0!");
        }
        
        balance += amount;
        System.out.println("Nạp thành công: " + amount);
        System.out.println("Số dư mới: " + balance);
    }
    
    public double getBalance() {
        return balance;
    }
}

public class ATMDemo {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("123456", 1000000);
        
        // Rút tiền hợp lệ
        try {
            account.withdraw(200000);
        } catch (InsufficientFundsException | InvalidAmountException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
        
        // Rút số tiền âm
        try {
            account.withdraw(-50000);
        } catch (InsufficientFundsException | InvalidAmountException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
        
        // Rút quá số dư
        try {
            account.withdraw(2000000);
        } catch (InsufficientFundsException | InvalidAmountException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
        
        // Nạp tiền
        try {
            account.deposit(500000);
        } catch (InvalidAmountException e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
    }
}
```

## Các Phương Thức của Exception

```java
public class ExceptionMethodsDemo {
    public static void main(String[] args) {
        try {
            int[] arr = {1, 2, 3};
            System.out.println(arr[10]);
        } catch (Exception e) {
            // Lấy thông điệp lỗi
            System.out.println("getMessage(): " + e.getMessage());
            
            // Lấy tên class của exception
            System.out.println("toString(): " + e.toString());
            
            // In stack trace
            System.out.println("printStackTrace():");
            e.printStackTrace();
            
            // Lấy nguyên nhân gốc
            System.out.println("getCause(): " + e.getCause());
        }
    }
}
```

## Best Practices

### ✅ NÊN làm:

```java
// 1. Bắt exception cụ thể
try {
    // code
} catch (FileNotFoundException e) {
    // xử lý cụ thể
} catch (IOException e) {
    // xử lý chung hơn
}

// 2. Log exception
catch (Exception e) {
    logger.error("Error: " + e.getMessage(), e);
}

// 3. Đóng resources
try (FileReader fr = new FileReader("file.txt")) {
    // code
}

// 4. Tạo custom exception có ý nghĩa
throw new InvalidUserInputException("Email không hợp lệ");
```

### ❌ KHÔNG NÊN làm:

```java
// 1. Bắt exception rồi không làm gì
try {
    // code
} catch (Exception e) {
    // Im lặng - rất nguy hiểm!
}

// 2. Bắt Exception quá chung chung
catch (Exception e) { } // Không nên

// 3. Sử dụng exception để điều khiển luồng
if (age < 18) {
    throw new Exception(); // Sai! Nên dùng if-else
}

// 4. Throw exception trong finally
finally {
    throw new Exception(); // Nguy hiểm!
}
```

## Bài Tập Thực Hành

1. Viết chương trình nhập và xử lý exception khi chuyển đổi String sang số
2. Tạo custom exception `InvalidEmailException` và validate email
3. Xây dựng hệ thống đăng nhập với các exception: `UserNotFoundException`, `InvalidPasswordException`
4. Viết chương trình đọc file và xử lý các exception có thể xảy ra
5. Tạo calculator với exception handling cho division by zero, invalid input

## Tổng Kết

- **try-catch** để bắt và xử lý exception
- **finally** luôn chạy, dùng để cleanup resources
- **throw** để ném exception
- **throws** để khai báo phương thức có thể ném exception
- **try-with-resources** tự động đóng resources
- Tạo custom exception bằng cách extends Exception
- Nên bắt exception cụ thể thay vì Exception chung
- Không bỏ qua exception mà không xử lý