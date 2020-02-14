# Tìm hiểu về React

## React là gì

React là một thư viện JavaScript mở, được Facebook cho ra mắt vào năm 2013. React được tạo ra để giúp xây dựng các interfaces một cách dễ dàng và có thể sử dụng lại được. Ý tưởng của React là chia nhỏ giao diện người dùng thành các components riêng rẽ. Những components riêng rẽ và có thể sử dụng lại được là chức năng chính của React, kèm theo đó là các thành phần chính không kém phần quan trọng khác như JSX, State, và Props. Chúng ta sẽ cùng tìm hiểu các phần chính của React bên dưới.

## Components

Giao diện của React được hình thành nên từ những components nhỏ. Những components này được biên dịch trở thành HTML và sau đó được thêm vào trong DOM để render cho người dùng. React components cũng có 2 loại, đó là class-based components, và functional components. 

Bên dưới đây là minh họa cho 2 loại components vừa nêu trên.

*Class-based component*

```
class Welcome extends React.Component {
  render() {
    return <h1>Hello</h1>
  }
}
```

*Functional component*

```
function Welcome() {
  return <h1>Hello</h1>
}
```

Từ 2 components trên, chúng ta có thể thấy, sự khác nhau chính giữa 2 loại components trên đó là Class-based component có thể lưu trữ **state**. Chúng ta sẽ bàn về state bên dưới, hiện giờ có thể hiểu state như là một parameter. State cho phép các component của chúng ta trở thành các component động và linh động hơn. Còn đối với functional components, nó không có khả năng lưu trữ các state, và nó cũng chỉ chưa mỗi một render method, được truyền vào giá trị là **props** (sẽ được giải thích ở phần bên dưới) và trả về cái cần render.

## JSX

JSX là một extension của JavaScript được sử dụng để giao tiếp với React về việc UI của chúng ta sẽ trông như thế nào. Mặc dù nó trông giống như HTML, JSX cho phép chúng ta tạo ra UI và các logic ở cùng một chỗ. Bằng cách sử dụng JSX, chúng ta có thể nhúng các logic JS vào ngay trong UI của mình. Nếu bạn đã từng làm việc với Ruby on Rails thì JSX cũng đóng vai trò tương tự như Ruby's ERB, chúng ta có sẽ sử dụng chúng để tạo một layout với các biến một cách linh động.

*Ví dụ JSX*

```
const name = 'Jen';
const element = <h1>My name is {name}</h1>; 
```

## State

Có lẽ bạn vẫn thắc mắc, thực ra state là gì? Giờ chúng ta sẽ tìm hiểu về State nhé.

State là một đối tượng được đính kèm vào một Class component. Nó có thể được khởi tạo hoặc được thay đổi thông qua input của người dùng hoặc các API. State được giữ bởi một component cha và có thể được truyền xuống các component con của nó thông qua **props**. Đây được gọi là **Unidirectional Flow**, đây cũng là một key feature của React nhé.

Giải thích thêm một chút về  **unidirectional flow**, nó còn được biết đến với tên gọi one-way data flow, có nghĩa là data sẽ có một và chỉ một hướng để chuyển đến các phần các của ứng dụng. Cụ thể hơn, các component con sẽ không thể cập nhật data được gửi đến từ component cha. Lợi ích chính của flow này là để chắc chắc chúng ta đang đi theo một mô hình data flow rõ ràng và "sạch", giúp chúng ta có thể quản lý nó dễ hơn.

Tiếp tục với State, state của một component phải được lưu trữ ở một cấp đủ cao trong hệ thống các components để có thể truyền nó đến các component con mà không phải truyền nó qua các component không cần thiết. State chỉ có thể truyền xuống các component con và không thể dùng ở các component đồng cấp. Bất kể khi nào state của một component bị thay thôi, component đó và cũng như các component con của nó sẽ được cập nhật để hiển thị state mới.

*Ví dụ về state trong component FetchData*

```
class FetchData extends React.Component {
   constructor(props) {
      super(props);
      this.state = {
         isLoading: false,
      };
   }
}
```

##Props##

Chúng ta đi đến phần cuối của bài viết hôm nay, Props. Props là các đối tượng được đứa đến các component bởi các component cha của chúng. Props được truyền để tạo ra các component động. Không phải lúc nào chúng ta cũng muốn render các data tĩnh, và đó là lúc props phát huy tác dụng của nó. Props được truyền đến các component khác nhau bởi vì mục tiêu chính của React là tạo ra các "small pure components". Sẽ thế nào nếu chúng ta muốn tạo ra một component lớn với state và cho nó render từng phần của UI? Cũng được thôi, nhưng nó sẽ gặp vấn đề với việt đọc hiểu và sử dụng lại các phần trong UI đó ở nơi khác. Thử hình dung, khi bạn cần một phần nhỏ trong component lớn vừa tạo, bạn sẽ cần phải render nguyên cả một component đó một lần nữa đấy.

*Ví dụ về Props*

```
const KanjiData = props => {
   return (
      <div>
         <p>Character: {props.character}</p>
         <p>Meaning: {props.meaning}</p>
         <p>Kunyomi Reading: {props.kunyomi}</p>
         <p>Onyomi Reading: {props.onyomi}</p>
      </div>
   );
};
```

Tóm lại, chúng ta nên nhớ, một thư viện chỉ là công cụ để giúp công cuộc coding của các developer trở nên dễ dàng hơn thôi. Nếu cảm thấy hứng thú với React, bạn có thể xem qua document của React ở đường link này [React document](https://reactjs.org/docs/getting-started.html). Tất cả mọi thứ bạn làm trong React, đều có thể làm với vanilla JavaScript. React và các thư viện JS khác như, Angular, Vue, và Ember không phải là các công cục bắt buộc phải có khi lập trình với JS. So... choose wisely!

**Link tham khảo:**

https://reactjs.org/tutorial/tutorial.html#what-is-react

https://www.geeksforgeeks.org/unidirectional-data-flow/

https://dev.to/talia/beginner-s-guide-to-react-3986
