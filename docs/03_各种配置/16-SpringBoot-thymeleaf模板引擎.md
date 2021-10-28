![1596701201161](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701201161.png)

模板引擎我们以前是JSP

![1596699798741](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596699798741.png)

### 先导入thymeleaf

![1596699904496](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596699904496.png)

```xml
        <!--thymeleaf-->
        <dependency>
            <groupId>org.thymeleaf</groupId>
            <artifactId>thymeleaf-spring5</artifactId>
        </dependency>
        <dependency>
            <groupId>org.thymeleaf.extras</groupId>
            <artifactId>thymeleaf-extras-java8time</artifactId>
        </dependency>
```

然后

在页面中创建一个html文件

![1596701046411](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701046411.png)

编辑test.html

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
<h2>用于测试此事</h2>
</body>
</html>
```



在Controller中配置

```java
package com.kuang.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

/**
 * @author victor
 * @site https://victorfengming.github.io/
 * @company XDL
 * @project springboot-03-web
 * @package com.kuang.controller
 * @created 2020-08-06 15:29
 * @function ""
 */
// 在Templates目录下的所有页面这能通过Controller来跳转!
// 这个需要模板引擎的支持 thymeleaf

@Controller
public class IndexController {
    @RequestMapping("/test")
    public String test() {
        return "test";
    }
}

```



在返回的"test",然后thymeleaf会有一定的规则进行匹配

![1596701261232](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701261232.png)

然后就找到页面了

![1596701331619](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701331619.png)

重新启动

![1596701350513](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701350513.png)

在看页面

![1596701372469](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701372469.png)

就成了

---

### 模板引擎

结论: 只需要使用thymeleaf,只需要导入对应的依赖就可以了!

我们将html页面放在我们的Template目录下即可

![1596701466727](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701466727.png)

语法

判断

显示

取值

### 首先想要使用,需要导入一个约束

![1596701524414](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596701524414.png)

我们来传递一个数据试试

> 早期没人教的时候,都是看源码学习的

1在Controller里面这样写

```java
package com.kuang.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;

/**
 * @author victor
 * @site https://victorfengming.github.io/
 * @company XDL
 * @project springboot-03-web
 * @package com.kuang.controller
 * @created 2020-08-06 15:29
 * @function ""
 */
// 在Templates目录下的所有页面这能通过Controller来跳转!
// 这个需要模板引擎的支持 thymeleaf

@Controller
public class IndexController {
    @RequestMapping("/test")
    public String test(Model model) {
        model.addAttribute("msg", "hello,springboot");
        return "test";
    }
}

```

2在test.html中

```html
<!doctype html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
<!--所有的html元素都可以被thymeleaf替换接管-->
<!--           th:元素名               -->
<h1 th:text="${msg}"></h1>
</body>
</html>
```

3在页面中康康

![1596702099464](16-SpringBoot-thymeleaf%E6%A8%A1%E6%9D%BF%E5%BC%95%E6%93%8E.assets/1596702099464.png)