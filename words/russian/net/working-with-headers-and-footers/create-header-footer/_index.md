---
"description": "Узнайте, как добавлять и настраивать верхние и нижние колонтитулы в документах Word с помощью Aspose.Words для .NET. Это пошаговое руководство обеспечивает профессиональное форматирование документов."
"linktitle": "Создать верхний колонтитул"
"second_title": "API обработки документов Aspose.Words"
"title": "Создать верхний колонтитул"
"url": "/ru/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Создать верхний колонтитул

## Введение

Добавление верхних и нижних колонтитулов в ваши документы может повысить их профессионализм и читабельность. С Aspose.Words for .NET вы можете легко создавать и настраивать верхние и нижние колонтитулы для ваших документов Word. В этом руководстве мы проведем вас через весь процесс шаг за шагом, гарантируя, что вы сможете реализовать эти функции без проблем.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующее:

- Aspose.Words для .NET: Загрузите и установите с сайта [ссылка для скачивания](https://releases.aspose.com/words/net/).
- Среда разработки: например, Visual Studio, для написания и запуска кода.
- Базовые знания C#: понимание C# и .NET Framework.
- Образец документа: образец документа для применения верхних и нижних колонтитулов или создания нового, как показано в руководстве.

## Импорт пространств имен

Сначала вам необходимо импортировать необходимые пространства имен для доступа к классам и методам Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Шаг 1: Определите каталог документов

Определите каталог, в котором будет сохранен ваш документ. Это помогает эффективно управлять путем.

```csharp
// Путь к каталогу документов
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Шаг 2: Создайте новый документ

Создайте новый документ и `DocumentBuilder` для облегчения добавления контента.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Шаг 3: Настройка параметров страницы

Настройте параметры страницы, включая то, будет ли на первой странице другой верхний/нижний колонтитул.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Шаг 4: Добавьте заголовок на первую страницу

Перейдите в раздел заголовка первой страницы и настройте текст заголовка.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Шаг 5: Добавьте основной заголовок

Перейдите к основному разделу заголовка и вставьте изображение и текст.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Вставьте изображение в заголовок
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Шаг 6: Добавьте основной нижний колонтитул

Перейдите в основной раздел нижнего колонтитула и создайте таблицу для форматирования содержимого нижнего колонтитула.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Добавить нумерацию страниц
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Шаг 7: Добавьте контент и разрывы страниц

Перейдите в конец документа, добавьте разрыв страницы и создайте новый раздел с другими параметрами страницы.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Шаг 8: Скопируйте верхние и нижние колонтитулы из предыдущего раздела

Если вы хотите повторно использовать верхние и нижние колонтитулы из предыдущего раздела, скопируйте их и внесите необходимые изменения.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Заключение

Выполнив эти шаги, вы сможете эффективно добавлять и настраивать верхние и нижние колонтитулы в документах Word с помощью Aspose.Words for .NET. Это улучшит внешний вид и профессионализм вашего документа, сделав его более читабельным и интересным.

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?

Aspose.Words для .NET — это библиотека, которая позволяет разработчикам программно создавать, редактировать и конвертировать документы Word в приложениях .NET.

### Могу ли я добавлять изображения в верхний или нижний колонтитул?

Да, вы можете легко добавлять изображения в верхний или нижний колонтитул с помощью `DocumentBuilder.InsertImage` метод.

### Как установить разные верхние и нижние колонтитулы для первой страницы?

Вы можете задать различные верхние и нижние колонтитулы для первой страницы, используя `DifferentFirstPageHeaderFooter` собственность `PageSetup` сорт.

### Где я могу найти дополнительную документацию по Aspose.Words?

Вы можете найти подробную документацию по [Страница документации API Aspose.Words](https://reference.aspose.com/words/net/).

### Доступна ли поддержка для Aspose.Words?

Да, Aspose предлагает поддержку через своих [форум поддержки](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}