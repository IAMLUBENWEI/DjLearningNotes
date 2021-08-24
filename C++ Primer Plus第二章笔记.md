## C++ Primer Plus第二章笔记

### 典型的C++程序

```c++
#include <iostream> //头文件
using namespace std; //名称空间

int myFunction(int n);
int main(){
    cout << output;
    cin >> input;
}

int myFunction(int n ){
    functionMainBody;
}

```

#### 头文件

`#include <iostream>`：该编译指令会将iostream文件的内容添加到程序中，处理器会将源代码文件和iostream组合成一个复合文件，编译的下一阶段会使用该文件。

#### 名称空间

作用：有助于组织程序，可通过使用名称空间来区分不同的版本。

使用方法：

```c++
//方法一
std::cout;
std::endl;
//方法二
using namespace std;
//方法三
using std::cout;
using std::cin;
using std::endl;
```

#### 函数

C++的函数分为两种：有返回值的和没有返回值的

1. 有返回值的函数

   C++程序应该为程序中使用的每个函数提供原型。也就是说，在使用函数前，C++的编译器必须知道函数的参数类型和返回值类型。

   1. 函数原型

      方法：`type-name funtion-name(type-name variable-name)`

      ```c++
      #include <iostream>
      using namespace std;

      int myFunction(int inputVariable);//this is a function prototype
      ```

   2. 函数格式

        ```c++
        type functionName(argumentList)
        {
            statements;
        }
        ```

    

2. 没有返回值的函数

   通过`void functionName(argumentList)`来实现

#### 总结

1. C++的语句主要包括以下六种：声明语句、赋值语句、消息语句、函数调用、函数原型、返回语句。
2. 类是用户定义的数据类型规范，它详细描述了如何表示信息以及可对数据执行的操作。对象是根据类规范创建的实体。
3. C++可以使用大量的库函数。要使用库函数，应当包含提供该函数原型的头文件。

