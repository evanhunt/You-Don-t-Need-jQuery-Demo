# `DOM Manipulation`

## `Remove`

```javascript
// jquery
$el.remove();

// native
el.parentNode.removeChild(el);
```

## `Text`

#### `get text`

返回指定元素及其后代的文本内容.

```javascript
// jquery
$el.text();

// native
el.textContent;
```

#### `set text`

```javascript
// jquery
$el.text(string);

// native
el.textContent = string;
```

## `HTML`

#### `get html`

```javascript
// jquery
$el.html();

// native
el.innerHTML;
```

#### `set html`

```javascript
// jquery
$el.html(htmString);

// native
el.innerHTML = htmString;
```

## `Append`

Append 插入到子节点的末尾

```javascript
// jquery
$el.append('<div>hello</div>');

// native
el.insertAdjacentHTML('feforeend', '<div>hello</div>');

el.appendChild(newEl);
```

## `Prepend`

```javascript
// jquery
$el.prepend('<div>hello</div>');

// native
el.insertAdjacentHTML('afterbegin', '<div>hello</div>');

el.insertBefore(newEl, el.firstChild);
```

## `insertBefore`

在选中元素前插入新节点

```javascript
// jquery
$newEl.insertBefore(queryString);

// native
el.insertAdjacentHTML('beforebegin', '<div>hello</div>');

const el = document.querySelector(selector);
if (el.parentNode) {
    el.parentNode.insertBefore(newEL, el);
}
```

## `insertAfter`

在选中元素后插入新节点

```javascript
// jquery
$el.insertAfter(queryString);

// native
el.insertAdjacentHTML('afterend', '<div>hello</div>');

const el = document.querySelector(selector);
if (el.parentNode) {
    el.parentNode.insertBefore(newEL, el.nextSibling);
}
```


## `is`

如果匹配给定的选择器，返回true

```javascript
// jquery
$el.is(selector);

// native
el.matches(selector);
```

## `clone`

深拷贝被选元素. (生成被选元素的副本，包含子节点、文本和属性. )

```javascript
// jquery
$el.clone();

// native
el.cloneNode();
```

## `empty`

移除所有子节点

```javascript
// jquery
$el.empty();

// native
el.innerHTML = '';
```

## `wrap`

把每个被选元素放置在指定的HTML结构中.

```javascript
// jquery
$el.wrap('<div></div>');

// native
Array.prototype.forEach.call(document.querySelector(el), (el) => {
    const wrapper = document.createElement('div');
    wrapper.className = 'wrapper'
    el.parentNode.insertBefore(wrapper, el);
    el.parentNode.removeChild(el);
    wrapper.appendChild(el);
});
```

## `unwrap`

移除被选元素的父元素的DOM结构

```javascript
// jquery
$(el).unwrap();

// native
Array.prototype.forEach.call(document.querySelector(el), (el) => {
    let elParentNode = el.parentNode;

    if (elParentNode !== document.body) {
        elParentNode.parentNode.insertBefore(el, elParentNode);
        elParentNode.parentNode.removeChild(elParentNode);
    }
});
```


## `replaceWith`

用指定的元素替换被选的元素

```javascript
// jquery
$el.replaceWith('<div>hello</div>');

// native
Array.prototype.forEach.call(document.querySelectorAll('.inner'), () => {
    const outer = document.createElement('div');
    outer.className = 'outer';
    el.parentNode.insertBefore(outer, el);
    el.parentNode.removeChild(el);
});
```
