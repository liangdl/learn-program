# gitbook折腾笔记
   如果不是需要在本地实现gitbook服务的话（如输出epub\mobi\pdf格式）本地编辑过程中完全不需要安装gitbook和nodejs以及插件，只需要在仓库下的.git/config里添加gitbook的仓库地址即可实现在本地编辑同时推送至gitbook和github。如果有冲突的话估计是远程仓库里面的版本和本地版本相冲突。
   由于我之前在gitbook上面写了一部分了，为了减少出问题的可能性，先把gitbook里面的数据倒过去github,让两边的内容一样。
1. 在书籍的详细页面点右下角的settings->Github->Export to GitHub里面很简单的，看着向导即可，记得第三步选public
2. 在本地clone github上的repo。

  ``````
  git clone [your github repo address]
  ``````
3. 编辑.git/config 添加gitbook远程仓库地址
在config里面的[remote "origin"]添加gitbook的仓库
``````
[remote "origin"]
    url = https://github.com/username/yourrepo.git
    # 照着上面那行添加gitbook仓库
    url = https://git.gitbook.com/username/youtrepo.git
    fetch = +refs/heads/*:refs/remotes/origin/*
``````

或者在命令行执行

``````
git remote set-url --add origin https://git.gitbook.com/username/yourrepo.git
``````

这样以后每次push的时候就可以同时推送到github和gitbook
4. 添加disqus插件
  1. dsiqus也是个巨坑，先在官网注册
  2. 在disqus页面右上角的齿轮处点选Add Disqus To Site
  3. 设置好site name shortname后跳转至{yourshortname}.disqus.com
  4. 在{yourshortname}.disqus.com页面进入edit settings->Advanced->Trusted Domains里面添加gitbooks.io和github.com
  5. 在gitbook目录下建立book.json里面填

```
  {
      "plugins": ["disqus"],
      "pluginsConfig": {
          "disqus": {
          "shortName": "liangdl"
          }
      }
  }
```
  6. Done！编辑完推送即可！
### 无需每次push都输入帐号密码
后每次push都要输入github和gitbook帐号密码，照着下面步骤设置就不用设置帐号密码了。github提供https和ssh方式访问仓库，我们需要把访问仓库方式改为ssh方式。
* 修改.git/config里面的url
``````
    url = https://github.com/username/yourrepo.git
    url = https://git.gitbook.com/username/youtrepo.git
    #改为
    url = git@github.com:username/yourrepo.git
    url = https://username:apitoken@git.gitbook.com/username/yourrepo.git
``````
然后想上传的时候出现

```
 Warning: Permanently added the RSA host key for IP address '192.30.252.130' to the list of known hosts.
 ```
 查了下原来是要把我vps的公钥传到github上面，接下来就是在vps生成一对key，把pub传到github上面。

 1. 在vps终端输入```ssh-keygen -t rsa```出现下面内容

 ```
 ➜  .ssh  ssh-keygen -t rsa
 Generating public/private rsa key pair.
 Enter file in which to save the key (/root/.ssh/id_rsa):这里是问私钥保存在哪里。
 Enter passphrase (empty for no passphrase):密语不输入也行
 Enter same passphrase again:同上
 Your identification has been saved in /root/.ssh/id_rsa.
 Your public key has been saved in /root/.ssh/id_rsa.pub.
 The key fingerprint is:
 XXXXXX
 ```
  2. 输入.ssh目录下执行```cat  id_rsa.pub```查看公钥，并复制下来
  3. 在[https://github.com/settings/ssh](http://https://github.com/settings/ssh)里面添加刚刚复制下来的公钥
  4. ok 再push一次试试。
