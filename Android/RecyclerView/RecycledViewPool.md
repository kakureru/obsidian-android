#android 

- Хранит переиспользуемые ViewHolder'ы
- По умолчанию имеет размер - 5 элементов
- Может переиспользоваться различными Recycler'ами

Например в таком случае чтобы не хранить лишние одинаковые ViewHolder'ы для разных Recycler'ов (по умолчанию у каждого свой view pool), можно назначить им один view pool:
![[RecycledViewPool usecase.png]]