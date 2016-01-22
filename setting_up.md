# Setting Up

### 設定

在寫程式之前，讓我們先把最新版的 **pixi.js** [( Pixi's GitHub Repo )](https://www.codeandweb.com/texturepacker) 載入 

```js
<script src="pixi.min.js"></script>
```

簡單的基本架構

```html
<!doctype html>
<meta charset="utf-8">
<title>Hello World</title>
<body>
    <script src="pixi.min.js"></script>
    <script>
    
    //Test that Pixi is working
    console.log(PIXI);
    
    </script>
</body>
```
    
如果正確載入了

```js
console.log(PIXI);
```

你應該會得到

```js
Object {VERSION: "3.0.8" ...
```