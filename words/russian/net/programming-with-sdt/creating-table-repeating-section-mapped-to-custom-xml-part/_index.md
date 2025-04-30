---
"description": "Узнайте, как создать таблицу с повторяющимся разделом, сопоставленным с CustomXmlPart в документе Word, с помощью Aspose.Words для .NET."
"linktitle": "Создание таблицы, повторяющей раздел, сопоставленный с пользовательской частью XML"
"second_title": "API обработки документов Aspose.Words"
"title": "Создание таблицы, повторяющей раздел, сопоставленный с пользовательской частью XML"
"url": "/ru/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Создание таблицы, повторяющей раздел, сопоставленный с пользовательской частью XML

## Введение

В этом уроке мы рассмотрим процесс создания таблицы с повторяющимся разделом, который сопоставляется с пользовательской частью XML с помощью Aspose.Words для .NET. Это особенно полезно для динамической генерации документов на основе структурированных данных.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующее:
1. Установлена библиотека Aspose.Words for .NET. Скачать ее можно с сайта [Сайт Aspose](https://releases.aspose.com/words/net/).
2. Базовые знания C# и XML.

## Импорт пространств имен

Обязательно включите в свой проект необходимые пространства имен:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Шаг 1: Инициализация документа и DocumentBuilder

Сначала создайте новый документ и инициализируйте его. `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Шаг 2: Добавьте пользовательскую часть XML

Добавьте пользовательскую часть XML в документ. Этот XML содержит данные, которые мы хотим сопоставить с нашей таблицей:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Шаг 3: Создание структуры таблицы

Далее используйте `DocumentBuilder` для создания заголовка таблицы:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Шаг 4: Создайте повторяющийся раздел

Создать `StructuredDocumentTag` (SDT) для повторяющегося раздела и сопоставьте его с данными XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Шаг 5: Создание повторяющегося элемента раздела

Создайте SDT для повторяющегося элемента раздела и добавьте его в повторяющийся раздел:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Шаг 6: Сопоставьте XML-данные с ячейками таблицы

Создайте SDT для заголовка и автора, сопоставьте их с данными XML и добавьте их в строку:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Шаг 7: Сохраните документ.

Наконец, сохраните документ в указанном каталоге:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Заключение

Выполнив эти шаги, вы успешно создали таблицу с повторяющимся разделом, сопоставленным с пользовательской частью XML с помощью Aspose.Words для .NET. Это позволяет генерировать динамический контент на основе структурированных данных, делая создание документов более гибким и мощным.

## Часто задаваемые вопросы

### Что такое StructuredDocumentTag (SDT)?
SDT, также известный как элемент управления содержимым, представляет собой ограниченную область в документе, которая используется для хранения структурированных данных.

### Могу ли я использовать другие типы данных в пользовательской части XML?
Да, вы можете структурировать свою пользовательскую XML-часть с любыми типами данных и соответствующим образом сопоставлять их.

### Как добавить больше строк в повторяющийся раздел?
Повторяющийся раздел автоматически реплицирует структуру строк для каждого элемента в сопоставленном пути XML.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}