---
title: Пропорциональное изменение размера диаграммы при изменении размера страницы в Word с использованием Aspose.Words for .NET
weight: 210
limit:
description: Научитесь автоматически изменять размер столбчатой диаграммы Word при переключении документа на A4 с помощью Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Научитесь автоматически изменять размер столбчатой диаграммы Word при
    переключении документа на A4 с помощью Aspose.Words for .NET.
  headline: Пропорциональное изменение размера диаграммы при изменении размера страницы
    в Word с использованием Aspose.Words for .NET
  type: TechArticle
- description: Научитесь автоматически изменять размер столбчатой диаграммы Word при
    переключении документа на A4 с помощью Aspose.Words for .NET.
  name: Пропорциональное изменение размера диаграммы при изменении размера страницы
    в Word с использованием Aspose.Words for .NET
  steps:
  - name: Создайте новый объект Document и DocumentBuilder для его редактирования.
    text: Создайте новый объект Document и DocumentBuilder для его редактирования.
  - name: Вставьте столбчатую диаграмму размером 432×252 пункта и получите её объект
      Chart.
    text: Вставьте столбчатую диаграмму размером 432×252 пункта и получите её объект
      Chart.
  - name: Установите текст заголовка диаграммы как "Quarterly Revenue" и сделайте
      его видимым.
    text: Установите текст заголовка диаграммы как "Quarterly Revenue" и сделайте
      его видимым.
  - name: Сохраните документ в файл, отображающий исходный размер диаграммы.
    text: Сохраните документ в файл, отображающий исходный размер диаграммы.
  - name: Измените размер бумаги документа на A4 и обновите макет.
    text: Измените размер бумаги документа на A4 и обновите макет.
  - name: Вычислите новую ширину диаграммы, равную 80 % ширины страницы, при сохранении
      исходного соотношения сторон.
    text: Вычислите новую ширину диаграммы, равную 80 % ширины страницы, при сохранении
      исходного соотношения сторон.
  - name: Если объект shape содержит диаграмму, примените вычисленную ширину и высоту
      для её изменения размера.
    text: Если объект shape содержит диаграмму, примените вычисленную ширину и высоту
      для её изменения размера.
  - name: Сохраните документ после изменения размера диаграммы, чтобы отразить новый
      размер страницы.
    text: Сохраните документ после изменения размера диаграммы, чтобы отразить новый
      размер страницы.
  type: HowTo
- questions:
  - answer: Да. Изменение `docBuilder.PageSetup.PaperSize` не приводит к автоматической
      корректировке существующих фигур, поэтому вам необходимо самостоятельно пересчитать
      и присвоить `chartContainer.Width` и `Height`, как показано.
    question: Нужно ли вручную изменять размер диаграммы после изменения размера бумаги
      документа?
  - answer: Он сохраняет `originalAspectRatio = chartContainer.Height / chartContainer.Width`,
      а затем вычисляет `newChartHeight = newChartWidth * originalAspectRatio` после
      определения новой ширины.
    question: Как код сохраняет исходное соотношение ширины к высоте диаграммы при
      изменении размера?
  - answer: '`UpdatePageLayout()` заставляет движок макета переоценить размеры страниц,
      гарантируя, что `docBuilder.PageSetup.PageWidth` отражает новую ширину A4 до
      пересчёта размера диаграммы.'
    question: Зачем вызывается `myDoc.UpdatePageLayout()` после установки размера
      бумаги на A4?
  - answer: Условие `if (chartContainer.HasChart)` предотвращает присвоение `Width`
      и `Height`, когда диаграмма отсутствует, тем самым избегая исключения во время
      выполнения.
    question: Что произойдёт, если вставленная фигура на самом деле не содержит диаграмму?
  - answer: Конечно — замените множитель `0.8` любой желаемой пропорцией; остальная
      часть логики изменения размера всё равно сохранит исходное соотношение сторон.
    question: Могу ли я изменить коэффициент масштабирования 80 % на другое значение?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Изменить размер диаграммы Word при переключении на A4
og_description: Сохраните пропорциональность диаграммы, автоматически изменяя её размер после переключения документа на A4.
og_image_alt: Скриншот, показывающий автоматическое изменение размера столбчатой диаграммы для соответствия документу Word формата A4 с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Пропорциональное изменение размера диаграммы при изменении размера страницы в Word с использованием Aspose.Words
Этот учебный материал показывает, как вставить столбчатую диаграмму в документ Word, переключить размер страницы документа на A4 и автоматически изменить размер диаграммы, чтобы она оставалась пропорциональной новой ширине страницы. Следуя инструкциям, вы увидите, как диаграмма корректирует свои размеры без ручного масштабирования, обеспечивая согласованный макет при разных форматах страниц.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Нужно ли вручную изменять размер диаграммы после изменения размера бумаги документа?**  
A: Да. Изменение `docBuilder.PageSetup.PaperSize` не приводит к автоматической корректировке существующих фигур, поэтому вам необходимо самостоятельно пересчитать и присвоить `chartContainer.Width` и `Height`, как показано.

**Q: Как код сохраняет исходное соотношение ширины к высоте диаграммы при изменении размера?**  
A: Он сохраняет `originalAspectRatio = chartContainer.Height / chartContainer.Width`, а затем вычисляет `newChartHeight = newChartWidth * originalAspectRatio` после определения новой ширины.

**Q: Зачем вызывается `myDoc.UpdatePageLayout()` после установки размера бумаги на A4?**  
A: `UpdatePageLayout()` заставляет движок макета переоценить размеры страниц, гарантируя, что `docBuilder.PageSetup.PageWidth` отражает новую ширину A4 до пересчёта размера диаграммы.

**Q: Что произойдёт, если вставленная фигура на самом деле не содержит диаграмму?**  
A: Условие `if (chartContainer.HasChart)` предотвращает присвоение `Width` и `Height`, когда диаграмма отсутствует, тем самым избегая исключения во время выполнения.

**Q: Могу ли я изменить коэффициент масштабирования 80 % на другое значение?**  
A: Конечно — замените множитель `0.8` любой желаемой пропорцией; остальная часть логики изменения размера всё равно сохранит исходное соотношение сторон.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}