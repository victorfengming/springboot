其实springboot项目主流是前后端分离的，因此之前mvc项目里的model模型到这里就变成了POJO目录。

POJO（Plain Ordinary Java Object）简单的Java对象，实际就是普通JavaBeans，是为了避免和EJB混淆所创造的简称。
使用POJO名称是为了避免和EJB混淆起来, 而且简称比较直接. 其中有一些属性及其getter setter方法的类,没有业务逻辑，有时可以作为VO(value -object)或dto(Data Transform Object)来使用.当然,如果你有一个简单的运算属性也是可以的,但不允许有业务方法,也不能携带有connection之类的方法。

##### POJO与javabean的区别

POJO 和JavaBean是我们常见的两个关键字，一般容易混淆，POJO全称是Plain Ordinary Java Object / Pure Old Java Object，中文可以翻译成：普通Java类，具有一部分getter/setter方法的那种类就可以称作POJO，但是JavaBean则比 POJO复杂很多， Java Bean 是可复用的组件，对 Java Bean 并没有严格的规范，理论上讲，任何一个 Java 类都可以是一个 Bean 。但通常情况下，由于 Java Bean 是被容器所创建（如 Tomcat) 的，所以 Java Bean 应具有一个无参的构造器，另外，通常 Java Bean 还要实现 Serializable 接口用于实现 Bean 的持久性。 Java Bean 是不能被跨进程访问的。JavaBean是一种组件技术，就好像你做了一个扳子，而这个扳子会在很多地方被拿去用，这个扳子也提供多种功能(你可以拿这个扳子扳、锤、撬等等)，而这个扳子就是一个组件。一般在web应用程序中建立一个数据库的映射对象时，我们只能称它为POJO。POJO(Plain Old Java Object)这个名字用来强调它是一个普通java对象，而不是一个特殊的对象，其主要用来指代那些没有遵从特定的Java对象模型、约定或框架（如EJB）的Java对象。理想地讲，一个POJO是一个不受任何限制的Java对象（除了Java语言规范）

---

开始操作

1. 先引入静态资源

   ![1596715597113](20-SpringBoot-%E5%91%98%E5%B7%A5%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F-%E9%A6%96%E9%A1%B5%E5%AE%9E%E7%8E%B0.assets/1596715597113.png)

   然后创建pojo类和config类

   ![1596715629774](20-SpringBoot-%E5%91%98%E5%B7%A5%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F-%E9%A6%96%E9%A1%B5%E5%AE%9E%E7%8E%B0.assets/1596715629774.png)

department.java

```java
package com.kuang.pojo;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

/**
 * @author victor
 * @site https://victorfengming.github.io/
 * @company XDL
 * @project springboot-demo-01
 * @package com.kuang.pojo
 * @created 2020-08-06 19:59
 * @function ""
 */
// 部门表
@Data
@AllArgsConstructor
@NoArgsConstructor
public class Department {
    private Integer id;
    private String departmentName;
}

```

employee.java

```java
package com.kuang.pojo;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.util.Date;

/**
 * @author victor
 * @site https://victorfengming.github.io/
 * @company XDL
 * @project springboot-demo-01
 * @package com.kuang.pojo
 * @created 2020-08-06 20:03
 * @function ""
 * pojo -==- * Plain Ordinary Java Object
 */
// 员工表

@Data
@AllArgsConstructor
@NoArgsConstructor
public class Employee {
    private Integer id;
    private String lastName;
    private String email;
    private Integer gender; // 0 nv  1男
    private Department department;
    private Date birth;
}

```

MyMvcConfig.java

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

pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.3.2.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.kuang</groupId>
    <artifactId>springboot-demo-01</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>springboot-demo-01</name>
    <description>Demo project for Spring Boot</description>

    <properties>
        <java.version>1.8</java.version>
    </properties>

    <dependencies>
        <!--thymeleaf-->
        <dependency>
            <groupId>org.thymeleaf</groupId>
            <artifactId>thymeleaf-spring5</artifactId>
        </dependency>
        <dependency>
            <groupId>org.thymeleaf.extras</groupId>
            <artifactId>thymeleaf-extras-java8time</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
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

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>

```

再创建一个dao包



![1596719577858](20-SpringBoot-%E5%91%98%E5%B7%A5%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F-%E9%A6%96%E9%A1%B5%E5%AE%9E%E7%8E%B0.assets/1596719577858.png)

department.dao文件

```java
package com.kuang.dao;

import com.kuang.pojo.Department;
import org.springframework.context.annotation.Bean;
import org.springframework.stereotype.Repository;

import java.util.Collection;
import java.util.HashMap;
import java.util.Map;

// 部门表
   @Repository
public class DepartmentDao {

    //    模拟数据库中的数据
    private static Map<Integer, Department> departments = null;
    static {
        // 创建一个部分表
        departments = new HashMap<Integer, Department>();

        departments.put(101, new Department(101,"教学部"));
        departments.put(102, new Department(102,"市场部"));
        departments.put(103, new Department(103,"教研部"));
        departments.put(104, new Department(104,"运营部"));
        departments.put(105, new Department(105,"后勤部"));
    }

//    获得所有部门信息
    public Collection<Department> getDepartments() {
        return departments.values();
    }

    // 通过id得到部门
    public Department getDepartmentById(Integer id) {

        return departments.get(id);
    }
}

```

EmployeeDao.java文件

```java
package com.kuang.dao;

import com.kuang.pojo.Department;
import com.kuang.pojo.Employee;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Repository;

import java.util.Collection;
import java.util.HashMap;
import java.util.Map;

/**
 * @author victor
 * @site https://victorfengming.github.io/
 * @company XDL
 * @project springboot-demo-01
 * @package com.kuang.dao
 * @created 2020-08-06 20:24
 * @function ""
 */
// 员工的Dao
@Repository
public class EmployeeDao {
    // 模拟数据库中的数据
    private static Map<Integer, Employee> employees = null;
    // 员工所属的部门
    @Autowired
    private DepartmentDao departmentDao;
    static {
        // 创建一个员工表
        employees = new HashMap<Integer, Employee>();

        employees.put(1001, new Employee(1001,"AA","510510280@qq.com",1,new Department(105, "后勤部")));
        employees.put(1002, new Employee(1002,"BB","410510280@qq.com",0,new Department(102, "市场部")));
        employees.put(1003, new Employee(1003,"vi","310510280@qq.com",0,new Department(105, "后勤部")));
        employees.put(1004, new Employee(1004,"ct","610510280@qq.com",1,new Department(103, "教研部")));
        employees.put(1005, new Employee(1005,"na","910510280@qq.com",1,new Department(105, "后勤部")));
    }

    // 主键自增
    private static Integer initId = 1006;

    // 增加一个员工
    public void save(Employee employee) {
        if (employee.getId() == null) {
            employee.setId(initId++);
        }

        employee.setDepartment(departmentDao.getDepartmentById(employee.getDepartment().getId()));

        employees.put(employee.getId(), employee);
    }

//    查询全部员工信息
    public Collection<Employee> getAll() {
        return employees.values();
    }

    // 通过id 查询员工
    public Employee getEmployeeById(Integer id) {
        return employees.get(id);
    }

    // 删除员工通过ied
    public void delete(Integer id) {
        employees.remove(id);
    }


}

```

