### 模块说明
#### 1. maven-bom-parent/pom.xml
```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.ml</groupId>
            <artifactId>maven-dependencies-bom</artifactId>
            <version>1.0-SNAPSHOT</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```
#### 2. maven-dependencies-bom 统一定义了 项目 依赖的三方库的版本号
```xml
<properties>
    <spring_version>4.3.16.RELEASE</spring_version>
    <fastjson_version>1.2.46</fastjson_version>
</properties>
```
```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-framework-bom</artifactId>
            <version>${spring_version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>${fastjson_version}</version>
        </dependency>
    </dependencies>
</dependencyManagement>
```

#### 3. project-bom  统一定义了项目的各个模块的版本号
```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.ml</groupId>
            <artifactId>project-common</artifactId>
            <version>${project.version}</version>
        </dependency>
        <dependency>
            <groupId>com.ml</groupId>
            <artifactId>project-service</artifactId>
            <version>${project.version}</version>
        </dependency>
    </dependencies>
</dependencyManagement>
```

#### 4. project-common 项目的具体模块
```xml
<parent>
    <artifactId>maven-bom-parent</artifactId>
    <groupId>com.ml</groupId>
    <version>1.0-SNAPSHOT</version>
</parent>
```
```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.ml</groupId>
            <artifactId>project-bom</artifactId>
            <version>${project.parent.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

