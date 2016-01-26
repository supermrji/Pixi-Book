# 更多設定

`.add()` 有四個參數可供使用

```js
PIXI.loader.add(name, url, option, callback)
```

* `name` **( string )** : 被載入的檔案命名，如果沒有這個參數，則等同於使用 `url`
* `url` **(string)必填** :  來源路徑，基於 loader 中的 `baseUrl`
* `option` **( object )** : 
    * `options.crossOrigin` **( Boolean )** : 是否跨網域？預設為自動判斷
    * `options.loadType` : 來源要用什麼模式載入，預設為 `Resource.LOAD_TYPE.XHR` 
    * `options.xhrType` :  使用 **XHR** 時如何解析來源資料 ? 預設為 `Resource.XHR_RESPONSE_TYPE.DEFAULT`
    
* `callback` **( function )** : 載入完成此資源的動作

以下有幾種使用 `add` 的方式

###**normal syntax**

```js
.add('logo', 'http://...', function () {})
// or
.add('http://...', function () {})
// or
.add('http://...')
```

###**object syntax**

```js
.add({
    name: 'key2',
    url: 'http://...'
}, function () {})

// or
.add({
    url: 'http://...'
}, function () {})

// or
.add({
    name: 'key3',
    url: 'http://...'
    onComplete: function () {}
})

// or
.add({
    url: 'https://...',
    onComplete: function () {},
    crossOrigin: true
})
```
很特別的，也可以大雜燴混著用

```js
.add([
    {name: 'key4', url: 'http://...', onComplete: function () {} },
    {url: 'http://...', onComplete: function () {} },
    'http://...'
]);
```

### **Reset**
如果你需要做不同的載入序列就需要使用 `reset` function

例如：你想要載入完一個檔案播放動畫，然後再跑進度條百分比，你必須在第一個 resource 載入完成後執行一次


    PIXI.loader.reset();

這樣可以清除剛剛暫存的序列，確保我們要的 **loading progress** 從 **0** 開始。

PIXI loader 有許多進階設定，讓你的各種類型檔案載入，但這些官方都幫你做好了，你只要定期去看官方文件獲取更多資訊。

>Pixi's loader has many more advanced features, including options to let you load and parse binary files of all types. This is not something you'll need to do on a day-to-day basis, and way outside the scope of this tutorial, so [make sure to check out the loader's GitHub repository for more information](https://github.com/englercj/resource-loader).