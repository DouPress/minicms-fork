# MiniCMS

## 项目介绍

MiniCMS是一个针对个人网站设计的微型内容管理系统。

主要特点：

1. 不需要数据库支持，只需要一个可以运行 PHP 的 Web 环境
2. 只针对个人网站设计，没有复杂的成员管理和权限设置
3. 没有分类只有标签，免除发布文章时到底该怎么分类的纠结
4. 只有“文章”和“页面”两个系统，没有“评论”、“插件”，让你更专注于创造内容
5. 其他功能：网站基本信息、状态、主题、URL 类型、ICP 备案号、账号和密码等可在后台配置

## 安装

1. 下载最新版的 install.php，上传到网站根目录
2. 浏览器访问根目录下 instal.php，填入网站信息和初始账号密码
3. 开始安装

## 文件结构

```
index.php          入口文件
admin              后台管理
core               核心
theme              主题
data               内容数据
  |--config.php    配置文件
  |--posts         文章
  |    |--data     数据
  |    |--index    索引
  |--pages         页面
       |--data     数据
       |--index    索引
.htaccess          Apache rewrite 配置文件
nginx.conf         Nginx rewrite 配置
```

## URL 格式

默认 query 模式

文章: `http://example.com/?post/[a-z0-9]{6}`

标签: `http://example.com/?tag/[^/]+`

日期: `http://example.com/?date/([0-9]{4}-[0-9]{2}`

页面: `http://example.com/?([-a-zA-Z0-9]+)+`

可选 history 模式，需要服务器支持开启路径重写

文章: `http://example.com/post/[a-z0-9]{6}`

标签: `http://example.com/tag/[^/]+`

日期: `http://example.com/date/([0-9]{4}-[0-9]{2}`

页面: `http://example.com/([-a-zA-Z0-9]+)+`

## 模板标签

```
app_site_name()  // 网站标题
app_site_desc()  // 网站描述
app_nick_name()  // 站长昵称

app_theme_url() // 主题文件夹中文件的URL

app_next_post()    // 循环获取文章
app_post_title()   // 文章标题
app_post_link()    // 文章标题A链接
app_post_content() // 文章内容
app_post_url()     // 文章URL
app_post_date()    // 文章发布日期
app_post_time()    // 文章发布时间
app_post_tags()    // 文章标签

app_comment_code()// 文章评论代码
app_footer_code() // 网页底部代码
```

## 打包发布

打包安装包文件 install.php 的构建命令

```shell
# 使用 php 命令执行
php build.php [指定版本号]
# 示例
php build.php 1.2.5
```
