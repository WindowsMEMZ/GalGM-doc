# GalGM开发者文档
## 介绍
### 什么是GalGM？
GalGM这个名称是Galgame Generator Modify的简写（对，取名就是这么随意，以后可能会改）。这是一个Galgame生成器，你可以在这里用最简单的方法来生成Galgame。
### 什么是GalGR
GalGR是Galgame Generator Runtime 的简写（同样随意）。仅通过读取data和asset(或gef)文件来运行，GalGM并不会更改它的源代码。
### 特点
- 仿Visual Studio的外观
- 代码高亮
- 实时代码错误检查
- 超快的编译速度
- 诊断工具
- ...
## 重要提醒
现在的GalGM处于非常早期预览（真的非常）的阶段，遇到各种Bug请不要惊讶，同时请记得养成随时保存的好习惯（因为随时可能因为程序崩溃而丢失）。遇到Bug请第一时间联系我以尽快修复。
## 工作进度
- [x] Visual Studio外观
- [ ] 更好的调试器
- [ ] 更好的默认外观（对于GalGR）
- [ ] 自定义外观（对于GalGR）
- [ ] 手动编辑并编译GalGR源码
- [ ] 代码补全
## 编写代码
要开始编写程序主代码，请先创建一个项目，并转到“对话”标签页。
### 人物名与对话文本
请使用`#`开头+当前人物名的方式来定义首个或切换另一人物。
例：
```GC
#WindowsMEMZ
```
在人物名下方输入人物的对话文本
例：
```GC
#WindowsMEMZ
大家好，这是一条测试文本捏～
```
输入多行文本以将对话分为多次点击完成
例：
```GC
#WindowsMEMZ
大家好，这是一条测试文本捏～
这还是一条测试文本～
```
另起一行并再次输入`#人物名`以切换人物
例：
```GC
#WindowsMEMZ
大家好，这是一条测试文本捏～
#memz233
这是另一个人说的测试文本捏～
```
#### 需要注意的地方
- 所有代码必须以`#`开头，下面的写法是错误的：
    ```GC
    这是一个错误代码哟～
    #WindowsMEMZ
    这样的代码不能被编译捏～
    ```
- 每次切换人物必须至少说一句话，以下写法是错误的：
    ```GC
    #WindowsMEMZ
    这是错误示范捏～
    #memz233
    #WindowsMEMZ
    上面这样是不对的哟～
    ```
   要想实现相同的效果，请使用：
    ```GC
    #WindowsMEMZ
    这是正确的
    #memz233
     
    #WindowsMEMZ
    这样就对了
    ```
   **注意：一定要在此处`#memz233`的下一行（第4行）添加一个空格**
- 目前没有办法处理一句话开头为`#`的情况，在必须出现这种文本的情况时，请考虑在本句话的开头添加空格
### 使用资源
#### 背景图片
**首个背景图片不能在代码中处理，请在“资源”选项卡中手动添加**
要切换背景图时，请使用`~`+资源名称进行切换，如：
```GC
#WindowsMEMZ
现在显示的是初始背景图
~这里是新背景图的资源名
现在显示的是新的背景图
```
#### 背景音乐
要开始播放或切换背景音乐时，请使用`&`+资源名称进行切换，如：
```GC
#WindowsMEMZ
现在没有播放任何背景音乐
&这里是新背景音乐的资源名
现在开始播放背景音乐了
&这里是另一个背景音乐的资源名
现在背景音乐切换为了另一个
```
#### 人物语音/配音
要将某句话加上配音时，请在末尾加上`|`(`Shift+\`)+资源名称以添加，如：
```GC
#WindowsMEMZ
这句话没有配音
这句话带有一个配音|这里是配音文件的资源名
```
## 项目设置
### 使用加密
在不使用加密的情况下，所有需要使用的资源会被直接拷贝到输出目录的`assets`文件夹下，如果您需要保护这些资源，可以使用加密。
**这里有两点需要注意：**
1. 加密会减慢编译时和软件开启时的速度
2. 加密**并不能**完全保护您的资源，它只是使用了加密7z来加密资源，如果您需要更高级的加密，请自寻方法。
## 其他需要注意的地方
- 代码的结尾**有且只能**有一行空行，当没有空行时，GalGM会自动为您添加，当空行过多时则会抛出错误
- 当遇到GalGM本身的运行时错误时，可以考虑排查您的代码是否符合规范，特别是这个错误是在尝试编译时发生的，编译器**并不能**检查出所有错误。
## 对于各种奇怪文件扩展名的解释
- `*.galgmproj`: GalGM Project的简写
- `*.gc`: Galgame Code的简写
- `*.gef`: Galgame Encrypted Files的简写
- `*.gds`: Galgame Debug Symbols的简写
- `*.resg`: Resources for Galgame的简写
- `*.wggproj`: WindowsMEMZ's GalGR Project File的简写
## 关于
GalGM和GalGR均为WindowsMEMZ单人独立开发

Darock Studio以及域名darock.top属于WindowsMEMZ

Visual Studio 是 Microsoft Corporation 的商标 (在多个国家或地区注册)

### 本项目使用的第三方库
- [DockPanel Suite](https://github.com/dockpanelsuite/dockpanelsuite) by Weifen Luo
- [SevenZipSharp](https://github.com/squid-box/SevenZipSharp) by squid-box(Forked from [tomap's](https://github.com/tomap/SevenZipSharp))
- [ICSharpCode.Decompiler](https://github.com/icsharpcode/ILSpy/) by [ILSpy Contributors](https://github.com/icsharpcode/ILSpy/graphs/contributors)

### 加入我们
若有意加入我们开发，请联系QQ: 3245146430

文档版本0.2.0-Preview
