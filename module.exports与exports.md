# module.exports与exports

exports是module.exports的引用,指向同一个内存空间.

因此当exports在module.exports被改变后，失效。

	//foo.js
	
	 exports.a = function(){
	  console.log('a')
	 }
	
	 module.exports = {a: 2}
	 exports.a = 1 

	//test.js
	
	 var x = require('./foo');
	
	 console.log(x.a)

	//result:2