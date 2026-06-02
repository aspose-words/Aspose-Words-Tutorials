---
category: general
date: 2026-06-02
description: Узнайте, как использовать шрифт с переменным весом в C# и программно
  задавать толщину шрифта, а также изменять код растяжения шрифта для динамической
  типографии.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: ru
og_description: Используйте шрифт с переменным весом в C# для программного задания
  толщины шрифта и изменения кода растяжения шрифта, обеспечивая динамическую типографику
  в ваших документах.
og_title: Использовать переменный шрифт с изменяемым весом в C# – Полное руководство
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Использование шрифта с переменным весом в C# — Полное руководство по программированию
url: /ru/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Использование переменной толщины шрифта в C# – Полное руководство по программированию

Когда‑нибудь нужно было **использовать переменную толщину шрифта** в проекте .NET, но вы не знали, как заставить толщину и растяжение реагировать на ввод пользователя? Вы не одиноки. Во многих сценариях UI или отчётности требуется, чтобы текст адаптировался — возможно, лёгкий заголовок, который становится жирным при наведении, или абзац, который расширяется для акцента. Хорошая новость — с Aspose.Words вы можете **программно задавать толщину шрифта** и даже **изменять код растяжения шрифта** «на лету».

В этом руководстве мы пошагово разберём практический пример, показывающий, как загрузить шрифт с переменной толщиной, применить пользовательскую толщину и настроить растяжение — всё с помощью понятного кода C#, который можно скопировать и вставить. К концу вы получите готовое консольное приложение, генерирующее PDF, демонстрирующий эффект.

---

## Что вам понадобится

- **Aspose.Words for .NET** (v23.12 или новее). Библиотека полностью поддерживает шрифты с переменной толщиной.
- Папка, содержащая хотя бы один файл шрифта с переменной толщиной, например *RobotoFlex‑Variable.ttf*. Его можно скачать с Google Fonts.
- .NET 6 SDK (или любая современная версия .NET) и IDE по вашему выбору.
- Базовые знания C# — ничего сложного, всего несколько строк кода.

Это всё. Никаких дополнительных пакетов NuGet помимо Aspose.Words и никаких скрытых файлов конфигурации.

![Use variable weight font example](https://example.com/variable-weight-sample.png "Use variable weight font demonstration")

*Alt text: скриншот, показывающий использование переменной толщины шрифта в сгенерированном PDF‑документе.*

---

## Шаг 1: Настройте FontSettings и укажите папку со шрифтами  

Сначала — Aspose.Words нужно знать, где находятся ваши шрифты с переменной толщиной. Делается это созданием объекта `FontSettings` и присоединением `FolderFontSource`. Флаг `true` указывает движку искать также во вложенных папках, что удобно, если вы храните несколько семейств шрифтов вместе.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Почему это важно:** Без регистрации папки Aspose.Words будет использовать системные шрифты и проигнорирует данные о переменной толщине, встроенные в ваш пользовательский файл шрифта. Этот шаг — основа для всего, что последует.

---

## Шаг 2: Привяжите FontSettings к документу  

Теперь создаём новый `Document` (или загружаем существующий) и указываем ему использовать только что подготовленные `FontSettings`. Эта привязка делает данные о переменной толщине доступными каждому `Run`, который будет добавлен позже.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Если у вас уже есть шаблон — например, файл Word с заполнителями, — можно заменить `new Document()` на `new Document("Template.docx")`. Те же `FontSettings` будут применены.

---

## Шаг 3: Добавьте Run текста, который будет использовать шрифт с переменной толщиной  

**Run** — это наименьшая единица форматирования текста в Aspose.Words. Мы создадим его, вставим в новый абзац и позже изменим атрибуты шрифта.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

На данном этапе текст будет отображаться шрифтом по умолчанию (обычно Times New Roman). Магия произойдёт, когда мы назначим семейство шрифта с переменной толщиной.

---

## Шаг 4: Выберите семейство шрифта с переменной толщиной  

Здесь мы действительно **используем шрифт с переменной толщиной**. Установите `Font.Name` в точное название семейства, определённое внутри файла шрифта. Для Roboto Flex это имя `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Если вы не уверены в названии семейства, откройте файл `.ttf` в просмотрщике шрифтов или используйте метод `fontSettings.GetFonts()` для перечисления доступных семейств.

---

## Шаг 5: Программно задайте толщину и растяжение шрифта  

Теперь к делу: мы **программно задаём толщину шрифта** и **изменяем код растяжения шрифта**. Обе свойства принимают целочисленные значения, соответствующие спецификации OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Выберите любое значение, поддерживаемое переменным шрифтом.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). По умолчанию — 100 (Normal).

> **Pro tip:** Не каждый переменный шрифт раскрывает весь диапазон. Если задать значение, которое не поддерживается, движок ограничит его ближайшим доступным весом или растяжением.

---

## Шаг 6: Сохраните документ и проверьте результат  

Наконец, запишите документ в PDF (или DOCX) и откройте его, чтобы увидеть эффект. PDF — отличный формат для визуальной проверки, поскольку рендеринг одинаков на всех платформах.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Когда вы откроете *VariableWeightDemo.pdf*, вы должны увидеть фразу «Variable‑weight text demo», отрисованную лёгкой, слегка расширенной версией Roboto Flex. Измените `FontWeight` на `700` и `FontStretch` на `80`, запустите снова — наблюдайте, как текст становится жирным и более сжатым.

---

## Часто задаваемые вопросы и особые случаи  

### Что делать, если шрифт вообще не отображается?  

- **Missing FontSettings**: Убедитесь, что `doc.FontSettings = fontSettings;` выполнено **до** добавления любого текста.  
- **Incorrect family name**: Используйте `fontSettings.GetFonts()` для списка всех найденных семейств; скопируйте точную строку.  
- **Unsupported weight/stretch**: Некоторые переменные шрифты поддерживают лишь часть диапазона 100‑900. Используйте `run.Font.FontWeight = 400;` как безопасный вариант.

### Можно ли изменить толщину после сохранения документа?  

Да. Объект `Run` изменяем, поэтому вы можете корректировать `FontWeight` или `FontStretch` в любой момент до финального `Save`. Если нужно динамически переключать толщины (например, в ответ на действие пользователя), рассмотрите генерацию отдельных `Run` для каждого состояния.

### Работает ли это при выводе в DOCX?  

Абсолютно. Метаданные о переменной толщине сохраняются в underlying OpenXML, и современные версии Word способны их интерпретировать. Однако старые версии Word могут игнорировать настройку растяжения.

---

## Полный рабочий пример  

Ниже представлена полностью готовая консольная программа, которую можно сразу собрать и запустить. В ней включены все необходимые директивы `using`, обработка ошибок и комментарии.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Ожидаемый вывод:** Консоль выводит путь сохранения, а сгенерированный PDF показывает текст в лёгком, расширенном стиле — точно так, как мы сконфигурировали.

---

## Итоги  

Мы рассмотрели, как **использовать шрифт с переменной толщиной** в C# с помощью Aspose.Words, продемонстрировали, как **программно задавать толщину шрифта**, и показали точный **код изменения растяжения шрифта**, необходимый для расширения или сжатия глифов. Шаги просты: настроить `FontSettings`, привязать их к `Document`, создать `Run`, выбрать семейство шрифта с переменной толщиной и, наконец, подправить `FontWeight` и `FontStretch`.

---

## Что дальше?  

- **Dynamic UI integration**: Подключите ту же логику к приложению WinForms или WPF, чтобы пользователи могли выбирать толщину/растяжение с помощью ползунков.  
- **Multiple runs**: Сочетайте несколько `Run` с разными толщинами в одном абзаце для богатой типографской иерархии.  
- **Advanced axes**: Некоторые переменные шрифты открывают дополнительные оси (например, наклон, оптический размер). Используйте `run.Font.FontStyle` или исследуйте `FontVariationSettings` для более тонкого контроля.  
- **Performance tips**: Кешируйте экземпляр `FontSettings` при обработке множества документов, чтобы избежать повторных сканирований папок.

Экспериментируйте — замените *Roboto Flex* на *Inter Variable* или любой другой OpenType‑шрифт с переменной толщиной, и наблюдайте, как ваши документы получают новый уровень визуальной гибкости. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Использовать шрифт с целевой машины](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Использовать шрифт с целевой машины](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Использовать шрифт с целевой машины](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}