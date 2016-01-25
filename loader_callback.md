# 個別載入 callback

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

**normal syntax**

```js
.add('logo', 'http://...', function () {})
// or
.add('http://...', function () {})
// or
.add('http://...')
```

**object syntax**

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

