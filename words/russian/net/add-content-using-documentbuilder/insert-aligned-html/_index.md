---
title: Вставка выровненного HTML в документ Word с помощью Aspose.Words for .NET
weight: 210
limit:
description: Научитесь вставлять необработанный HTML с выравниванием влево, по центру или вправо в документ Word с использованием Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка выровненного HTML в документ Word с помощью Aspose.Words
Этот интерактивный учебник показывает, как встроить необработанный HTML в документ Word, управляя его выравниванием — влево, по центру или вправо — с помощью Aspose.Words for .NET. Используя Document и DocumentBuilder, вы можете вставить строку HTML и задать нужное выравнивание абзаца всего в нескольких строках кода. Пример идеален, когда необходимо сохранить форматирование HTML и точно разместить содержимое в документе.

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

**Q: Что произойдёт, если строка HTML, передаваемая в DocumentBuilder.InsertHtml, содержит теги, которые Aspose.Words не поддерживает, например <script> или <iframe>?**
A: Неподдерживаемые теги игнорируются; Aspose.Words разбирает только тот набор HTML, который может отобразить, поэтому <script>, <iframe> и аналогичные элементы удаляются, а остальное содержимое вставляется.

**Q: Будут ли сохраняться встроенные стили CSS (например, <span style=\"color:red;\">) при использовании InsertHtml?**
A: Да, InsertHtml учитывает многие встроенные свойства CSS, такие как color, font-size и background, преобразуя их в соответствующее форматирование Word.

**Q: Создаёт ли InsertHtml автоматически новый абзац для блочных элементов, таких как <div> или <h1>?**
A: Блочные элементы сопоставляются с абзацами Word, поэтому каждый <div>, <p>, <h1> и т.п. превращается в отдельный абзац в документе.

**Q: Как вставить HTML в определённое место существующего документа, а не в начало?**
A: Переместите курсор DocumentBuilder к нужному узлу (например, builder.MoveToDocumentEnd() или builder.MoveToParagraph(index)) перед вызовом InsertHtml; HTML будет вставлен в текущую позицию курсора.

**Q: Если документ уже содержит текст, перезапишет ли вызов InsertHtml существующее содержимое?**
A: Нет, InsertHtml вставляет разобранный HTML в текущую позицию builder без удаления существующих узлов, если только вы явно не переместите курсор в эти узлы или не удалите их заранее.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}