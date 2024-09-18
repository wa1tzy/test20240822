# github你要添加的图片路径

```
![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/your_imgae.jpg)
```

# 完整流程

```
git init
git remote add origin https://github.com/wa1tzy/test20240822
git push origin master
git add Readyou.md
git commit -m "second commit" Readyou.md
git push origin master
```



```
初始化
git init
#配置签名

#项目级别/仓库级别
git config user.name XXX
git config user.email XXX@XXX.com

##系统用户级别
git config --global user.name XXX
git config --global user.email XXX@XXX.com
cat ~/.gitconfig

```

```
git status
git add XXX
git commit -m"your message" [file name]
git push origin master
#删除
git rm XXX
git log
git reflog

git reset --hard[局部索引值]
```

```
git remote -v
git remote add origin your_repositories_url
git push origin master
git pull repositories_url
```

```
# 设置代理
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

![image](https://github.com/wa1tzy/test20240822/blob/master/imgs/image-20240822145801609.png)

![image-20240822170609892](https://github.com/wa1tzy/test20240822/blob/master/imgs/未命名1724317562.png)

```
https://blog.csdn.net/m0_58700933/article/details/131246343
```

```
https://blog.csdn.net/qq_41709370/article/details/106282229
```

```
如果你在github官网修改了内容，本地也修改了内容，需要先git pull origin master，再git push origin master
```

