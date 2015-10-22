###字节长度
```js
function bytelen(str) {
  return str.replace(/[^x00-xFF]/g,'**').length;
}
```  
  
