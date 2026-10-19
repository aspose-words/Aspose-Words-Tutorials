---
title: Добавьте именованную серию данных в гистограмму в Word с помощью Aspose.Words for .NET
weight: 610
limit:
description: Узнайте, как встроить гистограмму в Word‑документ и добавить именованную серию данных с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Узнайте, как встроить гистограмму в Word‑документ и добавить именованную
    серию данных с помощью Aspose.Words for .NET.
  headline: Добавьте именованную серию данных в гистограмму в Word с помощью Aspose.Words
    for .NET
  type: TechArticle
- description: Узнайте, как встроить гистограмму в Word‑документ и добавить именованную
    серию данных с помощью Aspose.Words for .NET.
  name: Добавьте именованную серию данных в гистограмму в Word с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте новый пустой Word‑документ и DocumentBuilder для его редактирования.
    text: Создайте новый пустой Word‑документ и DocumentBuilder для его редактирования.
  - name: Вставьте в документ форму гистограммы размером 500×300 и получите её объект
      Chart.
    text: Вставьте в документ форму гистограммы размером 500×300 и получите её объект
      Chart.
  - name: Удалите серию‑заполнитель по умолчанию, которую Aspose.Words добавляет к
      новым диаграммам.
    text: Удалите серию‑заполнитель по умолчанию, которую Aspose.Words добавляет к
      новым диаграммам.
  - name: Добавьте именованную серию под названием "Demo Series" с указанными точками
      данных в гистограмму.
    text: Добавьте именованную серию под названием "Demo Series" с указанными точками
      данных в гистограмму.
  - name: Сохраните документ в файл .docx, содержащий помеченную серию диаграммы.
    text: Сохраните документ в файл .docx, содержащий помеченную серию диаграммы.
  type: HowTo
- questions:
  - answer: '`InsertChart` создаёт серию‑заполнитель по умолчанию; её очистка удаляет
      эту пустую серию, поэтому диаграмма отображает только данные, добавленные с
      помощью `Series.Add`.'
    question: Зачем мне вызывать `histogramChart.Series.Clear()` перед добавлением
      собственной серии?
  - answer: Да, вызывайте `histogramChart.Series.Add` несколько раз, каждый раз передавая
      отдельное имя и массив `double[]` значений; каждая серия будет перечислена в
      легенде диаграммы с указанным именем.
    question: Могу ли я добавить более одной серии, используя одну и ту же перегрузку,
      и будет ли каждая отображаться со своей меткой?
  - answer: Перегрузка ожидает `double[]`; если у вас есть `int[]` или другие числовые
      массивы, приведите их или преобразуйте в `double[]` перед передачей.
    question: Является ли аргумент `double[]` единственным типом, принимаемым для
      точек данных?
  - answer: Строка, переданная в качестве первого аргумента (например, "Demo Series"),
      используется как заголовок серии и по умолчанию отображается в легенде диаграммы.
    question: Появится ли указанное мной имя серии автоматически на диаграмме?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Добавьте именованную серию в гистограмму Word
og_description: Быстро подпишите серию диаграммы в Word с помощью Aspose.Words и сразу увидьте её отрисовку.
og_image_alt: Скриншот, показывающий Word‑документ с гистограммой, включающей помеченную серию данных, созданную с помощью Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавьте именованную серию данных в гистограмму в Word с помощью Aspose.Words
В этом учебнике показано, как создать Word‑документ с помощью Aspose.Words for .NET, вставить гистограмму и добавить помеченную серию данных, используя перегрузку ChartSeriesCollection.Add, принимающую имя и значения. Присваивая серии имя, вы можете чётко идентифицировать каждый набор данных на диаграмме, делая визуальный вывод более понятным и удобным для интерпретации.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: Зачем мне вызывать `histogramChart.Series.Clear()` перед добавлением собственной серии?**  
A: `InsertChart` создаёт серию‑заполнитель по умолчанию; её очистка удаляет эту пустую серию, поэтому диаграмма отображает только данные, добавленные с помощью `Series.Add`.

**Q: Могу ли я добавить более одной серии, используя одну и ту же перегрузку, и будет ли каждая отображаться со своей меткой?**  
A: Да, вызывайте `histogramChart.Series.Add` несколько раз, каждый раз передавая отдельное имя и массив `double[]` значений; каждая серия будет перечислена в легенде диаграммы с указанным именем.

**Q: Является ли аргумент `double[]` единственным типом, принимаемым для точек данных?**  
A: Перегрузка ожидает `double[]`; если у вас есть `int[]` или другие числовые массивы, приведите их или преобразуйте в `double[]` перед передачей.

**Q: Появится ли указанное мной имя серии автоматически на диаграмме?**  
A: Строка, переданная в качестве первого аргумента (например, "Demo Series"), используется как заголовок серии и по умолчанию отображается в легенде диаграммы.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}