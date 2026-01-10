---
category: general
date: 2026-01-10
description: Узнайте, как использовать LoadOptions для обработки отсутствующих шрифтов
  в Aspose.Words. Пошаговый код, советы и лучшие практики для надёжной загрузки документов.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: ru
og_description: Как использовать LoadOptions для обработки отсутствующих шрифтов в
  Aspose.Words. Получите полный, готовый к запуску пример с объяснениями и практическими
  советами.
og_title: Как использовать LoadOptions в Aspose.Words – Полное руководство
tags:
- Aspose.Words
- C#
- .NET
title: Как использовать LoadOptions в Aspose.Words – Полное руководство
url: /ru/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как использовать LoadOptions в Aspose.Words – Полное руководство

Когда‑нибудь задумывались **как использовать LoadOptions** при загрузке документа Word, в котором могут отсутствовать некоторые шрифты? Вы не одиноки в этом вопросе. Во многих реальных проектах документы перемещаются между машинами, и целевая система часто не имеет тех же шрифтов, что использовал автор. Результат? Неожиданные замены шрифтов, которые могут нарушить макет, скрыть важные символы или просто выглядеть небрежно.  

К счастью, Aspose.Words предоставляет удобный способ *обработать отсутствующие шрифты* через объект `LoadOptions` с обратным вызовом предупреждений. В этом руководстве вы узнаете **как использовать LoadOptions** для захвата предупреждений о замене шрифтов, их логирования и поддержания надёжного конвейера обработки.

Мы рассмотрим:

* Создание класса обратного вызова предупреждений  
* Настройку `LoadOptions` с этим обратным вызовом  
* Загрузку документа с отслеживанием отсутствующих шрифтов  
* Советы по отладке и расширению решения  

Никакой внешней документации не требуется — всё, что нужно, находится здесь.

---

## Что вам понадобится

Прежде чем приступить, убедитесь, что у вас есть:

* **Aspose.Words for .NET** (последняя версия на 2026 год), установленный через NuGet  
* Среда разработки .NET (Visual Studio, Rider или VS Code)  
* Пример DOCX, в котором используется шрифт, которого у вас нет (назовём его `input.docx`)  

Это всё — дополнительных библиотек не требуется.

---

## Шаг 1 – Определите обратный вызов предупреждений для захвата замены шрифтов

Первый элемент головоломки — класс, реализующий `IWarningCallback`. Aspose.Words будет вызывать его метод `Warning` каждый раз, когда встретит что‑то значимое, например отсутствующий шрифт.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Почему это важно:**  
Фильтруя по `WarningType.FontSubstitution`, мы избавляемся от лишних предупреждений (например, о устаревших функциях). Обратный вызов даёт полный контроль — вы можете записать информацию в файл, бросить исключение или даже программно внедрить запасной шрифт.

---

## Шаг 2 – Настройте LoadOptions с обратным вызовом

Теперь, когда у нас есть обработчик, нужно сообщить Aspose.Words использовать его. Здесь и проявляется **как использовать LoadOptions** на практике.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Подсказка:** `LoadOptions` предлагает множество других параметров (например, `Password`, `LoadFormat`, `Encoding`). Их можно комбинировать, но для обработки отсутствующих шрифтов звёздочкой является `WarningCallback`.

---

## Шаг 3 – Загрузите документ, используя настроенные параметры

С готовыми `LoadOptions` загрузка документа становится простой. Aspose.Words автоматически вызовет обратный вызов для любого шрифта, который не найдёт.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Ожидаемый вывод:**  

Если `input.docx` использует шрифт под названием *“GothicBold”*, которого нет в системе, вы увидите примерно следующее:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Строка предупреждения появляется **именно в момент, когда обнаруживается отсутствующий шрифт**, предоставляя мгновенную обратную связь.

---

## Шаг 4 – (Опционально) Продолжите обработку документа

Обычно после загрузки требуется выполнить дополнительные действия. Ниже представлены несколько типичных пост‑загрузочных операций, которые работают без проблем с нашей настройкой предупреждений.

### 4.1 Сохранить документ в PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Заменить отсутствующие шрифты известным запасным

Если вам нужен конкретный запасной шрифт (например, *“Calibri”*), можно скорректировать `FontSettings` перед сохранением:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Записать все предупреждения в файл

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Эти фрагменты кода демонстрируют **как использовать LoadOptions** за пределами базового случая, предоставляя гибкость для решений промышленного уровня.

---

## Распространённые подводные камни и как **обрабатывать отсутствующие шрифты** без сбоев

| Подводный камень | Почему происходит | Как исправить / смягчить |
|------------------|-------------------|--------------------------|
| **Обратный вызов не подключён** | Вы забыли установить `WarningCallback`. | Всегда создавайте экземпляр `LoadOptions` и присваивайте обработчик перед загрузкой. |
| **Обратный вызов только печатает, но не сохраняет** | В веб‑службе вывод в консоль исчезает. | Замените `Console.WriteLine` на логгер (Serilog, NLog) или запишите в постоянное хранилище. |
| **Несколько отсутствующих шрифтов, но сообщается только первый** | Обратный вызов бросает исключение при первом предупреждении. | Делайте обратный вызов лёгким; бросайте исключения только при реальной необходимости прерывания. |
| **Подменённый шрифт выглядит некорректно** | По умолчанию выбирается визуально несхожий шрифт. | Используйте `FontSettings.SubstitutionSettings.FontSubstitutionRules` для приоритизации желаемого запасного шрифта. |
| **Падение производительности на больших документах** | Обратный вызов вызывается тысячи раз. | Собирать предупреждения в список и обрабатывать после загрузки, либо фильтровать только уникальные имена шрифтов. |

Осведомлённость о этих сценариях поможет вам **обрабатывать отсутствующие шрифты** без неожиданностей.

---

## Полный рабочий пример – все части вместе

Ниже представлена полностью готовая к запуску программа, демонстрирующая весь процесс. Скопируйте‑вставьте её в консольный проект, добавьте пакет Aspose.Words через NuGet, и всё будет работать сразу.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Запуск этой программы** выполнит следующее:

1. Выведет любые предупреждения о замене шрифтов в консоль.  
2. Сохранит оригинальный макет как `output.pdf`.  
3. Сохранит второй PDF (`output-with-fallback.pdf`), принудительно используя запасной шрифт *Calibri* или *Arial*.

---

## Часто задаваемые вопросы (FAQ)

**В: Работает ли это с файлами DOC, RTF или HTML?**  
О: Да. `LoadOptions` не зависит от формата; при указании правильного пути к файлу обратный вызов будет срабатывать для отсутствующих шрифтов во всех поддерживаемых форматах.

**В: Можно ли полностью подавить предупреждения?**  
О: Можно назначить пустой обратный вызов (`new IWarningCallback { Warning = _ => {} }`) или установить `LoadOptions.WarningCallback = null`. Однако потеря видимости может привести к пропуску критических проблем со шрифтами.

**В: Как заменить отсутствующие шрифты встроенными?**  
О: Используйте `FontSettings` для встраивания запасного шрифта (`AddFontSource`). Сочетайте это с правилами подстановки для бесшовного опыта.

**В: Является ли обратный вызов потокобезопасным?**  
О: При загрузке больших документов в параллельных потоках обратный вызов может вызываться из нескольких потоков. Убедитесь, что общие ресурсы (например, файлы журналов) синхронизированы.

---

## Заключение

Мы прошли путь **как использовать LoadOptions** в Aspose.Words для **элегантной обработки отсутствующих шрифтов**. Определив собственный `IWarningCallback`, привязав его к объекту `LoadOptions` и загрузив документ с этой конфигурацией, вы получаете мгновенную информацию о любых событиях замены шрифтов. Далее вы можете логировать, заменять или встраивать запасные шрифты, чтобы ваш вывод выглядел точно так, как задумано.

Помните ключевые шаги:

1. Реализуйте обратный вызов предупреждений, ориентированный на `WarningType.FontSubstitution`.  
2. Подключите его к объекту `LoadOptions`.  
3. Загрузите документ с этими параметрами.  
4. (Опционально) Добавьте дополнительные правила подстановки шрифтов или логирование по необходимости.

Экспериментируйте — замените консольный логгер на структурированный, добавьте email‑оповещения о критических отсутствующих шрифтах или интегрируйте этот шаблон в более крупный конвейер обработки документов. Подход масштабируется как для одиночных файлов, так и для пакетной обработки тысяч документов.

Удачной разработки, и пусть ваши документы всегда отображаются нужными шрифтами!  

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}