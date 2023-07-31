## 常用数据库命令
```
#展示所有数据库
show databases;
#使用数据库
use ${databases_name};
#展示当前数据库所有表
shwo tables;
#展示表结构
desc ${table_name};
```
更多数据库命令，可以参考：[MySQL 有这一篇就够（呕心狂敲37k字，只为博君一点赞！！！）](https://blog.csdn.net/weixin_45851945/article/details/114287877)

## mysql数据库导入查询
```
#选择数据库
use ${database_name};
#导入数据（注意sql文件的路径）
source ${sql_path};
```
参考文章：[linux下导入、导出mysql数据库命令](https://blog.csdn.net/weixin_30299539/article/details/94830837)

# StarUML使用教程
[史上最全的StarUML使用教程](https://blog.csdn.net/csdn_20150804/article/details/105004375)
[starUML4.0导出的图片去除水印的方法](https://blog.csdn.net/weixin_44394801/article/details/116376185)
# docker小知识
[Docker MySQL的安装与远程连接](https://blog.csdn.net/hewusheng10/article/details/114581743?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165269436916782425136866%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165269436916782425136866&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-1-114581743-null-null.142^v9^control,157^v4^control&utm_term=dockers+MySQL+%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5&spm=1018.2226.3001.4187)
[Docker容器和本机之间的文件传输。](https://blog.csdn.net/Leafage_M/article/details/72082011)
# cmake的使用
## cmake的简单使用
cmake的最简单粗暴的使用方法，仅限于Windows。
下载cmake软件后，创建文件夹作为一个项目。

在文件夹中新建**CMakeLists.txt**

**Cmake文件**
```cmake
cmake_minimum_required(VERSION 3.5)#最低CMake版本

project (projectname)# 工程名

#添加源文件
aux_source_directory(${CMAKE_SOURCE_DIR} MAIN_FUNC_SRCS)#源文件目录(相对路径)


#添加.h文件
include_directories(${CMAKE_SOURCE_DIR})#.h文件目录(相对路径)


#指定生成目标
add_executable(${PROJECT_NAME} ${MAIN_FUNC_SRCS})
            生成的可执行文件名      所有的源文件
```

**Cmake命令**
```
mkdir build
cd build
cmake ..
make
```
## 文件目录理想结构

```md
└── ttms
   	 ├── config
  	 │    └── config
     ├── src
   	 │    ├── include
     │    └── main.cpp
     └── CMakeLists.txt
```
## cmake较理想结构

```cmake
cmake_minimum_required(VERSION 3.20.2)
project(SunProject)

set(CMAKE_CXX_STANDARD 14)

add_library(${PROJECT_NAME}-lib
        
        )

add_definitions(
       
)

target_include_directories(${PROJECT_NAME}-lib PUBLIC src)

add_executable(${PROJECT_NAME}-exe src/main.cpp)

target_link_libraries(${PROJECT_NAME}-exe PRIVATE ${PROJECT_NAME}-lib)
```

## add_definitions( )
变量名需要以D开头，变量在代码中作为宏定义出现
```cmake
add_definitions(
        -DCONFIG_FILE="${CMAKE_CURRENT_SOURCE_DIR}/config"
)
```

```cpp
std::ifstream conf(CONFIG_FILE"/config");
```

## cmake的资源文章
 [CMake菜谱](https://www.bookstack.cn/read/CMake-Cookbook/content-preface-preface-chinese.md)
 [GitBook](https://sfumecjf.github.io/cmake-examples-Chinese/)
 [CMake 3.21 (中文)](https://runebook.dev/zh-CN/docs/cmake/-index-)
# 正则表达式
## (.*?)知识点
利用这个符号可以在文字中添加变量，这个可以读取变量。
>**.*?**  表示非贪心算法，表示要精确的配对。
>**.***    表示贪心算法，表示要尽可能多的匹配
>**()**   表示要获取括弧之间的信息。

# Visual Studio Code
## VScode 配置
[从零开始手把手教你配置属于你的VS Code](https://www.bilibili.com/video/BV1TT4y1g7aF?spm_id_from=333.999.0.0&vd_source=c7f0a8a1b453261561b18cd69cebd8b3)
## VScode 代码格式配置文件
>.clang-format
```
# 语言: None, Cpp, Java, JavaScript, ObjC, Proto, TableGen, TextProto
Language:	Cpp
# BasedOnStyle:	LLVM
# 访问说明符(public、private等)的偏移
AccessModifierOffset:	-4
# 开括号(开圆括号、开尖括号、开方括号)后的对齐: Align, DontAlign, AlwaysBreak(总是在开括号后换行)
AlignAfterOpenBracket:	Align
# 连续赋值时，对齐所有等号
AlignConsecutiveAssignments:	true
# 连续声明时，对齐所有声明的变量名
AlignConsecutiveDeclarations:	true
# 左对齐逃脱换行(使用反斜杠换行)的反斜杠
AlignEscapedNewlinesLeft:	true
# 水平对齐二元和三元表达式的操作数
AlignOperands:	true
# 对齐连续的尾随的注释
AlignTrailingComments:	true
# 允许函数声明的所有参数在放在下一行
AllowAllParametersOfDeclarationOnNextLine:	true
# 允许短的块放在同一行
AllowShortBlocksOnASingleLine:	false
# 允许短的case标签放在同一行
AllowShortCaseLabelsOnASingleLine:	false
# 允许短的函数放在同一行: None, InlineOnly(定义在类中), Empty(空函数), Inline(定义在类中，空函数), All
AllowShortFunctionsOnASingleLine:	Empty
# 允许短的if语句保持在同一行
AllowShortIfStatementsOnASingleLine:	false
# 允许短的循环保持在同一行
AllowShortLoopsOnASingleLine:	false
# 总是在定义返回类型后换行(deprecated)
AlwaysBreakAfterDefinitionReturnType:	None
# 总是在返回类型后换行: None, All, TopLevel(顶级函数，不包括在类中的函数), 
#   AllDefinitions(所有的定义，不包括声明), TopLevelDefinitions(所有的顶级函数的定义)
AlwaysBreakAfterReturnType:	None
# 总是在多行string字面量前换行
AlwaysBreakBeforeMultilineStrings:	false
# 总是在template声明后换行
AlwaysBreakTemplateDeclarations:	false
# false表示函数实参要么都在同一行，要么都各自一行
BinPackArguments:	true
# false表示所有形参要么都在同一行，要么都各自一行
BinPackParameters:	true
# 大括号换行，只有当BreakBeforeBraces设置为Custom时才有效
BraceWrapping:   
  # class定义后面
  AfterClass:	false
  # 控制语句后面
  AfterControlStatement:	false
  # enum定义后面
  AfterEnum:	false
  # 函数定义后面
  AfterFunction:	false
  # 命名空间定义后面
  AfterNamespace:	false
  # ObjC定义后面
  AfterObjCDeclaration:	false
  # struct定义后面
  AfterStruct:	false
  # union定义后面
  AfterUnion:	false
  # catch之前
  BeforeCatch:	true
  # else之前
  BeforeElse:	true
  # 缩进大括号
  IndentBraces:	false
# 在二元运算符前换行: None(在操作符后换行), NonAssignment(在非赋值的操作符前换行), All(在操作符前换行)
BreakBeforeBinaryOperators:	NonAssignment
# 在大括号前换行: Attach(始终将大括号附加到周围的上下文), Linux(除函数、命名空间和类定义，与Attach类似), 
#   Mozilla(除枚举、函数、记录定义，与Attach类似), Stroustrup(除函数定义、catch、else，与Attach类似), 
#   Allman(总是在大括号前换行), GNU(总是在大括号前换行，并对于控制语句的大括号增加额外的缩进), WebKit(在函数前换行), Custom
#   注：这里认为语句块也属于函数
BreakBeforeBraces:	Custom
# 在三元运算符前换行
BreakBeforeTernaryOperators:	true
# 在构造函数的初始化列表的逗号前换行
BreakConstructorInitializersBeforeComma:	false
# 每行字符的限制，0表示没有限制
ColumnLimit:	200
# 描述具有特殊意义的注释的正则表达式，它不应该被分割为多行或以其它方式改变
CommentPragmas:	'^ IWYU pragma:'
# 构造函数的初始化列表要么都在同一行，要么都各自一行
ConstructorInitializerAllOnOneLineOrOnePerLine:	false
# 构造函数的初始化列表的缩进宽度
ConstructorInitializerIndentWidth:	4
# 延续的行的缩进宽度
ContinuationIndentWidth:	4
# 去除C++11的列表初始化的大括号{后和}前的空格
Cpp11BracedListStyle:	false
# 继承最常用的指针和引用的对齐方式
DerivePointerAlignment:	false
# 关闭格式化
DisableFormat:	false
# 自动检测函数的调用和定义是否被格式为每行一个参数(Experimental)
ExperimentalAutoDetectBinPacking:	false
# 需要被解读为foreach循环而不是函数调用的宏
ForEachMacros:	[ foreach, Q_FOREACH, BOOST_FOREACH ]
# 对#include进行排序，匹配了某正则表达式的#include拥有对应的优先级，匹配不到的则默认优先级为INT_MAX(优先级越小排序越靠前)，
#   可以定义负数优先级从而保证某些#include永远在最前面
IncludeCategories: 
  - Regex:	'^"(llvm|llvm-c|clang|clang-c)/'
    Priority:	2
  - Regex:	'^(<|"(gtest|isl|json)/)'
    Priority:	3
  - Regex:	'.*'
    Priority:	1
# 缩进case标签
IndentCaseLabels:	false
# 缩进宽度
IndentWidth:	4
# 函数返回类型换行时，缩进函数声明或函数定义的函数名
IndentWrappedFunctionNames:	false
# 保留在块开始处的空行
KeepEmptyLinesAtTheStartOfBlocks:	true
# 开始一个块的宏的正则表达式
MacroBlockBegin:	''
# 结束一个块的宏的正则表达式
MacroBlockEnd:	''
# 连续空行的最大数量
MaxEmptyLinesToKeep:	1
# 命名空间的缩进: None, Inner(缩进嵌套的命名空间中的内容), All
NamespaceIndentation:	Inner
# 使用ObjC块时缩进宽度
ObjCBlockIndentWidth:	4
# 在ObjC的@property后添加一个空格
ObjCSpaceAfterProperty:	false
# 在ObjC的protocol列表前添加一个空格
ObjCSpaceBeforeProtocolList:	true
# 在call(后对函数调用换行的penalty
PenaltyBreakBeforeFirstCallParameter:	19
# 在一个注释中引入换行的penalty
PenaltyBreakComment:	300
# 第一次在<<前换行的penalty
PenaltyBreakFirstLessLess:	120
# 在一个字符串字面量中引入换行的penalty
PenaltyBreakString:	1000
# 对于每个在行字符数限制之外的字符的penalty
PenaltyExcessCharacter:	1000000
# 将函数的返回类型放到它自己的行的penalty
PenaltyReturnTypeOnItsOwnLine:	60
# 指针和引用的对齐: Left, Right, Middle
PointerAlignment:	Left
# 允许重新排版注释
ReflowComments:	true
# 允许排序#include
SortIncludes:	true
# 在C风格类型转换后添加空格
SpaceAfterCStyleCast:	false
# 在赋值运算符之前添加空格
SpaceBeforeAssignmentOperators:	true
# 开圆括号之前添加一个空格: Never, ControlStatements, Always
SpaceBeforeParens:	ControlStatements
# 在空的圆括号中添加空格
SpaceInEmptyParentheses:	false
# 在尾随的评论前添加的空格数(只适用于//)
SpacesBeforeTrailingComments:	2
# 在尖括号的<后和>前添加空格
SpacesInAngles:	true
# 在容器(ObjC和JavaScript的数组和字典等)字面量中添加空格
SpacesInContainerLiterals:	true
# 在C风格类型转换的括号中添加空格
SpacesInCStyleCastParentheses:	true
# 在圆括号的(后和)前添加空格
SpacesInParentheses:	true
# 在方括号的[后和]前添加空格，lamda表达式和未指明大小的数组的声明不受影响
SpacesInSquareBrackets:	true
# 标准: Cpp03, Cpp11, Auto
Standard:	Cpp11
# tab宽度
TabWidth:	4
# 使用tab字符: Never, ForIndentation, ForContinuationAndIndentation, Always
UseTab:	Never
```

# Qt编程知识
## Qt使用MySQL CMakeLists.txt配置
qt6.1.3使用MySQL问题有点多，我解决不了，所以我进行版本降级，使用qt6.0.4

参考文章：[Qt Creator 6.1.0连接MySql8.0.23配置](https://blog.csdn.net/weixin_42043127/article/details/115363582)
生成了qsqlmysql.dll和qsqlmysql.dll.debug，并将其放到D:\Qt\6.0.4\mingw81_64\plugins\sqldrivers
安装完整的mysql，将libmysql.dll放到D:\Qt\6.0.4\mingw81_64\bin

```
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Sql)
target_link_libraries(first PRIVATE Qt${QT_VERSION_MAJOR}::Sql)

# Visual Studio编译器小问题解决
## Visual Studio使用scanf和printf函数
在文件头部加入	#define _CRT_SECURE_NO_WARNINGS
## 创建文件自动生成#define _CRT_SECURE_NO_WARNINGS
在newc++file文件中加入#define _CRT_SECURE_NO_WARNINGS

newc++file文件位置：Microsoft Visual Studio\Common7\IDE\VC\vcprojectitems\newc++file
```
## 前端ts
当使用ts时引入js组件时，可以同时引入@types/xxx达到使用ts的目的。