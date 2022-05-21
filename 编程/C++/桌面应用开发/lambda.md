# lambda
1. 引用
    1. 在构造函数中连接的时候，局部变量已被释放，无法引用使用值；
2. 值传递
3. 可直接作为连接槽

[]捕获局部变量
值传递 默认 const，改变值用 mutable

标准格式：
\[]()opt->retType{}
opt：usually mutable