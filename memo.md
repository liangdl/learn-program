#MEMO
有空的时候再从这里整理去正文

###出现语言设置错误
    perl: warning: Setting locale failed.
    perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_MESSAGES = "zh_CN.UTF-8",
        LANG = "zh_CN.UTF-8"
        are supported and installed on your system.
    perl: warning: Falling back to the standard locale ("C").

##解决办法是
###安装 localepurge 管理语言文件
    sudo apt-get install localepurge

当然也可以使用以下命令再次进行配置：
    sudo dpkg-reconfigure localepurge
生成自己想要的语言
    sudo locale-gen zh_CN.UTF-8 en_US.UTF-8
搞定了，然后进入vim发现空格变成倒问好的问题还在。。。百思不得骑姐。  
尝试改 /etc/default/locale 尝试在里面加入一行 LC_ALL="zh_CN.UTF-8" 重启后完美解决了，连系统里面的提示符也正常了


启用powerline
在~/.vimrc.before.local 里面添加



2.3 如果使用Javascript, 不需要的跳过
#### 安装jshint和jslint,用于javascript语法检查
#### 需要nodejs支持,各个系统安装见文档 https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager

###ubuntu
sudo npm install -g jslint
sudo npm install jshint -g

###install k-vim
git clone https://github.com/wklken/k-vim.git
cd k-vim/
sh -x install.sh

##shadowsocks

    wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
    chmod +x shadowsocks.sh
    ./shadowsocks.sh 2>&1 | tee shadowsocks.log

##install Oh My Zsh
                sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
