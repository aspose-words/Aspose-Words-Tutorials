---
category: general
date: 2026-10-13
description: Изучите замену шрифтов в документе с помощью C#. Это руководство показывает,
  как установить кодировку big5, загрузить DOCX и заменить устаревшие шрифты современными.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: ru
lastmod: 2026-10-13
og_description: Замена шрифтов в документе имеет решающее значение при работе с устаревшими
  китайскими файлами. Следуйте этому пошаговому руководству, чтобы загрузить DOCX
  с кодировкой big5 и заменить старые шрифты.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Замена шрифтов в документе с помощью C# – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Как выполнить замену шрифта в документе с помощью C#
url: /ru/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Замена шрифтов в документе – полный учебник C# 

Если вам нужна **font substitution in document** для корректного отображения устаревших китайских файлов, это руководство покажет, как это сделать. Настроив правильную кодировку текста и заменив устаревший шрифт на современный, вы гарантируете, что итоговый DOCX будет отображаться как задумано.

Обработка документов часто ломается, когда источник использует старую кодировку, такую как **big5**, или ссылается на шрифт, который больше не существует в системе. В этом учебнике вы пройдёте процесс загрузки DOCX с правильной **big5 encoding**, применения **legacy font replacement** и получения чистого результата, который работает на любой машине с Windows.

Вы узнаете:

* Как создать объект `LoadOptions` с **big5 encoding**.  
* Как открыть файл DOCX, используя **C# LoadOptions**.  
* Как выполнить **font substitution in document**, сопоставив старый шрифт с современным эквивалентом.  
* Обработку граничных случаев для отсутствующих шрифтов и нескольких семейств шрифтов.

Никакие внешние инструменты не требуются, кроме библиотеки Aspose.Words for .NET, а полный код можно скопировать в консольный проект и запустить сразу.

## Предварительные требования

* .NET 6.0 или новее (пример использует синтаксис консоли .NET 6).  
* Aspose.Words for .NET – установить через `dotnet add package Aspose.Words`.  
* Файл DOCX, сохранённый с **big5 encoding**, который ссылается на устаревший шрифт `MingLiU-ExtB`.  
* Базовое знакомство с C# и Visual Studio или любой выбранной IDE.

## Шаг 1: Настройте проект и импортируйте пространства имён

Создайте новое консольное приложение и добавьте необходимые директивы `using`. Это гарантирует, что код компилируется без дополнительных изменений.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Pro tip:** Держите метод `Main` минимальным; это улучшает читаемость и делает учебник проще для восприятия.

## Шаг 2: Определите параметры загрузки с правильной кодировкой текста (big5 для традиционного китайского)

`LoadOptions` класс сообщает Aspose.Words, как интерпретировать необработанные байты в исходном файле. Использование **big5 encoding** критично для традиционных китайских символов, сохранённых с этой устаревшей кодовой страницей.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Why this matters:** Если вы опустите указание кодировки или используете кодировку по умолчанию UTF‑8, символы могут отображаться как искажённые знаки (mojibake). Указание `big5` сохраняет оригинальные глифы до любой замены шрифтов.

## Шаг 3: Загрузите файл DOCX, используя указанную кодировку

Передайте экземпляр `loadOptions` конструктору `Document`. Это загрузит файл, учитывая **document encoding for Chinese**, которую вы задали ранее.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Если файл не найден, программа бросит `FileNotFoundException`. Убедитесь, что путь правильный и приложение имеет права чтения.

## Шаг 4: Замените устаревший шрифт на современный эквивалент

Во многих старых китайских документах используется `MingLiU-ExtB`, который может отсутствовать в новых установках Windows. Сопоставление его с `Microsoft JhengHei` (широко доступным шрифтом Unicode) обеспечивает корректное отображение.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Explanation:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` регистрирует глобальное правило замены. Каждый раз, когда Aspose.Words встречает `MingLiU-ExtB`, он заменяет его на `Microsoft JhengHei`.  
* Необязательный цикл выводит сопоставление, что полезно для отладки в больших документах с несколькими семействами шрифтов.

## Шаг 5: Сохраните обработанный документ

После замены запишите документ в новый файл. Вывод будет отображать китайский текст с использованием современного шрифта, устраняя предупреждения о недостающих глифах.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Откройте полученный файл в Microsoft Word или любом просмотрщике DOCX; вы должны увидеть традиционные китайские символы, отрисованные чисто с помощью `Microsoft JhengHei`.

## Обработка граничных случаев и распространённых подводных камней

| Situation | Recommended approach |
|-----------|----------------------|
| **Исходный шрифт не указан в документе** | Используйте `doc.FontInfos.Substitution.Add` с шаблонным паттерном, например `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Несколько устаревших шрифтов требуют замены** | Вызовите `Add` для каждой пары или загрузите словарь замен из конфигурационного файла. |
| **Целевой шрифт недоступен на целевой машине** | Выберите шрифт, поставляемый с Windows (например, `Arial Unicode MS`) или внедрите шрифт, используя `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Ошибки кодировки всё ещё появляются** | Проверьте, действительно ли исходный файл использует **big5**; вы можете просмотреть файл в hex‑редакторе или использовать `File.ReadAllBytes` и сравнить байтовые шаблоны. |

## Полный рабочий пример

Ниже приведена полная, автономная программа. Скопируйте её в `Program.cs`, скорректируйте пути к файлам и запустите.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Expected result:** При открытии `big5_doc_fixed.docx` все традиционные китайские символы отображаются корректно, без предупреждений о недостающих глифах, поскольку `MingLiU-ExtB` был заменён на `Microsoft JhengHei`.

## Заключение

Теперь у вас есть надёжный метод для задач **font substitution in document** с использованием C#. Настроив **big5 encoding**, загрузив DOCX с помощью `LoadOptions` и сопоставив устаревшие шрифты с современными эквивалентами, вы устраняете проблемы отображения, которые преследуют старые китайские файлы.  

Отсюда вы можете:

* Расширить карту замен, чтобы охватить дополнительные устаревшие шрифты.  
* Автоматизировать процесс для пакетов документов (цикл по каталогу).  
* Сочетать замену шрифтов с другими преобразованиями документов, такими как добавление водяных знаков или конвертация в PDF.

Не стесняйтесь экспериментировать с различными целевыми шрифтами или внедрять пользовательские шрифты для полной переносимости. Если возникнут проблемы, обратитесь к таблице граничных случаев выше или изучите документацию Aspose.Words для продвинутой работы со шрифтами.

Удачной разработки!

## Что вам стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Log Font Substitution Warnings – Complete Aspose.Words Guide](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}