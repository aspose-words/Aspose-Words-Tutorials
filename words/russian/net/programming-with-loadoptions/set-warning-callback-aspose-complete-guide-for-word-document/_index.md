---
category: general
date: 2026-05-23
description: Установите обработчик предупреждений Aspose для захвата предупреждений
  о замене шрифтов в Aspose.Words. Изучите LoadOptions, FontSettings и реализацию
  IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: ru
og_description: Установите обработчик предупреждений Aspose для мониторинга замены
  шрифтов в Aspose.Words. В этом руководстве показаны LoadOptions, FontSettings и
  реализация обработчика предупреждений.
og_title: Установить обратный вызов предупреждений Aspose – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Установка обратного вызова предупреждений Aspose – Полное руководство по загрузке
  Word‑документов
url: /ru/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Полное руководство по загрузке Word‑документов

Ever wondered how to **set warning callback aspose** so you never miss a font‑substitution alert again? You're not alone. When a DOCX references a font that isn’t installed, Aspose.Words silently swaps it, and without a proper callback you might never know something changed.

Задумывались ли вы когда‑нибудь, как **set warning callback aspose**, чтобы никогда не пропустить оповещение о замене шрифта? Вы не одиноки. Когда DOCX ссылается на шрифт, который не установлен, Aspose.Words тихо заменяет его, и без правильного обратного вызова вы можете никогда не узнать, что что‑то изменилось.

In this tutorial we’ll walk through a full, runnable example that shows exactly how to capture those warnings. By the end you’ll understand **Aspose.Words LoadOptions**, how to configure **FontSettings**, and why implementing **IWarningCallback** is the cleanest way to stay in the loop. No fluff—just the code you can drop into a .NET project today.

В этом руководстве мы пройдём через полностью готовый к запуску пример, который показывает, как именно перехватывать такие предупреждения. К концу вы поймёте **Aspose.Words LoadOptions**, как настроить **FontSettings**, и почему реализация **IWarningCallback** — самый чистый способ оставаться в курсе. Без лишних слов — только код, который можно сразу добавить в .NET‑проект.

## What You’ll Learn

## Что вы узнаете

- How to **set warning callback aspose** on a `LoadOptions` instance.  
- The role of **Aspose.Words LoadOptions** when opening a document.  
- Configuring **Aspose fonts substitution** handling with `FontSettings`.  
- Writing a custom **IWarningCallback implementation** to log font issues.  
- Loading a document safely with **Aspose document loading** best practices.

- Как **set warning callback aspose** на экземпляре `LoadOptions`.  
- Какова роль **Aspose.Words LoadOptions** при открытии документа.  
- Настройка обработки **Aspose fonts substitution** с помощью `FontSettings`.  
- Написание пользовательской реализации **IWarningCallback** для журналирования проблем со шрифтами.  
- Безопасная загрузка документа с лучшими практиками **Aspose document loading**.

### Prerequisites

### Предварительные требования

- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well).  
- A valid Aspose.Words for .NET license or a trial key.  
- Visual Studio, Rider, or any C# editor you prefer.  
- A sample DOCX (`fontTest.docx`) that references a missing font (optional but helpful).

- .NET 6.0 или новее (код также работает на .NET Framework 4.5+).  
- Действительная лицензия Aspose.Words для .NET или пробный ключ.  
- Visual Studio, Rider или любой предпочитаемый вами C#‑редактор.  
- Пример DOCX (`fontTest.docx`), содержащий ссылку на отсутствующий шрифт (необязательно, но полезно).

> **Pro tip:** If you don’t have a missing‑font DOCX, just rename a font in the document’s style and watch the warning fire.

> **Pro tip:** Если у вас нет DOCX с отсутствующим шрифтом, просто переименуйте шрифт в стиле документа и наблюдайте за срабатыванием предупреждения.

---

## How to set warning callback aspose for document loading

## Как установить set warning callback aspose при загрузке документа

Below is the complete, self‑contained program. Save it as `Program.cs`, restore NuGet packages, and run. The console will print every font‑substitution warning Aspose.Words generates while loading the file.

Ниже представлен полностью автономный пример программы. Сохраните его как `Program.cs`, восстановите пакеты NuGet и запустите. Консоль выведет каждое предупреждение о замене шрифта, которое генерирует Aspose.Words при загрузке файла.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Expected console output

### Ожидаемый вывод консоли

If `fontTest.docx` references a font that isn’t installed, you’ll see something like:

Если `fontTest.docx` ссылается на шрифт, который не установлен, вы увидите примерно следующее:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

If every font is present, the only line printed will be *Document loaded successfully*—no warnings, no noise.

Если все шрифты присутствуют, единственной напечатанной строкой будет *Document loaded successfully* — без предупреждений и лишнего шума.

![set warning callback aspose example](image.png "set warning callback aspose example")

---

## Understanding LoadOptions in Aspose.Words

## Понимание LoadOptions в Aspose.Words

`LoadOptions` is the gateway to every tweak you can make **aspose document loading**. It lets you:

`LoadOptions` — это точка входа для всех настроек, которые вы можете применить к **aspose document loading**. Он позволяет:

1. **Specify a custom `FontSettings`** – useful when your app ships its own fonts.  
2. **Attach a warning callback** – exactly what we did to catch font substitutions.  
3. Control document format detection, password handling, and more.

1. **Указать пользовательский `FontSettings`** — полезно, когда приложение поставляется со своими шрифтами.  
2. **Подключить обратный вызов предупреждений** — именно так мы отлавливаем замены шрифтов.  
3. Управлять определением формата документа, обработкой паролей и другими параметрами.

Because `LoadOptions` is passed to the `Document` constructor, the settings are applied **once**, right at the moment the file is parsed. That’s why we can guarantee our warning handler will see every substitution before the document is even built in memory.

Поскольку `LoadOptions` передаётся конструктору `Document`, настройки применяются **один раз**, в момент парсинга файла. Поэтому мы можем гарантировать, что наш обработчик предупреждений увидит каждую замену ещё до того, как документ будет построен в памяти.

### When to use a custom LoadOptions

### Когда использовать пользовательский LoadOptions

- **Batch processing** of many files where you want a uniform logging strategy.  
- **Cloud services** that need to report missing fonts back to the caller.  
- **Testing pipelines** that verify documents adhere to a corporate font policy.

- **Пакетная обработка** множества файлов, где требуется единая стратегия журналирования.  
- **Облачные сервисы**, которым необходимо сообщать о недостающих шрифтах вызывающему.  
- **Конвейеры тестирования**, проверяющие соответствие документов корпоративной политике шрифтов.

---

## Configuring FontSettings for Aspose fonts substitution

## Настройка FontSettings для замены шрифтов Aspose

The `FontSettings` object controls how Aspose.Words resolves fonts. By default it searches the system’s font folders, then falls back to built‑in substitutes. You can fine‑tune this behavior:

Объект `FontSettings` управляет тем, как Aspose.Words ищет шрифты. По умолчанию он просматривает системные папки со шрифтами, а затем использует встроенные замены. Вы можете точно настроить это поведение:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

These lines are optional for the basic “set warning callback aspose” scenario, but they illustrate how you can **reduce** the number of substitution warnings by providing the right fonts up front.

Эти строки необязательны для базового сценария «set warning callback aspose», но они показывают, как можно **сократить** количество предупреждений о замене, предоставив нужные шрифты заранее.

---

## Implementing IWarningCallback for font substitution warnings

## Реализация IWarningCallback для предупреждений о замене шрифтов

The `IWarningCallback` interface is tiny—just a single `Warning` method. Yet it gives you **full control** over how warnings are handled:

Интерфейс `IWarningCallback` крошечный — содержит лишь один метод `Warning`. Тем не менее он предоставляет **полный контроль** над обработкой предупреждений:

- **Log to a file** instead of the console.  
- **Collect warnings** in a list for later analysis.  
- **Throw exceptions** for critical warnings (e.g., when a required font is missing).

- **Записывать в файл** вместо консоли.  
- **Собирать предупреждения** в список для последующего анализа.  
- **Выбрасывать исключения** для критических предупреждений (например, когда отсутствует обязательный шрифт).

Here’s a quick example that stores warnings in a `List<string>`:

Ниже приведён простой пример, сохраняющий предупреждения в `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

You could then inspect `handler.Messages` after loading the document to decide whether to abort processing.

После загрузки документа вы можете проверить `handler.Messages`, чтобы решить, следует ли прервать обработку.

---

## Loading a document with custom warning handling (full workflow)

## Загрузка документа с пользовательской обработкой предупреждений (полный процесс)

Putting everything together, the final pattern you’ll likely reuse looks like this:

Объединив всё вместе, получаем окончательный шаблон, который вы, вероятно, будете переиспользовать:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

This snippet demonstrates the **aspose document loading** flow you’ll use in production: configure, load, then react. The pattern scales nicely whether you’re processing a single file or looping over thousands.

Этот фрагмент демонстрирует поток **aspose document loading**, который будет использоваться в продакшене: настройка, загрузка и реакция. Шаблон хорошо масштабируется как для обработки одного файла, так и для перебора тысяч файлов.

---

## Common Questions & Edge Cases

## Часто задаваемые вопросы и особые случаи

**What if the document is password protected?**  
Add `Password = "secret"` to the `LoadOptions` initializer. The warning callback still works once the file is decrypted.

**Что делать, если документ защищён паролем?**  
Добавьте `Password = "secret"` в инициализатор `LoadOptions`. Обратный вызов предупреждений продолжит работать после расшифровки файла.

**Will the callback fire for other warning types?**  
Yes—`WarningInfo.Type` can be `DocumentStructure`, `UnsupportedFileFormat`, etc. In our example we filter for `FontSubstitution`, but you can log everything by removing the `if` check.

**Будет ли обратный вызов срабатывать для других типов предупреждений?**  
Да — `WarningInfo.Type` может быть `DocumentStructure`, `UnsupportedFileFormat` и т.д. В нашем примере мы фильтруем `FontSubstitution`, но можно журналировать всё, удалив проверку `if`.

**Does this affect performance?**  
Negligibly. The callback is invoked only when a warning occurs, which is far less frequent than the normal parsing steps.

**Влияет ли это на производительность?**  
Практически не влияет. Обратный вызов вызывается только при возникновении предупреждения, что происходит гораздо реже, чем обычные шаги парсинга.

**Can I disable font substitution entirely?**  
You can set `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` but then Aspose.Words will throw an exception for missing fonts instead of swapping them.

**Можно ли полностью отключить замену шрифтов?**  
Можно установить `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;`, но тогда Aspose.Words будет бросать исключение при отсутствии шрифтов вместо их замены.

---

## Conclusion

## Заключение

You now know exactly how to **set warning callback aspose** to monitor font‑substitution events during **Aspose.Words LoadOptions** processing. By configuring `FontSettings`, implementing a lightweight `IWarningCallback`, and loading the document with those options, you get full visibility into any font changes Aspose makes behind the scenes.  

Now you can:

- Extend the warning handler to write to a central logging service.  
- Combine the callback with a custom font‑fallback strategy.  
- Use the pattern when building a cloud API that validates client‑uploaded documents.

You now know exactly how to **set warning callback aspose** to monitor font‑substitution events during **Aspose.Words LoadOptions** processing. By configuring `FontSettings`, implementing a lightweight `IWarningCallback`, and loading the document with those options, you get full visibility into any font changes Aspose makes behind the scenes.  

From here you might:

- Extend the warning handler to write to a central logging service.  
- Combine the callback with a custom font‑fallback strategy.  
- Use the pattern when building a cloud API that validates client‑uploaded documents.

Give it a try with your own DOCX files, tweak the `FontSettings`, and watch the console tell you exactly what fonts were swapped. Happy coding, and may your documents always render as intended!

Попробуйте это с вашими собственными DOCX‑файлами, поиграйте с `FontSettings` и наблюдайте, как консоль точно сообщает, какие шрифты были заменены. Приятного кодинга, и пусть ваши документы всегда отображаются корректно!

## Related Tutorials

## Похожие руководства

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}