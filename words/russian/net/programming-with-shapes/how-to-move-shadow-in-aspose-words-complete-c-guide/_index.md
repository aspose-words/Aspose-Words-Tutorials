---
category: general
date: 2026-05-01
description: Как переместить тень у фигуры в Aspose.Words с использованием C#. Узнайте,
  как добавить тень к фигуре, изменить размытие, установить прозрачность и повернуть
  тень за несколько минут.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: ru
og_description: Как переместить тень на фигуре в Aspose.Words с использованием C#.
  Этот учебник показывает, как добавить тень к фигуре, изменить размытие, установить
  прозрачность и повернуть тень.
og_title: Как переместить тень в Aspose.Words – Полное руководство по C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Как переместить тень в Aspose.Words – Полное руководство по C#
url: /ru/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как переместить тень в Aspose.Words – Полное руководство на C#

Когда‑нибудь задавались вопросом **как переместить тень** у фигуры в документе Word, не открывая Word вручную? В своей повседневной работе я часто нуждался в программном изменении тени фигуры — будь то для отшлифованного отчёта или динамического шаблона. Хорошая новость: с Aspose.Words это можно сделать в паре строк кода, а также вы узнаете, как **добавить тень к фигуре**, **изменить размытие**, **установить прозрачность** и **повернуть тень** за один проход.

В этом руководстве мы пройдём реальный сценарий: загрузим существующий DOCX, в котором уже есть фигура, настроим позицию тени, её мягкость, непрозрачность и направление, а затем сохраним результат. К концу вы получите переиспользуемый фрагмент, который можно вставить в любой .NET‑проект, и поймёте, зачем нужна каждая настройка.

## Предварительные требования – Что нужно перед началом

- **Aspose.Words for .NET** (версия 23.12 или новее). Установить можно через NuGet командой `Install-Package Aspose.Words`.
- Среда разработки .NET 6+ (Visual Studio, VS Code, Rider — что вам удобно).
- Входной Word‑файл (`input.docx`), уже содержащий хотя бы одну фигуру (прямоугольник, круг или изображение).
- Базовое знакомство с синтаксисом C# — ничего сложного.

Если чего‑то не хватает, сделайте паузу и установите библиотеку; дальше в руководстве предполагается, что пакет уже подключён.

## Шаг 1: Загрузка документа и получение целевой фигуры – **Как переместить тень** начинается здесь

Первым делом загружаем исходный документ и находим фигуру, которую будем менять. Aspose.Words рассматривает каждый объект (абзацы, таблицы, фигуры) как узел дерева, поэтому его можно запросить напрямую.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Почему это важно:** Загрузка документа один раз и повторное использование того же экземпляра `Document` экономит ресурсы. Вызов `GetChild` безопасен, так как возвращает `null`, если индекс выходит за пределы, позволяя корректно обрабатывать отсутствие фигур.

## Шаг 2: Регулировка радиуса размытия – Мастер‑класс **Как изменить размытие**

Мягкая тень выглядит профессионально, а резкий край — дешево. Свойство `BlurRadius` управляет мягкостью в пунктах (1 pt ≈ 1/72 дюйма). Увеличим его до 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Совет профи:** Значение размытия по умолчанию — 0,5 pt. Всё, что выше 5 pt, обычно заметно, но будьте осторожны: слишком большое значение может оторвать фигуру от страницы.

## Шаг 3: Установка прозрачности – Ответ на **Как установить прозрачность**

Прозрачность определяет, насколько «прозрачна» тень. Значение `0` — полностью непрозрачная; `1` — полностью невидимая. Для нежного эффекта используем `0.3` (30 % прозрачности).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Зачем это может понадобиться:** Если фигура тёмная, полностью непрозрачная тень может «заглушить» подлежащий текст. Регулировка прозрачности сохраняет читаемость документа, добавляя глубину.

## Шаг 4: Перемещение тени – Ядро **Как переместить тень**

Свойство `Distance` задаёт, насколько далеко тень смещена от фигуры, измеряется в пунктах. Большое расстояние отодвигает тень дальше, создавая более драматичный эффект.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **А если нужен крошечный сдвиг?** Установка `Distance` в `0` разместит тень непосредственно за фигурой, что удобно для эффекта тиснения.

## Шаг 5: Поворот источника света – Решаем **Как повернуть тень**

Тени не всегда падают строго вниз; они следуют углу источника света. Свойство `Angle` (в градусах) вращает тень вокруг фигуры. Повернём её на 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Быстрый эксперимент:** Попробуйте `90` для тени справа или `-30` для тени, наклонённой влево. Визуальное изменение будет мгновенным.

## Шаг 6: Сохранение документа – Видим результат **Добавить тень к фигуре**

После настройки тени запишем документ обратно на диск. Можно перезаписать оригинал или создать новый файл; в примере используется новый выходной файл.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Ожидаемый результат:** Откройте `output.docx`. Тень фигуры станет мягче, слегка смещённой, полупрозрачной и наклонённой на 45°. Сравнив её бок о бок с `input.docx`, разницу будет невозможно не заметить.

### Полный рабочий пример (готов к копированию)

Ниже представлен весь код в одном блоке. Вставьте его в новый консольный проект, замените `YOUR_DIRECTORY` реальным путём к папке и запустите.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Часто задаваемые вопросы и особые случаи

### Что делать, если в документе несколько фигур?

Можно пройтись по всем фигурам в цикле:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Можно ли добавить тень к фигуре, у которой её нет?

Конечно. Объект `ShadowFormat` всегда существует; нужно лишь включить его:

```csharp
shape.ShadowFormat.Enabled = true;
```

### Работает ли это с изображениями и SmartArt?

Да. Любой узел, наследующий `Shape` — включая картинки, диаграммы и SmartArt — имеет `ShadowFormat`. Те же свойства применимы.

### Как управлять цветом тени?

Используйте свойство `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Проблемы совместимости?

Aspose.Words 23.12+ поддерживает .NET 6, .NET Core 3.1 и .NET Framework 4.6.2+. Показанный API стабилен во всех этих версиях.

## Заключение

Мы только что разобрали, **как переместить тень** у фигуры с помощью Aspose.Words, а также продемонстрировали **добавление тени к фигуре**, **изменение размытия**, **установку прозрачности** и **поворот тени**. Полный, готовый к запуску пример позволяет за секунды настроить любую тень, придавая вашим документам отполированный, профессиональный вид без открытия Word.

Готовы к следующему шагу? Попробуйте комбинировать эти настройки тени с **условным форматированием** — например, применять более глубокую тень только к заголовкам или к диаграммам, превышающим определённый размер. Или исследуйте **градиентные заливки** самой фигуры, чтобы создать действительно бросающийся в глаза дизайн.

Если возникнут трудности, оставляйте комментарий ниже. Приятного кодинга, и пусть ваши тени всегда падают именно туда, куда вы хотите! 

![Диаграмма, показывающая эффект перемещения тени у фигуры – пример как переместить тень](https://example.com/images/shadow-demo.png "пример как переместить тень")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}