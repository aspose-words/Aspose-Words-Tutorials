---
category: general
date: 2026-06-27
description: Изменяйте стиль шрифта в документах Word с помощью C#. Узнайте, как задавать
  толщину шрифта, устанавливать полужирный вес и регулировать ширину шрифта для точной
  типографии.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: ru
og_description: Изменяйте стиль шрифта в документах Word с помощью C#. Узнайте, как
  установить толщину шрифта, задать полужирный вес и отрегулировать ширину шрифта
  в несколько простых шагов.
og_title: Изменение стиля шрифта в документах Word – полное руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Изменение стиля шрифта в документах Word – Полное руководство по C#
url: /ru/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Смена стиля шрифта в документах Word – Полное руководство на C#

Когда‑то вам нужно было **изменить стиль шрифта** в файле Word, но вы не знали, какой вызов API действительно решает задачу? Вы не одиноки — большинство разработчиков сталкиваются с этим, когда впервые пытаются программно менять типографику.  

Хорошая новость в том, что несколькими строками C# вы можете **установить вес шрифта**, даже задать более жирный вес, и точно настроить ширину каждого глифа. В этом руководстве мы пройдем полный, готовый к запуску пример, который изменяет файл `.docx` от начала до конца.

## Что покрывает это руководство

Мы начнём с загрузки существующего документа, затем создадим объект `FontSettings`, содержащий `FontVariation`. После этого мы **установим вес шрифта**, **установим жирный вес**, и **отрегулируем ширину шрифта**, а затем применим изменения и сохраним результат. Никаких внешних конфигурационных файлов, никаких «магических» строк — только чистый C# и библиотека Aspose.Words. К концу вы сможете **модифицировать шрифт в Word**‑документах с уверенностью, будь то построение отчётного движка или инструмент массового форматирования.

### Предварительные требования

- .NET 6.0 или новее (код также компилируется на .NET Core)  
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Пример `input.docx`, размещённый в папке, к которой вы можете обратиться (назовём её `YOUR_DIRECTORY`)  

Если у вас всё готово, давайте приступать.

---

## Шаг 1: Смена стиля шрифта – загрузка документа Word

Первое, что нужно сделать, — загрузить целевой файл в память. Представьте это как открытие чистого холста, на котором позже будет нарисована новая типографика.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Полезный совет:** Если вы запускаете код на сервере без UI, убедитесь, что лицензия Aspose.Words установлена в режим пробной версии или вы применили корректный файл лицензии, чтобы избежать сообщений о водяных знаках.

---

## Шаг 2: Установка веса шрифта и установка жирного веса

Теперь, когда документ находится в памяти, мы создаём контейнер `FontSettings`. Этот объект — шлюз ко всем возможным настройкам уровня шрифта.  

Класс `FontVariation` позволяет задать три основных атрибута:

| Свойство | Что делает | Типичный диапазон |
|----------|------------|-------------------|
| `Weight` | Управляет тем, насколько «тяжёлый» выглядит глиф. Значение **700** — стандартный «жирный». | 100‑900 |
| `Width`  | Растягивает или сжимает глиф по горизонтали. **100** — нормальная ширина. | 50‑200 |
| `Slant`  | Добавляет наклон, похожий на курсив. Положительные числа наклоняют вправо. | -90‑90 |

Ниже мы **устанавливаем вес шрифта** в 700 (жирный) и также показываем, как можно повысить его, если ваш шрифт поддерживает стиль «extra‑bold».

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Почему это важно:** Установка **жирного веса** напрямую через `SetWeight` избавляет от необходимости создавать отдельный объект стиля «Bold», предоставляя пиксель‑точный контроль над толщиной штрихов.

---

## Шаг 3: Регулировка ширины шрифта

Если вам когда‑нибудь нужно было сделать шрифт более плотным для заголовка или более просторным для абзаца, вы будете рады, что дошли до этого шага. Свойство `Width` делает именно это.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Распространённая ошибка:** Не каждый шрифт поддерживает изменения ширины. Если визуального эффекта нет, проверьте, поддерживает ли выбранное семейство шрифтов сжатые/расширенные глифы.

---

## Шаг 4: Применение настроек шрифта – модификация шрифта в Word

Когда наш `FontSettings` полностью сконфигурирован, последний шаг — сообщить документу использовать их. Здесь мы **модифицируем шрифт в Word** на уровне документа, влияя на каждый фрагмент текста, наследующий стиль по умолчанию.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Если нужно изменить только конкретный абзац или фрагмент, можно получить соответствующий узел и задать его `FontSettings` отдельно. Приведённый выше пример демонстрирует подход «широким мазком», идеальный для сценариев массового форматирования.

---

## Шаг 5: Сохранение и проверка изменений

Сохранение — последний, но определённо не менее важный, этап рабочего процесса. После записи файла вы можете открыть его в Microsoft Word и увидеть новое оформление в действии.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Ожидаемый результат

- Весь основной текст, ранее использующий шрифт по умолчанию, теперь отображается **жирным** (вес 700).  
- Если вы экспериментировали с `SetWidth(80)`, символы будут выглядеть чуть плотнее; `SetWidth(120)` — шире.  
- Другой контент (изображения, таблицы и т.д.) не изменяется — меняются только характеристики шрифта у текстовых фрагментов.

Откройте `output.docx` в Word, выделите абзац и откройте диалог **Font**. Вы увидите, что галочка **Bold** отмечена, а параметр **Scale** (ширина) отражает выбранное вами значение.

---

## Часто задаваемые вопросы и особые случаи

### Можно ли одновременно изменить семейство шрифта?

Конечно. После установки `FontVariation` вы также можете назначить новый `FontInfo` в `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### Как задать **жирный вес** только для заголовков?

Получите узел стиля заголовка и примените отдельный экземпляр `FontSettings`:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### Работает ли это с .NET Core на Linux?

Да — Aspose.Words кроссплатформенный. Просто убедитесь, что установлены необходимые библиотеки среды выполнения (`libgdiplus` в некоторых дистрибутивах), если планируете позже рендерить документ в PDF.

---

## Заключение

Мы только что **изменили стиль шрифта** в документе Word от начала до конца, рассмотрев, как **установить вес шрифта**, **установить жирный вес** и **регулировать ширину шрифта** с помощью C#. Полный, готовый к запуску пример демонстрирует каждый необходимый импорт, создание объектов и вызов методов, так что вы можете скопировать‑вставить его в свой проект и мгновенно увидеть трансформацию типографики.

Теперь, когда вы знаете, как **модифицировать шрифт в Word**, вы можете исследовать связанные темы, такие как **встраивание пользовательских шрифтов**, **применение градиентных цветов** или **создание динамических таблиц**. Все они опираются на ту же основу `FontSettings`, которую мы использовали здесь, так что вы уже на шаг впереди.

Есть сценарий, который не покрыт? Оставьте комментарий, и мы разберём его вместе. Приятного кодинга — и пусть ваши документы всегда выглядят именно так, как вы задумали!  

![change font style example](placeholder.png){alt="change font style example"}

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Set Font Emphasis Mark](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Set Font Fallback Settings](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Set Font Formatting](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}