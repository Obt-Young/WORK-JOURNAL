- 如何把用户添加到sudo命令列表汇中，使之可以使用sudo  
	1.调整/etc/sudoers文件的权限，增加可写，比如chmod u+w /etc/sudoers，或者chmod 777 /etc/sudoers  
	2.找到	root    ALL=(ALL)       ALL , 在下面增加一行：  
		yk      ALL=(ALL)       ALL  
