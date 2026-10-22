---
category: general
date: 2026-08-07
description: получить разделитель сносок с помощью Aspose.Words для .NET. Узнайте,
  как извлекать разделители сносок и концевых сносок, проверять типы узлов и изменять
  их в C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: ru
lastmod: 2026-08-07
og_description: получить разделитель сносок с помощью Aspose.Words для .NET. Это руководство
  показывает, как извлечь разделители сносок и концевых сносок, проверить их типы
  узлов и сохранить изменения.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: Получить разделитель сносок в C# – пошаговое руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Получить разделитель сносок в C# – полное руководство по Aspose.Words
url: /ru/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# получить разделитель сносок в C# – полное руководство Aspose.Words

Если вам нужно **retrieve footnote separator** из документа Word, этот учебник покажет, как это сделать с помощью Aspose.Words для .NET. Независимо от того, создаёте ли вы сервис обработки документов или очищаете форматирование сносок, вы увидите полностью готовый пример, который извлекает как разделители сносок, так и концевых сносок.

В этом руководстве вы узнаете, как загрузить файл `.docx`, вызвать свойства `FootnoteSeparator` и `EndnoteSeparator`, проанализировать полученные объекты `Node` и при необходимости заменить линию разделителя. Внешняя документация не требуется — всё, что нужно, включено ниже.

## Требования

* .NET 6.0 или новее (код также работает на .NET Framework 4.7.2)
* NuGet‑пакет Aspose.Words для .NET (версия 24.9 или новее)
* Документ Word, содержащий сноски и/или концевые сноски (например, `Footnotes.docx`)

Вы можете добавить пакет Aspose.Words с помощью следующей команды CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Шаг 1: Настройка проекта и импорт пространств имён

Создайте новый консольный проект или добавьте код в существующий. Необходимые директивы `using` перечислены ниже.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Эти пространства имён дают доступ к классу `Document`, иерархии `Node` и перечислению `NodeType`, необходимым для операций **retrieve footnote separator**.

## Шаг 2: Загрузка документа, содержащего сноски и концевые сноски

Первая операция в любом рабочем процессе Aspose.Words — загрузка исходного файла. Замените путь‑заполнитель фактическим расположением вашего `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Загрузка файла подготавливает внутреннее дерево узлов, что необходимо для **retrieve footnote separator**, поскольку узлы‑разделители находятся внутри этого дерева.

## Шаг 3: Получение узла разделителя сносок

Теперь вы можете **retrieve footnote separator**, обратившись к свойству `FootnoteSeparator` объекта `Document`. Этот узел представляет линию, отделяющую сноски от основного текста.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType` будет `Paragraph` для стандартной линии разделителя. Знание типа узла помогает решить, нужно ли изменять разделитель или полностью заменить его.

## Шаг 4: Получение узла разделителя концевых сносок

Аналогично, вы можете **retrieve endnote separator**, используя свойство `EndnoteSeparator`. Этот узел отделяет концевые сноски от основного содержимого.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Оба узла‑разделителя имеют одинаковый `NodeType` (`Paragraph`) в большинстве документов, но их можно настраивать независимо друг от друга.

## Шаг 5: Просмотр или изменение содержимого разделителя (по желанию)

Если необходимо изменить визуальный вид разделителя — например, заменить линию из тире на тонкую черту — вы можете редактировать узел `Paragraph` напрямую. Ниже приведён пример, заменяющий текст разделителя на пользовательскую строку.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

После изменения узлов вы можете сохранить документ, чтобы увидеть изменения в Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Ожидаемый вывод в консоли

При запуске программы с оригинальным `Footnotes.docx` вы должны увидеть что‑то похожее на следующее:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Если открыть `Footnotes_Updated.docx` в Microsoft Word, разделители сносок и концевых сносок отобразятся с вставленным вами пользовательским текстом.

## Часто задаваемые вопросы и особые случаи

**Что делать, если в документе нет сносок?**  
Свойство `FootnoteSeparator` всё равно возвращает узел `Paragraph`, потому что Word всегда включает заполнитель разделителя. Узел будет пустым, поэтому вы можете безопасно добавить содержимое или оставить его как есть.

**Можно ли получить разделитель для конкретного раздела?**  
Разделители сносок и концевых сносок действуют на уровне всего документа, а не отдельного раздела. Если нужен контроль на уровне раздела, следует работать с `Section.FootnoteOptions` и `Section.EndnoteOptions` вместо глобальных узлов‑разделителей.

**Работает ли это с .NET Core?**  
Да. Aspose.Words для .NET кроссплатформенный, и тот же код работает в Windows, Linux и macOS с .NET 6+.

**Какой тип узла следует ожидать?**  
И `FootnoteSeparator`, и `EndnoteSeparator` возвращают узел `Paragraph` (`NodeType.Paragraph`). Если вы получаете другой тип, документ может быть повреждён, и его следует перезагрузить или проверить исходный файл.

## Полный исходный код для быстрого копирования

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Скопируйте код в файл `Program.cs`, скорректируйте пути к файлам и выполните `dotnet run`. Программа демонстрирует полный рабочий процесс **retrieve footnote separator**, от загрузки документа до сохранения изменений.

## Заключение

Теперь вы знаете, как **retrieve footnote separator** и **endnote separator retrieval** с помощью Aspose.Words для .NET, просматривать их `document node type` и при желании заменять содержимое. Эта техника позволяет автоматизировать форматирование сносок, генерировать пользовательские линии разделителей или проверять структуру документа в любом приложении C#.

Далее вы можете изучить связанные темы, такие как **C# footnote extraction** для отдельного текста сносок, или узнать, как **modify footnote reference marks** с помощью `FootnoteOptions`. Оба концепта напрямую опираются на фундаментальные принципы дерева узлов, рассмотренные здесь.

Удачной разработки, и не стесняйтесь экспериментировать с различными стилями разделителей, чтобы они соответствовали брендингу вашего проекта!

## Что стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Обработка слов с сносками и концевыми сносками](/words/english/net/working-with-footnote-and-endnote/)
- [Добавление контента с помощью Document Builder в Aspose.Words для .NET](/words/english/net/add-content-using-document-builder/)
- [Работа с сносками и концевыми сносками](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}