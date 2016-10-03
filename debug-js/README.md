#debug.js

<b>功能描述</b>

在畫面上顯示trace的內容，或顯示error message

<b>cdn code</b>
```
https://krmfla.github.io/example/debug-js/debug.js
```

<b>使用</b>

語法
```javascript
<script type="text/javascript" src="debug.js"></script>

var debug;
document.addEventListener("DOMContentLoaded", function(event) {
  debug = new Debug;
  debug.log("TRACE MESSAGE");
  debug.time();
  debug.end();
});
```

Method

Method | Description
------ | ---
log    | 印出追蹤訊息
time   | 啟動計時器
end    | 停止計時器，並計算經過時間(ms)

<b>預計更新</b>
- [ ] 可自訂樣式(文字大小，顏色)
- [ ] 可自訂父層位置
