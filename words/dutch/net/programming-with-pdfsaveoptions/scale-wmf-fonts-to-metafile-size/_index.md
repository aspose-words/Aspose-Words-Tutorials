---
title: Verklein de PDF-grootte met Schaal WMF-lettertypen naar metabestandsgrootte
linktitle: Verklein de PDF-grootte met Schaal WMF-lettertypen naar metabestandsgrootte
second_title: Aspose.Words API voor documentverwerking
description: Stapsgewijze handleiding voor het verkleinen van de PDF-grootte met behulp van WMF-lettertypen naar de metabestandsgrootte bij het converteren naar PDF met Aspose.Words voor .NET.
weight: 10
url: /nl/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verklein de PDF-grootte met Schaal WMF-lettertypen naar metabestandsgrootte

## Invoering

Bij het werken met PDF-bestanden, met name die welke zijn gegenereerd vanuit Word-documenten met WMF (Windows Metafile)-afbeeldingen, kan groottebeheer een cruciaal aspect van documentverwerking worden. Een manier om de PDF-grootte te beheren, is door aan te passen hoe WMF-lettertypen in het document worden weergegeven. In deze tutorial onderzoeken we hoe u de PDF-grootte kunt verkleinen door WMF-lettertypen te schalen naar de metafile-grootte met behulp van Aspose.Words voor .NET.

## Vereisten

Voordat u met de stappen begint, moet u ervoor zorgen dat u het volgende heeft:

1. Aspose.Words voor .NET: Zorg ervoor dat u de Aspose.Words-bibliotheek hebt geïnstalleerd. Zo niet, dan kunt u[download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: in deze zelfstudie gaan we ervan uit dat u een .NET-ontwikkelomgeving hebt ingesteld (zoals Visual Studio) waarin u C#-code kunt schrijven en uitvoeren.
3. Basiskennis van .NET-programmering: Kennis van de basisconcepten van .NET-programmering en de C#-syntaxis is nuttig.
4. Word-document met WMF-graphics: U hebt een Word-document nodig met WMF-graphics. U kunt uw eigen document gebruiken of er een maken om te testen.

## Naamruimten importeren

Eerst moet u de benodigde namespaces importeren in uw C#-project. Dit geeft u toegang tot de klassen en methoden die nodig zijn om met Aspose.Words te werken.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 1: Laad het Word-document

 Om te beginnen laadt u het Word-document dat de WMF-afbeeldingen bevat. Dit doet u met behulp van de`Document` klas van Aspose.Words.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Laad het document
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Hier,`dataDir` is een tijdelijke aanduiding voor uw documentdirectorypad. We maken een instantie van de`Document` class door het pad naar het Word-bestand door te geven. Dit laadt het document in het geheugen, klaar voor verdere verwerking.

## Stap 2: Metafile-renderingopties configureren

 Vervolgens moet u de renderingopties voor het metabestand configureren. Stel met name de`ScaleWmfFontsToMetafileSize`eigendom van`false`Hiermee bepaalt u of WMF-lettertypen worden geschaald zodat ze overeenkomen met de grootte van het metabestand.

```csharp
// Maak een nieuw exemplaar van MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 De`MetafileRenderingOptions` klasse biedt opties voor hoe metafiles (zoals WMF) worden gerenderd. Door in te stellen`ScaleWmfFontsToMetafileSize` naar`false`, geeft u Aspose.Words de opdracht om lettertypen niet te schalen op basis van de metabestandsgrootte. Dit kan helpen om de algehele PDF-grootte te verkleinen.

## Stap 3: PDF-opslagopties instellen

Configureer nu de PDF-opslagopties om de metafile-renderingopties te gebruiken die u zojuist hebt ingesteld. Dit vertelt Aspose.Words hoe metafiles moeten worden verwerkt bij het opslaan van het document als een PDF.

```csharp
// Maak een nieuw exemplaar van PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 De`PdfSaveOptions` klasse kunt u verschillende instellingen opgeven voor het opslaan van het document als een PDF. Door de eerder geconfigureerde`MetafileRenderingOptions` naar de`MetafileRenderingOptions` eigendom van`PdfSaveOptions`, zorgt u ervoor dat het document wordt opgeslagen volgens de door u gewenste instellingen voor metabestandrendering.

## Stap 4: Sla het document op als PDF

Sla ten slotte het Word-document op als een PDF met behulp van de geconfigureerde opslagopties. Dit zal alle instellingen, inclusief de metafile-renderingopties, toepassen op de uitvoer-PDF.


```csharp
// Sla het document op als PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 In deze stap wordt de`Save` methode van de`Document` klasse wordt gebruikt om het document te exporteren naar een PDF-bestand. Het pad waar de PDF wordt opgeslagen, wordt gespecificeerd, samen met de`PdfSaveOptions` die de renderinginstellingen van het metabestand bevatten.

## Conclusie

Door WMF-lettertypen te schalen naar metafile-formaat, kunt u de grootte van uw PDF-bestanden die zijn gegenereerd uit Word-documenten aanzienlijk verkleinen. Deze techniek helpt bij het optimaliseren van documentopslag en -distributie zonder de kwaliteit van de visuele inhoud in gevaar te brengen. Door de hierboven beschreven stappen te volgen, zorgt u ervoor dat uw PDF-bestanden beter beheersbaar en efficiënter zijn in grootte.

## Veelgestelde vragen

### Wat is WMF en waarom is het belangrijk voor de PDF-grootte?

WMF (Windows Metafile) is een grafisch formaat dat wordt gebruikt in Microsoft Windows. Het kan zowel vector- als bitmapgegevens bevatten. Omdat vectorgegevens kunnen worden geschaald en gemanipuleerd, is het belangrijk om er goed mee om te gaan om onnodig grote PDF-bestanden te voorkomen.

### Welk effect heeft het schalen van WMF-lettertypen naar metabestandsgrootte op de PDF?

Door WMF-lettertypen te schalen naar de metabestandsgrootte, kunt u de algehele PDF-grootte verkleinen door te voorkomen dat lettertypen met een hoge resolutie worden weergegeven, waardoor de bestandsgrootte zou kunnen toenemen.

### Kan ik andere metabestandformaten gebruiken met Aspose.Words?

Ja, Aspose.Words ondersteunt verschillende metafileformaten, waaronder EMF (Enhanced Metafile) naast WMF.

### Is deze techniek toepasbaar op alle soorten Word-documenten?

Ja, deze techniek kan worden toegepast op elk Word-document dat WMF-afbeeldingen bevat, waardoor de grootte van de gegenereerde PDF wordt geoptimaliseerd.

### Waar kan ik meer informatie vinden over Aspose.Words?

 U kunt meer ontdekken over Aspose.Woorden in de[Aspose.Words-documentatie](https://reference.aspose.com/words/net/) . Voor downloads, proefversies en ondersteuning, bezoek de[Aspose.Words Downloadpagina](https://releases.aspose.com/words/net/), [Koop Aspose.Words](https://purchase.aspose.com/buy), [Gratis proefperiode](https://releases.aspose.com/), [Tijdelijke licentie](https://purchase.aspose.com/temporary-license/) , En[Steun](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
