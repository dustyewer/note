# 查看版本
$ npm -v

# 升级或安装 cnpm
npm install cnpm -g


# win10使用powershell 运行 cnpm ，vue ，vue-cli 出错
1. 使用get-ExecutionPolicy，获取到变量值，如果是Restricted，则进行2操作，否则请另寻办法；
2. 执行：set-ExecutionPolicy RemoteSigned，如果电脑深知你意，可能就到此ok了，but...我报以下错误，请继续往下看
3. 根据提示，输入：Set-ExecutionPolicy -Scope CurrentUser
提示输入参数值，输入RemoteSigned，又给出提示，再次输入Y



cnpm install --global vue-cli

cnpm install -g @vue/cli

# 高版本的vue-cli使用2.0的模板
cnpm install -g @vue/cli-init

# CLI2.0版本的项目初始化
vue init webpack 项目名

# CLI3.0版本的项目初始化
vue create 项目名
或者
vue ui



# idea eslint错误解决办法
//vue2.0适用
this.CliEngine = require(this.basicPath + "lib/cli-engine");
// vue3.0使用
// this.CliEngine = require(this.basicPath + "lib/cli-engine").CLIEngine;

