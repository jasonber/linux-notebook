配置：https://my.oschina.net/langxSpirit/blog/1647000

# cpu配置

配置cpu：注意使用cpupower https://www.linuxidc.com/Linux/2012-01/50732.htm

cpupower 使用 https://access.redhat.com/documentation/zh-tw/red_hat_enterprise_linux/6/html/power_management_guide/core_infrastructure#C-States

# GPU配置

[驱动安装](https://forum.manjaro.org/t/solved-cannot-install-video-hybrid-intel-nvidia-390xx-bumblebee/49275)

PURGE all nvidia related packages first:
``sudo pacman -Rnsc nvidia-utils linux414-rt-nvidia``
Switch to 390xx bumblebee profile:
``sudo mhwd -f -r pci video-hybrid-intel-nvidia-bumblebee``
`sudo mwhd -i pci video-hybrid-intel-nvidia-390xx-bumblebee`
Install nvidia properly module for 390xx from available in pacman search FOR your kernel.

Reboot.

使用独显

https://blog.csdn.net/yt4766269/article/details/77776938

[cuda](https://medium.com/@joelognn/installing-tensorflow-1-6-0-gpu-on-manjaro-linux-9657fa63478)

[部署数据科学环境](https://www.cnblogs.com/yangruiGB2312/p/9004335.html)

# chrome 搭ti zi

http://www.linuxdiyf.com/linux/21377.html

```shell
～$ google-chrome --proxy-server="socks5://localhost:1080"
```

# 添加SWAP分区

https://wiki.archlinux.org/index.php/Swap_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#.E6.89.8B.E5.8A.A8.E6.96.B9.E5.BC.8F



# 中文字体配置

用于处理软件显示中文乱码、不显示

https://my.oschina.net/langxSpirit/blog/1647000

终极字体配置方案

https://ohmyarch.github.io/2017/01/15/Linux%E4%B8%8B%E7%BB%88%E6%9E%81%E5%AD%97%E4%BD%93%E9%85%8D%E7%BD%AE%E6%96%B9%E6%A1%88/

# 更改软件仓库
https://blog.csdn.net/kxp9545/article/details/76136190

# ssh
https://www.xuebuyuan.com/3222385.html
https://blog.csdn.net/Oliver_Hong/article/details/80509099

# 外接屏幕设置
http://www.cnblogs.com/rossoneri/p/4068274.html
https://blog.csdn.net/mouse1598189/article/details/51991127
https://blog.csdn.net/jningwei/article/details/75044598

#vpn
https://kelvin.mbioq.com/ss-and-ssr-how-to-configure-protocol-confusion-is-the-best.html

# 黑苹果
https://blog.csdn.net/chenjiang2936/article/details/44106761
http://www.carrotchou.blog/18689.html
修改vmx文件
```
scm.version = "0"
cpuid.0.eax = "0000:0000:0000:0000:0000:0000:0000:1011"
cpuid.0.ebx = "0111:0101:0110:1110:0110:0101:0100:0111"
cpuid.0.ecx = "0110:1100:0110:0101:0111:0100:0110:1110"
cpuid.0.edx = "0100:1001:0110:0101:0110:1110:0110:1001"
cpuid.1.eax = "0000:0000:0000:0001:0000:0110:0111:0001"
cpuid.1.ebx = "0000:0010:0000:0001:0000:1000:0000:0000"
cpuid.1.ecx = "1000:0010:1001:1000:0010:0010:0000:0011"
featureCompat.enable = "FALSE"
keyboard.vusb.enable = "TRUE"
mouse.vusb.enable = "TRUE"
```
如果提示需要vax2
将virtualHW.version = "16"改成10
 
 # 关闭苹果sip
 https://mrmad.com.tw/vmware-close-macos-sip
 
# 手机同屏
1. 安装adb
2. android 开发工具
3. 启动adb server

# manjaro KDE 安装心得
##1. [分区](https://blog.csdn.net/lj402159806/article/details/80218360)
    / 20G
    /boot 512mb
    /boot/efi eps 512mb
    /var 15G
    /swap 4G
    /home 剩下所有

##[2.更换源](http://www.bubuko.com/infodetail-3432414.html)
  ```
  # 选择国内的最快的源
  sudo pacman-mirrors -i -c China -m rank
  # 添加源
  echo -e "\n[archlinuxcn]\nSigLevel = TrustAll\nServer = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/\$arch\n\n[antergos]\nSigLevel = TrustAll\nServer = https://mirrors.tuna.tsinghua.edu.cn/antergos/\$repo/\$arch\n"|sudo tee -a /etc/pacman.conf
  # 升级
  sudo pacman-Syy
  # 安装archlinux签名钥匙和antergos签名钥匙
  sudo pacman -S --noconfirm archlinuxcn-keyring antergos-keyring 
  ```
##[3. 触摸板](https://blog.csdn.net/impressionyang/article/details/95591122)
  ```
  yay -S kcm-pointing-devices-git 
  只适用于manjaro KDE。要新更新源。这个软件能实现触摸版的多种功能
  ```
##[4. 中文输入法](https://www.jianshu.com/p/bf6fa0bdc17f)
```
安装
sudo pacman -S fcitx-im  ---全部安裝
sudo pacman -S fcitx -configtool   ----配置工具
sudo pacman -S fcitx-rime    ----可选安装，fcitx默认已有中文输入

配置~/.xprofile 如果没有可以创建
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx
```
##[5. oh-my-sh](https://blog.csdn.net/Xin_101/article/details/83819870)
```
切换bash和zsh
# bash ⇒  zsh
chsh -s /bin/zsh root或者直接zsh
# zsh ⇒ bash
chsh -s /bin/bash或者直接bash
```
##[6. kde美化](https://www.cnblogs.com/luoshuitianyi/p/10587788.html)

#[pacman命令详解](https://blog.csdn.net/nangy2514/article/details/93194184)

命令  |   解释|   备注|
|:-|:-|:-|
|pacman -Syu 	|对整个系统进行更新（常用） 	
|pacman -Syy 	|强制更新 	
|pacman -Syudd 	|使用 -dd跳过所有检测
|pacman -S package_name 	|执行 pacman -S firefox 将安装 Firefox（常用） |你也可以同时安装多个包，只需以空格分隔包名即
|pacman -Sy package_name 	|与上面命令不同的是，该命令将在同步包数据库后再执行安装。 	
|pacman -Sv package_name 	|在显示一些操作信息后执行安装。 	
|pacman -U local_package_name 	|安装本地包，其扩展名为pkg.tar.gz或pkg.tar.xz 	
|pacman -U url 	|安装一个远程包（不在 pacman 配置的源里面） 	|例：pacman -U http://www.example.com/repo/example.pkg.tar.xz

#[8. markdown 常用命令](https://www.cnblogs.com/shawWey/p/8931697.html)
`

#[9. 查看磁盘大小](https://blog.csdn.net/davidhopper/article/details/80706457)

#10. 系统备份
```
dd命令的使用 备份成镜像文件
https://www.cnblogs.com/linuxde/p/8719253.html
https://blog.csdn.net/xtggbmdk/article/details/82706380

tar 备份所有系统文件
https://blog.csdn.net/qq_41932665/article/details/88411812

rsync 使用
https://www.cnblogs.com/Gbeniot/p/5482366.html
https://blog.csdn.net/jerry010101/article/details/88638738
 sudo rsync -vPa / /media/zhang/usb/back_20200228 --exclude=/media/ --exclude=/sys/ --exclude=/proc/ --exclude=/mnt/ --exclude=/tmp/

```

#11.shell 

#12.磁盘挂载
linux下磁盘可以挂载在任何目录下
df 查看磁盘的信息
fdisk 格式化硬盘
mount 挂载
umount 弹出

#[13. manjaro /根目录下的目录说明](https://www.cnblogs.com/lif323/p/10732905.html)

#[14. 安装xmind](https://blog.csdn.net/weixin_44120683/article/details/88431749)
```
yay -S xmind
xmind对jdk13兼容不好，会报错。所以要安装 jdk-8openjdk
yay -S jdk-8openjdk
转换默认的JDK
archlinux-java status 查看有那些jdk
archlinux-java set jdk-8openjdk 设置默认的jdk
```
#[15. wechat输入中文](http://blog.sciencenet.cn/blog-117412-1137251.html)
```
# 修改配置
sudo vim  /opt/deepinwine/apps/Deepin-WeChat
# 添加输入法
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```
#[16. wechat缩放](https://blog.csdn.net/weixin_36349646/article/details/102670624)
```
#env WINEPREFIX="$HOME/.deepinwine/Deepin-WeChat/"  winecfg 
```
