---
"description": "Изучите пошаговое руководство по использованию верхних и нижних колонтитулов в Aspose.Words для Java. Создавайте профессиональные документы без усилий."
"linktitle": "Использование верхних и нижних колонтитулов"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Использование верхних и нижних колонтитулов в Aspose.Words для Java"
"url": "/ru/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Использование верхних и нижних колонтитулов в Aspose.Words для Java


В этом подробном руководстве мы проведем вас через процесс работы с верхними и нижними колонтитулами в Aspose.Words для Java. Верхние и нижние колонтитулы являются важными элементами форматирования документов, и Aspose.Words предоставляет мощные инструменты для их создания и настройки в соответствии с вашими потребностями.

Теперь давайте подробно рассмотрим каждый из этих шагов.

## 1. Введение в Aspose.Words

Aspose.Words — это мощный API Java, позволяющий программно создавать, изменять и визуализировать документы Word. Он предоставляет обширные возможности для форматирования документов, включая верхние и нижние колонтитулы.

## 2. Настройка среды Java

Прежде чем начать использовать Aspose.Words, убедитесь, что у вас правильно настроена среда разработки Java. Необходимые инструкции по настройке вы найдете на странице документации Aspose.Words: [Документация Java Aspose.Words](https://reference.aspose.com/words/java/).

## 3. Создание нового документа

Для работы с верхними и нижними колонтитулами вам необходимо создать новый документ с помощью Aspose.Words. Следующий код демонстрирует, как это сделать:

```java
// Код Java для создания нового документа
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Понимание настройки страницы

Настройка страницы имеет решающее значение для управления макетом вашего документа. Вы можете указать различные свойства, связанные с верхними и нижними колонтитулами, используя `PageSetup` класс. Например:

```java
// Настройка свойств страницы
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Разные верхние и нижние колонтитулы первой страницы

Aspose.Words позволяет вам иметь разные верхние и нижние колонтитулы для первой страницы вашего документа. Используйте `pageSetup.setDifferentFirstPageHeaderFooter(true);` для включения этой функции.

## 6. Работа с заголовками

### 6.1 Добавление текста в заголовки

Вы можете добавить текст в заголовки с помощью `DocumentBuilder`. Вот пример:

```java
// Добавление текста в заголовок первой страницы
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2 Вставка изображений в заголовки

Чтобы вставить изображения в заголовки, вы можете использовать `insertImage` метод. Вот пример:

```java
// Вставка изображения в заголовок
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3 Настройка стилей заголовков

Вы можете настроить стили заголовков, задав различные свойства, такие как шрифт, выравнивание и т. д., как показано в примерах выше.

## 7. Работа с нижними колонтитулами

### 7.1 Добавление текста в нижние колонтитулы

Подобно заголовкам, вы можете добавлять текст в нижние колонтитулы с помощью `DocumentBuilder`. Вот пример:

```java
// Добавление текста в основной нижний колонтитул
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Вставьте текст и поля по мере необходимости.
```

### 7.2 Вставка изображений в нижние колонтитулы

Чтобы вставить изображения в нижние колонтитулы, используйте `insertImage` метод, как и в заголовках.

### 7.3 Настройка стилей нижнего колонтитула

Настройте стили нижнего колонтитула с помощью `DocumentBuilder`, аналогично настройке заголовков.

## 8. Нумерация страниц

Вы можете включить номера страниц в верхние и нижние колонтитулы, используя такие поля, как `PAGE` и `NUMPAGES`. Эти поля автоматически обновляются при добавлении или удалении страниц.

## 9. Информация об авторских правах в нижних колонтитулах

Чтобы добавить информацию об авторских правах в нижний колонтитул документа, вы можете использовать таблицу с двумя ячейками, выровняв одну по левому краю, а другую по правому, как показано во фрагменте кода.

## 10. Работа с несколькими разделами

Aspose.Words позволяет работать с несколькими разделами документа. Вы можете задать различные настройки страницы и колонтитулы для каждого раздела.

## 11. Альбомная ориентация

При необходимости вы можете изменить ориентацию отдельных разделов на альбомную.

## 12. Копирование верхних/нижних колонтитулов из предыдущих разделов

Копирование верхних и нижних колонтитулов из предыдущих разделов может сэкономить время при создании сложных документов.

## 13. Сохранение документа

После создания и настройки документа не забудьте сохранить его с помощью `doc.save()` метод.

## Полный исходный код
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Укажите, хотим ли мы, чтобы верхние/нижние колонтитулы первой страницы отличались от других страниц.
        // Вы также можете использовать свойство PageSetup.OddAndEvenPagesHeaderFooter, чтобы указать
        // разные верхние/нижние колонтитулы для четных и нечетных страниц.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Вставьте позиционируемое изображение в верхний/левый угол заголовка.
        // Расстояние от верхнего/левого края страницы установлено в 10 пунктов.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Для оформления одной части текста в строку (с нумерацией страниц) используем таблицу с двумя ячейками.
        // Выровнять по левому краю, а остальную часть текста (с указанием авторских прав) выровнять по правому краю.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Он использует поля PAGE и NUMPAGES для автоматического расчета текущего номера страницы и количества страниц.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Создайте разрыв страницы, чтобы создать вторую страницу, на которой будут видны основные верхние и нижние колонтитулы.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // В этом разделе не нужен отдельный верхний/нижний колонтитул первой страницы, нам нужен только один титульный лист в документе,
        // а верхний/нижний колонтитул для этой страницы уже был определен в предыдущем разделе.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // В этом разделе отображаются верхние и нижние колонтитулы из предыдущего раздела.
        // по умолчанию вызовите currentSection.HeadersFooters.LinkToPrevious(false) для отмены этой ширины страницы
        // для нового раздела она отличается, поэтому нам необходимо задать другую ширину ячеек для таблицы нижнего колонтитула.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Если мы хотим использовать уже существующий набор верхних/нижних колонтитулов для этого раздела.
        // Но с некоторыми небольшими изменениями, тогда может быть целесообразно скопировать верхние/нижние колонтитулы.
        // из предыдущего раздела и применяем необходимые изменения там, где это необходимо.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Исходный код метода copyHeadersFootersFromPreviousSection
```java
    /// <резюме>
    //Клонирует и копирует верхние и нижние колонтитулы из предыдущего раздела в указанный раздел.
    /// </резюме>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Заключение

В этом уроке мы рассмотрели основы работы с верхними и нижними колонтитулами в Aspose.Words для Java. Вы узнали, как создавать, настраивать и оформлять верхние и нижние колонтитулы, а также другие важные методы форматирования документов.

Для получения более подробной информации и дополнительных функций см. [Документация Java Aspose.Words](https://reference.aspose.com/words/java/).

## Часто задаваемые вопросы

### 1. Как добавить номера страниц в нижний колонтитул документа?
Вы можете добавить номера страниц, вставив `PAGE` поле в нижний колонтитул с помощью Aspose.Words.

### 2. Совместим ли Aspose.Words со средами разработки Java?
Да, Aspose.Words обеспечивает поддержку разработки Java. Убедитесь, что у вас есть необходимые настройки.

### 3. Могу ли я настроить шрифт и стиль верхних и нижних колонтитулов?
Конечно, вы можете настраивать шрифты, выравнивание и другие стили, чтобы сделать ваши верхние и нижние колонтитулы визуально привлекательными.

### 4. Можно ли иметь разные заголовки для четных и нечетных страниц?
Да, вы можете использовать `PageSetup.OddAndEvenPagesHeaderFooter` для указания разных заголовков для четных и нечетных страниц.

### 5. Как начать работу с Aspose.Words для Java?
Для начала посетите [Документация Java Aspose.Words](https://reference.aspose.com/words/java/) для получения исчерпывающих рекомендаций по использованию API.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}