# JS 的execCommand 方法 做的一个简单富文本

	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	</head>
	<body>
	<iframe id='HtmlEdit' style="width:400px; height: 300px" marginWidth='2px' marginHeight='2px'></iframe>
	<div id="butGroup">
	    <button id="bold">加粗</button>
	    <button id="copy">复制</button>
	    <button id="big">变大</button>
	    <button id="italic">斜体</button>
	    <button id="underline">下划线</button>
	    <button id="hiliteColor">背景色</button>
	
	    <button id="save">上传</button>
	</div>
	
	<div id="box" style="height: 300px;width: 400px;border: 1px solid black">
	
	</div>
	<script language="javascript">
	    window.onload=function(){
	        var editor,butGroup, doc,box;
	        editor = document.getElementById("HtmlEdit").contentWindow;//获取iframe Window 对象
	        doc = document.getElementById("HtmlEdit").contentDocument; //获取iframe documen 对象
	        butGroup = document.getElementById('butGroup');
	        box= document.getElementById('box');
	        //设置事件监听
	        butGroup.addEventListener('click',function(e){
	            //通过e 事件 获取点击的标签 id
	            switch (e.target.id){
	                case 'bold':addBold(); break;
	                case 'big':big(); break;
	                case 'copy':copy(); break;
	                case 'italic':italic();break
	                case 'hiliteColor':hiliteColor(); break;
	                case 'underline':underline();break;
	
	                case 'save':save();break
	            }
	
	        })
	
	        //只需键入以下设定，iframe立刻变成编辑器。
	        editor.document.designMode = 'On';  //打开设计模式
	        editor.document.contentEditable = true;// 设置元素为可编辑
	
	        function big(){
	            //所有字体特效只是使用 execComman() 就能完成。
	            editor.document.execCommand("fontSize", true, 10);
	           console.log( doc.body.innerHTML);
	
	        }
	       //复制方法
	        function copy(){
	            editor.document.execCommand("copy", true, null);
	        }
	        //加粗方法
	        function addBold() {
	            editor.document.execCommand("Bold", true, null);
	        }
	        //斜体方法
	         function  italic(){
	             editor.document.execCommand('italic',true,null)
	         }
	        //加背景色
	        var hiliteColor = ()=>{ editor.document.execCommand('hiliteColor',true,'yellow') }  //ES6 的箭头函数写法
	
	        //加下划线方法
	        var underline= ()=>{ editor.document.execCommand('underline',true,null)}  //ES6 的箭头函数写法
	
	        //上传方法
	        function save(){
	            box.innerHTML=doc.body.innerHTML;
	        }
	    }
	</script>
	</body>
	</html>