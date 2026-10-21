---
category: general
date: 2026-10-13
description: Группировка фигур в Word с помощью C# — узнайте, как группировать фигуры
  и добавлять их в группу, используя Aspose.Words, в несколько простых шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: ru
lastmod: 2026-10-13
og_description: Группировать фигуры в Word с помощью C# и Aspose.Words. Следуйте этому
  руководству, чтобы узнать, как группировать фигуры и добавлять их в группу в документе
  Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Группировка фигур в Word с помощью C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Группировка фигур в Word с помощью C# — полное руководство по программированию
url: /ru/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Группировка фигур в Word с помощью C# – полное руководство по программированию

Если вам нужно **группировать фигуры в Word** программно, это руководство покажет вам точный способ. К концу первых двух предложений вы будете знать необходимый код, причину каждого шага и как **добавлять фигуры в группу** без неожиданностей.

Мы рассмотрим всё от загрузки файла `.docx` до сохранения обновлённого документа. В руководстве предполагается, что у вас есть базовые знания C# и ссылка на библиотеку Aspose.Words for .NET. Внешняя документация не требуется — просто скопируйте, вставьте и запустите.

## Необходимые условия

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Документ Word (`input.docx`), который уже содержит как минимум две фигуры (например, изображения, AutoShapes)

> **Совет:** Если вы тестируете, создайте простой файл Word с двумя прямоугольниками через пользовательский интерфейс Word. Сохраните его как `input.docx` в папке, которой вы управляете.

## Группировка фигур в Word – пошаговое руководство

Ниже мы разбиваем процесс на пять логических шагов. Каждый шаг включает точный код C#, объяснение *почему* эта строка необходима и короткую заметку о распространённых подводных камнях.

### Шаг 1: Загрузка документа Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Почему:** `Document` — точка входа для любой работы с Word. Указание полного пути к файлу загружает документ в память, позволяя нам запрашивать и изменять его дерево узлов.

**Подводный камень:** Передача относительного пути может привести к ошибке, если рабочий каталог отличается. Используйте абсолютный путь или `Path.Combine` с `AppContext.BaseDirectory`.

### Шаг 2: Получение фигур, которые нужно сгруппировать

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Почему:** `GetChild` проходит по дереву документа и возвращает *n‑й* узел запрошенного типа. Установка `isDeep` в `true` ищет по всему документу, а не только в текущем разделе.

**Пограничный случай:** Если в документе меньше двух фигур, `firstShape` или `secondShape` будут `null`, и при попытке приведения будет выброшено исключение. Защититесь от этого:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Шаг 3: Создание нового контейнера `GroupShape`

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Почему:** `GroupShape` выступает в роли родительского узла, который может содержать несколько объектов `Shape`. Он наследуется от `Shape`, поэтому его можно вставлять в любое место, где допускается обычная фигура (например, внутри абзаца).

### Шаг 4: Добавление отдельных фигур в группу

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Почему:** `AppendChild` перемещает фигуры из их исходных мест в новую группу. После этого вызова оригинальные фигуры больше не существуют как независимые узлы; они становятся частью `groupShape`.

**Совет:** При группировке автоматически корректируются относительные позиции дочерних фигур. Если вам нужен определённый макет, установите свойство `GroupShape.Bounds` *до* добавления дочерних элементов.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Шаг 5: Вставка групповой фигуры в тело документа

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Почему:** `GroupShape` должна быть размещена внутри абзаца (или ячейки таблицы), чтобы отобразиться. Добавив её к первому абзацу, мы гарантируем видимое размещение без нарушения существующего макета.

### Шаг 6: Сохранение изменённого документа

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Почему:** `Save` записывает изменения из памяти обратно в файл `.docx`. Вы также можете сохранить в поток или в PDF, изменив перегрузку.

**Проверка результата:** Откройте `output.docx` в Microsoft Word. Вы должны увидеть две оригинальные фигуры, теперь объединённые в один групповой объект. При выборе группы отобразятся стандартные маркеры группировки Word.

## Как программно группировать фигуры – более глубокие сведения

- **Node ownership:** При вызове `AppendChild` ссылка `ParentNode` у фигуры изменяется автоматически. Это предотвращает появление «осиротевших» узлов, которые могут повредить документ.
- **Preserving formatting:** При группировке **не** теряется форматирование фигур (цвет заливки, стиль линии и т.д.). Все дочерние фигуры сохраняют свои исходные свойства.
- **Nested groups:** `GroupShape` может содержать другие объекты `GroupShape`, позволяя создавать многоуровневые иерархии. Просто рассматривайте вложенную группу как любую другую фигуру.

## Добавление фигур в группу и последующее управление ими

Если вам нужно добавить больше фигур после создания первоначальной группы, вы можете повторно использовать тот же экземпляр `GroupShape`:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Когда позже понадобится разгруппировать, пройдитесь по `groupShape.GetChildNodes(NodeType.Shape, true)` и заново вставьте каждый дочерний элемент туда, где вы хотите его разместить.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Почему это важно:** Некоторые рабочие процессы требуют временной группировки (например, выравнивание нескольких объектов) с последующим разгруппированием для дальнейшего индивидуального редактирования.

## Полный исполняемый пример

Ниже представлена автономная программа, которую можно скомпилировать и запустить как есть. Замените `YOUR_DIRECTORY` реальным путём к папке на вашем компьютере.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Ожидаемый результат:** При открытии `output.docx` две оригинальные фигуры появятся как один групповой объект. Выбор группы покажет привычные маркеры группировки Word, позволяя перемещать, изменять размер или вращать весь набор вместе.

## Заключение

Теперь вы знаете, как **группировать фигуры в Word** с помощью C# и Aspose.Words, и видели точные шаги для **добавления фигур в группу** и последующего их управления или разгруппировки. Эта техника идеальна для автоматизации макетов отчетов, создания составных диаграмм или подготовки шаблонов Word, требующих точного позиционирования нескольких объектов.

Далее изучайте связанные темы, такие как **как группировать фигуры** с различными типами привязки, применение **расширенного форматирования** к групповым объектам или экспорт сгруппированного результата в PDF. Экспериментируйте с вложенными группами для создания сложной графики программно.

Удачной разработки!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставка фигур в документы Word с использованием Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Создание групповой фигуры в документе Word с использованием Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Добавление эффекта тени к фигурам Word – Полное руководство C#](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}