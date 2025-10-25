---
title: "Bài 8: Collections Framework - ArrayList và LinkedList"
description: "Tìm hiểu về Collections Framework, ArrayList, LinkedList và cách sử dụng trong Java"
date: 2024-10-05
category: "Java"
tags: ["java", "collections", "arraylist", "linkedlist", "data structures"]
---

## Giới thiệu về Collections Framework

Collections Framework là một kiến trúc thống nhất để lưu trữ và thao tác với nhóm các đối tượng. Nó cung cấp các interface và class để làm việc với dữ liệu một cách hiệu quả.

### Hệ thống phân cấp Collections

```
Collection (Interface)
├── List (Interface) - Danh sách có thứ tự, cho phép duplicate
│   ├── ArrayList
│   ├── LinkedList
│   └── Vector
│
├── Set (Interface) - Không cho phép duplicate
│   ├── HashSet
│   ├── LinkedHashSet
│   └── TreeSet
│
└── Queue (Interface) - Hàng đợi
    ├── PriorityQueue
    └── LinkedList

Map (Interface) - Lưu key-value pairs
├── HashMap
├── LinkedHashMap
└── TreeMap
```

## ArrayList

ArrayList là một class implement List interface, sử dụng mảng động để lưu trữ phần tử.

### Khai báo và Khởi tạo

```java
import java.util.ArrayList;

public class ArrayListDemo {
    public static void main(String[] args) {
        // Khai báo ArrayList
        ArrayList<String> fruits = new ArrayList<>();
        
        // Hoặc chỉ định capacity ban đầu
        ArrayList<Integer> numbers = new ArrayList<>(10);
        
        // Khởi tạo với giá trị
        ArrayList<String> colors = new ArrayList<>();
        colors.add("Red");
        colors.add("Green");
        colors.add("Blue");
    }
}
```

### Các Phương Thức Cơ Bản

```java
import java.util.ArrayList;

public class ArrayListMethods {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        
        // 1. Thêm phần tử
        list.add("Java");           // Thêm vào cuối
        list.add("Python");
        list.add("JavaScript");
        list.add(1, "C++");        // Thêm vào vị trí index 1
        
        System.out.println("Danh sách: " + list);
        // [Java, C++, Python, JavaScript]
        
        // 2. Lấy phần tử
        String first = list.get(0);
        System.out.println("Phần tử đầu: " + first); // Java
        
        // 3. Sửa phần tử
        list.set(1, "C#");         // Thay C++ bằng C#
        System.out.println("Sau khi sửa: " + list);
        
        // 4. Xóa phần tử
        list.remove(0);            // Xóa theo index
        list.remove("Python");     // Xóa theo object
        System.out.println("Sau khi xóa: " + list);
        
        // 5. Kiểm tra tồn tại
        boolean hasJava = list.contains("JavaScript");
        System.out.println("Có JavaScript? " + hasJava); // true
        
        // 6. Lấy kích thước
        int size = list.size();
        System.out.println("Kích thước: " + size);
        
        // 7. Kiểm tra rỗng
        boolean isEmpty = list.isEmpty();
        System.out.println("Rỗng? " + isEmpty); // false
        
        // 8. Tìm index
        int index = list.indexOf("JavaScript");
        System.out.println("Index của JavaScript: " + index);
        
        // 9. Xóa tất cả
        list.clear();
        System.out.println("Sau clear: " + list); // []
    }
}
```

### Duyệt ArrayList

```java
import java.util.ArrayList;
import java.util.Iterator;

public class ArrayListIteration {
    public static void main(String[] args) {
        ArrayList<String> languages = new ArrayList<>();
        languages.add("Java");
        languages.add("Python");
        languages.add("JavaScript");
        languages.add("C++");
        
        // Cách 1: For-each loop
        System.out.println("For-each:");
        for (String lang : languages) {
            System.out.println(lang);
        }
        
        // Cách 2: For loop thông thường
        System.out.println("\nFor loop:");
        for (int i = 0; i < languages.size(); i++) {
            System.out.println(languages.get(i));
        }
        
        // Cách 3: Iterator
        System.out.println("\nIterator:");
        Iterator<String> iterator = languages.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
        
        // Cách 4: forEach với Lambda (Java 8+)
        System.out.println("\nLambda:");
        languages.forEach(lang -> System.out.println(lang));
        
        // Cách 5: Method reference (Java 8+)
        System.out.println("\nMethod reference:");
        languages.forEach(System.out::println);
    }
}
```

### Sắp xếp ArrayList

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;

public class ArrayListSorting {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(45);
        numbers.add(12);
        numbers.add(78);
        numbers.add(23);
        numbers.add(56);
        
        // Sắp xếp tăng dần
        Collections.sort(numbers);
        System.out.println("Tăng dần: " + numbers);
        
        // Sắp xếp giảm dần
        Collections.sort(numbers, Collections.reverseOrder());
        System.out.println("Giảm dần: " + numbers);
        
        // Sắp xếp String
        ArrayList<String> names = new ArrayList<>();
        names.add("Minh");
        names.add("An");
        names.add("Hoa");
        names.add("Bình");
        
        Collections.sort(names);
        System.out.println("Tên sắp xếp: " + names);
        
        // Sắp xếp với Comparator (Java 8+)
        names.sort(Comparator.reverseOrder());
        System.out.println("Tên đảo ngược: " + names);
    }
}
```

## LinkedList

LinkedList sử dụng cấu trúc danh sách liên kết đôi (doubly-linked list) để lưu trữ phần tử.

### Khai báo và Sử dụng

```java
import java.util.LinkedList;

public class LinkedListDemo {
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<>();
        
        // Thêm phần tử
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");
        
        // Thêm vào đầu
        list.addFirst("Mango");
        
        // Thêm vào cuối
        list.addLast("Orange");
        
        System.out.println("LinkedList: " + list);
        // [Mango, Apple, Banana, Cherry, Orange]
        
        // Lấy phần tử đầu
        String first = list.getFirst();
        System.out.println("Đầu: " + first);
        
        // Lấy phần tử cuối
        String last = list.getLast();
        System.out.println("Cuối: " + last);
        
        // Xóa phần tử đầu
        list.removeFirst();
        System.out.println("Sau removeFirst: " + list);
        
        // Xóa phần tử cuối
        list.removeLast();
        System.out.println("Sau removeLast: " + list);
    }
}
```

### LinkedList như Queue (Hàng đợi)

```java
import java.util.LinkedList;
import java.util.Queue;

public class LinkedListAsQueue {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();
        
        // Thêm vào queue
        queue.offer("First");
        queue.offer("Second");
        queue.offer("Third");
        
        System.out.println("Queue: " + queue);
        
        // Xem phần tử đầu (không xóa)
        System.out.println("Peek: " + queue.peek());
        
        // Lấy và xóa phần tử đầu
        System.out.println("Poll: " + queue.poll());
        System.out.println("Sau poll: " + queue);
        
        // Lấy và xóa phần tử đầu (throw exception nếu rỗng)
        System.out.println("Remove: " + queue.remove());
        System.out.println("Sau remove: " + queue);
    }
}
```

### LinkedList như Stack (Ngăn xếp)

```java
import java.util.LinkedList;

public class LinkedListAsStack {
    public static void main(String[] args) {
        LinkedList<String> stack = new LinkedList<>();
        
        // Push - thêm vào đầu (top)
        stack.push("One");
        stack.push("Two");
        stack.push("Three");
        
        System.out.println("Stack: " + stack);
        // [Three, Two, One]
        
        // Peek - xem phần tử trên cùng
        System.out.println("Top: " + stack.peek());
        
        // Pop - lấy và xóa phần tử trên cùng
        System.out.println("Pop: " + stack.pop());
        System.out.println("Sau pop: " + stack);
    }
}
```

## So Sánh ArrayList vs LinkedList

| Đặc điểm | ArrayList | LinkedList |
|----------|-----------|------------|
| Cấu trúc | Mảng động | Danh sách liên kết đôi |
| Truy xuất random (get) | O(1) - Nhanh | O(n) - Chậm |
| Thêm/xóa đầu/cuối | O(n) - Chậm | O(1) - Nhanh |
| Thêm/xóa giữa | O(n) | O(n) |
| Bộ nhớ | Ít hơn | Nhiều hơn (lưu pointer) |
| Sử dụng khi | Truy xuất nhiều | Thêm/xóa nhiều |

```java
import java.util.ArrayList;
import java.util.LinkedList;

public class PerformanceComparison {
    public static void main(String[] args) {
        // Test với 100,000 phần tử
        int size = 100000;
        
        // ArrayList
        ArrayList<Integer> arrayList = new ArrayList<>();
        long start = System.currentTimeMillis();
        for (int i = 0; i < size; i++) {
            arrayList.add(i);
        }
        long end = System.currentTimeMillis();
        System.out.println("ArrayList add: " + (end - start) + "ms");
        
        // LinkedList
        LinkedList<Integer> linkedList = new LinkedList<>();
        start = System.currentTimeMillis();
        for (int i = 0; i < size; i++) {
            linkedList.add(i);
        }
        end = System.currentTimeMillis();
        System.out.println("LinkedList add: " + (end - start) + "ms");
        
        // Test get (truy xuất)
        start = System.currentTimeMillis();
        for (int i = 0; i < 1000; i++) {
            arrayList.get(i);
        }
        end = System.currentTimeMillis();
        System.out.println("ArrayList get: " + (end - start) + "ms");
        
        start = System.currentTimeMillis();
        for (int i = 0; i < 1000; i++) {
            linkedList.get(i);
        }
        end = System.currentTimeMillis();
        System.out.println("LinkedList get: " + (end - start) + "ms");
    }
}
```

## Ví dụ Thực Tế: Quản Lý Sinh Viên

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;

class Student {
    private String id;
    private String name;
    private double gpa;
    
    public Student(String id, String name, double gpa) {
        this.id = id;
        this.name = name;
        this.gpa = gpa;
    }
    
    public String getId() { return id; }
    public String getName() { return name; }
    public double getGpa() { return gpa; }
    
    @Override
    public String toString() {
        return String.format("Student[id=%s, name=%s, gpa=%.2f]", id, name, gpa);
    }
}

public class StudentManager {
    private ArrayList<Student> students;
    
    public StudentManager() {
        students = new ArrayList<>();
    }
    
    public void addStudent(Student student) {
        students.add(student);
        System.out.println("Đã thêm: " + student.getName());
    }
    
    public void removeStudent(String id) {
        students.removeIf(s -> s.getId().equals(id));
        System.out.println("Đã xóa sinh viên ID: " + id);
    }
    
    public Student findStudent(String id) {
        for (Student s : students) {
            if (s.getId().equals(id)) {
                return s;
            }
        }
        return null;
    }
    
    public void sortByName() {
        students.sort(Comparator.comparing(Student::getName));
    }
    
    public void sortByGpa() {
        students.sort(Comparator.comparing(Student::getGpa).reversed());
    }
    
    public void displayAll() {
        System.out.println("\n=== Danh sách sinh viên ===");
        for (Student s : students) {
            System.out.println(s);
        }
    }
    
    public static void main(String[] args) {
        StudentManager manager = new StudentManager();
        
        // Thêm sinh viên
        manager.addStudent(new Student("SV001", "Nguyễn Văn A", 3.5));
        manager.addStudent(new Student("SV002", "Trần Thị B", 3.8));
        manager.addStudent(new Student("SV003", "Lê Văn C", 3.2));
        manager.addStudent(new Student("SV004", "Phạm Thị D", 3.9));
        
        // Hiển thị tất cả
        manager.displayAll();
        
        // Sắp xếp theo tên
        System.out.println("\nSắp xếp theo tên:");
        manager.sortByName();
        manager.displayAll();
        
        // Sắp xếp theo GPA
        System.out.println("\nSắp xếp theo GPA:");
        manager.sortByGpa();
        manager.displayAll();
        
        // Tìm sinh viên
        System.out.println("\nTìm SV002:");
        Student found = manager.findStudent("SV002");
        if (found != null) {
            System.out.println("Tìm thấy: " + found);
        }
        
        // Xóa sinh viên
        manager.removeStudent("SV001");
        manager.displayAll();
    }
}
```

## Các Phương Thức Hữu Ích Khác

### Chuyển đổi giữa Array và ArrayList

```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayConversion {
    public static void main(String[] args) {
        // Array sang ArrayList
        String[] arr = {"Java", "Python", "C++"};
        ArrayList<String> list = new ArrayList<>(Arrays.asList(arr));
        System.out.println("ArrayList: " + list);
        
        // ArrayList sang Array
        ArrayList<String> languages = new ArrayList<>();
        languages.add("Java");
        languages.add("Python");
        languages.add("JavaScript");
        
        String[] array = languages.toArray(new String[0]);
        System.out.println("Array: " + Arrays.toString(array));
    }
}
```

### SubList và Clone

```java
import java.util.ArrayList;
import java.util.List;

public class SubListDemo {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        for (int i = 1; i <= 10; i++) {
            numbers.add(i);
        }
        
        // Lấy sublist (từ index 2 đến 6-1)
        List<Integer> subList = numbers.subList(2, 6);
        System.out.println("SubList: " + subList); // [3, 4, 5, 6]
        
        // Clone ArrayList
        ArrayList<Integer> cloned = (ArrayList<Integer>) numbers.clone();
        cloned.set(0, 100);
        
        System.out.println("Original: " + numbers); // [1, 2, 3, ...]
        System.out.println("Cloned: " + cloned);    // [100, 2, 3, ...]
    }
}
```

### RemoveIf và ReplaceAll (Java 8+)

```java
import java.util.ArrayList;

public class Java8Methods {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        for (int i = 1; i <= 10; i++) {
            numbers.add(i);
        }
        
        System.out.println("Original: " + numbers);
        
        // Xóa tất cả số chẵn
        numbers.removeIf(n -> n % 2 == 0);
        System.out.println("Sau removeIf: " + numbers);
        
        // Nhân đôi tất cả các số
        numbers.replaceAll(n -> n * 2);
        System.out.println("Sau replaceAll: " + numbers);
    }
}
```

## Ví dụ Thực Tế: Todo List Application

```java
import java.util.ArrayList;
import java.util.Scanner;

class Task {
    private String title;
    private boolean completed;
    
    public Task(String title) {
        this.title = title;
        this.completed = false;
    }
    
    public String getTitle() { return title; }
    public boolean isCompleted() { return completed; }
    
    public void setCompleted(boolean completed) {
        this.completed = completed;
    }
    
    @Override
    public String toString() {
        return (completed ? "[✓] " : "[ ] ") + title;
    }
}

public class TodoListApp {
    private ArrayList<Task> tasks;
    private Scanner scanner;
    
    public TodoListApp() {
        tasks = new ArrayList<>();
        scanner = new Scanner(System.in);
    }
    
    public void addTask(String title) {
        tasks.add(new Task(title));
        System.out.println("Đã thêm: " + title);
    }
    
    public void removeTask(int index) {
        if (index >= 0 && index < tasks.size()) {
            Task removed = tasks.remove(index);
            System.out.println("Đã xóa: " + removed.getTitle());
        } else {
            System.out.println("Index không hợp lệ!");
        }
    }
    
    public void completeTask(int index) {
        if (index >= 0 && index < tasks.size()) {
            tasks.get(index).setCompleted(true);
            System.out.println("Đã hoàn thành!");
        } else {
            System.out.println("Index không hợp lệ!");
        }
    }
    
    public void displayTasks() {
        if (tasks.isEmpty()) {
            System.out.println("Không có task nào!");
            return;
        }
        
        System.out.println("\n=== TODO LIST ===");
        for (int i = 0; i < tasks.size(); i++) {
            System.out.println(i + ". " + tasks.get(i));
        }
    }
    
    public void showMenu() {
        System.out.println("\n=== MENU ===");
        System.out.println("1. Thêm task");
        System.out.println("2. Xóa task");
        System.out.println("3. Hoàn thành task");
        System.out.println("4. Hiển thị tất cả");
        System.out.println("0. Thoát");
        System.out.print("Chọn: ");
    }
    
    public void run() {
        while (true) {
            showMenu();
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline
            
            switch (choice) {
                case 1:
                    System.out.print("Nhập task: ");
                    String title = scanner.nextLine();
                    addTask(title);
                    break;
                case 2:
                    displayTasks();
                    System.out.print("Nhập index cần xóa: ");
                    int removeIndex = scanner.nextInt();
                    removeTask(removeIndex);
                    break;
                case 3:
                    displayTasks();
                    System.out.print("Nhập index đã hoàn thành: ");
                    int completeIndex = scanner.nextInt();
                    completeTask(completeIndex);
                    break;
                case 4:
                    displayTasks();
                    break;
                case 0:
                    System.out.println("Tạm biệt!");
                    return;
                default:
                    System.out.println("Lựa chọn không hợp lệ!");
            }
        }
    }
    
    public static void main(String[] args) {
        TodoListApp app = new TodoListApp();
        app.run();
    }
}
```

## Bài Tập Thực Hành

1. Viết chương trình quản lý danh bạ điện thoại sử dụng ArrayList
2. Tạo shopping cart với ArrayList để thêm, xóa, tính tổng giá sản phẩm
3. Xây dựng hệ thống quản lý thư viện sách với các chức năng CRUD
4. Viết chương trình tìm phần tử trùng lặp trong ArrayList
5. Tạo playlist nhạc với LinkedList, có thể phát next/previous

## Lưu Ý Quan Trọng

### Thread-Safety
ArrayList và LinkedList không thread-safe. Nếu cần, sử dụng:
```java
import java.util.Collections;
import java.util.List;
import java.util.ArrayList;

List<String> syncList = Collections.synchronizedList(new ArrayList<>());
```

### Capacity và Performance
```java
// Nên chỉ định capacity ban đầu nếu biết trước kích thước
ArrayList<String> list = new ArrayList<>(1000); // Tốt hơn
// ArrayList<String> list = new ArrayList<>();   // Capacity mặc định = 10
```

### Xóa phần tử khi duyệt
```java
// SAI - ConcurrentModificationException
for (String item : list) {
    if (item.equals("remove")) {
        list.remove(item); // Lỗi!
    }
}

// ĐÚNG - Sử dụng Iterator
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    String item = iterator.next();
    if (item.equals("remove")) {
        iterator.remove(); // OK
    }
}

// HOẶC - Sử dụng removeIf (Java 8+)
list.removeIf(item -> item.equals("remove")); // OK
```

## Tổng Kết

- **ArrayList**: Tốt cho truy xuất random, dựa trên mảng động
- **LinkedList**: Tốt cho thêm/xóa ở đầu/cuối, dựa trên danh sách liên kết
- Sử dụng **generics** để đảm bảo type-safety
- ArrayList phổ biến hơn trong hầu hết trường hợp
- LinkedList hữu ích khi implement Queue hoặc Stack
- Cả hai đều thuộc Collections Framework và có nhiều phương thức tiện ích