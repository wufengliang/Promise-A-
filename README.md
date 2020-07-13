#### Promise A+ 规范

##### 定义我们的YPromise的，采用ES6写法

```
var p = new Promise((resolve,reject)=>{

})
```

##### 分析

    1.promise传入的参数必须为函数
    2.promise传入的参数为函数且该函数内为2个函数(resolve,reject)为promise内处理函数

#### 代码

```
class YPromise {
    constructor(exector) {
        this.value = null;
        this.status = YPromise.PENDING;
        this.initBind();
        this.init(exector);
    }

    initBind() {
        this.resolve = this.resolve.bind(this);
        this.reject = this.reject.bind(this);
    }

    init(exector) {
        if (typeof exector !== 'function') {
            throw new TypeError('an argument must be function');
        }
        exector(this.resolve, this.reject);
    }

    resolve() {

    }

    reject() {

    }
}

/**
 * 定义YPromise几个状态
 */
YPromise.PENDING = 'pending';
YPromise.FULFILLED = 'fulfilled';
YPromise.REJECTED = 'rejected';
```

