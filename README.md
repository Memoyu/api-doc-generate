本项目为对利用Sandcastle、Doxygen、DocFX生成代码说明文档，并进行比对，且针对项目为C#项目；



## 方案

### 1. [Sandcastle](https://github.com/EWSoftware/SHFB)

Sandcastle是一个微软官方的管理类库的文档编译器，是用于编译发布组件（Assembly）信息的一个工具；

**文档：**[Getting Started SHFB](http://ewsoftware.github.io/SHFB/html/b772e00e-1705-4062-adb6-774826ce6700.htm)



### 2. [Doxygen](https://github.com/doxygen/doxygen)

支持多语言，可以将程序源码中的特定批注转换成为说明文件。

**文档：**[Doxygen Manual: Overview](https://www.doxygen.nl/manual/index.html)



### 3. [DocFX](https://github.com/dotnet/docfx)

目前微软文档使用的工具是 docfx ，这一项目隶属于.NET Foundation，MIT协议；支持将文档构建成静态Web项目，同时可以添加md文档进行说明的扩充；同时支持许多自定义操作，满足更多需求；

文档：[DocFX - static documentation generator](https://dotnet.github.io/docfx/)



### 功能支持

|    功能支持     |             Sandcastle(SHFB)             |                  Doxygen                   |           DocFX           |
| :-------------: | :--------------------------------------: | :----------------------------------------: | :-----------------------: |
|   跨平台构建    |                   支持                   |                    支持                    | 支持（安装Mono >= 5.1.0） |
|    构建环境     | (MSBuild 或 dotnet) + .NET FrameWork 4.8 |                  Doxygen                   |          MSBuild          |
|    维护状态     |                 停止维护                 |                  开源维护                  |         开源维护          |
|    输出文件     |       chm、mshc、docx、md、website       | CHM、RTF、PostScript、PDF、HTML、website等 |          website          |
|  支持cmd build  |                    是                    |                     是                     |            是             |
|  支持主题更换   |                    否                    |                     是                     |            是             |
| 支持xml资源生成 |                    是                    |                否，需要源码                |            是             |
| 支持添加md文档  |                    否                    |                     是                     |            是             |
|   自定义程度    |                    低                    |                    较高                    |            高             |
|  文档完善程度   |                    高                    |                     高                     |            高             |
|    近期维护     |                    是                    |                     是                     |            是             |
|    开源协议     |                  Ms-PL                   |                  GPL-2.0                   |            MIT            |
|      Star       |                   2K+                    |                    4K+                     |            3k+            |
|      其他       |                                          |   支持类继承体系图（需要插件、Java环境）   |                           |



## 生成

[SandCastle](https://github.com/Memoyu/api-doc-generate/tree/main/process/1-SandCastle)

[Doxygen](https://github.com/Memoyu/api-doc-generate/tree/main/process/2-Doxygen)

[DocFX](https://github.com/Memoyu/api-doc-generate/tree/main/process/3-DocFX)



## 案例

[api-doc-generate demo](https://github.com/Memoyu/api-doc-generate/tree/main/demo)



## 分析

综上表可得出一下结论：

- 从框架后续可维护性上考虑，可以选择Doxygen 或  DocFX；

- 从生成更多格式的API文档文件类型上考虑，可以选择Sandcastle 或 Doxygen；

- 从界面美观、自定义文档能力的角度上考虑，可以选择Doxygen 或  DocFX；

- 从构建API文档环境搭建的难易程度上考虑，可以选择Doxygen ，只需要Doxygen 本体支持编译即可，而其余两者都需要msbuild的配合构建；

- 从源码可权限上考虑，可以选择Sandcastle 或 DocFX，这两个框架都支持程序集生成的 xml + dll 解析，无需源码介入，而Doxygen 需要扫描源码，进行注释获取，最终生成文档；
