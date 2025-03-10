---
title: Minska PDF-storleken med skala Wmf-teckensnitt till metafilstorlek
linktitle: Minska PDF-storleken med skala Wmf-teckensnitt till metafilstorlek
second_title: Aspose.Words Document Processing API
description: Steg-för-steg guide för att minska pdf-storlek med skala wmf-teckensnitt till metafilstorlek vid konvertering till PDF med Aspose.Words för .NET.
weight: 10
url: /sv/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Minska PDF-storleken med skala Wmf-teckensnitt till metafilstorlek

## Introduktion

När du arbetar med PDF-filer, särskilt de som genereras från Word-dokument som innehåller WMF-grafik (Windows Metafile), kan storlekshantering bli en avgörande aspekt av dokumenthantering. Ett sätt att styra PDF-storleken är genom att justera hur WMF-teckensnitt renderas i dokumentet. I den här handledningen kommer vi att undersöka hur du minskar PDF-storleken genom att skala WMF-teckensnitt till metafilstorleken med Aspose.Words för .NET.

## Förutsättningar

Innan du dyker in i stegen, se till att du har följande:

1. Aspose.Words för .NET: Se till att du har Aspose.Words-biblioteket installerat. Om inte, kan du[ladda ner den här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Denna handledning förutsätter att du har en .NET-utvecklingsmiljö inställd (som Visual Studio) där du kan skriva och köra C#-kod.
3. Grundläggande förståelse för .NET-programmering: Bekantskap med grundläggande .NET-programmeringskoncept och C#-syntax kommer att vara till hjälp.
4. Word-dokument med WMF-grafik: Du behöver ett Word-dokument som innehåller WMF-grafik. Du kan använda ditt eget dokument eller skapa ett för testning.

## Importera namnområden

Först måste du importera de nödvändiga namnrymden i ditt C#-projekt. Detta ger dig tillgång till de klasser och metoder som krävs för att arbeta med Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Ladda Word-dokumentet

 Börja med att ladda Word-dokumentet som innehåller WMF-grafiken. Detta görs med hjälp av`Document` klass från Aspose.Words.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Ladda dokumentet
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Här,`dataDir` är en platshållare för sökvägen till din dokumentkatalog. Vi skapar en instans av`Document` klass genom att skicka sökvägen till Word-filen. Detta laddar dokumentet i minnet, redo för vidare bearbetning.

## Steg 2: Konfigurera metafilåtergivningsalternativ

 Därefter måste du konfigurera alternativen för metafilrendering. Specifikt, ställ in`ScaleWmfFontsToMetafileSize`egendom till`false`. Detta styr om WMF-teckensnitt skalas för att matcha metafilstorleken.

```csharp
// Skapa en ny instans av MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 De`MetafileRenderingOptions` klass ger alternativ för hur metafiler (som WMF) renderas. Genom att ställa in`ScaleWmfFontsToMetafileSize` till`false`, instruerar du Aspose.Words att inte skala teckensnitt enligt metafilstorleken, vilket kan hjälpa till att minska den totala PDF-storleken.

## Steg 3: Ställ in PDF-sparalternativ

Konfigurera nu PDF-sparalternativen för att använda alternativen för metafilrendering som du just har ställt in. Detta berättar för Aspose.Words hur man hanterar metafiler när man sparar dokumentet som en PDF.

```csharp
// Skapa en ny instans av PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 De`PdfSaveOptions` class låter dig ange olika inställningar för att spara dokumentet som en PDF. Genom att tilldela den tidigare konfigurerade`MetafileRenderingOptions` till`MetafileRenderingOptions` egendom av`PdfSaveOptions`, ser du till att dokumentet sparas enligt dina önskade metafilrenderingsinställningar.

## Steg 4: Spara dokumentet som PDF

Slutligen sparar du Word-dokumentet som en PDF med hjälp av de konfigurerade sparalternativen. Detta kommer att tillämpa alla inställningar, inklusive alternativen för rendering av metafiler, på den utgående PDF-filen.


```csharp
// Spara dokumentet som PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 I detta steg,`Save` metod för`Document` klass används för att exportera dokumentet till en PDF-fil. Sökvägen där PDF:en kommer att sparas anges, tillsammans med`PdfSaveOptions` som inkluderar metafilrenderingsinställningarna.

## Slutsats

Genom att skala WMF-teckensnitt till metafilstorlek kan du avsevärt minska storleken på dina PDF-filer som genereras från Word-dokument. Denna teknik hjälper till att optimera dokumentlagring och distribution utan att kompromissa med kvaliteten på det visuella innehållet. Genom att följa stegen ovan säkerställer du att dina PDF-filer är mer hanterbara och effektiva i storlek.

## FAQ's

### Vad är WMF och varför är det viktigt för PDF-storlek?

WMF (Windows Metafile) är ett grafiskt format som används i Microsoft Windows. Den kan innehålla både vektor- och bitmappsdata. Eftersom vektordata kan skalas och manipuleras är det viktigt att hantera det på rätt sätt för att undvika onödigt stora PDF-filer.

### Hur påverkar skalning av WMF-teckensnitt till metafilstorlek PDF:en?

Att skala WMF-teckensnitt till metafilstorlek kan hjälpa till att minska den totala PDF-storleken genom att undvika högupplöst teckensnittsrendering som kan öka filstorleken.

### Kan jag använda andra metafilformat med Aspose.Words?

Ja, Aspose.Words stöder olika metafilformat, inklusive EMF (Enhanced Metafile) förutom WMF.

### Är denna teknik tillämpbar på alla typer av Word-dokument?

Ja, den här tekniken kan tillämpas på alla Word-dokument som innehåller WMF-grafik, vilket hjälper till att optimera storleken på den genererade PDF-filen.

### Var kan jag hitta mer information om Aspose.Words?

 Du kan utforska mer om Aspose.Words i[Aspose.Words dokumentation](https://reference.aspose.com/words/net/) . För nedladdningar, testversioner och support, besök[Aspose.Words nedladdningssida](https://releases.aspose.com/words/net/), [Köp Aspose.Words](https://purchase.aspose.com/buy), [Gratis provperiod](https://releases.aspose.com/), [Tillfällig licens](https://purchase.aspose.com/temporary-license/) , och[Stöd](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
