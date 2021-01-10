### 1. Props trong react

- Props là một object được truyền vào trong một components, mỗi components sẽ nhận vào props và trả về react element.
- Props cho phép chúng ta giao tiếp giữa các components với nhau bằng cách truyền tham số qua lại giữa các components.
- Khi một components cha truyền cho component con một props thì components con chỉ có thể đọc và không có quyền chỉnh sửa nó.
- Cách truyền một props cũng giống như cách thêm một attributes cho một element HTML.

```angular2svg
const App = () => <Welcome name="Nguyen Tuan Anh"></Welcome>
```

- Ví dụ 1: Xây dựng ứng dụng hiển thị danh sách quần áo

![img.png](img.png)

### 2. State trong react

- State là một object có thể được sử dụng để chứa dữ liệu hoặc thông tin về components
- State có thể được thay đổi bất cứ khi nào mong muốn
- Khác với props có thể truyền props sang các components khác nhau thì state chỉ tồn tại trong phạm vi của components chứa nó
- Mỗi khi state thay đổi thì components đó sẽ được render lại.
- Trong react : state được dùng để phản hồi các yêu cầu từ người dùng, hay lưu trữ một dữ liệu nào đó trong components.

#### Thao tác với state trong ReactJS

##### a. Khởi tạo state
- Sử dụng state trong class component, không sử dụng đc trong functional component
- Cú pháp:
    ```angular2svg
        this.state = { name : 'Hoang Thuy Linh' }
    ```
  
- Lấy giá trị của state:
    ```angular2svg
        console.log(this.state.name) //Hoang Thuy Linh
    ```
  
- Constructor là hàm khởi chạy đầu tiên khi một components được gọi.
- Vì thế trong hầu hết trường hợp nên khởi tạo state bên trong hàm constructor() để tránh gặp các lỗ không mong muốn.
  
- Ví dụ về state:
    ```angular2svg
        import React from "react";

        class App extends React.Component {
            constructor(props) {
                super(props);
                // Chỉ định một state
                this.state = { name: "Nguyen Tuan Anh" };
            }
            render() {
                return (
                    <div>
                    <h1>Học ReactJS căn bản tại {this.state.website} </h1>
                    </div>
                );
            }
        }
  
        export default App;
    ```

##### b. Cập nhật state

- Cú pháp:

```angular2svg
this.setState({
     name : 'newValue'
})
```

- Lấy giá trị của state trước khi cập nhật

```angular2svg
this.setState((state) => {
      return newValue;
});
```

- Ví dụ : Tăng giảm giá trị

![img_1.png](img_1.png)

```angular2svg
import React from "react";
 
class App extends React.Component {
  constructor(props) {
    super(props);
    //Chỉ định một state
    this.state = { index: 1 };
  }
  render() {
    return (
      <div>
        <p>Giá trị {this.state.index}</p>
        <button
          onClick={() => {
            this.setState({
              index: this.state.index + 1
            })
          }}
        >
          Tăng
        </button>
        <button
          onClick={() => {
            this.setState({
              index: this.state.index -1
            })
          }}
        >
          Giảm
        </button>
      </div>
    );
  }
}
export default App;
```

### So sánh props và state

- <b>State</b> - Dữ liệu chỉ nằm trong phạm vi của một component. Nó được sở hữu bởi một components cụ thể mà chỉ là của component đó thôi. Ví dụ, như người yêu bạn chỉ là của bạn vậy =))). Và mỗi khi state thay đổi thì component cũng phải thay đổi theo.
- <b>Props</b> - Dữ liệu đường truyền từ component cha cho componet con, components con khi nhận được sẽ chỉ được đọc mà không thể thay đổi dữ liệu đó.

Sự khác nhau chính của 2 khái niệm này là component sở hữu dữ liệu. State là chỉ riêng nó có thể sử dụng. Props là dữ liệu mà component con được nhận về từ một component cha.
Vì phạm vi của state chỉ nằm trong components nên việc truyền dữ liệu từ các components với nhau người ta thường dùng props. Nhưng vấn đề ở đây là props chỉ có thể truyền cho componet con của nó và khi truyền cho các componet cháu, chắt khá rắc rối. Bởi vậy chúng ta có thêm khái niệm về <b>Redux</b>