---
category: general
date: 2026-04-10
description: как установить тень для фигуры в C# – узнайте, как применить падающую
  тень, изменить прозрачность, настроить размытие и добавить тень фигуре с помощью
  Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: ru
og_description: как установить тень для формы в C# – этот учебник показывает, как
  применить падающую тень, изменить прозрачность, настроить размытие и добавить тень
  к форме с понятными примерами кода.
og_title: как установить тень для фигуры в C# – полное руководство
tags:
- Aspose.Words
- C#
- Document Automation
title: Как добавить тень к фигуре в C# – пошаговое руководство
url: /ru/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# как установить тень на форму в C# – Полное руководство

Когда‑то задавались вопросом **как установить тень** на форму при программном построении документа Word? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда нужна тонкая падающая тень для текстового поля, логотипа или выноски, а документация API выглядит скудно.  

В этом руководстве мы пройдем весь процесс: от загрузки `.docx`, получения первой `Shape`, до применения падающей тени, настройки её прозрачности, регулировки радиуса размытия и окончательного позиционирования. К концу вы получите переиспользуемый фрагмент кода, работающий с Aspose.Words .NET 2023 и новее, и поймёте *почему* важен каждый параметр.

## Что понадобится

- **Aspose.Words for .NET** (NuGet‑пакет `Aspose.Words`) – библиотека, предоставляющая классы `Document`, `Shape` и `ShadowFormat`.  
- **.NET 6+** (или .NET Framework 4.7.2) – любой современный рантайм подойдёт.  
- Простой файл Word (`input.docx`), уже содержащий хотя бы одну форму, например текстовое поле.  
- Visual Studio, VS Code или ваша любимая IDE.

И всё. Никаких сторонних инструментов, без COM‑interop, только чистый C#.

![пример установки тени](image-placeholder.png){:alt="как установить тень на форму в документе Word"}

## Как установить тень – Обзор

Главная идея **как установить тень** состоит в том, чтобы управлять объектом `ShadowFormat`, который находится у `Shape`. Представьте `ShadowFormat` как мини‑«таблицу стилей» для самой тени: она указывает рендереру, видна ли тень, какого она цвета, насколько прозрачна, насколько размыта и где располагается относительно формы.  

Ниже приведена *полная* исполняемая программа. Скопируйте‑вставьте её в консольное приложение, нажмите **F5** и посмотрите, как тень появится в сохранённом `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Почему важны эти настройки

- **Visible** – Если этот флаг выключен, все остальные свойства игнорируются.  
- **Color** – Темно‑серый имитирует типичную UI‑тень; можно заменить любой `Color`.  
- **Transparency** – 0.3 даёт *мягкий* вид, сохраняя читаемость формы.  
- **Size** – Управляет размытием; значение 6 обычно достаточно для профессионального ощущения.  
- **Distance & Angle** – Вместе определяют *смещение*; 2 pt под 45° дают лёгкую диагональную тень.

Это суть **как установить тень**. Далее мы разберём каждую часть, чтобы вы могли **применить падающую тень**, **изменить прозрачность**, **регулировать размытие** и **добавить тень к форме** по отдельности.

---

## Применить падающую тень к форме

Когда люди спрашивают «как **применить падающую тень** в C#?», им часто нужен лишь переключатель видимости и цвет. Ниже фрагмент, изолирующий эти две строки:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Если вы нацелены на более старые версии Word (2003‑2007), используйте стандартные цвета. Некоторые экзотические ARGB‑значения могут быть проигнорированы устаревшим рендерером.

---

## Как изменить прозрачность тени

Прозрачность задаётся **float от 0 до 1**. Значение **0** означает полностью непрозрачную тень; **1** делает её невидимой. Большинство дизайнеров выбирают диапазон **0.2‑0.4** для естественного вида.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Пограничные случаи

- **Отрицательные значения** – Aspose.Words ограничит их до 0, но лучше проверять ввод.  
- **Значения > 1** – Ограничиваются до 1, фактически скрывая тень.  

Если нужно позволить пользователям выбирать процент, сначала преобразуйте его:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Как регулировать размытие (Size) тени

Свойство **Size** управляет радиусом размытия. Большие числа дают более мягкую, более диффузную тень. Измеряется в пунктах (pt), а не в пикселях.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Когда использовать небольшое или большое размытие

- **Небольшое размытие (2‑4 pt)** – Хорошо для UI‑выноски, где нужен чёткий край.  
- **Большое размытие (8‑12 pt)** – Подходит для печатных отчётов или когда форма удалена от фона.

---

## Добавить тень к форме – Позиционирование и направление

Последний элемент **add shape shadow** – это смещение. Два свойства работают совместно:

| Свойство   | Значение |
|------------|----------|
| **Distance** | Как далеко тень находится от формы (в пунктах). |
| **Angle**    | Направление смещения (0° = вправо, 90° = вниз, 180° = влево, 270° = вверх). |

Пример, создающий лёгкую тень снизу‑справа:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Можно экспериментировать с углами, имитируя свет из разных источников. Частый приём – позволить пользователю выбрать «источник света» из выпадающего списка и сопоставить его с углом.

---

## Полный рабочий пример (Все шаги вместе)

Ниже тот же код, что и ранее, но с **дополнительными комментариями**, делающими логику кристально ясной. Скопируйте его в `Program.cs` и запустите; в выходном файле будет текстовое поле с идеально настроенной тенью.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Ожидаемый результат:** Откройте `output.docx`. Первое текстовое поле покажет темно‑серую тень с 30 % прозрачностью, слегка размытая (size = 6) и смещённую на 2 pt под углом 45°. Эффект тонкий, но заметный — именно то, к чему стремятся большинство UI‑дизайнеров.

---

## Часто задаваемые вопросы и подводные камни

- **«Работает ли это с изображениями?»**  
  Да. Любая `Shape` — будь то текстовое поле, картинка или автофигура — имеет `ShadowFormat`. Просто замените логику получения формы на нужный индекс или имя.

- **«Что делать, если в документе несколько форм?»**  
  Пройдитесь циклом по `doc.GetChildNodes(NodeType.Shape, true)` и примените те же настройки к каждой. Можно также фильтровать по `shape.Name` или `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}