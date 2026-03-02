---
category: general
date: 2026-03-01
description: Создайте FontSettings в C# для обнаружения отсутствующих шрифтов, захвата
  сообщений о шрифтах и обработки отсутствующих шрифтов с помощью Aspose.Words. Пошаговое
  руководство для разработчиков.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: ru
og_description: Создайте FontSettings в C# для обнаружения отсутствующих шрифтов,
  перехвата сообщений о шрифтах и обработки отсутствующих шрифтов с помощью Aspose.Words.
  Полный учебник с кодом.
og_title: Создайте FontSettings в C# — обнаружение недостающих шрифтов и перехват
  сообщений о шрифтах
tags:
- Aspose.Words
- C#
- Font Management
title: Создание FontSettings в C# — обнаружение отсутствующих шрифтов и перехват сообщений
  о шрифтах
url: /ru/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание FontSettings в C# – Обнаружение отсутствующих шрифтов и захват сообщений о шрифтах

Когда‑нибудь вам нужно было **создать FontSettings** в проекте .NET, но вы не знали, как обнаружить шрифты, которые не установлены на целевой машине? Вы не одиноки. Во многих реальных приложениях — например, в генераторах автоматических отчетов или конвертерах документов — отсутствие шрифтов может тихо нарушить макет, и вы узнаете об этом только тогда, когда PDF выглядит некорректно.  

А что, если вы сможете **обнаруживать отсутствующие шрифты**, **захватывать сообщения о шрифтах** и **обрабатывать отсутствующие шрифты**, прежде чем они испортят ваш результат? Хорошая новость в том, что Aspose.Words делает это проще простого. В этом руководстве мы пройдем весь процесс, от настройки объекта `FontSettings` до подключения обратного вызова предупреждений, который точно укажет, какие глифы были заменены.

> **TL;DR:** К концу вы получите готовое к запуску консольное приложение C#, которое будет логировать каждую замену шрифта, позволяя решить, встраивать замену или оповестить пользователя.

---

## Предварительные требования

- .NET 6 SDK (или любая современная версия .NET)  
- Visual Studio 2022 или VS Code с расширениями C#  
- Лицензия Aspose.Words для .NET (бесплатная пробная версия подходит для этой демонстрации)  
- Пример DOCX, который ссылается на шрифт, не установленный у вас (например, *Comic Sans MS* на Linux‑машине)  

Никаких дополнительных пакетов NuGet, кроме `Aspose.Words`, не требуется.

---

## Шаг 1 – Установить Aspose.Words и настроить проект

Сначала создайте новый консольный проект и подключите библиотеку Aspose.Words.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Если у вас уже есть решение, просто добавьте пакет через UI NuGet Package Manager — так проще отслеживать версии.

---

## Шаг 2 – Создать FontSettings (Основное ключевое слово появляется здесь)

Шаг **create FontSettings** является краеугольным камнем любого рабочего процесса, связанного со шрифтами. `FontSettings` сообщает Aspose.Words, где искать шрифты, использовать ли системные папки и как действовать, когда чего‑то не хватает.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Почему это важно? Без правильно сконфигурированного `FontSettings` движок тихо заменяет недостающие глифы шрифтом по умолчанию, и вы никогда не увидите предупреждения.

---

## Шаг 3 – Подключить LoadOptions к FontSettings

`LoadOptions` позволяет передать `FontSettings` загрузчику документа. Это мост, который дает движку возможность **обнаруживать отсутствующие шрифты** во время фазы создания `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Теперь каждый раз, когда вы загружаете DOCX с помощью `loadOptions`, Aspose.Words будет обращаться к ранее настроенному `FontSettings`.

---

## Шаг 4 – Привязать обратный вызов предупреждений для **захвата сообщений о шрифтах**

Aspose.Words генерирует предупреждения для различных условий — замена шрифтов является одним из самых распространённых. Предоставив реализацию `IWarningCallback`, вы сможете **захватывать сообщения о шрифтах** в реальном времени.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Класс обработчика предупреждений

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Поле `info.Description` содержит человекочитаемое сообщение, например *«Font 'Comic Sans MS' was not found. Substituted with 'Arial'.»* Это именно тот вывод, который нужен для **обработки отсутствующих шрифтов** корректным способом.

---

## Шаг 5 – Загрузить документ и позволить обработчику выполнить свою работу

С учётом всех настроек загрузка документа становится простой. Если исходный файл ссылается на шрифт, отсутствующий в системе, наш обработчик предупреждений сработает.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

При запуске программы вы увидите вывод в консоль, похожий на:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Этот вывод — часть нашего процесса **захвата сообщений о шрифтах**. Вы можете расширить обработчик, чтобы писать в файл, отправлять телеметрию или даже прерывать конвертацию, если критические шрифты отсутствуют.

---

## Шаг 6 – Полный рабочий пример (Все части вместе)

Ниже полностью готовая к копированию программа. Вставьте её в `Program.cs`, скорректируйте пути к файлам и выполните `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Ожидаемый вывод

Запуск программы на машине, где отсутствует *Comic Sans MS*, выведет что‑то вроде:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

В результате вы также получите `Result.pdf`, использующий заменённые шрифты, и процесс конвертации не завершится с ошибкой.

---

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Что делать, если я хочу, чтобы конвертация завершалась ошибкой вместо замены?** | Внутри `FontSubstitutionWarningHandler` бросайте исключение, когда `info.Description` содержит название критически важного шрифта. |
| **Можно ли автоматически встраивать заменяющий шрифт?** | Да. После обнаружения отсутствующего шрифта вы можете загрузить запасной `FontInfo` из известного пути и добавить его в `fontSettings` через `fontSettings.SetFontsFolder`. |
| **Работает ли это на Linux/macOS?** | Абсолютно. `FontSettings` кроссплатформенен; просто убедитесь, что в папке‑резерве находятся соответствующие файлы `.ttf` или `.otf`. |
| **Является ли обратный вызов предупреждений потокобезопасным?** | Обратный вызов выполняется в том же потоке, который загружает документ, поэтому дополнительная синхронизация для вывода в консоль не требуется. В многопоточных сценариях защищайте общие ресурсы. |
| **Как записать предупреждения в файл?** | Замените `Console.WriteLine` на `File.AppendAllText("font_warnings.log", ...)` или используйте любой фреймворк логирования (Serilog, NLog). |

---

## Советы для продакшн‑готовой обработки шрифтов

1. **Кешировать поиск шрифтов** – Повторное использование одного экземпляра `FontSettings` при загрузке нескольких документов избавляет от повторных сканирований файловой системы.  
2. **Белый список критических шрифтов** – Если ваш бренд требует определённый шрифт, проверяйте его наличие заранее и прекращайте работу с чётким сообщением об ошибке.  
3. **Использовать `SetFontFolder` рекурсивно** – Установка `recursive: true` гарантирует сканирование подпапок, что удобно, когда вы поставляете целую коллекцию шрифтов.  
4. **Комбинировать с `FontSubstitutionSettings`** – Вы можете тонко настраивать правила замены (например, предпочитать шрифты той же семейства).  

---

## Заключение

Мы только что **создали FontSettings**, настроили `LoadOptions` для **обнаружения отсутствующих шрифтов**, подключили обратный вызов, который **захватывает сообщения о шрифтах**, и продемонстрировали, как **обрабатывать отсутствующие шрифты** чистым, готовым к продакшн способом. Весь процесс умещается в несколько десятков строк C#, но даёт полную видимость шрифтовой среды любого DOCX, который вы обрабатываете.

Дальше вы можете изучить:

- **Встраивание запасных шрифтов** непосредственно в итоговый PDF (`PdfSaveOptions.FontEmbeddingMode`).  
- **Программную замену шрифтов** в соответствии с корпоративными правилами брендинга.  
- **Интеграцию в CI‑конвейер** для автоматического помечания документов, использующих неразрешённые шрифты.

Попробуйте, подправьте обработчик предупреждений под свои нужды, и позвольте вашим конвейерам документов работать уверенно — больше никаких загадочных сбоев в макете из‑за невидимых замен шрифтов.

Удачной разработки! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}