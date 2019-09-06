
原作者：https://github.com/updateing <br> 
加入了一个咱们学校的特有字段，修改成了咱们学校的版本号和反破解数组。等等。<br> 
适用于郑州大学锐捷认证，8102年5月wlzx加了客户端检验之后搞的。minieap是适用于linux平台的客户端，修改过了原作者的minieap中的认证算法中的特殊数组，加上了特殊字段。pc端的，linux下直接编译即可。openwrt平台的，可以通过zzu-minieap-openwrt这个repo下的makefile交叉编译生成软件包，具体不会的可以联系我。
<br>
可以这样用 ：minieap -u 你的学号 -p 你的校园网密码 -n 网络接口视情况而定 --module printer --module rjv3 --module printer --if-impl sockraw --service default
## 在这个仓库的release里面可以找到几个编译好的二进制文件，有padavan的，x64的，等等，省的自己编译
## <br>https://github.com/2512500960/zzu-minieap/releases

编译方法：<br> 
  For桌面linux系统（或者任何有自编译工具链的系统），<br> 
   git clone https://github.com/25125000960/zzu-minieap.git <br> 
   cd zzu-minieap <br> 
   make <br> 
   chmod 777 minieap <br> 
   cp minieap /usr/sbin <br> 
    //开始认证吧
   <br> 
  For嵌入式linux系统，如openwrt 14.07+，去找路由器刷的固件的对应的sdk，从里面解压出来toolchain， <br> 
  export PATH=$PATH:path_to_your_cross_compiler <br>  
  vim config.mk 在最下面的有一行定义交叉编译器的行 <br> 
  CC：=mipsel-openwrt-linux-gcc 如果是pandorabox(openwrt)的toolchain <br> 
  然后执行命令make <br> 
  得到minieap二进制文件。<br> 
  当然如果有完整的sdk的话。可以是 <br> 
  cd sdk_path/package <br> 
  git clone https://github.com/2512500960/zzu-minieap-openwrt.git <br> 
  cd .. <br> 
  make menuconfig 勾选上minieap，默认勾选上的，不管也行 <br> 
  make package/zzu-minieap/compile <br> 
  最后得到客户端对应的ipk软件包 <br> 
  For padavan <br>
  1. 安装编译padavan系统的toolchain所需要的依赖（以unbuntu18.04为例）<br>
   apt-get install git autoconf automake bison build-essential flex gawk gettext gperf libtool pkg-config zlib1g-dev libgmp3-dev libmpc-dev libmpfr-dev texinfo python-docutils mc autopoint lrzsz -y<br>
  2. 下载padavan源码并编译toolchain<br>
  sudo git clone --depth=1 https://gitee.com/hanwckf/rt-n56u.git /opt/rt-n56u <br>
  sudo pushd /opt/rt-n56u/toolchain-mipsel<br>
  sudo ./build_toolchain<br>
  3. 下载minieap源码<br>
  git clone https://github.com/2512500960/zzu-minieap.git -b 4Padavan <br>
  4. 将刚才编译好的toolchain的可执行文件的路径加到环境变量里面<br>
  export PATH=&PATH:/opt/rt-n56u/toolchain-mipsel/toolchain-3.4.x/bin/ <br>
  5. 开始编译 make，最终得到能在padavan上执行的elf文件
  

