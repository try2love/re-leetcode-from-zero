## 4.18

1. 获取数组长度可以直接用 数组名.size()
2. 回忆起有序表的查找方式 二分查找
3. 新的遍历数组方式：for (char letter : letters) 遍历letters中的每个元素并赋值给letter

## 4.19

1. 获取字符串的长度我是根据记忆里面的`s.length()`写的，是正确的。
2. 对字符串的访问可以直接用下标，实现类似数组的访问方式
3. C++中map函数生成键值对，可以根据键值对中的任何一个索引得到对应元素的值
4. map： map内部实现了一个红黑树（红黑树是非严格平衡二叉搜索树，而AVL是严格平衡二叉搜索树），红黑树具有自动排序的功能，因此**map内部的所有元素都是有序的**，红黑树的每一个节点都代表着map的一个元素。因此，对于map进行的查找，删除，添加等一系列的操作都相当于是对红黑树进行的操作。map中的元素是按照二叉搜索树（又名二叉查找树、二叉排序树，特点就是左子树上所有节点的键值都小于根节点的键值，右子树所有节点的键值都大于根节点的键值）存储的，使用中序遍历可将键值按照从小到大遍历出来。
   unordered_map: unordered_map内部实现了一个**哈希表**（也叫散列表，通过把关键码值映射到Hash表中一个位置来访问记录，查找的时间复杂度可达到O(1)，其在海量数据处理中有着广泛应用）。因此，其元素的排列顺序是无序的。

## 4.20

1. 复习了数据结构中对二叉树的遍历，重新翻看了自己的408笔记
2. 对返回值的界定有了更深的理解
3. 复习了递归算法的实现，尤其是最后的`return getTargetCopy(original->right,cloned->right,target);`这个函数最后返回仍为函数本身，但是初始节点发生了变化，实现了递归操作。
4. 先序遍历方法中简洁写法的`if(left_res)`确实很简洁，因为`left_res`要么是null要么是一个确定节点，可以直接return。
5. C++中队列的初始化：`queue<type> name`
6. 队列获取队首元素：`name.front()`
7. 队列输入：`name.push(element)`  队列输出：`name.pop()`

## 4.21

### 在C/C++中可以使用下标来直接对字符串类型数据进行修改

### C++创建map对象：

`map<类型,类型,...>名称={{对应类型的值，对应类型的值，...}...}`
不进行赋值则去掉等号和后面数据
依据map中其中一个关键字写入对应位置的数据：`map[关键字]=数据`

### C++中 `string result(length, 0);`可以直接定义定长的字符串类型，其中元素都用0进行填充

### 在C++中，`std::vector<int>` 

是一种容器，用于存储相同类型元素的动态数组。这里的 `std::` 表示这个类型是标准命名空间的一部分，`vector` 是容器的名称，而 `<int>` 指定了这个容器存储的元素类型是 `int`（整数）。

下面是 `std::vector<int>` 的一些关键特性的详细解释：

**特性**

1. **动态数组**：`std::vector` 可以根据需要自动调整大小，这使得它比传统的数组更灵活。
2. **随机访问**：`std::vector` 提供了随机访问迭代器，这意味着可以快速地访问容器中的任何元素。
3. **模板类**：`vector` 是一个模板类，可以使用任何类型的对象，不仅仅是 `int`。
4. **异常安全性**：标准库的 `vector` 实现通常保证了良好的异常安全性。
5. **成对迭代器**：使用 `begin()` 和 `end()` 成员函数可以获取指向 vector 开始和结束的迭代器

### 在 C++ 中，`std::` 前的双冒号 `::` 

是作用域解析运算符，也称为范围解析运算符。它用于明确指出某个实体（如类型、函数、对象等）属于特定的命名空间或作用域。

当你看到 `std::vector` 或 `std::sort` 这样的表达式时，这里的 `std::` 表示 `vector` 和 `sort` 属于 `std`（标准）命名空间。在 C++ 中，为了避免命名冲突，许多标准库的组件都被放置在 `std` 这个命名空间下。

**使用场景**

1. **明确命名空间**：当你需要明确指出某个实体属于哪个命名空间时，可以使用 `::` 运算符。

   ```cpp
   std::vector<int> v; // 使用 std 命名空间下的 vector 模板类
   ```

2. **访问全局命名空间**：当局部作用域或类中有一个与全局命名空间中的名字相同的实体时，可以使用 `::` 来访问全局实体。

   ```cpp
   void myFunction() {
       int myVar = 10;
       std::cout << ::myVar; // 访问全局命名空间中的 myVar
   }
   ```

3. **多级命名空间**：当实体位于多级命名空间中时，可以通过连续使用 `::` 来访问。

   ```cpp
   namespace Outer {
       namespace Inner {
           void myFunction() {}
       }
   }
   
   int main() {
       Outer::Inner::myFunction(); // 调用 Outer 命名空间下的 Inner 命名空间中的 myFunction
   }
   ```

**注意事项**

- 如果没有使用 `std::`，编译器会尝试在程序的当前命名空间中查找 `vector` 或 `sort`，如果找不到，会导致编译错误。
- 使用 `using namespace std;` 可以避免每次都需要写 `std::`，但这通常不推荐在大型项目或头文件中使用，因为它可能导致命名冲突。

在 C++ 中，正确使用作用域解析运算符 `::` 是非常重要的，它有助于编写清晰、易于理解的代码，并避免潜在的命名冲突。

### C++中有个很方便的数据类型叫auto

在下午的解法中返回值设为auto，形参也为auto类型，可以有效避免代码重复，只要传入实参是相同的数据类型就可以完成交换操作

### 数组类型做形参时，可以书写为`类型 类型名[]`,`类型* 类型名`,`类型 类型名[个数]`最终都可以使用。

### 数组形参的辨析

在C++中，函数参数可以以多种方式声明，以适应不同的使用场景：

1. `vector<int>& array`

   - 这表示 `array` 是一个 `std::vector<int>` 类型对象的引用。使用引用（`&`）意味着函数**不会复制**整个 `vector` 对象，而是**直接操作传入的 `vector`**。这适用于当你想要修改传入的 `vector` 对象，或者避免不必要的复制以提高效率时。

   使用场景：

   - 需要在函数内部修改外部 `vector` 对象。
   - 希望避免复制大型容器，以提高性能。

   ```cpp
   void printVector(const vector<int>& array) {
       for (int num : array) {
           cout << num << " ";
       }
       cout << endl;
   }
   ```

2. `int array[]`

   - 这表示 `array` 是一个整数数组。这种形式通常用于函数参数，以便函数可以接收一个数组作为输入。然而，使用这种方式声明的数组参数在函数内部是按值传递的，这意味着会**复制整个数组**，这可能对性能不利。

   使用场景：

   - 当需要函数内部使用数组，并且不需要修改原始数组时。

   ```cpp
   void printArray(int array[], int size) {
       for (int i = 0; i < size; ++i) {
           cout << array[i] << " ";
       }
       cout << endl;
   }
   ```

3. `int *array`

   - 这表示 `array` 是一个指向整型的指针。指针参数允许函数**操作数组的第一个元素的地址**，但它不会自动传递整个数组。使用指针时，通常需要额外传递一个表示数组大小的参数，因为指针本身不包含它所指向的数组的大小信息。

   使用场景：

   - 当需要操作数组，但**不希望复制整个数组**以节省内存和提高效率时。
   - 当需要**处理大小可变或者多维数组**时。

   ```cpp
   void printPointerArray(int *array, int size) {
       for (int i = 0; i < size; ++i) {
           cout << array[i] << " ";
       }
       cout << endl;
   }
   ```

4. `int& array[]`

   - 这种声明是不合法的，因为引用必须绑定到一个对象上，而不能是数组。当你**想要通过引用修改数组时**，通常会使用 `vector` 或者传递数组的指针 `int*`。

在C++中，选择哪种方式取决于具体的应用场景和性能要求。例如，当你需要修改数组或避免复制时，可能会选择使用引用或指针。而当你不需要修改数组，并且不需要处理数组的边界时，可能会选择使用数组参数。

### C++中的`&`运算符在引用中的详解

在C++中，`&` 符号有两个主要含义：引用和位运算符。在函数形参中，`&` 通常用作引用运算符，表示参数按引用传递，而不是按值传递。

**引用运算符**（&）

1. **按引用传递**：当 `&` 用作函数参数类型前的修饰符时，它告诉编译器该参数是一个引用。这意味着函数接收的是变量的别名，而不是变量的副本。对引用参数的任何修改都会反映到传递给函数的实际变量上。

   ```cpp
   void modifyValue(int& ref) {
       ref += 10; // 修改引用的原始变量
   }
   ```

2. **使用场景**：

   - 当你想要函数修改传入的参数值时。
   - 当你想要避免复制大型对象或数组以提高效率时。

3. **注意事项**：

   - 引用必须在创建时就被初始化，即它们必须绑定到另一个对象。
   - 引用不同于指针，它们不允许 `NULL` 值，并且引用的生命周期通常与被引用的对象相同。

**引用的常见用途**

1. **函数参数**：允许函数修改传入的对象。

   ```cpp
   void increase(Student& student) {
       student.age++; // 直接修改传入对象的年龄
   }
   ```

2. **返回多个值**：允许函数通过引用返回多个值。

   ```cpp
   void getDimensions(const vector<int>& vec, int& size, int& capacity) {
       size = vec.size();
       capacity = vec.capacity();
   }
   ```

3. **大型对象或数组**：避免复制大型对象或数组，提高性能。

   ```cpp
   void processArray(const vector<int>& array) {
       // 处理数组，无需复制整个数组
   }
   ```

4. **指针参数的替代**：在某些情况下，引用可以作为指针的替代，提供更清晰的代码。

   ```cpp
   bool isValid(const string& str) {
       // 检查字符串是否有效，无需处理指针可能的空值问题
   }
   ```

在函数形参中使用 `&` 符号时，通常是为了创建引用，而不是按值传递参数。这在需要函数修改参数或提高性能时非常有用。

### `const`关键字在形参中的用法

<center>关键词：const<center>

在C++中，`const` 关键字用于指定一个变量或对象的状态不能被修改。当你在函数参数中使用 `const` 时，你告诉编译器这个参数在函数内部**不能被修改**。

#### `const` 在形参中的作用

1. **防止修改**：在函数参数中使用 `const` 可以防止函数内部修改传递给它的参数。这在你想要保持参数的原始状态不被函数改变时非常有用。

2. **明确意图**：使用 `const` 可以向阅读代码的其他开发者明确你的意图，即这个参数不应该被函数修改。

3. **编译时检查**：如果函数内部不小心尝试修改了 `const` 参数，编译器将会报错，这提供了一种编译时的安全性。

#### `const` 在 `getDimensions` 函数中的例子

```cpp
void getDimensions(const vector<int>& vec, int& size, int& capacity) {
    size = vec.size();
    capacity = vec.capacity();
}
```

在这个例子中：

- `const vector<int>& vec`：这里 `vec` 是一个 `std::vector<int>` 的引用，并且是 `const` 的。这意味着 `getDimensions` 函数**不能修改 `vec` 中的任何元素，也不能调用任何会修改 `vec` 大小或容量的成员函数**。`vec` 作为 `const` 引用传递，确保了传入的 `vector` 不会被函数修改。

- `int& size` 和 `int& capacity`：这两个参数是对整数的非 `const` 引用，意味着函数可以修改它们。这允许函数将 `vector` 的 `size` 和 `capacity` 赋值给调用者提供的变量。

#### 何时使用 `const` 在形参中

- **当你想返回多个值时**：使用 `const` 引用参数可以避免复制大型对象，同时还可以修改并返回多个值。

- **当你需要传递大型对象时**：为了避免昂贵的复制操作，你可以将大型对象作为 `const` 引用传递。

- **当你需要传递的对象不应被修改时**：如果你只想在函数中读取对象的内容，而不改变它，使用 `const` 引用是合适的。

- **当你需要提高代码的清晰度和安全性时**：使用 `const` 可以避免不小心修改参数，增加代码的可读性，并在编译时提供额外的检查。

#### 注意事项

- 使用 `const` 引用时，必须确保传递的对象在函数的整个生命周期内都是有效的。

- 如果你需要在函数内部修改参数的值，那么就不能使用 `const`。

- 如果你传递的是基本数据类型的引用（如 `int&`），`const` 不适用，因为基本数据类型的引用本身不能是 `const`。

- 有时候，即使参数在函数内部不需要修改，也会使用 `const`，这有助于传达函数的设计意图，即不会更改传入的参数。

### 数组作为形参引用的形式

 在C++中，数组作为函数参数传递时，通常会**退化为指向数组首元素的指针**。因此，如果你想要通过引用来操作整个数组，你需要采取特定的方法来确保数组被按引用传递，而不仅仅是数组的指针。

#### 使用引用传递整个数组

为了按引用传递整个数组，你可以使用数组的引用作为函数参数。但是，需要注意的是，**数组的大小信息不会随着引用传递**，所以如果你需要知道数组的大小，你必须以某种方式将其传递给函数。

```cpp
template <size_t N>
void processArray(const int (&array)[N]) {
    // 在这里操作数组元素，例如：
    for (int i = 0; i < N; ++i) {
        // do something with array[i]
    }
}

int main() {
    int myArray[] = {1, 2, 3, 4, 5};
    processArray(myArray); // 使用模板明确数组大小
    return 0;
}
```

在这个例子中，`processArray` 函数接受一个整数数组的引用，并且通过模板参数 `N` 明确了数组的大小。这样，函数就可以安全地访问数组的每个元素，而不需要担心越界。

#### 使用指针和大小

如果你不能或不想使用模板，你可以将数组作为指针传递，并额外传递一个表示数组大小的参数。

```cpp
void processArray(const int* array, size_t size) {
    // 在这里操作数组元素，例如：
    for (size_t i = 0; i < size; ++i) {
        // do something with array[i]
    }
}

int main() {
    int myArray[] = {1, 2, 3, 4, 5};
    processArray(myArray, sizeof(myArray) / sizeof(myArray[0])); // 传递数组和大小
    return 0;
}
```

在这个例子中，`processArray` 函数接受一个指向整数的指针和数组的大小。这样，函数就可以根据传递的大小安全地访问数组的每个元素。

#### 使用容器类

另一种常见的做法是使用标准库容器，如 `std::vector` 或 `std::array`，它们可以直接按引用传递，且不需要担心数组退化的问题。

```cpp
void processArray(const std::vector<int>& vec) {
    // 在这里操作 vector 的元素
    for (int value : vec) {
        // do something with value
    }
}

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};
    processArray(vec); // 使用 vector 按引用传递
    return 0;
}
```

使用 `std::vector` 或其他容器类不仅可以避免数组退化的问题，还可以利用容器类的成员函数进行更复杂的操作。

#### 总结

在C++中，直接按引用传递数组并不常见，因为数组退化为指针，且没有大小信息。通常，你会使用模板、指针和额外的大小参数，或者使用标准库容器来按引用传递数组。选择哪种方法取决于具体的使用场景和个人偏好。

### 基于范围的for循环

这段代码中的 `for` 循环使用了 C++11 标准引入的一种新的循环语法，称为**基于范围的 for 循环**（range-based for loop）。这种语法是在 C++11 中引入的，旨在简化对容器和数组的遍历。

#### 基于范围的 for 循环语法

```cpp
for (declaration : expression) statement
```

- `declaration`：这是一个声明，通常是一个变量，用于**在每次循环迭代中存储序列中的当前元素**。
- `expression`：这是一个表达式，它**产生一个序列**，可以是一个数组、向量（vector）、列表（list）等容器，或者任何其他提供迭代器的序列。
- `statement`：这是一个语句，通常是一个块（由花括号 `{}` 包围），在每次迭代中执行。

#### 示例代码解释

```cpp
void printVector(const vector<int>& array) {
    for (int num : array) {
        cout << num << " ";
    }
    cout << endl;
}
```

在这个例子中：

- `int num`：这是循环变量的声明，它在每次迭代中被初始化为序列中的下一个元素。
- `array`：这是 `vector<int>` 类型的容器，它被用作基于范围的 for 循环的表达式。由于 `vector` 提供了迭代器，所以它适合在这种循环中使用。
- `cout << num << " ";`：这是循环体，它打印出当前迭代中的元素 `num`，后面跟着一个空格。

#### 工作原理

基于范围的 for 循环背后的工作原理是利用了容器（如 `vector`）的开始和结束迭代器。在循环开始时，循环变量 `num` 被初始化为序列的第一个元素（通过 `array.begin()` 获取）。在每次迭代中，循环变量会自动更新为序列的下一个元素，直到达到序列的末尾（通过 `array.end()` 表示）。由于 `array` 是一个 `const vector<int>&` 类型，这意味着函数不能修改传入的 `vector`，并且迭代器也是 `const` 的，不能用于修改元素。

#### 使用场景

基于范围的 for 循环非常适合用于遍历容器中的元素，特别是当不需要显式处理迭代器或计数器时。它提供了一种简洁、可读性强的方式来访问序列中的每个元素。

#### 注意事项

- 确保使用的序列（如容器或数组）提供了有效的迭代器。
- 循环变量在每次迭代中都会被重新初始化，因此不要在循环外部使用相同的名字，以避免潜在的冲突。

基于范围的 for 循环是现代 C++ 编程中广泛使用的一种语法，它提高了代码的可读性和简洁性。

### 传递数组给函数并保存操作结果

在C++中，当你想要将数组传递给函数并允许函数修改数组中的元素时，你可以**直接传递数组的名称**，因为数组的名称在大多数表达式中会被解释为指向数组首元素的指针。但是，如果你想要明确指出你传递的是数组的引用（以避免数组退化为指针），你可以**使用数组的引用**作为函数参数。

下面是一个示例，演示如何声明一个函数，该函数接受一个整数数组的引用，并在函数体内操作数组元素：

```cpp
void operateArray(int (&array)[8]) {
    for (int i = 0; i < 8; ++i) {
        // 对 array 的每个元素进行操作
        array[i] += 10;  // 这里假设我们给每个元素加10
    }
}

int main() {
    int myArray[8] = {1, 2, 3, 4, 5, 6, 7, 8};
    operateArray(myArray);
    // 此时 myArray 中的每个元素都增加了10
    return 0;
}
```

在这个例子中，`operateArray` 函数的参数 `int (&array)[8]` 明确指出 `array` 是一个包含8个整数的数组的引用。这意味着函数可以直接修改传递给它的数组的元素。

### 声明并使用 vector 类型

<center>关键词：vector<center>
<center>
    关键词：声明vector
<center>

`std::vector` 是C++标准模板库（STL）中的一个容器类，它提供了动态数组的功能。以下是如何声明和使用 `std::vector` 的基本步骤：

1. **包含头文件**：首先，你需要包含 `<vector>` 头文件以使用 `std::vector`。

2. **声明 vector**：声明一个 `std::vector` 时，你需要指定存储在向量中的元素类型。

3. **构造 vector**：你可以在声明时初始化 `std::vector`，或者之后添加元素。

4. **访问和修改元素**：使用下标 `[]` 运算符来访问和修改 `std::vector` 中的元素。

5. **迭代器**：可以使用迭代器来遍历 `std::vector` 中的元素。

下面是使用 `std::vector` 的一个示例：

```cpp
#include <iostream>
#include <vector>

int main() {
    // 声明并初始化一个 vector，类型为 int
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // 使用下标操作符修改元素
    vec[2] = 30;  // 将第三个元素修改为30

    // 使用范围基于的for循环遍历 vector
    for (int num : vec) {
        std::cout << num << " ";
    }
    std::cout << std::endl;

    // 添加元素到 vector 的末尾
    vec.push_back(6);

    // 使用迭代器遍历 vector
    for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

在这个例子中，我们首先声明了一个 `std::vector<int>` 类型的变量 `vec`，并初始化了一些整数值。然后我们修改了 `vec` 中的一个元素，使用基于范围的for循环和迭代器遍历了 `vec`，并且使用 `push_back` 方法在 `vec` 的末尾添加了一个新的元素。

`std::vector` 是一个非常灵活和强大的容器，它支持许多有用的操作，如 `size()`、`empty()`、`clear()`、`insert()`、`erase()` 等。

## 4.22

1. 哈希表的**声明**：`unordered_map<类型,类型>表名;`
   哈希表的**初始化**实例：`unordered_map<int,int>hashmap{{1,10},{2,12},{3,13}};`也可以这样：`unordered_map<int,int>hash_map{{{1,10},{2,13},{3,13}},3}`
   上面两个语句等价，后者是给定一个确定的值3表示哈希表中有三个键值对，而前者是自动识别，也有三个键值对
   哈希表**添加键值对**：`hash_map.insert({key,value});`
   **复制构造**（初始化新的表）:`unordered_map<int,int>hmap(hash_map);`

2. **find()函数**：
   以key作为参数寻找哈希表中的元素，如果哈希表中存在该key值则返回该位置上的迭代器，否则返回哈希表最后一个元素下一位置上的迭代器。
   举例：

   ```cpp
   unordered_map<int, int> hmap{ {1,10},{2,12},{3,13} };
   unordered_map<int, int>::iterator iter;
   iter = hmap.find(2); //返回key==2的迭代器，可以通过iter->second访问该key对应的元素
   if(iter != hmap.end())  cout << iter->second;
   ```

3. 对迭代器vector类型的初始化：
   1.默认初始化：`vector<int> vec`没有被只能怪大小或者元素，被默认初始化为一个空向量
   2.通过大小初始化：`vector<int> vec(10[,val]);`指定向量的大小来初始化，所有元素被默认初始化，若不指定val值，默认全为0；指定val，每个元素都是val
   3.通过数组或者另一个容器初始化：

   ```cpp
   int arr[] = {1, 2, 3, 4, 5};
   std::vector<int> vec(arr, arr + sizeof(arr) / sizeof(arr[0]));
   // 或者更简单的写法
   std::vector<int> vec{1, 2, 3, 4, 5};
   ```

   4.使用花括号初始化：`vector<int> vec[ = ]{1,2,3,4,5};`等号可选（花括号内容为空，创建空向量）
   5.使用vector的构造函数：
   `std::vector<int, std::allocator<int>> vec(10); // 显式指定了容器类型和分配器类型`
   5.vector的成员函数：
   `vec.resize(10 [,val]);`向量大小调整为10，新元素默认val
   6.使用std::mov来动态内存优化：
   `vector<int> tmp=std::move(vec);`

## 4.23

### break和continue

`break;`用于跳出并结束当前的循环（同一个循环体中，后面的循环不用做了）
`continue;`本次循环后续内容跳过，继续执行下一次循环。

### string的赋值

#### 直接使用等号

对已经声明并赋值的string类型元素进行赋空值：正确做法`str="";`错误做法：`str='';`这样理解：string是char的复数形式，对char类型赋值通常使用单引号，则**对string类型赋值应该采用双引号**

#### 使用clear

`str.clear()`完成把str清空操作。

#### 使用erase

`str.erase(str.begin(),str.end());`也可实现清除字符串内容。且此做法更灵活，是对字符串从传入参数的初始到末尾之间的数据进行抹除

#### 赋值空字符

`str='\0';`虽然可以清空字符串，但是会存在一个空字符，长度不为0

#### 使用assign方法

`str.assign("");`该方法可以用来重新赋值字符串。

### 对vector类型的操作

<center>关键词：vector操作<center>

<center>关键词：vector<center>

#### 构造和初始化

- **默认构造**：创建一个空的 vector。

  ```cpp
  std::vector<int> vec;
  ```

- **指定大小构造**：创建一个具有指定大小的 vector，所有元素都会被默认初始化。

  ```cpp
  std::vector<int> vec(10); // 10 个 int 类型的元素，都被初始化为 0
  ```

- **带初始值的构造**：创建一个具有指定大小的 vector，所有元素都被初始化为某个特定的值。

  ```cpp
  std::vector<int> vec(10, 1); // 10 个 int 类型的元素，都被初始化为 1
  ```

- **复制构造**：创建一个 vector，它是另一个 vector 的副本。

  ```cpp
  std::vector<int> vec1 = {1, 2, 3};
  std::vector<int> vec2 = vec1; // vec2 是 vec1 的副本
  ```

- **移动构造**：创建一个 vector，它接管另一个 vector 的资源，不进行复制。

  ```cpp
  std::vector<int> vec1 = {1, 2, 3};
  std::vector<int> vec2 = std::move(vec1); // vec2 接管了 vec1 的资源
  ```

- **通过迭代器范围构造**：通过已有范围内的元素构造 vector。

  ```cpp
  复制int arr[] = {1, 2, 3};
  std::vector<int> vec(std::begin(arr), std::end(arr));
  ```

#### 赋值操作

- **赋值运算符**：将一个 vector 的内容赋值给另一个 vector。

  ```cpp
  vec = anotherVec;
  ```

- **移动赋值**：使用移动语义将一个 vector 的内容赋值给另一个，不进行复制。

  ```cpp
  复制
  vec = std::move(anotherVec);
  ```

#### 大小和容量操作

- **size()**：返回 vector 中的元素数量。

  ```cpp
  size_t size = vec.size();
  ```

- **resize()**：改变 vector 的大小，可以增大也可以减小，新元素将被默认初始化。

  ```cpp
  vec.resize(20);
  ```

- **capacity()**：返回 vector 目前分配的内存大小，即 vector 能容纳的元素数量而不重新分配内存。

  ```cpp
  size_t cap = vec.capacity();
  ```

- **reserve()**：改变 vector 分配的内存大小，使其至少能容纳指定数量的元素。

  ```cpp
  vec.reserve(100);
  ```

#### 元素访问

- **operator[]**：通过下标访问或修改元素。

  ```cpp
  int elem = vec[5]; // 获取下标为 5 的元素
  vec[5] = 10;      // 设置下标为 5 的元素为 10
  ```

- **at()**：通过下标访问元素，如果下标越界，会抛出异常。

  ```cpp
  int elem = vec.at(5);
  ```

- **front()**：访问第一个元素。

  ```cpp
  int frontElem = vec.front();
  ```

- **back()**：访问最后一个元素。

  ```cpp
  复制
  int backElem = vec.back();
  ```

#### 修改操作

- **push_back()**：在 vector 的末尾添加一个元素。

  ```cpp
  vec.push_back(20);
  ```

- **pop_back()**：移除 vector 最后一个元素。

  ```cpp
  vec.pop_back();
  ```

- **insert()**：在指定位置插入一个或多个元素。

  ```cpp
  vec.insert(vec.begin() + 1, 10); // 在下标为 1 的位置插入元素 10
  ```

- **erase()**：删除一个或多个元素。

  ```cpp
  vec.erase(vec.begin() + 1); // 删除下标为 1 的元素
  ```

- **clear()**：移除所有元素，使 vector 变为空。

  ```cpp
  vec.clear();
  ```

- **swap()**：交换两个 vector 的内容。

  ```cpp
  复制std::vector<int> anotherVec;
  vec.swap(anotherVec);
  ```

#### 特殊操作

- **emplace_back()**：在 vector 末尾构造并插入一个元素。

  ```cpp
  vec.emplace_back(20);
  ```

- **begin()/end()**：返回指向 vector 开始和结束的迭代器。

  ```cpp
  复制auto itBegin = vec.begin();
  auto itEnd = vec.end();
  ```

#### 排序和搜索

- **sort()**：对 vector 中的元素进行排序。

  ```cpp
  vec.sort(); // 默认按升序排序
  ```

- **binary_search()**：在有序 vector 中进行二分查找。**返回类型为bool型**，而不是元素的索引值

  ```cpp
  bool found = std::binary_search(vec.begin(), vec.end(), value);
  ```

### 从string到对应的vector\<string>

#### string中的元素依次存入vector\<string>

```cpp
string str="shdfhasdf";
vector<string> new_vector;
for(char c: str){
    new_vector.push_back(string(1,c))
}
```

#### string中的元素依次存入vector\<char>

```cpp
vector<char>char_vec;
for(char c: char_vec){
    char_vec.push_back(c);
}
```

### 求集合的交集

`set_intersection(a.begin(),a.end(),b.begin(),b.end(),back_inserter(result));`

上面的语句实现了求字符串a和b的交集，最终结果插入到字符串result中去，元素可以重复。使用此函数之前要保证a和b有序，因此在调用前应`sort(a.begin(),a.end());`b同理

经查阅资料，该函数返回类型可以是迭代器，`set_intersection(a.begin(),a.end(),b.begin(),b.end(),insert_iterator<vector<type>>(result,result.begin()));`



### 查询字符串中是否包含某字符

`if(str.find(val) != string::npos)`表示能够在字符串中找到val；而find()函数本身的返回值是val在str中的索引

### 思路拓展

以后遇到像只包含字母的情况，可以往开辟大小为26的数组空间来记录每个字母出现的频率。

## 4.24

二分查找既可以使用递归调用实现，也可以使用循环。最需要注意的是整体思路的选择，索引值的范围左边开还是闭and右边开还是闭？不同的选择得到的代码都会有差异，具体问题具体分析。

## 4.25

1. 对有序vector进行binary_search操作，返回的值是一个bool类型，而不是想当然的索引值。因此在尝试暴力的时候出错了。
2. vector中的remove函数得到的结果和双循环暴力破解得到的最后结果一样，都是把val移动到vect的末尾处而不是真正的删除，再结合erase函数删除尾部元素即可。这其中的逻辑是每一次使用了remove都会相应调用一次erase函数，因此不需要外部设置依据val个数的循环。
3. 如果已经获取要被删除的元素的索引值index，使用erase函数时的参数不能直接是index，而是`vec.begin()+index`。
4. 在对数组元素进行插入和删除操作时要记住插入/删除位点之后的所有元素都要一起移动，因此顺序表的性能差于链表，牵一发而动全身是很有可能的
5. C++中可以直接调用swap函数而不用重新定义
6. 感觉如果我没有学过/整理过C++vector类型的操作的化，我大概率会按照408数据结构编程题一样，进行双for循环暴力破解了

## 4.26

### sort函数

sort()函数一般情况下是等效于快速排序，时间复杂度o(nlogn)，在调用sort时，需要传入起始和结束。对vector类型进行排序，传入参数一般为`vec.begin()`和`vec.end()`；而对一个数组进行排序，传入参数一般为`arr`和`arr+arr.size()`。对vector类型使用sort后，顺序改变。除此之外还有一个可选的参数comp，要求传入一个bool类型。下面是C++ algorithm的API提供的示例：

```cpp
// sort algorithm example
#include <iostream>     // std::cout
#include <algorithm>    // std::sort
#include <vector>       // std::vector

bool myfunction (int i,int j) { return (i<j); }

struct myclass {
  bool operator() (int i,int j) { return (i<j);}
} myobject;

int main () {
  int myints[] = {32,71,12,45,26,80,53,33};
  std::vector<int> myvector (myints, myints+8);               // 32 71 12 45 26 80 53 33

  // using default comparison (operator <):
  std::sort (myvector.begin(), myvector.begin()+4);           //(12 32 45 71)26 80 53 33

  // using function as comp
  std::sort (myvector.begin()+4, myvector.end(), myfunction); // 12 32 45 71(26 33 53 80)

  // using object as comp
  std::sort (myvector.begin(), myvector.end(), myobject);     //(12 26 32 33 45 53 71 80)

  // print out content:
  std::cout << "myvector contains:";
  for (std::vector<int>::iterator it=myvector.begin(); it!=myvector.end(); ++it)
    std::cout << ' ' << *it;
  std::cout << '\n';

  return 0;
}
```

最后的一个参数可以传入bool型函数，也可以传入结构体。api中对comp形参的解释：“二进制函数，接受范围中的两个元素作为参数，并返回一个可转换为 bool 的值。返回值表示作为第一个参数传递的元素是否被认为在其定义的特定严格弱排序中排在第二个元素之前。函数不得修改其任何参数。该参数可以是函数指针，也可以是函数对象。”

CSDN上对sort函数的详细介绍：[C++ sort()排序详解](https://blog.csdn.net/qq_41575507/article/details/105936466)。总的来说sort函数功能强大，不需要我们再去手动编写相应的排序算法，也可以很方便地自定义排序方式。

### vector和数组

数组是静态编译的，一旦创建，其大小就不可改变。可以通过下标来访问和修改对应的元素。在内存上连续分配，所有元素必须是相同类型的。

vector容器可以理解为一个动态数组，可以根据需要自动调整大小，可以插入和删除元素。支持随机访问。可以通过索引值来访问其中的任何元素。当元素超过容量会自动分配新的内存并复制现有元素过去。

数组转vector：

```cpp
int main(){
    int arr[4]={1,2,3,4};
    vector<int> vec(arr,arr+arr.size());//欸二哥参数也可以是arr+sizeof(array)
}
```

也可先定义vector和元素个数，再进行拷贝，使用函数memcpy：

```cpp
vector<int> vec(n);
memcpy(&vec[0],array,sizeof(array));
```

vector转数组：

```python
memcpy(arr,&vec[0],vec.size()*sizeof(vec[0]));
```

三个参数：第一个是已经声明的空数组；第二个是vector中的起始元素的引用；第三个是拷贝长度的大小

### 数学运算

次方：`pow(a,b)`返回$a^b$

开方：`sqrt(a)`或者`pow(a,0.5)`返回$\sqrt a$

绝对值：`abs(a)`返回$|a|$​

求余：`a%b`

指数：`exp(a)`返回$e^a$

对数：`log(a)`返回$lna$

## 4.27

### vector中的find_if函数

C++标准库中的 `find_if` 算法是用于搜索容器中满足特定条件的第一个元素的函数。这个函数是模板化的，可以用于多种容器，如数组、向量（`std::vector`）、列表（`std::list`）、双端队列（`std::deque`）等。

#### 函数原型

`find_if` 函数的原型如下：

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator find_if (ForwardIterator first, ForwardIterator last, Predicate pred);
```

- `ForwardIterator`：迭代器类型，指向容器中的元素。
- `first` 和 `last`：迭代器，分别指向搜索范围的开始和结束（不包括 `last`）。
- `Predicate` `pred`：是一个可调用的模板参数，可以是一个函数、函数对象或lambda表达式，用于定义搜索的条件。

#### 工作机制

`find_if` 从 `first` 开始迭代，直到 `last`，对每个元素应用 `pred` 函数。一旦找到一个元素使得 `pred` 返回 `true`，`find_if` 就会停止搜索并返回指向该元素的迭代器。如果直到搜索结束都没有元素满足条件，`find_if` 将返回 `last`。

#### 使用示例

假设我们有一个整型向量，我们想要找到**第一个**大于10的元素：

```cpp
#include <algorithm> // for std::find_if
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v = {3, 7, 5, 10, 20, 4};
    
    // 使用 lambda 表达式作为 Predicate
    auto it = std::find_if(v.begin(), v.end(), [](int i) {
        return i > 10;
    });
    
    if (it != v.end()) {
        std::cout << "First element greater than 10 is " << *it << '\n';
    } else {
        std::cout << "No element greater than 10\n";
    }
    
    return 0;
}
```

在这个例子中，我们使用了一个 lambda 表达式作为 `find_if` 的第三个参数，定义了搜索条件：找到一个整数，它大于10。然后，我们检查返回的迭代器 `it` 是否不等于 `v.end()`，以确定是否找到了这样的元素。

#### 注意事项

- `find_if` 不修改容器或它的元素。
- 如果容器为空，或者没有元素满足条件，`find_if` 返回的迭代器等于 `last`。
- `find_if` 是线性时间复杂度的算法，即运行时间与容器中元素的数量成正比。

`find_if` 是C++算法库中非常有用的工具，它允许开发者以声明式的方式搜索容器中的元素，而不必显式编写循环。

### vector实现对应位置元素的加减操作

一种是暴力循环逐个位进行操作，另一种是借助`std::transform`函数来进行操作：

```cpp
#include <algorithm> // for std::transform

// ...

std::vector<int> result(vec1.size());
std::transform(vec1.begin(), vec1.end(), vec2.begin(), result.begin(),
                std::minus<int>());
```

如果结果返回到某个vector中，只用把result改成对应容器名称。

### 删除vector类型数据

删去首位元素：`vec.erase(vec.begin())`

删去末尾元素：`vec.pop_back()`或`vec.erase(vec.end())`

## 4.28

### 用vector定义多维数组

`vector<vector<int>>result(n,vector<int>(n,0))`生成n*n的二维数组矩阵，初始元素均置为0

vector中的`size`函数用于查询动态数组vector中有多少个有效数据（大范围的）；而`capacity`函数用于查询它的容量大小（最多可以存放多少数据）

例如，`result.size()`返回的结果是n，代表result中有多少行；`result[0].size()`返回的结果是n，代表列数

二维数组添加一行：`vector<int> in_row(n,2)`先初始化一个数组，包含n个元素且全为2，`result.insert(result.begin()+2,in_row);`在第二行和第三行中间插入一行元素全为2.

二维数组添加一列：`for(int i=0;i<result.size();i++){result[i].insert(result.begin()+2,9);}`实现在第二列和第三列之间插入一列全为9的元素。

二维数组删除一行：`result.erase(result.begin()+2,result.begin()+3);`用于删除第三行元素（0，1，2->被删除）

二维数组删除一列：`for (int i =0; i<result.size() ; i++){result[i].erase(a[i].begin()+2,a[i].begin()+3);}`用于删除第三列元素。

### 多维数组问题一定要搞清边界的判断

### 常见报错

`heap-buffer-overflow on address`报错是由于边界的设置有误，访问数组时发生了越界错误

` runtime error: reference binding to misaligned address`报错原因是数组越界，需要加入判断数组是否为空或者堆栈是否为空的语句。例如当二维数组为空，而访问`matrix[0].size()`就会这样报错

### goto语句

设置标签值和冒号，goto选择标签。

例如：

```cpp
cout<<c;
flag:
cout<<a;
cout<<b;
goto flag;
```

goto语句慎用。良好的goto语句可以用于从深层的嵌套循环中跳出程序。

## 4.29

### 链表的定义和初始化

定义：

```cpp
// 单链表
struct ListNode {
    int val;  // 节点上存储的元素
    ListNode *next;  // 指向下一个节点的指针
    ListNode(int x) : val(x), next(NULL) {}  // 节点的构造函数
};
```

其中第五行是节点的构造函数。可以写可以不写，因为C++默认生成一个构造函数。但是默认的构造函数不能再初始化的时候给变量赋值。

```cpp
ListNode* head = new ListNode(5);
//第一行代码如果自己定义了构造函数的话是可行的
ListNode* head = new ListNode();
head->val = 5;
//这两行代码用于没有定义构造函数，执行先定义再赋值
```

### 链表相关报错

`runtime error: member access within null pointer of type 'ListNode' (solution.cpp)`报错是因为试图访问ListNode空指针类型的成员。问题在于当移除的元素位于链表最后一个时，此时cur指向最后一个结点，cur->next为空，而访问cur->nex->next就是访问空指针的成员变量了。

`ERROR: AddressSanitizer: alloc-dealloc-mismatch (operator new vs free) on 0x502000000090`则是因为new和delete或者malloc和free没有成对使用

`ERROR: AddressSanitizer: heap-use-after-free on address 0x502000000278 at pc 0x558e2f2d2103 bp 0x7ffdc1baf5e0 sp 0x7ffdc1baf5d8`内存错误"heap-use-after-free"，这是因为在C++中，当使用delete关键字释放对象的内存后，该对象仍然会保留指向已经被释放内存的指针。这个指针称为悬挂指针（Dangling Pointer）。如果我们试图访问已经被释放的内存，就会触发"heap-use-after-free"错误。

### 链表中NULL和Nullptr的区别

用Null表示空指针是C语言中遗留下来的传统，但在C++中可能会引起问题，因此在C++11中引入了nullptr表示空指针，如果要在C++中表示空指针，那么使用nullptr而不是Null.。

### 链表中的new和delete操作对

在C++中，`new` 和 `delete` 操作符是对动态内存分配和管理的基本工具。它们允许程序员在堆上分配和释放内存，这是一块在程序运行时可以动态增长和缩小的内存区域。链表是展示 `new` 和 `delete` 如何工作的一个很好的例子，因为链表的每个节点通常都是动态分配的。

#### new 操作符

`new` 是一个运算符，用于在堆上分配一块内存。当你使用 `new` 分配内存时，它会：

1. 找到足够大的内存块来存储你的数据。
2. 初始化这块内存（通常填充为零）。
3. 返回一个指向这块内存的指针。

对于构造对象，`new` 还会调用对象的构造函数来初始化对象。

#### delete 操作符

`delete` 用于释放之前使用 `new` 分配的内存。当你使用 `delete` 时，它会：

1. 调用对象的析构函数（如果指针是指向一个对象的）。
2. 释放指向的内存块，使其可以被未来的 `new` 调用重新使用。

#### 使用 new 和 delete 的示例

假设我们有一个简单的链表节点类 `ListNode`：

```cpp
class ListNode {
public:
    int value;
    ListNode* next;

    ListNode(int val) : value(val), next(nullptr) {}
    ~ListNode() {
        // 清洁工作，比如删除指向下一个节点的指针
        next = nullptr;
    }
};
```

我们可以使用 `new` 和 `delete` 来创建和销毁链表：

```cpp
int main() {
    // 使用 new 分配并构造一个链表节点
    ListNode* head = new ListNode(1);

    // 创建更多的节点并构建链表
    head->next = new ListNode(2);
    head->next->next = new ListNode(3);

    // ... 链表操作 ...

    // 使用 delete 释放链表节点
    delete head->next->next; // 删除第三个节点
    head->next = nullptr;    // 断开链接，防止访问已删除的内存
    delete head->next;       // 删除第二个节点
    delete head;              // 删除第一个节点

    return 0;
}
```

#### 注意事项

- **成对使用**：每次使用 `new` 分配内存后，都应该有相应的 `delete` 来释放内存，以避免内存泄漏。
- **析构函数**：如果对象有析构函数，`delete` 会调用它。这对于管理资源（如文件句柄、套接字等）非常重要。
- **悬挂指针**：释放内存后，原始指针应设置为 `nullptr`，以避免悬挂指针问题。
- **new 异常**：如果内存分配失败，`new` 会抛出一个 `std::bad_alloc` 异常。你应该总是在使用 `new` 的地方考虑异常安全性。
- **delete[] 和 new[]**：如果你使用 `new[]` 分配了一个数组，应该使用 `delete[]` 来释放它，以确保正确调用析构函数。

正确使用 `new` 和 `delete` 对于避免内存泄漏和其他动态内存管理问题至关重要。在现代C++编程中，智能指针（如 `std::unique_ptr` 和 `std::shared_ptr`）被推荐用于自动管理动态分配的内存，减少内存管理错误。

### 链表中的malloc和free操作对

在C++中，`malloc` 和 `free` 是C语言标准库中的函数，它们用于动态内存分配和管理。虽然C++提供了自己的 `new` 和 `delete` 操作符来分配和释放动态内存，但 `malloc` 和 `free` 仍然可以在C++程序中使用，尤其是当与C语言代码交互或者在一些特定的、需要 `malloc` 和 `free` 的上下文中。

#### malloc 函数

`malloc` 函数是C标准库中的一个函数，它用于在堆上分配一块指定大小的内存。它的原型定义在 `<cstdlib>` 头文件中：

```cpp
void* malloc(size_t size);
```

- `size_t size`：要分配的内存大小，单位是字节。
- 返回值：如果分配成功，返回一个指向分配内存的起始地址的空指针；如果失败，返回 `nullptr`。

#### free 函数

`free` 函数用于释放之前使用 `malloc` 或 `calloc` 分配的内存。它的原型也定义在 `<cstdlib>` 头文件中：

```cpp
void free(void* ptr);
```

- `void* ptr`：指向要释放内存的指针。
- 无返回值。

#### 使用 malloc 和 free 的示例

```cpp
#include <cstdlib> // 包含 malloc 和 free 的定义
#include <iostream>

int main() {
    // 分配内存来存储一个整数
    int* p = static_cast<int*>(malloc(sizeof(int)));

    if (p == nullptr) {
        std::cerr << "Memory allocation failed." << std::endl;
        return 1;
    }

    // 使用分配的内存
    *p = 10;
    std::cout << "Value at p: " << *p << std::endl;

    // 释放内存
    free(p);
    p = nullptr; // 将指针设置为 nullptr，避免悬挂指针

    return 0;
}
```

#### 注意事项

- **类型转换**：`malloc` 返回 `void*` 类型，使用前需要转换为适当的指针类型。
- **构造函数和析构函数**：与 `new` 和 `delete` 不同，`malloc` 不会自动调用对象的构造函数或析构函数。如果分配的是对象的内存，需要手动调用构造函数和析构函数。
- **内存泄漏**：使用 `malloc` 分配的内存必须匹配地使用 `free` 来释放，否则会导致内存泄漏。
- **错误处理**：`malloc` 在内存分配失败时返回 `nullptr`，使用前应检查返回值。
- **跨语言交互**：`malloc` 和 `free` 常用于C和C++代码的交互，因为它们是C语言标准的一部分，而C++的 `new` 和 `delete` 不是。

#### 与 new 和 delete 的比较

- **构造和析构**：`new` 和 `delete` 会自动处理对象的构造和析构，而 `malloc` 和 `free` 不会。
- **类型安全**：`new` 和 `delete` 是类型安全的，它们确保指针类型与分配的内存类型匹配；`malloc` 和 `free` 需要显式转换指针类型。
- **异常安全性**：`new` 在分配失败时会抛出异常，而 `malloc` 只会返回 `nullptr`。

**在C++中，推荐使用 `new` 和 `delete` 来分配和释放对象的内存**，因为它们与C++的异常处理和类型系统更加集成。然而，在某些特殊的、需要与C代码交互或者需要手动管理内存大小的情况下，`malloc` 和 `free` 仍然是有用的工具。

## 4.30

### C++类中的构造函数

在C++中，构造函数是一种特殊的成员函数，用于创建类的对象时初始化对象的状态。构造函数的名字必须与类名完全相同，它没有返回类型，甚至连 `void` 也不是。

#### 构造函数的特点：

1. **同名性**：构造函数的名称必须与类名相同。
2. **无返回类型**：构造函数没有返回类型，包括 `void`。
3. **自动调用**：每当创建类的新对象时，构造函数会自动调用。
4. **初始化成员**：构造函数可以用于初始化对象的非静态成员变量。
5. **初始化基类**：在派生类中，构造函数还会调用基类的构造函数来初始化继承的部分。
6. **重载**：构造函数可以被重载，即一个类可以有多个构造函数，它们有不同的参数列表。

#### 构造函数的类型：

1. **默认构造函数**：没有参数的构造函数，如果用户没有提供任何构造函数，编译器会提供一个默认构造函数。
2. **参数化构造函数**：有一个或多个参数的构造函数，用于自定义初始化。
3. **拷贝构造函数**：使用同一类的对象作为参数的构造函数，用于创建一个对象的副本。

#### 构造函数的示例：

```cpp
class MyClass {
public:
    // 默认构造函数
    MyClass() {
        std::cout << "Default constructor called." << std::endl;
    }
    
    // 参数化构造函数
    MyClass(int value) : data(value) {
        std::cout << "Parameterized constructor called." << std::endl;
    }
    
    // 拷贝构造函数
    MyClass(const MyClass& other) : data(other.data) {
        std::cout << "Copy constructor called." << std::endl;
    }
    
    // 数据成员
    int data;
};

int main() {
    MyClass obj1; // 调用默认构造函数
    MyClass obj2(10); // 调用参数化构造函数
    MyClass obj3 = obj2; // 调用拷贝构造函数
    
    return 0;
}
```

#### 注意事项：

- **不在堆上分配内存**：构造函数不应该在堆上分配内存，因为 `new` 操作符已经为对象分配了内存。
- **不返回对象**：构造函数不应该返回任何值，包括 `void`。
- **对象初始化**：构造函数的主要目的是初始化对象，确保对象在首次使用时处于有效状态。
- **析构函数**：与构造函数相对的是析构函数，它在对象生命周期结束时自动调用，用于清理资源。

构造函数是C++面向对象编程的核心概念之一，它们为类的实例提供了一种初始化的方式。正确地设计和使用构造函数对于创建健壮和易于维护的类至关重要。

### C++同一个类中可调用的公共元素

在C++中，类中的成员（包括变量和函数）可以按照它们的访问权限被分为三类：公共（public）、保护（protected）和私有（private）。如果一个成员被声明为公共的，那么它可以在以下情况中被调用：

1. **类的内部**：类的公共成员可以在类的任何成员函数中被直接访问，无论这些成员函数是公共的、保护的还是私有的。

2. **同一个对象的其他成员函数**：一个对象的公共成员可以从该对象的任何非静态成员函数中被访问。

3. **友元函数**：如果一个函数被声明为类的友元（friend），那么它可以访问类的所有非私有成员，就像它们是类的公共成员一样。

4. **类的外部**：在类的外部，只能通过对象来访问公共成员，并且只能通过成员访问操作符（`.` 或 `->`）。

5. **派生类**：如果基类中的成员被声明为公共的，那么在派生类中也可以访问这些成员（除非派生类通过访问说明符改变了对这些成员的访问权限）。

6. **构造函数和析构函数**：即使它们是私有的或保护的，也可以在类的外部通过相应的构造和析构调用来访问。

#### 示例

```cpp
class MyClass {
public:
    int publicData;  // 公共数据成员
    void publicFunc() {}  // 公共成员函数

protected:
    int protectedData;  // 保护数据成员

private:
    int privateData;  // 私有数据成员

    void privateFunc() {}  // 私有成员函数
};

class DerivedClass : public MyClass {
public:
    void showPublicData() {
        publicData = 10;  // 派生类可以访问基类中公共的成员
    }
};

int main() {
    MyClass obj;
    obj.publicFunc();  // 调用公共成员函数

    // obj.protectedData = 20;  // 错误：protected成员在类外部不可见
    // obj.privateData = 30;     // 错误：private成员在类外部不可见

    DerivedClass dObj;
    dObj.showPublicData();  // 正确：派生类可以访问基类中公共的成员

    // dObj.protectedData = 20;  // 错误：即使在派生类中，protected成员也不能从外部访问

    return 0;
}
```

在上述示例中，`MyClass` 有三个访问权限不同的数据成员和成员函数。在 `DerivedClass` 中，可以访问继承自基类的公共成员，但不能直接访问保护或私有成员。然而，`DerivedClass` 中的成员函数可以访问从基类继承来的保护成员。

需要注意的是，即使成员函数是公共的，如果它们试图访问类的私有成员或保护成员，它们也必须遵循类的访问控制规则。

### C++类中的this指针

在C++中，`this` 是一个特殊的指针，它被自动定义在每一个**非静态成员函数**中。`this` 指针**指向调用成员函数的那个对象**，即它**指向当前对象的实例**。这个意思是说如果在类中调用了this指针，则是已经实例化过的对象的相关值进行访问和修改。

值得一提的是在官方给出的单链表解法中，只有在构造函数中调用了this指针

#### 用途

1. **区分参数和成员变量**：当成员变量和参数同名时，可以使用 `this` 指针来区分它们。

2. **指针传递**：可以将 `this` 指针传递给函数，以允许函数直接修改对象的状态。

3. **初始化列表中使用**：在构造函数的初始化列表中，`this` 指针可以用来明确成员初始化的顺序。

4. **返回对象本身**：在成员函数中，可以使用 `this` 返回当前对象的指针或引用。

5. **在嵌套类中**：如果有一个嵌套类，`this` 指针可以指向外部类的实例。

#### 示例

```cpp
class MyClass {
    int value;

public:
    MyClass(int v) : value(v), ptr(this) {}

    void SetValue(int v) {
        this->value = v; // 使用 this 指针区分成员变量和参数
    }

    int GetValue() const {
        return value;
    }

    // 返回对象本身的引用
    MyClass& GetThis() {
        return *this;
    }

    // 成员变量ptr指向同一个对象的this指针
    MyClass* ptr;
};

int main() {
    MyClass obj(10);
    obj.SetValue(20);
    std::cout << obj.GetValue() << std::endl; // 输出 20

    MyClass& ref = obj.GetThis();
    ref.SetValue(30);
    std::cout << obj.GetValue() << std::endl; // 输出 30

    return 0;
}
```

#### 注意事项

- `this` 指针在静态成员函数中是不可用的，因为静态成员函数不与任何特定对象实例相关联。

- `this` 指针通常是 `const` 的，这意味着你不能修改指向的对象。但是，如果你有一个非 `const` 成员函数，`this` 指针也不是 `const`，允许你修改对象的状态。

- 在多态类层次结构中，`this` 指针的类型是当前对象的静态类型，即使调用的方法可能是从基类继承的虚函数。

- `this` 指针**在构造和析构期间都是有效的**，即使在这些时候对象可能还没有完全构造或已经完全销毁。

- 在某些编译器优化中，`this` 指针可能被优化掉，因此不建议在程序中直接依赖 `this` 指针的值。

通过使用 `this` 指针，你可以编写更清晰和更高效的代码，特别是在处理具有同名成员和参数的情况时。

### C++结构体

在C++中，结构体（`struct`）是一种创建自定义数据类型的方式，它允许将不同的数据项组合成一个单一的数据结构。结构体在C++中非常灵活，它们可以包含数据成员（变量）和成员函数（方法）。

#### 定义结构体

结构体使用 `struct` 关键字定义，可以包含数据成员和成员函数。以下是定义结构体的基本语法：

```cpp
struct StructureName {
    // 数据成员
    int data_member;
    double another_member;
    
    // 成员函数
    void member_function() {
        // 函数体
    }
    
    // 可以有构造函数
    StructureName(int value) : data_member(value) {}
};
```

#### 初始化结构体

结构体可以像类一样初始化，但它们默认情况下所有成员都是公共的（public），这意味着它们可以直接访问，不需要任何特定的访问修饰符。

```cpp
struct Point {
    int x, y;
};

Point p = {1, 2}; // 初始化结构体变量p
```

#### 使用结构体

结构体可以像类一样使用，但它们通常不用于定义复杂的逻辑，而是用于创建简单的数据容器。

```cpp
struct Point {
    int x, y;
    
    Point(int x_val, int y_val) : x(x_val), y(y_val) {}
    
    void print() const {
        std::cout << "Point(" << x << ", " << y << ")" << std::endl;
    }
};

int main() {
    Point p(3, 4);
    p.print(); // 输出: Point(3, 4)
    
    return 0;
}
```

#### 结构体与类的区别

- **默认访问权限**：结构体的所有成员默认都是公共的，而类的所有成员默认是私有的。
- **成员访问**：由于默认访问权限的不同，结构体的成员可以直接访问，而类的私有成员需要通过公共的接口（如公共成员函数）来访问。
- **惯用法**：在C++中，结构体通常用于数据聚合，而类用于具有数据和方法的组合。

#### 具名返回值优化（NRVO）

在C++中，返回一个结构体或类对象时，编译器可能会使用一种称为具名返回值优化的技术来避免临时对象的创建。这意味着，返回的结构体或类对象可能直接在目标位置创建，而不是先在堆栈上创建后再复制。

#### 总结

结构体是C++中一种基本的数据结构，它允许你将不同的数据项组合成一个单一的实体。它们在C++中非常有用，尤其是在需要创建简单的数据容器时。尽管结构体和类在很多方面相似，但它们在默认访问权限和惯用法上有所不同。

### C++结构体中的构造函数

以该结构体为例

```cpp
struct ListNode{
    int val;
    ListNode *next;
    ListNode(int x):val(x),next(nullptr){}
};
```

在C++中，这段代码定义了一个名为 `ListNode` 的结构体，它通常用于创建链表中的节点。这个结构体包含了一个整型的数据成员 `val`，一个指向同类型结构体指针的成员 `next`，以及一个构造函数。

下面是对 `ListNode` 结构体及其构造函数的详细介绍：

#### 结构体定义

```cpp
struct ListNode {
    int val;    // 节点存储的数据
    ListNode *next; // 指向链表中下一个节点的指针
    ListNode(int x) : val(x), next(nullptr) {} // 构造函数
};
```

#### 成员变量：

1. `int val`：这是一个基本数据类型的成员变量，用于存储节点的值。在链表中，每个节点通常存储一个值，并且包含一个指向下一个节点的指针。

2. `ListNode *next`：这是一个指向 `ListNode` 类型的指针，它指向链表中的下一个节点。在链表的末尾节点中，这个指针通常被设置为 `nullptr`，表示没有后续节点。

#### 构造函数：

构造函数 `ListNode(int x)` 是一个特殊的成员函数，用于在创建 `ListNode` 对象时**初始化对象的状态**。它接受一个整型参数 `x`，并**使用成员初始化列表来初始化结构体的成员变量**。

- `ListNode(int x)`：构造函数的声明，它接受一个整型参数 `x`。

- `: val(x), next(nullptr)`：这是成员初始化列表，它在构造函数体执行之前被处理。它用于初始化 `ListNode` 的两个成员变量。

  - `val(x)`：这将构造函数的参数 `x` 传递给 `val` 成员，初始化节点的值。
  - `next(nullptr)`：这将空指针字面量 `nullptr`（在C++11及以后的版本中）赋值给 `next` 成员，表示初始时这个节点没有指向任何后续节点。

#### 构造函数的执行流程：

1. 当你使用 `new` 操作符和构造函数 `ListNode` 创建一个新节点时，如 `ListNode *node = new ListNode(10);`，构造函数被调用。

2. 成员初始化列表 `: val(x), next(nullptr)` 首先执行，初始化 `val` 为传递给构造函数的值 `x`，初始化 `next` 为 `nullptr`。

3. 然后，构造函数体 `{}` 执行，但由于这里是一个空的构造函数体，所以实际上不执行任何操作。

4. 最终，一个 `ListNode` 类型的节点被创建，其值被设置为 `10`，并且 `next` 指针被初始化为 `nullptr`。

这个构造函数的设计使得 `ListNode` 类型的对象在创建时就可以立即被设置为链表中的一个有效节点。这是链表操作中非常常见的模式。

## 5.1

拓宽了思路。对单链表的逆置不再局限于最熟悉和稳妥的断链头插法了。

## 5.2

不管是递归还是迭代，都拓宽了我的思路。对于迭代，我的提升点是多考虑辅助节点，从整体上考虑问题，不能急。比如参考答案里面给的方法是逐个组进行调换操作，借助组前指针tmp来实现链表的链接；而我的想法太过跳跃，想要一口吃个胖子，直接就让一个调整好的组的next指向下一个组的第二个元素，思路上跳跃导致编码上的不便。其次就是递归。在我自己进行解答的时候，也考虑过递归，但是我当时还是局限于前文中提到的方法。递归不会写，说白了是倒着考虑问题，总感觉很别扭，脑子转不过来这个弯。

## 5.3

链表解题经典三板斧，哑巴节点，栈，快慢指针。

## 5.4

### C++初始化栈

在C++中，栈（Stack）是一种遵循后进先出（LIFO，Last In First Out）原则的线性数据结构。C++标准库中并没有直接提供一个名为“Stack”的容器，但是可以使用 `std::vector`、`std::deque` 或 `std::list` 等容器来模拟栈的行为。以下是使用这些容器初始化栈的一些方法：

#### 使用 `std::vector`

```cpp
#include <vector>

std::vector<int> stack;
// 初始化一个空栈

// 推入元素
stack.push_back(1);
stack.push_back(2);
stack.push_back(3);

// 弹出元素
int top_element = stack.back();
stack.pop_back();
```

#### 使用 `std::deque`

```cpp
#include <deque>

std::deque<int> stack;
// 初始化一个空栈

// 推入元素
stack.push_back(1);
stack.push_back(2);
stack.push_back(3);

// 弹出元素
int top_element = stack.back();
stack.pop_back();
```

#### 使用 `std::list`

```cpp
#include <list>

std::list<int> stack;
// 初始化一个空栈

// 推入元素
stack.push_back(1);
stack.push_back(2);
stack.push_back(3);

// 弹出元素
int top_element = stack.back();
stack.pop_back();
```

在上述所有示例中，我们使用了容器的 `push_back()` 方法来模拟栈的“推入”操作，使用 `pop_back()` 方法来模拟“弹出”操作。这是因为 `std::vector`、`std::deque` 和 `std::list` 都支持在容器的末尾进行快速的插入和删除操作。

#### 注意事项

- 虽然 `std::vector`、`std::deque` 和 `std::list` 可以模拟栈的行为，但它们的性能特点不同。例如，`std::vector` 在随机访问方面更快，但插入和删除操作可能需要更多时间（如果需要重新分配内存）。相比之下，`std::list` 在插入和删除操作上更快，但不支持随机访问。
- 标准库中的 `std::stack` 适配器也可以用来实现栈，它使用其他标准容器作为底层容器。

#### 使用 `std::stack` 适配器

```cpp
#include <stack>
#include <vector>

std::stack<int, std::vector<int>> stack(std::vector<int>());
// 使用 vector 作为底层容器初始化一个空栈

// 推入元素
stack.push(1);
stack.push(2);
stack.push(3);

// 弹出元素
int top_element = stack.top();
stack.pop();
```

在这个示例中，我们使用了 `std::stack` 适配器，它模板化地使用了 `std::vector` 作为底层容器。`std::stack` 只提供了有限的操作，如 `push()`、`pop()` 和 `top()`，这些操作分别对应栈的推入、弹出和顶部元素访问。

选择哪种方法取决于你的具体需求，包括对性能的要求以及对底层容器特性的偏好。

栈的正统在`# include <stack>`

### C++对栈的操作

在C++中，栈（Stack）是一种常用的数据结构，它遵循后进先出（LIFO，Last In First Out）的原则。虽然C++标准模板库（STL）中没有直接提供名为“Stack”的容器，但是可以使用 `std::stack` 适配器，它基于其他容器（如 `std::vector`、`std::deque` 或 `std::list`）来实现栈的功能。

以下是使用 `std::stack` 适配器对栈进行操作的基本方法：

#### 包含必要的头文件

```cpp
#include <stack>
```

#### 初始化栈

```cpp
std::stack<int> myStack;
```

#### 推入元素（入栈）

```cpp
myStack.push(50); // 推入元素50
myStack.push(100); // 推入元素100
```

#### 弹出元素（出栈）

```cpp
if (!myStack.empty()) {
    int topElement = myStack.top(); // 获取栈顶元素
    myStack.pop(); // 弹出栈顶元素
}
```

需要注意一点是在C++的栈中，使用`pop`函数返回的是void类型，即该函数只完成把栈顶元素出栈操作，而不进行任何返回。若想获取并弹出栈顶元素，则必须先用`top`函数获取栈顶元素再进行`pop`出栈操作。

#### 获取栈顶元素

```cpp
if (!myStack.empty()) {
    int topElement = myStack.top();
    // 可以对topElement进行操作，但不能从栈中移除
}
```

#### 检查栈是否为空

```cpp
bool isEmpty = myStack.empty(); // 如果栈为空，则返回true
```

#### 获取栈的大小

```cpp
size_t size = myStack.size(); // 获取栈中元素的数量
```

#### 清空栈

```cpp
while (!myStack.empty()) {
    myStack.pop(); // 循环弹出所有元素，清空栈
}
```

#### 示例

```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<int> myStack;

    // 推入元素
    myStack.push(1);
    myStack.push(2);
    myStack.push(3);

    // 弹出元素
    while (!myStack.empty()) {
        int topElement = myStack.top();
        std::cout << "Popped: " << topElement << std::endl;
        myStack.pop();
    }

    return 0;
}
```

#### 注意事项

- `std::stack` 是一个容器适配器，它只提供了有限的操作集合，主要关注栈的基本操作。
- 由于 `std::stack` 是后进先出的，所以不支持随机访问，也不能直接访问除了顶部之外的其他元素。
- `std::stack` 的底层容器的选择会影响其性能特性。例如，基于 `std::vector` 的栈在随机访问时更快，而基于 `std::deque` 的栈可能在频繁的入栈和出栈操作时更高效。

使用 `std::stack` 适配器可以方便地在C++程序中实现栈的操作，同时保持代码的可读性和简洁性。

### C++中的swap函数

在C++中，`swap` 函数是一个非常有用的标准库函数，用于交换两个值或两个容器中的内容。它提供了一种高效且类型安全的方式来交换数据。

#### 标准库中的 `swap` 函数

C++标准库提供了一个通用的 `swap` 函数，它是一个模板函数，可以用于交换大多数类型的值。它的定义在 `<utility>` 头文件中。

**交换值**

```cpp
#include <utility>

void swap(ValueType& a, ValueType& b);
```

这里，`ValueType` 可以是大多数类型的值，包括内置类型、指针、某些用户定义的类型等。标准库中的 `swap` 函数通常实现得非常高效，它利用了类型特定的交换语义，以确保交换操作是安全的并且具有最佳性能。

**示例**

```cpp
#include <iostream>
#include <utility>

int main() {
    int x = 10;
    int y = 20;
    
    std::swap(x, y); // 交换 x 和 y 的值
    
    std::cout << "x: " << x << ", y: " << y << std::endl; // 输出 x: 20, y: 10
    
    return 0;
}
```

#### 交换容器内容

对于容器类型，如 `std::vector`、`std::string` 等，C++标准库也提供了 `swap` 函数的特化版本，这些特化版本通常比通用版本的 `swap` 更高效，因为它们利用了容器的内部实现细节。

**示例**

```cpp
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> vec1 = {1, 2, 3};
    std::vector<int> vec2 = {4, 5, 6};
    
    std::swap(vec1, vec2); // 交换两个向量的内容
    
    // vec1 现在包含 4, 5, 6，而 vec2 包含 1, 2, 3
    
    return 0;
}
```

#### 用户定义类型的 `swap` 函数

对于用户定义的类型，你可以提供自己类型的 `swap` 函数，以确保交换操作是安全的并且符合类型特定的需求。这通常通过定义在类型内部的 `friend` 函数来实现。

**示例**

```cpp
class MyClass {
public:
    MyClass(int v) : value(v) {}
    
    friend void swap(MyClass& first, MyClass& second) {
        // 交换两个 MyClass 对象的内部状态
        std::swap(first.value, second.value);
    }
    
private:
    int value;
};

int main() {
    MyClass obj1(10);
    MyClass obj2(20);
    
    swap(obj1, obj2); // 使用自定义的 swap 函数交换 obj1 和 obj2
    
    return 0;
}
```

#### 注意事项

- 使用标准库的 `swap` 函数通常是交换值或容器内容的首选方法，因为它是类型安全的，并且通常实现得非常高效。
- 为了使 `swap` 函数可交换任何两个元素，它应该满足一些基本的要求，如不抛出异常，并且其复杂度应该是最优的。
- 在某些情况下，如果类型具有昂贵的复制成本，可能会实现一个移动友好的 `swap` 函数，它利用了右值引用和移动语义来提高性能。

`swap` 函数是C++中实现资源有效利用和类型安全交换的重要工具。

### C++中的`unordered_set`哈希集合

在C++中，`unordered_set` 是标准模板库（STL）中的一个容器类，它存储一定数量的唯一元素，并保证插入和访问的高效性。`unordered_set` 是基于哈希表实现的，因此它的元素是以散列的方式存储的，这使得它在查找、插入和删除操作上都能提供平均时间复杂度为 O(1) 的性能。

#### 基本用法

1. **包含头文件**：
   要使用 `unordered_set`，首先需要包含头文件 `<unordered_set>`。

   ```cpp
   #include <unordered_set>
   ```

2. **声明和初始化**：
   声明一个 `unordered_set` 容器，可以指定元素类型和（可选的）初始容量。

   ```cpp
   std::unordered_set<int> mySet;
   ```

   或者使用初始化列表：

   ```cpp
   std::unordered_set<int> mySet = {1, 2, 3, 4};
   ```

3. **元素插入**：
   使用 `insert` 方法向 `unordered_set` 中添加元素。

   ```cpp
   mySet.insert(5);
   ```

4. **元素查找**：
   使用 `find` 方法查找元素是否存在。

   ```cpp
   if (mySet.find(3) != mySet.end()) {
       std::cout << "3 is in the set." << std::endl;
   } else {
       std::cout << "3 is not in the set." << std::endl;
   }
   ```

5. **检查元素是否存在**

   使用`count`函数，语法如下：

   ```cpp
   size_t count(const Key& key) const;
   ```

   这里，`Key` 是键的类型，`size_t` 是无符号整数类型，用于表示大小或计数。

   ```python
   size_t countResult=mySet.count(val);
   ```

   返回size_t类型的无符号整数，表示在哈希表中val存在的个数。

6. **元素删除**：
   使用 `erase` 方法删除一个元素。

   ```cpp
   mySet.erase(mySet.find(3)); // 删除元素3
   ```

7. **遍历**：
   使用迭代器遍历 `unordered_set`。

   ```cpp
   for (auto it = mySet.begin(); it != mySet.end(); ++it) {
       std::cout << *it << " ";
       // it->first返回key
       // it->second返回val
   }
   ```
   
8. **大小和是否为空**：
   使用 `size()` 方法获取 `unordered_set` 中元素的数量，使用 `empty()` 方法检查它是否为空。

   ```cpp
   std::cout << "Set size: " << mySet.size() << std::endl;
   std::cout << "Set is empty? " << (mySet.empty() ? "Yes" : "No") << std::endl;
   ```

#### 注意事项

- **唯一性**：`unordered_set` 中的所有元素都是唯一的，即它不允许有重复的元素。
- **无序性**：元素在 `unordered_set` 中的存储是无序的，这意味着你不能依赖元素的顺序来遍历它们。
- **哈希函数**：`unordered_set` 使用哈希函数来确定元素的存储位置，不同的元素可能有相同的哈希值，这称为哈希冲突。`unordered_set` 通过某种形式的冲突解决策略（如链地址法或开放寻址法）来处理这种情况。
- **性能**：虽然 `unordered_set` 在大多数情况下提供常数时间的查找性能，但在极端情况下（如大量哈希冲突）性能可能会降低。

#### 性能特点

- **时间复杂度**：平均情况下，`unordered_set` 的插入、删除和查找操作的时间复杂度为 O(1)。在最坏的情况下（例如，所有元素都映射到同一个哈希桶），时间复杂度可能退化到 O(n)，其中 n 是元素的数量。

### 适用场景

- 当你需要存储一组唯一的元素，并且频繁进行插入、删除和查找操作时，`unordered_set` 是一个很好的选择。
- 如果元素的顺序不重要，或者你不需要维护元素的顺序，那么 `unordered_set` 比 `set` 更适合，因为它通常提供更快的访问速度。

总的来说，`unordered_set` 是C++ STL中一个非常有用的容器，它在需要快速查找和插入操作时提供了高效的解决方案。

## 5.5

判断元素是否在哈希表内，可以使用find函数，判断返回点是不是末尾点；也可以用count函数，统计元素出现个数，直接`if(hash_set.count(val))`即可，因为如果没有元素返回0，有元素返回个数。

## 5.6

### 常见的三种哈希结构

当我们想使用哈希法来解决问题的时候，我们一般会选择如下三种数据结构。

- 数组
- set （集合）
- map(映射)

这里数组就没啥可说的了，我们来看一下set。

在C++中，set 和 map 分别提供以下三种数据结构，其底层实现以及优劣如下表所示：

| 集合               | 底层实现 | 是否有序 | 数值是否可以重复 | 能否更改数值 | 查询效率 | 增删效率 |
| ------------------ | -------- | -------- | ---------------- | ------------ | -------- | -------- |
| std::set           | 红黑树   | 有序     | 否               | 否           | O(log n) | O(log n) |
| std::multiset      | 红黑树   | 有序     | 是               | 否           | O(log n) | O(log n) |
| std::unordered_set | 哈希表   | 无序     | 否               | 否           | O(1)     | O(1)     |

std::unordered_set底层实现为哈希表，std::set 和std::multiset 的底层实现是红黑树，红黑树是一种平衡二叉搜索树，所以key值是有序的，但key不可以修改，改动key值会导致整棵树的错乱，所以只能删除和增加。

| 映射               | 底层实现 | 是否有序 | 数值是否可以重复 | 能否更改数值 | 查询效率 | 增删效率 |
| ------------------ | -------- | -------- | ---------------- | ------------ | -------- | -------- |
| std::map           | 红黑树   | key有序  | key不可重复      | key不可修改  | O(log n) | O(log n) |
| std::multimap      | 红黑树   | key有序  | key可重复        | key不可修改  | O(log n) | O(log n) |
| std::unordered_map | 哈希表   | key无序  | key不可重复      | key不可修改  | O(1)     | O(1)     |

std::unordered_map 底层实现为哈希表，std::map 和std::multimap 的底层实现是红黑树。同理，std::map 和std::multimap 的key也是有序的（这个问题也经常作为面试题，考察对语言容器底层的理解）。

当我们要使用集合来解决哈希问题的时候，优先使用unordered_set，因为它的查询和增删效率是最优的，如果需要集合是有序的，那么就用set，如果要求不仅有序还要有重复数据的话，那么就用multiset。

那么再来看一下map ，在map 是一个key value 的数据结构，map中，对key是有限制，对value没有限制的，因为key的存储方式使用红黑树实现的。

其他语言例如：java里的HashMap ，TreeMap 都是一样的原理。可以灵活贯通。

虽然std::set、std::multiset 的底层实现是红黑树，不是哈希表，std::set、std::multiset 使用红黑树来索引和存储，不过给我们的使用方式，还是哈希法的使用方式，即key和value。所以使用这些数据结构来解决映射问题的方法，我们依然称之为哈希法。 map也是一样的道理。

这里在说一下，一些C++的经典书籍上 例如STL源码剖析，说到了hash_set hash_map，这个与unordered_set，unordered_map又有什么关系呢？

实际上功能都是一样一样的， 但是unordered_set在C++11的时候被引入标准库了，而hash_set并没有，所以建议还是使用unordered_set比较好，这就好比一个是官方认证的，hash_set，hash_map 是C++11标准之前民间高手自发造的轮子。

### C++中set类型数据结构

在C++中，`std::set` 是一种关联容器，它存储的元素是唯一的，并按照升序进行排序。`std::set` 通常是基于平衡二叉搜索树（如红黑树）实现的，这使得它能够提供高效的查找、插入和删除操作。

以下是 `std::set` 的一些常用操作：

#### 构造和初始化

```cpp
std::set<int> mySet; // 默认构造一个空的set
std::set<int> mySet = {1, 2, 3}; // 列表初始化
std::set<int> mySet({1, 2, 3}); // 从初始化列表构造
```

#### 元素插入

```cpp
mySet.insert(4); // 插入一个元素
mySet.insert({5, 6}); // 插入多个元素
```

#### 元素查找

```cpp
if (mySet.find(2) != mySet.end()) {
    // 找到元素2
}
```

#### 元素计数

```cpp
int count = mySet.count(2); // 计数元素2的数量，set中每个元素都是唯一的，所以count只会是0或1
```

#### 元素删除

```cpp
mySet.erase(2); // 删除元素2
mySet.erase(mySet.find(3)); // 删除迭代器指向的元素
mySet.erase(mySet.begin(), mySet.end()); // 删除set中的所有元素
```

#### 查看大小

```cpp
size_t size = mySet.size(); // 获取set的大小
```

#### 清空

```cpp
mySet.clear(); // 移除set中的所有元素
```

#### 遍历

```cpp
for (int num : mySet) {
    // 处理num
}
```

或者使用迭代器：

```cpp
for (std::set<int>::iterator it = mySet.begin(); it != mySet.end(); ++it) {
    // 处理*it
}
```

#### 上下界查询

```cpp
std::set<int>::iterator lower = mySet.lower_bound(3); // 查找大于或等于3的最小元素的迭代器
std::set<int>::iterator upper = mySet.upper_bound(3); // 查找大于3的最小元素的迭代器
```

#### 集合操作

```cpp
std::set<int> set1 = {1, 2, 3};
std::set<int> set2 = {3, 4, 5};

set1.insert(set2.begin(), set2.end()); // 将set2的所有元素插入set1

std::set<int> set_union(set1.begin(), set1.end(), set2.begin(), set2.end()); // 并集
std::set<int> set_intersection(set1.begin(), set1.end(), set2.begin(), set2.end()); // 交集
std::set<int> set_difference(set1.begin(), set1.end(), set2.begin(), set2.end()); // 差集
```

#### 注意事项

- `std::set` 中的元素必须是可比较的，即必须能够使用 `<` 运算符进行比较。
- `std::set` 不允许有重复的元素，如果尝试插入一个已经存在的元素，那么这个插入操作将不会执行，并且 `insert` 函数会返回一个指向现有元素的迭代器。
- `std::set` 中的元素按照升序排列，这意味着元素的迭代顺序是有序的。

`std::set` 是C++标准模板库（STL）中非常有用的容器之一，它在需要维护有序且唯一元素集合的场景中非常有用。

### C++中map类型数据

在C++中，`std::map` 是一种关联容器，它存储键值对（key-value pairs），并且按照键的顺序进行排序。`std::map` 通常是基于平衡二叉搜索树（如红黑树）实现的，这使得它能够提供高效的查找、插入和删除操作。

以下是 `std::map` 的一些常用操作：

#### 构造和初始化

```cpp
std::map<int, std::string> myMap; // 默认构造一个空的map
std::map<int, std::string> myMap = {{1, "one"}, {2, "two"}}; // 列表初始化
std::map<int, std::string> myMap {{1, "one"}, {2, "two"}}; // 使用花括号初始化
```

#### 元素插入

```cpp
myMap.insert({3, "three"}); // 插入一个键值对
myMap[4] = "four"; // 通过下标运算符插入或修改键值对
```

#### 元素查找

```cpp
auto it = myMap.find(2);
if (it != myMap.end()) {
    // 找到键2，it->second 是对应的值
}
```

#### 元素访问

```cpp
std::string value = myMap[1]; // 获取键1对应的值，如果键不存在，将插入一个键1的默认值
```

#### 元素计数

```cpp
int count = myMap.count(2); // 计数键2的数量，map中每个键都是唯一的，所以count只会是0或1
```

#### 元素删除

```cpp
myMap.erase(2); // 删除键2
myMap.erase(it); // 删除迭代器指向的元素
myMap.clear(); // 删除map中的所有元素
```

#### 查看大小

```cpp
size_t size = myMap.size(); // 获取map的大小
```

#### 哈希表遍历/表的遍历

```cpp
for (const auto& pair : myMap) {
    // pair.first 是键，pair.second 是值
}
```

或者使用迭代器：

```cpp
for (auto it = myMap.begin(); it != myMap.end(); ++it) {
    // it->first 是键，it->second 是值
}
```

注意二者区别，前者是直接调用`.`来访问对应元素，后者是调用`->`。因为前者是表中的元素类型；后者是返回的迭代器。

#### 上下界查询

```cpp
std::map<int, std::string>::iterator lower = myMap.lower_bound(3); // 查找大于或等于3的最小键的迭代器
std::map<int, std::string>::iterator upper = myMap.upper_bound(3); // 查找大于3的最小键的迭代器
```

#### 注意事项

- `std::map` 中的键必须是可比较的，即必须能够使用 `<` 运算符进行比较。
- `std::map` 不允许有重复的键，如果尝试插入一个已经存在的键，那么这个插入操作将用新的值更新现有键对应的值。
- `std::map` 中的元素按照键的顺序进行排序，这意味着元素的迭代顺序是有序的。

`std::map` 是C++标准模板库（STL）中非常有用的容器之一，它在需要维护有序的键值对集合的场景中非常有用。

### C++中的sort函数

比如，给定字符串`string s='apple'`，对s进行sort操作，使得s变成`aelpp`

正确做法是`sort(s.begin(),s.end())`，而不应该想当然认为是`s=s.sort()`或者`s=s.sort(s.begin(),s.end())`因为会报错，说string类型对象没有对应的sort操作。也不应该和py中的sorted函数搞混淆。

排序的时间复杂度为$o(nlogn)$

### C++中的for循环类py写法

比如要遍历一个字符串类型中的所有字符，在py中是这样：`for ch in s:`在C++中也有类似写法：`for(auto& ch:s)`作用和py的一样，不过需要一个返回类型auto，适配所有循环遍历操作。

## 5.7

### 数组和set类型的选择与比较

C++中的数组和 `std::set` 是两种不同的数据结构，它们有各自的特点和适用场景。

#### 数组（Array）

数组是一种固定大小的连续内存区域，用于存储具有相同类型的多个元素。数组的关键特性包括：

- **固定大小**：一旦创建，数组的大小就不能改变。
- **内存连续**：数组中的元素在内存中是连续存储的，这有助于提高访问速度。
- **随机访问**：可以通过索引快速访问数组中的任何元素。
- **初始化**：可以初始化为默认值，但需要显式设置每个元素。

#### `std::set`

`std::set` 是一种关联容器，基于平衡二叉搜索树实现，它存储的元素是唯一的，并按照升序排序。`std::set` 的关键特性包括：

- **动态大小**：`std::set` 的大小可以根据需要动态变化。
- **唯一性**：`std::set` 中的元素是唯一的，不允许有重复。
- **排序**：元素自动按照值的升序排列。
- **查找效率**：提供对数时间复杂度的查找、插入和删除操作。

#### 使用数组实现哈希表

使用数组实现哈希表是一种简单但效率受限的方法。它适用于以下情况：

- **元素数量固定**：当你知道元素的数量并且它们不会改变时。
- **简单性**：当你需要一个简单的数据结构，并且不需要复杂的操作时。
- **内存效率**：数组是内存效率较高的数据结构，因为它不包含额外的指针或元数据。

#### 使用 `std::set` 实现哈希表

`std::set` 更适合以下情况：

- **动态数据**：当元素的数量可能会变化，或者你需要频繁插入和删除元素时。
- **唯一性**：当你需要确保数据结构中的元素是唯一的。
- **排序**：如果你需要元素有序，或者需要按顺序遍历元素时。
- **查找效率**：当查找操作的性能很重要，且元素数量可能很大时。

#### 总结

选择数组还是 `std::set` 取决于你的具体需求。如果需要一个固定大小、简单且内存高效的数据结构，可以选择数组。如果需要一个动态大小、元素唯一且有序的数据结构，应该选择 `std::set`。

在实际应用中，真正的哈希表实现通常使用专门的哈希表库（如 `std::unordered_set` 或 `std::unordered_map`），这些库提供了更好的性能和灵活性，尤其是在处理**大量数据**和需要**高效的查找、插入和删除操作**时。

## 5.8

### C++三目运算符

在C++中，三目运算符（也称为条件运算符）是一种基于条件表达式的简化形式的`if-else`语句。它的一般形式如下：

```cpp
condition ? expression_true : expression_false
```

这里的`condition`是一个布尔表达式，`expression_true`是当`condition`为真（true）时的返回值，而`expression_false`是当`condition`为假（false）时的返回值。

#### 使用三目运算符的示例

```cpp
int a = 10;
int b = 5;
int max = (a > b) ? a : b; // 如果 a > b 为真，max 将被赋值为 a，否则为 b
```

在这个例子中，我们比较了两个整数`a`和`b`，然后使用三目运算符来确定它们中的较大值，并将其存储在变量`max`中。

#### 三目运算符与`if-else`语句的比较

使用三目运算符可以写出更简洁的代码，特别是在简单的条件赋值情况下。下面是使用`if-else`语句和三目运算符实现相同功能的对比：

```cpp
// 使用 if-else 语句
if (a > b) {
    max = a;
} else {
    max = b;
}

// 使用三目运算符
max = (a > b) ? a : b;
```

#### 三目运算符中的`return`语句

三目运算符本身不包含`return`语句，它是一个表达式，其返回值是`expression_true`或`expression_false`中的一个。然而，三目运算符可以用在`return`语句中，作为函数返回值的条件表达式。例如：

```cpp
int getMax(int a, int b) {
    return (a > b) ? a : b; // 在 return 语句中使用三目运算符
}
```

在这个函数中，我们使用三目运算符来确定两个整数`a`和`b`中的较大值，并将其作为函数的结果返回。

#### 注意事项

- 三目运算符是右结合的，这意味着当有多个三目运算符连用时，最右边的运算符将首先被计算。
- 过度使用三目运算符可能会使代码变得难以阅读，尤其是在复杂的表达式中。在这些情况下，使用传统的`if-else`语句可能更清晰。
- 三目运算符只适用于有两个明确返回值的情况，如果需要更复杂的逻辑，应该使用`if-else`语句。

三目运算符提供了一种简洁的方式来处理简单的条件表达式，但在使用时应注意保持代码的可读性和清晰性。

### C++逐位提取整数型数字的每一位（数位分离）

在C++中，将无符号整数转换为字符串可以通过多种方式实现，以下是一些常用的方法：

#### 使用 `std::to_string`

这是最直接的方法，它使用标准库中的 `std::to_string` 函数：

```cpp
#include <string>
#include <iostream>

int main() {
    unsigned int num = 123;
    std::string str = std::to_string(num);
    
    // 逐位提取
    for (char c : str) {
        std::cout << c;
        //char 类型,对应相应的ASCII值
        std::cout << c-'0';
        //与0的ASCII做减法后得到的就是对应的数值了，可以进行相应的运算。
    }
    
    return 0;
}
```

我们使用 `for` 循环遍历字符串 `s` 中的每个字符，使用字符减去 `'0'` 的方式将其转换为整数（这是因为字符的内部表示是基于它们的ASCII码值，而数字字符的ASCII码值是连续的）。

#### 使用循环和数学运算

如果需要手动转换，可以通过循环和数学运算逐位提取数字：

```cpp
#include <iostream>

int main() {
    unsigned int num = 123;
    while (num > 0) {
        // 获取当前最低位的数字
        std::cout << num % 10;
        // 移除当前最低位
        num /= 10;
    }
    
    return 0;
}
```

#### 使用 `std::stringstream`

`std::stringstream` 可以用于将数字转换为字符串，并且可以方便地逐位访问：

```cpp
#include <sstream>
#include <string>
#include <iostream>

int main() {
    unsigned int num = 123;
    std::stringstream ss;
    ss << num;
    std::string str = ss.str();
    
    // 逐位提取
    std::reverse(str.begin(), str.end()); // 反转字符串以便从最低位开始
    
    for (char c : str) {
        std::cout << c;
    }
    
    return 0;
}
```

在这个例子中，我们首先将数字转换为字符串，然后使用 `std::reverse` 函数来反转字符串，这样我们就可以从最低位开始逐位提取数字。

#### 使用 `std::ostringstream` (C++11及以上)

`std::ostringstream` 是 `std::stringstream` 的一个特化版本，只支持输出操作：

```cpp
#include <sstream>
#include <iostream>

int main() {
    unsigned int num = 123;
    std::ostringstream oss;
    oss << num;
    std::string str = oss.str();
    
    // 逐位提取
    for (char c : str) {
        std::cout << c;
    }
    
    return 0;
}
```

选择哪种方法取决于你的具体需求。如果只是简单地需要将数字转换为字符串，`std::to_string` 是最简单直接的方法。如果你需要更多的控制，比如自定义格式或者在转换过程中进行其他操作，那么 `std::stringstream` 或 `std::ostringstream` 可能是更好的选择。

## 5.9

### C++统计vector\<int>类型数据中某元素出现的个数

在 C++ 中，如果你想要统计 `vector<int>` 类型容器中某个特定元素出现的次数，你可以使用标准库中的 `algorithm` 头文件提供的 `count` 函数。这是一个简单且直接的方法。

以下是使用 `count` 函数统计特定元素出现次数的示例代码：

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    // 创建并初始化一个 vector
    std::vector<int> vec = {1, 2, 3, 4, 5, 3, 3, 2, 3, 4};

    // 要统计的特定元素
    int target = 3;

    // 使用 count 函数统计特定元素出现的次数
    int count = std::count(vec.begin(), vec.end(), target);

    // 输出结果
    std::cout << "元素 " << target << " 出现的次数是: " << count << std::endl;

    return 0;
}
```

在上面的代码中，`std::count` 函数接受三个参数：容器的开始迭代器、结束迭代器和要搜索的目标值。它返回一个整数，表示目标值在容器中出现的次数。

如果你想要统计的元素在 `vector` 中是唯一的，或者你想要统计其他类型的元素，你也可以使用相同的方法。只需确保提供的迭代器与容器的类型相匹配，并且目标值的类型与 `vector` 中存储的元素类型一致。

此外，如果你想要更高效的统计（特别是在大型数据集上），可能需要考虑其他算法或数据结构，例如使用一个额外的 `std::map` 或 `std::unordered_map` 来跟踪每个元素的出现次数。但大多数情况下，`std::count` 已经足够高效且方便使用。

主要收获就是C++里面的count函数的用法是直接`count(begin,end,target)`这种结构，而不是`vec.count(target)`，因为这个函数是algorithm头文件里面专有的，而不是所谓vector类型中的可调用函数。

### 编程小技巧

在创建哈希表的时候，我的做法是

```cpp
for(int x: nums1){
    for(int y:nums2){
        if(hash_map1.find(x+y)!=hash_map1.end()){
            //能找到相同元素的
            hash_map1[x+y]+=1;
        }
        else{
            hash_map1.insert({x+y,1});
        }
```

看了参考答案才知道人家的写法更加简洁优雅：

```cpp
for(int x :num1){
    for(int y:num2){
        hash_map[x+y]++;
    }
}
```

这个编程方法真的值得学习，完成了插入新数据和增加旧数据的操作，相比之下我的ifelse结构就显得很幼稚。

## 5.10

### C++中的静态数组

#### 声明和初始化

声明静态数组时，必须指定数组的大小。数组可以在声明时初始化，也可以稍后在程序中初始化。

```cpp
// 声明并初始化一个静态数组
int myArray[5] = {1, 2, 3, 4, 5};

// 仅声明一个静态数组（未初始化的数组元素将自动初始化为0）
double otherArray[4];
int arr[26]={0};
int arr[26]{};
int arr[26];
//上面做法都生成并初始化固定大小的数组，初始元素均设置为0

std::string staticStringArray[3]; // 所有字符串元素都被默认构造为空字符串

//使用 std::fill 或 std::fill_n 函数来初始化数组的元素。
int staticArray[5];
std::fill(staticArray, staticArray + 5, -1); // 将所有元素初始化为-1
int value = 10;
std::fill_n(staticArray, 5, value); // 将所有元素初始化为10
```

#### 大小固定

静态数组的大小是固定的，一旦声明，就不能改变。这意味着你不能在程序运行过程中添加或删除数组中的元素。

#### 存储位置

静态数组在栈上分配内存，这是因为它们的整个生命周期与程序的整个运行时间相同，且大小在编译时已知。

#### 访问数组元素

可以通过索引来访问静态数组的元素，索引从0开始。

```cpp
int value = myArray[2]; // 获取数组第三个元素的值，结果是3
```

#### 使用范围for循环

C++11标准引入了基于范围的for循环，它可以用来方便地遍历数组。

```cpp
for (int num : myArray) {
    std::cout << num << " ";
}
```

#### 函数外部数组

如果静态数组在函数外部声明，它具有全局生命周期，即它从程序开始运行时存在，直到程序结束。

```cpp
static int globalArray[10]; // 全局静态数组
```

这里的 `static` 关键字不是类型的一部分，而是指示编译器该数组具有静态存储期，即使用静态内存分配。

#### 函数内部数组

如果静态数组在函数内部声明，它具有静态存储期，这意味着它在程序的整个运行时间内都存在，而不是仅仅在函数调用期间。

```cpp
void someFunction() {
    static int staticArray[10]; // 函数内部的静态数组
    // ...
}
```

在这种情况下，`staticArray` 在第一次函数调用时被初始化，并且在后续的函数调用中保持其值。

#### 注意事项

- 静态数组的大小必须在编译时已知，不能使用变量或运行时计算的表达式来指定大小。
- 静态数组的元素在声明时未显式初始化的，将自动初始化为0（对于基本数据类型）。
- 静态数组不能使用 `new` 或 `delete` 操作符进行动态内存分配。

### C++删除字符串中的某个元素

#### 使用 `std::string` 的 `erase` 方法

如果你使用的是 `std::string` 类型，可以直接使用它的 `erase` 方法来删除指定位置的字符。

```cpp
#include <string>

std::string str = "Hello, World!";
str.erase(5, 1); // 删除索引为5的字符，参数为删除的起始位置和数量
```

#### 使用 `std::remove` 和 `std::string` 的 `erase`

`std::remove` 是一个标准库算法，它可以用来**移除满足特定条件的元素**。通常与 `std::string` 的 `erase` 方法结合使用。

```cpp
#include <algorithm> // for std::remove
#include <string>

std::string str = "Hello, World!";
auto new_end = std::remove(str.begin(), str.end(), 'o'); // 移除所有 'o' 字符
str.erase(new_end, str.end());
```

#### 使用循环和 `std::string` 的 `clear`

如果你需要基于某种条件删除字符，可以使用循环来手动删除它们。

```cpp
#include <string>

std::string str = "Hello, World!";
str.clear(); // 清空字符串
for (char c : "Hello, World!") {
    if (c != 'o') {
        str.push_back(c); // 只添加不是 'o' 的字符
    }
}
```

#### 注意事项

- `std::string` 是一个可变容器，这意味着你可以修改它的大小和内容。
- `erase` 方法会移除字符串中的一个或多个字符，并返回一个新的字符串结尾的迭代器。
- `std::remove` 不会修改原始字符串，但它会返回一个新的迭代器，指向满足条件的最后一个元素之后的位置。你需要使用 `erase` 方法来实际删除这些元素。

选择哪种方法取决于你的具体需求，例如你要删除特定的字符、基于条件删除字符，或者删除特定位置的字符。在处理字符串时，`std::string` 提供了灵活的方法来修改和操作字符串内容。

### C++中for循环中`&`的差异

在C++中，`for` 循环的遍历方式对变量的引用和复制有重要影响。以下是 `for (char& c : magazine)` 和 `for (char c : magazine)` 两种形式的区别：

#### 1. `for (char& c : magazine)`

这种形式使用引用来遍历 `magazine` 中的元素。在这种情形下，`c` 是对 `magazine` 中每个字符的引用，而不是字符的副本。这意味着你对 `c` 所做的任何修改都会直接反映在 `magazine` 字符串中。

```cpp
for (char& c : magazine) {
    c = 'X'; // 直接修改magazine中的字符
}
```

#### 2. `for (char c : magazine)`

这种形式通过值来遍历 `magazine` 中的元素。这里，`c` 是 `magazine` 中每个字符的副本。因此，任何对 `c` 的修改都不会影响原始的 `magazine` 字符串。

```cpp
for (char c : magazine) {
    c = 'X'; // 修改的是c的副本，不会影响magazine
}
```

#### 区别和用途

- **引用（`char& c`）**：当你需要修改容器中的元素时使用。它允许你在循环内部直接修改 `magazine` 中的字符。
- **值（`char c`）**：当你只需要读取容器中的元素，不需要修改它们时使用。它为每个遍历的元素创建了一个临时副本。

#### 注意事项

- 当你使用引用遍历时（`char& c`），需要确保容器中的元素不是 `const` 类型的，否则你会得到一个编译错误，因为尝试修改一个 `const` 元素是不允许的。
- 使用引用遍历通常更高效，因为它避免了不必要的复制。但是，如果你的循环逻辑不需要修改元素，使用值遍历（`char c`）可以避免潜在的错误，并使代码的意图更加明确。

在处理字符串时，选择哪种形式取决于你是否需要修改字符串中的字符。如果需要修改，使用引用；如果不需要，使用值。

## 5.11

### vector中的find操作

在C++中，`std::vector` 是一种序列容器，用于存储相同类型的元素。`std::vector` 提供了 `find` 方法，它是 `<algorithm>` 头文件中 `std::find` 算法的特化版本，用于在 `vector` 中查找与给定值相等的第一个元素。

#### `find` 方法的基本用法

`find` 方法的基本语法如下：

```cpp
vector<T>::iterator find(const T& value);
```

这里，`T` 是 `vector` 存储的元素类型。`find` 方法接受一个参数，即要查找的值，然后返回一个迭代器，指向 `vector` 中第一个与该值相等的元素。如果 `vector` 中没有这样的元素，`find` 方法将返回 `vector` 的结束迭代器（`end()`）。

#### 示例

```cpp
#include <iostream>
#include <vector>
#include <algorithm> // 用于 std::find

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // 查找值 3
    auto it = vec.find(3);
    auto it = find(vec.begin(),vec.end(),3);

    if (it != vec.end()) {
        std::cout << "Found " << *it << " at position " << it - vec.begin() << std::endl;
    } else {
        std::cout << "Value not found in the vector." << std::endl;
    }

    return 0;
}
```

在这个例子中，我们创建了一个存储整数的 `vector`，然后使用 `find` 方法查找值 `3`。如果找到了，我们打印出找到的元素和它在 `vector` 中的位置；如果没有找到，我们打印出一个消息。

#### 注意事项

- `find` 方法的**时间复杂度是 O(n)**，其中 n 是 `vector` 中的元素数量。这是因为在最坏的情况下，`find` 可能需要遍历整个 `vector`。
- `find` 方法不会修改 `vector` 的内容或状态。
- 如果你需要在查找后继续遍历 `vector`，你应该记住 `find` 方法返回的迭代器，因为它指向找到的元素。
- 如果 `find` 返回的是 `end()`，这意味着元素不在 `vector` 中，你应该避免尝试解引用 `end()` 迭代器。

`find` 方法是 `std::vector` 的成员函数，它是查找操作的简单实现，适用于需要在 `vector` 中搜索特定值的场景。

### C++统计数组元素出现的次数（类似py中的counter）

在C++中，要统计数组中每个元素出现的次数并生成一张哈希表，可以使用 `std::unordered_map`，它是一种基于哈希表的关联容器，类似于Python中的字典。下面是一个示例代码，展示如何实现这一功能：

```cpp
#include <iostream>
#include <unordered_map>

int main() {
    int arr[] = {1, 2, 3, 2, 1, 4, 3, 2, 1};
    int n = sizeof(arr) / sizeof(arr[0]); // 计算数组元素的个数

    // 使用 std::unordered_map 作为哈希表
    std::unordered_map<int, int> hashTable;

    // 遍历数组，统计每个元素的出现次数
    for (int i = 0; i < n; ++i) {
        // 将元素出现的次数加1，如果元素不在表中，则会插入新的键值对
        hashTable[arr[i]]++;
    }

    // 输出结果
    for (const auto& pair : hashTable) {
        std::cout << "Element " << pair.first << " appears " << pair.second << " times" << std::endl;
    }

    return 0;
}
```

在这个示例中，我们首先定义了一个整数数组 `arr`，然后使用 `std::unordered_map` 来创建哈希表 `hashTable`。数组中的每个元素作为键，其出现次数作为值。

我们遍历数组，使用 `hashTable` 中的元素作为键来更新其值。如果元素已经在 `hashTable` 中，我们将其对应的值加一；如果不在，`std::unordered_map` 会自动将其插入为新的键值对，其中键是数组中的元素，值初始化为1。

最后，我们遍历 `hashTable` 并输出每个元素及其出现的次数。

这种方法的时间复杂度是 O(n)，其中 n 是数组中的元素数量，因为我们只遍历数组一次。使用 `std::unordered_map` 的空间复杂度是 O(m)，其中 m 是数组中不重复元素的数量，这是因为我们需要存储每个唯一元素及其出现的次数。

### C++一次push_back一个数组

比如有一个二维数组`vector<vector<int>> result`，要往这个二维数组中插入一行元素，可以创建临时一维数组，对一维数组逐个插入，再result插入tmp；另一种更好的方法是在result中直接插入数组：`result.push_back({nums[i],nums[j],nums[k]})`，括号里面的需要的是大括号括起来的数据组，因为定义数组的时候就是使用大括号来初始化数据的。

## 5.12

### 判断两个vector数组是否元素一致

在C++中，判断两个 `std::vector` 数组（向量）的元素是否完全一致，即它们包含相同的元素且顺序也相同，可以通过几种不同的方法实现。以下是两种常见的方法：

#### 方法1：直接比较操作符

C++标准库提供了直接比较两个 `std::vector` 的操作符 `==`。当且仅当两个向量的每个对应位置上的元素都相等时，比较结果为 `true`。

```cpp
#include <vector>
#include <iostream>

bool areVectorsEqual(const std::vector<int>& vec1, const std::vector<int>& vec2) {
    return vec1 == vec2;
}

int main() {
    std::vector<int> v1 = {1, 2, 3};
    std::vector<int> v2 = {1, 2, 3};
    std::vector<int> v3 = {3, 2, 1};

    std::cout << std::boolalpha << areVectorsEqual(v1, v2) << std::endl; // 输出: true
    std::cout << std::boolalpha << areVectorsEqual(v1, v3) << std::endl; // 输出: false
    return 0;
}
```

#### 方法2：遍历比较

如果你需要更细粒度的控制或者想要避免潜在的递归比较（当 `std::vector` 包含自身作为元素时），可以手动遍历两个向量并比较它们的元素。

```cpp
bool areVectorsEqual(const std::vector<int>& vec1, const std::vector<int>& vec2) {
    if (vec1.size() != vec2.size()) {
        return false; // 如果大小不同，则直接返回false
    }
    for (std::size_t i = 0; i < vec1.size(); ++i) {
        if (vec1[i] != vec2[i]) {
            return false; // 发现不匹配的元素，返回false
        }
    }
    return true; // 所有元素都匹配，返回true
}
```

这种方法首先检查两个向量的大小是否相同，如果不同，则它们不可能相等。然后，它遍历向量的每个元素并逐一比较。如果发现任何不匹配的元素，函数将返回 `false`。如果遍历完成后没有发现不匹配的元素，函数返回 `true`。

#### 注意事项

- 两种方法都适用于比较包含基本数据类型（如 `int`、`double` 等）的向量。
- 如果向量包含自定义类型的对象，那么这些类型必须定义了相等运算符（`operator==`），以便进行比较。
- 直接比较操作符可能更简洁，但在某些情况下，如向量元素是复杂类型或自定义类型时，可能需要手动实现比较逻辑。

选择哪种方法取决于你的具体需求和偏好。直接比较操作符通常更简洁且易于阅读，而手动遍历比较提供了更多的控制。

## 5.13

### C++中的reverse函数

在C++中，`std::reverse` 是一个标准库算法函数，用于反转序列容器中的元素顺序。这个函数定义在 `<algorithm>` 头文件中，可以应用于如 `std::vector`、`std::array`、`std::deque` 等序列容器。

#### 函数原型

```cpp
void reverse(BidirectionalIterator first, BidirectionalIterator last);
```

这里的 `BidirectionalIterator` 是一个双向迭代器，它指向了要反转序列的起始位置和结束位置（不包括 `last`）。

#### 使用示例

```cpp
#include <algorithm> // for std::reverse
#include <vector>
#include <iostream>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // 反转整个向量
    std::reverse(vec.begin(), vec.end());

    // 输出反转后的向量
    for (int num : vec) {
        std::cout << num << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

在这个例子中，`std::reverse` 被用来反转 `vec` 中的所有元素。函数接受 `vec.begin()` 作为序列的开始迭代器，`vec.end()` 作为序列的结束迭代器。

#### 注意事项

- `std::reverse` 不会返回任何值，它直接修改传入的序列。
- 如果序列是空的或者只有一个元素，`std::reverse` 不会执行任何操作。
- 反转操作的时间复杂度是 O(N)，其中 N 是序列中的元素数量。

#### 反转部分序列

`std::reverse` 也可以用于反转序列中的一部分元素：

```cpp
std::vector<int> vec = {1, 2, 3, 4, 5};
std::reverse(vec.begin() + 1, vec.begin() + 3);
```

这将只反转从索引 1 开始到索引 3 结束的元素（不包括索引 3 的元素）的部分序列。

#### 反转算法与逆序迭代器

除了 `std::reverse`，C++ 标准库还提供了 `std::reverse_copy`，它与 `std::reverse` 类似，但会将结果复制到另一个序列中，而不是原地修改。此外，还可以使用逆序迭代器（reverse iterator）来遍历序列的元素逆序：

```cpp
for (auto it = vec.rbegin(); it != vec.rend(); ++it) {
    std::cout << *it << " ";
}
```

这将输出 `vec` 中元素的逆序，而不需要改变 `vec` 本身。逆序迭代器在 `std::vector`、`std::deque` 和 `std::array` 等容器中可用。

## 5.14

无

## 5.15

### C++中对string字符串的修改操作

在C++中，`std::string` 是一个非常强大的字符串类，提供了多种方法来修改字符串。以下是一些常用的字符串修改操作：

#### 1. 赋值和追加

- **赋值**：使用 `=` 运算符可以将一个字符串赋值给另一个字符串。
- **追加**：使用 `+=` 运算符可以将一个字符串追加到另一个字符串。

```cpp
std::string str1 = "Hello";
std::string str2;
str2 = str1; // 赋值
str1 += " World"; // 追加
```

#### 2. `append` 方法

`append` 方法可以在字符串的末尾添加更多的字符或另一个字符串。

```cpp
str1.append(" and Goodbye");
```

#### 3. `push_back` 方法

`push_back` 方法可以在字符串的末尾添加一个字符。

```cpp
str1.push_back('!');
```

#### 4. `insert` 方法

`insert` 方法可以在指定位置插入一个字符或另一个字符串。

```cpp
str1.insert(5, " ");
```

#### 5. `erase` 方法

`erase` 方法可以删除字符串中的字符或字符串序列。

```cpp
str1.erase(5, 6); // 删除从位置5开始的6个字符
```

#### 6. `replace` 方法

`replace` 方法可以替换字符串中的部分内容。

```cpp
str1.replace(5, 6, "XXX"); // 从位置5开始，替换6个字符为"XXX"
```

#### 7. `clear` 方法

`clear` 方法可以清除字符串的所有内容。

```cpp
str1.clear(); // str1 变为空字符串
```

#### 8. `resize` 方法

`resize` 方法可以改变字符串的大小，如果增大，则在末尾添加填充字符。

```cpp
str1.resize(10, 'x'); // 将 str1 调整为10个字符长，不足的用 'x' 填充
```

#### 9. `assign` 方法

`assign` 方法可以替换字符串的内容为一个新的字符串或字符序列。

```cpp
str1.assign("New Content");
```

#### 10. 直接通过索引修改

`std::string` 提供了通过索引访问字符的能力，允许你直接修改特定位置的字符。

```cpp
str1[0] = 'S'; // 将字符串开头的字符从 'H' 改为 'S'
```

#### 注意事项

- `std::string` 是可变的，这意味着一旦创建，其内容可以被改变。
- 字符串是包含字符的数组，所以你可以像操作数组一样操作字符串，但请确保不要越界。
- 字符串的索引操作（通过 `[]`）未定义行为的区间检查，所以应该小心使用，避免越界访问。
- 在C++中，字符串字面量（如 `"Hello"`）是 `const char` 类型的数组，因此它们的内容在运行时是不可修改的。

通过上述方法，你可以灵活地修改C++中的字符串，以满足不同的编程需求。

### 字符串中某字符时候属于数字或者字母

在字符串中 ，每一个字符都是char类型的数据，每一个字符都有对应的ASCII值。因此不用把10个数字全部列出来，直接使用一个界值判断语句即可：`if(s[i]>='0' && s[i]<='9')`这样就完成了对当前字符是否是数字的判断。同理，对大写或者小写字母的判断也是这样，直接使用界值判断语句即可。

## 5.16

### C++分割字符串

在C++中，没有直接类似于Python中 `split()` 函数的函数，但你可以使用一些标准库函数和算法来实现类似的功能。以下是几种在C++中实现字符串分割的方法：

#### 1. 使用 `std::istringstream` 和 `std::getline`

这是分割字符串的常用方法，它使用 `std::istringstream` 来模拟流操作，然后使用 `std::getline` 来按指定分隔符读取字符串。

```cpp
#include <sstream>
#include <string>
#include <vector>

std::vector<std::string> split(const std::string& str, char delimiter) {
    std::vector<std::string> tokens;
    std::istringstream tokenStream(str);
    std::string token;
    while (std::getline(tokenStream, token, delimiter)) {
        tokens.push_back(token);
    }
    return tokens;
}
```

#### 2. 使用 `std::find_first_of` 和循环

这种方法通过查找分隔符的位置来分割字符串。

```cpp
#include <string>
#include <vector>

std::vector<std::string> split(const std::string& str, char delimiter) {
    std::vector<std::string> tokens;
    size_t start = 0;
    size_t end = str.find(delimiter);
    
    while (end != std::string::npos) {
        tokens.push_back(str.substr(start, end - start));
        start = end + 1;
        end = str.find(delimiter, start);
    }
    
    tokens.push_back(str.substr(start, end));
    return tokens;
}
```

#### 3. 使用 `std::regex`

C++11及以后版本支持正则表达式，你可以使用 `std::regex` 来分割字符串。

```cpp
#include <regex>
#include <string>
#include <vector>

std::vector<std::string> split(const std::string& str, char delimiter) {
    std::vector<std::string> tokens;
    std::regex re(1, delimiter);
    std::copy(std::sregex_token_iterator(str.begin(), str.end(), re, -1), std::sregex_token_iterator(), back_inserter(tokens));
    return tokens;
}
```

#### 注意事项

- 当处理空字符串或连续分隔符时，你可能需要修改上述函数以适应你的需求。
- 如果你的分隔符是一个字符串而不是单个字符，你需要相应地调整正则表达式的构造和 `std::getline` 的使用。
- 这些方法中，使用 `std::istringstream` 和 `std::getline` 的方法通常更直观和易于理解。

通过上述任何一种方法，你都可以在C++中实现类似Python中 `split()` 函数的功能。

### C++对字符串的find操作

在C++中，如果你想要在一个字符串的特定范围内寻找某个元素（字符），你可以使用 `std::string` 类的 `find` 成员函数。这个函数可以在字符串中查找子字符串的位置，也可以用来查找单个字符的位置。

以下是使用 `std::string` 的 `find` 函数来查找单个字符范围的示例：

#### 查找单个字符

```cpp
#include <string>

int main() {
    std::string str = "Hello, World!";
    char ch = 'o';
    size_t found_pos = str.find(ch, 0); // 从位置0开始查找字符'o'

    if (found_pos != std::string::npos) {
        std::cout << "Found character '" << ch << "' at position: " << found_pos << std::endl;
    } else {
        std::cout << "Character not found in the string." << std::endl;
    }

    return 0;
}
```

#### 查找子字符串

```cpp
#include <string>

int main() {
    std::string str = "Hello, World!";
    std::string to_find = "World";
    size_t found_pos = str.find(to_find, 0); // 从位置0开始查找子字符串"World"

    if (found_pos != std::string::npos) {
        std::cout << "Found substring '" << to_find << "' at position: " << found_pos << std::endl;
    } else {
        std::cout << "Substring not found in the string." << std::endl;
    }

    return 0;
}
```

`find` 函数的第二个参数是你想要开始搜索的位置。如果你想要在整个字符串中搜索，可以从 `0` 开始。

`std::string::npos` 是一个特殊的值，表示未找到。如果 `find` 函数没有找到指定的字符或子字符串，它将返回 `std::string::npos`。

#### 查找直到某个位置

如果你只想在字符串的特定范围内查找（例如，从位置 `start_pos` 到位置 `end_pos`），你可以使用 `find_first_of` 或 `find_last_of` 函数：

```cpp
#include <string>
#include <iostream>

int main() {
    std::string str = "Hello, World!";
    char ch = 'o';
    size_t start_pos = 0;
    size_t end_pos = str.find(' ') - 1; // 查找空格的位置作为结束位置

    // 查找字符在指定范围内的最后一次出现
    size_t found_pos = str.find_last_of(ch, end_pos);

    if (found_pos != std::string::npos) {
        std::cout << "Found character '" << ch << "' at position: " << found_pos << std::endl;
    } else {
        std::cout << "Character not found in the specified range." << std::endl;
    }

    return 0;
}
```

在这个例子中，我们使用 `find_last_of` 函数查找字符 `'o'` 在字符串 `str` 中从位置 `start_pos` 到 `end_pos` 的最后一次出现。`end_pos` 是空格字符前的位置，因为我们不包括空格在内。如果 `end_pos` 是空字符串或未找到空格，则可能需要调整逻辑以确保正确处理边界情况。

## 5.17

### 获取子字符串substr()

在C++中，`substr` 是 `std::string` 类的一个成员函数，用于从字符串中提取子字符串。这个方法返回一个 `std::string` 类型的副本，包含原始字符串中从指定位置开始的特定长度的字符序列。

#### 语法

```cpp
std::string substr(size_t pos = 0, size_t len = npos) const;
```

- `pos` 是一个可选参数，指定从哪个位置开始提取子字符串。如果未指定，`pos` 默认为 0，即从字符串的开头开始。
- `len` 是要提取的字符数。如果未指定或指定为 `std::string::npos`（这是 `std::string` 类的一个特殊值，表示直到字符串的末尾），则子字符串将包含从 `pos` 开始到原始字符串末尾的所有字符。

#### 示例

```cpp
#include <iostream>
#include <string>

int main() {
    std::string str = "Hello, World!";
    
    // 提取从位置 7 开始的子字符串，直到字符串末尾
    std::string sub1 = str.substr(7);
    std::cout << sub1 << std::endl; // 输出: World!

    // 提取从位置 5 开始，长度为 6 的子字符串
    std::string sub2 = str.substr(5, 6);
    std::cout << sub2 << std::endl; // 输出: World

    return 0;
}
```

#### 注意事项

- 如果 `pos` 大于字符串的长度，`substr` 将返回一个空字符串。
- 如果 `pos` 加上 `len` 超出了字符串的末尾，`substr` 将只返回从 `pos` 开始到字符串末尾的部分。
- `substr` 方法不会修改原始字符串。

`substr` 方法是C++中处理字符串时的一个有用工具，它允许你轻松地从字符串中提取特定部分。

## 5.18

[KMP算法，from评论区大佬](https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string/solutions/2600821/kan-bu-dong-ni-da-wo-kmp-suan-fa-chao-qi-z1y0)

## 5.19

### C++截取字符串

在C++中，可以使用`std::string`类的`substr`成员函数来截取字符串的一部分，并将其赋值给一个新的`std::string`对象。`substr`函数的原型如下：

```cpp
string substr(size_t pos = 0, size_t count = npos) const;
```

- `pos` 是要截取的子字符串的起始位置（从0开始计数）。
- `count` 是要截取的子字符串的长度。如果不指定或者指定为`string::npos`，则截取从`pos`开始到原字符串末尾的所有字符。

下面是一个使用`substr`函数的例子：

```cpp
#include <iostream>
#include <string>

int main() {
    std::string str = "Hello, World!";
    size_t pos = 7; // 从第8个字符开始截取
    size_t count = 5; // 截取5个字符

    std::string subStr = str.substr(pos, count);
    std::cout << subStr << std::endl; // 输出 "World"

    return 0;
}
```

在这个例子中，我们从字符串`"Hello, World!"`的第8个字符（位置7，因为索引从0开始）开始截取，截取长度为5的子字符串，得到的结果是`"World"`。

请根据你的具体需求调整`pos`和`count`的值。如果你想要截取从某个位置到字符串末尾的所有字符，可以将`count`设置为`std::string::npos`。

## 5.20

在C++中如果想要有在类中可以调用的数据结构，可以在private类型中进行声明，也可以在public中声明。在后面编写的函数中可以直接调用这些数据结构。

## 5.21

NULL

## 5.22

NULL

## 5.23

### C++使用string模拟存储类型为char的栈

<center>关键词：字符串模拟栈<center>
<center>
    关键词：string
<center>
<center>关键词：字符串
<center>

在C++中，可以使用`std::string`来模拟一个存储`char`数据的栈。`std::string`提供了在字符串末尾添加和删除元素的功能，这与栈的后进先出（LIFO）特性相符合。以下是使用`std::string`模拟栈的一个简单示例：

```cpp
#include <iostream>
#include <string>

class CharStack {
private:
    std::string stack; // 使用字符串作为栈的底层容器

public:
    // 入栈操作
    void push(char c) {
        stack.push_back(c); // 在字符串末尾添加元素
    }

    // 出栈操作
    void pop() {
        if (!stack.empty()) {
            stack.pop_back(); // 删除字符串末尾的元素
        } else {
            std::cout << "Stack is empty, cannot pop." << std::endl;
        }
    }

    // 查看栈顶元素
    char top() const {
        if (!stack.empty()) {
            return stack.back(); // 返回字符串末尾的元素
        } else {
            std::cout << "Stack is empty, no top element." << std::endl;
            return '\0'; // 返回空字符，表示栈为空
        }
    }

    // 检查栈是否为空
    bool empty() const {
        return stack.empty(); // 字符串为空则栈为空
    }

    // 获取栈的大小
    size_t size() const {
        return stack.size(); // 返回字符串的长度
    }
};

int main() {
    CharStack myStack;

    // 入栈操作
    myStack.push('a');
    myStack.push('b');
    myStack.push('c');

    // 查看栈顶元素
    std::cout << "Top element is: " << myStack.top() << std::endl;

    // 出栈操作
    myStack.pop();
    std::cout << "Top element after one pop is: " << myStack.top() << std::endl;

    // 检查栈是否为空
    if (myStack.empty()) {
        std::cout << "The stack is empty." << std::endl;
    } else {
        std::cout << "The stack is not empty." << std::endl;
    }

    return 0;
}
```

在这个示例中，`CharStack`类使用`std::string`作为底层容器来存储`char`类型的数据。我们定义了`push`、`pop`、`top`、`empty`和`size`方法来模拟栈的基本操作。

- `push`方法使用`std::string::push_back`在栈顶添加一个元素。
- `pop`方法使用`std::string::pop_back`移除栈顶元素，如果栈为空，则输出错误信息。
- `top`方法返回栈顶元素，如果栈为空，则输出错误信息并返回空字符。
- `empty`方法返回栈是否为空的状态。
- `size`方法返回栈中元素的数量。

这个简单的栈实现可以用于基本的字符数据栈操作。如果需要更复杂的功能，比如异常安全或者线程安全，可能需要进一步扩展这个类。

### C++对字符串的操作

<center>关键词：对字符串操作<center>

<center>关键词：对string的操作<center>

在C++中，`std::string` 是标准库中的一个类模板，专门用于处理字符串。以下是一些常见的 `std::string` 操作：

#### 构造和初始化

- 默认构造一个空字符串：

  ```cpp
  std::string str;
  ```

- 通过指定字符数量和默认字符初始化：

  ```cpp
  std::string str(10, 'a'); // 创建一个包含10个'a'的字符串
  ```

- 通过复制或移动构造：

  ```cpp
  std::string str1("Hello");
  std::string str2 = str1; // 复制构造
  std::string str3 = std::move(str1); // 移动构造
  ```

- 通过C风格字符串初始化：

  ```cpp
  const char* cstr = "C-string";
  std::string str(cstr);
  ```

#### 赋值操作

- 赋值操作符：

  ```cpp
  std::string str;
  str = "Hello"; // 赋值
  ```

- 移动赋值操作符：

  ```cpp
  str = std::move(otherStr); // 移动赋值
  ```

#### 访问元素

- 通过下标访问字符串中的字符：

  ```cpp
  char ch = str[0]; // 获取第一个字符
  ```

- 使用 `at()` 成员函数，它还检查索引是否有效：

  ```cpp
  char ch = str.at(0); // 获取第一个字符，带边界检查
  ```

#### 字符串长度和大小

- 获取字符串长度：

  ```cpp
  size_t len = str.length(); // 或者使用 str.size()
  ```

- 清空字符串：

  ```cpp
  str.clear();
  ```

#### 字符串拼接

- 使用 `+` 运算符拼接字符串：

  ```cpp
  std::string str1 = "Hello";
  std::string str2 = "World";
  std::string str3 = str1 + " " + str2;
  ```

- 使用 `append()` 或 `operator+=`：

  ```cpp
  str1.append(str2);
  str1 += str2; // 等价于 append
  ```

#### 字符串比较

- 使用 `==`, `!=`, `<`, `>`, `<=`, `>=` 比较字符串：

  ```cpp
  if (str1 == str2) {
    // 字符串相等
  }
  ```

#### 子字符串操作

- 使用 `substr()` 获取子字符串：

  ```cpp
  std::string sub = str.substr(0, 5); // 获取前5个字符
  ```

- 使用 `find()` 查找子字符串：

  ```cpp
  size_t pos = str.find("sub");
  if (pos != std::string::npos) {
    // 找到了子字符串
  }
  ```

#### 字符串替换

- 使用 `replace()` 替换字符串中的部分：

  ```cpp
  str.replace(0, 5, "New");
  // 将从索引0开始的5个字符替换为"New"
  ```

#### 字符串插入和删除

- 使用 `insert()` 在指定位置插入字符或字符串：

  ```cpp
  str.insert(0, "New-");
  // 在索引0的位置插入"New-"
  ```

- 使用 `erase()` 删除字符或字符串：

  ```cpp
  str.erase(0, 5);
  // 删除从索引0开始的5个字符
  ```

#### 字符串搜索和查找

- 查找字符或字符串的位置：

  ```cpp
  size_t pos = str.find('e');
  if (pos != std::string::npos) {
    // 找到了字符
  }
  ```

- 查找字符串的最后一次出现：

  ```cpp
  size_t pos = str.rfind('e');
  if (pos != std::string::npos) {
    // 找到了字符
  }
  ```

#### 字符串转换

- 转换为C风格字符串：

  ```cpp
  const char* cstr = str.c_str();
  ```

- 转换为其他数据类型（例如，整数、浮点数）：

  ```cpp
  int num = std::stoi(str);
  ```

#### 字符串格式化

- 使用 `std::ostringstream` 进行格式化：

  ```cpp
  std::ostringstream oss;
  oss << "The value is " << value;
  std::string formattedStr = oss.str();
  ```

这些是 `std::string` 类的一些基本操作。C++标准库提供了丰富的功能来处理字符串，可以根据需要使用这些功能来执行各种字符串操作。

## 5.24

### C++中string和int之间的相互转化

<center>关键词：类型转换：string和int<center>

在C++中，`std::string` 类型和 `int` 类型之间的相互转换可以通过以下几种方式实现：

#### 从 `int` 转换为 `std::string`

##### 通过 std::to_string() 函数转换

可以使用 `std::to_string` 函数将整数转换为字符串：

```cpp
#include <string>

int num = 123;
std::string str = std::to_string(num);
// str 现在是 "123"
```

##### 通过 ostringstream 转换

```cpp
#include <iostream>
#include <sstream>

int main()
{
    int num = 123;
    std::ostringstream ss;
    ss << num;
    std::cout << ss.str();
    return 0;
}
```

这是一种通过字符流的方式将整数转换成字符串，这种方式在C++11之前也可以使用。

##### 通过 sprintf 转换

```cpp
#include <stdio.h>

int main()
{
    int num = 123;
    char buffer[256];
    sprintf(buffer, "%d", num);

    printf("%s", buffer);
    return 0;
}
```

这是一种C语言中的转换方式，`sprintf` 也可以换成更安全的 `snprintf` 函数

#### 从 `std::string` 转换为 `int`

##### 通过 istringstream 转换

```cpp
#include <iostream>
#include <sstream>

int main()
{
    std::string str = "668";
    int num = 0;

    std::istringstream ss(str);
    ss >> num;

    std::cout << num;
    return 0;
}
```

使用 `istringstream` 可以从字符流中读取整数，与 `ostringstream` 是一种相反的操作

##### 使用 sscanf 来转化

```cpp
#include <iostream>
#include <stdio.h>

int main()
{
    std::string str = "668";
    int num = 0;

    sscanf(str.c_str(), "%d", &num);
    std::cout << num;
    return 0;
}
```

注意 `sscanf` 函数的第一个参数类型是 `const char *`，`string`类型的参数需要转换一下

##### 使用 atoi 转换

```cpp
#include <iostream>
#include <stdlib.h>

int main()
{
    std::string str = "668";
    std::cout << atoi(str.c_str());
    return 0;
}
```

`atoi` 函数的头文件是 `stdlib.h`，同样是一个C语言中的函数

##### 使用stoi转换

可以使用 `std::stoi` 函数将字符串转换为整数：

```cpp
#include <string>

std::string str = "123";
int num = std::stoi(str);
// num 现在是 123
```



#### 注意事项

- 在进行字符串到整数的转换时，如果字符串包含非数字字符，`std::stoi` 会抛出一个 `std::invalid_argument` 异常。如果字符串以数字开头，但后面有非数字字符，`std::stoi` 会抛出一个 `std::out_of_range` 异常。
- `std::to_string` 可以正确处理负数和正数的转换。

#### 示例代码

```cpp
#include <iostream>
#include <string>
#include <stdexcept>

int main() {
    // 从 int 转换为 string
    int number = -456;
    std::string numberStr = std::to_string(number);
    std::cout << "String: " << numberStr << std::endl;

    // 从 string 转换为 int
    std::string text = "7890";
    try {
        int number = std::stoi(text);
        std::cout << "Integer: " << number << std::endl;
    } catch (const std::invalid_argument& e) {
        std::cerr << "Invalid input: " << e.what() << std::endl;
    } catch (const std::out_of_range& e) {
        std::cerr << "Input out of range: " << e.what() << std::endl;
    }

    return 0;
}
```

在实际应用中，务必注意异常处理，以确保程序的健壮性。

### string转换为long long

<center>关键词：类型转换：string到longlong<center>

在C++中，`stoll` 是一个标准库函数，用于将字符串转换为 `long long` 类型的整数。这个函数位于 `<sstream>` 头文件中，因此在使用之前需要包含这个头文件。

`stoll` 函数的声明如下：

```cpp
long long stoll(const string& str, size_t* pos = 0, int base = 10);
```

参数说明：

- `str`：要转换的字符串。
- `pos`（可选）：指向 `size_t` 类型的指针，用于存储解析过程中到达的位置。如果提供了这个参数，转换将从 `str` 的这个位置开始，并且在转换完成后更新这个位置的值。如果转换失败，这个位置将被设置为0。
- `base`（可选）：数值基数，可以是2到36之间的任意值，表示字符串表示的数的进制。默认值为10，表示十进制。

使用 `stoll` 的示例：

```cpp
#include <iostream>
#include <sstream>
#include <string>

int main() {
    std::string str = "1234567890";
    long long result;

    // 转换十进制字符串
    result = std::stoll(str);
    std::cout << "Decimal string converted to long long: " << result << std::endl;

    // 转换十六进制字符串
    str = "1A3F";
    result = std::stoll(str, nullptr, 16);
    std::cout << "Hexadecimal string converted to long long: " << result << std::endl;

    return 0;
}
```

在这个示例中，我们首先将一个十进制的字符串转换为 `long long` 类型，然后转换一个十六进制的字符串。

如果字符串 `str` 不是一个有效的整数表示，或者它表示的数值超出了 `long long` 类型的范围，`stoll` 将抛出一个 `std::invalid_argument` 或 `std::out_of_range` 异常。因此，在使用 `stoll` 时，可能需要进行异常处理。

```cpp
try {
    std::string str = "1234abc";
    long long result = std::stoll(str);
} catch (const std::invalid_argument& e) {
    std::cerr << "Invalid argument: " << e.what() << '\n';
} catch (const std::out_of_range& e) {
    std::cerr << "Out of range: " << e.what() << '\n';
}
```

这将捕获并处理由 `stoll` 抛出的任何异常。

## 5.25

### 双端队列 deque

<center>关键词：双端队列<center>

<center>关键词：deque<center>

在 C++中，双端队列（deque，全称 double-ended queue）是一种类似于向量（vector）的序列容器，但它提供了在序列的两端快速添加（push）和删除（pop）元素的能力。双端队列通常通过某种形式的链表实现，这使得在两端进行操作的时间复杂度为 O(1)。

以下是 C++中使用双端队列的一些基本操作：

#### 包含头文件

```cpp
#include <deque>
```

#### 创建双端队列

```cpp
std::deque<int> deque;
```

#### 添加元素

- 在前端添加：

  ```cpp
  deque.push_front(10); // 在双端队列前端添加元素10
  ```

- 在后端添加：

  ```cpp
  deque.push_back(20); // 在双端队列后端添加元素20
  ```

#### 删除元素

- 从前端删除：

  ```cpp
  deque.pop_front(); // 删除双端队列前端的元素
  ```

- 从后端删除：

  ```cpp
  deque.pop_back(); // 删除双端队列后端的元素
  ```

#### 访问元素

- 访问第一个元素：

  ```cpp
  int frontElement = deque.front(); // 获取前端元素的值
  ```

- 访问最后一个元素：

  ```cpp
  int backElement = deque.back(); // 获取后端元素的值
  ```

#### 大小和容量

- 获取双端队列的大小：

  ```cpp
  size_t size = deque.size(); // 返回双端队列中的元素数量
  ```

- 检查双端队列是否为空：

  ```cpp
  bool isEmpty = deque.empty(); // 如果双端队列为空，则返回true
  ```

#### 遍历双端队列

```cpp
for (int elem : deque) {
    std::cout << elem << " ";
}
```

#### 例子

```cpp
#include <iostream>
#include <deque>

int main() {
    std::deque<int> d;

    // 添加元素
    d.push_back(10);
    d.push_back(20);
    d.push_front(30);

    // 访问元素
    std::cout << "Front element: " << d.front() << std::endl;
    std::cout << "Back element: " << d.back() << std::endl;

    // 删除元素
    d.pop_front();
    d.pop_back();

    // 遍历双端队列
    for (int elem : d) {
        std::cout << elem << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

输出将是：

```
Front element: 30
Back element: 20
20 
```

双端队列非常适合于需要在序列的两端进行操作的场景，例如实现队列或栈。与标准队列相比，双端队列提供了更大的灵活性。

### 优先队列 priority_queue

<center>关键词：优先队列<center>

<center>关键词：priority_queue<center>

在 C++中，`std::priority_queue` 是标准模板库（STL）中的一个容器适配器，它提供了一个优先队列的功能，其中元素按照特定的顺序自动排列。默认情况下，`std::priority_queue` 是一个最大堆，这意味着队列顶部（通过 `top()` 函数访问）的元素始终是最大的。

以下是 `std::priority_queue` 的一些关键特性和操作：

#### 包含头文件

要使用 `std::priority_queue`，你需要包含以下头文件：

```cpp
#include <queue>
```

#### 创建优先队列

创建一个 `std::priority_queue` 的实例：

```cpp
std::priority_queue<int> pq;
```

#### 插入元素

使用 `push()` 函数向优先队列中插入元素：

```cpp
pq.push(10);
pq.push(20);
```

#### 访问顶部元素

使用 `top()` 函数访问优先队列中的顶部元素（最大元素）：

```cpp
int topElement = pq.top();
```

#### 删除顶部元素

使用 `pop()` 函数从优先队列中删除顶部元素：

```cpp
pq.pop();
```

#### 检查队列是否为空

使用 `empty()` 函数检查优先队列是否为空：

```cpp
bool isEmpty = pq.empty();
```

#### 获取队列的大小

使用 `size()` 函数获取优先队列中的元素数量：

```cpp
size_t size = pq.size();
```

#### 自定义比较函数

可以通过模板参数自定义 `std::priority_queue` 的比较函数，以改变元素的排序方式（例如，改为最小堆）：

```cpp
#include <functional>

struct compare {
    bool operator()(int a, int b) {
        return a > b; // 改变为最小堆
    }
};

std::priority_queue<int, std::vector<int>, compare> minHeap;
```

#### 示例代码

```cpp
#include <iostream>
#include <queue>

int main() {
    std::priority_queue<int> pq;

    // 插入元素
    pq.push(30);
    pq.push(10);
    pq.push(20);

    // 访问并删除顶部元素
    while (!pq.empty()) {
        std::cout << pq.top() << " ";
        pq.pop();
    }

    return 0;
}
```

输出将是：

```
30 20 10 
```

`std::priority_queue` 在需要按照优先级处理元素的场景中非常有用，例如在任务调度、事件驱动模拟、Dijkstra 算法等算法中。然而，由于它是基于堆实现的，所以不支持随机访问，即不能高效地访问除了顶部之外的其他元素。此外，`std::priority_queue` 也不支持 `erase()` 操作或其他直接访问元素的操作。

### C++中的pair

<center>关键词：pair<center>

<center>关键词：键值对<center>

在C++中，`std::pair` 是一个模板类，用于表示一对元素的复合数据类型。它通常用于存储两个相关联的值，这两个值可以是不同的类型。`std::pair` 广泛用于标准库的容器和算法中，例如在关联容器（如 `std::map` 和 `std::multimap`）中存储键值对，或者在排序算法中返回两个元素的比较结果。

以下是 `std::pair` 的一些基本用法：

#### 包含头文件

要使用 `std::pair`，需要包含以下头文件：

```cpp
#include <utility>
```

#### 创建和初始化 `std::pair`

```cpp
// 使用构造函数创建 pair
std::pair<int, double> p(1, 3.14);

// 使用 make_pair 创建 pair，它是一个便捷函数
std::pair<int, std::string> p2 = std::make_pair(2, "C++");
```

#### 访问 `std::pair` 的元素

`std::pair` 提供了 `first` 和 `second` 两个成员变量来访问存储的值：

```cpp
int a = p.first;    // 获取第一个元素
double b = p.second; // 获取第二个元素

// 或者使用 make_pair 函数初始化并直接访问
int x = p2.first;
std::string y = p2.second;

vector<pair<int,int>> result;
//这样声明的数组访问元素是pair类型的键值对，再用first和second访问对应数值
cout<<result[3].first;
```

#### 使用 `std::pair` 作为函数返回类型

`std::pair` 可以作为函数的返回类型，用于一次返回两个值：

```cpp
std::pair<int, int> minMax(const std::vector<int>& vec) {
    if (vec.empty()) return std::make_pair(0, 0);
    
    int minVal = vec[0], maxVal = vec[0];
    for (int val : vec) {
        if (val < minVal) minVal = val;
        if (val > maxVal) maxVal = val;
    }
    return std::make_pair(minVal, maxVal);
}
```

#### 使用 `std::pair` 作为 `std::map` 的元素

`std::pair` 通常用作 `std::map` 的值类型，其中第一个元素是键（key），第二个元素是值（value）：

```cpp
std::map<std::string, int> myMap;
myMap["apple"] = 1;
myMap["banana"] = 2;

for (const auto& pair : myMap) {
    std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
}
```

#### 自定义比较函数

当使用 `std::pair` 作为 `std::sort` 或 `std::map` 等算法和容器的元素时，可以自定义比较函数：

```cpp
bool comparePairs(const std::pair<int, int>& a, const std::pair<int, int>& b) {
    return a.first < b.first;
}

// 使用自定义比较函数对 vector<pair> 进行排序
std::vector<std::pair<int, int>> vecOfPairs;
// ... 填充 vecOfPairs ...
std::sort(vecOfPairs.begin(), vecOfPairs.end(), comparePairs);
```

`std::pair` 是一个灵活且多用途的数据结构，它在C++标准库中扮演着重要的角色，特别是在需要同时返回或存储两个相关值的情况下。

### C++中的emplace函数

<center>关键词：emplace函数<center>

在C++中，`emplace` 是一种用于容器的函数，它允许你就地（in-place）构造容器中的元素，而不是先构造一个临时对象然后再将其复制或移动到容器中。`emplace` 方法通常用于避免不必要的复制或移动，从而提高性能。

`emplace` 函数在不同的容器中有不同的重载版本，但基本思想是相同的。以下是一些常见容器的 `emplace` 用法示例：

#### `std::vector` 和 `std::deque`

对于序列容器（如 `std::vector` 和 `std::deque`），`emplace` 通常用于在容器的末尾就地构造一个新元素。

```cpp
#include <vector>
#include <string>

int main() {
    std::vector<std::string> v;
    // 使用 emplace_back 构造一个新字符串
    v.emplace_back("Hello, World!");

    // 使用 emplace 和初始化列表构造一个新字符串
    v.emplace(1, "Hello,emplace");

    for (const auto& s : v) {
        std::cout << s << std::endl;
    }

    return 0;
}
```

#### `std::map` 和 `std::set`

对于关联容器（如 `std::map` 和 `std::set`），`emplace` 可以用于构造键值对或键。

```cpp
#include <map>

int main() {
    std::map<int, std::string> m;
    // 使用 emplace 构造一个键值对
    m.emplace(1, "one");

    // 使用 emplace 构造另一个键值对，带初始化列表
    m.emplace(std::piecewise_construct,
               std::forward_as_tuple(2),
               std::forward_as_tuple("two"));

    for (const auto& kv : m) {
        std::cout << "Key: " << kv.first << ", Value: " << kv.second << std::endl;
    }

    return 0;
}
```

#### `std::priority_queue`

对于 `std::priority_queue`，`emplace` 也可以用于就地构造元素，然后将其推入队列。

```cpp
#include <queue>

int main() {
    std::priority_queue<int> pq;
    // 使用 emplace 构造并推入一个整数
    pq.emplace(42);

    while (!pq.empty()) {
        std::cout << pq.top() << " ";
        pq.pop();
    }

    return 0;
}
```

#### 为什么使用 `emplace`？

使用 `emplace` 而不是 `push_back` 或 `insert` 的好处包括：

- **性能**：`emplace` 可以就地构造对象，避免了复制或移动构造函数的开销。
- **语义清晰**：`emplace` 明确表示元素是在容器中构造的，而不是从外部推入的。
- **支持复杂类型**：对于复杂或大型对象，使用 `emplace` 可以减少临时对象的创建，从而提高效率。

`emplace` 是C++11引入的特性，它提供了一种更现代、更高效的方法来构造容器中的元素。

## 5.26

### C++获取哈希表中值最大的前几个键

<center>关键词：哈希表排序<center>

#### 对哈希表全排列

在C++中，对哈希表（`std::unordered_map`）依据值大小进行排序，需要将哈希表的元素复制到另一个数据结构（如向量 `std::vector`）中，然后对这个数据结构中的元素进行排序。由于 `std::unordered_map` 并不保证元素的顺序，所以不能直接对其进行排序。

以下是对 `std::unordered_map` 依据值进行排序的步骤：

1. 创建 `std::unordered_map`

```cpp
std::unordered_map<Key, Value> umap;
```

2. 填充 `std::unordered_map`

```cpp
umap[key1] = value1;
umap[key2] = value2;
// ...
```

3. 复制到 `std::vector` 并排序

```cpp
#include <vector>
#include <algorithm> // std::sort

// 将 unordered_map 转换为 vector
std::vector<std::pair<Key, Value>> vec(umap.begin(), umap.end());

// 使用 std::sort 对 vector 进行排序
// 注意：这里使用自定义比较函数以根据值进行排序
std::sort(vec.begin(), vec.end(),
          [](const std::pair<Key, Value>& a, const std::pair<Key, Value>& b) {
              return a.second < b.second; // 对值进行升序排序
          });
```

4. 打印或使用排序后的 `std::vector`

```cpp
for (const auto& pair : vec) {
    std::cout << pair.first << " : " << pair.second << std::endl;
}
```

示例代码

```cpp
#include <iostream>
#include <unordered_map>
#include <vector>
#include <algorithm>

int main() {
    std::unordered_map<std::string, int> umap = {
        {"apple", 10},
        {"banana", 20},
        {"cherry", 15}
    };

    // 将 unordered_map 转换为 vector
    std::vector<std::pair<std::string, int>> vec(umap.begin(), umap.end());

    // 对 vector 进行排序（依据值）
    std::sort(vec.begin(), vec.end(),
              [&](const std::pair<std::string, int>& a, const std::pair<std::string, int>& b) {
                  return a.second < b.second; // 升序排序
              });

    // 打印排序后的 vector
    for (const auto& pair : vec) {
        std::cout << pair.first << " : " << pair.second << std::endl;
    }

    return 0;
}
```

输出将是：

```
apple : 10
cherry : 15
banana : 20
```

请注意，由于 `std::sort` 是一个稳定的排序算法，如果 `umap` 中有相同值的元素，它们在 `vec` 中的相对顺序将保持不变。

另外，如果你想要降序排序，只需更改比较函数中的 `<` 符号为 `>` 即可。此外，如果你**只需要排序前N个元素，可以使用 `std::partial_sort` 函数代替 `std::sort`。**

#### 排序哈希表前N个元素

在C++中，获取哈希表（如 `std::unordered_map`）中值最大的前N个键通常涉及以下步骤：

1. 遍历哈希表以收集所有键值对。
2. 使用适当的数据结构（如最小堆或排序向量）来找到最大的N个值。
3. 根据需要提取这些值对应的键。

这里有一个示例，演示如何找到 `std::unordered_map` 中值最大的前N个键：

```cpp
#include <iostream>
#include <unordered_map>
#include <vector>
#include <algorithm> // std::sort
#include <queue>     // std::priority_queue

int main() {
    // 示例哈希表
    std::unordered_map<std::string, int> umap = {
        {"apple", 10},
        {"banana", 20},
        {"cherry", 15},
        {"date", 30},
        {"elderberry", 5}
    };

    const int N = 3; // 我们想要的最大的键的数量
    std::vector<std::pair<std::string, int>> vec;

    // 将哈希表的键值对复制到向量中
    for (const auto& pair : umap) {
        vec.push_back(pair);
    }

    // 部分排序，只排序最大的N个元素
    std::partial_sort(vec.begin(), vec.begin() + N, vec.end(),
        [](const std::pair<std::string, int>& a, const std::pair<std::string, int>& b) {
            return a.second > b.second; // 降序排序
        });

    // 或者使用最小堆来找到最大的N个元素
    std::priority_queue<std::pair<std::string, int>, 
                        std::vector<std::pair<std::string, int>>, 
                        std::greater<std::pair<std::string, int>>> min_heap;

    for (const auto& pair : vec) {
        min_heap.push(pair);
    }

    // 从最小堆中提取最大的N个元素
    std::vector<std::pair<std::string, int>> topN;
    for (int i = 0; i < N; ++i) {
        topN.push_back(min_heap.top());
        min_heap.pop();
    }

    // 打印结果
    for (const auto& pair : topN) {
        std::cout << pair.first << " : " << pair.second << std::endl;
    }

    return 0;
}
```

在这个示例中，我们首先将 `std::unordered_map` 的内容复制到一个 `std::vector` 中，然后使用 `std::partial_sort` 函数对前N个元素进行排序，以找到最大的N个键值对。或者，我们也可以使用 `std::priority_queue`（最小堆）来有效地找到最大的N个键值对。

请注意，`std::partial_sort` 会部分排序整个向量，只确保前N个元素是最大的。而 `std::priority_queue` 则提供了一种更有效的方法来处理这个问题，特别是当N远小于哈希表的大小时。在这个示例中，我们使用最小堆（通过 `std::greater` 比较函数）来自动保持最大的元素在堆的顶部。

### 优先队列

<center>关键词：优先队列<center>

<center>关键词：priority_queue<center>

在C++中，`std::priority_queue` 是标准模板库（STL）中提供的一个容器适配器，它用来实现优先队列。优先队列是一种特殊的队列，元素出队的顺序是根据优先级决定的，而不是入队的顺序。在 `std::priority_queue` 中，默认情况下元素是按最大堆的性质组织的，即队首（top 元素）始终是当前队列中的最大元素。

以下是 `std::priority_queue` 的一些基本用法：

#### 包含头文件

```cpp
#include <queue>
#include <vector>
#include <iostream>
```

#### 定义优先队列

```cpp
priotiry_queuq<Type,Container.Functional>;
//Type是要存放的数据类型
//Container是实现底层堆的容器，必须是数组实现的容器，比如vector,deque
//Functional是比较方式/比较函数/优先级
priority_queue<type>;
//此时默认容器为vector，默认的比较方式是大顶堆 less<type>
```

#### 创建优先队列

```cpp
std::priority_queue<int> pq;

//小顶堆
priority_queue <int,vector<int>,greater<int> > q;
//大顶堆
priority_queue <int,vector<int>,less<int> >q;
//默认大顶堆
priority_queue<int> a;
```

#### 插入元素push

使用 `push()` 方法向优先队列中插入元素：

```cpp
pq.push(10);
pq.push(20);
```

#### 插入元素emplace

emplace用于就地构造元素，然后将其推入队列

```cpp
#include <queue>

int main() {
    std::priority_queue<int> pq;
    // 使用 emplace 构造并推入一个整数
    pq.emplace(42);

    while (!pq.empty()) {
        std::cout << pq.top() << " ";
        pq.pop();
    }

    return 0;
}
```

#### 访问顶部元素top

使用 `top()` 方法访问优先队列中的顶部元素（最大元素）：

```cpp
int topElement = pq.top();
```

#### 删除顶部元素pop

使用 `pop()` 方法从优先队列中删除顶部元素：

```cpp
pq.pop();
```

#### 检查队列是否为空empty

使用 `empty()` 方法检查优先队列是否为空：

```cpp
bool isEmpty = pq.empty();
```

#### 获取队列的大小

使用 `size()` 方法获取优先队列中的元素数量：

```cpp
size_t size = pq.size();
```

#### 自定义比较函数

可以通过模板参数自定义 `std::priority_queue` 的比较函数，以改变元素的排序方式（例如，改为最小堆）：

```cpp
#include <functional>

struct compare {
    bool operator()(int a, int b) {
        return a > b; // 改变为最小堆
    }
};

std::priority_queue<int, std::vector<int>, compare> minHeap;
```

当数据类型并不是基本数据类型，而是自定义的数据类型时，就不能用greater或less的比较方式了，而是需要自定义比较方式。在此假设数据类型是自定义的水果：

```cpp
struct fruit{
    string name;
    int price;
};
```

有两种自定义比较方法，如下：

##### 重载运算符

重载''<''

若希望水果价格高为优先级高，则

```cpp
//大顶堆
struct fruit
{
	string name;
	int price;
	friend bool operator < (fruit f1,fruit f2)
	{
		return f1.peice < f2.price;
	}
};
```

若希望水果价格低为优先级高

```python
//小顶堆
struct fruit
{
    string name;
    int price;
    friend bool operator < (fruit f1,fruit f2)
    {
        return f1.peice > f2.price;//此处是大于号
    }
};
```

##### 仿函数

若希望水果价格高为优先级高，则

```cpp
//大顶堆
struct myComparison
{
	bool operator () (fruit f1,fruit f2)
	{
		return f1.price < f2.price;
	}
};

//此时优先队列的定义应该如下
priority_queue<fruit,vector<fruit>,myComparison> q;
```

#### 示例代码

```cpp
int main() {
    std::priority_queue<int> pq;

    // 插入元素
    pq.push(30);
    pq.push(10);
    pq.push(20);

    // 访问并删除顶部元素
    while (!pq.empty()) {
        std::cout << pq.top() << " "; // 访问顶部元素
        pq.pop(); // 删除顶部元素
    }

    return 0;
}
```

输出将是：

```
30 20 10 
```

```cpp
priority_queue<pair<int, int> > a;
pair<int, int> b(1, 2);
pair<int, int> c(1, 3);
pair<int, int> d(2, 5);
a.push(d);
a.push(c);
a.push(b);
while (!a.empty()) 
{
   cout << a.top().first << ' ' << a.top().second << '\n';
   a.pop();
}
//输出结果为：
2 5
1 3
1 2
```

`std::priority_queue` 在需要根据优先级处理元素的场景中非常有用，例如在任务调度、事件驱动模拟、Dijkstra算法等算法中。然而，由于它是基于堆实现的，所以不支持随机访问，即不能高效地访问除了顶部之外的其他元素。此外，`std::priority_queue` 也不支持 `erase()` 操作或其他直接访问元素的操作。

### decltype关键字及应用

<center>关键词：decltype<center>

<center>关键词：推断类型<center>

在C++中，`decltype` 是一个关键字，用于推断表达式的类型。它常用于模板编程中，以便编写与模板参数类型相关的代码，而不需要事先知道这些类型具体是什么。`decltype` 的基本用法如下：

#### 基本语法

```cpp
decltype(expression) variable;
```

这里，`expression` 是你要推断类型的表达式，`variable` 是用来存储推断出来的类型的变量。

#### 示例

假设我们有一个变量，并希望创建一个类型与之相同的新变量：

```cpp
int a = 10;
decltype(a) b; // b 的类型被推断为 int
```

#### 与 decltype 关键字相关的几个要点：

1. **类型推断**：`decltype` 根据其参数的类型来推断类型。如果 `decltype` 的参数是一个未命名的值，那么 `decltype` 推断其类型但不包括顶层的引用修饰符。如果参数是一个变量，那么 `decltype` 会推断其类型，包括引用修饰符。

2. **顶层 const**：如果表达式是一个顶层 `const` 值，`decltype` 会忽略这个 `const`。例如：

   ```cpp
   const int ci = 10;
   decltype(ci) b; // b 的类型是 int, 而不是 const int
   ```

3. **引用类型**：如果表达式的结果是一个引用，`decltype` 会推断出引用类型：

   ```cpp
   int a = 10;
   int& ref = a;
   decltype(ref) b; // b 的类型是 int&
   ```

4. **指针类型**：如果表达式是一个指针，`decltype` 会推断出指针类型：

   ```cpp
   int* p = nullptr;
   decltype(p) q; // q 的类型是 int*
   ```

5. **函数类型**：如果表达式是一个函数调用，`decltype` 会推断出函数的返回类型：

   ```cpp
   int func() { return 1; }
   decltype(func()) a; // a 的类型是 int
   ```

6. **类成员函数**：对于类的成员函数，`decltype` 会推断出成员函数的类型（返回类型加 const 修饰符，如果有的话）：

   ```cpp
   class MyClass {
   public:
       void myMethod() const {}
   };
   
   MyClass myObject;
   decltype(myObject.myMethod) a; // a 的类型是 void (MyClass::*)() const
   ```

7. **decltype(auto)**：C++14 引入了 `decltype(auto)`，它用于自动推断类型，特别适用于 lambda 表达式和 decltype 的递归推断：

   ```cpp
   auto x = 5;
   decltype(auto) y = x; // y 被推断为 int
   ```

8. **模板参数**：`decltype` 可以用于模板参数中，以推断模板实参的类型：

   ```cpp
   template <typename T>
   void func(T t) {
       decltype(t) copy = t;
   }
   ```

`decltype` 是一个非常有用的工具，特别是在模板编程中，它允许程序员编写更灵活和通用的代码，同时保持类型安全。

在 C++ 中，`decltype` 是一个关键字，用于推断对象的类型。`decltype(&cmp)` 的作用是获取函数 `cmp` 的地址的类型。这里 `cmp` 是一个静态成员函数，其地址用作 `priority_queue` 的第三个模板参数，以指定优先队列中元素的比较方式。

让我们分解第 14 行代码：

```cpp
priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(&cmp)> q(cmp);
```

- `priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(&cmp)>`：这部分声明了一个 `priority_queue` 的类型。队列中的元素是 `pair<int, int>` 类型，即包含两个 `int` 的对。`vector<pair<int, int>>` 是存储这些对的底层容器类型。`decltype(&cmp)` 是指定自定义比较逻辑的函数或函数对象的类型，这里它是 `cmp` 函数地址的类型。

- `q(cmp)`：这里 `cmp` 函数被用作初始化参数传递给 `priority_queue` 的构造函数。由于 `cmp` 是一个静态成员函数，它需要被显式地绑定到类上（即 `Solution::cmp`），但在这种场景下，通常可以省略，因为构造函数能够推断出函数的正确地址。

为什么要这样写？这是因为 `priority_queue` 需要一个比较操作来确定元素的顺序。在这种情况下，我们想要一个最小堆，其中元素根据它们的第二个成员（即出现次数）来排序，但是 `priority_queue` 默认创建一个最大堆。为了反转元素的排序，我们提供一个自定义的比较函数 `cmp`，它告诉 `priority_queue` 当一个元素的第二个成员（出现次数）更大时，它应该排在前面。

自定义比较可以通过以下两种方式之一提供：

1. 使用函数对象（如 lambda 表达式）：

   ```cpp
   priority_queue<pair<int, int>, vector<pair<int, int>>, function<bool(const pair<int, int>&, const pair<int, int>&)>> q([](const pair<int, int>& a, const pair<int, int>& b) { return a.second > b.second; });
   ```

2. 使用函数的地址，像在示例代码中那样使用 `decltype(&cmp)`。

在示例代码中，使用 `decltype(&cmp)` 是为了明确指定比较函数的类型，并将其地址传递给 `priority_queue`。这是一种显式的类型转换，有助于代码的清晰性和可读性，尤其是在复杂的模板代码中。然而，通常可以省略 `decltype` 并直接使用函数名，因为编译器能够推断出正确的类型。例如：

```cpp
priority_queue<pair<int, int>, vector<pair<int, int>>, bool(*)(pair<int, int>&, pair<int, int>&)> q(cmp);
```

或者，如果函数是全局的或静态的，并且上下文足够明确，可以直接传递函数名：

```cpp
priority_queue<pair<int, int>, vector<pair<int, int>>, bool(*)(pair<int, int>&, pair<int, int>&)> q(cmp);
```

在 C++14 及以后的版本中，由于类型推断的改进，可以直接使用 `cmp` 作为比较函数，而不需要显式指定类型。

## 5.27

### 二叉树

<center>关键词：二叉树<center>

#### 二叉树的定义

```cpp
struct TreeNode{
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x): val(x), left(NULL), right(NULL){}
};
```

#### 二叉树的递归遍历

前置：递归算法三要素：

1. **确定递归函数的参数和返回值**：确定哪些参数是递归的过程中需要处理的，那么就在递归函数里加上这个参数， 并且还要明确每次递归的返回值是什么进而确定递归函数的返回类型。
2. **确定终止条件**：写完了递归算法, 运行的时候，经常会遇到栈溢出的错误，就是没写终止条件或者终止条件写的不对，操作系统也是用一个栈的结构来保存每一层递归的信息，如果递归没有终止，操作系统的内存栈必然就会溢出。
3. **确定单层递归的逻辑**： 确定每一层递归需要处理的信息。在这里也就会重复调用自己来实现递归的过程。

##### 先序遍历

```cpp
class Solution{
public:
    //确定递归函数的参数和返回值：因为要打印出前序遍历节点的数值，所以参数里需要传入vector来放节点的数值，除了这一点就不需要再处理什么数据了也不需要有返回值，所以递归函数返回类型就是void
	void traversal(TreeNode* cur,vector<int>& vec){
        //确定终止条件：在递归的过程中，如何算是递归结束了呢，当然是当前遍历的节点是空了，那么本层递归就要结束了，所以如果当前遍历的这个节点是空，就直接return
        if(cur == NULL)	return;
        //确定单层递归的逻辑：前序遍历是中左右的循序，所以在单层递归的逻辑，是要先取中节点的数值
        vec.push_back(cur->val);//中
        traversal(cur->left,vec);//左
        traversal(cur->right,vec);//右
    }
    vector<int> preorderTraversal(TreeNode* root){
        vector<int> result;
        traversal(root,result);
        return result;
    }
};
```

##### 中序遍历：

```cpp
void traversal(TreeNode* cur, vector<int>& vec){
    if(cur==NULL)	return;
    traversal(cur->left,vec);
    vec.push_back(cur->val);
    traversal(cur->right,vec);
}
```

##### 后续遍历

```cpp
void traversal(TreeNode* cur, vector<int>& vec){
    if(cur==NULL)	return;
    traversal(cur->left,vec);
    traversal(cur->right,vec);
    vec.push_back(cur->val);
}
```

