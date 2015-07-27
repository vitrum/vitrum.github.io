title: Install 7zip at CentOS
tags:
  - 7zip
  - centos
id: 703
categories:
  - 计算机与 Internet
date: 2011-05-05 21:29:42
---

1.yum

**yum –y install p7zip**

2.gcc-c++

wget http://nchc.dl.sourceforge.net/sourceforge/p7zip/p7zip_4.65_src_all.tar.bz2
tar -xjvf p7zip_4.65_src_all.tar.bz2
cd p7zip_4.65
make
make install

**
**