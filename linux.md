###1.系统目录	
	/     linux根目录
	/boot  启动目录，启动信息
	/sbin  程序的启动文件，程序的命令
	/dev   设备目录
	*/etc   可编辑文本配置的缩写，放置一些配置信息
	/home  家目录，其实是指用户的目录
	/root  最大的用户有一个单独的目录
	/lib   存放一些库文件
	/lost+found: 这个目录平时是空的，系统在非正常关系而留下的“无家可归”的文件就在这里
	/media:自动识别一些设备的时候，会自动挂载到这个目录，比如：cd/dvd
	/mnt 安装临时文件系统的安装点，让用户临时挂载其他的文件系统
	/proc 虚拟文件系统的目录
	/tmp 通用的临时文件
	*/usr 很重要，用来安装一些应用程序
	/opt 存放一些可选的应用程序
	/sys 是sysfs文件系统的挂载点 类似proc
	/selinux 用来保证系统的安全
		getenforce 查看
	/srv 系统启动的时候可以访问的数据库目录
	/var 用于存放运行时需要改变数据的文件，比如各种服务的日志文件
###2.基础命令
######命令格式
	命令 【选项】 【参数】
	
	1.基本
	cd: 					切换工作目录
	pwd:					查看工作目录
	cd -                    上一次操作目录
	cd ~					当前登录用户的家目录
	cd .					当前目录
	cd .. 					上级目录
	
	ls						查看当前目录下的文件
	ls -a					查看当前目录下所有文件，包含隐藏文件
	ls -l					显示文件及其详细信息
	ls -h					更人性化的显示文件
	ls-l == ll				等价
	
	2.文件类型说明
		-	普通文件
		d	目录文件
		b	块设备
		c	字符设备
		l	链接
		s	套接字
		p   管道
		
	3.其他命令
		ping   一般用于检测网络是否连通，可以跟地址和域名
		ipconfig  查看网卡信息
###3.终端工具 vim 和 vi
######安装vim
	yum install -y vim

######工作模式
	1.正常模式
		使用方式： vim filename 若文件存在，则直接打开若文件不存在，则会新建，若不修改，则不会创建空文件
		a.用来打开文件
		b.在任意模式下按ESC键即可进入该模式
		c.用来浏览和修改文本内容
	2.编辑模式
		主要用来向文本添加内容，也叫插入模式
		正常模式下 输入一下字符都可以进入该模式:
		i:	在光标所在字符前开始输入文字	
		I:	在行首第一个非空白字符处开始输入文字
		a:	在光标所在字符后开始输入文字
		A:  在行尾开始输入文字
		o:  在光标下面重新开始一行
		O:	在光标上面重新开始一行
		s:  删除光标所在的字符计入插入模式
		S： 直接删除光标所在行
	3.命令模式
		主要用来管理文件或设置vim， 如：保存，退出，放弃等，而不是修改文件内容
		正常模式下输入 '：'
		保存文件： w
		退出文件： q
		保存退出： x 等价于wq
		强制退出： ！
		放弃修改： e!
		强制退出： q!
		
###4.VIM的使用技巧
	
	1.打开文件 
	  vim filename	光标将定位到保存时候的位置
	  vim filename +n 打开文件，并将光标定位到文件第n行
	  vim filename +  打开文件，并将文件定位到末尾
	
	2.光标定位（在正常模式下操作）
	  gg: 首行
	  GG: 尾行
	  ngg: 第几行，等价于命令模式下的:n，然后敲回车
	  0： 行首
	  ^:  首个非空字符
	  $:  行尾
	  k:  向上
	  j:  向下
	  h:  向左 
	  l:  向右
	3.复制粘贴（在正常模式下操作）
	  yy: 复制光标所在行内容
	  dd: 剪切光标所在行内容
	  p:  粘贴缓冲取的内容
	  nyy: 复制光标开始的n行
      npp: 剪切光标开始的n行 包括光标所在的行
	
    4.回退操作（在正常模式下操作）
	  u: 撤销刚才的操作
	  ctrl+r: 反撤销
	
    5.查找操作（在命令模式下操作）	  
	  ：或者？查找内容，然后敲回车即可查找相关内容，n向前翻，N向后翻
	  ：%s/查找内容/替换内容/【g】,将查找的内容替换，g表示全局替换，【】参数可选
	  : 起始行，结束行s/查找内容/替换内容/【g】 替换从起始行到结束行查找到的内容 g同上
	
	6.设置行号
	 ：set nu 设置行号
	 : set nonu 取消行号
	 ：set tabstop 设置tab为4个空格
	 ：set fileeccoding 设置字符集

	 上面在命令模式下生效，退出后配置就无效
     可以在用户目录下创建 .vimrc 文件。这个文件是vim的配置文件
	
	7.
	  文件未保存就关闭vim,会产生临时文件，下次打开会提示回复和删除等相关操作

	8.查找文件
	  whereis php	
### 10.linux下的lamp安装路径
	apache:
	如果采用RPM包安装，安装路径应在 /etc/httpd目录下
	apache配置文件:/etc/httpd/conf/httpd.conf
	Apache模块路径：/usr/sbin/apachectl
	web目录:/var/www/html
	如果采用源代码安装，一般默认安装在/usr/local/apache2目录下
	
	php:
	如果采用RPM包安装，安装路径应在 /etc/目录下
	php的配置文件:/etc/php.ini
	如果采用源代码安装，一般默认安装在/usr/local/lib目录下
	php配置文件: /usr/local/lib/php.ini
	或/usr/local/php/etc/php.ini
	
	mysql:
	如果采用RPM包安装，安装路径应在/usr/share/mysql目录下
	mysqldump文件位置：/usr/bin/mysqldump
	mysqli配置文件:
	/etc/my.cnf或/usr/share/mysql/my.cnf
	mysql数据目录在/var/lib/mysql目录下
	如果采用源代码安装，一般默认安装在/usr/local/mysql目录下

	#root用户   $普通用户
	a. 从普通用户切换到root用户：	su
	   然后输入root用户的密码
	b. 从root用户切换到普通用户： su luhix
	   不需要密码
	
### 9.文件操作
	如果只是查看文件，不修改文件，没有必要用vim命令，可以用一下命令查看:
	a. cat filename   正序查看
	b. tac filename   倒序查看
	c. head -10 filename  查看前10行的内容
	d. tail -5  filename  查看结尾的5行内容
	e. more:
			作用：分也显示其他命令执行的结果
			格式：其他命令 | more,   例如: cat filename | more
			说明：
				1.当内容显示一屏的时候停止
				2.空格向下翻页（只能够向下）======
				3.回车键向下显示一行		 ======
				4.q键退出查看(结束查看)
	f. less:
			作用：分页显示其他命令执行的结果
			格式：其他命令 | more,   例如: cat filename | more
			说明：与more命令功能相同，多了上下按键上下翻一行
	more和less的前面可以是很多查询搜索等命令，如：ls find

### 10.对文件的整体操作
	1.创建文件
		touch:
				作用：创建文件
				格式：touch file1 [file2] 可以一次性创建多个
		cp:
				作用：拷贝文件
				格式：cp 源文件  目标文件
					 cp 源文件 -r 目标文件  强制拷贝 
		rm:
				作用：删除文件
				格式： rm 文件名
					  rm -f 文件名：忽略提示,强制删除
		mv:		
				作用：移动文件
				格式：mv 源文件  目标文件目录/目标文件名
		mkdir: 
				作用：创建文件夹
				格式：mkdir dir1, [dir2]
		rmdir:
				作用：删除文件夹
				格式：rmdir dir1
					 rmdir -r 提示删除
					 rmdir -rf 强制删除
		
		ln:
				作用： 创建链接文件
				格式：ln [-s] 源文件  目标文件
				硬链接：不加 '-s' 选项时，简单理解为一个文件有多个名字
					1.不占用实际空间
					2.不允许给目录创建
					3.只能够跨文件系统
				软连接：添加'-s'选项时，简单理解为一个文件的内容是另一个文件的路径
					1.类似于win下的快捷方式
					2.可以对目录创建
					3.可以跨文件系统

### 11.文件搜索定位
		grep:
			作用：查找文件，正则匹配
			格式：grep [选项] pattern [文件名]
			选项：
				-i:字母不区分大小写搜索
				-n:显示行号
			说明：
				1.pattern为所要匹配的的正则表达式字符串
				2.要用好grep这个工具，其实就是要用好正则表达式
			实例：
				grep ftp /etc/passwd
				grep ftp /etc/passwd -n 显示行号
				在/etc/passwd下查找包含‘ftp’的字符的行
				
				grep 'test' d*
				显示所有以d开头的文件中包含的'test'的行
				
				结合管道:
				ls /bin grep '^m'
				通过管道过滤ls /bin输出的内容，只显示以m开头的行
				
				grep -i 'hello world' menu.h main.c
				显示在menu.h和main.c文件中匹配'hello world' 的行，忽略大小写
			
		 find:
			作用：常见最强大的查找命令
			格式：
				find [目录] 【条件】 【动作】
				目录：所要搜索的目录及其所有子目录。默认为当前目录
				条件：所要搜索的文件的特征
				动作：对搜索结果进行特定的处理
			选项：
				什么都不加：显示当前目录下所有的内容
				-name filename: 指定文件名，可以通过*模糊匹配
				-type: 指定文件类型（b/c/d/p/l/f）
				-size: 指定文件大小，单位可以为K/M/G。 +vu表示大于，-表示小于
				-user:指定用户
				-group: 指定组
				-mtime/atime/ctime: 指定修改、访问、创建时间，单位为天，+表示几天前，-表示几天内
				-amin/min/cmin: 功能同上，单位为分钟
		
		whereis：
			作用：只能够用于搜索命令
			格式： wheresis 命令名
			结果：grep: /usr/bin/grep  /usr/share/man/man1/grep.1.gz
						命令					帮助文档手册
			查找处命令后，可以通过 man 命令名  查看帮助手册
			
		which：
			作用：在$PATH变量指定的路径中，搜索某个系统命令的位置。并且反悔第一个搜索结果
				 也就是说，使用which命令，就可以看到某个系统命令是否存在，以及执行的到底是哪一个
			格式：which 命令
		
	PATH:
		说明：环境变量，与windows中（我的电脑>高级系统设置>g高级>环境变量>系统变量）的PATH类似
	打印：echo $PATH
	导出:
		方式一：一次性的设置
				export PATH = $PATH:dir1[:dir2]
		方式二：永久性的设置，所有用户有效，需要重启生效或者使用source命令
				将方式一的导出操作添加到文件/etc/profile的末尾
		方式三： 永久性的设置，只针对一个用户，需要重庆生效或者使用source命令，优先级高于
				2，将方式1的导出操作添加到文件 ~/.bashrc的末尾
		
### 12.文件的压缩
	gzip：
		作用：压缩文件，只能够是单个文件，不能够是多个，也不能是目录
		格式：gzip file
		说明：执行命令会生成file.gz, 删除原来的文件
		选项： -d 等价于gunzip
	gunzip:
		作用：解压使用gzip压缩生存的文件
		格式：gunzip file.gz
		说明：解压file.gz文件，生存file,删除原来的file.gz
	
	bzip2/bunzip2:
		说明：
			1.用法与gzip/gunzip相同，只是多了‘-k’参数，压缩或者解压后保留源文件
			2.使用bzip2压缩后的文件后缀为bz2，使用gzip压缩的文件后缀为gz
	
	tar :
		说明:gzip/gunzip/bzip2/bunzip2命令只是用于单个文件
			而tar则可以将多个文件或者目录进行压缩
		
		选项：
			-c: 压缩
			-x: 解压
			-z: 使用gzip
			-j: 使用bzip2
			-f: 指定处理文件
			-v: 显示（压缩或解压过程的）详细信息
			-C: 指定解压后存放文件的目录
			
			实例：
				tar -zcvf 123.tar.gz 1 2 3
				使用gzip将1 2 3 压缩成123.tar.gz
				
				tar -zxvf 123.tar.gz [-C /tmp]
				使用gzip将123.tar.gz解压【至/tmp目录】
		
		
		
		

	



	
	


	
	
					
	
	