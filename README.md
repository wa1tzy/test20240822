**清华源**

```
-i https://pypi.tuna.tsinghua.edu.cn/simple
```

**百度源**

```
-i https://mirror.baidu.com/pypi/simple
```

**禁止conda自动激活base环境**

```
conda config --set auto_activate_base false
```

**拉流地址长期能用**

```
http://172.20.10.2:9002/v1/service/videoTask
```

**windows 计算 md5 值**

```
certutil -hashfile
```

```
# -*- coding:utf-8 -*-
```

**vmware**

```
https://blog.csdn.net/weixin_44842318/article/details/129836960
```

```
密钥：MC60H-DWHD5-H80U9-6V85M-8280D
```

```
下载链接：https://www.vmware.com/content/vmware/vmware-published-sites/us/products/workstation-pro/workstation-pro-evaluation.html.html
```

```
apt-get clean

```



## 1、更新

```
apt-get update
apt upgrade
源装不上：apt install ca-certificates  update-ca-certificates
https://blog.csdn.net/q965844841qq/article/details/121482942
```

```
pip install --upgrade XXXX
```



## 2、装vim

```
apt-get install vim -y
```

## 3、改源

```
vim /etc/apt/sources.list
```

```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```

```
apt-get update
```

## 4、卸载包

```
sudo apt purge package_name
```

## 5、Anaconda安装

```
chmod a+x Anaconda3-2020.07-Linux-x86_64.sh

./Anaconda3-2020.07-Linux-x86_64.sh

#yum install mesa-libGL.x86_64 -y

#进入conda环境 
source ~/.bashrc 
#退出conda环境
source deactivate

#查看conda的配置
conda config --show

#为Conda添加国内镜像源conda config --add channels
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge 
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --set show_channel_urls yes
#编辑
~/.condarc

#创建环境
conda create -n env_name python=3.7
#激活环境
conda activate env_name
#退出环境
source deactivate

#安装cuda、pytorch、torchvision、cudnn
conda install cudatoolkit=10.1 -y
conda install cudnn -y
conda install pytorch=1.6.0 -y
conda install torchvision=0.7.0 -y

pip install -i http://mirrors.aliyun.com/pypi/simple/ Cython matplotlib>=3.2.2 PyYAML>=5.3 scipy>=1.4.1 tensorboard>=2.2 tqdm>=4.41.0 flask opencv-python --trusted-host mirrors.aliyun.com
```

## 6、nginx

```
apt-get install nginx
nginx -v
cd /etc/nginx
service nginx start
service nginx stop
```

## 7、查看cuda和cudnn版本

apt-get install wget

```
查看cuda的版本：
cat /usr/local/cuda/version.txt
查看cudnn 版本：
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
```

## 8、装pip

```
apt install python3-pip
```

功能模块

## 9、安装python

https://blog.csdn.net/zhongjianboy/article/details/123448421

Ubuntu安装Python3
（第0步）建议配置阿里镜像https://developer.aliyun.com/mirror/ubuntu

一、安装相关依赖

```
apt-get update && apt-get upgrade
apt-get install -y build-essential checkinstall libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev
apt-get dist-upgrade
apt-get install -y build-essential python-dev python-setuptools python-pip python-smbus
apt-get install -y build-essential libncursesw5-dev libgdbm-dev libc6-dev zlib1g-dev libsqlite3-dev tk-dev libssl-dev openssl libffi-dev wget
```

二、源码安装

```
下载链接
wget https://www.python.org/ftp/python/3.9.8/Python-3.9.8.tgz
解压
tar zxvf Python-3.9.8.tgz -C /usr/local
cd /usr/local/Python-3.9.8
配置
./configure prefix=/usr/local/python3 --enable-optimizations
编译
make && make install 
```

三、配置系统环境

```
删除之前的python3
whereis python
#(有风险)* rm -rf 所有python3的版本（除去/usr/local/python3） 
删除之前软连接
rm -rf /usr/bin/python
rm -rf /usr/bin/pip
添加新的链接
cp /usr/local/python3/lib/libpython3.9.a /usr/lib
echo "/usr/lib" > /etc/ld.so.conf.d/python3.9.conf
ldconfig
ln -s /usr/local/python3/bin/python3 /usr/bin/python
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip
添加环境变量
vi /etc/profile
添加 export PATH=$PATH:/usr/local/python3/bin
source /etc/profile
```

四、测试

```
python -V
pip -V
pip list
python -m pip install --upgrade pip
```

## 10、装jdk

```
（1）创建jdk文件夹并导入jdk
（2）解压jdk包
① tar -xvf jdk-8u251-linux-x64.tar.gz
② 修改/etc/profile 
vi /etc/profile
添加如下：
export JAVA_HOME=/root/jdk/jdk1.8.0_251
export PATH=$PATH:$JAVA_HOME/bin
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
：wq 保存退出
③ source /etc/profile  刷新配置文件
④ java -version 查看是否安装成功
```

## 11、装torch、torchvision、torchaudio

```
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu113 -i https://pypi.tuna.tsinghua.edu.cn/s
imple
```

![image-20220330223820009](C:\Users\wa1tzy\AppData\Roaming\Typora\typora-user-images\image-20220330223820009.png)

## 12、装wget

```
apt-get install wget
```

## 13、安装的小问题

### 13.1

```
安装torch==1.9.0和torchvision==0.10.0时会报错 ModuleNotFoundError: No module named '_lzma'
```

解决

```
1、apt-get install liblzma-dev
2、pip install backports.lzma
3、把 /usr/local/lib/python3.6/lzma.py修改如下
```

```
#修改前
from _lzma import *
from _lzma import _encode_filter_properties, _decode_filter_properties

#修改后 
try:
    from _lzma import *
    from _lzma import _encode_filter_properties, _decode_filter_properties
except ImportError:
    from backports.lzma import *
    from backports.lzma import _encode_filter_properties, _decode_filter_properties
```

### 13.2

```
AttributeError: ‘Upsample‘ object has no attribute ‘recompute_scale_factor‘问题解决
```

在/usr/local/python3/lib/python3.9/site-packages/torch/nn/modules/upsampling.py修改如下:

```
def forward(self, input: Tensor) -> Tensor:
        # return F.interpolate(input, self.size, self.scale_factor, self.mode, self.align_corners,
        #                      recompute_scale_factor=self.recompute_scale_factor)
        return F.interpolate(input, self.size, self.scale_factor, self.mode, self.align_corners)
```

## 14、装ffmpeg

源码装

```
wget https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/ffmpeg/7:4.4-6ubuntu5/ffmpeg_4.4.orig.tar.xz
tar -xvf ffmpeg_4.4.orig.tar.xz
cd  ffmpeg-4.4
apt-get install gcc make yasm   # 可能需要装的
./configure
make -j4
make install
```

## 15、Vim小技术

```
:map <F10> :set paste<CR> :map <F11> :set nopaste<CR> 
```



```
设置粘贴模式
:set paste
设置不粘贴模式
:set nopaste
查找关键字
// 按n 
```

## 16、装django

```
pip install django 
python -m django --version
#apt-get update
apt install python-django-common
apt install python-django
django-admin startproject mydjangoapp

```

使用：

```css
apt install python3-venv
mkdir my_django_app
cd my_django_app
python3 -m venv venv
source venv/bin/activate
pip install django
python -m django --version
django-admin startproject mydjangoapp

默认情况下，Django使用SQLite数据库。 对于生产应用程序，您可以使用PostgreSQL，MariaDB，Oracle或MySQL数据库。

运行以下命令以迁移数据库：
python manage.py migrate
迁移数据库后，创建一个管理用户，以便您可以使用Django管理界面：
python manage.py createsuperuser
该命令将提示您输入管理用户的用户名，电子邮件地址和密码。
Username (leave blank to use 'linuxize'): admin
Email address: admin@linuxize.com    
Password: 
Password (again): 
Superuser created successfully.
使用manage.py脚本后跟runserver选项启动开发Web服务器：
python manage.py runserver
在Web浏览器中打开http://127.0.0.1:8000，您将看到默认的Django登录页面。
您可以通过在URL的末尾添加/ admin /来访问Django管理界面（http://127.0.0.1:8000/admin/）。 这将带您进入管理员登录界面.
```



## 17、装git

```
#apt-get update
apt install git
加速下载
git clone https://github.com.cnpmjs.org

git clone https://github.com/xxx/xxx.git改成
git clone https://hub.fastgit.org/xxx/xxx.git

```

### 加速下载

```

sudo vim /etc/hosts
添加
ping github.global.ssl.fastly.net
ping github.com
sudo /etc/init.d/networking restart
```

### 安装ping

```
apt-get install inetutils-ping
```



## 18、环境

更新环境变量1

```
source /etc/profile
```

更新环境变量2

```
gedit ~/.bashrc
export PATH=<你的要加入的路径>:$PATH
添加PYTHONPATH的方法也是这样，在.bashrc中添加

export PYTHONPATH=/home/zhao/setup/caffe-master/python:/home/zhao/setup/mypy:$PYTHONPATH 

source ~/.bashrc
```

加中文

```
env LANG=C.UTF-8
env LC_ALL=C.UTF-8
env LANGUAGE=C.UTF-8
```

解决Docker容器中文显示乱码问题

```
输入locale指令查看容器使用的语言集：locale
vi /etc/bash.bashrc
export LC_ALL="C.UTF-8"
source /etc/bash.bashrc
```



## 19、windows用法

```
type = cat
dir = ls
```

```
taskkill -f /pid 67872 #停止pid进程
```

## 20、vim 常用的

### 1、多行删除

```
在ESC模式下，输入以下内容并回车
:7,19d
就是将第7行至第19行的内容删除
```

### 2、粘贴不窜行

```
:set paste
```

### 3、多行编辑

```
光标放在第8行行首
按住Ctrl+v 进入visual block 模式
然后用小键盘的↓移动光标至第27行的行首
然后再按I（大写字母i）,这时光标会回到第8行的行首并进入编辑模式
在第8行的行首插入#号后按ESC退出
然后第9-27行的行首就自动也加了#号
```

### 4、块操作

```
跟上面的ctrl+v一样

linux在编辑大型文本信息时，常采用块操作ctrl+v
插入：大写I
替换：小写c
删除：小写x
剪切并粘贴
按“ctrl+v”，选中文字，按"d",剪切列，移动光标位置，按“p”粘贴
```

### 5、批量编辑命令

```
dd:删除游标所在的一整行(常用)
ndd:n为数字。删除光标所在的向下n行，例如20dd则是删除光标所在的向下20行
d1G:删除光标所在到第一行的所有数据
dG:删除光标所在到最后一行的所有数据
d$:删除光标所在处，到该行的最后一个字符
d0:那个是数字0,删除光标所在到该行的最前面的一个字符
x,X:x向后删除一个字符(相当于[del]按键),X向前删除一个字符(相当于[backspace]即退格键)
nx:n为数字，连续向后删除n个字符
```

### 6、vim跳转到指定行

```
在vim中有3中方法可以跳转到指定行（首先按esc进入命令行模式）：

1、ngg/nG （跳转到文件第n行，无需回车）
2、:n （跳转到文件第n行，需要回车）
3、vim +n filename （在打开文件后，跳转到文件的第n行）
```

## 7、用vim打开后中文乱码怎么办

```
https://www.cnblogs.com/gaogaoxingxing/p/15465284.html
```



## 21、编译pyc

### 1、Python生成单个pyc文件

#### 1.1 命令行

#### 对于py文件，可以执行下面命令来生成pyc文件

```
python -m foo.py
```

#### 1.2 代码

```
import py_compile
py_compile.compile('/path/to/foo.py')
```

### 2、Python批量生成pyc文件

#### 1.1 命令行

```
python -m compileall <dir>
```

#### 1.2 代码

```
import compileall
compileall.compile_dir(r'/path')
```

## 22、libreoffice文档转换

### 1、安装、使用、中文包

```
apt install libreoffice

soffice --headless --invisible --convert-to pdf example.doc

apt install ttf-wqy-zenhei
apt install fonts-wqy-microhei
```

### 2、介绍

```
官网： https://www.libreoffice.org/
```

```
Windows下安装Libreoffice

双击下载下来的 Libreoffice 程序，全部使用默认安装的方式进行安装，直接点击“下一步”安装完成。
将Libreoffice 加入到 Windows系统环境 Path 变量。
默认Windows的安装路径是:
C:\Program Files\LibreOffice
加入到系统环境变量中的 Path 变量值：
C:\Program Files\LibreOffice\program
```

```
Linux下安装Libreoffice
可以直接在官网进行下载，或者使用如下命令进行安装。

💕💕💕Ubuntu安装命令
[sudo] apt install libreoffice

cnetos安装命令
yum install -y libreoffice

Mac下安装Libreoffice

Mac 下，可直接从官网下载 Mac 下的软件包进行一键安装。或者用 brew 命令一键安装：
[sudo] brew install libreoffice

💕💕💕检测是否安装成功
在终端执行如下命令，查看版本号，能查到版本号，即表示安装成功。
soffice --version

如果查看不到版本号或者提示命令不存在，请检查 Libreoffice 是否已经安装并且配置了 Libreoffice 的系统环境变量。
如果是Linux或者Mac系统下使用命令一键安装的方式的话，在安装的过程中就已经自动添加进去了。
```

```
测试文档转换
测试以Ubuntu为例 Libreoffice 在进行文档转换的过程中，转换出来的文档可能会出现乱码，所以需要在正式使用之前，把可能存在的乱码问题进行测试和解决。

💕💕💕创建一个中英文内容的.doc 文档，用如下命令将文档转成 PDF:
```

```
soffice --headless --invisible --convert-to pdf example.doc
```

```
转换成功之后，会在当前目录下生成一个 example.pdf 的文件，然后打开转换后的PDF文件，查看文件中的中文是否存在乱码等。如果存在乱码，则朝以下两个方向去解决。
字符编码是否支持，比如 gbk 或者 utf-8 等

是否缺少相应的中文字体库。如 ubuntu 下，可以使用如下的方式进行安装：
```

```
apt install ttf-wqy-zenhei
apt install fonts-wqy-microhei
```

## 23、镜像换中国时区

dockerfile里加

```
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo ‘Asia/Shanghai’ >/etc/timezone
```

![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/image-20220809095857366.png)

## 24、python-ffmpeg镜像里报错

```
FileNotFoundError: [Errno 2] No such file or directory: 'ffprobe'
```

![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/image-20220809181149446.png)

解决：

```
apt-get update
apt-get install ffmpeg
```

## 25、curl返回中文

```
app.config['JSON_AS_ASCII'] = False
app.run(host='0.0.0.0',debug=False)
```

## 26、python使用pyzbar时报错如下

```
File "/usr/local/lib/python3.5/dist-packages/pyzbar/zbar_library.py", line 65, in load
    raise ImportError('Unable to find zbar shared library')
ImportError: Unable to find zbar shared library
```

```
sudo apt-get install libzbar-dev
pip install zbar
```

![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/image-20220829153901825.png)

# 27、pip装离线包

![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/image-20230721101557723.png)



## 1、离线下载

当一个离线[python环境](https://so.csdn.net/so/search?q=python环境&spm=1001.2101.3001.7020)缺少少数个包的时候，可以用以下方法进行安装：

```
pip download 包名 -d 要保存的路径
比如，下载jieba的离线包放到当前路径下：
pip download jieba -d  ./
```

如果下载太慢可以加上[清华镜像源](https://so.csdn.net/so/search?q=清华镜像源&spm=1001.2101.3001.7020)，利用下边的方法，可以加速下载：

```
pip download 包名 -d 要保存的路径 -i https://pypi.tuna.tsinghua.edu.cn/simple
```

## 2、离线安装

对于下载的包，可能有很多依赖文件，他们之间有强依赖关系，即必须先安装某一个，再安装另一个，这样会比较麻烦，需要一个一个的安装，因此利用以下方法，可以一键安装：

```
pip install  要安装的包的离线文件  --no-index --find-links=依赖文件的路径
```

![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/image-20230721101859254.png)

我们只需要利用以下命令就可以一键安装：

```
pip install fastapi-0.95.1-py3-none-any.whl  --no-index  --find-links=./
```

# 28、解决 Command "python setup.py egg_info" failed ...问题的参考 :

```
pip install --upgrade setuptools
python -m pip install --upgrade pip
```

# 29、Building wheel for opencv-python (pyproject.toml)卡住，解决方案（已解决）

①更新pip版本：pip install --upgrade pip ，之后再次尝试
②由于一般要下载30min左右，有时会误认为是卡死，此时需要用--verbose 进行安装命令跟踪安装过程，可以在每一行最前端显示安装百分比：

```
pip install opencv-python -i https://pypi.tuna.tsinghua.edu.cn/simple --verbose 
```

之后耐心等待即可

 ③使用pip装是源码编译安装的，所说的Building wheel for opencv-python就是在编译，编译非常慢，想快一点的话就用apt来装python版本cv，那个是预编译过的。

# 30、缩减镜像大小

```
RUN pip install --no-cache-dir -r requirements.txt
```

