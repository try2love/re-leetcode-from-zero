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

