## 快速上手

要了解完整的文档请访问 [mkdocs.org](https://www.mkdocs.org)，或者访问中文翻译站点 [mkdocs.zimoapps.com](https://mkdocs.zimoapps.com/)。

### 常用命令

* `mkdocs new [dir-name]` - 创建新的文档目录。
* `mkdocs serve` - 启动调试用实时更新服务。
* `mkdocs build` - 创建文档站点文件。
* `mkdocs -h` - 打印帮助信息。

### 项目布局

    mkdocs.yml    # 本文档项目的配置文件。
    docs/
        index.md  # 文档首页的内容
        ...       # 其他的markdown页面和附件文件。

### 环境安装
1. 安装mkdocs模块

```
~# pip install mkdocs
```

2. 安装主题相关模块

```
~# pip install mkdocs-bootswatch
```  

### 创建新项目
1. 执行下面命令，创建新的文档项目

```
~# mkdocs new notebook-hpc
~# cd notebook-hpc
~/notebook-hpc# tree .
.
├── docs
│   └── index.md
└── mkdocs.yml

1 directory, 2 files
```
查看文档项目目录，可以看到一个配置文件mkdocs.yml, 和一个文档源文件目录docs，其中包含的index.md为一个单一页面文件。

2. 预览页面

mkdoc内置了一个网页服务器，帮助用户预览开发的文件，在mkdocs.yml所在目录下执行如下命令即可启动预览服务器，查看网页。
```
~/notebook-hpc# mkdocs serve --dev-addr=your.server.ip.address:8080
```

### 将站点部署到Github上

mkdocs 支持将文档项目生成的静态文件部署到Github Pages上以生成静态站点，具体包括两种形式，作为项目文档的静态站点，和作为个人或组织页面的静态站点。如果希望通过mkdocs创个人博客，应该选择后者。

1. 创建 Github 项目

登录GitHub站点，创建一个新的 repository, 注意选择 repository name时要选择一个特殊的名字，如果登录github 所用用户名为username，则repository的名字应为 username.github.io，然后点击创建 repository。

2. 克隆 repository 到本地

因为是命令行操作，所以这里克隆地址选择ssh，地址样式为 git@github.com:username/username.github.io.git，克隆命令如下
```
~# git clone git@github.com:username/username.github.io.git username.github.io
```

3. 添加 github 免密登录

由于 github 官方关闭了用户名+密码登录上次代码的方式，因此需要添加token或者key的方式来实现代码上传，这里选择用公钥的方式。
首先执行 ssh-keygen -t rsa -b 4096 生成公钥私钥，然后将公钥的内容拷贝到GitHub上，具体方式是网页右上角头像，点击setting，点击SSH and GPG Keys，New SSH keys，将公钥粘入密钥框，名字任意取，保存。

4. 将静态文件部署到 Github

进入 username.github.io 目录，并执行 mkdocs deploy 命令

```
~# cd username.github.io
~/username.github.io# mkdocs gh-deploy --config-file ~/notebook-hpc/mkdocs.yml --remote-branch master
```
打开浏览器，输入 https://username.github.io/即可访问页面了。
