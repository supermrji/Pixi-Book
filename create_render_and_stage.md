# 創建 Render 以及 Stage

**PIXI** 會自動產生 `canvas` 且將你的所有物件放在這個 `canvas` 上面
我們需要創建一個 `Container` 當作舞台容器，如果你有用過 `flash` 應該對這個名詞不陌生。

這個 Stage 是用來裝你產生的所有圖片、動畫......等元件，你可以把他想像成 `HTML` 中的最外層的 `Div`，這樣也許好理解一些。

### 第一種創建方式
```js
// 創一個 Render 自動判斷是否有 webGL
var renderer = PIXI.autoDetectRenderer(256, 256);

// 新增至頁面
document.body.appendChild(renderer.view);

// 創建 Stage 
var stage = new PIXI.Container();

// 以 Render 去渲染 Stage
renderer.render(stage);
```

### 第二種創建方式

```html

```

* `PIXI.autoDetectRenderer` 會去判斷瀏覽器是否支援 `WebGL` ，若是支援的話使用 `WebGL` Render ，反之則使用 `Canvas` Render ，這一切都是 PIXI 幫你自動處理好的。
* 

