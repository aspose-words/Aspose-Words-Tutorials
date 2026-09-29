---
title: Вставка штрих‑кода DataMatrix в документ Word с помощью Aspose.Words for .NET
weight: 210
limit:
description: Программно добавьте штрих‑код DataMatrix в документ Word с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Программно добавьте штрих‑код DataMatrix в документ Word с помощью
    Aspose.Words for .NET.
  headline: Вставка штрих‑кода DataMatrix в документ Word с помощью Aspose.Words for
    .NET
  type: TechArticle
- description: Программно добавьте штрих‑код DataMatrix в документ Word с помощью
    Aspose.Words for .NET.
  name: Вставка штрих‑кода DataMatrix в документ Word с помощью Aspose.Words for .NET
  steps:
  - name: Создайте новый пустой документ Word и объект DocumentBuilder для его редактирования.
    text: Создайте новый пустой документ Word и объект DocumentBuilder для его редактирования.
  - name: Вставьте поле DISPLAYBARCODE в текущую позицию курсора, что добавит заполнитель
      поля в документ.
    text: Вставьте поле DISPLAYBARCODE в текущую позицию курсора, что добавит заполнитель
      поля в документ.
  - name: Установите свойство BarcodeType поля в DataMatrix и укажите строку данных
      для кодирования.
    text: Установите свойство BarcodeType поля в DataMatrix и укажите строку данных
      для кодирования.
  - name: При необходимости задайте цвета фона и переднего плана штрих‑кода.
    text: При необходимости задайте цвета фона и переднего плана штрих‑кода.
  - name: Вызовите метод UpdateFields у документа, чтобы отобразить изображение штрих‑кода
      внутри поля.
    text: Вызовите метод UpdateFields у документа, чтобы отобразить изображение штрих‑кода
      внутри поля.
  - name: Сохраните документ в файл формата .docx.
    text: Сохраните документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: Поле будет вставлено, но `document.UpdateFields()` оставит штрих‑код пустым,
      и Aspose.Words выбросит `FieldException`, указывающий на недопустимый тип штрих‑кода.
    question: Что произойдёт, если присвоить неподдерживаемое значение свойству `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` отрисовывает изображения штрих‑кодов, поэтому вы можете
      вставить несколько объектов `FieldDisplayBarcode` и вызвать `document.UpdateFields()`
      один раз в конце, чтобы отобразить их все.'
    question: Нужно ли вызывать `document.UpdateFields()` после каждой вставки штрих‑кода,
      или можно вызвать один раз после добавления всех полей?
  - answer: Оба свойства ожидают шестнадцатеричную строку RGB, начинающуюся с `0x`
      (например, "0xFF0000" для красного); любой другой формат будет игнорироваться,
      и будут использованы цвета по умолчанию.
    question: В каком формате должны быть строковые значения цветов для `BackgroundColor`
      и `ForegroundColor`?
  - answer: Да — просто задайте `displayBarcodeField.BarcodeValue` новой строкой и
      снова вызовите `document.UpdateFields()`, чтобы обновить отрисованное изображение.
    question: Можно ли изменить содержимое штрих‑кода после вставки поля?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Вставка штрих‑кода DataMatrix с помощью Aspose.Words
og_description: Узнайте, как добавить штрих‑код DataMatrix в файл Word всего в несколько строк кода .NET.
og_image_alt: Руководство, показывающее, как вставить и отобразить штрих‑код DataMatrix в документе Word с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка штрих‑кода DataMatrix в документ Word с помощью Aspose.Words
С помощью Aspose.Words for .NET вы можете программно добавить штрих‑код DataMatrix в документ Word. В этом руководстве показано, как создать новый документ, вставить поле DISPLAYBARCODE, установить его тип в DataMatrix и отобразить изображение штрих‑кода с помощью классов Document и DocumentBuilder. Следуйте инструкциям, чтобы создать печатаемый штрих‑код непосредственно в вашем файле .docx.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Что произойдёт, если присвоить неподдерживаемое значение свойству `displayBarcodeField.BarcodeType`?**  
A: Поле будет вставлено, но `document.UpdateFields()` оставит штрих‑код пустым, и Aspose.Words выбросит `FieldException`, указывающий на недопустимый тип штрих‑кода.

**Q: Нужно ли вызывать `document.UpdateFields()` после каждой вставки штрих‑кода, или можно вызвать один раз после добавления всех полей?**  
A: `UpdateFields()` отрисовывает изображения штрих‑кодов, поэтому вы можете вставить несколько объектов `FieldDisplayBarcode` и вызвать `document.UpdateFields()` один раз в конце, чтобы отобразить их все.

**Q: В каком формате должны быть строковые значения цветов для `BackgroundColor` и `ForegroundColor`?**  
A: Оба свойства ожидают шестнадцатеричную строку RGB, начинающуюся с `0x` (например, "0xFF0000" для красного); любой другой формат будет игнорироваться, и будут использованы цвета по умолчанию.

**Q: Можно ли изменить содержимое штрих‑кода после вставки поля?**  
A: Да — просто задайте `displayBarcodeField.BarcodeValue` новой строкой и снова вызовите `document.UpdateFields()`, чтобы обновить отрисованное изображение.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}