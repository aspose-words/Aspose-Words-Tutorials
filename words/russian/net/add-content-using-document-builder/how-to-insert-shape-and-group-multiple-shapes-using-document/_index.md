---
category: general
date: 2026-11-15
description: Узнайте, как вставлять фигуру в документ Word и группировать несколько
  фигур с помощью Aspose.Words DocumentBuilder. Включает примеры вставки прямоугольной
  фигуры и вставки нескольких фигур.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: ru
lastmod: 2026-11-15
og_description: Как вставить фигуру в файл Word с помощью Aspose.Words. Это руководство
  охватывает группировку нескольких фигур, вставку прямоугольной фигуры и эффективное
  добавление нескольких фигур.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Как вставить фигуру и сгруппировать несколько фигур с помощью DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Как вставить фигуру и сгруппировать несколько фигур с помощью DocumentBuilder
  в C#
url: /ru/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить форму и сгруппировать несколько форм с помощью DocumentBuilder в C#

Если вам нужно знать **how to insert shape** в документ Word с помощью Aspose.Words, это руководство покажет вам точные шаги. Вы также узнаете, как **group multiple shapes**, чтобы они вели себя как один объект, и как **insert rectangle shape** вместе с другими графическими элементами.

Автоматизация документов часто требует добавления нескольких графических элементов — диаграмм, логотипов, выноски — при этом сохраняя их упорядоченными. К концу этого руководства вы сможете **insert multiple shapes**, разместить их внутри группы и сохранить чистый, переиспользуемый макет.

## Требования

* .NET 6.0 или новее установлен  
* Visual Studio 2022 (или любая IDE для C#)  
* Лицензия Aspose.Words для .NET или бесплатный оценочный ключ  
* Базовое знакомство с C# и классом Aspose.Words `DocumentBuilder`  

Вам **не** нужны какие‑либо другие сторонние библиотеки; всё необходимое входит в состав Aspose.Words.

## Шаг 1: Установить Aspose.Words через NuGet

Откройте ваш проект в Visual Studio и выполните следующую команду в консоли диспетчера пакетов:

```powershell
Install-Package Aspose.Words
```

Пакет включает классы `DocumentBuilder`, `Shape` и `GroupShape`, используемые в этом руководстве.

## Шаг 2: Создать экземпляр DocumentBuilder — фундамент для **how to insert shape**

Первая практическая строка кода — создание `DocumentBuilder`. Этот объект предоставляет прямой доступ к дереву документа, позволяя размещать формы точно там, где вы хотите.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Почему это важно*: `DocumentBuilder` поддерживает курсор (точку «вставки»). Каждый последующий вызов `Insert...` использует этот курсор, поэтому позже мы перемещаем его в `GroupShape`, чтобы все формы оставались вместе.

## Шаг 3: **Insert rectangle shape** — первая графика, которую вы добавите

Прямоугольник — распространённый заполнитель для таблиц, изображений или выноски. Используйте `InsertShape` с `ShapeType.Rectangle` и укажите ширину и высоту в пунктах (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Прямоугольник появляется в текущем положении курсора. При необходимости вы можете позже настроить его заливку, стиль линии или текст.

## Шаг 4: Вставить другую форму — эллипс для визуального разнообразия

Добавление более чем одной формы демонстрирует **insert multiple shapes**. Эллипс будет расположен после прямоугольника в потоке документа.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

На данном этапе документ содержит две независимые формы. Если вы переместите курсор или добавите текст, формы останутся на месте их вставки.

## Шаг 5: **Group multiple shapes** чтобы они действовали как единый объект

Группировка необходима, когда нужно перемещать, вращать или форматировать несколько графических элементов вместе. Следующий код создаёт `GroupShape`, перемещает курсор builder'а внутрь него и затем снова вставляет те же формы — на этот раз они становятся дочерними элементами группы.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Зачем использовать группу?

* **Single‑point transformation** — вращать или изменять размер всей группы одним вызовом.  
* **Logical organization** — дерево документа Word отражает группировку, упрощая последующие правки.  
* **Consistent layout** — перемещение группы сохраняет относительные позиции её дочерних элементов.

### Добавление дополнительных форм — расширение **insert multiple shapes** внутри группы

Вы можете продолжать вызывать `InsertShape`, пока курсор находится внутри `GroupShape`. Например, чтобы добавить треугольник:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

## Шаг 6: Сохранить документ и проверить результат

После размещения всех форм сохраните документ в файл `.docx`. Открытие файла в Microsoft Word (или любом совместимом просмотрщике) должно показать две отдельные формы, а затем сгруппированный набор, содержащий тот же прямоугольник, эллипс и треугольник.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Ожидаемый результат

* **First two shapes** — прямоугольник и эллипс, размещённые независимо на странице.  
* **Grouped block** — прямоугольник, эллипс и треугольник, которые перемещаются вместе при щелчке по любой из них в Word.

Вы можете проверить группировку, выбрав любую форму внутри группы; Word подсветит всю коллекцию, подтверждая, что операция **group multiple shapes** выполнена успешно.

## Распространённые подводные камни и профессиональные советы

| Проблема | Почему это происходит | Решение |
|----------|----------------------|---------|
| Формы появляются за пределами нужной страницы | Курсор builder'а не был перемещён в `GroupShape` перед вставкой. | Всегда вызывайте `builder.MoveTo(group)` **до** любых вызовов `InsertShape`, принадлежащих группе. |
| Группа исчезает после сохранения | Группа была вставлена без добавления в коллекцию узлов документа. | Используйте `builder.InsertNode(group)` сразу после создания `GroupShape`. |
| Неожиданный размер из‑за DPI документа | Aspose.Words использует пункты; если вы думаете в пикселях, размеры могут не совпадать. | Преобразуйте пиксели в пункты (`points = pixels * 72 / 96`) или работайте напрямую в пунктах. |
| Формы перекрываются непреднамеренно | Не было задано явного позиционирования; Word размещает их последовательно. | Установите `Shape.Left` и `Shape.Top` после вставки, чтобы контролировать точное размещение. |

**Pro tip:** После группировки вы можете получить коллекцию `Shapes` группы (`group.Shapes`), чтобы перебрать, переименовать или применить массовое форматирование.

## Шаг 7: Расширение примера — что дальше?

Теперь, когда вы знаете **how to insert shape**, **insert rectangle shape** и **group multiple shapes**, вы можете исследовать:

* **Animating grouped shapes** — задайте свойства вращения или отражения для группы.  
* **Applying styles** — используйте `Shape.FillColor`, `Shape.LineFormat` или `Shape.TextBox` для добавления меток.  
* **Exporting to PDF** — тот же сгруппированный макет корректно экспортируется при вызове `doc.Save("output.pdf")`.  

Все эти расширения используют тот же рабочий процесс `DocumentBuilder`, поддерживая ваш код чистым и поддерживаемым.

## Заключение

Это руководство продемонстрировало **how to insert shape** в документ Word с помощью Aspose.Words, как **insert rectangle shape**, и как **group multiple shapes**, чтобы они вели себя как один объект. Следуя пошаговому коду, вы сможете надёжно **insert multiple shapes**, организовать их в группы и программно создавать документы профессионального уровня.

Не стесняйтесь экспериментировать с различными типами форм, цветами и трансформациями групп. Когда будете готовы, интегрируйте этот шаблон в более крупные решения по отчётности или шаблонизации, чтобы автоматизировать сложные макеты документов. Приятного кодинга!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставка фигур в документы Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Как создать и вставить эллипс и прямоугольник внутри групповой формы в документе Word с помощью Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Как группировать формы в документе Word с помощью Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}