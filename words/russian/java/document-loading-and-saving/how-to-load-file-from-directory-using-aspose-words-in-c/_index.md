---
category: general
date: 2026-09-11
description: Загрузить файл из каталога с помощью Aspose.Words, используя параметры
  загрузки по умолчанию, и узнать, как установить кодировку документа или настроить
  параметры загрузки в C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load file from directory
- default load options
- set document encoding
- set load options
language: ru
lastmod: 2026-09-11
og_description: Загрузить файл из каталога с помощью Aspose.Words, используя параметры
  загрузки по умолчанию, установить кодировку документа и настроить параметры загрузки
  для любого документа Word.
og_image_alt: Diagram illustrating load file from directory process with Aspose.Words
og_title: Загрузка файла из каталога с помощью Aspose.Words – полное руководство по
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Load file from directory with Aspose.Words using default load options
    and learn how to set document encoding or customize load options in C#.
  headline: How to load file from directory using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document processing
title: Как загрузить файл из каталога с помощью Aspose.Words в C#
url: /ru/java/document-loading-and-saving/how-to-load-file-from-directory-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как загрузить файл из каталога с помощью Aspose.Words на C#

Если вам нужно **загрузить файл из каталога** в рабочий процесс обработки Word, Aspose.Words делает это простым. В этом руководстве показано, как использовать **default load options**, **set document encoding** и **set load options**, чтобы подобрать их под ваш конкретный сценарий.

Загрузка документов часто ставит в затруднительное положение разработчиков, когда исходный файл находится в пользовательской папке или использует кодировку, отличную от UTF‑8. К концу этого руководства вы сможете загрузить любой файл `.docx` из любого каталога, контролировать его кодировку и настраивать поведение загрузки без написания дополнительного вспомогательного кода.

## Что вы достигнете

- Загрузить документ Word из произвольного каталога, используя одну строку кода.  
- Понять, что предоставляют **default load options**, и когда их необходимо изменить.  
- Применить **set document encoding** для корректной интерпретации устаревших наборов символов, таких как Big5.  
- Настроить **set load options** для точной настройки использования памяти, обработки паролей и прочего.  

### Предварительные требования

- .NET 6.0 или новее (пример ориентирован на .NET 6, но подходит любая современная версия .NET).  
- Aspose.Words for .NET 23.9 или новее – добавьте NuGet‑пакет `Aspose.Words`.  
- Базовое знакомство с C# и Visual Studio или вашей предпочтительной IDE.

---

## Как загрузить файл из каталога с помощью Aspose.Words

Суть операции заключается в едином конструкторе `Document`, который принимает путь к файлу и необязательный экземпляр `LoadOptions`. Когда вы опускаете `LoadOptions`, Aspose.Words автоматически применяет **default load options**, которые достаточны для большинства современных документов.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Define the absolute path to the .docx file you want to load.
        string filePath = @"C:\MyDocuments\big5.docx";

        // Step 2: Load the document using the default load options.
        Document doc = new Document(filePath, new LoadOptions());

        // Verify that the document loaded by outputting the page count.
        Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
    }
}
```

**Почему это работает:**  
- Конструктор `Document` читает файл, расположенный по `filePath`.  
- Передача `new LoadOptions()` сообщает Aspose.Words использовать **default load options**, которые автоматически определяют формат файла, выбирают подходящую кодировку и применяют стандартные проверки безопасности.  

Запуск программы выводит количество страниц, подтверждая, что операция **load file from directory** завершилась успешно.

## Использование default load options

Хотя вы можете полностью опустить аргумент `LoadOptions`, явное создание объекта `LoadOptions` проясняет намерения и готовит вас к последующим настройкам.

```csharp
// Create a LoadOptions instance with the default configuration.
LoadOptions loadOptions = new LoadOptions();

// Load the document with those options.
Document doc = new Document(@"C:\MyDocuments\sample.docx", loadOptions);
```

**Ключевые моменты о default load options**

| Функция | Поведение по умолчанию |
|---------|------------------------|
| **Определение формата** | Автоматически определяет DOC, DOCX, ODT, RTF, HTML и многие другие форматы. |
| **Кодировка** | Определяет UTF‑8, UTF‑16 и распространённые устаревшие кодировки; в случае неудачи использует UTF‑8. |
| **Обработка пароля** | Выбрасывает `IncorrectPasswordException`, если файл защищён паролем. |
| **Использование памяти** | Загружает весь документ в память, что оптимально для файлов размером менее 100 МБ. |

Если ваш документ закодирован в устаревшей кодировке (например, Big5) и автоматическое определение не срабатывает, вам необходимо вручную **set document encoding**.

## Установка кодировки документа

Когда файл содержит шрифты или текст, закодированные с использованием устаревшей кодовой страницы, вы можете указать Aspose.Words, какую кодировку использовать, через свойство `LoadOptions.Encoding`. Это типичный способ **set document encoding** для файлов, которые не удалось определить автоматически.

```csharp
using System.Text;

// Step 1: Create LoadOptions and specify the encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Big5 is code page 950.
    Encoding = Encoding.GetEncoding(950)
};

// Step 2: Load the document from the target directory.
Document doc = new Document(@"C:\MyDocuments\big5.docx", loadOptions);

// Step 3: Verify that the special characters are preserved.
Console.WriteLine($"First paragraph text: {doc.FirstSection.Body.Paragraphs[0].GetText()}");
```

**Почему это необходимо:**  
- Без явного указания `Encoding` Aspose.Words может интерпретировать байты как UTF‑8, что приводит к искажённым символам.  
- Предоставив правильную кодовую страницу, библиотека читает текст точно так, как задумал автор.

**Подсказка:** Используйте `Encoding.GetEncoding("big5")` или числовой код страницы (`950`) для традиционных китайских (Big5) документов.

## Настройка load options (set load options)

Помимо кодировки, `LoadOptions` предоставляет множество свойств, позволяющих **set load options** для продвинутых сценариев:

```csharp
// Create a LoadOptions object with several custom settings.
LoadOptions loadOptions = new LoadOptions
{
    // Force the document to be treated as a DOCX file, even if the extension is wrong.
    LoadFormat = LoadFormat.Docx,

    // Limit memory usage for very large files (e.g., 200 MB+).
    LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory,

    // Provide a password if the file is encrypted.
    Password = "MySecretPassword"
};

// Load the document using the customized options.
Document doc = new Document(@"C:\MyDocuments\protected.docx", loadOptions);
```

**Объяснение выбранных свойств**

| Свойство | Назначение |
|----------|------------|
| `LoadFormat` | Принудительно задаёт конкретный формат, обходя автоопределение. Полезно, когда расширения файлов вводят в заблуждение. |
| `LoadOptionsMemoryUsage` | Выбирает стратегию экономии памяти (`LowMemory`) для огромных документов. |
| `Password` | Предоставляет пароль для зашифрованных файлов, избегая исключения. |
| `ValidateDocumentStructure` | Если `true`, загрузчик проверяет внутреннюю структуру XML и бросает исключение при повреждении. |

Вы можете комбинировать любые из этих параметров с **set document encoding**, чтобы справиться с самыми требовательными конвейерами импорта.

## Полный исполняемый пример

Ниже представлена автономная программа, демонстрирующая все концепции в едином потоке:

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;

class LoadFileDemo
{
    static void Main()
    {
        // ------------------------------------------------------------------
        // 1️⃣ Define the directory and file name.
        // ------------------------------------------------------------------
        string directory = @"C:\MyDocuments";
        string fileName   = "big5.docx";               // Change as needed.
        string fullPath   = System.IO.Path.Combine(directory, fileName);

        // ------------------------------------------------------------------
        // 2️⃣ Create LoadOptions with explicit encoding (Big5) and low‑memory mode.
        // ------------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            Encoding = Encoding.GetEncoding(950), // Big5 code page.
            LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory
        };

        // ------------------------------------------------------------------
        // 3️⃣ Load the document from the directory using the custom options.
        // ------------------------------------------------------------------
        Document doc = new Document(fullPath, loadOptions);

        // ------------------------------------------------------------------
        // 4️⃣ Verify the load succeeded.
        // ------------------------------------------------------------------
        Console.WriteLine($"Document loaded from \"{fullPath}\"");
        Console.WriteLine($"Page count: {doc.PageCount}");
        Console.WriteLine($"First paragraph: {doc.FirstSection.Body.Paragraphs[0].GetText().Trim()}");

        // ------------------------------------------------------------------
        // 5️⃣ (Optional) Save as PDF to confirm visual fidelity.
        // ------------------------------------------------------------------
        string pdfPath = System.IO.Path.ChangeExtension(fullPath, ".pdf");
        doc.Save(pdfPath);
        Console.WriteLine($"Saved PDF version to \"{pdfPath}\"");
    }
}
```

**Ожидаемый вывод в консоль**

```
Document loaded from "C:\MyDocuments\big5.docx"
Page count: 3
First paragraph: 這是一個測試文件
Saved PDF version to "C:\MyDocuments\big5.pdf"
```

Запуск программы демонстрирует, как **load file from directory**, **set document encoding** и **set load options** в едином, понятном рабочем процессе.

## Распространённые подводные камни и как их избежать

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Искажённые китайские символы | Кодировка не установлена или указана неверная кодовая страница | **Set document encoding** на `Encoding.GetEncoding(950)` для Big5. |
| `IncorrectPasswordException`, хотя файл не защищён паролем | Загрузчик ошибочно определил бинарный файл как зашифрованный | Явно задайте `LoadFormat` правильного типа (например, `LoadFormat.Docx`). |
| Out

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, опирающиеся на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [восстановить повреждённый docx с Aspose.Words – установить режим восстановления и параметры загрузки](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Как загрузить RTF‑документы с настройкой RTF Load Options в Aspose.Words для Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)
- [Освоить Markdown Load Options с Aspose.Words для Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}