---
"description": "Узнайте, как определять форматы файлов документов с помощью Aspose.Words для .NET, с помощью этого подробного пошагового руководства."
"linktitle": "Определить формат файла документа"
"second_title": "API обработки документов Aspose.Words"
"title": "Определить формат файла документа"
"url": "/ru/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Определить формат файла документа

## Введение

В современном цифровом мире эффективное управление различными форматами документов имеет решающее значение. Независимо от того, работаете ли вы с Word, PDF, HTML или другими форматами, умение правильно определять и обрабатывать эти файлы может сэкономить вам много времени и усилий. В этом руководстве мы рассмотрим, как определять форматы файлов документов с помощью Aspose.Words для .NET. Это руководство проведет вас через все, что вам нужно знать, от предварительных условий до подробного пошагового руководства.

## Предпосылки

Прежде чем погрузиться в код, давайте убедимся, что у вас есть все необходимое:

- Aspose.Words для .NET: Вы можете загрузить его с [здесь](https://releases.aspose.com/words/net/). Убедитесь, что у вас есть действующая лицензия. Если нет, вы можете получить [временная лицензия](https://purchase.aspose.com/temporary-license/).
- Visual Studio: подойдет любая последняя версия.
- .NET Framework: убедитесь, что у вас установлена правильная версия.

## Импорт пространств имен

Для начала вам необходимо импортировать необходимые пространства имен в ваш проект:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Давайте разобьем пример на несколько шагов, чтобы его было легче понять.

## Шаг 1: Настройка каталогов

Сначала нам необходимо настроить каталоги, в которых файлы будут сортироваться по формату.

```csharp
// Путь к каталогу документов.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Создайте каталоги, если они еще не существуют.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Шаг 2: Получите список файлов

Далее мы получим список файлов из каталога, исключая поврежденные документы.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Шаг 3: Определите форматы файлов

Теперь мы просматриваем каждый файл и определяем его формат с помощью Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Отображение типа документа
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Заключение

Определение форматов файлов документов с помощью Aspose.Words для .NET — это простой процесс. Настроив каталоги, получив список файлов и используя Aspose.Words для определения форматов файлов, вы можете эффективно организовывать и управлять своими документами. Такой подход не только экономит время, но и гарантирует, что вы правильно обрабатываете различные форматы документов.

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?
Aspose.Words for .NET — мощная библиотека для программной работы с документами Word. Она позволяет разработчикам создавать, изменять и конвертировать документы в различных форматах.

### Может ли Aspose.Words обнаруживать зашифрованные документы?
Да, Aspose.Words может определить, зашифрован ли документ, и обрабатывать такие документы соответствующим образом.

### Какие форматы может обнаружить Aspose.Words?
Aspose.Words может распознавать широкий спектр форматов, включая DOC, DOCX, RTF, HTML, MHTML, ODT и многие другие.

### Как получить временную лицензию для Aspose.Words?
Вы можете получить временную лицензию в [Покупка Aspose](https://purchase.aspose.com/temporary-license/) страница.

### Где я могу найти документацию по Aspose.Words?
Документацию по Aspose.Words можно найти здесь [здесь](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}