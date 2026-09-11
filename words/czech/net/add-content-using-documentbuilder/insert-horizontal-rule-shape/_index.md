---
title: Vložení tvaru vodorovné čáry do Word dokumentu pomocí Aspose.Words pro .NET
weight: 110
limit:
description: Naučte se přidat tvar vodorovné čáry do Word dokumentu pomocí Aspose.Words pro .NET a DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení tvaru vodorovné čáry do Word dokumentu pomocí Aspose.Words pro .NET
V tomto tutoriálu se naučíte, jak programově vložit tvar vodorovné čáry do Word dokumentu pomocí Aspose.Words pro .NET. Pomocí tříd Document a DocumentBuilder vytvoříme nový dokument, přidáme odstavec textu a poté umístíme tvar vodorovné čáry na požadované místo. Vodorovná čára poskytuje vizuální oddělovač, který může být užitečný pro oddělení sekcí nebo vizuální zdůraznění.

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

**Q: Kde přesně metoda `builder.InsertHorizontalRule()` umístí čáru v dokumentu?**  
A: `InsertHorizontalRule` vloží tvar vodorovné čáry na aktuální pozici kurzoru v `DocumentBuilder`; pokud ji chcete na samostatném řádku, zavolejte před vložením `builder.Writeln()`.

**Q: Mohu změnit tloušťku, barvu nebo šířku vložené vodorovné čáry?**  
A: `InsertHorizontalRule` přidá výchozí styl čáry a neumožňuje nastavení formátování; pokud chcete tyto vlastnosti upravit, musíte ručně vložit `Shape` (např. `builder.InsertShape(ShapeType.HorizontalLine)`) a následně nastavit jeho vlastnosti `LineFormat`.

**Q: Je možné přidat více než jednu vodorovnou čáru do stejného dokumentu?**  
A: Ano – stačí zavolat `builder.InsertHorizontalRule()` pokaždé, když potřebujete novou čáru; každý volání vytvoří samostatný tvar na aktuální pozici builderu.

**Q: Bude vodorovná čára viditelná, když se uložený .docx otevře v Microsoft Wordu?**  
A: Rozhodně; čára je uložena jako tvar uvnitř souboru .docx, takže Word ji zobrazí přesně tak, jak se objeví v vygenerovaném dokumentu.

**Q: Co se stane, pokud složka `dataDir` neexistuje před voláním `doc.Save(...)`?**  
A: `doc.Save` vyhodí výjimku `DirectoryNotFoundException`; ujistěte se, že cílový adresář existuje, nebo jej vytvořte programově před uložením.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}