---
category: general
date: 2026-07-19
description: Взрыв среза круговой диаграммы с помощью Aspose.Words для C#. Узнайте,
  как взорвать срез, настроить размер отверстия кольца и быстро изменить точки данных
  диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: ru
lastmod: 2026-07-19
og_description: Отделить срез круговой диаграммы с помощью Aspose.Words для C#. Это
  руководство показывает, как отделить срез, настроить размер отверстия кольца и эффективно
  изменить точки данных диаграммы.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Взрыв сектора круговой диаграммы в C# – учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Отделить часть круговой диаграммы в C# с Aspose.Words – Полное руководство
url: /ru/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Взрывной срез круговой диаграммы в C# с Aspose.Words – Полное руководство

Когда‑нибудь задумывались, как **взять срез круговой диаграммы** в документе Word с помощью C#? Вы не одиноки. Будь то подготовка презентации продаж или визуализация результатов опроса, взрывной срез привлекает внимание именно туда, куда вам нужно. В этом руководстве мы пройдем весь процесс — загрузка документа, получение диаграммы, взрыв первого среза, настройка отверстия кольца и даже изменение точек данных диаграммы.

Мы также коснёмся второстепенных вопросов, которые могут вас интересовать: **как взорвать срез круговой диаграммы**, **изменить размер отверстия кольца**, и **изменить точки данных диаграммы**. Без лишних слов, готовое решение, которое можно сразу скопировать и вставить.

---

## Что понадобится

Прежде чем начать, убедитесь, что у вас есть:

- **Aspose.Words for .NET** (последняя версия на 2026‑07‑19). Вы можете установить её через NuGet командой `Install-Package Aspose.Words`.
- Проект **.NET 6+** (или .NET Framework 4.7.2+, если вы всё ещё работаете со старой платформой).
- Файл Word (`Chart.docx`), уже содержащий круговую или кольцевую диаграмму. Если его нет, быстро создайте диаграмму в Word и сохраните её.

Это всё — никаких дополнительных библиотек, без COM‑interop, только чистый управляемый код.

---

## Взрывной срез круговой диаграммы – пошаговая реализация

Ниже задача разбита на небольшие шаги. Каждый раздел имеет заголовок, фрагмент кода и короткое объяснение *почему* мы делаем именно так.

### Шаг 1: Установить и подключить Aspose.Words

Сначала добавьте пакет Aspose.Words в ваш проект. В консоли диспетчера пакетов:

```powershell
Install-Package Aspose.Words
```

> **Совет:** Если вы используете встроенный UI NuGet в Visual Studio, найдите “Aspose.Words” и нажмите Install. Это гарантирует, что вы получите последние исправления и возможность работать с диаграммами сразу из коробки.

### Шаг 2: Загрузить документ Word, содержащий диаграмму

Нужен объект `Document`, указывающий на `.docx` с нужной диаграммой.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Почему это важно:** `Document` — точка входа для любой операции в Aspose.Words. Проверив наличие диаграмм заранее, мы избегаем ошибки null reference, когда будем пытаться взорвать срез.

### Шаг 3: Получить первый узел диаграммы

Большинство примеров предполагают одну диаграмму, поэтому мы возьмём первую. Если диаграмм несколько, скорректируйте индекс.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Примечание:** Приведение к типу `Chart` безопасно после проверки, что диаграмма существует. Этот объект даёт доступ к сериям, точкам данных и настройкам, специфичным для типа диаграммы.

### Шаг 4: Взорвать первый срез круговой диаграммы

Теперь главный момент — **как взорвать срез круговой диаграммы**. Установим свойство `Exploded` у первой точки данных.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Почему это работает:** `Exploded` указывает Word отодвинуть этот срез от центра, создавая классический эффект “взрывной круговой диаграммы”. Свойство булево, поэтому установка `true` делает всё.

### Шаг 5: Настроить размер отверстия кольца (если это кольцевая диаграмма)

Если ваша диаграмма — кольцевая, можно **изменить размер отверстия кольца**. Размер отверстия задаётся в процентах от радиуса диаграммы.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Что означает число:** Значение `30` значит, что внутренний круг займет 30 % от общего радиуса, оставляя более толстое внешнее кольцо.

### Шаг 6: Изменить точки данных диаграммы (по желанию)

Иногда требуется **изменить точки данных диаграммы** — например, обновились исходные цифры и нужно отразить их визуально.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Зачем это нужно:** Изменение значения точки данных автоматически пересчитывает процентные доли срезов, поддерживая диаграмму актуальной без ручного редактирования в Word.

### Шаг 7: Сохранить изменённый документ

Наконец, запишем изменения на диск. Можно перезаписать оригинал или создать новый файл — на ваш выбор.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Подсказка:** Используйте `SaveFormat.Docx`, если хотите явно указать формат, но `Save(string)` автоматически определяет его по расширению файла.

---

## Ожидаемый результат

После открытия `FormattedChart.docx` в Microsoft Word вы увидите:

- Первый срез круговой диаграммы **взорван** наружу.
- Если диаграмма кольцевая, центральное отверстие теперь занимает **30 %** радиуса.
- Любые изменённые точки данных отображают новые значения.

Ниже условное изображение того, как выглядит взрывной срез (картинка только для иллюстрации).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Alt text:* **взрывной срез круговой диаграммы**, показывающий отодвинутый сегмент в документе Word.

---

## Часто задаваемые вопросы и особые случаи

**Что если диаграмма не круговая и не кольцевая?**  
Код проверяет `ChartType` перед применением `Exploded` или `HoleSize`. Для столбчатых, линейных или площадных диаграмм этих свойств просто нет, поэтому логика безопасно их пропускает.

**Можно ли взорвать несколько срезов?**  
Конечно. Пройдитесь циклом по `chart.PieChartData.Series[0].DataPoints` и установите `Exploded = true` для любого индекса, который хотите.

**Нужно ли учитывать региональные форматы чисел?**  
Aspose.Words хранит числовые значения как `double`, независимо от локали, так что проблем с запятыми и точками не будет.

**А как насчёт диаграмм, встроенных в колонтитулы?**  
Используйте `doc.GetChildNodes(NodeType.Chart, true)`, чтобы получить все диаграммы, затем проверьте `ParentNode` каждого узла, чтобы понять, где он находится. Тот же процесс взрыва применяется.

---

## Заключение

Теперь у вас есть готовое, копируемое решение для **взрыва среза круговой диаграммы** с помощью Aspose.Words в C#. Мы прошли весь рабочий процесс — от загрузки документа, получения диаграммы, взрыва среза, **регулировки размера отверстия кольца**, до **изменения точек данных** и сохранения файла.

Экспериментируйте: попробуйте взорвать другой срез, измените размер отверстия до 45 %, или обновите сразу несколько точек данных. API Aspose.Words делает такие правки простыми, а изменения сразу видны при открытии файла Word.

---

### Что дальше?

- **Оформить взорванный срез** (изменить цвет заливки, границу или добавить подпись данных). Ищите “Aspose.Words chart formatting”.
- **Автоматизировать пакетную обработку** нескольких документов — пройдитесь по папке, взорвите срезы и сохраните новые версии.
- **Комбинировать с Aspose.Slides**, если нужен тот же график в презентации PowerPoint.

Есть вопросы по работе с диаграммами или хотите углубиться в другие типы диаграмм? Оставляйте комментарий ниже, и happy coding!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающий код с пошаговыми объяснениями, чтобы вы могли освоить дополнительные возможности API и исследовать альтернативные подходы в своих проектах.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}