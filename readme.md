### 发布snapshot
```bash
mvn deploy
```
注意事项：1.nexus上的仓库，属性version policy:Snapshot 2.deployment policy: Allow redeploy

### 发布正式版准备工作
```bash
mvn release:prepare 
```
```
a.把你项目打一个release版本
b.在git的tag中打一个tag
c.自动升级SNAPSHOT 并提交更新后的pom文件到git
```

### 错误回滚
```bash
mvn release:rollback
```
将POM回退至release: prepare之前的状态，并提交。需要注意的是，该步骤不会删除release:prepare生成的标签，因此用户需要手动删除。

### 发布正式版
```bash
mvn release:perform
```
```
a.去git的tag上拿代码
b.用tag上的代码，打一个release版的包
c.deploy上你的maven私服
```

https://www.cnblogs.com/jixp/p/10670786.html

scm参数说明：
- connection表示一个只读的scm地址，
- developerConnection元素表示可写的scm地址，
- url则表示可以在浏览器中访问的scm地址。
> 为了能让Maven识别，connection和developerConnection必须以scm开头，冒号之后的部分表示版本控制工具的类型
```xml
<scm>
    <url>https://github.com/xujiuhua/nexus-deploy</url>
    <connection>scm:git:git@github.com:xujiuhua/nexus-deploy.git</connection>
    <developerConnection>scm:git:git@github.com:xujiuhua/nexus-deploy.git</developerConnection>
    <tag>HEAD</tag>
</scm>
```