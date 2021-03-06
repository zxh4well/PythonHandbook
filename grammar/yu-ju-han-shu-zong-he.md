# 语句函数综合

## 语句

程序就是一条条的语句，编译器或者解释器将语句翻译成机器码，通过CPU执行。

Python程序中每一行代码就是一条独立的语句，通过严格的缩进来控制语法结构。顺序、选择、循环，是程序的基本逻辑，编写程序实际上是在编写这三种逻辑的组合。

**顺序语句**：语句顺序执行，呈现线性结构。

![&#x4F9D;&#x6B21; 2020-02-06 213548.png](https://i.loli.net/2020/02/06/3AJ21d74Ye8KoLk.png)

**选择语句**：根据条件判断执行，会产生指向跳转。

![fgsdfdaf](https://i.loli.net/2020/07/17/jg9SKwuNk7InCbL.png)

```python
age = input('请输入你的年龄：')
if int(age) <= 18:
    print('teenager')
else:
    print('adult')
```

**循环语句**：根据条件判断执行，循环体被循环执行。

![dasdasdas](https://i.loli.net/2020/07/17/VmLjprWgJ8D3PAz.png)

循环语句常使用for或者while，do-while来实现；break和continue用于跳出循环。

## 函数

函数是用于执行某些特定行为的语句集合，可实现代码重用和功能模块化。

函数具有参数，python中的参数可以是变量（var）也可以是函数、方法（function、methdel）。

### **def**关键字用于函数的创建：

```python
def 函数名([形参1,形参2,...形参n]) :
        代码块
```

函数中保存的代码不会立即执行，需要**调用**函数代码才会执行。

```python
#创建一个求和函数
def function_sum(num1,num2) :
    print('num1 + num2 = %d'%(num1+num2))
#调用函数
function_sum(100,200) #num1 + num2 = 300
```

### **函数参数：**位置参数、默认参数、关键字参数、不定长参数

1. 位置参数：实参和形参一一对应，顺序不能颠倒

   ```python
   #定义一个say_age函数：可以告诉你的年龄
   def say_age(name,age) :
       print('hi!%s,you are %d years old.'%(name,age))
   #调用函数
   say_age('Tim',18)# hi!Tim,you are 18 years old.
   ```

2. 默认参数：指定形参时给参数设定的默认值

   默认参数在**没有**传递参数时才会起效，传递了参数则以传递的参数为准。

   默认参数也需要服从参数的位置对应的条件。

   ```python
   def adime(name='Tim',age=18,gender='男') :
       print('I am %s,%d years old,性别%s' %(name,age,gender))
   adime('张三',70,'女') #I am 张三,70 years old,性别女
   # adime(70,'男') #TypeError: %d format: a number is required, not str
   adime('张三',70)#I am 张三,70 years old,性别男
   adime('张三')#I am 张三,18 years old,性别男
   adime()#I am Tim,18 years old,性别男
   ```

3. 关键字参数：**不按照**形参定义的顺序传递参数，而是直接根据参数名传递参数

   ```python
   def people(name,age,gender):
       print(name)
       print(age)
       print(gender)

   people(name='Danile',gender='女',age=18)
   # Danile
   # 18
   # 女
   ```

   默认参数和关键字参数方法可以混合使用。位置参数和关键字参数可以混合使用；混合使用时，必须将位置参数写到前面。

4. 不定长参数：可变参数，传入的参数个数是可变的。

   在定义函数时，可以在形参前边加上一个\*，这样这个形参将会获取到所有的实参；并且将会将所有的实参保存到一个元组中（装包）

   ```python
   def sum(*num) :
       print(num) #(1, 2, 3, 4, 5, 6, 7)
       result = 0
       for i in num :
           result += i
       return result

   nums = sum(1,2,3,4,5,6,7)
   print(nums) #28
   ```

   可变参数可以和其他参数混合使用，可变参数不是必须写在最后。

   注意，**带\*的参数后**的所有参数，必须以关键字参数的形式传递。

   ```python
   # 所有的位置参数都给a，b和c必须使用关键字参数
   def Function(*a,b,c):
       print('a =',a)
       print('b =',b)
       print('c =',c)

   Function(1,2,3,4,b=5,c=7)
   a = (1, 2, 3, 4)
   b = 5
   c = 7
   ```

   **`*`形参只能接收位置参数**，而**不能**接收关键字参数。

`**`形参可以接收其他的关键字参数，统一保存到字典里。字典的key就是参数的名字，字典的value就是参数的值，\*\*形参只能有一个，并且必须写在所有参数的最后。

```python
def Function(b,c,**a) :
    print('a =',a,type(a))
    print('b =',b)
    print('c =',c)

Function(c=3,b=4,name='Tim',nums='1314')
# a = {'name': 'Tim', 'nums': '1314'} <class 'dict'>
# b = 4
# c = 3
```

**参数也可以解包**，要求序列中元素的个数必须和形参的个数的一致，解包的方法就是在序列类型的参数前添加星号。

通过`*`对元组解包（可以是列表吗？），通过`**`对字典解包。

```python
def Function(a,b,c):
    print('a =',a)
    print('b =',b)
    print('c =',c)

# 创建一个元组
t = (5，2，0)

# 传递实参时，在序列类型的参数前添加星号，这样他会自动将序列中的元素依次作为参数传递
Function(*t)    
# a = 5
# b = 2
# c = 0

def Function(a,b,c):
    print('a =',a)
    print('b =',b)
    print('c =',c)

# 创建一个字典
d = {'a':100,'b':200,'c':300}

# 通过 **来对一个字典进行解包操作
Function(**d)
# a = 100
# b = 200
# c = 300
```

Python的函数具有非常灵活的参数形态，既可以实现简单的调用，又可以传入非常复杂的参数。默认参数一定要用`不可变对象`，如果是可变对象，程序运行时会有逻辑错误！

要**注意**定义可变参数和关键字参数的语法：

```text
*args是可变参数，args接收的是一个tuple；

**kw是关键字参数，kw接收的是一个dict。
```

以及调用函数时如何传入可变参数和关键字参数的语法：

可变参数既可以直接传入：func\(1, 2, 3\)，又可以先组装list或tuple，再通过`*`args传入：func\(`*`\(1, 2, 3\)\)；

关键字参数既可以直接传入：func\(a=1, b=2\)，又可以先组装dict，再通过`**`kw传入：func\(`**`{'a': 1, 'b': 2}\)。

命名的关键字参数是为了限制调用者可以传入的参数名，同时可以提供默认值。定义命名的关键字参数在没有可变参数的情况下不要忘了写分隔符\*，否则定义的将是位置参数。

### **返回值return**:

通过 `return` 来指定函数的返回值,返回值可以跟任意的对象（包括函数），如果仅仅写一个return 或者 不写return，则相当于return None 。在函数中，return语句后的代码都不会执行。

* **break 用来退出当前循环**
* **continue 用来跳过当次循环**
* **return 用来结束函数**

### **作用域space**

作用域（scope）指的是变量生效的区域，为了保护数据安全，编译器会对变量进行划分。如全局变量和局部变量。

**全局作用域**：全局作用域在程序执行时创建，在程序执行结束时销毁（垃圾回收机制），所有函数以外的区域都是全局作用域。在全局作用域中定义的变量，都属于全局变量，全局变量可以在程序的任意位置被访问。

**函数作用域**：函数作用域在函数调用时创建，在调用结束时销毁。函数每调用一次就会产生一个新的函数作用域，在函数作用域中定义的变量，都是局部变量，它只能在函数内部被访问

**变量查找**：当我们使用变量时，会优先在当前作用域中寻找该变量，如果有则使用。如果没有则继续去上一级作用域中寻找，如果有则使用，如果依然没有则继续去上一级作用域中寻找，以此类推，直到找到全局作用域，依然没有找到，则会抛出异常 NameError: name 'a' is not defined

**当前作用域-&gt;上级作用域-&gt;...-&gt;全局作用域**

![&#x6355;&#x7684;&#x83B7;.PNG](https://i.loli.net/2020/02/08/x17yWroDme5aN3M.png)

**内层变量可以访问外层作用域，反之则不行**

如果希望在函数内部修改全局变量，则需要使用global关键字，来声明变量。

```python
def Function1():
a = 10 # 在函数中为变量赋值时，默认都是为局部变量赋值
print('函数内部：','a =',a) #函数内部： a = 10
print(id(a)) # 1477167056

Function1()
a = 20
print('函数外部：','a =',a) #函数外部： a = 20
print(id(a)) # 1477167376
# 虽然变量名都是a但是他们的实质却是不同的：其一是在不同的作用域，其二是经验证两者的id（对象的存储位置）都是不同的
```

```python
# 如果希望在函数内部修改全局变量，则需要使用global关键字，来声明变量
def Function2():
    global a # 声明在函数内部的使用a是全局变量，此时再去修改a时，就是在修改全局的a
    a = 520 # 修改全局变量
    print('函数内部：','a =',a) #函数内部： a = 520
    print(id(a)) #2306878055536

Function2()
# 假设a是全局的，那么不论内部外部，两次打印应该是相同的结果
print('函数外部：','a =',a) #函数外部： a = 520
print(id(a)) #2306878055536
```

### **命名空间namespace**

命名空间指的是变量存储的位置，每一个变量都需要存储到指定的命名空间当中, 每一个作用域都会有一个它对应的命名空间。

**全局命名空间，用来保存全局变量。函数命名空间，用来保存函数中的变量。**

命名空间实际上就是一个字典，是一个专门用来存储变量的字典，locals\(\)用来获取当前作用域的命名空间，返回值为一个字典。

* 如果在全局作用域中调用locals\(\)则获取全局命名空间，
* 如果在函数作用域中调用locals\(\)则获取函数命名空间。

```python
# locals()用来获取当前作用域的命名空间
# globals() 函数可以用来在任意位置获取全局命名空间
scope = locals() # 当前命名空间——全局命名空间
a = 'Tim'
b = 325
print(type(scope)) # <class 'dict'>
print(scope) #输出值会很多，但先不管那么多，先来看结果

# {'scope': {...}, 'a': 'Tim', 'b': 325}
# 输出中共分三项: scope  a  b
# 这三项分别是我们定义的三个变量，且是全局变量
# 'scope': {...} 表明scope类型是字典，所以证明了locals()返回值是字典无误
# 'a': 'Tim' 和 'b': 325 都是我们自己定义的，所以locals()的功能就是获取当前作用域的命名空间
```

```python
# 既然scope是一个字典，那么我们能够以操作字典的方式来调用scope呢？ 答案是： 当然可以
# 输出
print(a)
print(scope['a'])
'''
# Tim
# Tim
# 这两者的效果是一样的，反向验证了locals的功能

# 向scope中添加一个key-value
# scope['c'] = 'LOVE' 
# 向字典中添加key-value就相当于在全局中创建了一个变量（一般不建议这么做）
# print(c) #LOVE
```

