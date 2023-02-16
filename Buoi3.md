# JAVA - Buổi 3

## 1. Mô hình MVC

**MVC** là viết tắt của cụm từ ***“Model-View-Controller“***. Đây là mô hình thiết kế được sử dụng trong kỹ thuật phần mềm. **MVC** là một mẫu kiến trúc phần mềm để tạo lập giao diện người dùng trên máy tính. MVC chia thành ba phần được kết nối với nhau và mỗi thành phần đều có một nhiệm vụ riêng của nó và độc lập với các thành phần khác. Tên gọi 3 thành phần:

- **Model (dữ liệu)**: Quản lí xử lí các dữ liệu.
- **View (giao diện)**: Nới hiển thị dữ liệu cho người dùng.
- **Controller (bộ điều khiển)**: Điều khiển sự tương tác của hai thành phần Model và View.

![](https://vietnix.vn/wp-content/uploads/2021/07/MVC.webp)

Cụ thể về chức năng các thành phần trong mô hình MVC như sau:

**Model**
- Có nhiệm vụ quản lý dữ liệu của ứng dụng
- Chứa tất cả các nghiệp vụ logic, đối tượng mô tả dữ liệu
- Thông báo cho view để hiện thị lại kết quả cho người dùng

**View**
- Chứa giao diện, tương tác với người dùng, sử dụng Model để hiển thị kết quả cho người dùng
- Đưa ra kết quả từ tầng Controller
- Thu nhận các hoạt động, yêu cầu của người dùng và chuyển cho tầng Controller xử lý

**Controller**
- Định nghĩa các hoạt động, xử lý của hệ thống
- Đối chiếu các hành động của người dùng từ View. Đồng thời tương tác Model để gọi View và hiển thị thông tin tương ứng cho người dùng.

> Ưu điểm của mô hình MVC là ứng dụng của bạn sẽ dễ nâng cấp và bảo trì do code của bạn được chia thành các thành phần độc lập. Tuy nhiên đối với những dự án nhỏ thì việc áp dụng mô hình MVC sẽ gây cồng kềnh, tốn thời gian trong quá trình phát triển.

## 2. Đọc ghi file trong Java

### 2.1. Đọc ghi file với Scanner

Như chúng ta đã biết, lớp `Scanner` có thể được sử dụng để nhập dữ liệu từ bàn phím, phân tích chuỗi ký tự, **nhập dữ liêu** từ file. Thao tác hoàn toàn giống với nhập dữ liệu từ bàn phím bình thường

Ví dụ:
```java
Scanner sc = new Scanner(new File("myNumbers.txt"));
while (sc.hasNextLong()) {
    long aLong = sc.nextLong();
}
```

### 2.2. Đọc ghi file với Byte Stream

Các chương trình sử dụng Byte Stream để đọc ghi dữ liệu theo từng **byte(8bit)**. Tất cả các class Byte Stream có nguồn gốc từ `InputStream` và `OutputStream`.

Có rất nhiều class Byte Stream, để hình dung Byte Stream hoạt động như thế nào, chúng ta sẽ tập trung vào `FileInputStream` và `FileOutputStream`, ví dụ:

```java
public class CopyFileByte {
    public static void main(String [] args) throws IOException {
      FileInputStream inputStream = null;
      FileOutputStream outputStream = null;
 
      try {
         inputStream = new FileInputStream("inStream.txt");
         outputStream = new FileOutputStream("outStream.txt");
         int c;
         while ((c = inputStream.read()) != -1) {
            outputStream.write(c);           
         }
      } finally {
         if (inputStream != null) inputStream.close();
         if (outputStream != null) outputStream.close();
      }
    }
}
```

### 2.3. Đọc ghi file với Character Stream

Character Stream trong Java được sử dụng để thực hiện input và output cho **Unicode 16 bit**. Tất cả các class Character Stream có nguồn gốc từ `Reader` và `Writer`.

Mặc dù có nhiều lớp liên quan tới Character Stream nhưng các lớp thường dùng nhất là `FileReader` và `FileWriter`, ví dụ:

```java
public class CopyFileCharacter {
    public static void main(String [] args) throws IOException {
      FileReader in = null;
      FileWriter out = null;
 
      try {
         in = new FileReader("input.txt");
         out = new FileWriter("output.txt");
         int c;
         while ((c = in.read()) != -1) {
            out.write(c);           
         }
      } finally {
         if (in != null) in.close();
         if (out != null) out.close();
      }         
    }    
}
```

### 2.4. Đọc ghi file với Buffered Stream

Các ví dụ trên không sử dụng Buffered Streams, điều này có nghĩa là việc đọc và xuất dữ liệu được thực hiện trực tiếp dưới quyền điều khiển của **hệ điều hành**, gây lãng phí thời gian và tài nguyên.

**Buffered Streams** được sử dụng để *tăng tốc độ hoạt độn*g I/O, bằng cách đơn giản là tạo ra một khoảng nhớ đệm với kích thước cụ thể nào đó. Vì vậy chúng ta không cần phải truy cập vào ổ đĩa cứng khi thực hiện I/O

Một chương trình có thể chuyển đổi từ sử dụng Byte Stream hoặc Chracter Stream sang sử dụng Buffered Stream bằng việc sử dụng ý tưởng ***"Wrapping"***

- Lớp Wrapper cho Byte Stream: `BufferedInputStream`, `BufferedOutputStream`
- Lớp Wrapper cho Character Stream: `BufferedReader`, `BufferedReader`

Ví dụ:

```java
public class CopyFileBuffer {
    public static void main(String [] args) throws IOException {
        BufferedReader bufferedReader = null;
        BufferedWriter bufferedWriter = null;
 
        try {
            Reader reader = new FileReader("input.txt");
            Writer writer = new FileWriter("output.txt");
 
            bufferedReader = new BufferedReader(reader);
            bufferedWriter = new BufferedWriter(writer);
    
            int c;                    
            while ((c = bufferedReader.read()) != -1) {
                bufferedWriter.write(c);
            }            
        } finally {
            if (bufferedReader != null) bufferedReader.close();
            if (bufferedWriter != null) bufferedWriter.close();  
        }         
    }    
}
```

