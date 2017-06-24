# F.bind

- call和apply修改this指向并立即调用函数; 而bind是修改this指向返回一个函数**fBOUND**.

- 手写Function.bind函数:

	    if(!Function.prototype.bind){
	    
	    　　Function.prototype.bind = function(oThis){ //oThis为第一个参数,即想要指向的对象
	    
	    　　　　if(typeof this !=="function"){ //this为调用bind的对象
	    
	    　　　　　　throw new TyperError("")
	    
	    　　　　}
	    
	    　　　　var aArgs = Array.prototype.slice.call(arguments,1),   //此处的aArgs是除oThis外的参数
	    
	    　　　　　　fToBind = this,
	    
	    　　　　　　fNOP = function(){},
	    
	    　　　　　　fBound = function(){	//最后返回的函数
	    
	    　　　　　　　　return fToBind.apply(
	    
	    　　　　　　　　　　this instanceof fNOP ? this:oThis||this, aArgs.concat(Array.prototype.slice.call(arguments)));	//此处arguments为返回函数后再次传入的参数
	    
	    　　　　　　　　　　)
	    
	    　　　　　　};
	    
	    　　　　fNOP.prototype = this.prototype;	//使用空函数fnop中转,防止引用指针相同造成原对象被误操作
	    
	    　　　　fBound.prototype = new fNOP();
	    
	    　　　　return  fBound;
	    
	    　　}
	    
	    }