---
title: Вставьте пример диаграммы столбцов в документ Word с помощью Aspose.Words for .NET
weight: 410
limit:
description: Пошаговое руководство по созданию файла Word, вставке диаграммы столбцов по умолчанию с помощью DocumentBuilder.InsertChart, доступу к объекту диаграммы и сохранению в формате .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Пошаговое руководство по созданию файла Word, вставке диаграммы столбцов
    по умолчанию с помощью DocumentBuilder.InsertChart, доступу к объекту диаграммы
    и сохранению в формате .docx.
  headline: Вставьте пример диаграммы столбцов в документ Word с помощью Aspose.Words
    for .NET
  type: TechArticle
- description: Пошаговое руководство по созданию файла Word, вставке диаграммы столбцов
    по умолчанию с помощью DocumentBuilder.InsertChart, доступу к объекту диаграммы
    и сохранению в формате .docx.
  name: Вставьте пример диаграммы столбцов в документ Word с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте пустой документ Word и DocumentBuilder для его редактирования.
    text: Создайте пустой документ Word и DocumentBuilder для его редактирования.
  - name: Вставьте диаграмму столбцов размером 432 × 252 пункта в документ.
    text: Вставьте диаграмму столбцов размером 432 × 252 пункта в документ.
  - name: Получите объект Chart из вставленной фигуры для дальнейшей настройки при
      необходимости.
    text: Получите объект Chart из вставленной фигуры для дальнейшей настройки при
      необходимости.
  - name: Сохраните документ, который теперь содержит вставленную диаграмму столбцов,
      в файл .docx.
    text: Сохраните документ, который теперь содержит вставленную диаграмму столбцов,
      в файл .docx.
  type: HowTo
- questions:
  - answer: Размеры задаются в пунктах (1 пункт = 1/72 дюйма), поэтому 432 pt ≈ 6
      дюймов и 252 pt ≈ 3,5 дюйма.
    question: Какие единицы измерения используются для параметров ширины и высоты
      (432, 252) в InsertChart?
  - answer: Да — после вставки у вас есть объект Chart через `chartContainer.Chart`;
      вы можете изменить его SeriesCollection, Categories и Values, чтобы заменить
      примерные данные.
    question: Могу ли я изменить данные диаграммы после вызова InsertChart с набором
      данных по умолчанию?
  - answer: Просто замените `ChartType.Column` другим значением перечисления, например
      `ChartType.Line`, в вызове `InsertChart`.
    question: Можно ли вставить другой тип диаграммы (например, линейную) с использованием
      того же кода?
  - answer: Нет — `docBuilder.InsertChart` автоматически встраивает диаграмму в `Shape`;
      вызов `wordDoc.Save` сохраняет диаграмму вместе с документом.
    question: Нужно ли вызывать какой‑либо дополнительный метод для встраивания диаграммы
      перед сохранением документа?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Вставьте пример диаграммы столбцов в документ Word
og_description: Добавьте готовую диаграмму столбцов в документ Word с помощью Aspose.Words for .NET за несколько минут.
og_image_alt: Скриншот, показывающий документ Word с вставленной примерной диаграммой столбцов, созданной с помощью Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставьте пример диаграммы столбцов в документ Word с помощью Aspose.Words
Этот учебный материал пошагово покажет, как создать новый документ Word и вставить диаграмму столбцов по умолчанию с помощью DocumentBuilder.InsertChart. Вы также увидите, как получить встроенный объект Chart для дальнейшего манипулирования. В конце руководство демонстрирует, как сохранить документ в файл .docx.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: Какие единицы измерения используются для параметров ширины и высоты (432, 252) в InsertChart?**  
A: Размеры задаются в пунктах (1 пункт = 1/72 дюйма), поэтому 432 pt ≈ 6 дюймов и 252 pt ≈ 3,5 дюйма.

**Q: Могу ли я изменить данные диаграммы после вызова InsertChart с набором данных по умолчанию?**  
A: Да — после вставки у вас есть объект Chart через `chartContainer.Chart`; вы можете изменить его SeriesCollection, Categories и Values, чтобы заменить примерные данные.

**Q: Можно ли вставить другой тип диаграммы (например, линейную) с использованием того же кода?**  
A: Просто замените `ChartType.Column` другим значением перечисления, например `ChartType.Line`, в вызове `InsertChart`.

**Q: Нужно ли вызывать какой‑либо дополнительный метод для встраивания диаграммы перед сохранением документа?**  
A: Нет — `docBuilder.InsertChart` автоматически встраивает диаграмму в `Shape`; вызов `wordDoc.Save` сохраняет диаграмму вместе с документом.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}