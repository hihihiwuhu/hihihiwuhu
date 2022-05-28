这篇文章适用于所有MCSM 9，包括但不限于内卷云。

#### 购买面板

这里我用内卷云的MCSM作为演示，如果你已经拥有或者已经选好服务商，可以跳过这一步。

前往[内卷云](//www.involutions.cn ':target=_blank')官网，使用手机/邮箱注册并登录，进行实名认证，此处的实名认证不是防沉迷，并且是接入支付宝人脸识别的，不用担心数据会泄露。

实名认证后即可订购面板服，下单并支付后等待管理员开通，下单时需要选择你需要用到的JAVA版本，如后续需要更换JAVA版本可在官网发工单到技术部门更换版本。

![1](_media\imgs\mcsm\1.png)

这里我用高级套餐作为演示，这是下好单并且已经开通的情况。

![2](_media\imgs\mcsm\2.png)

稍作浏览后可以直接登录面板服控制中心。

#### 跳入深坑

MCSM面板服准备好之后，登录控制面板，账户密码均可在官网查看。

这是登录后的样子，点击管理按钮进入服务器管理。

![3](_media\imgs\mcsm\3.png)

##### 准备核心

进来之后不要直接点开启实例，因为这个是一个空壳，你怎么点都没有办法开启，我们先上传自己的服务端核心或者整合好的服务端。

<font color="red">注意：上传的压缩包只支持.zip格式！</font>

![4](_media\imgs\mcsm\4.png)

![5](_media\imgs\mcsm\5.png)

这里我还是用[Catserver](//catmc.org ':target=_blank,:crossorign')核心，下载好后直接上传，上传之后重命名核心为server.jar。

![6](_media\imgs\mcsm\6.png)

核心传好改完名字之后，就可以回主界面开启实例了。

##### 开启实例

首次开启会自动下载缺少的库文件，刷会抖音就好了。

![7](_media\imgs\mcsm\7.png)

有的核心在第一次启动时会要求你同意EULA协议，去左边的特定配置里编辑eula.txt文件，将false改成true，保存后再次开启实例即可。

![8](_media\imgs\mcsm\8.png)

当实例终端出现这个的时候就说明服务器已经开启成功了。

```bash
[Server thread/INFO]: Done (14.536s)! For help, type "help" or "?" 
```

##### 修改配置

基础服务端开好之后，我们是没办法直接进服务器的，要更改服务器的配置文件后才可以进服。

依旧是点击左边实例功能组的特定配置，浏览server.properties文件，并更改对应信息，保存后重启实例即可。

```properties
#true=允许 false=不允许
#Minecraft server properties
#Sat May 28 19:28:12 UTC 2022
max-tick-time=60000
generator-settings=
force-gamemode=false
allow-nether=true	#是否允许生成地狱
gamemode=0	#游戏模式，0生存 1创造 2冒险 3旁观
enable-query=false
player-idle-timeout=0
difficulty=1	#游戏难度，0和平 1简单 2普通 3困难
spawn-monsters=true	#是否允许生成怪物
op-permission-level=4
pvp=true	#是否允许玩家PVP
snooper-enabled=true
level-type=DEFAULT	#生成的世界类型，DEFAULT 默认 FLAT 超平坦
hardcore=false	#是否为极限模式
enable-command-block=false	#是否允许命令方块
max-players=20	#最大同时在线的玩家数量
network-compression-threshold=256
resource-pack-sha1=
max-world-size=29999984
server-port=25565	#服务器端口，需要对应官网产品页内的端口，前面有讲
server-ip=	#服务器IP，留空即可
spawn-npcs=true	#是否允许生成NPC
allow-flight=false	#是否允许玩家飞行
level-name=world	#世界名称
view-distance=10	#视距，可适当调整 推荐：5
resource-pack=	#服务器资源包，支持路径以及URL
spawn-animals=true	#是否允许生成动物
white-list=false	#是否开启白名单
generate-structures=true
online-mode=false	#正版验证，如果没有正版清改为false
max-build-height=256
level-seed=	#世界种子
prevent-proxy-connections=false
use-native-transport=true
motd=A Minecraft Server	#服务器简介
enable-rcon=false
```

浏览并更改后重启实例，然后使用 mccmd.cn:端口 连接服务器即可。

##### 开服成功

添加服务器，请确保你服务端的端口与官网产品页的端口一致！

![9](_media\imgs\mcsm\9.png)

tada！已经检测出来啦！

![10](_media\imgs\mcsm\10.png)

一切操作均与正常开服一致。