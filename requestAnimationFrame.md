window.requestAnimationFrame:随着浏览器的重绘频率来更新操作

兼容各浏览器的调用方法:

	(function() {
	    var lastTime = 0;
	    var vendors = ['webkit', 'moz'];
	    for(var x = 0; x < vendors.length && !window.requestAnimationFrame; ++x) {
	        window.requestAnimationFrame = window[vendors[x] + 'RequestAnimationFrame'];
	        window.cancelAnimationFrame = window[vendors[x] + 'CancelAnimationFrame'] ||    // Webkit中此取消方法的名字变了
	                                      window[vendors[x] + 'CancelRequestAnimationFrame'];
	    }
	
	    if (!window.requestAnimationFrame) {
	        window.requestAnimationFrame = function(callback, element) {
	            var currTime = new Date().getTime();
	            var timeToCall = Math.max(0, 16.7 - (currTime - lastTime));
	            var id = window.setTimeout(function() {
	                callback(currTime + timeToCall);
	            }, timeToCall);
	            lastTime = currTime + timeToCall;
	            return id;
	        };
	    }
	    if (!window.cancelAnimationFrame) {
	        window.cancelAnimationFrame = function(id) {
	            clearTimeout(id);
	        };
	    }
	}());


一个例子:

	document.querySelector(‘button’).onclick = function(){
	
	var oT = document.body.scrollTop,flag = ‘up';
	
	var moveup = function(){
	
	var ot = document.body.scrollTop;
	if( flag == ‘up’ ){
	
	ot -= 20;
	if(ot = oT){
	ot = oT;
	flag = ‘stop';
	}
	
	}
	console.log(ot)
	document.body.scrollTop = ot;
	var x = requestAnimationFrame(moveup);
	if(flag == ‘stop’){
	cancelAnimationFrame(x);
	}
	}
	
	if(oT){
	moveup();
	}
	
	}