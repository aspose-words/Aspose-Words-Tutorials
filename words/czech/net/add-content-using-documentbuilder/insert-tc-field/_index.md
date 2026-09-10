---
title: Přidejte pole TC do dokumentu Word pomocí Aspose.Words for .NET
weight: 310
limit:
description: Naučte se vložit pole TC do nového dokumentu Word pomocí Aspose.Words for .NET a DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidejte pole TC do dokumentu Word pomocí Aspose.Words
V tomto interaktivním tutoriálu se naučíte, jak programově přidat pole TC — skrytý značku používanou pro indexování a tvorbu obsahu ve Wordu — do nově vytvořeného dokumentu pomocí Aspose.Words for .NET. Pomocí DocumentBuilder můžete pole umístit přesně tam, kde jej potřebujete, a poté soubor uložit, připravený k dalšímu zpracování.

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

**Q: Co vlastně dělá pole "TC" vložené pomocí `builder.InsertField(\"TC \"Entry Text\" \\f t\")` ve Word dokumentu?**
A: Vytvoří položku obsahu s viditelným textem "Entry Text" a označí ji jako položku TC (Table of Contents), kterou Word později může použít při generování obsahu.

**Q: Jaký je účel přepínače `\\f t` v řetězci pole TC?**
A: Přepínač `\\f t` říká Wordu, aby položku považoval za běžný text (na rozdíl od nadpisu) a zahrnul ji do obsahu při jeho vytváření.

**Q: Mohu vložit více polí TC s různými texty položek pomocí stejné instance `DocumentBuilder`?**
A: Ano; stačí znovu zavolat `builder.InsertField` s jiným řetězcem, např. `builder.InsertField(\"TC \"Another Entry\" \\f t\")`, a každé volání vloží nové pole TC na aktuální pozici kurzoru.

**Q: Pokud potřebuji, aby text položky byl dynamický (např. z proměnné), jak mám naformátovat volání `InsertField`?**
A: Sestavte řetězec pole pomocí interpolace řetězce nebo `String.Format`, například: `string entry = \"Chapter 1\"; builder.InsertField($\"TC \"{entry}\" \\f t\");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}