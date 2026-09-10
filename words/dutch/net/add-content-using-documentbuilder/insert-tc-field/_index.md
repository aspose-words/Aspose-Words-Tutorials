---
title: Voeg een TC‑veld toe aan een Word‑document met Aspose.Words for .NET
weight: 310
limit:
description: Leer hoe je een TC‑veld in een nieuw Word‑document invoegt met Aspose.Words for .NET via DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg een TC‑veld toe aan een Word‑document met Aspose.Words
In deze interactieve tutorial leer je hoe je programmatically een TC‑veld—een verborgen markering die door Word’s indexeer‑ en inhoudsopgave‑functies wordt gebruikt—aan een vers nieuw document toevoegt met behulp van Aspose.Words for .NET. Door DocumentBuilder te gebruiken kun je het veld precies op de gewenste plaats plaatsen en vervolgens het bestand opslaan, klaar voor verdere verwerking.

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

**Q: Wat doet het \"TC\"‑veld dat wordt ingevoegd door `builder.InsertField(\"TC \\"Entry Text\" \\\\f t\")` eigenlijk in het Word‑document?**
A: Het maakt een inhoudsopgave‑item aan met de zichtbare tekst \"Entry Text\" en markeert het als een TC‑item (inhoudsopgave), die Word later kan gebruiken bij het genereren van een inhoudsopgave.

**Q: Wat is het doel van de `\\f t`‑schakelaar in de TC‑veld‑string?**
A: De `\\f t`‑schakelaar vertelt Word om het item te behandelen als een normale tekstinvoer (in tegenstelling tot een kop) en om het op te nemen in de inhoudsopgave wanneer deze wordt opgebouwd.

**Q: Kan ik meerdere TC‑velden met verschillende invoerteksten invoegen met dezelfde `DocumentBuilder`‑instantie?**
A: Ja; roep gewoon `builder.InsertField` opnieuw aan met een andere string, bijvoorbeeld `builder.InsertField(\"TC \\"Another Entry\" \\\\f t\")`, en elke aanroep voegt een nieuw TC‑veld in op de huidige cursorpositie.

**Q: Als ik de invoertekst dynamisch moet maken (bijv. vanuit een variabele), hoe moet ik de `InsertField`‑aanroep formatteren?**
A: Bouw de veld‑string met stringinterpolatie of `String.Format`, bijvoorbeeld: `string entry = \"Chapter 1\"; builder.InsertField($\"TC \\"{entry}\" \\\\f t\");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}