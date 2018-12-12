# Laravel + CoreUIの利用

LaravelとCoreUIを組みわせる方法およびそれを利用した作業テンプレート（ベータ）。

# テンプレート自体の作成手順

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

```diff
try {
    window.Popper = require('popper.js').default;
    window.$ = window.jQuery = require('jquery');

    require('bootstrap');
    //+追加
+   require('@coreui/coreui');

} catch (e) {}
```

### resources/sass/app.scss

```diff
// Fonts
@import url('https://fonts.googleapis.com/css?family=Nunito');

// Variables
@import 'variables';

// Bootstrap
@import '~bootstrap/scss/bootstrap';

//+Icons（追加）
+@import '~@fortawesome/fontawesome-free/css/all.min.css';
+@import '~simple-line-icons/css/simple-line-icons.css';

//+Coreui（追加）
+@import '~@coreui/coreui/dist/css/coreui.min.css';

// styles(option)
//@import 'styles.scss';

.navbar-laravel {
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04);
}
```

>自分用のカスタムCSS(SCSS)を一緒にコンパイルしたい場合はresources/sass/styles.scssを追加し、app.scssに@import 'styles.scss'とすれば合わせてコンパルされます。

### コンパイル

一度コンパイルが通るか試しておく。

```
npm run dev
```

>perfect-scrollbarが無い！と怒られたら、npm install --save perfect-scrollbar

## レイアウト

### 編集と新規作成

app.blade.phpを編集し、それに伴い、header, sidebarを追加。
auth画面用のテンプレート、authを追加。

* resouces/views/layouts/app.blade.php（編集）
* resouces/views/layouts/header.blade.php（追加）
* resouces/views/layouts/sidebar.blade.php（追加）
* resouces/views/layouts/auth.blade.php（追加）

### 編集（差し替え）

以下は差し替え（自分の用途に合ったものにしておく）。

* resources/views/auth/login.blade.php
* resources/views/auth/register.blade.php
* resources/views/auth/passwords/email.blade.php
* resources/views/auth/passwords/reset.blade.php

# テンプレートの利用（cloneして利用）

```
git clone
cd laracore
composer install
npm install
npm run dev

php artisan serve
```


