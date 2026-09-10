---
title: Вставка поля TC в документ Word с использованием Aspose.Words for .NET
weight: 110
limit:
description: Узнайте, как вставить поле TC с пользовательским текстом в документ Word с помощью Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Вставка поля TC в документ Word с использованием Aspose.Words
В этом учебном материале показано, как использовать Aspose.Words for .NET для вставки поля TC (Table of Contents) в только что созданный документ Word. С помощью DocumentBuilder можно добавить поле TC с пользовательским текстом записи, что полезно для создания поискового индекса оглавления. Пример также демонстрирует сохранение документа на диск.

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

**Q: Что означает переключатель "\f t" в коде поля TC?**
A: Переключатель "\f t" указывает Word рассматривать запись как табличную, что заставляет её появляться в оглавлении, сгенерированном с помощью переключателя \f.

**Q: Как изменить текст, отображаемый в поле TC?**
A: Замените "Entry Text" в вызове InsertField любой желаемой строкой, например, builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Можно ли вставить несколько полей TC в один документ?**
A: Да; просто вызовите builder.InsertField с разными текстами записей в нужных местах перед сохранением документа.

**Q: Работает ли этот код с форматами, отличными от .docx, например .pdf?**
A: В примере документ сохраняется как .docx, но Aspose.Words может сохранять в другие форматы (например, .pdf), изменив расширение файла в doc.Save и убедившись, что соответствующий формат вывода поддерживается.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}