---
category: general
date: 2026-09-14
description: Узнайте, как скрыть форму в Word с помощью C# — включая код создания
  документа Word, вставку прямоугольной формы в Word и программное скрытие формы в
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: ru
lastmod: 2026-09-14
og_description: Как скрыть форму в Word с помощью C# — пошаговое руководство, в котором
  также показано, как создать код документа Word и вставить прямоугольную форму.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Как скрыть фигуру в документе Word с помощью кода C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как скрыть фигуру в документе Word с помощью кода C#
url: /ru/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как скрыть форму в документе Word с помощью кода C#

Если вам нужно **how to hide shape** в файле Word, этот учебник показывает полное решение. Вы увидите, как создать документ Word, вставить прямоугольную форму, добавить эллипс и скрыть этот эллипс, чтобы при открытии файла отображался только прямоугольник.

Руководство охватывает всё, что вам понадобится — без внешних ссылок, только код и объяснения. К концу вы сможете внедрять скрытую графику в любой документ Word, генерируемый программно.

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- Aspose.Words for .NET (бесплатная пробная версия или лицензия)  
  Установите её через NuGet: `dotnet add package Aspose.Words`
- Базовое знакомство с C# и Visual Studio или любой другой IDE по вашему выбору

## Шаг 1: Настройка проекта и импорт пространств имён

Создайте новое консольное приложение и добавьте необходимые `using`‑операторы. Эти импорты дают доступ к классам `Document`, `DocumentBuilder` и рисования, необходимым для работы с формами.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Почему это важно** – Импорт правильных пространств имён предотвращает ошибки компиляции и делает доступным API для создания форм и управления их видимостью.

## Шаг 2: Создание нового документа Word и билдера

`Document` представляет файл, а `DocumentBuilder` предоставляет удобный API для добавления содержимого. Здесь вы впервые применяете логику **how to hide shape**: нужен контекст документа, прежде чем может существовать какая‑либо форма.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Объяснение** – Объект `Document` изначально пуст. `DocumentBuilder` позиционируется в начале первого абзаца, готовый вставлять формы или текст.

## Шаг 3: Вставка видимой прямоугольной формы

Прямоугольник будет формой, остающейся видимой при открытии документа. Вы можете управлять его размером, положением и форматированием напрямую через объект формы.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Почему этот шаг** – Добавление прямоугольника демонстрирует требование **insert rectangle shape word**. Установка `FillColor` и `LineColor` делает форму легко заметной в конечном документе.

## Шаг 4: Вставка эллипса и его скрытие

Теперь добавляем форму, которую планируем скрыть. Свойство `Hidden` сообщает Word не отображать форму в пользовательском интерфейсе, хотя она остаётся частью структуры документа.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Объяснение** – Установка `Hidden = true` является ядром **hide shape in word**. Word учитывает этот флаг при обычном просмотре и печати, но форма всё ещё доступна программно, если это необходимо.

## Шаг 5: Сохранение документа

Наконец, запишите документ на диск. Выберите папку, в которой у вас есть права записи, и дайте файлу понятное имя, отражающее цель учебника.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Результат** – Открытие `ShapeVisibility.docx` в Microsoft Word показывает только светло‑голубой прямоугольник. Скрытый эллипс не отображается, подтверждая, что вы успешно освоили **how to hide shape** в файле Word.

## Полный рабочий пример

Объединяя все фрагменты, получаем одну готовую к запуску программу:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Ожидаемый результат

- **Визуально**: При открытии `ShapeVisibility.docx` вы видите светло‑голубой прямоугольник, расположенный у левого поля. Эллипс не виден.
- **Программно**: Скрытый эллипс остаётся в XML‑структуре документа (`<w:drawing>` элемент) с установленным атрибутом `w:hidden`, что можно проверить, открыв файл как zip‑архив и изучив `document.xml`.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| *Можно ли скрыть несколько форм?* | Да. Установите `Hidden = true` для каждой формы, которую хотите скрыть. |
| *Будут ли скрытые формы печататься?* | По умолчанию Word не печатает скрытые объекты. Если требуется печать, очистите флаг `Hidden` перед печатью. |
| *Поддерживается ли свойство hidden в более старых версиях Word?* | Атрибут `Hidden` является частью стандарта Office Open XML и работает в Word 2007 и новее. |
| *Что если нужно переключать видимость во время выполнения?* | Получите форму через `document.GetChildNodes(NodeType.Shape, true)` и измените свойство `Hidden` в зависимости от вашей логики. |

## Профессиональные советы

- **Производительность**: При генерации большого количества документов переиспользуйте один экземпляр `DocumentBuilder` вместо создания нового для каждого файла.
- **Контроль версий**: Храните сгенерированные файлы `.docx` в папке под контролем версий; скрытые формы могут служить маркерами метаданных для последующей обработки.
- **Тестирование**: Автоматизируйте быструю визуальную проверку, конвертировав DOCX в PDF с помощью Aspose.Words (`document.Save("out.pdf")`). PDF также скроет эллипс, подтверждая, что флаг скрытия распространяется при конвертации форматов.

## Заключение

Теперь вы знаете **how to hide shape** в документе Word с использованием C#. В учебнике последовательно показано создание документа, **insert rectangle shape word**, добавление эллипса и применение флага `Hidden` для достижения поведения **hide shape in word**. Имея полностью готовый код, вы можете интегрировать скрытую графику в любой автоматизированный процесс отчётности или шаблонизации.

### Следующие шаги

- Исследуйте другие свойства форм, такие как вращение, тень и обтекание текстом.  
- Сочетайте скрытые формы с пользовательскими свойствами документа для внедрения машинно‑читаемых данных.  
- Изучите шаблоны **create word document code** для таблиц, диаграмм и элементов управления содержимым, чтобы расширить свой набор инструментов автоматизации.

Экспериментируйте с различными типами форм и настройками видимости — ваш следующий проект по автоматизации Word находится всего в нескольких строках кода!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создать прямоугольную форму в Word с помощью C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Создать пустой документ Word с прямоугольником в тени – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Добавить тень к форме Word в C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}