---
title: Ställ in typsnittsmappar med prioritet
linktitle: Ställ in typsnittsmappar med prioritet
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in teckensnittsmappar med prioritet i Word-dokument med Aspose.Words för .NET. Vår guide säkerställer att dina dokument återges perfekt varje gång.
weight: 10
url: /sv/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in typsnittsmappar med prioritet

## Introduktion

I en värld av dokumentmanipulation kan inställning av anpassade typsnittsmappar göra en värld av skillnad för att säkerställa att dina dokument återges perfekt, oavsett var de visas. Idag ska vi dyka in i hur du kan ställa in typsnittsmappar med prioritet i dina Word-dokument med Aspose.Words för .NET. Denna omfattande guide kommer att leda dig genom varje steg, vilket gör processen så smidig som möjligt.

## Förutsättningar

Innan vi börjar, låt oss se till att vi har allt vi behöver. Här är en snabb checklista:

-  Aspose.Words för .NET: Du måste ha detta bibliotek installerat. Om du inte har det än så kan du[ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Se till att du har en fungerande .NET-utvecklingsmiljö, som Visual Studio.
-  Dokumentkatalog: Se till att du har en katalog för dina dokument. För våra exempel kommer vi att använda`"YOUR DOCUMENT DIRECTORY"` som platshållare för denna väg.

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnrymden. Dessa namnutrymmen är viktiga för att komma åt klasserna och metoderna som tillhandahålls av Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss nu dela upp varje steg för att ställa in teckensnittsmappar med prioritet.

## Steg 1: Ställ in dina teckensnittskällor

Till att börja med vill du definiera teckensnittskällorna. Det är här du berättar för Aspose.Words var du ska leta efter typsnitt. Du kan ange flera teckensnittsmappar och till och med ställa in deras prioritet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

I det här exemplet ställer vi in två teckensnittskällor:
- SystemFontSource: Detta är standardfontkällan som inkluderar alla teckensnitt som är installerade på ditt system.
-  FolderFontSource: Detta är en anpassad typsnittsmapp som finns på`C:\\MyFonts\\` . De`true` parametern anger att denna mapp ska skannas rekursivt, och`1` sätter sin prioritet.

## Steg 2: Ladda ditt dokument

Ladda sedan in dokumentet du vill arbeta med. Se till att dokumentet finns i din angivna katalog.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Denna kodrad laddar ett dokument med namnet`Rendering.docx` från din dokumentkatalog.

## Steg 3: Spara ditt dokument med de nya teckensnittsinställningarna

Slutligen, spara ditt dokument. När du sparar dokumentet kommer Aspose.Words att använda de teckensnittsinställningar du angav.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

 Detta sparar dokumentet som en PDF i din dokumentkatalog med namnet`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Slutsats

Och där har du det! Du har framgångsrikt ställt in teckensnittsmappar med prioritet med Aspose.Words för .NET. Genom att ange anpassade typsnittsmappar och prioriteringar kan du säkerställa att dina dokument återges konsekvent, oavsett var de visas. Detta är särskilt användbart i miljöer där specifika teckensnitt inte är installerade som standard.

## FAQ's

### Varför skulle jag behöva ställa in anpassade teckensnittsmappar?
Att ställa in anpassade teckensnittsmappar säkerställer att dina dokument återges korrekt, även om de använder teckensnitt som inte är installerade på systemet där de visas.

### Kan jag ställa in flera anpassade teckensnittsmappar?
Ja, du kan ange flera teckensnittsmappar. Aspose.Words låter dig ställa in prioritet för varje mapp, och se till att de viktigaste typsnitten hittas först.

### Vad händer om ett teckensnitt saknas från alla angivna källor?
Om ett teckensnitt saknas från alla angivna källor kommer Aspose.Words att använda ett reservteckensnitt för att säkerställa att dokumentet fortfarande är läsbart.

### Kan jag ändra prioritet för systemteckensnitten?
Systemteckensnitten ingår alltid som standard, men du kan ställa in deras prioritet i förhållande till dina anpassade teckensnittsmappar.

### Är det möjligt att använda nätverkssökvägar för anpassade teckensnittsmappar?
Ja, du kan ange nätverkssökvägar som anpassade teckensnittsmappar, så att du kan centralisera teckensnittsresurser på en nätverksplats.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
