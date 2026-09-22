---
title: Вставка разрыва страницы в документ Word с помощью Aspose.Words for .NET
weight: 110
limit:
description: Научитесь добавлять разрывы страниц в файл Word с помощью Aspose.Words for .NET, используя Document и DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка разрыва страницы в документ Word с помощью Aspose.Words
В этом интерактивном учебнике вы узнаете, как программно добавлять разрывы страниц в документ Word с помощью Aspose.Words for .NET. Создавая объект Document и используя DocumentBuilder, вы можете управлять тем, где начинаются новые страницы, что важно для форматирования отчётов, счетов‑фактур или любого многоразделного документа. Следуйте пошаговому примеру, чтобы увидеть код в действии и просмотреть полученный файл.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: Могу ли я использовать InsertBreak для добавления разрыва строки или разрыва раздела вместо разрыва страницы?**
A: Да, InsertBreak принимает любое значение перечисления BreakType, например BreakType.LineBreak или BreakType.SectionBreakContinuous, чтобы вставить соответствующий разрыв.

**Q: Нужно ли вызывать InsertBreak до или после записи текста для новой страницы?**
A: InsertBreak следует вызывать после содержимого, которое должно остаться на текущей странице; следующая команда Writeln тогда начнёт запись на новой странице, созданной разрывом.

**Q: Что произойдёт, если путь dataDir не заканчивается разделителем каталогов?**
A: Если в dataDir отсутствует завершающий слеш, имя файла будет присоединено напрямую (например, "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), что может привести к недопустимому пути; убедитесь, что путь заканчивается "\\" или используйте Path.Combine.

**Q: Можно ли повторно использовать один и тот же экземпляр DocumentBuilder для вставки нескольких разрывов по всему документу?**
A: Да, один и тот же DocumentBuilder можно использовать многократно; каждый вызов InsertBreak вставляет разрыв в текущую позицию курсора builder'а.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}