---
"description": "Stapsgewijze handleiding voor het verkleinen van de PDF-grootte met behulp van schaalbare WMF-lettertypen naar metabestandsgrootte bij conversie naar PDF met Aspose.Words voor .NET."
"linktitle": "Verklein de PDF-grootte met WMF-lettertypen schalen naar metabestandsgrootte"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Verklein de PDF-grootte met WMF-lettertypen schalen naar metabestandsgrootte"
"url": "/nl/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verklein de PDF-grootte met WMF-lettertypen schalen naar metabestandsgrootte

## Invoering

Bij het werken met PDF-bestanden, met name die gegenereerd vanuit Word-documenten met WMF-afbeeldingen (Windows Metafile), kan bestandsgroottebeheer een cruciaal aspect van documentverwerking worden. Eén manier om de PDF-grootte te beheren, is door de weergave van WMF-lettertypen in het document aan te passen. In deze tutorial laten we zien hoe je de PDF-grootte kunt verkleinen door WMF-lettertypen te schalen naar de metafile-grootte met behulp van Aspose.Words voor .NET.

## Vereisten

Voordat u met de stappen begint, moet u ervoor zorgen dat u het volgende heeft:

1. Aspose.Words voor .NET: Zorg ervoor dat de Aspose.Words-bibliotheek geïnstalleerd is. Zo niet, dan kunt u... [download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: in deze zelfstudie gaan we ervan uit dat u een .NET-ontwikkelomgeving hebt ingesteld (zoals Visual Studio) waarin u C#-code kunt schrijven en uitvoeren.
3. Basiskennis van .NET-programmering: kennis van de basisconcepten van .NET-programmering en de C#-syntaxis is nuttig.
4. Word-document met WMF-afbeeldingen: Je hebt een Word-document met WMF-afbeeldingen nodig. Je kunt je eigen document gebruiken of er zelf een maken om te testen.

## Naamruimten importeren

Eerst moet je de benodigde naamruimten importeren in je C#-project. Dit geeft je toegang tot de klassen en methoden die nodig zijn om met Aspose.Words te werken.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 1: Laad het Word-document

Om te beginnen laadt u het Word-document met de WMF-afbeeldingen. Dit doet u met behulp van de `Document` klas van Aspose.Words.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Laad het document
Document doc = new Document(dataDir + "WMF with text.docx");
```

Hier, `dataDir` is een tijdelijke aanduiding voor het pad van uw documentdirectory. We maken een instantie van de `Document` klasse door het pad naar het Word-bestand door te geven. Dit laadt het document in het geheugen, klaar voor verdere verwerking.

## Stap 2: Metafile-renderingopties configureren

Vervolgens moet u de renderingopties voor het metabestand configureren. Stel specifiek de `ScaleWmfFontsToMetafileSize` eigendom van `false`Hiermee bepaalt u of WMF-lettertypen worden geschaald zodat ze overeenkomen met de grootte van het metabestand.

```csharp
// Maak een nieuw exemplaar van MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

De `MetafileRenderingOptions` klasse biedt opties voor hoe metabestanden (zoals WMF) worden weergegeven. Door in te stellen `ScaleWmfFontsToMetafileSize` naar `false`, geeft u Aspose.Words de opdracht om lettertypen niet te schalen op basis van de metabestandsgrootte. Dit kan helpen om de algehele PDF-grootte te verkleinen.

## Stap 3: PDF-opslagopties instellen

Configureer nu de PDF-opslagopties om de zojuist ingestelde metafile-renderingopties te gebruiken. Dit vertelt Aspose.Words hoe metafiles moeten worden verwerkt bij het opslaan van het document als PDF.

```csharp
// Een nieuw exemplaar van PdfSaveOptions maken
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

De `PdfSaveOptions` Met de klasse kunt u verschillende instellingen opgeven voor het opslaan van het document als PDF. Door de eerder geconfigureerde `MetafileRenderingOptions` naar de `MetafileRenderingOptions` eigendom van `PdfSaveOptions`, zorgt u ervoor dat het document wordt opgeslagen volgens de door u gewenste metabestand-renderinginstellingen.

## Stap 4: Sla het document op als PDF

Sla ten slotte het Word-document op als PDF met behulp van de geconfigureerde opslagopties. Hiermee worden alle instellingen, inclusief de weergaveopties voor het metabestand, toegepast op de PDF-uitvoer.


```csharp
// Sla het document op als PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

In deze stap wordt de `Save` methode van de `Document` klasse wordt gebruikt om het document naar een PDF-bestand te exporteren. Het pad waar de PDF wordt opgeslagen, wordt gespecificeerd, samen met de `PdfSaveOptions` die de renderinginstellingen van het metabestand bevatten.

## Conclusie

Door WMF-lettertypen te schalen naar metabestandsgrootte, kunt u de grootte van uw PDF-bestanden die vanuit Word-documenten worden gegenereerd aanzienlijk verkleinen. Deze techniek helpt bij het optimaliseren van de opslag en distributie van documenten zonder de kwaliteit van de visuele content in gevaar te brengen. Door de bovenstaande stappen te volgen, worden uw PDF-bestanden beter beheersbaar en efficiënter qua formaat.

## Veelgestelde vragen

### Wat is WMF en waarom is het belangrijk voor de PDF-grootte?

WMF (Windows Metafile) is een grafisch formaat dat gebruikt wordt in Microsoft Windows. Het kan zowel vector- als bitmapgegevens bevatten. Omdat vectorgegevens geschaald en bewerkt kunnen worden, is het belangrijk om er correct mee om te gaan om onnodig grote PDF-bestanden te voorkomen.

### Welk effect heeft het schalen van WMF-lettertypen naar metabestandsgrootte op de PDF?

Door WMF-lettertypen te schalen naar metabestandsgrootte, kunt u de algehele PDF-grootte verkleinen door rendering van lettertypen met een hoge resolutie te vermijden, wat de bestandsgrootte zou kunnen vergroten.

### Kan ik andere metabestandformaten gebruiken met Aspose.Words?

Ja, Aspose.Words ondersteunt verschillende metafileformaten, waaronder EMF (Enhanced Metafile) naast WMF.

### Is deze techniek toepasbaar op alle soorten Word-documenten?

Ja, deze techniek kan worden toegepast op elk Word-document dat WMF-afbeeldingen bevat, en helpt bij het optimaliseren van de grootte van de gegenereerde PDF.

### Waar kan ik meer informatie vinden over Aspose.Words?

U kunt meer ontdekken over Aspose.Woorden in de [Aspose.Words-documentatie](https://reference.aspose.com/words/net/)Voor downloads, proefversies en ondersteuning kunt u terecht op de [Aspose.Words Downloadpagina](https://releases.aspose.com/words/net/), [Koop Aspose.Words](https://purchase.aspose.com/buy), [Gratis proefperiode](https://releases.aspose.com/), [Tijdelijke licentie](https://purchase.aspose.com/temporary-license/), En [Steun](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}