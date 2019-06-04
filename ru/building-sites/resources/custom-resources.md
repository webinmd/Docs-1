---
title: "Пользовательские классы ресурсов"
translation: "building-sites/resources/custom-resources"
---

Пользовательские классы ресурсов доступны только в MODX 2.2 и более поздних версиях.

## Что такое пользовательский класс ресурсов?

Пользовательский класс ресурсов (CRC) - это класс PHP, который расширяет класс modResource, позволяя создавать пользовательские типы ресурсов, которые могут представлять различные типы данных или приложений. Ядро MODX использует четыре различных типа классов ресурсов: документы, веб ссылки, символические ссылки и статические ресурсы. Другими типами CRC могут быть тип блога, тип форума, тип альбома галереи, тип RSS-канала и т.д. - в основном любой тип контента, для которого требуется URL (помните, что «R» в URL обозначает _Ресурс_).

Пользовательские классы ресурсов создаются путем расширения класса modResource в PHP и загрузки нового класса в систему MODX через пакеты расширений. Они хранят свои данные в той же таблице, что и обычные ресурсы (в modx\_site\_content, но они будут использовать пользовательское значение для столбца class\_key), но они могут вести себя по-разному и иметь собственный интерфейс управления.

### Когда использовать

Пользовательские классы ресурсов полезны для создания «встроенных приложений» в MODX, таких как тип блога (например, [modBlog](/extras/articles "Articles")) это позволяет разместить блог на уже существующем сайте MODX. Вы можете использовать их, если у вас достаточно опыта разработчиков, и вы знакомы с объектно-ориентированным кодом и понимаете, как ваше приложение может вписаться в таблицу содержимого MODX вместе с другими ресурсами.

### Когда не использовать

Пользовательские классы ресурсов не рекомендуется использовать, когда вы просто хотите добавить несколько дополнительных полей в ресурс или изменить представление ресурса во внешнем интерфейсе. Эти ситуации лучше всего решать с помощью [Шаблонов](building-sites/elements/templates "Наблоны") и [Переменных шаблонов](building-sites/elements/template-variables "Переменные шаблонов"). Не используйте пользовательские классы ресурсов, если вы не являетесь сильным разработчиком или если ваши дополнения не нужно манипулировать и отображать с помощью встроенных списков ресурсов MODX.

Также помните, что пользовательские классы ресурсов не могут быть переопределены сами: вы не можете расширить пользовательские классы ресурсов.

**"Практическое правило"**
Если это можно сделать проще, используя [Сниппеты](extending-modx/snippets "Сниппеты") или [Переменные шаблона](building-sites/elements/template-variables "Переменные шаблона"), тогда, вероятно, лучше сделать это так: пользовательские классы ресурсов гораздо сложнее разработать.

## Использование

Пользовательские классы ресурсов выглядят как обычные ресурсы в дереве. Класс gользовательских классов ресурсов также может подключаться к контекстным меню в дереве ресурсов, чтобы добавить параметры для создания типа CRC, например «Создать блог здесь» и т.д. Они могут использовать панели редактирования ресурсов по умолчанию или могут предоставлять совершенно отдельного пользователя. интерфейс для управления своим контентом. Некоторые пользовательские классы ресурсов могут даже иметь другие подклассы (такие как modBlogPost при использовании modBlog CRC), которые полностью скрыты от основного дерева ресурсов. Это полезно при работе с большим количеством ресурсов, которые плохо масштабируются в древовидном интерфейсе.

Контроллеры, процессоры и основные функции рендеринга могут быть расширены и переопределены. Например, вы можете автоматически добавлять текст к выводу любого содержимого пользовательских классов ресурсов, переопределяя метод `process()` или `getContent()` CRC в классе PHP. Любой метод в классе `modResource` доступен для переопределения при использовании пользовательских классов ресурсов.

## Создание Пользовательских классов ресурсов

Пожалуйста, следуйте инструкциям на [Создание класса ресурса](extending-modx/custom-resources "Создание класса ресурса").