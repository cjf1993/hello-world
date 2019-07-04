#java环境安装(win10)#

目录放c盘之外，建立JAVA

     JAVA里分别建立JDK和JRE两目录

环境变量配置： 
              
              在用户变量里---》新建 JAVA_HOME 变量 ---》变量值填写jdk绝对路径(D:\Java\JDK)
              
              在系统变量里---》找出 Path  变量 ---》增加 %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
              
              在用户变量里---》新建 PATH 变量 ---》变量值填写jdk/bin绝对路径(%JAVA_HOME%\bin;)
              
              在用户变量里---》新建 CLASSPATH 变量 ---》变量值填写.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
              
              
验证是否安装成功: cmd---> java  &cmd--->javac             



#maven安装和配置(win10)#


     目录放c盘之外，建立MAVEN

将下载好的maven安装包解压到MAVEN
配置环境变量： 
              
              在用户变量里---》新建 MAVEN_HOME 变量 ---》变量值填写maven绝对路径(D:\maven)

              在系统变量里---》找出 Path  变量 ---》变量值填写maven/bin的绝对路径(D:\maven\bin) 
              

 c盘下找不到maven默认仓库目录【.m2】文件夹?
 
 解决办法：
 
    cmd--->输入【mvn -v】命令确保maven已成功安装
    cmd--->输入【mvn help:system】命令来让maven进行一次任务，在执行过程中就会在c盘生成【.m2】的目录
    新生成的目录中没有【settings.xml】文件，所以在执行上步命令可能会出现编译失败，可以从maven安装目录的config目录中拷贝到【.m2】的目录中
    再次在DOS窗口中输入第3步命令 则可以将maven初始化需要的插件都安装好

 
 
