---
title: Обновление заголовка диаграммы и переключение видимости легенды в Word с помощью Aspose.Words for .NET
weight: 810
limit:
description: Научитесь изменять заголовок диаграммы и управлять видимостью легенды в документе Word с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Научитесь изменять заголовок диаграммы и управлять видимостью легенды
    в документе Word с помощью Aspose.Words for .NET.
  headline: Обновление заголовка диаграммы и переключение видимости легенды в Word
    с помощью Aspose.Words for .NET
  type: TechArticle
- description: Научитесь изменять заголовок диаграммы и управлять видимостью легенды
    в документе Word с помощью Aspose.Words for .NET.
  name: Обновление заголовка диаграммы и переключение видимости легенды в Word с помощью
    Aspose.Words for .NET
  steps:
  - name: Задайте заголовок диаграммы, предоставленный пользователем, и укажите, должна
      ли отображаться легенда.
    text: Задайте заголовок диаграммы, предоставленный пользователем, и укажите, должна
      ли отображаться легенда.
  - name: Создайте новый документ Word и объект DocumentBuilder для добавления содержимого.
    text: Создайте новый документ Word и объект DocumentBuilder для добавления содержимого.
  - name: Вставьте столбчатую диаграмму размером 432 × 252 pt в документ и проверьте,
      что объект Shape действительно содержит диаграмму.
    text: Вставьте столбчатую диаграмму размером 432 × 252 pt в документ и проверьте,
      что объект Shape действительно содержит диаграмму.
  - name: Получите объект диаграммы, задайте его заголовку текст, полученный от пользователя,
      и убедитесь, что заголовок отображается.
    text: Получите объект диаграммы, задайте его заголовку текст, полученный от пользователя,
      и убедитесь, что заголовок отображается.
  - name: 'Настройте легенду: отобразите её справа, если это запрошено, иначе скройте,
      и разрешите ей накладываться на область построения.'
    text: 'Настройте легенду: отобразите её справа, если это запрошено, иначе скройте,
      и разрешите ей накладываться на область построения.'
  - name: Сохраните изменённый документ на диск под именем CustomChart.docx.
    text: Сохраните изменённый документ на диск под именем CustomChart.docx.
  type: HowTo
- questions:
  - answer: Когда `displayLegend` равно `true`, код устанавливает `chartLegend.Position`
      в `LegendPosition.Right`, делая легенду видимой справа от области построения;
      свойство `Overlay` остаётся `true`, поэтому легенда может перекрывать диаграмму,
      экономя место.
    question: Что изменяется в сгенерированной диаграмме при установке `displayLegend`
      в `true`?
  - answer: Установите `chartTitle.Show = false` (или просто не задавайте `Show =
      true`) после присвоения `chartTitle.Text`; заголовок не будет отображаться в
      документе Word.
    question: Как скрыть заголовок диаграммы, если пользователь его не предоставляет?
  - answer: Да — `InsertChart` возвращает объект `Shape`, который должен содержать
      диаграмму, но проверка `HasChart` гарантирует, что Shape действительно содержит
      объект `Chart`; в противном случае код бросит `InvalidOperationException`.
    question: Необходимо ли проверять `chartContainer.HasChart` после вызова `InsertChart`?
  - answer: Конечно; присвойте любое значение из перечисления `LegendPosition` (например,
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) свойству
      `chartLegend.Position`, чтобы переместить легенду в нужное место.
    question: Можно ли разместить легенду в месте, отличном от правой стороны?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Изменить заголовок и легенду диаграммы в Word
og_description: Научитесь задавать пользовательский заголовок диаграммы и управлять отображением легенды в документе Word с помощью Aspose.Words for .NET.
og_image_alt: Руководство, показывающее код, который обновляет заголовок диаграммы и переключает легенду в документе Word с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Обновление заголовка диаграммы и переключение видимости легенды в Word с помощью Aspose.Words
В этом учебнике показано, как программно изменять диаграмму внутри документа Word с помощью Aspose.Words for .NET. Вы научитесь вставлять столбчатую диаграмму, заменять её заголовок текстом, предоставленным пользователем, и управлять видимостью и наложением легенды в соответствии с предпочтениями пользователя. Эти шаги позволяют динамически настраивать отображение диаграммы без ручного редактирования.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Что изменяется в сгенерированной диаграмме при установке `displayLegend` в `true`?**  
A: Когда `displayLegend` равно `true`, код устанавливает `chartLegend.Position` в `LegendPosition.Right`, делая легенду видимой справа от области построения; свойство `Overlay` остаётся `true`, поэтому легенда может перекрывать диаграмму, экономя место.

**Q: Как скрыть заголовок диаграммы, если пользователь его не предоставляет?**  
A: Установите `chartTitle.Show = false` (или просто не задавайте `Show = true`) после присвоения `chartTitle.Text`; заголовок не будет отображаться в документе Word.

**Q: Необходимо ли проверять `chartContainer.HasChart` после вызова `InsertChart`?**  
A: Да — `InsertChart` возвращает объект `Shape`, который должен содержать диаграмму, но проверка `HasChart` гарантирует, что Shape действительно содержит объект `Chart`; в противном случае код бросит `InvalidOperationException`.

**Q: Можно ли разместить легенду в месте, отличном от правой стороны?**  
A: Конечно; присвойте любое значение из перечисления `LegendPosition` (например, `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) свойству `chartLegend.Position`, чтобы переместить легенду в нужное место.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}