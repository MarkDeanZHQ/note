# typedef的使用

## 工具-代码片段管理
可以实现 代码片段引用

## 工程-右键属性-c/c++ 预处理器
进行预处理器定义，可以在每个程序运行前，预处理内容
可以加入 _CRT_SECURE_NO_WARNINGS
简化代码块使用


* #include<stdio.h> //标准输入输出
* #include<string.h> //字符串处理函数  strcpy strcmp strcat
* include<stdlib.h> //标准库函数  malloc free

* int main(){} //程序入口



## typedef 
* 简化struct 关键字
* 区分数据类型
    * typedef PCHAR char*
        * PCHAR a，b； 两者均为 char* 类型
        * 否则需用写法 ： char* p1,*p2;
* 提高移植性
    * 将需要变化的类型定义用 typedef 定义，移植时，只需要改typedef一个地方
