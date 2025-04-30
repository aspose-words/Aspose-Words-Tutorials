---
"description": "Узнайте, как создавать и форматировать таблицы в документах Word с помощью Aspose.Words для .NET, с помощью этого подробного пошагового руководства."
"linktitle": "Форматированная таблица"
"second_title": "API обработки документов Aspose.Words"
"title": "Форматированная таблица"
"url": "/ru/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Форматированная таблица

## Введение

Создание и форматирование таблиц в документах Word программным способом может показаться сложной задачей, но с Aspose.Words for .NET это становится простым и управляемым. В этом руководстве мы расскажем вам, как создать отформатированную таблицу в документе Word с помощью Aspose.Words for .NET. Мы рассмотрим все, от настройки среды до сохранения документа с прекрасно отформатированной таблицей.

## Предпосылки

Прежде чем погрузиться в код, давайте убедимся, что у вас есть все необходимое:

1. Библиотека Aspose.Words для .NET: загрузите ее с [здесь](https://releases.aspose.com/words/net/).
2. Среда разработки: IDE, например Visual Studio.
3. .NET Framework: Убедитесь, что на вашем компьютере установлен .NET Framework.

## Импорт пространств имен

Перед написанием самого кода необходимо импортировать необходимые пространства имен:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Шаг 1: Настройте каталог документов

Сначала вам необходимо определить путь, по которому будет сохранен ваш документ.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Заменять `"YOUR DOCUMENT DIRECTORY"` на фактический путь, по которому вы хотите сохранить документ.

## Шаг 2: Инициализация документа и DocumentBuilder

Теперь инициализируйте новый документ и объект DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `DocumentBuilder` — вспомогательный класс, упрощающий процесс создания документов.

## Шаг 3: Начните таблицу

Далее приступайте к созданию таблицы с помощью `StartTable` метод.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Для начала таблицы необходимо вставить ячейку.

## Шаг 4: Примените форматирование ко всей таблице

Вы можете применить форматирование, которое влияет на всю таблицу. Например, установив левый отступ:

```csharp
table.LeftIndent = 20.0;
```

## Шаг 5: Отформатируйте строку заголовка

Задайте высоту, выравнивание и другие свойства строки заголовка.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

На этом этапе мы выделяем строку заголовка, устанавливая цвет фона, размер шрифта и выравнивание.

## Шаг 6: Вставьте дополнительные ячейки заголовка

Вставьте больше ячеек для строки заголовка:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Шаг 7: Форматирование строк тела

После настройки заголовка отформатируйте тело таблицы:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Шаг 8: Вставьте строки тела

Вставьте строки тела с содержимым:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Повторите для дополнительных рядов:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Шаг 9: Сохраните документ.

Наконец, сохраните документ в указанном каталоге:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Это создаст и сохранит документ Word с отформатированной таблицей.

## Заключение

И вот оно! Выполнив эти шаги, вы сможете создать хорошо отформатированную таблицу в документе Word с помощью Aspose.Words для .NET. Эта мощная библиотека упрощает программную обработку документов Word, экономя ваше время и усилия.

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?
Aspose.Words для .NET — мощная библиотека для программного создания, редактирования и преобразования документов Word.

### Могу ли я использовать разные цвета для разных рядов?
Да, вы можете применять различное форматирование, включая цвета, к разным строкам или ячейкам.

### Является ли Aspose.Words для .NET бесплатным?
Aspose.Words для .NET — платная библиотека, но вы можете получить [бесплатная пробная версия](https://releases.aspose.com/).

### Как получить поддержку по Aspose.Words для .NET?
Вы можете получить поддержку от [Форумы сообщества Aspose](https://forum.aspose.com/c/words/8).

### Могу ли я создавать другие типы документов с помощью Aspose.Words для .NET?
Да, Aspose.Words для .NET поддерживает различные форматы документов, включая PDF, HTML и TXT.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}