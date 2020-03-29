# IDEA Java相对文件问题

在此记录下困扰了20分钟的IDEA 相对文件问题。

## 问题出现场景

```java
 BufferedInputStream in = new BufferedInputStream(
                        new FileInputStream("Java8/StandardIo/Redirecting.java"));
```

报错信息如下：

```
Exception in thread "main" java.lang.RuntimeException: java.io.FileNotFoundException: ../Java8/StandardIo/Redirecting.java (No such file or directory)
```

## 问题定位

当前运行项目/main方法的工作目录问题，IDEA中查看工作目录的方法：

```java
 System.out.println(System.getProperty("user.dir"));
```

## 问题修复

在IDEA中设置工作目录：

![](./img/idea_file_relativePath.jpg)

## 问题延伸1——IDEA项目结构

```
--src　　应用程序源代码与测试代码的根目录

　　--main　　应用程序代码的源目录

　　　　--java　　源代码

　　　　--resources　　项目用到的资源文件

　　--test　　测试程序代码的源目录

　　　　--java　　测试代码

　　　　--resources　　测试用到的资源文件

--target　　运行目标目录，属于临时的
```



![](/Users/yuexiangfan/Library/Application Support/typora-user-images/image-20200329222759982.png)

因此应该将working dictionary设置为：

```
/Users/yuexiangfan/coding/JavaProject/learning_coding_language/src/main/java/com/coding/lanuage
```

