#android 

Intent является ключевым классом для взаимодействия между различными объектами activity. Он представляет собой задачу, которую надо выполнить приложению.

Существует два вида intent: 

- Явный (explicit) intent 
	Явно содержит информацию о классе компонента. Явные интенты часто используются для старта компонентов внутри приложения, т.к. имена классов известны.

- Неявный (implicit) intent 
	Не содержит информацию о конкретном компоненте. Система использует косвенные атрибуты, такие как action, type и category для выбора стартуемого компонента. Неявные интенты часто используются для старта компонентов других приложений.  

Мы посылаем intent в систему, а система уже возвращает нам нужную [[Activity]], которую встраивает в процесс нашего приложения.
Поэтому всё, что мы передаём в intent, должно перегоняться в поток байт. Всё, что передаём в intent, кладём в bundle - поток байт, который хранится в оперативе. Это могут быть:
- Примитивы
- [[Parcelable]]
- [[Serializable]]
Ограничение порядка 1MB на всё приложение
Google рекомендует передавать не больше 50 KB