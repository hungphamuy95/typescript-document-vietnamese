# Kiểu dữ liệu cơ bản

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

'enum' là một tập hợp các kiểu dữ liệu trong Javascript rất hữu ích. Giống như C#, enum là một cách thể hiện một tập hợp các giá trị số học giúp chúng ta dễ hình dung.

```javascript
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```

Mặc định thì enum sẽ bắt đầu với chỉ mục `0`. Bạn có thể thay đổi nó bằng cách đặt giá trị cho một trong các phần tử. Ví dụ như ta có thể khai báo chỉ mục cho phần tử đầu tiên là `1` thay vì `0`:

```javascript
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;
```

Hoặc thay đổi tất cả giá trị của các phần tử:

```javascript
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Green;
```

Một đặc điểm khá hay của enum là bạn có thể lấy được tên của một giá trị trong enum. Ví dụ như ta muốn lấy một giá trị trong enum bằng 2 nhưng không biết tên nó là gì trong enum `Color`, ta có thể lấy tên chính xác bằng cách:

```javascript
enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];

alert(colorName); // Hiển thị 'Green' có giá trị bằng 2
```

### Kiểu Any

Trong trường hợp chúng ta muốn mô tả kiểu dữ liệu của một biến nhưng lại không biết nó sẽ được gọi ở đâu. Giá trị của biến lại linh hoạt, ví dụ như khi ta sử dụng các thư viện của bên thứ ba. Khi đó chúng ta có thể không cần kiểm tra kiểu dữ liệu và code sẽ không báo lỗi mỗi lần biên dịch. Để làm điều đó thì ta có thể đánh dấu một biến là kiểu `any`:

```javascript
let notSure: any = 4;
notSure = "có thể nó là một chuỗi";
notSure = false; // OK, chắc chắn nó là kiểu boolean
```

Kiểu `any` rất hữu dụng, nó giúp bạn bỏ qua việc kiểm tra dữ liệu mỗi khi biên dịch. Bạn có thể nghĩ rằng `Object` cũng làm được điều tương tự, giống với các ngôn ngữ khác. với `Object` thì ta không thể gán cho nó phương thức một cách tùy tiện, mặc dù phương thức đó có tồn tại:

```javascript  
let notSure: any = 4;
notSure.ifItExists(); // OK, ifItExists có thể được thông dịch
notSure.toFixed(); // OK, toFixed đã tồn tại ( có thể trình thông dịch chưa kiểm tra)

let preetySure: Object = 4;
preetySure.toFixed(); // Error: Property 'toFixed' doesn't exist on type 'Object'.
```

Kiểu `any` cũng rất tiện dụng khi bạn chỉ biết được một phần của dữ liệu. Ví dụ, bạn có một mảng là tập hợp của nhiều kiểu dữ liệu;

```javascript
let list: any[] = [1, true, "false"];

list [1] = 100;
```

### Kiểu Void

`void` có một chút giống như là trái ngược so với `any`: không có kiểu dữ liệu nào cả. Bạn có thể nhận thấy một function không trả về bất cứ giá trị nào:

```javascript
function warnUser(): void {
    alert("Đây là một tin cảnh báo");
}
```

Khai báo một biến có kiểu là void hoàn toàn vô dụng vì bạn chỉ có thể gán cho nó giá trị `undefined` hoặc `null`:

```javascript
let unusable: void = undefined;
```

### Kiểu Null và Undefined

Trong TypeScript, cả `undefined ` và `null` thật ra đều có kiểu riêng của nó. Giống như void, nó thật sự không hữu dụng:

```javascript
// Not much else we can assign to these variables!
let u: undefined = undefined;
let n: null = null;
```

Mặc định thì cả `null` và `undefined` đều là kiểu con của tất cả các kiểu khác. Điều đó có nghĩa là bạn có thể gán chúng cho một biến có kiểu giả dụ như `number`.

Tuy nhiên, khi sử dụng `--strictNullChecks`, `null` và `undefined` chỉ có thể gán cho các biến có giá trị là kiểu `void`. Điều này giúp chúng ta có thể tránh được khá nhiều *lỗi thường gặp*. Trong trường hợp chúng ta muốn truyền kiểu `string` hoặc `null` hoặc `undefinded`, bạn có thể sử dụng kiểu thống nhất `string | null | undefinded`. 
> Chú ý rằng: Chúng tôi khuyên bạn sử dụng `--strictNullChecks` khi có thể, nhưng trong các tutorial , chúng ta sẽ tắt nó.

### Kiểu Never

Kiểu `never` mô tả kiểu dữ liệu không bao giờ xảy ra. Ví dụ kiểu `never` mô tả một `function` hoặc biểu thức luôn luôn ném ra lỗi hoặc nó không bao giờ trả về dữ liệu. 

Kiểu `never` là kiểu con và có thể gán cho mọi kiểu khác; tuy nhiên *không* có kiểu dữ liệu nào là con hoặc có thể gán cho `never` ngoại trừ chính nó. Ngay cả `any` cũng không thể gán cho `never`.

Một số ví dụ dưới đây mô tả một `function` trả về `never`:

```javascript
// Function returning never must have unreachable end point
function error(message: string): never{
    throw new Error(message);
}

// Inferred return type is never
function fail(){
    return error("something failed");
}

// Function returning never must have unreachable end point
function infiniteLoop(): never{
    while(true){
    }
}
```

### Kiểu khẳng định

Đôi khi bạn sẽ gặp phải trường hợp mà kiểu dữ liệu của bạn nằm ngoài tầm hiểu biết của Typescript. Thường thì nó sẽ xảy ra khi một số entity đòi hỏi kiểu dữ liệu cụ thể hơn so với dữ liệu hiện tại.

Kiểu khẳng định có tác dụng như "tin tôi đi, tôi đang biết mình làm gì." Kiểu khẳng định giống như hành động ép kiểu giống đa phần ngôn ngữ khác nhưng không cần kiểm tra hay tái cấu trúc dữ liệu. Nó không ảnh hưởng gi đến quá trình runtime và được sử dụng bởi trình biên dịch. Typescript giả dụ rẳng lập trình viên đã tự kiểm tra kiểu dữ liệu.

Kiểu dữ liệu có thể sử dụng dưới hai dạng. Một trong số đó là "dấu ngoặc nhọn":

```javascript
let someValue: any = "This is a string";

let strLength: number = (<string>somaValue).length;
```

và cách còn lại là sử dụng từ khóa `as`:

```javascript
let someValue: any = "đây là một chuỗi";

let strLength: number = (someValue as string).length;
```

Hai cách ở trên hoàn toàn giống nhau. Chúng ta thường hay sử dụng cách đầu tiên hơn, tuy nhiên khi sử dụng Typescript với JSX thì chỉ có thể sử dụng `-as`.

### Chú ý nhỏ khi sử dụng let

Bạn cần chú ý rằng chúng ta sử dụng `let` thay thế cho `var` mặc dù bạn cảm thấy nó quen thuộc hơn. từ khóa `let` được tạo ra trong Javascipt nhờ có sự ảnh hưởng từ Typescript. Chúng ta sẽ nói về `let` và `var` sau, nhưng khá nhiều lỗi thường xảy ra khi sử dụng `let`, bạn nên sử dụng luân phiên cả `var` khi có thể.

### Chương sau
...Updating












