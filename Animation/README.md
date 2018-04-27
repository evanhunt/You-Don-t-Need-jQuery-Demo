# @ `Animation`

## `Show & Hide`

```javascript
// jquery
$el.show();
$el.hide();

// native
el.style.display = '' | 'inline' | 'inline-block' | 'inline-table' | 'block';
el.style.display = 'none';
```

## `Toggle`

显示或隐藏元素.

```javascript
// jquery
$el.toggle();

// native
if (el.ownerDocument.defaultView.getComputedStyle(el, null).display === 'none') {
    el.style.display = ''|'inline'|'inline-block'|'inline-table'|'block';
} else {
    el.style.display = 'none';
}
```

## `FadeIn & FadeOut`

```javascript
// jquery
$el.FadeIn(3000);
$el.FadeOut(3000);

// native
el.style.transition = 'opacity 3s';
// fadeIn
el.style.opacity = '1';
// fadeOut
el.style.opacity = '0';
```

## `FadeTo`

调整元素透明度.

```javascript
// jquery
$el.fadeTo('slow',0.15);

// native
el.style.transition = 'opacity 3s'; // 假设 'slow' 等于 3 秒
el.style.opacity = '0.15';
```

## `FadeToggle`

动画调整透明度用来显示或隐藏.

```javascript
// jquery
$el.fadeToggle();

// native
el.style.transition = 'opacity 3s';
const { opacity } = el.ownerDocument.defaultView.getComputedStyle(el, null);
if (opacity === '1') {
    el.style.opacity = '0';
} else {
    el.style.opacity = '1';
}
```

## `SlideUp & SlideDown`

```javascript
// jquery
$el.slideUp();
$el.slideDown();

// native
const originHeight = '100px';
el.style.transition = 'height 3s';
// slideUp
el.style.height = '0px';
// slideDown
el.style.height = originHeight;
```

## `SlideToggle`

滑动切换显示或隐藏.

```javascript
// jquery
$el.slideToggle();

// native
const originHeight = '100px';
el.style.transition = 'height 3s';
const { height } = el.ownerDocument.defaultView.getComputedStyle(el, null);
if (parseInt(height, 10) === 0) {
    el.style.height = originHeight;
} else {
    el.style.height = '0px';
}
```

## `Animate`

执行一系列 `CSS` 属性动画. 

```javascript
// jquery
$el.animate({ params }, speed);

// native
el.style.transition = 'all ' + speed;
Object.keys(params).forEach((key) =>
    el.style[key] = params[key];
)
```
