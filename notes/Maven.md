# maven学习笔记
- [maven是什么](1.-maven是什么？)
- [仓库](8.仓库)

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

## 3. maven 核心概念

+ 1. 约定的目录结构
+ 2. POM
+ 3. 坐标
+ 4. **依赖**
+ 5. 仓库
+ 6. 生命周期/插件/目标
+ 7. 继承
+ 8. 聚合

部分详细解释见下文。

## 4. 常用maven命令
**注意：在命令行下运行maven命令的时候需要进入pom.xml所在的目录下。**
+ 1. 清理： `mvn clean` 
+ 2. 编译主程序: `mvn compile`
+ 3. 编译测试程序： `mvn test-compile`
+ 4. 测试： `mvn test`
+ 5. 打包: `mvn package`
+ 6. 安装: `mvn imstall`
+ 7. 生成站点: `mvn site`

## 5.修改本地仓库默认位置

+ 打开maven解压目录下的\conf\settings.xml
+ 加入如下配置：`<localRepository>D:\MavenRep</localRepository>`(其中的D:\MavenRep即为本地的仓库目录！)

## 6. POM
+ 含义： **Project Object Model** : 项目对象模型（类比：DOM,文档对象模型）
+ pom.xml对于Maven工程是核心配置文件，与构建过程相关的一切设置都在这个文件中进行配置。重要程度相当于web.xml对于动态web工程。

## 7. 坐标

+ 数学中的坐标：使用X,Y,Z三个向量可以唯一定位空间中的任何一个点。
+ **Maven的坐标**：使用下面三个向量在仓库中唯一定位一个Maven工程

  \[1]**g**roupid:公司或者组织域名的倒序+项目名
  
  ```xml
  <groupid>com.ljk.maven</groupid>
  ```
  
  \[2]**a**rtifactid:模块名
  
  ```xml
  <artifactid>Hello</artifactid>
  ```

  \[3]**V**ersion:版本
  
  ```xml
  <version>1.0.0</version>
  ```
+  **Maven 工程的坐标与仓库中的路径对应的关系:**
```xml
<groupid>org.springframework</groupid>
<artifactid>spring-core</artifactid>
<version>4.0.0.RELEASE</version>
```
则其对应的仓库中的路径为：
`org/springframework/spring-core/4.0.0.RELEASE/spring-core-4.0.0.RELEASE.jar`

## 8.仓库
### 仓库的分类
+ 本地仓库：当前电脑上部署的仓库目录，为当前电脑上的所有maven工程服务
+ 远程仓库：
   - 私服：搭建在局域网环境中，为局域网范围内的所有maven工程服务
   - 中央仓库： 架设在Internet上，为全世界的Maven工程服务
   - 中央仓库镜像：为了分担中央仓库的流量，提升用户的访问速度
### 仓库中保存的内容
+ Maven 自身所需的插件
+ 第三方框架或者工具
+ 我们自己写的Maven工程

## 9. 依赖
+ Maven 解析依赖信息时会到本地仓库中查找被依赖的jar包，**对于我们自己开发的Maven工程，使用`mvn install`命令安装后即可进入仓库**
+ 依赖的范围
  - **compile** 范围依赖
    * 对主程序是否有效：有效
    * 对测试程序是否有效： 有效
    * 是否参与打包：参与
    * 是否参与部署：参与
    * 典型例子：spring-core
    
  - **test** 范围依赖
    * 对主程序是否有效：无效
    * 对测试程序是否有效： 有效
    * 是否参与打包：参与
    * 是否参与部署：参与
    * 典型例子：junit
    
  - **provided** 范围依赖
    * 对主程序是否有效：有效
    * 对测试程序是否有效： 有效
    * 是否参与打包：不参与
    * 是否参与部署：不参与
    * 典型例子：servlet-api.jar
    
  ![图示](https://github.com/magentaLi/My-CS-Notes/blob/master/pictures/maven_note_2.png)
    
 ## 10. 生命周期
 + 各个构建环节执行的顺序：不能打乱，必须按照既定的正确顺序来执行
 + Maven的核心程序中定义了抽象的生命周期，生命周期的各个阶段的具体任务是由插件来完成的
 + Maven核心程序为了更好的实现自动化构建，按照这一特点执行生命周期中的各个阶段：不论要执行生命周期的哪一个阶段，都是从这个生命周期的最初的位置开始的
 + 插件和目标
    * 生命周期的各个阶段仅仅定义了要执行的任务是什么
    * 各个阶段和插件的目标是对应的
    * 相似的目标由特定的插件来完成
  
    |生命周期阶段|插件目标|插件|
    |-------------|---------|------|
    |compile|compile|maven-compile-plugin|
    |test-compile|test-compile|maven-compile-plugin|
    * 可以将目标看做“调用插件功能的命令”
  
 ## 11. 依赖
  * 依赖的传递性
    - 好处：可以传递的依赖不必在每个模块工程中都重复声明，在“最下面”的工程中依赖一次即可
    - **注意：** 非compile范围的依赖不能传递，所以在各个工程模块中如果有需要就得重复声明依赖
    
  * 依赖的排除
    - 需要排除的场合
    
     ![图示](https://github.com/magentaLi/My-CS-Notes/blob/master/pictures/maven_note_3.png)
     
    - 排除的方法
    ```xml
      <exclusions>
        <exclusion>
          <groupId>commons-logging</groupId>
          <artifactId>commons-logging</artifactId>
        </exclusion>
      </exclusions>
    ```
   * 依赖的原则
      - 解决模块工程之间的jar包冲突问题
      - 原则1：路径最短者优先
      - 原则2：路径相同者先声明的依赖优先
   * 统一管理依赖的版本，建议的配置方式
      - 在properties标签内使用自定义标签统一声明版本号
      ```xml
          <properties>
              <atljk.spring.version>4.0.0.RELEASE</atljk.spring.version>
          </properties>
      ```
      - 在需要统一设置版本的位置，使用EL表达式引用声明的版本号
      ```xml
          <version>${atljk.spring.version}</version>
      ```
 ## 12.继承
  - 现状：
    Hello依赖的junit:4.0
    HelloFriend依赖的junit:4.0
    MakeFriends依赖的junit:4.9
    
    由于test范围的依赖不能传递：所以必然会分散在各个模块工程中，很容易造成版本不一致
    
  - 需求：统一管理各个模块工程中的junit依赖的版本
  - 解决思路：将junit依赖统一提取到“父”工程中，在自工程中声明junit依赖时不指定版本。
  - 操作步骤：
    1. 创建一个Maven工程作为父工程。注意：**打包方式为pom**
    ```xml
      <groupId>com.atljk.maven</groupId>
      <artifactId>Parent</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <packaging>pom</packaging>
    ```
    2. 在子工程中声明对父工程的引用
    ```xml
    <parent>
      <groupId>com.atljk.maven</groupId>
      <artifactId>Parent</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      
      <!-- 以当前的文件为基准的父工程pom.xml文件的相对路径 -->
      <relativePath>../Parent/pom.xml</relativePath>
    </parent>  
    ```
  
    3. 将子工程的坐标中与父工程坐标中重复的内容删除
    4. 在父工程中统一管理junit的依赖
    
    ```xml
    <!-- 配置依赖的管理 -->
      <dependencyManagement>
        <dependencies>
          <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.9</version>
            <scope>test</scope>
          </dependency>
        </dependencies>
      </dependencyManagement>
    ```
    
    5. 在子工程中删除junit依赖的版本号部分
   注意：**配置继承后，执行安装命令时要先安装父工程**
   
 ## 13. 聚合
 
  + 作用：一键安装各个模块工程
  + 配置方式： 在一个“总的聚合工程”中配置各个参与聚合的模块
  
  ```xml
    <!-- 配置聚合 -->
    <modules>
      <!-- 指定各个子工程的相对路径 -->
      <module>../HelloFriend</module>
      <module>../MakeFriends</module>
      <module>../Hello</module>
    </modules>
  ```
