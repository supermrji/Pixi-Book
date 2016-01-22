# 創建 Render 以及 Stage

**PIXI** 會自動產生 `canvas` 且將你的所有物件放在這個 `canvas` 上面
我們需要創建一個 `Container` 當作舞台容器，如果你有用過 `flash` 應該對這個名詞不陌生。

這個 Stage 是用來裝你產生的所有圖片、動畫......等元件，你可以把他想像成 `HTML` 中的最外層的 `Div`，這樣也許好理解一些。

## 第一種創建方式

#####JS
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

## 第二種創建方式

**HTML**
```html
<!doctype html>
<meta charset="utf-8">
<title>Hello World</title>
<body>
    <canvas id="main"></canvas>
    <script src="pixi.min.js"></script>
</body>
```

**Js**
```js
// 使用我們自創的 HTML Tag - canvas#main 
// 給予 256 X 256 的大小
var renderer = new PIXI.autoDetectRenderer(256, 256, {
            view: document.getElementById('main')
        }
    );
    
// 創建 Stage 
var stage = new PIXI.Container();

// 以 Render 去渲染 Stage
renderer.render(stage);
```

### 這時打開瀏覽器將會看到一塊黑色的 canvas 產生
### 因為我們什麼東西也沒建立，所以目前它只是一塊空的場景

![](01.png)

* `PIXI.autoDetectRenderer` 會去判斷瀏覽器是否支援 `WebGL` ，若是支援的話使用 `WebGL` Render ，反之則使用 `Canvas` Render 

    ```js
    // canvas 
    renderer = new PIXI.CanvasRenderer(256, 256);
    // webGL
    renderer = new PIXI.WebGLRenderer(256, 256);
    
    // PIXI 會自動判斷為這兩種 Render 的其中一種
    ```
    
* Render 就是一個渲染引擎，它會渲染你提供的 Stage (Container) ，後續我們會加入許多元件，也都是會放在這個 Stage 裡面
* 從**第二個創建方式**看到，`PIXI.autoDetectRenderer` 可以代入參數，以下是更多的參數設定。
```js    
    {
        view: document.getElementById('main'),
        antialias: false, 
        transparent: false, 
        resolution: 1
    }
    ```

* `antialias` 去除文字鋸齒，這個屬性是基於 WebGL ，但不是每個瀏覽器平台都完全支援這個屬性，所以若是有使用的話，最好要全面測試過，不支援或是支援度不好的話文字會很破。
* `transparent` 讓 canvas 背景透明，沒設定的話預設背景為黑色
* `resolution` 這個參數與瀏覽器的 pixel densities 相關，可以用來因應 retina 的調整，基本上沒有特殊需求的話，設為 1 就對了。如果想要了解更多可以參考這篇 [ Mat Grove's explanation](http://www.goodboydigital.com/pixi-js-v2-fastest-2d-webgl-renderer/)

#### 還有幾個未提到的參數，基本上我們用不到，如果想要更加了解請自行上網查詢


## 獲得屬性
`renderer` 是 PIXI 的渲染引擎


`renderer.view` 其實就是我們剛剛所創建的 canvas，
可以設定或是取得的屬性就如同一般的 **HTML Tag** 一樣
 
* 寬高
``` js
var w = renderer.view.width
var h = renderer.view.height
```
[ 重要提示 !! ] 這兩個屬性只是你的 canvas 寬高，跟你裡面的元件的寬高不相關，這裡只是跟你的瀏覽器講說你的 Canvas 容器有多大
白話點就是這個 HTML Tag 有多大，跟你 **Stage** 內容的寬高一點關係都沒有。

* resize
```js
renderer.autoResize = true;
renderer.resize(512, 512);
```
我們可以 resize renderer.view 的大小，但是要確保 retina 螢幕的解析能正常，所以將 `autoResize` 設為 `true`
* 設定背景色
```js 
renderer.backgroundColor = 0x061639;
```
