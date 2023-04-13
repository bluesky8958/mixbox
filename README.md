MIXBOX


MIXBOX是一款全新的，完全基于Shell脚本的工具箱，为在路由器上实现程序的快速配置及运行管理，欢迎大佬们stars、fork及pr.

Telegram群：MIXBOX CHAT
我的博客：Monlor's Blog，备用地址
GitHub地址：monlor/MIXBOX
更新日志
2022-04-25
更新frp版本0.42.0
【测试版】添加插件aliyundrive-fuse, LingMaxDns
2022-04-18
由于部分地区安装失败，现在新增 ghproxy 源、github.do 源
如果还是安装失败，可能因为 CDN 未同步，请在24小时后继续尝试，或者尝试其他源
介绍
工具箱MIXBOX公测发布，Monlor Tools不再更新。新版本有以下改变：

MIXBOX

工具箱尝试支持更多的路由器固件，正在努力中，需要测试
去掉随时可能被小米封的web界面
移除针对小米路由器设置的功能，如修改samba路径和禁用迅雷等，合并到新的插件MIWIFI
增加一个应急功能，在用户目录创建文件uninstall_mixbox即可卸载工具箱
增加几个工具箱常用命令，applist:用于管理插件列表，cru:定时任务管理，mbdb:工具箱数据库，基于uci，mixbox:工具箱命令行交互界面
工具箱增加目录，/etc/mixbox/mbdb:存放数据文件，/etc/mixbox/var/run:存在程序进程pid文件，/etc/mixbox/var/log:工具箱日志目录
工具箱现在不会特意去兼容某个型号，比如R3上的Aria2问题，只考虑CPU架构，mips/arm等，所以如果R3/R1CM发现程序不兼容的情况，可以选择自己替换程序，或同时安装Monlor-Tools工具箱
插件安装去掉了离线安装的功能，后续会加入进来，给用户提供一个自己修改打包插件的机会
ShadowSocks

订阅现在会多次尝试，如已安装EntWare中的curl程序会自动调用用作订阅
现已支持v2ray并测试黑白名单和全局模式，正常使用，v2ray订阅暂不支持
已支持kcptun加速功能，ss和kcp需为同一个服务器，否则不启用
优化添加ss节点时的提示信息
增加haveged程序，用于生成随机数
KoolProxy

由于作者更新程序修改了视频模式的启用方式，更新了启动脚本
https证书生成不再使用openssl程序，而使用kp自带程序生成
新增插件

AliDDNS：获取当前网络的ip，自动解析到阿里云
BaiduPCS：第三方百度网盘下载工具，带web界面
DropBear：移植小米路由器的SSH功能到工具箱
Frps：快速搭建frp服务端
PPTPD：快速搭建vpn服务器，基于EntWare环境
SmartDNS：智能dns解析，从多个上游dns服务器中选取最快的解析地址
SSServer：搭建ss服务器
Transmission：强大的pt下载工具，基于EntWare环境
WebD：极其小巧的网盘工具，功能比较简单
其他等等等小更新...

注意事项
用户目录是指存放一下大文件的目录，如下载的文件等
经测试R3不支持EntWare环境，原因未知，所以基于EntWare的程序都无法使用
0.1.9.7以前的版本请手动更换下载源，步骤：mixbox => 工具箱管理 => 更换下载源 => 输入以下地址
https://cdn.jsdelivr.net/gh/monlor/mbfiles
默认源更换为jsdelivr源，coding源不再使用
命令
本站提供的下载源，基于 cloudflare 搭建【NEW】
export MB_URL=https://g.monlor.com/https://raw.githubusercontent.com/monlor/mbfiles/master && sh -c "$(curl -kfsSl ${MB_URL}/install.sh)" && source /etc/profile &> /dev/null
ghproxy源一键安装命令【NEW】
export MB_URL=https://ghproxy.com/https://raw.githubusercontent.com/monlor/mbfiles/master && sh -c "$(curl -kfsSl ${MB_URL}/install.sh)" && source /etc/profile &> /dev/null
github.do源一键安装命令【NEW】
export MB_URL=https://github.do/https://raw.githubusercontent.com/monlor/mbfiles/master && sh -c "$(curl -kfsSl ${MB_URL}/install.sh)" && source /etc/profile &> /dev/null
github源一键安装命令
export MB_URL=https://raw.githubusercontent.com/monlor/mbfiles/master && sh -c "$(curl -kfsSl ${MB_URL}/install.sh)" && source /etc/profile &> /dev/null
jsdelivr源一键安装命令
export MB_URL=https://cdn.jsdelivr.net/gh/monlor/mbfiles && sh -c "$(curl -kfsSl ${MB_URL}/install.sh)" && source /etc/profile &> /dev/null
手动更新命令
sh -c "$(curl -kfsSl https://cdn.jsdelivr.net/gh/monlor/mbfiles/update.sh)" && source /etc/profile &> /dev/null
手动卸载命令
sh -c "$(curl -kfsSl https://cdn.jsdelivr.net/gh/monlor/MIXBOX/apps/mixbox/scripts/uninstall.sh)" && source /etc/profile &> /dev/null
一键更新所有插件（请先更新工具箱）
applist installed -n | while read line; do mixbox upgrade $line; done
查看插件常用命令（appname为插件名）
mixbox help
小米路由器目录结构
/
|--- /etc/mixbox
|    |--- /apps/        --- 插件安装目录
|    |--- /config/      --- 工具箱配置文件目录
|    |--- /scripts/     --- 工具箱脚本目录
|    |--- /mbdb/        --- 工具箱数据文件目录
|  |--- /var/   --- 工具箱运行pid及日志存放目录
|--- /tmp
|    |--- /messages     --- 系统日志，工具箱日志
|--- /userdisk
|    |--- /data/        --- 硬盘目录
|--- /extdisks/
|    |--- /sd*/         --- 外接盘目录
插件列表
感谢以下插件列表中的作者给我们带来的这么好用的程序！作者链接待完善

ShadowSocks
KoolProxy
Aria2
VsFtpd
kms
Frpc
Ngrok
WebShell
TinyProxy
Entware
KodExplorer
EasyExplorer
HttpFile
VerySync
FastDick
FireWall
JetBrains
QianDao
FileBrowser
ZeroTier
MIWIFI
[AliDDNS]
[BaiduPCS]
[DropBear]
[Frps]
[PPTPD]
[SmartDNS]
[SSServer]
[Transmission]
[WebD]
ttyd
快速制作插件
步骤
git clone https://github.com/monlor/MIXBOX.git
cd MIXBOX/
chmod +x ./tools/*.sh
./tools/newapp.sh [插件名] [插件服务名] [插件介绍]
修改插件脚本和配置文件
./tools/gitsync.sh pack [插件名] [-v]
注意事项
插件名必须为小写，插件服务名一般为驼峰的写法
插件二进制名称建议与插件名对应，二进制名不能出现下划线，建议用横杠，如obfs-local
执行完插件生成脚本后，插件会生成在apps中，注意名称不能与现有插件重复
