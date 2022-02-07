# SoCMake
Something of CMake

## cmake_minimum_required 

设置使用的最低cmake版本

## project

设置工程名，如果是在顶层则会存放在变量<font color=blue>CMAKE_PROJECT_NAME</font>,否则存放在<font color=blue>PROJECT_NAME</font>

## set

将普通、缓存或环境变量设置为给定值。

普通变量：set(\<variable\> \<value\>... [PARENT_SCOPE])

缓存：set(\<variable\> \<value\>... CACHE \<type\> \<docstring\> [FORCE])

环境变量：set(ENV{\<variable\>} [\<value\>])

## if

有条件的执行一组命令

复合条件执行的顺序以及相关关键字：https://cmake.org/cmake/help/latest/command/if.html

## option

提供一个选项供用户选择为 ON 或 OFF。如果没有提供初始 \<value\>，则使用 OFF。如果 \<variable\> 已设置为普通或缓存变量，则该命令不执行任何操作

## file

用于需要访问文件系统的文件和路径操作。

## find_package

找到一个包（通常由项目外部提供），并加载其包特定的详细信息。

1. 通过Cmake内置模块引入依赖包(https://cmake.org/cmake/help/latest/manual/cmake-modules.7.html#find-modules)
2. 通过find_package引入非官方的库(该方式只对支持cmake编译安装的库有效)

reference: https://zhuanlan.zhihu.com/p/97369704

## find_library

寻找第三方库

该命令用于查找库。如果指定了 NO_CACHE，则创建由 \<VAR\> 命名的高速缓存条目或普通变量以存储此命令的结果。如果找到库，结果将存储在变量中，除非清除变量，否则不会重复搜索。如果没有找到，结果将是 \<VAR\>-NOTFOUND。

## get_filename_component

3.20已经被cmake_path()命令取代

##  execute_process

执行一个或多个子进程

## include

从文件或模块加载并运行 CMake 代码

include与add_subdirectory的不同

1. include可以重用“cmake代码”
2. add_subdirectory主要用项目存在多个文件夹，然后使用其进行组合

https://cmake.org/pipermail/cmake/2007-November/017897.html

## include_directories

预处理器列表，包括文件搜索目录。将指定目录添加到编译器的头文件搜索路径之下，指定的目录被解释成当前源码路径的相对路径。

## add_subdirectory

将子目录添加到构建

## add_library

## add_dependencies

在顶级目标之间添加依赖关系

用到的情况就是两个targets有依赖关系（通过target_link_libraries解决）并且依赖库也是通过编译源码产生的。这时候一句add_dependencies可以在直接编译上层target时，自动检查下层依赖库是否已经生成。没有的话先编译下层依赖库，然后再编译上层target，最后link depend target。(https://www.cnblogs.com/wpcockroach/p/6625699.html)

## add_executable

使用指定的源文件将可执行文件添加到项目中

## foreach

为列表中的每个值评估一组命令