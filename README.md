# mvn-repo
## 个人 mvn 仓库

### 自定义archetype

##### spring-boot-archetype

构建自己的 maven spring-boot-archetype 

* src
* target

src包含原工程,target 使用 mvn archetype:create-from-project

#### 修改

在 **archetype/pom.xml** 添加

```xml
 <plugins>
      <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-resources-plugin</artifactId>
          <configuration>
            <includeEmptyDirs>true</includeEmptyDirs>
          </configuration>
      </plugin>
    </plugins>
```

在 **classes/META-INF/maven/archetype-metadata.xml** 中修改

```xml
  <fileSet filtered="true" packaged="true" encoding="UTF-8">
      <directory>src/main/java</directory>
      <includes>
        <include>**/**</include>
        <include>**/*.java</include>
      </includes>
    </fileSet>
```

> 使之包含空文件夹



### 自定义 jar包

