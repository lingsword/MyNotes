##八大基本数据类型
* byte  short  int  long
* char
* double float
* boolean

##基本类型间转换
* 自动类型转换（隐式类型转换）：从小类型到大类型可以自动完成。

```
byte --> short --> int --> long --> float --> double
                    |
          char ----->
```

* 强制类型转化:：从大类型转化到小类型需要强制转换符

`(需要转换成的类型) 变量`

因为大类型的精度值大于小类型，取值范围大于小类型，所以当使用强制转化是，有可能会造成精度的损失或者溢出，所以在使用强制转换时，需要{% em %}**显式** {% endem %}地告诉编译器，正在进行强制转换！
##声明时类型转换
```java
int a = 100;
int b = 200;
long c = a + b;//自动将int转化为long

long l1 = 10423l;
int i = (int)l1;//需要加强制转化符，此时没有溢出

long l = 1024L*4*1024*1024;
int j = (int) l;//会产生溢出
System.out.println(j);//结果为0

double pi = 3.1415926535897932384;
float f = (float)pi;//会造成精度的损失，因为单精度的精确度小于double
System.out.println(f);//结果为： 3.1415927

salary = 1555.30;//编译错误，整型赋值了浮点类型
double d = 123.222;
int n = d%2; //编译错误 
```
##运算时类型转换
```java
//由于有 long 型的直接量参与，整个表达式的结果为 long
long distance = 10000 * 365 * 24 * 60 * 60 * 299792458l;
//由于有 double 型的直接量 599.0 参与，整个表达式的结果为 double
double change = 800 - 599.0;
//结果为 0.0，右边都是 int 型数据运算结果也为 int 类型，结果为 0，再赋值给 double型，将 0 转化为 0.0
double persent1 = 80 / 100;
//结果为 0.8，右边表达式有 double 型直接量参与， 运算结果为 double 型
double persent2 = 80.0 / 100;
```
## byte、 char、 short 转换为 int
在前面所介绍的 8 种数据类型中，byte、 char、 short、 int、 long 都表示整数类型，而整型的直接量为 int，在实际使用中，为了方便使用，遵循了如下的规则：
* int 直接量可以直接赋值给 byte、 char 和 short，只要不超过其表示范围。示例如下：

```java
byte b = 97;short s = 97;char c = 97;
```
* byte、 char、 short 三种类型参与运算时，先一律转换成 int 类型再进行运算。示例如下：

```java
byte b = 97;
int num = b + b; //num 的值为 194
```