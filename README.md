# wsgo

### 底层为go，逻辑层js，轻松快速构建高性能WebSocket服务端。

#### 欢迎加入QQ群：739721147

#### index.js
```
let count=0;
let users=[];

function onOpen(ctx){
	count++;
	if(!users.find(x=>x.Id==ctx.Id))users.push(ctx);
	console.log("open", ctx.Id, count, users.length);
}

function onMsg(ctx, msg){
	console.log("msg", msg);
	api.sendTo(users, msg);
}

function onClose(ctx, err){
	console.log("close",ctx.Id);
}
```
