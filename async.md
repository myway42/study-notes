# async

## 基本概念：

- async 表示这是一个async函数，await只能用在这个函数里面。
- await 表示在这里等待promise返回结果了，再继续执行。
- await 后面跟着的应该是一个promise对象（当然，其他返回值也没关系，不过那样就没有意义了…）

## 举例：

	//获取返回值：
	var sleep = function (time) {
	  return new Promise(function (resolve, reject) {
	    setTimeout(function () {
	      // 返回 ‘ok'
	      resolve('ok');
	    }, time);
	  })
	};
	var start = async function () {
	  let result = await sleep(3000);
	  console.log(result); // 收到 ‘ok'
	};

	//捕捉错误：
	var sleep = function (time) {
	  return new Promise(function (resolve, reject) {
	    setTimeout(function () {
	      // 模拟出错了，返回 ‘error'
	      reject('error');
	    }, time);
	  })
	};
	var start = async function () {
	  try {
	    console.log('start');
	    await sleep(3000); // 这里得到了一个返回错误
	 	// 所以以下代码不会被执行了
	    console.log('end');
	  } catch (err) {
	    console.log(err); // 这里捕捉到错误 `error`
	  }
	};

	// 在循环中：
	var start = async function () {
	  for (var i = 1; i <= 10; i++) {
	    console.log(`当前是第${i}次等待..`);
	    await sleep(1000);
	  }
	};
	在循环中使用不需要闭包，每次循环会被阻塞。