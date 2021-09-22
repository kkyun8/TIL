# JSでImageObject操作

```javascript
const div = document.createElement('div')
// create image
const image = new Image()
image.src = url // file url

div.appendChild(image); 
// こんなdomができる→ <div><img src="image/5.gif"></div>
```


