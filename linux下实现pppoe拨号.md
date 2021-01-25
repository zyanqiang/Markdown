# 1 、Linx下实现pppoe拨号

1. 安装rp-pppoe

   ```shell
   yum install rp-pppoe -y
   ```

2. 配置pppoe账号

   pppoe 使用pap认证或者chap认证，账号密码分别保存在/etc/ppp/pap-secrets和文件/etc/ppp/chap-secrets里面

   ```shell
   echo "user1  *  passwd1 " >>/etc/ppp/pap-secrets 
   echo "user1  *  passwd1 " >>/etc/ppp/chap-secrets 
   ```

   

3. 创建ifcfg-ppp0

   ```
   
   ```



# 2、多pppoe账号拨号实现

一个pppoe拨号创建一个ppp连接，一个ppp0连接带宽正常是100M，如果服务器一台要求跑到5G，这就需要50个pppoe账号同时拨号。每个ppp连接还需要配置策略路由，如果人工维护很麻烦，需要一个脚本来维护这些账号。脚本实现下面功能：

1、根据配置文件生成ifcfg-ppp*

2、定期检查ppp口的ip变化，如果发生变化更新策略路由并通知nat部件的更新回源ip

3、检查ppp账号是否能正常上网，记录到日志给告警使用



# 3、cx维护回源ip列表



# 4、c4-f维护回源ip列表



# 5、cfw维护回源ip列表



# 6、问题讨论

1. pppoe接入是二层广播，pppoe网关只能和拨号机器在同个以太网，我们传输需要和运营商pppoe认证网关二层互联。
2. 如果重一个小区接入多条宽带，我们高峰时候每条都跑满，会不会导致这个小区出口跑满。
3. 如果有多个不同的pppoe接入点，这些pppoe接入到我们项目交换机在同个vlan下，会不会有问题，类似一个局方只能有一个主dhcp服务一样。
4. 如果整个项目流量全部使用pppoe拨号，能否直接配置项目机器上，不要配置在cx上，不然需要增加很多机器。
5. 

