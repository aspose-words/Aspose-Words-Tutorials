---
title: Сохранение документов в формате Markdown в Aspose.Words для Java
linktitle: Сохранение документов в формате Markdown
second_title: API обработки документов Java Aspose.Words
description: Узнайте, как преобразовать документы Word в Markdown с помощью Aspose.Words для Java. Это пошаговое руководство охватывает выравнивание таблиц, обработку изображений и многое другое.
weight: 18
url: /ru/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранение документов в формате Markdown в Aspose.Words для Java


## Введение в сохранение документов в формате Markdown в Aspose.Words для Java

В этом пошаговом руководстве мы покажем, как сохранять документы в формате Markdown с помощью Aspose.Words for Java. Markdown — это легкий язык разметки, который обычно используется для форматирования текстовых документов. С помощью Aspose.Words for Java вы можете легко преобразовать документы Word в формат Markdown. Мы рассмотрим различные аспекты сохранения файлов Markdown, включая выравнивание содержимого таблиц и обработку изображений.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующие предварительные условия:

- В вашей системе установлен Java Development Kit (JDK).
-  Библиотека Aspose.Words for Java. Вы можете скачать ее здесь[здесь](https://releases.aspose.com/words/java/).

## Шаг 1: Создание документа Word

Давайте начнем с создания документа Word, который мы позже преобразуем в формат Markdown. Вы можете настроить этот документ в соответствии с вашими требованиями.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Вставьте таблицу с двумя ячейками
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Сохраните документ как Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 В этом примере мы создаем простую таблицу с двумя ячейками и задаем выравнивание абзацев внутри этих ячеек. Затем мы сохраняем документ как Markdown с помощью`MarkdownSaveOptions`.

## Шаг 2: Настройте выравнивание содержимого таблицы

Aspose.Words for Java позволяет настраивать выравнивание содержимого таблицы при сохранении в формате Markdown. Вы можете выровнять содержимое таблицы по левому краю, правому краю, центру или позволить ему определяться автоматически на основе первого абзаца в каждом столбце таблицы.

Вот как настроить выравнивание содержимого таблицы:

```java
// Установить выравнивание содержимого таблицы по левому краю
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Установить выравнивание содержимого таблицы по правому краю
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Установить выравнивание содержимого таблицы по центру
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Установите выравнивание содержимого таблицы на автоматическое (определяется первым абзацем)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Изменяя`TableContentAlignment` Свойство позволяет контролировать выравнивание содержимого таблиц при конвертации в Markdown.

## Шаг 3: Обработка изображений

 Чтобы включить изображения в документ Markdown, вам необходимо указать папку, в которой находятся изображения. Aspose.Words for Java позволяет вам задать папку с изображениями в`MarkdownSaveOptions`.

Вот как задать папку для изображений и сохранить документ с изображениями:

```java
// Загрузить документ, содержащий изображения
Document doc = new Document("document_with_images.docx");

// Укажите путь к папке с изображениями
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Сохраните документ с изображениями
doc.save("document_with_images.md", saveOptions);
```

 Обязательно замените`"document_with_images.docx"` с путем к вашему документу Word, содержащему изображения и`"images_folder/"` с фактическим путем к папке, где хранятся ваши изображения.

## Полный исходный код для сохранения документов в формате Markdown в Aspose.Words для Java

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
	// Выравнивает все абзацы внутри таблицы.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Выравнивание в этом случае будет взято из первого абзаца в соответствующем столбце таблицы.
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

## Заключение

В этом руководстве мы рассмотрели, как сохранять документы в формате Markdown с помощью Aspose.Words for Java. Мы рассмотрели создание документа Word, настройку выравнивания содержимого таблицы и обработку изображений в файлах Markdown. Теперь вы можете эффективно преобразовывать документы Word в формат Markdown, делая их подходящими для различных платформ публикации и нужд документирования.

## Часто задаваемые вопросы

### Как установить Aspose.Words для Java?

 Aspose.Words для Java можно установить, включив библиотеку в свой проект Java. Вы можете загрузить библиотеку с[здесь](https://releases.aspose.com/words/java/) и следуйте инструкциям по установке, приведенным в документации.

### Можно ли конвертировать сложные документы Word с таблицами и изображениями в Markdown?

Да, Aspose.Words for Java поддерживает преобразование сложных документов Word с таблицами, изображениями и различными элементами форматирования в Markdown. Вы можете настроить вывод Markdown в соответствии со сложностью вашего документа.

### Как обрабатывать изображения в файлах Markdown?

 Чтобы включить изображения в файлы Markdown, укажите путь к папке с изображениями с помощью`setImagesFolder`метод в`MarkdownSaveOptions`. Убедитесь, что файлы изображений хранятся в указанной папке, и Aspose.Words для Java обработает ссылки на изображения соответствующим образом.

### Доступна ли пробная версия Aspose.Words для Java?

Да, вы можете получить пробную версию Aspose.Words for Java на сайте Aspose. Пробная версия позволяет оценить возможности библиотеки перед покупкой лицензии.

### Где я могу найти больше примеров и документации?

 Дополнительные примеры, документацию и подробную информацию об Aspose.Words для Java можно найти на сайте[документация](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
