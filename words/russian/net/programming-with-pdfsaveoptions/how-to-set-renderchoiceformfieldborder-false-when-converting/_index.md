---
category: general
date: 2026-09-21
description: Узнайте, как установить RenderChoiceFormFieldBorder в значение false
  в Aspose.Words, чтобы экспортировать поля формы Word без рамок. Включает полный
  код и рекомендации.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set renderchoiceformfieldborder false
- Aspose.Words PDF conversion
- disable choice field border
- PdfSaveOptions configuration
- Word form fields
- convert Word to PDF
language: ru
lastmod: 2026-09-21
og_description: Установите RenderChoiceFormFieldBorder в false, чтобы убрать границы
  полей выбора при преобразовании Word в PDF с помощью Aspose.Words.
og_image_alt: PDF preview showing choice form fields without borders after setting
  RenderChoiceFormFieldBorder false
og_title: Установите RenderChoiceFormFieldBorder в false для чистого экспорта PDF
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  headline: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  type: TechArticle
- description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  name: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  steps:
  - name: Additional PdfSaveOptions you may want to set
    text: '| Option | Typical value | When to use it | |----------------------------|---------------|----------------|
      | `Compliance` | `PdfCompliance.PdfA1b` | For archival PDFs | | `EmbedStandardFonts`
      | `true` | To avoid font substitution on other machines | | `SaveFormat` | `SaveFormat.Pdf`
      | Explicitly st'
  - name: Verifying the result
    text: Open `NoBorderChoice.pdf` in any PDF viewer (Adobe Acrobat, Foxit Reader,
      or the browser). You should see the drop‑down or combo‑box fields rendered as
      plain text placeholders—no gray rectangle is visible. The fields remain interactive;
      clicking on them still displays the list of choices.
  - name: Sample code for checking form fields
    text: '```csharp int choiceFieldCount = 0; foreach (FormField field in doc.Range.FormFields)
      { if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
      choiceFieldCount++; } Console.WriteLine($"Document contains {choiceFieldCount}
      choice form fields."); ```'
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- C#
- Form fields
title: Как установить RenderChoiceFormFieldBorder в false при конвертации Word в PDF
url: /ru/net/programming-with-pdfsaveoptions/how-to-set-renderchoiceformfieldborder-false-when-converting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить RenderChoiceFormFieldBorder в false при конвертации Word в PDF

Если вам необходимо **установить RenderChoiceFormFieldBorder в false** при экспорте документа Word, содержащего поля выбора, это руководство покажет вам точные шаги. Отключив отрисовку границы, полученный PDF выглядит чище и соответствует макету оригинального документа.

В этом учебнике вы узнаете, как настроить **PdfSaveOptions** в Aspose.Words, почему эта настройка важна и как обрабатывать типичные граничные случаи, такие как документы без каких‑либо полей формы. Решение работает с последней версией Aspose.Words for .NET (v23.10 на момент написания) и требует всего несколько строк кода на C#.

## Prerequisites

Перед началом убедитесь, что у вас есть:

* .NET 6.0 или новее установлен.
* Действительная лицензия Aspose.Words for .NET (или бесплатный оценочный ключ).
* Документ Word (`.docx`), содержащий поля выбора (например, выпадающие списки или комбинированные поля).
* Visual Studio 2022 (или любая IDE для C#).

## Step 1: Load the source Word document

Первый шаг — создать объект `Document`, представляющий ваш исходный файл. Aspose.Words читает файл в память, позволяя вам просматривать или изменять его содержимое перед конвертацией.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word document that contains choice form fields
Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");
```

**Why this matters:** Загрузка документа дает доступ к коллекции полей формы, которую позже можно проверить, чтобы убедиться, что файл действительно содержит поля выбора. Если в документе нет таких полей, настройка `RenderChoiceFormFieldBorder` визуально не влияет, но код всё равно выполнится безопасно.

## Step 2: Configure PdfSaveOptions and set RenderChoiceFormFieldBorder false

`PdfSaveOptions` управляет каждым аспектом вывода PDF, от качества изображений до отрисовки полей формы. Установка `RenderChoiceFormFieldBorder` в `false` сообщает рендереру не рисовать серый прямоугольник, обычно окружающий выпадающие списки и комбинированные поля.

```csharp
// Create PDF save options and disable the rendering of choice field borders
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false
};
```

**Why this matters:** По умолчанию Aspose.Words рисует тонкую границу вокруг полей выбора, чтобы пользователь видел, где можно взаимодействовать. Во многих сценариях публикации — например, печатных формах или отшлифованных отчётах — такая граница нежелательна. Флаг `RenderChoiceFormFieldBorder` предоставляет однострочный способ отключить её.

### Additional PdfSaveOptions you may want to set

| Option                     | Typical value                | When to use it                                          |
|----------------------------|------------------------------|----------------------------------------------------------|
| `Compliance`               | `PdfCompliance.PdfA1b`       | Для архивных PDF                                         |
| `EmbedStandardFonts`       | `true`                       | Чтобы избежать подстановки шрифтов на других компьютерах |
| `SaveFormat`               | `SaveFormat.Pdf`             | Явно указывает целевой формат (необязательно)           |

You can chain these settings with the border flag:

```csharp
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false,
    Compliance = PdfCompliance.PdfA1b,
    EmbedStandardFonts = true
};
```

## Step 3: Save the document as a PDF using the configured options

Теперь, когда параметры заданы, вызовите `Document.Save` с указанием пути назначения и экземпляра `PdfSaveOptions`.

```csharp
// Save the document as a PDF using the configured options
doc.Save("YOUR_DIRECTORY/NoBorderChoice.pdf", pdfOptions);
```

**Why this matters:** Метод `Save` выполняет фактическую конвертацию. Поскольку `pdfOptions` содержит `RenderChoiceFormFieldBorder = false`, полученный PDF будет содержать поля выбора **без** окружающей границы.

### Verifying the result

Откройте `NoBorderChoice.pdf` в любом PDF‑просмотрщике (Adobe Acrobat, Foxit Reader или браузере). Вы должны увидеть поля выпадающих списков или комбинированных полей как простые текстовые заполнители — серый прямоугольник не виден. Поля остаются интерактивными; при клике по ним по‑прежнему отображается список вариантов.

## Handling edge cases

| Situation                              | Recommended approach                                                                                                                                                                                                 |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Document has no choice form fields** | Флаг границы не оказывает эффекта. При желании можно проверить `doc.Range.FormFields.Count` перед конвертацией, чтобы пропустить ненужную конфигурацию.                                                            |
| **Password‑protected Word file**       | Загрузите документ с помощью объекта `LoadOptions`, включающего пароль, а затем примените те же `PdfSaveOptions`.                                                                                                   |
| **Large documents (> 100 MB)**         | Используйте параметры `MemoryOptimization` в `PdfSaveOptions` для снижения потребления памяти во время конвертации.                                                                                                 |
| **Need to keep the border for specific fields** | После загрузки документа пройдитесь по `doc.Range.FormFields`, установите `FieldType` в `FieldType.FieldFormDropDown` или `FieldFormComboBox` и вручную измените свойство `Border` перед сохранением.               |

### Sample code for checking form fields

```csharp
int choiceFieldCount = 0;
foreach (FormField field in doc.Range.FormFields)
{
    if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
        choiceFieldCount++;
}
Console.WriteLine($"Document contains {choiceFieldCount} choice form fields.");
```

Если `choiceFieldCount` равен нулю, вы можете полностью пропустить настройку границы, что сэкономит небольшое количество времени обработки.

## Full working example

Ниже приведена полная, готовая к запуску программа, объединяющая все шаги. Замените `YOUR_DIRECTORY` реальным путём на вашем компьютере.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");

        // Optional: verify that the document contains choice fields
        int choiceCount = 0;
        foreach (FormField field in doc.Range.FormFields)
        {
            if (field.Type == FieldType.FieldFormDropDown ||
                field.Type == FieldType.FieldFormComboBox)
                choiceCount++;
        }
        Console.WriteLine($"Found {choiceCount} choice form fields.");

        // 2️⃣ Configure PdfSaveOptions and set RenderChoiceFormFieldBorder false
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            RenderChoiceFormFieldBorder = false,
            // Example of additional options you might need
            Compliance = PdfCompliance.PdfA1b,
            EmbedStandardFonts = true
        };

        // 3️⃣ Save the PDF
        string outputPath = "YOUR_DIRECTORY/NoBorderChoice.pdf";
        doc.Save(outputPath, pdfOptions);
        Console.WriteLine($"PDF saved to {outputPath} with borders disabled.");
    }
}
```

**Expected output in the console**

```
Found 3 choice form fields.
PDF saved to C:\MyProjects\NoBorderChoice.pdf with borders disabled.
```

Когда откроете `NoBorderChoice.pdf`, поля выпадающих списков будут отображаться без стандартной серой границы, делая документ визуально чище, но сохраняя интерактивность.

## Pro tips and common pitfalls

* **Pro tip:** Если вы генерируете PDF в веб‑службе, явно задайте `pdfOptions.SaveFormat = SaveFormat.Pdf`, чтобы избежать случайных проблем с определением формата.
* **Watch out for:** Старые версии Aspose.Words (до v20) не предоставляют `RenderChoiceFormFieldBorder`. Обновитесь до последней версии, чтобы использовать этот флаг.
* **Performance tip:** При пакетной конвертации множества документов переиспользуйте один экземпляр `PdfSaveOptions`; создание нового объекта каждый раз добавляет лишние накладные расходы.
* **Testing tip:** Добавьте модульный тест, который загружает известный `.docx` с выпадающим списком, выполняет конвертацию и проверяет, что полученный PDF‑поток не содержит аннотации `/Border` для этих полей.

## Conclusion

Теперь вы знаете, **как установить RenderChoiceFormFieldBorder в false**, чтобы генерировать PDF без границ полей выбора, используя Aspose.Words. Решение охватывает загрузку документа, настройку `PdfSaveOptions`, сохранение PDF и обработку граничных случаев, таких как отсутствие полей формы или защищённые паролем источники.  

Далее вы можете изучить связанные темы, такие как **отключение границы поля выбора** для других типов полей формы, или узнать, как **конвертировать Word в PDF** с пользовательским разрешением изображений, используя `ImageSaveOptions`. Оба направления углубят ваше владение **Aspose.Words PDF conversion** и дадут полный контроль над внешним видом конечного документа.

Удачной разработки!

## Что стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [конвертировать Word в PDF на C# с помощью Aspose.Words – Руководство](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [Сохранить Word как PDF с Aspose Words – Полное руководство на C#](/words/hindi/net/programming-with-pdfsaveoptions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Конвертировать Word в PDF с Aspose.Words для Java](/words/english/java/document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}