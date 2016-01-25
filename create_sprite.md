# 建立 Sprite

**[PIXI.Sprite](http://pixijs.github.io/docs/PIXI.Sprite.html)** 是 PIXI 中最重要的角色之一。

創建 Sprite 的方式有很多種

* **單一圖片檔案路徑**，這也是最基本的產生圖片方式
* **tileset 圖片** 類似 css sprites 的圖片使用方式，可用 [Texture Packer](https://www.codeandweb.com/texturepacker) 去產生 Json Hash 提供座標與縫圖

PIXI 使用 GPU 和 WebGL 來渲染圖片，圖片需要經過格式化 GPU 才能處理，一張處理好的 **WebGL-ready image** 我們稱為 **Texture** 

如果你有接觸過 3D 建模，這概念就像我今天建立了一個模型 **( PIXI.Sprite )**，這模型是素面的，需要再給它貼上貼圖 **( texture )** ，這才是一個完整的模型呈現，才是我們平常看到的一個人物／角色呈現。

### 所以記住這個觀念，**建立 Sprite ，給予貼圖**，就這麼簡單。

---

當我們從 [PIXI.loader](http://pixijs.github.io/docs/PIXI.loaders.Loader.html) 成功載入一張圖片後，圖片會被 PIXI 存成 **Texture Cache** 

如果你從資料夾載入了一張 `images/logo.png`
它將會被放到 Cache 裡面，而您要取用時便可以使用以下指令獲取

```js
PIXI.utils.TextureCache["images/logo.png"];
``` 

記住剛剛的口訣 「建模，上貼圖」，

```js
var texture = PIXI.utils.TextureCache["images/logo.pngg"];
var logo = new PIXI.Sprite(texture);
```

但現在問題來了，我們怎麼載入這些圖片？

根據上方講到的 **[PIXI.loader](http://pixijs.github.io/docs/PIXI.loaders.Loader.html) API** ，我們需要使用 PIXI 的載入器來將圖片做成 **Texture Cache**。

前往下一章節我們來了解 **[PIXI Loader](pixi_loader.md)**
