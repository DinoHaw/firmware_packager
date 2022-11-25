# firmware_packager

### 一、介绍
这是一个 bin 固件打包器， 为 bin 固件附上一个 fpk 表头（[《fpk固件包表头信息》](https://gitee.com/DinoHaw/firmware_packager/blob/master/document/fpk%E5%9B%BA%E4%BB%B6%E5%8C%85%E8%A1%A8%E5%A4%B4%E4%BF%A1%E6%81%AF.pdf)）后，生成 fpk 固件包。该固件打包器是 [ **mOTA** ](https://gitee.com/DinoHaw/mOTA) 组件的一部分。

### 二、实现的功能
#### （一）固件打包部分
1.  选择 bin 固件后进行打包，将会为固件添加一个 96-byte 的表头（表头尺寸下选框可指定其它的表头尺寸，多出 96-byte 的部分，将会填充为 `0x00` ），表头与固件合并后将在保存路径上生成一个 fpk 固件包。  
2.  可选择是否加密（采用 AES256 加密算法）、填写字符水印、选择表头尺寸（默认 96 byte）、固件存放的分区名、固件的版本（数值型，若要采用字符型请修改源码）。    
![fpk固件打包器_打包](image/fpk%E5%9B%BA%E4%BB%B6%E6%89%93%E5%8C%85%E5%99%A8_%E6%89%93%E5%8C%85.png)

#### （二）固件解析部分
可通过选择打包后的 fpk 固件包，软件将自动解析固件包的信息并展示出来。  
![fpk固件打包器_解析](image/fpk%E5%9B%BA%E4%BB%B6%E6%89%93%E5%8C%85%E5%99%A8_%E8%A7%A3%E6%9E%90.png)


### 三、编译环境

本工程采用 Qt6 编译， Qt5 也支持，需要自己设置一下（如果不知道怎么编译，直接用 [`firmware_packager.exe
`](https://gitee.com/DinoHaw/firmware_packager/tree/master/exe) 文件即可）

### 四、Linux 下编译或打包

Linux 下编译及安装桌面启动文件：

```bash
qmake6 source/firmware_packager.pro
sudo install -Dm755 source/firmware_packager /usr/bin/firmware-packager
sudo install -Dm644 source/images/icon.png /usr/share/icons/hicolor/192x192/apps/firmware-packager.png
sudo install -Dm644 source/desktop/com.gitee.dinohaw.firmware-packager.metainfo.xml /usr/share/metainfo/com.gitee.dinohaw.firmware-packager.metainfo.xml
sudo install -Dm644 source/desktop/com.gitee.dinohaw.firmware-packager.desktop /usr/share/applications/com.gitee.dinohaw.firmware-packager.desktop
```

### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request
