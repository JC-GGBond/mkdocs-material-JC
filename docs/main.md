# 1. JC.GGbond的数据结构与算法MkDocs书稿


记录个人算法学习过程，
代替hexo的next主题页面部署，
其实感觉差不多，
就是更好看一些。


learn from [hello-algo](https://www.hello-algo.com/) & [chatGPT](https://chat.openai.com/)

页面网址：[mkdocs-material-JC](https://jc-ggbond.github.io/mkdocs-material-JC/)

部署方法：

```
git add .
git commit -m "XXX"
git push origin main
```


每一个Page是横向标题，所以直接在一个.md文件里写完所有的稿子，
写一个轻量电子书的感觉


自动编号方法：

markdown-index插件：
F1 run: Markdown add index
















## 1.1. Part.A Python Basis

### 1.1.1. 类


#### 1.1.1.1. 定义类
定义一个类，类是一种用于创建对象的模板。在类中定义属性（成员变量）和方法（成员函数）来描述对象的特征和行为。以下是一个简单的类定义的示例：

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print(f"{self.name} says woof!")
```

在上面的示例中，我们定义了一个名为 `Dog` 的类，它有两个属性 `name` 和 `age`，以及一个方法 `bark`。


#### 1.1.1.2. 使用类

要在一个函数中调用一个类，你需要首先导入这个类所在的模块，然后可以通过模块名加类名的方式来访问和使用这个类。导入的是模块，而不是类名或文件名。

假设你有一个名为 `dog.py` 的文件，其中定义了一个 `Dog` 类，你可以这样导入并在其他函数中使用：

```python
# 导入模块，模块名就是文件名（不包括.py扩展名）
import dog

# 创建一个Dog类的实例
my_dog = dog.Dog("Buddy", 2)

# 调用Dog类的方法
my_dog.bark()
```

在上述示例中，我们首先导入了 `dog` 模块（即 `dog.py` 文件）。然后，我们通过 `dog.Dog` 来访问 `Dog` 类，并创建了一个 `Dog` 类的实例 `my_dog`，最后调用了 `bark` 方法。

请注意，导入模块的方式通常比导入文件名更好，因为它更具可读性和维护性。使用模块名可以让你清晰地知道你正在导入哪个模块，并避免了与其他同名模块或类的冲突。



销毁对象：在Python中，你无需手动销毁对象，Python的垃圾回收机制会自动处理对象的销毁。

实际应用中，类可以更复杂，包括更多的属性和方法，用于实现特定的功能。使用类的主要目的是将相关的数据和功能组织在一起，以便更好地管理和维护代码，并实现面向对象编程的思想。

#### 1.1.1.3. 类示例

```python
# 初始化stack
# Python中使用List初始化
# import ListNode_module
# ListNode=ListNode_module.ListNode()
from ListNode_module import ListNode
ListNode=ListNode()
class LinkedListStack:
    # 类名使用驼峰命名法
    
    def __init__(self):
        """构造方法"""
        self.__peek: ListNode | None=None
        # 这行代码定义了一个类的私有成员变量 __peek。
        # ListNode | None 是一个类型注解，表示 __peek 可以是 ListNode 类型或者 None 类型。
        # 然后默认为None
        # 类型注解在 Python 3.5+ 版本中引入，用于增加代码可读性和类型检查。
        # 这里使用了 __peek 的私有命名规则，以双下划线开头表示该成员变量是私有的，只能在类内部访问。
        self.__size: int=0
    
    def size(self)  -> int:
        return self.__size

    def isEmpty(self) -> bool:
        return not self.__peek
    
    def push(self,val:int):
        node=ListNode(val)
        node.next=self.__peek
        self.__size += 1
        
    def pop(self)   -> int:
        num: int = self.peek()
        self.__peek=self.__peek.next
        self.__size -= 1
        return num  
    
    def peek(self) -> int:
        if not self.__peek:
            return None
        return self.__peek.val
    
    def to_list(self) -> list[int]:
        arr=[]
        node=self.__peek
        while node:
            arr.append(node.val)  
            node=node.next
        arr.reverse()
        return arr     
            
```


### 1.1.2. 代码规范化

#### 1.1.2.1. 文档命名
在Python中，类名和类所在的 `.py` 文件的命名有一些常见的约定和最佳实践，尽管它们不是强制性规则，但遵循这些约定可以提高代码的可读性和可维护性。

**类名的命名约定**：

1. 类名通常使用驼峰命名法（CamelCase）：每个单词的首字母大写，没有下划线。例如，一个表示学生的类可以命名为 `Student`。

2. 类名应该清晰、简洁且有描述性，以便于理解类的用途。

3. 避免使用Python的保留字（例如，不要将类命名为 `class` 或 `int`）。

4. 类名通常以大写字母开头，以便与变量名和函数名区分开。

**类所在的 .py 文件的命名约定**：

1. 通常情况下，类应该放置在一个与类名相关的 `.py` 文件中。例如，如果你有一个 `Student` 类，那么类定义应该位于一个名为 `student.py` 的文件中。

2. 文件名应该使用小写字母，并且可以包含下划线以提高可读性。例如，对于一个表示数据库连接的类，文件名可以是 `database_connection.py`。

3. 如果一个模块（包含类定义的文件）是主要的可执行脚本，你可以使用 `__main__.py` 作为文件名。

4. 避免使用与Python标准库或已安装的第三方库冲突的文件名。

总之，遵循这些命名约定有助于保持代码的一致性，并使其更易于阅读和维护。虽然这些约定不是强制性的，但它们是Python社区广泛接受的标准，建议在项目中尽量遵循。
#### 1.1.2.2. 类型注解（Type Annotation）
Python的类型注解是一种静态类型检查工具，用于在代码中声明变量、函数参数和函数返回值的类型信息。这些类型注解不会影响代码的运行，但可以在开发过程中提供有关变量和函数的类型信息，以帮助开发者编写更可读、更可维护和更健壮的代码。

以下是关于Python类型注解的一些重要信息：

1. **变量注解**：你可以在变量声明时使用类型注解，明确变量的数据类型。例如：

```python
count: int = 5
name: str = "John"
```

变量注解和变量初始化不一样，
虽然都声明了变量，
但变量注解并不创建或初始化变量。
只是为了提供类型提示和文档。
代码中`x: int=5`这种写法实际上就是将类型注解和变量初始化合并到了一行。

2. **函数参数注解**：你可以在函数定义中为参数添加类型注解，以指定函数参数的期望类型。例如：

```python
def add(x: int, y: int) -> int:
    return x + y
```

在上面的例子中，`x` 和 `y` 的类型注解指定为整数，而函数的返回值类型注解为整数。

3. **函数返回值注解**：你可以使用 `->` 符号在函数定义中添加返回值类型注解。这有助于说明函数的返回值类型。例如：

```python
def divide(x: float, y: float) -> float:
    return x / y
```

在上面的例子中，函数 `divide` 的返回值类型注解指定为浮点数。

4. **类型检查工具**：Python的类型注解不会在运行时执行类型检查，但你可以使用第三方工具来执行静态类型检查，例如`mypy`。`mypy` 可以分析你的代码并检查类型注解是否与实际代码的使用情况一致。这有助于发现潜在的类型错误。

5. **可选和默认值**：类型注解可以与可选参数和默认参数一起使用。例如：

```python
def greet(name: str, greeting: str = "Hello") -> str:
    return f"{greeting}, {name}"
```

在上面的例子中，`greeting` 参数有一个默认值，并且带有类型注解。

6. **任意类型**：你可以使用特殊的 `Any` 类型注解来表示一个变量可以具有任何类型。这通常用于动态类型的情况或者为不希望进行类型检查的变量添加注解。

```python
def process_data(data: Any) -> Any:
    # 处理数据的代码
    return processed_data
```

总的来说，类型注解是Python 3引入的一项功能，它有助于提高代码的可维护性和可读性，减少类型相关的错误，并提供更好的文档。虽然类型注解不是强制性的，但它可以在大型项目和团队合作中发挥重要作用，特别是在保持代码清晰和可靠方面。



### 1.1.3. data type
基本数据类型以二进制的形式存储在计算机中。
一个二进制位即为1比特。
在绝大多数现代系统中，
1字节（byte）由8比特（bits）组成。


#### 1.1.3.1. list
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

#### 1.1.3.2. 赋值操作

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


在Python中，当涉及到可变对象时，修改一个变量的值可能会影响到另一个变量，因为多个变量可以引用同一个可变对象。这可能导致副作用，因为它们实际上引用的是相同的内存位置。

这种情况通常发生在对可变对象（如列表、字典和集合）进行操作时。当一个变量引用了一个可变对象，然后将该变量赋给另一个变量，实际上两个变量都引用了同一个对象。因此，对一个变量所引用的对象进行修改会反映在另一个变量上。

```py
# 创建一个列表并将其赋给两个变量
list1 = [1, 2, 3]
list2 = list1

# 修改列表中的元素
list1[0] = 100

# 打印两个变量的值
print("list1:", list1)  # 输出: list1: [100, 2, 3]
print("list2:", list2)  # 输出: list2: [100, 2, 3]
```

#### 1.1.3.3. ()与[]

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

### 1.1.4. 内置函数

#### 1.1.4.1. len()


`len()`是 Python 内置函数之一，用于获取容器（如列表、元组、字符串等）中元素的数量或长度。


#### 1.1.4.2. pop()

`pop()`是列表（List）的一个内置方法，用于从列表中移除并返回指定索引位置的元素。该方法还可以接受一个可选的参数，即要移除的元素的索引位置，默认为列表的最后一个元素。

```py
element=list_name.pop(index)
#index为要pop()的元素的索引位置
```

#### 1.1.4.3. range()

`range()` 是一个Python内置的函数，用于生成一个整数序列。它常用于 `for` 循环中，用于指定循环的迭代范围。`range()` 函数有三种常见的用法：

1. `range(stop)`：生成从0开始到 `stop-1` 结束的整数序列。

```python
for i in range(5):
    print(i)
```

上述代码将输出：

```
0
1
2
3
4
```

2. `range(start, stop)`：生成从 `start` 开始到 `stop-1` 结束的整数序列。

```python
for i in range(2, 6):
    print(i)
```

上述代码将输出：

```
2
3
4
5
```

3. `range(start, stop, step)`：生成从 `start` 开始到 `stop-1` 结束的整数序列，步长为 `step`。步长表示每个相邻整数之间的差值。

```python
for i in range(1, 10, 2):
    print(i)
```

上述代码将输出：

```
1
3
5
7
9
```

需要注意的是，`range()` 函数生成的序列不包括 `stop` 参数指定的值。例如，`range(5)` 生成的序列是0到4，不包括5。

`range()` 函数通常与 `for` 循环结合使用，以便在循环中进行迭代。但你也可以将 `range()` 生成的序列转换成列表，如下所示：

```python
my_list = list(range(1, 6))
print(my_list)
```

上述代码将生成一个包含1到5的整数的列表并打印出来。

`range()` 函数在许多情况下非常有用，特别是当你需要控制循环的次数或在一定范围内生成数字时。

### 1.1.5. 异常


#### 1.1.5.1. `raise`关键字
在Python中，raise关键字用于手动引发异常。异常是在程序执行过程中发生的错误或异常情况的表示。使用`raise`关键字，你可以在代码中显式地引发异常，从而使程序在特定条件下停止执行并进入异常处理流程。

raise语法的一般格式是：

```py
raise ExceptionClass("Error message")
这里的ExceptionClass是内置的或自定义的异常类，可以是ValueError、TypeError、CustomError等。异常类是从BaseException继承而来的。"Error message"是一个描述异常的文本，它可以在异常处理过程中被捕获和显示。
```
使用raise关键字可以帮助你在程序中明确地引发并处理异常，从而提高代码的健壮性和可读性。

### 1.1.6. 流程控制（循环）

#### 1.1.6.1. if语句

```py
age = 20
if age >= 100 age < 120: # 条件成立时执行否则跳过
    print('百岁老人')
elif age > 60: # 同上, 如果只有两个分支可没有 elif
    print('老人')
elif age > 18:
    print('成年人')
else: # 所有不符合上边条件的均执行此内容, 必须有
    print('未成年人')

```


#### 1.1.6.2. for语句

`for` 循环是Python中用于遍历可迭代对象的控制结构，可用于重复执行一组语句，直到遍历完整个可迭代对象。以下是 `for` 循环的基本语法：

```python
for 变量 in 可迭代对象:
    # 在这里执行循环体的代码
```

解释一下 `for` 循环的各个部分：

- `变量`：这是一个临时变量，它在每次循环迭代时都会获取可迭代对象中的下一个值。你可以在循环体内使用这个变量。

- `可迭代对象`：这可以是一个序列（如列表、元组、字符串等）或其他可迭代对象（如字典、集合等），`for` 循环将遍历其中的元素。

- `循环体`：这是 `for` 循环的主体部分，包含要在每次循环迭代时执行的代码块。缩进是Python中非常重要的，用于表示代码块。

下面是一个简单的示例，演示如何使用 `for` 循环来遍历列表：

```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

上述代码将输出：

```
apple
banana
cherry
```

在每次迭代中，`fruit` 变量会获取列表 `fruits` 中的一个值，然后在循环体中打印它。

你还可以使用 `range()` 函数来生成一个数字范围，并在 `for` 循环中使用它来进行迭代：

```python
for i in range(1, 5):
    print(i)
```

上述代码将输出：

```
1
2
3
4
```

这个示例中，`range(1, 5)` 生成一个从1到4的数字范围，`for` 循环遍历这个范围并打印每个值。

`for` 循环非常灵活，可以与各种不同类型的可迭代对象一起使用，同时还支持 `break` 和 `continue` 语句来控制循环的行为。

## 1.2. Part.B Data Structuresxs



### 1.2.1. 链表

**链表的操作，一定要在纸上把过程先画出来，再写程序**

链表是一种线性数据结构，由一系列节点组成，每个节点包含一个值和一个指向下一个节点的指针。

在很多编程问题中，链表经常用来解决需要动态添加或删除元素的场景，因为链表的插入和删除操作非常高效。

ListNode用于表示链表的节点：


### 1.2.2. 栈
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

### 1.2.3. 队列


### 1.2.4. 树



## 1.3. Algorithm