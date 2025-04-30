---
"description": "Узнайте, как управлять заменой шрифтов без суффиксов в Aspose.Words для .NET. Следуйте нашему пошаговому руководству, чтобы ваши документы всегда выглядели идеально."
"linktitle": "Получить замену без суффиксов"
"second_title": "API обработки документов Aspose.Words"
"title": "Получить замену без суффиксов"
"url": "/ru/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Получить замену без суффиксов

## Введение

Добро пожаловать в это всеобъемлющее руководство по управлению заменой шрифтов с помощью Aspose.Words для .NET. Если вы когда-либо сталкивались с тем, что шрифты не отображались правильно в ваших документах, вы попали по адресу. Это руководство проведет вас через пошаговый процесс эффективной обработки замены шрифтов без суффиксов.

## Предпосылки

Прежде чем приступить к изучению руководства, убедитесь, что у вас есть следующее:

- Базовые знания C#: понимание программирования на C# облегчит выполнение шагов и их реализацию.
- Библиотека Aspose.Words for .NET: Загрузите и установите библиотеку с сайта [ссылка для скачивания](https://releases.aspose.com/words/net/).
- Среда разработки: настройте среду разработки, например Visual Studio, для написания и запуска вашего кода.
- Образец документа: Образец документа (например, `Rendering.docx`) для работы в ходе этого урока.

## Импорт пространств имен

Во-первых, нам необходимо импортировать необходимые пространства имен для доступа к классам и методам, предоставляемым Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Шаг 1: Определите каталог документов

Для начала укажите каталог, в котором находится ваш документ. Это поможет найти документ, над которым вы хотите работать.

```csharp
// Путь к каталогу ваших документов
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Шаг 2: Настройка обработчика предупреждений о замене

Далее нам нужно настроить обработчик предупреждений, который будет уведомлять нас всякий раз, когда происходит замена шрифта во время обработки документа. Это имеет решающее значение для обнаружения и обработки любых проблем со шрифтами.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Шаг 3: Добавьте пользовательские источники шрифтов

На этом этапе мы добавим пользовательские источники шрифтов, чтобы Aspose.Words мог находить и использовать правильные шрифты. Это особенно полезно, если у вас есть определенные шрифты, хранящиеся в пользовательских каталогах.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

В этом коде:
- Мы извлекаем текущие источники шрифтов и добавляем новые `FolderFontSource` указывая на наш каталог пользовательских шрифтов (`C:\\MyFonts\\`).
- Затем мы обновляем источники шрифтов этим новым списком.

## Шаг 4: Сохраните документ.

Наконец, сохраните документ после применения настроек замены шрифта. Для этого урока мы сохраним его как PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Шаг 5: Создание класса обработчика предупреждений

Для эффективной обработки предупреждений создайте пользовательский класс, реализующий `IWarningCallback` интерфейс. Этот класс будет захватывать и регистрировать любые предупреждения о замене шрифтов.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

В этом классе:
- The `Warning` метод фиксирует предупреждения, связанные с заменой шрифтов.
- The `FontWarnings` коллекция сохраняет эти предупреждения для дальнейшей проверки или регистрации.

## Заключение

Теперь вы освоили процесс обработки замены шрифтов без суффиксов с помощью Aspose.Words для .NET. Эти знания гарантируют, что ваши документы сохранят свой предполагаемый вид, независимо от шрифтов, доступных в системе. Продолжайте экспериментировать с различными настройками и источниками, чтобы полностью использовать возможности Aspose.Words.

## Часто задаваемые вопросы

### Как использовать шрифты из нескольких пользовательских каталогов?

Вы можете добавить несколько `FolderFontSource` экземпляры к `fontSources` перечислите и обновите источники шрифтов соответствующим образом.

### Где можно загрузить бесплатную пробную версию Aspose.Words для .NET?

Вы можете загрузить бесплатную пробную версию с сайта [Страница бесплатной пробной версии Aspose](https://releases.aspose.com/).

### Могу ли я обрабатывать несколько типов предупреждений с помощью `IWarningCallback`?

Да, `IWarningCallback` Интерфейс позволяет обрабатывать различные типы предупреждений, а не только замену шрифтов.

### Где я могу получить поддержку по Aspose.Words?

Для получения поддержки посетите [Форум поддержки Aspose.Words](https://forum.aspose.com/c/words/8).

### Можно ли приобрести временную лицензию?

Да, вы можете получить временную лицензию в [временная страница лицензии](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}