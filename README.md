# 达梦LuaSQL支持说明

## 源文件

达梦和Oracle高度兼容，src目录下的ls_dm.c和dm.def这两个文件，是ls_oci8.c和oci8.def的拷贝，只是将里面和OCI8/oci8相关的字样，修改为了DM/dm。

## 库目录

dmoci这个目录是达梦数据库 (Redhat 7 64位) 服务器安装目录下的drivers/oci目录。

## 运行时

数据库客户端需要dmoci下的三个so文件，可以将这三个文件放在客户机目录/usr/local/lib/dmoci下。

同时，一定要将LD_LIBRARY_PATH环境变量，设置为/usr/local/lib/dmoci！！！

`export LD_LIBRARY_PATH=/usr/local/lib/dmoci`

这是因为libdmoci.so加载依赖库libcrypto.so和libssl.so的方式不规范，它是靠环境变量LD_LIBRARY_PATH手工加载依赖库的，而不是通过建立依赖关系让系统自动加载依赖库。

如果不这样做，到去连接服务器的时候就会出错，出错内容是'加密模块加载失败'。。。
