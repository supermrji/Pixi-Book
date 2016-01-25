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
    


```js
function loadProgressHandler(loader, resource) { //...
```