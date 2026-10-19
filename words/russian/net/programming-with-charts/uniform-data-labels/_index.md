---
title: Установите одинаковые подписи данных в столбчатой диаграмме с помощью Aspose.Words for .NET
weight: 110
limit:
description: Научитесь создавать столбчатую диаграмму в Word и применять одинаковый размер шрифта и цвет подписи данных ко всем сериям с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Научитесь создавать столбчатую диаграмму в Word и применять одинаковый
    размер шрифта и цвет подписи данных ко всем сериям с помощью Aspose.Words for
    .NET.
  headline: Установите одинаковые подписи данных в столбчатой диаграмме с помощью
    Aspose.Words for .NET
  type: TechArticle
- description: Научитесь создавать столбчатую диаграмму в Word и применять одинаковый
    размер шрифта и цвет подписи данных ко всем сериям с помощью Aspose.Words for
    .NET.
  name: Установите одинаковые подписи данных в столбчатой диаграмме с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте новый пустой документ Word и объект DocumentBuilder для его редактирования.
    text: Создайте новый пустой документ Word и объект DocumentBuilder для его редактирования.
  - name: Вставьте в документ столбчатую диаграмму размером 500×300 и получите её
      объект Chart.
    text: Вставьте в документ столбчатую диаграмму размером 500×300 и получите её
      объект Chart.
  - name: Удалите стандартную образцовую серию, которую Aspose.Words добавляет в новую
      диаграмму.
    text: Удалите стандартную образцовую серию, которую Aspose.Words добавляет в новую
      диаграмму.
  - name: Определите метки категорий и добавьте в диаграмму две серии данных (Item
      Alpha и Item Beta) с их значениями.
    text: Определите метки категорий и добавьте в диаграмму две серии данных (Item
      Alpha и Item Beta) с их значениями.
  - name: Установите базовый размер шрифта и цвет, которые будут применяться ко всем
      подписям данных.
    text: Установите базовый размер шрифта и цвет, которые будут применяться ко всем
      подписям данных.
  - name: Включите подписи данных для каждой серии, отобразите числовое значение и
      примените заранее определённый размер шрифта и цвет.
    text: Включите подписи данных для каждой серии, отобразите числовое значение и
      примените заранее определённый размер шрифта и цвет.
  - name: Сохраните документ в файл формата .docx.
    text: Сохраните документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` создаёт диаграмму с образцовой серией по умолчанию; её
      очистка удаляет этот заполнитель, поэтому диаграмма отображает только добавленные
      вами серии (`Item Alpha` и `Item Beta`).'
    question: Зачем мне вызывать `chart.Series.Clear()` перед добавлением собственных
      серий?
  - answer: Замените `Color.White` на любое значение `System.Drawing.Color`, например
      `Color.Black` или `Color.FromArgb(255, 30, 144, 255)`; новый цвет применяется
      через `series.DataLabels.Font.Color` внутри цикла.
    question: Как изменить цвет подписи данных на что‑то отличное от белого?
  - answer: Подписи данных будут скрыты, поэтому применённые настройки шрифта станут
      невидимыми; необходимо оставить `HasDataLabels` установленным в `true`, чтобы
      подписи (и их оформление) отображались.
    question: Что произойдёт, если я установлю `series.HasDataLabels = false` после
      настройки размера шрифта и цвета?
  - answer: Да — у каждого `ChartSeries` есть собственный объект `DataLabels`, поэтому
      любые серии, добавленные после первоначального цикла, также должны иметь установленные
      `HasDataLabels`, `ShowValue` и свойства шрифта, либо путем повторного прохода
      цикла, либо вынесения оформления в вспомогательный метод.
    question: Нужно ли снова проходить цикл по сериям, если я добавлю ещё одну серию
      позже в коде?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Применить одинаковые подписи данных к диаграмме Word
og_description: Быстро задайте одинаковый размер шрифта и цвет для всех подписей диаграммы с помощью Aspose.Words for .NET.
og_image_alt: Руководство, показывающее документ Word со столбчатой диаграммой, где все подписи данных имеют одинаковый размер шрифта и цвет, созданный с помощью Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Установите одинаковые подписи данных в столбчатой диаграмме с помощью Aspose.Words
В этом руководстве показано, как создать документ Word, вставить столбчатую диаграмму и добавить пользовательские серии данных с помощью Aspose.Words for .NET. Затем демонстрируется определение размера шрифта и цвета подписи данных по умолчанию, чтобы каждая серия на диаграмме отображала одинаковые подписи. Применяя один стиль, вы обеспечиваете единообразный визуальный вид всей диаграммы.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Зачем мне вызывать `chart.Series.Clear()` перед добавлением собственных серий?**  
A: `InsertChart` создаёт диаграмму с образцовой серией по умолчанию; её очистка удаляет этот заполнитель, поэтому диаграмма отображает только добавленные вами серии (`Item Alpha` и `Item Beta`).

**Q: Как изменить цвет подписи данных на что‑то отличное от белого?**  
A: Замените `Color.White` на любое значение `System.Drawing.Color`, например `Color.Black` или `Color.FromArgb(255, 30, 144, 255)`; новый цвет применяется через `series.DataLabels.Font.Color` внутри цикла.

**Q: Что произойдёт, если я установлю `series.HasDataLabels = false` после настройки размера шрифта и цвета?**  
A: Подписи данных будут скрыты, поэтому применённые настройки шрифта станут невидимыми; необходимо оставить `HasDataLabels` установленным в `true`, чтобы подписи (и их оформление) отображались.

**Q: Нужно ли снова проходить цикл по сериям, если я добавлю ещё одну серию позже в коде?**  
A: Да — у каждого `ChartSeries` есть собственный объект `DataLabels`, поэтому любые серии, добавленные после первоначального цикла, также должны иметь установленные `HasDataLabels`, `ShowValue` и свойства шрифта, либо путем повторного прохода цикла, либо вынесения оформления в вспомогательный метод.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}