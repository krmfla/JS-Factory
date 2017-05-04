# debug.js

<b>功能描述</b>

在畫面上顯示trace的內容，或顯示error message

**cdn code**
```
https://krmfla.github.io/example/debug-js/debug.js
```

<br>

## 使用

<b>載入component</b>
```javascript
<script type="text/javascript" src="https://krmfla.github.io/example/debug-js/debug.js"></script>
```
<br>

<b>語法</b>
```javascript
var debug;
document.addEventListener("DOMContentLoaded", function() {
  debug = new Debug;
  debug.log("TRACE MESSAGE");
});
```

預設會將trace message的外層，貼於body tag上

若要指定位置，需帶入DOM物件的id
```javascript
var debug = new Debug("ELEMENT_ID");
```

<br>

<b>計時器</b>
```javascript
debug.start(); //啟動計時器

debug.end(); //結算經過的時間

// print
// >>> Timer Start >>>
// >>> process: 1594ms >>>
```

<br>

<b>自定義樣式</b>

外層
```javascript
//外層
debug.setBackground({ CONFIG_OBJECT });

//example
debug.setBackground({
  "background": "black",
  "opacity":.8
})

//內容文字
debug.setItem({ CONFIG_OBJECT });

//example
debug.setItem({
  "color": "green",
  "fontSize": "12px"
})
```

<br>

<b>Error Handle</b>

當程式發生錯誤時，會印出log
```
Error: Uncaught ReferenceError: ttt is not defined
Script: main.js
Line: 62
```

也可以自訂Error Handle
```javascript
window.onerror = function(errorMsg, url, lineNumber) {
  debug.log('Error: ' + errorMsg);
  debug.log('Script: ' + url);
  debug.log('Line: ' + lineNumber);
  //...
}
```


<b>Method</b>

Method         | Description
-------------- | ------------------
log            | 印出追蹤訊息
start          | 啟動計時器
end            | 停止計時器，並計算經過時間(ms)
setBackground  | 設定外層樣式
setItem        | 設定log message樣式

<br>

<b>已更新</b>

2017.5.3
- [x] 可自訂樣式(文字大小，顏色)
- [x] 可自訂父層位置

<b>待更新</b>
