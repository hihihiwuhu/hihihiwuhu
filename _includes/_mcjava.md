开一个我的世界服务器其实并不难，只是麻烦在服务器的配置上，在这篇文章中我将会教大家在Windows/Linux上搭建一个我的世界Java版的服务器。

### Windows

在Windows上搭建我的世界Java版服务器，适用于家机/云服/物理机。

视频教程：还没录

#### 开服环境

首先我们要有一个开服的环境，这个环境可以是你自己的电脑，也可以是云服务器甚至物理服务器。在前期，你可以选择现在自己的电脑上配置好服务端，再将服务端迁移到云服/物理机上，这样可以节省不必要的浪费，如果资金充裕，可以直接购买云服进行开服。

而电脑与云服两者的区别就是电脑无法做到7x24小时稳定开服，而云服可以做到，但不是所有服务商都是那么的稳定，所以在购买云服的时候一定要货比三家，认准后再下单。

#### 环境选择

那么如何选一个适合自己服务端的云服呢，这个取决于你要开的是什么类型的服务端。在1.16以下版本的插件服，你可以选择E5且满载主频在3.0以上的云服，例如E5-2667v2、E5-2687wv2等，反之开的是模组服，那么就建议购买高主频的云服，可以满足大部分需求。1.16以上最好使用云服或者性能较好的面板服，1.18以上可用运行内存建议在4G以上，否则会影响游戏体验。

可选择阿里云、腾讯云、旋律云、星域互联等大厂或口碑较好的服务商，也可以考虑一下我的[内卷云](//www.involutions.cn ':target=_blank')哇:heart_eyes:

#### 运行环境

云服购买后，建议安装Windows server 2012版本的镜像以减少不必要的性能浪费。在开服之前我们需要安装好Java，对应的版本需要对应版本的Java，否则会出现错误，以下是各个版本需要用到的Java：

- 1.8-1.12.2：[Jdk8](//www.aliyundrive.com/s/ge8JEbFNNiZ ':target=_blank,:crossorgin')

- 1.13-1.16：Jdk8/[Jdk11](//www.aliyundrive.com/s/fYRUNWEWUWa ':target=_blank,:crossorgin')

- 1.17：[Jdk16](//www.aliyundrive.com/s/Pr3mhQqgbZW ':target=_blank,:crossorgin')/Jdk17

- 1.18：[Jdk17](//www.aliyundrive.com/s/YEfu89Qmgfb ':target=_blank,:crossorgin')

下载好对应版本的Java之后，默认安装即可，安装后可能需要配置Java环境变量，可参考[菜鸟教程](//www.runoob.com/w3cnote/windows10-java-setup.html ':target=_blank,:crossorgin')。

#### 入坑开始

开服环境以及运行环境都准备好之后，就可以开始开服了，这里用的是内卷云的i9云机作为演示，配置为2核心4G运存10Mbps带宽。

##### 连接云服

摁组合键 <kbd>Win</kbd>+<kbd>R</kbd> 进入运行，输入 mstsc 打开远程桌面连接。

![](./_media/imgs/mcjava/1.png)

然后在图片填入对应的信息，点击连接，输入密码即可。

![](./_media/imgs/mcjava/2.png)

进去后安装好Java，配置环境变量之后就可以进行下一步操作。

##### 核心选择

如果你是购买了成品服务端，可以跳过这一步。

- 插件端

  - [Spigot](//getbukkit.org/download/spigot ':target=_blank,:crossorign') 几乎全版本，只能装插件

  - [Paper](//github.com/PaperMC/Paper 'target=_blank,:crossorign') spigot的衍生版本，性能优化比较好

  - [Purpur](//github.com/PurpurMC/Purpur 'target=_blank,:crossorign') 没用过，可以试试这个

- 插件+模组端
  - [Catserver](//github.com/Luohuayu/CatServer ':target=_blank,:crossorign') 1.12.2-1.18.2
  - [Arclight](//github.com/IzzelAliz/Arclight ':target=_blank,:crossorign') 1.14-1.18.2
  - [Mohist](//github.com/MohistMC/Mohist ':target=_blank,:crossorign') 1.7.10-1.18.2

- 跨服端
  - [BungeeCord](//github.com/SpigotMC/BungeeCord 'target=_blank,:crossorign')
  - [Waterfall](//github.com/PaperMC/Waterfall 'target=_blank,:crossorign')

这里不是完整的，因为懒没把其他的核心整合进来，但是这些核心已经可以满足了，上面的链接均为国外站点，没有魔法下载会很慢 :grin:

这里我就用~~Arclight 1.18.2~~ Catserver 1.12.2作为演示服。

##### 启动脚本

下载好核心之后，可以 <kbd>Ctrl</kbd>+<kbd>C</kbd>/<kbd>V</kbd> 复制粘贴扔进云服里，接着可以创建一个文件夹作为服务端的存放文件夹，把下载好的核心扔进文件夹内即可。

接着我们在与核心文件同级目录下创建一个 start.bat 文件作为启动脚本。

![3](./_media/imgs/mcjava/3.png)

我们右键-编辑这个文件，在里面填入下面的代码，并更改对应信息：

```bash
@ECHO off
java -Xms最小内存 -Xmx最大内存 -jar 核心文件名.jar
```

内存的格式为 1G/1024M 可根据自己的云服进行分配，比如8G的云服，你可以分配7G给服务端，-Xms 可有可无，核心文件名为你下载的核心的名字，粘贴的时候检查一下是否正确。

![4](./_media/imgs/mcjava/4.png)

接着保存退出即可。

##### 跳入深坑

运行启动脚本，正常情况下会自动下载所需的库文件，反之为环境变量没有配置好，请回去配置好变量再运行。

![5](./_media/imgs/mcjava/5.png)

库文件下载完之后，有的核心会提示要你同意EULA才能开启服务器，只要把服务端目录下的 eula.txt 文件里的 eula=false 改成 eula=true 保存退出，再次开服即可。

当出现这一行的时候就说明服务器已经开启成功。

![6](./_media/imgs/mcjava/6.png)

当然，先不要急着进服务器，请看下一步。

##### 修改配置

我们基础的端开好之后，80%是没办法直接进入服务器的，我们需要修改服务端的配置文件，再次开服即可。这里我们可以安装一个文件编辑器 [notepad++](//www.aliyundrive.com/s/L8D415deneN ':target=_blank.:crossorign')，方便编辑配置文件。

右键服务端目录下 server.properties 文件，以notepad++打开。

![7](./_media/imgs/mcjava/7.png)

改完图片里的配置项后，再次开服，进入我的世界，添加服务器 IP:端口 即可。

##### 插件/模组

插件放在plugins文件夹内，模组放在mods文件夹内，如果没有这些文件夹，那就是你选择的核心不支持。每一次安装插件/模组都要重新启动服务器才能生效，并且一定要下载对应MC版本的插件/模组。

插件/模组一定不要盲目的加，可以批量加，否则大概率会报错、不生效等。

有些模组是只用安装在客户端而服务端不需要安装的，请不要混淆，不然会报错，在 [MC百科](//www.mcmod.cn ':target=_blank,:crossorign') 里可以看到该模组的类型，如果该模组只是辅助模组，没有任何附加标签，则为客户端模组，服务端不需要添加，反之两者都要加。

![9](./_media/imgs/mcjava/9.png)

##### 注意事项

- 按照上面的操作开好服务器之后，但无法连接MC服务器，多半为服务器的防火墙没有配置。
  - 如果是腾讯云、阿里云这种大厂，请前往官网-云服务器的防火墙内开放端口，协议选择TCP。
  - 如果是普通服务商，请关闭服务器防火墙，并检查服务端端口是否正确。

![8](./_media/imgs/mcjava/8.png)

#### 内网穿透

如果你是家机开服，可以使用内网穿透让别的玩家进入你的服务器，这里推荐使用 [Sakura Frp](//www.natfrp.cn ':target=_blank,:crossorign') 进行内网穿透，国内节点需要实名认证，因为这是政策要求的，并不是防沉迷。

![10](./_media/imgs/mcjava/10.png)

创建完之后，启动对应的隧道，并进入日志，找到穿透后的地址以及端口。

![11](./_media/imgs/mcjava/11.png)

复制发给你的小伙伴就可以啦！

如果看的不是很明白，可以看视频教程哦:hugs: 

### Linux

在Linux上搭建我的世界Java版服务器，适用于云服/物理机。

视频教程：还没录
