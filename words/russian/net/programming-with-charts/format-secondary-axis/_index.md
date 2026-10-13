---
title: Форматирование вторичной оси Y как валюты в диаграмме Word с использованием Aspose.Words for .NET
weight: 710
limit:
description: Научитесь добавлять и форматировать вторичную ось Y как валюту в линейной диаграмме Word с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Научитесь добавлять и форматировать вторичную ось Y как валюту в линейной
    диаграмме Word с помощью Aspose.Words for .NET.
  headline: Форматирование вторичной оси Y как валюты в диаграмме Word с использованием
    Aspose.Words for .NET
  type: TechArticle
- description: Научитесь добавлять и форматировать вторичную ось Y как валюту в линейной
    диаграмме Word с помощью Aspose.Words for .NET.
  name: Форматирование вторичной оси Y как валюты в диаграмме Word с использованием
    Aspose.Words for .NET
  steps:
  - name: Создайте новый пустой документ Word и объект DocumentBuilder для его редактирования.
    text: Создайте новый пустой документ Word и объект DocumentBuilder для его редактирования.
  - name: Вставьте в документ линейную диаграмму размером 450×250 пунктов и получите
      её объект Chart.
    text: Вставьте в документ линейную диаграмму размером 450×250 пунктов и получите
      её объект Chart.
  - name: Удалите серию‑заполнитель по умолчанию, которую Aspose добавляет в новую
      диаграмму.
    text: Удалите серию‑заполнитель по умолчанию, которую Aspose добавляет в новую
      диаграмму.
  - name: Определите метки кварталов и добавьте основную серию данных с примерными
      значениями в диаграмму.
    text: Определите метки кварталов и добавьте основную серию данных с примерными
      значениями в диаграмму.
  - name: Создайте вторичную группу серий типа Line и назначьте её группе вторичной
      оси.
    text: Создайте вторичную группу серий типа Line и назначьте её группе вторичной
      оси.
  - name: Скройте вторичную ось X, чтобы была видна только вторичная ось Y.
    text: Скройте вторичную ось X, чтобы была видна только вторичная ось Y.
  - name: Отобразите заголовок вторичной оси Y и задайте его текст как "Sales (USD)".
    text: Отобразите заголовок вторичной оси Y и задайте его текст как "Sales (USD)".
  - name: Установите числовой формат вторичной оси Y в валютный шаблон с двумя знаками
      после запятой и отключите привязку к форматированию источника.
    text: Установите числовой формат вторичной оси Y в валютный шаблон с двумя знаками
      после запятой и отключите привязку к форматированию источника.
  - name: Добавьте вспомогательную серию во вторичную группу, предоставив данные,
      которые будут отображаться по вторичной оси Y.
    text: Добавьте вспомогательную серию во вторичную группу, предоставив данные,
      которые будут отображаться по вторичной оси Y.
  - name: Сохраните готовый документ в файл с именем ProfitChart.docx в текущем каталоге.
    text: Сохраните готовый документ в файл с именем ProfitChart.docx в текущем каталоге.
  type: HowTo
- questions:
  - answer: Диаграмма сохранит серию‑заполнитель по умолчанию, которую вставляет Aspose.Words,
      поэтому ваша пользовательская "Main Series" появится вместе с нежелательными
      точками данных.
    question: Что произойдёт, если я опущу вызов `lineChart.Series.Clear()`?
  - answer: Установите `secondarySeriesGroup.AxisX.Hidden = false;` (или просто удалите
      строку, которая задаёт `true`).
    question: Как отобразить вторичную ось X вместо её скрытия?
  - answer: Да — измените строку формата, например `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";` для евро или настройте шаблон под вашу локаль.
    question: Можно ли использовать другой символ валюты или формат для вторичной
      оси Y?
  - answer: Когда `IsLinkedToSource` равно true, ось наследует числовой формат из
      базового источника данных, переопределяя любой пользовательский `FormatCode`;
      установка в false заставляет диаграмму использовать указанный вами формат.
    question: Зачем нужно устанавливать `IsLinkedToSource = false` при применении
      пользовательского числового формата?
  - answer: Да, назначьте `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (или `Right` для значения по умолчанию), чтобы управлять стороной, на которой
      ось рисуется.
    question: Можно ли переместить вторичную ось Y в левую часть диаграммы?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Форматировать вторичную ось диаграммы как валюту
og_description: Научитесь добавлять вторичную ось Y в линейную диаграмму Word и оформлять её как валюту с двумя знаками после запятой.
og_image_alt: Скриншот, показывающий линейную диаграмму Word с вторичной осью Y, отформатированной как валюта, с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Форматирование вторичной оси Y как валюты в диаграмме Word с использованием Aspose.Words
В этом руководстве вы увидите, как создать документ Word, вставить линейную диаграмму, добавить вторичную ось Y, отформатировать эту ось как валюту с двумя знаками после запятой и привязать к ней вторичную серию данных, используя Aspose.Words for .NET. Форматирование вторичной оси как валюты позволяет чётко представить финансовые данные рядом с основной серией. Следуйте пошаговому коду, чтобы увидеть диаграмму, отрисованную непосредственно в сгенерированном документе.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Что произойдёт, если я опущу вызов `lineChart.Series.Clear()`?**  
A: Диаграмма сохранит серию‑заполнитель по умолчанию, которую вставляет Aspose.Words, поэтому ваша пользовательская "Main Series" появится вместе с нежелательными точками данных.

**Q: Как отобразить вторичную ось X вместо её скрытия?**  
A: Установите `secondarySeriesGroup.AxisX.Hidden = false;` (или просто удалите строку, которая задаёт `true`).

**Q: Можно ли использовать другой символ валюты или формат для вторичной оси Y?**  
A: Да — измените строку формата, например `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";` для евро или настройте шаблон под вашу локаль.

**Q: Зачем нужно устанавливать `IsLinkedToSource = false` при применении пользовательского числового формата?**  
A: Когда `IsLinkedToSource` равно true, ось наследует числовой формат из базового источника данных, переопределяя любой пользовательский `FormatCode`; установка в false заставляет диаграмму использовать указанный вами формат.

**Q: Можно ли переместить вторичную ось Y в левую часть диаграммы?**  
A: Да, назначьте `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (или `Right` для значения по умолчанию), чтобы управлять стороной, на которой ось рисуется.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}