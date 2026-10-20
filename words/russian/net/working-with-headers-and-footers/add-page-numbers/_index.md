---
title: Добавьте номера страниц в нижний колонтитул документа Word с помощью Aspose.Words for .NET
weight: 210
limit:
description: Добавьте автоматически обновляемые номера страниц в основной нижний колонтитул документа Word с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Добавьте автоматически обновляемые номера страниц в основной нижний
    колонтитул документа Word с помощью Aspose.Words for .NET.
  headline: Добавьте номера страниц в нижний колонтитул документа Word с помощью Aspose.Words
    for .NET
  type: TechArticle
- description: Добавьте автоматически обновляемые номера страниц в основной нижний
    колонтитул документа Word с помощью Aspose.Words for .NET.
  name: Добавьте номера страниц в нижний колонтитул документа Word с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте новый объект Document и DocumentBuilder, привязанный к нему.
    text: Создайте новый объект Document и DocumentBuilder, привязанный к нему.
  - name: Переместите курсор builder'а в основной нижний колонтитул первой секции.
    text: Переместите курсор builder'а в основной нижний колонтитул первой секции.
  - name: Установите выравнивание абзаца по центру, чтобы текст в нижнем колонтитуле
      был центрирован.
    text: Установите выравнивание абзаца по центру, чтобы текст в нижнем колонтитуле
      был центрирован.
  - name: Запишите метку "Page " и вставьте поле PAGE, которое отображает текущий
      номер страницы.
    text: Запишите метку "Page " и вставьте поле PAGE, которое отображает текущий
      номер страницы.
  - name: Запишите " of " и вставьте поле NUMPAGES, которое показывает общее количество
      страниц.
    text: Запишите " of " и вставьте поле NUMPAGES, которое показывает общее количество
      страниц.
  - name: Сохраните документ в файл формата .docx.
    text: Сохраните документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: Нет. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` перемещает builder
      только в основной нижний колонтитул *первой* секции, поэтому поля вставляются
      только туда.
    question: Если в документе более одной секции, добавит ли этот код номера страниц
      в нижний колонтитул каждой секции?
  - answer: Установите `builder.ParagraphFormat.Alignment` в другое значение `ParagraphAlignment`
      (например, `ParagraphAlignment.Right`) перед записью полей.
    question: Как изменить выравнивание абзаца с номером страницы в нижнем колонтитуле?
  - answer: '`InsertField` принимает код поля и необязательный результат поля; передача
      `null` указывает Aspose.Words позволить Word вычислить результат во время выполнения.'
    question: Что представляет собой аргумент `null` в `InsertField("PAGE", null)`?
  - answer: Да — замените `HeaderFooterType.FooterPrimary` на `HeaderFooterType.HeaderPrimary`
      (или другой тип заголовка) перед вставкой полей.
    question: Могу ли я разместить те же поля "Page X of Y" в заголовке вместо нижнего
      колонтитула?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Вставьте автоматические номера страниц в нижний колонтитул Word
og_description: Пошаговый код для добавления «живых» номеров страниц в нижний колонтитул Word с помощью Aspose.Words for .NET.
og_image_alt: Руководство, показывающее, как добавить автоматические номера страниц в нижний колонтитул документа Word с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавьте номера страниц в нижний колонтитул документа Word с помощью Aspose.Words
В этом учебнике показано, как использовать Aspose.Words Document и DocumentBuilder для вставки автоматически обновляемых номеров страниц в основной нижний колонтитул документа Word. Добавляя номера страниц программно, вы обеспечиваете единообразную нумерацию по всему файлу без ручного редактирования. Пример кода готов к запуску в среде .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Если в документе более одной секции, добавит ли этот код номера страниц в нижний колонтитул каждой секции?**  
A: Нет. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` перемещает builder только в основной нижний колонтитул *первой* секции, поэтому поля вставляются только туда.

**Q: Как изменить выравнивание абзаца с номером страницы в нижнем колонтитуле?**  
A: Установите `builder.ParagraphFormat.Alignment` в другое значение `ParagraphAlignment` (например, `ParagraphAlignment.Right`) перед записью полей.

**Q: Что представляет собой аргумент `null` в `InsertField("PAGE", null)`?**  
A: `InsertField` принимает код поля и необязательный результат поля; передача `null` указывает Aspose.Words позволить Word вычислить результат во время выполнения.

**Q: Могу ли я разместить те же поля "Page X of Y" в заголовке вместо нижнего колонтитула?**  
A: Да — замените `HeaderFooterType.FooterPrimary` на `HeaderFooterType.HeaderPrimary` (или другой тип заголовка) перед вставкой полей.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}