## Hàm built-in function
1. alert
2. console
3. confirm
4. prompt 
5. setTimeOut 
6. setInterval 
## Làm việc với chuỗi
> keywork: javascript string methods
1. length 
2. findIndex 
3. Cut String
4. Replace 
5. toUpperCase 
6. toLowerCase
8. split 
9. Get a character by index
## Làm việc với số 
1. Tạo giá trị number 
2. Làm việc với number 
   a. toString
   b. toFixed 
## Làm việc với mảng 
1. toString
2. join
3. pop
4. push
5. shift
6. unShift
7. splice
8. concat
9. slice
## Hàm (function)
1. Hàm? 
- Mội khổi mã <br/>
- Làm một việc cụ thể 
2. Loại hàm.
- Built-in <br/>
- Tự định nghĩa <br/>
3. Tính chât 
- Không thực thi khi định nghĩa.
- Sẽ thực thi khi được gọi. 
- Có thể nhận tham số.
- Có thể trả về 1 giá trị.
4. Hiểu hơn về function
- Khi đặt trùng tên function<br/>
    Thực thi hàm được khai báo cùng tên cuối cùng, các hàm phía trên sẽ bỏ qua.
- Khai báo biến trong hàm.
- Có thể định nghĩa hàm trong hàm.
5. Các loại function 
- Declaration function.
  + Bắt buộc đặt tên.
  + Có thể gọi được trước khi được định nghĩa.
  ```javascript
  demo();
  function demo() {
    logic
  }
  ```
- Expression function 
  + Được gán vào 1 biến.
  + Có thể đặt tên hoặc không. Đặt tên chỉ phục vụ mục đích dễ hiểu.
  + Không thể gọi khi chưa được định nghĩa 
    
  ```javascript
  const demo = function() {
    logic
  }
  demo();
  ```
- Arrow function
  ```javascript
   () => {
    logic
   }
  ```
## Polyfill
```javascript
    if(!String.prototype.includes){
        String.prototype.includes = function(search, start){
            'use strict'
            if(search instanceof RegExp){
                throw TypeError('first argument must not be a RegExp')
            }
            if(start === undefined){start=0;}
            return this.indexOf(search, start) !== -1;
        }
    }
```
## Object 
1. contructer
```javascript
    function User(firstName, lastName, avt){
        this.fileName = firstName;
        this.lastName = lastName;
        this.avt = avt;
    }
    var author = new User('van', 'hai', 'avatar');
    var user = new User('van1', 'hai1', 'avatar1');
    console.log(author, user);
```
2. Object prototype
## Array
1. forEach 
   - Duyệt các phần tử trong mảng.
   - Không trả về giá trị.
2. every 
   - Duyệt các phần tử trong mảng các phần tử đều phải thỏa mãn điều kiện 
     nếu 1 phần tử trong mảng không thỏa mãn điều kiện sẽ trả về false.
   - Trả về giá trị boolean
4. some 
   - Duyệt các phần tử trong mản 1 phần tử trong mảng thỏa mãn điều kiện sẽ trả về true.
   - Trả về giá trị boolean
5. find
   - Trả về item tìm kiếm được
6. filter
   - Trả về danh sách item tìm kiếm được
7. map
   - Trả về mảng mới.
8. reduce
    - Lưu trữ các giá trị trong mảng
    - Trả về giá trị lưu trữ.

## Math object 
1. Math.PI 
2. Math.round 
3. Math.abs 
4. Math.ceil 
5. Math.floor 
6. Math.random 
7. Math.min 
8. Math.max 
## Callback 
- Là hàm được truyền qua đối số 
- Khi gọi hàm khác
## Recursion (Đệ quy);
- Một hàm đệ quy là một hàm gọi chính nó cho đến khi không thể gọi. 
  Kỹ thuật này được gọi là Đệ quy (Recursion).
  ```javascript
    // Hàm đệ quy
    function recurse() {
        // ...
        // Tự gọi lại chính nó
        recurse();
        // ...
    }
  ```
## HTML DOM - DOM API. 

> Document Object Model, 
> viết tắt là DOM, là một giao diện lập trình ứng dụng. Thông thường, 
> DOM có dạng một cây cấu trúc dữ liệu, được dùng để truy xuất các tài liệu dạng HTML và XML. 
> Mô hình DOM độc lập với hệ điều hành và dựa theo kỹ thuật lập trình hướng đối tượng để mô tả tài liệu
<h1 align="center">
  <img src="https://www.w3schools.com/js/pic_htmltree.gif"/><br/>
</h1>

- Element  `id, class, tag, css sellect, html collection`
- Attribute 
- Text 
1. DOM Attribute
2. DOM console
3. DOM document
4. DOM element

# Quick Links
