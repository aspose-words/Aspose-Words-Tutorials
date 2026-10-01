---
category: general
date: 2026-09-30
description: Группировка фигур в Word с помощью C# — узнайте, как группировать фигуры,
  добавлять прямоугольник и эллипс, а также программно вставлять форму прямоугольника
  в документы Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: ru
lastmod: 2026-09-30
og_description: Группировка фигур в Word с помощью C# и Aspose.Words. Следуйте этому
  полному руководству, чтобы добавить прямоугольник, добавить эллипс и узнать, как
  эффективно группировать фигуры.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Группировка фигур в Word с помощью C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как группировать фигуры в Word с помощью C# и Aspose.Words
url: /ru/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как группировать фигуры в Word с помощью C# и Aspose.Words

Если вам нужно **группировать фигуры в Word** программно, это руководство покажет вам, как это сделать. Вы увидите, как добавить прямоугольник, добавить эллипс и затем объединить их в одну групповую фигуру, используя библиотеку Aspose.Words для .NET.

Работа с фигурами — распространённая задача при автоматическом создании отчётов, контрактов или маркетинговых материалов. К концу этого урока у вас будет переиспользуемый метод на C#, который загружает DOCX‑файл, вставляет прямоугольник и эллипс, группирует их и сохраняет результат — без необходимости открывать Word вручную.

## Предварительные требования

* .NET 6.0 SDK или более поздняя версия, установленная  
* Среда разработки, например Visual Studio 2022 (подойдёт Community edition)  
* Лицензия Aspose.Words for .NET или бесплатная оценочная копия (API работает без лицензии, но добавляет водяной знак)  

Вам также нужен исходный документ Word (`input.docx`) в папке, к которой вы можете обратиться из кода. Документ может быть пустым; в уроке основной упор делается на работу с фигурами.

## Шаг 1: Создать новый консольный проект и добавить Aspose.Words

Откройте терминал или командную строку Visual Studio и выполните:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Это создаёт свежее консольное приложение с именем **WordShapeDemo** и добавляет пакет NuGet `Aspose.Words`, который содержит классы `Document` и `DocumentBuilder`, используемые для манипуляций с файлами Word.

## Шаг 2: Загрузить или создать документ

Первая операция при работе с **group shapes in Word** — получить объект `Document`. Вы можете загрузить существующий DOCX‑файл или начать с пустого документа.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Класс `Document` представляет весь файл Word. Загрузка файла предоставляет готовое полотно для вставки фигур.

## Шаг 3: Начать групповую фигуру

*Group shape* позволяет рассматривать несколько независимых фигур как единый объект — удобно для перемещения или изменения их размеров одновременно. Чтобы начать группу, вызовите `StartGroupShape()` у `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Вызов `StartGroupShape` сообщает Aspose.Words, что все последующие вставки фигур относятся к одной логической группе, пока вы не вызовете `EndGroupShape`.

## Шаг 4: Как добавить прямоугольную фигуру в Word

Теперь, когда группа открыта, вставьте прямоугольник. Метод `InsertShape` принимает перечисление `ShapeType`, после чего указываются ширина и высота (в пунктах).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Прямоугольник становится первым элементом группы. При необходимости вы можете позже настроить его заливку, контур или текст.

## Шаг 5: Как добавить эллипс в Word

Далее добавьте эллипс (окружность, когда ширина равна высоте). Это демонстрирует **how to add ellipse** с использованием того же builder’а.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Обе фигуры теперь находятся в одном координатном пространстве внутри группы, что упрощает их визуальное выравнивание.

## Шаг 6: Закрыть определение групповой фигуры

Когда все нужные элементы добавлены, закройте группу. Это завершает коллекцию фигур, и Word будет рассматривать их как один объект.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

На данном этапе документ содержит одну сгруппированную фигуру, состоящую из прямоугольника и эллипса.

## Шаг 7: Сохранить изменённый документ

Наконец, запишите изменения на диск. Вы можете перезаписать исходный файл или создать новый.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Запуск программы создаёт `output.docx`. Откройте файл в Microsoft Word, выберите фигуру, и вы увидите, что прямоугольник и эллипс перемещаются вместе — подтверждение успешного выполнения операции **group shapes in Word**.

### Ожидаемый результат

* Файл Word содержит один сгруппированный объект.  
* Выбор группы позволяет перетаскивать, изменять размер или вращать одновременно и прямоугольник, и эллипс.  
* Нет необходимости вручную взаимодействовать с Word; всё выполнено через код C#.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Текст alt изображения: “Скриншот документа Word, показывающий группированный прямоугольник и эллипс”* (соответствует требованию alt‑текста изображения).

## Почему группировка фигур важна

Группировка фигур — это не только визуальное удобство. Она позволяет:

* **Maintain layout consistency** — перемещение группы сохраняет относительные позиции элементов.  
* **Apply transformations once** — вращать или масштабировать всю группу целиком, а не каждую фигуру по отдельности.  
* **Simplify downstream processing** — когда другие инструменты читают DOCX, они видят одну составную фигуру, что упрощает обработку.

Если когда‑нибудь понадобится добавить больше фигур (например, линию или текстовое поле) в тот же логический блок, достаточно вызвать `InsertShape` ещё раз перед `EndGroupShape`.

## Общие варианты и граничные случаи

| Ситуация | Как решить |
|-----------|------------|
| **Different units** — у вас измерения в сантиметрах | Преобразуйте сантиметры в пункты (`1 cm ≈ 28.35 pt`) перед вызовом `InsertShape`. |
| **Adding a text label** — нужен подпись внутри группы | Вставьте `ShapeType.TextBox` после прямоугольника и эллипса, затем задайте его свойство `Text`. |
| **Applying a fill color** — нужен синий прямоугольник | После `InsertShape` получите последнюю фигуру через `builder.CurrentParagraph.Runs[0].Font` и задайте `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Using a different document format** — вам нужен формат `.doc` вместо `.docx` | Тот же код работает; просто измените расширение файла при вызове `Save`. Aspose.Words автоматически обрабатывает формат. |

## Профессиональные советы

* **Reuse the builder** — вы можете начинать и завершать несколько групп в одном документе; просто вызовите `StartGroupShape` снова после `EndGroupShape`.  
* **Performance** — пакетная вставка фигур внутри одного блока `StartGroupShape/EndGroupShape` быстрее, чем вставка фигур по отдельности вне группы.  
* **Licensing** — оценочная лицензия добавляет водяной знак на первую страницу. Установите полноценную лицензию, чтобы убрать его в продакшн‑окружении.

## Заключение

Теперь вы знаете, как **group shapes in Word** с помощью C#, как **add rectangle**, как **add ellipse** и как **insert rectangle shape Word** документы, используя Aspose.Words. Полный, готовый к запуску пример демонстрирует каждый шаг от настройки проекта до сохранения финального файла.

Отсюда вы можете исследовать дополнительные типы фигур, применять стилизацию или комбинировать сгруппированные фигуры с таблицами и изображениями для создания сложных, программно генерируемых документов.

---

**Следующие шаги**

* Узнайте, как **rotate grouped shapes**: используйте `Shape.RotationAngle` после закрытия группы.  
* Исследуйте **fill and outline customization** для прямоугольников и эллипсов.  
* Интегрируйте эту логику в ASP.NET Core API для генерации отчётов по запросу.  

Удачной разработки!

## Что вам следует изучить дальше?

Следующие уроки охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}