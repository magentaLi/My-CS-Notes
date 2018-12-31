# maven学习笔记
## 1. maven是什么？
+ Maven是一款服务于Java平台的自动化构建工具。

&emsp; Make -> Ant -> **Maven** -> Gradle

+ 构建
1. 概念：以为“Java源文件”、“框架配置文件”，“JSP”、“图片”等资源为“源材料”，去生产一个可以运行的项目的过程。
2. 编译：Java源文件->编译->字节码文件->交给JVM去执行
3. 部署 一个BS项目最终运行的并不是动态web工程本身，而是这个web工程“编译的结果”
![如图](https://github.com/magentaLi/My-CS-Notes/blob/master/pictures/maven-note-1.png)
**开发过程中，所有路径或配置文件中的配置的类路径等都是以编译的结果的目录结构为标准的。**

+ 构建过程中的各个环节
  1. 清理：将以前编译得到的旧的class字节码文件删除，为下一次编译做准备。
  2. 编译：将Java源程序编译成class字节码文件
  3. 测试：自动测试，自动调用junit程序
  4. 报告：测试程序执行的结果
  5. 打包：动态web程序打成war包，java工程打成jar包
  6. 安装：Maven的特定概念，将打包得到的文件复制到“仓库”的指定位置中
  7. 部署：将动态web工程生成的war包复制到servlt容器的指定目录下，使其可以运行
+ 自动化构建

## 2.安装Maven核心程序
  + 需要java环境,[下载maven](http://maven.apache.org/download.cgi)
  + 配置环境变量
    -变量名：MAVEN_HOME或者M2_HOME
    * 变量值：解压下载的maven到一个不含中文的目录下时的bin目录的上一级目录（如：D:\apache-maven-3.6.0）
    -变量名：path
    * 变量值：bin目录所在目录（如：D:\apache-maven-3.6.0\bin）
  + 验证：运行 `mvn -v` 命令查看maven版本
