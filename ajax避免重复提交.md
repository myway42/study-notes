# 防止重复数据

在实际项目开发中，提交表单时常常由于网络或者其原因，用户点击提交按钮误认为自己没有操作成功，进而会重复提交按钮操作次数，如果页面前端代码没有做一些相应的处理，通常会导致多条同样的数据插入数据库，导致脏数据的增加。要避免这种现象，在$.ajax请求中的beforeSend方法中把提交按钮禁用掉，等到Ajax请求执行完毕，在恢复按钮的可用状态。

> 举个例子：

	// 提交表单数据到后台处理
	$.ajax({
	    type: "post",
	    data: studentInfo,
	    contentType: "application/json",
	    url: "/Home/Submit",
	    beforeSend: function () {
	        // 禁用按钮防止重复提交，发送前响应
	        $("#submit").attr({ disabled: "disabled" });
	    },
	    success: function (data) {
	        if (data == "Success") {
	            //清空输入框
	            clearBox();
	        }
	    },
	    complete: function () {//完成响应
	        $("#submit").removeAttr("disabled");
	    },
	    error: function (data) {
	        console.info("error: " + data.responseText);
	    }
	});