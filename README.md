适用于郑州大学锐捷认证，8102年5月wlzx加了客户端检验之后搞的。minieap是适用于linux平台的客户端，修改过了原作者的minieap中的认证算法中的特殊数组，加上了特殊字段。pc端的，linux下直接编译即可。openwrt平台的，可以通过zzu-minieap-openwrt这个repo下的makefile交叉编译生成软件包，具体不会给我发邮件
。
从别人哪里import过来的
从别人哪里import过来的
从别人哪里import过来的
从别人哪里import过来的
从别人哪里import过来的
加入了一个咱们学校的特有字段，修改成了咱们学校的版本号和反破解数组。等等。

可以这样用 ：minieap -u 你的学号 -p 你的校园网密码 -n 网络接口视情况而定 --module printer --module rjv3 --module printer --if-impl sockraw --service default --fake-serial 硬盘序列号（可以不用管）
