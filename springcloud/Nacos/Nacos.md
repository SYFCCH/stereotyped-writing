

* 在主 pom 中定义基础组件版本，使用dependencyManagement引入版本依赖。
```xml
<properties>
	<java.version>1.8</java.version>
	<spring-boot.version>2.1.9.RELEASE</spring-boot.version>
	<springcloud-alibaba.version>0.9.0.RELEASE</springcloud-alibaba.version>
	<mybatis-plus.version>3.1.1</mybatis-plus.version>
	<mysql.version>5.1.47</mysql.version>
	<encoding>UTF-8</encoding>
	<maven.compiler.source>1.8</maven.compiler.source>
	<maven.compiler.target>1.8</maven.compiler.target>
</properties>

<dependencyManagement>
    <dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-dependencies</artifactId>
			<version>${spring-boot.version}</version>
			<type>pom</type>
			<scope>import</scope>
		</dependency>
		<!--database-->
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>${mysql.version}</version>
		</dependency>
		<dependency>
			<groupId>com.baomidou</groupId>
			<artifactId>mybatis-plus-boot-starter</artifactId>
			<version>${mybatis-plus.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-alibaba-dependencies</artifactId>
			<version>${springcloud-alibaba.version}</version>
			<type>pom</type>
			<scope>import</scope>
		</dependency>
	</dependencies>
</dependencyManagement>
```

在 Service 模块中引入具体依赖    

```xml
<dependencies>
	<!--Spring Boot-->
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
		<exclusions>
			<exclusion>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-starter-logging</artifactId>
			</exclusion>
		</exclusions>
	</dependency>

	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-log4j2</artifactId>
	</dependency>

	<!--Spring Cloud Alibaba-->
	<dependency>
		<groupId>org.springframework.cloud</groupId>
		<artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
	</dependency>

	<!--database-->
	<dependency>
		<groupId>mysql</groupId>
		<artifactId>mysql-connector-java</artifactId>
	</dependency>

	<dependency>
		<groupId>com.baomidou</groupId>
		<artifactId>mybatis-plus-boot-starter</artifactId>
	</dependency>

	<dependency>
		<groupId>org.projectlombok</groupId>
		<artifactId>lombok</artifactId>
		<optional>true</optional>
	</dependency>

</dependencies>
```


# 集成Nacos注册中心   


* 引入spring-cloud-starter-alibaba-nacos-discovery，上一步骤已完成；
* 修改配置文件application.yml，配置 nacos 的服务地址（注意修改服务端口）；  
```xml
server:
  port:8010
spring:
  application:
    name:account-service
  cloud:
    nacos:
      discovery:
        server-addr:10.0.10.48:8848/
```

* 在项目启动类上添加@EnableDiscoveryClient注解
```java
@SpringBootApplication
@RestController
@EnableDiscoveryClient
publicclass AccountServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(AccountServiceApplication.class, args);
    }
}
```   

启动完成后访问 nacos 服务端地址http://10.0.10.48:8848/nacos可以发现服务正常注册    


