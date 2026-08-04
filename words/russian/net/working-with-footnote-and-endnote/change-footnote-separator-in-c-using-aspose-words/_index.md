---
category: general
date: 2026-08-04
description: Изменить разделитель сносок в C# с помощью Aspose.Words — узнайте, как
  редактировать разделитель сносок и менять разделитель концевых сносок в документах
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: ru
lastmod: 2026-08-04
og_description: Измените разделитель сносок в C# с помощью Aspose.Words. Это руководство
  покажет, как редактировать разделитель сносок, настраивать разделитель примечаний
  и сохранять обновлённый документ.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Изменить разделитель сносок в C# – полное руководство по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Изменить разделитель сносок в C# с помощью Aspose.Words
url: /ru/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Изменение разделителя сносок в C# с помощью Aspose.Words

Если вам нужно **изменить разделитель сносок** в документе Word, этот учебник проведёт вас через все шаги с использованием Aspose.Words для .NET. Хотите заменить стандартную линию символом или применить иной стиль к разделителям концевых сносок — приведённый ниже код охватывает весь процесс.

Вы также узнаете, как **редактировать разделитель сносок** и выполнить связанную операцию **изменения разделителя концевой сноски**, чтобы один документ имел единый стиль как для сносок, так и для концевых сносок. Внешние инструменты не требуются — достаточно нескольких строк C#.

## Что вы получите

К концу этого руководства вы сможете:

* Загрузить существующий файл *.docx*, содержащий сноски и концевые сноски.  
* Получить доступ к узлам‑разделителям для сносок, продолжений сносок и концевых сносок.  
* Заменить символ разделителя (например, изменить стандартную линию на звёздочку).  
* Сохранить изменённый документ, не потеряв остальное содержимое.  

В учебнике предполагается базовое знание C# и установленный пакет **Aspose.Words** NuGet (версия 24.9 или новее).  

---

## Предварительные требования

| Требование | Причина |
|-------------|--------|
| .NET 6.0+ или .NET Framework 4.7.2+ | Необходимая среда выполнения для Aspose.Words |
| Библиотека Aspose.Words for .NET | Предоставляет API `Document` и `FootnoteOptions` |
| Входной файл Word (`input.docx`) с хотя бы одной сноской или концевой сноской | Демонстрирует изменение разделителя |

Вы можете добавить Aspose.Words в свой проект с помощью следующей команды CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Шаг 1: Загрузка документа, содержащего сноски

Первой операцией является чтение исходного файла в объект `Document`. Этот объект представляет весь файл Word в памяти и даёт доступ ко всем его узлам.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Почему это важно:** Загрузка документа — точка входа для любой модификации. Если файл не найден, Aspose.Words бросит `FileNotFoundException`, поэтому убедитесь, что путь указан правильно перед продолжением.

---

## Шаг 2: Доступ к узлам‑разделителям сносок и концевых сносок

`Document.FootnoteOptions` раскрывает три узла‑разделителя:

* `Separator` – линия, отображаемая после коллекции сносок на первой странице.  
* `ContinuationSeparator` – линия, используемая, когда сноски продолжаются на следующей странице.  
* `EndnoteSeparator` – линия, разделяющая основной текст и список концевых сносок.

Вы получаете эти узлы как общие объекты `Node`, а затем приводите их к типу `Run` для изменения текста.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Почему это важно:** Именно в этих узлах хранится визуальный символ разделителя. Изменение любого другого узла (например, обычного абзаца) не повлияет на форматирование сносок.

---

## Шаг 3: Изменение символа разделителя сносок

Самая распространённая задача — заменить стандартную линию символом, например, звёздочкой (`*`). Поскольку разделитель хранится как `Run`, вы можете безопасно изменить его свойство `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Почему это важно:** Прямое редактирование `Run.Text` обновляет визуальное представление в конечном документе, не затрагивая остальное содержимое сносок. Тот же подход можно использовать для любой строки, включая Unicode‑символы.

---

## Шаг 4: Изменение разделителя концевой сноски (по желанию)

Если вам также нужно **изменить разделитель концевой сноски**, процесс полностью аналогичен изменению разделителя сносок. Замените текст `endnoteSeparator` на желаемый символ.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Почему это важно:** Концевые сноски часто стилизуются иначе, чем сноски. Отдельный разделитель позволяет поддерживать визуальную согласованность с рекомендациями по дизайну вашего документа.

---

## Шаг 5: Сохранение изменённого документа

После всех модификаций сохраните изменения с помощью `Document.Save`. Вы можете перезаписать исходный файл или записать его в новое место.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Почему это важно:** `Save` записывает представление в памяти на диск, сохраняя все остальные элементы (стили, изображения, таблицы) без изменений.

---

## Полный, готовый к запуску пример

Объединив все части, получаем самостоятельное консольное приложение, демонстрирующее весь процесс:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Ожидаемый результат:** Откройте *ModifiedSeparators.docx* в Microsoft Word. Разделительная линия сноски внизу первой страницы сносок теперь будет одной звёздочкой (`*`). Если документ содержит концевые сноски, линия, разделяющая основной текст и список концевых сносок, будет отображаться как тире (`-`). Всё остальное содержимое (текст, изображения, таблицы) останется нетронутым.

---

## Часто задаваемые вопросы и обработка граничных случаев

| Вопрос | Ответ |
|----------|--------|
| **Что если в документе нет сносок?** | `FootnoteOptions.Separator` всё равно возвращает узел `Run`, но его текст может быть пустым. Код безопасно проверяет тип узла перед изменением. |
| **Можно ли использовать строку из нескольких символов (например, "***")?** | Да. Свойство `Run.Text` принимает любую строку, включая Unicode‑символы. |
| **Повлияет ли изменение разделителя на нумерацию существующих сносок?** | Нет. Разделитель независим от схемы нумерации. |
| **Нужно ли освобождать объект `Document`?** | `Document` неявно реализует `IDisposable` через `Node`. В короткоживущем консольном приложении это необязательно, но в длительно работающих сервисах рекомендуется обернуть его в `using`. |
| **Как это работает в .NET Core vs .NET Framework?** | API идентичен на всех платформах; важна только поддерживаемая версия целевого фреймворка (должна поддерживаться пакетом Aspose.Words). |

**Совет:** Если требуется применить разные разделители для разных разделов, можно пройтись по `doc.GetChildNodes(NodeType.Footnote, true)` и индивидуально настроить свойство `Separator` каждой сноски. Это более продвинуто, но полезно для сложных документов.

---

## Заключение

Теперь вы знаете, как **изменить разделитель сносок** и **изменить разделитель концевой сноски** в файле Word с помощью Aspose.Words для C#. Руководство охватывало загрузку документа, доступ к нужным узлам‑разделителям, изменение их текста и сохранение результата — всё в одном самостоятельном приложении.

Далее вы можете изучать связанные темы, такие как **редактирование стиля разделителя сносок**, настройка нумерации сносок или применение условного форматирования в зависимости от макета страниц. Тот же шаблон (получить узел, привести к `Run`, изменить `Text`) работает во многих сценариях обработки Word‑документов.

Удачной разработки, экспериментируйте с разными символами или даже вставляйте изображения в качестве разделителей для действительно уникального оформления документа!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, опираясь на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Обработка слов с сносками и концевыми сносками](/words/english/net/working-with-footnote-and-endnote/)
- [Получить разделитель стиля абзаца в документе Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Вставить разделитель стиля документа в Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}