# wsgo

### 底层为go，逻辑层js，轻松快速构建高性能WebSocket服务端。

#### 欢迎加入QQ群：739721147
#### v3.0重要更新：
1. 支持ES6语法（之前版本仅支持ES5语法）
2. 线程间可方便地共享数据
#### index.js
```
function onOpen(ctx){
	console.log("open", ctx.Id, "conns", ctx.GetAllConns().length)
}

function onMsg(ctx, msg){
	console.log("msg", msg)
	{//操作共享变量代码块
		let db=ctx.DbGet();
		console.log("db",db)
		if(!db.main)db.main=[];
		if(!db.vars)db.vars={};
		let main=[...db.main];
		if(!main.find(x=>x.Id==ctx.Id))db.main=[...main,ctx];
		db.vars.time=new Date();
		ctx.DbDone();
	}//操作共享变量结束
	let conns=ctx.GetAllConns() //获取当前所有连接实例
	//console.log("conns", conns.length, JSON.stringify(conns))
	//conns=conns.filter(function(x){return x.Id!=ctx.Id}) //除自己外其他人
	ctx.SendTo(conns, "Reply:"+msg)
}

function onClose(ctx, err){
	console.log("close")
}
```
