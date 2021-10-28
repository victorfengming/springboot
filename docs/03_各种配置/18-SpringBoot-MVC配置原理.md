![1596704069184](18-SpringBoot-MVC%E9%85%8D%E7%BD%AE%E5%8E%9F%E7%90%86.assets/1596704069184.png)



创建一个

![1596704629922](18-SpringBoot-MVC%E9%85%8D%E7%BD%AE%E5%8E%9F%E7%90%86.assets/1596704629922.png)

```java
package com.kuang.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.View;
import org.springframework.web.servlet.ViewResolver;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

import java.util.Locale;


// 扩展springmvc DispatcherServlet
@Configuration

public class MyMvcConfig implements WebMvcConfigurer {

    // public interface ViewResolver 实现了视图解析器的类,我们就可以把它看做视图解析器
    @Bean
    public ViewResolver myViewResolver() {
        return new MyViewResolver();
    }


    // 自定义了一个自己的视图解析器MyViewResolver
    // 我们自己写了一个解析器,并且装配到bean上面
    public static class MyViewResolver implements ViewResolver {
        @Override
        public View resolveViewName(String viewName, Locale locale) throws Exception {
            return null;
        }
    }

}
```

