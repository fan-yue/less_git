### 选择器变量

让选择器变成动态，变量名必须使用**大括号**包着

`LESS`

```
// 选择器变量
@myselect:#warp;
@warp:warp;

@{myselect}{    //变量名必须使用大括号包着
    background-color: aqua;
    width: 400px;
    height: 20px;
}

.@{warp}{
    width:400px;
    height: 500px;
    background-color: black;
}
```

`CSS`

```
/* CSS */
#warp {
  background-color: aqua;
  width: 400px;
  height: 20px;
}
.warp {
  width: 400px;
  height: 500px;
  background-color: black;
}

```



### 属性变量

可减少代码书写量，变量名必须使用**大括号**包着

`LESS`

```
// 
    // 选择器变量
@myselect:#warp;    
    //属性变量
@borderStyle:border-style;
@soild:soild;

@{myselect}{
    @{borderStyle}:@soild;		 //变量名必须用大括号包着
}

```

`CSS`

```
#warp {
  border-style: soild;
}
```



### url变量

当项目结构改变时，修改其变量即可，可以省略全体替换路径的方法。

变量名必须使用**大括号**包着

`LESS`

```
// url变量
@image:"../../image";

body{
    background: url("@{image}/01.png");
}
```

`CSS`

```
body {
  background: url("../../image/01.png");
}
```



### 声明变量

有点类似于下面的混合方法（使用时一定要用 **小括号()**  ）：

- 结构： @name:{属性：值}；
- 使用： @name();

`LESS`

```
// 声明变量
@background:{
    background: red;
}
@Rulse:{
    width: 200px;
    height: 300px;
    border: 1px solid black;
}
#warp{
    @background();
}
#main{
    @Rulse();
}
```

`CSS`

```
#warp {
  background: red;
}
#main {
  width: 200px;
  height: 300px;
  border: 1px solid black;
}
```



### 变量运算

LESS可以使用变量运算

- 加减法时，以第一个数据的单位为基准

- 乘除法，注意单位

- 在链接运算的时候，注意添加空格

  `LESS`

  ```
  //  变量运算
  @width:300px;
  @color:#222;
  
  #warp{
      width: @width - 20;
      height: @width - 20*5;
      margin: (@width - 20)*5;
      color: @color * 2;
      background-color:@color + #111;
  }
  ```

  `CSS`

  ```
  #warp {
    width: 280px;
    height: 200px;
    margin: 1400px;
    color: #444444;
    background-color: #333333;
  }
  ```



### 避免变量运算

将属性当字符串用引号括起来，并在前面加上波浪符 **`~`**

```
// less
width: ~'calc(100% - 10px)';
height: ~'calc(100vh - 20px)';
```

```
 // css
width: calc(100% - 10px);
height: calc(100vh - 20px);
```



### 变量作用域

就近原则

`LESS`

```
// 变量作用域
@var:@a;
@a:100%;

#warp{
    width: @var;
    @a:9%;
}
```

`CSS`

```
#warp {
  width: 9%;
}
```



### 用变量定义变量

`LESS`

```
// 用变量去定义变量
@fond:@va;
@va:'fond';
#warp::after{
    content: @fond;
}
```

`CSS`

```
#warp::after {
  content: 'fond';
}
```

