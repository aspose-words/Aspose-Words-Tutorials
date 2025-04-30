---
"description": "Откройте для себя мощь Aspose.Words для Java. Научитесь загружать текстовые документы, управлять списками, обрабатывать пробелы и контролировать направление текста."
"linktitle": "Загрузка текстовых файлов с помощью"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Загрузка текстовых файлов с помощью Aspose.Words для Java"
"url": "/ru/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Загрузка текстовых файлов с помощью Aspose.Words для Java


## Введение в загрузку текстовых файлов с помощью Aspose.Words для Java

В этом руководстве мы рассмотрим, как загружать текстовые файлы с помощью Aspose.Words для Java и манипулировать ими как документами Word. Мы рассмотрим различные аспекты, такие как обнаружение списков, обработка пробелов и управление направлением текста.

## Шаг 1: Обнаружение списков

Чтобы загрузить текстовый документ и обнаружить списки, вы можете выполнить следующие действия:

```java
// Создайте текстовый документ в виде строки с частями, которые можно интерпретировать как списки.
// При загрузке первые три списка всегда будут обнаружены Aspose.Words,
// и после загрузки для них будут созданы объекты List.
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
// Четвертый список с пробелом между номером списка и содержимым элемента списка,
// будет распознан как список только в том случае, если «DetectNumberingWithWhitespaces» в объекте LoadOptions имеет значение true,
// чтобы избежать ошибочного определения абзацев, начинающихся с цифр, как списков.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Загрузите документ, применив LoadOptions в качестве параметра, и проверьте результат.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Этот код демонстрирует, как загрузить текстовый документ с различными форматами списков и использовать `DetectNumberingWithWhitespaces` возможность правильного определения списков.

## Шаг 2: Обработка параметров пространства

Для управления начальными и конечными пробелами при загрузке текстового документа можно использовать следующий код:

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

В этом примере мы загружаем текстовый документ и обрезаем начальные и конечные пробелы с помощью `TxtLeadingSpacesOptions.TRIM` и `TxtTrailingSpacesOptions.TRIM`.

## Шаг 3: Управление направлением текста

Чтобы указать направление текста при загрузке текстового документа, можно использовать следующий код:

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

Этот код устанавливает автоматическое определение направления документа (`DocumentDirection.AUTO`) и загружает текстовый документ с текстом на иврите. Вы можете настроить направление документа по мере необходимости.

## Полный исходный код для загрузки текстовых файлов с помощью Aspose.Words для Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Создайте текстовый документ в виде строки с частями, которые можно интерпретировать как списки.
	// При загрузке первые три списка всегда будут обнаружены Aspose.Words,
	// и после загрузки для них будут созданы объекты List.
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
	// Четвертый список с пробелом между номером списка и содержимым элемента списка,
	// будет распознан как список только в том случае, если «DetectNumberingWithWhitespaces» в объекте LoadOptions имеет значение true,
	// чтобы избежать ошибочного определения абзацев, начинающихся с цифр, как списков.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Загрузите документ, применив LoadOptions в качестве параметра, и проверьте результат.
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

## Заключение

В этом руководстве мы изучили, как загружать текстовые файлы с помощью Aspose.Words для Java, обнаруживать списки, обрабатывать пробелы и управлять направлением текста. Эти методы позволяют вам эффективно манипулировать текстовыми документами в ваших приложениях Java.

## Часто задаваемые вопросы

### Что такое Aspose.Words для Java?

Aspose.Words for Java — это мощная библиотека обработки документов, которая позволяет разработчикам создавать, изменять и преобразовывать документы Word программным способом в приложениях Java. Она предоставляет широкий спектр функций для работы с текстом, таблицами, изображениями и другими элементами документа.

### Как начать работу с Aspose.Words для Java?

Чтобы начать работу с Aspose.Words для Java, выполните следующие действия:
1. Загрузите и установите библиотеку Aspose.Words для Java.
2. Обратитесь к документации по адресу [Справочник API Aspose.Words для Java](https://reference.aspose.com/words/java/) для получения подробной информации и примеров.
3. Изучите примеры кода и руководства, чтобы узнать, как эффективно использовать библиотеку.

### Как загрузить текстовый документ с помощью Aspose.Words для Java?

Чтобы загрузить текстовый документ с помощью Aspose.Words для Java, вы можете использовать `TxtLoadOptions` класс и `Document` class. Убедитесь, что вы указали соответствующие параметры для обработки пробелов и направления текста по мере необходимости. Обратитесь к пошаговому руководству в этой статье для подробного примера.

### Могу ли я конвертировать загруженный текстовый документ в другие форматы?

Да, Aspose.Words for Java позволяет преобразовывать загруженный текстовый документ в различные форматы, включая DOCX, PDF и другие. Вы можете использовать `Document` класс для выполнения преобразований. Проверьте документацию для конкретных примеров преобразования.

### Как обрабатывать пробелы в загруженных текстовых документах?

Вы можете контролировать обработку начальных и конечных пробелов в загруженных текстовых документах с помощью `TxtLoadOptions`. Такие варианты, как `TxtLeadingSpacesOptions` и `TxtTrailingSpacesOptions` позволяют обрезать или сохранять пробелы по мере необходимости. Пример см. в разделе «Параметры обработки пробелов» в этом руководстве.

### Какое значение имеет направление текста в Aspose.Words для Java?

Направление текста необходимо для документов, содержащих смешанные письменности или языки, такие как иврит или арабский. Aspose.Words для Java предоставляет параметры для указания направления текста, обеспечивая правильное отображение и форматирование текста на этих языках. Раздел «Управление направлением текста» в этом руководстве демонстрирует, как задать направление текста.

### Где я могу найти дополнительные ресурсы и поддержку по Aspose.Words для Java?

Для получения дополнительных ресурсов, документации и поддержки посетите [Документация Aspose.Words для Java](https://reference.aspose.com/words/java/). Вы также можете принять участие в форумах сообщества Aspose.Words или обратиться в службу поддержки Aspose за помощью по конкретным вопросам или запросам.

### Подходит ли Aspose.Words for Java для коммерческих проектов?

Да, Aspose.Words for Java подходит как для личных, так и для коммерческих проектов. Он предлагает варианты лицензирования для различных сценариев использования. Обязательно ознакомьтесь с условиями лицензирования и ценами на веб-сайте Aspose, чтобы выбрать подходящую лицензию для вашего проекта.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}