## 环境配置

---

Linux下安装yum：

* 下载最新的yum-3.2.28.tar.gz并解压

  wget http://yum.baseurl.org/download/3.2/yum-3.2.28.tar.gz
  
  tar xvf yum-3.2.28.tar.gz
  
* 运行安装

  touch/etc/ yum.conf

  cd yum-3.2.28
  
  yummain.py install yum

* 更新系统，搞定收工
  yum check-update
  
  yum update
  
  yum clean all
