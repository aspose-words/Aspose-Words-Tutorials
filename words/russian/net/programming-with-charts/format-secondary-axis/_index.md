---
title: Форматирование вторичной оси X и установка единиц отображения в тысячи в линейных диаграммах Word с использованием Aspose.Words for .NET
weight: 710
limit:
description: Создайте линейную диаграмму Word, добавьте вторичную ось X, установите её единицу отображения в тысячи и примените пользовательский числовой формат с помощью Aspose.Words for .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Создайте линейную диаграмму Word, добавьте вторичную ось X, установите
    её единицу отображения в тысячи и примените пользовательский числовой формат с
    помощью Aspose.Words for .NET.
  headline: Форматирование вторичной оси X и установка единиц отображения в тысячи
    в линейных диаграммах Word с использованием Aspose.Words for .NET
  type: TechArticle
- description: Создайте линейную диаграмму Word, добавьте вторичную ось X, установите
    её единицу отображения в тысячи и примените пользовательский числовой формат с
    помощью Aspose.Words for .NET.
  name: Форматирование вторичной оси X и установка единиц отображения в тысячи в линейных
    диаграммах Word с использованием Aspose.Words for .NET
  steps:
  - name: Создайте новый Document и DocumentBuilder, чтобы начать построение файла
      Word.
    text: Создайте новый Document и DocumentBuilder, чтобы начать построение файла
      Word.
  - name: Вставьте линейную диаграмму размером 500×300 в документ и получите объект
      Chart.
    text: Вставьте линейную диаграмму размером 500×300 в документ и получите объект
      Chart.
  - name: Удалите стандартную демонстрационную серию, которую Aspose.Words добавляет
      автоматически.
    text: Удалите стандартную демонстрационную серию, которую Aspose.Words добавляет
      автоматически.
  - name: Определите массив меток категорий, которые будут использоваться для оси
      X.
    text: Определите массив меток категорий, которые будут использоваться для оси
      X.
  - name: Добавьте основную серию данных с именем "Main Data", используя метки и значения.
    text: Добавьте основную серию данных с именем "Main Data", используя метки и значения.
  - name: Создайте вторичную группу серий типа Line и назначьте её вторичной группе
      осей.
    text: Создайте вторичную группу серий типа Line и назначьте её вторичной группе
      осей.
  - name: Установите единицу отображения вторичной оси X в тысячи, чтобы значения
      отображались в K.
    text: Установите единицу отображения вторичной оси X в тысячи, чтобы значения
      отображались в K.
  - name: Примените пользовательский числовой формат "#,##0.0" к меткам делений вторичной
      оси X.
    text: Примените пользовательский числовой формат "#,##0.0" к меткам делений вторичной
      оси X.
  - name: При необходимости добавьте вспомогательную серию данных во вторичную группу.
    text: При необходимости добавьте вспомогательную серию данных во вторичную группу.
  - name: Сохраните документ в файл формата .docx.
    text: Сохраните документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: Нет — настройки `AxisX` относятся к `ChartSeriesGroup`, поэтому вы можете
      установить `secondaryGroup.AxisX.DisplayUnit.Unit` и `secondaryGroup.AxisX.NumberFormat.FormatCode`
      до или после добавления серий; конфигурация будет применена к оси группы в любом
      случае.
    question: Нужно ли добавлять вторичную серию перед установкой единицы отображения
      и числового формата на вторичной оси X?
  - answer: Да — присвойте любое значение `AxisBuiltInUnit`, например `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;`, чтобы отображать значения оси в миллионах вместо
      тысяч.
    question: Могу ли я использовать другую встроенную единицу, например миллионы,
      для вторичной оси X?
  - answer: Нет — код формата применяется только к оси, которую вы изменяете (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      поэтому основная ось X сохраняет своё форматирование по умолчанию.
    question: Повлияет ли пользовательский формат "#,##0.0" на метки основной оси
      X?
  - answer: Диаграмма будет содержать стандартную демонстрационную серию вместе с
      добавленными вами, что может привести к лишним линиям и несоответствующим категориям;
      очистка коллекции гарантирует, что отображаются только ваши данные.
    question: Что произойдёт, если я забуду очистить демонстрационную серию с помощью
      `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Форматировать вторичную ось X и установить единицы в тысячи
og_description: Добавьте вторичную ось X к линейной диаграмме Word и отформатируйте её метки в тысячах с помощью пользовательского шаблона.
og_image_alt: Руководство, показывающее, как добавить вторичную ось X к линейной диаграмме Word и отформатировать её метки для отображения единиц в тысячах с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Форматирование вторичной оси X и установка единиц отображения в тысячи в линейных диаграммах Word с использованием Aspose.Words
В этом учебном материале пошагово показано, как создать документ Word, содержащий линейную диаграмму, добавить вторичную ось X и настроить её отображение значений в тысячах. Вы также узнаете, как применить пользовательский числовой формат к меткам вторичной оси, получив точный контроль над представлением данных. Следуйте инструкциям, чтобы повысить читаемость многосевых диаграмм в ваших отчётах Word.

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

**Q: Нужно ли добавлять вторичную серию перед установкой единицы отображения и числового формата на вторичной оси X?**  
A: Нет — настройки `AxisX` относятся к `ChartSeriesGroup`, поэтому вы можете установить `secondaryGroup.AxisX.DisplayUnit.Unit` и `secondaryGroup.AxisX.NumberFormat.FormatCode` до или после добавления серий; конфигурация будет применена к оси группы в любом случае.

**Q: Могу ли я использовать другую встроенную единицу, например миллионы, для вторичной оси X?**  
A: Да — присвойте любое значение `AxisBuiltInUnit`, например `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;`, чтобы отображать значения оси в миллионах вместо тысяч.

**Q: Повлияет ли пользовательский формат "#,##0.0" на метки основной оси X?**  
A: Нет — код формата применяется только к оси, которую вы изменяете (`secondaryGroup.AxisX.NumberFormat.FormatCode`), поэтому основная ось X сохраняет своё форматирование по умолчанию.

**Q: Что произойдёт, если я забуду очистить демонстрационную серию с помощью `lineChart.Series.Clear();`?**  
A: Диаграмма будет содержать стандартную демонстрационную серию вместе с добавленными вами, что может привести к лишним линиям и несоответствующим категориям; очистка коллекции гарантирует, что отображаются только ваши данные.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}