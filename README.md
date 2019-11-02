# 利用腾讯云cos搭建的静态博客，顺便用下SCF更新

## 前置条件
1. 申请腾讯云账号，开通一个免费cos [对象存储 COS_云存储服务_安全存储服务 - 腾讯云](https://cloud.tencent.com/product/cos)
2. 新建一个存储桶
3. 安装配置好SCF CLI [教程](https://cloud.tencent.com/document/product/583/37510)

## 用法
1. fork仓库，然后```npm i```
2. 根目录新建cos_config.json，内容参照cos_config_sample.js 信息能在[访问密钥 - 控制台](https://console.cloud.tencent.com/cam/capi)找到
3. ```cd blog && npm install && hexo new "new post title"```
4. 找到```blog/public/source/_posts```下的post，用MD语法写post
5. 跑 ```npm run remotePublish```
6. 首次部署后，到[SCF控制台](https://console.cloud.tencent.com/scf/)，找到publishCosBlog函数，找到“触发方式”-“API网关触发器”，把访问路径复制到/blog/_config.yml 下的url字段处
7. 再跑```npm run remotePublish```
8. 以后每次修改后再重复remotePublish就ok了
