# gitbook实现目标
   教学过程中主要需要接触到的gitbook需要用的东西有
   * 本地gitbook github建立
   * github
   * gitbook
   需要实现在本地编辑后push后就可以gitbook和github同步更新，主要还是在本地编辑然后推出去，以免版本混乱
    。这里自己试了好久才发现组里面有教程，只是太不容易发现了，[git_double_push](https://github.com/OpenM    indClub/OMOOC.py/wiki/gitbook_double_push)
   dsiqus也是个巨坑，在官网注册后需要
  1. 在本地安装disqus安装个插件啥的，（想起细节再补上）
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