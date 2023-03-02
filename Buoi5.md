# JAVA - Buổi 5

## 1. Giới thiệu Java Swing

### 1.1. Java Swing là gì?

**Java Swing** là một phần của **Java Foundation Classes (JFC)** được sử dụng để tạo các ứng dụng window-based. Nó được xây dựng trên **API AWT (Abstract Windowing Toolkit)** và được viết *hoàn toàn bằng Java*.

Các thành phần Swing nhẹ hơn AWT và tuân theo *mô hình MVC*.

### 1.2. Phân cấp các lớp Java Swing

![](https://viettuts.vn/images/java-swing/phan-cap-cac-lop-java-swing.jpg)

### 1.3. Phương thức thường dùng của lớp Component

|Phương thức|Mô tả|
|--|--|
|public void add(Component c)|Thêm một thành phần vào thành phần khác.|
|public void setSize(int width, int height)|Thiết lập kích thước của thành phần.|
|public void setLayout(LayoutManager m)|Thiết lập trình quản lý bố cục (layout) cho thành phần.|
|public void setVisible(boolean b)|Thiết lập khả năng hiển thị của thành phần. Nó theo mặc định là false (ẩn)|

## 2. Các lớp trong Java Swing

### 2.1. Container

**Container** là thành phần chủ chốt trong các thành phần của *SWING GUI*. Một Container cung cấp một không gian, là nơi đặt một thành phần. Một **Container** trong *AWT* chính là một Component và nó có thêm khả năng để thêm các thành phần khác vào chính nó.

Khi xem xét về Container, bạn cần chú ý các điểm sau:

- Các lớp con của Container được gọi là Container. Một số ví dụ về các lớp con của Container là `JPanel`, `JFrame` và `JWindow`.
- Container chỉ có thể thêm Component vào chính nó.
- Một layout mặc định có mặt trong mỗi container. Layout này có thể bị ghi đè bởi sử dụng phương thức `setLayout()`.

### 2.2. Lớp JFrame

Lớp JFrame là một lớp kế thừa từ `java.awt.Frame` mà bổ sung các hỗ trợ cho cấu trúc thành phần `JFC/Swing`. 

Lớp JFrame này có các constructor sau:

- `JFrame()`: Xây dựng một Frame mới, ban đầu là **không nhìn thấy (invisible)**.
- `JFrame(GraphicsConfiguration gc)`: Tạo một Frame trong **GraphicsConfiguration** đã cho của một thiết bị màn hình và một **title trống**.
- `JFrame(String title)`: Tạo một Frame mới, ban đầu là **không nhìn thấy (invisible)** với title đã cho.
- `JFrame(String title, GraphicsConfiguration gc)`: Tạo một Frame với **title** đã cho và **GraphicsConfiguration** đã cho của một thiết bị màn hình.

Ví dụ: tạo 1 cửa sổ với title là *"Hello World"*, kích cỡ *320x240*


```java
import javax.swing.JFrame;
import javax.swing.WindowConstants;

public class JavaTest {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Hello World");
        frame.setSize(320, 240);
        frame.setVisible(true);
        frame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
}
```

Để đóng cửa sổ, ta sử dụng hàm `dispose()`

### 2.3. Lớp JTextField

Lớp JTextField trong Java Swing là một thành phần cho phép sửa đổi **một dòng text đơn**.

Lớp JTextField có các constructor sau:

- `JTextField()`: Xây dựng một TextField mới.
- `JTextField(Document doc, String text, int columns)`: Xây dựng một JTextField mới mà sử dụng mô hình lưu trữ text đã cho và số cột đã cho.
- `JTextField(int columns)`: Xây dựng một TextField mới và trống với số cột đã cho.
- `JTextField(String text)`: Xây dựng một TextField mới được khởi tạo với text đã cho.
- `JTextField(String text, int columns)`: Xây dựng một TextField mới được khởi tạo với text và các cột đã cho.

Lấy chuỗi trong JTextField ta sử dụng hàm `getText()`

### 2.4. Lớp JButton

Lớp JButton trong Java Swing được sử dụng để tạo một nút có thể **click**.

Thành phần này có **một label** và tạo **một sự kiện** (event) khi được nhấn. Bạn cũng có thể chèn ảnh vào button.

Lớp JButton có các constructor sau:
- `JButton()`: Tạo một button mà không thiết lập text hoặc icon.
- `JButton(Action a)`: Tạo một button tại đây các thuộc tính được nhận từ Action đã cung cấp.
- `JButton(Icon icon)`: Tạo một button với một icon.
- `JButton(String text)`: Tạo một button với text.
- `JButton(String text, Icon icon)`: Tạo một button với text ban đầu và một icon.

### 2.5. Lớp JPanel

Lớp JPanel là một container chung và gọn nhẹ, được sử dụng để chứa các phần tử khác.

Lớp JPanel bao gồm các constructor sau:
- `JPanel()`: Tạo một JPanel mới với một double buffer và một Flow Layout.
- `JPanel(boolean isDoubleBuffered)`: Tạo một JPanel mới với Flow Layout và trình đệm đã xác định.
- `JPanel(LayoutManager layout)`: Tạo một JPanel mới với Layout Manager đã cho
- `JPanel(LayoutManager layout, boolean isDoubleBuffered)`: Tạo một JPanel mới với Layout Manager đã cho và trình đệm đã xác định.

### 2.6. Lớp JMenu

Mỗi cửa sổ window có một thanh trình đơn (menu bar) được liên kết với nó. Thanh trình đơn này gồm các lựa chọn có sẵn tới người dùng cuối cùng. Các điều khiển Menu và MenuItem là lớp con của lớp MenuComponent.

Lớp JMenu trong Java biểu diễn thành phần pull-down menu mà được triển khai từ một thanh trình đơn.

Lớp JMenu bao gồm các constructor sau:
- `JMenu()`: Xây dựng một JMenu mới không có text.
- `JMenu(Action a)`: Xây dựng một menu có các thuộc tính được nhận từ Action đã cho.
- `JMenu(String s)`: Xây dựng một JMenu mới với chuỗi s đã cho (như là text của nó).
- `JMenu(String s, boolean b)`: Xây dựng một JMenu mới với chuỗi s đã cho (như là text của nó) và một giá trị boolean để xác định có hay không một tear-off menu.

### 2.7. Lớp JLabel

Lớp JLabel trong Java Swing có thể hiển thị hoặc text, hoặc hình ảnh hoặc cả hai. Các nội dung của Label được gán bởi thiết lập căn chỉnh ngang và dọc trong khu vực hiển thị của nó.

Theo mặc định, các label được căn chỉnh theo chiều dọc trong khu vực hiển thị.

Theo mặc định, text-only label là căn chỉnh theo cạnh, image-only label là căn chỉnh theo chiều ngang.

Lớp JLabel bao gồm các constructor sau:

- `JLabel()`: Tạo một instance của JLabel, không có hình ảnh, và với một chuỗi trống cho title.
- `JLabel(Icon image)`: Tạo một instance của JLabel với hình ảnh đã cho.
- `JLabel(Icon image, int horizontalAlignment)`: Tạo một instance của JLabel với hình ảnh và căn chỉnh ngang đã cho.
- `JLabel(String text)`: Tạo một instance của JLabel với text đã cho.
- `JLabel(String text, Icon icon, int horizontalAlignment)`: Tạo một instance của JLabel với text, hình ảnh, và căn chỉnh ngang đã cho.
- `JLabel(String text, int horizontalAlignment)`: Tạo một instance của JLabel với text và căn chỉnh ngang đã cho.

### 2.8. Lớp JComboBox
Lớp JComboBox trong Java Swing là một thành phần mà kết hợp một button, một trường có thể chỉnh sửa và một drop-down list. Tại một thời điểm chỉ có một item có thể được lựa chọn từ list.

Lớp JComboBox bao gồm các constructor sau:
- `JComboBox()`: Tạo một JComboBox với data model mặc định.
- `JComboBox(Object[] items)`: Tạo một JComboBox mà chứa các phần tử trong mảng đã cho.
- `JComboBox(Vector items)`: Tạo một JComboBox mà chứa các phần tử trong Vector đã cho.

Các phương thức được sử dụng phổ biến của lớp JComboBox:
|Phương thức|Mô tả|
|--|--|
|public void **addItem(Object anObject)**|Được sử dụng để thêm một item tới list|
|public void **removeItem(Object anObject)**|Được sử dụng để xóa một item từ list|
|public void **removeAllItems()**|Được sử dụng để xóa tất cả item từ list|
|public void **setEditable(boolean b)**|Được sử dụng để xác định xem có hay không JComboBox là editable|
|public void **addActionListener(ActionListener a)**|Được sử dụng để thêm ActionListener|
|public void **addItemListener(ItemListener i)**|Được sử dụng để thêm ItemListener|

### 2.9. Lớp JTable
Chi tiết về cách sử dụng (7 phần):
https://codersontrang.wordpress.com/2012/08/20/74/