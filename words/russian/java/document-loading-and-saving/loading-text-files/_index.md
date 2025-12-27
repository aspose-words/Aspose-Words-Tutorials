---
date: 2025-12-27
description: Узнайте, как установить направление, загрузить txt‑файлы, удалить пробелы
  и преобразовать txt в docx с помощью Aspose.Words for Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Как задать направление и загрузить текстовые файлы с помощью Aspose.Words для
  Java
url: /ru/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как задать направление и загружать текстовые файлы с помощью Aspose.Words для Java

## Введение в загрузку текстовых файлов с помощью Aspose.Words для Java

В этом руководстве вы узнаете **как задать направление** при загрузке простых текстовых документов и увидите практические способы **загрузки txt**, **удаления пробелов** и **конвертации txt в docx** с помощью Aspose.Words для Java. Независимо от того, создаёте ли вы сервис конвертации документов или вам нужен тонкий контроль над определением списков, это руководство проведёт вас через каждый шаг с понятными объяснениями и готовым к запуску кодом.

## Быстрые ответы
- **Как задать направление текста для загруженного TXT‑файла?** Используйте `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` или укажите `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Может ли Aspose.Words определять нумерованные списки в простом тексте?** Да – включите `DetectNumberingWithWhitespaces` в `TxtLoadOptions`.
- **Как обрезать начальные и конечные пробелы?** Установите `TxtLeadingSpacesOptions.TRIM` и `TxtTrailingSpacesOptions.TRIM`.
- **Можно ли конвертировать TXT‑файл в DOCX одной строкой?** Загрузите TXT с `TxtLoadOptions` и вызовите `Document.save("output.docx")`.
- **Какая версия Java требуется?** Java 8+ достаточно для Aspose.Words 24.x.

## Что такое «задать направление» в Aspose.Words?
Когда текстовый файл содержит скрипты справа‑налево (например, иврит или арабский), библиотеке необходимо знать порядок чтения. Перечисление `DocumentDirection` позволяет **задать направление** вручную или позволить Aspose автоматически определить его, обеспечивая правильную разметку и bidi‑форматирование.

## Почему стоит использовать Aspose.Words для загрузки TXT‑файлов?
- **Точное определение списков** – обрабатывает нумерованные, маркированные и списки, разделённые пробелами.
- **Тонкая настройка обработки пробелов** – обрезать или сохранять начальные/конечные пробелы.
- **Автоматическое определение направления текста** – идеально для многоязычных документов.
- **Конвертация в один шаг** – загрузите `.txt` и сохраните как `.docx`, `.pdf` или любой поддерживаемый формат.

## Требования
- Java 8 или новее.
- Библиотека Aspose.Words для Java (добавьте зависимость Maven/Gradle или JAR в проект).
- Базовые знания потоков ввода‑вывода Java.

## Пошаговое руководство

### Шаг 1: Определение списков (как загрузить txt)
Чтобы загрузить текстовый документ и автоматически определить списки, создайте экземпляр `TxtLoadOptions` и включите определение списков. Ниже показан код, демонстрирующий несколько стилей списков и включающий нумерацию, учитывающую пробелы.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Совет:** Если вам нужна только базовая детекция списков, можно пропустить опцию пробельной нумерации – Aspose всё равно распознаёт стандартные шаблоны `1.` и `1)`.

### Шаг 2: Параметры обработки пробелов (как обрезать пробелы)
Начальные и конечные пробелы часто вызывают проблемы с форматированием. Используйте `TxtLeadingSpacesOptions` и `TxtTrailingSpacesOptions` для управления этим поведением.

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **Почему это важно:** Обрезка пробелов предотвращает нежелательные отступы в получаемом DOCX, делая документ чистым без ручной пост‑обработки.

### Шаг 3: Управление направлением текста (как задать направление)
Для языков справа‑налево задайте направление документа перед загрузкой. Пример ниже загружает файл с еврейским текстом и выводит флаг bidi для подтверждения направления.

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **Распространённая ошибка:** Забвение установки `DocumentDirection` может привести к искажённому арабскому/ивритскому тексту, где символы идут в неправильном порядке.

### Полный исходный код для загрузки текстовых файлов с Aspose.Words для Java
Ниже представлен полностью готовый к запуску код, объединяющий определение списков, обработку пробелов и контроль направления. Скопируйте его в один класс и запускайте три тестовых метода по отдельности.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Распространённые проблемы и решения
| Проблема | Причина | Решение |
|----------|----------|----------|
| Списки не определяются | `DetectNumberingWithWhitespaces` оставлен `false` для списков, разделённых пробелами | Включите `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| После загрузки появляется лишний отступ | Начальные пробелы были сохранены | Установите `TxtLeadingSpacesOptions.TRIM` |
| Текст на иврите отображается наоборот | Не задано направление документа или задано `LEFT_TO_RIGHT` | Используйте `DocumentDirection.AUTO` или `RIGHT_TO_LEFT` |
| Выходной DOCX пустой | Поток ввода не был сброшен перед второй загрузкой | Создайте новый `ByteArrayInputStream` для каждого вызова загрузки |

## Часто задаваемые вопросы

### Q: Что такое Aspose.Words для Java?
A: Aspose.Words для Java — мощная библиотека обработки документов, позволяющая разработчикам программно создавать, изменять и конвертировать Word‑документы в Java‑приложениях. Она поддерживает широкий спектр возможностей, от простого загрузки текста до сложного форматирования и конвертации.

### Q: Как начать работу с Aspose.Words для Java?
A: 1. Скачайте и установите библиотеку Aspose.Words для Java. 2. Обратитесь к документации по адресу [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) для получения подробной информации и примеров. 3. Изучите образцы кода и учебные материалы, чтобы эффективно использовать библиотеку.

### Q: Как загрузить текстовый документ с помощью Aspose.Words для Java?
A: Используйте класс `TxtLoadOptions` вместе с конструктором `Document`. Укажите параметры, такие как определение списков, обработка пробелов или направление текста, как показано в пошаговых разделах выше.

### Q: Можно ли конвертировать загруженный текстовый документ в другие форматы?
A: Да. После загрузки TXT‑файла в объект `Document` вызовите `doc.save("output.pdf")`, `doc.save("output.docx")` или любой другой поддерживаемый формат.

### Q: Как обрабатывать пробелы в загруженных текстовых документах?
A: Управляйте начальными и конечными пробелами с помощью `TxtLeadingSpacesOptions` и `TxtTrailingSpacesOptions`. Установите их в `TRIM`, чтобы удалить лишние пробелы, или в `PRESERVE`, если необходимо сохранить оригинальное форматирование.

### Q: Каково значение направления текста в Aspose.Words для Java?
A: Направление текста обеспечивает корректное отображение скриптов справа‑налево (иврит, арабский и др.). Установив `DocumentDirection`, вы гарантируете правильное отображение bidi‑текста в результирующем документе.

### Q: Где можно найти дополнительные ресурсы и поддержку по Aspose.Words для Java?
A: Посетите [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) для справочников API, примеров кода и подробных руководств. Вы также можете присоединиться к форумам сообщества Aspose или связаться со службой поддержки Aspose для решения конкретных вопросов.

### Q: Подходит ли Aspose.Words для Java для коммерческих проектов?
A: Да. Библиотека предлагает варианты лицензирования как для личного, так и для коммерческого использования. Ознакомьтесь с условиями лицензирования на сайте Aspose, чтобы выбрать подходящий план для вашего проекта.

## Заключение
Теперь у вас есть полный набор инструментов для **загрузки txt‑файлов**, **определения списков**, **обрезки пробелов** и **задания направления** при преобразовании простого текста в полноценные Word‑документы с помощью Aspose.Words для Java. Применяйте эти шаблоны для автоматизации документооборота, улучшения поддержки многоязычности и обеспечения чистого, профессионального результата каждый раз.

---

**Последнее обновление:** 2025-12-27  
**Тестировано с:** Aspose.Words для Java 24.12  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}