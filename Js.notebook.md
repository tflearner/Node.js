# Js.notebook

####实现定时器

- 超时时间

setTimeout(callback,delayMilliSeconds,[args])

```setTimeout(myFunction,1000);```

setTimeout()返回定时器对象的ID，可以在delayMilliSeconds到期前使用clearTimeout(TimeoutID)取消超时时间函数

```javascript
myTimeout = setTimeout(myFunction,1000);
...
clearTimeout(myTimeout);
```

```javascript
// 启动计时器
console.time('testForEach');

// (写一些测试用代码)

// 停止计时，输出时间
console.timeEnd('testForEach');

// 4522.303ms
```

- 时间间隔

setInterval(callback,delayMilliSeconds,[args])

```setInterval(myFunction,1000);```

```javascript
MyInterval = setInterval(myFuction,1000);
...
clearInterval(myInterval);
```

- 即时计时器

它用来在I/O事件的回调函数开始执行后，但任何超时时间或时间间隔事件被执行之前，立即执行工作。

```setImmediate(myFunc(),1000);```

- 从事件循环中取消定时器引用

```javascript
myInterval = setInterval(myFunction);
myInterval.unref();
```

```myInterval.ref()```

####使用nextTick调度工作

nextTick在I/O事件被触发前执行

#### 实现事件发射器和监听器

- 将自定义事件添加到JavaScript对象

事件使用events模块中EventEmitter对象发出

```javascript
var events = require('events');
var emitter = new events.EventEmitter();
emitter.emit("simpleEvent")
```

或者把事件添加到JavaScript对象，需要通过在对象实例中调用events.EventEmitter.call(this)来集成EventEmitter功能。还需要把events.EventEmitter.prototype添加到对象的原型中

```javascript
Function MyObj(){
  Events.EventEmitter.call(this);
}
MyObj.prototype.__proto__ = events.EventEmitter.prototype;
//然后就可以直接从对象实例中发出事件
var myObj = new MyObj();
myObj.emit("Some Event");
```

- 将事件监听器添加到对象

```javascript
function myCallback(){
  ...
}
var myObject = newMyObj();
myObject.on("SomeEvent",myCallback);
//.addListener(eventName,callback)
//.on(eventName,callback)
//.once(eventName,callback)
```

- 从对象中删除监听器

```javascript
.listeners(eventName)//返回一个连接到eventName事件的监听器函数的数组
.setMaxListeners(n)//如果多余n的监听器加入到EventEmitter对象，就触发警报。默认值是10
.removeListener(eventName,callback)//将callback函数从EventEmitter对象的eventName事件中删除
```












