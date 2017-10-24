<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.



## 序、前言

> Bjarne Stroustrup曾经总结说，，C++同时支持4种不同的编程风格：C风格、基于对象、面向对象和泛型。事实上，把微软的COM也算进来的话，还可以加上一种“基于组件”的风格。

本书自带资源：http://www.informit.com/store/c-plus-plus-primer-9780321714114

课后习题答案：https://github.com/search?utf8=%E2%9C%93&q=c%2B%2B+primer&type=

C++书籍推荐：
- 《C++ Primer 5th》
- 《Effective C++ 3rd》
- 《C++ Concurrency in Action》
- 《Linux 多线程服务端编程》

C++不断发展的目标：简单，高效，安全。

C++分三部分：

- 继承于C的低级语言，保证兼容和效率；
- 高级语言特性，面向对象等抽象；
- 标准库。

养成良好习惯，从现在开始。

根据**需要**来决定：

- 知其然知其所以然的深度；
- 思考和实践的平衡点；
- 此时此刻必学或需要查询时再学。
- 了解多少陷阱，了解多少细节，了解多少奇巧淫技；

当然凭兴趣尝试的事情很难立刻有什么反馈，但过程本身可能在很久以后才会体现出回报.

> 种一棵树最好的时间是十年前，其次是现在。

> When I was a child, I ate a lot of food. Most of it is long gone and fogotten, but certainly some of it became my very bones and flesh. Think of reading as the same thing for the mind. 

> 当我还是个孩子时，我吃过很多的食物，现在已经记不起来吃过什么了。但可以肯定的是，它们中的一部分已经长成我的骨头和肉。阅读于心灵同样如是。

----------

## Chapter 1 开始

- parameter 和 argument：parameter一般指形参，argument指实参。
- `return`:终止当前函数的运行，一般函数将控制权返回给调用它的函数，`main()`函数则将控制权返回给操作系统。
- `#include` 
    - 必须出现在单行且在所有函数体外。
    - `<iostream>`尖括号对应标准库；`"mylib"`双引号对应自定义库；
- `std::cout<<"hi"<<std::endl;`
    - `<<`, operator;
    - `std::cout`,`"hi"`,operands;
    - `std::endl`, I/O manipulators操纵符, ending the current line **and** flushing the buffer.
    - `"hi"`, string literal字符串字面值常量。
    - `<<`&`>>`, return left hand operand
- Comments
    - `//`, single-line comments(*c++ style*):单行注释。
        - double slash, all things right of slashes on the current line is ignored.
    - `/*...*/`, multi-line comments(*inherited from `C`*):
        - all things inside will be ignored except `*/`, so, can't **nest**.多行注释默认不支持嵌套（虽然想支持一定能支持，由于历史继承原因，不支持）。
    - Comments will be remove before preprocessing stage,so u can't use **MACRO**.在预处理前注释将被移除替换为空字符，所以注释中不能用**宏定义**。
    - other format to do nothing
        `#if 0`
        `xxx`
        `#endif`
        or
        `if (false)`
        `xxx`
- `++i` and `++i`
    - `++i`:get &i, i=i+1,return &i;
    - `i++`:get &i,j=i,i=i+1,return j;
    - tips:
        - for non-obj: either is ok, efficient depands on compiler's implementation,usually no difference.
        - for iterators,template  types, use `++i`.
- Flow of control
    - Why?Statements normally execute sequentially.某些语句运行的很频繁，所以将其抽象出一种新的结构。
- Difference in `while`, `do while` and `for`
    - > The pattern happens so often- -using a variable in a condition and incrementing the variable in the body(if the variable need to be changed out of body,you shouldn't define it inside).
    - `while` -->condition-->then do
    - `do while` --> do at least for 1 time then same to while
    - `for`--> init-statement,then condition.last
    - when
        - `break`, no difference
        - `continue`,
            - `for`: goto this turn's third expression in `for(;;third expression)`
            - `while`: goto next turn's condition
    - efficiecy: depend on compiler, test it if necessary.
    - some other loop:`goto`? recusion?
- istream becomes invalid when
    - meet `END OF FILE`：`Ctrl D`,`Ctrl Z`
    - invalid input

- **No** correct style but consistency, readability and comprehension.
- Class
    - class defines a type by its name.`Sales_item.h` and `Sale_item.cpp`
    - class include all the operation on the objects of the class type
    - "`.`" operator
        - left-hand operand must be an object of class type;
        - right-hand operand must name a member of that type.

----------

# Part Ⅰ C++基础

## Chapter 2 变量和基本类型

- C++定义了算数类型的最小尺寸`char` 8,`short` 16,`int` 16,`long` 32,`long long` 64,`float` 6位有效数字， `double` 10位有效数字,`long double`10位有效数字，注意在16位，32位，64位不同编译器上他们的大小是不一样的。
- C++定义了标准而非具体实现：`int`至少和`short`一样大，`long`至少和`int`一样大，`long long`至少和`long`一样大。
- Type classification

    > Objects, references, functions including function template specializations, and expressions have a property called type, which both restricts the operations that are permitted for those entities and provides semantic meaning to the otherwise generic sequences of bits.
    限制操作，提供语义。

    - fundamental type(`std::is_fundamental`)
        - arithmetic types(`std::is_arithmetic`) 
            - floating-point types(`std::is_floating_point`):`float`,`double`,`long double`.
            - integral types(`std::is_integral`)
                - `bool`:sizeof(bool) depand on implementation so minght not be 1.
                - characters
                    - narrow:`char`,`signed char`,`unsigned char`;`char`会实现为signed 或者unsigned其中一种，依赖具体实现。
                    - wide:`char16_t`,`char32_t`,`wchar_t`.
                - intergers
                    - signed integer type:`short int`,`int`,`long int`,`long long int`.
                    - unsigned interger types:`unsigned short int`,`unsigned int`,`unsigned long int`,`unsigned long long int`.
        - void(`std::is_void`)
            - has no associated values
            - it is an incomplete type that cannot be completed objects of type void are disallowed
            - no arrays of void ,no references to void
            - pointer to void and return type
        - std::nullptr_t(`std::is_null_pointer`)
            - defined in header <cstddef>,`typedef decltype(nullptr) nullptr_t;`
            - null pointer literal: `nullptr` is a type `std::nullptr_t`
            - It is a distinct type. Not a pointer type or a pointer to member type
    - compound types (`std::is_compound`):
        - reference types(`std::is_reference`):
            - lvalue reference types(`std::is_lvalue_reference`):
                - lvalue reference to object types;
                - lvalue reference to function types;
            - rvalue reference types(`std::is_rvalue_reference`):
                - rvalue reference to object types;
                - rvalue reference to function types;
        - pointer types(`std::is_pointer`):
            - pointer to object types;
            - pointer to function types;
        - pointer to member types(`std::is_member_pointer`):
            - pointer to data member types(`std::is_member_object_pointer`);
            - pointer to member function types(`std::is_member_function_pointer`);
        - array types(`std::is_array`)
        - function types(`std::is_function`)
        - enumeration types(`std::is_enum`)
        - class types:
            - non-union types(`std::is_class`)
            - union types(`std::is_union`)
除了引用reference和函数外每个类型提供了`const`,`volatile`,`const volatile`三类限定符
- 如何选择类型：
    - 不会出现负数，选`unsigned`
    - 一般用`int`执行整数运算，`short`太小，`long`一般和`int`尺寸一样，如果超过`int`直接用`long long`。
    - 避免`char`、`bool`参与算术运算。`char`有的实现为有符号，有的为无符号，容易出现问题。
    - 浮点运算用`double`，精度大于float，运算速度与float相比依靠具体实现，long double 太费精度。
- 类型表示的值的范围决定转换过程：
    - 非布尔->布尔：0则false，其它为true；
    - 布尔->非布尔：false则0，true则为1；
    - 浮点->整数：去掉小数部分；
    - 整数->浮点：小数部分记为0，整数若超过浮点类型容量，精度可能会有损失。
    - 超范围赋值给无符号：取模取余数。
    - 超范围赋值给带符号：结果未定义。可能崩溃，可能自动转换，以来具体实现。
- 字面值常量：
    - 20 十进制字面值DEC，默认为带符号数，类型为能容纳该值的（int，long，long long）三者中最小的。
    - 024 八进制OCT，默认可能带符号，可能不带。类型为能容纳该数值的（int,unsigned int,long,unsigned long,long long,unsigned long long ）中的尺寸最小者
    - 0x14 十六进制HEX 默认可能带符号，可能不带。类型为能容纳该数值的（int,unsigned int,long,unsigned long,long long,unsigned long long ）中的尺寸最小者
    - 虽然整型字面值存储为带符号数据类型，但十进制字面值不会是负数，负号仅对字面值取负。
    - 浮点型字面值,带小数，或者带e或E，默认为double。
    - `‘a’`字符字面值；`"a"`字符串字面值，字符数组。字符串字面值尾处增加空字符`'\0'`
    - escape sequence转义序列：`\123`超过3个八进制数之后数字不参与转义。`\x123456`十六进制字符x后的所有字符参与转义。char类型一般为8位，所以`\x123456`可能报错。
- 指定字面值类型
    - 字符或字符串前缀
        - u Unicode 16
        - U Unicode 32
        - L 宽字符
        - u8 UTF-8仅用于字符串字面常量
    - 整形字面值后缀：**最小匹配类型**
        - u或U unsigned
        - l或L long
        - ll或LL long long
    - 浮点型字面值后缀
        - f或F float
        - l或L long double
- 指定了u or U后缀的10、8、16进制数将从unsigned的int,long,long long匹配最小可容纳类型。 l or  L后缀则匹配long, long long 中最小可容纳类型，LL则在unsigned long long和long long 中匹配。
- 初始化与赋值的区别
- `int a = 0;`,`int a = {0};`,`int a(0);`,`int a{0};`定义并初始化。列表初始化值如果纯在丢失信息的风险，将报错而不是原来的默默无闻自动转换。
- 内置类型的变量未被显示初始化，如果定义在任何函数体外的变量将被赋值位0，如果定义在函数体内，则不被初始化，其值未定义。
- 类决定对象初始化，是否允许不初始化就定义对象也由类决定。绝大多数类支持无需显示初始化而定义对象，这样的类会提供合适的默认值。一些类要求对象必须初始化，如果创建对象无初始化将会错误。
- 声明与定义：声明是宣称要使用；定义是创建这个实体；变量能且仅能被定义一次，但可被多次声明；
    - `extern int i;`仅声明i
    - `int i;`声明且定义i
    - `extern int i = 1;`带显示初始化的声明即成为定义；
- 标识符identifier
    - 大小写敏感。
    - 只由字母，数字，下划线组成。
    - 必须字母、下划线开头。
    - 良好的习惯不用下划线开头，一般标准库中用下划线开头。
- 作用域
    - `::`域操作符左侧为空则为全局作用域global scope
    - 全局变量和局部变量同名时，在局部块中默认是局部变量；
    - 若想使用外部作用域同名变量使用作用域操作符。
    - 良好的习惯尽量避免同名变量。
- 引用
    - `int i = 1;`
    - `int &j = i;`j是i的别名,而非新的对象。
    - `int &k;`错误；引用一旦声明不可更改绑定，故定义时必须初始化；
    - `int &l = 3;`错误，此处需要lvalue。3不是lvalue,是int型的rvalue；
    - 引用不可重复声明，不可更改绑定，对引用名的改变都是对原名变量的改变；
    - `int &(&m) = i;`错误，引用非对象，所以不能定义引用的引用；
    - `int &ri =i, j =3;`ri为类型为int的i的引用，j为类型为int的一个变量。引用和变量可混合一起定义。
    - `int &ri = i, &rj = j;`多引用声明都要带`&`.
    - `int i = 1;double &j = i;`引用类型不匹配将直接报错，不会自动转换。
    - 引用类型不匹配有两个意外：const的引用可指向任意可转换为引用类型的字面值，变量，表达式；
- 指针
    - 指针本身就是一个对象，可赋值，可复制，可改变指向对象，定义时可不进行初始化。（与引用相比）
    - 和其他内置类型一样，块作用域内定义的指针如果没有初始化，默认不初始化。
    - `int *pi =i, j =3;`pi为类型为int的i的指针，j为类型为int的一个变量。指针和变量可混合一起定义。
    - `int *pi = i, *pj = j;`多指针声明都要带`*`.
    - 指针存放的值为对象的内存地址，获取该地址需取地址符`&`
    - `int &r = i;` `int *pi = &r;`错误，引用非对象，无实际地址，无法获取地址。
    - `int ival =42; double *pd = &ival;`错误，指针类型与所指对象类型不匹配。
    - 指针类型不匹配也有2种例外：
    - 指针的值处于4种状态：
        - 一个对象
        - 对象所占空间的下个位置
        - 空指针，没有志向任何对象
        - 无效指针，上述情况的其他值
        试图拷贝或其他方式访问无效指针的值将引发错误。
    - `*`解引用符来访问对象。
    - `*`,`&`符号出现在声明和语句中有不同的含义：表明复合类型或者运算符。
        - `int i = 42;`
        - `int &r = i;` `&`紧随类型名之后，是声明的一部分，此为引用
        - `int *p = i;`指针
        - `p = &i;`取地址符
        - `*p = i;`解引用符
    - 空指针
        - `int *p1 = nullptr;`
        - `int *p2 = 0;`
        - `int *p3 = NULL;`
        以上为空指针的生成方法；避免使用NULL，预处理变量NULL在cstdlib中定义，值为0；
        - 注意可以用0初始化给指针`int *p2 = 0;`或者用0来来赋值给指针变量`p2 =0;`给使其为空指针，但是用值为0的int变量来初始化指针则会错误。
        - 建议：初始化所有指针（防止使用未经初始化的指针防止运行时错误是其目的和需求，如果不妨碍这个需求，那么就可以比不用管）
    - void* 指针
        - 可以存放任意对象的地址
        - void*的视角来看内存空间仅仅是内存空间而没法访问他所存储的地址的对象。
- 复合类型的声明
    - 变量的定义
        - 基本数据类型
        - 一组声明符
        同一条定义语句中类型可以有一个，声明符可以有多个如`int i = 1,*p =&i, &r =i;`
    - 指针的指针
    - 指向指针的引用:引用非对象，故引用无指针，指针是对象，所以指针有引用
        `int i =42;`
        `int *p;`
        `int *&r = p;`
    遇到`*`,`&`,多层嵌套的时候看变量名从右向左，从最近的修饰符到外看变量名。如`int *&r = p;`，r最近的是`&`,所以r是一个引用，往外是一个`*`，是一个指针的引用。
- const限定符
    - 常量，声明时就需要初始化。
    - `const int k;`错误，未初始化。、
    - const类型限定在这个类型上的操作，可以做除了改变其值的其他操作。所以const值与非const值之间的拷贝初始化都是允许的。
    - 默认const只在文件内有效，如果需要文件间共享const变量，需用`extern const int bufSize = 512;`在源文件中定义一次，然后在头文件中添加`extern xonst int bufSize;`这一声明，指明bufSize非本文件独有，它的定义将在其他地方出现。
    - 常量的引用
        - 常量的引用无法改变。
        - 非常量的引用无法引用一个常量对象，直接报错，如果可以引用那么可以用非常量的引用更改常量对象。
        - 引用的是常量还是非常量决定可在其上的操作，而引用是不可变的。
    - 初始化和对const的引用
        - 引用类型必须与其引用对象类型一致，有2个例外
            - **初始化常量**引用允许任意表达式作为初始值，只要表达式结果可以转化为所引用的类型，转化过程中有个临时量。
            - 对const的引用可能引用自一个非const的对象。
    - 指针和const
        - 非const指针不能指向const变量`const int i = 3;int *pi = &i;`
        - const指针可以指向非const变量：这样通过指针限制了不可变性，而对象本身可通过其他形式进行可变化。
        - 常量指针是对象，常量的指针是对象，而常量引用指的是常量的引用。
            - 常量指针,说明指针是个常量，指针的内容不可变，而非指针内的对象不可变。
                `int err = 0;`
                `int *const cstErr = &err;`
            - 常量的指针，说明指针所指的对象是个常量，即指向的对象本身不可变，而指针指向哪个对象可变.
                `int err =0;`
                `const int *cpErr = &err;`
            - 顶层const指常量指针，底层const指指针指向的常量对象。顶层const可忽略类型一致，底层在除了例外（const可接受任何）之外，必须严格一致。
            - 
    - constexpr和常量表达式
        
