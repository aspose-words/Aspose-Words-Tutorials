---
category: general
date: 2026-01-08
description: Создайте пустой документ Word и узнайте, как добавить тень к прямоугольной
  фигуре. Вставьте файлы Word с фигурой и добавьте тень к фигуре в C# с помощью Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: ru
og_description: Создайте пустой документ Word и посмотрите, как добавить тень к прямоугольной
  фигуре с помощью C#. Полный код, объяснения и советы.
og_title: Создать пустой документ Word – добавить прямоугольник с тенью
tags:
- Aspose.Words
- C#
- Document Automation
title: Создайте пустой документ Word с прямоугольником с тенью – пошаговое руководство
url: /ru/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание пустого документа Word с фигурой прямоугольника с тенью – Полный учебник

Когда‑нибудь вам нужно было **create blank Word** файлы программно, а затем украсить их красивым прямоугольником с тенью? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда обнаруживают, что вставка фигур и применение эффектов не так просто, как ввод текста.  

В этом руководстве мы пройдем весь процесс — от создания пустого `.docx` до **how to add shadow** к объекту **rectangle shape word**, и наконец **insert shape word** содержимого с отшлифованным эффектом **add shape shadow**. К концу вы получите готовый фрагмент кода, работающий с последней версией Aspose.Words для .NET.

## Что понадобится

- **Aspose.Words for .NET** (v24.10 или новее) — библиотека, обеспечивающая всё ниже.  
- Среда разработки .NET (Visual Studio, Rider или `dotnet` CLI).  
- Базовые знания C# — если вы можете написать «Hello World», вы готовы.  

Дополнительные пакеты NuGet не требуются; всё находится внутри `Aspose.Words` и `System.Drawing`.

## Шаг 1: Создание пустого документа Word

Первое, что нужно сделать, — создать пустой объект `Document`. Считайте его чистым холстом, как при открытии нового файла Word вручную.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Почему это важно:*  
`Document` представляет весь файл Word. Начало с пустого документа дает полный контроль над каждым элементом, который вы добавите позже, от абзацев до фигур.

## Шаг 2: Определение прямоугольной фигуры (Rectangle Shape Word)

Теперь нам нужна фигура для работы. Прямоугольник — самая простая геометрия и хорошо подходит для баннеров, заполнителей или простых макетов UI.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Почему это важно:*  
Установка `Width` и `Height` позволяет контролировать визуальный размер фигуры. `ShapeType.Rectangle` указывает Aspose отрисовать классический прямоугольник — идеально для последующей демонстрации **add shape shadow**.

## Шаг 3: Применение тени к фигуре (How to Add Shadow)

Тени придают глубину, делая плоский прямоугольник похожим на физический объект. Aspose.Words предоставляет свойство `Shadow`, где можно настроить цвет, расстояние, размытие и прозрачность.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Почему это важно:*  
Каждое свойство влияет на визуальный эффект:

- **Enabled** — без этого остальные настройки игнорируются.  
- **Color** — выберите оттенок, соответствующий теме вашего документа.  
- **Distance** — большие значения отодвигают тень дальше.  
- **BlurRadius** — более высокие значения делают тень мягче.  
- **Transparency** — тонко настраивает непрозрачность для нежного эффекта.  

Не стесняйтесь экспериментировать; для драматического эффекта увеличьте `Distance` до `10` и установите `Transparency` в `0.5`.

## Шаг 4: Вставка фигуры в документ (Insert Shape Word)

Когда прямоугольник готов, нам нужно место для его размещения. Самое простое — первый абзац тела документа.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Почему это важно:*  
`FirstSection.Body.FirstParagraph` всегда присутствует в новом `Document`. Добавляя фигуру здесь, вы гарантируете, что она появится в верхней части файла — полезно для заголовков или баннеров.  

Если нужно вставить фигуру в другое место, можно найти конкретный `Paragraph` или `Run` и использовать `InsertAfter` или `InsertBefore`.

## Шаг 5: Сохранение файла Word

Последний шаг — сохранить документ из памяти на диск. Выберите папку, в которую у вас есть права записи, и дайте файлу осмысленное имя.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Почему это важно:*  
Вызов `Save` записывает полностью совместимый файл `.docx`. Откройте его в Microsoft Word, LibreOffice или любом просмотрщике, и вы увидите прямоугольник с мягкой серой тенью — именно то, что мы настроили.

## Полный рабочий пример

Ниже приведена полная программа, которую можно скопировать и вставить в консольное приложение. Она включает все директивы `using`, создание фигуры, настройку тени, вставку и сохранение.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ожидаемый результат:**  
Откройте `ShadowedRectangle.docx`, и вы увидите светло-серый прямоугольник, центрированный в верхней части страницы, с тонкой тенью, смещённой на 5 pt. Никакого дополнительного текста, только фигура — именно то, что генерирует код.

## Часто задаваемые вопросы и особые случаи

### Что если мне нужна другая фигура?

Замените `ShapeType.Rectangle` на любое другое значение перечисления `ShapeType` (`Ellipse`, `Triangle`, `Star` и т.д.). Свойства тени работают так же.

### Можно ли добавить несколько теней?

Aspose.Words поддерживает только одну тень на фигуру. Если нужны слоистые эффекты, создайте две перекрывающиеся фигуры с разными настройками тени.

### Как это работает на .NET Core?

Тот же API работает на .NET 6/7/8. Просто убедитесь, что вы подключили пакет **Aspose.Words.NETCore** (или стандартный пакет, который теперь кроссплатформенный).

### Поддерживается ли `System.Drawing` на Linux?

`System.Drawing.Common` начиная с .NET 6 доступен только на Windows. Для кроссплатформенных проектов используйте `Aspose.Drawing` (отдельный NuGet) или оставайтесь с цветами, определенными самим `Aspose.Words`.

### Что насчёт масштабирования DPI?

Размеры фигуры указаны в пунктах (1 pt = 1/72 дюйма). Если нужна точная пиксельная размерность для конкретного DPI, вычисляйте пункты как `pixels * 72 / dpi`.

## Профессиональные советы и подводные камни

- **Pro tip:** Установите `rectangleShape.WrapType = WrapType.Inline;`, если хотите, чтобы фигура текла вместе с текстом, а не плавала над ним.  
- **Watch out for:** Забвение включить тень (`Enabled = true`). Остальные настройки будут тихо игнорированы.  
- **Performance note:** Добавление большого количества фигур в быстром цикле может быть медленным. Сгруппируйте их в один `Section` и вызовите `document.UpdatePageLayout()` один раз в конце.  
- **Version check:** API тени был введён в Aspose.Words 20.2. Если вы используете более старую версию, обновитесь, чтобы не пропустить свойства.

## Заключение

Мы **created a blank Word** документ, построили **rectangle shape word**, изучили **how to add shadow**, и наконец **insert shape word** содержимое с отшлифованным эффектом **add shape shadow** — всё с помощью Aspose.Words для .NET.  

Этот фрагмент полностью исполняем, работает на Windows и кроссплатформенном .NET, и его можно расширять другими фигурами, цветами или даже анимированными GIF. Далее вы можете попробовать добавить текст внутрь прямоугольника, применить градиентные заливки или сгенерировать целый отчёт с несколькими стилизованными фигурами.  

Есть ещё идеи? Попробуйте заменить серую тень на синюю, увеличить размытие для мечтательного вида или объединить несколько фигур в пользовательский логотип. Возможности безграничны, и теперь у вас есть строительные блоки для их реализации.  

Счастливого кодинга, и пусть ваши документы всегда выглядят чётко (с правильным количеством тени)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}