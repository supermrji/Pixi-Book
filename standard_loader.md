# 基本 loader

讓我們先來做一個最簡單的載入

```js
PIXI.loader
    .add('images/logo.png')
    .load(init);

function init() {
  // 這裡代表資源都已載入完畢，可以使用 'images/logo.png' 的 Texture Cache 了
}
```

在使用 **Texture Cache** 的方式有很多種

官方建議使用這種方式，[可參考這篇](http://www.html5gamedevs.com/topic/16019-preload-all-textures/#comment-90907)

```js
PIXI.loader
    .add("images/logo.png")
    .load(init);

function init() {
    var sprite = new PIXI.Sprite(
        PIXI.loader.resources["images/logo.png"].texture // get Texture Cache
    );
}
```
也可使用
```js
var sprite = new PIXI.Sprite(
    PIXI.Texture.fromImage("images/logo.png"); // get Texture Cache
);

// or 
var sprite = new PIXI.Sprite(
    PIXI.utils.TextureCache["images/logo.png"]
);
```

不管在哪裡使用以上這些方法，都要確保是在 `PIXI.loader.load()` 執行完畢才能使用，否則資源尚未載入完畢會發生錯誤。

載入多項資源

```js
PIXI.loader
    .add([
        "images/imageOne.png",
        "images/imageTwo.png",
        "images/imageThree.png"
    ])
    .load(init);
```

你也可以指定名稱給你所載入的 **resource**

```js
PIXI.loader
  .add("logo", "images/logo.png")
  .load(init);
 
function init() {
    // 以指定名稱的方式去取用 Texture Cache
    var sprite = new PIXI.Sprite(PIXI.loader.resources.logo.texture);;
}
```

指定名稱可以讓你對某些 Texture 快速處理，但是你必須要記住所有的命名，在寫程式的過長中上算是不小的負擔，我們在之後的幾個範例中會有更多使用建議。
