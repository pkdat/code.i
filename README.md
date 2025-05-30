Các mô hình ngôn ngữ lớn (LLM) ngày càng trở thành công cụ quan trọng giúp lập trình viên nâng cao hiệu suất làm việc. Theo xu hướng này, Samsung đã phát triển trợ lý lập trình code.i. Bài viết này sẽ so sánh Code.i với ChatGPT, nhằm đánh giá khả năng, ưu điểm và hạn chế của từng công cụ trong quá trình hỗ trợ lập trình.

## Một số thông tin cơ bản về Code.i

Code.i là trợ lý lập trình được học code liên quan đến các lĩnh vực sản phẩm của Samsung, hỗ trợ tạo code chuyên biệt phù hợp với nhu cầu của công ty. Các ngôn ngữ được hỗ trợ chính thức là C, C++, Java, Kotlin, Python, C# và Rust. Code.i được tích hợp trong VS Code, Visual Studio và các IDE của JetBrains. Khi người dùng viết code, Code.i sẽ tự động đưa ra các gợi ý để hoàn thành đoạn code (autocomplete). Ngoài ra, Code.i cũng cung cấp tính năng chat để trả lời các câu hỏi của lập trình viên thông qua ngôn ngữ tự nhiên.

## So sánh ChatGPT và Code.i

### Test: Viết mã từ mô tả tự nhiên

Mục tiêu là: Kiểm tra khả năng hiểu yêu cầu bằng ngôn ngữ tự nhiên và chuyển nó thành mã nguồn **đúng chức năng**, **đúng cú pháp**, **dễ hiểu**, và **tuân thủ quy ước lập trình**.

Promt 1: Write a Java method that takes a list of integers and returns a new list containing only the even numbers, sorted in ascending order.

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Collections;

public class EvenNumberFilter {
    
    public static List<Integer> getSortedEvenNumbers(List<Integer> numbers) {
        List<Integer> evenNumbers = new ArrayList<>();
        
        // Filter even numbers
        for (Integer num : numbers) {
            if (num % 2 == 0) {
                evenNumbers.add(num);
            }
        }

        // Sort in ascending order
        Collections.sort(evenNumbers);
        
        return evenNumbers;
    }
}
```

Promt 2: Create a Java class called Rectangle with two fields: width and height. Include methods to calculate the area and perimeter.

```java
public class Rectangle {
    private double width;
    private double height;

    // Constructor
    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    // Method to calculate area
    public double getArea() {
        return width * height;
    }

    // Method to calculate perimeter
    public double getPerimeter() {
        return 2 * (width + height);
    }

    // Getters
    public double getWidth() {
        return width;
    }

    public double getHeight() {
        return height;
    }

    // Setters
    public void setWidth(double width) {
        this.width = width;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    // Main method for testing
    public static void main(String[] args) {
        Rectangle rect = new Rectangle(5, 3);
        System.out.println("Area: " + rect.getArea());
        System.out.println("Perimeter: " + rect.getPerimeter());
    }
}
```

Nhận xét: 


Promt 3: **Write a Java function that rearranges a list of items (tuples) where each item has a type (like 'a', 'b', 'c', etc.) and a value (like a number).**
The input list is ordered, and the goal is to **interleave items from different types** in the order they first appear. Within each type, the order of the items must be preserved.

```java
import java.util.*;

class Item {
    String key;
    int value;

    Item(String key, int value) {
        this.key = key;
        this.value = value;
    }

    public String toString() {
        return "(" + key + ", " + value + ")";
    }
}

public class InterleaveItems {
    public static List<Item> interleave(List<Item> input) {
        // Bước 1: Gom nhóm theo key
        Map<String, Queue<Item>> groups = new LinkedHashMap<>();
        for (Item item : input) {
            groups.computeIfAbsent(item.key, k -> new LinkedList<>()).add(item);
        }

        List<Item> result = new ArrayList<>();
        boolean done;

        // Bước 2: Vòng lặp trộn dữ liệu
        do {
            done = true;
            for (Queue<Item> queue : groups.values()) {
                if (!queue.isEmpty()) {
                    result.add(queue.poll());
                    done = false;
                }
            }
        } while (!done);

        return result;
    }

    public static void main(String[] args) {
        List<Item> input = Arrays.asList(
            new Item("a", 1), new Item("a", 5), new Item("a", 3),
            new Item("b", 3),
            new Item("c", 2), new Item("c", 4), new Item("c", 1), new Item("c", 6)
        );

        List<Item> output = interleave(input);
        System.out.println(output);
    }
}
```

Nhận xét: code i lâu hơn



### Test: Giải thích đoạn mã


### Hiểu và sửa lỗi build/test (CI/CD, unit test)
