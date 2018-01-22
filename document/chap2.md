
## Khai báo biến

>Tham khảo bài gốc tại [đây](https://www.typescriptlang.org/docs/handbook/variable-declarations.html)

### Bài trước

[Kiểu dữ liệu cơ bản](document/chap1.md)

### Khai báo biến chung

`let` và `const` là hai biến mới được thêm trong Javascript. Như chúng tôi đã đề cập, `let` gần giống `var` nhưng nó giúp người dùng tránh được một số lỗi trong Javascript. `const` khác với `let` khi nó có thể ngăn cho một biến bị gán lại giá trị.

Typescript là tập cha của Javascript, bản thân ngôn ngữ này cũng hỗ trợ `let` và `const`. Chúng ta sẽ nghiên cứu kỹ hơn về cách khai báo biến và tại sao nó lại được sử dụng nhiều hơn so với `var`.

Nếu như bạn sử dụng Javascript không thật sự tốt, phần tiếp theo sẽ giúp bạn hệ thống lại kiến thức. Còn nếu như bạn đã quen với việc sử dụng
`var`, bạn sẽ cảm thấy nó khá là dễ dàng.

### khai báo `var`

Khai báo một biến trong Javascript theo cách truyền thống, chúng ta hay sử dụng từ khóa `var`

```javascript
var a = 10;
```

Bạn sẽ dễ dàng nhận thấy, chúng ta vừa khai báo một biến tên `a` với giá trị nhận vào là `10`.

Chúng ta cũng có thể khai báo biến bên trong một `function`

```javascript
function f(){
  var message = "Hello, world!";
  
  return message;
}
```

và chúng ta cũng có thể sử dụng biến vừa khai báo với một `function` khác:

```javascript
function f(){
  var a = 10;
  return function g(){
    var b = a + 1;
    return b;
  }
}

var g = f();
g(); // return '11'
```

Ở ví dụ phía dưới, `g` nhận lấy biến `a` được khai báo trong `f`. Mỗi khi `g` được gọi, giá trị của `a` sẽ được ràng buộc vào giá trị của biến `a` trong `f`. Ngay cả nếu `g` được gọi sau khi `f` đã chạy xong, nó vẫn có thể truy cập và chỉnh giá trị của biến `a`.

```javascript
functino f(){
  var a = 1;
  
  a = 2;
  var b = g();
  a = 3;
  
  return b;
  
  function g(){
    return a;
  }
}

f();// return '2'
```
### Phạm vi sử dụng

`var` có một số quy tắc khai báo khá dị. Bạn có thể tham khảo ví dụ dưới đây:

```javascript
function f(shouldInitialize: boolean){
  if(shouldInitialize){
    var x = 10;
    }
    
    return x;
}

f(true); // returns '10'
f(false); // return 'undefinded'
```

Biến `x` được khai báo bên trong điều kiện `if`, tất nhiên chúng ta có thể gọi nó bên ngoài điều kiện `if`. Bởi vì khai báo biến với `var` giúp chúng ta có thể gọi biến đó ở mọi nơi từ function, module, namespace, hay biến toàn cục - chúng ta sẽ đề cập sau.

Phạm vi biến có thể là nguyên nhân của nhiều loại lỗi. Khai báo môt biến nhiều lần có thể làm vấn đề thêm trầm trọng hơn:

```javascript
function sumMatrix(matrix: number[][]){
  var sum = 0;
  for(var i = 0; i < matrix.length; i++){
      var currentRow = matrix[i];
      for(var i = 0; i< currentRow.length; i++){
        sum += currentRow[i];
      }
  }
  
  return sum;
}
```

Có thể chúng ta dễ dàng nhận thấy rằng vòng `for` bên trong sẽ ghi đè biến `i` bởi vì biến `i` có phạm vi bên trong `function`. Khi bạn là một lập trình viên kinh nghiệm, một số lỗi tương tự sẽ khiến bạn rơi vào sự thất vọng đến vô cùng.

### Biến không minh bạch

Chúng ta hãy suy nghĩ về output của ví dụ dưới đây:

```javascript
for (var i = 0; i < 10; i++){
setTimeout(function () { console.log(i); }, 100 * i);
}
```

`setTimeout` sẽ khởi chạy một function sau một khoảng thời gian xác định.

Chúng tay hãy nhìn lại:

```javascript
10
10
10
10
10
10
10
10
10
10
```

Rất nhiều lập trình viên cảm thấy nó quen quen, nhưng bạn đừng ngạc nhiên, không chỉ mỗi bạn nghĩ như vậy. Rất nhiều người đoán rằng output sẽ nhứ thế này

```javascript
0
1
2
3
4
5
6
7
8
9
```

Như chúng ta đã đề cập về variable capturing. Mỗi khi chúng ta truyền `setTimeout` vào function thì biến i được lấy ngay trong cùng một phạm vi










