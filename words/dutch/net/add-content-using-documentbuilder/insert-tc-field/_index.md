---
title: TC‑veld invoegen in Word‑document met Aspose.Words for .NET
weight: 110
limit:
description: Leer hoe je een TC‑veld met aangepaste tekst in een Word‑document kunt invoegen met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# TC‑veld invoegen in Word‑document met Aspose.Words
Deze tutorial laat zien hoe je Aspose.Words for .NET gebruikt om een TC (Table of Contents)‑veld in een nieuw aangemaakt Word‑document in te voegen. Met DocumentBuilder kun je een TC‑veld met aangepaste invoertekst toevoegen, wat nuttig is voor het bouwen van een doorzoekbare index voor een inhoudsopgave. Het voorbeeld toont ook hoe je het document op schijf opslaat.

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

**Q: Wat betekent de "\f t"‑schakelaar in de TC‑veldcode?**
A: De "\f t"‑schakelaar vertelt Word om de invoer als een tabelinvoer te behandelen, waardoor deze verschijnt in een inhoudsopgave die is gegenereerd met de \f‑schakelaar.

**Q: Hoe kan ik de tekst die in het TC‑veld verschijnt wijzigen?**
A: Vervang "Entry Text" in de InsertField‑aanroep door een willekeurige tekenreeks, bijvoorbeeld: builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Kan ik meerdere TC‑velden in hetzelfde document invoegen?**
A: Ja; roep gewoon builder.InsertField aan met verschillende invoerteksten op de gewenste locaties voordat je het document opslaat.

**Q: Werkt deze code voor andere formaten dan .docx, zoals .pdf?**
A: Het document wordt in het voorbeeld opgeslagen als .docx, maar Aspose.Words kan naar andere formaten opslaan (bijv. .pdf) door de bestandsextensie in doc.Save te wijzigen en te zorgen dat het betreffende uitvoerformaat wordt ondersteund.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}