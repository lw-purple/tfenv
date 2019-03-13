
python 虚拟环境

virtualenv 是创建独立Python开发环境的工具，用于解决同一台机器上不同的Python工程的依赖、版本以及间接权限等问题。比如项目foo1依赖Django1.3，而项目foo2依赖Django1.7，而当前全局开发环境为Django1.8，版本的不同会导致项目所需包的版本不兼容等问题，使项目无法正常运行，使用virtualenv来创建相对独立的虚拟环境，可以很好的解决此类问题。此外，值得一提的是，对于项目打包迁移，如部署Web应用项目等应用场景，virtualenv都很有用武之地。

virtualenv创建一个拥有自己安装目录的环境, 这个环境不与其他虚拟环境共享库, 能够方便的管理python版本和管理python库。

下面介绍一下与使用Virtualenv相关的技巧。

 

1.安装Virtualenv
$ pip install virtualenv
//或者由于权限问题使用sudo临时提升权限
$ sudo pip install virtualenv
2.virtualenv创建虚拟环境
1 virtualenv ENV    
2 #创建一个名为ENV的目录，并安装了ENV/bin/python
3 #创建了lib,include,bin目录，安装了pip
lib目录 : 所有安装的python库都会放在这个目录中的lib/pythonX.X/site-packages/中 ;

bin目录 : bin/python是当前虚拟环境使用的python解析器 ;

如果在命令行中运行virtualenv --system-site-packages ENV, 会继承/usr/lib/python3.6/site-packages下的所有库, 最新版本virtualenv把把访问全局site-packages作为默认行为
default behavior.

3.激活virtualenv
1 #ENV目录下使用如下命令
2 source ./bin/activate  #激活当前virtualenv
3 #当用户名前面出现小括号括起来的虚拟环境名时，表明虚拟环境被成功激活
使用“pip list”指令可查看当前库

4.关闭virtualenv
deactivate
5.指定python版本
可使用-p PYTHON_EXE选项在创建虚拟环境的时候指定Python版本

1 #创建python2.7虚拟环境
2 virtualenv -p /usr/bin/python2.7 ENV2.7
3 
4 #创建python3.4虚拟环境
5 virtualenv -p /usr/local/bin/python3.4 ENV3.4
这样可以解决不同项目python版本冲突以及和python库版本不兼容等问题。

6.生成可打包环境
某些特殊需求下，可能没有网络，我们希望直接打包一个ENV，解压后直接使用，这时候可以使用virtualenv --relocatable指令将ENV修改为可更改位置的ENV

#对当前已经创建的虚拟环境更改为可迁移
virtualenv --relocatable ./
7.获得帮助
virtualenv -h
8.官方文档
http://virtualenv.readthedocs.org/en/latest/virtualenv.html




 virtualenvwrapper-win 安装 和使用
介绍 ： virtualenvwrapper-win 是Windows下对于虚拟环境的管理工具，用它可以简化virtualenv的操作
安装：
pip install virtualenvwrapper-win
进入和退出虚拟环境：
首先，设置virtualenvwrapper-win 的默认环境目录 ： 在win10中，添加系统环境变量 WORKON,指向 path/dir  (自己想要的虚拟环境目录位置)
复制代码
# 1.  显示当前path/dir 目录下的虚拟环境
workon

#显示如下（我的目录下）
C:\Users\GoFree>workon

Pass a name to activate one of the following virtualenvs:
==============================================================================
env_python2.7
env_python3.6
PycharmProjects

C:\Users\GoFree>

## 其中，存在 env_python2.7，env_python3.6， PycharmProjects 三个独立虚拟环境

# 2.  激活env_python3.6 环境
workon PycharmProjects # 直接workon 即可

#激活状态显示如下：
C:\Users\GoFree>workon env_python3.6
(env_python3.6) C:\Users\GoFree>


# 3.  冻结env_python3.6 环境
deactivate env_python3.6 # 使用deactivate命令

#冻结显示如下
(env_python3.6) C:\Users\GoFree>deactivate env_python3.6
C:\Users\GoFree>
复制代码
 

新建和删除虚拟环境：
复制代码
# 新建虚拟环境,指定python3环境
mkvirtualenv -p python3 venv 



# 删除虚拟环境
rmvitualenv venv
复制代码
 

冻结和重建虚拟环境：
冻结：所谓 冻结(freeze) 环境，就是将当前环境的软件包等固定下来:
pip freeze >packages.txt　　# 安装包列表保存到文件packages.txt中　
 重建：重建(rebuild) 环境就是在部署的时候，在生产环境安装好对应版本的软件包，不要出现版本兼容等问题:
pip install -r packages.txt
 作用：配合pip，可以批量安装对应版本的软件包，快速重建环境，完成部署。通俗讲，把当前环境的包复制粘贴到另一个新环境中，把当前环境拷贝到新环境中。