到底多么简单

- jdk1.8
- maven3.6.1
- springboot:最新版
- IDEA

![1596681917764](04-SpringBoot-%E7%A8%8B%E5%BA%8F.assets/1596681917764.png)

一般直接在idea中创建就OK

![1596682136895](04-SpringBoot-%E7%A8%8B%E5%BA%8F.assets/1596682136895.png)

![1596682201758](04-SpringBoot-%E7%A8%8B%E5%BA%8F.assets/1596682201758.png)

```java
package com.kuang.springboot01helloworld.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

/**
 * @author victor
 * @site https://victorfengming.github.io/
 * @company XDL
 * @project springboot-01-helloworld
 * @package com.kuang.springboot01helloworld.controller
 * @created 2020-07-24 14:17
 * @function ""
 */

/*
*
* Spring boot 热部署
* */

@Controller
@RequestMapping("/hello")
public class HelloController {


    @RequestMapping("/hello")
    @ResponseBody
    public String hello() {
        return "HEllow";
    }

}

```

程序入口

![1596682229526](04-SpringBoot-%E7%A8%8B%E5%BA%8F.assets/1596682229526.png)

```java
package com.kuang.springboot01helloworld;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Springboot01HelloworldApplication {

    public static void main(String[] args) {

        SpringApplication.run(Springboot01HelloworldApplication.class, args);

    }

}

```



配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.kuang</groupId>
    <artifactId>springboot-01-helloworld</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>springboot-01-helloworld</name>
    <description>victor first project</description>

    <properties>
        <java.version>1.8</java.version>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <spring-boot.version>2.3.0.RELEASE</spring-boot.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
            <exclusions>
                <exclusion>
                    <groupId>org.junit.vintage</groupId>
                    <artifactId>junit-vintage-engine</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
    </dependencies>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>${spring-boot.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                    <encoding>UTF-8</encoding>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>

```

