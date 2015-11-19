###字节长度
```js
function bytelen(str) {
  return str.replace(/[^x00-xFF]/g,'**').length;
}
```  
###JQuery.url
https://github.com/allmarkedup/purl/blob/master/purl.js
> url = $.url("http://markdown.com/awesome/language/markdown.html?show=all#top");
> url.attr('source');
"http://markdown.com/awesome/language/markdown.html?show=all#top"

> url.attr('protocol');
"http"

> url.attr('host');
"markdown.com"

> url.attr('relative');
"/awesome/language/markdown.html?show=all#top"

> url.attr('path');
"/awesome/language/markdown.html"

> url.attr('directory');
"/awesome/language/"

> url.attr('file');
"markdown.html"

> url.attr('query');
"show=all"

> url.attr('fragment');
"top"
