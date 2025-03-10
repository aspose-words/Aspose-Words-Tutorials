---
title: Сохраняйте нумерацию источников
linktitle: Сохраняйте нумерацию источников
second_title: API обработки документов Aspose.Words
description: Узнайте, как импортировать документы, сохраняя форматирование, с помощью Aspose.Words для .NET. Пошаговое руководство с примерами кода.
weight: 10
url: /ru/net/join-and-append-documents/keep-source-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохраняйте нумерацию источников

## Введение

 При работе с Aspose.Words для .NET импорт документов из одного источника в другой с сохранением форматирования может быть эффективно выполнен с помощью`NodeImporter` класс. Это руководство проведет вас через весь процесс шаг за шагом.

## Предпосылки

Перед началом убедитесь, что у вас есть следующее:
- Visual Studio установлена на вашем компьютере.
-  Aspose.Words for .NET установлен. Если нет, скачайте его с[здесь](https://releases.aspose.com/words/net/).
- Базовые знания программирования на C# и .NET.

## Импорт пространств имен

Сначала включите необходимые пространства имен в свой проект:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Шаг 1: Настройте свой проект

Начните с создания нового проекта C# в Visual Studio и установите Aspose.Words через диспетчер пакетов NuGet.

## Шаг 2: Инициализация документов
Создать экземпляры источника (`srcDoc`) и пункт назначения (`dstDoc`) документы.

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Шаг 3: Настройте параметры импорта
Настройте параметры импорта для сохранения исходного форматирования, включая нумерацию абзацев.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Шаг 4: Импорт абзацев
Пройдитесь по абзацам исходного документа и импортируйте их в целевой документ.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Шаг 5: Сохраните документ.
Сохраните объединенный документ в желаемом месте.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Заключение

 В заключение следует отметить, что использование Aspose.Words для .NET для импорта документов с сохранением форматирования не вызывает затруднений.`NodeImporter` класс. Этот метод гарантирует, что ваши документы сохранят свой первоначальный вид и структуру без проблем.

## Часто задаваемые вопросы

### Могу ли я импортировать документы с разными стилями форматирования?
 Да,`NodeImporter` класс поддерживает импорт документов с различными стилями форматирования.

### Что делать, если мои документы содержат сложные таблицы и изображения?
Aspose.Words для .NET обрабатывает сложные структуры, такие как таблицы и изображения, во время операций импорта.

### Совместим ли Aspose.Words со всеми версиями .NET?
Aspose.Words поддерживает версии .NET Framework и .NET Core для бесшовной интеграции.

### Как обрабатывать ошибки при импорте документов?
Используйте блоки try-catch для обработки исключений, которые могут возникнуть в процессе импорта.

### Где я могу найти более подробную документацию по Aspose.Words для .NET?
 Посетите[документация](https://reference.aspose.com/words/net/) для получения подробных руководств и справок по API.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
