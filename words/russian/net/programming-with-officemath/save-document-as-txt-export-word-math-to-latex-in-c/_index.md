---
category: general
date: 2026-04-24
description: Сохраните документ как txt и преобразуйте Word в LaTeX с помощью Aspose.Words.
  Узнайте, как быстро экспортировать математические уравнения Word в LaTeX.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: ru
og_description: Сохраните документ в формате txt и преобразуйте уравнения Word в LaTeX
  с помощью C#. Полное пошаговое руководство с кодом.
og_title: Сохранить документ как TXT – экспортировать формулы Word в LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Сохранить документ как TXT – экспортировать формулы Word в LaTeX на C#
url: /ru/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить документ как TXT – экспортировать математические формулы Word в LaTeX на C#

Когда‑нибудь нужно было **сохранить документ как txt**, не теряя при этом сложные уравнения? Вы не одиноки. Встроенная в Word функция «Сохранить как обычный текст» удаляет Office Math, оставляя нечитаемый мусор. А что, если можно сохранить эти уравнения в чистом LaTeX?

В этом руководстве мы пошагово покажем, как **convert Word to LaTeX**‑готовый текст с помощью Aspose.Words for .NET. В итоге у вас будет файл `.txt`, где каждое уравнение представлено корректным LaTeX‑разметкой, готовым к вставке в статью или markdown‑файл. Никаких внешних конвертеров, без ручного копирования‑вставки — только несколько строк C#.

## Что вы узнаете

- Как загрузить файл `.docx` с помощью Aspose.Words.  
- Настройка `TxtSaveOptions` для экспорта Office Math в LaTeX.  
- Сохранение результата в обычный текстовый файл, который можно открыть в любом редакторе.  
- Обработка граничных случаев для встроенных и отображаемых уравнений, а также быстрый совет по пакетной обработке нескольких документов.

### Требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+).  
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Документ Word, содержащий хотя бы одно уравнение (объект Office Math).

---

## Шаг 1: Установить Aspose.Words и настроить проект

Сначала добавьте библиотеку в ваш проект. Откройте терминал в папке решения и выполните:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Если вы используете Visual Studio, менеджер пакетов NuGet UI работает так же — найдите “Aspose.Words” и нажмите Install.

Теперь создайте новое консольное приложение (или вставьте код в существующее). Необходимые директивы `using`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Эти директивы делают доступными класс `Document` и тип `TxtSaveOptions`.

## Шаг 2: Загрузить исходный документ

Нужно указать Aspose.Words путь к файлу Word, содержащему уравнения. Замените `YOUR_DIRECTORY/input.docx` реальным путём на вашем компьютере.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Why this matters:** Загрузка документа даёт Aspose.Words полный доступ к внутренним объектам Office Math, которые иначе невидимы простому экспортёру текста.

## Шаг 3: Настроить TxtSaveOptions для экспорта в LaTeX

Всё волшебство происходит в объекте `TxtSaveOptions`. Установив `OfficeMathExportMode` в `LaTeX`, каждое уравнение преобразуется в его LaTeX‑эквивалент.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **What if you need MathML instead?** Измените `OfficeMathExportMode` на `MathML`. Тот же API поддерживает несколько форматов вывода.

## Шаг 4: Сохранить документ как обычный текст

Теперь записываем файл. Полученный `Math.txt` будет содержать обычный текст плюс фрагменты LaTeX для каждого уравнения.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Запуск программы создаёт файл, выглядящий примерно так:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Обратите внимание, что встроенное уравнение оформлено `$…$`, а отображаемое — в `\[` и `\]`. Это стандартный стиль LaTeX, и Aspose.Words делает это автоматически.

## Шаг 5: Проверить результат (по желанию)

Если хотите убедиться, что LaTeX корректен, передайте `.txt` в компилятор LaTeX, например `pdflatex`, или в онлайн‑рендерер вроде Overleaf. Текст должен компилироваться без ошибок, а уравнения появятся точно так же, как в Word.

```bash
pdflatex Math.txt
```

Если появляется ошибка «Undefined control sequence», убедитесь, что в преамбулу вашего большого LaTeX‑документа включены необходимые пакеты (например, `amsmath`).

## Обработка распространённых вариантов

### Конвертация нескольких файлов в папке

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Работа с встроенными и отображаемыми уравнениями

Aspose.Words автоматически определяет тип уравнения по его расположению в Word. Если нужно принудительно задать стиль, можно пост‑обработать вывод:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Экспорт в другие форматы

Если LaTeX не ваш целевой формат, просто смените режим экспорта:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Или используйте `HtmlSaveOptions`, если предпочитаете MathML, встроенный в HTML.

---

## Полный рабочий пример

Ниже полностью готовая к запуску программа. Скопируйте её в `Program.cs` проекта консольного приложения .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Запустите программу (`dotnet run`), откройте `Math.txt`, и вы увидите содержимое Word с сохранёнными уравнениями в LaTeX.

---

## Часто задаваемые вопросы

**Q: Работает ли это со старыми файлами .doc?**  
A: Да — Aspose.Words может открывать устаревшие файлы `.doc`, но сложные уравнения могут быть сохранены как изображения. В таком случае экспортёр заменит их комментариями‑заполнителями.

**Q: Что делать, если уравнение содержит пользовательские символы?**  
A: Aspose.Words сопоставляет большинство символов Office Math со стандартными командами LaTeX. Для действительно уникальных символов, вероятно, придётся вручную отредактировать сгенерированный LaTeX.

**Q: Выводится ли файл в кодировке UTF‑8?**  
A: По умолчанию `TxtSaveOptions` записывает в UTF‑8, что безопасно для большинства языков и символов.

---

## Заключение

Теперь вы знаете, как **save document as txt**, сохраняя каждое уравнение в виде чистой LaTeX‑разметки. Этот подход позволяет **convert Word to LaTeX** без сторонних инструментов и масштабируется от одного файла до целых папок. Далее вы можете изучить **convert word equations to LaTeX** для пакетной обработки или погрузиться в **export word math latex** для HTML‑ или Markdown‑конвейеров.

Экспериментируйте — меняйте `OfficeMathExportMode` на MathML, настраивайте обработку разрывов строк или интегрируйте этот фрагмент в более крупный процесс генерации документов. Приятного кодинга, и пусть ваши уравнения всегда отображаются безупречно!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}