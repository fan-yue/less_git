### & 的用处

标签之间嵌套

`LESS`

```
.center{
    width: 100px;
    height: 100px;
    background-color: red;
    & .list{
        width: 50px;
        height: 50px;
        background-color: green;
        li{
            width: 30px;
            height: 30px;
            background-color: blue;
            & a{
                color: red;
            }
        }
    }
}
```

`CSS`

```
.center {
  width: 100px;
  height: 100px;
  background-color: red;
}
.center .list {
  width: 50px;
  height: 50px;
  background-color: green;
}
.center .list li {
  width: 30px;
  height: 30px;
  background-color: blue;
}
.center .list li a {
  color: red;
}
```



### 媒体查询

在以往的工作中，我们使用媒体查询，都要吧一个元素分开写，使用LESS后，就会方便许多。

`LESS`

```
#main{
    @media screen {
        @media (max-widht:768px) {
            width: 100px;
        }
    }
    @media tv {
        width: 2000px;
    }
}
```

`CSS`

```
@media screen and (max-widht: 768px) {
  #main {
    width: 100px;
  }
}
@media tv {
  #main {
    width: 2000px;
  }
}
```

唯一的缺点就是每一个元素都会编译处自己的`@media`声明，并不会合并



### 实战技巧

可以接住Less在元素中，去定义自己的私有样式

`Less`

```
#main{
    .show{
        display: block;
    }
}
.show{
    display: none;
}
```

`CSS`

```
#main .show {
  display: block;
}
.show {
  display: none;
}
```

