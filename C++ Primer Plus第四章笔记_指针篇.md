## 指针和自由储存空间

### 计算机在存储数据时必须跟踪的三种属性

1. 信息存储在何处
2. 存储的值为多少
3. 存储的信息是什么类型

### 指针的基本属性

1. 指针是一个变量，其存储的是值的地址，而不是值本身。
2. 使用地址运算符（&）

example:

```c++
#include <iostream>
int main()
{
    using namespace std;
    int higgens = 5;
    int* pt = &higgens;
}
```

:warning:：int*是一种类型——指向int的指针

:warning:：一定要在对指针应用解除引用运算符（`*`）之前，将指针初始化为一个确定的、适当的地址。



###  `new`语句的使用

```c++
typename* pointer_name = new typeName;
```

分析：`typename*`说明这是一个指针类型，`pointer_name`描述了指针的名称，而`new typeName`则告诉程序，需要适合存储的内存。`new`运算符根据类型来确定需要多少字节的内存，他找到这样的内存，并返回其地址赋给指针。

### `delete`语句的使用

当需要内存时，可以使用`new`来请求。同样，`delete`语句可以使得在使用完内存后，能够将内存归还给内存池。

```c++
int* ps = new int;
...
delete ps;
```

### 使用`new`来创建动态数组

1. 使用`new`创建动态数组

   在C++中，创建动态数组很容易；只要将数组的元素类型和元素数目告诉`new`。

   ```c++
   int* psome = new int [10];
   delete [] psome;//释放内存时应该采用这种格式
   ```

   `new`运算符返回第一个元素的地址。在上述例子中，这个地址被赋给指针`psome`。

   当程序使用完`new`分配的内存块时，应该用`delete`释放它们。

   使用`new`和`delete`，应该遵守以下规则：

   * 不要使用`delete`来释放不是`new`分配的内存

   * 不要使用`delete`释放同一个内存两次
   * 如果使用`new[]`为数组分配内存，则应该使用`delete[]`来释放
   * 如果使用`new`为一个实体分配内存，则应使用`delete`（没有方括号）来释放

2. 使用动态数组

   **只要把指针当作数组名使用即可。**



## 指针小结

1. 声明指针

   要声明指向特定类型的指针，请使用下面的格式：

   ```c++
   typeName* pointerName;
   //for example
   double* pn;
   char* pc;
   ```

2. 给指针赋值

   应将内存地址赋给指针。可以对变量名应用`&`运算符，来获得被命名的内存的地址，`new`运算符返回未命名的内存的地址。

3. 对指针解除引用

   对指针解除引用意味着获得指针的指向的值。

   * 方法一：对指针应用解除引运算符
   * 方法二：使用数组表示法。例如，`pn[0]`和`*pn`是一样的

   :warning:：绝不要对未被初始化为适当地址的指针解除引用

4. 区分指针和指针所指向的值

5. 数组名

   **在多数情况下，C++将数组名视为数组的第一个元素的地址**

6. 指针算数

7. 数组的动态联编和静态联编

   使用数组声明来创建数组时，将使用静态联编，即数组的长度在编译时设置：

   ```c++
   int tacos[10];
   ```

   使用`new[]`运算符创建数组时，将使用动态联编，即将在运行时为数组分配空间，其长度也将在运行时设置。使用完这种数组后，应使用`delete[]`释放其占用的内存：

   ```c++
   int size;
   cin >> size;
   int* pt = new int [size];
   //......
   delete[] pt;
   ```

   

## 数组的替代品——`vector`和`array`

### 模板类`vector`

模板类`vector`:point_right:动态数组，可在运行阶段设置`vector`对象的长度，可在末尾附加新数据，可在中间插入新数据。

要使用模板类`vector`，必须导入头文件：

```c++
#include <vector>

using namespace std;
vector <int> vi;

int size;
cin >> size;
vector <double> vd(size);

//vector <typeName> vt(n_element);
```



### 模板类`array`

**`vector`模板类的功能比数组强大，但付出的代价是效率较低。因此在数组长度固定时，使用array类是更加优秀的选择**

```c++
#include <array>

using namespace std;
array <int,5> ai;
array <double,4> ad = {1.2, 2.1, 3.43, 4.3}

//array <typeName, n_elem> arr_name;
```

:warning:：n_elem不能是变量，必须是一个确定的数字