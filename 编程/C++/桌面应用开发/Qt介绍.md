# Qt介绍
## 基类
QWidget —— 最基础的窗口类  所有Qt中可视化窗口的基类

## 继承QWidget
QMainWindow —— 菜单栏、工具栏、状态栏
QDialog —— 对话框，没有最大化的窗口


## 应用程序对象
QApplication 
1. 维护qt应用程序生命的一个对象。
2. 每个qt有且仅有一个对象。

...Widget 窗口类对象
().show   显示窗口
().exec()  消息循环(一个死循环)

## 头文件 Widget继承QWidget

Q_OBJECT  //宏定义，引入qt信号、槽
// 转到定义：1. ctril + click 2. F2 3. 右键 转到

构造函数：
1. 使用了默认参数 QWidget *parent=0
2. parent 为 0 或 NULL，表示当前窗口对象是个顶层窗口(即可在任务栏找到的窗口)