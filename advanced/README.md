# IIFE - Immedately Invojed Function Expression
> Self-Invoking Function
### Content
1. IIFF trông như thế nào ?
2. Dùng dấu ; trước IIFE.
3. IIFE là hàm private.
4. Sử dụng IIFE khi nào ? Khi không muốn ảnh hưởng tới phạm vi bên ngoài.
5. Cách tạo ra 1 IIFE.
```
   (function(){
        logic
   })()   
```
```
   (function(){
        logic
   }())   
```

# Scope - Phạm vi
### Content
1. Các phạm vi.
   - Global - Toàn cầu
   - Code block - Khối mã: let, const
   - Local scope - Hàm: var, function
2. Khi gọi mỗi hàm luôn có 1 phạ vi mới được tạo ra.
3. Các hàm có thể truy cập các biến được khai báo trong phạ vi của nó và bên ngoài nó.
4. Cách thức 1 bến được truy cập.
   a. Biến toàn cầu?
   b. Biến trng code block & hàm? 
   c. Biến trong hàm được tham chiếu bởi 1 hàm?
# Closure 
Là một hàm có thể ghi nhớ nơi nó được tạo ra và truy cập được biến ở bên ngoài phạm vi của nó.
### Ứng dụng
   - viết code ngắn gọn hơn 
   - Biểu diễn, ứng dụng tính Private trong OOP 
## Lưu ý 
   - Biến được tham chiếu refer trong closure sẽ không được xóa khỏi bộ nhớ kho hàm thực thi 
   xong
   - Các khái niệm javascript nâng cao rất dễ gây nhầm lẫn.

#Hosting - Kéo lên / đưa lên 
Đưa các khai báo biến với var và khai báo hàm lên đầu phạm vi được khai báo 
## Hosting với `var`, `function` `decalaration`
   - Xem ví dụ sau:
   ```javascript
    console.log(age) //undefined 
    console.log(fullname) // ReferenceError: fullname is not defined 
    var age = 16
   ```
   - Xét ví dụ sau:
   ```javascript
    console.log(sum(6,9)) //15
    function sum(a,b){
        return a+b 
    };
   ```
> Lưu ý: Phần khai báo được đưa lên trên, phần gán không được đưa lên trên.
## Hosting với `let`, `const`
   - Xem ví dụ sau:
   ```javascript
    {
        sonsole.log(fullName); // ReferenceError: Cannot access fullName before initialization
        let fullName= 'vanhaiit'
    }   
   ```
> Lưu ý: Khai báo biến với 'let' và 'const' khi được hoisted không được tạo giá trị và đưa vào "Temporal Dead Zone"

# JavaScript Use Strict
Báo lỗi hoặc ngăn chặn khi sử dụng những đoạn code không an toàn hay dễ gây nhầm lẫn 
## Cách sử dụng 
   - Thêm 'use-strict' vào đầu file.js 
   - Thêm 'use-strict' vào ngay sau thẻ mở `<script>`
   - Thêm 'use-strict' vào đầu phạm vi hàm
## Đặc trưng
Không thể khai báo biến mà không sử dụng tử khóa `var`, `let`, `const`
   ```javascript
    fullName = 'Nguyên văn A ' // Tạo ra biến fullName ở phạm vi global 
    function test(){
        age = 18;
    }
    test();
    console.log(fullName)
    console.log(age)
   ```
   - Báo lỗi khi gán lại giá trị cho thuộc tính có writable: false 
   - Báo lỗi khi hàm có tham số trùng tên
   - Khao báo hàm trong code-block thì hàm sẽ thuộc phạm vi code block 
   - Không đặt tên biến tên hàm bằng từ khóa nhạy cảm của ngôn ngữ 
## Công dụng 
   - Tránh quên từ khóa khai báo biến 
   - Tránh trùng tên biến lẫn tới lỗi logic 
   - Sử dụng bộ nhớ hiệu quả vì tránh tạo biến Global 

# The JavaScript this Keyword
Từ khóa `this` trong javascript đề cập tới đối tượng mà nó thuộc về 
## Đặc tính 
   - Trọng 1 phương thức, `this` tham chiếu tới đối tượng truy cập phương thức (Đối tượng trước dấu .)
   - Đứng ngoài phương thức, this tham chiếu tới đối tượng global

## Lưu ý 
   - `this` trong hàm tạo đại diện cho đối tượng sẽ được tạo 
   - `this` trong một hàm là `undefined` khi ở `use-strict` 
   - Các phương thức `bind()`, `call()`, `apply()` có thể tham chiếu `this` tới đối tượng khác.
