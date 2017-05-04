# FirebaseLog.js

<b>功能描述</b>

利用firebase做紀錄追蹤的功能

<br>

<b>引入</b>

在firebase上建立專案後，透過API引入

設定 > 一般 > 將 Firebase 加入您的網路應用程式

![banner](https://github.com/krmfla/JS-Factory/blob/master/firebaseLog-js/setting.jpg "Firebase")

```html
<!-- 引入firebase.js及project config -->
<script src="https://www.gstatic.com/firebasejs/3.6.4/firebase.js"></script>
<script>
  // Initialize Firebase
  var config = {
    apiKey: APIKEY,
    authDomain: AUTH_DOMAIN, 
    databaseURL: DATABASE_URL,
    storageBucket: STORAGE_BUCKET,
    messagingSenderId: MESSAGING_SENDER_ID
  };
  firebase.initializeApp(config);
</script>
```

<br>

firebaseLog.js CDN Code
```html
<script src="https://krmfla.github.io/example/firebaseLog-js/FirebaseLog.js"></script>
```

<br>

<b>使用</b>

語法

```javascript
//trace message
FirebaseLog.log("TRACE_MESSAGE", "DATA_KEY");

//set/rewrite data 
FirebaseLog.set("TRACE_MESSAGE", "DATA_KEY");

//remove data
FirebaseLog.remove("DATA_KEY");
```

TRACE_MESSAGE可以是字串、數值、陣列、物件...

<br>

Method

Method | Description
------ | -----------
log    | 將紀錄存於firebase中 <br> 若未定義DATA_KEY，會自動產生一組<br>資料會以寫入時間排序
set    | 將新的資料寫入或覆蓋掉舊有資料
remove | 將firebase中的紀錄刪除

<br>

<b>data type</b>

```javascript
 FirebaseLog.log("message");
 
 // PROJECT_NAME
 //   └ RANDOM_CHARACTER_KEY
 //       └ LOG_TIME : "message"
```

<br>

```javascript
FirebaseLog.log("message", "A1");

 // PROJECT_NAME
 //   └ A1
 //      └ LOG_TIME : "message"
```
<br>

```javascript
 FirebaseLog.set("message", "A2");
 
 // PROJECT_NAME
 //   └ A2 : "message"
```
