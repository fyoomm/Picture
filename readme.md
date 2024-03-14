<b><details><summary>📚 目录 </summary></b>

-  [<h4>环境</h4>](#环境)
-  [<h4>问题点与解决方法</h4>](#问题点与解决方法)

</details>



<a id="cdn"></a>
# 环境
在 Linux version 5.15.0-73-generic (buildd\@bos03-amd64-060) (gcc (Ubuntu 11.3.0-1ubuntu1\~22.04.1) 11.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #80-Ubuntu SMP Mon May 15 15:18:26 UTC 2023

<a id="cdn1"></a>
# 问题点与解决方法
### 1、rdk代码下载提示权限不足，但秘钥已添加到git

**解决方法**：因为repo默认采用当前的用户名去登陆远程git的用户名，拉取时的用户名导致地址不对。所以开账户时，请与远程仓库账户名一致。

### 2、m4_native配方编译错误问题
**解决方法**：m4_native 1.4.18版本的代码与ubuntu22有冲突，升级到m4_native 1.4.19版本

### 3、util-linux config失败
**解决方法**：在bb文件增加--dis-raw
