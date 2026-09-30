---
category: general
date: 2026-02-12
description: Сохраните docx как txt и преобразуйте уравнения в LaTeX за один раз.
  Узнайте, как экспортировать математические формулы из Word с помощью C# и Aspose.Words.
draft: false
keywords:
- save docx as txt
- convert docx to txt
- how to export math
- convert equations to latex
- how to export equations
language: ru
og_description: Сохраните docx как txt и экспортируйте формулы в LaTeX с помощью C#.
  Пошаговое руководство по Aspose.Words.
og_title: Сохранить docx как txt – экспорт уравнений Word в LaTeX
tags:
- Aspose.Words
- C#
- Document Conversion
title: Сохранить docx как txt – экспортировать уравнения в LaTeX с Aspose.Words
url: /ru/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/
---

There's a link maybe? No.

We need to translate step-by-step.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить docx как txt – экспорт уравнений Word в LaTeX с помощью Aspose.Words

Когда‑то вам нужно было **сохранить docx как txt**, но вы сталкивались с проблемой, если документ содержит Office Math? Вы не одиноки. Большинство разработчиков полагают, что экспорт в простой текст просто удалит всё, однако уравнения исчезают, оставляя нечитаемый беспорядок.  

Хорошая новость? С Aspose.Words вы можете **сохранить docx как txt** *и* заставить библиотеку выводить каждое уравнение в виде кода LaTeX. В этом руководстве мы пройдем весь процесс, от загрузки файла `.docx` до получения чистого `.txt`, содержащего всю вашу математику в формате, готовом к научным публикациям.

К концу вы узнаете **как экспортировать математику** из Word, почему может потребоваться **преобразовать уравнения в LaTeX**, и как **преобразовать docx в txt** без потери важного содержимого.

## Что понадобится

- **Aspose.Words for .NET** (версия 23.8 или новее). Пакет NuGet — `Aspose.Words`.
- Среда разработки .NET (Visual Studio, Rider или VS Code с расширением C#).
- Пример документа Word (`input.docx`), содержащий хотя бы один объект Office Math.
- Базовые знания C# и консольных приложений.

Никакие сторонние инструменты не требуются; всё работает на чистом C#.

## Шаг 1 – Загрузка исходного документа

Первое, что мы делаем, — читаем файл Word в объект `Document`. Этот объект представляет весь пакет Word в памяти, давая доступ к абзацам, таблицам и скрытым узлам Office Math.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyFiles\input.docx");
```

> **Почему это важно:** Загрузка документа таким способом позволяет Aspose.Words сохранить оригинальную структуру, так что при последующем экспорте в TXT библиотека всё ещё знает, где находится каждое уравнение.

## Шаг 2 – Указать Aspose.Words, как обрабатывать Office Math

По умолчанию `TxtSaveOptions` просто записывает обычный текст и отбрасывает любую математику. Мы меняем это поведение, задавая `OfficeMathExportMode` значение `LaTeX`. Это заставляет движок заменять каждый объект Office Math его LaTeX‑представлением.

```csharp
// Step 2: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **Совет:** Если вам нужны уравнения в MathML, замените `OfficeMathExportMode.LaTeX` на `OfficeMathExportMode.MathML`. Один и тот же API работает для обоих форматов.

## Шаг 3 – Сохранить документ как файл простого текста

Теперь выполняем фактическое преобразование. Метод `Save` получает путь назначения и только что настроенные параметры.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save(@"C:\MyFiles\Equations.txt", txtSaveOptions);
```

Когда код выполнится, файл `Equations.txt` будет содержать:

```
This is a sample paragraph.
Here is an inline equation: $E = mc^2$
And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

> **Что вы видите:** Каждый объект Office Math теперь обёрнут в LaTeX‑делимитеры (`$…$` для встроенного, `\[`…`\]` для отображаемого). Обычный текст остаётся точно таким же, как в оригинальном DOCX.

## Полный, готовый к запуску пример

Ниже минимальное консольное приложение, которое можно скопировать в новый проект C# и сразу запустить.

```csharp
using System;
using Aspose.Words;

namespace DocxToTxtWithLatex
{
    class Program
    {
        static void Main(string[] args)
        {
            // Define input and output paths
            string inputPath = @"C:\MyFiles\input.docx";
            string outputPath = @"C:\MyFiles\Equations.txt";

            // Load the Word document
            Document doc = new Document(inputPath);

            // Configure save options – export equations as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX
            };

            // Perform the conversion
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"Successfully saved TXT with LaTeX equations to: {outputPath}");
        }
    }
}
```

### Ожидаемый результат

Откройте `Equations.txt` в любом текстовом редакторе. Вы увидите оригинальные абзацы, а каждое уравнение будет представлено как код LaTeX. Этот файл готов к передаче в компилятор LaTeX, markdown‑процессор или любую систему, понимающую синтаксис LaTeX.

## Часто задаваемые вопросы и особые случаи

### 1. *Что если в документе нет уравнений?*  
Преобразование всё равно выполнится; Aspose.Words просто запишет текстовое содержимое. Дополнительные LaTeX‑делимитеры добавлены не будут.

### 2. *Можно ли настроить делимитеры?*  
Да. `TxtSaveOptions` предоставляет свойства `InlineMathDelimiter` и `DisplayMathDelimiter`. Например:

```csharp
saveOptions.InlineMathDelimiter = @"\(";
saveOptions.DisplayMathDelimiter = @"\[\[";
```

### 3. *А как насчёт больших документов (сотни мегабайт)?*  
Aspose.Words потоково обрабатывает файл, поэтому потребление памяти остаётся умеренным. Тем не менее, при возникновении `OutOfMemoryException` можно увеличить параметр `MemoryUsage`.

### 4. *Гарантировано ли, что LaTeX‑вывод будет компилироваться?*  
Aspose.Words использует сопоставление Office Math → LaTeX, определённое Microsoft. Большинство распространённых конструкций (дроби, интегралы, суммы, матрицы) компилируются без проблем. Редкие символы могут потребовать ручной доработки.

### 5. *Можно ли экспортировать в другие форматы простого текста?*  
Конечно. Та же схема работает с `HtmlSaveOptions`, `MarkdownSaveOptions` и т.д. Просто замените `TxtSaveOptions` на нужный класс.

## Советы для безболезненной работы

- **Проверяйте вывод**: Запустите быстрый `pdflatex` на небольшом фрагменте, чтобы убедиться, что сгенерированный LaTeX не требует дополнительных пакетов.
- **Пакетная обработка**: Оберните приведённый код в цикл `foreach`, чтобы конвертировать сразу несколько файлов DOCX.
- **Логирование**: Используйте `Console.WriteLine` или полноценный логгер, чтобы фиксировать любые предупреждения Aspose.Words о неподдерживаемых математических конструкциях.
- **Проверка версии**: Перечисление `OfficeMathExportMode` появилось в Aspose.Words 22.9. Если у вас более старая версия, обновите пакет через NuGet.

## Заключение

Мы показали, как **сохранить docx как txt**, сохранив каждое уравнение в виде LaTeX. Трёхшаговый подход — загрузить, настроить, сохранить — охватывает весь рабочий процесс, а полный пример позволяет сразу вставить код в любой .NET‑проект.  

Если вам нужно **преобразовать docx в txt** для дальнейшей обработки, или вы просто хотите **как экспортировать уравнения** для научной статьи, этот метод надёжен и легко расширяется. Далее вы можете исследовать **как экспортировать математику** в другие разметки (MathML, ASCIIMath) или комбинировать TXT‑вывод со статическим генератором сайтов для документации.

Счастливого кодинга и безошибочных конвертаций!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}