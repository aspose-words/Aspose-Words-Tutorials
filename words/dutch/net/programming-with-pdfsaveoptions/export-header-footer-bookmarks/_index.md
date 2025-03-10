---
title: Word-documentkoptekstvoettekstbladwijzers exporteren naar PDF-document
linktitle: Word-documentkoptekstvoettekstbladwijzers exporteren naar PDF-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u kop- en voettekstbladwijzers vanuit een Word-document naar PDF kunt exporteren met Aspose.Words voor .NET met behulp van onze stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-documentkoptekstvoettekstbladwijzers exporteren naar PDF-document

## Invoering

Het converteren van Word-documenten naar PDF is een veelvoorkomende taak, vooral als u documenten wilt delen of archiveren met behoud van de opmaak. Soms bevatten deze documenten belangrijke bladwijzers in de kop- en voetteksten. In deze tutorial doorlopen we het proces van het exporteren van deze bladwijzers van een Word-document naar een PDF met behulp van Aspose.Words voor .NET.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

- Aspose.Words voor .NET: U moet Aspose.Words voor .NET geïnstalleerd hebben. U kunt het downloaden van[hier](https://releases.aspose.com/words/net/).
- Development Environment: Stel uw development environment in. U kunt Visual Studio of een andere .NET-compatibele IDE gebruiken.
- Basiskennis van C#: Kennis van C#-programmering is vereist om de codevoorbeelden te kunnen volgen.

## Naamruimten importeren

Allereerst moet u de benodigde namespaces importeren in uw C#-project. Voeg deze regels toe bovenaan uw codebestand:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Laten we het proces opsplitsen in eenvoudig te volgen stappen.

## Stap 1: Initialiseer het document

De eerste stap is om uw Word-document te laden. Dit is hoe u dat kunt doen:

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

In deze stap geeft u eenvoudigweg het pad naar uw documentmap op en laadt u het Word-document.

## Stap 2: PDF-opslagopties configureren

Vervolgens moet u de opties voor het opslaan van PDF-bestanden configureren om ervoor te zorgen dat bladwijzers in de kop- en voetteksten correct worden geëxporteerd.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Hier zijn we bezig met het opzetten van de`PdfSaveOptions` . De`DefaultBookmarksOutlineLevel` eigenschap stelt het overzichtsniveau voor bladwijzers in, en de`HeaderFooterBookmarksExportMode` Deze eigenschap zorgt ervoor dat alleen de eerste bladwijzer in kop- en voetteksten wordt geëxporteerd.

## Stap 3: Sla het document op als PDF

Sla ten slotte uw document op als PDF met de geconfigureerde opties.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

In deze stap slaat u het document op in het opgegeven pad met de opties die u hebt geconfigureerd.

## Conclusie

En daar heb je het! Door deze stappen te volgen, kun je eenvoudig bladwijzers exporteren van de kop- en voetteksten van een Word-document naar een PDF met Aspose.Words voor .NET. Deze methode zorgt ervoor dat belangrijke navigatiehulpmiddelen in je document behouden blijven in de PDF-indeling, waardoor lezers gemakkelijker door je document kunnen navigeren.

## Veelgestelde vragen

### Kan ik alle bladwijzers uit het Word-document naar PDF exporteren?

 Ja, dat kan. In de`PdfSaveOptions`, kunt u de instellingen aanpassen om indien nodig alle bladwijzers op te nemen.

### Wat als ik ook bladwijzers uit de hoofdtekst van het document wil exporteren?

 U kunt de`OutlineOptions` in`PdfSaveOptions` om bladwijzers uit de hoofdtekst van het document op te nemen.

### Is het mogelijk om de bladwijzerniveaus in de PDF aan te passen?

 Absoluut! Je kunt de`DefaultBookmarksOutlineLevel` eigenschap om verschillende overzichtsniveaus voor uw bladwijzers in te stellen.

### Hoe ga ik om met documenten zonder bladwijzers?

Als uw document geen bladwijzers heeft, wordt de PDF gegenereerd zonder bladwijzercontour. Zorg ervoor dat uw document bladwijzers bevat als u ze in de PDF nodig hebt.

### Kan ik deze methode gebruiken voor andere documenttypen, zoals DOCX of RTF?

Ja, Aspose.Words voor .NET ondersteunt verschillende documenttypen, waaronder DOCX, RTF en andere.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
