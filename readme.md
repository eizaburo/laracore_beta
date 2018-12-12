## Laravel + CoreUIの利用


## 準備

### Laravel

```
composer create-project laravel/laravel laracore
```

### ライブラリ

coreui本体。

```
npm install --save @coreui/coreui
```

>chalkが無い！と怒られたら、npm install --save chalk

フォント系。

```
npm install @fortawesome/fontawesome-free --save
npm install simple-line-icons --save
```

### resources/js/bootstrap.js

```
try {
    window.Popper = require('popper.js').default;
    window.$ = window.jQuery = require('jquery');

    require('bootstrap');
 +   require('@coreui/coreui');
} catch (e) {}
```

### resources/sass/app.scss

```
// Fonts
@import url('https://fonts.googleapis.com/css?family=Nunito');

// Variables
@import 'variables';

// Bootstrap
@import '~bootstrap/scss/bootstrap';

//+Icons
@import '~@fortawesome/fontawesome-free/css/all.min.css';
@import '~simple-line-icons/css/simple-line-icons.css';

//+Coreui
@import '~@coreui/coreui/dist/css/coreui.min.css';

// styles(option)
//@import 'styles.scss';

.navbar-laravel {
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04);
}
```

## レイアウト

