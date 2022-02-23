# wsgo

### 底层为go，逻辑层js，轻松快速构建高性能WebSocket服务端。

#### 欢迎加入QQ群：739721147

#### index.js
```
function onOpen(ctx){
	console.log("open")
}

function onMsg(ctx, msg){
	console.log("msg", msg)
	var conns=ctx.GetAllConns()
	console.log("conns", conns.length, JSON.stringify(conns))
	// conns=conns.filter(function(x){return x.Id!=ctx.Id}) //其他人
	ctx.SendTo(conns, "Anser:"+msg)
}

function onClose(ctx, err){
	console.log("close")
}
```
