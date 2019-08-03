

Homebrew

--------



安装

----

\`/usr/bin/ruby -e "$\(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/instd\`

命令

----



\`安装软件：brew install 软件名，例：brew install wget\`\

 \`搜索软件：brew search 软件名，例：brew search wget\`\

 \`卸载软件：brew uninstall 软件名，例：brew uninstall wget\`\

 \`更新所有软件：brew update\`\

 \`更新具体软件：brew upgrade 软件名 ，例：brew upgrade git\`\

 \`显示已安装软件：brew list\`\



\`查看软件信息：brew info／home 软件名 ，例：brew info git ／ brew home git\`\

 \`显示包依赖：brew reps\`\

 \`显示安装的服务：brew services list\`\

 \`安装服务启动、停止、重启：brew services start/stop/restart serverName\`



homebrew cask

-------------



安装

----



\`brew tap phinze/homebrew-cask\`\

 \`brew install brew-cask\`



\#\#\# 软件列表



可视化homebrew安装工具\

 \`brew cask install cakebrew\`



图形化管理Homebrew安装的服务软件\

 \`brew tap jimbojsb/launchrocket\`\

 \`brew cask install launchrocket\`



全局搜索工具\

 \`brew cask install alfred\`\

 //快捷键option+space\

 //command+回车打开文件所在文件夹\

 //把/usr/local/Caskroom增加到 alfred

的search目录中,偏好设置-\&gt;Features-\&gt;Default Results-\&gt;Search Scope



//百度搜索添加设置\

 1.Features-\&gt;Web Search-\&gt;Add Custom Search\

 2.Search

Url-\&gt;\[https://www.baidu.com/s?wd={query}\]\(https://www.baidu.com/s?wd=%7Bquery%7D\)\

 Title-\&gt;Search Baidu for ‘{query}’\

 Keywords-\&gt;baidu\

 Validation:alfredpp



//国人必备的30个Alfred Workflow\



\[https://www.waerfa.com/alfred-workflow\]\(https://www.waerfa.com/alfred-workflow\)\

 brew cask install google-chrome\

 //chrome://components



终端工具\

 brew cask install iterm2\

 //配色https://github.com/mbadolato/iTerm2-Color-Schemes



mac chm阅读工具\

 \`brew cask install ichm\`



shadowsocks客户端\

 \`brew cask install shadowsocksx-ng\`



redis客户端\

 \`brew cask install rdm\`\

 \`brew install macvim --with-override-system-vim\`\

 \`brew install emacs --with-cocoa --with-gnutls\`\

 \`brew install adminer\`



mac环境工具\

 brew install mysql\

 brew install httpd24\

 brew install php56 --with-httpd24\

 brew install redis\

 brew install php56-redis\

 //redis可视化管理工具 redis-desktop-manager\

 brew install php56-yaf\

 brew install php56-swoole\

 brew install mongodb\

 brew install php56-mongodb\

 brew install nginx\

 brew install memcached\

 brew install php56-memcached\

 //mongodb可视化管理工具 robomongo\

 浏览器插件



HTTP Status\

 IPvFoo\

 Proxy SwitchyOmega\

 WEB前端助手\(FeHelper\)\

 二维码生成器\

 译库网页翻译\

 购物比价助手\

 httpd22配置文件



Alias /workspace "/Users/redraiment/workspace/"



\[//升级到2.4版本之后\]\(https://xn--2-8e8al7ab38j.xn--4-bs6a77pj5wjwm/\)：Order

allow,deny和Allow from all要改成Require all granted，如下所示：



Alias /workspace "/Users/redraiment/workspace/"



\&lt;VirtualHost \\*:80\&gt;\

 DocumentRoot “/www/test”\

 ServerName localhost\

 ErrorLog “/private/var/log/apache2/localhost-error\\_log”\

 CustomLog “/private/var/log/apache2/localhost-access\\_log” common\

 \&lt;Directory “/www/test”\&gt;\

 Options FollowSymLinks Multiviews\

 MultiviewsMatch Any\

 AllowOverride None\

 Require all granted\

 \

 \

 虚拟机\

 brew cask install virtualbox\

 brew cask install vagrant



前端工具\

 brew install node



\[\]\(https://edu.csdn.net/topic/ai30?utm\_source=blogt0 "这项技术，百度/华为等大佬力捧！程序员：我彻底慌了..."\)



\#\#\#\# 这项技术，百度/华为等大佬力捧！程序员：我彻底慌了... {.text-truncate .oneline}



\[没有创造力,

996也打不过AI到底趋势如何？\]\(https://edu.csdn.net/topic/ai30?utm\_source=blogt0 "没有创造力, 996也打不过AI到底趋势如何？"\)



\[!\[\]\(./homebrew%20&%20brew%20cask使用技巧及Mac软件安装%20-%20不加班加班%20-%20CSDN博客\_files/anonymous-User-img.png\)\]\(javascript:void\(0\);\)



\[\*\*\]\(https://blog.csdn.net/woshikuangdage/article/details/82781165\#insertcode\)



\[发表评论\]\(https://blog.csdn.net/woshikuangdage/article/details/82781165\#\)



添加代码片



-   HTML/XML

-   objective-c

-   Ruby

-   PHP

-   C

-   C++

-   JavaScript

-   Python

-   Java

-   CSS

-   SQL

-   其它



