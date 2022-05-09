# linux 设置文件共享
https://baijiahao.baidu.com/s?id=1690557148787249171&wfr=spider&for=pc

	1、安装
	yum -y install samba


	2、修改文件配置 ：

	[global]

	workgroup = WORKGROUP

	[homes]

	comment = Home Directories

	valid users = %S, %D%w%S

	browseable = No

	read only = No

	inherit acls = Yes

	writable=yes


	[share]
			read only = No
			path = /data/share/
			writable = yes
			public = yes
			create mode = 0777
			directory mode = 0777


	3、建目录：
	mkdir /sharefile

	chmod 777 /sharefile

	mkdir /public

	chmod 777 /public

	4、建立用户

	useradd lxtone

	smbpasswd -a lxtone

	5、重启服务

	systemctl restart smb

	6、测试（注意系统的防火墙和SELinux）

		需要注意的两个地方：

		1)如果CentOS服务器有开启SELINUX的话，建议关闭掉

		vi /etc/selinux/config

		将SELINUX=enforcing 改成SELINUX=disabled，然后reboot重启生效
		2）防火墙配置，若有开启防火墙，需要加入一下规则