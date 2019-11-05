# 使用VPS下载数据教程

Author:Silence
Email:cocoa9th@gmail.com

## 简介

入门生物信息学我们首先需要有可分析数据，才能进行后续操作。但目前国内网络环境的限制，使得我们很难畅快地从各大数据库下载数据。今天就为大家推荐一种简单快捷的下载方式——使用VPS下载，再使用FileZilla软件下载到本地。

## VPS选择

这里我给大家推荐我一直使用的vultr公司的VPS服务器，大家可以使用我下面发的链接注册使用（PS.如果注册使用的人多我可以免费给大家提供FQ工具)。vultr公司VPS服务器优点：速度不错、稳定且性价比高；按小时计费，能够随时开通和删除服务器。当然大家也可以自行选择，Google搜索可以找到一大堆VPS。

##购买VPS

vultr注册地址：https://www.vultr.com/?ref=8250130

![Screen Shot 2019-11-04 at 11.14.31 AM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8lvllet39j31mj0u0gs2.jpg)

注册好后登陆即进入上述页面，点击Billing可以进行充值。

**注意：**充值可以选择支付宝或微信，但单次最少充值10美元；推荐选择外币信用卡或者Paypal充值，可选择任意金额，如果只用来下载数据那充值1美元就足够啦。

**服务器配置及价格**

5美元/月的服务器配置信息： 单核 1G内存 25G SSD硬盘 带宽峰值100M 1000G流量/月

10美元/月的服务器配置信息： 单核 2G内存 55G SSD硬盘 带宽峰值100M 2000G流量/月

20美元/月的服务器配置信息： 2cpu 4G内存 80G SSD硬盘 带宽峰值100M 3000G流量/月

40美元/月的服务器配置信息： 4cpu 8G内存 160G SSD硬盘 带宽峰值100M 4000G流量/月

充值完成后，可根据下图提示开通服务器。

**注意：**服务器的选择可根据自己下载文件大小选择，如下载30G大小的文件可选择10美元/月的服务器，开通后每小时**10/30/24=0.0139美元**，下载完成后即可把服务器删除，删除后就不会再扣费，算下来一小时成本不到0.1元。

**开通及删除服务器步骤**

第一步

![Screen Shot 2019-11-04 at 11.14.31 AM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m1bd4p8bj31mj0u0q9u.jpg)

第二步

![Screen Shot 2019-11-04 at 3.18.56 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m1bcz6lwj31k80u019o.jpg)

第三步

![Screen Shot 2019-11-04 at 3.18.56 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m1h8hr2ej31kc0u04b7.jpg)

第四步：查看服务器信息及删除服务器

![Screen Shot 2019-11-04 at 3.31.17 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m1o2fgj0j31nt0u0dnd.jpg)

![Screen Shot 2019-11-04 at 3.30.38 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m1o9k6quj31nr0u07f7.jpg)

通过上述步骤，我们已经成功部署了一台Ubuntu服务器。

**注意：**服务器类最好选择Ubuntu，自带wget不需要额外的环境配置。另外，下载工具也可以使用健明老师之前推荐的prefetch等，具体方法请自行查找。

接下来我们通过Terminal连接服务器，下载ftp://ftp.ncbi.nlm.nih.gov/geo/series/GSE60nnn/GSE60607/suppl/GSE60607_RAW.tar的数据。

```shell
#首先查看服务器能否在国内访问
ping 167.179.75.187
# Request timeout for icmp_seq 0
#一直显示即为无法连接IP，请重新部署服务器

#64 bytes from 149.248.2.86: icmp_seq=0 ttl=47 time=4729.195 ms
#有该显示即为可以连接上

#连接到服务器，IP地址及密码可在步骤四查看
ssh root@167.179.75.187
#复制粘贴输入密码即可登录
mkdir data
cd data
wget ftp://ftp.ncbi.nlm.nih.gov/geo/series/GSE60nnn/GSE60607/suppl/GSE60607_RAW.tar
#速度：最高可达17M/s左右，最低6M/s左右，全程基本保持最高速度，偶有波动；25.6G文件总耗时27min左右
ls -lh
#查看下载情况
#total 26G
#-rw-r--r-- 1 root root 26G Nov  4 08:14 GSE60607_RAW.tar
```
**下载速度展示**
 ![Screen Shot 2019-11-04 at 3.50.57 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m334vz1zj30vm0gl47q.jpg)

 ![Screen Shot 2019-11-04 at 4.17.00 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m34malqqj30vo0izwp5.jpg)


##使用FileZilla下载到本地

![Screen Shot 2019-11-04 at 4.10.50 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m30kqadgj316m0u0tx9.jpg)

![Screen Shot 2019-11-04 at 4.17.58 PM](https://tva1.sinaimg.cn/large/006y8mN6gy1g8m30qo6q0j316m0u01kx.jpg)

**注意：**下载到本地速度取决于自己的网速。下载完成后就可删除服务器，避免产生不必要的费用。以后下载再创建一个新服务器即可。
