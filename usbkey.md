# 使用usb_key实现安全的WEB登录

* [产品链接](https://item.jd.com/22214444669.html)
* [附带文档链接](https://pan.baidu.com/s/1JNTmbWvvfYTkWALwU4_HLw) 提取码: 2ye3 
* [SafeNet Authentication Client下载链接](https://support.globalsign.com/customer/portal/articles/1698654)

##制作证书

1.虚拟机安装winserver2008 r2
2.添加角色 Active Directory 证书服务、 Web 服务器(IIS)
3.导出根证书并将根证书拷贝到centos服务器,我用的版本 CentOS Linux release 7.4.1708 (Core)
4.使用openssl命令创建证书申请(服务端证书)
‘’‘ openssl req -nodes -newkey rsa:1024 -keyout service.something.key -out service.something.csr  ’‘’
5.在winserver上粘贴service.something.csr里文本到创建证书页面生成证书(服务端)






[步骤参考](https://cbudde.com/microsoft/certificate-services/setting-up-windows-root-ca-on-centos-6-9-linux-server/)
