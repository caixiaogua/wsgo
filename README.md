# wsgo

### 底层为go，逻辑层js，轻松快速构建高性能WebSocket服务端。

#### 欢迎加入QQ群：739721147
#### v3.0重要更新：支持ES6语法（之前版本仅支持ES5语法）
#### index.js
```
function onOpen(ctx){
	console.log("open", ctx.Id, "conns", ctx.GetAllConns().length)
}

function onMsg(ctx, msg){
	console.log("msg", msg)
	var conns=ctx.GetAllConns()
	// console.log("conns", conns.length, JSON.stringify(conns))
	// conns=conns.filter(function(x){return x.Id!=ctx.Id}) //其他人
	ctx.SendTo(conns, "Reply:"+msg)
}

function onClose(ctx, err){
	console.log("close")
}
```
