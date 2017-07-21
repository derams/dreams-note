不用 Redux 如何实现组件间通信呢？

答案简单来说就一句话：
>通过子组件，修改父组件的 state ，然后把父组件的 state 作为所有子组件的 props 值传入各个子组件

这样就实现了各个子组件间的通信了
###子组件修改父组件的 state 值：
```js
import React, { Component } from 'react';


class Child extends Component {

  handleClick = () => {
    this.props.changeColor('green')
  }

  render() {
    return (
      <div style={{ 'border' : '3px solid red' }}>
        <button onClick={this.handleClick}>Child button</button>
      </div>
    );
  }
}

class App extends Component {
  state = {
    bgColor: 'yellow'
  }

  changeBackground = (color) => {
    this.setState({
      bgColor: color
    })
  }

  render() {
    return (
      <div style={{ 'border' : '3px solid green',
                    'padding' : '20px',
                    'backgroundColor' : this.state.bgColor
      }}>
        <Child changeColor={this.changeBackground} />
      </div>
    );
  }
}

export default App
```
###redux-hello 项目中
实现评论效果

go without redux

show comment num
###参考资料
You May Not Need Redux
2222
