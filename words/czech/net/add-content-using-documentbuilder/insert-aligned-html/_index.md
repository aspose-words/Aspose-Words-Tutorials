---
title: Vložení zarovnaného HTML do dokumentu Word pomocí Aspose.Words pro .NET
weight: 210
limit:
description: Naučte se, jak vložit HTML s konkrétním zarovnáním do dokumentu Word pomocí Aspose.Words pro .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení zarovnaného HTML do dokumentu Word pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak použít DocumentBuilder z Aspose.Words pro .NET k vložení HTML značek do dokumentu Word a řízení jejich zarovnání. Uvidíte, jak vložit HTML, nastavit zarovnání odstavce (vlevo, na střed nebo vpravo) a poté uložit výsledný dokument. Příklad je ideální pro vývojáře, kteří potřebují zachovat formátování ve stylu webu při programovém generování souborů Word.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: Lze InsertHtml použít k přidání HTML do existujícího dokumentu Word místo nového?**  
A: Ano. Vytvořte Document ze stávajícího souboru, umístěte kurzor DocumentBuilderu tam, kam chcete HTML vložit (např. pomocí builder.MoveToDocumentEnd()), a poté zavolejte builder.InsertHtml s vaším markupem.

**Q: Které HTML atributy jsou InsertHtml‑em respektovány pro zarovnání?**  
A: InsertHtml respektuje atribut "align" u blokových elementů, jako jsou &lt;p&gt;, &lt;div&gt; a nadpisové tagy, a použije odpovídající zarovnání odstavce ve výsledném dokumentu Word.

**Q: Co se stane, pokud řetězec HTML obsahuje nepodporované tagy nebo CSS?**  
A: Nepodporované tagy jsou ignorovány a jejich vnitřní text je vložen jako prostý text; inline CSS styly, které Aspose.Words nerozpozná, jsou také ignorovány, takže je vykreslena pouze podporovaná podmnožina HTML.

**Q: Musím před uložením dokumentu zavřít DocumentBuilder?**  
A: Explicitní zavření není potřeba; po vložení HTML můžete přímo zavolat doc.Save s požadovaným názvem souboru a formátem a prostředky builderu jsou uvolněny automaticky.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}