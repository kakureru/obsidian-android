#android 

### ListView

RecyclerView появился на замену ListView, достоинствами которого являлось:
- возможность переиспользования view
- паттерн adapter
- паттерн [[ViewHolder]]
а недостатками:
- не умеет из коробки обрабатывать сложные жесты
- мало вариантов размещения элементов
- тяжело делать красивые анимации

### RecyclerView

RecyclerView создаёт только те элементы, которые видны на экране, и поддерживает концепцию переиспользования.

Недостатки:
- в пуле лежат "dirty view", заполненные предыдущим содержимым

Компоненты RecyclerView:
Основные:
- Adapter
- LayoutManager
Вспомогательные:
- [[ItemDecorator]]
- [[ItemTouchHelper]]
- ItemAnimator
- [[RecycledViewPool]]

ListAdapter - наследует Adapter и является оберткой над AsyncListDiffer

Как правильно вешать onClickListener:
``` kotlin
override fun onCreateViewHolder() {
	holder.itemView.setOnClickListener {
		if (holder.adapterPosition != RecyclerView.NO_POSITION) {
			onItemClicked(...)
		}
	}
}
```

![[RecyclerView logic.mkv]]