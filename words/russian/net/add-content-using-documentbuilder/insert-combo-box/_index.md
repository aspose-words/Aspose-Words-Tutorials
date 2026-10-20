---
title: Добавьте поле формы Combo Box в документ Word с помощью Aspose.Words for .NET
weight: 310
limit:
description: Узнайте, как добавить поле формы комбо‑бокс с предопределёнными элементами в документ Word с помощью Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавьте поле формы Combo Box в документ Word с помощью Aspose.Words
В этом учебнике показано, как использовать DocumentBuilder из Aspose.Words for .NET для создания нового документа Word и вставки поля формы‑комбо‑бокс, заполненного предопределёнными элементами. Следуя пошаговому коду, вы увидите, как настроить варианты комбо‑бокса и затем сохранить документ для использования в интерактивных формах.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: Что представляет собой массив `items`, передаваемый в `InsertComboBox`?**
A: Он определяет список строк, которые отображаются как варианты выбора в выпадающем списке комбо‑бокса.

**Q: Как изменить элемент, выбранный по умолчанию, при открытии документа?**
A: Установите третий аргумент (`selectedIndex`) метода `InsertComboBox` в нулевой индекс желаемого элемента по умолчанию (например, `2` для "Three").

**Q: Можно ли разместить комбо‑бокс в определённом месте документа?**
A: Да — переместите курсор `DocumentBuilder` в нужное место с помощью методов, таких как `MoveToParagraph`, `InsertParagraph` или `Write`, перед вызовом `InsertComboBox`.

**Q: Какой формат файла создаётся этим кодом и можно ли открыть его в более старых версиях Word?**
A: Код сохраняет файл `.docx`, который может быть открыт в Word 2007 и более новых версиях, а также в любом приложении, поддерживающем формат OpenXML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}