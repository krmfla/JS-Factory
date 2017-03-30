# FirebaseLog.js

<b>功能描述</b>

利用firebase做紀錄追蹤的功能

<b>使用</b>

引入

```html
<!-- 引入firebase.js及project config -->
<!-- 設定 > 一般 > 將 Firebase 加入您的網路應用程式 -->
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

<!-- cdn code -->
<script src="https://krmfla.github.io/example/firebaseLog-js/FirebaseLog.js"></script>
```
語法

```javascript
//trace message
FirebaseLog.log("TRACE_TEXT", "DATA_LOCATION");

//remove data
FirebaseLog.remove("DATA_LOCATION");
```

Method

Method | Description
------ | -----------
log    | 將紀錄存於firebase中 <br /> 若未定義DATA_LOCATION，會自動產生一組key
remove | 將firebase中的紀錄刪除
