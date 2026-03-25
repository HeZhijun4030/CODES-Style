### Warning
**注意以下内容皆为本人胡扯,只是为了抽象好玩所以不要应到任何你自己的或团队的生产环境中！！**

中文 | [English](./README.md)

# CODES - C++ - WIP
## COmpact DEfense Coding Style - C++
## C++紧凑型防御式编码风格



## 目录：

- [前言](#前言)
- [背景](#背景)
- [正文](#正文)
- - [宗旨](#宗旨)
- - [CPP版本](#版本)
- - [环境](#环境)
- - [文件格式](#文件格式)
- - [格式纪律](#格式纪律)
- - [头文件](#头文件)
- - [包含纪律](#包含纪律)
- - [全局命名纪律](#全局命名纪律)
- - - [文件命名](#文件命名)
- - - [变量](#变量)
- - - [函数](#函数)

---

# 前言

- 更新时间：2026/03/23
- 原作者: HeZhijun4030
- 参考: Google C++ Style Guide

我(CodeManStudio)经常会发布一些开源项目, 而且**很少接受**来自其他代码贡献者的代码. 但是如果代码贡献者的编程风格好呢好, 反而会给我造成不小的困扰, 人话即我看不懂😡😡😡. CodeManStudio 因此发布了这份自己的编程风格指南, 使所有提交代码的人都必须严格按照 COmpact DEfense Coding Style 写 , 违抗者默认一天内变为猫娘

# 以下C++统一称为CPP

关于(暂定),为后续可能会**着重修改更新,有歧义,有问题的地方**,不代表其他内容不会更新

---

# 背景

2026年2月20日, 春节期间, 我在接触CPP后发现, **Python is fx a p o s** 所以我喜欢上了CPP,我要成为阴暗后端大蛇, 经过几天CPP Primer的修炼后我勉强入门,CPP真是太吊了


CPP程序员都知道, 该语言有很多强大的特性 (feature), 但强大之处也伴随着很少复杂性, **让代码不容易出错, 容易阅读、维护**.

本指南的目标是详述CPP的注意事项来控制**抽象性**. 这些规则会在保持代码易于管理的同时, 不影响程序员高效地开玩笑何瞎几把写.

注意: 本指南并非 CPP 教程, 我们假定读者已经非常熟悉 CPP.

---

# 正文

## 宗旨
人类到如今已经繁衍了250000年,只有最近的4000年是有意义的.

所以,我们在将近250000年中在干嘛？我们躲在写代码,吃Bug,和编译器玩神秘小游戏

人类不能再生活在恐惧中.没有东西能保护我们,我们必须保护我们自己.

当其他人在阳光下生活时,我们必须在阴影中和它们战斗,并防止它们暴露在大众眼中,这样其他人才能生活在一个理智的,普通的世界中

我们不稳定,我们抽象,我们很神秘.

——码人StudioAAA好纸巾批发


- **明智的AI使用**：只求原理而不求结果,写出来的代码只有理解了你才能说这是我写上去的
- **抽象的编程**要用最简单的方法解决问题
- **明确的目标,清晰的框架**
- **不必要的可读性,严禁大规模注释,**
- **不必要的复杂性**,少点屎,是为我们写出更好的屎做准备
- **我们很紧,我们很受,我们防御,内存泄漏者,拉出去艹十分钟直到草饲**
- 尽你一生的努力,最大程度利用**分号**,不为别的,只为写出来最抽象的代码

---

## 版本
都给劳资用CPP20/17, 不应该使用CPP23及以上的特性. 这是一个严峻的命令👊👊👊👊👊👊👊👊.

---

## 环境 
严肃使用命令行😎

### 系统

任何**Linux**发行版都可以,包括安卓Termux及衍生
**Windows10/11**

### 编译器严厉限制为：
- **MSVC** V143 (Visual Studio 2022) **or later**
- **GCC** (MinGW-W64) **any version**

**No clang, LLVM or other compilers.**

### 构建工具

- **CMake** 3.20+
- **Ninja** idk

### IDE

- **Visual Studio Code**
- **Visual Studio2022** (VS2022)
- **CLion** 
- **NVim** 

---

## 文件格式
编码格式统一为UTF-8 ,BOM随意
源文件扩展名为`.cpp`
头文件扩展名为`.hpp`

---

## 格式纪律
使用**小于等于4个空格**作为缩进

大括号**推荐使用非K&R风格**,即`{` 与 `}` 单独占一行,而`}` 另起一行

### 全局通用回车纪律

必要情况下若2-6行代码块写在同一行时未超出屏幕外,必须写在同一行,可以添加单个空格
如：
~~~cpp
int x = 10;int y = 20;int z = 30;
std::cin.clear(); std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');

if (progress >= 1.0f) {IsRunning = false;if (BindTarget) *BindTarget=FinalValue;BindTarget=nullptr;}
if (BindTarget) *BindTarget = StartValue + (FinalValue-StartValue) * ApplyCurve(progress);
~~~

#### 以下规则均可按照这个思路推导组装,即将符合纪律的函数调用、变量赋值、条件判断、循环等代码都必须放在同一行,并在必要时添加空格


### 函数

若为简单的函数(定义为可以明显看出功能)如get/set方法必须写在一行如：
~~~cpp
int GetX() const { return x_; }
void SetX(int x) { x_ = x; }
int SetX(int x,int y) { return x + y; }
~~~
花括号随意

### if-else
简单判断优先单行,复杂嵌套按标准缩进展开.

**简单判断(单条语句)** — 必须写在一行,括号可选：
~~~cpp
if (!GetIsRunning()) return FinalValue;
if (x > 0) { return 1; }
~~~

**中等复杂度**允许单行紧凑或适当换行：
~~~cpp
void BaseTween::ApplyToUpdate()
    {
        if (!GetIsRunning()) BindTarget=nullptr;
        const auto now = GetCurrentTimeMs();

        const float progress = (now - StartTime)  / Duration;
        if (progress >= 1.0f) {IsRunning = false;if (BindTarget) *BindTarget=FinalValue;BindTarget=nullptr;}
        if (BindTarget) *BindTarget = StartValue + (FinalValue-StartValue) * ApplyCurve(progress);
    }
~~~

**若为多重判断超复杂语句**(如4层以上嵌套)必须按照正常格式进行缩进回车
~~~cpp
if (condition1) 
{
    if (condition2) 
    {
        if (condition3) 
        {
            if (condition4) 
            {
                // 业务逻辑
            }
        }
    }
}
~~~


### switch-case
简单分支紧凑化,复杂分支常规展开.
花括号随意

**超简单 case** 所有case与执行代码写在同一行：
~~~cpp
float BaseTween::ApplyCurve(const float& t)const{switch (CurCurve){case Curve::Linear:return t;case Curve::QuadIn:return t*t;default: return t;}}
~~~

**正常简单 case** 与执行代码写在同一行：
~~~cpp
float BaseTween::ApplyCurve(const float& t) const
{
    switch (CurCurve)
    {
        case Curve::Linear: return t;
        case Curve::QuadIn: return t * t;
        default: return t;
    }
}
~~~

**复杂 case** 换行并缩进：
~~~cpp
switch (type)
{
    case Type::Complex:
        DoSomething();
        DoMore();
        break;
    default:
        break;
}
~~~

### for-while-do-while
简单循环优先单行,复杂嵌套按标准缩进展开
例：
~~~cpp
for (int i = 0; i < 10; i++){std::cout << i << std::endl;}

while (true){std::cout << "Hello, world!" << std::endl;}

do{std::cout << "Hello, world!" << std::endl;}while (true);
~~~

---

## 声明纪律

### 指针声明
`*` 紧贴变量名,**不紧贴类型名**
例：
~~~cpp
int *ptr;
~~~

### 引用声明
`&` 紧贴变量名,**不紧贴类型名**
例：
~~~cpp
int &ptr;
~~~


### 函数参数中的指针/引用
同上

~~~cpp
void SetValue(int *ptr, int &ref){*ptr = ref;}

void Swap(int *a, int *b) { int t = *a; *a = *b; *b = t; }
~~~

### 函数返回值中的指针/引用
`&` , `*`紧贴类型
~~~cpp
int* GetPointer(){return &x;}
int& GetReference(){return x;}
~~~

### const
类型之前
~~~cpp
const int x = 10;
const int *ptr = &x;
const int &ref = x;
~~~

---

## 头文件

所有头文件都应该用 #define 防护符来防止重复导入. 防护符的格式是: `<文件名(全大写)>_HPP `.
`#endif`后接注释,注释内容为防护符,

例：

~~~cpp
#ifndef CMS_UTILS_DLL_HPP
#define CMS_UTILS_DLL_HPP
#endif // CMS_UTILS_DLL_HPP
~~~

### 配套的头文件

#### 位置
若你的头文件是一个普通源文件配套的头文件,请将其放在同一目录下

#### 命名
头文件名应与源文件名相同,但后缀名为`.hpp`
[具体详情全局命名规则](#全局命名规则)

#### 内容

头文件应包含所有所需的声明,但不应包含实现
头文件应包含所有所需的依赖,依赖内容见下文：[包含规则](#包含规则)包含规则

### Header-Only 库头文件 (暂定)

#### 位置
若你的头文件是一个Header-Only 库头文件,**请将其放在include/库名** 目录下

#### 命名
随意,但请不要与其他头文件重名,后缀名为`.hpp`

#### 内容

Header-Only 库头文件应包含所有所需的声明,包含实现且包含所有依赖或者你有个专门的依赖头文件来用
函数实现使用inline关键字 

---

## 包含纪律
### 一级
若你已知并且确定你只会用到这些库,请**直接写进配套头文件的include语句中**,避免源文件的引用

### 二级
若你已知并且确定你只会用到这些库,但后续需要添加新的库,请写进**源文件在include你的配套库时语句的下方空一格**

### 三级
若你完全不知道你会用到什么,**应直接写进源文件中**,是否写进include语句中都无所谓,但请不要写太多,避免头文件过大

---

## 全局命名纪律


### 文件命名

文件名要全部小写, 可以包含下划线 ( _ ) 严禁连字符 (-).

例：`cms_toolkit_dll.cpp`

### 变量

统一大驼峰命名法,严禁下划线( _ ),小驼峰命名法

例：
~~~cpp
float StartValue;
float FinalValue;
float Duration;
bool IsRunning;
~~~

### 函数

统一大驼峰命名法,严禁下划线( _ ),小驼峰命名法
尽量动词开头

例：
~~~cpp
void ClearScreen();
bool GetIsRunning() const;
~~~

### 命名空间命名

命名空间命名全部小写,多个单词用嵌套,可以缩写如io

例：
~~~cpp
namespace io {
    namespace i {void ReadFile();}
    namespace o {void WriteFile();}
}
~~~

### 类/结构体命名
统一大驼峰命名法,严禁下划线( _ ),小驼峰命名法

