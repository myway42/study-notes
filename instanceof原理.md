# instanceof 原理

A instanceof B : 沿着A的\_\_proto\_\_这条线来递归的查找, 如果B的prototype在这条线上, 返回true, 如果\_\_proto\_\_是null了(说明查找到了尽头Object.prototype.\_\_proto\_\_)就返回false.

	function instance_of(L, R) {//L is A, R is B
	  var O = R.prototype;//R is waiting L
	  L = L.__proto__;
	  while (true) {
	    if (L === null) //find until Object.prototype.__proto__
	      return false;
	    if (O === L)
	      return true;
	    L = L.__proto__; //recursively
	  }
	 }

例：

    function Foo(){}
    var f1 = new Foo();
    console.log(f1 instanceof Foo); // true
    console.log(f1 instanceof Object); // true
     
    分析方法：
        f1的__proto__路线A：
            (1) f1.__proto__ === Foo.prototype
            (2) Foo.prototype.__proto__ === Object.prototype
            (3) Object.prototype.__proto__ === null //到终点
    结论：
        f1 instanceof Foo ：A线路(1)中出现了Foo.prototype
        f1 instanceof Object ：A线路(2)中出现了Object.prototype