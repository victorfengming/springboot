



# SpringBoot使用IDEA创建项目

![1596682450024](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682450024.png)

选择springboot,选择java版本,maven项目

![1596682417089](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682417089.png)

然后

![1596682501875](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682501875.png)

然后完成了就

![1596682521594](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682521594.png)

现在就是这样了

![1596682548029](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682548029.png)

删除多余的文件

![1596682561162](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682561162.png)

现在直接启动

![1596682587488](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682587488.png)

现在运行完就结束了

怎么能不结束呢,是不是需要导入web依赖啊

![1596682643975](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682643975.png)

在启动

![1596682660852](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682660852.png)

现在tomcat就被继承进来了

我们写一个controller

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
        return "helloworld!!!哦哦哦";
    }

}

```

重新启动
在配置文件中更改项目的端口号

编辑`application.properties`文件:

```properties
spring.application.name=springboot-01-helloworld
management.endpoints.jmx.exposure.include=*
management.endpoints.web.exposure.include=*
management.endpoint.health.show-details=always
# spring cloud access&secret config
# 可以访问如下地址查看: https://usercenter.console.aliyun.com/#/manage/ak
alibaba.cloud.access-key=****
alibaba.cloud.secret-key=****
# 应用服务 WEB 访问端口
server.port=8180
# Actuator Web 访问端口
management.server.port=8081

```

我们可以自定义banner

springboot banner 在线生成

比如: www.bootschool.net/ascii-art

我们找一个图形,然后编辑`banner.txt`文件:

```javascript
                              _.-="_-         _
                         _.-="   _-          | ||"""""""---._______     __..
             ___.===""""-.______-,,,,,,,,,,,,`-''----" """""       """""  __'
      __.--""     __        ,'   spring victor    o \           __        [__|
 __-""=======.--""  ""--.=================================.--""  ""--.=======:
]       [w] : /        \ : |========================|    : /        \ :  [w] :
V___________:|          |: |========================|    :|          |:   _-"
 V__________: \        / :_|=======================/_____: \        / :__-"
 -----------'  "-____-"  `-------------------------------'  "-____-"
```

重新启动运行

![1596682911262](05-SpringBoot-IDEA%E5%88%9B%E5%BB%BA%E5%BD%A9%E8%9B%8B.assets/1596682911262.png)

就成了

