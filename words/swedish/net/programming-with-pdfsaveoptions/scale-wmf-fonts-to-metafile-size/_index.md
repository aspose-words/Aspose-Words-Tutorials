---
"description": "Steg-för-steg-guide för att minska PDF-storleken med skalning av wmf-teckensnitt till metafilstorlek vid konvertering till PDF med Aspose.Words för .NET."
"linktitle": "Minska PDF-storleken med skala WMF-teckensnitt till metafilstorlek"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Minska PDF-storleken med skala WMF-teckensnitt till metafilstorlek"
"url": "/sv/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Minska PDF-storleken med skala WMF-teckensnitt till metafilstorlek

## Introduktion

När man arbetar med PDF-filer, särskilt de som genereras från Word-dokument som innehåller WMF-grafik (Windows Metafile), kan storlekshantering bli en avgörande aspekt av dokumenthanteringen. Ett sätt att kontrollera PDF-storleken är att justera hur WMF-teckensnitt återges i dokumentet. I den här handledningen utforskar vi hur man minskar PDF-storleken genom att skala WMF-teckensnitt till metafilstorleken med hjälp av Aspose.Words för .NET.

## Förkunskapskrav

Innan du går vidare till stegen, se till att du har följande:

1. Aspose.Words för .NET: Se till att du har Aspose.Words-biblioteket installerat. Om inte kan du [ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Den här handledningen förutsätter att du har en .NET-utvecklingsmiljö konfigurerad (som Visual Studio) där du kan skriva och köra C#-kod.
3. Grundläggande förståelse för .NET-programmering: Bekantskap med grundläggande .NET-programmeringskoncept och C#-syntax är meriterande.
4. Word-dokument med WMF-grafik: Du behöver ett Word-dokument som innehåller WMF-grafik. Du kan använda ditt eget dokument eller skapa ett för testning.

## Importera namnrymder

Först måste du importera de nödvändiga namnrymderna i ditt C#-projekt. Detta ger dig tillgång till de klasser och metoder som krävs för att arbeta med Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Ladda Word-dokumentet

För att börja, ladda Word-dokumentet som innehåller WMF-grafiken. Detta görs med hjälp av `Document` klass från Aspose.Words.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Ladda dokumentet
Document doc = new Document(dataDir + "WMF with text.docx");
```

Här, `dataDir` är en platshållare för din dokumentkatalogs sökväg. Vi skapar en instans av `Document` klassen genom att skicka sökvägen till Word-filen. Detta laddar dokumentet till minnet, redo för vidare bearbetning.

## Steg 2: Konfigurera renderingsalternativ för metafiler

Nästa steg är att konfigurera renderingsalternativen för metafiler. Ställ specifikt in `ScaleWmfFontsToMetafileSize` egendom till `false`Detta styr om WMF-teckensnitt skalas för att matcha metafilstorleken.

```csharp
// Skapa en ny instans av MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

De `MetafileRenderingOptions` klassen ger alternativ för hur metafiler (som WMF) renderas. Genom att ställa in `ScaleWmfFontsToMetafileSize` till `false`, instruerar du Aspose.Words att inte skala teckensnitt efter metafilstorleken, vilket kan bidra till att minska den totala PDF-storleken.

## Steg 3: Ställ in PDF-sparalternativ

Konfigurera nu PDF-sparalternativen för att använda de metafilrenderingsalternativ du just ställt in. Detta talar om för Aspose.Words hur metafiler ska hanteras när dokumentet sparas som en PDF.

```csharp
// Skapa en ny instans av PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

De `PdfSaveOptions` klassen låter dig ange olika inställningar för att spara dokumentet som en PDF. Genom att tilldela den tidigare konfigurerade `MetafileRenderingOptions` till `MetafileRenderingOptions` egendom av `PdfSaveOptions`, ser du till att dokumentet sparas enligt dina önskade inställningar för metafilrendering.

## Steg 4: Spara dokumentet som PDF

Spara slutligen Word-dokumentet som en PDF med de konfigurerade sparalternativen. Detta kommer att tillämpa alla inställningar, inklusive renderingsalternativen för metafiler, på den utgående PDF-filen.


```csharp
// Spara dokumentet som PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

I detta steg, `Save` metod för `Document` Klassen används för att exportera dokumentet till en PDF-fil. Sökvägen där PDF-filen ska sparas anges, tillsammans med `PdfSaveOptions` som inkluderar inställningarna för metafilrendering.

## Slutsats

Genom att skala WMF-teckensnitt till metafilstorlek kan du avsevärt minska storleken på dina PDF-filer som genereras från Word-dokument. Den här tekniken hjälper till att optimera dokumentlagring och distribution utan att kompromissa med kvaliteten på det visuella innehållet. Genom att följa stegen som beskrivs ovan säkerställer du att dina PDF-filer är mer hanterbara och effektiva i storlek.

## Vanliga frågor

### Vad är WMF och varför är det viktigt för PDF-storleken?

WMF (Windows Metafile) är ett grafikformat som används i Microsoft Windows. Det kan innehålla både vektor- och bitmappsdata. Eftersom vektordata kan skalas och manipuleras är det viktigt att hantera det korrekt för att undvika onödigt stora PDF-filer.

### Hur påverkar skalning av WMF-teckensnitt till metafilstorlek PDF-filen?

Att skala WMF-teckensnitt till metafilstorlek kan bidra till att minska den totala PDF-storleken genom att undvika högupplösta teckensnittsrendering som kan öka filstorleken.

### Kan jag använda andra metafilformat med Aspose.Words?

Ja, Aspose.Words stöder olika metafilformat, inklusive EMF (Enhanced Metafile) utöver WMF.

### Är den här tekniken tillämpbar på alla typer av Word-dokument?

Ja, den här tekniken kan tillämpas på alla Word-dokument som innehåller WMF-grafik, vilket hjälper till att optimera storleken på den genererade PDF-filen.

### Var kan jag hitta mer information om Aspose.Words?

Du kan utforska mer om Aspose.Words i [Aspose.Words-dokumentation](https://reference.aspose.com/words/net/)För nedladdningar, testversioner och support, besök [Aspose.Words nedladdningssida](https://releases.aspose.com/words/net/), [Köp Aspose.Words](https://purchase.aspose.com/buy), [Gratis provperiod](https://releases.aspose.com/), [Tillfällig licens](https://purchase.aspose.com/temporary-license/)och [Stöd](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}