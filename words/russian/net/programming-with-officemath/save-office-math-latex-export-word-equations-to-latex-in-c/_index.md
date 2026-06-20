---
category: general
date: 2026-04-21
description: Сохраняйте математические формулы Office в LaTeX быстро с помощью Aspose.Words –
  также узнайте, как сохранить обычный текст Word и экспортировать уравнения Word
  в LaTeX за один раз.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: ru
og_description: Сохраняйте математические формулы Office в LaTeX мгновенно; узнайте,
  как экспортировать уравнения Word в LaTeX и конвертировать математические формулы
  Word в LaTeX с помощью Aspose.Words на C#.
og_title: save office math latex – экспортировать уравнения Word в LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: save office math latex – Экспорт уравнений Word в LaTeX на C#
url: /ru/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Export Word equations to LaTeX with Aspose.Words

Когда‑то вам нужно было **save office math latex** из файла `.docx`, но вы не знали, с чего начать? Вы не одиноки, и хорошая новость в том, что решение довольно простое. В этом руководстве мы пройдём пошагово процесс экспорта уравнений Word в LaTeX (и даже MathML) с помощью Aspose.Words for .NET, одновременно показывая, как **save word plain text** вместе с математикой.

Мы расскажем обо всём, что может вас заинтересовать: почему стоит выбрать LaTeX вместо других форматов, как настроить `TxtSaveOptions` и что делать, если нужно **convert word math latex** в другое представление. В конце вы получите готовый фрагмент кода, который берёт документ Word с объектами Office Math и создаёт чистый файл `.txt` с уравнениями LaTeX (или MathML). Никаких внешних инструментов, никаких ручных копирований — просто чистый C#‑код, который можно вставить в любой проект.

## Prerequisites

- **Aspose.Words for .NET** (v23.10 или новее). Пакет NuGet — `Aspose.Words`.
- Среда разработки .NET (Visual Studio, Rider или VS Code с расширением C#).
- Файл Word (`.docx`), содержащий хотя бы одно уравнение, созданное в редакторе Office Math.
- Базовое знакомство с синтаксисом C# — ничего сложного, только обычные `using`‑директивы.

Если все пункты уже выполнены, отлично — погнали.

## Step 1 – Set up **save office math latex** options

Первое, что нужно сделать, — сообщить Aspose.Words, как отобразить математическое содержимое. Класс `TxtSaveOptions` имеет свойство `OfficeMathExportMode`, которое принимает три значения: `LaTeX`, `MathML` или `Text`. Для нашей основной задачи выберем `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Why this matters:** When you set `OfficeMathExportMode` to `LaTeX`, each equation is transformed into its raw LaTeX source. That source can later be compiled with any LaTeX engine, giving you pixel‑perfect typesetting without the need to re‑type the formulas.

> **Pro tip:** If you ever need to **convert word equations mathml**, just swap the enum value to `OfficeMathExportMode.MathML`. The rest of the code stays the same.

## Step 2 – Load the Word document (the **save word plain text** scenario)

Next, we load the source `.docx`. This step is identical whether you’re only interested in plain‑text extraction or you also want the equations in LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**What’s happening here?** The `Document` constructor reads the file into memory. The quick check with `GetChildNodes` helps you catch a common edge case—trying to export LaTeX from a file that contains no equations. It’s a tiny safeguard that saves you a puzzling empty output later.

## Step 3 – **save office math latex** to a plain‑text file

Now we finally write the file. The `Save` method respects the `TxtSaveOptions` we configured earlier, so the resulting `.txt` will contain both regular text and LaTeX snippets for each equation.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

When you open `Equations.txt` you’ll see something like:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

The LaTeX blocks are wrapped in `\begin{equation}` … `\end{equation}` automatically, which makes them ready for inclusion in any LaTeX document.

## Step 4 – Alternative: **convert word equations mathml** instead of LaTeX

If your downstream toolchain prefers MathML (for example, a web page that renders equations with MathJax), just change the export mode:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

The output will now contain XML‑style MathML tags, like:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

That’s the quick way to **convert word equations mathml** without writing a custom parser.

## Step 5 – Bonus: **save word plain text** while keeping equations separate

Sometimes you want a clean text version of the document *without* any LaTeX or MathML embedded. You can achieve that by switching the export mode to `Text` and running a second save pass:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Now you have three files side‑by‑side:

| Файл                         | Содержание                               |
|------------------------------|------------------------------------------|
| `Equations.txt`              | Обычный текст **+** уравнения LaTeX      |
| `EquationsMathML.txt`        | Обычный текст **+** уравнения MathML    |
| `PlainDocument.txt`          | Чистый текст, уравнения удалены          |

This pattern is handy when you need to feed the plain text into a search index while still preserving the original math for academic publishing.

## Full Working Example (Copy‑Paste Ready)

Below is the complete program you can compile and run as is. It demonstrates **save office math latex**, **export word equations latex**, **convert word math latex**, and **save word plain text**—all in one tidy script.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Expected result:** After running, you’ll find three text files in `C:\MyDocs`. Open `Equations.txt` and you’ll see LaTeX blocks; `EquationsMathML.txt` will contain MathML; `PlainDocument.txt` will be free of any equation markup.

## Common Questions & Edge Cases

- **What if I only need LaTeX for a subset of equations?**  
  Use the `OfficeMath` node API to iterate over each equation, export it manually with `MathConverter`, and replace the placeholder text where you want. That approach gives you fine‑grained control but adds a few extra lines of code.

- **Does this work with .NET Core / .NET 5+?**  
  Absolutely. Aspose.Words is cross‑platform, so the same code runs on Windows, Linux, and macOS as long as the runtime version matches the library’s requirements.

- **Can I change the LaTeX wrapper (`\begin{equation}`) to something else?**  
  Yes. Set `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` and then modify `txtOptions.MathExportSettings` (available in newer releases) to customize delimiters.

- **Performance concerns for huge documents?**  
  The library streams the output, so memory usage stays modest. However

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}