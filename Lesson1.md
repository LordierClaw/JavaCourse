# JAVA - Buổi 1

## 1. Syntax cơ bản

### 1.1. Nhập xuất trong Java

#### 1.1.1. Xuất dữ liệu

Để xuất dữ liệu ra màn hình chúng ta có 3 loại:

- `System.out.println("");` xuất kết quả ra màn hình và đưa con trỏ xuống dòng tiếp theo

- `System.out.print("");` xuất kết quả ra màn hình và con trỏ không xuống dòng

- `System.out.printf("");` xuất kết quả ra màn hình đồng thời có thể định dạng với các đối số thích hợp

Các bộ định dạng có sẵn trong `printf`

- `%c` : Ký tự
- `%d` : Số thập phân (số nguyên) (cơ số 10)
- `%e` : Dấu phẩy động theo cấp số nhân
- `%f` : Dấu phẩy động
- `%i` : Số nguyên (cơ sở 10)
- `%o` : Số bát phân (cơ sở 8)
- `%s` : Chuỗi
- `%u` : Số thập phân (số nguyên) không dấu
- `%x` : Số trong hệ thập lục phân (cơ sở 16)
- `%t` : Định dạng ngày / giờ
- `%%` : Dấu phần trăm
- `\%` : Dấu phần trăm

Ví dụ:

```java
String name = "ProPTIT";
int year = 2023;
System.out.printf("Happy new year %d!\nFrom %s with love!", year, name);
```

```
Happy new year 2023!
From ProPTIT with love!
```

#### 1.1.2. Nhập dữ liệu

Để nhập dữ liệu từ bàn phím trong Java, chúng ta sử dụng lớp `Scanner`, nằm trong gói `java.util`

Đầu tiên phải `import` thư viện vào: 
```java
import java.util.Scanner;
```
Sau đó ta gọi và khởi tạo đối tượng từ lớp `Scanner`:
```java
Scanner sc = new Scanner(System.in);
```
Khai báo 1 biến để lưu giá trị người dùng nhập vào, ví dụ:
```java
String name = sc.nextLine();
int age = sc.nextInt();
```
Ngoài ra, lớp `Scanner` còn cung cấp phương thức khác nhau cho chúng ta đọc đầu vào của các loại khác nhau: `next()`, `nextFloat()`, `nextBigInteger()`,...

#### 1.1.3. Lỗi trôi lệnh trong Java
Chúng ta cùng xét ví dụ sau:

```java
Scanner input = new Scanner(System.in);
String name = input.nextLine();
int age = input.nextInt();
String hometown = input.nextLine();
System.out.printf("Name: %s, Age: %d, Hometown: %s.", name, age, hometown);
```

Sau khi chạy thử, các bạn thấy trong quá trình nhập, chúng ta đã bị chường trình bỏ qua 1 phần nhập giá trị biến `hometown`. Đây là ví dụ về lỗi cơ bản, lỗi bị trôi lệnh.

**Vì sao lại trôi lệnh?**

Như qua ví dụ trên, trôi lệnh xảy ra khi chúng ta nhập một số sau đó nhập vào một chuỗi? Vậy có bạn nào đoán được vì sao lại trôi lệnh không? Đó là lý do khi các bạn nhập vào một số, sau đó nhấn **Enter** thì lúc này, `input.nextLine()` vì nó là trả về là một chuỗi kiểu `String` nên sẽ nhận giá trị là ***ký tự Enter***.

**Xử lý trôi lệnh khi dùng Scanner**

Chúng ta sẽ có 2 cách chính:
- Cách 1: Dùng `input.nextLine()` để nhận ký tự Enter
```java
String name = input.nextLine();
int age = input.nextInt(); input.nextLine();
String hometown = input.nextLine();
```
- Cách 2: Dùng `Integer.parseInt()` hoặc `Integer.valueOf()`
```java
String name = input.nextLine();
int age = Integer.parseInt(input.nextLine());
String hometown = input.nextLine();
```

### 1.2. Biến và kiểu dữ liệu

#### 1.2.1. Biến trong Java

Cú pháp khai báo biến:

```
DataType varName [ = value] [, varName2] [ = value2]...;
```
Trong đó, `DataType` là kiểu dữ liệu của biến, `varName` là tên biến, `value` là giá trị của biến nếu có

Có 3 loại biến trong Java:
- Biến local (biến cục bộ)
- Biến instance (biến toàn cục)
- Biến static

Ví dụ:
```java
public class Test {
    public static float PI = 3.14f;   // Đây là biến static
    int n;                            // Đây là biến instance
     
    public Test () {
        char c = 'c';                 // Đây là biến local
    }
}
```
#### 1.2.2. Kiểu dữ liệu trong Java

- Kiểu dữ liệu nguyên thủy: `byte`, `char`, `boolean`, `short`, `int`, `long`, `float`, `double`
- Kiểu dữ liệu đối tượng: `Array`, `class`, `interface`

### 1.3. Toán tử

Về cơ bản toán tử trong Java cũng giống với toán tử trong C, C++

- Toán tử số học: `+`, `-`, `*`, `/`, `%`,...
- Toán tử quan hệ: `==`, `!=`, `>`, `<`,...
- Toán tử logic: `&&`, `||`, `^`, `!`,...
- Toán tử bit: `&`, `|`,...

### 1.4. Mệnh đề điều kiện (If-else)

Nhìn chung, mệnh đề điều kiện trong Java cũng giống với C và C++
```java
if (condition1) {
    //do something
} else if (condition2) {
    
} else {
    
}
```

### 1.5. Vòng lặp

Nhìn chung, vòng lặp trong Java cũng giống với C và C++

Java hỗ trợ 3 loại vòng lặp khác nhau:
- Vòng lặp **for**
- Vòng lặp **while**
- Vòng lặp **do-while**

Vòng lặp **for** có 2 biến thể:
- Vòng lặp **for** thông thường
- Vòng lặp **for-each** (yêu cầu Java 5 trở lên)

Các lệnh có thể sử dụng trong vòng lặp:
- break
- continue

### 1.6. Mảng

#### 1.6.1. Khai báo mảng

Để khai báo một mảng, khai báo loại biến với dấu ngoặc vuông []:
```
dataType[] arr;
dataType []arr; 
dataType arr[]; 
```
Ngoài ra còn 1 số cách khác:
```java
// tạo một mảng có độ dài 4, giá trị mặc định là null hoặc 0
String[] cars1 = new String[4];
 
// tạo một mảng không cần chỉ định số phần tử cụ thể
String[] cars2 = new String[] { "Honda", "BMW", "Ford", "Mazda" };
 
// tạo một mảng không cần chỉ định số phần tử cụ thể và không cần dùng từ khóa new
String[] cars3 = { "Honda", "BMW", "Ford", "Mazda" };
```

#### 1.6.2. Độ dài của mảng

Để biết có bao nhiêu phần tử một mảng, sử dụng thuộc tính `length`

```java
String[] cars = { "Honda", "BMW", "Ford", "Mazda" };
System.out.println(cars.length);
```
Output:
```
4
```

#### 1.6.3. Lớp Arrays

Lớp `java.util.Arrays` trong java được sử dụng để thực hiện một số thao tác như sao chép, sắp xếp và tìm kiếm các phần tử trên các mảng

Một số phương thức hữu ích của lớp `Arrays`

|Phương thức|Công dụng|Sử dụng|
|---|---|---|
|**toString()**<br/>**deepToString()**|Trả về chuỗi của tất cả các phần tử của một mảng. Chuỗi này bao gồm tất cả các phần tử được bao quanh trong “**[ ]**”. Tất cả các phần tử được phân tách bằng dấu “**,**”|`Arrays.toString(a)`<br/>`Arrays.deepToString(b)`|
|**sort()**|Sử dụng QuickSort để sắp xếp các phần tử có kiểu nguyên thủy<br/>Sử dụng MergeSort để sắp xếp các phần tử có kiểu đối tượng|`Arrays.sort(a);`<br/>`Arrays.sort(a, 0, 9);`|
|**binarySearch()**|Tìm kiếm nhị phân với mảng đã được sắp xếp<br/>Nếu giá trị được tìm thấy trong mảng, nó trả lại giá trị index của phần tử trong mảng. Nếu không tìm thấy nó trả về giá trị âm là `(-n-1)`. Trong đó, `n` được gọi là *điểm chèn (insertion)*.<br/> **Điểm insertion** là điểm mà ở đó giá trị tìm kiếm sẽ được chèn vào mảng được sắp xếp. Chẳng hạn, nó sẽ là index của ***phần tử đầu tiên lớn hơn*** giá trị tìm kiếm, hoặc nó sẽ là độ dài của mảng nếu tất cả các phần tử của mảng nhỏ hơn giá trị tìm kiếm.|`Arrays.binarySearch(a, 5);`|
|**fill()**|Sử dụng để gán giá trị xác định cho mỗi phần tử của một mảng|`Arrays.fill(a, 10);`|
|**copyOf()**|Sử dụng để sao chép mảng được chỉ định vào mảng mới của cùng một kiểu|`int[] b = Arrays.copyOf(a, a.length)`|
|**copyOfRange()**|Sử dụng để sao chép một phần của một mảng vào mảng khác cùng kiểu|`int[] b = Arrays.copyOfRange(a, 3, 6)`|
|**equals()**<br/>**deepEquals()**|Sử dụng để so sánh hai mảng có bằng nhau hay không|`Arrays.equals(a, b)`<br/>`Arrays.deepEquals(c, d)`|

### 1.7. Lớp Wrapper

Lớp Wrapper trong java cung cấp cơ chế để chuyển đổi kiểu dữ liệu nguyên thủy thành kiểu đối tượng và từ đối tượng thành kiểu dữ liệu nguyên thủy.

Từ **J2SE 5.0**, tính năng **autoboxing** và **unboxing** chuyển đổi kiểu dữ liệu nguyên thủy thành kiểu đối tượng và ngược lại một cách tự động.

Có 8 lớp Wrapper trong gói **java.lang**
|Kiểu nguyên thủy|Kiểu Wrapper|
|--|--|
|boolean|Boolean|
|char|Character|
|byte|Byte|
|short|Short|
|int|Integer|
|long|Long|
|float|Float|
|double|Double|

Ví dụ:
```java
int a = 20;
Integer i = Integer.valueOf(a); //đổi int thành Integer
Integer j = a; //autoboxing, tự động đổi int thành Integer
```
```java
Integer a = new Integer(3);
int i = a.intValue(); //đổi Integer thành int
int j = a; //unboxing, tự động đổi Integer thành int
```

### 1.8. String trong Java

#### 1.8.1. Lớp String

String là **bất biến (immutable)** tức là không thể thay đổi. Có nghĩa là khi nào bạn thay đổi giá trị của bất kỳ chuỗi nào thì một instance mới được tạo ra. Đối với chuỗi có thể thay đổi, bạn có thể sử dụng các lớp **StringBuffer** và **StringBuilder**.

Khai báo:
```java
String s1 = "java"; //Tạo chuỗi bằng string literal  
char ch[] = { 's', 't', 'r', 'i', 'n', 'g', 's' };
String s2 = new String(ch); //convert mảng char thành chuỗi
String s3 = new String("example"); //Tạo chuỗi bằng từ khóa new 
```
Lớp String trong java cung cấp rất nhiều các phương thức để thực hiện các thao tác với chuỗi như: `compare()`, `concat()`, `equals()`, `split()`, `length()`, `replace()`, `compareTo()`, `intern()`, `substring()`,...

#### 1.8.2. Lớp StringBuffer

Lớp **StringBuffer** được sử dụng để tạo chuỗi có thể **thay đổi (mutable)**. Lớp StringBuffer trong java tương tự như lớp String ngoại trừ nó có thể thay đổi

Các phương thức của lớp StringBuffer:

1. **public synchronized StringBuffer append(String s)**: được sử dụng để nối thêm các chuỗi được chỉ định với chuỗi này. Các phương thức `append()` được nạp chồng như `append(char)`, `append(boolean)`, `append(int)`, `append(float)`, `append(double)`,...
2. **public synchronized StringBuffer insert(int offset, String s)**: được sử dụng để chèn chuỗi chỉ định với chuỗi này tại vị trí quy định. Các phương thức `insert()` được nạp chồng như `insert(int, char)`, `insert(int, boolean)`, `insert(int, int)`, `insert(int, float)`, `insert(int, double)`, ...
3. **public synchronized StringBuffer replace(int startIndex, int endIndex, String str)**: được sử dụng để thay thế chuỗi từ vị trị *startIndex* đến *endIndex* bằng chuỗi `str`.
4. **public synchronized StringBuffer delete(int startIndex, int endIndex)**: được sử dụng để xóa chuỗi từ vị trí *startIndex* đến *endIndex*.
5. **public synchronized StringBuffer reverse()**: được sử dụng để đảo ngược chuỗi.
6. **public int capacity()**: được sử dụng để trả về dung lượng hiện tại.
7. **public void ensureCapacity(int minimumCapacity)**: được sử dụng để đảm bảo dung lượng - ít nhất bằng mức tối thiểu nhất định.
8. **public char charAt(int index)**: được sử dụng trả về ký tự tại vị trí quy định.
9. **public int length()**: được sử dụng trả về chiều dài của chuỗi
10. **public String substring(int beginIndex)**: được sử dụng trả về chuỗi con bắt đầu từ vị trí được chỉ định.
11. **public String substring(int beginIndex, int endIndex)**: được sử dụng trả về chuỗi con với vị trí bắt đầu và vị trí kết thúc được chỉ định.

#### 1.8.3. Lớp StringBuilder

Lớp **StringBuilder** được sử dụng để tạo chuỗi có thể **thay đổi (mutable)**. Lớp StringBuilder trong java tương tự như lớp StringBuilder ngoại trừ nó **không đồng bộ (non-synchronized)**.

Các phương thức của lớp **StringBuilder** cũng giống với lớp **StringBufffer**

#### 1.8.4. So sánh String, StringBuffer, StringBuilder

|String|StringBuffer|
|--|--|
|Lớp String là bất biến (immutable)|Lớp StringBuffer là có thể sửa đổi (mutable)|
|Khi thực hiện nối nhiều chuỗi thì lớp String xử lý chậm và tốn nhiều bộ nhớ hơn, bởi vì mỗi lần nối thêm chuỗi nó tạo ra instance mới|Khi thực hiện nối nhiều chuỗi thì lớp StringBuffer xử lý nhanh và tốn ít bộ nhớ hơn|
|Lớp String ghi đề phương thức `equals()` của lớp Object. Vì thế ta có thể so sánh nội dung của 2 chuỗi bằng phương thức `equals()`|Lớp StringBuffer không ghi đề phương thức `equals()` của lớp Object.|

|StringBuffer|StringBuilder|
|--|--|
|StringBuffer là đồng bộ (synchronized) tức là luồng an toàn. Điều này có nghĩa là không thể có 2 luồng cùng truy cập phương thức của lớp StringBuffer đồng thời|StringBuilder là không đồng bộ (non-synchronized) tức là luồng không an toàn. Điều này có nghĩa là có 2 luồng cùng truy cập phương thức của lớp StringBuilder đồng thời|
|StringBuffer không hiệu quả bằng StringBuilder|StringBuilder hiệu quả hơn StringBuffer|

### 1.9. Lớp Maths

Trước khi gọi các hàm Math, bạn có thể import package để khỏi phải viết đầy đủ tên pack như sau:

```java
import java.lang.Math;
```

Các phương thức thường dùng: `Math.sqrt()`, `Math.abs()`, `Math.max()`, `Math.min`, `Math.random()`,...

Ngoài ra ta cũng có thể lấy giá trị Pi bằng: `Math.PI`

## 2. Regex - Regular Expression

### 2.1. Giới thiệu Regex

**Regular Expression (Biểu thức chính quy)** hay gọi tắt là **Regex** là một dãy các ký tự liên tục, qua nó giúp người sử dụng tìm kiếm hoăc so khớp hoặc các thao tác liên quan tuân theo những quy tắc và cú pháp nhất định.

### 2.2. Regex trong Java

#### 2.2.1. Gói java.util.regex

Gói `java.util.regex` cung cấp các lớp và giao diện cơ bản sau:
- Interface MatchResult
- Lớp Matcher
- Lớp Pattern
- Lớp PatternSyntaxException

Lớp Matcher và Pattern trong java cung cấp cơ sở của ***biểu thức chính quy***:

#### 2.2.2. Lớp Pattern

**Lớp Pattern** là một đối tượng mẫu được biên dịch từ một ***biểu thức chính quy***, không có constructor public. Chúng ta sử dụng method `compile()` để tạo đối tượng, với tham số là ***biểu thức chính quy***.

Các phương thức cơ bản

|Phương thức|Mô tả|
|---|---|
|static Pattern compile(String regex)|Biên dịch regex đã cho và trả về thể hiện của Pattern.|
|Matcher matcher(CharSequence input)|Tạo một matcher khớp với đầu vào đã cho với mẫu.|
|static boolean matches(String regex, CharSequence input)|Biên dịch biểu thức chính quy và tìm kiếm các chuỗi con từ chuỗi input phù hợp với mẫu regex.|
|String[] split(CharSequence input)|Chia chuỗi input đã cho thành mảng các kết quả trùng khớp với đầu vào.|
|String pattern()|Trả về mẫu regex.|

#### 2.2.3. Lớp Matcher

**Lớp Matcher** là một phương tiện để so khớp chuỗi dữ liệu đầu vào với đối tượng Pattern đã được tạo trước, không có constructor public. Chúng ta lấy đối tượng này thông qua method `matcher()` của đối tượng **Pattern** với tham số là ***đầu vào cần kiểm tra***.

Các phương thức cơ bản

|Phương thức|Mô tả|
|---|---|
|boolean matches()|	Kiểm tra xem biểu thức chính quy có khớp với mẫu hay không.|
|boolean find()|Tìm biểu thức tiếp theo khớp với mẫu.|
|boolean find(int start)|Tìm biểu thức tiếp theo khớp với mẫu từ chỉ số bắt đầu đã cho.|
|String group()|Trả về chuỗi con phù hợp.|
|int start()|Trả về vị trí bắt đầu của chuỗi con phù hợp.|
|int end()|Trả về vị trí kết thúc của chuỗi con phù hợp.|
|int groupCount()|Trả về tổng số các chuỗi con phù hợp.|

### 2.3. Quy tắc viết Regex

|Regex|Mô tả|
|:-:|---|
| . |So khớp với bất kỳ ký tự đơn nào |
| ^ | So khớp phần đầu của chuỗi hay dòng |
| $ | So khớp phần cuối của chuỗi hay dòng |
| (…) | So khớp với các ‘nhóm’ ký tự bên trong |
| […] | So khớp với bất kỳ ký tự đơn nào trong dấu ngoặc vuông |
| [^…] | So khớp với bất kỳ ký tự đơn nào ngoại trừ các ký tự trong dấu ngoặc vuông |
| [m-n] | So khớp từ ký tự m đến ký tự n theo thứ tự trong ASCII |
| XY | So khớp với ‘X theo sau là Y’, ví dụ: [a-e][i-u] |
| X &#124; Y | So khớp với X hoặc Y |
| \d | So khớp với ký tự là chữ số, viết tắt của [0-9] |
| \D | So khớp với ký tự không phải là chữ số, viết tắt của [^0-9] |
| \s | So khớp với bất kỳ ký tự trống nào (dấu cách, tab, xuống dòng), viết tắt của [\t\n\x0B\f\r] |
| \S | So khớp với bất kỳ ký tự không phải ký tự trống, viết tắt của [^\s] |
| \w | So khớp bất kỳ ký tự chữ nào (chữ cái và chữ số), viết tắt của [a-zA-Z0-9] |
| \W | So khớp bất kỳ ký tự nào không phải chữ cái và chữ số, viết tắt của [^\w] |
| \b | Ranh giới của một từ |
| \B | Không phải là ranh giới của một từ |
| \A | So khớp phần đầu của đầu vào |
| \G | So khớp phần cuối của đầu vào |
| X* | So khớp với 0 hoặc nhiều sự xuất hiện của X, viết gọn cho X{0,} |
| X+ | So khớp với 1 hoặc nhiều sự xuất hiện X,  viết gọn cho X{1,} |
| X? | So khớp 0 hoặc 1 sự xuất hiện của X, viết gọn cho X{0,1} |
| X{n} | So khớp chính xác n lần sự xuất hiện của X |
| X{n,} | So khớp n hoặc nhiều hơn số lần xuất hiện của X |
| X{n,m} | So khớp với ít nhất n và nhiều nhất m lần xuất hiện của X |

### 2.4. Ví dụ sử dụng Regex trong Java

#### 2.4.1. Sử dụng String.matches(String)

`String.matches(String)` được dùng để kiểm tra chuỗi đầu vào có phù hợp với biểu thức regex hay không. Đây là cách thông dụng nhất.

Ví dụ:

```java
String[] strTest = { "","1602","1998","NMD98","1998d","nmdse"};
// Kiểm tra xem chuỗi có chứa các chữ cái hay không
for(String str: strTest){
    System.out.println("'" +str + "' matches: "+ str.matches(".*[a-zA-Z].*"));
}
```
Output:
```
'' matches: false
'1602' matches: false
'1998' matches: false
'NMD98' matches: true
'1998d' matches: true
'nmdse' matches: true
```

#### 2.4.2. Sử dụng lớp Pattern, Matcher

Trước hết ta phải import 2 lớp Pattern và Matcher vào:

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;
```
```java
String strTest = "Abcxyz 31-01-2023, Lap Trinh PTIT 30/04/1975. Deadline 12_12_2012";
Pattern patternDate = Pattern.compile("\\d{2}[-|/]\\d{2}[-|/]\\d{4}");
Matcher matcher = patternDate.matcher(strTest);
    
System.out.println("Ngày tháng năm trong chuỗi đầu vào là:");
while(matcher.find()) {
    System.out.println(strTest.substring(matcher.start(), matcher.end()));
}
```
Output:
```
Ngày tháng năm trong chuỗi đầu vào là:
31-01-2023
30/04/1975
```

## 3. Class & Objects

### 3.1. Encapsulation

**Tính đóng gói** trong java là kỹ thuật ẩn giấu thông tin không liên quan và hiện thị ra thông liên quan. Mục đích chính của đóng gói trong java là giảm thiểu mức độ phức tạp phát triển phần mềm.

Ví dụ:

File: `Student.java`
```java
public class Student {
    private String name;
 
    public String getName() {
        return name;
    }
 
    public void setName(String name) {
        this.name = name;
    }
}
```
File: `Test.java`
```java
class Test {
    public static void main(String[] args) {
        Student s = new Student();
        s.setName("Hai");
        System.out.println(s.getName()); //output: Hai
    }
}
```

### 3.2. Inheritance

**Kế thừa trong java** là sự liên quan giữa hai class với nhau, trong đó có **class cha (superclass)** và **class con (subclass)**. Khi kế thừa class con được hưởng tất cả các phương thức và thuộc tính của class cha. Tuy nhiên, nó chỉ được truy cập các thành viên `public` và `protected` của class cha. Nó không được phép truy cập đến thành viên `private` của class cha.

Cú pháp: ta sử dụng từ khóa `extends` để kế thừa

```java
class Subclass extends Superclass {  
   //methods and fields
}
```

Trong java, **đa kế thừa** chỉ được hỗ trợ thông qua `interface`

### 3.3. Polymorphism

#### 3.3.1. Đa hình trong Java

**Đa hình trong java (Polymorphism)** là một khái niệm mà chúng ta có thể thực hiện một hành động bằng nhiều cách khác nhau.

Có hai kiểu của đa hình trong java, đó là đa hình lúc **biên dịch (compile)** và đa hình lúc **thực thi (runtime)**. Chúng ta có thể thực hiện đa hình trong java bằng cách ***nạp chồng phương thức*** và ***ghi đè phương thức***.

#### 3.3.2. Upcasting và Downcasting

- **Upcasting** là gán object của *subclass* cho biến tham chiếu *superclass*

- **Downcasting** là gán object của *superclass* cho biến tham chiếu *subclass*

Ví dụ: lớp `Orange` và lớp `Apple` cùng kế thừa lớp `Fruit`

Upcasting
```java
Fruit fruit = new Orange();
Fruit fruit1 = new Apple();
```
Downcasting
```java
Orange orange = (Orange)fruit;
```

### 3.4. Common Modifiers

Có hai loại **Common Modifiers** trong Java: đó là **Access Modifier** và **Non-access Modifier**

Có 4 loại Access Modifier:

||Trong lớp|Trong package|Ngoài package bởi lớp con|Ngoài package|
|--|--|--|--|--|
|Private|Yes|No|No|No|
|Default|Yes|Yes|No|No|
|Protected|Yes|Yes|Yes|No|
|Public|Yes|Yes|Yes|Yes|

Nếu không khai báo Modifier nào, thì mặc định là `Default`

### 3.5. Modifier static

`Từ khóa static` trong Java được sử dụng chính để quản lý bộ nhớ. Chúng ta có thể áp dụng từ khóa static với các biến, các phương thức, các khối, các lớp lồng nhau(nested class). 

Từ khóa static ***thuộc về lớp*** chứ không thuộc về instance(thể hiện) của lớp

Trong Java, Static có thể là:

- **Biến static**: Khi bạn khai báo một biến là static, thì biến đó được gọi là biến tĩnh, hay biến static.
- **Phương thức static**: Khi bạn khai báo một phương thức là static, thì phương thức đó gọi là phương thức static.
- **Khối static**: Được sử dụng để khởi tạo thành viên dữ liệu static.

Ta có hai cách để khởi tạo biến static.

**Cách thứ nhất:** khởi tạo ngay tại dòng khai báo biến
```java
private static int numOfCows = 0;
```
**Cách thứ hai:** Java cung cấp một cú pháp đặc biệt là **khối khởi tạo static** ***(static initialization block)*** – một khối mã được bọc trong cặp ngoặc { } và có tiêu đề là từ khóa `static`.
```java
static {
    numOfCows = 0;
}
```

Một lớp có thể có vài khối khởi tạo static đặt ở bất cứ đâu trong định nghĩa lớp. Chúng được đảm bảo sẽ được kích hoạt theo *đúng thứ tự xuất hiện* trong mã.

Và quan trọng bậc nhất là chúng được đảm bảo sẽ chạy trước khi bất gì biến thành viên nào được truy nhập hay phương thức static nào được chạy.

### 3.6. Interfaces

Một Interface trong Java là một **bản thiết kế** của một lớp. Nó chỉ có các phương thức trừu tượng.

Interface là một kỹ thuật để thu được tính trừu tượng hoàn toàn và đa kế thừa trong Java. Nó không thể được khởi tạo giống như lớp trừu tượng.

Nói cách khác, các trường của Interface là `public`, `static` và `final` theo mặc định và các phương thức là `public` và `abstract`

Một interface tương tự với một class bởi những điểm sau đây:

- Một interface được viết trong một file với định dạng .java, với tên của interface giống tên của file.
- Bytecode của interface được lưu trong file có định dạng .class.
- Khai báo interface trong một package, những file bytecode tương ứng cũng có cấu trúc thư mục có cùng tên package.

Một interface khác với một class ở một số điểm sau đây:

- Bạn không thể khởi tạo một interface.
- Một interface không chứa bất cứ hàm Contructor nào.
- Tất cả các phương thức của interface đều là abstract.
- Một interface không thể chứa một trường nào trừ các trường vừa static và final.
- Một interface không thể kế thừa từ lớp, nó được triển khai bởi một lớp.
- Một interface có thể kế thừa từ nhiều interface khác.

Ví dụ:

```java
interface Printable {  
    void print();  
}  
   
interface Showable{  
    void show();  
}  
   
class Test implements Printable, Showable {  
    public void print() {
        System.out.println("Hello");
    }  
    public void show() {
        System.out.println("Welcome");
    }  
   
    public static void main(String args[]){  
        Test obj = new Test();  
        obj.print();  
        obj.show();
    }  
}
```

### 3.7. Abstract Classes

Một lớp được khai báo với từ khóa `abstract` là **lớp abstract** trong Java. Lớp abstract có nghĩa là **lớp trừu tượng**, nó có thể có các phương thức `abstract` hoặc `non-abtract`.

Khai báo phương thức trừu tượng như sau:

```java
abstract void printStatus();
```

Ví dụ về lớp trừu tượng:


```java
abstract class Shape {  
    abstract void draw();  
}
class Rectangle extends Shape {  
    void draw() {
        System.out.println("draw rect");
    }
}
class Circle1 extends Shape {  
    void draw() {
        System.out.println("draw circle");
    }
}
class Test{  
    public static void main(String args[]) {  
        Shape s = new Circle1();
        s.draw();  
    }
}
```
Output:
```
Ve hinh tron
```