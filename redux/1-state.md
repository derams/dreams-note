# 第一节：状态值得复习

```
        <form ref="commentForm" onSubmit={this.handleSubmit}   className="comment-form">
            <input ref={(value) => { this.textInput = value} } type="text" className="input" />
            <button type="submit" className="submit-btn" >提交</button>
        </form>

```


定义 handleSubmit

```js
handleSubmit = () =>{

}
```
由于使用了ES6的胖箭头函数语法，所以在使用中，就不需要bind(this)了

```
e.preventDefualt() 阻止跳转
```
###拿到input的value值

首先添加ref如下

```js
 <input ref={value=> this.comment = value} type="text" className="input" />
```
ref字面意思是"指针"，后面大括号的内容，也就是
```
value => this.comment = value
```
是一个胖箭头函数，其中value指代当前input这个节点对应的Object，然后
```
this.comment = value
```
就是把input对象，赋值给一个成员变量，目的是在整个class之内，可以随处访问

这样，如果想在 handleSubmit函数中拿到用户输入的文本就

```js
handleSubmit = (e) => {console.log(this.comment.value)}
```
到这里，如何能从form的输入框中拿到字符串，这个技巧我们就掌握了，同时这个也是最简单的方式，同时也可以通过受控组件的形式来取值，那个比较麻烦，就先不学习了。

###修改state

>先来讨论render函数的属性，一旦state变，render()自动重新执行

所以，界面上两天评论变三天评论，不需要碰html只要控制setState就可以了


###清空input
需要在提交结束后，清空input的value值
handleSubmit中添加
```
this.comment.value=''
```
或者

```
  <form ref = {value => this.myForm = value} onSubmit={this.handleSubmit} className="comment-form">
```
dfd
