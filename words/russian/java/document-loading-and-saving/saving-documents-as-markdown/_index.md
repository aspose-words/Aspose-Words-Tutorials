---
date: 2026-02-24
description: Узнайте, как конвертировать Word в Markdown с помощью Aspose.Words для
  Java. Это руководство охватывает выравнивание таблиц, работу с изображениями и сохранение
  документа в формате Markdown.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Конвертировать Word в Markdown с помощью Aspose.Words для Java
url: /ru/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Конвертировать Word в Markdown с помощью Aspose.Words for Java

## Введение в конвертацию Word в Markdown с Aspose.Words for Java

В этом пошаговом руководстве вы узнаете **как конвертировать Word в Markdown** с помощью мощного API Aspose.Words for Java. Markdown — это лёгкий язык разметки, который используют многие разработчики и платформы контента для чистой, читаемой документации. К концу этого руководства вы сможете взять любой файл `.docx`, сохранить таблицы, изображения и форматирование и экспортировать его как файл `.md`, готовый для статических генераторов сайтов, README‑файлов на GitHub или любого рабочего процесса, поддерживающего markdown.

## Быстрые ответы
- **Какая библиотека мне нужна?** Aspose.Words for Java (`aspose-words.jar`).
- **Можно ли настроить выравнивание таблиц?** Да — используйте `TableContentAlignment` в `MarkdownSaveOptions`.
- **Как обрабатываются изображения?** Установите папку для изображений с помощью `setImagesFolder()`; библиотека создаст относительные ссылки.
- **Нужна ли лицензия для продакшна?** Коммерческая лицензия требуется для использования не в режиме пробной версии.
- **Совместима ли она с Java 17?** Да, библиотека поддерживает Java 8 и выше.

## Что означает конвертация Word в Markdown?

Конвертация Word в Markdown подразумевает преобразование богатого форматирования документа Microsoft Word в простую markdown‑разметку. Этот процесс сохраняет заголовки, списки, таблицы и ссылки на изображения, одновременно удаляя бинарное форматирование, делая контент переносимым и удобным для систем контроля версий.

## Почему использовать Aspose.Words for Java для сохранения документа в markdown?

* **Полная точность** – сохраняются таблицы, изображения и сложные макеты.
* **Тонкая настройка** – можно настроить выравнивание таблиц, пути к изображениям и многое другое.
* **Без внешних зависимостей** – библиотека работает сразу, без необходимости установки Office.
* **Кроссплатформенность** – работает на Windows, Linux и macOS с любой JVM.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

- Установленный Java Development Kit (JDK).
- Библиотека Aspose.Words for Java. Вы можете скачать её [здесь](https://releases.aspose.com/words/java/).

## Пошаговое руководство

### Шаг 1: Создать документ Word, который будет конвертирован

Сначала мы создаём простой документ Word, содержащий таблицу из двух ячеек. Этот пример демонстрирует, как выравнивание абзацев внутри ячеек таблицы сохраняется при последующем **сохранении документа как markdown**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

### Шаг 2: Настроить выравнивание содержимого таблицы

Aspose.Words for Java позволяет управлять тем, как ячейки таблицы выравниваются в сгенерированном markdown. Используйте свойство `TableContentAlignment`, чтобы **настроить выравнивание таблицы** влево, вправо, по центру или позволить библиотеке определить его автоматически на основе первого абзаца в каждом столбце.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Переключая эту настройку, вы можете **экспортировать таблицы Word в markdown** с точным выравниванием, необходимым для downstream‑движков рендеринга.

### Шаг 3: Обрабатывать изображения во время конвертации

Когда исходный документ Word содержит изображения, необходимо указать Aspose.Words, куда сохранять экспортированные файлы изображений. Метод `setImagesFolder` у `MarkdownSaveOptions` задаёт папку, в которой будут храниться изображения, а markdown будет содержать относительные ссылки на эти файлы.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Замените `"document_with_images.docx"` на путь к вашему исходному файлу и `"images_folder/"` на желаемую папку вывода для изображений.

### Полный исходный код для всех сценариев

Ниже приведён объединённый пример, показывающий, как **автоматически выравнивать таблицы**, **настраивать выравнивание** и **устанавливать папку для изображений** в одном методе. Этот фрагмент полностью соответствует оригинальному коду учебника и работает без изменений.

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Распространённые проблемы и решения

| Проблема | Причина | Решение |
|----------|---------|----------|
| Изображения отображаются как битые ссылки | `setImagesFolder` не установлен или путь к папке неверен | Проверьте правильность пути к папке и убедитесь, что папка доступна для записи |
| Выравнивание таблицы выглядит некорректно | Неправильное значение `TableContentAlignment` | Используйте `TableContentAlignment.AUTO`, чтобы первое предложение определяло выравнивание, либо явно задайте LEFT/RIGHT/CENTER |
| Выходной файл пустой | Параметры сохранения не переданы в `doc.save()` | Убедитесь, что экземпляр `MarkdownSaveOptions` передаётся в метод `save` |
| Не поддерживаются некоторые функции Word (например, SmartArt) | Markdown не может представить некоторые сложные объекты | Преобразуйте такие элементы в изображения перед сохранением или упростите исходный документ |

## Часто задаваемые вопросы

**В: Как установить Aspose.Words for Java?**  
О: Aspose.Words for Java можно установить, добавив библиотеку в ваш Java‑проект. Скачайте её [здесь](https://releases.aspose.com/words/java/) и следуйте инструкциям по установке, приведённым в документации.

**В: Можно ли конвертировать сложные документы Word с таблицами и изображениями в Markdown?**  
О: Да, Aspose.Words for Java поддерживает конвертацию сложных документов Word с таблицами, изображениями и различными элементами форматирования в Markdown. Вы можете настроить вывод Markdown в соответствии со сложностью вашего документа.

**В: Как обрабатывать изображения в файлах Markdown?**  
О: Чтобы включить изображения в файлы Markdown, задайте путь к папке изображений с помощью метода `setImagesFolder` в `MarkdownSaveOptions`. Убедитесь, что файлы изображений находятся в указанной папке, и Aspose.Words for Java автоматически сформирует ссылки на них.

**В: Есть ли пробная версия Aspose.Words for Java?**  
О: Да, пробную версию Aspose.Words for Java можно получить на сайте Aspose. Пробная версия позволяет оценить возможности библиотеки перед покупкой лицензии.

**В: Где можно найти больше примеров и документацию?**  
О: Для получения дополнительных примеров, документации и подробной информации о Aspose.Words for Java посетите [документацию](https://reference.aspose.com/words/java/).

## Заключение

В этом руководстве мы рассмотрели всё, что нужно для **конвертации Word в markdown** с помощью Aspose.Words for Java: создание исходного документа, **настройку выравнивания таблиц** и обработку изображений с правильной конфигурацией папки. С помощью этих приёмов вы сможете надёжно экспортировать содержимое Word в markdown для блогов, сайтов документации или любой платформы, поддерживающей markdown.

---

**Последнее обновление:** 2026-02-24  
**Тестировано с:** Aspose.Words for Java 24.12 (на момент написания)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}