### 发布snapshot
```
<version>3.1.3-SNAPSHOT</version>
```
如果版本以`-SNAPSHOT`会发布到仓库`xjh-snapshot`；
否则发布到仓库`xjh-release`

### 发布正式版准备工作
```bash
mvn release:prepare 

a.把你项目打一个release版本
b.在git的tag中打一个tag
c.自动升级SNAPSHOT 并提交更新后的pom文件到git
```

### 发布正式版
```bash
mvn release:perform
```

```
a.去git的tag上拿代码
b.用tag上的代码，打一个release版的包
c.deploy上你的maven私服
```