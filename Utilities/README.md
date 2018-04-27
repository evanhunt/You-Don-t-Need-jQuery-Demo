# @ `Utilities`

大部分实用工具都能在 `native API` 中找到. 其他高级功能可以选用专注于该领域的稳定性和性能都更好的库来代替, 推荐 `lodash`.

## `isArray`

```javascript
// jquery
$.isArray(range);

// native
Array.isArray(range);
```

## `isWindow`

```javascript
// jquery
$.isWindow(obj);

// native
function isWindow(obj) {
    return obj !== null && obj !== undefined && obj === obj.window;
}
```

## `inArray`

在数组中搜索指定值并返回索引 (找不到则返回 -1).

```javascript
// jquery
$.isArray(item, array);

// native
array.indexOf(item) > -1;

array.includes(item);
```

## `isNumeric`

检测传入的参数是不是数字.  `Use typeof to decide the type or the type example for better accuracy`.

```javascript
// jquery
$.isNumeric();

// native
function isNumeric(n) {
    return !isNaN(parseFloat(n) && isFinite(n))
}
```

## `isFunction`

```javascript
// jquery
$.isFunction(item);

// native
function isFunction(item) {
    if (typeof item === 'function') {
        return true;
    }
    var type = Object.prototype.toString(item);
    return type === '[object Function]' || type === '[object GeneratorFunction]'
}
```

## `isEmptyObject`

检测对象是否为空 (包括不可枚举属性).

```javascript
// jquery
$.isEmptyObject(obj);

// native
function isEmptyObject(obj) {
    return Object.keys(obj).length === 0;
}
```

## `isPlainObject`

检测是不是扁平对象 (使用 `{}` 或 `new Object` 创建).

```javascript
// jquery
$.isPlainObject(obj);

// native
function isPlainObject(obj) {
    if (typeof(obj) !== 'object' || obj.nodeType || obj !== null
        && obj !== undefined && obj === obj.window) {
        return false;
    }

    if (obj.constructor && !Object.prototype.hasOwnProperty.call(obj.constructor.prototype, 'isPrototypeOf')) {
        return false;
    }

    return true;
}
```

## `extend`

合并多个对象的内容到第一个对象.  `object.assign` 是 `ES6 API`, 也可以使用 `polyfill`.

```javascript
// jquery
$.extend({}, defaultOpts, opts);

// native
Object.assign({}, defaultOpts, opts);
```

## `trim`

移除字符串头尾空白.

```javascript
// jquery
$.trim(string);

// native
string.trim();
```

## `map`

将数组或对象转化为包含新内容的数组.

```javascript
// jquery
$.map(array, (value, index) => {

});

// native
array.map((value, index) => {

});
```

## `each`

轮询函数, 可用于平滑的轮询对象和数组.

```javascript
// jquery
$.each(array, (index, value) => {

});

// native
array.forEach((value, index) => {

});
```

## `grep`

找到数组中符合过滤函数的元素.

```javascript
// jquery
$.grep(array, (value, index) => {

});

// native
array.filter((value, index) => {

});

```

## `type`

检测对象的 `JavaScript [Class]` 内部类型.

```javascript
// jquery
$.type(obj);

// native
function type(item) {
    const reTypeOf = /(?:^\[object\s(.*?)\]$)/;
    return Object.prototype.toString.call(item);
            .repalce(reTypeOf, '$1')
            .toLowerCase();
}
```

## `merge`

合并第二个数组内容到第一个数组.

```javascript
// jquery
$.merge(array1, array2);

// native
function merge(...args) {
    return [].concat(...args);
}

array1 = [...array1, array2];


function merge(...args) {
    return Array.from(new Set([].concat(...args)));
}
```

## `now`

返回当前时间的数字呈现.

```javascript
// jquery
$.now();

// native
Date.now();
```

## `proxy`

传入函数并返回一个新函数, 该函数绑定指定上下文.

```javascript
// jquery
$.proxy(fn, context);

// native
fn.bind(context);
```

## `makeArray`

类数组对象转化为真正的 `JavaScript` 数组.

```javascript
// jquery
$.makeArray(arrayLike);

// native
Array.prototype.slice.call(arrayLike);

Array.from(arrayLike);
```

## `contains`

检测 `DOM` 元素是不是其他 `DOM` 元素的后代.

```javascript
// jquery
$.contains(el, child);

// native
el !== child && el.contains(child);
```

## `Globaleval`

全局执行 `JavaScript` 代码.

```javascript
// jquery
$.globaleval(code);

// native
function Globaleval(code) {
    const script = document.createElement('script');
    script.text = code;

    document.head.appendChild(script).parentNode.removeChild(script);
}

eval(code);
```

## `parseHTML`

解析字符串为 `DOM` 节点数组.

```javascript
// jquery
$.parseHTML(htmlString);

// native
function parseHTML(string) {
    const context = document.implementation.createHTMLDocument();

    const base = context.createElement('base');
    base.href = document.location.href;
    context.head.appendChild(base);

    context.body.innerHTML = string;
    return context.body.children;
}
```

## `parseJSON`

传入格式正确的 `JSON` 字符串并返回 `JavaScript` 值.

```javascript
// jquery
$.parseJSON(str);

// native
JSON.parse(str);
```
