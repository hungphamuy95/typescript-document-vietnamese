# Kiểu cơ bản

### Giới thiệu

Trong quá trình phát triển phần mềm chúng ta thường xuyên làm việc với các kiểu dữ liệu cơ bản như: số thực, chuỗi, structure, giá trị boolean.
Typescirpt cũng hỗ trợ các kiểu dữ liệu cơ bản trong javascript kèm theo đó là mở rộng thêm các kiểu khác giúp quá trình viết code thuận tiện hơn.

### Kiểu Boolean

Kiểu dữ liệu cơ bản nhất đặc tả hai giá trị true/false, dưới đây là cách mà Typescript và Javascript khởi tạo một biến ```boolean```.

```javascript
let isDone: boolean = false;
```

### Kiểu Number

Trong Javascript tất cả các kiểu number đều là số thực. Không chỉ có kiểu thập lục phân và thập phân, Typescript hỗ trợ cả nhị phân và bát phân
được giới thiệu trong ECMAScript 2015

```javascript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

### Kiểu String

Chúng ta đều biết khi làm việc với Javascript ở cả client và server thì đều cần đến dữ liệu dạng ký tự. Với các ngôn ngữ lập trình khác,
chúng ta dùng ```string``` để biểu diễn dữ liệu dưới dạng ký tự. Giống với Javascript, Typescript cũng sử dụng dấu nháy kép (") hoặc nháy đơn (')
xung quanh dữ liệu chuỗi.

```javascript
let color: string = "blue";
color = 'red';
```

Bạn cũng có thể sử dụng *template strings*, nó có thể kéo xuống nhiều dòng và nhúng các biểu thức. Chuỗi dữ liệu được bao quanh bởi dấu (`), biểu thức nhúng 
sẽ có dạng ```${ expr }```.

```javascript
let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${ fullName }.

I'll be ${ age + 1 } years old next month.`;
```
Chúng ta cũng có thể sử dụng để khai báo `sentences` như sau:

```javascript
let sentence: string = "Hello, my name is " + fullName + ".\n\n" +
    "I'll be " + (age + 1) + " years old next month.";
```
### Kiểu mảng

Giống như Javascript, chúng ta cũng có thể khai báo một mảng dữ liệu. Mảng có thể khai báo bằng hai cách. Trong cách đầu tiên, chúng ta sử dụng `[]` 
để đánh dấu biến là mảng giá trị:

```javascript
let list: number[] = [1,2,3];
```
Cách thứ hai là sử dụng mảng generic, `Array<elemType>` :

```javascript
let list: Array<number> = [1, 2, 3];
```

### Kiểu Tuple

Kiểu Tuple giúp chúng ta có thể mô tả một mảng gồm các phần tử đã biết trước, nhưng không cần phải chung một kiểu dữ liệu. Ví dụ như chúng ta muốn 
thể hiện một cặp giá trị gồm kiểu `string` và `number`:

```javascript
// Declare a tuple type
letx: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error
```

Khi ta muốn lấy một phần tử trong mảng khi đã biết được vị trí của nó:

```javascript
console.log(x[0].substr(1)); // OK
console.log(x[1].substr(1)); // Error, kiểu 'number' không có phương thức 'substr'
```

Lấy một phần tử không rõ chỉ mục, sử dụng kiểu thống nhất:

```javascript
x[3] = "world"; // OK, 'string' có thể gán thành 'string | number'
console.log(x[5].toString()); // OK, 'string' và 'number' đều có phương thức 'toString'
x[6] = true; // Error, kiểu 'boolean' không thể là 'string | number'
```

Kiểu thống nhất là một chủ để nâng cao sẽ được giới thiệu ở các chương sau.

### Kiểu Enum








