---
title: JDK热替换功能
date: 2016-11-05 01:11:07
tags: 
     - Java
---

### 热替换原理

现在已经有各种智能的IDE可以为我们生成jar包，war包，ear包，甚至带上了自动替换，部署的功能。但一定会有那么些时候，我们需要修改或是替换jar包，war包，ear包中的某个文件而不是整个重新生成。JDK为我们提供了一些命令让我们可以直接修改jar包，war包，ear包中的某个文件，而不需要重新生成。（jar包，war包，ear包本质上都是zip包或称为压缩包）

### 热替换适用场景

例如，将war包部署到生产环境的服务器上。此时如果需要更改war包中的配置文件时，只需要用jdk提供的命令进行修改即可，无需再到开发工具中修改后重新打包上传，提高效率。

### 热替换工具

用到的工具是jar command，这是jdk自带的工具。其中，我们用到的命令主要是以下几个：

| 命令   | 解释                           |
| ---- | ---------------------------- |
| c    | 创建一个新的压缩包                    |
| t    | 列出压缩包中的所有内容                  |
| x    | 将指定文件或者整个压缩包解压到当前目录          |
| u    | 将当前压缩包更新                     |
| v    | 将你触发的所有动作都打印到标准输出f可以指定压缩包的名字 |

**注意：这里的压缩包可以是jar，war，ear或者其他包。你只需要在调用jar命令的时候，指定你要的后缀名。**

### 热替换示例

我这里以war包为例，修改已经压缩好的war包中的一个配置文件。

示例：在windows上，修改manager.war中的application.properties文件。

操作步骤：

**1. 利用jar -tvf manager.war列出该war包中的文件**

1

由于窗口高度问题，此处只显示了部分文件。从中可以看出，该命令执行后会将war包的所有文件一一显示出来，包括所在路径。

**2. 执行jar -xvf manager.war命令，解压该war包。得到如下结果**

![2]()

上图中的红框中的META-INF,org,WEN-INF即为解压后的文件

**3. 修改application.properties文件**

找到application.properties文件，打开该文件，并将我们想要修改的内容进行修改。然后保存。application.properties文件的所在路径为下图红框中所标注的地方；![4]()

**4.执行jar -uvf manager.war WEN-INF/classes/config/application.properties**

![3]()

上图中的红框部分即为执行过程

**5.执行完上述执行后，即可得到最新的manager.war，如下图所示**

**![5]()**

**6.总结：以上就是修改一个war中的配置文件的过程，主要使用了两个指令**

(1) 利用 jar -xvf manager.war 解压；

(2) 修改application.properties配置文件，利用jar -uvf manager.war WEN-INF/classes/config/application.properties将修改后的配置文件信息更新到manager.war中。得到的manager.war即是最新的war。

参考链接：[http://blog.csdn.net/u013613428/article/details/51669882](http://blog.csdn.net/u013613428/article/details/51669882)