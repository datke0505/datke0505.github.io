---
title: "Bài 9: HashMap và HashSet - Collections Framework (Phần 2)"
description: "Tìm hiểu về HashMap, HashSet và cách làm việc với Map và Set trong Java"
date: 2024-10-05
category: "Java"
tags: ["java", "collections", "hashmap", "hashset", "map", "set"]
---

## Giới thiệu về Map và Set

**Map**: Lưu trữ dữ liệu dạng key-value pairs, mỗi key là duy nhất
**Set**: Lưu trữ các phần tử không trùng lặp, không có thứ tự cụ thể

## HashMap

HashMap là implementation phổ biến nhất của Map interface, lưu trữ dữ liệu dạng key-value.

### Khai báo và Khởi tạo

```java
import java.util.HashMap;

public class HashMapDemo {
    public static void main(String[] args) {
        // Khai báo HashMap<KeyType, ValueType>
        HashMap<String, Integer> ages = new HashMap<>();
        
        // Với capacity ban đầu
        HashMap<String, String> phoneBook = new HashMap<>(16);
        
        // Khởi tạo với giá trị
        HashMap<String, Double> prices = new HashMap<>();
        prices.put("Apple", 50000.0);
        prices.put("Banana", 30000.0);
        prices.put("Orange", 40000.0);
    }
}
```

### Các Phương Thức Cơ Bản

```java
import java.util.HashMap;

public class HashMapMethods {
    public static void main(String[] args) {
        HashMap<String, Integer> scores = new HashMap<>();
        
        // 1. Thêm phần tử - put()
        scores.put("Alice", 85);
        scores.put("Bob", 92);
        scores.put("Charlie", 78);
        scores.put("David", 95);
        
        System.out.println("HashMap: " + scores);
        
        // 2. Lấy giá trị - get()
        int aliceScore = scores.get("Alice");
        System.out.println("Điểm của Alice: " + aliceScore);
        
        // 3. Kiểm tra key tồn tại - containsKey()
        boolean hasCharlie = scores.containsKey("Charlie");
        System.out.println("Có Charlie? " + hasCharlie);
        
        // 4. Kiểm tra value tồn tại - containsValue()
        boolean has95 = scores.containsValue(95);
        System.out.println("Có điểm 95? " + has95);
        
        // 5. Xóa phần tử - remove()
        scores.remove("Bob");
        System.out.println("Sau khi xóa Bob: " + scores);
        
        // 6. Thay thế giá trị - replace()
        scores.replace("Alice", 90);
        System.out.println("Sau khi sửa điểm Alice: " + scores);
        
        // 7. Lấy kích thước - size()
        System.out.println("Số phần tử: " + scores.size());
        
        // 8. Kiểm tra rỗng - isEmpty()
        System.out.println("Rỗng? " + scores.isEmpty());
        
        // 9. getOrDefault() - lấy giá trị hoặc default
        int eveScore = scores.getOrDefault("Eve", 0);
        System.out.println("Điểm của Eve: " + eveScore);
        
        // 10. putIfAbsent() - chỉ thêm nếu key chưa tồn tại
        scores.putIfAbsent("Alice", 100); // Không thêm vì Alice đã có
        scores.putIfAbsent("Eve", 88);     // Thêm Eve vì chưa có
        
        System.out.println("Sau putIfAbsent: " + scores);
        
        // 11. Xóa tất cả - clear()
        // scores.clear();
    }
}
```

### Duyệt HashMap

```java
import java.util.HashMap;
import java.util.Map;

public class HashMapIteration {
    public static void main(String[] args) {
        HashMap<String, Integer> population = new HashMap<>();
        population.put("Hà Nội", 8000000);
        population.put("TP.HCM", 9000000);
        population.put("Đà Nẵng", 1200000);
        population.put("Hải Phòng", 2000000);
        
        // Cách 1: Duyệt qua keySet()
        System.out.println("Duyệt keySet:");
        for (String city : population.keySet()) {
            System.out.println(city + ": " + population.get(city));
        }
        
        // Cách 2: Duyệt qua values()
        System.out.println("\nDuyệt values:");
        for (Integer pop : population.values()) {
            System.out.println("Dân số: " + pop);
        }
        
        // Cách 3: Duyệt qua entrySet() - Hiệu quả nhất
        System.out.println("\nDuyệt entrySet:");
        for (Map.Entry<String, Integer> entry : population.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
        
        // Cách 4: forEach với Lambda (Java 8+)
        System.out.println("\nLambda forEach:");
        population.forEach((city, pop) -> {
            System.out.println(city + " có " + pop + " người");
        });
    }
}
```

### Ví dụ Thực Tế: Quản Lý Từ Điển

```java
import java.util.HashMap;
import java.util.Scanner;

public class Dictionary {
    private HashMap<String, String> dict;
    
    public Dictionary() {
        dict = new HashMap<>();
        // Khởi tạo một số từ
        dict.put("hello", "xin chào");
        dict.put("world", "thế giới");
        dict.put("java", "ngôn ngữ lập trình Java");
        dict.put("computer", "máy tính");
        dict.put("programming", "lập trình");
    }
    
    public void addWord(String english, String vietnamese) {
        dict.put(english.toLowerCase(), vietnamese);
        System.out.println("Đã thêm: " + english + " = " + vietnamese);
    }
    
    public String lookup(String english) {
        return dict.getOrDefault(english.toLowerCase(), "Không tìm thấy từ này!");
    }
    
    public void removeWord(String english) {
        if (dict.remove(english.toLowerCase()) != null) {
            System.out.println("Đã xóa từ: " + english);
        } else {
            System.out.println("Không tìm thấy từ: " + english);
        }
    }
    
    public void displayAll() {
        System.out.println("\n=== TỪ ĐIỂN ===");
        dict.forEach((eng, vie) -> {
            System.out.println(eng + " = " + vie);
        });
    }
    
    public int countWords() {
        return dict.size();
    }
    
    public static void main(String[] args) {
        Dictionary dictionary = new Dictionary();
        Scanner scanner = new Scanner(System.in);
        
        while (true) {
            System.out.println("\n1. Tra từ");
            System.out.println("2. Thêm từ");
            System.out.println("3. Xóa từ");
            System.out.println("4. Hiển thị tất cả");
            System.out.println("5. Số lượng từ");
            System.out.println("0. Thoát");
            System.out.print("Chọn: ");
            
            int choice = scanner.nextInt();
            scanner.nextLine();
            
            switch (choice) {
                case 1:
                    System.out.print("Nhập từ tiếng Anh: ");
                    String word = scanner.nextLine();
                    System.out.println("Nghĩa: " + dictionary.lookup(word));
                    break;
                case 2:
                    System.out.print("Từ tiếng Anh: ");
                    String eng = scanner.nextLine();
                    System.out.print("Nghĩa tiếng Việt: ");
                    String vie = scanner.nextLine();
                    dictionary.addWord(eng, vie);
                    break;
                case 3:
                    System.out.print("Từ cần xóa: ");
                    String remove = scanner.nextLine();
                    dictionary.removeWord(remove);
                    break;
                case 4:
                    dictionary.displayAll();
                    break;
                case 5:
                    System.out.println("Số từ: " + dictionary.countWords());
                    break;
                case 0:
                    System.out.println("Tạm biệt!");
                    return;
            }
        }
    }
}
```

## HashSet

HashSet là implementation của Set interface, không chứa phần tử trùng lặp và không có thứ tự.

### Khai báo và Sử dụng

```java
import java.util.HashSet;

public class HashSetDemo {
    public static void main(String[] args) {
        HashSet<String> fruits = new HashSet<>();
        
        // Thêm phần tử - add()
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Orange");
        fruits.add("Apple");  // Không thêm được vì đã có
        
        System.out.println("HashSet: " + fruits);
        // Thứ tự không được đảm bảo!
        
        // Kiểm tra phần tử - contains()
        boolean hasApple = fruits.contains("Apple");
        System.out.println("Có Apple? " + hasApple);
        
        // Xóa phần tử - remove()
        fruits.remove("Banana");
        System.out.println("Sau khi xóa: " + fruits);
        
        // Kích thước - size()
        System.out.println("Kích thước: " + fruits.size());
        
        // Kiểm tra rỗng - isEmpty()
        System.out.println("Rỗng? " + fruits.isEmpty());
        
        // Xóa tất cả - clear()
        fruits.clear();
    }
}
```

### Duyệt HashSet

```java
import java.util.HashSet;
import java.util.Iterator;

public class HashSetIteration {
    public static void main(String[] args) {
        HashSet<Integer> numbers = new HashSet<>();
        numbers.add(5);
        numbers.add(2);
        numbers.add(8);
        numbers.add(1);
        numbers.add(9);
        
        // Cách 1: For-each
        System.out.println("For-each:");
        for (Integer num : numbers) {
            System.out.println(num);
        }
        
        // Cách 2: Iterator
        System.out.println("\nIterator:");
        Iterator<Integer> iterator = numbers.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
        
        // Cách 3: forEach Lambda
        System.out.println("\nLambda:");
        numbers.forEach(num -> System.out.println(num));
        
        // Cách 4: Stream (Java 8+)
        System.out.println("\nStream:");
        numbers.stream().forEach(System.out::println);
    }
}
```

### Các Thao Tác Set

```java
import java.util.HashSet;

public class SetOperations {
    public static void main(String[] args) {
        HashSet<Integer> set1 = new HashSet<>();
        set1.add(1);
        set1.add(2);
        set1.add(3);
        set1.add(4);
        
        HashSet<Integer> set2 = new HashSet<>();
        set2.add(3);
        set2.add(4);
        set2.add(5);
        set2.add(6);
        
        System.out.println("Set 1: " + set1);
        System.out.println("Set 2: " + set2);
        
        // Hợp (Union) - addAll()
        HashSet<Integer> union = new HashSet<>(set1);
        union.addAll(set2);
        System.out.println("Hợp: " + union);
        
        // Giao (Intersection) - retainAll()
        HashSet<Integer> intersection = new HashSet<>(set1);
        intersection.retainAll(set2);
        System.out.println("Giao: " + intersection);
        
        // Hiệu (Difference) - removeAll()
        HashSet<Integer> difference = new HashSet<>(set1);
        difference.removeAll(set2);
        System.out.println("Hiệu (Set1 - Set2): " + difference);
    }
}
```

### Ví dụ Thực Tế: Loại Bỏ Trùng Lặp

```java
import java.util.ArrayList;
import java.util.HashSet;

public class RemoveDuplicates {
    public static void main(String[] args) {
        // ArrayList có phần tử trùng lặp
        ArrayList<String> listWithDups = new ArrayList<>();
        listWithDups.add("Java");
        listWithDups.add("Python");
        listWithDups.add("Java");
        listWithDups.add("C++");
        listWithDups.add("Python");
        listWithDups.add("JavaScript");
        
        System.out.println("Có trùng lặp: " + listWithDups);
        
        // Loại bỏ trùng lặp bằng HashSet
        HashSet<String> uniqueSet = new HashSet<>(listWithDups);
        System.out.println("Không trùng lặp: " + uniqueSet);
        
        // Chuyển lại thành ArrayList
        ArrayList<String> uniqueList = new ArrayList<>(uniqueSet);
        System.out.println("ArrayList unique: " + uniqueList);
    }
}
```

## LinkedHashMap và TreeMap

### LinkedHashMap - Duy trì thứ tự insertion

```java
import java.util.LinkedHashMap;

public class LinkedHashMapDemo {
    public static void main(String[] args) {
        LinkedHashMap<String, Integer> linkedMap = new LinkedHashMap<>();
        
        linkedMap.put("One", 1);
        linkedMap.put("Two", 2);
        linkedMap.put("Three", 3);
        linkedMap.put("Four", 4);
        
        // Duy trì thứ tự thêm vào
        System.out.println(linkedMap);
        // {One=1, Two=2, Three=3, Four=4}
    }
}
```

### TreeMap - Sắp xếp theo key

```java
import java.util.TreeMap;

public class TreeMapDemo {
    public static void main(String[] args) {
        TreeMap<String, Integer> treeMap = new TreeMap<>();
        
        treeMap.put("Charlie", 30);
        treeMap.put("Alice", 25);
        treeMap.put("Bob", 35);
        treeMap.put("David", 28);
        
        // Tự động sắp xếp theo key
        System.out.println(treeMap);
        // {Alice=25, Bob=35, Charlie=30, David=28}
        
        // Các phương thức đặc biệt
        System.out.println("First key: " + treeMap.firstKey());
        System.out.println("Last key: " + treeMap.lastKey());
        System.out.println("Lower key than Charlie: " + treeMap.lowerKey("Charlie"));
    }
}
```

## Ví dụ Thực Tế: Đếm Tần Suất Từ

```java
import java.util.HashMap;
import java.util.Map;

public class WordFrequency {
    public static void main(String[] args) {
        String text = "java is great and java is fun java programming is awesome";
        
        // Tách từ
        String[] words = text.toLowerCase().split("\\s+");
        
        // Đếm tần suất
        HashMap<String, Integer> wordCount = new HashMap<>();
        
        for (String word : words) {
            wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);
        }
        
        // Hiển thị kết quả
        System.out.println("Tần suất xuất hiện:");
        wordCount.forEach((word, count) -> {
            System.out.println(word + ": " + count);
        });
        
        // Tìm từ xuất hiện nhiều nhất
        String mostFrequent = null;
        int maxCount = 0;
        
        for (Map.Entry<String, Integer> entry : wordCount.entrySet()) {
            if (entry.getValue() > maxCount) {
                maxCount = entry.getValue();
                mostFrequent = entry.getKey();
            }
        }
        
        System.out.println("\nTừ xuất hiện nhiều nhất: " + mostFrequent + " (" + maxCount + " lần)");
    }
}
```

## So Sánh Map và Set

| Collection | Đặc điểm | Sử dụng khi |
|------------|----------|-------------|
| HashMap | Key-value, không thứ tự | Cần tra cứu nhanh theo key |
| LinkedHashMap | Key-value, có thứ tự insertion | Cần duy trì thứ tự thêm vào |
| TreeMap | Key-value, sắp xếp theo key | Cần dữ liệu được sắp xếp |
| HashSet | Không trùng lặp, không thứ tự | Loại bỏ duplicate, kiểm tra tồn tại nhanh |
| LinkedHashSet | Không trùng lặp, có thứ tự | Cần unique và duy trì thứ tự |
| TreeSet | Không trùng lặp, sắp xếp | Cần unique và được sắp xếp |

## Bài Tập Thực Hành

1. Viết chương trình quản lý danh bạ điện thoại sử dụng HashMap (tên -> số điện thoại)
2. Tạo hệ thống quản lý kho hàng với HashMap (mã sản phẩm -> số lượng)
3. Viết chương trình tìm các ký tự duy nhất trong một chuỗi sử dụng HashSet
4. Xây dựng shopping cart với HashMap (sản phẩm -> số lượng)
5.