---
category: general
date: 2026-03-08
description: Пользовательские настройки шрифтов позволяют задавать параметры шрифта,
  безопасно загружать документы Word и обрабатывать отсутствующие шрифты с помощью
  Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: ru
og_description: Пользовательские настройки шрифтов позволяют задавать параметры шрифтов,
  безопасно загружать документы Word и обрабатывать отсутствующие шрифты с помощью
  Aspose.Words.
og_title: Настройки пользовательских шрифтов в C# — загрузка Word и обработка отсутствующих
  шрифтов
tags:
- Aspose.Words
- C#
- Font Management
title: Пользовательские настройки шрифтов в C# – загрузка Word и обработка отсутствующих
  шрифтов
url: /ru/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Настройки пользовательских шрифтов в C# – загрузка Word и обработка отсутствующих шрифтов

Когда‑нибудь задумывались, как работают **настройки пользовательских шрифтов**, когда файл Word ссылается на шрифты, которые у вас не установлены? Это распространённая проблема — ваш документ выглядит нормально на одной машине, а затем вдруг каждый абзац переключается на резервный шрифт на другой.  

Хорошие новости? С Aspose.Words вы можете **устанавливать настройки шрифтов**, **загружать содержимое Word‑документа** и **обрабатывать отсутствующие шрифты** в одном удобном процессе. Ниже вы найдёте полностью готовый к запуску пример, который точно показывает, как это сделать, а также объяснение «почему» каждого шага.

## Что вы узнаете

В этом руководстве мы рассмотрим:

* Создание объекта `LoadOptions` и привязка к нему экземпляра `FontSettings`.  
* Регистрация обратного вызова предупреждений, чтобы видеть, какие шрифты заменяются.  
* Загрузка файла DOCX, в котором могут отсутствовать шрифты, и вывод деталей замены в консоль.  

К концу вы сможете уверенно распространять своё C#‑приложение, зная, что каждый сценарий с отсутствующим шрифтом будет зафиксирован и может быть обработан позже.

> **Требования:** Aspose.Words for .NET (v23.12 или новее), установленный через NuGet, и базовое знакомство с консольными приложениями C#.

---

## Настройки пользовательских шрифтов – конфигурация LoadOptions

Первое, что вам нужно, — объект `LoadOptions`. Он сообщает Aspose.Words, как обрабатывать входящий файл. Присваивая новый экземпляр `FontSettings`, мы предоставляем библиотеке место для поиска пользовательских шрифтов.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Почему это важно:**  
Если пропустить `FontSettings`, Aspose.Words будет использовать системную коллекцию шрифтов по умолчанию. Это значит, что любой отсутствующий шрифт будет тихо заменён, и вы не узнаете, какие именно были заменены. Создавая явный контейнер `FontSettings`, вы получаете полный контроль над процессом поиска.

---

## Установка настроек шрифтов в LoadOptions

Теперь, когда у нас есть объект `FontSettings`, вы можете задаться вопросом, куда его направить. Обычно вы добавляете папку, содержащую шрифты, которые поставляете вместе с приложением:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Если у вас нет отдельной папки, вы можете опустить этот блок — Aspose.Words всё равно будет сообщать об отсутствующих шрифтах через обратный вызов предупреждений.*

**Совет:** Используйте флаг `recursive: true`, если ваши шрифты разбросаны по подпапкам. Это избавит вас от необходимости вручную добавлять каждый путь.

---

## Загрузка Word‑документа с пользовательскими настройками шрифтов

С подготовленными параметрами загрузка документа становится простой. Конструктор `Document` принимает путь к файлу и объект `LoadOptions`, который мы только что создали.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Что происходит под капотом?**  
Aspose.Words разбирает DOCX, проверяет каждую ссылку `<w:font>` и обращается к предоставленным вами `FontSettings`. Если шрифт не найден, генерируется предупреждение типа `FontSubstitution`. Наш пользовательский обработчик (показан ниже) перехватит эти предупреждения.

---

## Обработка отсутствующих шрифтов с помощью обратного вызова предупреждений

Интерфейс `IWarningCallback` позволяет реагировать на любые проблемы, возникающие во время загрузки. Его реализация проста:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Когда документ загружается, каждый отсутствующий шрифт вызовет строку вида:

```
Font substituted: Arial -> Liberation Sans
```

**Почему стоит это логировать:**  
В продакшене вы можете перенаправлять эти сообщения в файл или систему телеметрии, что упрощает определение, какие шрифты необходимо включить в пакет или лицензировать.

---

## Полный рабочий пример

Ниже приведена автономная консольная программа, объединяющая всё вместе. Скопируйте‑вставьте её в новый проект .NET Core console и нажмите **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Ожидаемый вывод** (при условии, что `input.docx` использует шрифт, которого у вас нет):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Если все шрифты присутствуют, вы увидите только последнюю строку подтверждения.

---

## Часто задаваемые вопросы и крайние случаи

| Вопрос | Ответ |
|----------|--------|
| **Что если мне нужно встроить отсутствующие шрифты в PDF?** | После загрузки вызовите `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` и затем включите встраивание с помощью `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Могу ли я подавлять предупреждения вместо их логирования?** | Да — установите `loadOptions.WarningCallback = null;` или реализуйте обратный вызов, чтобы игнорировать предупреждения, не связанные со шрифтами. |
| **Работает ли это с файлами `.doc` и `.rtf`?** | Абсолютно. Тот же объект `LoadOptions` применяется к любому формату, поддерживаемому Aspose.Words. |
| **Является ли обратный вызов потокобезопасным?** | Обратный вызов выполняется в том же потоке, который загружает документ, поэтому вы можете безопасно писать в консоль. Для многопоточных сценариев используйте потокобезопасную коллекцию или систему логирования. |

---

## Советы и подводные камни

* **Совет:** Если вы поставляете шрифт, который не установлен на целевой машине, добавьте его в папку, которую передаёте в `SetFontsFolder`. Это гарантирует детерминированное отображение.
* **Осторожно с лицензированием:** Некоторые шрифты требуют коммерческой лицензии для встраивания. Всегда проверяйте EULA шрифта перед включением его в пакет.
* **Замечание о производительности:** Загрузка больших библиотек шрифтов может замедлять разбор документа. Держите папку компактной — включайте только те шрифты, которые действительно нужны.
* **Крайний случай:** Когда документ ссылается на шрифт по его *PostScript‑имени* вместо семейного названия, Aspose.Words всё равно его найдёт, если файл шрифта присутствует в пути поиска.

---

## Заключение

Теперь у вас есть полный, готовый к продакшену шаблон для использования **настроек пользовательских шрифтов** в C#. Настраивая `LoadOptions`, регистрируя обратный вызов предупреждений и при необходимости указывая приватную папку со шрифтами, вы можете **устанавливать настройки шрифтов**, **надёжно загружать содержимое Word‑документа** 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}