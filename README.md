# wsgo

### 底层为go，逻辑层js，轻松快速构建高性能WebSocket服务端。

#### 欢迎加入QQ群：739721147

#### app.js
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

#### 框架接口
```
//ctx
type Ctx struct {
	Conn *websocket.Conn
	Id   string
	Mode int
	Errs int
	Msg  string
	Info interface{}
}

//api
map[string]interface{}{
	"sendTo":   SendTo,
	"syncMap":  syncMap,
	"conns":    &conns,
	"syncDb":   &syncDb,
	"db":       &Db,
	"syncLock": &syncLock,

	"OS":      &kgo.KOS,
	"FS":      &kgo.KFile,
	"Date":    &kgo.KTime,
	"Encode":  &kgo.KEncr,
	"Convert": &kgo.KConv,
	"Array":   &kgo.KArr,
	"String":  &kgo.KStr,
	"Number":  &kgo.KNum,

	"getFile":  getFileStr,
	"saveFile": saveFile,
	"httpGet":  httpGet,
	"httpPost": httpPost,
}
```
##### 接口kgo工具库，请参考：https://github.com/kakuilan/kgo
