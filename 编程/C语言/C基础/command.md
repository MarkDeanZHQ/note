# command



# 定义

## 宏定义
#define 名字 数值或类型      宏定义相当于 纯粹的替换  ，并非真实定义。

## 枚举定义
enum 对象名 {成员....};   //递增

## 类型定义
typedef 类型 名字     

一个简便的结合 结构体使用方法
typedef struct TIME
{
    int sec;
    int min;
    int hor;
    
}TIME;
之后就可以用 TIME 进行变量定义。     




# 输入
## scanf ()
用来数值等 小数据的读取

scanf("%d",&num);   // 可通过手动输入 从地址上更改 变量值   
能读取  回车
成功返回 参数数目  失败返回-1


### 读取字符串
scanf("%s",&num);
* 遇到 \0 、空格 就会结束。
* 会造成内存污染：无视数组可存的大小，存放字符空间不足，会继续向后存放，占用其他的空间。

fscanf(文件流指针, format);
从文件中提取数据到变量地址
成功返回参数数目，失败返回-1



## gets()
gets(&num);
* 遇到空格不结束读取
* 也会造成内存污染


## fgets()
用来字符串的读取

fgets(&num, sizeof(num) ,stdin);  // 从 stdin 读取到 num 数组中  ，最大可读取sizeof(num)-1 个`//-1 是因为 会在后面自动添加一个 '\0'`。
* 成功返回字符串，失败返回NULL
* 会读取 空格 和 \n ，读取后直接结束。·
* 不会污染内存
* 使用时配合strlen() 可避免读取 回车
    * char buf[1024]="";
    * fgets(buf,sizeof(buf),stdin);
    * buf[strlen(buf)-1]=0;


## strlen()  
测字符数组有效字符(除\0外的字符)的个数
```c
char buf[]="hello";
int i = 0 ;
i = strlen(buf);

```




## getchar()
与scanf 类似
作用：从键盘读取一个字符
ch=getchar();
printf("%c\n",ch);

## _getch()  输入任意键结束
返回 获取的字符

头文件 <conio.h>

# 输出

## puts()
puts(buf)//数组首元素地址
自动换行


## fputs()
fputs(buf,stdout);    // 数组首元素地址；stdout 标准输出(屏幕)


## putchar()
输出打印一个字符 
putchar('a')'


## printf()
           

printf格式字符：

| **打印格式** | **对应数据类型** | **含义** |
| --- | --- | --- |
| %d | int | 接受整数值并将它表示为有符号的十进制整数 |
| %hd | short int | 短整数 |
| %hu | unsigned short | 无符号短整数 |
| %o | unsigned int | 无符号8进制整数 |
| %u | unsigned int | 无符号10进制整数 |
| %x,%X | unsigned int | 无符号16进制整数，x对应的是abcdef，X对应的是ABCDEF |
| %f | float | 单精度浮点数 |
| %lf | double | 双精度浮点数 |
| %e,%E | double | 科学计数法表示的数，此处"e"的大小写代表在输出时用的"e"的大小写 |
| %c | char | 字符型。可以把输入的数字按照ASCII码相应转换为对应的字符 |
| %s | char \* | 字符串。输出字符串中的字符直至字符串中的空字符（字符串以'\\0‘结尾，这个'\\0'即空字符） |
| %p | void \* | 以16进制形式输出指针 |
| %% | % | 输出一个百分号 |

printf附加格式：

|     **字符**     |                                                          **含义**                                                          |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------- |
| l(字母l)          | 附加在d,u,x,o前面，表示长整数                                                                                                |
| \-               | 左对齐                                                                                                                      |
| m(代表一个整数)   | 数据最小宽度                                                                                                                |
| 0(数字0)          | 将输出的前面补上0直到占满指定列宽为止不可以搭配使用\-                                                                            |
| m.n(代表一个整数) | m指域宽，即对应的输出项在输出设备上所占的字符数。n指精度，用于说明输出的实型数的小数位数。对数值型的来说，未指定n时，隐含的精度为n=6位。 |




# 流程结构
## switch
* 在 判断条件为 整数、字符 的情况下适用
* 在没有使用 break 情况下 ，只会跳到对应case，并依次执行完 下面的所有case
```c
switch(a)//(里面的判断雕件只能是整数)
{
    case 0: //不需要用大括号括起来
        printf("0\n");
        printf("hello\n");
        break;//  跳出 switch语句 
    case 1:
        printf("1\n");
        break;//  跳出 switch语句 
    case 2:
        printf("2\n");
        break;//  跳出 switch语句 
    case 3:
        printf("3\n");
        break;//  跳出 switch语句 
    default:
        printf("4\n"); //默认
        break;//  跳出 switch语句 
}
```
另一种情况 
判断字符时可以直接使用
因为字符在内存中存的是 ASCII值 ，可视为整数
```c
int main()
{
char c;
c=getchar();
switch(c)//(里面的判断雕件只能是整数)
{
    case '0': //不需要用大括号括起来
        printf("0\n");
        printf("hello\n");
        break;//  跳出 switch语句 
    case '1':
        printf("1\n");
        break;//  跳出 switch语句 
    case '2':
        printf("2\n");
        break;//  跳出 switch语句 
    case '3':
        printf("3\n");
        break;//  跳出 switch语句 
    default:
        printf("4\n"); //默认
        break;//  跳出 switch语句 
}
}
```




# 杂项
## 随机数
<stdlib.h>
srand(10);  //设置种子
rand();//获得随机数

## 获取当前时间
time(NULL);    

## 延迟
Sleep(2);

头文件 <Windows.h>




# 字符串处理


## 字符串替换

### 字符串拷贝
---    
#### strcpy(dst,scr);  拷贝字符串，遇到\0结束  
* **返回dest起始地址**
    * strncpy(dst,scr,n);  拷贝n个字符，遇到\0结束，不拷贝\0之后。
---    

### 字符串追加
---    
#### strcat(dst,scr);  追加字符串，从dst的\0位置替换追加。
* **返回dest起始地址**
    * strncat(dst,scr);  追加n个字符，遇到\0结束，不会读取\0后。
---    

### 字符串比较
---    
#### strcmp(str1,str2);  比较字符串，遇到\0结束
* **相等返回 0；大于返回 >0;小于返回 <0;
    * strncmp(str1,str2,n);   比较指定个数的字符串，遇\0结束。    
---    
    
## 组拆包

### 组包
---    
#### sprintf(buf,format);  组包函数，format 格式等同于 printf 中的参数。
* **返回值为 buf的长度，不包括最后的0**； *可以测量字符串中间的\0*
    * snprintf   // sprintf 有缓冲溢出问题，可以使用sprintf 来替代。
---    
   
## 拆包 
---    
### sscanf(buf,"format",&a,&b);  拆包函数，format 格式等同于 buf 中的格式，将想要的内容提取到 a , b 中。
* **返回值为参数数目**
 * * sscanf() - 从一个字符串中读进与指定格式相符的数据.
　　函数原型:
　　int sscanf( string str, string fmt, mixed var1, mixed var2 ... );
　　int scanf( const char *format [,argument]... );
　　说明：
　　sscanf与scanf类似，都是用于输入的，只是后者以屏幕(stdin)为输入源，前者以固定字符串为输入源。
　　其中的format可以是一个或多个 {%[*] [width] [{h | l | I64 | L}]type | ' ' | '\t' | '\n' | 非%符号}
　　注：
　　1、 * 亦可用于格式中, (即 %*d 和 %*s) 加了星号 (*) 表示跳过此数据不读入. (也就是不把此数据读入参数中)
　　2、{a|b|c}表示a,b,c中选一，[d],表示可以有d也可以没有d。
　　3、width表示读取宽度。
　　4、{h | l | I64 | L}:参数的size,通常h表示单字节size，I表示2字节 size,L表示4字节size(double例外),l64表示8字节size。
　　5、type :这就很多了，就是%s,%d之类。
　　6、特别的：%*[width] [{h | l | I64 | L}]type 表示满足该条件的被过滤掉，不会向目标参数中写入值
　　支持集合操作：
　　%[a-z] 表示匹配a到z中任意字符，贪婪性(尽可能多的匹配)
　　%[aB'] 匹配a、B、'中一员，贪婪性
　　%[^a] 匹配非a的任意字符，贪婪性
---    




## 字符串查找
---    
### strchr(buf,'char');   在字符串中找一个字符。
* **返回值为 在该字符串中找到的第一个指定字符的地址**
失败返回0

### strstr(buf,buf);  在字符串中寻找指定字符串的位置
* **返回指定字符串第一次出现的地址**
失败返回0
---    


## 字符串切割
---    
### strtok(buf,"注意是双引号"  或  buf)；  切割字符串，将替换成 \0 字符。    
* 双引号里的 不是指 切割一次，而且一次性切割所有相邻、相关字符。
* >notice 原先字符串 中的分隔符 将被替换成 \0;
* **返回值为 上一次分割的字符串指针，分割结束返回 NULL**
    * 第一次分割时，必须给 buf 值。
    * 之后分割，strtok(NULL,""); 将buf设置成NULL，会自动记录分割位置，并往后进行分割。
    * 切割结束返回 NULL
---    
    

## 字符串转数字
* 跳过空格，遇到数字或正负号开始转换，遇到非数字或'\0' 结束转换，返回结果。
    * atoi();  int
    * atol();  long
    * atof();  float
    








# 内存处理
优点： 遇到 \0  和 0  不会结束操作。


* memcpy(\*dest,\*scr,num);             从 scr地址拷贝 num个 **字节** 到 dest地址；
    * 返回 dest 首地址
* memcmp(\*dest,\*scr,num);            比较 dest 地址和 scr 地址的n个**字符**
    * 相同返回 0，大于返回1，小于返回-1；
* memset(\*dest,const char,num);     在 dest地址处 插入 num个 char **字符**；————char 字符若为 int 类型 ，必须是 unsigned char.     
    * 返回 dest 首地址                      
    



## malloc(申请空间位数)  申请空间
free(申请过的空间首地址) 释放空间








# 文件操作
## 打开文件
* fopen(”路径名“，”打开方式“);    // 打开一个文件，
* 成功返回FILE结构体地址，失败返回NULL
* fopen("./a.txt","r");
    * 打开方式 
        * r只读
        * w只写  清空文件  
        * r+可读可写
        * w+可读可写清空文件
        * a追加
        * a+在文件末尾更改文件
        * b 二进制文件 + b
    * w清空文件
    * 只有r不会创建文件
      
## 打印出错信息   
* perror("前缀");
* 配合文件流指针使用
    * 
```c
     if(NULL == fp) // 或者 if(!fp);    fp 为文件流指针
     {
         perror("open");
         return;
    }
```

## 关闭文件
*一个程序最多打开1024个文件*
fclose(文件结构体指针);

## 修改文件
### 写入
* fputc(char,文件流指针);  一个字符一个字符得写
* 成功返回写入字符，失败 -1  ——EOF

#### 组包写入
fprintf(文件流,format);
失败返回-1 成功返回 字符数

#### fwrite
* fwrite(写入的指针，数据块大小，块数，文件流指针);
* 成功返回块数
* 技巧，
    * 1. 将数据块大小填1，块数等于 写入数据字节数
 

### 读取
* fgetc(文件流指针)  获取一个文件中一个字符
    * 成功返回读取的字符，失败-1  ——EOF
    
* fscanf(文件流指针，format 格式);
* 成功返回参数数目，失败返回-1
* 提取文件中的数据到变量地址中

#### fread
* fread(写入的指针，数据块大小，块数，文件流指针);
* 成功返回块数
* 技巧，
    * 1. 当返回值比块数小，说明读到文件末尾 
 

### 删除与重命名

#### 删除
remove(“路径名”)；
成功0，失败-1

#### 移动 和 重命名
rename(“旧路径名”，“新路径名”)  
成功0，失败-1



### 判断是否读取完全
* feof(文件流指针);     既可以判断 二进制文件 也可以判断 文本文件。
* 返回值 没有读取完 0 ，读取完全非0
* 判断的是 最后一次读取文件的内容




## 移动文件光标
fseek(文件流指针,偏移位,模式);
    * 偏移位：相对位置 ，通过正负 前移或后移  
    * 模式：SEEK_SET 头 
        * SEEK_CUR 当前
        * SEEK_END 尾
        
rewind(文件流指针);
    * 移动到开头
    
ftell(文件流指针);
    * 返回当前相对开头的偏移值
    



## 获取文件状态信息 stat

stat(“文件目录”，stat结构体地址)
    * stat 结构体地址
        * struct stat buf;
        * stat("t.txt",&buf);
    * 成功返回0，失败返回 -1 
        * 可判断文件是否存在

stat_size  取文件大小 - >  t.st_size.        





