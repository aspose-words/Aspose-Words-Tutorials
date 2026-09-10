---
title: Вставка формы горизонтальной линии в документ Word с помощью Aspose.Words for .NET
weight: 110
limit:
description: Пошаговое руководство по вставке формы горизонтальной линии в документ Word с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка формы горизонтальной линии в документ Word с помощью Aspose.Words
Узнайте, как использовать Aspose.Words for .NET для вставки формы горизонтальной линии в документ Word. Это руководство проведёт вас через создание нового документа, добавление строки текста, размещение формы горизонтальной линии с помощью DocumentBuilder и сохранение файла. Горизонтальная линия служит простым визуальным разделителем вашего контента.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Можно ли изменить внешний вид (цвет, толщину) горизонтальной линии, вставленной с помощью DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule создаёт встроенную форму горизонтальной линии с форматированием по умолчанию; чтобы изменить её внешний вид, необходимо получить вставленный объект Shape (builder.CurrentParagraph.LastChild) и скорректировать свойства LineFormat.

**Q: Что произойдёт, если вызвать InsertHorizontalRule() после абзаца, который уже заканчивается разрывом строки?**
A: Метод вставляет линию как отдельный абзац, поэтому любой предшествующий разрыв строки просто создаёт пустой абзац перед линией; линия всё равно будет отображаться на своей отдельной строке.

**Q: Можно ли вставить более одной горизонтальной линии в один документ с помощью DocumentBuilder?**
A: Да, каждый вызов builder.InsertHorizontalRule() добавляет новую форму горизонтальной линии в текущую позицию курсора, позволяя размещать несколько линий в документе.

**Q: Работает ли InsertHorizontalRule() при сохранении документа в форматы, отличные от DOCX, например PDF?**
A: Горизонтальная линия хранится как форма в модели документа, поэтому при сохранении в PDF, XPS или другие поддерживаемые форматы линия корректно отображается в результате.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}