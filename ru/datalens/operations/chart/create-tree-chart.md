---

__system: {"dislikeVariants":["Нет ответа на мой вопрос","Рекомендации не помогли","Содержание не соответсвует заголовку","Другое"]}
---
# Создание древовидной диаграммы

Чтобы создать древовидную диаграмму:

1. На [главной странице]({{ link-datalens-main }}) сервиса {{ datalens-full-name }} нажмите **Создать чарт**.
1. В разделе **Датасет** выберите датасет для визуализации. Если у вас нет датасета, [создайте его](../dataset/create.md).
1. Выберите тип чарта **Древовидная диаграмма**.
1. Перетащите одно или несколько измерений из датасета в секцию **Измерения**.
1. Перетащите один показатель из датасета в секцию **Размер**. Значения отобразятся в виде прямоугольников. Площади прямоугольников будут пропорциональны соответствующим значениям выбранного показателя.
1. Перетащите один показатель или одно измерение в секцию **Цвета**. Прямоугольники окрасятся в цвета, зависящие от значения добавленного показателя или измерения.

   {% note info %}

   В секцию **Цвета** можно добавить измерение только из секции **Измерения**.

   {% endnote %}

1. Перетащите измерение или показатель из датасета в секцию **Фильтры**. Поле может быть пустым, тогда фильтрация не будет применена.