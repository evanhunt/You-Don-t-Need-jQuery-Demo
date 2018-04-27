# @ `Ajax`

`Fetch API` 是用于替换 `XMLHttpRequest` 处理 `ajax` 的新标准, `Chrome` 和 `Firefox` 均支持, 旧浏览器可以使用 `polyfills` 提供支持.

`IE9+` 请使用 `github/fetch`, `IE8+` 请使用 `fetch-ie8`, `JSONP` 请使用 `fetch-jsonp`. 


```javascript
// jquery
$(selector).load(url, completeCallback)

// native
// fetch(url).then(data => data.text()).then(data => {
  document.querySelector(selector).innerHTML = data
}).then(completeCallback)
```
