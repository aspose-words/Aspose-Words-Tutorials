---
category: general
date: 2026-03-19
description: Создайте документ Word с использованием Aspose.Words и переменного шрифта.
  Узнайте, как изменить толщину шрифта, задать ширину шрифта и определить вариацию
  шрифта в C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: ru
og_description: Создайте документ Word с переменным шрифтом с помощью Aspose.Words.
  Этот учебник покажет, как загрузить шрифт, изменить его толщину, установить ширину
  и задать вариацию шрифта.
og_title: Создайте документ Word с переменным шрифтом — полное руководство
tags:
- Aspose.Words
- C#
- Variable Font
title: Создайте документ Word с переменным шрифтом — руководство
url: /ru/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа с переменным шрифтом – Руководство

Когда‑нибудь вам нужно было **создать Word‑документ**, использующий современный переменный шрифт, но вы не знали, с чего начать? Вы не одиноки. Во многих проектах — подумайте о динамических отчетах или брошюрах, соответствующих бренду — возможность **изменять толщину шрифта** «на лету» действительно меняет правила игры.  

В этом руководстве мы пройдем весь процесс: от загрузки переменного шрифта в Aspose.Words, до установки его веса и ширины, и, наконец, сохранения DOCX, который выглядит точно так, как вы задумали. Никаких расплывчатых ссылок, только конкретный код, который вы можете сразу вставить в свой проект C#.

## Что вы узнаете

- Как **загрузить переменный шрифт** в Aspose.Words с помощью `FontSettings`.
- Синтаксис для **определения осей вариаций шрифта** таких как `wght` (weight) и `wdth` (width).
- Способы **установить ширину шрифта** и **изменить толщину шрифта** в одном `Run`.
- Советы по устранению распространённых проблем (отсутствующие глифы, неверные пути к папкам и т.д.).
- Полный, готовый к запуску пример, который можно скопировать‑вставить и сразу протестировать.

> **Prerequisites**: .NET 6+ (or .NET Framework 4.6+), Aspose.Words for .NET installed via NuGet, and a variable‑font file like *RobotoFlex.ttf* placed in a local *Fonts* folder.

---

## Шаг 1 – Загрузка переменного шрифта в Aspose.Words

Сначала нужно указать Aspose.Words, где искать наши пользовательские шрифты. За это отвечает класс `FontSettings`.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Почему это важно**: Если не зарегистрировать папку, Aspose.Words будет использовать системные шрифты и проигнорирует любые данные OpenType‑вариаций, которые вы попытаетесь применить позже. Указав конкретный каталог, вы гарантируете, что *RobotoFlex* (или любой другой переменный шрифт) будет найден каждый раз при выполнении кода.

> **Pro tip**: Установите второй параметр `SetFontsFolder` в `true`, если хотите, чтобы Aspose также искал в подпапках. Это удобно, когда шрифты организованы по стилю или весу.

---

## Шаг 2 – Создание нового документа и добавление примера текста

Теперь, когда движок шрифтов знает, где искать файлы, создаём пустой `Document` и вставляем абзац с `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Что происходит**: `Run` представляет собой непрерывный фрагмент текста с единообразным форматированием. Создавая его сначала, мы изолируем логику форматирования — идеально для последующего применения разных осей вариаций к отдельным `Run`, если понадобится.

---

## Шаг 3 – Определение желаемых осей вариаций (Weight & Width)

Переменные шрифты раскрывают *оси*, которые можно менять во время выполнения. Две наиболее распространённые — `wght` (вес шрифта) и `wdth` (ширина шрифта). Aspose.Words моделирует это через коллекцию `OpenTypeFontVariation`.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Почему именно такие числа**: В спецификации OpenType `wght` варьируется от минимального до максимального веса шрифта (обычно 100–900). Значение **700** соответствует полужирному виду. `wdth` работает аналогично; **100** — это ширина по умолчанию (нормальная), а значения ниже 100 сжимают глифы.

> **Edge case**: Некоторые переменные шрифты не поддерживают определённую ось. Если задать неподдерживаемый тег, Aspose просто игнорирует его. Всегда проверяйте спецификацию шрифта (обычно находится в метаданных файла `.ttf` или `.otf`).

---

## Шаг 4 – Применение вариации к Run с указанием имени шрифта

Теперь привязываем данные вариации к реальному тексту. Класс `FontInfo` хранит название семейства шрифта и коллекцию осей.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explanation**: By setting `FontInfo`, we bypass the usual `Font.Name` property and hand the engine a fully‑qualified font configuration. This is the only way to tell Aspose.Words to use a variable font with custom axes.

> **Common mistake**: Forgetting to match the exact family name inside the font file (`RobotoFlex` in this example). A typo will cause Aspose to fall back to a default font, and your variation will be lost.

---

## Шаг 5 – Сохранение документа и проверка результата

Наконец, записываем документ на диск. Сгенерированный DOCX будет содержать инструкции для переменного шрифта, которые Microsoft Word (2016+) сможет корректно отобразить.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Откройте полученный файл в Word, выделите текст и посмотрите в диалог **Font**. Вы должны увидеть *Roboto Flex* в списке, а текст будет выглядеть жирнее окружающего контента — точно то, что задаёт настройка `wght = 700`.

> **Verification tip**: If the text looks unchanged, double‑check that the font file truly supports the `wght` axis. Some “variable” fonts only expose `ital` (italic) or `opsz` (optical size).

---

## Опционально: Добавьте больше вариаций — динамическое изменение ширины

Если хотите *установить ширину шрифта* иначе для другого абзаца, просто повторите шаги 3‑4 с новой коллекцией `OpenTypeFontVariation`.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Теперь у вас два `Run` — один жирный, другой немного шире — демонстрирующие как **change font weight**, так и **set font width** в одном документе.

---

## Полный рабочий пример

Скопируйте фрагмент ниже в новое консольное приложение (`Program.cs`) и запустите его. Убедитесь, что в папке `Fonts` находится `RobotoFlex.ttf` (или любой другой переменный шрифт по вашему выбору).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Expected output**: A `VariableFont.docx` file where the phrase “Variable‑weight text” appears bolded, thanks to the `wght = 700` axis, while retaining the default width.

---

## Часто задаваемые вопросы и особые случаи

| Question | Answer |
|----------|--------|
| *What if the font isn’t found?* | Verify the folder path, ensure the file name matches, and that the process has read permissions. You can also call `fontSettings.GetFonts()` to list detected fonts. |
| *Can I combine multiple runs with different variations?* | Absolutely. Each `Run` can carry its own `FontInfo`. Just repeat steps 3‑4 for each run. |
| *Do older versions of Word support variable fonts?* | Word 2016 (Build 16.0.8001) introduced basic support. If you target older versions, the document will fall back to the nearest static instance of the font. |
| *Is there a limit to how many axes I can set?* | You can set any number the font defines. Common tags are `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Supplying an unsupported tag simply has no effect. |
| *How do I debug missing glyphs?* | Use `FontSettings.GetFontSources()` to inspect loaded fonts, and `FontInfo.HasGlyph(char)` to test individual characters. |

---

## Заключение

В нескольких шагах мы показали **how to create word document** файлы, использующие мощь переменных шрифтов, позволяя вам **change font weight**, **set font width**, **load variable font** файлы и **define font variation** оси — всё это с помощью Aspose.Words for .NET.  

Основная идея проста: зарегистрировать папку со шрифтами, описать нужные оси, привязать их к `Run` и сохранить. Отсюда вы можете расширять технику на целые секции, таблицы или даже программно генерировать отчёты, соответствующие бренду.

**Next steps**: try swapping `RobotoFlex` for another variable font, experiment with the `ital` (italic) axis, or generate a PDF version of the same document using Aspose.PDF. The same pattern applies—load, define, apply, save.

Happy coding, and enjoy the flexibility that variable fonts bring to your Word automation projects!  

<img src="variable-font-demo.png" alt="Пример создания Word‑документа с переменным шрифтом">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}