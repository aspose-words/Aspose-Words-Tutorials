---
title: Voeg een Check Box Form Field toe aan een Word-document met Aspose.Words for .NET
weight: 210
limit:
description: Leer hoe je via code een selectievakje-formulierveld toevoegt aan een nieuw Word-document met Aspose.Words for .NET en het bestand opslaat.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg een Check Box Form Field toe aan een Word-document met Aspose.Words
Deze tutorial laat zien hoe je een nieuw Word-document maakt en de DocumentBuilder van Aspose.Words for .NET gebruikt om een selectievakje-formulierveld in te voegen. Door de stappen te volgen, zie je de exacte code die nodig is om het interactieve element toe te voegen en vervolgens het document naar een bestand op te slaan. Het is een snelle manier om via code eenvoudige, formulier‑ondersteunde Word‑bestanden te bouwen.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Wat stelt het vierde argument (0) in InsertCheckBox voor?**
A: Het geeft de visuele grootte van het selectievakje in punten aan; een waarde van 0 vertelt Aspose.Words de standaardgrootte te gebruiken.

**Q: Kan ik meer dan één selectievakje met dezelfde naam invoegen?**
A: Nee – elke naam van een formulierveld moet uniek zijn; proberen een ander selectievakje met de naam \"CheckBox\" in te voegen zal een ArgumentException veroorzaken.

**Q: Hoe voeg ik een selectievakje toe aan een bestaand document in plaats van aan een nieuw document?**
A: Laad eerst het document (bijv. `Document doc = new Document(\"Existing.docx\");`) en maak vervolgens een DocumentBuilder voor dat document en roep `InsertCheckBox` aan op de gewenste cursorpositie.

**Q: Hoe kan ik de status van het ingevoegde selectievakje lezen nadat het document is opgeslagen?**
A: Haal het formulierveld op via `doc.Range.FormFields[\"CheckBox\"]` en inspecteer de `Checked`‑eigenschap om te zien of het aangevinkt was.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}