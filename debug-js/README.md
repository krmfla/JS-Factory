# debug.js

<b>功能描述</b>

在畫面上顯示trace的內容，或顯示error message

**cdn code**
```
https://krmfla.github.io/example/debug-js/debug.js
```

## 使用

<b>載入component</b>
```javascript
<script type="text/javascript" src="debug.js"></script>
```

<b>語法</b>
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

<b>計時器</b>
```javascript
debug.start(); //啟動計時器

debug.end(); //結算經過的時間
```

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

<b>Method</b>

Method        | Description
------------- | ------------------
log           | 印出追蹤訊息
start         | 啟動計時器
end           | 停止計時器，並計算經過時間(ms)
setBackground | 設定外層樣式
setItem       | 設定log message樣式

**已更新**

2017.5.3
- [x] 可自訂樣式(文字大小，顏色)
- [x] 可自訂父層位置
