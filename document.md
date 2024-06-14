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
