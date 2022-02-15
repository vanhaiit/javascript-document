# Fundamental Topics
## JSX Components
JSX produces React “elements”.
We will explore rendering them to the DOM in the next section
## Props, State
### Props
Props and State là hai kiểu dữ liệu được control như một component
- Props thực chất là viết tắt của Properties
- Props có thể đến từ parent, hoặc có thể được thiết lập bởi chính component đó.
    + Đến từ parent: 
    ```javascript
    function Welcome(props) {
    return <h1>Hello {props.name}</h1>;
    }
    ```
    + Thiết lập bởi chính nó:
    ```javascript
    class Welcome extends React.Component {
    render() {
      return <h1>Hello {this.props.name}</h1>;
    }
    }
    
    Welcome.defaultProps = {
    name: "world",
    };
    ```
### State
Giống như props, sate cũng giữ thông tin về component.
Tuy nhiên, loại thông tin và cách xử lý nó khác nhau. 
State hoạt động khác với Props. 
State là thành phần của component, 
trong khi các props lại được truyền giá trị từ bên ngoài vào component 
Có một lưu ý nhỏ là chúng ta không nên 
cập nhật state bằng cách sử dụng trực tiếp this.state mà luôn sử dụng 
setState để cập nhật state của các đối tượng. Sử dụng setState để re-renders 
một component và tất cả các component con. 
Điều này thật tuyệt, bởi vì bạn không phải lo lắng về việc viết 
các xử lý sự kiện (event handler) như các ngôn ngữ khác.
```javascript
    class Form extends React.Component {
      constructor (props) {
         super(props)
         this.state = {
           input: ''
         }
      }
    handleChange = (text) => {
        this.setState({ input: text })
      }
      
      render () {
        const { input } = this.state
        return (
        <div>
            <label>
              Name:
               <input type="text" value={this.state.value} 
                      onChange={this.handleChange} />
            </label>
            <input type="submit" value="Submit" />
          </div>
          )
        }
     }

```
## Conditional Rendering

Kết xuất có điều kiện trong React hoạt động giống như cách các điều kiện hoạt động
trong JavaScript. Sử dụng các toán tử JavaScript như if hoặc toán tử điều kiện để
tạo các phần tử đại diện cho trạng thái hiện tại và để React cập nhật giao diện 
người dùng để khớp với chúng.
## Component Life Cycle 
<h1 align="center">
  <img src="https://res.cloudinary.com/djeghcumw/image/upload/v1559793682/blog/1_cEWErpe-oY-_S1dOaT1NtA.jpg"/><br/>
</h1>
Each component has several “lifecycle methods” that you can override to run code at particular times in the process. You can use this lifecycle diagram as a cheat sheet. In the list below, commonly used lifecycle methods are marked as bold. The rest of them exist for relatively rare use cases.

> Document: [The Component Lifecycle](https://reactjs.org/docs/react-component.html)

### Mounting
Những phương thức bên dưới được gọi theo thứ tự khi một instance của component đang được tạo và chèn vào DOM:
- constructor()
  + Khai báo các đối tượng.
  + Chạy ngay đầu tiên khi khởi tạo component.
- static getDerivedStateFromProps()
  + Được gọi ngay trước khi gọi phương thức render, cả ở lần mount ban đầu và các lần cập nhật tiếp theo. 
    Nó nên return một object để cập nhật state, hoặc null để không cập nhật.
  + Phương thức này tồn tại cho các trường hợp sử dụng hiếm gặp khi state phụ thuộc vào sự thay đổi của props theo thời gian
  >Lưu ý rằng phương thức này được kích hoạt ở mọi lần render, bất kể nguyên nhân là gì.
- render()
  Phương thức render() là phương thức bắt buộc duy nhất trong một class component.
  >render() sẽ không được gọi nếu shouldComponentUpdate() returns false.
- componentDidMount()
  componentDidMount() được gọi ngay lập tức sau khi một component được mount (được chèn vào tree). Quá trình khởi tạo mà yêu cầu các DOM node sẽ được thực hiện tại đây. Nếu bạn cần tải dữ liệu từ một remote endpoint, đây là một nơi phù hợp để thực hiện network request.
### Updating
- static getDerivedStateFromProps():
  + Nội dung tương tự bên trên!
- shouldComponentUpdate()
  + Được gọi trước render khi nhận được props hoặc state mới. Mặc định là true. Phương thức này không được gọi ở lần render đầu tiên hoặc khi forceUpdate() được sử dụng.
- render()
  + Nội dung tương tự bên trên!
- getSnapshotBeforeUpdate()
  + Được gọi ngay trước khi output của lần render gần nhất được commit tới DOM. Nó cho phép component của bạn lấy một số thông tin từ DOM (ví dụ. vị trí thanh cuộn) trước khi những thông tin đó có khả năng bị thay đổi. Bất kỳ giá trị nào được return bởi phương thức lifecycle này sẽ được truyền dưới dạng tham số cho componentDidUpdate().
  + Trường hợp sử dụng này không phổ biến, nhưng nó có thể xảy ra trong các UI như một chat thread cần xử lý vị trí thanh cuộn theo cách đặc biệt.
  + Một giá trị snapshot (hoặc null) nên được return.
- componentDidUpdate()
### Unmounting
- componentWillUnmount()
  + Được gọi ngay trước khi một component bị unmount và destroy. Thực hiện mọi thao tác cleanup cần thiết trong phương thức này, chẳng hạn như invalidating timers, hủy các network request, hoặc cleanup bất kỳ subscription nào mà đã được tạo ra trong componentDidMount().
### Xử Lý Lỗi
- static getDerivedStateFromError();
  + Lifecycle này được gọi sau khi một component con ném ra một error. Nó nhận error được ném ra dưới dạng một tham số và sẽ return một giá trị để cập nhật state.
  > getDerivedStateFromError() được gọi trong “render” phase, do đó side-effects không được phép thực hiện. Để thực hiện side-effects, sử dụng componentDidCatch() thay thế.
- componentDidCatch()
  + Lifecycle này được gọi sau khi một component con ném ra một error. Nó nhận hai tham số:
    + error - Error được ném ra.
    + info - Một object với một componentStack key chứa thông tin về component nào đã ném ra error.
  + componentDidCatch() được gọi trong “commit” phase, do đó các side-effect được phép thực hiện. Nó nên được sử dụng cho những việc như log các error:
  ```javascript
    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = { hasError: false };
      }
    
      static getDerivedStateFromError(error) {
        // Cập nhật state để lần render tiếp theo sẽ hiển thị fallback UI.
        return { hasError: true };
      }
    
      componentDidCatch(error, info) {
        // Example "componentStack":
        //   in ComponentThatThrows (created by App)
        //   in ErrorBoundary (created by App)
        //   in div (created by App)
        //   in App
        logComponentStackToMyService(info.componentStack);
      }
    
      render() {
        if (this.state.hasError) {
          // Bạn có thể render bất kỳ custom fallback UI
          return <h1>Something went wrong.</h1>;
        }
    
        return this.props.children;
      }
    }
  ```
> Lưu ý: Trong trường hợp xảy ra lỗi, bạn có thể render một fallback UI với componentDidCatch() bằng cách gọi setState, nhưng cách này sẽ không được sử dụng nữa trong một phiên bản tương lai. Thay vào đó, sử dụng static getDerivedStateFromError() để xử lý fallback render.
## List and key
- Các key giúp React xác định những phần tử nào đã thay đổi, được thêm, hay bị xóa. Các key nên được truyền vào các element bên trong một mảng để cho các element này có một định danh cố định (stable identity):
- Các tốt nhất để chọn một key là sử dụng một chuỗi mà được xác định là duy nhất trong các nút anh em (siblings). Cách thông thường nhất mà bạn sẽ sử dụng là dùng các ID từ dữ liệu của bạn làm key:
- Các Key được sử dụng bên trong các mảng nên là duy nhất giữa các nút anh em của chúng. Tuy nhiên chúng không cần là duy nhất đối với toàn bộ component. Chúng ta có thể sử dụng các key giống nhau khi chúng ta tạo hai mảng khác nhau:
## Composion & Inheritance

## Base hook 

# Advanced Topics
# Ecosystem
# Web Sucurity Knowledge
# Css Acrchitecture -  Css Preprocessorts
# Build Tools
# Pick a Framework
# Modern Css
# Web Components
# CSS Frameworks
# Testing your Apps
# Type Check
# Progresslve Web App 
# Server Side Rendering (SSR)
# GraphQL 
# Static Site Fenerators
# Mobile Applications
# Desktop Applications