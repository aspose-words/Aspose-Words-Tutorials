---
category: general
date: 2026-10-13
description: Как изменить разделитель сносок в документе Word с помощью Aspose.Words.
  Узнайте, как программно изменить цвет шрифта в документе Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: ru
lastmod: 2026-10-13
og_description: Как изменить разделитель сносок в документе Word с помощью Aspose.Words.
  Этот учебник показывает, как изменить цвет шрифта в документе Word, используя C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Как изменить разделитель сносок в документе Word – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Как изменить разделитель сносок и настроить его стиль в документе Word
url: /ru/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как изменить разделитель сносок и настроить его стиль в документе Word

Если вам нужно **how to change footnote separator** в документе Word, это руководство предоставляет полное готовое решение. С помощью Aspose.Words for .NET вы также можете **change font color in Word document** элементы, такие как разделители сносок и концевых сносок, делая конечный файл соответствующим вашему бренду или руководству по стилю.

Авторы документов часто задают вопрос: *Почему стандартный разделитель сносок выглядит простым, и как сделать его более заметным?* Ответ заключается в прямом доступе к объектам абзацев‑разделителей, изменении их свойств шрифта и сохранении результата. Это руководство проведёт вас через каждый шаг, от загрузки файла .docx до сохранения стилизованного вывода.

Вы узнаете, как:

* Загрузить файл Word, который уже содержит сноски и концевые сноски.  
* Найти абзацы‑разделители сносок и концевых сносок.  
* Изменить цвет шрифта каждого разделителя (красный для сносок, синий для концевых сносок).  
* Сохранить изменённый документ, не потеряв существующее содержимое.

Для выполнения этой задачи не требуются внешние инструменты, кроме библиотеки Aspose.Words и среды разработки .NET.

## Требования

* .NET 6.0 SDK или новее (код также работает с .NET Framework 4.7+).  
* Visual Studio 2022, Rider или любой предпочитаемый редактор C#.  
* NuGet‑пакет Aspose.Words for .NET (`Aspose.Words`).  
* Пример файла Word (`Footnotes.docx`), содержащий хотя бы одну сноску и одну концевую сноску.

> **Pro tip:** Если у вас нет примера файла, создайте новый документ Word, вставьте сноску (`References → Insert Footnote`) и концевую сноску (`References → Insert Endnote`). Сохраните его как `Footnotes.docx` в папке, к которой можно обратиться из кода.

## Как изменить разделитель сносок с помощью Aspose.Words

Суть задачи — получить специальные абзацы, которые Aspose.Words представляет как *separator*‑узлы. Эти узлы имеют тип `Paragraph` и могут форматироваться как любой другой абзац.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Почему важна каждая строка

* **Loading the document** (`new Document`) даёт вам представление документа в памяти, которое Aspose.Words может изменять.  
* **`GetChild` with `ParagraphNodeType.FootnoteSeparator`** возвращает скрытый абзац, который Word использует для рисования линии, разделяющей сноски от основного текста. Тот же метод работает и для разделителя концевых сносок.  
* **Changing `Font.Color`** напрямую влияет на внешний вид линии, потому что Word отображает разделитель как абзац с единственным символом “‑”. Установка цвета в `Color.Red` (или любой `System.Drawing.Color`) обновляет визуальный стиль.  
* **Saving** записывает изменения обратно в файл .docx, который может открыть любой текстовый процессор.

### Ожидаемый результат

При открытии `FootnoteSeparatorsStyled.docx` в Microsoft Word:

* Линия разделителя сносок отображается **красным**.  
* Линия разделителя концевых сносок отображается **синим**.  

Весь оригинальный контент сносок и концевых сносок остаётся нетронутым.

## Изменение цвета шрифта в документе Word с помощью C#

Продемонстрированная выше операция — это конкретный случай более широкой возможности: **change font color in Word document** программно. Как только у вас есть `Paragraph`, `Run` или любой `Node`, содержащий текст, вы можете изменить его свойство `Font.Color`.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Этот фрагмент кода перебирает каждый абзац, проверяет, использует ли он стиль `Heading 1`, и задаёт цвет шрифта.  
* Вы можете адаптировать условие для работы с сносками, таблицами или любыми другими типами узлов.

## Пошаговое разбор

### 1. Установите Aspose.Words

Откройте терминал в папке проекта и выполните:

```bash
dotnet add package Aspose.Words
```

Пакет включает все сборки, необходимые для кода, показанного ранее.

### 2. Подготовьте входной файл

Поместите `Footnotes.docx` в известный каталог (например, `C:\Docs`). Убедитесь, что файл содержит хотя бы одну сноску и одну концевую сноску, чтобы узлы‑разделители существовали.

### 3. Напишите программу на C#

Создайте новый консольный проект (`dotnet new console -n FootnoteStyler`) и замените сгенерированный `Program.cs` полным блоком кода из раздела **How to change footnote separator**. Не забудьте скорректировать пути к файлам под вашу среду.

### 4. Запустите и проверьте

Выполните программу:

```bash
dotnet run
```

После завершения выполнения откройте `FootnoteSeparatorsStyled.docx`. Вы должны увидеть красную и синюю линии разделителей, как описано.

### 5. Расширьте решение

* **Different colors:** Используйте любое значение `System.Drawing.Color`, например `Color.FromArgb(255, 128, 0)` для оранжевого.  
* **Custom line style:** Вместо изменения цвета можно изменить свойства `ParagraphFormat`, такие как `LineSpacing`, `Shading` или даже заменить символ разделителя.  
* **Multiple documents:** Оберните логику в метод, принимающий пути входного и выходного файлов, и вызывайте его в цикле для пакетной обработки.

## Распространённые ошибки и как их избежать

| Признак | Причина | Решение |
|---------|----------|--------|
| `GetChild` returns `null` | В исходном документе отсутствует разделитель сносок/концевых сносок (например, нет сносок). | Добавьте хотя бы одну сноску или концевую сноску, либо проверяйте `null` перед доступом к `Font`. |
| Color change not visible | Разделитель отображается как линия, а не как символ в некоторых версиях Word. | Установите `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` и `ParagraphFormat.LineSpacing = 1`, чтобы принудительно отобразить символ. |
| Runtime exception `FileNotFoundException` | Неправильный путь к файлу. | Используйте абсолютные пути или `Path.Combine` с `Environment.CurrentDirectory`. |

## Полный, готовый к запуску пример

Ниже представлен полный код программы, который можно скопировать‑вставить в консольное приложение. Он содержит обработку ошибок и комментарии, объясняющие каждую операцию.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Запуск этой программы создаёт файл Word, где линия разделителя сносок красная, а линия разделителя концевых сносок синяя, удовлетворяя требованию **how to change footnote separator** и одновременно демонстрируя **change font color in word document**.

## Заключение

Теперь вы знаете **how to change footnote separator** в документе Word с помощью Aspose.Words for .NET и как **change font color in Word document** программно. Последовательность действий такова:

1. Загрузить документ.  
2. Получить скрытые абзацы‑разделители.  
3. Установить их свойства `Font.Color`.  
4. Сохранить изменённый файл.

Дальше вы можете исследовать более продвинутые стилизации — изменение толщины линии, применение разных шрифтов или автоматизацию процесса для множества файлов. Освоив эти техники, вы получаете тонкий контроль над внешним видом документов Word непосредственно из кода C#.

---


## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}