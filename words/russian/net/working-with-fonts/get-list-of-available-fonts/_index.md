---
title: Получить список доступных шрифтов
linktitle: Получить список доступных шрифтов
second_title: API обработки документов Aspose.Words
description: Узнайте, как получить список доступных шрифтов с помощью Aspose.Words для .NET в этом подробном пошаговом руководстве. Повысьте свои навыки управления шрифтами.
weight: 10
url: /ru/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Получить список доступных шрифтов

## Введение

Вы когда-нибудь сталкивались с трудностями при управлении шрифтами в документах Word? Если вы разработчик .NET, Aspose.Words для .NET здесь, чтобы спасти вас! Эта мощная библиотека не только помогает вам создавать и обрабатывать документы Word программным способом, но и предлагает обширные возможности управления шрифтами. В этом руководстве мы проведем вас через пошаговое руководство о том, как получить список доступных шрифтов с помощью Aspose.Words для .NET. Мы разобьем его на удобоваримые шаги, чтобы вы могли легко следовать им. Итак, давайте погрузимся и сделаем управление шрифтами легким!

## Предпосылки

Прежде чем мы начнем, вам понадобится несколько вещей:

-  Aspose.Words for .NET: Убедитесь, что у вас установлена библиотека Aspose.Words for .NET. Вы можете загрузить ее с[здесь](https://releases.aspose.com/words/net/).
- Visual Studio: в этом примере в качестве среды разработки используется Visual Studio.
- .NET Framework: Убедитесь, что на вашем компьютере установлен .NET Framework.
- Каталог документов: путь к каталогу, в котором хранятся ваши документы.

## Импорт пространств имен

Сначала импортируйте необходимые пространства имен в свой проект:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Шаг 1: Инициализация настроек шрифта

Первый шаг — инициализация настроек шрифтов. Это позволит вам управлять источниками шрифтов для ваших документов.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: этот класс используется для указания настроек подстановки шрифтов и источников шрифтов.
- fontSources: Мы создаем список существующих источников шрифтов на основе текущих настроек шрифтов.

## Шаг 2: Определите каталог документов

Далее укажите путь к каталогу ваших документов. Именно там Aspose.Words будет искать шрифты.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Эта строковая переменная содержит путь к каталогу, где находятся ваши шрифты. Заменить`"YOUR DOCUMENT DIRECTORY"` с реальным путем.

## Шаг 3: Добавьте папку с пользовательскими шрифтами

Теперь добавьте новый источник папки, чтобы указать Aspose.Words искать шрифты в этой папке.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Этот класс представляет источник шрифта папки. Второй параметр (`true`) указывает, следует ли выполнять рекурсивный поиск шрифтов во вложенных папках.

## Шаг 4: Обновите источники шрифтов

Добавьте папку с пользовательскими шрифтами в список существующих источников шрифтов и обновите настройки шрифтов.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): добавляет папку пользовательских шрифтов к существующим источникам шрифтов.
- updatedFontSources: преобразует список источников шрифтов в массив.

## Шаг 5: Извлечение и отображение шрифтов

Наконец, извлеките доступные шрифты и отобразите их сведения.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): извлекает список доступных шрифтов из первого источника шрифтов в обновленном списке.
-  fontInfo: Экземпляр`PhysicalFontInfo` содержащий подробную информацию о каждом шрифте.

## Заключение

Поздравляем! Вы успешно получили список доступных шрифтов с помощью Aspose.Words for .NET. Это руководство провело вас через каждый шаг, от инициализации настроек шрифта до отображения сведений о шрифте. С этими знаниями вы теперь можете легко управлять шрифтами в ваших документах Word. Помните, Aspose.Words for .NET — это мощный инструмент, который может значительно улучшить ваши возможности обработки документов. Так что продолжайте и изучите больше функций, чтобы сделать ваш процесс разработки еще более эффективным.

## Часто задаваемые вопросы

### Могу ли я использовать Aspose.Words для .NET с другими фреймворками .NET?
Да, Aspose.Words для .NET совместим с различными фреймворками .NET, включая .NET Core и .NET 5+.

### Как установить Aspose.Words для .NET?
Вы можете установить его через диспетчер пакетов NuGet в Visual Studio, выполнив поиск по запросу «Aspose.Words».

### Можно ли добавить несколько пользовательских папок шрифтов?
 Да, вы можете добавить несколько папок пользовательских шрифтов, создав несколько`FolderFontSource` экземпляров и добавление их в список источников шрифтов.

### Могу ли я получить сведения о шрифте из определенного источника шрифтов?
 Да, вы можете получить сведения о шрифте из любого источника шрифтов, указав индекс источника шрифтов в`updatedFontSources` множество.

### Поддерживает ли Aspose.Words для .NET замену шрифтов?
Да, он поддерживает замену шрифтов, что гарантирует корректную визуализацию текста, даже если исходный шрифт недоступен.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
