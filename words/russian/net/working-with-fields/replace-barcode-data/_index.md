---
title: Замена данных штрих‑кода в документах Word с помощью Aspose.Words for .NET
weight: 110
limit:
description: Узнайте, как вставить поле DISPLAYBARCODE и заменить его строку данных с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Узнайте, как вставить поле DISPLAYBARCODE и заменить его строку данных
    с помощью Aspose.Words for .NET.
  headline: Замена данных штрих‑кода в документах Word с помощью Aspose.Words for
    .NET
  type: TechArticle
- description: Узнайте, как вставить поле DISPLAYBARCODE и заменить его строку данных
    с помощью Aspose.Words for .NET.
  name: Замена данных штрих‑кода в документах Word с помощью Aspose.Words for .NET
  steps:
  - name: Создайте новый объект Document и DocumentBuilder для построения его содержимого.
    text: Создайте новый объект Document и DocumentBuilder для построения его содержимого.
  - name: Вставьте поле DISPLAYBARCODE и задайте его тип, начальное значение и символы
      начала/конца, затем добавьте разрыв строки.
    text: Вставьте поле DISPLAYBARCODE и задайте его тип, начальное значение и символы
      начала/конца, затем добавьте разрыв строки.
  - name: Вызовите UpdateFields, чтобы отобразить только что вставленное поле штрих‑кода.
    text: Вызовите UpdateFields, чтобы отобразить только что вставленное поле штрих‑кода.
  - name: Используйте механизм Find/Replace для замены строки данных штрих‑кода с
      INIT123 на NEWVAL.
    text: Используйте механизм Find/Replace для замены строки данных штрих‑кода с
      INIT123 на NEWVAL.
  - name: Снова обновите поля, чтобы DISPLAYBARCODE отразил новую строку данных.
    text: Снова обновите поля, чтобы DISPLAYBARCODE отразил новую строку данных.
  - name: Сохраните документ в файл формата .docx.
    text: Сохраните документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` изменяет только исходный текст; визуальное представление
      поля DISPLAYBARCODE пересоздаётся только при вызове `UpdateFields()`, поэтому
      новый штрих‑код появляется в сохранённом документе.'
    question: Зачем мне вызывать `myDocument.UpdateFields()` после выполнения `Range.Replace`?
  - answer: Да, `Document.Range.Replace` работает со всем диапазоном документа, поэтому
      любой совпадающий текст в других местах будет заменён, если только вы не ограничите
      поиск с помощью `FindReplaceOptions` (например, указав конкретный `Range` или
      используя `.MatchWholeWord`).
    question: Повлияет ли вызов `Replace("INIT123", "NEWVAL", ...)` на другие вхождения
      "INIT123" вне поля штрих‑кода?
  - answer: Вы можете в любой момент присвоить новое значение `displayBarcode.BarcodeType`,
      но после этого необходимо вызвать `myDocument.UpdateFields()`, чтобы изменение
      отразилось в отрисованном штрих‑коде.
    question: Можно ли изменить тип штрих‑кода (например, с CODE39 на QR) после вставки
      поля?
  - answer: Когда `AddStartStopChar` установлен в true, Aspose.Words автоматически
      добавляет необходимые символы начала/конца (`*`) вокруг значения штрих‑кода,
      что требуется для CODE39; установите false, если ваша символьная система их
      не требует.
    question: Что делает свойство `AddStartStopChar = true` для штрих‑кодов CODE39?
  - answer: Для простого точного совпадения специальные настройки не требуются, но
      вы можете включить `.MatchCase` или `.MatchWholeWord` в `FindReplaceOptions`,
      чтобы избежать случайных частичных замен.
    question: Нужно ли настраивать какие‑либо специальные параметры в `FindReplaceOptions`
      для безопасной замены значения штрих‑кода?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Обновление поля штрих‑кода в Word с помощью Aspose.Words
og_description: Замените строку данных штрих‑кода и мгновенно обновите её в файле Word.
og_image_alt: Скриншот, показывающий документ Word с полем DISPLAYBARCODE до и после замены данных с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Замена данных штрих‑кода в документах Word с помощью Aspose.Words
Этот учебник демонстрирует, как вставить поле DISPLAYBARCODE в документ Word и затем использовать метод Document.Range.Replace для изменения строки данных штрих‑кода. После замены поле обновляется, чтобы обновлённый штрих‑код появился в сохранённом файле. Следуйте инструкциям, чтобы увидеть мгновенное обновление штрих‑кода без необходимости воссоздавать поле.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: Зачем мне вызывать `myDocument.UpdateFields()` после выполнения `Range.Replace`?**  
A: `Range.Replace` изменяет только исходный текст; визуальное представление поля DISPLAYBARCODE пересоздаётся только при вызове `UpdateFields()`, поэтому новый штрих‑код появляется в сохранённом документе.

**Q: Повлияет ли вызов `Replace("INIT123", "NEWVAL", ...)` на другие вхождения "INIT123" вне поля штрих‑кода?**  
A: Да, `Document.Range.Replace` работает со всем диапазоном документа, поэтому любой совпадающий текст в других местах будет заменён, если только вы не ограничите поиск с помощью `FindReplaceOptions` (например, указав конкретный `Range` или используя `.MatchWholeWord`).

**Q: Можно ли изменить тип штрих‑кода (например, с CODE39 на QR) после вставки поля?**  
A: Вы можете в любой момент присвоить новое значение `displayBarcode.BarcodeType`, но после этого необходимо вызвать `myDocument.UpdateFields()`, чтобы изменение отразилось в отрисованном штрих‑коде.

**Q: Что делает свойство `AddStartStopChar = true` для штрих‑кодов CODE39?**  
A: Когда `AddStartStopChar` установлен в true, Aspose.Words автоматически добавляет необходимые символы начала/конца (`*`) вокруг значения штрих‑кода, что требуется для CODE39; установите false, если ваша символьная система их не требует.

**Q: Нужно ли настраивать какие‑либо специальные параметры в `FindReplaceOptions` для безопасной замены значения штрих‑кода?**  
A: Для простого точного совпадения специальные настройки не требуются, но вы можете включить `.MatchCase` или `.MatchWholeWord` в `FindReplaceOptions`, чтобы избежать случайных частичных замен.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}