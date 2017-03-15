# toast.js

**功能描述**

在畫面上呈現提示訊息的效果

**原理**

設定進場及退場的style狀態後，使用css transition或javascript做漸變效果

<br />

**使用**

引入toast.css樣式及toast.js模組

```javascript
<link rel="stylesheet" href="toast.css">
<script type="text/javascript" src="toast.js"></script>
```
語法

```javascript
var toast = new Toast("YOUR TEXT", CONFIG-OBJECT);
toast.short();
toast.long();
toast.closeMe();
```
CONFIG-OBJECT(optional)
```javascript
var config = {
  "targetEl": "ELEMNET ID",            //要將提示訊息貼到哪個DOM id上
  "style": "STYLE",                    //可使用預設的style: "slide"或"fadeInOut"
  "inState": {                         //進入效果
    "PROPERTY": "VALUE"
  },
  "outState": {                        //退出效果
    "PROPERTY": "VALUE"
  },
  "speed": DURATION(millisecond),      //動畫速率
  "shortTime": DURATION(millisecond),  //自定出現時間長度(短)
  "longTime": DURATION(millisecond)    //自定出現時間長度(長)
};
```

Methods

Method  | Description
------- | ---
short	| 出現提示訊息(停留較短, 預設為3秒)
long	| 出現提示訊息(停留較短, 預設為6秒)
closeMe | 立即結束提示效果

<br />

**範例**
```javascript
//使用預設效果
var toast = new Toast("Welcome!");

//使用自定效果
var configData = {
  "targetEl": "main",
  "style": null,
	"inState": {
    "left": "50%",
    "bottom": "20px",
  },
  "outState": {
    "left": "-50%",
    "bottom": "-50px",
  },
  "speed": 24,
  "shortTime": 3000,
  "longTime": 6000
};
var toast = new Toast("Welcome!", configData);
```

<br />

**DEMO:**

https://krmfla.github.io/example/toast-js/index.html

<br />

**預計更新**
- [ ] 單體模式
- [ ] 可置換文字內容及設定檔
- [ ] 多任務排程
