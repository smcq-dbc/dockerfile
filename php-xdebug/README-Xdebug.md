# 配置介绍

​	整体配置过程参考 https://www.sqlsec.com/2020/09/xdebug.html#toc-heading-8 ，先测试php7.4，毕竟是Ubuntu20.04默认的，安装ssh和php，把xdebug的配置写入 /etc/php/7.4/cli/php.ini     /etc/php/7.4/apache2/php.ini

​	php8.1-xdebug参考 https://xdebug.org/docs/upgrade_guide#changed-xdebug.auto_trace    http://www.feimoc.com/2021/03/21/PhpStorm+Xdebug3/#xdebug%E9%85%8D%E7%BD%AE

  **此配置适用于xdebug2**

```ini
[XDebug]
; 如果大家要配置这个的话，可以模仿一下下面的规则，去对应的版本目录下找到对应的 xdebug.so 文件即可
;zend_extension=/usr/lib/php/20190902/xdebug.so 其他版本目录不同，使用相对路径
zend_extension=xdebug.so

; 开启远程调试功能
xdebug.remote_enable=1

; 远程调试地址
xdebug.remote_host=localhost

; 远程调试端口
xdebug.remote_port=9000

; 每次执行脚本都会启动 xdebug 调试
xdebug.remote_autostart = 1

; 每次请求都会生成一个性能报告文件
xdebug.profiler_enable = 1

; 在 IDE 上等待确认传入调试连接以的时间(毫秒)
xdebug.remote_timeout=2000

; debug 调试的日志位置
xdebug.remote_log = /tmp/xdebug.log
```

  **此配置适用于xdebug3** 

```ini
[XDebug]
zend_extension = xdebug.so
xdebug.log  = /tmp/xdebug.log
xdebug.mode = develop,debug
xdebug.start_with_request = yes
#xdebug.start_with_request = yes #当改为yes时所有请求都会走debug，不需要设置idekey
xdebug.client_port = 9003
xdebug.client_host = 127.0.0.1
xdebug.remote_handler = dbgp
xdebug.cli_color = 2
xdebug.var_display_max_depth = 15
xdebug.var_display_max_data  = 2048
```

**添加MySQL8  root/smcq123** 



# 需要自己做的： 

1，手动在docker容器建一个php项目，或者创建容器时目录映射。

2，按国光师傅上面写的文章连接到docker容器，root/root  （需要vscode扩展）

3，在项目目录下 php  -S   0.0.0.0:80   (我这里写的暴露22和80端口) 

​	  目前也支持将项目添加到 /var/www/html 目录（修改后配置文件同步添加到了/etc/php/x.x/apache2/php.ini目录下）

4，在容器内安装扩展<img src="https://raw.githubusercontent.com/smcq-dbc/upload_picture/main/image-20220609121215702.png" alt="image-20220609121215702" style="zoom:80%;" /> 

5，创建launch.json文件，我是把国光师傅的直接复制过来的，在我这可以，端口号得和php.ini配置文件对应

好像只要第一块就行了（

**本项目中除了php8.1下面这个皆可**

```json
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for Xdebug",
            "type": "php",
            "request": "launch",
            "port": 9000
        }
    ]
}
```

**本项目php8.1(不知道为啥改配置文件后还是监听9003端口。。。**

```
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for Xdebug",
            "type": "php",
            "request": "launch",
            "port": 9003
        }
    ]
}
```

6，至少目前单个文件看起来是成功了（：<img src="https://raw.githubusercontent.com/smcq-dbc/upload_picture/main/image-20220609121714266.png" alt="image-20220609121714266" style="zoom:80%;" /> 

用国赛的thinkphp测试也能拦截到

![image-20220609125352243](https://raw.githubusercontent.com/smcq-dbc/upload_picture/main/image-20220609125352243.png) 



# 注意：有些扩展需要自己按需求安装！！！

------------------------

# 排错记录

1，在搭php7.0的时候，会报错无法加载xdebug

```
Failed loading /usr/lib/php/20210902/xdebug.so:  /usr/lib/php/20210902/xdebug.so: undefined symbol: zend_pass_function
```

dockerfile的安装命令是 apt-get install php-xdebug，改成apt-get install php7.0-xdebug成功。

也是因为这个命令导致的顺带安装了php8（大概，没仔细追究）



刚开始以为几个RUN就有几层镜像。。结果全写在一个里面了，导致排错有点麻烦，不过问题不大，手动改下就行了

2，php5.6、7.0、7.4都能正常调试了，但8.1一直不行。。。让Mr_King表哥帮忙看了看，初步判断可能是php8.1-xdebug的问题。

确实。。。php8.1-xdebug是xdebug3，前几个是2版本，3改动了一些参数，所以配置文件得改改才行（：



3，搜到一个备忘录，自己前几个用的都是xdebug2,第三条内容未测试，不过看起来挺靠谱的（：

![image-20220610083142001](https://raw.githubusercontent.com/smcq-dbc/upload_picture/main/image-20220610083142001.png)



# 待完善

1，php8.1修改配置文件 xdebug.client_port = 9000 后重载还是监听9003默认端口。。。不知道为啥

2，配置文件有些参数还没搞懂，后面可能需要根据实际情况修改，还可以考虑在根目录建一个指定项目目录，把.vscode的launch.json也放进去，就又少一步。累了，以后再说吧（：