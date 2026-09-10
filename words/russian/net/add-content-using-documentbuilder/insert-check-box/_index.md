---
title: Добавьте поле формы с флажком в документ Word с помощью Aspose.Words for .NET
weight: 210
limit:
description: Узнайте, как программно добавить поле формы с флажком в новый документ Word с помощью Aspose.Words for .NET и сохранить файл.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавьте поле формы с флажком в документ Word с помощью Aspose.Words
Этот учебник показывает, как создать новый документ Word и использовать DocumentBuilder из Aspose.Words for .NET для вставки поля формы с флажком. Следуя инструкциям, вы увидите точный код, необходимый для добавления интерактивного элемента, а затем сохраните документ в файл. Это быстрый способ программно создавать простые Word‑файлы с поддержкой форм.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Что обозначает четвёртый аргумент (0) в InsertCheckBox?**
A: Он задаёт визуальный размер флажка в пунктах; значение 0 указывает Aspose.Words использовать размер по умолчанию.

**Q: Можно ли вставить более одного флажка с одинаковым именем?**
A: Нет — имя каждого поля формы должно быть уникальным; попытка вставить ещё один флажок с именем "CheckBox" вызовет ArgumentException.

**Q: Как добавить флажок в существующий документ, а не в новый?**
A: Сначала загрузите документ (например, `Document doc = new Document("Existing.docx");`), затем создайте DocumentBuilder для этого документа и вызовите `InsertCheckBox` в нужной позиции курсора.

**Q: Как прочитать состояние вставленного флажка после сохранения документа?**
A: Получите поле формы через `doc.Range.FormFields["CheckBox"]` и проверьте его свойство `Checked`, чтобы увидеть, отмечено ли оно.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}