# 复合数据类型

容器类型指的就是列表\(list\)、元组\(tuple\)、字典\(dict\)、集合\(set\)，所谓容器就是能容纳大量个体元素的对象。上述的所有数据类型都是Python内置的数据类型。

序列是Python中最基本的一种数据结构，用于保存一组有序的数据，所有的数据在序列中都有一个唯一的索引。

分类：

* 可变序列（序列中的元素可以改变）：列表（list）  
* 不可变序列（序列中的元素不能改变）：字符串（str）、元组（tuple）

## 列表list

list是一种有序的集合，是一种对象，可以用来保存多个有序的数据。

列表是用来存储对象的对象： 列表主要用来存储数据，是数据的容器，可以通过列表的索引来操作数据。

1. 通过`[]`就可以创建一个列表

   ```python
   my_list = [] # 创建了一个空列表
   print(my_list , type(my_list))# [] <class 'list'>
   ```

2. 列表基础
   * 列表存储的数据，称为元素。元素之间使用`,`间隔。

     ```python
     my_list = [10,20,30,40,50] # 创建了一个有5个元素的列表
     ```

   * 列表中可以保存任意的对象，包括函数、方法； 列表中的对象会按插入的顺序存储到列表中 。
   * 通过索引获取列表中的元素，通过len（）获取列表的长度。

     ```python
     my_list = [10,20,30,40,50]
     my_list[0]  
     print(my_list[4]) # 50
     ```
3. 列表切片

   切片可以简化对于列表的操作

   使用**列表名\[起始：结束\]**方法

   * 通过切片获取元素时，会包括起始位置的元素，但是不会包括结束位置的元素
   * 切片操作时，总会返回一个新的列表，不会影响原来的列表
   * 起始和结束位置的索引都可以省略不写，省略结束位置，则会一直截取到最后。省略起始位置，则会从第一个元素开始截取。起始位置和结束位置全部省略，则相当于创建了一个列表的副本。

     ```python
     stus = ['Ana','Tim','Bill','Juan','aploe']
     print(stus[1:]) #  ['Tim', 'Bill', 'Juan', 'aploe']
     print(stus[:3]) #  ['Ana', 'Tim', 'Bill']
     print(stus[:]) # ['Ana', 'Tim', 'Bill', 'Juan', 'aploe']
     print(stus) # ['Ana', 'Tim', 'Bill', 'Juan', 'aploe']
     ```

   使用**列表\[起始:结束:步长\]**方法

   ​ 步长表示每次获取元素的间隔，默认值是1。步长不能是0，但是可以是负数。 如果是负数，则会从列表的后部向前边取元素，如果是-1，则反置列表。

   ```python
   print(stus[::0]) ValueError: slice step cannot be zero
   stus = ['Ana','Tim','Bill','Juan','aploe']
   print(stus[0:5:3]) #['Ana', 'Juan']
   print(stus[::-1]) #['aploe', 'Juan', 'Bill', 'Tim', 'Ana']
   ```

4. 序列通用方法
   * `+`号可以将两个列表拼接为一个列表；`*` 可以将列表重复指定的次数。
   * `in`和`not in` ，`in`用来检查指定元素是否存在于列表中, 如果存在，返回True，否则返回False，`not in`刚好相反。

     ```python
     stus = ['孙悟空','猪八戒','沙和尚','唐僧','蜘蛛精','白骨精','沙和尚','沙和尚']
     print('牛魔王' not in stus)# True
     print('牛魔王' in stus)# False
     ```

   * `len()`、 `min()`和`max()`函数
   * `s.index()` 方法用于获取指定元素在列表中的第一次出现时索引

     ```python
     stus = ['孙悟空','猪八戒','沙和尚','唐僧','蜘蛛精','白骨精','沙和尚','沙和尚']
     print(stus.index('沙和尚'))# 结果为2
     ```

     `index()`的参数：第一个参数表示需要查找的对象，第二个参数，表示查找的起始位置 ， 第三个参数，表示查找的结束位置。

     ```python
     stus = ['孙悟空','猪八戒','沙和尚','唐僧','蜘蛛精','白骨精','沙和尚','沙和尚']
     print(stus.index('沙和尚',3,7)) # 6
     ```

* `s.count()` 统计指定元素在列表中出现的次数

  ```python
  stus = ['Ana','Tim','Tim','Bill','Juan','Tim','aploe']
  print(stus.count('Tim')) #3
  ```

1. 修改列表元素
   * 使用索引来引用或修改元素
   * 通过del删除元素

     ```python
     stus = ['Ana','Tim','Bill','Juan','aploe']
     del stus[2] # 删除索引为2的元素
     print(stus) # ['Ana', 'Tim', 'Juan', 'aploe']
     ```

   * 使用切片操作修改元素，简化操作

     1. 在给切片进行赋值时，只能使用序列  

     ```python
     stus = ['孙悟空','猪八戒','沙和尚','唐僧','蜘蛛精','白骨精']
     stus[0:2] = ['牛魔王','红孩儿'] 使用新的元素替换旧元素
     stus[0:2] = ['牛魔王','红孩儿','二郎神']
     stus[0:0] = ['牛魔王'] # 向索引为0的位置插入元素
     # 当设置了步长时，序列中元素的个数必须和切片中元素的个数一致
     stus[::2] = ['牛魔王','红孩儿','二郎神']
     ```

     * 通过切片达到删除元素的目的

     ```python
     stus = ['Ana','Tim','Bill','Juan','aploe']
     del stus[0:2]
     print(stus) #['Bill', 'Juan', 'aploe']

     stus = ['Ana','Tim','Bill','Juan','aploe']
     del stus[::2]
     print(stus) #['Tim', 'Juan']

     stus = ['Ana','Tim','Bill','Juan','aploe']
     stus[1:3] = []
     print(stus) #['Ana', 'Juan', 'aploe']
     ```

以上的所有操作，只适用于可变序列,不可变序列，无法通过索引来修改；可以通过 `list()` 函数将其他的序列转换为`list`，然后进行修改。

```python
s = 'hello'
s[1] = 'a' #TypeError: 'str' object does not support item assignment

s = list(s)
print(s)
```

### 列表的方法

1. `append()`，向列表的末尾添加一个元素

   ```python
   stus = ['Ana','Tim','Bill','Juan','aploe']
   stus.append('DEAR')
   print(stus) # ['Ana', 'Tim', 'Bill', 'Juan', 'aploe', 'DEAR']
   ```

2. `insert()`，向列表的指定位置插入一个元素

   ```python
   stus = ['Ana','Tim','Bill','Juan','aploe']
   stus.insert(0,'DEAR')
   print(stus) # ['DEAR', 'Ana', 'Tim', 'Bill', 'Juan', 'aploe']
   ```

3. `extend()`，扩展当前序列

   需要一个序列作为参数，它会将该序列中的元素添加到当前列表中

   ```python
   stus.extend(['唐僧','白骨精'])  
   # 相当于：
   stus += ['唐僧','白骨精']
   ```

4. `clear()`，直接清空整个序列

   ```python
   stus = ['Ana','Tim','Bill','Juan','aploe']
   stus.clear()
   print(stus) #[]
   ```

5. `pop()`，根据索引删除元素并将其返回

   ```python
   stus = ['Ana','Tim','Bill','Juan','aploe']
   result = stus.pop(2) # 删除索引为2的元素
   result = stus.pop() # 删除最后一个
   print('result =',result) #result = aploe
   ```

6. `remove()`，根据值来删除元素

   如果相同值得元素有多个，只会删除第一个

7. `sort()`，对列表进行排序，默认是升序

   降序排列则需要传递`reverse=True`作为参数

### 遍历列表

1. 通过循环语句有while或for遍历

   ```python
   # 通过while循环来遍历列表
   stus = ['Ana','Tim','Bill','Juan','aploe']
   i = 0
   while i < len(stus):
       print(stus[i])
       i += 1
   ```

   通过for循环遍历列表，循环体中的代码块会执行多次，序列中有几个元素就会执行几次。每执行一次就会将序列中的一个元素赋值给变量，所以我们可以通过变量，来获取列表中的元素。

   ```python
   # 语法：  
   for 变量 in 序列 :  
       代码块 
   stus = ['Ana','Tim','Bill','Juan','aploe']
   for s in stus :
       print(s)
   ```

2. 通过range\(\)执行指定次数的for循环

   `range()`是一个函数，用自然数序列的生成

   该函数需要三个参数 ： 1.起始位置（可以省略，默认是0） 2.结束位置 3.步长（可以省略，默认是1）

   ```python
   r = range(5) # 生成一个这样的序列[0,1,2,3,4]
   print(list(r)) # 输出序列[0,1,2,3,4]

   for i in range(30):
       print(i)
   ```

## 元组tuple

元组是另一种有序列表，但与list不同，tuple一旦初始化就不能修改。所以没有append\(\)，insert\(\)这样的方法，获取元素的方法和list是一样的，因为tuple不可变，所以数据更安全。

元组tuple是一个不可变的序列，它的操作方式基本和列表一致，在操作元组时，把元组当成一个不可变的列表即可。一般当不希望数据改变时，就使用元组。

* 使用`()`来创建元组

```python
my_tuple = () # 创建了一个空元组
print(my_tuple,type(my_tuple)) # <class 'tuple'>
```

元组是不可变对象，不能尝试为元组中的元素重新赋值，否者出错

```python
my_tuple = (1,2,3,4,5) # 创建了一个5个元素的元组
my_tuple[3] = 10 TypeError: 'tuple' object does not support item assignment
print(my_tuple[3])# 运行结果为4
```

元组的括号可以省略，但不建议

* 元组的解构

解构指指将元组当中每一个元素都赋值给一个变量。

```python
  my_tuple = 10 , 20 , 30 , 40
  a,b,c,d = my_tuple
  print("a =",a)# a = 10
  print("b =",b)# b = 20
  print("c =",c)# c = 30
  print("d =",d)# d = 40
```

利用解构可以交换a 和 b的值

```python
  a = 100
  b = 300
  print(a , b)
  # 100 300
  a , b = b , a
  print(a , b)
  # 300 100
```

解包时，变量的数量必须和元组中的元素的数量一致。可以在变量前边添加一个`*`，这样变量将会获取元组中所有剩余的元素。不能同时出现两个或以上的`*`变量。

```python
  my_tuple = 10 , 20 , 30 , 40

  a , b , *c = my_tuple
  a , *b , c = my_tuple
  *a , b , c = my_tuple

  # a = 10
  # b = 20
  # c = [30, 40]

  # a = 10
  # b = [20, 30]
  # c = 40

  # a = [10, 20]
  # b = 30
  # c = 40
```

不仅是元组能够解构，列表序列都可以解构。

```python
  a , b , *c = [1,2,3,4,5,6,7]
  # a = 1
  # b = 2
  # c = [3, 4, 5, 6, 7]

  a , b , *c = 'hello world'
  # a = h
  # b = e
  # c = ['l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd']
```

tuple所谓的“不变”是说，tuple的每个元素，指向永远不变。如何理解指向永远不变这个意思呢，那有没有特殊的例子呢？当然是有的。假设我们有如下一个元组

```python
 t = ('a', 'b', ['A', 'B'])
```

t中有三个元素 a、 b、 list\['A','B'\]，如果我们做如下操作

```python
    t[2][0] = 'X'
    t[2][1] = 'Y'
    print(t)
```

你知道会发生什么嘛？答案是 \('a', 'b', \['X', 'Y'\]\)。

有没有很奇怪，不是说元组是不变的序列吗。为什么此时元组的内容却发生了改变？别急，tuple所谓的“不变”是说，tuple的每个元素，指向永远不变。即指向'a'，就不能改成指向'b'，指向一个list，就不能改成指向其他对象，但指向的这个list本身是可变的！

list和tuple是Python内置的有序集合，一个可变，一个不可变。他们的操作方法大致相同，适用于list的都可以在tuple。

## 集合set

集合和列表非常相似，不同点在于：

1.集合中只能存储不可变对象

2.集合中存储的对象是无序（不是按照元素的插入顺序保存）

3.集合中不能出现重复的元素

* 使用`{}` 来创建集合

```python
s={1,2,3}
print(s) #{1, 2, 3}
# 错误示例:
s = {10,3,5,1,2,1,2,3,1,1,1,1} #输出{1, 2, 3, 5, 10}
```

**集合具有数学上集合的独一性，样本集合中的所有数据都是不一样的**

* 使用 `set()` 函数创建集合

```python
s = set() # 空集合
s = set([1,2,3,4,5,1,1,2,3,4,5])
s = set('hello')
s = set({'a':1,'b':2,'c':3}) # 使用set()将字典转换为集合时，只会包含字典中的键
print(s)
# {1, 2, 3, 4, 5}
# {'o', 'l', 'e', 'h'}
# {'a', 'b', 'c'}
```

* `in`和`not in`检查集合中的元素

```python
s = {'hello'}
print('c' in s )# False
print('c' not in s) # True
```

* 集合的基本方法
  1. 使用len\(\)获取集合中元素的数量
  2. 使用add\(\)向集合中添加元素
  3. 使用pop\(\)随机删除集合中的一个元素并返回
  4. 使用remove\(\)删除集合中的指定元素
  5. 使用clear\(\)清空集合
  6. 使用copy\(\)对集合进行浅复制
  7. 使用update\(\) 将一个集合中的元素添加到当前集合中

```python
s = {'world'}    # {'world'}
s2 = set('hello')    # {'o', 'l', 'h', 'e'}
s.update(s2)    # {'l', 'world', 'o', 'e', 'h'}
s.update((10,20,30,40,50))    # {'world', 'e', 10, 20, 'o', 'h', 30, 40, 'l', 50}
s.update({10:'ab',20:'bc',100:'cd',1000:'ef'})
print(s)# {'world', 'e', 10, 20, 'o', 'h', 30, 100, 40, 1000, 'l', 50}
# update()可以传递序列或字典作为参数，字典只能使用键
```

### 集合的数学运算

在对集合做运算时，不会影响原来的集合，对原集合不做任何改变，而是返回一个运算结果。

首先创建两个集合`A`&`B`

```text
A = {1,2,3,4,5}
B = {3,4,5,6,7}
```

* `&` 交集运算

```text
result = A & B  # {3, 4, 5}
```

* `|` 并集运算

```text
result = A | B # {1,2,3,4,5,6,7}
```

* `-` 差集

  result = A - B \# {1, 2}

* `^` 异或运算 获取集合（两个或多个）中不同的原素

```text
result = A ^ B # {1, 2, 6, 7}
```

* `<=`运算 

  检查一个集合是否是另一个集合的子集    

如果a集合中的元素全部都在b集合中出现，那么a集合就是b集合的子集，b集合是a集合超集

```python
a = {1,2,3}
b = {1,2,3,4,5}
result = a <= b # True
result = {1,2,3} <= {1,2,3} # True
result = {1,2,3,4,5} <= {1,2,3} # False
```

* `<`运算

检查一个集合是否是另一个集合的真子集

```python
# 如果超集b中含有子集a中所有元素，
# 并且b中还有a中没有的元素，
# 则b就是a的真超集，a是b的真子集
result = {1,2,3} < {1,2,3} # False
result = {1,2,3} < {1,2,3,4,5} # True
```

* `>=`运算

  检查一个集合是否是另一个的超集

* `>`运算 

  检查一个集合是否是另一个的真超集

## 字典dict

字典也是Python内置的一种数据结构，称为映射（mapping），使用键-值（key-value）存储，具有极快的查找速度。

具备快速查找能力的原因是，字典在存储数据的时候都是根据key算出value的存放位置（哈希查找）这样，取的时候直接根据key拿到value。

hash查找：dict内部存放的顺序和key放入的顺序没有关系。一个key只能对应于一个value，多一个key放入多个value，后面的值会把前面的值冲掉。

和list比较，dict有以下几个特点：

* 查找和插入的速度极快，不会随着key的增加而变慢；
* 需要占用大量的内存，内存浪费（由字典的机制决定）

在程序中，通常时间和空间是两个对立的方面，时间消耗少，内存开销就大；内存开销小，时间花费就越多。

字典的作用和列表类似，都是用来存储对象的容器。列表存储性能很好，但是查询效率太低，字典查询效率高。

字典，我们也称为叫做键值对（key-value）结构`key:value`，字典是对象的存储列表。

1. **使用 {} 来创建字典 {key:value,key:value,key:value}**

   字典的值可以是任意对象 ，字典的键只能是不变对象，一般使用str。

2. **使用 dict\(\)函数来创建字典** dict\(name='孙悟空',age=18,gender='男'\)

   dict函数也可以将一个包含有双值子序列的序列转换为字典

   ```python
   d = dict([('name','孙悟饭'),('age',18)])
   print(d , type(d))#{'name': '孙悟饭', 'age': 18} <class 'dict'>
   ```

3. len\(\) &&in

   len\(\) 获取字典中键值对的个数，in 检查字典中是否包含指定的键 。

4. del&&clear

   del 删除字典中的 key-value，clear\(\)用来清空字典。

5. copy\(\)用于对字典进行浅复制

   复制以后的对象，和原对象是独立，修改一个不会影响另一个。

6. keys\(\) 方法会返回字典的所有的key ，values\(\)来获取所有的值。
7. items\(\) 该方法会返回字典中所有的项 （key-value）

