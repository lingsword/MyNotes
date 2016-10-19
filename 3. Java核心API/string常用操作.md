#字符串基本操作


### String 是不可变对象

由于字符串在实际开发中被广泛使用，那么在频繁使用某个字符串时，会出现频繁创建一个字符串对象的现象，java 为此对字符串的使用采用了一个优化措施，使得 String 对象为不可变对象，一旦在内存中创建，内容不能发生变化，若要对字符串内容改变，那么就会创建新对象。这样做的目的是可以最大程度的重用相同内容的字符串以减小系统资源的开销。

* **那么字符串对象是如何做到重用的？**

### String 常量池

上一节我们已经知道， JVM 对字符串有一个限制，让字符串作为不变对象，这样就可以做到重用。事实上，当我们通过字面量，常量来初始化一个字符串时，JVM 首先会从字符串的常量池\(一个 JVM内部维护的内存区域，用来保存已经创建过的字符串对象\)中查询用来保存该字符串的对象是否存在，若存在则直接引用，若不存在则创建该字符串对象并存入常量池，然后引用它。因为字符串内容不能
改变，所以我们可以放心的重用他们。

### 内存编码及长度

java 存储每一个字符均使用 2 个字节保存，使用的是 Unicode 编码。并且任何一个字符\(无论是英
文还是汉字\)每个字符的长度都是 1。所以字符串的长度就是该字符串所有的字符个数。
int length\(\):返回当前字符串的长度。
例如:
```java
1. String str = "HelloWorld";
2. System.out.println\(str.length\(\)\);\/\/10
```

### 使用 indexOf 实现检索

int indexOf\(int ch\):用来检查给定的一个字符在当前字符串中第一次出现的下标位置。这里的下标和数组的下标意思相近，0 表示该字符串的第 1 个字符，以此类推。当该字符串中并不包含给定的字符时，那么该方法返回-1。
例如:
```java
1. String str = "HelloWorld";
2. System.out.println\(str.indexOf\('W'\)\);\/\/5
3. System.out.println\(str.indexOf\('h'\)\)\/\/-1
```
### 使用 substring 获取子串

String substring\(int begin,int end\):用来截取当前字符串的部分内容以获取这个子字符串。我们只需要传入两个整数，一个用来表示从哪里开始，另一个用来表示截取到哪里。这里的位置要使用字符串的下标来表示，并且要注意，这两个数字表示的范围是“含头不含尾的”，换句话说就是包含开始下标的字符，但是不包含结束下标的字符。例如:
```java
1. String str = "HelloWorld";
2. String subStr = str.substring\(0,5\);
3. System.out.println\(subStr\)\/\/Hello
```
### trim

String trim\(\):将字符串两边的空白\(空白有很多种，空格是其中之一\)去除掉，并将去除后的新字符串返回给我们。例如:
```java
1. String str =" Hello World ";
2. String trim = str.trim\(\);
3. System.out.println\(trim\);\/\/ Hello World
```
### charAt

char charAt\(int index\):用于给定一个下标位置，来获取该字符串中这个位置的字符。例如:

```java
1. String str = "HelloWorld";
2. char chr = str.charAt\(5\);
3. System.out.println\(chr\);\/\/W
```

### startsWith 和 endsWith

boolean startsWith\(String suffix\):用来判断当前字符串是否是以给定的字符串开始的。这里要注意。大小写是敏感的。boolean endsWith\(String suffix\):用来判断当前字符串是否是以给定的字符串结尾的。例如我们可以使用 endsWith\(\)就可以根据一个文件的名字来判断它是否是以".jpg",".gif"等字符串结尾来得知该文件是否为图片。
例如:
```java
1. String str = "java.jpg";
2. if(str.endsWith(".jpg")){
3.     System.out.println("是一张图片");
4. }else{
5.     System.out.println("不是一张图片");
6. }
```

### 大小写变换

String toUpperCase\(\):用来将当前字符串中的英文部分的字符全部变为大写后再将新的字符串返回String toLowerCase\(\):用来将当前字符串中的英文部分的字符全部变为小写后再将新的字符串返回例如，我们上网时常会要求我们输入验证码，图片中的英文可能是大写的，但我们输入时并不需要严格按照大小写输入却依旧可以验证成功。这就得力于该方法。我们可以将输入的验证码全部转换为大写，在将图片中显示的内容也全部转换为大写后再比较即可。
例如:
```java
1. String str = "HelloWorld";
2. String lower = str.toLowerCase\(\);
3. String upper = str.toUpperCase\(\);
4. System.out.println\("lower:"+lower\);\/\/helloworld
5. System.out.println\("upper:"+upper\);\/\/HELLOWORLD
```

### valueOf

字符串提供了很多重载的 valueOf\(\)方法，可以将其他基本类型的值以字符串的形式描述。
```java
static String valueOf\(int i\): 返回 int 参数的字符串表示形式
static String valueOf\(boolean b\): 返回 boolean 参数的字符串表示形式
static String valueOf\(char c\): 返回 char 参数的字符串表示形式
static String valueOf\(double d\): 返回 double 参数的字符串表示形式
static String valueOf\(char\[\] c\): 返回 char 数组参数的字符串表示形式
static String valueOf\(char\[\] c,int offset,int count\): 返回 char 数组参数的特定子数组的字符串表示形式。
static String valueOf\(float\): 返回 float 参数的字符串表示形式
static String valueOf\(long l\): 返回 long 参数的字符串表示形式
static String valueOf\(Object o\): 返回 Object 参数的字符串表示形式
```

例如:
```java
double pi = 3.1415926;
int value = 123;
boolean flag = true;
char\[\] charArr = { 'a', 'b', 'c', 'd', 'e', 'f', 'g' };
String str = String.valueOf\(pi\);
System.out.println\(str\);
str = String.valueOf\(value\);
System.out.println\(str\);
str = String.valueOf\(flag\);
System.out.println\(str\);
str = String.valueOf\(charArr\);
System.out.println\(str\); 
```

 

