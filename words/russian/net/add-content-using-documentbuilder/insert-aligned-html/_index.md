---
title: Вставка выровненного HTML в документ Word с помощью Aspose.Words for .NET
weight: 210
limit:
description: Узнайте, как вставлять HTML с определённым выравниванием в документ Word с помощью Aspose.Words for .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка выровненного HTML в документ Word с помощью Aspose.Words
В этом учебнике показано, как использовать DocumentBuilder из Aspose.Words for .NET для внедрения HTML‑разметки в документ Word и управления её выравниванием. Вы увидите, как вставлять HTML, задавать выравнивание абзаца (по левому, центру или правому краю) и затем сохранять полученный документ. Пример идеально подходит для разработчиков, которым необходимо сохранять веб‑стиль форматирования при программной генерации файлов Word.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Можно ли использовать InsertHtml для добавления HTML в существующий документ Word, а не в новый?**
A: Да. Создайте Document из существующего файла, переместите курсор DocumentBuilder в место, где нужно вставить HTML (например, с помощью builder.MoveToDocumentEnd()), а затем вызовите builder.InsertHtml с вашей разметкой.

**Q: Какие атрибуты HTML учитываются InsertHtml при выравнивании?**
A: InsertHtml учитывает атрибут \"align\" у блочных элементов, таких как <p>, <div> и теги заголовков, применяя соответствующее выравнивание абзаца в полученном документе Word.

**Q: Что происходит, если строка HTML содержит неподдерживаемые теги или CSS?**
A: Неподдерживаемые теги игнорируются, а их внутренний текст вставляется как обычный текст; встроенные стили CSS, которые Aspose.Words не распознаёт, также игнорируются, поэтому рендерится только поддерживаемый набор HTML.

**Q: Нужно ли закрывать DocumentBuilder перед сохранением документа?**
A: Явное закрытие не требуется; после вставки HTML вы можете сразу вызвать doc.Save с нужным именем файла и форматом, а ресурсы builder освобождаются автоматически.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}