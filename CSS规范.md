#CSS代码风格
---
###1.命名
	lass应优先虑以这元素具体目的来进行命名，应尽量简短且富有含义。
	统一采用小写英文字母、数字、“-” 的组合。其中不得包含汉字、空格和特殊字符
	
	不推荐：
	.demoimage {}    /*demo和image中间没加 - */
	.error_status {} /* 用下划线 _ 的是屌丝的风格*/
	推荐：
	.add-sample {}
	
	注意：原则上不建议缩写，除非一看就懂的缩写，如nav
		 尽量避免使用id来控制样式.
###2.常用CSS类命名清单
	全屏：full_bg（全屏背景）
	容器：wrapper（最外面的主框架）
	页头：header（子项：h_1、h_2、……）
	内容：container
	页面主体：main
	页尾：footer
	导航：nav（子项：n_1、n_2、……）
	菜单：menu（子项：m_1、m_2、……）
	导航：nav（子项：n_1、n_2、……）
	子菜单：submenu
	侧栏：sidebar
	栏目：column（扩展：column1、column2、……）
	左右中：left、right、center
	搜索：search
	登陆：signin
###3.选择器
######避免出现过多的祖先选择器，各浏览器会有性能差异，消耗在选择器的时间也不尽相同。尽量最多控制在**3**级以内。
	/* 不推荐 */
	ul.example {}
	.example1 .example2 .example3 .example4 {}

	/* 推荐 */
	.example {}
	.example1, 
	.example2 {}
######非必要的情况下不要使用元素标签名和ID或class进行组合
	/*不推荐*/
	ul#example {}
	div.error {}
	
	/*推荐*/
	#example {}
	.error {}
	
###4.简化CSS
######写属性值的时候尽量使用缩写
	/*不推荐*/
	.example { 
	  border-top-style:none; 
	  font-family:Palatino, serif; 
	  font-size:100%; 
	  line-height:1.6; 
	  padding-bottom:2em; 
	  padding-left:1em; 
	  padding-right:1em; 
	  padding-top:0; 
	}

	/*推荐*/
	.example { border-top: none; font: 100%/1.6 Palatino, serif; padding: 0 1em 2em;}
######属性值为0时，忽略单位
	/*不推荐*/
	.example ｛ margin:0px; padding:0px;｝
	
	/*推荐*/
	.example { margin:0; padding:0; }
######属性值出现小数点忽略0
	/*不推荐*/
	.example { font-size:0.8em; }
	
	/*推荐*/
	.example { font-size:.8em; }
######省略URL外的引号
	/*不推荐*/
	.example {background-image: url("images/noise.png");}
	
	/*推荐*/
	.example {background-image: url(image/noise.png);}
######十六进制尽可能使用3个字符
	/*不推荐*/
	.example { color:#bccbee; }
	
	/*推荐*/
	.example { olor: #ebc; }
######分隔选择器
	每个选择器和声明都要独立新行
	/*不推荐*/
	a:focus, a:active { position: relative; top: 1px;}
	
	/*推荐*/
	h1,
	h2,
	h3 { font-weight: normal; line-height: 1.2;}
######声明完结
	考虑到一致性和拓展性，请在每个声明尾部都加上分号
	
	/*不推荐*/
	.test {
	  display: block;
	  height: 100px
	}

	/* 推荐 */
	.test { display: block; height: 100px;}

###5.CSS书写顺序
######书写顺序按 显示属性----自身属性----文本属性顺序
	显示属性
		display
		list-style
		position
		float
		clear

	自身属性
		width
		height
		margin
		padding
		border
		background

	文本属性
		color
		font
		text-decoration
		text-align
		vertical-align
		white-space

###6.CSS Meta规则
######编码
	utf-8
######注释
	页面注释
		有时候一份CSS会把首页和各种二级页面样式写在一起，这时需要做页面注释。
		/*********************************** 
		 * 首页 
		 ***********************************/	
	
	分级注释
		比如在main模块下，建立了news、photo等栏目，可使用分级注释，以指明层级结构。
			/*----------------main-----------------*/
			#main {}
			.main-bg {}
			
			/* news */
			.news {}
			
			/* photo */
			.photo  {}

	区块间注释
		/* news */
		.news {}
		
		/* photo */
		.photo  {}
	
	修改注释
		当后期维护中有修改到css，需添加修改的注释。

		.news {} /* 修正横向滚动条错误 by your name */

###7.样式初始化
	*{word-wrap:break-word}
	html,body,h1,h2,h3,h4,h5,h6,hr,p,iframe,dl,dt,dd,ul,ol,li,pre,form,button,input,textarea,th,td,fieldset{margin:0;padding:0}
	ul,ol,dl{list-style-type:none}
	html,body{*position:static}
	html{font-family: sans-serif;-webkit-text-size-adjust:100%;-ms-text-size-adjust:100%}
	address,caption,cite,code,dfn,em,th,var{font-style:normal;font-weight:400}
	input,button,textarea,select,optgroup,option{font-family:inherit;font-size:inherit;font-style:inherit;font-weight:inherit}
	input,button{overflow: visible;vertical-align:middle;outline:none}
	body,th,td,button,input,select,textarea{font-family:"Microsoft Yahei","Hiragino Sans GB","Helvetica Neue",Helvetica,tahoma,arial,Verdana,sans-serif,"WenQuanYi Micro Hei","\5B8B\4F53";font-size:12px;color: #333;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing:grayscale}
	body{line-height:1.6}
	h1,h2,h3,h4,h5,h6{font-size:100%}
	a,area{outline:none;blr:expression(this.onFocus=this.blur())}
	a{text-decoration:none;cursor: pointer}
	a:hover{text-decoration:underline;outline:none}
	a.ie6:hover{zoom:1}
	a:focus{outline:none}
	a:hover,a:active{outline:none}:focus{outline:none}
	sub,sup{vertical-align:baseline}
	button,input[type="button"], input[type="submit"] {line-height:normal !important}
	/*img*/
	img{border:0;vertical-align:middle}
	a img,img{-ms-interpolation-mode:bicubic}
	.img-responsive{max-width: 100%;height: auto}
	 
	/*IE下a:hover 背景闪烁*/
	*html{overflow:-moz-scrollbars-vertical;zoom:expression(function(ele){ele.style.zoom = "1";document.execCommand("BackgroundImageCache",false,true)}(this))}
	 
	/*HTML5 reset*/
	header,footer,section,aside,details,menu,article,section,nav,address,hgroup,figure,figcaption,legend{display:block;margin:0;padding:0}time{display:inline}
	audio,canvas,video{display:inline-block;*display:inline;*zoom:1}
	audio:not([controls]){display:none}
	legend{width:100%;margin-bottom:20px;font-size:21px;line-height:40px;border:0;border-bottom:1px solid #e5e5e5}
	legend small{font-size:15px;color:#999}
	svg:not(:root) {overflow: hidden}
	fieldset {border-width:0;padding: 0.35em 0.625em 0.75em;margin: 0 2px;border: 1px solid #c0c0c0}
	input[type="number"]::-webkit-inner-spin-button,input[type="number"]::-webkit-outer-spin-button {height: auto}
	input[type="search"] {-webkit-appearance: textfield; /* 1 */-moz-box-sizing: content-box;-webkit-box-sizing: content-box; /* 2 */box-sizing: content-box}
	input[type="search"]::-webkit-search-cancel-button,input[type="search"]::-webkit-search-decoration {-webkit-appearance: none}
	/*
	Name:			style_clearfix
	Example:		class="clearfix|cl"
	Explain:		Clearfix（简写cl）避免因子元素浮动而导致的父元素高度缺失能问题
	*/
	.cl:after,.clearfix:after{content:".";display:block;height:0;clear:both;visibility:hidden}.cl,.clearfix{zoom:1}	
	
###8.清除浮动
	.clearfix:after{ content: ""; height: 0; visibility: hidden; display: block; clear: both;} 
	.clearfix{ zoom: 1;}