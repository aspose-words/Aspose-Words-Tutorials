---
category: general
date: 2026-01-08
description: Узнайте, как экспортировать LaTeX из файла DOCX с помощью Aspose.Words —
  конвертировать docx в markdown, сохранять Word как markdown и сохранять docx как
  txt за считанные минуты.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save word as markdown
- save docx as markdown
- save docx as txt
language: ru
og_description: Пошаговое руководство по экспорту LaTeX из документов Word, конвертации
  docx в markdown и сохранению docx в txt с помощью Aspose.Words.
og_title: 'Как экспортировать LaTeX: преобразовать DOCX в Markdown и TXT'
tags:
- Aspose.Words
- C#
- Document Conversion
title: 'Как экспортировать LaTeX: преобразовать DOCX в Markdown и TXT'
url: /ru/net/programming-with-markdownsaveoptions/how-to-export-latex-convert-docx-to-markdown-txt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как экспортировать LaTeX из документов Word  

Когда‑нибудь вам нужно было **как экспортировать latex** из файла Word, но вы не знали, какой API использовать? Вы не одиноки — разработчики постоянно спрашивают: «Могу ли я сохранить свои уравнения, когда преобразую .docx в более лёгкий формат, например markdown?»

Краткий ответ — **да**. С помощью Aspose.Words вы можете преобразовать docx в markdown, сохранить Word как markdown и даже сохранить docx как txt, сохраняя оригинальные уравнения Office Math в виде LaTeX. В этом руководстве мы пройдем весь процесс, объясним, почему важна каждая настройка, и предоставим готовый к запуску пример кода.

## Что понадобится  

- .NET 6+ (или .NET Framework 4.7.2+).  
- Ссылка на пакет NuGet **Aspose.Words** (`Install-Package Aspose.Words`).  
- Документ Word (`input.docx`), содержащий хотя бы одно уравнение (OfficeMath).  

Вот и всё. Никаких дополнительных конвертеров, никаких сложных скриптов пост‑обработки.

![Как экспортировать LaTeX из Word](/images/export-latex-word.png)

*Текст alt изображения: как экспортировать latex из документа Word с помощью Aspose.Words*

## Шаг 1: Как экспортировать LaTeX — настройка проекта  

Сначала создайте новое консольное приложение (или интегрируйте код в любой существующий проект C#). Добавьте необходимые директивы `using`, чтобы компилятор знал, где находятся классы:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Зачем нужен неймспейс `Aspose.Words.Saving`? В нём находятся классы `MarkdownSaveOptions` и `TxtSaveOptions`, позволяющие задавать, как будут отображаться объекты OfficeMath. Без этих параметров вы получите общие заполнители вместо настоящего LaTeX.

## Шаг 2: Загрузка исходного DOCX  

```csharp
// Step 2: Load the source document containing equations
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Если файл не найден, Aspose бросает `FileNotFoundException`. Быстрый совет: держите входной файл рядом с исполняемым файлом во время разработки или используйте абсолютный путь в продакшн‑скриптах.

## Шаг 3: Преобразование DOCX в Markdown — экспорт LaTeX  

Markdown — популярный лёгкий формат, но по умолчанию он отбрасывает OfficeMath. Чтобы сохранить уравнения, настройте `MarkdownSaveOptions`:

```csharp
// Step 3: Configure Markdown save options to export OfficeMath as LaTeX
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This tells Aspose to render each equation as a LaTeX block
    OfficeMathExportMode = OfficeMathExportMode.LaTeX   // alternatives: MathML, Text
};
```

**Почему LaTeX?** LaTeX является де‑факто стандартом для научных документов; большинство рендереров markdown (GitHub, MkDocs, Jekyll) понимают блоки `$…$` или `$$…$$`. Если вы предпочитаете MathML для веб‑рендеринга, просто замените значение перечисления.

Теперь сохраните файл markdown:

```csharp
// Step 4: Save the document as a Markdown file with LaTeX equations
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

Полученный `output.md` будет содержать примерно следующее:

```markdown
Here is an equation:

$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

## Шаг 4: Сохранение DOCX как TXT — сохранение LaTeX в строке  

Иногда нужен просто обычный текст — возможно, для быстрого поискового индекса. Тот же `OfficeMathExportMode` работает с `TxtSaveOptions`:

```csharp
// Step 5: Configure plain‑text (TXT) save options to export OfficeMath as LaTeX
TxtSaveOptions textOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};

// Step 6: Save the document as a plain‑text file with LaTeX equations
document.Save("YOUR_DIRECTORY/output.txt", textOptions);
```

`output.txt` будет содержать представление LaTeX встроенно в окружающий текст, делая его доступным для поиска и при этом математически корректным.

## Общие варианты и граничные случаи  

| Сценарий | Рекомендуемая настройка | Почему |
|----------|------------------------|--------|
| Вам нужен MathML для веб‑страницы | `OfficeMathExportMode.MathML` | MathML нативно понимается браузерами, поддерживающими MathML. |
| Вы хотите только текст уравнения без форматирования | `OfficeMathExportMode.Text` | Убирает символы LaTeX, оставляя обычные символы Unicode для математики. |
| Ваш документ содержит изображения, которые также нужны в markdown | Установите `markdownOptions.ImagesFolder = "images"` и `markdownOptions.ExportAsBase64 = false` | Сохраняет изображения отдельными файлами, что ожидают многие генераторы статических сайтов. |
| Большие документы вызывают нагрузку на память | Используйте `Document.LoadOptions` с `LoadFormat.Docx` и обрабатывайте страницы по частям | Предотвращает загрузку всего файла в память сразу. |

**Совет профессионала:** Всегда тестируйте сгенерированный markdown в целевом рендерере (GitHub, предпросмотр VS Code и т.д.), потому что некоторые платформы поддерживают только `$…$` для встроенной математики и `$$…$$` для отображаемой.

## Полный рабочий пример  

Ниже приведена полная, готовая к копированию и вставке программа, включающая каждый описанный шаг:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace ExportLatexDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Adjust these paths to match your environment
            string inputPath = "YOUR_DIRECTORY/input.docx";
            string markdownPath = "YOUR_DIRECTORY/output.md";
            string txtPath = "YOUR_DIRECTORY/output.txt";

            // Load the source document
            Document doc = new Document(inputPath);

            // ---------- Export to Markdown ----------
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                // Optional: keep images as separate files
                ExportImagesAsBase64 = false,
                ImagesFolder = "images"
            };
            doc.Save(markdownPath, mdOptions);
            Console.WriteLine($"Markdown with LaTeX saved to: {markdownPath}");

            // ---------- Export to Plain Text ----------
            TxtSaveOptions txtOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX
            };
            doc.Save(txtPath, txtOptions);
            Console.WriteLine($"Plain‑text with LaTeX saved to: {txtPath}");
        }
    }
}
```

Запустите программу (`dotnet run`), и вы получите два файла, сохраняющих каждое уравнение в виде LaTeX — именно то, что нужно, когда вы разбираетесь, **как экспортировать latex** из Word.

## Часто задаваемые вопросы  

**В: Работает ли это с файлами .doc (старый бинарный формат)?**  
**О:** Да. Aspose.Words может загружать файлы `.doc` тем же способом; просто укажите `new Document("file.doc")`. Логика экспорта LaTeX остаётся той же.

**В: Что если уравнение содержит неподдерживаемые символы?**  
**О:** Aspose заменит их ближайшим представлением Unicode. Для действительно экзотических символов может потребоваться пост‑обработка строки LaTeX.

**В: Могу ли я пакетно обрабатывать папку с файлами DOCX?**  
**О:** Конечно. Оберните логику `Main` в цикл `foreach (var file in Directory.GetFiles(folder, "*.docx"))` и соответственно скорректируйте имена выходных файлов.

## Заключение  

Теперь вы знаете, **как экспортировать LaTeX** из документов Word с помощью Aspose.Words, как **преобразовать docx в markdown**, как **сохранить Word как markdown**, и как **сохранить docx как txt**, сохраняя каждое уравнение в целости. Главное — свойство `OfficeMathExportMode`: установите его в `LaTeX`, и библиотека выполнит всю тяжелую работу за вас.

Что дальше? Попробуйте переключить режим экспорта на MathML, поэкспериментировать с параметрами обработки изображений или интегрировать эту логику в CI‑конвейер, который автоматически генерирует документацию из ваших исходных файлов `.docx`. Возможностей бесконечно много, а написанный вами код — надёжная основа.

Удачной разработки, и пусть ваши уравнения всегда отображаются идеально!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}