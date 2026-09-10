---
title: Вставка формы горизонтального правила в документ Word с помощью Aspose.Words for .NET
weight: 110
limit:
description: Научитесь добавлять форму горизонтального правила в документ Word с помощью Aspose.Words for .NET, используя DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка формы горизонтального правила в документ Word с помощью Aspose.Words
В этом учебнике вы узнаете, как программно вставить форму горизонтального правила в документ Word с помощью Aspose.Words for .NET. С помощью классов Document и DocumentBuilder мы создаём новый документ, добавляем абзац текста и затем размещаем форму горизонтальной линии в нужном месте. Горизонтальное правило служит визуальным разделителем, который может быть полезен для разрывов разделов или визуального акцента.

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

**Q: Где именно `builder.InsertHorizontalRule()` размещает линию в документе?**
A: `InsertHorizontalRule` вставляет форму горизонтального правила в текущую позицию курсора `DocumentBuilder`; если вы хотите, чтобы она находилась на отдельной строке, вызовите `builder.Writeln()` перед вставкой.

**Q: Могу ли я изменить толщину, цвет или ширину вставленного горизонтального правила?**
A: `InsertHorizontalRule` добавляет правило со стилем по умолчанию и не предоставляет параметров форматирования; чтобы настроить эти свойства, необходимо вручную вставить `Shape` (например, `builder.InsertShape(ShapeType.HorizontalLine)`) и затем задать его свойства `LineFormat`.

**Q: Можно ли добавить более одного горизонтального правила в один документ?**
A: Да — просто вызывайте `builder.InsertHorizontalRule()` каждый раз, когда требуется новое правило; каждый вызов создаёт отдельную форму в текущем месте Builder.

**Q: Будет ли горизонтальное правило видно, когда сохранённый .docx откроется в Microsoft Word?**
A: Абсолютно; правило сохраняется как форма внутри файла .docx, поэтому Word отображает его точно так же, как оно выглядит в сгенерированном документе.

**Q: Что произойдёт, если папка `dataDir` не существует перед вызовом `doc.Save(...)`?**
A: `doc.Save` выбросит `DirectoryNotFoundException`; убедитесь, что целевая директория существует, или создайте её программно перед сохранением.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}