# 安装yarn tyarn
npm  i yarn tyarn -g
# 安装umi
tyarn global add umi







# 工程项目目录执行
# 生成package.json
tyarn init -y
# 生成页面,好像用不上
umi g  page index
# 下载umi依赖
tyarn add umi --dev
# 安装插件
tyarn add umi-plugin-react --dev
# 启动
umi dev
# 构建，转码
umi builder


# 参考官网
https://umijs.org/zh-CN/docs/getting-started
# 创建项目
yarn create @umijs/umi-app
# 安装依赖
yarn
# 启动
yarn start