#android

Content provider - это оболочка в которую заключены данные. Если ваше приложение использует базу данных, то только ваше приложение имеет к ней доступ. Но бывают ситуации, когда данные желательно сделать общими. Так как вы не имеете доступа к базе данных чужого приложения, был придуман специальный механизм, позволяющий делиться своими данными всем желающим.

Content provider применяется лишь в тех случаях, когда вы хотите использовать данные совместно с другими приложениями, работающих в устройстве.

Возвращает cursor - указатель на ячейку данных.

Content provider стартует раньше всех других компонентов.