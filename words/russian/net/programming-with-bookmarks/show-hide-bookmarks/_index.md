---
title: Показать скрыть закладки в документе Word
linktitle: Показать скрыть закладки в документе Word
second_title: API обработки документов Aspose.Words
description: Узнайте, как динамически отображать или скрывать закладки в документе Word с помощью Aspose.Words для .NET, с помощью нашего пошагового руководства. Идеально подходит для разработчиков.
weight: 10
url: /ru/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Показать скрыть закладки в документе Word

## Введение

Вам когда-нибудь приходилось динамически скрывать или показывать определенные части документа Word? Что ж, вам повезло! С помощью Aspose.Words для .NET вы можете легко управлять видимостью содержимого закладок в ваших документах. В этом руководстве вы узнаете, как показывать и скрывать закладки в документе Word с помощью Aspose.Words для .NET. Мы разберем код шаг за шагом, поэтому независимо от того, являетесь ли вы опытным разработчиком или новичком, вам будет легко следовать этому руководству.

## Предварительные условия

Прежде чем мы углубимся в код, давайте убедимся, что у вас есть все необходимое:

1.  Aspose.Words for .NET: убедитесь, что у вас установлена библиотека Aspose.Words for .NET. Если нет, то вы можете скачать его[здесь](https://releases.aspose.com/words/net/).
2. Среда разработки: IDE, например Visual Studio.
3. Базовые знания C#: Знание программирования на C# будет полезным.
4. Документ Word: образец документа Word с закладками.

## Импортировать пространства имен

Прежде чем начать работу с кодом, вам необходимо импортировать необходимые пространства имен. Добавьте следующее в начало вашего файла C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Шаг 1. Загрузите документ

Прежде всего, вам необходимо загрузить документ Word, содержащий закладки. Вот как вы можете это сделать:

```csharp
// Путь к каталогу документов.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Объяснение

- dataDir: это путь к каталогу, в котором находится ваш документ Word.
-  Документ документа: инициализирует новый экземпляр`Document` class с указанным вами файлом.

## Шаг 2. Показать или скрыть контент, добавленный в закладки

Далее мы определим метод для отображения или скрытия содержимого закладок. Вот полный метод:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MARGEFIELD bookmark}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Объяснение

- Bookmark bm: извлекает закладку из документа.
- Конструктор DocumentBuilder: помогает в навигации и изменении документа.
- Поле поля: вставляет поле IF для проверки состояния закладки.
- Node currentNode: проходит через узлы, чтобы найти начало и конец поля.

## Шаг 3. Выполните функцию «Показать/Скрыть».

 Теперь вам нужно позвонить в`ShowHideBookmarkedContent` метод, передавая документ, имя закладки и флаг видимости:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Объяснение

- doc: ваш объект документа.
- «MyBookmark1»: имя закладки, которую вы хотите показать/скрыть.
- false: флаг видимости (истина для отображения, ложь для скрытия).

## Шаг 4. Сохраните документ

Наконец, сохраните измененный документ:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Объяснение

- dataDir + «WorkingWithBookmarks.ShowHideBookmarks.docx»: путь и имя нового документа, в котором будут сохранены изменения.

## Заключение

И вот оно! Вы успешно научились показывать и скрывать закладки в документе Word с помощью Aspose.Words для .NET. Этот метод может быть невероятно полезен для динамического создания документов с условным содержимым.

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?
Aspose.Words for .NET — это мощная библиотека обработки документов, которая позволяет разработчикам программно создавать, изменять и конвертировать документы Word.

### Как мне получить Aspose.Words для .NET?
 Вы можете скачать Aspose.Words для .NET с сайта[здесь](https://releases.aspose.com/words/net/). Также доступна бесплатная пробная версия.

### Могу ли я использовать этот метод для других типов закладок?
Да, этот метод можно адаптировать для управления видимостью любых закладок в документе Word.

### Что делать, если в моем документе нет указанной закладки?
Если закладка не существует, метод выдаст ошибку. Убедитесь, что закладка существует, прежде чем пытаться ее показать/скрыть.

### Как я могу получить поддержку, если у меня возникнут проблемы?
 Вы можете получить поддержку от сообщества Aspose[здесь](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
