---
category: general
date: 2026-02-21
description: Узнайте, как включить предупреждения, обнаружить отсутствующие шрифты
  и безопасно загружать docx с помощью Aspose.Words в C#. Следуйте пошаговому руководству.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: ru
og_description: Как включить предупреждения, обнаружить отсутствующие шрифты и правильно
  загружать файлы docx с помощью Aspose.Words. Включён полный пример кода.
og_title: Как включить предупреждения и обнаружить отсутствующие шрифты при загрузке
  DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Как включить предупреждения и обнаружить отсутствующие шрифты при загрузке
  файлов DOCX
url: /ru/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как включить предупреждения и обнаружить недостающие шрифты при загрузке DOCX‑файлов

Когда‑нибудь задумывались **как включить предупреждения** о недостающих шрифтах, прежде чем они молча испортят отображение вашего документа? Вы не одиноки — большинство разработчиков полагают, что библиотека «само собой сделает правильное», а потом обнаруживают, что шрифт был заменён без единого намёка.

В этом руководстве мы покажем, **как включить предупреждения**, **как обнаружить недостающие шрифты** и правильный способ **как загрузить docx** с помощью Aspose.Words для .NET. К концу вы получите готовый к запуску пример, который выводит каждое предупреждение о замене шрифта в консоль, чтобы вам больше не пришлось гадать, что произошло внутри файла.

## Предварительные требования

- .NET 6.0 или новее (код также работает на .NET Framework 4.7+)  
- Visual Studio 2022 или любая другая IDE для C#  
- NuGet‑пакет **Aspose.Words** (`Install-Package Aspose.Words`)  
- DOCX‑файл, в котором могут быть шрифты, не установленные на вашем компьютере (назовём его `input.docx`)

> **Pro tip:** Если у вас нет тестового файла, просто откройте документ Word, использующий кастомный корпоративный шрифт, и сохраните его как `input.docx`. Это вызовет нужное нам предупреждение.

## Обзор решения

1. **Создать** объект `LoadOptions` с включённым `FontSubstitutionWarnings`.  
2. **Загрузить** DOCX‑файл, используя эти параметры.  
3. **Проверить** коллекцию `WarningCallback` на наличие записей `FontSubstitution`.  
4. **Отреагировать** — можно записать в лог, отобразить пользователю или даже программно заменить недостающий шрифт.

Ниже мы разберём каждый шаг, объясним *почему* он важен и предоставим полностью готовый, исполняемый фрагмент кода.

---

## Шаг 1: Установить Aspose.Words и настроить проект

Прежде чем мы сможем **как включить предупреждения**, нам нужна библиотека, которая действительно их поддерживает.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Или в консоли менеджера пакетов Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **Почему это необходимо?**  
> Без пакета классы `LoadOptions`, `Document` и инфраструктура предупреждений просто не существуют. Добавление ссылки на NuGet гарантирует, что вы используете последнюю стабильную версию (на момент написания — 24.5).

---

## Шаг 2: Создать параметры загрузки, включающие предупреждения о замене шрифтов

Суть **как включить предупреждения** скрыта в классе `LoadOptions`. Установка `FontSubstitutionWarnings` в `true` заставляет движок фиксировать каждый случай замены недостающего шрифта.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Зачем включать этот флаг?**  
> По умолчанию Aspose.Words тихо заменяет недостающие шрифты запасным (обычно Arial). Это может привести к смещению макета, невидимым символам или нарушению фирменного стиля. Включив флаг, вы получаете полную видимость происходящего.

---

## Шаг 3: Загрузить DOCX‑файл, используя сконфигурированные параметры

Теперь, когда мы знаем **как загрузить docx** с включёнными предупреждениями, действительно выполняем загрузку.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Что происходит «под капотом»?**  
> При разборе DOCX Aspose.Words проверяет каждый элемент `<w:rFonts>`. Если указанный шрифт не установлен, фиксируется предупреждение `FontSubstitution` и происходит переход к шрифту‑по‑умолчанию. Поскольку мы включили предупреждения, эти записи попадают в `document.WarningCallback.Warnings`.

---

## Шаг 4: Получить и отобразить предупреждения о замене шрифтов

Свойство `WarningCallback` содержит `WarningInfoCollection`. Пройдитесь по ней, отфильтруйте `WarningType.FontSubstitution` и выведите сообщения.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Ожидаемый вывод** (пример):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Что делать с этими сообщениями?**  
> Их можно записать в файл, отобразить в пользовательском интерфейсе или даже запустить пользовательскую процедуру замены шрифтов. Главное — теперь вы *обнаруживаете недостающие шрифты*, а не догадываетесь об этом позже.

---

## Шаг 5: (Опционально) Заменить недостающие шрифты на конкретный запасной

Если у вас есть корпоративный шрифт, который необходимо принудительно использовать, можно обработать предупреждения и заменить их «на лету».

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Зачем это может понадобиться?**  
> Это гарантирует визуальную согласованность всех генерируемых документов, что критично для соблюдения фирменного стиля.

---

## Полный, исполняемый пример

Ниже один файл C#, который можно скопировать в консольное приложение. Он охватывает всё — от установки пакета до вывода предупреждений.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Запустите**: `dotnet run` из папки проекта. Если какие‑то шрифты отсутствуют, вы увидите соответствующие предупреждения, а опциональная замена будет применена перед сохранением файла.

---

## Часто задаваемые вопросы

### Работает ли это при конвертации в PDF?

Да. После обработки предупреждений вы можете вызвать `doc.Save("output.pdf")`, и заменённые шрифты отобразятся в PDF так же, как в DOCX.

### Как подавить предупреждения для конкретного шрифта?

Можно отфильтровать их в цикле — просто пропустите `WarningInfo`, сообщение которого (`Message`) содержит имя шрифта, который нужно игнорировать.

### Доступен ли `FontSubstitutionWarnings` в более старых версиях Aspose.Words?

Он появился в версии 20.5. Если вы используете более старый релиз, обновите пакет через NuGet; изменение API совместимо со старыми версиями.

---

## Заключение

Мы прошли путь от **как включить предупреждения**, через **обнаружение недостающих шрифтов**, к правильному способу **как загрузить docx** с Aspose.Words, получая полную видимость замен шрифтов. Проверяя `document.WarningCallback.Warnings`, вы получаете надёжный журнал событий — больше никаких тихих замен.

Что дальше? Попробуйте подключить логику предупреждений к системе логирования, например Serilog, или построить UI, который будет выделять недостающие шрифты перед отправкой документа пользователям. Также стоит изучить класс `FontSettings` для более тонкой настройки политики замены шрифтов.

Счастливого кодинга, и пусть ваши документы всегда отображаются точно так, как вы задумали! 

![Диаграмма, иллюстрирующая поток от загрузки DOCX‑файла до захвата предупреждений о замене шрифтов — как включить предупреждения в Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}