# 用less自动px转换rem

先计算出px和rem比值, 利用less自动把px转换为rem, 再通过编译器(koala)传回css文件:

	//js文件设置比值:
	function() {
		var html = document.documentElement;
		var hWidth = html.getBoundingClientRect().width;
		html.style.fontSize = hWidth/(想设置的px和rem比值) + 'px';
	}

	//在less文件头部写入:
	@r:(fontSize值)rem;

	//例子:
	header{width=200/@r;height=100/@r;}

