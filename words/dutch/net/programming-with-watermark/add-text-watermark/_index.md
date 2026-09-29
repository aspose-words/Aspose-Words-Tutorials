---
title: Rode diagonale tekstwatermark toevoegen aan Word‑documenten met Aspose.Words voor .NET
weight: 110
limit:
description: Pas automatisch een rode diagonale tekstwatermark toe op elk Word‑bestand dat in een batch wordt gegenereerd met Aspose.Words voor .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Pas automatisch een rode diagonale tekstwatermark toe op elk Word‑bestand
    dat in een batch wordt gegenereerd met Aspose.Words voor .NET.
  headline: Rode diagonale tekstwatermark toevoegen aan Word‑documenten met Aspose.Words
    voor .NET
  type: TechArticle
- description: Pas automatisch een rode diagonale tekstwatermark toe op elk Word‑bestand
    dat in een batch wordt gegenereerd met Aspose.Words voor .NET.
  name: Rode diagonale tekstwatermark toevoegen aan Word‑documenten met Aspose.Words
    voor .NET
  steps:
  - name: Doe de map "GeneratedReports" aan waar de uitvoerbestanden worden opgeslagen.
    text: Doe de map "GeneratedReports" aan waar de uitvoerbestanden worden opgeslagen.
  - name: Start een lus die drie afzonderlijke documenten genereert.
    text: Start een lus die drie afzonderlijke documenten genereert.
  - name: Maak een nieuw leeg Word‑documentobject aan.
    text: Maak een nieuw leeg Word‑documentobject aan.
  - name: Gebruik DocumentBuilder om een titelregel en een beschrijving in het document
      te schrijven.
    text: Gebruik DocumentBuilder om een titelregel en een beschrijving in het document
      te schrijven.
  - name: Definieer het uiterlijk van de watermark, inclusief lettertype, grootte,
      kleur en diagonale lay-out.
    text: Definieer het uiterlijk van de watermark, inclusief lettertype, grootte,
      kleur en diagonale lay-out.
  - name: Pas de geconfigureerde rode diagonale watermark met de tekst "PROTECTED"
      toe op het document.
    text: Pas de geconfigureerde rode diagonale watermark met de tekst "PROTECTED"
      toe op het document.
  - name: Sla het watergemerkte document op in de map "GeneratedReports" met een unieke
      bestandsnaam.
    text: Sla het watergemerkte document op in de map "GeneratedReports" met een unieke
      bestandsnaam.
  - name: Sluit de lus na het verwerken van het huidige document.
    text: Sluit de lus na het verwerken van het huidige document.
  type: HowTo
- questions:
  - answer: IsSemitrasparent bepaalt of de watermark met gedeeltelijke doorzichtigheid
      wordt gerenderd; het instellen op **true** maakt de tekst semi‑transparant zodat
      onderliggende inhoud beter leesbaar blijft.
    question: Wat regelt de optie **IsSemitrasparent** en welk effect heeft het instellen
      ervan op **true**?
  - answer: Ja—stel de eigenschap **Layout** in op **WatermarkLayout.Horizontal**
      in de **TextWatermarkOptions** voordat je **document.Watermark.SetText** aanroept.
    question: Kan ik de oriëntatie van de watermark wijzigen naar horizontaal in plaats
      van diagonaal?
  - answer: De code maakt een nieuw **Document**‑object aan, maar je kunt elk bestaand
      bestand openen (bijv. `new Document("Existing.docx")`) en vervolgens **document.Watermark.SetText**
      aanroepen om dezelfde watermark toe te passen.
    question: Voegt deze code een watermark toe aan een bestaand Word‑bestand, of
      alleen aan nieuw aangemaakte documenten?
  - answer: Wijs een aangepaste kleur toe met **Color.FromArgb(red, green, blue)**
      aan de **Color**‑eigenschap van **TextWatermarkOptions**, bijv. `Color = Color.FromArgb(128,
      0, 128)` voor paars.
    question: Hoe kan ik een aangepaste RGB‑kleur voor de watermark gebruiken in plaats
      van de vooraf gedefinieerde **Color.Red**?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Voeg een rode diagonale tekstwatermark toe aan Word‑documenten
og_description: Bekijk hoe je een rode diagonale watermark automatisch toepast op elk Word‑document in een batch met Aspose.Words.
og_image_alt: Gids die laat zien hoe je een rode diagonale tekstwatermark toevoegt aan Word‑documenten met Aspose.Words voor .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rode diagonale tekstwatermark toevoegen aan Word‑documenten met Aspose.Words voor .NET
Deze tutorial demonstreert hoe je automatisch een rode diagonale tekstwatermark in elk Word‑document dat tijdens een batch‑rapportgeneratie wordt aangemaakt, kunt insluiten. Met behulp van de Document‑ en DocumentBuilder‑klassen van Aspose.Words voor .NET wordt de watermark programmatisch toegepast terwijl de bestanden worden gegenereerd, zodat elk document dezelfde branding of vertrouwelijkheidsmelding bevat zonder handmatige inspanning.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Wat regelt de optie **IsSemitrasparent** en welk effect heeft het instellen ervan op **true**?**  
A: IsSemitrasparent bepaalt of de watermark met gedeeltelijke doorzichtigheid wordt gerenderd; het instellen op **true** maakt de tekst semi‑transparant zodat onderliggende inhoud beter leesbaar blijft.

**Q: Kan ik de oriëntatie van de watermark wijzigen naar horizontaal in plaats van diagonaal?**  
A: Ja—stel de eigenschap **Layout** in op **WatermarkLayout.Horizontal** in de **TextWatermarkOptions** voordat je **document.Watermark.SetText** aanroept.

**Q: Voegt deze code een watermark toe aan een bestaand Word‑bestand, of alleen aan nieuw aangemaakte documenten?**  
A: De code maakt een nieuw **Document**‑object aan, maar je kunt elk bestaand bestand openen (bijv. `new Document("Existing.docx")`) en vervolgens **document.Watermark.SetText** aanroepen om dezelfde watermark toe te passen.

**Q: Hoe kan ik een aangepaste RGB‑kleur voor de watermark gebruiken in plaats van de vooraf gedefinieerde **Color.Red**?**  
A: Wijs een aangepaste kleur toe met **Color.FromArgb(red, green, blue)** aan de **Color**‑eigenschap van **TextWatermarkOptions**, bijv. `Color = Color.FromArgb(128, 0, 128)` voor paars.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}