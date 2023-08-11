# JC.GGbond的数据结构与算法MkDocs书稿


记录个人算法学习过程，
代替hexo的next主题页面部署，
其实感觉差不多，
就是更好看一些。


learn from hello-algo & chatGPT

页面网址：[mkdocs-material-JC](https://jc-ggbond.github.io/mkdocs-material-JC/)

部署方法：

* git add.
* git commit -m "XXX"
* git push origin mains

每一个Page是横向标题，所以直接在一个.md文件里写完所有的稿子，
写一个轻量电子书的感觉
















## Python Basis

### data type
基本数据类型以二进制的形式存储在计算机中。
一个二进制位即为1比特。
在绝大多数现代系统中，
1字节（byte）由8比特（bits）组成。


#### list
列表 list	一个列表的每个元素被分配一个数字来表示它的位置或索引	[1, 2, 3, 4, 5 ], ['apple', 'orange', 'lemon', 'cherry']

```py
# 创建一个空列表
empty_list = []

# 创建一个包含整数的列表
numbers = [1, 2, 3, 4, 5]

# 创建一个包含字符串的列表
fruits = ["apple", "banana", "cherry"]

# 创建一个混合类型的列表
mixed = [1, "hello", 3.14, True]

# 访问列表中的元素
print(numbers[0])  # 输出：1
print(fruits[1])   # 输出："banana"

# 修改列表中的元素
fruits[0] = "orange"
print(fruits)  # 输出：["orange", "banana", "cherry"]

# 添加元素到列表末尾
numbers.append(6)
print(numbers)  # 输出：[1, 2, 3, 4, 5, 6]

# 删除列表中的元素
del mixed[1]
print(mixed)  # 输出：[1, 3.14, True]

# 获取列表的长度
length = len(numbers)
print(length)  # 输出：6

```

#### 赋值操作：

在 Python 中，对于不可变类型的对象（如整数），赋值操作实际上是创建一个新的对象，并让变量指向这个新的对象。而对于可变类型的对象（如列表），赋值操作并不会创建新的对象，而是让新的变量指向原始对象。

```py
# 创建一个整数对象并将其赋值给变量 x
x = 42

# 创建另一个变量 y 并将其指向 x 所指向的同一个整数对象
y = x

# 修改 y 的值，不会影响 x 的值，因为它们指向的是不同的整数对象
y = 100

print(x)  # 输出结果为 42
print(y)  # 输出结果为 100
```

#### ()与[]

()理解为函数调用时候使用的括号，而[]用于索引

要索引二维列表（矩阵）中的特定元素，您需要使用两个索引值，一个表示行索引，另一个表示列索引。索引从 0 开始，因此要访问第 i 行、第 j 列的元素，您可以使用`num_matrix[i][j]`的形式。

例如，如果`num_matrix`是一个大小为 3 x 3 的二维列表，如下所示：

```py
num_matrix = [[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]]
```

要获取其中某个元素的值，可以使用行索引和列索引来访问它：

```py
element_1_1 = num_matrix[1][1]  # 获取第2行（索引为1）第2列（索引为1）的元素，值为 5
element_0_2 = num_matrix[0][2]  # 获取第1行（索引为0）第3列（索引为2）的元素，值为 3
```

请注意，行索引和列索引都是从 0 开始的。在上面的例子中，`num_matrix[1][1]` 返回值 5，因为它访问第 2 行（索引为 1）第 2 列（索引为 1）的元素。

确保行索引和列索引不超出列表的有效范围，否则可能会导致索引错误。例如，如果使用了一个超出范围的索引，Python 将引发 `IndexError` 异常。

使用正确的行索引和列索引，您可以在二维列表中定位和操作特定位置的元素。

### 内置函数

* len()


`len()`是 Python 内置函数之一，用于获取容器（如列表、元组、字符串等）中元素的数量或长度。


* pop()

`pop()`是列表（List）的一个内置方法，用于从列表中移除并返回指定索引位置的元素。该方法还可以接受一个可选的参数，即要移除的元素的索引位置，默认为列表的最后一个元素。

```py
element=list_name.pop(index)
#index为要pop()的元素的索引位置
```

## 异常


#### `raise`关键字
在Python中，raise关键字用于手动引发异常。异常是在程序执行过程中发生的错误或异常情况的表示。使用`raise`关键字，你可以在代码中显式地引发异常，从而使程序在特定条件下停止执行并进入异常处理流程。

raise语法的一般格式是：

```py
raise ExceptionClass("Error message")
这里的ExceptionClass是内置的或自定义的异常类，可以是ValueError、TypeError、CustomError等。异常类是从BaseException继承而来的。"Error message"是一个描述异常的文本，它可以在异常处理过程中被捕获和显示。
```
使用raise关键字可以帮助你在程序中明确地引发并处理异常，从而提高代码的健壮性和可读性。



## Data Structuresxs



### 链表
链表是一种线性数据结构，由一系列节点组成，每个节点包含一个值和一个指向下一个节点的指针。

在很多编程问题中，链表经常用来解决需要动态添加或删除元素的场景，因为链表的插入和删除操作非常高效。

ListNode用于表示链表的节点：


### 栈
先入后出的线性数据结构。
常用操作包括`push()` `pop()` `peek()`访问栈顶元素

两种实现方法：
1. 基于链表的实现方法
```py
class LinkedListStack

    def __init__(self):
        self.__peek: ListNode | None = None
        #类的私有成员变量 __peek
        self.__size: int = 0

    def size(self) -> int:
        return self.__size

    def is_empty(self) -> bool:
        return self.__size

    def push(self,val: int):
        node=ListNode(val)
        node.next=self.__peek
        self.__peek=node
        self.__size+=1

    def pop(self):
        num: int=self.peek()
        #num: int 是类型注解，表示变量 num 是整数类型。
        self.__peek=self.__peek.next
        self.__size-=1
        return num
                
   def to_list(self) -> list[int]
       arr=[]
       node=self.__peek
       while node:
            arr.append(node.val)
            node=node.next
       arr.reverse()
       return arr 
    


```

2. 基于数组的实现方法


```py
class ArrayStack
    def __init__(self):
        self.__stack=list[int]=[]

    def size(self) -> int:
        return len(self.__stack)
       
    def is_empty(self) -> bool:
        return self.__stack==[]
    
    def push(self,item) -> int:
        self.__stack.append(item)

    def pop(self) -> int:
        if self.is_empty():
            raise IndexError("栈为空")
        return self.__stack.pop()

```

### 队列


### 树



## Algorithm