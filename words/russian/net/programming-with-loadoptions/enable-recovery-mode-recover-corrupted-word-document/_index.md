---
category: general
date: 2026-07-06
description: Включите режим восстановления, чтобы открыть повреждённый файл docx с
  помощью Aspose.Words. Узнайте, как быстро восстановить повреждённый документ Word.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: ru
og_description: Включение режима восстановления позволяет открыть повреждённый файл docx
  и попытаться восстановить повреждённый документ Word.
og_title: Включить режим восстановления – Восстановить повреждённый документ Word
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: Включить режим восстановления — восстановить повреждённый документ Word
url: /ru/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Включить режим восстановления – восстановление повреждённого документа Word

Когда‑то пытались открыть **повреждённый docx** и получали диалог ошибки? Это раздражает, особенно если файл содержит недели работы. К счастью, Aspose.Words предоставляет возможность *включить режим восстановления*, чтобы попытаться спасти содержимое без ручного копирования‑вставки.

В этом руководстве мы пройдём все шаги по **включению режима восстановления**, загрузке повреждённого файла и сохранению пригодной копии. К концу вы будете знать, как *восстанавливать повреждённые документы Word* программно и как корректно обрабатывать сценарий *восстановления повреждённого docx‑файла*.

## Что понадобится

- .NET 6 (или любой современный .NET‑runtime) – библиотека также работает на .NET Framework.  
- Visual Studio 2022 или VS Code – любой любимый IDE.  
- **Aspose.Words for .NET** пакет NuGet (`Install-Package Aspose.Words`) – единственная внешняя зависимость.  
- Пример повреждённого `docx` (назовём его `corrupted.docx`).

Вот и всё. Никаких дополнительных инструментов, никаких ручных правок XML. Всего несколько строк C#.

![enable recovery mode in Aspose.Words](image-url-placeholder.png)

*Текст alt изображения: включить режим восстановления в Aspose.Words*

## Шаг 1: Установить Aspose.Words и настроить проект

Откройте терминал (или консоль диспетчера пакетов) и выполните:

```bash
dotnet add package Aspose.Words
```

Или в Visual Studio откройте **Tools → NuGet Package Manager → Manage NuGet Packages** и найдите *Aspose.Words*. После установки добавьте пространство имён в начале файла:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **Полезный совет:** Держите пакеты в актуальном состоянии. Логика восстановления улучшается с каждым релизом.

## Шаг 2: Включить режим восстановления с помощью `LoadOptions`

Сердце решения – класс `LoadOptions`. Установив его свойство `RecoveryMode` в `RecoveryMode.Recover`, вы говорите Aspose.Words *включить режим восстановления* при разборе документа.

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

Почему это важно? Без режима восстановления Aspose.Words прерывает работу при первой же ошибке. С включённым режимом библиотека пытается пропустить повреждённые части и всё равно вернуть пригодный объект `Document`.

## Шаг 3: Загрузить потенциально повреждённый файл

Теперь действительно загружаем файл. Если документ невозможно восстановить, Aspose.Words всё равно вернёт экземпляр `Document`, но некоторые элементы могут отсутствовать.

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

Обратите внимание, что путь указан как абсолютная строка; измените его под расположение вашего тестового файла. Конструктор `Document` читает файл **с включённым режимом восстановления**, давая шанс *восстановить повреждённый документ Word*.

## Шаг 4: Проверить, что восстановилось (необязательно, но полезно)

Хорошая практика – осмотреть загруженный документ перед тем, как что‑то перезаписывать. Для быстрой проверки можно вывести первые несколько абзацев в консоль:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

Если вы видите «мусорный» текст или множество пустых строк, файл может быть **слишком повреждён**. Тем не менее у вас уже есть объект `Document`, которым можно манипулировать – добавить заголовок, заменить отсутствующие изображения и т.д.

## Шаг 5: Сохранить восстановленный документ

Если проверка прошла успешно, запишите восстановленную версию в новый файл. Этот шаг фактически *восстанавливает повреждённый docx‑файл* и даёт чистую копию, которую можно открыть в Word.

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Если исходный файл был `.doc` или другого формата, измените `SaveFormat` соответственно (например, `SaveFormat.Pdf` для PDF‑вывода).

## Шаг 6: Обработка исключений и граничных случаев

Даже при включённом режиме восстановления некоторые катастрофы необратимы (например, полностью обрезанные ZIP‑структуры). Оберните загрузку в блок `try‑catch`, чтобы отловить такие проблемы:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

Распространённый вопрос: **«как открыть повреждённый docx»**, когда файл защищён паролем. Режим восстановления **не** обходит шифрование; пароль всё равно нужен. В этом случае задайте `LoadOptions.Password` перед загрузкой.

## Часто задаваемые вопросы (FAQ)

**В: Влияет ли включение режима восстановления на оригинальный файл?**  
О: Нет. Он меняет только способ чтения файла в памяти. Исходный файл остаётся нетронутым, если вы явно не вызовете `Save`.

**В: Могу ли я восстановить изображения, встроенные в повреждённый docx?**  
О: Обычно да, пока соответствующая запись ZIP не повреждена. Если поток изображения отсутствует, Aspose.Words пропустит его и продолжит работу.

**В: Замедляет ли режим восстановления работу?**  
О: Немного, так как парсер выполняет дополнительные проверки. Нагрузка пренебрежимо мала для типичных документов (<10 МБ).

**В: Какие ещё варианты восстановления существуют?**  
О: `RecoveryMode.Auto` (по умолчанию) пытается восстановиться только при возникновении ошибки. `RecoveryMode.None` отключает любые попытки восстановления. `RecoveryMode.Recover` принудительно запускает попытку каждый раз.

## Полный рабочий пример

Ниже представлено самостоятельное консольное приложение, которое можно скопировать в новый .NET‑проект. Оно демонстрирует весь процесс – от установки пакета до сохранения восстановленного файла.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**Ожидаемый вывод (при успешном восстановлении):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

Если файл невозможно спасти, вместо дампа абзацев вы увидите сообщение об ошибке.

## Заключение

Мы только что показали, как **включить режим восстановления** в Aspose.Words, загрузить повреждённый `docx` и **восстановить данные повреждённого документа Word** в новый файл. Та же схема позволяет *восстанавливать повреждённый docx‑файл* в пакетных заданиях, автоматических вложениях электронной почты или


## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [how to recover docx – set recovery mode & open corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [how to recover docx with Aspose.Words – step by step](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Recover Damaged Word File – Complete Guide to Open Corrupted DOCX & Get Page](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}