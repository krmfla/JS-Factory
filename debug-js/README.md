# debug.js

<b>功能描述</b>

在畫面上顯示trace的內容，或顯示error message

**cdn code**
```
https://krmfla.github.io/example/debug-js/debug.js
```

<b>使用</b>

載入component
```javascript
<script type="text/javascript" src="debug.js"></script>
```
語法
```javascript
var debug;
document.addEventListener("DOMContentLoaded", function(event) {
  debug = new Debug;
  debug.log("TRACE MESSAGE");
});
```

預設會將trace message，貼於body tag上

若要指定位置，則代入DOM物件的id
```javascript
var debug = new Debug("ELEMENT_ID");
```

<b>Method</b>

Method | Description
------ | ---
log    | 印出追蹤訊息
time   | 啟動計時器
end    | 停止計時器，並計算經過時間(ms)

**預計更新**
- [x] 可自訂樣式(文字大小，顏色)
- [x] 可自訂父層位置
