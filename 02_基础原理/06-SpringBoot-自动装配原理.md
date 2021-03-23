# 自动装配原理 SpringBoot

在spirngboot 中的依赖是存储在pom.xml

这个pom.xml在父工程中

### pom.xml

- spring-boot-dependencies:核心依赖在父工程中

- 我们在写或者引入一些SpringBoot依赖的时候,不需要指定版本,就因为有这些版本仓库

  

![1596683114594](06-SpringBoot-%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D%E5%8E%9F%E7%90%86.assets/1596683114594.png)

### 主程序

```java
package com.kuang.springboot01helloworld;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Springboot01HelloworldApplication {

    public static void main(String[] args) {
        // 将spirngboot应用启动
        SpringApplication.run(Springboot01HelloworldApplication.class, args);

    }

}

```

### 注解

![1596683434949](06-SpringBoot-%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D%E5%8E%9F%E7%90%86.assets/1596683434949.png)

![1596683449863](06-SpringBoot-%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D%E5%8E%9F%E7%90%86.assets/1596683449863.png)

#### 获取获选配置

![1596683531884](06-SpringBoot-%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D%E5%8E%9F%E7%90%86.assets/1596683531884.png)

META-INF/spring.factories : 自动配置的核心文件

![1596683717423](06-SpringBoot-%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D%E5%8E%9F%E7%90%86.assets/1596683717423.png)

所有资源加载到配置类中

`properties properties = PropertiesLoaderUtils.loadProperties(resources);`

![1596683673358](06-SpringBoot-%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D%E5%8E%9F%E7%90%86.assets/1596683673358.png)

画一个图



结论:spirngboot所有的自动配置都是在启动的时候扫描并加载:spring.factories所有的自动配置类都在这里面,但是不一定生效,要判断条件是否成立,只要导入了对应start,就有对应的启动器,有了启动器,我们自动装配就会生效,然后就配置成功!

![1596684442017](06-SpringBoot-%E8%87%AA%E5%8A%A8%E8%A3%85%E9%85%8D%E5%8E%9F%E7%90%86.assets/1596684442017.png)

