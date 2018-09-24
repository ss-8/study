# 1 spring框架概述

## 1.1 什么是spring

l Spring是一个开源框架，Spring是于2003 年兴起的一个轻量级的Java 开发框架，由Rod Johnson 在其著作Expert One-On-One J2EE Development and Design中阐述的部分理念和原型衍生而来。它是为了解决企业应用开发的复杂性而创建的。框架的主要优势之一就是其分层架构，分层架构允许使用者选择使用哪一个组件，同时为 J2EE 应用程序开发提供集成的框架。Spring使用基本的JavaBean来完成以前只可能由EJB完成的事情。然而，Spring的用途不仅限于服务器端的开发。从简单性、可测试性和松耦合的角度而言，任何Java应用都可以从Spring中受益。Spring的核心是控制反转（IoC）和面向切面（AOP）。简单来说，Spring是一个分层的JavaSE/EE full-stack(一站式) 轻量级开源框架。

- ​



```java

public class UserServiceImpl implements UserService {

	@Override
	public void addUser() {
		System.out.println("a_ico add user");
	}

}
```

## 1.2 配置文件

- l 位置：任意，开发中一般在classpath下（src）
- l 名称：任意，开发中常用applicationContext.xml
- l 内容：添加schema约束

​	约束文件位置：spring-framework-3.2.0.RELEASE\docs\spring-framework-reference\html\ xsd-config.html

```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans 
       					   http://www.springframework.org/schema/beans/spring-beans.xsd">
	<!-- 配置service 
		<bean> 配置需要创建的对象
			id ：用于之后从spring容器获得实例时使用的
			class ：需要创建实例的全限定类名
	-->
	<bean id="userServiceId" class="com.itheima.a_ioc.UserServiceImpl"></bean>
</beans>
```

## 1.13 测试

```java
@Test
public void demo02(){
  //从spring容器获得
  //1 获得容器
  String xmlPath = "com/itheima/a_ioc/beans.xml";
  ApplicationContext applicationContext = new ClassPathXmlApplicationContext(xmlPath);
  //2获得内容 --不需要自己new，都是从spring容器获得
  UserService userService = (UserService) applicationContext.getBean("userServiceId");
  userService.addUser();

}
```



# 2 入门案例：DI【掌握】

-  DI Dependency Injection ,依赖注入
- ​	is a ：是一个，继承。
- ​	has a：有一个，成员变量，依赖。
- ​		class B {
- ​           private A a;   //B类依赖A类
- ​        }
- ​	依赖：一个对象需要使用另一个对象
- ​	注入：通过setter方法进行另一个对象实例设置。



l 例如：

​	class BookServiceImpl{

​        //之前开发：接口 = 实现类  （service和dao耦合）

​		//private BookDao bookDao = new BookDaoImpl();

 		//spring之后 （解耦：service实现类使用dao接口，不知道具体的实现类）

​		private BookDao bookDao;

​		setter方法

   }

​	模拟spring执行过程

​	创建service实例：BookService bookService = new BookServiceImpl()		-->IoC  <bean>

​	创建dao实例：BookDao bookDao = new BookDaoImple()				-->IoC

​	将dao设置给service：bookService.setBookDao(bookDao);				-->DI   <property>



