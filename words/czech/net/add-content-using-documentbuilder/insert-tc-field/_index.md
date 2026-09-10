---
title: Vložení pole TC do dokumentu Word pomocí Aspose.Words for .NET
weight: 110
limit:
description: Naučte se, jak vložit pole TC s vlastním textem do dokumentu Word pomocí Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení pole TC do dokumentu Word pomocí Aspose.Words
Tento tutoriál ukazuje, jak pomocí Aspose.Words for .NET vložit pole TC (Table of Contents) do nově vytvořeného dokumentu Word. Pomocí DocumentBuilder můžete přidat pole TC s vlastním textem položky, což je užitečné pro vytvoření prohledávatelného rejstříku obsahu. Příklad také demonstruje uložení dokumentu na disk.

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

**Q: Co znamená přepínač "\f t" v kódu pole TC?**
A: Přepínač "\f t" říká Wordu, aby položku považoval za položku tabulky, což způsobí, že se objeví v obsahu vytvořeném pomocí přepínače \f.

**Q: Jak mohu změnit text, který se zobrazuje v poli TC?**
A: Nahraďte "Entry Text" v volání InsertField libovolným řetězcem, který chcete, např. builder.InsertField(\"TC \\"Chapter 1\" \\f t\");

**Q: Mohu vložit více polí TC do stejného dokumentu?**
A: Ano; stačí zavolat builder.InsertField s různými texty položek na požadovaných místech před uložením dokumentu.

**Q: Funguje tento kód i pro jiné formáty než .docx, například .pdf?**
A: V příkladu je dokument uložen jako .docx, ale Aspose.Words může ukládat do jiných formátů (např. .pdf) změnou přípony souboru v doc.Save a zajištěním, že je podporován požadovaný výstupní formát.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}