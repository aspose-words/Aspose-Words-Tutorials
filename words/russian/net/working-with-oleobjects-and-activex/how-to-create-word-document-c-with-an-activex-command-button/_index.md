---
category: general
date: 2026-10-26
description: Узнайте, как создать документ Word на C# и программно добавить кнопку
  ActiveX. Это пошаговое руководство охватывает вставку командной кнопки, её скрытие
  во время разработки и сохранение файла.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: ru
lastmod: 2026-10-26
og_description: Создайте документ Word на C# и программно добавьте кнопку ActiveX.
  Следуйте этому полному руководству, чтобы встроить кнопку‑команду, отображающуюся
  только во время выполнения.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Создание документа Word на C# с кнопкой ActiveX – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Как создать документ Word в C# с кнопкой ActiveX
url: /ru/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать документ Word C# с кнопкой ActiveX

Если вам нужно **создать документ Word C#**, содержащий интерактивную кнопку, это руководство покажет вам точный порядок действий. К концу первых двух предложений вы поймёте общий подход, а последующие шаги проведут вас через каждую строку кода, которую необходимо написать.

Вы узнаете, как добавить кнопку ActiveX, скрыть её во время разработки и сделать видимой только при открытии файла пользователем. Руководство также охватывает распространённые подводные камни, такие как предупреждения безопасности и совместимость версий, чтобы вы могли поставлять надёжные документы.

## Требования

* .NET 6.0 или новее, установленный  
* Лицензионная копия **Aspose.Words for .NET** (бесплатная пробная версия подходит для экспериментов)  
* Базовые знания C# и Visual Studio (подойдёт любой IDE, поддерживающий .NET)  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words`.

## Шаг 1: Создать документ Word C# и инициализировать DocumentBuilder

Первый шаг — создать объект `Document` и `DocumentBuilder`. `Document` представляет весь файл .docx, а `DocumentBuilder` предоставляет удобные методы для добавления содержимого.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Почему это важно:** Без `DocumentBuilder` вам пришлось бы вручную манипулировать DOM OpenXML, что склонно к ошибкам и труднее читается. Builder абстрагирует эти детали и гарантирует корректно сформированный файл Word.

## Шаг 2: Как добавить кнопку ActiveX – вставить элемент управления CommandButton

Теперь мы вставляем **элемент управления CommandButton ActiveX** в определённое место. Прямоугольник задаёт позицию кнопки (X, Y) и её размер (ширина, высота) в пунктах.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Почему это важно:** `InsertForms2OleControl` — единственный метод Aspose.Words, создающий настоящий объект ActiveX OLE. Значение перечисления `Forms2OleControlType.CommandButton` указывает Word встроить кликабельную кнопку, а не обычный контейнер OLE.

## Шаг 3: Программно добавить кнопку команды – скрыть её до выполнения

Word по умолчанию считает любую вставленную форму видимой. Чтобы скрыть кнопку во время разработки шаблона, установите свойство `Hidden` у формы, которую только что создал builder.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Почему это важно:** Установка `Hidden = true` предотвращает появление кнопки в режиме дизайна. Когда документ открывается в Word, среда выполнения автоматически отображает элемент управления, сохраняя задуманное пользовательское взаимодействие.

## Шаг 4: Сохранить файл – создать документ Word с кнопкой команды

Наконец, запишите документ на диск. Выберите путь, в который ваше приложение имеет права записи, и используйте расширение `.docx` для обеспечения современной совместимости.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Почему это важно:** Сохранение в формате `.docx` гарантирует, что встроенный элемент ActiveX соответствует стандарту Office Open XML, поддерживаемому Word 2007 и новее. Если требуется поддержка устаревшего формата `.doc`, замените расширение и используйте `SaveFormat.Doc`.

## Полный рабочий пример

Объединив всё вместе, представляем полный пример программы, который вы можете скопировать, вставить и запустить:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Ожидаемый результат:** После запуска программы откройте `C:\Temp\ActiveX.docx` в Microsoft Word. Вы увидите пустой документ; кнопка не видна в режиме дизайна. Нажмите **Alt + F9**, чтобы переключить отображение полей, затем кликните по области кнопки — Word отобразит элемент управления ActiveX, и вы сможете взаимодействовать с ним (например, двойным щелчком открыть свойства).

## Пограничные случаи и рекомендации по лучшим практикам

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Пользователь отключает ActiveX** | Word может показать предупреждение безопасности или заблокировать элемент управления. | Попросите конечных пользователей включить «ActiveX controls» в Центре доверия или предоставить макрос‑подписанную альтернативу. |
| **Документ открыт в Word Online** | Word Online не поддерживает ActiveX; кнопка будет удалена. | Используйте резервную гиперссылку или элемент управления содержимым, если нужна облачная совместимость. |
| **Разные настройки DPI** | Размер прямоугольника может выглядеть больше или меньше на дисплеях с высоким DPI. | Используйте `GraphicsUnit.Point` (по умолчанию) и протестируйте на типичных настройках DPI (96 dpi, 120 dpi). |
| **Несколько кнопок** | Вызов `GetChildNodes(NodeType.Shape, true)[0]` получает только первую форму. | Пройдитесь в цикле по `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` и установите `Hidden` для каждой добавляемой формы. |
| **Устаревший формат .doc** | Некоторые свойства ActiveX теряются при сохранении в `.doc`. | Предпочтительно использовать `.docx`, если только нет строгой необходимости в старом формате. |

**Совет:** После вставки кнопки вы можете назначить макрос её свойству `OnAction` через интерфейс Word. Это позволяет определить пользовательское действие при клике без написания дополнительного кода C#.

## Часто задаваемые вопросы

* **Работает ли это с .NET Core?**  
  Да. Aspose.Words for .NET полностью совместим с .NET 5, .NET 6 и более новыми версиями. Просто укажите тот же пакет NuGet.

* **Можно ли изменить подпись кнопки после генерации документа?**  
  Подпись, установленная в `InsertForms2OleControl`, становится текстом по умолчанию в режиме дизайна. Пользователи могут изменить её в Word, но вы также можете обновить подпись программно, получив доступ к свойствам OLE‑объекта через API `Shape.OleFormat`.

* **Что делать, если нужен другой размер кнопки?**  
  Отрегулируйте значения `RectangleF`. Первые два параметра — координаты X и Y; последние два — ширина и высота в пунктах (1 pt = 1/72 дюйма).

## Заключение

Теперь вы знаете, как **создать документ Word C#** и **программно добавить кнопку команды** с помощью Aspose.Words. Руководство охватило инициализацию документа, вставку кнопки ActiveX, её скрытие до выполнения и сохранение конечного файла. С этими строительными блоками вы можете внедрять интерактивные элементы управления в любой шаблон Word, который генерируете.

Далее изучайте связанные темы, такие как **how to add ActiveX button** обработка событий, **create command button word** стилизация с VBA и **programmatically add command button** в существующие документы. Расширение этого шаблона на флажки, комбобоксы или пользовательские OLE‑объекты следует тем же шагам — просто измените значение перечисления `Forms2OleControlType`.

Начните экспериментировать: замените подпись, скорректируйте позицию или соедините несколько элементов управления. Чем больше вы практикуете, тем легче будет создавать насыщенные интерактивные документы Word из C#. Приятного кодинга!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, опирающиеся на техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как программно добавить кнопку команды в документ Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Как добавить кнопку ActiveX в документ Word с помощью Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Создание документа Word с кнопкой ActiveX – руководство C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}