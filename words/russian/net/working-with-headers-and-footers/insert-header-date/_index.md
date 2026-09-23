---
title: Вставка динамической даты в заголовок Word‑документа с помощью Aspose.Words for .NET
weight: 110
limit:
description: Узнайте, как добавить динамическое поле DATE в основной заголовок Word‑документа с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Узнайте, как добавить динамическое поле DATE в основной заголовок Word‑документа
    с помощью Aspose.Words for .NET.
  headline: Вставка динамической даты в заголовок Word‑документа с помощью Aspose.Words
    for .NET
  type: TechArticle
- description: Узнайте, как добавить динамическое поле DATE в основной заголовок Word‑документа
    с помощью Aspose.Words for .NET.
  name: Вставка динамической даты в заголовок Word‑документа с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте новый Document и DocumentBuilder для его редактирования.
    text: Создайте новый Document и DocumentBuilder для его редактирования.
  - name: Переместите курсор builder'а в основной заголовок, чтобы последующие вставки
      влияли на заголовок.
    text: Переместите курсор builder'а в основной заголовок, чтобы последующие вставки
      влияли на заголовок.
  - name: Запишите статическую метку и вставьте поле DATE, отформатированное как «MMMM
      d, yyyy», в заголовок, создавая динамическую дату.
    text: Запишите статическую метку и вставьте поле DATE, отформатированное как «MMMM
      d, yyyy», в заголовок, создавая динамическую дату.
  - name: Вернитесь к основному телу документа и добавьте примерный абзац, демонстрируя
      обычное содержание документа рядом с заголовком.
    text: Вернитесь к основному телу документа и добавьте примерный абзац, демонстрируя
      обычное содержание документа рядом с заголовком.
  - name: Сохраните документ в файл формата .docx.
    text: Сохраните документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: Вызов `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` позиционирует
      builder в существующий основной заголовок, а `Write`/`InsertField` просто добавляют
      текст к уже находящемуся содержимому; они не удаляют существующий контент.
    question: Что произойдёт, если документ уже имеет основной заголовок — перезапишет
      ли мой код его?
  - answer: Yes — modify the switch format in the field code passed to `InsertField`,
      e.g. `builder.InsertField(\"DATE \\\\@ \\\"yyyy-MM-dd\\\")` will produce a date
      like 2026-09-22.
    question: Могу ли я изменить формат даты, используемый полем DATE, и как это сделать?
  - answer: Замените `HeaderFooterType.HeaderPrimary` на `HeaderFooterType.HeaderFirst`
      при вызове `MoveToHeaderFooter`; остальная часть кода работает так же.
    question: Если мне нужно поле даты в заголовке первой страницы вместо основного
      заголовка, что мне делать?
  - answer: Поле вставляется только с переключателем `\\@`, который указывает Word
      отображать текущую дату каждый раз при обновлении поля (например, при открытии
      файла или при нажатии Ctrl+Alt+F9).
    question: Обновляется ли поле DATE автоматически, когда документ открывается позже?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Добавьте динамическую дату в заголовок Word
og_description: Пошаговое руководство по встраиванию живого поля даты в ваш заголовок Word с помощью Aspose.Words.
og_image_alt: Скриншот, показывающий, как вставить динамическое поле DATE в заголовок Word‑документа с использованием Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка динамической даты в заголовок Word‑документа с помощью Aspose.Words
Этот учебник демонстрирует, как использовать классы Document и DocumentBuilder в Aspose.Words for .NET для вставки динамического поля DATE в основной заголовок Word‑документа. Добавленное поле автоматически обновляется до текущей даты каждый раз при открытии документа, гарантируя, что ваш заголовок всегда отображает актуальную дату. Следуйте пошаговому коду, чтобы добавить поле и сохранить обновлённый файл.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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

**Q: Что произойдёт, если документ уже имеет основной заголовок — перезапишет ли мой код его?**  
A: Вызов `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` позиционирует builder в существующий основной заголовок, а `Write`/`InsertField` просто добавляют текст к уже находящемуся содержимому; они не удаляют существующий контент.

**Q: Могу ли я изменить формат даты, используемый полем DATE, и как это сделать?**  
A: Yes — modify the switch format in the field code passed to `InsertField`, e.g. `builder.InsertField(\"DATE \\\\@ \\\"yyyy-MM-dd\\\")` will produce a date like 2026-09-22.

**Q: Если мне нужно поле даты в заголовке первой страницы вместо основного заголовка, что мне делать?**  
A: Замените `HeaderFooterType.HeaderPrimary` на `HeaderFooterType.HeaderFirst` при вызове `MoveToHeaderFooter`; остальная часть кода работает так же.

**Q: Обновляется ли поле DATE автоматически, когда документ открывается позже?**  
A: Поле вставляется только с переключателем `\\@`, который указывает Word отображать текущую дату каждый раз при обновлении поля (например, при открытии файла или при нажатии Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}