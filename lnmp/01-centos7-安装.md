1.安装EPEL源
    yum -y install epel-release

2.安装yum-axelget插件
    yum -y install yum-axelget
    
3.更新CentOS源
    yum clean all && yum makecache && yum -y update
    yum -y install gcc gcc-c++ make kernel kernel-devel
    内核版本：
        cat /proc/version
    发行版本：
        lsb_release -a
        注：使用yum安装lsb
            yum install -y redhat-lsb
        
4.使用sshd登录
    cd ~ && mkdir .ssh && cd .ssh
    ssh-keygen -b 1024 -t rsa -f authorized_keys
    chmod 0700 -R ~/.ssh/ && chmod 0600 ~/.ssh/authorized_keys
    
    将私钥文件下载到Windows主机后，马上删除避免被恶意使用
    rm -rf authorized_keys

    其他配置：/etc/ssh/sshd_config
    
6.修改主机名    
    hostnamectl set-hostname typecodes
    
7.安装vim
    yum -y install vim
    将vi映射为vim命令   
        echo -e "\nalias vi=vim\n" >>~/.bashrc && source ~/.bashrc
    配置vimrc文件
        echo -e "\n\nset nobomb
            set number
            set showmode
            set autoindent
            set smartindent
            set showmatch
            set tabstop=4
            set softtabstop=4
            set shiftwidth=4
            set encoding=utf-8
            set fileencodings=cp936,gb18030,gbk,gb2312,utf-8,ucs-bom,latin-1
            set hlsearch
            set noignorecase
            set fileformats=unix
            set pastetoggle=<F9>\n" >> /etc/vimrc
    
8.常用工具
    yum -y install gcc gcc-c++ net-tools unzip zip curl-devel openssl-devel httpd-tools
    
    
    
9.重新编译
    ./configure
    make
    备份旧的程序
    cp objs/程序 /usr/程序 把新的nginx程序覆盖旧的
    
    
    
    
systemctl stop firewalld.service #停止firewall
systemctl disable firewalld.service #禁止firewall开机启动
