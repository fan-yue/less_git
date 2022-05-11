# 初识LESS

### LESS注释

```less
// 这种注释，编译后不会出现在css样式表中
/* 这种注释会出现 */
```

### LESS属性值变量

修改`bgcolor`这个变量，所有相关样式的变量都会随之改变，其变量是常量，只能定义一次，不能重复使用

```
@color:#999;
@bgcolor:red;
@width:50%;

.one{
    width: @width;
    color: @color;
    background-color: @bgcolor;
}
```

以`@`开头定义变量，并且使用时直接键入`@名称`，在平时工作中，我们可以把变量封装到一个文件中，这样便于代码维护

```
// 颜色模块
@footer:red;
@nav:yellow;
@header:aqua;
```

