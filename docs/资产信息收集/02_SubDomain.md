# 子域名收集

## 工具爆破

- 🔨[OneForAll](https://github.com/shmilylty/OneForAll)	一款强大的一款功能强大的子域收集工具

## 网络搜索引擎

## 在线平台

- 🔗[ip138](https://site.ip138.com/)

- 🔗[站长之家](https://site.ip138.com/)
- 🔗[phpinfo-me](https://phpinfo.me/domain/)
- 🔗[hackertarget](https://hackertarget.com/find-dns-host-records/)

权重SEO查询

政府基本数据库

## ssl与证书

通过查询SSL证书，获取的域名存活率很高，这应该也是不错的思路。
 SSL证书在线检测工具：https://www.chinassl.net/ssltools/ssl-checker.html

### 工具一键查询

通过工具可以调用各个证书接口进行域名查询

常用工具

```bash
Findomain
Sublist3r（SSL Certificates）等
```

Findomain

Findomain不使用子域名寻找的常规方法，而是使用证书透明度日志来查找子域，并且该方法使其工具更加快速和可靠。该工具使用多个公共API来执行搜索：

```
Certspotter
Crt.sh
Virustotal
Sublist3r
Facebook 
Spyse (CertDB)
Bufferover
Threadcrow
Virustotal with apikey
```

项目地址：`https://github.com/Edu4rdSHL/findomain`

子域名收集：`findomain -t target.com`

使用所有API搜索子域并将数据导出到CSV文件：`findomain -t target.com -a -o csv`

### 在线平台查询

- 🔗[crt.sh](https://crt.sh/)
- 🔗[censys](https://censys.io/)
- 🔗[myssl](https://myssl.com/)

## DNS历史解析

### 在线平台查询

- 🔗[dnsdb](https://www.dnsdb.io/)全球DNS搜索引擎
- 🔗[viewdns.info](http://viewdns.info)DNS历史记录网站，记录了几年内的更改记录
- 🔗[securitytrails.com](http://securitytrails.com)可以查出几年内网站用过的IP、机房信息等

- 🔗[NETCRAFT](https://sitereport.netcraft.com/?url=)

- 🔗[threatbook](https://x.threatbook.cn/)微步在线贴吧

  