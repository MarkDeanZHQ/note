# command

## 输出

System.out.print(); 输出不换行

System.out.println(); 输出换行

## 一、键盘录入  函数使用三步骤

* 一、
导包：
头文件 import java.util.Scanner;  这里叫导包
* 二、
创建对象：
Scanner sc = new Scanner(System.in);    
类型        标识符       调用函数
即获取 该函数的返回值
这里是个结构体
* 三、
使用变量接收数据：
int i = sc.nextInt();


## Random 的使用

import java.util.Random;

Random r = new Random();

int number = r.nextInt(10);  //  获取数据范围  [0,10)

获取随机数