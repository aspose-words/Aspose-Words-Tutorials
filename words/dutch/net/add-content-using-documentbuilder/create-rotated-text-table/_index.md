---
title: Maak een gedraaide‑tekst‑tabel in een Word‑document met Aspose.Words voor .NET
weight: 110
limit:
description: Leer een Word‑tabel te bouwen met vaste kolombreedtes, gedraaide tekst, precieze rijhoogtes en gevulde cellen met behulp van Aspose.Words voor .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Leer een Word‑tabel te bouwen met vaste kolombreedtes, gedraaide tekst,
    precieze rijhoogtes en gevulde cellen met behulp van Aspose.Words voor .NET.
  headline: Maak een gedraaide‑tekst‑tabel in een Word‑document met Aspose.Words voor
    .NET
  type: TechArticle
- description: Leer een Word‑tabel te bouwen met vaste kolombreedtes, gedraaide tekst,
    precieze rijhoogtes en gevulde cellen met behulp van Aspose.Words voor .NET.
  name: Maak een gedraaide‑tekst‑tabel in een Word‑document met Aspose.Words voor
    .NET
  steps:
  - name: Instantieer een nieuw Document en een DocumentBuilder die worden gebruikt
      om de tabel te construeren.
    text: Instantieer een nieuw Document en een DocumentBuilder die worden gebruikt
      om de tabel te construeren.
  - name: Start een nieuwe tabel, voeg de eerste cel in en fixeër de kolombreedtes
      zodat ze niet automatisch worden aangepast.
    text: Start een nieuwe tabel, voeg de eerste cel in en fixeër de kolombreedtes
      zodat ze niet automatisch worden aangepast.
  - name: Centreer de inhoud verticaal in de huidige cel en schrijf de tekst van de
      eerste cel van de eerste rij.
    text: Centreer de inhoud verticaal in de huidige cel en schrijf de tekst van de
      eerste cel van de eerste rij.
  - name: Voeg de tweede cel van de eerste rij in en schrijf de tekst ervan.
    text: Voeg de tweede cel van de eerste rij in en schrijf de tekst ervan.
  - name: Sluit de eerste rij, waarmee de lay-out wordt afgerond.
    text: Sluit de eerste rij, waarmee de lay-out wordt afgerond.
  - name: Start de eerste cel van de tweede rij, stel de rijhoogte in op exact 100
      punten, roteer de tekst naar boven en schrijf de tekst van de cel.
    text: Start de eerste cel van de tweede rij, stel de rijhoogte in op exact 100
      punten, roteer de tekst naar boven en schrijf de tekst van de cel.
  - name: Voeg de tweede cel van de tweede rij in, roteer de tekst naar beneden en
      schrijf de tekst van de cel.
    text: Voeg de tweede cel van de tweede rij in, roteer de tekst naar beneden en
      schrijf de tekst van de cel.
  - name: Sluit de tweede rij, waarmee de tweede regel van de tabel wordt voltooid.
    text: Sluit de tweede rij, waarmee de tweede regel van de tabel wordt voltooid.
  - name: Beëindig de constructie van de tabel, waardoor de tabelstructuur wordt afgesloten.
    text: Beëindig de constructie van de tabel, waardoor de tabelstructuur wordt afgesloten.
  - name: Sla het voltooide document op als een .docx‑bestand.
    text: Sla het voltooide document op als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: Na het fixeren van de kolombreedtes, ken een breedte toe aan elke cel
      met `builder.CellFormat.Width = <valueInPoints>;` voordat u de volgende cel
      invoegt; de tabel behoudt die exacte breedtes.
    question: Hoe kan ik specifieke kolombreedtes instellen nadat ik `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`
      heb aangeroepen?
  - answer: '`builder.CellFormat.VerticalAlignment` is een cel‑niveau instelling,
      dus u moet deze opnieuw instellen voor de cellen in de tweede rij (bijv. `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) voordat u hun inhoud schrijft.'
    question: Waarom heeft de verticale uitlijning alleen effect op de eerste rij
      en niet op de tweede rij?
  - answer: Ja—stel `builder.RowFormat.Height` en `builder.RowFormat.HeightRule =
      HeightRule.Exactly` in vóór elke `builder.EndRow();`‑aanroep; de volgende rij
      kan een andere hoogtewaarde hebben.
    question: Kan ik elke rij een andere exacte hoogte geven, en zo ja, hoe?
  - answer: Reset de oriëntatie door `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      toe te wijzen voordat u naar de volgende cel schrijft.
    question: Hoe zet ik de tekstoriëntatie terug naar de standaard nadat ik `TextOrientation.Upward`
      of `Downward` heb gebruikt?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Maak een gedraaide‑tekst‑tabel in Word met Aspose.Words
og_description: Stapsgewijze code om een tabel met vaste breedte te bouwen met verticaal gedraaide tekst en exacte rijhoogtes.
og_image_alt: Schermafbeelding die een Word‑document toont met een tabel die vaste kolombreedtes, gedraaide tekst in cellen en gedefinieerde rijhoogtes heeft, gemaakt met Aspose.Words voor .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Maak een gedraaide‑tekst‑tabel in een Word‑document met Aspose.Words voor .NET
Deze tutorial laat zien hoe u een Word‑document genereert en een tabel toevoegt waarvan de kolommen vaste breedtes hebben, de rijen exacte hoogtes, en de celtekst verticaal gedraaid is. U leert verticale uitlijning in te stellen, tekstoriëntatie toe te passen, elke cel met inhoud te vullen en uiteindelijk het document op te slaan — alles met Aspose.Words voor .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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

**Q: Hoe kan ik specifieke kolombreedtes instellen nadat ik `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` heb aangeroepen?**  
A: Na het fixeren van de kolombreedtes, ken een breedte toe aan elke cel met `builder.CellFormat.Width = <valueInPoints>;` voordat u de volgende cel invoegt; de tabel behoudt die exacte breedtes.

**Q: Waarom heeft de verticale uitlijning alleen effect op de eerste rij en niet op de tweede rij?**  
A: `builder.CellFormat.VerticalAlignment` is een cel‑niveau instelling, dus u moet deze opnieuw instellen voor de cellen in de tweede rij (bijv. `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) voordat u hun inhoud schrijft.

**Q: Kan ik elke rij een andere exacte hoogte geven, en zo ja, hoe?**  
A: Ja—stel `builder.RowFormat.Height` en `builder.RowFormat.HeightRule = HeightRule.Exactly` in vóór elke `builder.EndRow();`‑aanroep; de volgende rij kan een andere hoogtewaarde hebben.

**Q: Hoe zet ik de tekstoriëntatie terug naar de standaard nadat ik `TextOrientation.Upward` of `Downward` heb gebruikt?**  
A: Reset de oriëntatie door `builder.CellFormat.Orientation = TextOrientation.Horizontal;` toe te wijzen voordat u naar de volgende cel schrijft.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}