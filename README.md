# 码农开发必备之LNMP环境搭建:see_no_evil:
>Linux / Nginx / MySQL / PHP

下面的内容列举了LNMP环境搭建的整个过程，可以通过"页面内查找"的方式进行快速查询：`Ctrl/Command+f`。

## 安装必读
1. 如果之前未曾使用过Linux系统，请事先了解相关知识再进行开发环境的搭建，以免浪费自己的宝贵时间
2. 此次环境搭建基于windows平台中安装虚拟机的方式，软件使用 `yum` 安装，此次安装已在以下版本上测试通过
3. 测试版本：
	- CentOS-6.8-x86_64-minimal
	- PHP 5.6.28
	- Nginx 1.10.2
	- MySQL 5.7.16
4. 如果喜欢这个项目，欢迎[Star](https://github.com/xiaostory) 提交Pr、[反馈问题](https://github.com/xiaostory/vmware-lnmp/issues)😊

## 目录
* [准备工作](#准备工作)
* [环境安装](#环境安装)
* [文件同步](#文件同步)
* [安装帮助](#安装帮助)

## 准备工作
 - VMWare
 - [CentOS-6.8-x86_64-minimal.iso](http://mirrors.163.com/centos/6.8/isos/x86_64/)

## 环境安装

### 虚拟机安装
 - [安装教程参考](http://jingyan.baidu.com/article/3a2f7c2e3d9e3126afd61136.html)

### 更新Yum源
 - [Yum源使用帮助](http://mirrors.163.com/.help/centos.html)
 - Yum源获取
    ```
    wget http://mirrors.163.com/.help/CentOS6-Base-163.repo
    ```

### 系统设置

 - 修改网卡自启动

    ```
    vi /etc/sysconfig/network-scripts/ifcfg-eth0
    修改：ONBOOT=yes 保存
    service network restart
    ```

 - 关闭防火墙(或自行添加规则)

    ```
    1) 永久生效
       开启： chkconfig iptables on
       关闭： chkconfig iptables off
    2) 即时生效，重启后失效
       开启： service iptables start
       关闭： service iptables stop
    ```

 - 关闭SELINUX

    ```
    vi /etc/sysconfig/selinux
    修改：SELINUX=disabled
    ```

### Nginx安装
 - 创建Yum源
    ```
    cd /etc/yum.repos.d
    vi nginx.repo

    [nginx]
    name=nginx repo
    baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
    gpgcheck=0
    enabled=1

    ```

 - 安装
    ```
    yum -y install nginx
    ```

### MySQL安装
 - [MySQL 5.7 on CentOS Via Yum](http://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/)

### PHP安装
 - [PHP 5.6 on CentOS Via Yum](https://webtatic.com/packages/php56/)


## 文件同步

### vmtools 安装
 - 安装依赖
    ```
    yum -y install perl
    ```
 - [vmware tools on CentOS-6.8-x86_64-minimal](http://blog.sina.com.cn/s/blog_4c86552f0102wmab.html)
 - 设置本地项目和虚拟机共享目录同步
    >菜单栏 虚拟机 > 设置 > 选项 > 共享文件夹

 - CentOS共享目录
     ```
     /mnt/hgfs
     ```

## 安装帮助
 - [libmcrypt](https://pkgs.org/centos-6/epel-x86_64/libmcrypt-2.5.8-9.el6.x86_64.rpm.html)
 
    >PHP安装过程中,如出现 libmcrypt 相关报错,参考以上链接

## 联系我
- 邮箱：<a href="mailto:itwangxf@sina.cn">发邮件给我</a>
- 或者直接提Pr，Issues


**[⬆ 返回顶部](#安装必读)**

