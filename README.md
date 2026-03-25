### Warning
**Note: The following content is purely my own nonsense. It is intended to be abstract and fun, so please do not apply it to any of your own or your team's production environments!!**

[中文](./README.zh-CN.md) | English

# CODES - C++ - WIP
## COmpact DEfense Coding Style - C++
## C++ Compact Defense Coding Style

## Table of Contents:

- [Preface](#preface)
- [Background](#background)
- [Main Text](#main-text)
- - [Guiding Principles](#guiding-principles)
- - [CPP Version](#version)
- - [Environment](#environment)
- - [File Format](#file-format)
- - [Formatting Discipline](#formatting-discipline)
- - [Declaration Discipline](#declaration-discipline)

- - [Header Files](#header-files)
- - [Include Discipline](#include-discipline)
- - [Global Naming Discipline](#global-naming-discipline)
- - - [File Naming](#file-naming)
- - - [Variables](#variables)
- - - [Functions](#functions)

---

# Preface

- Last Updated: 2026/03/23
- Original Author: HeZhijun4030
- Reference: Google C++ Style Guide

I (CodeManStudio) often release open-source projects, and I **rarely accept** code contributions from other developers. However, if a contributor's coding style is particularly good, it actually causes me considerable trouble – to put it bluntly, I can't understand it 😡😡😡. CodeManStudio has therefore released this own coding style guide, requiring all code submitters to strictly follow the COmpact DEfense Coding Style. Defiers will, by default, transform into femboys within one day.

# Hereinafter, C++ will be uniformly referred to as CPP

Regarding (Tentative): This section indicates areas that may be subject to **significant revisions and updates, ambiguous points, or issues in the future**, and does not imply that other content will not be updated.

---

# Background

On February 20, 2026, during the Spring Festival, after being exposed to CPP, I realized that **Python is fx a p o s**. So I fell in love with CPP. I want to become a dark backend serpent. After a few days of studying CPP Primer, I barely got started. CPP is truly amazing.

CPP programmers know that this language has many powerful features, but with that power comes significant complexity, **making it easy for code to contain errors and difficult to read and maintain.**

The goal of this guide is to detail the considerations for CPP to control **abstraction**. These rules will help keep the code manageable while allowing programmers to efficiently joke around and write code arbitrarily.

Note: This guide is not a CPP tutorial; we assume the reader is already very familiar with CPP.

---

# Main Text

## Guiding Principles
Humanity has survived for 250,000 years, but only the last 4,000 have been meaningful.

So, what were we doing for nearly 250,000 years? We were hiding, writing code, eating bugs, and playing mysterious little games with compilers.

Humanity can no longer live in fear. Nothing can protect us; we must protect ourselves.

While others live their lives in the sunlight, we must fight them in the shadows and prevent them from being exposed to the public eye, so that others can live in a rational, ordinary world.

We are unstable, we are abstract, we are mysterious.

—— CodeManStudioAAA Good Tissue Wholesale

- **Wise AI Usage**: Seek only the principle, not the result. The code you write can only be considered yours if you understand it.
- **Abstract Programming**: Solve problems using the simplest methods.
- **Clear Goals, Clear Framework**.
- **Unnecessary Readability**: Strictly prohibit large-scale comments.
- **Unnecessary Complexity**: Less crap paves the way for us to write better crap.
- **We are tight, we are defensive**: Those who cause memory leaks will be fucked out and fucked to ten minutes of severe punishment until they learn their lesson.
- **Strive with all your might**: Make maximum use of the **semicolon** for no other reason than to write the most abstract code possible.

---

## Version
Everyone must use CPP20/17. Features from CPP23 and above should not be used. This is a stern command 👊👊👊👊👊👊👊👊.

---

## Environment
Solemnly use the command line 😎

### System
Any **Linux** distribution is acceptable, including Android Termux and its derivatives.
**Windows 10/11**

### Compiler strictly limited to:
- **MSVC** V143 (Visual Studio 2022) **or later**
- **GCC** (MinGW-W64) **any version**

**No clang, LLVM or other compilers.**

### Build Tools
- **CMake** 3.20+
- **Ninja** idk

### IDE
- **Visual Studio Code**
- **Visual Studio 2022** (VS2022)
- **CLion**
- **NVim**

---

## File Format
The encoding format is uniformly UTF-8. BOM is optional.
Source file extension is `.cpp`.
Header file extension is `.hpp`.

---

## Formatting Discipline
Use **less than or equal to 4 spaces** for indentation.

Braces **preferably use non-K&R style**, meaning `{` and `}` each occupy their own line, and `}` starts on a new line.

### Universal Global Carriage Return Discipline

If necessary, when 2-6 lines of code block can be written on the same line without exceeding the screen width, they must be written on the same line. Single spaces may be added.
Example:
~~~cpp
int x = 10;int y = 20;int z = 30;
std::cin.clear(); std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');

if (progress >= 1.0f) {IsRunning = false;if (BindTarget) *BindTarget=FinalValue;BindTarget=nullptr;}
if (BindTarget) *BindTarget = StartValue + (FinalValue-StartValue) * ApplyCurve(progress);
~~~

#### The following rules can be derived and assembled according to this idea: i.e., function calls, variable assignments, conditional judgments, loops, etc., that conform to the discipline must be placed on the same line, adding spaces when necessary.

### Functions

If it is a simple function (defined as one where the functionality is clearly evident), such as get/set methods, it must be written on a single line, like:
~~~cpp
int GetX() const { return x_; }
void SetX(int x) { x_ = x; }
int SetX(int x,int y) { return x + y; }
~~~
Braces are optional.

### if-else
Simple judgments prioritize being on a single line. Complex nesting should be expanded with standard indentation.

**Simple judgment (single statement)** — Must be written on one line, braces optional:
~~~cpp
if (!GetIsRunning()) return FinalValue;
if (x > 0) { return 1; }
~~~

**Moderate complexity** allows single-line compactness or appropriate line breaks:
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

**If it is a highly complex judgment with multiple conditions** (e.g., more than 4 levels of nesting), it must be formatted with indentation and line breaks normally.
~~~cpp
if (condition1) 
{
    if (condition2) 
    {
        if (condition3) 
        {
            if (condition4) 
            {
                // business logic
            }
        }
    }
}
~~~

### switch-case
Compact for simple branches, standard expansion for complex branches.
Braces optional.

**Extremely simple case** All cases and execution code written on the same line:
~~~cpp
float BaseTween::ApplyCurve(const float& t)const{switch (CurCurve){case Curve::Linear:return t;case Curve::QuadIn:return t*t;default: return t;}}
~~~

**Normally simple case** Case and execution code written on the same line:
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

**Complex case** Newline and indent:
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
Simple loops prioritize single lines. Complex nesting uses standard indentation.
Example:
~~~cpp
for (int i = 0; i < 10; i++){std::cout << i << std::endl;}

while (true){std::cout << "Hello, world!" << std::endl;}

do{std::cout << "Hello, world!" << std::endl;}while (true);
~~~

---

## Declaration Discipline

### Pointer Declaration
`*` is placed adjacent to the variable name, **not adjacent to the type name**.
Example:
~~~cpp
int *ptr;
~~~

### Reference Declaration
`&` is placed adjacent to the variable name, **not adjacent to the type name**.
Example:
~~~cpp
int &ptr;
~~~

### Pointers/References in Function Parameters
`&`, `*` are placed adjacent to the type.

~~~cpp
void SetValue(int* ptr, int& ref){*ptr = ref;}

void Swap(int* a, int* b) { int t = *a; *a = *b; *b = t; }
~~~

### Pointers/References in Function Return Values
`&`, `*` are placed adjacent to the type.
~~~cpp
int* GetPointer(){return &x;}
int& GetReference(){return x;}
~~~

### const
Place before the type.
~~~cpp
const int x = 10;
const int *ptr = &x;
const int &ref = x;
~~~

---

## Header Files
All header files should use `#define` guards to prevent duplicate inclusion. The guard format is: `<FILENAME(ALL UPPERCASE)>_HPP`.
Add a comment after `#endif` containing the guard name.

Example:
~~~cpp
#ifndef CMS_UTILS_DLL_HPP
#define CMS_UTILS_DLL_HPP
#endif // CMS_UTILS_DLL_HPP
~~~

### Associated Header Files

#### Location
If your header file is associated with a regular source file, place it in the same directory.

#### Naming
The header file name should be the same as the source file name, but with the suffix `.hpp`.
[For specific details, see the Global Naming Rules](#global-naming-rules)

#### Content

Header files should contain all necessary declarations but should not contain implementations.
Header files should include all necessary dependencies. See below for dependency content: [Include Rules](#include-rules)

### Header-Only Library Header Files (Tentative)

#### Location
If your header file is a header-only library header file, **place it in the include/library_name directory**.

#### Naming
Arbitrary, but please avoid name conflicts with other header files. Use the `.hpp` suffix.

#### Content

Header-only library header files should contain all necessary declarations, including implementations, and should include all dependencies, or you can have a dedicated dependency header file for this purpose.
Use the `inline` keyword for function implementations.

---

## Include Discipline
### Level 1
If you know and are certain you will only use these libraries, **directly write them into the include statements of the associated header file** to avoid references in the source file.

### Level 2
If you know and are certain you will only use these libraries for now, but may need to add new libraries later, write them into the **source file, leaving a blank line below the include statement for your associated library**.

### Level 3
If you have no idea what you will need, **write them directly into the source file**. Whether they are written into the include statements or not doesn't matter, but don't include too many to avoid making the header file excessively large.

---

## Global Naming Discipline

### File Naming
File names should be entirely lowercase and may contain underscores ( _ ). Hyphens ( - ) are strictly prohibited.

Example: `cms_toolkit_dll.cpp`

### Variables
Uniformly use PascalCase (upper camel case). Underscores ( _ ) and camelCase (lower camel case) are strictly prohibited.

Example:
~~~cpp
float StartValue;
float FinalValue;
float Duration;
bool IsRunning;
~~~

### Functions
Uniformly use PascalCase (upper camel case). Underscores ( _ ) and camelCase (lower camel case) are strictly prohibited.
Preferably start with a verb.

Example:
~~~cpp
void ClearScreen();
bool GetIsRunning() const;
~~~

### Namespace Naming
Namespace names are entirely lowercase. Multiple words are handled by nesting. Abbreviations like `io` are acceptable.

Example:
~~~cpp
namespace io {
    namespace i {void ReadFile();}
    namespace o {void WriteFile();}
}
~~~

### Class/Struct Naming
Uniformly use PascalCase (upper camel case). Underscores ( _ ) and camelCase (lower camel case) are strictly prohibited.