---
category: general
date: 2026-07-23
description: Создайте пустой документ Word и добавьте прямоугольную форму в C#. Узнайте,
  как вставлять формы и группировать формы в Word с помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: ru
lastmod: 2026-07-23
og_description: Создайте пустой документ Word на C# и узнайте, как вставлять фигуры,
  добавить прямоугольную форму и группировать фигуры в Word с помощью Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Создайте пустой документ Word с группированными прямоугольниками – учебник
  по C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Создание пустого документа Word с группированными прямоугольниками – руководство
  по C#
url: /ru/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание пустого документа Word с группированными прямоугольниками – руководство C#

Когда‑нибудь вам нужно было **создать пустой документ Word**, который уже содержит набор фигур, но вы не знали, как их красиво сгруппировать? Вы не одиноки. Во многих сценариях отчётности или генерации шаблонов вам нужен чистый холст с парой прямоугольников, выступающих в качестве заполнителей, и вы хотите, чтобы они перемещались вместе как единое целое.

В этом руководстве мы пройдём точные шаги, чтобы **создать пустой документ Word**, **добавить прямоугольную форму**, а затем **группировать формы Word** с помощью библиотеки Aspose.Words. К концу вы получите готовый к использованию файл `.docx`, где два прямоугольника находятся в одной группе, так что любое последующее позиционирование или изменение размеров будет влиять на оба сразу.

Мы также ответим на часто задаваемые вопросы «**как вставить формы**» и «**как группировать формы**», которые появляются на форумах и Stack Overflow. Никакой внешней документации не требуется — всё, что нужно, находится здесь.

---

## Требования

- .NET 6 или новее (код также компилируется с .NET Core)  
- Aspose.Words for .NET (пакет NuGet `Aspose.Words`)  
- Базовое понимание синтаксиса C# (если вы уже писали «Hello World», вам достаточно)  

Если вы ещё не установили Aspose.Words, выполните:

```bash
dotnet add package Aspose.Words
```

Вот и всё — никаких дополнительных DLL, без COM‑interop, только чистая ссылка NuGet.

---

## Шаг 1: Создать пустой документ Word и инициализировать builder

Первое, что мы делаем, — создаём пустой объект `Document`. Представьте его как чистый лист бумаги. Затем мы присоединяем `DocumentBuilder`, удобный инструмент, который предоставляет Aspose для вставки контента.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Почему это важно:** Без `DocumentBuilder` вам пришлось бы вручную манипулировать низкоуровневым деревом узлов, что склонно к ошибкам. Builder абстрагирует XML‑детали файла `.docx`.

---

## Шаг 2: Как вставить формы – сначала добавить контейнер группы

Aspose позволяет вставить *групповую форму*, которая позже может содержать другие формы. Это основа для **группировать формы Word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Pro tip:** Сама группа невидима, пока вы не добавите дочерние формы, поэтому в результирующем документе вы не увидите артефактов до следующего шага.

---

## Шаг 3: Добавить прямоугольную форму – реальные видимые объекты

Теперь мы **добавим прямоугольную форму** дважды, каждая со своим размером. Метод `InsertShape` принимает `ShapeType` и размеры в пунктах (1 pt ≈ 1/72 дюйма).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Почему прямоугольники?** Они самая простая геометрическая фигура, идеальная для заполнителей, имитаций кнопок UI или простых графических элементов.

---

## Шаг 4: Как группировать формы – присоединить прямоугольники к группе

После создания прямоугольников мы теперь **как группировать формы**, добавляя их как дочерние элементы к ранее вставленной групповой форме.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Что происходит под капотом?** Групповая форма становится родительским узлом в XML‑дереве документа. Перемещение группы перемещает оба прямоугольника вместе, сохраняя их относительные позиции.

---

## Шаг 5: Сохранить документ – теперь у вас файл Word с группированными формами

Наконец, сохраняем документ на диск. Измените путь на существующее расположение на вашем компьютере.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Это вся программа. Запустите её, откройте `GroupShape.docx`, и вы увидите два прямоугольника, сидящие вместе. Если выбрать один, вся группа будет выделена — именно то, что **группировать формы Word** должна делать.

---

## Полный исходный код в одном месте

Для удобства представляем полностью готовый к копированию пример:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Ожидаемый результат:** При открытии `GroupShape.docx` вы увидите пустую страницу с двумя сгруппированными прямоугольниками. Выбор одного прямоугольника автоматически выбирает другой, подтверждая успешное группирование.

---

## Часто задаваемые вопросы и обработка граничных случаев

### Что делать, если нужно больше двух форм?

Просто продолжайте вызывать `builder.InsertShape(...)` и `group.AppendChild(...)` для каждой новой формы. Группа может содержать любое количество дочерних элементов.

### Можно ли задать цвет заливки или границу прямоугольникам?

Конечно. После создания прямоугольника вы можете изменить его `FillColor`, `OutlineColor` и `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Как переместить всю группу после её создания?

Используйте свойства группы `Left` и `Top`, измеряемые в пунктах:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Как масштабировать группу?

Установите `group.Width` и `group.Height` или используйте `group.ScaleX` / `group.ScaleY`. Дочерние прямоугольники сохраняют свои пропорции относительно группы.

### Работает ли это с более старыми файлами .doc?

Aspose.Words абстрагирует формат файла, поэтому тот же код работает и для `.doc`, и для `.docx`. Единственное ограничение — некоторые новые возможности форм могут быть упрощены при сохранении в старый бинарный формат.

---

## Pro tips для production‑ready кода

- **Dispose of resources** — Оберните `Document` в блок `using`, если работаете с большими файлами, чтобы своевременно освобождать память.  
- **Error handling** — Перехватывайте `Aspose.Words.Fonts.FontSettingsException`, если планируете встраивать пользовательские шрифты.  
- **Performance** — При вставке большого количества форм временно отключайте обновления макета с помощью `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` и включайте их позже.

---

## Заключение

Теперь вы знаете, **как создать пустой документ Word**, **добавить прямоугольную форму** и **группировать формы Word** с помощью Aspose.Words в C#. Пример охватывает основные шаги «**как вставить формы**» и «**как группировать формы**», объясняет, почему каждая строка кода необходима, и даже затрагивает настройку, граничные случаи и лучшие практики.

Далее вы можете изучить **как вставлять изображения**, **добавлять текст внутри группированных форм** или **экспортировать документ в PDF** — всё это следует той же схеме использования `DocumentBuilder` и манипуляций формами. Экспериментируйте; API Aspose достаточно мощный, чтобы справиться почти с любой задачей автоматизации Word, которую только можно представить.

Счастливого кодинга, и не стесняйтесь оставить комментарий, если столкнётесь с трудностями!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Вставка форм в документы Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Создание групповой формы в документе Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создание прямоугольной формы в Word с использованием C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}