---
title: Удаление серии диаграммы из Word Document с помощью Aspose.Words for .NET
weight: 510
limit:
description: Узнайте, как удалить определённую серию данных из столбчатой диаграммы в Word документе с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Узнайте, как удалить определённую серию данных из столбчатой диаграммы
    в Word документе с помощью Aspose.Words for .NET.
  headline: Удаление серии диаграммы из Word Document с помощью Aspose.Words for .NET
  type: TechArticle
- description: Узнайте, как удалить определённую серию данных из столбчатой диаграммы
    в Word документе с помощью Aspose.Words for .NET.
  name: Удаление серии диаграммы из Word Document с помощью Aspose.Words for .NET
  steps:
  - name: Создайте новый Word Document и DocumentBuilder, привязанный к нему.
    text: Создайте новый Word Document и DocumentBuilder, привязанный к нему.
  - name: Вставьте столбчатую диаграмму размером 432×252 пункта и получите объект
      Chart для дальнейшего изменения.
    text: Вставьте столбчатую диаграмму размером 432×252 пункта и получите объект
      Chart для дальнейшего изменения.
  - name: Определите нулевой индекс серии, которую следует удалить (вторая серия).
    text: Определите нулевой индекс серии, которую следует удалить (вторая серия).
  - name: Если индекс действителен, вызовите RemoveAt у коллекции Series диаграммы,
      чтобы удалить эту серию.
    text: Если индекс действителен, вызовите RemoveAt у коллекции Series диаграммы,
      чтобы удалить эту серию.
  - name: Сохраните обновлённый документ в файл формата .docx.
    text: Сохраните обновлённый документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: Проверка `if` (`targetSeriesIdx < columnChart.Series.Count`) не пройдёт,
      поэтому `RemoveAt` никогда не будет вызван, и диаграмма останется без изменений.
    question: Что произойдёт, если я передам индекс, равный количеству серий в диаграмме?
  - answer: Да, после `columnChart.Series.RemoveAt` легенда пересоздаётся, отражая
      оставшиеся серии, поэтому удалённый элемент исчезает из легенды.
    question: Обновляется ли автоматически легенда диаграммы при удалении серии?
  - answer: Код работает для любого типа диаграммы, поддерживающего коллекцию `Series`;
      просто замените `ChartType.Column` на нужный тип при вставке диаграммы.
    question: Можно ли использовать тот же код для удаления серии из линейной или
      круговой диаграммы?
  - answer: Диаграмма без серий всё ещё является корректным `Shape` и будет сохранена,
      но в получившемся документе она будет выглядеть пустой.
    question: Если я удалю единственную серию в диаграмме, будет ли диаграмма всё
      равно корректно сохранена?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Удалить серию диаграммы в Word Document
og_description: Пошаговое руководство по удалению серии данных из диаграммы Word с использованием Aspose.Words for .NET.
og_image_alt: Руководство, показывающее, как удалить определённую серию данных из столбчатой диаграммы в Word документе с помощью Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Удаление серии диаграммы из Word Document с помощью Aspose.Words
В этом учебнике показано, как создать Word документ, добавить столбчатую диаграмму с помощью DocumentBuilder и затем удалить определённую серию данных из этой диаграммы, используя метод ChartSeriesCollection.RemoveAt. В результате у вас будет сохранённый документ без нежелательной серии, что даёт точный контроль над содержимым диаграммы непосредственно из кода .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Что произойдёт, если я передам индекс, равный количеству серий в диаграмме?**  
A: Проверка `if` (`targetSeriesIdx < columnChart.Series.Count`) не пройдёт, поэтому `RemoveAt` никогда не будет вызван, и диаграмма останется без изменений.

**Q: Обновляется ли автоматически легенда диаграммы при удалении серии?**  
A: Да, после `columnChart.Series.RemoveAt` легенда пересоздаётся, отражая оставшиеся серии, поэтому удалённый элемент исчезает из легенды.

**Q: Можно ли использовать тот же код для удаления серии из линейной или круговой диаграммы?**  
A: Код работает для любого типа диаграммы, поддерживающего коллекцию `Series`; просто замените `ChartType.Column` на нужный тип при вставке диаграммы.

**Q: Если я удалю единственную серию в диаграмме, будет ли диаграмма всё равно корректно сохранена?**  
A: Диаграмма без серий всё ещё является корректным `Shape` и будет сохранена, но в получившемся документе она будет выглядеть пустой.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}