# xfg-frame-archetype - DDD 脚手架

## 1. 脚手架安装使用

### 1. 生成

```shell
md5 ddd-scaffold-lite-1.0.pom > ddd-scaffold-lite-1.0.pom.md5
shasum ddd-scaffold-lite-1.0.pom > ddd-scaffold-lite-1.0.pom.sha1
```

```shell
mvn clean install
```

```shell
mvn clean install net.ju-n.maven.plugins:checksum-maven-plugin:1.2:artifacts
```

```shell
mvn deploy
```

```shell
jar -cvf bundle.jar scaffold-lite-1.0.pom scaffold-lite-1.0.pom.asc scaffold-lite-1.0.jar scaffold-lite-1.0.jar.asc scaffold-lite-1.0-javadoc.jar scaffold-lite-1.0-javadoc.jar.asc scaffold-lite-1.0-sources.jar scaffold-lite-1.0-sources.jar.asc
```

```shell[archetype-catalog.xml](..%2F..%2F..%2F..%2Fapache-maven-3.8.6%2Frepository%2Farchetype-catalog.xml)
mvn archetype:crawl
```

```shell
mvn deploy:deploy-file \
    -DgroupId=cn.bugstack \
    -DartifactId=ascaffold-lite \
    -Dversion=6.0 \
    -Dpackaging=xml \
    -Dfile=/Users/fuzhengwei1/Documents/develop/github/xfg-studio/xfg-frame-archetype-lite/docs/archetype-catalog.xml \
    -Durl=https://packages.aliyun.com/maven/repository/2452122-release-dbuebF \
    -DrepositoryId=2452122-release-dbuebF
```

```shell
mvn org.apache.maven.plugins:maven-archetype-plugin:2.4:generate
-DarchetypeGroupId=cn.bugstack
-DarchetypeArtifactId=scaffold-lite
-DarchetypeCatalog=https://packages.aliyun.com/maven/repository/2452122-release-dbuebF/
-DarchetypeVersion=6.0
-DgroupId=com.xfg.testdemo
-DartifactId=testdemo
-Dversion=0.0.1-SNAPSHOT    
```

- 在 IntelliJ IDEA 执行 `mvn clean install` 这样会把脚手架安装到本地仓库中

### 2. 配置

```shell
/Users/fuzhengwei/Documents/develop/apache-maven-3.8.6/repository
```

- 把你的 Maven 路径的 repository 配置到 IntelliJ IDEA 创建 Maven 工程的路径下。

## 2. 工程结构介绍

```java
.
├── README.md
├── docs
│   └── dev-ops
│       ├── app
│       │   └── docker-compose-1.0.yml
│       └── mysql
│           ├── docker-compose.yml
│           └── sql
│               └── xfg-frame-archetype.sql
├── pom.xml
├── xfg-ddd-app
│   ├── Dockerfile
│   ├── build.sh
│   ├── pom.xml
│   ├── src
│   │   ├── main
│   │   │   ├── java
│   │   │   │   └── cn
│   │   │   │       └── bugstack
│   │   │   │           ├── Application.java
│   │   │   │           ├── config
│   │   │   │           │   ├── GuavaConfig.java
│   │   │   │           │   ├── ThreadPoolConfig.java
│   │   │   │           │   ├── ThreadPoolConfigProperties.java
│   │   │   │           │   └── package-info.java
│   │   │   │           └── package-info.java
│   │   │   └── resources
│   │   │       ├── application-dev.yml
│   │   │       ├── application-prod.yml
│   │   │       ├── application-test.yml
│   │   │       ├── application.yml
│   │   │       ├── logback-spring.xml
│   │   │       └── mybatis
│   │   │           ├── config
│   │   │           │   └── mybatis-config.xml
│   │   │           └── mapper
│   │   │               └── frame_case_mapper.xml
│   │   └── test
│   │       └── java
│   │           └── cn
│   │               └── bugstack
│   │                   └── test
│   │                       └── ApiTest.java
│   ├── start.sh
│   └── stop.sh
├── xfg-ddd-domain
│   ├── pom.xml
│   └── src
│       └── main
│           └── java
│               └── cn
│                   └── bugstack
│                       └── domain
│                           ├── xxx
│                           │   ├── adapter
│                           │   │   └── package-info.java
│                           │   ├── model
│                           │   │   ├── aggregate
│                           │   │   │   └── package-info.java
│                           │   │   ├── entity
│                           │   │   │   └── package-info.java
│                           │   │   └── valobj
│                           │   │       └── package-info.java
│                           │   ├── repository
│                           │   │   └── package-info.java
│                           │   └── service
│                           │       └── package-info.java
│                           └── yyy
│                               ├── model
│                               │   ├── aggregate
│                               │   │   └── package-info.java
│                               │   ├── entity
│                               │   │   └── package-info.java
│                               │   └── valobj
│                               │       └── package-info.java
│                               ├── repository
│                               │   └── package-info.java
│                               └── service
│                                   └── package-info.java
├── xfg-ddd-infrastructure
│   ├── pom.xml
│   └── src
│       └── main
│           └── java
│               └── cn
│                   └── bugstack
│                       └── infrastructure
│                           ├── gateway
│                           │   ├── adapter
│                           │   │   └── package-info.java
│                           │   ├── api
│                           │   │   └── package-info.java
│                           │   └── dto
│                           │       └── package-info.java
│                           └── persistent
│                               ├── dao
│                               │   └── package-info.java
│                               ├── po
│                               │   └── package-info.java
│                               └── repository
│                                   └── package-info.java
├── xfg-ddd-trigger
│   ├── pom.xml
│   └── src
│       └── main
│           └── java
│               └── cn
│                   └── bugstack
│                       └── trigger
│                           ├── http
│                           │   └── package-info.java
│                           ├── job
│                           │   └── package-info.java
│                           └── listener
│                               └── package-info.java
└── xfg-ddd-types
```


