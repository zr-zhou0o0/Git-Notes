# Git-Notes
Common git command and error notes


# 常见命令

+ **用户名和邮箱**

```
git config --global user.name “your name”
git config --global user.email “your email”
ssh-keygen -t rsa -C “your email”
```

+ **分支管理**
```
git branch -m master main //将本地分支（master）改名为main
git branch --set-upstream-to=origin/main //将本地的当前分支与远程的main分支连接
git checkout master //切换分支
git checkout -b test //创建新的分支
git branch -vv //检查跟踪分支
```

+ **push**
```
git add .
git add -u
git commit -m "test first"//这里引号里写一些讯息，比如版本更新之类的
git push origin main //push到远程仓库的main分支
git push --set-upstream origin master
git push --force origin test
```

+ **pull**
```
git clone git仓库地址# ?
git pull origin main
```

+ **clone**
```
git clone <ssh>
```


+ **设置url或者ssh**
```
git remote -v //查看当前仓库地址
git remote add origin “仓库SSH地址”//或者url
git remote set-url origin git@gitee.com:someaccount/someproject.git
```

+ **版本**
```
git status
```

+ **其他**
```
git help
```

# 常见报错


+ **permission denied**
//publickey的问题
//403：修改url：http://username:password@gitee.com/name/projectname.git  

+ **git connection timed out**
```
//vpn设置全局代理,tun模式
//或者
git config --global http.proxy http://127.0.0.1:1080
git config --global https.proxy http://127.0.0.1:1080
注：127.0.0.1是主机号：是使用的代理的主机号(自己电脑有vpn那么本机可看做访问github的代理主机)，即填入127.0.0.1即可，否则填入代理主机 ip(就是网上找的那个ip)
1080是端口号：为代理软件(代理软件不显示端口的话，就去Windows中的代理服务器设置中查看)或代理主机的监听IP，可以从代理服务器配置中获得，否则填入网上找的那个端口port 。从clash里面可以看到我的是7890.
//或
git config --global --unset http.proxy
git config --global --unset https.proxy
//或者从ssh换成url
//或者端口22和433切换
//或者改hosts
```

+ **reject**  

+ **git denied to deploy key**
  注意项目里的ssh和个人主页里的ssh不能共用

+ **working tree clean**
//重新改动一下，再add


+ **not a repository**
```
git init
```

+ **src refspec**
//本地分支和远程分支不匹配
//需要建立并切换分支


+ **error setting certificate**
git 本地的ssl密钥不匹配或找不到
找到.gitconfig文件
找到此文件后，使用文本编辑器打开就可以。然后添加如下几行：如果有[http]的话直接添加下面两行。如果没有，就把[http]这个也带上。
```
[http]
sslVerify = false
sslCAinfo = /bin/curl-ca-bundle.crt
```

+ **gnutls_handshake() failed**
  多试几次，可能是网不好


评价：用git进行版本控制不如用邮箱进行版本控制(x
