
## 1、abs(x)
* 返回x的绝对值，x可以为int型或者float型


```python
abs(-10), abs(-1.2), abs(8)
```




    (10, 1.2, 8)



## 2、all(iterable)
* 如果iterable的每一个元素都是true,则返回True。否则返回False。非零为真，零为假


```python
all([1,2,3])
```




    True




```python
all([2,0])
```




    False




```python
all([-1,2,3])
```




    True



## 3、any(iterable)
* 如果iterable中有一个非零零值则返回True，如果全为零则返回False


```python
any([1,0,0,3])
```




    True




```python
any([0,0,0])
```




    False




```python
any(['a','b'])
```




    True



## 4、bin(x)
* 将整数x转换为2进制


```python
bin(4)
```




    '0b100'




```python
bin(-10)
```




    '-0b1010'



## 5、callable(object)
* object对象是否是可调用的。类是可调用的，实例如果含有\_\_call\_\_()方法，则也是可调用的


```python
class C:
    def __call__(self):
        pass
    pass
```


```python
callable(C)
```




    True




```python
c = C()
callable(c)
```




    True



## 6、chr(i)
* i为整数，以字符串的形式返回i对应的Unicode字符


```python
chr(97)
```




    'a'




```python
chr(8364)
```




    '€'



## 7、@classmethod
* 将一个方法转换为类方法。类方法以类本身作为第一个参数，通常写为cls


```python
class C:
    @classmethod
    def f(cls,*args):
        pass
```

* 它既可以在类上进行调用，又可以在类的实列上调用


```python
C.f()#类上调用
```


```python
C().f()#类的实例上调用
```

## 8、类complex([real[,imag])
* 转换为复数形式，参数可以是字符串，但是字符串-+之间不能有空白;并且使用 j作为虚部


```python
complex('1-2j')
```




    (1-2j)




```python
complex('1 + 2j')#有空白
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-19-5515fc33addb> in <module>()
    ----> 1 complex('1 + 2j')#有空白
    

    ValueError: complex() arg is a malformed string


## 9、delattr(object,name)
* 删除object对象的名为name的属性，name为一个字符串，并且对象有同名的属性


```python
class C:
    def __init__(self,value):
        self.value = value
    def f(self):
        pass
```


```python
c = C(2)
delattr(c,'value') # 相当于 del c.value 
```

## 10、dir([object])
* 如果没有传入参数，则返回当前作用域的命名的列表；如果有参数则返回object对象的有效属性。
* dir()会根据对象有不同的机制。如果object是一个模块，则返回模块的所有属性的列表；如果object是一个类对象，则返回类的属性的名列表；


```python
import struct
dir(struct)
```




    ['Struct',
     '__all__',
     '__builtins__',
     '__cached__',
     '__doc__',
     '__file__',
     '__loader__',
     '__name__',
     '__package__',
     '__spec__',
     '_clearcache',
     'calcsize',
     'error',
     'iter_unpack',
     'pack',
     'pack_into',
     'unpack',
     'unpack_from']




```python
class Shape:
    def __dir__(self):
        return ['area','permiter','location']
s = Shape()
dir(s)
```




    ['area', 'location', 'permiter']



## 11、divmod(a,b)
* 接收两个非复数的参数，返回它们的商和余数，对于整数相当于（a//b, a%b）
* 对于float数相当于（math.floor(a/b), a%b）


```python
divmod(7,3)
```




    (2, 1)




```python
divmod(2.5, 1.5)
```




    (1.0, 1.0)



## 12、enumerate(iterable,[start=0])
* 返回一个枚举的list，可以指定起始值


```python
num = ['one','two','three','four']
list(enumerate(num))
```




    [(0, 'one'), (1, 'two'), (2, 'three'), (3, 'four')]




```python
list(enumerate(num,start=100))
```




    [(100, 'one'), (101, 'two'), (102, 'three'), (103, 'four')]




```python
# 相当于：
def enumerate2(sequence,start=0):
    n = start
    for element in sequence:
        yield n, element
        n += 1
```


```python
list(enumerate2(num,start=100))
```




    [(100, 'one'), (101, 'two'), (102, 'three'), (103, 'four')]



## 12、eval（expression, global=None, local=None）
* 如果提供了global参数，则其必须为字典形式；如果提供了local参数，则其可以为任何mapping object


```python
x = 3
eval('x+3')
```




    6



## 13、filter(function,iterable)
* 过滤掉iterable中的元素不满足function的


```python
list(filter(lambda x: x>2,[1,2,3,0,4]))
```




    [3, 4]



## 14、float([x])
* 将一个数或者数字的字符串转换为float数


```python
float('+1.23')
```




    1.23




```python
float('    -1234')
```




    -1234.0




```python
float('1e-003')
```




    0.001




```python
float(1E6)
```




    1000000.0




```python
float('Infinity')
```




    inf



## 15、getattr(object,name[,default])
* 返回object对象的name属性，name必须为字符串。getattr(x,'foobar)相当于x.foobar


```python
class C:
    def __init__(self,value):
        self.value = value
    pass
```


```python
c = C(10)
getattr(c,'value')
```




    10



## 16、hasattr(object,name)
* 如果object有name属性则返回True，否则返回False，name必须为字符串格式


```python
hasattr(c,'value')
```




    True




```python
hasattr(c,'x')
```




    False



## 17、help([object])


```python
help()
```

    
    Welcome to Python 3.6's help utility!
    
    If this is your first time using Python, you should definitely check out
    the tutorial on the Internet at http://docs.python.org/3.6/tutorial/.
    
    Enter the name of any module, keyword, or topic to get help on writing
    Python programs and using Python modules.  To quit this help utility and
    return to the interpreter, just type "quit".
    
    To get a list of available modules, keywords, symbols, or topics, type
    "modules", "keywords", "symbols", or "topics".  Each module also comes
    with a one-line summary of what it does; to list the modules whose name
    or summary contain a given string such as "spam", type "modules spam".
    
    help> dict
    Help on class dict in module builtins:
    
    class dict(object)
     |  dict() -> new empty dictionary
     |  dict(mapping) -> new dictionary initialized from a mapping object's
     |      (key, value) pairs
     |  dict(iterable) -> new dictionary initialized as if via:
     |      d = {}
     |      for k, v in iterable:
     |          d[k] = v
     |  dict(**kwargs) -> new dictionary initialized with the name=value pairs
     |      in the keyword argument list.  For example:  dict(one=1, two=2)
     |  
     |  Methods defined here:
     |  
     |  __contains__(self, key, /)
     |      True if D has a key k, else False.
     |  
     |  __delitem__(self, key, /)
     |      Delete self[key].
     |  
     |  __eq__(self, value, /)
     |      Return self==value.
     |  
     |  __ge__(self, value, /)
     |      Return self>=value.
     |  
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |  
     |  __getitem__(...)
     |      x.__getitem__(y) <==> x[y]
     |  
     |  __gt__(self, value, /)
     |      Return self>value.
     |  
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |  
     |  __iter__(self, /)
     |      Implement iter(self).
     |  
     |  __le__(self, value, /)
     |      Return self<=value.
     |  
     |  __len__(self, /)
     |      Return len(self).
     |  
     |  __lt__(self, value, /)
     |      Return self<value.
     |  
     |  __ne__(self, value, /)
     |      Return self!=value.
     |  
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |  
     |  __repr__(self, /)
     |      Return repr(self).
     |  
     |  __setitem__(self, key, value, /)
     |      Set self[key] to value.
     |  
     |  __sizeof__(...)
     |      D.__sizeof__() -> size of D in memory, in bytes
     |  
     |  clear(...)
     |      D.clear() -> None.  Remove all items from D.
     |  
     |  copy(...)
     |      D.copy() -> a shallow copy of D
     |  
     |  fromkeys(iterable, value=None, /) from builtins.type
     |      Returns a new dict with keys from iterable and values equal to value.
     |  
     |  get(...)
     |      D.get(k[,d]) -> D[k] if k in D, else d.  d defaults to None.
     |  
     |  items(...)
     |      D.items() -> a set-like object providing a view on D's items
     |  
     |  keys(...)
     |      D.keys() -> a set-like object providing a view on D's keys
     |  
     |  pop(...)
     |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
     |      If key is not found, d is returned if given, otherwise KeyError is raised
     |  
     |  popitem(...)
     |      D.popitem() -> (k, v), remove and return some (key, value) pair as a
     |      2-tuple; but raise KeyError if D is empty.
     |  
     |  setdefault(...)
     |      D.setdefault(k[,d]) -> D.get(k,d), also set D[k]=d if k not in D
     |  
     |  update(...)
     |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
     |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
     |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
     |      In either case, this is followed by: for k in F:  D[k] = F[k]
     |  
     |  values(...)
     |      D.values() -> an object providing a view on D's values
     |  
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |  
     |  __hash__ = None
    
    help> 
    
    You are now leaving help and returning to the Python interpreter.
    If you want to ask for help on a particular object directly from the
    interpreter, you can type "help(object)".  Executing "help('string')"
    has the same effect as typing a particular string at the help> prompt.
    

## 18、hex(x)
* 将一个整数转换为16进制，以‘0x’开头


```python
hex(255)
```




    '0xff'




```python
hex(-42)
```




    '-0x2a'



## 19、id(object)
* 返回object 得到identity


```python
x = 10
y = 100
id(x)
```




    499111104




```python
id(y)
```




    499112544



## 20、input([prompt])
* 接收用户输入，并赋值


```python
s = input('>>>>>')
```

    >>>>>i love you ,nanana
    


```python
s
```




    'i love you ,nanana'



## 21、isinstance(object,classinfo)
* 判断对象是否为指定的类的实例


```python
isinstance('aaa',str)
```




    True




```python
class C:
    pass
c = C()
isinstance(c,C)
```




    True



## 22、issubclass(class,classinfo)
* 判断是否是classinfo的子类


```python
class C_base:
    pass
class C_derive(C_base):
    pass
```


```python
issubclass(C_derive, C_base)
```




    True



## 23、iter(object[,sentinel])
* 返回一个迭代对象。如果第二个参数没给，则object必须支持\_\_iter\_\_()或\_\_getitem\_\_()方法；如果第二个参数给定了，object必须是可调用对象


```python
with open('data_file/file_w.txt') as fp:
    for line in iter(fp.readline,''):
        print(line)
```

    a new line
    
    add line2d
    

## 24、len(s)
* 返回s的长度


```python
s = [1,2,3]
len(s)
```




    3




```python
s = 'asdadfa'
len(s)
```




    7



## 25、map(function, iterables)
* 接收多个参数，将iterables的元素依次作为function的参数传入，并返回结果


```python
def func(x):
    return x*x
list(map(func,[1,2,3]))
```




    [1, 4, 9]




```python
list(map(lambda x:x**3, [1,2,3,4]))
```




    [1, 8, 27, 64]



## 26、max(iterable, *[,key,default]）和max(arg1,arg2,*args[,key])
* 返回可迭代对象的最大值或者 返回两个或者多个参数中的最大值


```python
max([1,2,3,10,34,9])
```




    34




```python
max(1,10,9,4)
```




    10



## 27、min(iterable, *[,key,default]）和min(arg1,arg2,*args[,key])
* 类似于max()求取最小值

## 28、memoryview(obj)


```python
a = b'10'
memoryview(a)
```




    <memory at 0x045CA7E8>



## 29、next(iterator[,default])
* 通过调用\_\_next\_\_()返回一个可迭代对象的下一项，


```python
a = iter([1,2,3])
next(a)
```




    1




```python
next(a)
```




    2




```python
next(a)
```




    3




```python
next(a)
```


    ---------------------------------------------------------------------------

    StopIteration                             Traceback (most recent call last)

    <ipython-input-80-15841f3f11d4> in <module>()
    ----> 1 next(a)
    

    StopIteration: 


## 30、oct(x)
* 返回x的八进制形式


```python
oct(10)
```




    '0o12'



## 31、open(filename, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
* 以指定的模式打开文件，并返回文件对象；如果打开失败，提示OSError

## 32、ord(s)
* 返回一个Unicode的字符串的字符码


```python
ord('a')
```




    97



## 33、pow(x,y[,z])
* 返回x的y次方，如果z参数也给出了，则返回x^y%z，但是比pow(x,y)%z效率更高


```python
pow(2,3)
```




    8




```python
pow(2,3)%3
```




    2




```python
pow(2,3,3)
```




    2



## 34、property(fget=None, fset=None, fdel=None, doc=None)
* 返回一个 property attribute.fget is a function for getting an attribute value. fset is a function for setting an attribute value. fdel is a function for deleting an attribute value. And doc creates a docstring for the attribute.


```python
class C:
    def __init__(self):
        self._x = None
    def getx(self):
        return self._x
    def setx(self, value):
        self._x = value
    def delx(self):
        del self._x
    x = property(getx,setx,delx,"I'm the 'x' property")
```


```python
c = C()
c.x
```


```python
c.x = 10
c.x
```




    10




```python
del c.x
c.x
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-93-d32ce31f0255> in <module>()
          1 del c.x
    ----> 2 c.x
    

    <ipython-input-90-9df78dadcd7a> in getx(self)
          3         self._x = None
          4     def getx(self):
    ----> 5         return self._x
          6     def setx(self, value):
          7         self._x = value
    

    AttributeError: 'C' object has no attribute '_x'



```python
class Parrot:
    def __init__(self):
        self._voltage = 1000
    @property
    def voltage(self):
        '''Get the current voltage'''
        return self._voltage
p = Parrot()
p.voltage
```




    1000




```python
class C:
    def __init__(self):
        self._x = None
    @property
    def x(self):
        '''the x property'''
        return self._x 
    @x.setter
    def x(self,value):
        self._x = value
    @x.deleter
    def x(self):
        del self._x
```

## 35、range(stop)和range(start,stop[,step])


```python
range(4)
```




    range(0, 4)




```python
list(range(4))
```




    [0, 1, 2, 3]




```python
list(range(1,9,2))
```




    [1, 3, 5, 7]



## 36、reversed(seq)
* 反转一个序列,返回的是一个迭代器


```python
a = [1,2,3,4]
list(reversed(a))
```




    [4, 3, 2, 1]



## 37、round(number[,ndigit])
* 如果没有ndigit参数，则返回与输入最接近的整数。如果有ndigit，则返回与输入最近的n位值


```python
a = 12.454
b = 10.51
round(a)
```




    12




```python
round(b)
```




    11




```python
round(a,2)
```




    12.45




```python
round(b,1)
```




    10.5




```python
round(12.345,2)
```




    12.35



## 38、set(iterable)
* 返回一个集合，不含重复元素


```python
set([1,2,3,4,2])
```




    {1, 2, 3, 4}



## 39、setattr(object,name,value)
* 将object的名为name的属性设置为value值


```python
class C:
    def __init__(self,value):
        self.value = value
        pass
```


```python
c = C(10)
print(c.value)
setattr(c,'value',100)# 相当于c.value = 100
print(c.value)
```

    10
    100
    

## 40、slice(stop)或者slice（start,stop[,step]）
* 切片操作


```python
a = slice(10,20,2)
```


```python
a
```




    slice(10, 20, 2)




```python
a.start
```




    10



## 41、sorted（iterable,*,key=None,reverse=False）
* 默认是升序


```python
a = [1,10,7,5,6,18,3]
sorted(a)
```




    [1, 3, 5, 6, 7, 10, 18]




```python
sorted(a,reverse=True)
```




    [18, 10, 7, 6, 5, 3, 1]



## 42、@staticmethod
* 将一个方法变为静态方法，静态方法不接受一个隐含的第一个参数


```python
class C:
    @staticmethod
    def f(*args):
        pass
```


```python
# 既可以在类上调用，也可以在实例上调用
C.f()
C().f()
```

## 43、str()


```python
str(12)
```




    '12'



## 44、sum(iterable[,start])
* start与iterable的每项相加求和，start默认为0


```python
sum([1,2,3,4,5,5])
```




    20




```python
sum([1,2,3,4,5,6],3)
```




    24



## 45、type(object)
* 返回对象的类型


```python
type('dasd')
```




    str



## 46、type(name,bases,dict)
* 返回一个新的type对象


```python
class X:
    a = 1
X = type('X',(object,),dict(a = 1))
```

## 47、vars([object])
* 本函数是实现返回对象object的属性和属性值的字典对象。如果默认不输入参数，就打印当前调用位置的属性和属性值，相当于locals()的功能。如果有参数输入，就只打印这个参数相应的属性和属性值。


```python
class Foo:
    def __init__(self):
        self.a = 1
        self.b = 2
vars(Foo())
```




    {'a': 1, 'b': 2}



## 48、zip(*iterables)
* 返回一个由各个iterable对象相同位置上的值组成的元组


```python
a = [1,2,3]
b = ['a','b','c']
c = [10,20,30,40]
list(zip(a,b))
```




    [(1, 'a'), (2, 'b'), (3, 'c')]




```python
list(zip(b,c))
```




    [('a', 10), ('b', 20), ('c', 30)]




```python
list(zip(a,b,c))
```




    [(1, 'a', 10), (2, 'b', 20), (3, 'c', 30)]




```python
def Zip(*iterables):
    sentinel = object()
    iterators = [iter(it) for it in iterables]
    while iterators:
        result = []
        for it in iterators:
            elem = next(it, sentinel)
            if elem is sentinel:
                return 
            result.append(elem)
        yield tuple(result)
```


```python
list(Zip(a,b))
```




    [(1, 'a'), (2, 'b'), (3, 'c')]



* 可以使用*zip()来解压缩


```python
x1, x2 = zip(*zip(a,b))
```


```python
x1
```




    (1, 2, 3)


