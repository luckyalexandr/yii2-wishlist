Yii2-wishlist
==========
Модуль избранного для Yii2 фреймворка. ДЛЯ АВТОРИЗОВАННЫХ ПОЛЬЗОВАТЕЛЕЙ


Установка
---------------------------------
Выполнить команду

```
composer require halumein/yii2-wishlist "*"
```

Либо в composer.json строку:

```
"halumein/yii2-wishlist": "dev-master",
```

Далее, мигрируем базу:

```
php yii migrate --migrationPath=vendor/halumein/yii2-wishlist/migrations
```

Подключение и настройка
---------------------------------
В конфигурационный файл приложения добавить модуль и компонент wishlist

```php
    'modules' => [
        'wishlist' => [
            'class' => 'halumein\wishlist\Module',
        ],
        //...
    ],

    'components' => [
        'wishlist' => [
            'class' => 'halumein\wishlist\Wishlist'
        ],
        //...
    ],
```

Компоненты
===========
Получить вишлист ТЕКУЩЕГО пользователя (возвращает массив моделей добавленных в вишлист объектов):
```php
\Yii::$app->wishlist->getUserWishList()
```

Получить количество добавленных в вишлист объектов для текущего пользователя
```php
\Yii::$app->wishlist->getUserWishlistAmount()
```

Виджеты
==========
Кнопка добавить/убрать объект в избранное.

```php

<?php
use halumein\wishlist\widgets\WishlistButton;
?>

<?php /* Выведет кнопку "добавить в избранное" */ ?>
<?= WishlistButton::widget([
	'model' => $model
]) ?>

<?php /* Выведет кнопку "добавить в избранное" с пользовательскими параметрами */ ?>
<?= WishlistButton::widget([
	'model' => $model, // модель для добавления
	'anchorActive' => 'В избранном', // свой текст активной кнопки
	'anchorUnactive' => 'В избранное', // свой текст неактивной кнопки
	'htmlTag' => 'a', // тэг
	'cssClass' => 'custom_class', // свой класс
    'cssClassInList' => 'custom_class' // свой класс для добавленного объекта
]) ?>

```

Дэфолтные css-стили
```css

.hal-wishlist-button {
    font-weight: 700;
}

.hal-wishlist-button:before {
    content: "\f08a";
    font: 400 15px/31px "FontAwesome";
    color: white;
    background: #929292; /* цвет сердечка */
    width: 30px;
    text-align: center;
    display: inline-block;
    height: 30px;
    margin: 0 6px 0 0;
    -moz-border-radius: 50px;
    -webkit-border-radius: 50px;
    border-radius: 50px;
}

.hal-wishlist-button:hover {
    cursor: pointer;
}

.in-list:before {
    background: #CC63B0; /* цвет сердечка */
}


```
