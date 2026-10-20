---
title: Вставка пользовательской столбчатой диаграммы в документ Word с помощью Aspose.Words for .NET
weight: 310
limit:
description: Создайте файл Word, вставьте столбчатую диаграмму, замените её данные пользовательским массивом, добавьте заголовок и сохраните — всё с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Создайте файл Word, вставьте столбчатую диаграмму, замените её данные
    пользовательским массивом, добавьте заголовок и сохраните — всё с помощью Aspose.Words
    for .NET.
  headline: Вставка пользовательской столбчатой диаграммы в документ Word с помощью
    Aspose.Words for .NET
  type: TechArticle
- description: Создайте файл Word, вставьте столбчатую диаграмму, замените её данные
    пользовательским массивом, добавьте заголовок и сохраните — всё с помощью Aspose.Words
    for .NET.
  name: Вставка пользовательской столбчатой диаграммы в документ Word с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте новый Document и DocumentBuilder, привязанный к нему.
    text: Создайте новый Document и DocumentBuilder, привязанный к нему.
  - name: Вставьте в документ столбчатую диаграмму размером 432×252 пункта и получите
      её объект Chart.
    text: Вставьте в документ столбчатую диаграмму размером 432×252 пункта и получите
      её объект Chart.
  - name: Удалите автоматически сгенерированный образец ряда из диаграммы.
    text: Удалите автоматически сгенерированный образец ряда из диаграммы.
  - name: Определите подписи категорий оси X и элементы легенды для каждого ряда.
    text: Определите подписи категорий оси X и элементы легенды для каждого ряда.
  - name: Создайте двумерный массив, где каждая строка содержит значения для одного
      ряда.
    text: Создайте двумерный массив, где каждая строка содержит значения для одного
      ряда.
  - name: Пройдитесь по каждому ряду, извлеките его значения из матрицы и добавьте
      ряд в диаграмму с соответствующим элементом легенды и подписями оси X.
    text: Пройдитесь по каждому ряду, извлеките его значения из матрицы и добавьте
      ряд в диаграмму с соответствующим элементом легенды и подписями оси X.
  - name: Установите текст заголовка диаграммы как 'Half‑Yearly Revenue' и сделайте
      его видимым.
    text: Установите текст заголовка диаграммы как 'Half‑Yearly Revenue' и сделайте
      его видимым.
  - name: Сохраните документ, содержащий пользовательскую диаграмму, в файл формата
      .docx.
    text: Сохраните документ, содержащий пользовательскую диаграмму, в файл формата
      .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` ожидает, что длина массива значений будет равна количеству
      меток оси X, и необходимо добавить ровно один ряд на каждый элемент легенды;
      несоответствие вызовет `ArgumentException` во время выполнения.'
    question: Что будет, если строки или столбцы в `dataMatrix` не совпадают по длине
      с `legendEntries` или `xLabels`?
  - answer: Да — замените `ChartType.Column` в `docBuilder.InsertChart` на любой другой
      `ChartType` (например, `ChartType.Line`), и последующие вызовы `Series.Add`
      заполнят новую диаграмму тем же способом.
    question: Могу ли я использовать другой тип диаграммы, например линейную, с той
      же логикой заполнения данными?
  - answer: Отрегулируйте свойства `Width` и `Height` объекта `Shape`, возвращаемого
      `InsertChart` (например, `chartContainer.Width = 500; chartContainer.Height
      = 300;`).
    question: Как изменить размер диаграммы после её вставки?
  - answer: Установите `chartObj.Series[i].HasDataLabel = true;` для каждого ряда
      после его добавления, либо пройдитесь по `chartObj.Series` и включите `HasDataLabel`,
      чтобы отобразить значения на диаграмме.
    question: Есть ли быстрый способ отобразить подписи данных на каждом столбце диаграммы?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Добавить пользовательскую столбчатую диаграмму в документ Word
og_description: Замените данные диаграммы по умолчанию вашим массивом и установите заголовок за считанные секунды.
og_image_alt: Скриншот, показывающий документ Word с пользовательской столбчатой диаграммой, созданной с помощью Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка пользовательской столбчатой диаграммы в документ Word с помощью Aspose.Words
Это руководство проведёт вас через процесс создания документа Word, вставки столбчатой диаграммы, очистки её данных по умолчанию и заполнения диаграммы пользовательскими значениями из двумерного массива — сопоставляя каждую строку с рядом и каждый столбец с категорией. Вы также увидите, как добавить заголовок диаграммы перед сохранением файла. Следуйте инструкциям, чтобы получить полностью настроенную диаграмму непосредственно в вашем файле Word.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Что будет, если строки или столбцы в `dataMatrix` не совпадают по длине с `legendEntries` или `xLabels`?**  
A: `Chart.Series.Add` ожидает, что длина массива значений будет равна количеству меток оси X, и необходимо добавить ровно один ряд на каждый элемент легенды; несоответствие вызовет `ArgumentException` во время выполнения.

**Q: Могу ли я использовать другой тип диаграммы, например линейную, с той же логикой заполнения данными?**  
A: Да — замените `ChartType.Column` в `docBuilder.InsertChart` на любой другой `ChartType` (например, `ChartType.Line`), и последующие вызовы `Series.Add` заполнят новую диаграмму тем же способом.

**Q: Как изменить размер диаграммы после её вставки?**  
A: Отрегулируйте свойства `Width` и `Height` объекта `Shape`, возвращаемого `InsertChart` (например, `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Есть ли быстрый способ отобразить подписи данных на каждом столбце диаграммы?**  
A: Установите `chartObj.Series[i].HasDataLabel = true;` для каждого ряда после его добавления, либо пройдитесь по `chartObj.Series` и включите `HasDataLabel`, чтобы отобразить значения на диаграмме.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}