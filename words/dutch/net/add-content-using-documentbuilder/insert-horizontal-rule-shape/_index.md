---
title: Horizontale Lijnvorm Invoegen in Word-document met Aspose.Words voor .NET
weight: 110
limit:
description: Stapsgewijze gids om een horizontale lijnvorm in een Word-document in te voegen met Aspose.Words voor .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Horizontale Lijnvorm Invoegen in Word-document met Aspose.Words voor .NET
Leer hoe je Aspose.Words voor .NET gebruikt om een horizontale lijnvorm in een Word-document in te voegen. Deze tutorial leidt je stap voor stap door het maken van een nieuw document, het toevoegen van een regel tekst, het plaatsen van een horizontale lijnvorm met DocumentBuilder, en het opslaan van het bestand. De horizontale lijn biedt een eenvoudige visuele scheiding voor je inhoud.

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

**Q: Kan ik het uiterlijk (kleur, dikte) van de horizontale lijn die is ingevoegd met DocumentBuilder.InsertHorizontalRule() wijzigen?**
A: InsertHorizontalRule maakt een ingebouwde horizontale lijnvorm met standaardopmaak; om het uiterlijk aan te passen moet je het ingevoegde Shape-object (builder.CurrentParagraph.LastChild) ophalen en de LineFormat-eigenschappen wijzigen.

**Q: Wat gebeurt er als ik InsertHorizontalRule() aanroep na een alinea die al eindigt met een regeleinde?**
A: De methode voegt de lijn toe als een aparte alinea, dus een voorafgaand regeleinde creëert simpelweg een lege alinea vóór de lijn; de lijn zal nog steeds op een eigen regel verschijnen.

**Q: Is het mogelijk om meer dan één horizontale lijn in hetzelfde document in te voegen met DocumentBuilder?**
A: Ja, elke oproep van builder.InsertHorizontalRule() voegt een nieuwe horizontale lijnvorm toe op de huidige cursorpositie, waardoor meerdere lijnen door het document heen mogelijk zijn.

**Q: Werkt InsertHorizontalRule() bij het opslaan van het document naar andere formaten dan DOCX, zoals PDF?**
A: De horizontale lijn wordt opgeslagen als een shape in het documentmodel, dus bij het opslaan naar PDF, XPS of andere ondersteunde formaten wordt de lijn correct gerenderd in de output.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}