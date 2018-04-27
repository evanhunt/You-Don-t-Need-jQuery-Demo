# @ `Query Selector`

常用的 `class`、`id`、属性 选择器都可以使用 `document.querySelector` 或 `document.querySelectorAll` 替代. 区别是
- `document.querySelector` 返回第一个匹配的 `Element`
- `document.querySelectorAll` 返回所有匹配的 `Element` 组成的 `NodeList`. 它可以通过 `[].slice.call()` 把它转成 `Array`
- 如果匹配不到任何 `Element`, `jQuery` 返回空数组 [], 但 `document.querySelector` 返回 `null`, 注意空指针异常. 当找不到时, 也可以使用 || 设置默认的值, 如 `document.querySelectorAll(selector) || []`

> 注意：`document.querySelector` 和 `document.querySelectorAll` 性能很差. 如果想提高性能, 尽量使用 `document.getElementById`、`document.getElementsByClassName `或 `document.getElementsByTagName`.

> 补充: 在现在硬件、软件、网络在高速发展的情况下查询性能可以忽略不计

## 选择器查询

```javascript
// jquery
$(selector);

// native
document.querySelectorAll('selector');
```

## `class` 查询

```javascript
// jquery
$('.class');

// native
document.querySelectorAll('.class');
document.getElementsByClassName('class');
```

## `id`查询

```javascript
// jquery
$('$id')

// native
document.querySelector('#id');
document.getelementById('id');
```

## 属性查询

```javascript
// jquery
$('a[target=_blank]');

// native
document.querySelectorAll('a[target=_blank]');
```

## 后代查询

```javascript
// jquery
$el.find('li');

// native
el.querySelectorAll('li');
```

## 兄弟及上下元素

#### 1.1 兄弟元素

```javascript
// jquery
$el.siblings();

// native - latest, Edge13+
[...el.parentNode.children].filter((child) => {
    child !== el;
});

// Native (alternative) - latest, Edge13+
Array.from(el.parentNode.children).filter((child) => {
    child !== el;
});

// Native - IE10+
Array.prototype.filter.call(el.parentNode, (child) => {
    child !== el;
});
```

#### 1.2 上一个元素

```javascript
// jquery
$el.prev();

// native
el.previousElementSibling;
```

#### 1.3 下一个元素

```javascript
// jquery
$el.next();

// native
el.nextElementSibling;
```

## `Closest`

`Closest` 获得匹配选择器的第一个祖先元素, 从当前元素开始沿 `DOM` 树向上.

```javascript
// jquery
$el.closest(queryString);
$el.closest(selector);

// native
function closest(el, selector){
    const matchesSelector = el.matches
                    || el.webkitMatchesSelector
                    || el.mozMatchesSelector || el.msMatchesSelector;
    while(el) {
        if (matchesSelector.call(el, selector)) {
            return el;
        } else {
            el = el.parentElement;
        }
    }
    return null;
}
```

## `Parents Until`

获取当前每一个匹配元素集的祖先, 不包括匹配元素的本身.

```javascript
// jquery
$el.parentsUntil(selector, filter);

// native
function parentsUntil(el, selector, filter) {
    const result = [];
    const matchesSelector = el.matches
                    || el.webkitMatchesSelector
                    || el.mozMatchesSelector || el.msMatchesSelector;
    el = el.parentElement;
    while(el && !matchesSelector.call(el, selector)) {
        if (!filter) {
            result.push(el);
        } else {
            if (matchesSelector.call(el, filter)) {
                result.push(el);
            }
        }
        el = el.parentElement;
    }
    return result;
}
```

## `Form`

```javascript
// jquery
$('#my-input').val();
$('.radio').index(e.currentTarget);

// native
document.querySelector('#my-input').value;
Array.prototype.indexOf.call(document.querySelectorAll('.radio'), e.currentTarget)
```

## `Iframe Contents`

`jQuery` 对象的 `iframe contents()` 返回的是 `iframe` 内的 `document`

```javascript
// jquery
$iframe.contents();
$iframe.contents().find('.css');

// native
iframe.contentDocument;
iframe.contentDocument.querySelectorAll('.css');
```

## 获取 `body`

```javascript
// jquery
$('body');

// native
document.body;
```

## 获取或设置属性

#### 1.1 获取属性

```javascript
// jquery
$el.attr('foo');

// native
el.getAttribute('foo');
```

#### 1.2 设置属性

```javascript
// jquery
$el.attr('foo', 'bar');

// native
el.setAttribute('foo', 'bar');
```

#### 1.3 获取 `data-` 属性

```javascript
// jquery
$el.data('foo');

// native
el.getAttribute('data-foo');
el.dataset['foo'];
```
