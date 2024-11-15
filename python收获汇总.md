## 4.18

### enumerate返回类型为tuple元组

### py中的生成器和next函数的联合使用

当我们需要在迭代过程中动态生成值序列时，Python 中的**生成器表达式**就变得非常有用。生成器表达式类似于列表推导，但是它使用圆括号而不是方括号，并且**生成的是一个生成器对象**而不是一个列表。生成器对象可以逐个地生成值，而不是一次性生成所有值，因此在内存使用上更加高效。

生成器表达式的一般形式是：

```python
(expression for item in iterable)
```

其中，`expression` 是生成每个值的表达式，`item` 是迭代的元素，`iterable` 是可迭代的对象，如列表、元组、集合等。

下面是一个简单的示例，演示了如何使用生成器表达式生成一个包含 1 到 5 的平方的生成器对象：

```python
squares_generator = (x ** 2 for x in range(1, 6))
```

生成器对象 `squares_generator` 可以通过迭代逐个生成值。可以使用 `next` 函数来获取生成器对象的下一个值。

```python
print(next(squares_generator))  # 输出：1
print(next(squares_generator))  # 输出：4
print(next(squares_generator))  # 输出：9
```

`next` 函数用于获取生成器对象的下一个值。每次调用 `next` 函数时，生成器都会继续执行，直到生成一个新的值。当生成器耗尽时，即没有更多的值可供生成时，会触发 `StopIteration` 异常。因此，通常会将 `next` 函数用在循环中，以便在生成器耗尽之前遍历所有值。

例如：

```python
for square in squares_generator:
    print(square)
```

这样会打印出生成器对象的所有剩余值。

总之，生成器表达式和 `next` 函数是 Python 中用于处理惰性计算的强大工具，能够有效地处理大型数据集，节省内存并提高性能。



### py3中的bitsect_right函数

`bisect_right` 函数是 Python 标准库中 `bisect` 模块提供的一个功能，**用于在已排序的序列中查找元素应该插入的位置，以保持序列的有序性**。

该函数的一般形式是：

```python
bisect_right(a, x, lo=0, hi=len(a))
```

其中，参数含义如下：

- `a`：已排序的序列，可以是列表、元组或其他支持索引操作的序列。
- `x`：要插入的元素。
- `lo`：可选参数，用于指定搜索的起始位置，默认值为 0。
- `hi`：可选参数，用于指定搜索的结束位置，默认值为序列的长度。

函数返回值是一个整数，表示将元素 `x` 插入到序列 `a` 中的位置，具体来说，返回的位置是在保持序列有序的前提下，将 `x` 插入到已排序序列中大于等于 `x` 的元素之后的位置。

下面是一个简单示例，演示了如何使用 `bisect_right` 函数：

```python
from bisect import bisect_right

a = [1, 3, 5, 7, 9]
x = 6

insert_index = bisect_right(a, x)
print(insert_index)  # 输出：3
```

在这个示例中，列表 `a` 已经按升序排列。元素 `x` 的值为 6。使用 `bisect_right` 函数，找到了将元素 6 插入到列表 `a` 中的位置，这个位置是在索引 3 处。

需要注意的是，如果序列中存在与 `x` 相等的元素，则 `bisect_right` 函数会返回将 `x` **插入到相等元素之后**的位置。

## 4.19

1. 获取字符串的长度`n=len(s)`
2. py中键值对字典的生成格式：`dict={'index':'val','index':'val',...}`
3. `enumerate()`函数的返回是index, val。可以用于遍历字符串
4. `list()`返回所有单个元素，也可用于遍历字符串
5. 逆向思维节省了步骤，包括获取长度、判别溢出等

## 4.20

1. py中函数递归自我调用需要用到关键词self
2. 定义函数时括号内： `名称：类型名称`  返回值是在def的最后`->返回类型`
3. py中判别同类型元素是否完全一致可以使用关键词`is`
4. py的return语句可以包含逻辑判断关键词如and，or等；and关键词二者全为真时才返回；or关键词返回第一个为真的语句的结果
5. py中使用`deque(em1,em2)`创建双线队列即双端队列，输入输出无限制的队列。
   1. Deque ()创建双端队列
   2.  insert (item)向队首插入项
   3. append (item)向队尾插入项
   4. popFront()返回队首的项，并从双端队列中删除该项
   5. pop()返回队尾的项，并从双端队列中删除该项
   6.  isEmpty ()判断双端队列是否为空
   7. size ()返回双端队列中项的个数
   8.  get (index)返回对列中的对象

## 4.21

1. py中字符串和数字都是不可变对象，无法通过下标形式修改对应元素。对字符串的操作可以是split切割、+拼接、.join等

2. 若想用下标来存储或修改元素，则类型应该是字典或者列表，最后返回结果则用`.join(列表)`来获取字符串

3. `enumerate()`函数会返回从零开始的索引值和对应元素的值

4. `list()`函数直接返回每一个元素的值

5. `zip()`函数接收两个可迭代对象作为参数，返回一个元组列表。对元组列表的列进行访问可以是`[列序号]`。

6. py自带的排序函数是`sorted()`而不是想当然的`sort`。参数中先要传入被排序元组/列表，然后可以用key关键字确定排序依据

7. `lambda` 是创建匿名函数的一种简洁方式。匿名函数是一种无需定义标识符（函数名）的函数或子程序。它们通常用于编写简单的函数，这些函数不会被重复调用。

   下面是对 `lambda x : x[0]` 的详细解释：

   1. `lambda` 关键字：这告诉 Python 解释器，接下来的代码将是一个匿名函数。
   2. `x`：这是传递给匿名函数的参数。在这个上下文中，`x` 是一个元组。
   3. `:`：冒号后面是匿名函数的主体，即函数要执行的表达式。
   4. `x[0]`：这是匿名函数的返回值，即参数 `x` 中的第一个元素。在这个上下文中，`x` 是通过 `zip(indices, s)` 创建的元组，其中 `x[0]` 就是 `indices` 中的元素。

8. 初始化列表需要中括号关键符号`[]`

## 4.22

1. 哈希表实际上是一个字典，内容都是键值对：`key:val` 但是在python中键值对之间是靠冒号链接的，C++中则是大括号里面用逗号分隔
2. `dict.get(key, default=None)`函数返回返回指定键的值，如果值不在字典中返回default值。因此方法三中都是把num的val映射到对应的索引上去，可以直接依赖key来等效查找val
3. 在对数组生成哈希表时，可以使用`enumerate`枚举函数把index和nums都映射到表中。`hashmap[num]=index`
4. 在py中不需要声明一个类型的变量，编译器会根据数据类型自动确认类型。本题中也不需要result的创建，因为可以直接返回一个用中括号包起来的整数对来表示list类型的结果。

## 4.23

### 字典相关

#### 创建字典

1. 直接指定key和value：
   `dic={'name':'try2love','date':'2024_4_24'}`键值对之间用逗号隔开
2. 字典推导式
   `dic={f'key{i}': i**2 for i in range(1,4)}`
   得到结果：`{'key1': 1, 'key2': 4, 'key3': 9}`
   `dic = {char: 0 for char in string.asii_lowercase}`对应的输出结果：`{'a': 0, 'b': 0, 'c': 0, ..., 'z': 0}`.其中，`string.ascii_lowercase` 是一个字符串常量，包含了所有小写字母。
3. 内置函数
   `dic=dict(name='try2love',date='2024_4_24')`或者使用元组`dic=dict([('name','try2love'),('date','2024_4_24')])`
4. 使用`dict.fromkeys()`
   `keys=['a','b','c']``dic=dict.fromkeys(keys,'try2love')`前者规定了键，后者初始会对应的值均为'try2love'
5. 修改
   `my_dict['new_key'] = 'new_value'  *# 添加键值对* ` 
   `my_dict['new_key'] = 'updated_value'  *# 更新键的值*`
   当一次性修改多个键值对时，使用update(): `dic.update({'b':2,'c':3})`把对应键值对进行了修改。也可以直接使用关键字参数：`dic.update(a=4,d=5)`直接修改已存在的键值对的值并生成不存在的键值对
6. 访问
   直接通过键来访问值`dic['new_key'] #输出updated_value`
7. 删除键值对
   使用del语句或者pop语句：`del dic['new_key']#删除键new_key`  `value=dic.pop('new_key',None)#返回键new_key的值并删除。若键不存在则返回默认的none`
8. 遍历字典
   遍历键：`for key in dic:`
   遍历值：`for val in dic.values():`
   遍历键值对：`for key,val in dic.items():` 

### 统计字符串中字符的出现次数

1. 使用内置的 `count()` 方法

字符串对象有一个 `count()` 方法，可以用来统计指定字符出现的次数：

```
text = "example string"
char = "e"
count = text.count(char)
print(f"字符 '{char}' 出现了 {count} 次。")
```

2. 使用字典

可以遍历字符串中的每个字符，并使用字典来计数：

```
text = "example string"
char_count = {}

for char in text:
    if char in char_count:
        char_count[char] += 1
    else:
        char_count[char] = 1

print(char_count)
```

3. 使用 `collections.Counter`

`collections` 模块的 `Counter` 类是一个专门的工具，用于快速计数：

```
from collections import Counter

text = "example string"
counter = Counter(text)

print(counter)
```

`Counter` 对象返回的是一个字典，其中键是字符，值是该字符出现的次数。

4. 使用列表推导式和 `sum()`

列表推导式可以与 `sum()` 函数结合使用来统计字符出现的次数：

```
text = "example string"
char = "e"
count = sum(char == current_char for current_char in text)
print(f"字符 '{char}' 出现了 {count} 次。")
```

5. 使用 `numpy` 或 `pandas`

如果你已经安装了 `numpy` 或 `pandas`，这些库提供了更高效的计数方法：

```
import numpy as np

text = np.array("example string")
unique, counts = np.unique(text, return_counts=True)
char_count = dict(zip(unique, counts))

print(char_count)
```

或者使用 `pandas`：

```
import pandas as pd

text = pd.Series(list("example string"))
char_count = text.value_counts()

print(char_count)
```

选择哪种方法？

- 如果你只需要统计一个字符，使用 `count()` 方法就足够了。
- 如果需要统计整个字符串中所有唯一字符的出现次数，`collections.Counter` 是一个非常方便的选择。
- 如果你处理的是非常大的数据集，并且需要更高效的计数，可以考虑使用 `numpy` 或 `pandas`。

## 4.24

1. python中数据变量一般都是小数，做索引时要先把它int化。在py的二分法时，出现了一个错误就是直接`middle=(i+j)/2`，得到的middle是一个float类型，无法用于索引，加一个强制转换为int即可。或者是使用py中的整数除法`\\`这样得到的middle值为整数。`middle=(i+j)//2`.这样可能会有i+j溢出的风险，因此参考答案的解法更值得记忆：`mid=(j-i)//2+i`因为i和j不可能溢出，而i+j可能溢出。

2. python连续初始化并不能用逗号连接，在二分法中，我曾尝试`i=0,j=length-1`这样来赋值，但是报错了。若想在一行内完成多个变量的初始化赋值，需要分号连接。改为`i=0;j=length-1`即可成功运行。

3. 对list类型数据的原始操作：

   <center>关键词：list<center>

   <center>关键词：对list的操作<center>

   - 尾部插入数据`list.append(val)`
   - 指定索引处插入数据（index取0标志首部插入数据）`list.insert(index,val)`
   - 通过值删除元素`list.remove(val)`
   - 通过索引删除元素`del list[index]`
   - 通过索引进行切片操作(左闭右开)`sub_list=list[begin:end]`
   - 排序（默认升序，降序可选）`list.sort([reverse=True])`
   - 快速创建列表推导`sq_list=[x**2 for x in list]`
   - 列表连接，用加号`combine_list=list+[val1,val2]`
   - 列表本体连接`list.extend(another_list)`
   - 列表元素计数`count=list.count(val)`统计val在列表中出现的次数
   - 列表反转`list.reverse()`
   - 查找元素索引`index=list.index(val)`查找第一个val的索引值
   - 列表去重（使用集合的方法）`unique_list=list(set(list))`原理是把列表转化为集合后自动去除重复元素
   - 列表排序+去重`unique_sorted_list=sorted(set(list))`先去重后排序，因为sorted()返回一个列表类型数据

4. `bisect`是py标准库中的模块，可以完成二分插入和二分搜索。常见函数有

   - `bisect_left(a, x, lo=0, hi=None)`
     这个函数将 `x` 插入到数组 `a` 中，以保持数组的有序性，并且返回`x`在数组中的插入点索引。如果数组中已经存在与`x`相等的元素，则会返回最左边（即索引最小的）那个相等元素的索引。如果没有指定 `lo` 和 `hi`，则在整个数组中进行搜索。

   - `bisect_right(a, x, lo=0, hi=None)`
     与 `bisect_left` 类似，但是返回最右边的那个相等元素的索引。如果没有相等元素，则返回`x`应该插入的位置，该位置会大于所有小于`x`的元素的索引。

   - `insort_left(a, x, lo=0, hi=None)`
     在 `a` 中插入 `x`，保持有序性，并返回插入后的数组。如果没有指定 `lo` 和 `hi`，则在整个数组中进行插入。

   - `insort_right(a, x, lo=0, hi=None)`

     与 `insort_left` 类似，但是插入后 `x` 会是右侧插入点相等元素中的第一个。


## 4.25

巩固了对list类型数据操作的记忆，学了双指针的操作

## 4.26

循环数组没必要根据下标，直接循环本身即可。

## 4.27

### np中的argmax和argmin

这两个函数是np中的函数，返回的是当前列表中最大/最小元素的索引值。这个知识点是在学机器学习的时候积累的。但是本题使用这个做法没有意义。

### py中的滑动窗口

py中实现更为简单，使用enumerate会很方便。

## 4.28

### py初始化二维数组

`result=[[]*n]*m`得到一个m行n列的二维数组。比如创建`result=[[0]*4]*4`实际上创建了一个包含4个对同一个列表引用的列表。这意味着当你修改 `result[0][0]` 的值时，所有其他行的第一个元素也会被修改，因为它们都是同一个对象的引用。这就是为什么你不会得到预期的结果 `[[2, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]`。

对二维数组的修改和访问直接调用下标即可。

初始化真正独立的二维数组的方式：

方法一：使用列表推导式和map：

`result=list(map(lambda _: [0]*n,range(n)))`这里的map函数把一个匿名函数`lambda _:[0]*n`应用到`range(n)`生成的序列上，创建了四个独立的列表。

方法二：使用两层循环

```python
result=[]
for _ in range(n):
    result.append([0]*n)
```

参考答案生成的result二维数组实际上是使用双层for：`result=[[0 for _ in range(n)] for _ in range(n)]`先生成内层列表，再生成外层

### try和except

在Python中，`try` 和 `except` 是异常处理的关键组成部分，它们允许程序在遇到错误时以更可控的方式响应，而不是直接崩溃。异常处理是一种结构化的方法，用于捕获程序执行中出现的异常（错误）。

#### try 语句

`try` 语句使程序员能够标记一个代码块，在该代码块中，可能会发生异常。`try` 块让你可以测试代码以查找错误，而不会立即让程序崩溃。

#### except 语句

`except` 语句用于捕获 `try` 块中发生的异常。你可以为 `except` 指定一个或多个异常类型，以确定应该处理哪些类型的异常。

#### 基本用法

```python
try:
    # 尝试执行的代码
    pass
except ExceptionType:
    # 当特定类型的异常发生时执行的代码
    pass
```

#### 详细解释

1. **try 块**：`try` 关键字后面跟着一个代码块，这个代码块包含了可能会引发异常的代码。

2. **except 块**：如果 `try` 块中的代码抛出了一个异常，程序的执行将立即跳转到 `except` 块。`except` 块可以捕获并处理特定的异常类型。

3. **异常类型**：在 `except` 后面，你可以指定一个异常类型，以捕获特定类型的异常。你也可以捕获所有类型的异常，使用 `except Exception`（其中 `Exception` 是所有非系统退出类异常的基类）。

4. **多个 except 块**：你可以有多个 `except` 块来处理不同类型的异常。

5. **finally 块**：`finally` 块用于执行无论是否发生异常都要执行的代码，比如清理资源。

6. **else 块**：`else` 块用于当 `try` 块中没有异常发生时执行的代码。

#### 示例

```python
try:
    # 尝试读取文件
    with open('file.txt', 'r') as f:
        data = f.read()
except FileNotFoundError:
    # 如果文件不存在，打印错误信息
    print("文件未找到。")
except Exception as e:
    # 捕获其他类型的异常
    print(f"发生了一个错误：{e}")
else:
    # 如果没有异常发生，处理数据
    print("文件读取成功，数据为：", data)
finally:
    # 无论是否发生异常，都会执行
    print("这是 finally 块。")
```

在这个例子中，如果 `file.txt` 文件不存在，将引发 `FileNotFoundError` 并被第一个 `except` 块捕获。如果发生了其他类型的异常，它将被第二个 `except` 块捕获。无论是否发生异常，`finally` 块中的代码都将执行。

通过使用 `try` 和 `except`，你可以创建更加健壮和用户友好的程序，因为它允许你优雅地处理错误情况。

## 4.29

###  py定义链表

```python
class ListNode:
    def __init__(self, val, next=None):
        self.val = val
        self.next = next
```

py判断节点是否为空不用 `p!=none`这样的写法，直接`if !p`即可，这样就完成了对p节点是否为空的判断。

py无需手动删除不需要节点的内存空间，它会自动删除。因此和C++不同，有节点pre和后继p，删除p：`pre.next=p.next;p=p.next`就可以了，不用像C++那样定义一个tmp在对其进行delete操作。

### 创建和释放链表的节点

在Python中，创建和释放链表节点通常涉及到类的定义和引用计数的管理。Python本身并没有内置的链表数据结构，但可以通过类来模拟链表的行为。下面是一个简单的单链表节点类的定义，以及如何创建和释放节点的示例。

#### 单链表节点类的定义

```python
class ListNode:
    def __init__(self, value=0, next=None):
        self.value = value  # 节点存储的值
        self.next = next    # 指向下一个节点的指针
```

在这个类中，每个节点包含一个值（`value`）和一个指向下一个节点的指针（`next`）。`next` 默认为 `None`，表示链表的末尾。

#### 创建链表节点

创建链表节点非常简单，只需要实例化 `ListNode` 类：

```python
# 创建头节点（可以不存储实际数据）
head = ListNode()

# 创建其他节点
node1 = ListNode(1)
node2 = ListNode(2)
node3 = ListNode(3)

# 构建链表
head.next = node1
node1.next = node2
node2.next = node3
```

#### 释放链表节点

在Python中，内存管理是自动的，使用了引用计数和垃圾回收机制。当一个对象的引用计数降到0时，Python解释器会自动调用对象的 `__del__` 方法并释放内存。但是，对于链表这种包含多个对象引用的场景，我们需要手动将不再使用的节点的引用设置为 `None`，以避免循环引用导致的内存泄漏。

```python
# 假设我们要释放 node2
node2.next = None  # 断开对下一个节点的引用

# 由于 node2 没有其他引用指向它，它的引用计数变为0，Python会自动垃圾回收
node3 = None  # 同样，释放 node3
```

#### 注意事项

- **循环引用**：在链表中，如果不注意，可能会形成循环引用，导致引用计数永远不会降到0，从而造成内存泄漏。因此，当链表节点不再需要时，应手动将相关引用设置为 `None`。
- ** `__del__` 方法**：虽然Python会自动管理内存，但如果你想要自定义销毁链表节点时的行为（比如释放外部资源），可以为 `ListNode` 类定义一个 `__del__` 方法。
- **内存管理**：在Python中，通常不需要手动管理内存，但是对于复杂的数据结构，如链表，了解引用计数和垃圾回收的原理是有益的。

#### 使用上下文管理器

为了更安全地管理链表节点的生命周期，可以使用Python的上下文管理器：

```python
class ListNode:
    def __init__(self, value=0):
        self.value = value
        self.next = None

    def __del__(self, value=None):
        print(f"ListNode({self.value}) has been deleted.")

# 使用 with 语句
with ListNode(1) as node:
    print(node.value)
# 输出: ListNode(1) has been deleted.
```

使用 `with` 语句和上下文管理器可以确保即使发生异常，链表节点也能被正确地清理。这是一种编写更安全代码的方法，尤其是在涉及到资源管理时。

## 4.30

### py中不同类之间的调用

在Python中，不同类之间的调用通常涉及以下几个方面：

#### 1. 创建实例

你可以创建另一个类的实例，即使这个类是在另一个类定义的内部。

```python
class OuterClass:
    def __init__(self):
        self.inner = InnerClass()

class InnerClass:
    def say_hello(self):
        return "Hello from InnerClass"

# 创建 OuterClass 的实例
outer = OuterClass()

# 通过 outer 实例调用 InnerClass 的方法
print(outer.inner.say_hello())  # 输出: Hello from InnerClass
```

#### 2. 作为属性或方法的返回值

一个类的对象可以作为另一个类的属性或方法的返回值。

```python
class Engine:
    def start(self):
        return "Engine started"

class Car:
    def __init__(self):
        self.engine = Engine()

    def start_car(self):
        return self.engine.start()

# 创建 Car 的实例并调用方法
my_car = Car()
print(my_car.start_car())  # 输出: Engine started
```

#### 3. 作为参数传递

一个类的对象可以作为参数传递给另一个类的构造函数或方法。

```python
class NavigationSystem:
    def give_directions(self):
        return "Giving directions to the destination"

class Car:
    def __init__(self, navigation_system):
        self.navigation = navigation_system

    def start_trip(self):
        return self.navigation.give_directions()

# 创建 NavigationSystem 的实例
nav_system = NavigationSystem()

# 将 nav_system 实例作为参数传递给 Car 的构造函数
my_car = Car(nav_system)

# 调用方法
print(my_car.start_trip())  # 输出: Giving directions to the destination
```

#### 4. 继承

一个类可以通过继承另一个类来复用其功能，这允许派生类访问基类的属性和方法。

```python
class Vehicle:
    def start(self):
        return "Vehicle started"

class Car(Vehicle):
    def start_engine(self):
        super().start()
        print("Engine roar")

# 创建 Car 的实例并调用方法
my_car = Car()
my_car.start_engine()  # 输出: Vehicle started 和 Engine roar
```

#### 5. 组合

组合是指一个类的对象作为另一个类的属性，这与继承不同，因为组合是一种“has-a”关系。

```python
class Tire:
    def inflate(self):
        return "Tire inflated"

class Car:
    def __init__(self):
        self.tires = [Tire(), Tire(), Tire(), Tire()]

    def inflate_tires(self):
        for tire in self.tires:
            print(tire.inflate())

# 创建 Car 的实例并调用方法
my_car = Car()
my_car.inflate_tires()  # 输出四次 Tire inflated
```

#### 6. 多态

多态是指对象可以有多种形式，允许你将不同类型的对象视为同一类的对象。

```python
class Vehicle:
    def start(self):
        pass

class Car(Vehicle):
    def start(self):
        return "Car started"

class Motorcycle(Vehicle):
    def start(self):
        return "Motorcycle started"

def start_vehicle(vehicle):
    print(vehicle.start())

# 创建不同类型的实例
car = Car()
motorcycle = Motorcycle()

# 使用多态通过基类类型引用调用派生类的方法
start_vehicle(car)        # 输出: Car started
start_vehicle(motorcycle)  # 输出: Motorcycle started
```

在Python中，类的调用和交互非常灵活，支持面向对象编程的所有基本特性，如封装、继承和多态。通过这些机制，你可以构建复杂的程序结构，同时保持代码的清晰和可维护性。

### py中类的self如何使用

在Python中，`self` 是一个约定俗成的名称，用于指代类实例的本身。当你创建一个类时，任何实例方法的第一个参数（无论是命名的还是位置的）都应该是 `self`。Python解释器在调用实例方法时会自动传递 `self` 参数。

#### `self` 的用途：

1. **访问实例属性**：`self` 用于明确区分局部变量和实例的属性或方法。

2. **调用其他实例方法**：在实例方法内部，可以通过 `self` 调用类的其他方法。

3. **从实例方法返回实例**：通常，实例方法返回 `self` 对象的引用，这允许方法链。

4. **初始化实例**：在类的 `__init__` 方法中，`self` 用于访问或初始化实例的属性。

#### 示例：

```python
class MyClass:
    def __init__(self, value):
        self.value = value  # 使用 self 来初始化实例属性

    def print_value(self):
        print(self.value)  # 使用 self 来访问实例属性

    def __del__(self):
        print(f"{self.value} is being deleted.")  # 使用 self 引用实例

# 创建实例
my_object = MyClass(10)

# 调用实例方法
my_object.print_value()  # 输出: 10

# 实例销毁时自动调用析构函数
del my_object
# 输出: 10 is being deleted.
```

#### 注意事项：

- **非显式传递**：虽然 `self` 参数看起来像是需要手动传递，但实际上，当你通过实例调用方法时，Python解释器会自动将实例的引用作为第一个参数传递给方法。

- **构造函数**：`__init__` 方法是类的构造函数，它在创建类的新实例时被调用。`self` 在 `__init__` 方法中用于访问或设置实例的属性。

- **方法定义**：在定义实例方法时，`self` 必须作为方法的第一个参数，即使方法不使用它。

- **类方法和静态方法**：对于类方法（使用 `@classmethod` 装饰器），第一个参数是类（通常命名为 `cls`），而不是实例。静态方法（使用 `@staticmethod` 装饰器）不需要类或实例的引用作为第一个参数。

- **返回 self**：实例方法通常返回 `self` 对象，这允许方法链的使用，例如：`obj.method1().method2()`。

通过使用 `self`，你可以确保在类的实例方法中正确地访问和操作实例的属性和方法。这是Python面向对象编程的一个基本原则。

### py中对链表依据索引值的遍历访问方式

那么提前就需要准备一个size表示链表的容量。

```python
for i in range(size):
    print(p.val)
    p=p.next
```

这样子可以完成对链表的遍历。

还可以

```python
#假设头节点为head
current=head
index=0
while current and index!=target:
    print(current.val)
    current=current.next
    index+=1
```

还可以创建一个索引映射来加速访问

```python
index_map={}
current=head
index=0
while current:
    index_map[index]=current
    current=current.next
    index+=1

print(index_map[target].val)
```



### py中一个函数调用另一个函数

如果目的是调用完毕此函数即可，则必须在调用函数后面添加return语句，否则后面的语句会被继续执行

如在本题中的根据索引添加节点的函数

```python
def addAtIndex(self, index: int, val: int) -> None:
    if index<0 or index>self.size: return
    if index==self.size:
        self.addAtTail(val)
        return#没有这个return，调用addtail后还会执行后面的函数和size+=1
    p=self.virtue_node
    for i in range(index):
        p=p.next
    new_node=LinkNode(val,p.next)
    p.next=new_node
    self.size+=1
```

调用`addAtTail()`之后如果没有return，则后面的语句被照常执行，元素被添加两遍且size+2

## 5.1

Python 语言中的平行赋值（也称为元组赋值或多变量赋值）是一种允许你在同一行代码中为多个变量赋值的语法。这种赋值通常用于同时从元组或列表中解包多个值。

### 平行赋值的基本语法：

```python
a, b = 1, 2
```

这行代码将值 `1` 分配给变量 `a`，将值 `2` 分配给变量 `b`。

### 平行赋值的高级用法：

1. **从序列中解包**：

```python
# 从元组中解包
a, b, c = (1, 2, 3)

# 从列表中解包
a, b, c = [1, 2, 3]
```

2. **交换变量的值**：

```python
a, b = 1, 2
a, b = b, a  # 交换 a 和 b 的值
```

3. **在函数返回多个值时使用**：

```python
def get_coordinates():
    return 10, 20

x, y = get_coordinates()  # 平行赋值用于接收多个返回值
```

4. **扩展赋值**：

你可以在赋值的右侧使用比左侧更多的值，Python 会自动丢弃多余的值。

```python
a, b = 1, 2, 3, 4  # a 将被赋值为 1，b 将被赋值为 2
```

5. **捕获未定义的变量**：

如果你在左侧使用比右侧更多的变量，Python 会为未赋值的变量赋值为 `None`。

```python
a, b, c = (1, 2)  # a 将被赋值为 1，b 将被赋值为 2，c 将被赋值为 None
```

6. **嵌套平行赋值**：

你可以在平行赋值中嵌套其他平行赋值。

```python
a, (b, c) = 1, (2, 3)  # a 将被赋值为 1，b 将被赋值为 2，c 将被赋值为 3
```

7. **解包序列中的序列**：

你可以解包序列中的序列，Python 允许你为内部序列指定变量名。

```python
a, (b, c) = [1, [2, 3]]  # a 将被赋值为 1，b 将被赋值为 2，c 将被赋值为 3
```

### 注意事项：

- 平行赋值要求左侧变量的数量与右侧序列中的元素数量一致，否则会引发 `ValueError`。
- 从Python 3.5开始，可以使用“星号赋值”（`*`）来捕获元组或列表中的剩余元素。

```python
a, *b, c = 1, 2, 3, 4  # a 将被赋值为 1，b 将是一个列表 [2, 3]，c 将被赋值为 4
```

平行赋值是Python中一种强大且表达性极强的特性，它允许你以简洁的语法进行复杂的赋值操作。



在 `Solution` 类的 `reverseList` 方法中，目标是将传入的链表反转。这个方法接收一个 `ListNode` 类型的参数 `head`，它指向链表的头节点，并返回一个新的头节点，该节点是原始链表反转后的结果。

以下是 `while` 循环中关键的一行代码的详细解释：

```python
cur.next, pre, cur = pre, cur, cur.next
```

这行代码是一个平行赋值（也称为元组赋值），它利用了Python的GIL（全局解释器锁）和赋值的原子性来在一行中完成三个赋值操作。这行代码的目的是更新三个变量 `cur.next`、`pre` 和 `cur` 的值，以实现链表节点的反转。

### 平行赋值的执行步骤：

1. `cur.next, pre, cur`：这三个变量将被赋予右侧表达式的值。
2. `= pre, cur, cur.next`：右侧的表达式按照从左到右的顺序求值，并将值赋给左侧的变量。

### 赋值过程：

- 首先，`cur.next` 被赋值为**当前**的 `pre` 值，这实际上是将当前节点的 `next` 指针指向前一个节点，从而反转链接的方向。
- 然后，`pre` 被赋值为**当前**的 `cur` 值，这样 `pre` 就指向了下一个要处理的节点。
- 最后，`cur` 被赋值为 `cur.next`，即当前节点的原始 `next` 指针，这样 `cur` 就移动到了下一个节点。

### 反转过程的示例：

假设我们有如下链表：`1 -> 2 -> 3 -> None`。

1. 初始状态：`cur` 指向 `1`，`pre` 为 `None`。
2. 执行平行赋值后：
   - `cur.next` (即 `1` 的 `next` 指针) 指向 `pre` (`None`)。
   - `pre` 指向 `cur` (`1`)。
   - `cur` 指向 `cur.next` (`2`)。
3. 下一个循环迭代：
   - `cur` 现在指向 `2`，`pre` 指向 `1`。
   - 重复上述过程。

这个过程会一直进行，直到 `cur` 为 `None`，表示链表已经完全遍历和反转。

### 为什么这样做是安全的？

由于Python的赋值操作是原子的，这意味着在多线程环境中，这行代码不会导致竞争条件。在单线程程序中，这行代码安全地重新链接了节点，而不会对链表的完整性造成风险。

这种方法是Python中常见的技巧，它利用了Python的赋值机制来简化代码并提高效率。

## 5.2

今日收获是可视化网站:[可视化执行](https://pythontutor.com/)，可以完全模拟一个程序的执行过程。

## 5.3

无

## 5.4

`a,b=b,a`可以完成a和b互换的操作

## 5.5

### 集合的初始化

特别注意：使用**强制类型转化为set，相同元素会被删除只保留一个**。且集合无序

1.  初始化一个空集合：`my_set=set()`

2. 花括号赋值：`my_set={1,2,3,4}`

3. 也可以从list类型强制转化为set类型：`my_list=[1,2,3,4]``my_set=set(my_list)`

4. 亦可以从其他类型强制转换，每一个字符都是集合的一个元素

   ```python
   >>> my_string="hello"
   >>> my_set=set(my_string)
   >>> my_set
   {'e', 'o', 'l', 'h'}
   >>> my_tuple=(1,2,2,3,4,4,5)
   >>> my_set=set(my_tuple)
   >>> my_set
   {1, 2, 3, 4, 5}
   >>> my_dict = {'a': 1, 'b': 2, 'c': 3, 'a': 4}
   >>> my_set = set(my_dict.keys())
   >>> my_set
   {'c', 'b', 'a'}
   ```

5. 使用集合的推导式来初始化`my_set={x**2 for x in range(10)}`

### 查找元素是否存在于集合中

#### 检查元素是否存在

使用in关键字

```python
my_set = {1, 2, 3, 4}

# 检查元素是否存在
if 3 in my_set:
    print("3 is in the set.")
else:
    print("3 is not in the set.")
```

#### 查找并返回元素

由于 `set` 是无序的，并且不保留元素的索引，所以你不能像列表或元组那样通过索引来查找并返回元素。但是，如果你知道元素在集合中，你可以通过遍历集合来找到它：

```python
for item in my_set:
    if item == 3:
        print("Found the element:", item)
        break
else:
    print("Element not found in the set.")
```

### 集合的相关操作

- `add()`：向集合添加一个新元素。
- `remove()` 或 `discard()`：从集合中移除一个元素。`remove()` 在元素不存在时会抛出 `KeyError`，而 `discard()` 不会。
- `union()` 或 `|`：集合的并集。
- `intersection()` 或 `&`：集合的交集。
- `difference()` 或 `-`：集合的差集。
- `symmetric_difference()` 或 `^`：集合的对称差集。

### py中同一个类下的函数如何调用

正确方法：使用`self.function`来调用自身实例中的其他函数。在第二种做法中我在原函数中错误地使用了`count=getcount(head)`这个写法，正确方式应该是`count=self.getcount(head)`，这样才能调用实例自身中的获取序号函数。长知识了。

## 5.6

Python collections模块中Counter()和defaultdict()详解：https://blog.csdn.net/weixin_44772440/article/details/122311744?

| 容器        | 用途                                                         |
| ----------- | ------------------------------------------------------------ |
| namedtuple  | 创建命名元组子类的工厂函数                                   |
| deque       | 类似列表(list)的容器，实现了在两端快速添加(append)和弹出(pop) |
| OrderDict   | 字典的子类，保存了他们被添加的顺序                           |
| defaultdict | 字典的子类，提供了一个工厂函数，为字典查询提供一个默认值     |
| Counter     | 字典的子类，提供了可哈希对象的计数功能                       |
| ChainMap    | 类似字典(dict)的容器类，将多个映射集合到一个视图里面         |
| UserDict    | 封装了字典对象，简化了字典子类化                             |
| UserList    | 封装了列表对象，简化了列表子类化                             |
| UserString  | 封装了字符串对象，简化了字符串子类化                         |

## 5.7

### 集合求交集的用法

使用函数intersection或者与符号\&，返回一个新的set类型数据。

intersection()方法将返回一个新集合，其中包含所有集合相同的元素。

两个或更多集合的交集是所有集合相同的元素集合。例如：

```python
A = {100, 7, 8}
B = {200, 4, 5}
C = {300, 2, 3}
D = {100, 200, 300}

print(A.intersection(D))
print(B.intersection(D))
print(C.intersection(D))
print(A.intersection(B, C, D))
'''
输出
{100}
{200}
{300}
set()
'''
A = {100, 7, 8}
B = {200, 4, 5}
C = {300, 2, 3, 7}
D = {100, 200, 300}

print(A & C)
print(A & D)


print(A & C & D)
print(A & B & C & D)
'''
{7}
{100}
set()
set()
'''
```

### py中对字典的操作

<center>关键词：字典<center>

<center>关键词：对字典的操作<center>

<center>关键词：dic<center>

在Python中，字典（`dict`）是一种可变容器模型，用于存储键值对。字典的每个键必须是唯一的，而值则不必唯一。以下是一些常用的字典操作方法：

#### 创建字典

```python
# 使用花括号创建一个空字典
my_dict = {}

# 使用花括号创建一个带有初始键值对的字典
my_dict = {'name': 'Alice', 'age': 25}

# 使用 dict() 函数创建字典
my_dict = dict(name='Alice', age=25)
```

#### 添加键值对

```python
# 直接赋值添加键值对
my_dict['height'] = 165

# 使用 .update() 方法添加一个或多个键值对
my_dict.update({'weight': 60}, city='New York')
```

#### 修改值

```python
# 通过键来修改值
my_dict['age'] = 26
```

#### 删除键值对

```python
# 使用 del 语句删除键值对
del my_dict['height']

# 使用 .pop() 方法删除键值对并返回值
age = my_dict.pop('age')

# 使用 .popitem() 方法删除并返回一个随机键值对
item = my_dict.popitem()
```

#### 查找键值对

**特别要学会运用字典中的`get`函数**

```python
# 通过键获取值
name = my_dict['name']

# 使用 .get() 方法获取值，如果键不存在则返回 None 或指定的默认值
weight = my_dict.get('weight', 'Unknown')
```

#### 遍历字典

```python
# 遍历所有键值对
for key, value in my_dict.items():
    print(f"{key}: {value}")

# 遍历所有键
for key in my_dict.keys():
    print(key)

# 遍历所有值
for value in my_dict.values():
    print(value)
```

#### 检查键是否存在

```python
# 使用 in 关键字检查键是否存在
if 'city' in my_dict:
    print("City key exists.")
```

#### 获取字典的长度

```python
# 获取字典中键值对的数量
length = len(my_dict)
```

#### 清空字典

```python
# 使用 .clear() 方法清空字典
my_dict.clear()
```

#### 字典推导式

```python
# 使用字典推导式创建新字典
squared_numbers = {x: x**2 for x in range(6)}
```

#### 默认值

```python
# 使用 .setdefault() 方法设置键的默认值
default_city = my_dict.setdefault('city', 'Unknown')
```

#### 注意事项

- 字典的键必须是不可变的类型，如字符串、数字、元组（只要元组内的元素也都是不可变的）。
- 尝试通过不存在的键访问值将抛出 `KeyError`，使用 `.get()` 方法可以避免这个错误。
- 字典是可变的，这意味着你可以更改、添加或删除键值对。
- 字典中键值对的顺序从Python 3.7开始是保持插入顺序的。

字典是Python中非常灵活和强大的数据结构，它在存储和管理关联数据时非常有用。

## 5.8

### py逐位获取整数的每一位（数位分离）

<center>关键词：数位分离<center>

<center>关键词：int数字分割<center>

在Python中，逐位获取一个整数的每一位数字可以通过几种不同的方法实现。以下是一些常用的方法：

#### 方法1：使用循环和模10运算

```python
number = 1564
while number > 0:
    digit = number % 10  # 获取当前最低位的数字
    print(digit)
    number //= 10  # 移除当前最低位
```

这个方法通过不断地对整数进行模10运算来获取最低位的数字，然后通过整除10来移除该位。

#### 方法2：将整数转换为字符串

```python
number = 1564
for digit in str(number):
    print(int(digit))
```

这个方法首先将整数转换为字符串，然后遍历字符串中的每个字符，并将每个字符转换回整数。

#### 方法3：使用列表推导式

```python
number = 1564
digits = [int(digit) for digit in str(number)]
print(digits)
```

列表推导式是一种简洁的方法，可以快速生成一个包含整数每一位数字的列表。

#### 方法4：使用 `map` 函数

```python
number = 1564
digits = list(map(int, str(number)))
print(digits)
```

这里，我们使用 `map` 函数将字符串中的每个字符转换为整数，并将其转换为列表。

#### 方法5：使用 `divmod`

```python
number = 1564
digits = []
while number > 0:
    number, digit = divmod(number, 10)
    digits.append(digit)
print(digits[::-1])  # 反转列表，因为它们是逆序获得的
```

`divmod` 函数返回一个元组，包含整除和取模的结果，这可以用来获取最低位的数字。

#### 方法6：使用 `math.ceil` 和 `math.log10`

```python
import math
number = 1564
length = math.ceil(math.log10(number))  # 计算数字的位数
for _ in range(length):
    number //= 10
    print(number)
```

这个方法首先计算数字的位数，然后通过循环和整除10来逐位打印数字。

选择哪种方法取决于你的具体需求和个人喜好。通常，将整数转换为字符串然后遍历它是一种简单且直接的方法。如果你需要处理非常大的整数，或者需要更复杂的操作，可能需要考虑其他方法。

## 5.9

### py中的Counter函数

<center>关键词：Counter函数<center>

在 Python 中，`Counter` 是 `collections` 模块中的一个类，它用于计数可哈希对象。它也被称为直方图（histogram），因为它类似于统计数据中出现的频率分布。`Counter` 类在处理计数问题时非常有用，如词频统计、投票计数等。

以下是 `Counter` 类的一些关键特性和方法：

#### 初始化

你可以通过几种不同的方式初始化 `Counter` 对象：

1. 空 `Counter()` 创建一个空的计数器。
2. `Counter(iterable)` 通过迭代器来初始化计数器，计数迭代器中每个元素出现的次数。

#### 常用方法

- `__contains__`: 检查元素是否在计数器中。
- `elements()`: 返回一个迭代器，生成计数器中的元素，重复次数与计数相符。
- `most_common()`: 返回一个列表，包含计数器中最常出现的元素及其计数，按降序排列。可以限制返回的元素数量。
- `subtract()`: 减去另一个计数器中的计数，或者减去通过 `iterable` 提供的元素。
- `update()`: 基于另一个计数器或 `iterable` 更新当前计数器。

#### 示例

```python
from collections import Counter

# 初始化一个空的 Counter 对象
c = Counter()

# 通过可迭代对象初始化
words = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
word_counts = Counter(words)

# 打印计数结果
print(word_counts)  # 输出: Counter({'apple': 2, 'orange': 2, 'pear': 1, 'banana': 1})

# 更新计数器
word_counts.update(['orange', 'orange', 'orange'])

# 打印更新后的计数结果
print(word_counts)  # 输出: Counter({'orange': 5, 'apple': 2, 'pear': 1, 'banana': 1})

# 检查元素是否存在
print('orange' in word_counts)  # 输出: True

# 返回计数器中最常见的元素及其计数
print(word_counts.most_common(1))  # 输出: [('orange', 5)]

# 元素的减法操作
another_counter = Counter(['orange', 'grape'])
word_counts.subtract(another_counter)
print(word_counts)  # 输出: Counter({'apple': 2, 'pear': 1, 'banana': 1})

# 元素的迭代
for elem in word_counts.elements():
    print(elem, end=' ')  # 可能的输出顺序: apple pear banana
```

`Counter` 对象的行为类似于字典，但它的值表示元素的计数，并且计数器中元素的顺序并不重要。

#### 注意事项

- 计数器中的元素必须是可哈希的，这意味着它们必须有稳定的哈希值。
- 如果元素在迭代器中重复出现，它们的计数会增加。
- `Counter` 对象的键（元素）和值（计数）可以被分别修改，但通常你会使用 `Counter` 类的内置方法来处理计数。

`Counter` 是处理计数问题的一个非常有用的工具，它提供了一种简洁、高效的方式来跟踪元素的出现次数。

## 5.10

### py获取字符的ASCII

<center>关键词：ASCII<center>

因为在py中无法像C++一样两个字符做差得到相对位置，在py中无法实现两个str类型数据的减法操作，因此需要借助ascii转化

获取字符的ascii使用函数：`ord()`

ASCII转字符使用函数：`chr()`

```python
>>> ch = 'g'
>>> ord(ch)
103
>>> chr(103)
'g'
```

## 5.11

### 数组的排序

可以使用`nums.sort()`直接完成排序，也可以`nums = sorted(nums)`完成排序

### 二维数组中插入一个一维数组

第一种是定义一个临时一维数组tmp，元素分别append到一维数组里面，然后再把tmp给append到二维数组里面。

第二种方法是直接对二维数组append一个维数组：`nums.append([1,2,3])`，因为list类型定义的时候就是用中括号，在这里用中括号括起来数据就相当于定义了一个临时一维数组。

## 5.12

### 统计数组中每个数字出现的次数并可以根据数字访问出现的频次

<center>关键词：统计频次<center>

<center>关键词：counter函数<center>


在Python中，统计数组中每个数字出现的次数并允许根据数字访问出现的频次，可以使用内置的`collections.Counter`类，它是一个专门的字典子类，用于计数可哈希对象。以下是如何使用`Counter`的示例：

```python
from collections import Counter

# 假设这是我们的数组
array = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]

# 使用 Counter 统计每个数字出现的次数
counter = Counter(array)

# 输出每个数字及其出现的次数
print(counter)

# 根据数字访问出现的频次
number = 3
count = counter[number]  # 获取数字3出现的次数
print(f"Number {number} appears {count} times in the array.")
```

在这个例子中，`Counter(array)` 创建了一个计数器对象，其中键是数组中的数字，值是这些数字出现的次数。然后，你可以通过数字作为键来访问它的频次。

如果你想要手动实现这个功能，而不是使用`Counter`，可以使用字典来存储每个数字的计数：

```python
array = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]

# 创建一个空字典来存储计数
count_dict = {}

# 遍历数组并更新计数
for num in array:
    if num in count_dict:
        count_dict[num] += 1
    else:
        count_dict[num] = 1

# 输出每个数字及其出现的次数
print(count_dict)

# 根据数字访问出现的频次
number = 3
count = count_dict.get(number, 0)  # 使用 get 方法，如果数字不在字典中则返回0
print(f"Number {number} appears {count} times in the array.")
```

在这个手动实现中，我们首先创建了一个空字典`count_dict`，然后遍历数组，对于数组中的每个数字，如果它已经在字典中，就将其计数加一，如果不在字典中，就将其添加到字典中并设置计数为1。最后，我们使用`dict.get()`方法来访问特定数字的计数，如果该数字不在字典中，`get`方法将返回默认值0。

## 5.13

### py中的栈

<center>关键词：栈<center>

在Python中，栈（Stack）是一种遵循后进先出（LIFO，Last In First Out）原则的线性数据结构。在栈中，元素的添加（push）和删除（pop）操作都发生在栈的同一侧，称为栈顶。

以下是栈的一些基本操作和特性：

#### 初始化栈

在Python中，可以使用列表（list）来模拟栈的操作，因为列表具有动态数组的特性，可以方便地进行元素的添加和删除。

```python
stack = []
```

#### 元素添加（Push）

在栈顶添加一个新元素，可以使用列表的`append()`方法。

```python
stack.append(element)
```

#### 元素删除（Pop）

从栈顶删除一个元素，并返回该元素，可以使用列表的`pop()`方法。如果栈为空，`pop()`方法会抛出一个`IndexError`异常。

```python
element = stack.pop()
```

#### 查看栈顶元素

查看栈顶元素，但不删除它，可以使用列表的索引操作。

```python
top_element = stack[-1]
```

#### 栈的大小

获取栈中元素的数量，可以使用列表的`len()`函数。

```python
size = len(stack)
```

#### 判断栈是否为空

判断栈是否为空，可以使用列表的`len()`函数或直接使用`not`操作符。

```python
is_empty = len(stack) == 0  # 或者 is_empty = not stack
```

#### 清空栈

清空栈中的所有元素，可以使用列表的`clear()`方法。

```python
stack.clear()
```

#### 示例

下面是一个使用Python列表实现栈的简单示例：

```python
stack = []

# 元素添加
stack.append(1)
stack.append(2)
stack.append(3)

# 查看栈顶元素
print(stack[-1])  # 输出: 3

# 元素删除
print(stack.pop())  # 输出: 3
print(stack.pop())  # 输出: 2

# 栈的大小
print(len(stack))  # 输出: 1

# 判断栈是否为空
print(len(stack) == 0)  # 输出: False

# 清空栈
stack.clear()
print(len(stack))  # 输出: 0
```

#### 注意事项

- Python本身没有内置的栈数据结构，但可以使用列表、元组或集合等其他数据结构来模拟栈的行为。
- 在模拟栈操作时，要注意Python列表的`pop()`方法默认从右侧删除并返回元素，这与栈的LIFO原则相反。因此，通常使用`pop()`方法的索引参数`stack.pop(0)`来模拟栈的pop操作。
- 栈的应用场景包括函数调用的逆序执行（调用栈）、表达式求值、回溯算法等。

栈是一种基础且重要的数据结构，在很多算法和程序设计中都有广泛应用。在Python中，通过合理利用列表等内置数据结构，可以方便地实现栈的各种操作。

### py中的reverse函数和reversed函数

<center>关键词：逆置<center>
<center>关键词：reverse函数<center>
<center>关键词：reversed函数<center>

在Python中，`reverse` 和 `reversed` 都与反转序列相关，但它们在用法和行为上有所不同。

#### `reverse()` 方法

`reverse()` 是列表（list）的一个方法，用于原地反转列表中的元素顺序。这意味着它直接修改调用该方法的列表，而不返回一个新的列表或原列表的副本。

```python
my_list = [1, 2, 3, 4, 5]
my_list.reverse()
print(my_list)  # 输出: [5, 4, 3, 2, 1]
```

`reverse()` 方法没有返回值，即使它修改了列表本身。因此，如果你尝试打印 `my_list.reverse()` 的结果，你将得到 `None`。

#### `reversed()` 函数

`reversed()` 是一个内置函数，它接受一个序列（如列表、元组或字符串），并返回一个迭代器，该迭代器按逆序提供序列中的元素。

```python
my_list = [1, 2, 3, 4, 5]
reversed_iterator = reversed(my_list)
print(list(reversed_iterator))  # 输出: [5, 4, 3, 2, 1]
```

`reversed()` 函数返回的是一个迭代器，不是列表。如果你需要一个列表形式的反转序列，可以使用 `list()` 函数将迭代器转换为列表。

#### 字符串反转

对于字符串，由于它们是不可变的，`reversed()` 函数可以用来创建一个逆序的字符串迭代器，但不能用 `reverse()` 方法，因为字符串没有这个方法。

```python
my_string = "hello"
reversed_string_iterator = reversed(my_string)
print(''.join(reversed_string_iterator))  # 输出: "olleh"
```

#### 总结

- `reverse()` 是列表的实例方法，原地反转列表，没有返回值。
- `reversed()` 是一个内置函数，返回一个迭代器，可以用于任何可迭代对象的逆序访问。

根据你的需求，你可以选择使用 `reverse()` 方法或 `reversed()` 函数。如果你需要修改现有列表，使用 `reverse()`。如果你需要保留原始序列并创建一个新的反转序列，使用 `reversed()`。

### list类型数据逆置/反转的可行方法

1. 双指针交换前后元素
2. 借助栈，输入：append；输出：pop
3. 数学推导，使用range函数：`for i in range(n//2):  s[i],s[n-1-i] = s[n-1-i],s[i]`
4. 使用reverse函数，直接`s.reverse()`
5. 使用reversed函数，该函数返回迭代对象，需要`s[:] = reversed(s)`
6. 使用list的切片操作：`s[:]=s[::-1]`
7. 列表的推导：`s[:] = [s[i] for i in range(len(s)-1, -1, -1)]`

## 5.14

### py改变字符串

<center>关键词：字符串<center>

在Python中，字符串是可迭代的数据类型，你可以通过下标（索引）来访问和修改字符串中的单个字符。字符串的索引也是基于0的，即第一个字符的索引是0。

#### 访问字符串中的字符

要访问字符串中的特定字符，你可以使用方括号`[]`，后面跟上你想要的字符的索引。

```python
my_string = "Hello, World!"
char_at_index_7 = my_string[7]  # 'W'
```

#### 修改字符串中的字符

Python中的**字符串是不可变的**，这意味着你不能直接修改字符串中的单个字符。但是，你可以通过创建一个新的字符串来实现“修改”字符的目的。

例如，如果你想将字符串中的某个字符替换为另一个字符，可以这样做：

```python
my_string = "Hello, World!"
index_to_modify = 7  # 假设我们要修改索引为7的字符

# 创建一个新的字符串，其中包含了原始字符串，除了修改的字符
new_string = my_string[:index_to_modify] + 'A' + my_string[index_to_modify + 1:]

print(new_string)  # "Hello, World!" 中的 'W' 被替换为 'A'，结果为 "Hello, Aorld!"
```

在这个例子中，我们创建了一个新的字符串 `new_string`，它由三部分组成：

1. 原始字符串 `my_string` 从开始到索引 `index_to_modify`（不包括该索引）的部分。
2. 我们想要的新字符 `'A'`。
3. 原始字符串 `my_string` 从索引 `index_to_modify + 1` 到末尾的部分。

#### 使用字符串推导式

你也可以使用字符串推导式来创建修改后的字符串：

```python
new_string = ''.join([my_string[:7], 'A', my_string[8:]])
```

这行代码使用了相同的逻辑，但是更加简洁。

#### 注意

由于字符串是不可变的，所以当你“修改”一个字符串时，实际上是在创建一个新的字符串对象。原来的字符串保持不变。这种特性使得字符串操作在多线程环境中是安全的。如果你需要频繁修改字符串内容，可能需要考虑使用列表（`list`），列表中的元素是可变的。

### py从list到str

有一个修改后的list型数据，要转化为str类型：

`return ''.join(listType)`

### py中的for循环

for和in相连用，range可以设置步长，比如说`for i in range(0,n,2*k)`的使用

## 5.15

### py中判断某一字符的类型

<center>关键词：类型判断<center>

<center>关键词：数据类型判断
<center>

在Python中，如果你想要判断一个字符的类型，通常是指检查它是否是字母、数字、空白字符等。Python提供了一些内置的函数和模块来帮助进行这些判断。以下是一些常用的方法：

#### 使用内置函数

1. `str.isalpha()`：检查字符串中的所有字符是否都是字母。

2. `str.isdigit()`：检查字符串中的所有字符是否都是数字。

3. `str.isnumeric()`：类似于 `isdigit()`，但还包括数字字符（如罗马数字）。

4. `str.isspace()`：检查字符串是否只包含空白字符。

5. `str.islower()`：检查字符串中的所有字母字符是否都是小写。

6. `str.isupper()`：检查字符串中的所有字母字符是否都是大写。

#### 示例

```python
char = 'A'

if char.isalpha():
    print(f"'{char}' 是字母。")
elif char.isdigit():
    print(f"'{char}' 是数字。")
elif char.isspace():
    print(f"'{char}' 是空白字符。")
else:
    print(f"'{char}' 不是字母、数字或空白字符。")
```

#### 使用正则表达式

你还可以使用正则表达式来检查字符的类型。Python的 `re` 模块提供了正则表达式的功能。

```python
import re

char = 'A'

if re.match('^[a-zA-Z]$', char):
    print(f"'{char}' 是字母。")
elif re.match('^[0-9]$', char):
    print(f"'{char}' 是数字。")
# 正则表达式可以编写更复杂的规则来匹配特定的字符类型
```

#### 注意事项

- 内置的字符串方法适用于检查整个字符串，如果你只想检查单个字符的类型，可以对单个字符使用这些方法。

- 正则表达式提供了更灵活的字符类型检查方式，但可能需要更复杂的规则。

- 如果你只是想检查变量是否是字符串类型，可以使用 `isinstance()` 函数：

  ```python
  char = 'A'
  if isinstance(char, str):
      print(f"'{char}' 是一个字符串。")
  ```

使用这些方法，你可以在Python中判断字符的类型，并根据需要进行相应的处理。

## 5.16

### py中的split函数

<center>关键词：split<center>
<center>关键词：split函数<center>

<center>关键词：分割列表<center>



在Python中，`split()` 是字符串（`str`）对象的一个方法，用于将字符串分割成一个列表（`list`）中的多个子字符串。默认情况下，如果没有指定分隔符，`split()` 方法会根据空白字符（如空格、制表符、换行符等）来分割字符串。

#### 基本用法

```python
str.split([sep, [maxsplit]])
```

- `sep`：分隔符。可以是字符串或正则表达式，用于标识子字符串之间的边界。如果不提供，则任何空格字符都作为分隔符。
- `maxsplit`：可选参数，指定最大分割次数，0表示没有限制（默认为0）。

#### 示例

##### 默认分隔符

```python
s = "One two three four"
print(s.split())  # 输出: ['One', 'two', 'three', 'four']
```

在这个例子中，`split()` 方法根据空格字符将字符串分割成多个子字符串。

##### 指定分隔符

```python
s = "One,two,three,four"
print(s.split(","))  # 输出: ['One', 'two', 'three', 'four']
```

在这个例子中，我们指定了逗号（`,`）作为分隔符。

##### 使用正则表达式作为分隔符

```python
import re

s = "One;two,three;four"
print(re.split(r"[;,]", s))  # 输出: ['One', 'two', 'three', 'four']
```

在这个例子中，我们使用了正则表达式 `[;,]` 作为分隔符，它可以匹配分号（`;`）或逗号（`,`）。

##### 限制分割次数

```python
s = "One two three four five"
print(s.split(None, 2))  # 输出: ['One', 'two', 'three four five']
```

在这个例子中，我们限制了分割次数为2，因此字符串在分割成两个子字符串后不再继续分割。

#### split()与split(' ')的区别

split()的时候，多个空格当成一个空格；split(' ')的时候，多个空格都要分割，每个空格分割出来空。

#### 注意事项

- 如果分隔符是一个字符串，那么返回的子字符串中不会包含该分隔符。
- 如果分隔符是一个正则表达式，那么返回的子字符串中可能包含匹配的分隔符，具体取决于正则表达式的匹配规则。
- 如果原始字符串为空，`split()` 方法将返回一个只包含一个空字符串的列表。
- `split()` 方法是惰性的，只有在需要时才会进行分割，这使得它在处理大型字符串时非常高效。

`split()` 方法是Python中处理字符串常用的方法之一，它在文本处理、数据解析和字符串操作中非常有用。

### py中的strip函数

<center>关键词：strip<center>

<center>关键词：strip函数
<center>

在Python中，`strip()` 函数是字符串（`str`）对象的一个方法，用于移除字符串两端的特定字符。默认情况下，如果没有指定任何参数，`strip()` 会移除字符串两端的所有空白字符，这包括空格、制表符（`\t`）、换行符（`\n`）、回车符（`\r`）以及任何其他在字符串开始或结束时的空白字符。

#### 基本用法

```python
str.strip([chars])
```

- `chars`（可选）：一个字符串，包含需要从字符串两端移除的字符集合。如果不提供，则默认移除空白字符。

#### 示例

##### 默认移除空白字符

```
s = "  Hello, World!  "
print(s.strip())  # 输出: "Hello, World!"
```

在这个例子中，`strip()` 方法移除了字符串两端的空格字符。

##### 移除指定字符

```
s = "--Hello, World!--"
print(s.strip("-"))  # 输出: "Hello, World!"
```

在这个例子中，我们指定了连字符（`-`）作为需要移除的字符。`strip()` 方法移除了字符串两端的连字符。

##### 移除多个不同字符

```
s = "----Hello, World!---"
print(s.strip("-"))  # 输出: "Hello, World!"
```

即使字符串两端有多个连字符，`strip()` 方法也只会移除两端的连字符，不会影响字符串中间的连字符。

```python
s = "  Hello, World!  "
print(s.strip())  # 输出: "Hello, World!"
```

在这个例子中，`strip()` 方法移除了字符串两端的空格字符。

##### 移除指定字符

```python
s = "--Hello, World!--"
print(s.strip("-"))  # 输出: "Hello, World!"
```

在这个例子中，我们指定了连字符（`-`）作为需要移除的字符。`strip()` 方法移除了字符串两端的连字符。

##### 移除多个不同字符

```python
s = "----Hello, World!---"
print(s.strip("-"))  # 输出: "Hello, World!"
```

即使字符串两端有多个连字符，`strip()` 方法也只会移除两端的连字符，不会影响字符串中间的连字符。

#### 注意事项

- `strip()` 方法只会移除字符串两端的字符，不会影响字符串中间的字符。
- 如果需要移除字符串中间的字符，可以使用 `replace()` 方法或正则表达式。
- `strip()` 方法不会修改原始字符串，而是返回一个新的字符串对象。
- 对于其他类似的操作，还有 `lstrip()`（移除左侧字符）和 `rstrip()`（移除右侧字符）。

`strip()` 函数是Python中处理字符串常用的方法之一，它在文本处理、数据清洗和字符串操作中非常有用。

## 5.17

通过input获得的数据默认为str类型，必要时要对数据类型进行转换

## 5.18

None

## 5.19

### py中KMP算法next数组的构建

<center>关键词：KMP算法<center>

#### 前缀表 减一

```python
def getNext(self, nxt, s):
    nxt[0] = -1
    j = -1
    for i in range(1, len(s)):
        while j >= 0 and s[i] != s[j+1]:
            j = nxt[j]
        if s[i] == s[j+1]:
            j += 1
        nxt[i] = j
    return nxt
```

#### 前缀表 不减一

```python
def getNext(self, nxt, s):
    nxt[0] = 0
    j = 0
    for i in range(1, len(s)):
        while j > 0 and s[i] != s[j]:
            j = nxt[j - 1]
        if s[i] == s[j]:
            j += 1
        nxt[i] = j
    return nxt
```

## 5.20

py中的类如果想要有一个能够在类中使用的数据结构，则需要在构造函数`def __init__(self)`中进行`self.名称=...`样式的声明，表明在此类对象中有数据结构可以调用。在后面的函数中调用这些数据结构也需要进行`self.名称`的样式来进行操作。

## 5.21

### py中的队列

<center>关键词：队列<center>

Python 提供了几种队列的实现，包括标准的队列（FIFO - First In, First Out）和双端队列（deque - 双端队列，允许在两端进行操作）。以下是对这些数据结构的详细介绍：

#### 1. 列表（List）作为队列

虽然列表不是真正的队列数据结构，但可以通过使用列表的 `append()` 方法在一端添加元素，使用 `pop(0)` 方法在另一端移除元素来模拟队列的行为。然而，这种方法在移除元素时效率较低，因为 `pop(0)` 需要移动列表中的所有元素。

```python
from collections import deque

queue = deque()
queue.append('a')  # 入队
queue.append('b')
queue.append('c')

print(queue.popleft())  # 出队，返回 'a'
```

#### 2. `collections.deque` 作为双端队列

Python 的 `collections` 模块提供了 `deque` 类，它是一个双端队列的实现，允许在两端快速添加和删除元素。`deque` 是通过双向链表实现的，因此它提供了 `append()` 和 `appendleft()` 方法来分别在两端添加元素，以及 `pop()` 和 `popleft()` 方法来分别在两端移除元素。

```python
from collections import deque

dq = deque()
dq.append('a')  # 在右侧添加元素
dq.append('b')
dq.appendleft('z')  # 在左侧添加元素

print(dq)  # 输出：deque(['z', 'a', 'b'])

dq.pop()  # 从右侧移除元素，返回 'b'
dq.popleft()  # 从左侧移除元素，返回 'z'

print(dq)  # 输出：deque([])
```

#### 3. `queue.Queue` 作为线程安全的队列

Python 的 `queue` 模块提供了一个线程安全的队列实现，适用于多线程编程。`Queue` 类提供了 `put()` 方法来添加元素，`get()` 方法来移除元素，并且还有 `task_done()` 和 `join()` 方法来支持任务完成的通知。

```python
import queue

q = queue.Queue()
q.put('a')
q.put('b')

print(q.get())  # 从队列中获取元素，返回 'a'
print(q.get())  # 返回 'b'

# 如果队列为空，get() 将阻塞，直到有元素被添加
```

#### 4. 优先队列

虽然标准的 `queue.Queue` 不支持优先级，但是 `heapq` 模块可以用来实现一个优先队列。`heapq` 提供了一个列表的堆队列算法实现，允许你维护一个列表，使得列表的第一个元素总是最小的（或最大的，取决于你的实现）。

```python
import heapq

pq = []
heapq.heappush(pq, (1, 'low priority'))
heapq.heappush(pq, (3, 'high priority'))

print(heapq.heappop(pq))  # 返回最小元素的元组，(1, 'low priority')
```

在这个例子中，我们使用元组 `(优先级, 值)` 来存储元素，`heapq` 会根据元组的第一个元素（即优先级）来排序。

#### 总结

- 使用列表作为队列时，需要注意性能问题，尤其是在频繁地从列表头部移除元素时。
- `collections.deque` 是实现队列和双端队列的理想选择，因为它提供了高效的两端操作。
- `queue.Queue` 是线程安全的队列实现，适用于多线程环境。
- `heapq` 可以用来实现优先队列，但需要手动管理优先级。

每种队列实现都有其适用场景，你可以根据你的具体需求来选择最合适的一种。

## 5.22

None

## 5.23

list类型数据也有pop操作，弹出最后一个元素。

## 5.24

### 操作符从字符串到运算符

<center>关键词：类型转换<center>

可以构建一个映射表

```python
op_to_binary_fn = {
    "+": add,
    "-": sub,
    "*": mul,
    "/": lambda x, y: int(x / y),   # 需要注意 python 中负数除法的表现与题目不一致
}
```

后面就可以通过调用映射表来实现运算操作，如：`op_to_binary_fn[tokens[10]](tmp1,tmp2)`假设`tokens[10]="-"`，则等价于`sub(tmp1,tmp2)=tmp1-tmp2`

### 使用eval函数进行逆波兰运算

<center>关键词：eval函数<center>

在Python中，`eval` 函数用于执行一个字符串表达式，并返回表达式的值。这个函数可以接受一个字符串参数，该字符串包含了有效的Python表达式，并且可以执行它。

在你提供的代码片段中，`eval` 被用于计算两个操作数的算术运算。让我们来详细解释第十行代码：

```python
stack.append(
    int(eval(f'{second_num} {item} {first_num}'))   # 第一个出来的在运算符后面
)
```

这行代码位于一个逆波兰表达式（Reverse Polish Notation, RPN）求值函数中。逆波兰表达式是一种不需要括号来标识操作符优先级的算术表达式表示方法。在逆波兰表达式中，操作符位于它们的两个操作数之后。

在这个特定的代码段中，`second_num` 和 `first_num` 是从栈中弹出的两个操作数，`item` 是一个操作符（"+", "-", "*", "/" 中的一个）。`eval` 函数被用来计算这两个操作数和操作符组成的表达式的值。

- `f'{second_num} {item} {first_num}'`：这是一个格式化字符串（也称为 f-string），它将 `second_num`、`item` 和 `first_num` 插入到字符串中，形成一个新的字符串，这个字符串代表了一个有效的Python表达式。例如，如果 `second_num` 是 `"3"`，`item` 是 `"+"`，`first_num` 是 `"5"`，那么这个字符串将是 `"3 + 5"`。
- `eval(...)`：这个函数执行上述创建的字符串表达式，并返回计算结果。
- `int(...)`：由于 `eval` 返回的结果可能是浮点数（特别是当进行除法操作时），而题目要求返回一个整数结果，因此使用 `int()` 函数将 `eval` 的结果转换为整数。

因此，这行代码的作用是：从栈中弹出两个操作数和一个操作符，使用 `eval` 计算它们的运算结果，并将这个结果转换为整数后压入栈中。

**注意**：在实际应用中，使用 `eval` 可以带来安全风险，因为它会执行字符串中的任何代码。因此，如果输入不可信，应避免使用 `eval` 或采取适当的安全措施。在逆波兰表达式求值的问题中，可以考虑使用更安全的方法来避免使用 `eval`。

## 5.25

### py 获取数组中最大值和索引

<center>关键词：数组最值索引<center>

在 Python 中，获取列表中的最大值及其对应索引可以通过几种方式实现。以下是一些常见的方法：

#### 方法 1: 使用内置函数 `max()` 和 `index()`

```python
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
max_value = max(my_list)  # 获取最大值
max_index = my_list.index(max_value)  # 获取最大值的索引
print(f"最大值: {max_value}, 索引: {max_index}")
```

#### 方法 2: 使用循环遍历

```python
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
max_value = my_list[0]
max_index = 0

for i, value in enumerate(my_list):
    if value > max_value:
        max_value = value
        max_index = i

print(f"最大值: {max_value}, 索引: {max_index}")
```

#### 方法 3: 使用 `max()` 函数和 `enumerate()`

```python
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
max_item = max(enumerate(my_list), key=lambda item: item[1])
max_value, max_index = max_item
print(f"最大值: {max_value}, 索引: {max_index}")
```

#### 方法 4: 使用 `heapq.nlargest()`

如果你需要找到最大的 N 个元素及其索引，可以使用 `heapq` 模块中的 `nlargest` 函数。

```python
import heapq

my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
largest_items = heapq.nlargest(1, enumerate(my_list), key=lambda item: item[1])
max_value, max_index = largest_items[0]
print(f"最大值: {max_value}, 索引: {max_index}")
```

以上方法中，方法 1 和方法 2 是最直接的。方法 3 提供了一种更 Pythonic 的方式，而方法 4 适用于需要找到多个最大值的情况。

选择哪种方法取决于你的具体需求，例如是否需要找到多个最大值，以及对性能的考虑。

### py 中的双端队列

<center>关键词：双端队列<center>

<center>关键词：deque<center>

在 Python 中，双端队列（deque，全称为 "double-ended queue"）是 `collections` 模块提供的一种数据结构，它支持在两端进行快速的添加和删除操作。`deque` 是基于双向链表实现的，这使得它在队列的两端进行操作时具有很高的效率。

以下是如何在 Python 中使用双端队列的一些基本操作：

#### 导入模块

```python
from collections import deque
```

#### 创建双端队列

```python
d = deque()
```

#### 添加元素

- 在前端添加：

  ```python
  d.appendleft('a')  # 在双端队列前端添加元素'a'
  ```

- 在后端添加：

  ```python
  d.append('b')  # 在双端队列后端添加元素'b'
  ```

#### 删除元素

- 从前端删除：

  ```python
  d.popleft()  # 删除双端队列前端的元素
  ```

- 从后端删除：

  ```python
  d.pop()  # 删除双端队列后端的元素
  ```

#### 访问元素

- 访问前端元素：

  ```python
  front_element = d[0]  # 获取前端元素的值
  ```

- 访问后端元素：

  ```python
  back_element = d[-1]  # 获取后端元素的值
  ```

#### 大小和容量

- 获取双端队列的大小：

  ```python
  size = len(d)  # 返回双端队列中的元素数量
  ```

- 检查双端队列是否为空：

  ```python
  is_empty = not d  # 如果双端队列为空，则返回True
  ```

#### 遍历双端队列

```python
for element in d:
    print(element)
```

#### 例子

```python
from collections import deque

# 创建并初始化双端队列
d = deque(['a', 'b', 'c'])

# 在前端添加元素
d.appendleft('x')

# 在后端添加元素
d.append('d')

# 访问前端和后端元素
print("Front element:", d[0])
print("Back element:", d[-1])

# 删除前端和后端元素
d.popleft()
d.pop()

# 遍历双端队列
print("Deque elements:")
for element in d:
    print(element)

# 输出双端队列的大小
print("Size of deque:", len(d))
```

输出将是：

```
Front element: x
Back element: d
Deque elements:
x
b
c
d
Size of deque: 4
```

双端队列在 Python 中非常有用，特别是在需要快速从两端添加或删除元素的场景中。此外，`deque` 还提供了线程安全的选项，可以通过设置 `deque` 的 `maxlen` 属性来创建一个线程安全的队列。

### py中的堆

jz

<center>关键词：堆排序<center>

在Python中，堆（Heap）是一种特殊的树状数据结构，通常用于实现优先队列。Python标准库中的`heapq`模块提供了堆队列算法的实现，它允许你以堆的形式维护一组元素，并执行高效的堆操作。

以下是使用`heapq`模块的一些基本操作：

#### 导入模块

```python
import heapq
```

#### 创建堆

在Python中，堆通常用一个列表来表示。你可以使用`heapq`模块的`heapify()`函数将一个列表转换成堆。

```python
# 创建一个列表并将其转换成堆
h = [1, 3, 5, 7]
heapq.heapify(h)
counter = {1:3,2:2,3:1}
p=[]
```

#### 添加元素到堆

使用`heappush(heap,item)`函数将一个新元素添加到堆中。

当添加的元素是一个键值对时，排序依据为最前面的数据

```python
heapq.heappush(h, 2)  # 堆现在是 [1, 3, 5, 7, 2]
heaq.heappush(q,(3,1))
#元素为1，出现频率为3，堆排序的排序依据是频率3
```

#### 弹出堆顶元素

使用`heappop(heap)`函数从堆中弹出最小的元素（根节点）。

```python
 smallest = heapq.heappop(h)  # 返回 1，堆现在是 [2, 3, 5, 7]
```

#### 添加一个元素到堆并返回堆顶元素

`heappushpop(heap,item)`原子性地添加一个元素到堆中并返回堆中的最小元素。如果堆为空，则返回添加的元素。

```python
h = [1]
item = 5
heapq.heappushpop(h,item)
#返回1，堆现在是[5]
```

#### `heapreplace(heap, item)`

类似于 `heappop()` 后再 `heappush()`，但这个过程是原子的，即它确保堆在操作期间保持不变。

```python
h = [1, 3, 5]
new_item = 4
heapq.heapreplace(h, new_item)  # 返回1，堆现在是[3, 5, 4]
```

#### 查看堆顶元素

虽然`heapq`不提供直接访问堆顶元素的函数，但你可以通过索引来访问。

```python
top_element = h[0]  # 返回最小的元素，即堆顶元素
```

#### 返回最大n个元素

`nlargest(n, iterable[, key])`返回可迭代对象中最大的 `n` 个元素的列表（元素是有序的，从最大到最小）。

```python
data = [1, 3, 5, 7, 9, 2, 4, 6, 8]
result = heapq.nlargest(3, data)  # 返回最大的3个元素：[9, 8, 7]
```

#### 返回最小的n个元素

`nsmallest(n, iterable[, key])`返回可迭代对象中最小的 `n` 个元素的列表（元素是有序的，从小到大）。

```python
data = [1, 3, 5, 7, 9, 2, 4, 6, 8]
result = heapq.nsmallest(3, data)  # 返回最小的3个元素：[1, 2, 3]
```

#### 合并堆

`merge(*iterables)`合并多个可迭代对象的元素。类似于 `functools.reduce` 中的 `functools.reduce(lambda x, y: x+y, iterables)`，但比 `reduce` 更高效。

```python
iter1 = [1, 3, 5, 7]
iter2 = [2, 4, 6, 8]
merged = heapq.merge(iter1, iter2) 
# 返回合并排序后的迭代器：2, 1, 4, 3, 6, 5, 8, 7
```



#### 检查堆是否为空

检查列表是否为空，因为`heapq`本身不维护任何状态信息。

```py
is_empty = not h  # 如果堆为空，则返回True
```

检查列表是否为空，因为`heapq`本身不维护任何状态信息。

```python
is_empty = not h  # 如果堆为空，则返回True
```

#### 获取堆的大小

使用`len()`函数获取堆中的元素数量。

```python
heap_size = len(h)
```

#### 例子

```python
import heapq

# 初始化一个空堆
h = []

# 添加一些元素
heapq.heappush(h, 10)
heapq.heappush(h, 20)
heapq.heappush(h, 15)

# 弹出元素
while h:
    print(heapq.heappop(h))  # 输出：10, 15, 20
```

#### 自定义比较函数

默认情况下，`heapq`模块实现一个最小堆。如果你需要最大堆的行为，可以通过在添加元素之前对它们应用一个转换函数。

```python
# 创建一个最大堆
max_heap = []
for num in [1, 3, 5, 7]:
    heapq.heappush(max_heap, -num)  # 通过取负号来模拟最大堆

# 弹出元素
while max_heap:
    print(-heapq.heappop(max_heap))  # 输出：7, 5, 3, 1
```

`heapq`模块是实现优先队列和执行各种堆相关算法（如Dijkstra算法）的有用工具。由于Python的`heapq`实现是最小堆，因此如果需要最大堆的行为，你需要适当地调整元素的值。

## 5.26

### py寻找前n个最值

<center>关键词：前n个最值<center>

<center>关键词：统计<center>

#### 字典类型数据

调用函数`most_common(n)`即可返回字典数据中value值最大的前几个可迭代对象

#### 堆类型数据

`nlargest(n, iterable[, key])`返回可迭代对象中最大的 `n` 个元素的列表（元素是有序的，从最大到最小）。

`nsmallest(n, iterable[, key])`返回可迭代对象中最小的 `n` 个元素的列表（元素是有序的，从小到大）。

堆排序

## 5.27

### py中的二叉树

#### 二叉树的定义

```python
class TreeNode:
    def __init__(self,val,left = None, right = None):
        self.val = val
        self.left = left
        self.right = right
```

#### 二叉树的递归遍历

##### 先序遍历

```python
# 前序遍历-递归-LC144_二叉树的前序遍历
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        
        def dfs(node):
            if node is None:
                return
            
            res.append(node.val)
            dfs(node.left)
            dfs(node.right)
        
        return res
```

##### 中序遍历

```python
xxxxxxxxxx1 1pythonclass Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        
        def dfs(node):
            if node is None:
                return
            
            dfs(node.left)
            res.append(node.val)
            dfs(node.right)
        
        return res
```

```python
class Solution:
    @staticmethod
    def traversal(root,result):
        if root is None:    return
        Solution.traversal(root.left,result)
        result.append(root.val)
        Solution.traversal(root.right,result)

    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        result = list()    
        Solution.traversal(root,result);
        return result
```

##### 后序遍历

```python
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        
        def dfs(node):
            if node is None:
                return
            
            dfs(node.left)
            dfs(node.right)
            res.append(node.val)
        
        return res
```

#### 二叉树的迭代遍历

##### 先序遍历

```python
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        # 根结点为空则返回空列表
        if not root:
            return []
        stack = [root]
        result = []
        while stack:
            node = stack.pop()
            # 中结点先处理
            result.append(node.val)
            # 右孩子先入栈
            if node.right:
                stack.append(node.right)
            # 左孩子后入栈
            if node.left:
                stack.append(node.left)
        return result
```



##### 中序遍历

```python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        stack = []  # 不能提前将root结点加入stack中
        result = []
        cur = root
        while cur or stack:
            # 先迭代访问最底层的左子树结点
            if cur:     
                stack.append(cur)
                cur = cur.left		
            # 到达最左结点后处理栈顶结点    
            else:		
                cur = stack.pop()
                result.append(cur.val)
                # 取栈顶元素右结点
                cur = cur.right	
        return result
```



##### 后序遍历

```python
class Solution:
   def postorderTraversal(self, root: TreeNode) -> List[int]:
       if not root:
           return []
       stack = [root]
       result = []
       while stack:
           node = stack.pop()
           # 中结点先处理
           result.append(node.val)
           # 左孩子先入栈
           if node.left:
               stack.append(node.left)
           # 右孩子后入栈
           if node.right:
               stack.append(node.right)
       # 将最终的数组翻转
       return result[::-1]
```

```python
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return list()
        
        res = list()
        stack = list()
        prev = None

        while root or stack:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            if not root.right or root.right == prev:
                res.append(root.val)
                prev = root
                root = None
            else:
                stack.append(root)
                root = root.right
        
        return res
```

#### Morris遍历

##### 先序遍历

```python
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        res = list()
        if not root:
            return res
        
        p1 = root
        while p1:
            p2 = p1.left
            if p2:
                while p2.right and p2.right != p1:
                    p2 = p2.right
                if not p2.right:
                    res.append(p1.val)
                    p2.right = p1
                    p1 = p1.left
                    continue
                else:
                    p2.right = None
            else:
                res.append(p1.val)
            p1 = p1.right
        
        return res
```

##### 中序遍历

```python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        # cur = pre = TreeNode(None)
        cur = root

        while cur:
            if not cur.left:
                res.append(cur.val)
                # print(cur.val)
                cur = cur.right
            else:
                pre = cur.left
                while pre.right and pre.right != cur:
                    pre = pre.right
                if not pre.right:
                    # print(cur.val) 这里是前序遍历的代码，前序与中序的唯一差别，只是输出顺序不同
                    pre.right = cur
                    cur = cur.left
                else:
                    pre.right = None
                    res.append(cur.val)
                    # print(cur.val)
                    cur = cur.right
        return res
```

##### 后序遍历

```python
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        def addPath(node: TreeNode):
            count = 0
            while node:
                count += 1
                res.append(node.val)
                node = node.right
            i, j = len(res) - count, len(res) - 1
            while i < j:
                res[i], res[j] = res[j], res[i]
                i += 1
                j -= 1
        
        if not root:
            return list()
        
        res = list()
        p1 = root

        while p1:
            p2 = p1.left
            if p2:
                while p2.right and p2.right != p1:
                    p2 = p2.right
                if not p2.right:
                    p2.right = p1
                    p1 = p1.left
                    continue
                else:
                    p2.right = None
                    addPath(p1.left)
            p1 = p1.right
        
        addPath(root)
        return res
```

#### 标记法迭代遍历

```python
# 前、中、后、层序通用模板，只需改变进栈顺序或即可实现前后中序遍历，
# 而层序遍历则使用队列先进先出。0表示当前未访问，1表示已访问。
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        stack = [(0, root)]
        while stack:
            flag, cur = stack.pop()
            if not cur: continue
            if flag == 0:
                # 前序，标记法
                stack.append((0, cur.right))
                stack.append((0, cur.left))
                stack.append((1, cur))
                
                # # 后序，标记法
                # stack.append((1, cur))
                # stack.append((0, cur.right))
                # stack.append((0, cur.left))
                
                # # 中序，标记法
                # stack.append((0, cur.right))
                # stack.append((1, cur))
                # stack.append((0, cur.left))  
            else:
                res.append(cur.val)  
        return res
```

由此可见list类型数据的兼容性有多强大，内部的元素甚至不需要同种类型，想要插入什么元素都可以。把上文append和初试创建的小括号换成中括号也一样能正常运行。

## 5.30

### py中的extend函数

<center>关键词：extend函数<center>

在Python中，`extend` 是一个用于列表（list）的方法，它用于在列表的末尾一次性追加另一个迭代器（如列表、元组、集合或任何支持迭代的对象）。这个方法会修改原来的列表，而不是创建一个新的列表。

下面是 `extend` 方法的一些使用示例：

#### 基本用法

```python
# 创建两个列表
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# 使用 extend 将 list2 添加到 list1 的末尾
list1.extend(list2)

# 现在 list1 变成了 [1, 2, 3, 4, 5, 6]
print(list1)
```

#### 与 `+` 操作符的区别

使用 `extend` 方法与使用 `+` 操作符连接两个列表不同。`extend` 会直接修改原来的列表，而 `+` 操作符会创建一个新的列表。

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# 使用 + 操作符连接两个列表
new_list = list1 + list2

# list1 保持不变，仍然是 [1, 2, 3]
# new_list 是连接后的新列表，[1, 2, 3, 4, 5, 6]
print(list1)  # 输出: [1, 2, 3]
print(new_list)  # 输出: [1, 2, 3, 4, 5, 6]
```

#### 扩展其他可迭代对象

`extend` 不仅限于列表，它可以接受任何可迭代对象作为参数。

```python
list1 = [1, 2, 3]
tuple1 = (4, 5)
set1 = {6, 7}

# 扩展元组和集合
list1.extend(tuple1)
list1.extend(set1)

# 现在 list1 变成了 [1, 2, 3, 4, 5, 6, 7]
print(list1)
```

#### 注意事项

- `extend` 会修改调用它的列表，它不会返回新的列表。
- 如果传给 `extend` 的迭代器是空的，原列表不会发生变化。
- 如果你尝试扩展一个不可迭代的对象，Python 将抛出 `TypeError`。

`extend` 是处理列表合并和添加元素时非常有用的工具，它提供了一种高效且直观的方式来增加列表的内容。

## 6.1

### pairwise函数

<center>关键词：pairwise函数<center>

#### [itertools](https://so.csdn.net/so/search?q=itertools&spm=1001.2101.3001.7020).pairwise()

首先，这个函数是Python 3.10 新特性。
它表示的是一个迭代器（有点废话，itertools里面都是各种迭代器），他的含义是，从对象中获取连续的**重叠对**。

比如说：s= ‘abcde’，itertools.pairwise(s)的输出应该为，ab, bc, cd, de;
如果s中的个数小于2，输出为空。

示例程序：

```python
from itertools import pairwise
a = pairwise('12345') 
# 输出的a应为是 12 23 34 45

b = pairwise([1])
# b为空
```

#### 替换itertools.pairwise()函数

如上所述，这个函数在python3.10后才有，之前的版本中并不能使用。
那么如果要在程序中实现这个功能，其实也很简单，一次for循环即可。

```python
s = '12345'
for i in range(1,len(s)):
	k1, k2 = s[i-1], s[i] # k1,k2输出应该为1,2;2,3...
```

与迭代器pairwise相比，这个的麻烦地方在于，不能使用迭代器对`重叠对`进行比较，程序效率较慢一点。

实际上也有一些其他的pairwise函数的实例，比如：[python实现pariwise](http://t.zoukankan.com/kuzaman-p-7202146.html)。该链接中有完整的python程序。

### nonlocal关键字

<center>关键词：nonlocal<center>
<center>关键词：嵌套函数调用变量<center>

在Python中，`nonlocal` 关键字用于在嵌套的函数中修改外层（非全局）作用域中的变量。当在一个函数内部定义了一个变量，该变量与嵌套函数外部的变量同名时，使用 `nonlocal` 可以指明内部函数中的变量应该绑定到外部（非全局）作用域中的变量，而不是在内部函数中创建一个新的局部变量。

#### 使用场景

`nonlocal` 主要用于闭包（closures），即当一个嵌套的函数在其定义中引用了外部函数的变量时。

#### 示例

以下是一个使用 `nonlocal` 的示例：

```python
def outer():
    x = 0  # 这是外部函数的局部变量

    def inner():
        nonlocal x  # 指明 x 绑定到外部函数的局部变量
        x = x + 1  # 修改外部函数中的局部变量
        print("Inner:", x)

    inner()
    print("Outer:", x)

outer()
```

输出将是：

```
Inner: 1
Outer: 1
```

在这个示例中，`inner` 函数中的 `nonlocal x` 语句告诉Python解释器，`x` 应该绑定到 `outer` 函数中的局部变量，而不是在 `inner` 函数中创建一个新的局部变量。

#### 规则和限制

- `nonlocal` 只能用于修改嵌套作用域中的变量，不能用于全局变量。
- 如果在嵌套函数中尝试修改一个没有在外部函数中声明的变量，Python会抛出一个 `UnboundLocalError`。
- `nonlocal` 声明必须在嵌套函数中所有使用该变量之前出现。

#### 与 `global` 的比较

- `global` 关键字用于在函数内部声明一个全局变量，即它属于全局作用域。
- `nonlocal` 关键字用于在**嵌套函数**中声明一个变量，该变量属于最近的非全局（通常是外层函数的局部）作用域。

#### 另一个示例

考虑一个计数器的例子，其中外部函数希望在每次调用嵌套函数时递增计数器：

```python
def create_counter():
    count = 0

    def counter():
        nonlocal count
        count += 1
        return count

    return counter

my_counter = create_counter()
print(my_counter())  # 输出: 1
print(my_counter())  # 输出: 2
```

在这个例子中，每次调用 `my_counter()` 时，它都会递增 `create_counter` 函数中的 `count` 变量。

`nonlocal` 是Python作用域规则的一个重要组成部分，它提供了在嵌套函数中修改外部变量的能力。

## 6.2（补）

### python中的位运算

<center>关键词：位运算<center>

在Python中，位运算与在其他编程语言中类似，可以应用于整数类型。Python支持以下几种位运算符：

#### 1. 位非 (`~`)

位非运算符对操作数的每一位进行取反操作。

```python
a = 0b0011  # 二进制表示为 0011
b = ~a      # b 的二进制表示为 1100 (补码表示)
```

#### 2. 位与 (`&`)

位与运算符对两个操作数的对应位进行逻辑与操作。

```python
a = 0b0011
b = 0b0101
c = a & b    # c 的二进制表示为 0001
```

#### 3. 位或 (`|`)

位或运算符对两个操作数的对应位进行逻辑或操作。

```python
a = 0b0011
b = 0b0101
c = a | b    # c 的二进制表示为 0111
```

#### 4. 位异或 (`^`)

位异或运算符对两个操作数的对应位进行逻辑异或操作。

```python
a = 0b0011
b = 0b0101
c = a ^ b    # c 的二进制表示为 0110
```

#### 5. 位左移 (`<<`)

位左移运算符将操作数的所有位向左移动指定的位数，左边空出的位填充0。

```python
a = 0b0011
b = a << 2   # b 的二进制表示为 110000
```

#### 6. 位右移 (`>>`)

位右移运算符将操作数的所有位向右移动指定的位数，右边空出的位通常按符号位填充。

```python
a = 0b0011
b = a >> 1   # b 的二进制表示为 000011
```

#### 示例代码

```python
# 位非
a = 13      # 二进制: 1101
b = ~a      # 二进制: 10010 (-14 的补码)
print(f"~{a:b} = {b:b}")

# 位与
x = 0b1010  # 二进制: 1010
y = 0b1100  # 二进制: 1100
z = x & y    # 二进制: 1000
print(f"{z:b} = {x:b} & {y:b}")

# 位或
x = 0b1010
y = 0b1100
z = x | y    # 二进制: 1110
print(f"{z:b} = {x:b} | {y:b}")

# 位异或
x = 0b1010
y = 0b1100
z = x ^ y    # 二进制: 0110
print(f"{z:b} = {x:b} ^ {y:b}")

# 位左移
x = 0b1010
y = x << 2   # 二进制: 101000
print(f"{y:b} = {x:b} << 2")

# 位右移
x = 0b1010
y = x >> 2   # 二进制: 0010
print(f"{y:b} = {x:b} >> 2")
```

输出将是：

```
~1101 = 10010
1000 = 1010 & 1100
1110 = 1010 | 1100
0110 = 1010 ^ 1100
101000 = 1010 << 2
0010 = 1010 >> 2
```

Python中的位运算符可以用于执行位级操作，这在某些底层编程任务中非常有用，例如处理二进制数据或实现某些算法。然而，由于Python的动态类型特性，位运算符只能用于整数类型。

## 6.7

### 深拷贝

<center>关键词：深拷贝<center>

在Python中，深拷贝（Deep Copy）意味着创建一个对象的全新副本，这个副本与原始对象完全独立，包括对象所引用的所有子对象。如果对象中含有其他对象的引用，深拷贝会递归地复制这些引用的对象，确保副本对象与原始对象在内存中是两个完全不同的实体。

#### 如何实现深拷贝

在Python中，实现深拷贝的最常用方法是使用`copy`模块中的`deepcopy()`函数。

```python
import copy

original_list = [[1, 2, 3], [4, 5, 6]]
copied_list = copy.deepcopy(original_list)
```

在这个例子中，`original_list` 是一个包含列表的列表。使用`deepcopy()`函数后，`copied_list` 将成为一个全新的列表，它包含与原始列表相同的元素，但是它们在内存中是独立的。对`copied_list`的修改不会影响到`original_list`。

#### 深拷贝的应用场景

- **独立性**：当你需要修改对象而又不想影响原始对象时，使用深拷贝可以保证两者的独立性。
- **复杂对象**：对于包含复杂嵌套结构的对象，深拷贝可以确保所有嵌套的对象都被复制。
- **避免副作用**：在函数或方法中使用深拷贝可以避免对调用者传递的对象产生副作用。

#### 注意事项

- **性能**：深拷贝可能会消耗更多的内存和时间，特别是当对象很大或包含大量嵌套对象时。
- **递归问题**：深拷贝过程中可能会遇到递归对象（即对象直接或间接引用自己），这可能导致无限递归。
- **特殊对象**：有些对象可能不支持深拷贝，比如文件句柄或数据库连接。对于这些特殊对象，`deepcopy()` 会抛出异常。

深拷贝在Python中是通过`copy`模块的`deepcopy()`函数来实现的。它递归地复制对象及其所有子对象，创建一个完全独立的副本。这在需要独立操作对象而又不影响原始对象时非常有用。然而，深拷贝可能会因为复制大量数据而影响性能，并且在处理特殊对象或递归对象时需要特别注意。

## 6.10

### py中的复制赋值和引用赋值

<center>关键词：赋值区别<center>

在Python中，赋值操作通常涉及两个概念：复制赋值（Copy Assignment）和引用赋值（Reference Assignment）。然而，Python的动态类型特性和内存管理机制（使用引用计数）使得这两种赋值操作的表现与静态类型语言（如C++）有所不同。

#### 复制赋值（Copy Assignment）

在Python中，复制赋值通常意味着创建一个对象的新的独立副本。当你将一个对象赋值给一个新的变量时，新变量将拥有原始对象的一个副本。

对于不可变类型（如整数、字符串、元组），复制赋值是直接的值复制。

```python
a = 10  # a 是一个整数对象的引用
b = a   # b 复制了 a 的值，现在 b 也有一个整数对象的引用
```

对于可变类型（如列表、字典、集合），复制赋值会创建一个对象的浅拷贝（Shallow Copy），这意味着新对象将包含对原始对象中元素的引用。

```python
list1 = [1, 2, 3]
list2 = list1.copy()  # list2 是 list1 的浅拷贝，包含相同的元素引用
list2.append(4)
print(list1)  # 输出: [1, 2, 3]
print(list2)  # 输出: [1, 2, 3, 4]
```

#### 引用赋值（Reference Assignment）

在Python中，引用赋值意味着两个变量指向内存中的同一个对象。当你将一个变量直接赋值给另一个变量时，两者都引用同一个对象。

```python
a = [1, 2, 3]
b = a  # b 是 a 的引用赋值，两者都指向同一个列表对象
b.append(4)
print(a)  # 输出: [1, 2, 3, 4]
```

#### 深拷贝（Deep Copy）

如果你需要创建一个对象的完全独立的副本，包括所有嵌套对象，你需要使用深拷贝（Deep Copy）。Python的`copy`模块提供了`deepcopy()`函数来实现深拷贝。

```python
import copy

a = [[1, 2], [3, 4]]
b = copy.deepcopy(a)  # b 是 a 的深拷贝
b[0][0] = 99
print(a)  # 输出: [[1, 2], [3, 4]]
print(b)  # 输出: [[99, 2], [3, 4]]
```

#### 注意事项

- 在Python中，赋值操作默认创建对象的引用，而不是对象的副本。
- 对于不可变类型，赋值操作实质上是复制赋值。
- 对于可变类型，默认的赋值操作是引用赋值，除非你使用深拷贝。
- 深拷贝可以避免原始对象和副本对象之间的相互影响。

理解Python中的赋值操作对于编写清晰、可维护的代码非常重要，尤其是在处理可变数据结构时。

### 详细介绍sPath = '->'.join(map(str, path))

<center>关键词：join与map<center>

代码行 `sPath = '->'.join(map(str, path))` 在构建二叉树路径字符串中扮演着重要角色。让我们详细了解这行代码的作用和组成部分：

#### `map(str, path)`

- `map()` 函数在Python中用于将一个函数应用于可迭代对象的每个元素，并收集结果。
- `str` 是将要应用于 `path` 中每个元素的函数，即将每个元素转换为字符串类型。
- `path` 是一个列表，包含了从根节点到当前叶子节点的节点值（整数）。
- `map(str, path)` 将 `str` 函数应用于 `path` 中的每个整数元素，将它们转换为字符串。结果是一个迭代器，其中的元素是 `path` 列表中整数的字符串表示。

#### `->'.join(...)`

- `join()` 是字符串对象的方法，用于将序列中的元素连接（concatenate）成一个单一的字符串。
- `'->'` 是 `join()` 方法中的分隔符，意味着序列中的元素将通过 `'->'` 字符串连接起来。
- `join()` 方法接受一个可迭代对象作为参数，通常是一个列表或元组。

#### 综合 `map` 和 `join`

将 `map(str, path)` 和 `'->'.join(...)` 结合起来：

- 首先，`map(str, path)` 将 `path` 中的每个整数值转换为字符串。
- 然后，`'->'.join(map(str, path))` 将这些字符串元素通过 `'->'` 连接起来，形成一个表示完整路径的单一字符串。

#### 示例

假设 `path` 列表包含以下整数值，表示从根节点到叶子节点的路径：

```python
path = [1, 2, 5]
```

执行 `map(str, path)` 后，我们得到：

```python
['1', '2', '5']
```

然后，执行 `'->'.join(...)` 将这些字符串元素连接起来：

```python
'1->2->5'
```

最终，`sPath` 变量将包含字符串 `'1->2->5'`，这是一个表示从根到叶子节点的路径的字符串。

#### 为什么这样做？

- 这种方法将整数列表转换为一个易于阅读的字符串表示形式，其中每个节点用 `'->'` 分隔，清晰地展示了二叉树中节点的访问顺序。
- 它使得最终的路径结果对于人类阅读者来说是友好的，可以直观地看出路径是如何在树中前进的。

这就是 `sPath = '->'.join(map(str, path))` 这行代码的详细介绍。

### py中的join函数

<center>关键词：join函数<center>

在Python中，`join()` 是字符串对象的一个方法，用于将序列中的元素连接（concatenate）成一个单一的字符串。这个方法通常用于将字符串列表或元组中的元素合并成一个完整的字符串，元素之间可以指定一个分隔符。

#### 基本语法：

```python
str.join(iterable)
```

- `str` 是要连接的元素之间的分隔符字符串。
- `iterable` 是一个可迭代对象，如列表、元组、集合等，其元素将被连接。

#### 参数：

- **iterable**：一个可迭代对象，其元素将按照迭代顺序被 `str` 分隔符连接起来。

#### 返回值：

- 返回一个新的字符串，由 `iterable` 中的元素使用 `str` 作为分隔符连接而成。

#### 示例：

##### 连接字符串列表：

```python
words = ['Hello', 'World', 'Python', 'is', 'awesome']
sentence = ' '.join(words)
print(sentence)  # 输出: "Hello World Python is awesome"
```

在这个例子中，空格 `' '` 用作分隔符，将列表 `words` 中的字符串元素连接成一个完整的句子。

##### 使用特定分隔符：

```python
items = ['apple', 'banana', 'cherry']
result = ', '.join(items)
print(result)  # 输出: "apple, banana, cherry"
```

在这个例子中，逗号加空格 `', '` 作为分隔符，将 `items` 列表中的字符串元素连接成一个以逗号分隔的列表。

##### 连接数字：

```python
numbers = [1, 2, 3, 4, 5]
str_numbers = ''.join(map(str, numbers))
print(str_numbers)  # 输出: "12345"
```

在这个例子中，首先使用 `map()` 函数将每个数字转换为字符串，然后使用空字符串 `''` 作为分隔符将它们连接起来。

#### 注意事项：

- `join()` 方法是字符串对象的方法，所以它不能直接用于非字符串类型的可迭代对象。如果尝试连接非字符串元素，需要先将它们转换为字符串。
- 如果 `iterable` 中包含 `None`，`join()` 会引发 `TypeError`，因为 `None` 类型不能被转换为字符串。如果存在 `None`，需要先将其替换或排除。
- `join()` 是一个非常有用的字符串操作，特别是在处理文本文件、生成报告或将数据格式化为特定格式时。

`join()` 方法提供了一种简洁且高效的方式来合并字符串，是Python文本处理中不可或缺的工具之一。

## 6.19

### py在类中初始化变量

<center>关键词：初始化变量<center>

在Python中，类的变量声明与C++有一些不同。Python是一种动态类型语言，不需要在声明变量时指定类型，而且变量可以在类的任何地方被赋值，而不需要先声明。不过，Python允许你在类中初始化变量，**这在构造函数（`__init__` 方法）中完成。**

以下是如何在Python类中声明和初始化变量的示例，以及如何实现类似于C++中的变量声明和访问：

#### Python类中的变量声明和初始化

```python
class MyClass:
    def __init__(self, value):
        self.my_var = value  # 类变量的初始化

# 创建类的实例并初始化变量
my_instance = MyClass(42)
print(my_instance.my_var)  # 输出: 42
```

#### 类属性与实例属性

- **类属性**：属于类的所有实例共享，可以在类定义的外部或内部声明和访问。

```python
class MyClass:
    class_var = 100  # 类属性

    def __init__(self):
        self.instance_var = 200  # 实例属性

# 访问类属性
print(MyClass.class_var)  # 输出: 100

# 创建实例并访问实例属性
my_instance = MyClass()
print(my_instance.instance_var)  # 输出: 200
```

#### 类变量的动态赋值

在Python中，类变量可以在任何地方被赋值，包括在方法内部。

```python
class MyClass:
    def set_class_var(self, value):
        self.class_var = value  # 动态赋值类变量

    def get_class_var(self):
        return self.class_var

# 创建实例并动态设置类变量
my_instance = MyClass()
my_instance.set_class_var(300)
print(my_instance.get_class_var())  # 输出: 300
```

#### 类的静态方法和类方法

- **静态方法**：使用 `@staticmethod` 装饰器，不需要类或实例的引用。
- **类方法**：使用 `@classmethod` 装饰器，需要类的引用，但不需要实例的引用。

```python
class MyClass:
    @staticmethod
    def static_method():
        print("This is a static method.")

    @classmethod
    def class_method(cls):
        print(f"This is a class method of {cls}")

# 调用静态方法
MyClass.static_method()

# 调用类方法
MyClass.class_method()
```

#### 类的属性访问控制

虽然Python没有像C++那样的访问控制（如 `private` 或 `protected` 关键字），但你可以约定俗成地使用单下划线 `_` 或双下划线 `__` 来表示属性或方法不应该被外部直接访问。

```python
class MyClass:
    def __init__(self):
        self._internal_var = 0  # 约定俗成的“私有”变量

    def _private_method(self):
        pass

# 尝试访问“私有”变量将导致错误
# print(my_instance._internal_var)  # 这将引发 AttributeError
```

在Python中，类的变量声明和使用比C++更为灵活，但也需要程序员自觉遵守一些约定，以保持代码的清晰和可维护性。

## 7.4

### py对字符串的操作

<center>关键词：字符串操作<center>

<center>关键词：string操作<center>

Python中的字符串操作非常丰富，因为字符串在Python中是不可变的（immutable），这意味着一旦创建就不能更改。但即便如此，Python提供了大量的方法来处理字符串。以下是一些常用的字符串操作：

#### 1. 访问字符串中的字符

可以通过索引访问字符串中的每个字符，索引从0开始。

```python
s = "Hello, World!"
print(s[0])  # 输出: H
```

#### 2. 切片操作

切片操作允许你获取字符串的一部分。

```python
print(s[1:5])  # 输出: ello
print(s[-6:-1])  # 输出: World
```

#### 3. 字符串连接

使用`+`操作符或`join()`方法连接字符串。

```python
name = "John"
greeting = "Hello, " + name + "!"
print(greeting)  # 输出: Hello, John!

# 使用 join()
items = ["apple", "banana", "cherry"]
fruits = ", ".join(items)  # 输出: apple, banana, cherry
```

#### 4. 字符串长度

使用`len()`函数获取字符串的长度。

```python
print(len(s))  # 输出: 13
```

#### 5. 大小写转换

使用`upper()`和`lower()`方法转换字符串的大小写。

```python
print(s.upper())  # 输出: HELLO, WORLD!
print(s.lower())  # 输出: hello, world!
```

#### 6. 字符串查找

使用`find()`或`index()`方法查找子字符串的位置。

```python
pos = s.find("World")
print(pos)  # 输出: 7

# 如果子字符串不存在，index() 会抛出 ValueError
# pos = s.index("Python")  # 抛出 ValueError
```

#### 7. 字符串替换

使用`replace()`方法替换字符串中的某些字符或子字符串。

```python
modified = s.replace("World", "Python")
print(modified)  # 输出: Hello, Python!
```

#### 8. 字符串分割

使用`split()`方法按分隔符分割字符串。

```python
parts = s.split(", ")
print(parts)  # 输出: ['Hello', 'World!']
```

#### 9. 字符串格式化

使用`format()`方法或f-string（Python 3.6+）进行字符串格式化。

```python
name = "Alice"
age = 30
print("Name: {}, Age: {}".format(name, age))  # 输出: Name: Alice, Age: 30

# 使用 f-string
print(f"Name: {name}, Age: {age}")  # 输出: Name: Alice, Age: 30
```

#### 10. 字符串去除空白

使用`strip()`, `rstrip()`, `lstrip()`去除字符串两端或一端的空白字符。

```python
s = "  Hello, World!  "
print(s.strip())  # 输出: 'Hello, World!'
print(s.lstrip())  # 输出: 'Hello, World!  '
print(s.rstrip())  # 输出: '  Hello, World!'
```

#### 11. 字符串比较

使用`==`和`!=`操作符比较字符串。

```python
print("Hello" == "hello")  # 输出: False
print("Hello".lower() == "hello")  # 输出: True
```

#### 12. 字符串遍历

使用循环遍历字符串中的每个字符。

```python
for char in s:
    print(char)
```

#### 13. 字符串方法链

可以像链式调用一样，连续调用字符串的方法。

```python
print(s.strip().upper()[:5])  # 输出: 'HELLO'
```

Python的字符串操作非常灵活，由于字符串的不可变性，很多操作会返回新的字符串而不是修改原始字符串。这保证了字符串操作的安全性和可预测性。

## 7.8

### 对list型数据的操作

<center>关键词：list<center>

<center>关键词：对list的操作<center>

Python中的`list`是一种非常灵活的数据结构，支持广泛的操作。以下是一些常用的列表操作：

#### 创建列表

```python
empty_list = []
number_list = [1, 2, 3]
string_list = ["apple", "banana", "cherry"]
```

#### 访问列表元素

```python
first_element = number_list[0]  # 获取第一个元素
last_element = number_list[-1]  # 获取最后一个元素
```

#### 修改列表元素

```python
number_list[1] = 10  # 将第二个元素修改为10
```

#### 列表切片

```python
sub_list = number_list[1:3]  # 获取从第二个到第三个元素的切片
full_slice = number_list[:]  # 获取整个列表的副本
```

#### 添加元素

```python
number_list.append(4)  # 在列表末尾添加一个元素
number_list.insert(1, 9)  # 在指定位置插入一个元素
```

#### 删除元素

```python
del number_list[0]  # 删除指定位置的元素
popped_element = number_list.pop()  # 删除并返回列表的最后一个元素
```

#### 列表遍历

```python
for element in number_list:
    print(element)
```

#### 列表长度

```python
length = len(number_list)
```

#### 列表排序

```python
number_list.sort()  # 原地排序
sorted_list = sorted(number_list)  # 返回一个新的排序列表
```

#### 列表反转

```python
number_list.reverse()  # 原地反转
reversed_list = number_list[::-1]  # 返回一个新的反转列表
```

#### 列表连接

```python
combined_list = number_list + [5, 6, 7]
```

#### 列表复制

```python
list_copy = number_list.copy()  # 返回列表的浅拷贝
```

#### 列表推导式

```python
squared_list = [x**2 for x in number_list]
```

#### 列表成员资格

```python
if 2 in number_list:
    print("2 is in the list")
```

#### 列表统计

```python
count = number_list.count(2)  # 统计元素出现的次数
```

#### 列表去重

```python
unique_list = list(set(number_list))  # 使用集合去除重复元素
```

#### 列表合并与扩展

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list1.extend(list2)  # 将list2的元素添加到list1的末尾
```

#### 列表元素位置

```python
position = number_list.index(2)  # 查找元素的索引位置
```

#### 列表清空

```python
number_list.clear()  # 清空列表中的所有元素
```

#### 列表乘法

```python
repeated_list = number_list * 3  # 将列表重复3次
```

#### 列表与字符串转换

```python
str_list = str(number_list)  # 将列表转换为字符串
list_from_str = list("hello")  # 将字符串转换为字符列表
```

这些操作覆盖了列表的基本使用场景，包括创建、访问、修改、遍历、排序、筛选和转换等。Python的列表是动态类型的，可以容纳不同类型的元素，但通常最佳实践是让列表保持元素类型的一致性。

## 8.2

### py实现list中数字的拼接

<center>关键词：list拼接<center>

<center>关键词：int数字拼接<center>

在Python中，将列表中的数字合并为一个数可以通过多种方法实现。以下是一些常见的方法：

#### 方法1: 使用字符串拼接

```python
s = [1, 2, 3, 4, 5]
number = ''.join(map(str, s))
number = int(number)  # 将合并后的字符串转换为整数
print(number)  # 输出: 12345
```

#### 方法2: 使用`reduce()`函数

```python
from functools import reduce

s = [1, 2, 3, 4, 5]
number = reduce(lambda x, y: str(x) + str(y), s)
number = int(number)  # 将合并后的字符串转换为整数
print(number)  # 输出: 12345
```

#### 方法3: 使用列表推导式和`join()`

```python
s = [1, 2, 3, 4, 5]
number = int(''.join([str(num) for num in s]))
print(number)  # 输出: 12345
```

#### 方法4: 使用循环

```python
s = [1, 2, 3, 4, 5]
number = 0
for num in s:
    number = number * 10 + num
print(number)  # 输出: 12345
```

#### 方法5: 使用`sum()`和列表推导式

这个方法适用于数字列表，其中每个数字的位数相同。

```python
s = [1, 2, 3, 4, 5]
number = sum([num * 10**i for i, num in enumerate(s[::-1])])
print(number)  # 输出: 12345
```

在这个例子中，我们通过计算每个数字向左移动的位数（`10**i`）来实现合并。

#### 方法6: 使用`itertools.chain()`和`int()`转换

如果你想要处理的数字列表很长，这种方法可以避免字符串操作的性能问题。

```python
import itertools

s = [1, 2, 3, 4, 5]
number = int(''.join(map(str, itertools.chain(*s))))
print(number)  # 输出: 12345
```

选择哪种方法取决于你的具体需求，例如列表的长度、数字的大小以及是否需要考虑性能。对于较短的列表，使用字符串拼接或列表推导式通常是简单且直观的方法。对于更长的列表或性能敏感的应用，使用循环或`sum()`方法可能更合适。

## 8.8

### py 中的排列组合函数

<center> 关键词：排列组合 <center>


<center> 关键词：comb 函数 <center>


<center> 关键词：perm 函数 <center>


<center> 关键词：factorial 函数 <center>


在 Python 中，`comb`、`perm` 和 `factorial` 是与组合数学相关的函数，它们分别用于计算组合数、排列数和阶乘。以下是对这些函数的详细介绍：

#### 1. `math.factorial` 函数（阶乘）

`math.factorial` 函数用于计算一个非负整数的阶乘。阶乘表示从 1 到该整数的连乘积。

- **函数原型**：`factorial(x)`
- **参数**：`x` - 一个非负整数。
- **返回值**：返回 `x` 的阶乘。

```python
import math

result = math.factorial(5)  # 计算5的阶乘，结果为120
```

#### 2. `math.comb` 函数（组合数）

在 Python 中，`comb` 函数是 `math` 模块中的一个函数，用于计算组合数，即从 n 个不同元素中取出 k 个元素的组合方式数目（不考虑元素的顺序）。这个函数的全称是 "combinations"，它基于数学中的组合公式：

$ \text{comb}(n, k) = \frac{n!}{k!(n-k)!} $

其中，\( n! \)（n 的阶乘）表示从 1 乘到 n，\( k! \) 表示从 1 乘到 k，\( (n-k)! \) 表示从 1 乘到 \( n-k \)。

##### 函数原型：

```python
math.comb(n, k)
```

- `n`：非负整数，表示总数。
- `k`：不超过 n 的整数，表示选择的数量。

##### 返回值：

- 返回一个整数，表示从 n 个元素中选择 k 个元素的组合数。

##### 使用示例：

```python
import math

# 计算从5个元素中选择2个元素的组合数
combinations = math.comb(5, 2)
print(combinations)  # 输出: 10
```

在这个例子中，`math.comb(5, 2)` 计算的是 $ \frac{5!}{2!(5-2)!} = \frac{5 \times 4}{2 \times 1} = 10 $。

##### 注意事项：

- 如果 `k` 大于 `n`，将抛出 `ValueError` 异常，因为组合数在这种情况下没有意义。
- 如果 `k` 是负数或不是整数，同样会抛出 `ValueError` 异常。
- `math.comb` 函数从 Python 3.8 开始引入，如果你使用的是早期版本的 Python，需要使用其他方法来计算组合数。

##### 替代方法：

在 Python 3.8 之前的版本中，你可以使用 `math.factorial` 函数来手动计算组合数：

```python
import math

def comb(n, k):
    if k < 0 or k > n:
        raise ValueError("k must be between 0 and n")
    return math.factorial(n) // (math.factorial(k) * math.factorial(n - k))

# 使用自定义的 comb 函数
combinations = comb(5, 2)
print(combinations)  # 输出: 10
```

在这个自定义函数中，我们首先检查 `k` 是否在有效范围内，然后使用阶乘公式计算组合数，并使用整除 `//` 来得到整数结果。

`math.comb` 函数是 Python 中处理组合数的直接和高效的方法，尤其适用于需要频繁进行组合数计算的场景。

`math.comb` 函数用于计算从 n 个不同元素中取出 k 个元素的组合数，不考虑元素的顺序。

#### 3. `math.perm` 函数（排列数）

在 Python 中，如果你想要计算排列数，应该使用 `math` 模块中的 `factorial` 函数。排列数是指从 n 个不同元素中取出 k 个元素的所有可能排列的数量，考虑了元素的顺序。排列数的计算公式是：

$ P(n, k) = \frac{n!}{(n-k)!} $

其中，\( n! \)（n 的阶乘）表示从 1 乘到 n，\( (n-k)! \) 表示从 1 乘到 \( n-k \)。

##### 使用 `math.factorial` 计算排列数：

```python
import math

def perm(n, k):
    if k > n:
        return 0  # 如果k大于n，排列数为0
    return math.factorial(n) // math.factorial(n - k)

# 计算从5个元素中选择2个元素的排列数
permutation_count = perm(5, 2)
print(permutation_count)  # 输出: 20
```

在这个例子中，`perm(5, 2)` 计算的是 $\frac{5!}{(5-2)!} = \frac{5 \times 4}{1} = 20 $。

##### 注意事项：

- 如果 `k` 大于 `n`，排列数为 0，因为没有足够的元素进行选择。
- 如果 `k` 是负数或不是整数，将抛出 `ValueError` 异常。
- `math.factorial` 函数返回一个整数，表示给定非负整数的阶乘。

##### 替代方法：

在 Python 3.8 之前，如果你需要计算排列数，可以使用 `math.factorial` 函数，如上所示。从 Python 3.8 开始，`math` 模块提供了 `math.perm` 函数，它直接计算排列数：

```python
import math

# 从Python 3.8开始，直接使用 math.perm 函数
permutation_count = math.perm(5, 2)
print(permutation_count)  # 输出: 20
```

#### 注意事项：

- `math.factorial` 函数从 Python 3.8 开始提供。在早期版本的 Python 中，可以使用 `math.factorial` 函数计算阶乘。
- `math.comb` 和 `math.perm` 函数从 Python 3.8 开始提供。在早期版本的 Python 中，可以通过组合 `math.factorial` 和其他数学运算来手动计算组合数和排列数。
- 如果 `k` 大于 `n`，`math.comb` 函数将返回 0，因为无法从较少的元素中选择更多的元素。
- 如果 `k` 是负数或不是整数，`math.comb` 和 `math.perm` 函数将抛出 `ValueError` 异常。

这些函数在处理组合和排列问题时非常有用，例如在概率论、统计学和算法设计等领域。通过使用这些内置函数，可以简化代码并提高计算效率。

## 8.24

### 装饰器@cache

<center>关键词：@cache<center>

<center>关键词：装饰器<center>

在Python中，`@cache` 是一个装饰器，它是 `functools.lru_cache` 装饰器的别名。`lru_cache` 代表 "Least Recently Used"（最近最少使用），它是一种缓存机制，用于存储函数的调用结果，以便在后续调用时能够快速返回结果，从而避免重复计算。这对于性能优化尤其有用，特别是对于计算成本高昂的函数。

#### 如何使用 `@cache`：

1. **导入装饰器**：首先，你需要从 `functools` 模块导入 `lru_cache`。

   ```python
   from functools import lru_cache
   ```

2. **应用装饰器**：将 `@cache` 装饰器应用于你想要缓存结果的函数。

   ```python
   @lru_cache(maxsize=None)  # maxsize=None 表示缓存大小没有限制
   def your_function(args):
       # 函数体
       return result
   ```

3. **函数调用**：当你调用这个函数时，如果之前已经计算过相同的参数组合，它将返回缓存的结果，而不是重新执行函数体。

#### 示例：

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    if n < 2:
        return n
    return fib(n - 1) + fib(n - 2)

# 调用 fib 函数
print(fib(10))  # 输出: 55
```

在这个例子中，`fib` 函数计算斐波那契数列的第 `n` 项。使用 `@lru_cache` 装饰器可以缓存每一项的计算结果，从而提高计算效率。

#### 注意事项：

- `maxsize` 参数：你可以设置 `maxsize` 为一个正整数，以限制缓存的大小。如果设置为 `None`（默认值），缓存可以无限大，直到内存耗尽。
- 线程安全：`lru_cache` 默认不是线程安全的。如果你需要在多线程环境中使用它，可以设置 `lru_cache` 的 `typed` 参数为 `True`，以使缓存键考虑参数的类型。
- 缓存失效：`lru_cache` 仅缓存调用的结果，不跟踪参数对象的内部变化。如果参数是可变对象，它们的内部状态变化不会影响缓存。

`@cache`（即 `lru_cache`）是一个非常有用的工具，可以显著提高具有重复计算的函数的性能，尤其是在处理递归或动态规划问题时。

## 9.6

### 二分查找

<center>关键词：二分查找<center>

在Python中，并没有内置的二分查找函数，但是你可以轻松地使用`bisect`模块来实现二分查找的功能。`bisect`模块提供了一个用于维护有序列表的函数，同时提供了二分查找的功能。

以下是如何使用`bisect`模块进行二分查找的示例：

#### 1. 使用 `bisect_left` 进行二分查找

`bisect_left` 函数会返回列表中第一个不小于目标值的元素的索引。

```python
import bisect

def binary_search(arr, target):
    # 找到第一个不小于目标值的元素的索引
    index = bisect.bisect_left(arr, target)
    if index != len(arr) and arr[index] == target:
        return index
    return -1

# 示例
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
target = 5
result = binary_search(arr, target)
print("Index of", target, "is", result)
```

#### 2. 使用 `bisect_right` 进行二分查找

`bisect_right` 函数会返回列表中第一个大于目标值的元素的索引。

```python
import bisect

def binary_search(arr, target):
    # 找到第一个大于目标值的元素的索引
    index = bisect.bisect_right(arr, target)
    if index != len(arr) and arr[index - 1] == target:
        return index - 1
    return -1

# 示例
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
target = 5
result = binary_search(arr, target)
print("Index of", target, "is", result)
```

#### 3. 使用 `bisect` 进行二分插入

如果你需要找到元素应该插入的位置以保持列表的有序性，可以使用 `bisect` 函数。

```python
import bisect

def binary_insert(arr, target):
    index = bisect.bisect(arr, target)
    arr.insert(index, target)
    return arr

# 示例
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
target = 5
result = binary_insert(arr, target)
print("Array after insertion:", result)
```

#### 注意事项

1. **列表必须是有序的**：`bisect` 模块的函数都要求列表是有序的。
2. **返回值**：`bisect_left` 和 `bisect_right` 返回的是索引，而不是元素值。如果未找到目标值，`bisect_left` 返回数组长度，`bisect_right` 返回数组长度或最后一个元素的索引。
3. **时间复杂度**：`bisect` 模块的函数时间复杂度为 O(log n)。

`bisect` 模块是Python中处理有序列表的强大工具，它不仅可以用于二分查找，还可以用于维护有序列表的插入和删除操作。

## 9.22

### py实现把列表元素和索引映射到哈希表

<center>关键词：列表的哈希映射<center>

<center>关键词：list的哈希映射<center>

```python
idx = {x: i for i, x in enumerate(nums1)}
```



在Python中，可以使用字典（`dict`）来实现一个哈希表，将列表中的元素及其索引映射到哈希表中。下面是一个简单的示例代码，它将列表中的每个元素及其对应的索引存储到一个字典中：

```python
def map_elements_to_hashtable(lst):
    hashtable = {}
    for index, element in enumerate(lst):
        hashtable[element] = index
    return hashtable

# 示例列表
my_list = ['apple', 'banana', 'cherry', 'date']

# 调用函数并打印结果
hashtable = map_elements_to_hashtable(my_list)
print(hashtable)
```

在这个例子中，`map_elements_to_hashtable` 函数接受一个列表 `lst` 作为参数，然后使用 `enumerate` 函数遍历列表，`enumerate` 会同时返回元素的索引和值。然后，将元素作为键，索引作为值，存储到字典 `hashtable` 中。

请注意，如果列表中有重复的元素，字典中只会保留最后一个元素的索引，因为字典的键是唯一的。

如果你需要保留所有元素及其索引，可以使用列表作为字典的值：

```python
def map_elements_to_hashtable_with_duplicates(lst):
    hashtable = {}
    for index, element in enumerate(lst):
        if element in hashtable:
            hashtable[element].append(index)
        else:
            hashtable[element] = [index]
    return hashtable

# 示例列表
my_list = ['apple', 'banana', 'cherry', 'apple']

# 调用函数并打印结果
hashtable = map_elements_to_hashtable_with_duplicates(my_list)
print(hashtable)
```

在这个修改后的版本中，如果遇到重复的元素，我们会将索引追加到该元素对应的列表中，这样就可以保留所有元素及其索引了。

## 9.30

从py中获取int输入（中间用空格隔开）的做法：

`n, m = map(int, input().split())`

py打印的时候如果使用format，则默认是换行输出的。如果想要打印一个路径中的所有数字并以空格隔开，使用`print(' '.join(map(str, pa)))`

### python中的map函数

在Python中，`map()` 函数是一个非常有用的高阶函数，它允许你对可迭代对象（如列表、元组等）的每个元素应用一个给定的函数，并返回一个新的迭代器。

#### 函数原型

```python
map(func, *iterables)
```

#### 参数

- `func`: 一个函数，它会被应用到每个元素上。
- `*iterables`: 一个或多个可迭代对象，函数 `func` 将依次应用于这些可迭代对象的元素。

#### 返回值

- `map()` 返回一个 `map` 对象，这是一个迭代器，可以被转换为列表或其他数据结构。

#### 使用示例

```python
def square(x):
    return x * x

numbers = [1, 2, 3, 4, 5]

# 使用 map 函数
squared_numbers = map(square, numbers)

# 将结果转换为列表
print(list(squared_numbers))
```

#### 输出

```
[1, 4, 9, 16, 25]
```

#### 多个可迭代对象

`map()` 也可以接受多个可迭代对象，并将函数应用于每个可迭代对象的对应元素。

```python
def add(a, b):
    return a + b

list1 = [1, 2, 3]
list2 = [4, 5, 6]

# 使用 map 函数
result = map(add, list1, list2)

# 将结果转换为列表
print(list(result))
```

#### 输出

```
[5, 7, 9]
```

#### 注意事项

1. **Lambda 表达式**：你可以使用 `lambda` 表达式作为 `map()` 的第一个参数，这样可以在一行代码内定义和应用函数。

   ```python
   numbers = [1, 2, 3, 4, 5]
   squared_numbers = map(lambda x: x * x, numbers)
   print(list(squared_numbers))
   ```

2. **惰性求值**：`map()` 返回的是一个迭代器，这意味着它不会立即计算所有结果，而是在迭代时才计算。这可以提高效率，特别是处理大数据集时。

3. **空可迭代对象**：如果任何一个可迭代对象是空的，那么 `map()` 返回的结果也将是空的。

4. **类型限制**：`map()` 只能用于可迭代对象，不能用于非可迭代对象。

5. **性能**：对于简单的操作，使用 `map()` 通常比使用列表推导式更快。

6. **错误处理**：如果 `func` 函数抛出异常，`map()` 会停止执行并抛出异常。

7. **Python 3**：在Python 3中，`map()` 不再返回列表，而是返回一个迭代器。如果你需要一个列表，可以使用 `list()` 函数来转换。

8. **与 `filter()` 结合**：`map()` 经常与 `filter()` 函数结合使用，以过滤和转换数据。

`map()` 函数是Python中实现函数式编程风格的强大工具之一，它可以使代码更加简洁和高效。

### python中的defaultdict

<center>关键词：defaultdict<center>

<center>关键词：图的邻接表存储<center>

在Python中，`defaultdict` 是 `collections` 模块中的一个非常有用的类，它继承自内置的 `dict` 类。`defaultdict` 解决了普通字典在访问不存在的键时会抛出 `KeyError` 的问题。它允许你为字典提供一个默认值，当访问一个不存在的键时，会返回这个默认值。

#### 如何导入

首先，你需要从 `collections` 模块导入 `defaultdict`：

```python
from collections import defaultdict
```

#### 基本用法

当你创建一个 `defaultdict` 对象时，你需要提供一个函数，这个函数会在访问不存在的键时被调用，以生成默认值：

```python
# 创建一个默认值为int的defaultdict
dd = defaultdict(int)
```

在上面的例子中，如果尝试访问一个不存在的键，`defaultdict` 将使用 `int()` 函数（返回0）作为默认值。

#### 示例代码

```python
from collections import defaultdict

# 创建一个默认值为int的defaultdict
dd = defaultdict(int)

# 访问不存在的键，不会抛出KeyError，而是返回默认值0
print(dd['apple'])  # 输出: 0

# 更新键的值
dd['apple'] += 1
print(dd['apple'])  # 输出: 1

# 另一个不存在的键
print(dd['banana'])  # 输出: 0

# 创建一个默认值为list的defaultdict
dd_list = defaultdict(list)

# 访问不存在的键，返回一个空列表
print(dd_list['orange'])  # 输出: []

# 添加元素到列表
dd_list['orange'].append(1)
print(dd_list['orange'])  # 输出: [1]
```

#### 常用默认值类型

- **int**：用于计数。
- **list**：用于累积元素。
- **dict**：用于嵌套字典。
- **set**：用于累积不重复的元素。

#### 更多示例

##### 计数示例

```python
# 计数示例
word_count = defaultdict(int)

for word in ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']:
    word_count[word] += 1

print(word_count)
# 输出: defaultdict(<class 'int'>, {'apple': 2, 'orange': 2, 'pear': 1, 'banana': 1})
```

##### 累积列表

```python
# 累积列表示例
items = defaultdict(list)

items['apple'].append(1)
items['apple'].append(2)
items['orange'].append(3)

print(items)
# 输出: defaultdict(<class 'list'>, {'apple': [1, 2], 'orange': [3]})
```

##### 嵌套字典

```python
# 嵌套字典示例
nested_dict = defaultdict(lambda: defaultdict(int))

nested_dict['apple']['color'] = 1
nested_dict['orange']['color'] = 1

print(nested_dict)
# 输出: defaultdict(<function <lambda> at 0x...>, {'apple': defaultdict(<class 'int'>, {'color': 1}), 'orange': defaultdict(<class 'int'>, {'color': 1})})
```

#### 注意事项

1. **默认值是可变的**：默认值（如列表和字典）是可变的，所以如果你不小心修改了默认值，它会影响所有后续的默认值生成。
2. **性能**：`defaultdict` 在访问不存在的键时，性能开销比普通字典稍高，因为它需要调用默认值生成函数。

`defaultdict` 是处理字典时非常有用的工具，特别是在你需要自动初始化默认值的情况下。

## 10.21

### pairwise函数

<center>关键词：pairwise<center>

`pairwise` 是 Python 3.10 版本中新增到 `itertools` 模块的一个函数，它用于从给定的可迭代对象中生成连续重叠的元素对。这意味着每一对元素中的第一个元素会与下一对元素中的第二个元素重叠。此函数非常适合用于需要处理相邻元素对的场景，如计算差异、比较操作等。

#### 基本用法

```python
from itertools import pairwise
data = [1, 2, 3, 4, 5]
pairs = pairwise(data)
for pair in pairs:
    print(pair)  # 输出：(1, 2) (2, 3) (3, 4) (4, 5)
```

#### 特点

- 如果输入的可迭代对象元素少于两个，则 `pairwise` 不会生成任何元素对。
- 返回的迭代器生成的元素对是按顺序的，并且只包含相邻的元素对。

#### 应用场景

- **数据处理**：在需要依次处理相邻元素对的数据分析和转换过程中非常有用。
- **迭代器操作**：对于大型数据集，可以避免一次性加载所有数据，而是逐对处理数据，减少内存消耗。
- **算法实现**：在实现一些算法时，需要访问相邻元素对，如计算差值或者比较操作。

#### 实用案例

计算相邻元素差值：

```python
from itertools import pairwise
data = [10, 15, 20, 25, 30]
differences = [y - x for x, y in pairwise(data)]
print(differences)  # 输出：[5, 5, 5, 5]
```

在这个例子中，我们使用 `pairwise` 函数来计算列表中相邻元素之间的差值。

#### 注意事项

- `pairwise` 函数返回的是一个迭代器，如果你需要一个列表，可以使用 `list()` 函数来转换。
- 在 Python 3.10 之前的版本中没有 `pairwise` 函数，但可以通过简单的循环来实现类似的功能。

#### 替代实现

在 Python 3.10 之前的版本中，可以通过以下方式实现类似的功能：

```python
data = "abcdef"
for i in range(len(data) - 1):
    print((data[i], data[i+1]))
```

这将输出与 `pairwise` 相同的相邻元素对。

`pairwise` 是一个非常实用的函数，特别是在处理连续元素对时，可以简化代码并提高效率。

## 11.15

### 二维列表行优先转化为列优先

<center>关键词：转置<center>

<center>关键词：列表转置<center>

在Python中，`zip(*grid)` 是一种常用的技巧，用于将行优先的二维列表（或数组）转换为列优先。这里的 `grid` 是一个二维列表，代表一个矩阵。`zip` 函数接受一个或多个迭代器（如列表、元组等）作为参数，并将它们“压缩”成一个元组的迭代器。当使用星号表达式 `*` 与 `zip` 函数结合时，它将 `grid` 中的每个子列表（即每一行）作为独立的参数传递给 `zip` 函数。

让我们逐步分析 `for col in zip(*grid):` 这行代码：

1. `*grid`：星号表达式 `*grid` 会将 `grid` 二维列表中的每个子列表（即每一行）解包为独立的参数。如果 `grid` 是一个 `m x n` 的矩阵，那么 `*grid` 将会生成 `m` 个参数，每个参数都是一个长度为 `n` 的列表。

2. `zip(*grid)`：`zip` 函数接受这些解包后的行列表作为参数，并将它们“压缩”成一个迭代器，该迭代器生成元组。每个元组包含所有行中相同列索引位置的元素。例如，如果 `grid` 是：

   ```python
    grid = [
     [1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]
   ]
   ```

   那么 `zip(*grid)` 将会生成一个迭代器，其输出为：

   ```
    [(1, 4, 7), (2, 5, 8), (3, 6, 9)]
   ```

   这里，每个元组代表 `grid` 中的一列。

3. `for col in zip(*grid):`：这个循环遍历 `zip(*grid)` 生成的迭代器。对于每一列（即每个元组），`col` 变量将会包含该列的所有元素。在循环体内部，`col` 代表当前处理的列。

在您提供的代码中，`for col in zip(*grid):` 这行代码用于遍历 `grid` 中的每一列。然后，代码使用一个内部循环来检查每一列的前半部分和后半部分是否对称。如果对称，则 `diff_col` 计数器增加。这种方法有效地计算了矩阵中列的对称差异数量，与之前计算行的对称差异数量类似。

总结来说，`for col in zip(*grid):` 这行代码通过 `zip` 函数和星号表达式将二维列表中的行转换为列，并遍历每一列以计算对称差异。这是一种高效且Pythonic的方式来处理二维数据结构中的列操作。

### python中的*操作

<center>关键词：*<center>

<center>关键词：解包<center>

<center>关键词：乘法<center>

在Python中，`*`操作符有多种用途，包括数学乘法、解包（unpacking）、参数传递以及与`zip`函数一起使用。下面详细介绍这些用途：

#### 1. 数学乘法

`*`最基本的用途是作为数学乘法运算符，用于两个数之间的乘法运算。

```python
result = 3 * 4  # 结果为 12
```

#### 2. 解包（Unpacking）

`*`可以用来解包序列（如列表、元组）、集合或任何可迭代对象，将其元素作为独立的参数传递给函数或其他操作。

##### 解包列表或元组

```python
my_list = [1, 2, 3]
a, b, c = *my_list  # a = 1, b = 2, c = 3
```

##### 解包字典

```python
my_dict = {'a': 1, 'b': 2}
for key, value in my_dict.items():
    print(key, value)  # 输出: a 1 b 2
```

##### 解包与`zip`函数

```python
a = [1, 2]
b = [3, 4]
for x, y in zip(*a, *b):  # 等价于 zip(a, b)
    print(x, y)  # 输出: 1 3 和 2 4
```

#### 3. 参数传递

在函数定义中，`*`可以用来收集多余的位置参数到一个元组中。

```python
def func(*args):
    for arg in args:
        print(arg)

func(1, 2, 3)  # 输出: 1 2 3
```

#### 4. 关键字参数

`**`操作符用于收集多余的关键字参数到一个字典中。

```python
def func(**kwargs):
    for key, value in kwargs.items():
        print(key, value)

func(a=1, b=2)  # 输出: a 1 b 2
```

#### 5. 与`zip`函数一起使用

当`*`与`zip`函数一起使用时，可以将多个列表或元组中的元素“压缩”成一个个元组。

```python
a = [1, 2, 3]
b = [4, 5, 6]
for x, y in zip(a, b):
    print(x, y)  # 输出: 1 4 和 2 5 和 3 6
```

#### 6. 创建可变长列表、字典和字符串

`*`可以用来创建可变长的列表、字典和字符串。

##### 列表

```python
my_list = [*[1, 2, 3]]  # my_list = [1, 2, 3]
```

##### 字典

```python
my_dict = {**{'a': 1, 'b': 2}}  # my_dict = {'a': 1, 'b': 2}
```

##### 字符串

```python
my_str = "hello" * 3  # my_str = "hellohellohello"
```

#### 7. 解包字典项

在函数调用中，`*`可以用来解包字典项作为关键字参数。

```python
def func(a, b):
    print(a, b)

kwargs = {'a': 1, 'b': 2}
func(**kwargs)  # 等同于 func(a=1, b=2)
```

#### 总结

`*`操作符在Python中有多种用途，包括数学乘法、解包、参数传递、与`zip`函数一起使用以及创建可变长的数据结构。这些用途使得`*`成为一个非常灵活和强大的工具，可以在多种场景下简化代码和提高效率。

### python中的解包操作

<center>关键词：解包操作<center>

在Python中，解包操作（unpacking）通常用于将序列类型的数据（如列表、元组）中的元素提取出来，以便可以分别对它们进行操作。当涉及到多维数据结构时，解包操作可以递归地进行，这意味着你可以解包嵌套的数据结构以访问更深层的元素。

#### 多维数据结构的解包

假设我们有一个多维列表（列表的列表），我们想要解包它以访问内部的元素。以下是一些例子：

##### 二维列表解包

```python
# 二维列表
two_dim_list = [[1, 2], [3, 4], [5, 6]]

# 解包操作
for inner_list in two_dim_list:
    a, b = inner_list  # 对每个内部列表进行解包
    print(a, b)
```

在这个例子中，`two_dim_list` 是一个二维列表。当我们遍历 `two_dim_list` 时，每次迭代都会取出一个内部列表 `inner_list`。然后，我们对 `inner_list` 进行解包，将其第一个元素赋值给 `a`，第二个元素赋值给 `b`。

##### 三维列表解包

对于三维列表，解包操作可以递归地进行：

```python
# 三维列表
three_dim_list = [[[1, 2], [3, 4]], [[5, 6], [7, 8]]]

# 解包操作
for two_dim_sublist in three_dim_list:
    for one_dim_sublist in two_dim_sublist:
        a, b = one_dim_sublist  # 对最内层的列表进行解包
        print(a, b)
```

在这个例子中，`three_dim_list` 是一个三维列表。我们首先遍历最外层的列表，然后遍历每个二层列表，最后对最内层的列表进行解包。

#### 解包与函数参数

当涉及到函数调用时，解包操作可以用来将列表或元组中的元素作为独立的参数传递给函数：

```python
# 函数定义
def func(a, b, c):
    print(a, b, c)

# 多维列表
args = [(1, 2, 3), (4, 5, 6)]

# 解包操作
for arg_tuple in args:
    func(*arg_tuple)  # 使用 * 操作符解包并传递参数
```

在这个例子中，`args` 是一个包含多个元组的列表。我们遍历 `args`，并对每个元组使用 `*` 操作符进行解包，将元组中的元素作为独立的参数传递给 `func` 函数。

#### 解包与字典

对于包含字典的多维结构，解包操作可以用来同时提取键和值：

```python
# 包含字典的多维结构
dict_list = [{'a': 1, 'b': 2}, {'c': 3, 'd': 4}]

# 解包操作
for d in dict_list:
    for key, value in d.items():
        print(key, value)
```

在这个例子中，`dict_list` 是一个包含字典的列表。我们遍历 `dict_list`，然后对每个字典使用 `.items()` 方法和解包操作来同时获取键和值。

总结来说，解包操作可以应用于任何维度的数据结构，允许你访问和操作嵌套的数据。在函数参数传递、循环遍历和数据处理中，解包是一个非常有用的特性，它使得代码更加简洁和灵活。
