## 自动化构建

Jenkins 是一款开源 CI&CD 软件，用于自动化各种任务，包括构建、测试和部署软件

- Jenkins 支持各种运行方式，可通过系统包、Docker 或者通过一个独立的 Java 程序

### 安装依赖

> 安装参考：[Windows环境下安装Jenkins](https://blog.csdn.net/weixin_43184774/article/details/104428244)

- **注意：**解锁 Jenkins 的密码所在地址每台电脑会有所区别，复制自己的即可

```bash
# 前台启动命令
$ java -jar jenkins.war --httpPort=8084

# 后台启动命令
$ nohup java -jar jenkins.war --httpPort=8084 &
# 查看 java 的 pid
$ ps -ef | grep java
# 关闭 java 进程
$ kill -9 xxx(pid)
```

![image-20230525102631276](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230525102631276.png)

**安装包官网下载链接**

- [Jenkins.war](https://www.jenkins.io/download/)

![image-20230525094343594](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230525094343594.png)

如果使用官网最新的 Jenkins.war 包，需要安装 Java11 以上

> 升级参考：[Java 8（JDK 1.8）升级更新至 Java 17（JDK 17）](https://blog.csdn.net/beita08/article/details/122128069)

- [Java17 安装包](https://www.oracle.com/java/technologies/downloads/#jdk17-windows)

![image-20230525094421475](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230525094421475.png)

### 本地使用 Jenkins

1. 点击 **新建Item**，开始创建项目

   ![image-20230524141426137](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230524141426137.png)

2. 输入一个任务名称，如：`jenkins-test-project`。选择 **Freestyle project**，点击 **确定**

   ![image-20230524141640031](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230524141640031.png)

3. 点击 **General**。添加描述：`这是我的第一个 jenkins 项目，用来测试`

   ![image-20230524150322503](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230524150322503.png)

4. 点击 **源码管理**，点击 **Git**，在 Repository URL 中输入

   `http://192.168.1.242:9000/lilin/test-jenkins.git`

   一般还得添加 `Credentials`，这里就不演示了

   ![image-20230524151659589](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230524151659589.png)

5. 点击 **构建环境**。这里无需勾选任何东西，如果为了展示更加优化，可以勾选 `Add timestamps to the Console Output` 和 `Color ANSI Console Output`

   注意：需要安装两个插件 [Timestamper](https://plugins.jenkins.io/timestamper) 和 [AnsiColor](https://plugins.jenkins.io/ansicolor)

   ![image-20230525105556265](https://gitee.com/lilyn/pic/raw/master/lagoulearn-img/image-20230525105556265.png)

6. 点击 **构建**，点击 **增加构建步骤**。选择 `Execute shell`，填入如下内容。之后点击保存即可

   ```bash
   node -v
   
   # 内网环境下需要修改
   npm install --registry https://registry.npm.taobao.org/
   npm run build
   
   DIR_PATH=`pwd`/dist
   # 需要修改
   FILE_NAME=jenkins-test-project
   # 需要修改
   TO_PATH=D:/Develop/nginx-1.20.2/project
   cd $TO_PATH
   rm -rf $FILE_NAME
   mkdir  $FILE_NAME
   cp -r $DIR_PATH/* $TO_PATH/$FILE_NAME
   ```

### Jenkins插件

> [Jenkins：插件安装及使用教程](https://blog.csdn.net/qq_42428264/article/details/120614219)
>
> [Jenkins常用插件汇总以及简单介绍](https://www.cnblogs.com/iancloud/p/16045093.html)
>
> [Jenkins针对不同的项目视图对不同的用户进行权限分配](https://blog.csdn.net/chj_1224365967/article/details/117924420)
>
> [新版Jenkins 2.346.1自动化部署（SVN+Maven）](https://www.cnblogs.com/leyfung/p/16881843.html)
>
> [Jenkins构建(8):Jenkins 执行远程shell :Send files or execute commands over SSH](https://blog.csdn.net/fen_fen/article/details/114649877)
>
> [jenkins：一个jenkins项目远程触发另一个jenkins项目构建配置](https://www.cnblogs.com/wolfshining/p/7685725.html)
>
> [前端工程化：保姆级教学 Jenkins 部署前端项目](https://juejin.cn/post/7102360505313918983)
>
> [Jenkins Blue Ocean 环境搭建和Pipeline基本使用（基于docker-compose）](https://blog.csdn.net/asd0654123/article/details/108993781)
>
> [Jenkins持续集成部署实战采坑系列(三)](https://blog.csdn.net/madeByOurselves/article/details/100130915)
>
> [Generic Webhook Trigger 实现特定提交触发自动构建](https://blog.csdn.net/qq_33248407/article/details/123430187)
>
> [Jenkins常用插件汇总以及简单介绍](https://wiki.eryajf.net/pages/2280.html)