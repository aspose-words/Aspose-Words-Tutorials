---
title: Добавление красного диагонального текстового водяного знака в документы Word с помощью Aspose.Words for .NET
weight: 110
limit:
description: Автоматически применяйте красный диагональный текстовый водяной знак к каждому файлу Word, генерируемому в пакете с использованием Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Автоматически применяйте красный диагональный текстовый водяной знак
    к каждому файлу Word, генерируемому в пакете с использованием Aspose.Words for
    .NET.
  headline: Добавление красного диагонального текстового водяного знака в документы
    Word с помощью Aspose.Words for .NET
  type: TechArticle
- description: Автоматически применяйте красный диагональный текстовый водяной знак
    к каждому файлу Word, генерируемому в пакете с использованием Aspose.Words for
    .NET.
  name: Добавление красного диагонального текстового водяного знака в документы Word
    с помощью Aspose.Words for .NET
  steps:
  - name: Создайте папку "GeneratedReports", в которой будут сохраняться выходные
      файлы.
    text: Создайте папку "GeneratedReports", в которой будут сохраняться выходные
      файлы.
  - name: Запустите цикл, который сгенерирует три отдельные документа.
    text: Запустите цикл, который сгенерирует три отдельные документа.
  - name: Создайте новый пустой объект документа Word.
    text: Создайте новый пустой объект документа Word.
  - name: Используйте DocumentBuilder, чтобы записать строку заголовка и описание
      в документ.
    text: Используйте DocumentBuilder, чтобы записать строку заголовка и описание
      в документ.
  - name: Определите внешний вид водяного знака, включая шрифт, размер, цвет и диагональное
      расположение.
    text: Определите внешний вид водяного знака, включая шрифт, размер, цвет и диагональное
      расположение.
  - name: Примените настроенный красный диагональный водяной знак с текстом "PROTECTED"
      к документу.
    text: Примените настроенный красный диагональный водяной знак с текстом "PROTECTED"
      к документу.
  - name: Сохраните документ с водяным знаком в папку "GeneratedReports" под уникальным
      именем файла.
    text: Сохраните документ с водяным знаком в папку "GeneratedReports" под уникальным
      именем файла.
  - name: Закройте цикл после обработки текущего документа.
    text: Закройте цикл после обработки текущего документа.
  type: HowTo
- questions:
  - answer: IsSemitrasparent определяет, будет ли водяной знак отображаться с частичной
      непрозрачностью; установка его в **true** делает текст полупрозрачным, чтобы
      подлежащий контент оставался более читаемым.
    question: Что контролирует параметр **IsSemitrasparent** и какой эффект имеет
      установка его в **true**?
  - answer: Да — установите свойство **Layout** в **WatermarkLayout.Horizontal** в
      объекте **TextWatermarkOptions** перед вызовом **document.Watermark.SetText**.
    question: Могу ли я изменить ориентацию водяного знака на горизонтальную вместо
      диагональной?
  - answer: Этот фрагмент кода создаёт новый экземпляр **Document**, но вы можете
      открыть любой существующий файл (например, `new Document("Existing.docx")`)
      и затем вызвать **document.Watermark.SetText**, чтобы применить тот же водяной
      знак.
    question: Добавит ли этот код водяной знак в существующий файл Word или только
      в только что созданные документы?
  - answer: Назначьте пользовательский цвет с помощью **Color.FromArgb(red, green,
      blue)** свойству **Color** в **TextWatermarkOptions**, например, `Color = Color.FromArgb(128,
      0, 128)` для пурпурного.
    question: Как использовать пользовательский RGB‑цвет для водяного знака вместо
      предопределённого **Color.Red**?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Добавить красный диагональный текстовый водяной знак в документы Word
og_description: Посмотрите, как автоматически применять красный диагональный водяной знак к каждому документу Word в пакете с помощью Aspose.Words.
og_image_alt: Руководство, показывающее, как добавить красный диагональный текстовый водяной знак в документы Word с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавление красного диагонального текстового водяного знака в документы Word с помощью Aspose.Words
Этот учебный материал демонстрирует, как автоматически внедрять красный диагональный текстовый водяной знак в каждый документ Word, создаваемый в процессе пакетной генерации отчётов. С помощью классов Document и DocumentBuilder из Aspose.Words for .NET водяной знак применяется программно во время создания файлов, обеспечивая наличие одинакового брендинга или уведомления о конфиденциальности в каждом документе без ручных действий.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Что контролирует параметр **IsSemitrasparent** и какой эффект имеет установка его в **true**?**  
A: IsSemitrasparent определяет, будет ли водяной знак отображаться с частичной непрозрачностью; установка его в **true** делает текст полупрозрачным, чтобы подлежащий контент оставался более читаемым.

**Q: Могу ли я изменить ориентацию водяного знака на горизонтальную вместо диагональной?**  
A: Да — установите свойство **Layout** в **WatermarkLayout.Horizontal** в объекте **TextWatermarkOptions** перед вызовом **document.Watermark.SetText**.

**Q: Добавит ли этот код водяной знак в существующий файл Word или только в только что созданные документы?**  
A: Этот фрагмент кода создаёт новый экземпляр **Document**, но вы можете открыть любой существующий файл (например, `new Document("Existing.docx")`) и затем вызвать **document.Watermark.SetText**, чтобы применить тот же водяной знак.

**Q: Как использовать пользовательский RGB‑цвет для водяного знака вместо предопределённого **Color.Red**?**  
A: Назначьте пользовательский цвет с помощью **Color.FromArgb(red, green, blue)** свойству **Color** в **TextWatermarkOptions**, например, `Color = Color.FromArgb(128, 0, 128)` для пурпурного.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}