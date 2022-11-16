本项目为对利用Sandcastle、Doxygen、DocFX生成代码说明文档，并进行比对，且针对项目为C#项目；



## 方案

### 1. [Sandcastle](https://github.com/EWSoftware/SHFB)

Sandcastle是一个微软官方的管理类库的文档编译器，是用于编译发布组件（Assembly）信息的一个工具，该工具是相对比较古老的东西，也早停止了维护，只支持语言仅限于微软旗下的VB/C#/F#/C/C++等；

**文档：**[Getting Started SHFB](http://ewsoftware.github.io/SHFB/html/b772e00e-1705-4062-adb6-774826ce6700.htm)



### 2. [Doxygen](https://github.com/doxygen/doxygen)

Doxygen是一款开平台的类Java文档风格的生成框架，支持多语言C/C++/C#/Objective-C/PHP/Java，可以将程序源码中的特定批注转换成为说明文件，但问题也相对还是比较多的，目前还是比较多的open issue，且在使用过程中，会发现有些类是无法生成文档，原因在于注释字符编码或者注释格式的问题导致（理论上不至于类文档都没有，顶多没有说明），default theme还是挺丑的，不过好在可以自定义html。

**文档：**[Doxygen Manual: Overview](https://www.doxygen.nl/manual/index.html)



### 3. [DocFX](https://github.com/dotnet/docfx)

docfx是微软文档也在使用的工具，其由C#开发，项目隶属于.NET Foundation，MIT协议；仅支持将文档构建成静态Web项目、PDF，同时可以添加md文档进行说明的扩充；同时支持许多自定义操作，满足更多需求；目前支持C#/VB/JavaCcript/TypeScript/Python(coming soon)等

文档：[DocFX - static documentation generator](https://dotnet.github.io/docfx/)


### 功能支持

|    功能支持     |             Sandcastle(SHFB)             |                  Doxygen                   |           DocFX           |
| :-------------: | :--------------------------------------: | :----------------------------------------: | :-----------------------: |
|   语言支持    |  VB/C#/F#/C/C++    |       C/C++/C#/Objective-C/PHP/Java       | C#/VB/JavaCcript/TypeScript/Python(coming soon) |
|   跨平台构建    |     支持（linux/mac下安装Mono >= 5.1.0 或 .NET Core SDK）   |                    支持                    | 支持（linux/mac下安装Mono >= 5.1.0） |
|    构建环境     | (MSBuild 或 dotnet) + .NET FrameWork 4.8 |                  Doxygen                   |          MSBuild          |
|    维护状态     |                 停止维护                 |                  开源维护                  |         开源维护          |
|    输出文件     |       chm、mshc、docx、md、website       | CHM、RTF、PostScript、PDF、HTML、website等 |          website          |
|  支持GUI  |                    是                    |                     是                     |            否             |
|  支持cmd build  |                    是                    |                     是                     |            是             |
|  支持主题更换   |                    否                    |                     是                     |            是             |
| 支持xml资源生成 |                    是                    |                否，需要源码                |            是             |
| 支持添加md文档  |                    是                    |                     是                     |            是             |
|   自定义程度    |                    低                    |                    较高                    |            高             |
|  文档完善程度   |                    高                    |                     高                     |            高             |
|    近期维护     |                    是                    |                     是                     |            是             |
|    开源协议     |                  Ms-PL                   |                  GPL-2.0                   |            MIT            |
|      Star       |                   2K+                    |                    4K+                     |            3k+            |
|      其他       |                                          |   支持类继承体系图（需要插件、Java环境）   |                           |



## 生成
### 1-SandCastle
[SandCastle 生成操作](https://www.cnblogs.com/memoyu/p/16896126.html)<br/>
[SandCastle 生成Web Demo](https://github.com/Memoyu/api-doc-generate/tree/main/process/1-SandCastle)

### 2-Doxygen
[Doxygen 生成操作](https://www.cnblogs.com/memoyu/p/16896203.html)<br/>
[Doxygen 生成Web Demo](https://github.com/Memoyu/api-doc-generate/tree/main/process/2-Doxygen)

### 3-DocFX
[DocFX 生成操作](https://www.cnblogs.com/memoyu/p/16896265.html)<br/>
[DocFX](https://github.com/Memoyu/api-doc-generate/tree/main/process/3-DocFX)


## 案例

[api-doc-generate demo](https://github.com/Memoyu/api-doc-generate/tree/main/demo)

## 分析

综上表可得出一下结论：

- 从对语言的支持上考虑，Doxygen无疑是最合适的；

- 从框架后续可维护性上考虑，可以选择Doxygen 或  DocFX；

- 从生成更多格式的API文档文件类型上考虑，可以选择Sandcastle 或 Doxygen；

- 从界面美观、自定义文档能力的角度上考虑，可以选择Doxygen 或  DocFX；

- 从构建API文档环境搭建的难易程度上考虑，可以选择Doxygen ，只需要Doxygen 本体支持编译即可，而其余两者都需要msbuild的配合构建；

- 从源码可权限上考虑，可以选择Sandcastle 或 DocFX，这两个框架都支持程序集生成的 xml + dll 解析，无需源码介入，而Doxygen 需要扫描源码，进行注释获取，最终生成文档；

