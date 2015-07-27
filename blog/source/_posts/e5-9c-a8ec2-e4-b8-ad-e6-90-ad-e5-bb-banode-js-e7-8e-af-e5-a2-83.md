title: 在EC2 中搭建node.js 环境
id: 720
categories:
  - 计算机与 Internet
date: 2011-09-27 09:15:24
tags:
---

**1，为什么用EC2搭建node.js环境。**
<div>首先，本地虚拟机装centOs是很好的选择，但是需要在家里和公司同时搭好相同的环境比较麻烦，而且也不方便小团队一起折腾。</div>
<div>亚马逊的免费虚拟机只要不跑太复杂的运算大概不会有额外的费用，而且亚马逊么有被墙，国内的托管目前cnode的邀请号求不到啊，还是自己动手丰衣足食吧。</div>
**2，如何申请免费一年的EC2**
<div>在http://aws.amazon.com/上注册。</div>
<div>网上有很多教程，请自行GOOGLE。</div>
<div>**3，EC2虚拟机简单的管理和设置**</div>
<div>新建KEY，保存。</div>
<div>For MAC &amp; Linux</div>
<div>很简单，只要一句话</div>
<div>
<pre>ssh -i user.pem ec2-user@ec2-XXX-XXX-XXX-XXX.compute-1.amazonaws.com</pre>
</div>
<div>以上user.pem可以是你的KEY的路径。</div>
<div>For PC</div>
<div>putty 链接ec2-XXX-XXX-XXX-XXX.compute-1.amazonaws.com</div>
<div>注意需要在connection-&gt;SSH-&gt;Auth里选上你的KEY，之前需要转pem到ppk。</div>
<div>怎么看DNS名：在管理界面里，先点击你要查看的虚拟机，点右键，再弹出的菜单上点“connect”就可以看到如下图：</div>
<div>其中ec2-XXX-XXX-XXX-XXX.compute-1.amazonaws.com是你的DNS名</div>
<div>一般不太需要调整什么，可能要改的就是端口8080要开启。</div>
<div>**4，搭建node前的准备**</div>
<div>默认的liunx中不会吧所有工具都装好，一些基本的工具，需要我们自己装。</div>
<div>以下：</div>
<div>a. make</div>
<div>b.gcc++</div>
<div>c.curl</div>
<div>d.git</div>
<div>一句话安装：</div>
<div>
<pre>sudo yum install gcc-c++ openssl-devel make curl git</pre>
</div>
**5，安装node**
<div>
<pre>wget http://nodejs.org/dist/node-v0.4.12.tar.gz
tar -xvf node-v0.4.12.tar.gz
cd node-v0.4.12
./configure
make</pre>
</div>
<div>由于是在云里跑的，所以make可能会花上30多分钟， 我出去吃了个中饭，回办公室发现好了的。所以，不用在屏幕前傻等，出去走走，预防一下颈椎病。</div>
<div>
<pre>make install</pre>
</div>
<div>其他调整，由于EC2中path的问题，node装完了不一定能直接跑。所以有时候需要做些映射。</div>
<div>
<pre>sudo ln -s /usr/local/bin/node /usr/bin/node
sudo ln -s /usr/local/lib/node /usr/lib/node
sudo ln -s /usr/local/bin/npm /usr/bin/npm
sudo ln -s /usr/local/bin/node-waf /usr/bin/node-waf</pre>
</div>
<div>**6，测试第一个静态文件服务**</div>
<div>先在/home/ec2-user/上建个nodeweb目录，里面放静态页面，然后可以测试了～～</div>
<div>
<pre>var libpath = require('path'),
    http = require("http"),
    fs = require('fs'),
    url = require("url"),
    mime = require('mime');
var path = "/home/ec2-user/nodeweb";
var port = 8080;
http.createServer(function (request, response) {
    var uri = url.parse(request.url).pathname;
    var filename = libpath.join(path, uri);
    libpath.exists(filename, function (exists) {
        if (!exists) {
            response.writeHead(404, {
                "Content-Type": "text/plain"
            });
            response.write("404 Not Found\n");
            response.end();
            return;
        }
        if (fs.statSync(filename).isDirectory()) {
            filename += '/index.html';
        }
        fs.readFile(filename, "binary", function (err, file) {
            if (err) {
                response.writeHead(500, {
                    "Content-Type": "text/plain"
                });
                response.write(err + "\n");
                response.end();
                return;
            }
            var type = mime.lookup(filename);
            response.writeHead(200, {
                "Content-Type": type
            });
            response.write(file, "binary");
            response.end();
        });
    });
}).listen(port);</pre>
</div>
**7，推荐阅读：**
<div> a.Installing Node.js On Amazon EC2 :http://www.embracingthecloud.com/2010/12/05/InstallingNodejsOnAmazonEC2.aspx</div>
<div> b.npm : https://github.com/isaacs/npm</div>
<div> c.mime : https://github.com/bentomas/node-mime</div>
<div>**8，其他～**</div>
求推荐操作简单的配合node用数据库。

我的微博：[http://weibo.com/vitrum](http://weibo.com/vitrum)