一个学习skynet的demo，不知道能不能坚持下去，先放着看看那？emmmm
       
一、安装并启动skynet：

        开发环境：Linux  centos
        开发前准备：
        git   
        命令行：sudo apt-get install git
        autoconf
        命令行：sudo apt-get install autoconf
        readline
        sudo apt-get install libreadline-dev
        下载源码：
        sudo git clone https://github.com/cloudwu/skynet.git
        编译:
        1.切换到skynet目录下
        2.执行命名行 sudo make linux

        参考：https://www.cnblogs.com/decode1234/p/7905577.html

        注意点：
        启动skynet服务端和客户端  都需要在skynet根目录下
        启动服务端一般 ./skynet 配置表
        启动客户端一般 ./3rd/lua/lua 客户端启动文件

        项目架构：
        3rd 第三方库
        examples 样例
        luaclib 封装的so文件 so
        lualib  lua库 lua
        lualib-src lua库源文件 c
        makefile 编译文件
        service 服务库文件 lua
        skynet-src  skynet核心文件 c
        cservice 客户端动态文件 so
二、新项目搭建：

        1.新建目录，命名为项目名(demo)        
        2.进入到该目录下，新建一个项目，命名skynet
        3.把编译后的skynet根目录下的所有文件拷贝到skynet目录下
        4.在demo根目录下，新建config和service两个目录
        5.拷贝skynet/examples/下的config和config.path到demo/condig目录下
        6.拷贝skynet/examples下的main.lua到demo/service目录下
        7.打开demo/config/config.path，添加project_root，其他配置参靠见
                root = "./"
                project_root = "../"
                luaservice = root.."service/?.lua;"..root.."test/?.lua;"..root.."test/?/init.lua;"..project_root.."service/?.lua"
                lualoader = root .. "lualib/loader.lua"
                lua_path = root.."lualib/?.lua;"..root.."lualib/?/init.lua"
                lua_cpath = root .. "luaclib/?.so"
                snax = root.."test/?.lua;"..project_root.."service/?.lua"

        注意：重点是把原本的examples/?.lua替换为project_root.."service/?.lua，因为启动入口已经在demo/service/main.lua中
        8.进入skynet，运行
        ./skynet ../config/config
      
   
