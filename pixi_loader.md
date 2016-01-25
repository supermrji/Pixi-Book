# PIXI Loader

[PIXI.Loader](http://pixijs.github.io/docs/PIXI.html#.loader) 是一個強大的工具，可以載入許多種類型的 **resources** 

* 圖片 **( png / jpg ... )**
* 音效 **( mp3 / ogg ... )**
* 影片 **( mp4 , webm ... ) **
* 字型 **( Bitmap font / Web font ... )**


經過 PIXI.Loader 處理後，讓我們很簡易的可以去使用各種包裝好的 **Texture Cache** 。

讓我們先來做一個最簡單的載入

```js
PIXI.loader
    .add('images/logo.png')
    .load(init);

function init() {
  // 這裡代表資源都已載入完畢，可以使用 'images/logo.png' 的 Texture Cache 了
}
```

在使用 Texture Cache 的方式有很多種

官方建議使用這種方式

```js
var sprite = new PIXI.Sprite(
    PIXI.loader.resources[“images/anyImage.png”].texture
);
```