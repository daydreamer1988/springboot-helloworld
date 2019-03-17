# 使用Spring Initializer
![New Project ](https://upload-images.jianshu.io/upload_images/6214815-2d8586439881acf0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![选择构建类型](https://upload-images.jianshu.io/upload_images/6214815-21d7102aabfa374e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![选择需要的依赖](https://upload-images.jianshu.io/upload_images/6214815-0ced1baf30132e6a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![解析下载依赖](https://upload-images.jianshu.io/upload_images/6214815-039f0fe5920bea24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![初始目录结构](https://upload-images.jianshu.io/upload_images/6214815-ae5e83a751c48451.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### pom.xml
```java
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.3.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.minicup</groupId>
    <artifactId>springboot-helloworld</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>springboot-helloworld</name>
    <description>Demo project for Spring Boot</description>

    <properties>
        <java.version>1.8</java.version>
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
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                // 支持命令行中输入mvn spring-boot:run启动应用
                // 支持Maven打包
            </plugin>
        </plugins>
    </build>

</project>

```


### Application
```java

@SpringBootApplication
public class SpringbootHelloworldApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringbootHelloworldApplication.class, args);
    }
}
```

#### 以上就是所有的配置,运行main函数
![image.png](https://upload-images.jianshu.io/upload_images/6214815-c01b1ecfc3c8fac5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 打开浏览器http://localhost:8080

![image.png](https://upload-images.jianshu.io/upload_images/6214815-def67ebc2b100a6e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 服务是启动了, 但是还没有接口,接下来创建HelloController.java


```java
@RestController
public class HelloController {

    @GetMapping("/hello/{name}")
    public String hollo(@PathVariable String name){
        return "Hello "+ name;
    }
}

```
#### 重新运行

![image.png](https://upload-images.jianshu.io/upload_images/6214815-d567e74eff25d646.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 除了运行main函数之外, 还可以通过命令行执行`mvn spring-boot:run`来启动

![image.png](https://upload-images.jianshu.io/upload_images/6214815-7538f5f4cc8733ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 项目打包部署

![image.png](https://upload-images.jianshu.io/upload_images/6214815-ce90c44f6bbaa46f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/6214815-d27e23d02f3a91d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在命令行中输入`java -jar target/springboot-helloworld-0.0.1-SNAPSHOT.jar`
![image.png](https://upload-images.jianshu.io/upload_images/6214815-368cdb4e47415601.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


###### 注意, pom文件中的依赖没有版本号, 这是因为parent的`spring-boot-starter-parent`中已经定义了
