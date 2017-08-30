### 一 Flex 布局是什么？
Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。
任何一个容器都可以指定为 Flex 布局。
```js
    display: flex;
    display: inline-flex;
```
当设为 Flex 布局后，子元素的 float clear 和 vertical-align 属性将会失效。
### 二 容器的属性
1 flex-direction 属性决定主轴的方向
```
row(默认值):主轴为水平方向，起点为左端。
row-reverse:主轴为水平方向，起点在右端。
column:主轴为垂直方向，起点为上沿，
column-reverse:主轴为垂直方向，起点为下端。
```
2flex-wrap属性 如果空间占满，如何换行
```
nowrap: 不换行。
wrap：换行，第一行在上方。
wrap-reverse:换行，第一行在下方。
```
3flex-flow :flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

4justify-content属性
justify-content属性定义了项目在主轴上的对齐方式。
```
justify-content: 
```
flex-start 左边对齐
flex-end 右侧对其
center 中间对其
space-between 紧贴两侧对齐，
space-around 两侧对齐，但有空隙。
```
