---
date: 2020-01-01
category:
  - CategoryC
tag:
  - tag E
sticky: 10
archive: false
---

# Rails学习之路

## Ruby版本管理工具

一般都推荐或者配套的是`rbenv`或者`rvm`,由于需要科学上网再加上安装网速超级慢,因此不推荐

我更推荐使用[asdf](https://asdf-vm.com/),可以管理ruby,node等各个版本,切换也简单

### 安装依赖

### 安装asdf

<CodeGroup>
  <CodeGroupItem title="linux" active>

```bash
  apt install asdf
```
   </CodeGroupItem>
  <CodeGroupItem title="mac">

```bash
  brew install asdf
```
   </CodeGroupItem>
</CodeGroup>

## Bundler-管理gem

```bash
bundle install rails
```

## 把开发中的秘钥放到环境变量里

```bash
# 运行
PASSWORD=password irb

# 读取
ENV['PASSWORD']

# 查看所有的环境变量
ENV

# 存储环境变量(只能在terminal未关闭的情况下,临时存储)
export PASSWORD=password

# 永久存储环境变量(~/.zshrc添加)
export PASSWORD=password
```

## Rails常用命令

### 指定版本安装

```bash
rails _5.1.4_ new hello_app
```

### 运行
```bash
# 指定端口号运行
rails s -p 3000
```

## Rails目录(以5.x.x为例)

```
├── Gemfile 
├── Gemfile.lock
├── README.md
├── Rakefile
├── app
│   ├── assets
│   │   ├── config
│   │   │   └── manifest.js
│   │   ├── images
│   │   ├── javascripts
│   │   │   ├── application.js
│   │   │   ├── cable.js
│   │   │   └── channels
│   │   └── stylesheets
│   │       └── application.css
│   ├── channels
│   │   └── application_cable
│   │       ├── channel.rb
│   │       └── connection.rb
│   ├── controllers
│   │   ├── application_controller.rb
│   │   └── concerns
│   ├── helpers
│   │   └── application_helper.rb
│   ├── jobs
│   │   └── application_job.rb
│   ├── mailers
│   │   └── application_mailer.rb
│   ├── models
│   │   ├── application_record.rb
│   │   └── concerns
│   └── views
│       └── layouts
│           ├── application.html.erb
│           ├── mailer.html.erb
│           └── mailer.text.erb
├── bin
│   ├── bundle
│   ├── rails
│   ├── rake
│   ├── setup
│   ├── spring
│   ├── update
│   └── yarn
├── config
│   ├── application.rb
│   ├── boot.rb
│   ├── cable.yml
│   ├── database.yml
│   ├── environment.rb
│   ├── environments
│   │   ├── development.rb
│   │   ├── production.rb
│   │   └── test.rb
│   ├── initializers
│   │   ├── application_controller_renderer.rb
│   │   ├── assets.rb
│   │   ├── backtrace_silencers.rb
│   │   ├── cookies_serializer.rb
│   │   ├── filter_parameter_logging.rb
│   │   ├── inflections.rb
│   │   ├── mime_types.rb
│   │   └── wrap_parameters.rb
│   ├── locales
│   │   └── en.yml
│   ├── puma.rb
│   ├── routes.rb
│   ├── secrets.yml
│   └── spring.rb
├── config.ru
├── db
│   └── seeds.rb
├── lib
│   ├── assets
│   └── tasks
├── log
│   └── development.log
├── package.json
├── public
│   ├── 404.html
│   ├── 422.html
│   ├── 500.html
│   ├── apple-touch-icon-precomposed.png
│   ├── apple-touch-icon.png
│   ├── favicon.ico
│   └── robots.txt
├── test
│   ├── application_system_test_case.rb
│   ├── controllers
│   ├── fixtures
│   │   └── files
│   ├── helpers
│   ├── integration
│   ├── mailers
│   ├── models
│   ├── system
│   └── test_helper.rb
├── tmp
│   ├── cache
│   │   └── assets
│   ├── pids
│   ├── restart.txt
│   └── sockets
└── vendor
```
