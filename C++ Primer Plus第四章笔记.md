## C++ Primer Plus第四章笔记

## 复合类型

### 本章内容

1. 数组
2. 字符串
3. 结构
4. 共用体
5. 枚举
6. 指针
7. 管理动态内存
8. `vector`类和`array`类

### 数组

* 创建数组

1. 储存在每个元素中的值的类型
2. 数组名
3. 数组中的元素数

```c++
typeName arrayName[arraySize]
```

:warning:：`arraySize`指定元素数目，它必须是整形常数或`const`值，不能是变量，但使用`new`运算符可以避开这种限制。

* 数组初始化规则

1. 可以使用下标分别给数组中的元素赋值
2. 初始化数组时，提供的值可以少于数组的元素数目，编译器会自动将其他元素设置为0

### 字符串

* C风格的字符串

1. 字符串可以储存在`char`数组中，以空字符结尾。（空字符写作`\0`）

```c++
char dog[8] = {'b','e','a','u','x',' ','I','I'};//not a string
char cat[8] = {'f','a','t','e','s','s','a','\0'};//a string
```

2. 更好的、将字符数组初始化为字符串的方法——只需使用一个用引号括起的字符串即可，这种字符串被称为字符串常量或字符串字面值。

```c++
char bird[11] = "Mr. cheeps";//省略了\0
char fish[] = "Bubbles";//让编译器自动计算
```

:warning:：在确定存储字符串所需要的最短数组时，别忘了将结尾的空字符计算在内。

:warning:：字符串常量（使用双引号）不能与字符常量（使用单引号）互换

3. 字符串输入

:question:`cin`如何确定已完成字符串输入呢？

`cin`通过空白来确定字符串的结束位置，包括空格、制表符和换行符

因此我们需要使用`cin`的较高级特性

|    名称     |                             作用                             |
| :---------: | :----------------------------------------------------------: |
| `getline()` | 读取整行，通过回车键输入的换行符来确定结尾，并用空字符替换换行符 |
|   `get()`   | 读取整行，通过回车键输入的换行符来确定结尾，并在输入序列保留换行符 |



```c++
cin.get(name,Arsize);
cin.get(dessert,Arsize);//会出bug，因为get()函数会将换行符保留在输入序列中，导致第二个get函数看到的第一个字符就是换行符。

cin.get(name,Arsize);
cin.get();//通过多一次的调用，让换行符被去除。
cin.get(dessert,Arsize);
```

* `String`类(important)

要使用`string`类，必须在程序中包含头文件`string`

1. 可以使用C-风格字符串来初始化`string`对象
2. 可以使用`cin`来将键盘输入存储到`string`对象中
3. 可以使用`cout`来显示`string`对象
4. 可以使用数组表示法来访问存储在`string`对象中的字符

赋值、拼接和附加

1. 可以将`string`对象赋给另一个`string`对象
2. 可以使用运算符`+`将两个`string`对象合并起来

* `string`类I/O

两种确定字符串中字符数的方法：

```c++
int len1 = str1.size();
int len2 = strlen(charr1);
```

读取：

```c++
getline(cin,str);
```

这里没有使用句点表示法，这表明这个`getline`不是类方法。它将`cin`作为参数，指出到哪里去查找输入。另外，也没有指出字符串长度的参数，因为`string`对象将根据字符串的长度自动调整自己的大小。

### 结构

数组:arrow_right:虽然可以存储多个元素，但所有元素的类型必须相同。

结构则是一种比数组更灵活的数据模式。

1. 创建结构

   * 定义结构描述
   * 按描述创建结构变量

2. 说明

   ```c++
   struct inflatable
   {
       char name[20];
       float volume;
       double price;
   }
   
   inflatable hat;
   inflatable woopie_cushion;
   inflatable mainframe;
   ```

   关键字`struct`表明，这些代码定义的是一个结构的布局。标识符`inflatable`是这种数据格式的名称。这样，便可以创建`inflatable`类型的变量了。

3. 结构数组

   如上所示，`inflatable`结构包含一个数组，但同时可以创建元素为结构的数组，例如，要创建一个包含100个`inflatable`结构的数组，可以这样做：

   ```c++
   inflatable gifts[100];
   ```

### 共用体

1. 简介

   `union`是一种数据格式，它能够储存不同的数据类型，但只能同时存储其中的一种类型。

   例如：

   ```c++
   union one4all
   {
       int int_val;
       long long_val;
       double double_val;
   };
   //可以使用one4all变量来储存int、long、double，条件是在不同的时间进行
   ```

   理解：实际上可以将共用体理解为单个变量，而这个变量可以为很多不同的类型。

### 枚举

枚举提供了另一种创建符号常量的方式，这种方式可以代替`const`。

```c++
enum spectrum{red, orange, yellow, green, blue, violet, indigo, ultraviolet};
```

1. 让`spectrum`成为新类型的名称；`spectrum`被称为枚举.

2. 将`red`、`orange`、`yellow`等作为符号常量，它们对应整数值0~7。这些常量叫做枚举量。

