# @ `CSS & Style`

## `css`

#### 1.1 `Get Style`

```javascript
// jquery
$el.css('color');

// native
const win = el.ownerDocument.defaultView;
win.getComputedStyle(el, null).color;
```

#### 1.2 `Set style`

```javascript
// jquery
$el.css({ color: '#ff0011' });

// native
el.style.color = '#ff0011';
```

#### 1.3 `Get/Set Styles`

注意, 如果想一次设置多个 `style`, 可以参考 `oui-dom-utils` 中 `setStyles` 方法

#### 1.4 `Add class`

```javascript
// jquery
$el.addClass(className);

// native
el.classList.add(className);
```

#### 1.5 `Remove class`

```javascript
// jquery
$el.removeClass(className);

// native
el.classList.remove(className);
```

#### 1.6 `has class`

```javascript
// jquery
$el.hasClass(className);

// native
el.classList.contains(className);
```

#### 1.7 `Toggle class`

```javascript
// jquery
$el.toggleClass(className);

// native
```

## `Width & Height`

Width 与 Height 获取方法相同, 下面以 Height 为例:

#### `Window height`

```javascript
// jquery
$(window).height();

// native
window.document.documentElement.clientHeight;
window.innerHeight;
```

#### `Document height`

```javascript
// jquery
$(document).height();

// native
const body = document.body;
const html = document.documentElement;
const height = Math.max(
    body.offsetHeight,
    body.scrollHeight,
    html.clientHeight,
    html.offsetHeight,
    html.scrollHeight,
);
```

#### `Element height`

```javascript
// jquery
$el.height();

// native
function getHeight(el) {
    const styles = this.getComputedStyle(el);
    const height = el.offsetHeight;
    const borderTopWidth = parseFloat(styles.borderTopWidth);
    const borderBottomWidth = parseFloat(styles.borderBottomWidth);
    const paddingTop = parseFloat(styles.paddingTop);
    const paddingBottom = parseFloat(styles.paddingBottom);
    return height - borderTopWidth - borderBottomWidth - paddingTop - paddingBottom;
}

// 精确到整数（border-box 时为 height - border 值, content-box 时为 height + padding 值）
el.clientHeight;

// 精确到小数（border-box 时为 height 值, content-box 时为 height + padding + border 值）
el.getBoundingClientRect().height;
```

## `Position & Offset`

#### `Position`

```javascript
// jquery
$el.position();

// native
{
    left: el.offsetLeft,
    top: el.offsetTop,
}
```

#### `Offset`

```javascript
// jquery
$el.offset();

// native
function getOffset(el) {
    const box = el.getBoundingClientRect();

    return {
        top: box.top + window.pageYOffset - document.documentElement.clientTop,
        left: box.left + window.pageXOffset - document.documentElement.clientLeft,
    };
}
```

#### `Scroll Top`

```javascript
// jquery
$(window).scrollTop();

// native
(document.documentElement && document.documentElement.scrollTop) || document.body.scrollTop;
```
