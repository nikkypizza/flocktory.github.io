---
layout: doc
title:  "Аналитика"
section: widget
order: 2
---

Существует два способа отправить событие в аналитику из виджета.

1. добавить к элементу взаимодействие с которым мы хотим отслеживать атрибут `data-fl-track`
2. принудительно вызвать `widget.track`

События попадают в базу flocktory и в Google Analytics (если настроенно).


# data-fl-track

Добавляем необходимому элементу атрибут `data-fl-track`, значением которого будет имя передаваемого события.

<sup>*</sup> При отправке события клика на ссылку вида `a[target=_top]`, будет произведенна задержка в 300ms для отправки события в аналитику. После которой произойдет переход.

Если внутри ссылки используются другие html-элементы (например картинка), то `data-fl-track` нужно добавлять на элемент внутри ссылки.

**Пример: отправка события клика на ссылку-картинку**
```html
<a href="https://site.com" target="_blank" class="Widget-link"><img data-fl-track="click-link" class="Widget-img" src="http://www.fillmurray.com/50/50" width="50" height="50"></a>
```

**Пример использования**

```html
<button data-fl-track="take-reward">Получить подарок</button>
```

В данном примере при клике на кнопку получить подарок произойдет отправка события `take-reward` в аналитику.


# widget.track

Для отправки события в аналитику из JavaScript кода необходимо воспользоваться методом `widget.track`.

`widget.track` принимает в качестве параметра строковое значение которое и будет отправленно в аналитику.

**Пример использования**

```javascript
document.body.addEventListener('click', function() {
  widget.track('User click on body');
});
```


