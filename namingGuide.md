#命名规范
---

##共性规范
###1. 标识符应当简单明了，望文生义
>标识符采用英文单词。切忌使用汉语拼音来命名。程序中的英文单词一般不要太复杂，用词应当准确。例如不要把CurrentValue写成NowValue。  
尽量不要使用单词缩写或首字母缩写。只有当标识符过长时才考虑使用单词缩写。在使用缩写时，不要自创缩写，尽量使用被广泛接受的缩写。

###2. 标识符长度应当符合“min-length && max-information”原则。
>一般的讲，长名字能更好地表达含义，所以函数名、变量名、类名长达十几个字符不足为怪。但是名字也不是越长越好。  
例如：变量名maxval就比maxValueUntilOverflow更好用。单字符的名字也是有用的，常见的如i,j,k,m,n,x,y,z等，它们通常用作函数内的局部变量。
 
###3. 命名规则尽量与所采用的操作系统或开发工具的风格保持一致。
>例如Windows应用程序的标识符通常采用“大小写”混排的方式，如AddChild。而Unix应用程序的标识符通常采用“小写加下划线”的方式，如add_child。别把这两类风格混在一起用。
 
###4. 程序中不要出现仅靠大小写区分的标识符。
>例如：int x; 和 int X;   void foo() 和 void FOO() 等。
 
###5. 避免在不同级别的作用域中重名。
>程序中不要出现标识符完全相同的局部变量和全局变量，尽管两者因作用域的不同而不会发生语法错误，但会使人产生误解。
 
###6. 正确命名具有互斥意义的标识符。
>使用正确的反义词组命名具有互斥意义的变量或相反动作的函数。  
如："MinValue"和"MaxValue"，"GetName()" 和 "SetName()"
 
###7. 尽量避免名字中出现数字编号。
>如Value1,Value2等，除非逻辑上的确需要编号。这是为了防止程序产生无意义的名字，降低程序的可读性。
 
###8. 使用库标志
>在开发动态库时，为了防止软件库中的一些标识符和其它软件库中标识符冲突，可以为各种标识符加上能反映软件性质的前缀。  
例如三维图形标准OpenGL的所有库函数均以gl开头，所有常量（或宏定义）均以GL开头。


##细则

### 方法命名

一个方法的命名首先描述**返回什么**，接着是什么情况下被返回。方法签名中冒号的前面描述传入参数的类型。
类方法和实例方法命名的格式写法：
```
    [object/class thing + condition];
    [object/class thing + input:input];
    [object/class thing + indentifer:input];
    
cocoa命名举例：
    realPath = [path stringByExpandingTildelnPath];
    fullString = [string stringByAppendingString:@"Extra Text"];
    object = [array objectAtIndex:3];
    newString = [NSString stringWithFormat:@"%f", 1.5];
    newArray = [NSString arrayWithObject:newString];
    
例:
    recipients = [email recipientsSortedByLastName];
    newEmail = [CDCEmail emailWithSubjectLine:@"Extra Text"];
    emails = [mailbox messagesReceivedAfterDate:yesterdayDate];
```

当需要获取对象值的另一种类型的适合，方法名格式语法如下：

```
    [object adjective + thing];
    [object adjective + thing + condition];
    [object adjective + thing + input:input];
    
good:
    capitalized = [name capitalizedString];
    rate = [number floatValue];
    newString = [string decomposedStringWithCanonicalMapping];
    subArray = [array subArrayWithRange:segment];
```

方法签名尽量做到含义明确
```
bad:
    - sortInfo      // 是返回排序结果还是给info做排序
    - refreshTimer  // 返回一个用于刷新的定时器还是刷新定时器
    - update        // 更新什么，如何更新
    
good:
    - currentSortInfo  
    - refreshDefaultTimer   // refresh表明为动词
    - updateMenuItemTitle   // 
```

### 参数

方法参数前可以使用前缀 "the", "an", "new", "in", "out"

```
    - (void)setTitle:(NSString *)aTitle;
    - (void)setName:(NSString *)newName;
    - (id)keyForOption:(CDCOption *)anOption
```

### 变量

变量应该尽量做到自描述，除for循环中，单字母的变量应该尽量避免使用。一般循环语句的当前对象的命名前缀包含"one", "a/an", 对于简单的单个对象使用"item"命名。


### 常用的一些缩略词

```
----------------------------------------
    alloc   |   分配，拨出
    alt     |   轮流，交替
    app     |   应用程序
    calc    |   计算
    dealloc |   销毁，析构
    func    |   函数
    horiz   |   水平的
    info    |   信息
    max     |   最大的
    min     |   最小的
    msg     |   消息
    nib     |   Interface Builder Doc
    pboard  |   paste Board
    rect    |   rectangle
    temp    |   临时、暂时
    vert    |   垂直的
---------------------------------------
```