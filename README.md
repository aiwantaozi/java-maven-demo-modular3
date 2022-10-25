# Example Maven multi-module project by include dependencyManagement

## 方式：

在子模块中指定父模块的相对路径

### 父模块 pom.xml

```xml
  <groupId>seal.io</groupId>
  <artifactId>example-root</artifactId>
  <version>2.0-SNAPSHOT</version>
  <name>example-root</name>
  <!-- pom 打包方式代表父工程 -->
  <packaging>pom</packaging>

  <!-- 父pom中把依赖通过dependencyManagement引入，表示子pom可能会用到的依赖 -->
  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>sevlet-api</artifactId>
        <version>2.5</version>
      </dependency>
    </dependencies>
  </dependencyManagement>
```

### 子模块 pom.xml

Module 2:

```xml
   <!-- 继承父pom文件 -->
  <parent>
    <groupId>seal.io</groupId>
    <artifactId>example-root</artifactId>
    <version>2.0-SNAPSHOT</version>
    <relativePath>../pom.xml</relativePath>
  </parent>

  <!-- 子模块pom，groupID和version使用父模块的 -->
  <artifactId>module1</artifactId>
  <name>module2</name>

  <!--子pom可以直接引用该包，不需要再加入version，便于统一管理-->
  <dependencies>
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>servlet-api</artifactId>
    </dependency>
  </dependencies>
```
