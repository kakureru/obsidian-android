#android 

Данные для частичного обновления элемента [[RecyclerView]]

Уведомление об изменении элемента с данными:
``` kotlin
fun notifyItemChanged(position: Int, payload: Object)
fun notifyItemRangeChanged(positionStart: Int, itemCount: Int, payload: Object)
```

Обработка payload:
``` kotlin
fun onBindViewHolder(holder: RecyclerView.ViewHolder, position: Int, payloads: MutableList<Any>) {
	if (payloads.isEmpty())
		onBindViewHolder(holder, position)
	else 
		holder.someTextView.text = payloads[0] as String
}
```

