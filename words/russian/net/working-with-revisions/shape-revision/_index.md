---
title: Пересмотр формы
linktitle: Пересмотр формы
second_title: API обработки документов Aspose.Words
description: Узнайте, как обрабатывать изменения форм в документах Word с помощью Aspose.Words для .NET с помощью этого всеобъемлющего руководства. Освойте отслеживание изменений, вставку форм и многое другое.
weight: 10
url: /ru/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Пересмотр формы

## Введение

Редактирование документов Word программным способом может быть сложной задачей, особенно когда дело касается обработки фигур. Независимо от того, создаете ли вы отчеты, разрабатываете шаблоны или просто автоматизируете создание документов, возможность отслеживать и управлять изменениями фигур имеет решающее значение. Aspose.Words для .NET предлагает мощный API, чтобы сделать этот процесс плавным и эффективным. В этом руководстве мы углубимся в особенности изменения фигур в документах Word, гарантируя, что у вас будут инструменты и знания для легкого управления документами.

## Предпосылки

Прежде чем погрузиться в код, давайте убедимся, что у вас есть все необходимое:

-  Aspose.Words для .NET: Убедитесь, что у вас установлена библиотека Aspose.Words. Вы можете[скачать здесь](https://releases.aspose.com/words/net/).
- Среда разработки: у вас должна быть настроена среда разработки, например Visual Studio.
- Базовое понимание C#: знакомство с языком программирования C# и основными концепциями объектно-ориентированного программирования.
- Документ Word: документ Word, с которым можно работать, или вы можете создать его во время обучения.

## Импорт пространств имен

Сначала импортируем необходимые пространства имен. Они предоставят нам доступ к классам и методам, необходимым для обработки документов и фигур Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Шаг 1: Настройка каталога документов

Прежде чем начать работать с фигурами, нам нужно определить путь к нашему каталогу документов. Это то место, где мы будем сохранять наши измененные документы.

```csharp
// Путь к каталогу документов.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Шаг 2: Создание нового документа

Давайте создадим новый документ Word, в который будем вставлять и редактировать фигуры.

```csharp
Document doc = new Document();
```

## Шаг 3: Вставка встроенной фигуры

Начнем со вставки в наш документ встроенной фигуры без отслеживания правок. Встроенная фигура — это та, которая течет вместе с текстом.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Шаг 4: Начало отслеживания изменений

Чтобы отслеживать изменения в нашем документе, нам нужно включить отслеживание ревизий. Это необходимо для идентификации изменений, внесенных в формы.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Шаг 5: Вставка другой фигуры с изменениями

Теперь, когда отслеживание изменений включено, давайте вставим еще одну фигуру. На этот раз любые изменения будут отслеживаться.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Шаг 6: Извлечение и изменение фигур

Мы можем получить все фигуры в документе и изменить их по мере необходимости. Здесь мы получим фигуры и удалим первую.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Шаг 7: Сохранение документа

После внесения изменений нам необходимо сохранить документ. Это гарантирует сохранение всех правок и изменений.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Шаг 8: Обработка изменений перемещения формы

Когда фигура перемещается, Aspose.Words отслеживает это как ревизию. Это означает, что будет два экземпляра фигуры: один в исходном месте и один в новом месте.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Заключение

И вот оно! Вы успешно научились обрабатывать изменения форм в документах Word с помощью Aspose.Words for .NET. Независимо от того, управляете ли вы шаблонами документов, автоматизируете отчеты или просто отслеживаете изменения, эти навыки бесценны. Следуя этому пошаговому руководству, вы не только освоили основы, но и получили представление о более продвинутых методах обработки документов.

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?
Aspose.Words для .NET — это мощная библиотека, которая позволяет разработчикам создавать, изменять и преобразовывать документы Word программным способом с использованием C#.

### Могу ли я отслеживать изменения, внесенные в другие элементы документа Word?
Да, Aspose.Words для .NET поддерживает отслеживание изменений различных элементов, включая текст, таблицы и многое другое.

### Как получить бесплатную пробную версию Aspose.Words для .NET?
 Вы можете получить бесплатную пробную версию Aspose.Words для .NET[здесь](https://releases.aspose.com/).

### Можно ли принять или отклонить изменения программно?
Да, Aspose.Words для .NET предоставляет методы для программного принятия или отклонения изменений.

### Могу ли я использовать Aspose.Words для .NET с другими языками .NET, помимо C#?
Конечно! Aspose.Words для .NET можно использовать с любым языком .NET, включая VB.NET и F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
