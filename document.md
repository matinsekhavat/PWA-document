# PWA - Document

### App Manifest

- manifest.json is a file which include all PWA configs , such as : name , icons , display(standalone - browser) theme color and ... others options that we can set in manifest.json file.

in second step when we want to deploy we should set an `SSL` for that.(our URL need SSL)

so we need a package called <a href="https://www.npmjs.com/package/http-server">http-server</a>

```bash
npm i -g http-server
```

---

when you want to connect `manifest.json` to your index.html
in manifest.json

```json
{
  "short_name": "pwa",
  "name": "pwa-document"
}
```

`short name`: when user click to add to home screen for exmaple: the short name is default value of app name

you can write sth like this pattern into this file then for link that to index.html
we use :

```html
<link rel="manifest" href="path" />
```

---

`setup http-server`
for start http-server:

```bash
http-server -p 9000
```

---

### display in manifest

when user add PWA into his homescreen then when open that app user navigate to browser simulate , but this is not what we want. we want that App open into seperate display that we called `standalone`

```json
{
  "short_name": "pwa",
  "name": "pwa name",
  "display": "standalone"
}
```

this means there isnot any broweser URL at the top of phone or any device .

---

### theme_color

for add color to the top of the mobile nav we set
`theme_color`

---

### name in manifest

- so the name key is show when the pwa splash runs.
  splash means: the first time we want to open the app we see sth like loading the name appear there

### start_url

- when user for the first time open the app which page should be shown up into his phone , so for controll this we say :

```json
{
  "start_url": "/"
}
```

### lang & dir

for set that for example we are using fa language and our website direction is rtl we just say:

```json
{
  "lang": "fa",
  "dir": "rtl"
}
```

---

### icons in manifest

for add icons

```json
{
  "icons": [
    {} //pwa icons generator
  ]
}
```

### manifest in safari

```html
<link rel="apple-touch-icon" href="path/48*48" size="48*48" />
<meta rel="apple-mobile-web-app-title" content="appTitle" />
<!-- standalone -->
<meta name="apple-mobile-web-app-capable" content="yes" />

<!-- theme_color -->
<meta
  name="apple-mobile-web-app-status-bar-style"
  content="black-translucent"
/>
```

---

# service worker

- at first we should check that user Browser support service worker or not?

for check is a key inside of object we can say

we make a file named `app.js` and another one `sw.js`
in app.js we say

---

### activate register

```javascript
if ("serviceWorker" in navigator) {
  navigator.serviceWorker
    .register("../sw.js")
    .then((register) => console.log(register))
    .catch((err) => console.log(err));
}

// navigator.serviceWorker  this syntax we write in if state return Boolean
```

### install event in service worker

in app.js file we just introduce sw.js file into broswer
but all logic should be handle in sw.js file
in javascript for point to a self thing we said `this` but here in PWA we have something similar to this we called : `self`

for install service worker in sw.js file we say :

```javascript
slef.addEventListener("install", () => {
  console.log("service worker successfuly installed");
});
```

in application in service worker tab we can see the output
in each change in sw.js file we should update service worker and click skipWaiting btn instead each time clicking just click to update on reload checkbox

---

### activate event in service worker

in this scenario we wanna talk about
that install event only happened once but activate event update every time we make change into our files + acctive we can click into ` update on reload`
but for better user experience developers should be handle this beacuase user need the last version of activate

```javascript
self.addEventListener("activate", (e) => console.log(e));
```
