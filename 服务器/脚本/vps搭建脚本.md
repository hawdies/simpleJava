# 服务器搭建

## 最简单的Trojan一键脚本，效率高/速度快/延迟低，支持tls1.3，系统支持centos7+/debian9+/ubuntu16+

### 安装bbr加速

先安装wget: `yum -y install wget`
再安装bbr: `wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh`

### 安装trojan

`curl -O https://raw.githubusercontent.com/atrandys/trojan/master/trojan_mult.sh && chmod +x trojan_mult.sh && ./trojan_mult.sh`

启动start.bat.

### 安装switchyomega

配置switchyomega中的proxy情景模式.`sock5`, `127.0.0.1`, `1080`.
进入`auto switch`,删除默认的两条规则,点击`添加规则列表`.
然后，在规则列表规则中，情景模式改为proxy，规则列表网站复制下面的网址，然后点击立即更新情景模式，保存即可。
`https://raw.githubusercontent.com/atrandys/proV/master/fgfwlist.txt`

**tips**:要将switchyomega先选到`proxy`,再更新.否则可能更新失败.
最后选择`autoswitch`模式即可.
