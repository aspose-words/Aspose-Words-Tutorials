---
title: Обновление данных серии диаграммы в документе Word с использованием Aspose.Words for .NET
weight: 610
limit:
description: Научитесь изменять точки данных серии диаграммы в документе Word и обновлять диаграмму с использованием Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Научитесь изменять точки данных серии диаграммы в документе Word и
    обновлять диаграмму с использованием Aspose.Words for .NET.
  headline: Обновление данных серии диаграммы в документе Word с использованием Aspose.Words
    for .NET
  type: TechArticle
- description: Научитесь изменять точки данных серии диаграммы в документе Word и
    обновлять диаграмму с использованием Aspose.Words for .NET.
  name: Обновление данных серии диаграммы в документе Word с использованием Aspose.Words
    for .NET
  steps:
  - name: Создайте новый Document, вставьте колонную диаграмму с помощью DocumentBuilder
      и сохраните его как исходный файл.
    text: Создайте новый Document, вставьте колонную диаграмму с помощью DocumentBuilder
      и сохраните его как исходный файл.
  - name: Откройте сохранённый файл и найдите форму диаграммы, чтобы получить существующий
      объект Chart.
    text: Откройте сохранённый файл и найдите форму диаграммы, чтобы получить существующий
      объект Chart.
  - name: Очистите значения первой серии и добавьте новые точки, затем скорректируйте
      вторую серию, удалив её первую точку и добавив новую.
    text: Очистите значения первой серии и добавьте новые точки, затем скорректируйте
      вторую серию, удалив её первую точку и добавив новую.
  - name: Сохраните изменённый документ в новый файл, содержащий обновлённую диаграмму.
    text: Сохраните изменённый документ в новый файл, содержащий обновлённую диаграмму.
  type: HowTo
- questions:
  - answer: Используйте `document.GetChildNodes(NodeType.Shape, true)`, чтобы получить
      все формы, затем отфильтруйте их с помощью `s.HasChart` и выберите первую (или
      нужную вам) — это предотвращает выбор несвязанных изображений или текстовых
      полей.
    question: Как надёжно найти форму диаграммы в документе, который может содержать
      другие формы?
  - answer: '`ClearValues()` удаляет существующие точки данных; без этого новые точки
      добавляются к старым, что может привести к дублированию категорий или неверным
      итоговым значениям.'
    question: Зачем нужно вызывать `ClearValues()` перед добавлением новых точек в
      серию?
  - answer: Используйте `FromString`, когда категории оси X диаграммы являются текстовыми
      (например, "Group A"), и `FromDouble`, когда ось ожидает числовые значения,
      такие как даты или измерения.
    question: Когда следует использовать `ChartXValue.FromString` вместо `ChartXValue.FromDouble`
      для значений оси X?
  - answer: Попытка обратиться к несуществующей серии вызывает `ArgumentOutOfRangeException`;
      всегда проверяйте `existingChart.Series.Count` перед обращением к конкретному
      индексу.
    question: Что произойдёт, если в диаграмме только одна серия, а я попытаюсь обратиться
      к `existingChart.Series[1]`?
  - answer: Сохранение `openedDoc` достаточно, потому что это экземпляр документа,
      содержащий изменённую диаграмму; оригинальный `document` использовался только
      для создания исходного файла.
    question: Нужно ли повторно сохранять оригинальный `document` после изменения
      диаграммы, или достаточно сохранить `openedDoc`?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Редактирование данных серии диаграммы в Word
og_description: Пошаговое руководство по изменению значений серии диаграммы в файле Word с Aspose.Words for .NET.
og_image_alt: Руководство, показывающее документ Word с колонной диаграммой до и после обновления данных её серии с использованием Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Обновление данных серии диаграммы в документе Word с использованием Aspose.Words
Этот учебник показывает, как создать документ Word, содержащий колонную диаграмму, затем открыть файл повторно, получить существующие серии диаграммы, изменить их точки данных и сохранить документ, чтобы диаграмма отображала новые значения. Следуйте пошаговому коду, чтобы увидеть, насколько просто программно корректировать данные диаграммы с помощью Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: Как надёжно найти форму диаграммы в документе, который может содержать другие формы?**  
A: Используйте `document.GetChildNodes(NodeType.Shape, true)`, чтобы получить все формы, затем отфильтруйте их с помощью `s.HasChart` и выберите первую (или нужную вам) — это предотвращает выбор несвязанных изображений или текстовых полей.

**Q: Зачем нужно вызывать `ClearValues()` перед добавлением новых точек в серию?**  
A: `ClearValues()` удаляет существующие точки данных; без этого новые точки добавляются к старым, что может привести к дублированию категорий или неверным итоговым значениям.

**Q: Когда следует использовать `ChartXValue.FromString` вместо `ChartXValue.FromDouble` для значений оси X?**  
A: Используйте `FromString`, когда категории оси X диаграммы являются текстовыми (например, "Group A"), и `FromDouble`, когда ось ожидает числовые значения, такие как даты или измерения.

**Q: Что произойдёт, если в диаграмме только одна серия, а я попытаюсь обратиться к `existingChart.Series[1]`?**  
A: Попытка обратиться к несуществующей серии вызывает `ArgumentOutOfRangeException`; всегда проверяйте `existingChart.Series.Count` перед обращением к конкретному индексу.

**Q: Нужно ли повторно сохранять оригинальный `document` после изменения диаграммы, или достаточно сохранить `openedDoc`?**  
A: Сохранение `openedDoc` достаточно, потому что это экземпляр документа, содержащий изменённую диаграмму; оригинальный `document` использовался только для создания исходного файла.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}