---
title: Добавьте поле TC в документ Word с помощью Aspose.Words for .NET
weight: 310
limit:
description: Научитесь вставлять поле TC в новый документ Word с помощью Aspose.Words for .NET, используя DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавьте поле TC в документ Word с помощью Aspose.Words
В этом интерактивном учебнике вы узнаете, как программно добавить поле TC — скрытый маркер, используемый функциями индексации и оглавления Word — в только что созданный документ с помощью Aspose.Words for .NET. С помощью DocumentBuilder вы можете разместить поле точно там, где нужно, а затем сохранить файл, готовый к дальнейшей обработке.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: Что фактически делает поле "TC", вставленное с помощью `builder.InsertField("TC \"Entry Text\" \\f t")`, в документе Word?**
A: Оно создаёт запись в оглавлении с видимым текстом "Entry Text" и помечает её как запись TC (Table of Contents), которую Word позже может использовать при построении оглавления.

**Q: Какова цель переключателя `\f t` в строке поля TC?**
A: Переключатель `\f t` указывает Word рассматривать запись как обычный текст (в отличие от заголовка) и включать её в оглавление при его построении.

**Q: Могу ли я вставлять несколько полей TC с разными текстами записей, используя один и тот же экземпляр `DocumentBuilder`?**
A: Да; просто вызовите `builder.InsertField` ещё раз с другой строкой, например `builder.InsertField("TC \"Another Entry\" \\f t")`, и каждый вызов вставит новое поле TC в текущую позицию курсора.

**Q: Если мне нужен динамический текст записи (например, из переменной), как следует оформить вызов `InsertField`?**
A: Сформируйте строку поля с помощью интерполяции строк или `String.Format`, например: `string entry = "Chapter 1"; builder.InsertField($"TC \"{entry}\" \\f t");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}