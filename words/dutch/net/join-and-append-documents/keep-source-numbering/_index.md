---
title: Bronnummering behouden
linktitle: Bronnummering behouden
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u documenten importeert met behoud van opmaak met Aspose.Words voor .NET. Stapsgewijze handleiding met codevoorbeelden.
weight: 10
url: /nl/net/join-and-append-documents/keep-source-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bronnummering behouden

## Invoering

 Bij het werken met Aspose.Words voor .NET kan het importeren van documenten van de ene bron naar de andere, met behoud van opmaak, efficiënt worden afgehandeld met behulp van de`NodeImporter` klasse. Deze tutorial begeleidt u stap voor stap door het proces.

## Vereisten

Zorg ervoor dat u het volgende bij de hand hebt voordat u begint:
- Visual Studio op uw computer geïnstalleerd.
-  Aspose.Words voor .NET geïnstalleerd. Zo niet, download het dan van[hier](https://releases.aspose.com/words/net/).
- Basiskennis van C# en .NET-programmering.

## Naamruimten importeren

Neem eerst de benodigde naamruimten op in uw project:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Stap 1: Stel uw project in

Begin met het maken van een nieuw C#-project in Visual Studio en installeer Aspose.Words via NuGet Package Manager.

## Stap 2: Documenten initialiseren
Maak instanties van de bron (`srcDoc`) en bestemming (`dstDoc`) documenten.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Stap 3: Importopties configureren
Stel importopties in om de opmaak van de bron te behouden, inclusief genummerde alinea's.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Stap 4: Alinea's importeren
Loop door de paragrafen in het brondocument en importeer ze in het doeldocument.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Stap 5: Sla het document op
Sla het samengevoegde document op de gewenste locatie op.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Conclusie

 Concluderend is het gebruik van Aspose.Words voor .NET om documenten te importeren met behoud van opmaak eenvoudig met de`NodeImporter` klasse. Deze methode zorgt ervoor dat uw documenten hun oorspronkelijke uiterlijk en structuur naadloos behouden.

## Veelgestelde vragen

### Kan ik documenten met verschillende opmaakstijlen importeren?
 Ja, de`NodeImporter` klasse ondersteunt het importeren van documenten met verschillende opmaakstijlen.

### Wat moet ik doen als mijn documenten complexe tabellen en afbeeldingen bevatten?
Aspose.Words voor .NET verwerkt complexe structuren zoals tabellen en afbeeldingen tijdens importbewerkingen.

### Is Aspose.Words compatibel met alle versies van .NET?
Aspose.Words ondersteunt .NET Framework- en .NET Core-versies voor naadloze integratie.

### Hoe kan ik fouten tijdens het importeren van documenten oplossen?
Gebruik try-catch-blokken om uitzonderingen af te handelen die tijdens het importproces kunnen optreden.

### Waar kan ik meer gedetailleerde documentatie vinden over Aspose.Words voor .NET?
 Bezoek de[documentatie](https://reference.aspose.com/words/net/) voor uitgebreide handleidingen en API-referenties.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
