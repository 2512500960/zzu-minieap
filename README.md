
原作者：https://github.com/updating
加入了一个咱们学校的特有字段，修改成了咱们学校的版本号和反破解数组。等等。
适用于郑州大学锐捷认证，8102年5月wlzx加了客户端检验之后搞的。minieap是适用于linux平台的客户端，修改过了原作者的minieap中的认证算法中的特殊数组，加上了特殊字段。pc端的，linux下直接编译即可。openwrt平台的，可以通过zzu-minieap-openwrt这个repo下的makefile交叉编译生成软件包，具体不会给我发邮件
。

编译方法：
  For桌面linux系统（或者任何有自编译工具链的系统），
   git clone https://github.com/25125000960/zzu-minieap.git
   cd zzu-minieap
   make 
   chmod 777 minieap
   cp minieap /usr/sbin
    //开始认证吧
   
  For嵌入式linux系统，如openwrt 14.07+，去找路由器刷的固件的对应的sdk，从里面解压出来toolchain，
  export PATH=$PATH:path_to_your_cross_compiler
  vim config.mk 在最下面的有一行定义交叉编译器的行
  CC：=mipsel-openwrt-linux-gcc 如果是pandorabox(openwrt)的toolchain
  然后执行命令make
  得到minieap二进制文件。
  当然如果有完整的sdk的话。可以是
  cd sdk_path/package
  git clone https://github.com/2512500960/zzu-minieap-openwrt.git
  cd ..
  make menuconfig 勾选上minieap，默认勾选上的，不管也行
  make package/zzu-minieap/compile
  最后得到客户端对应的ipk软件包


可以这样用 ：minieap -u 你的学号 -p 你的校园网密码 -n 网络接口视情况而定 --module printer --module rjv3 --module printer --if-impl sockraw --service default
