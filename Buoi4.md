# JAVA - Buổi 4

## 1. Package trong Java

### 1.1. Khái niệm

- Một package (gói) trong java là một nhóm các kiểu tương tự của các lớp, giao diện và các package con .

- Package trong java có thể được phân loại theo hai hình thức, package được dựng sẵn và package do người dùng định nghĩa.

![](https://viettuts.vn/images/java/package-trong-java-1.jpg)

Vậy tại sao lại nên sử dụng package?

- Package được sử dụng để phân loại lớp và interface giúp dễ dàng bảo trì.
- Package cung cấp bảo vể truy cập
- Package khắc phục được việc đặt trùng tên.

### 1.2. Biên dịch và chạy

Ví dụ ta có package tên là `proptit`, và file `Main.java` trong package đó:

Biên dịch:
```
javac -d . Main.java
```
Lệnh `-d` được sử dụng để xách định nơi lưu trữ file .class sau khi biên dịch. Nếu bạn muốn giữ các package này trong thư mục hiện tại ban sử dụng dấu chấm `.`

Chạy:
```
javac proptit.Main
```

### 1.3. Truy cập package

Có 3 cách để truy cập package từ package bên ngoài:

- Khai báo `import package.*;`
- Khai báo `import package.classname;`
- Sử dụng tên đầy đủ.

### 1.4. Subpackage

Package bên trong một package khác được gọi là **subpackage** hay **package con** trong java.

Ví dụ:

Sun Microsystem đã định nghĩa một gói có tên `java` chứa nhiều lớp như `System`, `String`, `Reader`, `Writer`, `Socket`,...

Các lớp này đại diện cho một nhóm cụ thể ví dụ như các lớp `Reader` và `Writer` cho các hoạt động **Input/Output**, `Socket` và `ServerSocket` các lớp **xử lý mạng**,..

Vì vậy, Sun đã phân loại lại gói `java` thành các gói phụ như `lang`, `net`, `io`,... Và đặt các lớp liên quan đến **Input/Output** trong gói `io`, các lớp **Server** và **ServerSocket** trong các gói `net`.


## 2. Exception trong Java

### 2.1. Exception là gì?

**Exception** (ngoại lệ) là một tình trạng bất thường.

Trong java, ngoại lệ là một sự kiện làm gián đoạn luồng bình thường của chương trình. Nó là một đối tượng được ném ra tại runtime.

**Exception Handling** (xử lý ngoại lệ) là một cơ chế xử lý các lỗi runtime như `ClassNotFound`, `IO`, `SQL`, `Remote`,...

![](https://topdev.vn/blog/wp-content/uploads/2021/01/exceptionhierarchy.png)

### 2.2. Các loại Exception

Có 3 loại ngoại lệ: **Checked Exception**, **Unchecked Exception**, **Error**

#### 2.2.1. Checked Exception
Các lớp extends từ lớp `Throwable` ngoại trừ `RuntimeException` và `Error` được gọi là **Checked Exception**, ví dụ như *Exception, IOException,..* 

Các **Checked Exception** được kiểm tra tại ***compile-time***.

#### 2.2.2. Unchecked Exception
Các lớp extends từ `RuntimeException` được gọi là **Unchecked Exception**, ví dụ: *ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException,...*

Các **Unchecked Exception** không được kiểm tra tại compile-time mà chúng được kiểm tra tại ***runtime***.

> Nếu một exception xảy ra mà người dùng có thể khắc phục được thì sử dụng checked exception, còn nếu một exception khi xảy ra mà người dùng không thể làm gì để khắc phục thì sử dụng unchecked exception

#### 2.2.3. Error

Error là lỗi không thể cứu chữa được. Ví dụ: *OutOfMemoryError, VirtualMachineError, AssertionError,...*

### 2.3. Các phương thức của lớp Exceptions

|Phương thức|Mô tả|
|--|--|
|public String **getMessage()**|Trả về một message cụ thể về exception đã xảy ra. Message này được khởi tạo bởi phương thức constructor của Throwable|
|public Throwable **getCause()**|Trả về nguyên nhân xảy ra exception biểu diễn bởi đối tượng Throwable|
|public String **toString()**|Trả về tên của lớp và kết hợp với kết quả từ phương thức getMessage()|
|public void **printStackTrace()**|In ra kết quả của phương thức toString() cùng với stack trace đến System.err|

## 3. Xử lý Exception

### 3.1. Khối lệnh try-catch

Khối lệnh `try` trong java được sử dụng để chứa một đoạn code có thế xảy ra một ngoại lệ. Nó phải được khai báo trong phương thức.

Sau một khối lệnh `try` bạn phải khai báo khối lệnh `catch` hoặc `finally` hoặc cả hai.

Cú pháp:

```java
try {  
    // code có thể ném ra ngoại lệ
} catch (Exception_class_Name ref) {
    // code xử lý ngoại lệ
} finally {
    // code trong khối này luôn được thực thi
}
```

Lưu ý: Bạn có thể sử dụng nhiều khối `catch` với một khối `try` duy nhất.

Quy tắc xử lý ngoại lệ:

- Vào một thời điểm chỉ xảy ra một ngoại lệ và tại một thời điểm chỉ có một khối catch được thực thi.
- Tất cả các khối catch phải được sắp xếp từ cụ thể nhất đến chung nhất, tức là phải khai báo khối lệnh catch để xử lý lỗi `ArithmeticException` trước khi khai báo catch để xử lý lỗi `Exception`.

Ví dụ về sử dụng khối lệnh try-catch:

```java
public class MainApp {
    public static void main(String args[]) {
        try {
            int data = 9 / 0;
        } catch (ArithmeticException e) {
            System.out.println(e);
        }
        System.out.println("continue...");
    }
}
```
Output:
```
java.lang.ArithmeticException: / by zero
continue...
```

### 3.2. Khối lệnh finally

Khối lệnh `finally` trong java được sử dụng để thực thi các lệnh quan trọng như **đóng kết nối**, **đóng cả stream**,...

Khối lệnh `finally` trong java **luôn được thực thi** cho dù có ngoại lệ xảy ra hay không hoặc gặp lệnh `return` trong khối `try`.

Quy tắc:

- Đối với mỗi khối `try`, có thể có không hoặc nhiều khối `catch`, nhưng chỉ có một khối `finally`.
- Khối `finally` sẽ không được thực thi nếu chương trình bị **thoát** (bằng cách gọi **System.exit()** hoặc xảy ra một lỗi không thể tránh khiến chương trình bị chết).

### 3.3. Từ khóa throw

Từ khoá `throw` trong java được sử dụng để ném ra một ngoại lệ cụ thể.

Chúng ta có thể ném một trong hai ngoại lệ **checked** hoặc **unchecked** trong java bằng từ khóa throw. Từ khóa throw chủ yếu được sử dụng để ném ngoại lệ tùy chỉnh (ngoại lệ do người dùng tự định nghĩa).

Cú pháp:

```java
throw exception;
```

Ví dụ:

```java
public class TestThrow2 {
    static void validate(int age) {
        try {
            if (age < 18)
                throw new ArithmeticException("not valid");
            else
                System.out.println("welcome");
        } catch (ArithmeticException ex) {
            System.out.println(ex.getMessage());
        }
    }
 
    public static void main(String args[]) {
        validate(13);
        System.out.println("rest of the code...");
    }
}
```
Output:
```
not valid
rest of the code...
```

### 3.4. Từ khóa throws

Từ khóa `throws` trong java được sử dụng để **khai báo** một ngoại lệ.

Nó thể hiện thông tin cho lập trình viên rằng có thể xảy ra một ngoại lệ, vì vậy nó là tốt hơn cho các lập trình viên để cung cấp các mã xử lý ngoại lệ để duy trì luồng bình thường của chương trình.

Cú pháp:
```java
return_type method_name() throws exception_class_name {  
    // method code
}
```
Ví dụ:
```java
import java.io.IOException;
 
public class TestThrows1 {
    void m() throws IOException {
        throw new IOException("Loi thiet bi");// checked exception
    }
 
    void n() throws IOException {
        m();
    }
 
    void p() {
        try {
            n();
        } catch (Exception e) {
            System.out.println("ngoai le duoc xu ly");
        }
    }
 
    public static void main(String args[]) {
        TestThrows1 obj = new TestThrows1();
        obj.p();
        System.out.println("luong binh thuong...");
    }
}
```
Output:
```
ngoai le duoc xu ly
luong binh thuong...
```

### 3.5. So sánh throw và throws

|throw|throws|
|--|--|
|Từ khóa throw trong java được sử dụng để ném ra một ngoại lệ rõ ràng.|Từ khóa throws trong java được sử dụng để khai báo một ngoại lệ.|
|Ngoại lệ checked không được truyền ra nếu chỉ sử dụng từ khóa throw.|Ngoại lệ checked được truyền ra ngay cả khi chỉ sử dụng từ khóa throws.|
|Sau throw là một instance.|Sau throws là một hoặc nhiều class.|
|Throw được sử dụng trong phương thức.|Throws được khai báo ngay sau dấu đóng ngoặc đơn của phương thức.|
|Bạn không thể throw nhiều exceptions.|Bạn có thể khai báo nhiều exceptions.|

> Lưu ý: Trong overriding phương thức, nếu phương thức của lớp cha không khai báo ném ra `exception`, phương thức được ghi đè của lớp cha không thể khai báo ném ra **ngoại lệ checked**, nhưng **ngoại lệ unchecked** thì có thể.

## 4. Custom Exception

### 4.1. Tùy chỉnh Checked Exception

Chúng ta có thể khai báo 1 class mới và extends `Exception` để trở thành 1 ngoại lệ checked

```java
public class CustomCheckedException extends Exception { 
    public CustomCheckedException(String errorMessage) {
        super(errorMessage);
    }

    public CustomCheckedException(String errorMessage, Throwable err) {
        super(errorMessage, err);
    }
}
```

### 4.2. Tùy chỉnh Unchecked Exception

Chúng ta có thể khai báo 1 class mới và extends `RuntimeException` để trở thành 1 ngoại lệ unchecked

```java
public class CustomUncheckedException extends RuntimeException {
    public IncorrectFileExtensionException(String errorMessage, Throwable err) {
        super(errorMessage, err);
    }
}
```