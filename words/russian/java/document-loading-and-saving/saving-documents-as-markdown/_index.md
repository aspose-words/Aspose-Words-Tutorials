---
date: 2025-12-22
description: Узнайте, как экспортировать markdown, преобразуя документы Word в Markdown
  с помощью Aspose.Words для Java. Это пошаговое руководство охватывает выравнивание
  таблиц, обработку изображений и многое другое.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Как экспортировать Markdown с помощью Aspose.Words для Java
url: /ru/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как экспортировать Markdown с помощью Aspose.Words для Java

## Введение в экспорт Markdown в Aspose.Words для Java

В этом пошаговом руководстве **вы узнаете, как экспортировать markdown** из документов Word с помощью Aspose.Words for Java. Markdown — это легковесный язык разметки, идеально подходящий для документации, генераторов статических сайтов и многих платформ публикаций. К концу этого руководства вы сможете **конвертировать Word в markdown**, настраивать выравнивание таблиц и **работать с изображениями в markdown** без усилий.

## Быстрые ответы
- **Какой основной класс используется для сохранения в Markdown?** `MarkdownSaveOptions`
- **Можно ли автоматически встраивать изображения?** Да — укажите папку для изображений с помощью `setImagesFolder`.
- **Как управлять выравниванием таблиц?** Используйте `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Каковы минимальные требования?** JDK 8+ и библиотека Aspose.Words for Java.
- **Доступна ли пробная версия?** Да, скачайте её с сайта Aspose.

## Что означает «как экспортировать markdown»?
Экспорт markdown означает преобразование богатого текстового документа Word (`.docx`) в обычный текстовый файл `.md`, сохраняющий заголовки, таблицы и изображения в синтаксисе Markdown.

## Почему стоит использовать Aspose.Words for Java для конвертации docx с изображениями?
Aspose.Words обрабатывает сложные макеты, встроенные изображения и структуры таблиц без потери точности. Он также предоставляет детальный контроль над выводом Markdown, например выравнивание таблиц и управление папкой изображений.

## Требования

- Установленный Java Development Kit (JDK) на вашей системе.
- Библиотека Aspose.Words for Java. Вы можете скачать её [здесь](https://releases.aspose.com/words/java/).

## Шаг 1: Создание простого документа Word

Сначала мы создадим небольшой документ, содержащий таблицу. Это позволит нам позже продемонстрировать **настройку выравнивания таблицы**.

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

В приведённом выше фрагменте мы:

1. Создаём новый `Document`.
2. Используем `DocumentBuilder` для вставки таблицы из двух ячеек.
3. Применяем **правое** и **центральное** выравнивание абзацев внутри каждой ячейки.
4. Сохраняем файл в формате Markdown с помощью `MarkdownSaveOptions`.

## Шаг 2: Настройка выравнивания содержимого таблицы

Aspose.Words позволяет задавать, как ячейки таблицы будут отображаться в итоговом Markdown. Вы можете принудительно задать выравнивание влево, вправо, по центру или позволить библиотеке определить его автоматически на основе первого абзаца в каждом столбце.

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

Переключая свойство `TableContentAlignment`, вы контролируете **настройку выравнивания таблицы** для вывода в Markdown.

## Шаг 3: Работа с изображениями при экспорте в markdown

Когда документ содержит изображения, вы захотите, чтобы они корректно отображались в сгенерированном файле `.md`. Укажите папку, в которую Aspose.Words будет сохранять извлечённые изображения.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Замените `"document_with_images.docx"` на путь к вашему исходному файлу и `"images_folder/"` на место, где вы хотите хранить изображения. Полученный Markdown будет содержать ссылки на изображения, указывающие на эту папку, что позволит вам **работать с изображениями в markdown** без проблем.

## Полный исходный код для сохранения документов в Markdown в Aspose.Words for Java

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

| Проблема | Решение |
|----------|----------|
| Изображения не отображаются в файле `.md` | Убедитесь, что `setImagesFolder` указывает на доступный для записи каталог и что папка правильно указана в сгенерированном Markdown. |
| Выравнивание таблицы выглядит некорректно | Используйте `TableContentAlignment.AUTO`, чтобы Aspose.Words автоматически определил оптимальное выравнивание на основе первого абзаца в каждом столбце. |
| Выходной файл пустой | Убедитесь, что объект `Document` действительно содержит содержимое перед вызовом `save`. |

## Часто задаваемые вопросы

**В: Как установить Aspose.Words for Java?**  
О: Aspose.Words for Java можно установить, включив библиотеку в ваш Java‑проект. Вы можете скачать библиотеку [здесь](https://releases.aspose.com/words/java/) и следовать инструкциям по установке, приведённым в документации.

**В: Можно ли конвертировать сложные документы Word с таблицами и изображениями в Markdown?**  
О: Да, Aspose.Words for Java поддерживает конвертацию сложных документов Word с таблицами, изображениями и различными элементами форматирования в Markdown. Вы можете настраивать вывод Markdown в соответствии со сложностью вашего документа.

**В: Как работать с изображениями в файлах Markdown?**  
О: Укажите путь к папке изображений с помощью метода `setImagesFolder` в `MarkdownSaveOptions`. Убедитесь, что файлы изображений находятся в указанной папке; Aspose.Words сгенерирует соответствующие ссылки на изображения в Markdown.

**В: Доступна ли пробная версия Aspose.Words for Java?**  
О: Да, пробную версию Aspose.Words for Java можно получить на сайте Aspose. Пробная версия позволяет оценить возможности библиотеки перед покупкой лицензии.

**В: Где можно найти больше примеров и документацию?**  
О: Для получения дополнительных примеров, документации и подробной информации об Aspose.Words for Java, пожалуйста, посетите [документацию](https://reference.aspose.com/words/java/).

---

**Последнее обновление:** 2025-12-22  
**Тестировано с:** Aspose.Words for Java 24.12 (последняя версия на момент написания)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}