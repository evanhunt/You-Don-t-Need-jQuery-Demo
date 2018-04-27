# @ `Events`

完整地替代命名空间和事件代理，链接到 https://github.com/oneuijs/oui-dom-events

## `Document ready by DOMContentLoaded`

```javascript
// jquery
$(document).ready(eventHandler);

// native
if (document.readyState !== 'loading') {
    eventHandler();
} else {
    document.addEventListener('DOMContentLoaded', eventHandler);
}
```

## 使用 `on` 绑定事件

```javascript
// jquery
$el.on(eventName, eventHandler);

// native
el.addEventListener(eventName, eventHandler);
```

## 使用 `off` 解绑事件

```javascript
// jquery
$el.off(eventName, eventHandler);

// native
el.removeEventListener(eventName, eventHandler);
```

## `Trigger`

```javascript
// jquery
$(el).trigger('custom-event', {
    key1: 'data',
});

// native
if (window.CustomEvent) {
    const event = new CustomEvent('custom-event', {
        detail: {
            key1: 'data',
        },
    });
} else {
    const event = document.createEvent('CustomEvent');
    event.initCustomEvent('custom-event', true, true, {
        key1: 'data',
    });
}

el.dispatchEvent(event);
```
