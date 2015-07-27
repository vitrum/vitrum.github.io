title: 关于如何架设sproutcore环境-2
id: 46
categories:
  - Uncategorized
date: 2008-06-18 09:26:06
tags:
---

<div id="msgcns!9697D6160EFEBC17!1688" class="bvMsg"><div>windowsXP里面,我下了个ruby-1.8.6,直接就带了GEM,</div>
<div> </div>
<div>命令行</div>
<div>gem install sproutcore</div>
<div> </div>
<div>第一次运行的时候,要提示安装很多东西,搞不懂,都选YES了,后来某个选择选错了,就报错咯,</div>
<div>总结一下,还是要选x86-mswin32的安装方式,后面第二次试就安装成功了,时间关系,下班,明天再试,</div>
<div> </div>
<div>SproutCore 的地址是,http://rubyforge.rubyuser.de/gems/sproutcore-0.9.10.gem(还有1~9,10应该是最新的吧)</div>
<div> </div>
<div>代码如下:</div>
<div>运行文件:RubyGems Package Manager</div>
<div>C:rubybingemhelp.bat</div>
<div> 
c:ruby&gt;cmd /k &quot;c:rubybingem&quot;</div>
<div>RubyGems is a sophisticated package manager for Ruby.  This is a
basic help message containing pointers to more information.</div>
<div>  Usage:
    gem -h/--help
    gem -v/--version
    gem command [arguments...] [options...]</div>
<div>  Examples:
    gem install rake
    gem list --local
    gem build package.gemspec
    gem help install</div>
<div>  Further help:
    gem help commands            list all 'gem' commands
    gem help examples            show some examples of usage
    gem help &lt;COMMAND&gt;           show help on COMMAND
                                   (e.g. 'gem help install')
  Further information:
    [http://rubygems.rubyforge.org](http://rubygems.rubyforge.org/)</div>
<div>c:ruby&gt;gem install sproutcore
Bulk updating Gem source index for: [http://gems.rubyforge.org](http://gems.rubyforge.org/)
Install required dependency activesupport? [Yn]  y
Install required dependency merb-core? [Yn]  y
Install required dependency erubis? [Yn]  y
Install required dependency abstract? [Yn]  y
Install required dependency json_pure? [Yn]  y
Install required dependency rspec? [Yn]  y
Install required dependency rack? [Yn]  y
Install required dependency mime-types? [Yn]  y
Install required dependency erubis? [Yn]  y
Install required dependency rubigen? [Yn]  y
Install required dependency mongrel? [Yn]  y
Select which gem to install for your platform (i386-mswin32)
 1\. mongrel 1.1.5 (ruby)
 2\. mongrel 1.1.5 (x86-mswin32-60)
 3\. mongrel 1.1.5 (java)
 4\. mongrel 1.1.4 (x86-mswin32-60)
 5\. mongrel 1.1.4 (ruby)
 6\. mongrel 1.1.4 (java)
 7\. Skip this gem
 8\. Cancel installation
&gt; 1
Install required dependency gem_plugin? [Yn]  y
Install required dependency daemons? [Yn]  y
Install required dependency fastthread? [Yn]  y
Select which gem to install for your platform (i386-mswin32)
 1\. fastthread 1.0.1 (mswin32)
 2\. fastthread 1.0.1 (ruby)
 3\. fastthread 1.0.1 (i386-mswin32)
 4\. Skip this gem
 5\. Cancel installation
&gt; 2
Building native extensions.  This could take a while...
ERROR:  While executing gem ... (Gem::Installer::ExtensionBuildError)
    ERROR: Failed to build gem native extension.</div>
<div>ruby extconf.rb install sproutcore
creating Makefile</div>
<div>nmake
'nmake' 不是内部或外部命令，也不是可运行的程序
或批处理文件。</div>
<div>
Gem files will remain installed in c:/ruby/lib/ruby/gems/1.8/gems/fastthread-1.0
.1 for inspection.
Results logged to c:/ruby/lib/ruby/gems/1.8/gems/fastthread-1.0.1/ext/fastthread
/gem_make.out</div>
<div>c:ruby&gt;gem install sproutcore
Install required dependency mongrel? [Yn]  y
Select which gem to install for your platform (i386-mswin32)
 1\. mongrel 1.1.5 (ruby)
 2\. mongrel 1.1.5 (x86-mswin32-60)
 3\. mongrel 1.1.5 (java)
 4\. mongrel 1.1.4 (x86-mswin32-60)
 5\. mongrel 1.1.4 (ruby)
 6\. mongrel 1.1.4 (java)
 7\. Skip this gem
 8\. Cancel installation
&gt; 2
Install required dependency cgi_multipart_eof_fix? [Yn]  y
Successfully installed sproutcore-0.9.10
Successfully installed mongrel-1.1.5-x86-mswin32-60
Successfully installed cgi_multipart_eof_fix-2.5.0
Installing ri documentation for sproutcore-0.9.10...
Installing ri documentation for mongrel-1.1.5-x86-mswin32-60...
Installing ri documentation for cgi_multipart_eof_fix-2.5.0...
Installing RDoc documentation for sproutcore-0.9.10...
Installing RDoc documentation for mongrel-1.1.5-x86-mswin32-60...
Installing RDoc documentation for cgi_multipart_eof_fix-2.5.0...</div>
<div>c:ruby&gt;</div></div>