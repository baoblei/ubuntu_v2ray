v2ray ubuntu配置

参考：https://crainyday.gitee.io/Ubuntu_006.html

## 客户端

#### v2ray-core

- 下载v2raycore：https://github.com/v2ray/v2ray-core/releases/，测试用的4.28.2，
- 解压到~/.config/qv2ray/vcore目录下（qv2ray客户端默认位置，也可以后面更改）

#### 客户端下载

汇总：https://itlanyan.com/v2ray-clients-download/

使用qv2ray.v2.2.3为例：

- 下载后：右键`→`属性`→`权限`→`允许文件作为程序执行

- 通过命令打开

  ```bash
  # 通过命令提权并执行
  sudo chmod +x ./Qv2ray.v2.2.3.linux-x64.AppImage
  # 若是sudo不能成功运行，请去掉sudo
  sudo ./Qv2ray.v2.2.3.linux-x64.AppImage
  ```

  

  - 若提示FUSE错误，需要安装一下(https://docs.appimage.org/user-guide/troubleshooting/fuse.html)：

    - ubuntu<22.04

      ![](https://cdn.jsdelivr.net/gh/baoblei/imgs_md/20231208174650.png)

    ```shell
    # ubuntu<22.04
    sudo apt-get install fuse libfuse2
    
    # 确保 FUSE 内核模块已加载：
    sudo modprobe -v fuse
    
    # 添加所需的组
    sudo addgroup fuse
    sudo adduser $USER fuse
    
    ```

  - ubuntu22.04

    ![](https://cdn.jsdelivr.net/gh/baoblei/imgs_md/20231208174616.png)

    ```shell
    > sudo apt install libfuse2
    ```

    

- 配置qv2ray

  点击`首选项`，开始配置：`常规配置`。配置后，可点击`检查v2ray核心设置`来确定是否配置成功。

  ![](https://cdn.jsdelivr.net/gh/baoblei/imgs_md/20231208175347.png)

- 订阅地址：添加自己的URL即可

## 设置终端代理

- 打开系统设置，将系统代理设置为手动

  ![](https://cdn.jsdelivr.net/gh/baoblei/imgs_md/20231208184214.png)

- 打开qv2ray，代理方式设置为系统代理

- 编辑～/.bashrc

  ```bash
  # 端口号和手动代理中设置的一样
  export https_proxy=http://127.0.0.1:8889 
  export http_proxy=http://127.0.0.1:8889 
  export all_proxy=socks5://127.0.0.1:1089
  
  source ~/.bashrc
  ```

  