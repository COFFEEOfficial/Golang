# SKD等介绍

SDK = software development kit(开发工具包)  (工具和API)

pkg ：图形化安装包

安装路径不要有中文和特殊符号

bin:指令（go/godoc/gofmt)

src:源代码


# 环境变量

GOROOT  指定SDK的安装路径  E：/go

Path 添加SDK的/bin目录

GOPATH  工作目录  go项目的工作路径

 系统变量适用于所有用户

# Typora使用

ctrl+shift+k  代码

ctrl+shift+m 公式

ctrl+B 加粗

ctrl+i 斜体

ctrl +u 下划线

# Go了解

#### 调用方法

eg1

time包有一个表示日期（年、月、日）和时间（小时、分钟、秒等）的Time类型。每一个time.Time值都有一个返回年份的Year方法。下面的代码使用这个方法打印当前年份：

```go
package main(

import{
       "fmt"
       "time"//导入 time 包，以便使用time.Time类型
}
func main(){
    var now time.Time = time.Now()//time.Now返回一个代表当前日期和时间的time.Time值
    var year int = now.Year()//time.Time值有一个返回年份的Year方法
    fmt.Println(year)
}
```



time.Now函数返回当前日期和时间的新Time值，我们将其存储在now变量中。然后，我们对now引用的值调用Year方法：

```go
now.Year()
```

///////////////////////////////////////////////////////////////////////

eg2.strings包有一个Replacer类型，可以在字符串中搜索子字符串，并且在每次该子字符串出现的地方用另一个字符串替换它：

```go
package main

import{
    "fmt"
    "strings"
}
func main(){
    broken := "G#r#cks!"
    replacer := strings.NewReplacer("#","o")//这将返回一个strings.Replacer ，其设置为将每个"#"替换成"o"
    fixed := replacer.Replace(broken)//对strings.Replacer调用Replace方法，并传递一个字符来进行替换
    fmt.Println(fixed)//打印Replace方法返回的字符串
}
```

#### Golang执行流程分析

如果是对源码先编译后，再执行（快）

go文件（源文件） >>>>>>（go build) >>>>>> 可执行文件（exe) >>>>结果

如果直接对源代码直接执行 go run源码（慢）

go文件 >>>>(go run)>>>>结果  

Golang执行流程分析
说明:两种执行流程的方式区别
1)如果我们先编译生成了可执行文件，那么我们可以将该可执行文件拷贝到没有go开发环
境的机器上，仍然可以运行
2)如果我们是直接go run go源代码，那么如果要在另外一个机器上这么运行，也需要go
开发环境,否则无法执行。
3)在编译时，编译器会将程序运行依赖的库文件包含在可执行文件中，所以，可执行文件
变大了很多。

#### 编译和运行

编译

1，有了go源文件，通过编译器将其编译成机器可以识别的二进制文件

2，在该源文件目录下，通过go build 对hello.go文件进行编译。可以指定生成的可执行文件名，在windows下必须是.exe后缀。
3，如果程序没有错误，没有任何提示，会在当前目录下会出现一个可执行文件(windows下是.exe Linux下是一个可执行文件)，该文件是二进制码文件，也是可以执行的程序。
4，如果程序有错误，编译时，会在错误的那行报错

5，运行有两种形式

运行

1，直接运行生成的可执行Go程序 比如hello.exe

2，通过运行工具 go run对源代码文件进行执行 

#### Go程序开发语法要求和注意事项

1，Go源文件以"go"为扩展名

 2，Go应用程序的执行入口是main()函数

3，Go严格区分大小写

4，Go方法由一条条语句构成，每个语句后不需要分号（自动加）

5，Go编译器是一行一行编译，不能把多条语句写在同一行

6，go语言定义的变量或者import的包如果没有使用到，代码不能编译通过

7，大括号成对存在

#### 常见开发错误和解决方法

1，文件路径和文件名错误

2，语法错误   |||||尝试看懂报错信息

####  COMMENT（注释）

在Golang中注释有两种形式

1，行注释：

基本语法：**// 注释文字**

快捷：**ctrl+/**

2，块注释（多行注释）

基本语法： **/***

​                            **注释内容**

​                      ***/**



细节：

1，对于行注释和块注释，被注释的文字，不会被Go编译器执行

2，块注释里面不允许有块注释嵌套

#### 规范的代码风格要求

正确的注释和注释风格：推荐行注释

正确的缩进和空白：

1,tab整体右移，shift+tab 左移

2,cmd:   gofmt -w 文件名.go   **//格式化**

 代码风格：不超过80个字符



# Golang 标准库API文档

1，API（Application Programming Interface，应用程序编程接口）是Golang提供的基本编程接口

2，https://studygolang.com/pkgdoc

​      https://golang.org/pkg



# 初 素人Goの变量了解





Go文件几乎总是有一个或多个import语句

###### 

​    1 package子句   package main

​     2   imports部分    import "fmt"

​     3   实际代码        func main(){

​                                                       fmt.Println("FUCKING BITCH")

​                                                }

  

### 调用函数

  当需要看程序在做什么时，使用Println函数

传递给它的任何参数都将在终端上打印（显示）出来，每个参数之间用空格分隔。打印完所有参数后，Println将跳到新的终端行。（这就是为什么“ln”在它名字的末尾。）



我们第一个程序中的代码是main包的一部分，但是Println函数在fmt包中（fmt代表“format.”）。为了能够调用Println，我们首先必须导入包含它的包。

   导入包后，我们可以通过输入包名、点和我们想要的函数名来访问它提供的任何函数。

Go程序模板

```go
package main

import "fmt"

func main(){
    fmt.Println(    在这里插入你的代码！     )
}
  
```



## 





### 变量的数据类型





基本数据类型

##### 字符类型



###### 字符串   

我们将字符串作为参数传递给Println 。字符串通常表示文本字符

双引号之间的文本，Go将把它们视为字符串



字符串通常用于表示一系列文本字符

字符串字面量由双引号（"）包围

Go的字符串不同，它是由字节组成的





注意事项和使用细节

1，Go语言的字符串字节使用UTF-8编码标识Unicode文本（乱码就是歌姬吧）

2，go中字符串一旦赋值，是不可变的

3，字符串两种表示形式

1）双引号，会识别转义字符

2）反引号，以字符串的原生形式输出，包括换行和特殊字符，可以实现防止攻击，输出源代码等效果

反引号就是esc下面的键 ``

4,字符串的拼接方式

在字符串中，换行符、制表符和其他难以包含在程序代码中的字符可以用转义序列来表示：反斜杠后跟表示另一个字符的字符。

escape char：

\n ：换行符

\t ： 制表符

\\"  ：双引号

\\\  ： 反斜杠

\t   :  一个制表位，实现对齐的功能

 

###### 符文（rune)//单个字符

符文用于表示单个字符

rune字面量由单引号（'）包围

没有专门的字符型，使用byte来保持单个字母字符

Go程序几乎可以使用地球上任何语言的任何字符，因为Go使用Unicode标准来存储rune。rune被保存为数字代码，而不是字符本身，如果你把rune传递给fmt.Println，你会在输出中看到数字代码，而不是原始字符。

与字符串字面量一样，转义序列也可以用在rune字面量中，用来表示程序代码中难以包含的字符

##### 布尔值

布尔值只有true    false 

条件语句只在条件为true或false时才会导致代码段运行

##### 数字//整数，浮点数

定义数字：只需要输入数字即可

Go将整数和浮点数视为不同的类型，可以使用小数点来区分整数和浮点数

fmt.Printf( )： 可以用于格式化输出

```go
fmt.Printf("n1的类型 %T "，n1 )
```



浮点型/小数类型

基本介绍 小树类型就是用于存放小数的 

小数类型的分类 ：

说明

1，按数字来区分表数范围

2，浮点数都是有符号的

3，float64的精度比float32的要准确

浮点数使用细节

浮点型使用细节
1)Golang浮点类型有固定的范围和字段长度，不受具体os(操作系统)的影响。

2)Golang 的浮点型默认声明为float64类型。
3)浮点型常量有两种表示形式
十进制数形式:如:5.12.512(必须有小数点)
科学计数法形式:如:5.1234e2 = 5.12* 10的2次方5.12E-2 = 5.12/10的2次方4)

4）通常情况下，应该使用float64，因为它比float32更精确。



##### 数学运算与比较

Go的基本数学运算符的工作方式与大多数其他语言一样。符号+表示加法，–表示减法，*表示乘法，/表示除法。

你可以使用<和>来比较两个值，看看其中一个值是否小于或大于另一个值。你可以使用==（这是两个等号）来查看两个值是否相等，以及！=（这是一个感叹号和一个等号，读作“不等于”）来查看两个值是否不相等。<=测试第二个值是否大于或等于第一个值，>=测试第二个值是否小于或等于第一个值。

比较结果是一个布尔值，要么是true，要么是false。



##### 类型总结

math.Floor 函数将浮点数向下取舍为最接近的整数

strings.Title函数将字符串转化为首字母大写

将数字作为参数传递给Floor函数，将字符串作为参数传递给Title函数，是有意义的

Go是静态类型的，这意味着它甚至在程序运行之前就知道值的类型是什么。函数期望它们的参数具有特定的类型，它们的返回值也具有类型

你可以通过将任何值传递给reflect包的TypeOf函数，来查看它们的类型
int 整型。保存数字

float64   浮点数。保存带小数部分的数字（类型名中的64是因为要用64位的数据来保存浮点数。保存带小数部分的数字（类型名中的64是因为要用64位的数据来保存

bool   布尔值 true  or false

string  字符串 通常表示文本字符的一系列数据

## 



#### 派生/复杂数据类型（后面学）

1，指针（pointer）

2，数组

3，结构体（struct）

4，管道（Channel)

5，函数

6，切片（slice）

7，接口（interface）

8，map

### 声明变量（定义变量）

###### 变量介绍

变量是包含值的一块存储

变量是程序的基本组成单位，变量相当于内存中一个数据存储空间的表示

使用变量声明为变量命名。只需使用var关键字，后跟所需的名称以及变量将保存的值的类型

一旦你声明了一个变量，就可以用=（这是一个单等号）为它分配该类型的任何值

1，第一种，指定变量类型，声明后若不赋值，使用默认值，下一个部分介绍

2，根据值自行判定变量类型（类型推导）

3，短变量声明

可以在同一语句中为多个变量赋值。只需将多个变量名                            放在=的左侧，将相同数量的值放在右侧，并使用逗号分隔。

eg  :

```go
length, width = 1.2,2.4 
```

###### 一次性声明多个变量的方式

```go
package main
import "fmt"

func main(){
    //一次性声明多个变量的方式1
    var n1, n2, n3 int
    fmt.Println("n1=",n1, "n2=", n2, "n3=", n3)
    
    //一次性声明多个变量的方式2
    var n1, name, n2 = 100, "StudyBitch" ,888.88
    fmt.Println("n1= ",n1, "name=", name, "n2=", n2)
    
    //一次性声明多个变量的方式3
    n1, name, n2 = 100, "StudyBitch" ,888.88
    fmt.Println("n1= ",n1, "name=", name, "n2=", n2)
}
```

###### 全局变量

如何一次性声明多个全局变量 （在go中函数外部定义变量就是全局变量）？

```go
package main
import "fmt"

var n1 = 100
var n2 = 200
var name = "StudyBitch"

func main(){
    fmt.Println("n1= ",n1, "name=", name, "n2=", n2)
}
```



###### 赋值与使用

```go
package main

import "fmt"

func main(){
    var quantity int 
    var length, width float64
    var customerName string  //声明变量
    
    quantity = 4
    length, width = 1.2, 2.4
    customerName = "Damon Cole" //给变量赋值
    
    fmt.Println(customerName)
    fmt.Println("has ordered", quantity,"sheets")
    fmt.Println("each with an erea of")
    fmt.Println(length*width, "square meters")
    
}

```

你可以为现有变量分配新值，但它们必须是相同类型的值

如果在声明变量的同时为其赋值，通常可以在声明中省略变量类型。这个分配给变量的值的类型将用作该变量的类型。

eg:

```go
var quantity = 4
var length, width =1.2,2.4
var c
```



###### 零值

如果声明一个变量但没有赋值，该变量将包含其类型的零值

对于数值类型，就是0；

```go
var mylnt int
var myFloat float64
fmt.Println(mylnt, myFloat)
```

但是对于其他类型来说，0值是无效的，因此该类型的零值可能是其他值，比如字符串变量的零值是空字符串，布尔变量的零值是false。

###### 短变量声明 

如果你声明变量时就知道它的初始值是什么，那么更具有代表性的是使用短变量声明。你不必很明确地声明变量的类型并在之后使用=为其赋值，而是同时使用：=

不需要明确地声明变量的类型；赋给变量的值的类型成为该变量的类型。

：=左侧的变量不应该是已经声明过的，否则会导致编译错误

```go
quantity := 4
length, width := 1.2, 2.4
customerName :="FUCKING BITCH"
```



###### 变量使用的注意事项

1，该区域的数据值可以在同一类型范围内不断变化，但是不能改变数据类型

2，变量在同一个作用域内不能重名

3，变量 = 变量名 + 值 + 数据类型



###### 命名规则

 1.名称必须以字母开头，并且可以有任意数量的额外的字母和数字。

2.**如果变量、函数或类型的名称以大写字母开头，则认为它是导出的，可以从当前包之外的包访问它。**（这就是为什么fmt.Println中的P是大写的：这样它就可以在main包或任何其他包中使用。）如果变量/函数/类型的名称是以小写字母开头的，则认为该名称是未导出的，只能在当前包中使用。

3.如果一个名称由多个单词组成，那么第一个单词之后的每个单词都应该首字母大写，并且它们应该连接在一起，中间没有空格，比如topPrice、RetryConnection，等等。（名称的第一个字母只有在你想从包中导出时才应大写。）这种样式通常称为驼峰大小写，因为大写字母看起来像驼峰

4.当名称的含义在上下文中很明显时，Go社区的惯例是缩写它：用i代替index，用max代替maximum，等等



#### 基本数字类型的转换

Go中的数学运算和比较运算，为变量分配新值要求包含的值具有相同的类型。如果不是的话，则在尝试运行代码时会报错。

解决方法是使用转换，它允许你将值从一种类型转换为另一种类型。只需提供要将值转换成的类型，后面紧接着是在圆括号中的要转换的值

```go
var myInt int = 2
float64 (myInt)
```



Go在不同类型的变量之间赋值时需要显式转换，也就是说Golang中数字类型不能自动转换

转换的基本语法：表达式T（v)将值v转换为类型T

  T就是数据类型，比如int32,int64,float32等等

v就是要转换的变量

➢细节说明

1）Go中，数据类型的转换可以是从表示范围小-->表示范围大，也可以范围大-- ->范围小
2)被转换的是变量存储的数据(即值)，变量本身的数据类型并没有变化!
3)在转换中，比如将int64转成int8，编译时不会报错，只是转换的结果是按溢出处理，和我们希望的结果不一样。


```go
package main

func main() {

	var n1 int32 = 12
	var n2 int64
	var n3 int8
	n2 = n1 + 20//wrong
	n3 = n1 + 20//wrong
}

修改：
   package main

func main() {

	var n1 int32 = 12
	var n2 int64
	var n3 int8
    n2 = int64(n1) + 20//wrong
    n3 = int8(n1) + 20//wrong
}
```

 

```go
func main(){
    var n1 int32 = 12
    var n3 int8
    var n4 int8
    n4 = int8(n1) + 127 //编译通过，但是结果不是127+12
    n3 = int8(n1) + 128//编译不通过
}
```

####  基本数据类型转string

方式1，fmt.Sprintf("%参数"，表达式)

1，参数需要和表达式的数据类型相匹配

2，fmt.Sprintf（）后返回转换后的字符串


方法2，使用strconv包的函数
```go
package main

import (
	"fmt"
	"strconv"
	_ "unsafe"
)

//演示golang中基本数据练习转成string使用
func main() {

	var num1 int = 99
	var num2 float64 = 23.456
	var b bool = false
	var myChar byte = 'h'
	var str string //空的str
	//用fmt.Sprintf
	str = fmt.Sprintf("%d", num1)
	fmt.Printf("str type %T  str=%v\n", str, str)
	str = fmt.Sprintf("%f", num2)
	fmt.Printf("str type %T  str=%v\n", str, str)
	str = fmt.Sprintf("%t", b)
	fmt.Printf("str type %T  str=%v\n", str, str)
	str = fmt.Sprintf("%c", myChar)
	fmt.Printf("str type %T  str=%v\n", str, str)

	//使用strconv包
	var num3 int = 99
	var num4 float64 = 23.456
	var b2 bool = false
	str = strconv.FormatInt(int64(num3), 10)
	fmt.Printf("str type %T  str=%v\n", str, str)
	//str = strconv.FormatFloat(num4,'f',10,64)
	//说明：'f'： 格式   10：表示小数位保留10位   64：表示这个数是float64
	str = strconv.FormatFloat(num4, 'f', 10, 64)
	fmt.Printf("str type %T  str=%v\n", str, str)

	str = strconv.FormatBool(b2)
	fmt.Printf("str type %T  str=%v\n", str, str)

}
```







#### string转基本数据类型

1）使用strconv包的函数

```go
package main

import (
	"fmt"
	"strconv"
)

//演示golang中string转成基本数据类型

func main() {

	var str string = "true"
	var b bool
	//b ,_ = strconv.ParseBool(str 	)
	//1,该函数会返回两个值(value bool, err error)
	//2,我只要value bool，不要 err所以用_忽略
	b, _ = strconv.ParseBool(str)
	fmt.Printf("b type %T  b=%v\n", b, b)

	var str2 string = "123456"
	var n1 int64
	var n2 int
	n1, _ = strconv.ParseInt(str2, 10, 64)
	//str2,   10:十进制   64：64位
	fmt.Printf("n1 type %T  n1=%v\n", n1, n1)
	n2 = int(n1)
	fmt.Printf("n2 type %T  n2=%v\n", n2, n2)

	var str3 string = "123.456"
	var f1 float64
	f1, _ = strconv.ParseFloat(str3, 64)
	fmt.Printf("f1 type %T  f1=%v", f1, f1)

}

b type bool  b=true
n1 type int64  n1=123456
n2 type int  n2=123456
f1 type float64  f1=123.456
```

说明：因为返回的是float64,int64,所以希望得到其他的(float32等) 要进行转换

注意事项
➢在将String类型转成基本数据类型时，**要确保String类型能够转成有效的数据**，比如我们
可以把"123",转成一个整数，但是不能把"hello"转成一个整数，如果这样做，Golang直接将其转成默认值

```go
var str4 string = "hello"
	var n3 int64 = 11
	n3, _ = strconv.ParseInt(str4, 10, 64)
	fmt.Printf("n3 type %T  n3=%v\n", n3, n3)//如果没有转成功，n3为默认值
```

### 复杂数据类型

##### 指针

基本介绍

1，基本数据类型，变量存的就是值，也叫值类型

2，获取变量的地址，用&，  比如var num int ,获取num的地址，&num

分析基本数据类型在内存的布局

3,指针类型，指针变量存的是一个地址，这个地址指向的空间存的才是值

var **ptr** *int = &num

4，获取指针类型所指向的值，使用： * ，比如 var ptr  *int,.

使用*ptr 获取 ptr指向的值

**指针的使用细节**

1)值类型，都有对应的指针类型，形式为（星号）数据类型，比如int的对应的指针就是（星号）int, float32对应的指针类型就是*float32,依次类推。
2)值类型包括:基本数据类型int系列, float系列, bool, string 、数组和结构体struct



### 值类型和引用类型

  1，值类型 ，基本数据类型，数组 ，结构体

值类型：变量直接存储值，内存通常在栈中分配


  2，引用类型，指针，slice切片，map，管道chan, interface

引用类型:变量存储的是一个地址，这个地址对应的空间才真正存储数据(值)，内存通常在堆上分配，当没有任何变量引用这个地址时，该地址对应的数据空间就成为一个垃圾，由GC来回收。

# 字符

### 标识符基本使用

标识符概念

1）Golang对各种变量、方法、函数等命名时使用的字符序列称为标识符

2)凡是自己可以起名字的地方都叫标识符

标识符的命名规则

1)由26个英文字母大小写，0-9 ，__组成_

2)数字不可以开头。

3)Golang中严格区分大小写。

4)标识符不能包含空格。

5)下划线"_"本身在Go中是一个特殊的标识符，称为空标识符。可以代表任何其它的标识符，但是它对应的值会被忽略(比如:忽略某个返回值)。所以仅能被作为占位符使用，不能作为标识符使用。

6)不能以系统保留关键字作为标识符，比如 break，if 等等...


标识符命名事项

1)包名:保持package的名字和目录保持一致，尽量采取有意义的包名，简短，有意义,
不要和标准库不要冲突     fmt

2)变量名、函数名、常量名:采用驼峰法。

3)如果变量名、函数名、常量名首字母大写，则可以被其他的包访问;如果首字母小写，
则只能在本包中使用(注:可以简单的理解成，首字母大写是公有的，首字母小写是私有的)  **没有public ，private 等关键字**



保留关键字和预定义标识符

### 运算符

#### 运算符分类

运算符是一种特殊的符号，用以表示数据的运算、赋值和比较等
1)算术运算符

2)赋值运算符

3)比较运算符

4)逻辑运算符

5)位运算符

6)其它运算符

7）三元运算符（反转了 go语言里面没有）

##### 算术运算符

算数运算符是对数值类型的变量进行运算的，比如，加减乘除


使用案例：

```go
 package main
 import (
	"fmt"
)
 func main(){
   
     fmt.Println(10/4)                   //2
	 var n1 float32 = 10/4
	 fmt.Println(n1)                     //2
	 var n2 float32 = 10.0/4
	 fmt.Println(n2)                     //2.5
	 fmt.Println("10%3=",10%3)           //1
	 fmt.Println("-10%3=",-10%3)         //-1
	 fmt.Println("10%-3=",10%-3)         //1
	 fmt.Println("-10%-3=",-10%-3)       //-1  
	 //a % b = a - a / b * b
     
 }
```

**a % b = a - a / b * b**

**细节说明：**

1）Golang的自增自减只能当作一个独立语言使用，不能这样使用：  <u>*b := a++或者 b := a--*</u>，即++和-只能独立使用
2）Golang的++和--只能学在变量后面，不能写在变量的前面，即，只有 a++,a--，没有 ++a,--a

##### 关系运算符（比较运算符）

1)关系运算符的结果都是bool型，也就是要么是true，要么是false

2)关系表达式经常用在i**f结构**的条件中或**循环结构**的条件中

3)关系运算符组成的表达式，我们称为关系表达式 ：a>b

4）比较运算符 “ ==” 不能写成 ''=''

##### 逻辑运算符

用于连接多个条件（一般来说就是关系表达式），最终结果也是bool值


```go
 package main
 import (
	 "fmt"
 )
 func main
      	var  age int = 40
	//逻辑运算符的使用  &&
	if age >30 && age <50{
		fmt.Println("ok1")
	}
	if age > 30 && age <40{
		fmt.Println("ok2")
	}
	//逻辑运算符的使用 ||
	if age >30 || age <50{
		fmt.Println("ok3")
	}
	if age > 30 ||age <40{
		fmt.Println("ok4")
	}
     //逻辑运算符的使用  !
	 if age >30 {
		fmt.Println("ok5")
	}
	if !(age>30){
		fmt.Println("ok6")
    }
}
```

注意事项和细节说明

1)**&&也叫短路与**:如果第一个条件为false，则第二个条件不会判断，最终结果为false

2)**||也叫短路或**:如果第一个条件为true，则第二个条件不会判断，最终结果为true

```go
 package main
 import (
	 "fmt"
 )
 func test() bool{
       fmt.Println("test....")
	   return true
 }
 func main(){
	 var i int = 10
	 //短路与
	 //说明 因为 i<9 为false  ,所以后面的test()不执行
	 if i < 9 && test(){
		 fmt.Println("ok")
	 }
     
	 //短路或
	 //说明 因为 i>9 为true  ,所以后面的test()不执行
	 if i > 9 || test(){
		fmt.Println("hello")
	}
	
}
```

##### 赋值运算符

赋值运算符就是将某个运算后的值，赋给指定的变量!

赋值运算符的分类
 =  ：简单的赋值运算符，将一个表达式的值赋给一个左值| C=A+ B将A+ B表达式结果赋值给C

+= ：相加后再赋值|C +=A等于C=C+A

-=  ：相减后再赋值|C-=A等于c=c-A
星号= ：相乘后再赋值|*=A等于c= C乘A
/=  : 相除后再赋值|C/=A等于c=c/A
%= : 求余后再赋值|C%=A等于c=C %A


说明：

1）赋值运算的执行顺序是从右向左进行

2）赋值运算符的左边 只能是**变量**  ，右边可以是**变量、表达式、常量值**

表达式：任何有值都可以看作表达式

##### 位运算符


##### 其他运算符


```go
 package main
 import(
	 "fmt"
 )
 func main(){

	a := 100
	fmt.Println("a的地址=",&a)
	var ptr *int = &a
	fmt.Println("ptr 指向的值=",*ptr)

	var n int 
	var i int = 10
	var j int = 12
	//传统的三元运算
	// n = i > j ? i : j
	if i>j{
		n = i
	} else{
		n = j
	}
	fmt.Println("n=",n)
}
```



#### 运算符优先级

# 获取用户终端输入（键盘输入语句）

介绍：在编程中，需要接收用户输入的数据，可以使用键盘输入语句来获取



步骤：

1）导入fmt包

2）调用fmt包的fmt.Scanln() 或者 fmt.Scanf()

```go
package main

import "fmt"

func main() {
	//接收用户信息 ：姓名，年龄，薪水，是否通过考试
	//方式1，fmt.Scanln
	var name string
	var age byte
	var sal float32
	var isPass bool
	fmt.Println("请输入姓名 ")
	//当程序执行到 fmt.Scanln(&name)，程序会停在这里，等待用户输入，并回车
	fmt.Scanln(&name)
	fmt.Println("请输入年龄 ")
	fmt.Scanln(&age)
	fmt.Println("请输入薪水 ")
	fmt.Scanln(&sal)
	fmt.Println("请输入是否通过考试 ")
	fmt.Scanln(&isPass)
fmt.Printf("名字是%v\n 年龄是%v\n 薪水是%v\n 是否通过考试%v\n", name, age, sal, isPass)
}
```



2) 使用fmt.Scanf()获取

   ```go
   	fmt.Println("请输入你的姓名，年龄，薪水，是否通过考试，使用空格隔开")
   	fmt.Scanf("%s %d %f %t", &name, &age, &sal, &isPass)
   	fmt.Printf("名字是%v\n 年龄是%v\n 薪水是%v\n 是否通过考试%v\n", name, age, sal, isPass)
   ```


# 位运算及原码 反码 补码

##### 位运算符

"&"  ：按位与运算符"&"是双目运算符。其功能是参与运算的两数各对应的二进位相与。**运算规则是:同时为1,结果为1,否则为0**

"|"   : 按位或运算符"|"是双目运算符。其功能是参与运算的两数各对应的二进位相或  **运算规则是:有一个为1,结果为1,否则为0**

"^":按位异或运算符“"是双目运算符。其功能是参与运算的两数各对应的二进位相异或.**运算规则是:当二进位不同时,结果为1,否则为0**
"<<":  左移运算符"<<"是双目运算符。其功能把"<<"左边的运算数的各二进位全部左移若干位，高位丢弃,低位补0。左移n位就是乘以2的n次方。

">>"右移运算符">>"是双目运算符。其功能是把">>"左边的运算数的各二进位全部右移若干位,右移n位就是除以2的n次方

例题：

```go
package main
import "fmt"
func main(){
	var a int = 1 >> 2
	var b int = -1 >> 2
	var c int = 1 << 2
	var d int = -1 << 2
	//a,b,c,d结果是多少？ 
	fmt.Println("a=", a)  //0
	fmt.Println("b=", b)  //-1
	fmt.Println("c=", c)  //4
	fmt.Println("d=", d) 
}
```



##### 原码反码补码

对于有符号的而言:
1)二进制的最高位是符号位:0表示正数,1表示负数

1 ===》 [0000 0001]      -1 ===》 [1000 0001]



2)正数的原码，反码，补码都一样

3)负数的反码=它的原码符号位不变，其它位取反(0->1,1->0)

4)负数的补码=它的反码+1

1 ===》原码[0000 0001]  反码[0000 0001] 补码[0000 0001]

-1 ===》原码[1000 0001] 反码[1111 1110] 补码[1111 1111]

5)0的反码，补码都是0

6)在计算机运算的时候，都是以补码的方式来运算的.

##### 位运算深度讲解

2&3

2的补码 0000 0010

3的补码 0000 0011

2&3       0000 0010 => 2

```go
package main
import "fmt"

func main() {
	//位运算的测试
	fmt.Println(2 & 3)  //2
	fmt.Println(2 | 3)  //3
	fmt.Println(2 ^ 3)  //1
	fmt.Println(-2 ^ 2) //-4
    fmt.Println(1 >> 2) //0
	fmt.Println(1 << 2) //4
}
```

# 程序流程控制

在程序中，程序运行的流程控制决定程序是如何执行的，是我们必须掌握的，主要有三大流程控制语句

1）顺序控制

2）分支控制

3）循环控制



### 顺序控制

程序从上到下逐步执行，中间没有任何判断和跳转，因此程序按照默认的流程执行

Golang中定义变量时采用合法的前向引用

### 分支控制

分支控制if -else 介绍

分支控制就是让程序有选择的执行

1）单分支

2）双分支

3）多分支

##### 单分支

基本语法

if  条件表达式{

​                     执行代码块

}

说明：当条件表达式为true 时，就会执行{}的代码

注意{}是必须有的

```go
package main
import (
	"fmt"
)

func main() {
	var age int
	fmt.Scanln(&age)
	if age > 18 {
		fmt.Println("打个胶先")
	}
}
```

细节说明： Go的if 还有一个强大的地方就是条件判断语句里面允许声明一个变量，这个变量的作用域只能在该条件逻辑块内，其他地方就不起作用了



##### 双分支

基本语法

if  条件表达式{

​                     执行代码块1

}else{

​                      执行代码块2

}

```go
package main

import "fmt"
func main() {
	var x int = 4
	var y int = 1
	if x > 2 {
		if y > 2 {
			fmt.Println(x + y)
		}
		fmt.Println("你就是歌姬吧")
	} else {
		fmt.Println("x=", x)
	}
    // 输出  你就是歌姬吧
}
```

##### 多分支

基本语法

if  条件表达式{

​                     执行代码块1

}else if   条件表达式2{

​                      执行代码块2

}

 .......

else{

​                      执行代码块n

}



说明：

1）多分支的判断流程如下

​    1，先判断条件表达式1是否成立，如果为真，就执行代码块1

​     2，如果条件表达式1为假，就去判断条件表达式2是否成立，如果条件表达式2为真，就执行代码块2

​     3，以此类推

​      4，如果所有条件表达式都不成立，就执行else的语句块

2）else不是必须的

3）**多分支最终只能有一个执行入口**



```go
package main
import (
	"fmt"
)
func main() {
	var score int
	fmt.Scanln(&score)
	if score == 100 {
		fmt.Println("奖励一辆BMW")
	} else if score > 80 && score <= 99 {
		fmt.Println("奖励一个iPhone")
	} else if score >= 60 && score <= 80 {
		fmt.Println("奖励一辆ipad")
	} else {
		fmt.Println("你就是歌姬吧")
	}
}
```

```go
//使用陷阱___只输出ok1
	var n int = 10
	if n > 9 {
		fmt.Println("ok1") //输出ok1
	} else if n > 6 {
		fmt.Println("ok2")
	} else if n  > 3 {
		fmt.Println("ok3")
	}
```

##### 嵌套分支

在一个分支结构中又完整地嵌套了另一个完整的分支结构，里面的分支的结构称为内层分支，外面的分支机构称为外层分支

基本语法

if 条件表达式{

​            if 条件表达式{

​                  }else{

​                  }

}

##### switch

基本介绍

1）switch 语句用于基于不同条件执行不同动作，每一个case分支都是唯一的，从上到下逐一测试，直到匹配为止

2）匹配项后面也不需要再加break

上图说明和总结

1）switch的执行的流程是，先执行表达式，得到值，然后和case的表达式进行比较，如果相等，就匹配到，然后执行对应的case的语句块2，然后退出switch控制

2）如果switch 的表达式的值没有和任何case的表达式匹配成功，则执行default 的语句块，执行后退出switch的控制

3）golang的case表达式可以有多个，之间用 逗号间隔

4）golang中的case语句块不需要写break, 因为默认会有 ，即在默认情况下，当程序执行完case语句后，就直接退出switch控制结构

```go
package main
import (
	"fmt"
)
func main() {
	var key byte
	fmt.Println("请输入一个字符,a,b,c,d,e,f,g")
	fmt.Scanf("%c", &key)

	switch key {
	case 'a':
		fmt.Print("znw")
	case 'b':
		fmt.Print("zxh")
	case 'c':
		fmt.Print("zyk")
	default:
		fmt.Println("寄")
    }
}
```

细节讨论：

1. case后是一个表达式(即:常量值、变量、一个有返回值的函数等都可以

2. case后的各个表达式的值的数据类型，必须和 switch 的表达式数据类型一致

   ```go
       var n1 int32 = 20
   	var n2 int32 = 20
   	switch n1 {
   	case n2:
   		fmt.Println("ok")
   	default:
   		fmt.Println("no")
   	}
   ```

 
3. case后面可以带多个表达式，使用逗号间隔。比如case表达式1,表达式2 ...

4. case后面的表达式如果是常量值(字面量)，则要求不能重复

5. case后面不需要带break ,程序匹配到一个case后就会执行对应的代码块，然后退出switch，如果一个都匹配不到，则执行default

6) default语句不是必须的.

7. switch后也可以不带表达式，类似多个if --else分支来使用。

8.  switch后也可以直接声明/定义一个变量，分号结束，不推荐。


9. switch穿透-fallthrough，如果在case语句块后增加fallthrough ,则会继续执行下一个case,也叫switch穿透。

  ```go
  func main() {
  	var num int = 10
  	switch num {
  	case 10:
  		fmt.Println("ok1")
  		fallthrough
  	case 20:
  		fmt.Println("ok2")
  	case 30:
  		fmt.Println("ok3")
  	default :
  		fmt.Println("?")
  	}
  }
  ```

-----

  10，Type Switch : switch语句还可以被用于 type-switch 来判断某个 interface 变量中实际指向的变量类型



### 循环控制

让代码可以循环地执行



##### for循环控制

**基本语法：**

for  循环变量初始化 ; 循环条件 ; 循环变量迭代 {

​                     循环操作（语句）

}

```go
package main
import(
	"fmt"
)
func main(){
	for i := 1; i <= 10 ; i++ {
		fmt.Println("你就是个寄吧",i)
	}
}
```

**for循环执行的顺序说明**：

1，执行循环变量初始化，比如 i :=1

2,   执行循环条件 ，比如 i<=10

3，如果循环条件为真，就执行循环操作：比如fmt.Println("你就是个寄吧",i)

4，执行循环变量迭代，比如 i++

5，反复执行 2，3，4步骤，直到循环条件为false，就退出for循环



**注意事项和细节说明**

1，循环条件是返回一个布尔值的表达式

2，for循环的第二种使用方式

```go
// for 循环的第二种写法
	j := 1 //循环变量初始化
	for j <= 10 {  //循环条件
		fmt.Println("打胶", j)
		j++ //循环变量迭代
	}
```

3，for循环的第三种使用方式

for{

​			//循环执行语句

}

无限循环，加break使用

```go
//for 循环的第三种写法
	for ； ；{
		fmt.Println("j")
		j++
		if j > 16 {
			fmt.Println(j)
			break
		}
	}
//或
for{
		fmt.Println("j")
		j++
		if j > 16 {
			fmt.Println(j)
			break
		}
	}
```





4，Golang 提供for-range的方式，可以方便遍历字符串和数组(注:数组的遍历，我们放到讲数组的时候再讲解)，案例说明如何遍历字符串。


```go
package main
import (
	"fmt"
)
func main() {
	// 字符串遍历方式 1 -传统方式
	var str string = "hello,world!"
	for i := 0; i < len(str); i++ {
		fmt.Printf("%c\n", str[i])
	}
	// 字符串遍历方式 2 - for - range
	str = "abc-ok"
	for index, val := range str {
		fmt.Printf("index=%d val=%c\n", index, val)
	}
}
```

细节：

如果字符串有中文，那么传统的遍历字符串方式就会出现乱码，因为传统对字符串的遍历是按字节来遍历，一个汉字在utf8编码是对应3个字节

如何解决 ：需要将str转成[]rune切片

```go
var str string = "hello,world!哈哈"
	str2 := []rune(str)
	for i := 0; i < len(str2); i++ {
		fmt.Printf("%c\n", str2[i])
	}
```

而for-range 有汉字也行


##### while和do...while的实现

go语言中没有while和do..while语法

1）for循环实现while的效果

```go
循环变量初始化
for{
    if 循环条件表达式{
        break//跳出for循环
    }
	循环操作（语句）
    循环变量迭代
}
```

说明：

1，该for循环是无限循环

2，break语句用于跳出for循环

eg.

```go
package main
import (
	"fmt"
)
func main() {
	//使用while方式输出10句"hello world"
	var i int = 1
	for {
		if i > 10 {
			break
		}
		fmt.Println("hello world")
		i++
	}
}
```



do...while的实现

```go
循环变量初始化
for{
	循环操作（语句）
	循环变量迭代
	if 循环条件表达式{
	break//跳出for循环
	}
}
```

说明：

1，先执行，再判断，因此至少执行一次

2，当循环条件成立后，就会执行break

```go
var j int = 1
	for {
		fmt.Println("hello jiba", j)
		j++
		if j > 10 {
			break
		}
	}
```

##### 多重循环

1)将一个循环放在另一个循环体内，就形成了嵌套循环。在外边的for称为外层循环在里面的for循环称为内层循环。【建议一般使用两层,最多不要超过3层】
2)实质上，嵌套循环就是把内层循环当成外层循环的循环体。当只有内层循环的循环条件为 false时，才会完全跳出内层循环，才可结束外层的当次循环，开始下一次的循环。
3)外层循环次数为m次，内层为n次，则内层循环体实际上需要执行m*n次

```go
package main
import (
	"fmt"
)

func main() {
	var classNum int = 2
	var stuNum int = 3
	var totalSum float64 = 0.0
	var passCounter int = 0
	for j := 1; j <= classNum; j++ {
		var sum float64 = 0.0
		for i := 1; i <= stuNum; i++ {
			var score float64
			fmt.Printf("请输入第%d班第%d个学生的成绩\n", j, i)
			fmt.Scanln(&score)
			sum += score
			if score >= 60 {
				passCounter++
			}
		}
		totalSum += sum
		fmt.Printf("第%d个班级平均分是%v\n", j, sum/float64(stuNum))
	}
	fmt.Printf("所有班的平均分是%v\n", totalSum/(float64(stuNum)*float64(classNum)))
	fmt.Printf("及格人数为%v\n", passCounter)
}
```



案例 ：

1，打印空心金字塔

```go
package main
import (
	"fmt"
)
func main() {
	var n int
	fmt.Println("请输入金字塔的高度")
	fmt.Scanln(&n)
	//i表示层数
	for i := 1; i <= n; i++ {
		for k := 1; k <= n-i; k++ {
			fmt.Print(" ")
		}
		//j表示每层打印多少*
		for j := 1; j <= i*2-1; j++ {
			if j == 1 || j == 2*i-1 || i == n {
				fmt.Print("*")
			} else {
				fmt.Print(" ")
			}
		}
		fmt.Println()
	}
}
```

2，打印出九九乘法表

```go
package main
import "fmt"
func main() {
	// i表示层数
	for i := 1; i <= 9; i++ {
		for j := 1; j <= i; j++ {
			fmt.Printf("%v * %v = %v\t", j, i, j*i)
		}
		fmt.Println()
	}
}
```



### 跳转控制

##### break 

break终止整个循环

看一个具体需求，引出break
随机生成1-100的一个数，直到生成了99这个数，看看你一共用了几次?
分析:编写一个无限循环的控制，然后不停的随机生成数，当生成了99时，就退出这个无限循环==break提示使用
这里我们给大家说一下，如下随机生成1-100整数.


```go
var count int = 0
	rand.Seed(time.Now().UnixNano())
	for {
		n := rand.Intn(101)
		count++
		if n == 99 {
			break
		}
	}
	fmt.Printf("生成 99 一共用了%v次", count)
```



基本介绍：
break语句用于终止某个语句块的执行，中断for循环或者跳出switch语句

注意事项和细节说明 ：

1）break语句出现在多层嵌套的语句块中 ，可以通过标签来指明要终止的是哪一层语句块

2 ）标签的基本使用

```go
label1 :{ ....
label2    { 
label3       { ... 
               break label2
				}
          }
	}
```

```go
label2:
	for i := 0; i < 4; i++ {
		// label1: //设置一个标签
		for j := 0; j < 10; j++ {
			if j == 2 {
				break label2 // break 默认会跳出最近的for循环
			}
			fmt.Println("j=", j)
		}
	}
```

说明：

1，break 默认会跳出最近的 for 循环 

2，break 可以指定标签， 跳出标签对应的for循环

##### continue

continue 终止本次循环

1，continue语句用于结束本次循环，继续执行下一次循环

2，continue语句出现在多次嵌套的循环语句体中时，可以通过标签指明要跳过的是哪一层循环

##### goto

Go语言的goto语句可以无条件地转移到程序中指定的行

##### return

return使用在方法或者函数中， 表示跳出所在的方法或函数

如果return是在普通的函数，则表示跳出该函数，即不再执行函数中return后面代码

基本语法

go函数支持返回多个值

```go
func 函数名 （形参列表） （返回值类型列表） {
    语句
    return 返回值列表
}
```

1，如果返回多个值时，在接收的时候，希望忽略某个返回值，呢可以使用 _ 符合表示占位忽略

```go
package main
import "fmt"
func getSumAndSub(n1 int, n2 int) (int, int) {
	sum := n1 + n2
	sub := n1 - n2
	return sum, sub
}
func main() {
	res1, res2 := getSumAndSub(1, 2)
	fmt.Printf("res=%v res2=%v\n", res1, res2)
	_, res3 := getSumAndSub(1, 2)
	fmt.Println("res3=", res3)
}
```

2，如果返回值只有一个， （返回值类型列表) 可以不写（）



# 函数，包，错误处理

##### 函数

函数基本概念 ： 为完成某一功能的程序指令（语句）的集合 ，称为函数

基本语法：

func 函数名（形参列表)(返回值列表) {

​					执行语句

​					return 返回值列表

}

1，形参列表 ：表示函数的输入

2，函数中的语句，表示为了实现某一功能代码块

3，函数可以有返回值，也可以没有



##### 包的引出和使用原理

包的本质实际上就是创建不同的文件夹，来存放程序文件

包的基本概念：go的每一个文件都是属于一个包的，也就是说 go是以包的形式来管理文件和项目目录结构的

包的作用：

1，区分相同名字的函数，变量等标识符

2，当程序文件很多时，可以很好地管理项目

3，控制函数，变量等访问范围，即作用域

包的相关说明

> 打包基本语法
>
> package 包名
>
> 引入包的基本语法
>
> import “包的路径”

##### 包的注意事项和细节说明：

1，在给一个文件打包时，该包对应一个文件夹，比如这里的utls文件夹对应的报名就是utls，文件包名通常和文件所在的文件夹名一致，一般为小写字母

2，当一个文件要使用其他包函数或变量时，需要先引入对应的包

1，引入方式1， import ”包名“

2，引入方式2，

​			import{

​						”包名“

​						”包名“

}

3，package 指令在文件第一行，然后是import指令

4，在import包时，路径从SKD的src下面开始，不用带src，编译器会自动从src下开始引入（旧版）

5，为了让其他包的文件，可以访问本包函数，则该**函数的首字母必须大写**

6，在访问其他包函数，变量时，其语法是  **包名.函数名**

7，如果包名较长，Go支持给包取别名，注意细节，取别名后，原来的包名就不能使用了

8，在同一个包下，不能有相同的函数名（也不能有相同的全局变量名），否则报重复定义

9，如果你要编译成一个可执行程序文件，就需要将这个包声明为main，即 package main ，这个就是一个语法规范，如果你是写一个库，包名可以自定义



##### 函数-调用机制

```go
package main
import (
	"fmt"
)
func test(n1 int) {
	n1 = n1 + 1
	fmt.Println("test's n1=", n1) //11
}
func main() {
	n1 := 10
	//调用test
	test(n1)
	fmt.Println("main's n1=", n1) //10
}
```
1，在调用一个函数时，会给该函数分配一个新的空间，编译器会通过自身的处理让这个新的空间和其他的栈的空间区分开来

2，在每个函数对应的栈中，数据空间是独立的，不会混淆

3，当一个函数调用完毕（执行完毕）后，程序会销毁对应的栈空间

##### 函数-递归调用

基本介绍： 一个函数在函数体内调用了本身，称为递归调用

```go
package main
import (
	"fmt"
)
func test(n int) {
	if n > 2 {
		n--
		test(n)
	}
	fmt.Println("n=", n)
}
func test2(n int) {
	if n > 2 {
		n--
		test2(n)
	} else {
		fmt.Println("n=", n)
	}
}
func main() {
	test(100)
	// n = 2
	// n = 2
	// n = 3

	test2(100)
	// n = 2
}
```

函数递归的重要原则：

1，执行一个函数时，就创建一个新的受保护的独立空间（新函数栈）

2，函数的局部变量是独立的，不会互相影响

3，递归必须向退出递归的条件逼近，否则就是无限递归

4，当一个函数执行完毕，或者遇到return ，就会返回，遵守谁调用，就将结果返回给谁，同时当函数执行完毕或者返回时，该函数同时被销毁



eg:  斐波那契数

```go
package main
import "fmt"
func fbn(n int) int {
	if n == 1 || n == 2 {
		return 1
	} else {
		return fbn(n-1) + fbn(n-2)
	}
}
func main() {
	res := fbn(3)
	fmt.Println("res=", res)
	fmt.Println("res=", fbn(4))
	fmt.Println("res=", fbn(5))
	fmt.Println("res=", fbn(6))
	fmt.Println("res=", fbn(7))
}
```



##### 函数注意事项和细节讨论

1，函数的形参列表可以是多个，返回值列表也可以是多个

2，形参列表和返回值列表的数据类型可以是值类型和引用类型

3，函数的命名遵循标识符命名规范，首字母不能是数字，首字母大写可被本包和其他包使用。首字母小写只能被本包文件使用

4，函数中的变量是局部的，函数外不生效

```go
package main
func test() {
	// n1是test函数的局部变量，只能在test函数中使用
	var n1 int = 10
}
func main() {
	// 这里不能使用n1，因为n1是test函数的局部变量
	//fmt.Println("n1=",n1)
}
```

5，基本数据类型和数组默认都是**值传递的**，即进行值拷贝，在函数内修改，不会影响到原来的值

```go
package main
import (
	"fmt"
)
func test(n1 int) {
	n1 = n1 + 10
	fmt.Println("test's n1=", n1) //30
}
func main() {
	n1 := 20
	test(n1)
	fmt.Println("main's n1=", n1) //20
}
```

6，如果希望函数内的变量能修改函数外的变量（指的是默认以值传递的方式的数据类型），可以传入变量的地址&，函数内以指针的方式操作变量，从效果上看类似引用

```go
func test(n1 *int) {
	*n1 = *n1 + 10
	fmt.Println("test's n1=", *n1) //30 
}
func main() {
	num := 20
	test(&num)
	fmt.Println("main's n1=", num) //30
}
```


7，Go函数不支持重载

8，在go中，**函数也是一直数据类型**，可以给赋值一个变量，则该变量就是一个函数类型的变量，通过该变量可以对函数调用

```go
func getSum(n1 int, n2 int) int {
	return n1 + n2
}
func main() {
	a := getSum
	fmt.Printf("a的类型是%T,getSum类型是%T\n", a, getSum)
	res := a(10, 40)
	fmt.Println("res=", res)
}
//a的类型是func(int, int) int,getSum类型是func(int, int) int
//res= 50
```

9，函数可以作为形参，并可以调用

```go
package main
import (
	"fmt"
)
func getSum(n1 int, n2 int) int {
	return n1 + n2
}
func myFunc(funcvar func(int, int) int, num1 int, num2 int) int {
	return funcvar(num1, num2)
}
func main() {
	a := getSum
	fmt.Printf("a的类型是%T,getSum类型是%T\n", a, getSum)
	res := a(10, 40)
	fmt.Println("res=", res)
	res2 := myFunc(getSum, 50, 60)
	fmt.Println("res2=", res2)
}
```

10，为了简化数据类型定义，Go支持**自定义数据类型**

基本语法 ： type 自定义数据类型名 数据类型 // 理解 ：相当于一个别名

```go
func main() {
	type myInt int // 给int 取了别名。 在go中，int和myInt虽然都是int类型，但是go认为myInt 和int 是两个类型
	var num1 myInt
	var num2 int
	num1 = 40
	num2 = int(num1)//这里需要显示转换，因为go认为int和myInt 是两个类型
	fmt.Println("num1=", num1)
	fmt.Println("num2=", num2)
}
```

11，支持对函数返回值命名

```go
func getSumAndSub(n1 int, n2 int) (sum int, sub int) {
	sum = n1 + n2
	sub = n1 - n2
	return
}
func main() {
	a, b := getSumAndSub(1, 2)
	fmt.Printf("a=%v b=%v", a, b)
}
```

12，使用 _ 标识符，忽略返回值

13，Go支持可变参数

（3），如果一个函数的形参列表中有可变参数，则可变参数变量需要放在形参列表最后

##### init函数

基本介绍：每一个源文件都可以包含一个init函数，该函数会在main函数执行前，被go运行框架调用，也就是说init会在main函数前被调用

```go
package main
import (
	"fmt"
)
// init函数，通常可以在init函数中完成初始化工作
func init() {
	fmt.Println("init()...")
}
func main() {
	fmt.Println("main()...")
}
```

细节讨论:

1,如果一个文件同时包含**全局变量定义**，**init函数和main函数**，则执行的流程是变量定义 >init函数 > main函数

```go
package main
import (
	"fmt"
)
var age = test()
func test() int {
	fmt.Println("test()")
	return 90
}
// init函数，通常可以在init函数中完成初始化工作
func init() {
	fmt.Println("init()...")
}
func main() {
	fmt.Println("main()...age=", age)
}
/*
test()
init()...
main()...age= 90
*/
```

2，init函数最主要的作用就是完成一些初始化的工作

##### 匿名函数

介绍：GO支持匿名函数，如果我们某个函数只希望使用一次，可以考虑使用匿名函数，匿名函数也可以实现多次调用

使用方式：

1，在定义匿名函数时就直接调用

```go
package main
import "fmt"
func main() {
	// 求两个数的和，使用匿名函数方式完成
	res := func(n1 int, n2 int) int {
		return n1 + n2
	}(10, 20)
	fmt.Println("res=", res)
}
```

2，将匿名函数赋予给一个变量（函数变量），再通过该变量来调用匿名函数



**全局匿名函数**：

如果将匿名函数赋给一个全局变量，那么这个匿名函数，就成为一个全局匿名函数，可以在程序有效

```go
var (
	// func1 就是一个全局匿名函数
	func1 = func(n1 int, n2 int) int {
		return n1 * n2
	}
)
    res4 := func1(6, 9)
	fmt.Println("res4=", res4)  // 54
```

##### 闭包

基本介绍： 闭包就是一个函数和与其相关的引用环境组合的一个整体（实体）

```go
package main
import (
	"fmt"
)
// 累加器
func AddUpper() func(int) int {
	var n int = 10
	return func(i int) int {
		n = n + i
		return n
	}
}
func main() {
	f := AddUpper()
	fmt.Println(f(1)) // 11
	fmt.Println(f(2)) // 13
	fmt.Println(f(3)) // 16
}
```

对上面代码的说明和总结：

1，AddUpper 是一个函数，返回的数据类型是func (int) int

2,  闭包的说明


  返回的是一个匿名函数，但是这个匿名函数引用到函数外的n,因此这个匿名函数和n形成一个整体，构成闭包

4，当我们反复调用f函数时，n是初始化一次，因此每调用一次，就会累加

5，闭包的关键 ------> 返回的函数引用到哪些变量，因为函数和引用的变量共同构成闭包

实践一下：

```go
func makeSuffix(suffix string) func(string) string {
	return func(name string) string {
		// 如果 name 没有指定的后缀，则加上，否则返回原名字
		if !strings.HasSuffix(name, suffix) {
			return name + suffix
		} else {
			return name
		}
	}
}
func main() {
	// 返回一个闭包
	f := makeSuffix(".jpg")
	fmt.Println("文件名处理后=", f("winter")) // winter.jpg
	fmt.Println("文件名处理后=", f("winter.avi")) //winter.avi.jpg
}
```

代码说明
1)返回的匿名函数和makeSuffix (suffix string)的 suffix变量组合成一个闭包,因为返回的函数引用到suffix这个变量
2)我们体会一下闭包的好处，如果使用传统的方法，也可以轻松实现这个功能，但是传统方法需要每次都传入后缀名，比如.jpg ,而闭包因为可以保留上次引用的某个值，所以我们传入—次就可以反复使用。大家可以仔细的体会一把!

##### 函数中-defer

在函数中，程序员经常需要创建资源（比如，数据库连接，文件句柄，锁等)，为了在函数执行完毕后，及时地释放资源，Go的设计者提供defer（延时机制）

```go
package main
import (
	"fmt"
)
func sum(n1 int, n2 int) int {
	// 当执行到 defer时，暂时不执行，会将 defer 后面的语句压入到独立的栈中（defer栈）
	// 当函数执行完毕后，再从defer栈，按照先入后出的方式出栈
	defer fmt.Println("ok1 n1=", n1)
	defer fmt.Println("ok2 n2=", n2)
	res := n1 + n2
	fmt.Println("ok3 res=", res)
	return res
}
func main() {
	res := sum(10, 20)
	fmt.Println("res=", res)
}
/*
ok3 res= 30
ok2 n2= 20
ok1 n1= 10
res= 30
*/
```

细节说明：

1，当go执行到一个defer时，不会立即执行defer后的语句，而是将defer 后的语句压入到一个栈中

2，当函数执行完毕后，在从defer栈中，依次从栈顶取出语句执行性（注：遵守栈 先入后出的机制）

3，在defer将语句放入到栈时，也会将相关的值拷贝同时入栈

```go
func sum(n1 int, n2 int) int {
	// 当执行到 defer时，暂时不执行，会将 defer 后面的语句压入到独立的栈中（defer栈）
	// 当函数执行完毕后，再从defer栈，按照先入后出的方式出栈
	defer fmt.Println("ok1 n1=", n1)
	defer fmt.Println("ok2 n2=", n2)
	n1++
	n2++
	res := n1 + n2
	fmt.Println("ok3 res=", res)
	return res
}
func main() {
	res := sum(10, 20)
	fmt.Println("res=", res)
}
/*
输出结果：
ok3 res= 32
ok2 n2= 20
ok1 n1= 10
res= 32
*/
```



defer的最佳实践

defer最主要的价值是在，当函数执行完毕后，可以及时到释放函数创建的资源。

```go
func test(){
	// 关闭文件资源
    file = openfile(文件名)
    defer file.close()
    // 其它代码
}
func test(){
    // 释放数据库资源
    connect = openDatabase()
    defer connect.close()
    // 其它代码
}
```

说明：

1，在golang编程中的通常做法是，创建资源后，比如（打开了文件，获取了数据库的链接，或者是锁资源），可以执行 defer file Close() defer connect Close()

2，在defer后，可以继续使用创建资源

3，当函数完毕后，系统会依次从defer栈中，取出语句，关闭资源

4，这种机制，非常简洁，程序员不用再为在为什么时机关闭资源而烦心



##### 函数参数的传递方式

**基本介绍**
     我们在讲解函数注意事项和使用细节时，已经讲过值类型和引用类型了，这里我们再系统总结一下，因为这是重难点，值类型参数默认就是值传递，而引用类型参数默认就是引用传递。

**两种传递方式**：
1)值传递（基本数据类型 int系列 float系列 bool string 数组和结构体struct）
2)引用传递 （指针 slice切片 map 管道chan interface )
其实，不管是值传递还是引用传递，传递给函数的都是变量的副本，不同的是，值传递的是值的拷贝，引用传递的是地址的拷贝，一般来说，地址拷贝效率高，因为数据量小，而值拷贝决定拷贝的数据大小，数据越大，效率越低。


##### 变量作用域

说明：

1，函数内部声明/定义的变量叫做局部变量，作用域仅限于函数内部

2，函数外部声明/定义的变量叫做全局变量，作用域在整个包都有效，如果其首字母为大写，则作用域在整个程序有效

```go
package main
import "fmt"
var age int = 50  		   // 其他包不可以使用
var Name string = "jack~"  // 其他包可以使用
//函数
func test() {
	//age 和 Name 的作用域只在 test函数内部
	age := 10
	Name := "tom~"
	fmt.Println("age=", age)
	fmt.Println("Name=", Name)
}
func main() {
	fmt.Println("age=", age)
	fmt.Println("Name=", Name)
	test()
}
/*
age= 50
Name= jack~
age= 10
Name= tom~
*/
```

3，如果变量是在一个代码块，比如for / if 中，那么这个变量的作用域就在该代码块

##### 字符串函数

说明:字符串在我们程序开发中，使用的是非常多的，常用的函数需要同学们掌握[带看手册或者官方编程指南]:
1)统计字符串的长度，按字节  len(str)

```go
func main() {
	// 统计字符串的长度，按字节 len(str)
	str := "hello寄吧"
	// golang 的编码统一为 UTF-8
	//（ascii的字符/数字）占一个字节，汉字占三个字节
	fmt.Println("str len=", len(str))
}
```

2,字符串遍历，同时处理有中文的问题r :=[]rune(str)

```go
	str2 := "hello寄吧"
	// 字符串遍历，同时处理有中文的问题r :=[]rune(str)
	str3 := []rune(str2)
	for i := 0; i < len(str3); i++ {
		fmt.Printf("字符=%c\n", str3[i])
	}
```

3,字符串转整数: n, enr := strconv.Atoi("12")

```go
n, err := strconv.Atoi("123")
	if err != nil {
		fmt.Println("转换错误", err)
	} else {
		fmt.Println("转换结果是", n)
	}
```

4,整数转字符串str = strconv.Itoa(12345)

```go
str4 := strconv.Itoa(12345)
	fmt.Printf("str4=%v, str4=%T", str4, str4)
```

5，字符串转 []byte :  var bytes = []byte("hell go")

```
var bytes = []byte("hell go")
	fmt.Printf("bytes=%v\n", bytes)
//bytes=[104 101 108 108 32 103 111]
```

6,[] byte 转字符串: str = string([]byte{97,98,99})

```go
str = string([]byte{97, 98, 99})
	fmt.Println("str=", str)
//str= abc
```

7, 10进制转 2，8，16进制 ： str = strconv.FormatInt(123,2)  // 返回对应的字符串

```go
str = strconv.FormatInt(123, 2)
fmt.Println("123对应的二进制是", str)
// 123对应的二进制是 1111011
```

8, 查找子串是否在指定的字符串中 : strings.Contains("fuckingBitch","fu")  //   bool

```go
b := strings.Contains("fuckingBitch", "fu")
	fmt.Printf("b=%v\n", b)
// b = true
```

9，统计一个字符串中 有几个指定的子串： strings.Count("cheese","e")   // 3

```go
a := strings.Count("cheese", "e")
	fmt.Printf("a=%v\n", a)
// a = 3
```

10,字符串比较：

1）区分大小写  ：     a    ==   b

```
fmt.Println("结果", "abc" == "ABC")
// 结果 false
```

2）不区分大小写 ：strings.EqualFold("ABC","abc") // bool

```go
b = strings.EqualFold("ABC", "abc")
	fmt.Printf("b=%v\n", b)
//true
```

 11，返回子串在字符串第一次出现的index值(下标），如果没有，返回 -1

：  strings.Index("NLT_abc","abc") //4

12，返回子串在字符串最后一次出现的index，如没有返回-1 : strings.LastIndex("go golang", "go")

```go
index = strings.LastIndex("go golang", "go")
	fmt.Printf("index=%v\n", index)  // 3
```

13，将指定的子串替换成另外一个子串: strings.Replace("go go hello" , "go", "go语言", n)n可以指定你希望替换几个，如果n=-1表示全部替换

```go
str6 := "go go hello"
	str5 := strings.Replace(str6, "go", "寄吧", 1)
	fmt.Println("str5=", str5)
```

14，按照指定的某个字符，为分割标识，将一个字符串拆分成字符串数组。strings.Split("hello,world,ok", ",")

```go
str7 := strings.Split("hello,world,ok", ",")
	fmt.Println("str7=", str7)
// str7= [hello world ok]
```

15，将字符串的字母进行大小写的转换: strings.ToLower("Go") // go strings.ToUpper"Go")/GO

```go
	str7 := strings.ToLower("Go")
	fmt.Println("str7=", str7)  //go
	str8 := strings.ToUpper("Go")
	fmt.Println("str8=", str8)  //GO
```

16,将字符串左右两边的空格去掉:strings.TrimSpace(" tn a lone gopher jiba ")

```
str9 := strings.TrimSpace(" tn a lone gopher jiba ")
	fmt.Println("str9=", str9)
	//tn a lone gopher jiba
```

17,将字符串左右两边指定的字符去掉:strings.Trim("! hello! "," !")                     //     ["hello"]//将左右两边!和""去掉

```go
str10 := strings.Trim("! he!llo! ", " !")
	fmt.Println("str10=", str10)  // he!llo
```

18,将字符串左边指定的字符去掉:strings.TrimLeft("! hello! "," !")               l/["hello"]//将左边!和""去掉
19,将字符串右边指定的字符去掉: strings.TrimRight(" hello! "" !")  //["hello"]//将右边!和""去掉

20,判断字符串是否以指定的字符串开头:   strings.HasPrefix("ftp://192.168.10.1", "ftp") // true

```go
ad := strings.HasPrefix("ftp://192.168.10.1", "ftp")
	fmt.Println("ad=", ad)
```

21,判断字符串是否以指定的字符串结束: strings.HasSuffix("NLT_abc.jpg","abc")//false

```go
adc := strings.HasSuffix("NLT_abc.jpg", "abc")
	fmt.Println("adc=", adc)
```



##### 时间和日期相关函数

说明： 在编程中，程序员会经常使用到日期相关的函数，比如，统计某段代码执行花费的时间



1，时间和日期相关函数，需要引入time包

2，time.Time 类型，用于表示时间

```go
now := time.Now()
	fmt.Printf("now=%v  now's type is %T", now, now)
// now=2022-05-24 22:11:23.6190219 +0800 CST m=+0.009165301  now's type is time.Time
```

3，获取当前时间的方法

now := time.Now()   // now 的类型就是 time.Time

4，如何获取到其它的日期信息

```go
	fmt.Printf("年=%v\n", now.Year())
	fmt.Printf("月=%v\n", int(now.Month()))
	fmt.Printf("日=%v\n", now.Day())
	fmt.Printf("时=%v\n", now.Hour())
	fmt.Printf("分=%v\n", now.Minute())
	fmt.Printf("秒=%v\n", now.Second())
```

5，格式化日期时间

1） 第一种方式 ：使用SPrintf 或者 Printf

```go
fmt.Printf("当前年月日 %02d-%02d-%02d %02d:%02d:%02d \n", now.Year(),now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second())
```

```go
Str := fmt.Sprintf("当前年月日 %02d-%02d-%02d %02d:%02d:%02d \n", now.Year(),
		now.Month(), now.Day(), now.Hour(), now.Minute(), now.Second())
	fmt.Printf("Str=%v", Str)
```

2）第二种方式 ：

fmt.Printf(now.Format("2006/01/02 15:04:05"))

fmt.Printf(now.Format("2006/01/02"))

fmt.Printf(now.Format("15:04:05"))

6, 时间的常量

```go
const (
    Nanosecond  Duration = 1
    Microsecond          = 1000 * Nanosecond
    Millisecond          = 1000 * Microsecond
    Second               = 1000 * Millisecond
    Minute               = 60 * Second
    Hour                 = 60 * Minute
)
```

7, 休眠

func.Sleep(d Duration)

```go
func main() {
	// 需求，每隔一秒钟打印一个数字，打印到100时就退出
	i := 0
	for {
		i++
		fmt.Println(i)
		// 休眠
		time.Sleep(time.Millisecond * 100)
		if i == 100 {
			break
		}
	}
}

```

8, 获取Unix时间戳和UnixNano 时间戳（可以获取随机数字）

```go
func main() {
	now := time.Now()
	// Unix 和 UnixNano 的使用
	fmt.Printf("Unix时间戳=%v UnixNano时间戳=%v", now.Unix(), now.UnixNano())
}
```

练习： 统计函数执行时间

```go
package main
import (
	"fmt"
	"strconv"
	"time"
)
func test() {
	str := ""
	for i := 0; i < 100000; i++ {
		str += "hello" + strconv.Itoa(i)
	}
}
func main() {
	// 在执行test前，先获取当前的时间戳
	start := time.Now().Unix()
	test()
	end := time.Now().Unix()
	fmt.Printf("执行test用时%vs\n", end-start)
}
```



##### 内置函数

1，len :用来求长度，比如 string ,array,slice,map,channel

2,	new : 用来分配内存，主要用来分配值类型，比如 int,float32,struct  返回的是指针

```go
num1 := 100
	fmt.Printf("num1的类型为%T, num1的值=%v, num1地址为%v\n", num1, num1, &num1)

	num2 := new(int)
	*num2 = 100
	fmt.Printf("num2的类型为%T, num2的值=%v, num2地址为%v\n num2指向的值为%v", num2, num2, &num2, *num2)
```

3，make : 用来分配内存，主要是用来分配引用类型，比如 channel ,map ,slice

##### 错误处理

```go
package main
import (
	"fmt"
)
func test() {
	num1 := 10
	num2 := 0
	res := num1 / num2
	fmt.Println("res=", res)
}
func main() {
	test()
	fmt.Println("main()下面的代码...")
}
/*
panic: runtime error: integer divide by zero

goroutine 1 [running]:
main.test()
        D:/Golang/SDK/src/go_code/go_study/chapter06/cuowuchuli/main.go:19 +0x11
main.main()
        D:/Golang/SDK/src/go_code/go_study/chapter06/cuowuchuli/main.go:23 +0x19
exit status 2
*/
```

1，在默认情况下，当发生错误后，程序就会退出

2，如果我们希望，当发生错误后，可以捕获到错误，并进行处理，保证程序继续执行。

错误处理的基本说明：

1）Go语言追求简洁优雅，所以，Go语言不支持传统的 try...catch...finally这种处理。

2)Go中引入的处理方式为:defer, panic, recover

3)这几个异常的使用场景可以这么简单描述: Go中可以抛出一个panic的异常，然后在defer中通过recover捕获这个异常，然后正常处理



**使用defer + recover 来处理错误**

```go
// 使用defer + recover 来捕获和处理异常
	defer func() {
		err := recover() // recover()是内置函数，可以捕获到异常
		if err != nil {  // 说明捕获到异常
			fmt.Println("err=", err)
			// 这里可以将错误信息发送给管理员
			fmt.Println("sent a email to zwang2365@gamil.com~")
		}
	}()
```



**自定义错误**

go程序中，也支持自定义错误，使用errors.New  和  panic 内置函数

1，errors.New("错误说明")，会返回一个error类型的值，表示一个错误

2，panic内置函数,接收一个interface{)类型的值(也就是任何值了）作为参数。可以接收error类型的变量,输出错误信息,并退出程序!

```go
package main
import (
	"errors"
	"fmt"
)
// 函数去读取已配置文件 init.conf的信息
// 如果文件名传入不正确，我们就返回一个自定义的错误
func readConf(name string) (err error) {
	if name == "config.ini" {
		// 读取
		return nil
	} else {
		// 返回一个自定义错误
		return errors.New("读取文件错误")
	}
}
func test() {
	err := readConf("config.ini2")
	if err != nil {
		// 如果读取文件发送错误， 就输出这个错误，并终止程序
		panic(err)
	}
	fmt.Println("test()继续执行")
}
func main() {
	test()
	fmt.Println("main()下面的代码")
}
/*
panic: 读取文件错误

goroutine 1 [running]:
main.test()
        D:/Golang/SDK/src/go_code/go_study/chapter06/cuowuchuli/zidingyi/main.go:32 +0x49
main.main()
        D:/Golang/SDK/src/go_code/go_study/chapter06/cuowuchuli/zidingyi/main.go:38 +0x19
exit status 2

```



# 数组 切片 排序 查找

### 数组介绍

数组介绍： 数组可以存放多个同一类型数据。数组也是一种数据类型，在Go中，数组是值类型

```go
func main() {
	var hens [7]float64
	hens[0] = 3.0
	hens[1] = 5.0
	hens[2] = 1.0
	hens[3] = 3.4
	hens[4] = 2.0
	hens[5] = 50.0
	hens[6] = 99.9999
	totalWeight := 0.0
	for i := 0; i < len(hens); i++ {
		totalWeight += hens[i]
	}
	avgWeight := fmt.Sprintf("%.2f", totalWeight/float64(len(hens)))
	fmt.Printf("totalWeight=%.2f avgWeight=%v", totalWeight, avgWeight)
}
```

1，使用数组来解决问题，程序的可维护性增加

2，而且方法代码更加清晰，也更容易扩展



### 数组的定义和内存分布

var 数组名 [数组大小]数据类型  (    var arr [5]int    )

赋初值  a[0] = 1


3，数组的各个元素的地址间隔是依据数组的类型决定，比如 int64-8, int32-4

```go
func main() {
	var intArr [3]int
	//当我们定义完数组后，其实数组的各个元素有默认值
	fmt.Println(intArr)
	intArr[0] = 10
	intArr[1] = 20
	intArr[2] = 30
	fmt.Println(intArr)
	fmt.Printf("intArr的地址=%p\n intArr[0]的地址为%p\n intArr[1]的地址为%p\n intArr[2]的地址为%p\n",
		&intArr, &intArr[0], &intArr[1], &intArr[2])
}
/*
[0 0 0]
[10 20 30]
intArr的地址=0xc0000ae078
 intArr[0]的地址为0xc0000ae078
 intArr[1]的地址为0xc0000ae080
 intArr[2]的地址为0xc0000ae088
*/
```

### 数组的使用

访问数组元素：数组名[下标] 比如：  你要使用a数组的第三个元素 a[2]

```go
var score [5]float64
	for i := 0; i < len(score); i++ {
		fmt.Printf("请输入第%d个元素的值\n", i+1)
		fmt.Scanln(&score[i])
	}
	for i := 0; i < len(score); i++ {
		fmt.Printf("score[%d]=%v\nee", i, score[i])
	}
}
```



**四种初始化数组的方式：**

```go
var numsArray01 [3]int = [3]int {1, 2, 3}
var numsArray02 = [3]int {1, 2, 3}
var numsArray03 = [...]int {6, 7, 8，10}
// 可以指定元素值对应的下标...
var names = [3]string{1:"Tom", 0:"jack", 2:"bitch"}
```



### 数组的遍历

1，常规遍历 -for 循环

2， for-range结构遍历 ：Go语言一种独有的结构，可以用来遍历访问数组的元素

```go
// 基本语法
for index, value := range array01 {
 ...
}
```

说明：

1） 第一个返回值index是数组的下标

2）第二个value是在该下标位置的值

3）他们都是仅在for循环内部可见的局部变量

4）遍历数组元素的时候，如果不想使用index下标，可以使用_

5）index和value的名称不是固定的，自己设定

```go
var heroes [3]string = [3]string{"寄吧", "打几把", "硝基苯"}
	for index, value := range heroes {
		fmt.Printf("index=%v value=%v\n", index, value)
		fmt.Printf("heroes[%d]=%v\n", index, heroes[index])
	}
/*
index=0 value=寄吧
heroes[0]=寄吧
index=1 value=打几把
heroes[1]=打几把
index=2 value=硝基苯
heroes[2]=硝基苯
*/
```



### 数组使用注意事项和细节

1)数组是多个相同类型数据的组合,一个数组一旦声明/定义了,其长度是固定的,不能动态变化。

```go
var arr01 [3]int
	arr01[0] = 1
	arr01[1] = 2
	//arr01[2] = 1.1 cannot use 1.1 (untyped float constant) as int value in assignment
	arr01[2] = 90
	//arr01[3] = 6 invalid argument: index 3 (constant of type int) is out of bounds
```

2)var arr []int这时arr就是一个slice切片，切片后面专门讲解，不急哈.
3)数组中的元素可以是任何数据类型，包括值类型和引用类型，但是不能混用。

4)数组创建后，如果没有赋值，有默认值

数值类型数组:默认值为o

 字符串数组:默认值为""

bool数组:默认值为false

```go
var arr01 [3]float32
	var arr02 [3]string
	var arr03 [3]bool
	fmt.Printf("arr01=%v arr02=%v arr03=%v", arr01, arr02, arr03)
//arr01=[0 0 0] arr02=[  ] arr03=[false false false]
```

5)使用数组的步骤1.声明数组并开辟空间   2，给数组各个元素赋值3使用数组

6)数组的下标是从0开始的。
7）数组下标必须在指定范围内使用，否则报panic:数组越界

比如 var arr [5]int则有效下标为0-4
8)Go的数组属值类型，在默认情况下是值传递，因此会进行值拷贝。数组间不会相互影响

```go
func test01(arr [3]int) {
	arr[0] = 88
}

func main() {
	arr := [3]int{11, 22, 33}
	test01(arr)
	fmt.Println(arr)   // 11 22 33
}
```
9)如想在其它函数中，去修改原来的数组，可以使用引用传递(指针方式)

```go
func test01(arr *[3]int) {
	(*arr)[0] = 88
}

func main() {
	arr := [3]int{11, 22, 33}
	test01(&arr)
	fmt.Println("main arr=", arr) // 88 22 33
}
```



10） **长度是数组类型的一部分**，在传递函数参数时，需要考虑数组的长度



### 数组复杂使用-数组反转

要求：随机生成五个数，并将其反转打印

```go
// 要求：随机生成五个数，并将其反转打印
	// 思路
	// 1，随机生成五个数，  rand.Intn()
	// 2, 当我们得到随机数后，放在数组里面
	// 3，反转打印喵 , 交换的次数是 len / 2，倒数第x个和第x个元素交换
	var intArr [5]int
	len := len(intArr)
	rand.Seed(time.Now().UnixNano()) // 随机种子喵
	for i := 0; i < len; i++ {
		intArr[i] = rand.Intn(100) //   0 <= n < 100
	}
	fmt.Println("交换前=", intArr)
	temp := 0
	for i := 0; i < len/2; i++ {
		temp = intArr[len-1-i]
		intArr[len-1-i] = intArr[i]
		intArr[i] = temp
	}
	fmt.Println("交换后=", intArr)
```



### 为什么需要切片？

先看一个需求:我们需要一个数组用于保存学生的成绩，但是学生的**个数是不确定的**，请问怎么办?解决方案:使用切片

### 切片的基本介绍

1)切片的英文是slice
2)切片是数组的一个引用，因此切片是引用类型，在进行传递时，遵守引用传递的机制
3)切片的使用和数组类似，遍历切片、访问切片的元素和求切片长度len(slice)都一样。
4)切片的长度是可以变化的，因此切片是一个可以动态变化数组。5)切片定义的基本语法:
var变量名[]类型
比如: var a [] int



```go
func main() {
	// 切片的基本使用
	var intArr [5]int = [...]int{1, 22, 33, 66, 99}
	// 定义一个切片
	// 1,slice 是切片名
	// 2,intArr[1:3] 表示 slice 引用到intArr这个数组
	// 3，引用 intArr 数组的起始下标为1，最后的下标为3 （但是不包含3）
	slice := intArr[1:3]
	fmt.Println("intArr=", intArr)
	fmt.Println("slice的元素是=", slice)
	fmt.Println("slice的元素个数是=", len(slice))
	fmt.Println("slice的容量是=", cap(slice))

	fmt.Printf("intArr[1]的地址=%p\n", &intArr[1])
	fmt.Printf("slice[0]的地址=%p slice[0]==%v\n", &slice[0], slice[0])
}
/*
intArr= [1 22 33 66 99]
slice的元素是= [22 33]
slice的元素个数是= 2
slice的容量是= 4
intArr[1]的地址=0xc0000c0068
slice[0]的地址=0xc0000c0068 slice[0]==22
*/
```

### 使用切片的三种方式：

方法一：定义一个切片，然后用切片去引用一个已经创建好的数组



方法二： 通过make（内置函数） 来创建切片

基本语法：  **var 切片名 []type = make ([]type,len,[cap])**

参数说明 ： type就是数据类型

​					 len : 大小 

​					 cap:指定切片容量，可选，如果分配cap，则要求cap>=len

```go
var slice []float64 = make([]float64, 5, 10)
	slice[1] = 10
	slice[3] = 20
	// 对于切片，必须 make后使用
	fmt.Println(slice)
	fmt.Println("the size of slice is ", len(slice))
	fmt.Println("the cap of slice is ", cap(slice))
/*
[0 10 0 20 0]
the size of slice is  5
the cap of slice is  10
*/
```


对上面代码的小结：

1，通过make方式创建切片可以指定切片的大小和容量

2，如果没有给切片的各个元素赋值，那么就会使用默认值

3，通过make方式创建的切片对应的数组是由make底层维护，对外不可见，即只能通过slice去访问各个元素



方法三：定义一个切片，直接指定具体数组，使用原理类似make的方式



方法一和方法二的区别



### 切片的遍历

方法一：常规遍历

```go
// 常规的for循环遍历切片
	var arr [5]int = [...]int{10, 20, 30, 40, 50}
	slice := arr[1:4]
	for i := 0; i < len(slice); i++ {
		fmt.Printf("slice[%v]=%v ", i, slice[i])
	}
```



方法二 : for range

```go
for i, v := range slice {
		fmt.Printf("i=%v v=%v ", i, v)
	}
```



### 切片注意事项和细节说明：

1，切片初始化时  var slice = arr[startindex:endindex]	

说明：从arr数组下标为startindex,取到下标为endindex的元素（不包含arr[endindex]）

2，切片初始化时，仍然不能越界。 范围在[0   ----   len(arr)]之间，但是可以**动态增长**	

1） var slice = arr [0:end]   可以简写为 var slice = arr[:end]

2)···var slice = arr[start:len(arr)] 可以简写为var slice = arr[start:]

3).... var slice = arr[0:len(arr)] 可以简写为 var slice = arr[:]

3， cap是一个内置函数，用于统计切片的容量，即最大存放多少个元素。

4，切片定义完后，还不能使用，因为本身是一个空的，需要让其引用到一个数组，或者 make 一个空间供切片来使用

6，切片可以继续切片

```go
var arr [5]int = [...]int{10, 20, 30, 40, 50}
	slice := arr[:]
	for i := 0; i < len(slice); i++ {
		fmt.Printf("slice[%v]=%v ", i, slice[i])
	}
	fmt.Println()
	for i, v := range slice {
		fmt.Printf("i=%v v=%v ", i, v)
	}
	slice2 := slice[1:2]
	slice2[0] = 100
	fmt.Println("slice2=", slice2)
	fmt.Println("slice=", slice)
	fmt.Println("arr=", arr)
	/*
	slice[0]=10 slice[1]=20 slice[2]=30 slice[3]=40 slice[4]=50
i=0 v=10 i=1 v=20 i=2 v=30 i=3 v=40 i=4 v=50 slice2= [100]
slice= [10 100 30 40 50]
arr= [10 100 30 40 50]
*/
```

7,改变切片的值，对应的切片和数组的值都会改变

8, 用append内置函数，可以对切片进行动态追加

```go
//用 append内置函数对切片进行动态追加
	var slice3 []int = []int{100, 200, 300}
	fmt.Println("slice3=", slice3)
	// 通过append直接给slice3追加具体的元素
	slice4 := append(slice3, 400, 50, 600)
	fmt.Println("slice4=", slice4)
	slice5 := append(slice3, slice4...)
	fmt.Println("slice5=", slice5)
/*
slice3= [100 200 300]
slice4= [100 200 300 400 50 600]
slice5= [100 200 300 100 200 300 400 50 600]
*/
```

切片append操作的底层原理分析：

1)切片append操作的本质就是对数组扩容

2)go底层会创建一下新的数组newArr(安装扩容后大小)

3)将slice原来包含的元素拷贝到新的数组newArr

4）slice重新引用到newArr

5)注意newArr是在底层来维护的，程序员不可见.

9，切片的拷贝操作

切片使用copy内置函数完成拷贝

```go
var a []int = []int{1, 2, 3, 4, 5}
	var slice6 = make([]int, 10)
	fmt.Println(slice6)
	copy(slice6, a)
	fmt.Println(slice6)
/*
[0 0 0 0 0 0 0 0 0 0]
[1 2 3 4 5 0 0 0 0 0]
*/
```

说明：

1）copy(para1,para2)参数的数据类型是切片

2）按照上面的代码来看，slice6和a的数据空间是独立的，相互不影响，也就是说该a[0] = 99 ，slice6 仍然是1

10，关于拷贝的注意事项

```go
var a []int = []int{1, 2, 3, 4, 5}
	var slice = make([]int, 1)
	fmt.Println(slice)
	copy(slice, a)
	fmt.Println(slice)
```

说明：上面的代码没有问题，可以运行，最后输出的是[0]  [1]



11，切片是引用类型，所以在传递时，遵循引用传递机制。



```go
var slice []int
	var arr [5]int = [...]int{1, 2, 3, 4, 5}
	slice = arr[:]
	var slice2 = slice
	slice2[0] = 10
	fmt.Println("slice2=", slice2)
	fmt.Println("slice=", slice)
	fmt.Println("arr=", arr)
/*
slice2= [10 2 3 4 5]
slice= [10 2 3 4 5]
arr= [10 2 3 4 5]
*/
```

```go
func test(slice []int) {
	slice[0] = 100
}
func main() {
	var slice = []int{1, 2, 3, 4}
	fmt.Println("slice=", slice)
	test(slice)
	fmt.Println("slice=", slice)
}
/*
slice= [1 2 3 4]
slice= [100 2 3 4]
*/
```



### string 和 slice

1,string底层是一个byte数组，因此string可以进行切片处理

```go
str := "hello@atguigu"
	// 使用切片获取到 atguigu
	slice := str[6:]
	fmt.Println("slice=", slice) //slice= atguigu
```

2,string 和切片在内存的形式


3，string是不可变的，也就是说不能通过str[0] = z 的方式来修改字符串

4,如果需要修改字符串，可以先将string ---> []byte 或者[]rune ----> 修改 >重新转成string

```go
str := "hello@atguigu"
	// 使用切片获取到 atguigu
	slice := str[6:]
	fmt.Println("slice=", slice)
	// str[0] = 'z' 编译不通过，string是不可变的
	arr1 := []byte(str)
	arr1[0] = 'z'
	str = string(arr1)
	fmt.Println("str=", str)
// 我们转成[]byte后，可以处理英文和数字，但是不能处理中文
// []byte字节来处理，而一个汉字是三个字节，会出现乱码
// 解决方法是将string转成[]rune即可，因为[]rune是按字符处理，兼容汉字
	arr2 := []rune(str)
	arr2[0] = '集'
	str = string(arr2)
	fmt.Println("str=", str)
/*
slice= atguigu
str= zello@atguigu
str= 集ello@atguigu
*/
```





排序是将一组数据,依指定的顺序进行排列的过程。排序的分类:
1,内部排序:
指将需要处理的所有数据都加载到内部存储器中进行排序。包括(**交换式排序法、选择式排序法和插入式排序法**);

交换式排序法
交换式排序属于内部排序法,是运用数据值比较后，依判断规则对数据位置进行交换，以达到排序的目的。
交换式排序法又可分为两种:

**1)**

### **冒泡排序法**(Bubble sort)

: 冒泡排序(Bubble Sorting）的基本思想是:通过对待排序序列从后向前(从下标较大的元素开始)，依次比较相邻元素的排序码,若发现逆序则交换,使排序码较小的元素逐渐从后部移向前部（从下标较大的单元移向下标较小的单元)，就象水底下的气泡一样逐渐向上冒。

因为排序的过程中，各元素不断接近自己的位置，如果一趟比较下来没有进行过交换，就说明序列有序，因此要在排序过程中设置一个标志flag判断元素是否进行过交换。从而减心不必要的比较（优化)

```go
//从小到大
package main
import (
	"fmt"
)
func BubbleSort(arr *[5]int) {
	fmt.Println("排序前arr=", (*arr))
	temp := 0 //临时变量，用来做交换
	n := len(*arr)
	for i := 0; i < n-1; i++ {
		for j := 0; j < n-i-1; j++ {
			if (*arr)[j] > (*arr)[j+1] {
				//交换
				temp = (*arr)[j]
				(*arr)[j] = (*arr)[j+1]
				(*arr)[j+1] = temp
			}
		}
	}
	fmt.Println("排序后arr=", (*arr))
}
func main() {
	// 定义数组
	arr := [5]int{24, 69, 80, 57, 13}
	// 将数组传递给一个函数，完成排序
	BubbleSort(&arr)
}
/*
排序前arr= [24 69 80 57 13]
排序后arr= [13 24 57 69 80]
*/
```

**2)快速排序法**(Quick sort)



2,外部排序法:
数据量过大，无法全部加载到内存中，需要借助外部存储进行排序。包括(**合并排序法和直接合并排序法**)。



### 查找

在golang中有顺序查找和二分查找（该数字是有序的）

 

**顺序查找**

```go
func main() {
	names := [4]string{"金毛狮王", "白眉鹰王", "紫衫龙王", "青翼蝠王"}
	var heroName = ""
	fmt.Println("请输入要查找的人名")
	fmt.Scanln(&heroName)

	// 顺序查找的第一种方式
	for i := 0; i < len(names); i++ {
		if heroName == names[i] {
			fmt.Printf("找到%v,下标为%v\n", heroName, i)
			break
		} else if i == (len(names) - 1) {
			fmt.Printf("没有找到%v\n", heroName)
		}
	}

	// 顺序查找的第二种方式(推荐使用)
	index := -1
	for i := 0; i < len(names); i++ {
		if heroName == names[i] {
			index = i
			break
		}
	}
	if index != -1 {
		fmt.Printf("找到%v,下标为%v\n", heroName, index)
	} else {
		fmt.Printf("没有找到%v\n", heroName)
	}
}
```



**二分查找**


```go
func BinaryFind(arr *[6]int, leftIndex int, rightIndex int, findVal int) {

	// 判断 leftIndex 是否大于 rightIndex
	if leftIndex > rightIndex {
		fmt.Println("找不到")
		return
	}

	// 先找到中间的下标
	middle := (leftIndex + rightIndex) / 2

	if (*arr)[middle] > findVal {
		BinaryFind(arr, leftIndex, middle-1, findVal)
	} else if (*arr)[middle] < findVal {
		BinaryFind(arr, middle+1, findVal, findVal)
	} else {
		fmt.Printf("找到了,下标为%v\n", middle)
	}
}
func main() {
	arr := [6]int{1, 8, 10, 89, 1000, 1234}
	BinaryFind(&arr, 0, len(arr)-1, 89	)

}
```





### 二维数组

第一种使用方式 :先声明后赋值

```go
func main() {
	// 声明一个二维数组
	var arr [4][6]int
	// 赋值
	arr[1][2] = 1
	arr[2][1] = 2
	arr[2][3] = 3

	// 遍历二维数组，按照要求输出
	for i := 0; i < 4; i++ {
		for j := 0; j < 6; j++ {
			fmt.Print(arr[i][j], " ")
		}
		fmt.Println()
	}
}
/*
0 0 0 0 0 0
0 0 1 0 0 0
0 2 0 3 0 0
0 0 0 0 0 0
*/
```


第二种使用方式 ：直接初始化


```go
var arr [2][3]int = [2][3]int{{1, 2, 3}, {4, 5, 6}}
	fmt.Println(arr)
```

### 二维数组的遍历

1，用双层for循环

```go
// for循环来遍历
	for i := 0; i < len(arr); i++ {
		for j := 0; j < len(arr[i]); j++ {
			fmt.Printf("%v\t",arr[i][j])
		} 
		fmt.Println()
	}
```

 2,for-range

```go
// for-range来遍历二维数组
	for i, v := range arr {
		for j, v2 := range v {
			fmt.Printf("arr[%v][%v]=%v\t ", i, j, v2)
		}
	}
```





# map

### map的介绍和说明

map是key-value数据结构，又称为字段或者关联数组 

**基本语法** ： var map变量名 map[keytype]valuetype

key可以是什么类型
golang中的map，的 key可以是很多种类型，比如bool,数字，string,指针，channel ,还可以是只包含前面几个类型的接口，结构体，数组
通常为int . string
注意: slice,map还有function 不可以，因为这几个没法用==来判断

valuetype的类型和key基本一样，通常为：数字（整数，浮点数），string,map,struct

```go
/举例
var a map[string]string
var a map[string]int
var a map[string]map[string][string]
```

注意喵：声明是不会分配内存的，初始化需要make，分配内存后才能赋值和使用

说明：

1)map在使用前一定要make

2)map的key是不能重复的，如果重复了，以最后的key-value为准

3)map的value是可以相同的



### map的三种用法和使用实例

map的使用方式： 

1）

```go
//声明，这时候map=nil
var cities map[string]string
//make(map[string]string,10) 分配一个map空间
cities = make(map[string]string,10)
```

2）

```go
//声明，直接make
var cities = make(map[string]string)
```

3)

```go
// 声明，直接赋值
var cities map[string]string = map[string]string{
 "no1" : "周牛娃"，
    "no2" : "zhouniu",
}
cities["no1"] = "周牛"
```

```go
func main(){
	// 第一种使用方式
	var a map[string]string
	// 在使用map前，需要先make, make的作业就是给map分配数据空间
	a = make(map[string]string, 10)
	a["no1"] = "几把"
	a["no2"] = "打几把"
	a["no1"] = "小鸡吧"
	a["no3"] = "打几把"
	fmt.Println(a)
	// 第二种使用方式
	cities := make(map[string]string)
	cities["no1"] = "北京"
	cities["no2"] = "天津"
	cities["no3"] = "伤害"
	cities["no4"] = "西安"
	fmt.Println(cities)
	// 第三种方式
	heroes := map[string]string{
		"hero1" : "周牛娃",
		"hero2" : "周牛",
	}
    heroes["hero4"]="林冲"
	fmt.Println(heroes)
}
```

```go
package main

import(
	"fmt"
)

func main(){
	studentsMap := make(map[string]map[string]string)

	studentsMap["stu01"] = make(map[string]string,3)
	studentsMap["stu01"]["name"] = "Tom"
	studentsMap["stu01"]["sex"] = "male"
	studentsMap["stu01"]["address"] = "西电"

	studentsMap["stu02"] = make(map[string]string,3)
	studentsMap["stu02"]["name"] = "Mary"
	studentsMap["stu02"]["sex"] = "female"
	studentsMap["stu02"]["address"] = "原神西电"
	
	fmt.Println(studentsMap["stu01"])
	fmt.Println(studentsMap["stu02"]["address"])
}
```



### map的增删改查操作

map增加和更新：map["key"] = value //如果key还没有就是增加，有就是更新

