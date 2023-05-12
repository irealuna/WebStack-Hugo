# 一个基于 Hugo 的静态响应式网址导航主题 

本项目是基于**纯静态**的网址导航网站 [webstack.cc](https://github.com/WebStackPage/WebStackPage.github.io) 制作的 [Hugo](https://gohugo.io/) 主题，是一个基于 Hugo 的静态响应式网址导航主题。<br/>

## Linux 下安装部署
安装完本 WebStack-Hugo 主题后，将 exampleSite 目录下的文件复制到 hugo 站点根目录，根据需要把 config.toml 的一些信息改成自己的，导航的网址信息可通过 data 目录下 webstack.yml 修改。

具体执行步骤如下：
```shell
mkdir /home/dev/mysite 
cd /home/dev/mysite

# 安装 WebStack-Hugo 主题
git clone https://github.com/shenweiyan/WebStack-Hugo.git themes/WebStack-Hugo

# 将 exampleSite 目录下的文件复制到 hugo 站点根目录
cp -r themes/WebStack-Hugo/exampleSite/* ./

# 启动 hugo 站点
hugo server 
# 如果你知道你的公网 ip, 如下面的 132.76.230.31, 可以使用下面的方式执行 hugo server
hugo server --baseUrl=132.76.230.31 --bind=0.0.0.0 
```

## 导出 HTML 静态网页至 publishDir
Windows/Linux 下执行的 hugo server 命令将会通过热加载的方式临时启动一个 Hugo 服务器（Hugo 可以启动一个 Web 服务器，同时构建站点内容到内存中并在检测到文件更改后重新渲染，方便我们在开发环境实时预览对站点所做的更改），这个时候我们打开浏览器 http://127.0.0.1:1313/，就可以看到我们站点的样子了。

如果我们想要把我们的站点部署到 GitHub/Gitee Pages（或者本地的服务器），我们可以：

### 1. 生成静态页面内容

可以通过下面的命令，生成(构建)静态页面内容。
```shell
hugo -D 或者 hugo --minify
```
这个命令会默认在public/目录中生成您的网站，当然您可以通过改变站点配置中的publishDir选项来配置这个输出目录。

`🏷️Hugo` 小知识 - 草案、未来和过期内容

Hugo 允许您在网站内容的前言设定中设置文档的draft，publishdate甚至expirydate字段。默认情况下，Hugo 不会发布下面内容：
1. `publishdate` 发布日期值设定在未来的内容；
2. `draft:true` 草案状态设置为真的内容；
3. `expirydate` 过期日期值设置为过去某事件的内容。

这三个可以在本地开发和部署编译时通过对hugo和hugo server分别添加如下参数来重新设定，或者在配置文件中设定对应(不包含--)域的 boolean 值：
1. -F, --buildFuture    include content with publishdate in the future
2. -D, --buildDrafts    include content marked as draft
3. -E, --buildExpired   include expired content

### 2. 部署站点

把生成的 public/静态内容目录上传到 GitHub，开启 GitHub/Gitee Pages，并且绑定 cname 域名即可。


## 获取网站图标

可以使用一为提供的的 Favicon 图标 api：[https://api.iowen.cn/doc/favicon.html](https://api.iowen.cn/doc/favicon.html)。

接口地址：[https://api.iowen.cn/favicon](https://api.iowen.cn/favicon)
返回格式：图片
请求方式：get
请求示例：
    ■ https://api.iowen.cn/favicon/www.iowen.cn.png
    ■ https://api.iowen.cn/favicon/www.baidu.com.png

