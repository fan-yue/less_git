mixin混合方法

### 普通混合，无参数方法

方法类似声明的集合，使用则直接键入名称即可。**带括号**

使用场景，大量重复代码编写时，直接调用。

`less`

```
.public(){
    width: 200px;
    height: 200px;
}

.box{
    width: 400px;
    height: 400px;
    border: 1px solid black;
    .a{
        .public();
        background-color: pink;
    }
    .b{
        .public();
        background-color: red;
    }
}
```

`CSS`

```
.box {
  width: 400px;
  height: 400px;
  border: 1px solid black;
}
.box .a {
  width: 200px;
  height: 200px;
  background-color: pink;
}
.box .b {
  width: 200px;
  height: 200px;
  background-color: red;
}
```

`HTML`

```
    <div class="box">
        <div class="a"></div>
        <div class="b"></div>
    </div>
```

其中为了避免代码混淆，一定要**带括号**。



### 带参数混合，加参数的使用方法

#### 	可以通过**传参**的方式将less代码更加优化，接受参数的方法

`less`

```
.public(@w,@h,@bc){
    width: @w;
    height: @h;
    background-color: @bc;
}

.box{
    width: 400px;
    height: 400px;
    border: 1px solid black;
    .a{
        .public(100px,100px,pink);
    }
    .b{
        .public(200px,200px,red);
    }
}
```

`HTML`

```
    <div class="box">
        <div class="a"></div>
        <div class="b"></div>
    </div>
```

#### 	可以通过**传参**的方式将less代码更加优化，带默认参数的方法

`less`

```
.public(@w:10px,@h:10px,@bc:red){
    width: @w;
    height: @h;
    background-color: @bc;
}

.box{
    width: 400px;
    height: 400px;
    border: 1px solid black;
    .a{
        .public(100px,100px,pink);
    }
    .b{
    		// 注意这儿
        .public();
    }
}
```



### 匹配模式

更好的自定义自己的CSS元素

`less`

```
.triangle(L,@w,@color){
    width: 0px;
    height: 0px;
    border-width: @w;
    border-style: solid;
    border-color: transparent @color transparent transparent;
}
.triangle(T,@w,@color){
    width: 0px;
    height: 0px;
    border-width: @w;
    border-style: solid;
    border-color:@color transparent  transparent transparent;
}

.T_sjx{
    .triangle(T, 10px, black);
}
.L_sjx{
    .triangle(L, 10px,red);
}
```



### arguements

使用场景不多

`less`

```
.border(@w,@h,@bgc){
    border: @arguments;
}

.a{
    .border(1px,solid,black);
}
```



### 导入不同的LESS文件

```
@import url(./01.less);
```

