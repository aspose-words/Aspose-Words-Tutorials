---
title: Единица измерения
linktitle: Единица измерения
second_title: API обработки документов Aspose.Words
description: Узнайте, как настроить функцию единиц измерения в Aspose.Words для .NET, чтобы сохранить форматирование документа во время преобразования ODT.
weight: 10
url: /ru/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Единица измерения

## Введение

Вам когда-нибудь приходилось конвертировать документы Word в разные форматы, но вам нужна была определенная единица измерения для макета? Независимо от того, имеете ли вы дело с дюймами, сантиметрами или точками, обеспечение целостности документа в процессе конвертации имеет решающее значение. В этом руководстве мы рассмотрим, как настроить функцию единиц измерения в Aspose.Words для .NET. Эта мощная функция гарантирует, что форматирование вашего документа будет сохранено именно так, как вам нужно, при конвертации в формат ODT (Open Document Text).

## Предпосылки

Прежде чем погрузиться в код, вам понадобится сделать несколько вещей:

1. Aspose.Words for .NET: Убедитесь, что у вас установлена последняя версия Aspose.Words for .NET. Если у вас ее еще нет, вы можете загрузить ее с[здесь](https://releases.aspose.com/words/net/).
2. Среда разработки: IDE, например Visual Studio, для написания и выполнения кода C#.
3. Базовые знания C#: понимание основ C# поможет вам усвоить материал урока.
4. Документ Word: подготовьте образец документа Word, который вы сможете использовать для преобразования.

## Импорт пространств имен

Прежде чем начать кодирование, давайте убедимся, что у нас импортированы необходимые пространства имен. Добавьте эти директивы using в начало вашего файла кода:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Шаг 1: Настройте каталог документов

Во-первых, вам нужно определить путь к каталогу вашего документа. Это то место, где находится ваш документ Word и где будет сохранен преобразованный файл.

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Заменять`"YOUR DOCUMENTS DIRECTORY"` с фактическим путем к вашему каталогу. Это гарантирует, что ваш код знает, где найти ваш документ Word.

## Шаг 2: Загрузите документ Word

 Далее вам нужно загрузить документ Word, который вы хотите преобразовать. Это делается с помощью`Document` класс из Aspose.Words.

```csharp
// Загрузите документ Word
Document doc = new Document(dataDir + "Document.docx");
```

Убедитесь, что ваш документ Word с именем «Document.docx» присутствует в указанном каталоге.

## Шаг 3: Настройте единицу измерения

 Теперь давайте настроим единицу измерения для преобразования ODT. Вот где происходит волшебство. Мы настроим`OdtSaveOptions` использовать дюймы в качестве единицы измерения.

```csharp
// Настройка параметров резервного копирования с помощью функции «Единица измерения»
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 В этом примере мы устанавливаем единицу измерения на дюймы. Вы также можете выбрать другие единицы, такие как`OdtSaveMeasureUnit.Centimeters` или`OdtSaveMeasureUnit.Points` в зависимости от Ваших требований.

## Шаг 4: Преобразование документа в ODT

 Наконец, мы преобразуем документ Word в формат ODT, используя настроенный`OdtSaveOptions`.

```csharp
// Конвертировать документ в ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Эта строка кода сохраняет преобразованный документ в указанном каталоге с применением новой единицы измерения.

## Заключение

И вот оно! Выполнив эти шаги, вы сможете легко настроить функцию единиц измерения в Aspose.Words для .NET, чтобы гарантировать сохранение макета вашего документа во время преобразования. Независимо от того, работаете ли вы с дюймами, сантиметрами или точками, этот урок показал вам, как с легкостью взять под контроль форматирование вашего документа.

## Часто задаваемые вопросы

### Что такое Aspose.Words для .NET?
Aspose.Words for .NET — мощная библиотека для программной работы с документами Word. Она позволяет разработчикам создавать, изменять, конвертировать и обрабатывать документы Word без необходимости использования Microsoft Word.

### Могу ли я использовать другие единицы измерения, помимо дюймов?
 Да, Aspose.Words for .NET поддерживает другие единицы измерения, такие как сантиметры и точки. Вы можете указать нужную единицу, используя`OdtSaveMeasureUnit` перечисление.

### Существует ли бесплатная пробная версия Aspose.Words для .NET?
 Да, вы можете загрузить бесплатную пробную версию Aspose.Words для .NET с сайта[здесь](https://releases.aspose.com/).

### Где я могу найти документацию по Aspose.Words для .NET?
 Вы можете получить доступ к полной документации по Aspose.Words для .NET по адресу[эта ссылка](https://reference.aspose.com/words/net/).

### Как я могу получить поддержку по Aspose.Words для .NET?
 Для получения поддержки вы можете посетить форум Aspose.Words по адресу[эта ссылка](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
