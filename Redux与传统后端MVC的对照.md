# Redux与传统后端MVC的对照

	**Redux	                      传统后端 MVC**
	store	                      数据库实例
	state	                      数据库中存储的数据
	dispatch(action)	          用户发起请求
	action: { type, payload }	  type 表示请求的 URL，payload 表示请求的数据
	reducer	                      路由 + 控制器（handler）
	reducer中的 switch-case 分支	  路由，根据 action.type 路由到对应的控制器
	reducer                       内部对 state 的处理	控制器对数据库进行增删改操作
	reducer 返回 nextState	      将修改后的记录写回数据库