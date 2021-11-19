# RT前期思路

## 0x01 前言

在红蓝对抗中，信息收集是红队中最重要的一个环节，信息收集的广度决定了团队进攻的入口点

```bash
根据公司/企业/客户提供的信息找到根域/子域/子公司/代理商...
绕CDN找出目标所有真实ip段
找目标的各种Web管理后台登录口
批量抓取目标所有真实C段 Web banner
批量对目标所有真实C段 进行基础服务端口扫描探测识别
尝试目标DNS是否允许区域传送,如果不允许则继续尝试子域爆破
批量抓取目标所有子域 Web banner
批量对目标所有子域集中进行基础服务端口探测识别
批量识别目标 所有存活Web站点的Web程序指纹 及其详细版本
从 Git 中查找目标泄露的各类 敏感文件 及 账号密码,偶尔甚至还能碰到目标不小心泄露的各种云的 "AccessKey"
从网盘 / 百度文库 中查找目标泄露的各类 敏感文件 及 账号密码
从各第三方历史漏洞库中查找目标曾经泄露的 各种敏感账号密码 [ 国内目标很好使 ]
目标Svn里泄露的各类 敏感文件
网站目录扫描 [ 查找目标网站泄露的各类敏感文件, 网站备份文件, 敏感配置文件, 源码 , 别人的webshell, 等等等...]
目标站点自身在前端代码中泄露的各种敏感信息
fofa / shodan / bing / google  hacking 深度利用
搜集目标 学生学号 / 员工工号 / 目标邮箱 [ 并顺手到各个社工库中去批量查询这些邮箱曾经是否泄露过密码 ]
目标自己对外提供的各种 技术文档 / wiki 里泄露的各种账号密码及其它敏感信息
目标微信小程序
分析目标app Web请求
借助js探针搜集目标内网信息
想办法混入目标的各种 内部QQ群 / 微信群
分析目标直接供应商 [尤其是技术外包]
根据前面已搜集到的各类信息制作有针对性的弱口令字典
目标所用 Waf 种类识别 与 绕过
BypassWAF 文件上传 / 读取 / 下载
   BypassWAF Sql注入
   BypassWAF RCE
   BypassWAF 各类Java Web中间件已知Nday漏洞利用
   BypassWAF Webshell 免杀
	
其它更多 , 待补充修正...
```

## 0x02 简介思路

信息收集姿势很多，但是时间不等人，不可能每个方法都去走一遍，要更快的搜集到资产，目前个人采用自动化利用工具与手工的方法去结合。

### 自动化工具

- [ShuiZe_0x727](https://github.com/0x727/ShuiZe_0x727)
- [DBJ大宝剑🗡](https://github.com/wgpsec/DBJ)  可视化边界资产梳理工具

### Web端资产收集

父子公司、根域、子域、C段

### 移动端资产收集

JavaScript、APP、小程序、公众号

### 资产指纹识别

https://github.com/ShiHuang-ESec/EHole

https://github.com/EdgeSecurityTeam/EHole

https://github.com/winezer0/whatweb-plus

https://github.com/r0eXpeR/fingerprint

### 资产相关信息检测

NMAP

Tx_portmap

网络搜索引擎

### POC批量检测

X-ray

Goby

## 0x03 如何利用

#### 1.获取公司/企业相关信息

ICP备案查询地址：https://beian.miit.gov.cn
 输入根域名（如wps.cn）查询对应的公司备案名

#### 2.收集父子公司

通过天眼查中的“股权穿透图”，收集目标企业的子公司及父公司

#### 3.收集根域

ICP备案查询地址：https://beian.miit.gov.cn
 通过ICP备案收集根域，依次输入查询到的备案公司名，查询对应的全部根域名

#### 4.收集子域

fofa收集子域

https://fofa.so
 结果导出：之前使用工具https://github.com/wgpsec/fofa_viewer，不过发现fofa_viewer导出的结果不完整，改用自己工具[fofa-Extractor.py](https://github.com/ybdt/mind-map/blob/main/1-自动化薄弱检测/1-Web/附件/fofa-Extractor.py)

phpinfo.me收集子域

https://phpinfo.me/domain
 结果导出：可使用工具[phpinfo_me_extractor.py](https://github.com/ybdt/mind-map/blob/main/1-自动化薄弱检测/1-Web/附件/phpinfo_me_extractor.py)

subDomainsBrute收集子域

https://github.com/lijiejie/subDomainsBrute

ksubdomain收集子域

https://github.com/knownsec/ksubdomain

OneForAll收集子域

https://github.com/shmilylty/OneForAll

subfinder收集子域

https://github.com/projectdiscovery/subfinder

#### 5.收集C段

nmap收集C段

查询到某个子域ip和目标组织位于同一城市，可考虑收集目标IP全端口、目标IP半个C段、目标IP整个C段
 坑1：上来就扫描整个C段，12小时候才发现，卡在第2台主机......
 经验1：扫描开始后要观察一下扫描进度，确实是否有防火墙，不要挂到VPS上就不管了

Tx_portmap