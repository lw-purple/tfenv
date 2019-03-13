pip install --upgrade tensorflow   下载tf存在就升级
 

python -C "import tensorflow as tf"

pip install jupyter   安装交互式环境

python -m ipykernel install --user --name=venv      使ipykernel 指向自己的虚拟环境

jupyter kernelspec list 查看多少kernelspec
jupyter-notebook 打开 jupyter-notebook


pip 国内镜像

http://pypi.douban.com/simple/ 豆瓣

http://mirrors.aliyun.com/pypi/simple/ 阿里

http://pypi.hustunique.com/simple/ 华中理工大学

http://pypi.sdutlinux.org/simple/ 山东理工大学

http://pypi.mirrors.ustc.edu.cn/simple/ 中国科学技术大学

https://pypi.tuna.tsinghua.edu.cn/simple 清华


由于Nodejs的我使用的是阿里的，所以这里我也是选择阿里的。


使用办法

1、临时使用，添加“-i”或“--index”参数

 

pip install -i http://pypi.douban.com/simple/ flask

2、配制成默认的

 


在你的“C:\Users\你的用户名\”目录下创建“pip”目录，
“pip”目录下创建“pip.ini”文件（注意：以UTF-8 无BOM格式编码）；

“pip.ini”文件内容：


[global]

index-url=http://mirrors.aliyun.com/pypi/simple/

[install]

trusted-host=mirrors.aliyun.com


注意：trusted-host 选项为了避免麻烦是必须的，否则使用的时候会提示不受信任，或者添加“--trusted-host=mirrors.aliyun.com”选项；

 


注意：有网页提示需要创建或修改配置文件（linux的文件在~/.pip/pip.conf，windows在%HOMEPATH%\pip\pip.ini），至少Windows7下“%HOMEPATH%\pip\pip.ini”这个目录是不起作用的。

