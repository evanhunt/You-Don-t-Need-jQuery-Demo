# @ `Promises`

`Promise` 代表异步操作的最终结果. `jQuery` 用它自己的方式处理 `promises`, 原生 `JavaScript` 遵循 `Promises/A+` 标准实现了最小 `API` 来处理 `promises`.


## `done, fail, always`

`done` 会在 `promise` 解决时调用, `fail` 会在 `promise` 拒绝时调用, `always`总会调用.

```javascript
// jquery
$promise
    .done(doneCallback)
    .fail(failCallback)
    .always(alwaysCallback);

// native
promise
    .then(doneCallback, failCallback)
    .then(alwaysCallback, alwaysCallback);
```

## `when`

`when` 用于处理多个 `promises`. 当全部 `promises` 被解决时返回, 当任一 `promise` 被拒绝时拒绝.

```javascript
// jquery
$.when($promise1, $promise2)
    .done((promise1Result, promise2Result) => {

    });

// native
Promise.all([promise1, promise2])
    .then(([promise1Result, promise2Result]) => {

    });
```

## `Deferred`

`Deferred` 是创建 `promises` 的一种方式.

```javascript
// jquery
function asyncFunc() {
    const defer = new $.Deferred();
    setTimeout(() => {
        if(true) {
            defer.resolve('some_value_computed_asynchronously');
        } else {
            defer.reject('failed');
        }
    }, 1000);

    return defer.promise();
}

// native
function asyncFunc() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (true) {
                resolve('some_value_computed_asynchronously');
            } else {
                reject('failed');
            }
        }, 1000);
    });
}

function defer() {
    const deferred = {};
    const promise = new Promise((resolve, reject) => {
        deferred.resolve = resolve;
        deferred.reject = reject;
    });

    deferred.promise = () => {
        return promise;
    };

    return deferred;
}

function asyncFunc() {
    const defer = defer();
    setTimeout(() => {
        if(true) {
            defer.resolve('some_value_computed_asynchronously');
        } else {
            defer.reject('failed');
        }
    }, 1000);

    return defer.promise();
}
```
