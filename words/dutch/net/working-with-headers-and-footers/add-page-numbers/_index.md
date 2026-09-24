---
title: Voeg paginanummers toe aan de voettekst van een Word‑document met Aspose.Words voor .NET
weight: 210
limit:
description: Voeg automatisch bijgewerkte paginanummers toe aan de primaire voettekst van een Word‑document met Aspose.Words voor .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Voeg automatisch bijgewerkte paginanummers toe aan de primaire voettekst
    van een Word‑document met Aspose.Words voor .NET.
  headline: Voeg paginanummers toe aan de voettekst van een Word‑document met Aspose.Words
    voor .NET
  type: TechArticle
- description: Voeg automatisch bijgewerkte paginanummers toe aan de primaire voettekst
    van een Word‑document met Aspose.Words voor .NET.
  name: Voeg paginanummers toe aan de voettekst van een Word‑document met Aspose.Words
    voor .NET
  steps:
  - name: Maak een nieuw Document‑object en een DocumentBuilder die eraan gekoppeld
      is.
    text: Maak een nieuw Document‑object en een DocumentBuilder die eraan gekoppeld
      is.
  - name: Verplaats de cursor van de builder naar de primaire voettekst van de eerste
      sectie.
    text: Verplaats de cursor van de builder naar de primaire voettekst van de eerste
      sectie.
  - name: Stel de alinea‑uitlijning in op centreren zodat de voetteksttekst gecentreerd
      wordt.
    text: Stel de alinea‑uitlijning in op centreren zodat de voetteksttekst gecentreerd
      wordt.
  - name: Schrijf het label "Page " en voeg een PAGE‑veld in dat het huidige paginanummer
      weergeeft.
    text: Schrijf het label "Page " en voeg een PAGE‑veld in dat het huidige paginanummer
      weergeeft.
  - name: Schrijf " of " en voeg een NUMPAGES‑veld in dat het totale aantal pagina's
      toont.
    text: Schrijf " of " en voeg een NUMPAGES‑veld in dat het totale aantal pagina's
      toont.
  - name: Sla het document op als een .docx‑bestand.
    text: Sla het document op als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: Nee. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` verplaatst de
      builder alleen naar de primaire voettekst van de *eerste* sectie, zodat de velden
      daar alleen worden ingevoegd.
    question: Als het document meer dan één sectie heeft, voegt deze code dan paginanummers
      toe aan de voettekst van elke sectie?
  - answer: Stel `builder.ParagraphFormat.Alignment` in op een andere `ParagraphAlignment`‑waarde
      (bijv. `ParagraphAlignment.Right`) voordat je de velden schrijft.
    question: Hoe kan ik de uitlijning van de paginanummer‑alinea in de voettekst
      wijzigen?
  - answer: '`InsertField` neemt de veldcode en een optioneel veldresultaat; door
      `null` door te geven, wordt Aspose.Words verteld Word het resultaat tijdens
      runtime te laten berekenen.'
    question: Wat stelt het `null`‑argument in `InsertField("PAGE", null)` voor?
  - answer: Ja—vervang `HeaderFooterType.FooterPrimary` door `HeaderFooterType.HeaderPrimary`
      (of een ander kopteksttype) voordat je de velden invoegt.
    question: Kan ik dezelfde "Page X of Y"‑velden in de koptekst in plaats van de
      voettekst plaatsen?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Automatische paginanummers invoegen in Word‑voettekst
og_description: Stapsgewijze code om live paginanummers toe te voegen aan een Word‑voettekst met Aspose.Words voor .NET.
og_image_alt: Gids die laat zien hoe je automatische paginanummers toevoegt aan de voettekst van een Word‑document met Aspose.Words voor .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg paginanummers toe aan de voettekst van een Word‑document met Aspose.Words voor .NET
Deze tutorial laat zien hoe je Aspose.Words Document en DocumentBuilder gebruikt om automatisch bijgewerkte paginanummers in te voegen in de primaire voettekst van een Word‑document. Door paginanummers programmatisch toe te voegen, zorg je voor consistente paginering in het hele bestand zonder handmatige bewerking. De voorbeeldcode is klaar om uitgevoerd te worden in een .NET‑omgeving.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Als het document meer dan één sectie heeft, voegt deze code dan paginanummers toe aan de voettekst van elke sectie?**  
A: Nee. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` verplaatst de builder alleen naar de primaire voettekst van de *eerste* sectie, zodat de velden daar alleen worden ingevoegd.

**Q: Hoe kan ik de uitlijning van de paginanummer‑alinea in de voettekst wijzigen?**  
A: Stel `builder.ParagraphFormat.Alignment` in op een andere `ParagraphAlignment`‑waarde (bijv. `ParagraphAlignment.Right`) voordat je de velden schrijft.

**Q: Wat stelt het `null`‑argument in `InsertField("PAGE", null)` voor?**  
A: `InsertField` neemt de veldcode en een optioneel veldresultaat; door `null` door te geven, wordt Aspose.Words verteld Word het resultaat tijdens runtime te laten berekenen.

**Q: Kan ik dezelfde "Page X of Y"‑velden in de koptekst in plaats van de voettekst plaatsen?**  
A: Ja—vervang `HeaderFooterType.FooterPrimary` door `HeaderFooterType.HeaderPrimary` (of een ander kopteksttype) voordat je de velden invoegt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}