# koa-server-demo

> Declaratively create a Koa server inside of your electron applications using polymer web components.


## Run

```
$ npm install && bower install && npm start
```

### Build

```
$ npm run build
```

# Usage

```html
<!doctype html>
<html>

<head>
  <meta charset="utf-8">
  <title>Electron polymer koa</title>
  <script src="bower_components/webcomponentsjs/webcomponents-lite.js"></script>
  <link rel="import" href="bower_components/koa-server.html">
  <link rel="import" href="bower_components/koa-route.html">
</head>

<body>
  <template id="app" is="dom-bind">
    <koa-server port="{{port}}">
      <koa-route method="get" path="/" middleware="[[_home()]]">
      </koa-route>
    </koa-server>
    <h1>Koa Server running on port: [[port]]</h1>
  </template>
  <script>
  (function(fs) {
    'use strict';
    const app = document.getElementById('app');

    app._home = () => {
      return function*() {
        this.type = 'text/html';
        this.body = yield fs.readFile('home.html');
      };
    };
  })(require('co-fs'));
  </script>
</body>

</html>

```
