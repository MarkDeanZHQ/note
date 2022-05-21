# map 容器
1. 数据结构：关联式容器、平衡二叉树
2. 迭代器：双向迭代器
3. 特性：元素是对组； 用于分开键值和实值
    1. 对组第一个元素是键值
    2. 第二个元素是实值
4. API

## map 赋值操作
1. =
2. swap

## map大小
1. size()
2. empty()

## 插入
1. insert      返回pair
    1. pair 插入
    2. make_pair 插入    insert(make_pair(..,..))
    3. map<>::value_type(..,..);
    4. mapobj[n]="...";
    
使用[]访问元素，返回实值；
越界时，会创建键值，但不会创建实值。

## 查找
1. low_bound
2. upper_bound
3. equal_range()
    1. 返回大等于的两个值，放在对组中
    2. 返回对组的元素也是对组