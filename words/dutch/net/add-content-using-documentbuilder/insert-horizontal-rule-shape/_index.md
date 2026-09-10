---
title: Invoegen van een horizontale regelvorm in een Word-document met Aspose.Words for .NET
weight: 110
limit:
description: Leer hoe je een horizontale regelvorm aan een Word-document toevoegt met Aspose.Words for .NET via DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Invoegen van een horizontale regelvorm in een Word-document met Aspose.Words
In deze tutorial leer je hoe je programmatically een horizontale regelvorm in een Word-document kunt invoegen met Aspose.Words for .NET. Met behulp van de Document- en DocumentBuilder-klassen maken we een nieuw document, voegen we een alinea tekst toe, en plaatsen we vervolgens een horizontale lijnvorm op de gewenste locatie. De horizontale regel dient als visuele scheiding die nuttig kan zijn voor sectie‑breuken of visuele nadruk.

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

**Q: Waar precies plaatst `builder.InsertHorizontalRule()` de lijn in het document?**
A: `InsertHorizontalRule` voegt een horizontale regelvorm in op de huidige cursorpositie van de `DocumentBuilder`; als je het op een eigen regel wilt, roep dan `builder.Writeln()` aan vóór de invoeging.

**Q: Kan ik de dikte, kleur of breedte van de ingevoegde horizontale regel aanpassen?**
A: `InsertHorizontalRule` voegt een standaard gestylede regel toe en biedt geen opmaakopties; om die eigenschappen aan te passen moet je handmatig een `Shape` invoegen (bijv. `builder.InsertShape(ShapeType.HorizontalLine)`) en vervolgens de `LineFormat`‑eigenschappen instellen.

**Q: Is het mogelijk om meer dan één horizontale regel toe te voegen in hetzelfde document?**
A: Ja—roep simpelweg `builder.InsertHorizontalRule()` telkens wanneer je een nieuwe regel nodig hebt; elke oproep maakt een aparte vorm op de huidige locatie van de builder.

**Q: Zal de horizontale regel zichtbaar zijn wanneer het opgeslagen .docx‑bestand wordt geopend in Microsoft Word?**
A: Absoluut; de regel wordt opgeslagen als een vorm binnen het .docx‑bestand, zodat Word deze precies weergeeft zoals hij in het gegenereerde document verschijnt.

**Q: Wat gebeurt er als de `dataDir`‑map niet bestaat voordat `doc.Save(...)` wordt aangeroepen?**
A: `doc.Save` zal een `DirectoryNotFoundException` werpen; zorg ervoor dat de doelmap bestaat of maak deze programmatically aan vóór het opslaan.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}