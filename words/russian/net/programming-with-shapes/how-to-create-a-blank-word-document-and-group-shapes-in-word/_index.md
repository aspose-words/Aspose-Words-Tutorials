---
category: general
date: 2026-10-20
description: Узнайте, как создать пустой документ Word, сгруппировать фигуры в Word,
  задать цвет заливки фигуры и использовать тип обтекания «в строке» с полным примером
  на C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: ru
lastmod: 2026-10-20
og_description: Создайте пустой документ Word, сгруппируйте фигуры в Word и задайте
  цвет заливки фигуры с типом обтекания inline, используя Aspose.Words и C#. Следуйте
  полному руководству.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Создайте пустой документ Word и сгруппируйте фигуры в Word – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Как создать пустой документ Word и сгруппировать фигуры в Word с помощью Aspose.Words
url: /ru/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать пустой документ Word и сгруппировать фигуры в Word

Если вам нужно **создать пустой документ Word**, содержащий несколько фигур, действующих как единый объект, это руководство покажет вам, как это сделать. Вы увидите, как **группировать фигуры в Word**, задать цвет заливки фигуры и применить **wrap type inline** — всё это в лаконичной, исполняемой C# программе.

В этом учебнике мы пройдем каждую строку кода, объясним, почему каждый шаг важен, и укажем распространённые подводные камни. К концу вы получите файл .docx, в котором прямоугольник и текстовое поле сгруппированы вместе, готовый к дальнейшей автоматизации.

## Чему вы научитесь

* Как инициализировать пустой файл Word с помощью Aspose.Words.
* Правильный способ создания **GroupShape** и добавления дочерних фигур.
* Приёмы **set shape fill color** и управления позиционированием.
* Использование **wrap type inline**, чтобы группа вела себя как один встроенный объект.
* Как сохранить и проверить результат.

Предыдущий опыт работы с Aspose.Words не требуется, но вы должны быть знакомы с базовым синтаксисом C# и иметь установленный Visual Studio (или другую IDE).

## Требования

| Требование | Причина |
|-------------|--------|
| .NET 6.0 or later | Обеспечивает среду выполнения для проекта C#. |
| Aspose.Words for .NET (latest version) | Предоставляет классы `Document`, `DocumentBuilder` и shape, используемые в примере. |
| A writable folder path | Вызов `doc.Save` требует действительного каталога для записи выходного файла. |
| Basic C# knowledge | Позволяет вам следовать коду и изменять его под свои сценарии. |

Установите Aspose.Words через NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Шаг 1: Создать пустой документ Word

Первая операция — **создать пустой документ Word**. Класс `Document` из Aspose.Words представляет Word‑файл в памяти, а `DocumentBuilder` предоставляет удобный API для его редактирования.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему это важно*: Начало с чистого документа гарантирует, что добавляемая вами групповая фигура будет единственным содержимым, что упрощает проверку.

## Шаг 2: Определить групповую фигуру с wrap type inline

**GroupShape** выступает контейнером для других фигур. Установка её `WrapType` в `Inline` гарантирует, что группа будет вести себя как один встроенный объект в потоке абзаца.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Почему это важно*: Использование **wrap type inline** предотвращает «плавание» группы от окружающего текста, что необходимо, когда вы хотите перемещать группу как единое целое.

## Шаг 3: Добавить прямоугольник и задать цвет заливки фигуры

Прямоугольник — распространённый визуальный элемент. Конструктор `Shape` принимает `ShapeType`; затем мы указываем размеры и цвет заливки.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Почему это важно*: Свойство `FillColor` демонстрирует **set shape fill color** на практике, задавая прямоугольнику светло‑голубой фон, который выделяется в итоговом документе.

## Шаг 4: Добавить текстовое поле — как эффективно группировать фигуры

Текстовое поле предоставляет редактируемый текст внутри группы. Позиционируйте его относительно системы координат группы, изменяя свойство `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Почему это важно*: Этот шаг отвечает на вопрос **how to group shapes** — путем добавления каждой дочерней фигуры в один и тот же экземпляр `GroupShape`. Смещение `Top` гарантирует, что текстовое поле появится под прямоугольником, демонстрируя точный контроль макета.

## Шаг 5: Вставить готовую групповую фигуру в документ

Теперь, когда группа содержит обе дочерние фигуры, вставьте её в текущую позицию builder.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Почему это важно*: Вставка группы как единого узла гарантирует, что Word будет рассматривать прямоугольник и текстовое поле как один логический объект, сохраняя их относительные позиции при редактировании.

## Шаг 6: Сохранить документ и проверить результат

Наконец, запишите документ на диск. Замените `YOUR_DIRECTORY` реальным путём на вашем компьютере.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Когда вы откроете `GroupShape.docx` в Microsoft Word, вы должны увидеть светло‑голубой прямоугольник с текстовым полем, помеченным «Grouped text», расположенным непосредственно под ним. Выбор любой из фигур выделит всю группу, подтверждая, что **group shapes in Word** работает как задумано.

### Ожидаемый результат

* Файл .docx, содержащий один абзац.
* Внутри абзаца — встроенная группа, выглядящая как один составной объект.
* Прямоугольник заполнен светло‑голубым цветом, а текстовое поле отображает «Grouped text».

![Снимок сгенерированного документа Word](grouped_shapes.png){.center width=600 alt="Снимок пустого документа Word с сгруппированным прямоугольником и текстовым полем, созданным с помощью Aspose.Words"}

## Часто задаваемые вопросы и обработка крайних случаев

### Что если мне нужно, чтобы группа плавала, а не была встроенной?

Замените `WrapType.Inline` на `WrapType.TopBottom` (или любое другое значение перечисления `WrapType`). Плавающие группы могут позиционироваться независимо от потока абзаца, но они теряют автоматическое выравнивание по строке.

### Можно ли добавить больше фигур, например круги или изображения?

Да. Создайте дополнительные объекты `Shape` с `ShapeType.Ellipse` или `ShapeType.Image`, настройте их свойства и вызовите `group.AppendChild(newShape)`. Группа автоматически расширится, чтобы вместить новые границы, если вы соответствующим образом обновите `group.Bounds`.

### Как изменить общий размер группы после добавления дочерних фигур?

Отрегулируйте `group.Bounds` после добавления всех дочерних фигур, либо программно вычислите объединение границ дочерних фигур. Это гарантирует, что область захвата группы соответствует визуальному содержимому.

### Что если папка вывода не существует?

Aspose.Words генерирует `DirectoryNotFoundException`. Сначала создайте каталог:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Работает ли это с .NET Framework вместо .NET Core?

Все используемые API (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) доступны в версии Aspose.Words для .NET Framework, поэтому тот же код работает без изменений.

## Профессиональные советы

* **Совет по производительности** — Переиспользуйте один экземпляр `DocumentBuilder` при вставке множества групп; создание нового builder для каждой группы добавляет накладные расходы.
* **Визуальная согласованность** — Установите `rectangle.StrokeColor` в тот же цвет, что и `FillColor`, для бесшовного вида, либо задайте `rectangle.LineWidth = 0`, чтобы скрыть границу.
* **Отладка** — Вызовите `doc.UpdatePageLayout()` перед сохранением, если вы модифицируете много фигур; это заставит Word пересчитать макет и может предотвратить неожиданное обрезание.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **группировать фигуры в Word**, **задать цвет заливки фигуры** и применить **wrap type inline** с помощью Aspose.Words для .NET. Полный пример демонстрирует стандартный подход к созданию составной графики, которая ведёт себя как один объект в Word.

Отсюда вы можете исследовать:

* Добавление дополнительных фигур, таких как изображения или диаграммы.
* Эксперименты с различными значениями `WrapType` для плавающих групп.
* Автоматизацию пакетного создания сгруппированных диаграмм в нескольких документах.

Не стесняйтесь адаптировать код под свои сценарии автоматизации и делиться результатами в комментариях!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}