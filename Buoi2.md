# JAVA - Buổi 2

## 1. Lớp Collection

### 1.1. Collection và Collections

`Collections` trong java là một khuôn khổ cung cấp một kiến trúc để lưu trữ và thao tác tới nhóm các đối tượng. Tất cả các hoạt động mà bạn thực hiện trên một dữ liệu như tìm kiếm, phân loại, chèn, xóa,... có thể được thực hiện bởi **Java Collections**.

`Collection` trong java là **một root interface** trong hệ thống cấp bậc Collection. **Java Collection** cung cấp nhiều interface (*Set, List, Queue, Deque,...*) và các lớp (*ArrayList, Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet,*...)

![](https://viettuts.vn/images/java/java-collection/colection-vs-collections-trong-java.png)

### 1.2. Hệ thống cấp bậc Collection

Gói **java.util** chứa tất cả các lớp và interface của Collection

![](https://viettuts.vn/images/java/java-collection/he-thong-cap-bac-colection-trong-java.png)

### 1.3. Các phương thức của Iterator interface

Iterable interface chứa dữ liệu thành viên Iterator interface.

Giao tiếp Iterator cung cấp phương tiện để lặp đi lặp lại các thành phần từ đầu đến cuối của một collection.

|Phương thức|Mô tả|
|---|---|
|public boolean hasNext()|Nó trả về true nếu iterator còn phần tử kế tiếp phần tử đang duyệt|
|public object next()|Nó trả về phần tử hiện tại và di chuyển con trỏ trỏ tới phần tử tiếp theo|
|public void remove()|Nó loại bỏ phần tử cuối được trả về bởi Iterator. Nó hiếm khi được sử dụng|

### 1.4. Các phương thức của Collection interface

|Phương thức|Mô tả|
|---|---|
|public boolean add(Object element)|Được sử dụng để chèn một phần tử vào collection|
|public boolean addAll(Collection c)|Được sử dụng để chèn các phần tử collection được chỉ định vào collection gọi phương thức này|
|public boolean remove(Object element)|Được sử dụng để xóa phần tử từ collection|
|public boolean removeAll(Collection c)|Được sử dụng để xóa tất cả các phần tử của collection được chỉ định từ collection gọi phương thức này|
|public boolean retainAll(Collection c)|Được sử dụng để xóa tất cả các thành phần từ collection gọi phương thức này ngoại trừ collection được chỉ định|
|public int size()|Trả lại tổng số các phần tử trong collection|
|public void clear()|Loại bỏ tổng số của phần tử khỏi collection|
|public boolean contains(Object element)|Được sử dụng để tìm kiếm phần tử|
|public boolean containsAll(Collection c)|Được sử dụng để tìm kiếm collection được chỉ định trong collection|
|public Iterator iterator()|Trả về một iterator|
|public Object[] toArray()|Chuyển đổi collection thành mảng (array)|
|public boolean isEmpty()|Kiểm tra nếu collection trống|
|public boolean equals(Object element)|So sánh 2 collection|
|public int hashCode()|Trả về số hashcode của collection|


## 2. List và ArrayList

### 2.1. List interface

List là một interface trong java. Nó chứa các phương thức để chèn và xóa các phần tử dựa trên chỉ số **index**.

Khai báo của interface List trong Java:
```java
public interface List<E> extends Collection<E>
```

Các phương thức:

|Phương thức|Mô tả|
|---|---|
|void add(int index,Object element)|Nó được sử dụng để chèn các phần tử vào list tại chỉ số index|
|boolean addAll(int index,Collection c)|Nó được sử dụng để chèn tất cả các yếu tố của c vào danh sách tại chỉ số index|
|object get(int index)|Nó được sử dụng để trả về đối tượng được lưu trữ tại chỉ số index trong list|
|object set(int index,Object element)|Nó được sử dụng để gán phần tử cho vị trí được chỉ định index trong list|
|object remove(int index)|Nó được sử dụng để xóa các phần tử tại vị trí có chỉ số index và trả về phần tử đã xóa|
|ListIterator listIterator()|Nó được sử dụng để trả về một Iterator mà bắt đầu từ phần tử đầu tiên của list|
|ListIterator listIterator(int index)|Nó được sử dụng để trả về một Iterator mà phần tử bắt đầu từ chỉ số index chỉ định|

### 2.2. ListIterator

ListIterator là một interface được sử dụng để duyệt các phần tử của List trong java.

Khởi tạo:
```java
List<Student> list1 = new ArrayList<>();
List<Student> list2 = new Vector<>();
List<Student> list3 = new LinkedList<>();
```

Các phương thức của interface ListIterator trong Java

|Phương thức|Mô tả|
|--|--|
|boolean hasNext()|Phương pháp này trả về true nếu list interator có tồn tại phần tử kế tiếp phần tử hiện tại|
|Object next()|Phương thức này trả về phần tử kế tiếp trong danh sách và vị trí con trỏ tăng lên 1|
|boolean hasPrevious()|Phương pháp này trả về true nếu list interator có tồn tại phần tử kế sau phần tử hiện tại|
|Object previous()|Phương thức này trả về phần tử kế sau trong danh sách và vị trí con trỏ giảm đi 1|

### 2.3. Lớp ArrayList

Lớp ArrayList trong java là một lớp kế thừa lớp AbstractList và triển khai của List Interface nên nó sẽ có một vài đặc điểm và phương thức tương đồng với List. 

ArrayList được sử dụng như một mảng động để lưu trữ các phần tử.

Những đặc điểm của ArrayList:
- Lớp ArrayList trong java có thể chứa các phần tử trùng lặp.
- Lớp ArrayList duy trì thứ tự của phần tử được thêm vào.
- Lớp ArrayList là không đồng bộ (non-synchronized).
- Lớp ArrayList cho phép truy cập ngẫu nhiên vì nó lưu dữ liệu theo chỉ mục.
- Lớp ArrayList trong java, thao tác chậm vì cần nhiều sự dịch chuyển nếu bất kỳ phần tử nào bị xoá khỏi danh sách.

Khởi tạo ArrayList:
```java
ArrayList<String> list = new ArrayList<>();
```
Các phương thức trong ArrayList:

|Phương thức|Mô tả|
|---|---|
|boolean add(Object o)|Nó được sử dụng để nối thêm phần tử được chỉ định vào cuối một danh sách|
|void add(int index, Object element)|Nó được sử dụng để chèn phần tử element tại vị trí index vào danh sách|
|boolean addAll(Collection c)|Nó được sử dụng để nối tất cả các phần tử trong collection c vào cuối của danh sách, theo thứ tự chúng được trả về bởi bộ lặp iterator|
|boolean addAll(int index, Collection c)|Nó được sử dụng để chèn tất cả các phần tử trong collection c vào danh sách, bắt đầu từ vị trí index|
|void retainAll(Collection c)|Nó được sử dụng để xóa những phần tử không thuộc collection c ra khỏi danh sách|
|void removeAll(Collection c)|Nó được sử dụng để xóa những phần tử thuộc collection c ra khỏi danh sách|
|int indexOf(Object o)|Nó được sử dụng để trả về chỉ mục trong danh sách với sự xuất hiện đầu tiên của phần tử được chỉ định, hoặc -1 nếu danh sách không chứa phần tử này|
|int lastIndexOf(Object o)|Nó được sử dụng để trả về chỉ mục trong danh sách với sự xuất hiện cuối cùng của phần tử được chỉ định, hoặc -1 nếu danh sách không chứa phần tử này|
|Object[] toArray()|Nó được sử dụng để trả về một mảng chứa tất cả các phần tử trong danh sách này theo đúng thứ tự|
|Object[] toArray(Object[] a)|Nó được sử dụng để trả về một mảng chứa tất cả các phần tử trong danh sách này theo đúng thứ tự|
|Object clone()|Nó được sử dụng để trả về một bản sao của ArrayList|
|void clear()|Nó được sử dụng để xóa tất cả các phần tử từ danh sách này|
|void trimToSize()|Nó được sử dụng để cắt dung lượng của thể hiện ArrayList này là kích thước danh sách hiện tại|
|boolean contains(element)|Kết quả trả về là true nếu tìm thấy element trong danh sách, ngược lại trả về false|

### 2.4. So sánh List và ArrayList

Ta có 2 cách khai báo:

```java
List<Student> listOfStudents = new ArrayList<>(); // Cách 1
```
```java
ArrayList<Student> listOfStudents = new ArrayList<>(); // Cách 2
```

- Về mặt lý thuyết khai báo như **cách 1** hay **cách 2** thì nó đều tạo một đối tượng mà ta khai báo sau toán tử `new`, chỉ khác nhau là ở cái kiểu biến ta tham chiếu đến đối tượng đó
- Khai báo theo **cách 1** sẽ tận dụng được ***tính đa hình*** trong lập trình hướng đối tượng và làm cho chương trình của chúng ta linh hoạt hơn, dễ mở rộng hơn sau này. Nếu ta sử dụng **cách 2** sẽ phải xử lí nhiều hơn, vì thực tế mỗi cấu trúc dữ liệu sẽ phù hợp với một loại dữ liệu hoặc chạy đơn luồng hay đa luồng nên sẽ phải có các hàm trả về khác nhau

## 3. Lớp Collections

Lớp Collections trong java chỉ chứa các phương thức static để thao tác và trả về các collection. Nó kế thừa lớp Object.

### 3.1. Các phương thức hay dùng

|Phương thức|Mô tả|
|--|--|
|addAll(Collection<? super T> c, T... elements)|Nó được sử dụng để thêm tất cả các phần tử quy định vào bộ sưu tập được chỉ định|
|binarySearch(List<? extends T> list, T key, Comparator<? super T< c)|Nó được sử dụng để tìm kiếm danh sách được chỉ định cho đối tượng được chỉ định sử dụng thuật toán tìm kiếm nhị phân|
|reverse(List<?> list)|Nó được sử dụng để đảo ngược thứ tự của các phần tử trong danh sách được chỉ định|
|max(Collection<? extends T> coll, Comparator<? super T> comp)|Nó được sử dụng để trả về phần tử max của bộ sưu tập đã cho, theo thứ tự được sắp xếp bởi comparator được chỉ định|
|min(Collection<? extends T> coll)|Nó được sử dụng để trả về phần tử min của bộ sưu tập đã cho, theo thứ tự được sắp xếp bởi comparable được chỉ định|
|replaceAll(List list, T oldVal, T newVal)|Nó được sử dụng để thay thế tất cả các lần xuất hiện của một giá trị được chỉ định trong danh sách với một giá trị khác|
|sort(List<T> list, Comparator<? super T> c)|Sắp xếp danh sách được chỉ định theo thứ tự của bộ so sánh được chỉ định.
|fill(List<? super T> list, T obj)|Thay thế tất cả các phần tử của danh sách được chỉ định với phần tử được chỉ định|
|copy(List<? super T> dest, List<? extends T> src)|Sao chép tất cả các phần tử từ một danh sách này sang một danh sách khác|

### 3.2. Sort trong Collections

#### 3.2.1. Sort sử dụng Comparable

Lớp **String** và các lớp **Wrapper** được ***implements*** giao diện **Comparable**. Vì vậy nếu bạn lưu trữ các đối tượng của lớp String và Wrapper thì chúng đã là kiểu Comparable. Khi đó bạn có thể áp dụng phương thức `Collections.sort(List list)` mà không phải cài đặt gì thêm.

Còn đối với List của các đối tượng do người dùng tự định nghĩa thì bạn phải ***implements*** giao diện **Comparable** cho lớp của đối tượng đó.

Ví dụ ta có 1 lớp **Student** do người dùng tự định nghĩa:

Lớp **Student** implements giao diện `java.lang.Comparable` để cài đặt phương thức `compareTo()` được dùng để so sánh các đối tượng Student với nhau.

File: Student.java
```java
package com.mycompany.javatest;
public class Student implements Comparable<Student> {
    private String name;

    public Student() {
    }
 
    public Student(String name) {
        super();
        this.name = name;
    }
 
    public String getName() {
        return this.name;
    }
    
    @Override
    public int compareTo(Student student) {
        return this.name.compareTo(student.name);
    }
}
```
File: Test.java
```java
package com.mycompany.javatest;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        List<Student> list = new ArrayList<>();
        list.add(new Student("Hai"));
        list.add(new Student("Khoa"));
        list.add(new Student("Duy"));
        Collections.sort(list);
        for(Student x: list) {
            System.out.println(x.getName());
        }
    }
}
```
Output:
```
Duy
Hai
Khoa
```

### 3.2.2. Sort sử dụng Comparator

Ngoài cách trên, để thuận tiện trong việc sắp xếp theo nhiều kiểu khác nhau, ta có thể sử dụng Comparator. 

Cách làm: Tạo đối tượng nặc danh `java.util.Comparator` để cài đặt phương thức `compare()` được dùng để so sánh các đối tượng Student với nhau.

File: Student.java
```java
package com.mycompany.javatest;
public class Student {
    private String name;

    public Student() {
    }
 
    public Student(String name) {
        super();
        this.name = name;
    }
 
    public String getName() {
        return this.name;
    }
}
```
File: Test.java
```java
package com.mycompany.javatest;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        List<Student> list = new ArrayList<>();
        list.add(new Student("Hai"));
        list.add(new Student("Khoa"));
        list.add(new Student("Duy"));
        Collections.sort(list, new Comparator<Student>(){
            @Override
            public int compare(Student s1, Student s2) {
                return s1.getName().compareTo(s2.getName());
            }
        });
        for(Student x: list) {
            System.out.println(x.getName());
        }
    }
}
```
Output:
```
Duy
Hai
Khoa
```
Ngoài ra, ta có thể không cần import `java.util.Comparator` và rút gọn bằng **hàm lambda** như sau:
```java
Collections.sort(list, (Student s1, Student s2) -> s1.getName().compareTo(s2.getName()));
```