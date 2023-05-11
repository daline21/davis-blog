# 检查Git config是否配置

```shell
git config --global --list
```

# 配置Git用户名和邮箱

```shell
git config --global user.name "daline21"
git config --global user.email "2118523076@qq.com"
```

# 本地Windows生成Ssh key

*Win+R并输入cmd按Enter键确认*<br>

进入目录

```shell
cd C:\Users\Administrator
```

参数写上自己的邮箱

```shell
ssh-keygen -t rsa -C "2118523076@qq.com"
```

# 将https项目切换成ssh方式

```shell
git remote set-url origin git@github.com:daline21/davis-blog.git
```
