# 1 spring框架概述

## 1.1 什么是spring

l Spring是一个开源框架，Spring是于2003 年兴起的一个轻量级的Java 开发框架，由Rod Johnson 在其著作Expert One-On-One J2EE Development and Design中阐述的部分理念和原型衍生而来。它是为了解决企业应用开发的复杂性而创建的。框架的主要优势之一就是其分层架构，分层架构允许使用者选择使用哪一个组件，同时为 J2EE 应用程序开发提供集成的框架。Spring使用基本的JavaBean来完成以前只可能由EJB完成的事情。然而，Spring的用途不仅限于服务器端的开发。从简单性、可测试性和松耦合的角度而言，任何Java应用都可以从Spring中受益。Spring的核心是控制反转（IoC）和面向切面（AOP）。简单来说，Spring是一个分层的JavaSE/EE full-stack(一站式) 轻量级开源框架。

- 轻量级：与EJB对比，依赖资源少，销毁的资源少。
- 分层： 一站式，每一个层都提供的解决方案
- web层：struts，spring-MVC
- service层：spring
- dao层：hibernate，mybatis ， jdbcTemplate  --> spring-data



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

