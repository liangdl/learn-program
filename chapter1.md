# First Chapter

我自己使用的方案是用自己的vps，好处是我可以在任何地方调试，不是只限于家里面。坏处是vim的门槛确实有点高。

常见的坑
* 最好还是在ubuntu上面做，不然会碰到不少不知名的坑
* ubuntu装nodejs的时候不少教程都没有说明还需要分别安装npm和nodejs-legacy不然运行，特别是nodejs-legacy没有装的情况下安装gitbook会显示找不到目录什么的
* vim下中文乱码。我是在vps上面弄的，不知道是不是vps的默认的系统不是通常下载安装的版本，竟然看不到中文，后来google了下就好了
* * 修改~/.vimrc
* * 添加下面三行
'''
set fileencodings=utf-8,gb2312,gbk,gb18030
set termencoding=utf-8 
set encoding=prc
'''
测试一下哈哈
