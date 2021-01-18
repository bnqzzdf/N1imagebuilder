![Build Openwrt img](https://github.com/mingxiaoyu/N1imagebuilder/workflows/Build%20Openwrt%20img/badge.svg)

基于flippy的51+o打包Phicomm N1的openwrt

N1的openwrt来自mingxiaoyu的另一个项目[N1Openwrt](https://github.com/mingxiaoyu/N1Openwrt)
# 如何使用

1. fork项目
2. 上传51+0（Armbian_20.10_Aml-s9xxx_buster_5.4.77-flippy-49+o.img.xz）的flippy的Armbian底包到Google云盘
3. 创建分享链接。大概格式：https://drive.google.com/u/0/uc?export=download&id=xxxx 然后在 Secrets中新建FLIPPY_51_FILEID，值为51+o分享链接中id后面的xxxxxxx
4. 修改n1img.yml文件 
  * 找到这句 wget  https://github.com/mingxiaoyu/N1Openwrt/releases/download/$version/openwrt-armvirt-64-default-rootfs.tar.gz
  * 修改为 wget [openert的URL]
  * 如果你的openwrt固件也在Google云盘， 参考下面代码修改。不会的自己Google、baidu。  
  ```
  curl -L -c cookies.txt 'https://docs.google.com/uc?export=download&id='$OPENWRT_ID  |  sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1/p' > confirm.txt
  curl -L -b cookies.txt -o openwrt-armvirt-64-default-rootfs.tar.gz  'https://docs.google.com/uc?export=download&id='$OPENWRT_ID'&confirm='$(<confirm.txt) 
  ```
5. 点击Actions -> Workflows -> Run workflow -> Run workflow

# 感激
 * [flippy](https://www.right.com.cn/forum/space-uid-285101.html)
 * [coolsnowwolf/Lede](https://github.com/coolsnowwolf/lede)
 * [mingxiaoyu/N1imagebuilder](https://github.com/mingxiaoyu/N1imagebuilder)
