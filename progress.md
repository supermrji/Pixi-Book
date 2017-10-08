# 進度條

說到網頁就一定會有這個需求，監控是否將資源載入完畢後做初始化設定，所以 `PIXI.loader` 也提供了一個很強大的 **progress handler** 讓你在各種資源載入的時候可以監控進度，或是你想要在某個資源載入後優先做某些 loading 動畫等動作，都能從此 **API** 去達到。

```js
PIXI.loader
  .add([
    "images/one.png",
    "images/two.png",
    "images/three.png"
  ])
  .on("progress", loadProgressHandler)
  .load(init);

function loadProgressHandler() {
    console.log("loading"); 
}

function init() {
    console.log("init");
}
```

執行上方的程式碼的話可以得到

    loading
    loading
    loading
    init
    
**Progress Handler** 提供了兩個參數可供使用

```js
function loadProgressHandler(loader, resource) { //...
```

* 你可以利用這 `resource.url` 去得知某項資源是否載入完畢，如果你有指定名稱給某個載入檔案，可以使用 `resource.name` 去找尋您所要找尋的檔案資源

* 使用 `loader.progress` 去得到現在的載入進度百分比

```js
PIXI.loader
    .add([
        "images/one.png",
        "images/two.png",
        "images/three.png"
    ])
    .on("progress", loadProgressHandler)
    .load(init);

function loadProgressHandler(loader, resource) {

    // 顯示已載入的檔案路徑
    console.log("loading: " + resource.url); 
    
    // 顯示已載入資源百分比
    console.log("progress: " + loader.progress + "%"); 
    
    // 若是你在 add() 的時候有指定名稱
    // 可以使用下面這種方式來確認你指定的檔案已經載入完畢
    // console.log("loading: " + resource.name);
}

function init() {
    console.log("All files loaded");
}
```

以上的程式碼會得到

```js
    loading: images/one.png
    progress: 33.333333333333336%
    loading: images/two.png
    progress: 66.66666666666667%
    loading: images/three.png
    progress: 100%
    All files loaded
```

還有一些其它的資料如
* `resource.error` loading 發生錯誤時的資訊
* `resource.data` lets you access the file's raw binary data

###小技巧

如果要讓百分比整數呈現，可使用 

```js
console.log("progress: " + (loader.progress | 0) + "%");
``` 