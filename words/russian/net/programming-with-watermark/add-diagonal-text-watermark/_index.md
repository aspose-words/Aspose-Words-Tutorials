---
title: Создание диагонального текстового водяного знака с пользовательским шрифтом в документе Word с помощью Aspose.Words for .NET
weight: 210
limit:
description: Пошаговый код для добавления диагонального текстового водяного знака с пользовательским шрифтом в файл Word .docx с использованием Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Пошаговый код для добавления диагонального текстового водяного знака
    с пользовательским шрифтом в файл Word .docx с использованием Aspose.Words for
    .NET.
  headline: Создание диагонального текстового водяного знака с пользовательским шрифтом
    в документе Word с помощью Aspose.Words for .NET
  type: TechArticle
- description: Пошаговый код для добавления диагонального текстового водяного знака
    с пользовательским шрифтом в файл Word .docx с использованием Aspose.Words for
    .NET.
  name: Создание диагонального текстового водяного знака с пользовательским шрифтом
    в документе Word с помощью Aspose.Words for .NET
  steps:
  - name: Создайте новый пустой экземпляр документа Word с именем `document`.
    text: Создайте новый пустой экземпляр документа Word с именем `document`.
  - name: Настройте `watermarkSettings` с шрифтом Arial 48 пт серого цвета, диагональным
      расположением и непрозрачным отображением.
    text: Настройте `watermarkSettings` с шрифтом Arial 48 пт серого цвета, диагональным
      расположением и непрозрачным отображением.
  - name: Примените текстовый водяной знак «Private» к `document`, используя ранее
      определённые настройки.
    text: Примените текстовый водяной знак «Private» к `document`, используя ранее
      определённые настройки.
  - name: Укажите путь к файлу, в котором будет сохранён документ с водяным знаком.
    text: Укажите путь к файлу, в котором будет сохранён документ с водяным знаком.
  - name: Сохраните изменённый `document` по указанному пути в виде файла .docx.
    text: Сохраните изменённый `document` по указанному пути в виде файла .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` определяет, будет ли водяной знак отображаться с частичной
      непрозрачностью; значение `false` делает его полностью непрозрачным, а `true`
      применяет стандартный полупрозрачный эффект.'
    question: Что контролирует флаг **IsSemitrasparent** в `TextWatermarkOptions`?
  - answer: Да — установите свойство `Layout` в `WatermarkLayout.Horizontal` (или
      другое значение перечисления) перед вызовом `document.Watermark.SetText`.
    question: Можно ли изменить ориентацию водяного знака на горизонтальную вместо
      диагональной?
  - answer: Word переключится на шрифт по умолчанию для водяного знака, поэтому текст
      всё равно будет отображён, но может выглядеть иначе, чем задумывалось.
    question: Что произойдёт, если указанный `FontFamily` (например, "Arial") не установлен
      на целевой машине?
  - answer: Загрузите существующий файл с помощью `Document document = new Document("Existing.docx");`,
      затем настройте `TextWatermarkOptions` и вызовите `document.Watermark.SetText`,
      как показано.
    question: Можно ли добавить водяной знак в существующий файл `.docx`, а не создавать
      новый?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Добавить диагональный текстовый водяной знак с пользовательским шрифтом
og_description: Научитесь за считанные минуты внедрять наклонённый текстовый водяной знак со своим шрифтом в файл Word.
og_image_alt: Руководство, показывающее, как добавить диагональный текстовый водяной знак с пользовательским шрифтом в документ Word с помощью Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Создание диагонального текстового водяного знака с пользовательским шрифтом в документе Word с помощью Aspose.Words
В этом учебном материале пошагово показано, как создать новый документ Word, настроить диагональный текстовый водяной знак с выбранными параметрами шрифта, применить его через API Document.Watermark.SetText и сохранить результат в виде файла .docx. В итоге вы получите профессионально оформленный документ с водяным знаком, демонстрирующим ваш бренд или право собственности. Код шаг за шагом готов к копированию в любой проект .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Что контролирует флаг **IsSemitrasparent** в `TextWatermarkOptions`?**  
A: `IsSemitrasparent` определяет, будет ли водяной знак отображаться с частичной непрозрачностью; значение `false` делает его полностью непрозрачным, а `true` применяет стандартный полупрозрачный эффект.

**Q: Можно ли изменить ориентацию водяного знака на горизонтальную вместо диагональной?**  
A: Да — установите свойство `Layout` в `WatermarkLayout.Horizontal` (или другое значение перечисления) перед вызовом `document.Watermark.SetText`.

**Q: Что произойдёт, если указанный `FontFamily` (например, "Arial") не установлен на целевой машине?**  
A: Word переключится на шрифт по умолчанию для водяного знака, поэтому текст всё равно будет отображён, но может выглядеть иначе, чем задумывалось.

**Q: Можно ли добавить водяной знак в существующий файл `.docx`, а не создавать новый?**  
A: Загрузите существующий файл с помощью `Document document = new Document("Existing.docx");`, затем настройте `TextWatermarkOptions` и вызовите `document.Watermark.SetText`, как показано.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}