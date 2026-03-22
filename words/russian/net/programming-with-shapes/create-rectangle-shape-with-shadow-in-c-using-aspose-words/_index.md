---
category: general
date: 2026-03-22
description: Создайте прямоугольную форму в C# и добавьте к ней тень с помощью Aspose.Words.
  Узнайте, как добавить тень, как создать прямоугольник и как задать свойства тени.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: ru
og_description: Создайте прямоугольную форму в C# и добавьте к ней тень с помощью
  Aspose.Words. Пошаговое руководство, охватывающее, как добавить тень, как создать
  прямоугольник и как настроить тень.
og_title: Создайте прямоугольную форму с тенью в C# – Полное руководство
tags:
- Aspose.Words
- C#
- Document Automation
title: Создать прямоугольную форму с тенью в C# с использованием Aspose.Words
url: /ru/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры с тенью в C# с использованием Aspose.Words

Когда‑нибудь вам нужно было **create rectangle shape** в документе Word, но вы не знали, как добавить к нему нежную падающую тень? Вы не одиноки — многие разработчики сталкиваются с этой проблемой, когда впервые начинают работать с автоматизацией документов. В этом руководстве мы подробно покажем, как **add shadow to shape** с помощью Aspose.Words, а также ответим на вопросы «**how to add shadow**», «**how to create rectangle**» и «**how to set shadow**».

Мы начнём с чистого листа `Document`, нарисуем прямоугольник, включим его тень, настроим размытие, расстояние, угол и цвет, а затем сохраним файл. В конце у вас будет готовый к использованию `.docx`, в котором отображается серый прямоугольник, «плавающий» над страницей. Никаких загадок, просто прямой код, который можно скопировать и вставить в любой проект .NET.

## Требования

* **Aspose.Words for .NET** (последняя версия на март 2026). Вы можете получить её из NuGet с помощью `Install-Package Aspose.Words`.
* Среда разработки .NET — Visual Studio, Rider или даже VS Code с расширением C# — подойдет.
* Базовые знания C# — ничего сложного, просто умение создать консольное приложение или WinForms.

Вот и всё. Никаких дополнительных библиотек, никаких скрытых шагов. Готовы? Приступим.

## Шаг 1: Инициализация нового пустого документа

Чтобы **create rectangle shape**, нам сначала нужен контейнер — объект `Document`, представляющий файл Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

Класс `Document` — точка входа для всех возможностей Aspose.Words. Считайте его пустым холстом; без него вы не сможете добавить ни фигур, ни таблиц, ни текста.

## Шаг 2: Создание прямоугольника, который будет держать тень

Теперь мы покажем **how to create rectangle**, создав объект `Shape` типа `Rectangle`. Мы также задаём его размер в пунктах (1 пункт ≈ 1/72 дюйма).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Почему выбраны 200 × 100 пунктов? Это удобный размер для демонстрации — достаточно большой, чтобы чётко увидеть тень, но не настолько огромный, чтобы перегрузить страницу. При желании можете изменить эти значения под ваш макет.

## Шаг 3: Включение эффекта тени и настройка её внешнего вида

Это сердце руководства: **how to add shadow** и **how to set shadow** свойства. Aspose.Words предоставляет объект `Shadow` для каждой фигуры, позволяя включать эффект и настраивать визуальные параметры.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** смягчает края — более высокое значение делает тень более рассеянной.
* **Distance** отодвигает тень дальше от прямоугольника.
* **Angle** определяет, откуда, по‑видимому, исходит свет; 45° дают диагональный, естественный вид.
* **Color** позволяет выбрать любой `System.Drawing.Color`. Серый — безопасный вариант по умолчанию, но можно использовать смелый `Color.Black` или нежный `Color.LightGray`.

Подсказка: если установить `Enabled = false`, все остальные настройки тени игнорируются, поэтому всегда проверяйте этот флаг.

## Шаг 4: Вставка фигуры в тело документа

Когда прямоугольник готов и его тень настроена, нам нужно разместить его в документе. Самый простой способ — добавить его к первому абзацу первой секции.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Если ваш документ уже содержит текст, вы можете найти конкретный `Paragraph` или даже ячейку `Table` и вставить туда фигуру. Метод `AppendChild` универсален — он работает с любым типом `Node`.

## Шаг 5: Сохранение документа и проверка результата

Наконец, мы записываем файл на диск. Измените путь на любой удобный вам; папка должна существовать, иначе возникнет исключение.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Откройте полученный `ShadowedRectangle.docx` в Microsoft Word (или LibreOffice), и вы увидите серый прямоугольник с чёткой диагональной тенью, смещённой вниз‑вправо. Если тень выглядит слишком слабой, увеличьте `BlurRadius` или `Distance` и запустите код снова — эксперименты являются частью процесса.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Пример создания прямоугольной фигуры с тенью"}

### Ожидаемый результат

* Одностраничный документ Word.
* Серый прямоугольник размером 200 × 100 пунктов, расположенный в левом верхнем углу страницы.
* Тонкая серая тень, смещённая на 8 пикселей под углом 45°, размазана на 5 пикселей.

## Как добавить тень к фигуре — более глубокий разбор

Вы можете задаться вопросом: *«Могу ли я анимировать тень или менять её в зависимости от ввода пользователя?»* Хотя Aspose.Words не поддерживает анимацию, вы можете программно изменять свойства тени перед сохранением, эффективно создавая несколько вариантов одного документа с разным внешним видом. Например, перебирая коллекцию цветов:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Этот небольшой фрагмент демонстрирует **how to set shadow** динамически — отлично подходит для создания отчётов в разных темах.

## Как создать прямоугольник — альтернативные формы

Если нужен скруглённый прямоугольник, просто измените `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Или, для идеального квадрата, задайте `Width` равным `Height`. Те же свойства тени применимы, так что вы уже покрыты в вопросе **how to add shadow** для любой выбранной формы.

## Распространённые ошибки и их устранение

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Тень не отображается | `Shadow.Enabled` оставлен `false` | Установите `rectangleShape.Shadow.Enabled = true;` |
| Тень выглядит слишком резкой | `BlurRadius` установлен в 0 | Увеличьте `BlurRadius` минимум до 3 |
| При сохранении документ бросает `FileNotFoundException` | Папка назначения не существует | Создайте папку заранее или используйте корректный путь |
| Фигура невидима | Width/Height установлены в 0 | Убедитесь, что обе размеры > 0 |

## Итоги — чего мы достигли

* **Create rectangle shape** в новом документе Word с помощью Aspose.Words.  
* **Add shadow to shape** путем переключения флага `Shadow.Enabled` и настройки размытия, расстояния, угла и цвета.  
* Продемонстрировано **how to add shadow**, **how to create rectangle** и **how to set shadow** в чистом, переиспользуемом фрагменте кода.  
* Предоставлен полный, готовый к запуску пример, который можно вставить в любой проект C#.

## Что дальше?

Теперь, когда вы освоили основы, рассмотрите возможность изучения:

* **How to add shadow to images** — тот же API `Shadow` работает для `ShapeType.Image`.
* **Combining multiple shapes** — создавайте блок‑схемы или инфографику непосредственно в Word.
* **Exporting to PDF** — вызовите `document.Save("output.pdf")` после добавления теней для печатной версии.

Не стесняйтесь экспериментировать с разными цветами, углами или даже градиентными заливками. API достаточно гибок, чтобы вы могли создавать профессионально выглядящие документы, не открывая Word вручную.

Счастливого кодинга! Если возникнут проблемы, оставьте комментарий ниже или загляните на форумы Aspose.Words — сообщество быстро поможет.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}