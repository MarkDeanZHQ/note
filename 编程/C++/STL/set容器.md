# set容器
set容器存储对象时，如何使用查找api？
传入相同参数的对象即可

1. 数据结构：关联性容器、平衡二叉树
2. 特性：
    1. 可以根据键值自动排序
    2. 键值和实值是同一个数据
    3. 传入对象时，需要传入谓词
    4. 不允许存在相同键值
        1. 注：multiset 允许存在相同键值
3. 迭代器：双向迭代器

* 谓词：结构体重载函数调用符


4. API

## 构造函数
1. set\<T>
2. multiset\<T>
3. set(st)

## 赋值
1. =
2. swap

## 大小
1. size()
2. empty()

## 插入
1. insert()
2. clear()
3. erase()
    1. 迭代器指向元素
    2. 按值删除
    3. 迭代器范围

insert 返回值为 对组
pair<...::iterator, bool> 
    - bool 返回插入成功与否
    
## 改变set容器规则
谓词加入参数列表


## 查找
find
    - count()  该键元素数
    - lower_bound()  大等于
    - upper_bound()  大于
    - equal_range()  返回大于等于 两个 
        - pair 接
    