# list
1. 数据结构：循环双向链表。
2. 迭代器：双向迭代器。
3. at、empty、size、

迭代器：
_Nodeptr
Mysize, Myhead 过去版本不是函数 不加()

## 构造
1. 始末迭代器
2. n 个元素
3. 对象

## 插入、删除
1. push_back() 元素
2. pop_back()  删除最后
3. push_front() 插在最前
8. insert()
    1. pos elem
    2. pos n elem
    3. pos begin end
9. clear()
10. earase()
    1. begin end
    2. pos
1. remove()  elem   删除所有与 elem匹配的元素
2. remove_if(myfunc)   
    1. 提供回调函数返回bool 
    2. 单个单个元素判断
    3. 满足条件的删除 

## 存取
1. front() 
2. back()

## 赋值操作
4. assign()  始末迭代器
5. assign()  n 个元素
6. 重载=
7. swap()  

## 大小操作
1. resize() 
2. size()
3. empty()

## 反转
1. reverse()
2. sort  
list 需要使用自身的sort，通用sort算法无法对list排序；