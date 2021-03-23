# 



# 导入静态资源

![1596697868493](14-SpringBoot-%E9%9D%99%E6%80%81%E8%B5%84%E6%BA%90%E5%AF%BC%E5%85%A5%E6%8E%A2%E7%A9%B6.assets/1596697868493.png)

### 什么是webjars

![1596697936504](14-SpringBoot-%E9%9D%99%E6%80%81%E8%B5%84%E6%BA%90%E5%AF%BC%E5%85%A5%E6%8E%A2%E7%A9%B6.assets/1596697936504.png)

他可以以maven的方式引入JQuery

```xml
        <!--maven的jquery-->
        <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>jquery</artifactId>
            <version>3.4.1</version>
        </dependency>
```

这样就能通过jar包的形式引入jquery了

![1596698230203](14-SpringBoot-%E9%9D%99%E6%80%81%E8%B5%84%E6%BA%90%E5%AF%BC%E5%85%A5%E6%8E%A2%E7%A9%B6.assets/1596698230203.png)

webjars就相当于下面的多级目录

![1596698288713](14-SpringBoot-%E9%9D%99%E6%80%81%E8%B5%84%E6%BA%90%E5%AF%BC%E5%85%A5%E6%8E%A2%E7%A9%B6.assets/1596698288713.png)

---

![1596698503346](14-SpringBoot-%E9%9D%99%E6%80%81%E8%B5%84%E6%BA%90%E5%AF%BC%E5%85%A5%E6%8E%A2%E7%A9%B6.assets/1596698503346.png)



这3个目录中,resources>static>public 优先级排名

---

总结: 

1. 在SpringBoot中,我们可以使用以下方式处理静态资源
   - webjars `localhost:8080/webjars/`
   - public,static,/** ,resources `localhost:8080/
2. 优先级: resources>static(默认)>public





