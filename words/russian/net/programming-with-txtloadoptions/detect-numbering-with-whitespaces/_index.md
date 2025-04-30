---
"description": "Узнайте, как использовать Aspose.Words для .NET для обнаружения нумерации с пробелами в текстовых документах и обеспечения правильного распознавания ваших списков."
"linktitle": "Определить нумерацию с помощью пробелов"
"second_title": "API обработки документов Aspose.Words"
"title": "Определить нумерацию с помощью пробелов"
"url": "/ru/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Определить нумерацию с помощью пробелов

## Введение

Aspose.Words для энтузиастов .NET! Сегодня мы погрузимся в увлекательную функцию, которая может сделать обработку списков в текстовых документах легкой. Вы когда-нибудь имели дело с текстовыми файлами, где некоторые строки должны быть списками, но они просто не выглядят правильно при загрузке в документ Word? Что ж, у нас есть изящный трюк в рукаве: обнаружение нумерации с пробелами. Этот урок покажет вам, как использовать `DetectNumberingWithWhitespaces` опция в Aspose.Words для .NET, гарантирующая правильное распознавание списков, даже если между числами и текстом есть пробелы.

## Предпосылки

Прежде чем начать, убедитесь, что у вас есть следующее:

- Aspose.Words для .NET: Вы можете загрузить его с сайта [Релизы Aspose](https://releases.aspose.com/words/net/) страница.
- Среда разработки: Visual Studio или любая другая C# IDE.
- На вашем компьютере установлен .NET Framework.
- Базовые знания C#: понимание основ поможет вам разобраться в примерах.

## Импорт пространств имен

Прежде чем перейти к коду, убедитесь, что в вашем проекте импортированы необходимые пространства имен. Вот небольшой фрагмент, с которого можно начать:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Давайте разобьем процесс на простые, управляемые шаги. Каждый шаг проведет вас через необходимый код и объяснит, что происходит.

## Шаг 1: Определите каталог документов

Для начала давайте настроим путь к вашему каталогу документов. Это место, где будут храниться ваши входные и выходные файлы.

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Шаг 2: Создайте текстовый документ

Далее мы создадим текстовый документ в виде строки. Этот документ будет содержать части, которые можно интерпретировать как списки.

```csharp
const string textDoc = "Full stop delimiters:\n" +
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
```

## Шаг 3: Настройка параметров загрузки

Чтобы обнаружить нумерацию с пробелами, нам нужно установить `DetectNumberingWithWhitespaces` возможность `true` в `TxtLoadOptions` объект.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Шаг 4: Загрузите документ

Теперь давайте загрузим документ с помощью `TxtLoadOptions` как параметр. Это гарантирует, что четвертый список (с пробелами) будет обнаружен правильно.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Шаг 5: Сохраните документ.

Наконец, сохраните документ в указанном вами каталоге. Это выведет документ Word с правильно обнаруженными списками.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Заключение

И вот оно! Всего несколько строк кода — и вы овладели искусством обнаружения нумерации с пробелами в текстовых документах с помощью Aspose.Words for .NET. Эта функция может быть невероятно полезна при работе с различными текстовыми форматами и для обеспечения точного отображения списков в документах Word. Так что в следующий раз, когда вы столкнетесь с этими сложными списками, вы будете точно знать, что делать.

## Часто задаваемые вопросы

### Что такое `DetectNumberingWithWhitespaces` в Aspose.Words для .NET?
`DetectNumberingWithWhitespaces` это вариант в `TxtLoadOptions` что позволяет Aspose.Words распознавать списки даже при наличии пробелов между нумерацией и текстом элемента списка.

### Могу ли я использовать эту функцию для других разделителей, таких как маркеры и скобки?
Да, Aspose.Words автоматически определяет списки с общими разделителями, такими как маркеры и скобки. `DetectNumberingWithWhitespaces` особенно помогает со списками, содержащими пробелы.

### Что произойдет, если я не буду использовать `DetectNumberingWithWhitespaces`?
Без этой опции списки с пробелами между нумерацией и текстом могут не распознаваться как списки, а элементы могут отображаться как простые абзацы.

### Доступна ли эта функция в других продуктах Aspose?
Эта специфическая функция разработана специально для Aspose.Words for .NET и предназначена для обработки документов Word.

### Как получить временную лицензию на Aspose.Words для .NET?
Вы можете получить временную лицензию в [Временная лицензия Aspose](https://purchase.aspose.com/temporary-license/) страница.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}