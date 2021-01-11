# 0 链接

https://how2j.cn/

https://www.zhihu.com/people/Java_3y/answers

课程链接：https://github.com/ZhongFuCheng3y/3y/blob/master/src/resource.md

## 0.1 写在前言

在我看来，无论学习什么技术都好，在**学习该项技术的细节之前**都得知道：**这项技术是什么，为什么我要学习这项技术，学习了这项技术有什么好处**。

- 看似好像我在说多余的话，但如果你在学习某项技术的时候无法回答上面的三个问题。再过几天，你很大程度上会**忘记**这项你所“学过”的技术。
- 比如说，如何你连“为什么要用多线程”你都无法用通俗的话来解释清楚。即便你**当时**学习的时候知道多线程可以用xxx方式来创建，多线程的xxx的api。那再过两个月，人家问你”Java多线程有什么用啊？”。你想想你还能答什么，我认为你是记不住“多线程可以用xxx方式来创建、多线程的xxx的api”这些知识点了。
- 再比如说，如果学习Spring时不知道IOC和new对象有什么区别，那我为啥不直接new对象而要那么麻烦去学Spring呢？

如果你是零基础学习Java并**理解力不是爆棚**的话，我建议以**视频**学习为主。

**可能**你会看到这样类似的言论：

- “看视频学习太慢了”
- “直接看源码啊，源码就是最好的解释”
- “有问题直接Google啊，用什么百度”
- “最好的资料是官网文档”
- …..

但是，那都是对有经验的人或者高智商的人群来讲的。

如果是**零基础普通人**，看视频学习/看不懂源码/用百度/看中文博客来学习**不丢人**。

- ps:如果看的视频讲师的语速不是特别快，建议以1.5或者1.75倍速观看。

## 0.2 学习重点

在学习Java基础时，我简单来说一下**什么东西可以不碰**：

- `&^|`位运算符，`++i`和`i++`类似这种绕死人的语法
- 内部类
- AWT,SWING编程
- 注解

需要**深入理解**的知识点：

- 流程控制

- 面向对象的概念

- Java语法

- - this指针、重写和重载、final、static等等这些基础的东西

- 集合(包括泛型)

- - 常用的集合类

- IO流

- - IO流代码的编写  

- (理解这些知识点，能够在有提示的情况下码出代码，但**不要为了一些细节钻牛角尖**)

**简单过一遍**的知识：

- 异常
- 多线程
- 网络编程
- 反射机制
- (你**得知道这个知识点是干嘛用的**，为什么要学这个知识点，能看懂具体的代码！)

## 0.3 实用的工具

对于上面所说**深入理解**的知识点，我个人是**非常建议在学习期间写笔记(博客)的**。如果你想写笔记的话，**最好直接**就用`markdown`语法来编写，而不是用word/简单的记事本。

markdown语法非常好学，几分钟跟着就可以学习了，几乎所有的it博客网站都支持`markdown`：

- markdown学习：https://www.jianshu.com/p/q81RER

如果喜欢**画思维导图**的，我这里推荐processOn就可以了。无需下载Xmind这么麻烦了：

- ProcessOn来画思维导图：https://www.processon.com/i/5815483ce4b0baccb2d1f8c6

有的时候并不需要使用IDEA打开一个`.java`或者`.xml`这样的文件，可以使用`notepad++`记事本：

- NotePad++记事本：https://notepad-plus-plus.org/

学会科学上网和使用Chrome浏览器，比如说下载拦截广告插件，英语翻译插件

- Chrome浏览器：https://www.google.com/chrome/
- 拦截广告插件：https://chrome.google.com/webstore/search/uBlock%20Origin?hl=zh-CN&_category=extensions
- 英语翻译插件：https://chrome.google.com/webstore/search/%E6%B2%99%E6%8B%89%20%E6%9F%A5%20%E8%AF%8D?hl=zh-CN

虽然是快速学习Java，但学完上面的**估计得一个月了**(:..

一个月发现都是面向控制台编程(console)，输入输出一些数据来玩。

# 1 反射机制

## 1.1 类对象

- 获取类对象的方法

<img src="https://i.loli.net/2020/12/15/LcuEqWYajwMSPr9.png" alt="image-20201129225723572" style="zoom:50%;" />

![image-20210106101741040](https://i.loli.net/2021/01/06/KND74YtaRwJW9OG.png)

## 1.2 获取类对象的方法

![image-20210106102102875](https://i.loli.net/2021/01/06/6NbEJWjBMrIGn4P.png)

## 1.3 通过反射机制来操作对象

![image-20210106104615855](https://i.loli.net/2021/01/06/AhzDPTi9jrk4fBK.png)

![image-20210106104816449](https://i.loli.net/2021/01/06/6TGevw5M3WBEZSu.png)

- getField和getDeclaredField的区别
  这两个方法都是用于获取字段
  getField **只能获取**public的，包括**从父类继承**来的字段。
  getDeclaredField 可以获取本类所有的字段，**包括private**的，但是**不能获取继承**来的字段。 (**注**： 这里只能获取到private的**字段**，但并不能访问该private字段的**值**,除非加上**setAccessible(true)**)

## 1.4 反射的用途 - 其实就是解决一个问题：某些代码如果要换参数，必须重新编译和运行

反射非常强大，但是学习了之后，会不知道该如何使用，反而觉得还不如直接调用方法来的直接和方便。

通常来说，需要在学习了[Spring ](https://how2j.cn/k/spring/spring-ioc-di/87.html)的依赖注入，反转控制之后，才会对反射有更好的理解，但是刚学到这里的同学，不一定接触了Spring，所以在这里举两个例子，来演示一下反射的一种实际运用。

### 1.4.1 首先创建两个个 业务类

这两个业务类很简单，就是各自都有一个业务方法，分别打印不同的字符串

```java
package reflection;

public class Service1 {

	public void doService1(){
		System.out.println("业务方法1");
	}
}
```
```
package reflection;

public class Service2 {

	public void doService2(){
		System.out.println("业务方法2");
	}
}
```

### 1.4.2 使用非反射方式来处理

当需要从第一个业务方法切换到第二个业务方法的时候，使用非反射方式，必须修改代码，并且重新编译运行，才可以达到效果

```java
package reflection;

public class Test {

	public static void main(String[] args) {
		new Service1().doService1();
	}
}
```

```java
package reflection;

public class Test {

	public static void main(String[] args) {
//		new Service1().doService1();
		new Service2().doService2();
	}
}
```

### 1.4.3 使用反射方式来处理 

使用反射方式，首先准备一个配置文件，就叫做spring.txt吧, 放在src目录下。 里面存放的是类的名称，和要调用的方法名。
在测试类Test中，首先取出类名称和方法名，然后通过反射去调用这个方法。

当需要从调用第一个业务方法，切换到调用第二个业务方法的时候，不需要修改一行代码，也不需要重新编译，只需要修改配置文件spring.txt，再运行即可。

这也是[Spring框架](https://how2j.cn/k/spring/spring-ioc-di/87.html)的最基本的原理，只是它做的更丰富，安全，健壮。

```java
class=reflection.Service1
method=doService1
```

```java
package reflection;

import java.io.File;
import java.io.FileInputStream;
import java.lang.reflect.Constructor;
import java.lang.reflect.Method;
import java.util.Properties;

public class Test {

	@SuppressWarnings({ "rawtypes", "unchecked" })
	public static void main(String[] args) throws Exception {

		//从spring.txt中获取类名称和方法名称
		File springConfigFile = new File("e:\\project\\j2se\\src\\spring.txt");
		Properties springConfig= new Properties();
		springConfig.load(new FileInputStream(springConfigFile));
		String className = (String) springConfig.get("class");
		String methodName = (String) springConfig.get("method");
		
		//根据类名称获取类对象
		Class clazz = Class.forName(className);
		//根据方法名称，获取方法对象
		Method m = clazz.getMethod(methodName);
		//获取构造器
		Constructor c = clazz.getConstructor();
		//根据构造器，实例化出对象
		Object service = c.newInstance();
		//调用对象的指定方法
		m.invoke(service);
		
	}
}
```

# 2 Static

- static先于对象被系统加载，所以静态方法不能调用非静态的，但是非静态的可以调用静态的

![image-20201203075604403](https://i.loli.net/2020/12/19/yIBfRovl3LUeXHC.png)

## 2.1 静态代码块

![image-20201203075819751](C:%5CUsers%5CDeon%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20201203075819751.png)

# 3 抽象类

![image-20201203100950348](https://i.loli.net/2020/12/15/AwMKXnriahQCBS9.png)

![image-20201203183621632](https://i.loli.net/2020/12/19/mtaBi1EkfrA378l.png)

# 4 Exception

![image-20201214144828928](https://i.loli.net/2020/12/14/lfWjG8QeNzKgBTn.png)

# 5 Collection集合框架 - 保存对象List，Set，Map

![image-20201214221952376](https://i.loli.net/2020/12/14/Wv5r4ML8sYU3BtO.png)

![image-20201215104407696](https://i.loli.net/2020/12/15/1D2vU5xIcRjfJiq.png)

- list和数组的区别在于，list可以自动扩容

## 5.1 Map

![image-20201227121656395](https://i.loli.net/2020/12/27/WC6wSjAVRE9z3r8.png)

### 5.1.1 HashMap和TreeMap

![image-20201227122106378](https://i.loli.net/2020/12/27/iILBFsxoHXUr8fM.png)

