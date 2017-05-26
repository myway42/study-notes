# Web Workers

创建一个新线程, 将需要处理的数据传输给新线程, 监听获取处理完成的数据, 提高运行速度.

	主线程中:
	
	var w1 = new Worker('test.js');//test.js即为创建的新线程
	
	w1.postMessage(需要传输的数据);
	
	w1.onmessage = function (ev) {
	得到处理后的结果ev,执行后续操作
	};
	
	分线程test.js中:
	
	self.onmessage = function (ev) {
	var data = 获得主线程传输的数据并处理;
	self.postMessage(data);	//返回处理后的结果
	};

> 注意! 分线程并不能操作dom以及各种事件等,支持的运行环境如下:
> 
> navgator: appName, appVersion, userAgent, platform
> 
> location: 所有属性都是只读的
> 
> self: 指向全局worker对象
> 
> 所有的ECMA对象, Object, Array, Date等
> 
> XMLHttpRequest构造器
> 
> setTimeout和setInterval方法
> 
> close()方法, 立刻停止worker运行
> 
> importScript方法