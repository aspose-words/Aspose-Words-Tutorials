---
title: Dela Word-dokument efter rubriker Html
linktitle: Efter rubriker Html
second_title: Aspose.Words Document Processing API
description: Lär dig hur du delar upp ett Word-dokument efter rubriker till HTML med Aspose.Words för .NET. Följ vår detaljerade, steg-för-steg-guide.
weight: 10
url: /sv/net/split-document/by-headings-html/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dela Word-dokument efter rubriker Html

## Introduktion

Att dela upp ett Word-dokument efter rubriker kan vara en spelomvandlare för att hantera stora dokument eller skapa segmenterade HTML-utdata. Aspose.Words för .NET ger ett enkelt sätt att uppnå detta. I den här handledningen går vi igenom hela processen och ser till att du förstår varje detalj längs vägen.

## Förutsättningar

Innan du dyker in i handledningen, se till att du har följande:

1. Aspose.Words för .NET: Om du inte redan har gjort det, ladda ner det från[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio.
3. Grundläggande kunskaper om C#: Att förstå grunderna hjälper dig att enkelt följa med.
4. Ett exempeldokument: Ha ett Word-dokument redo som du vill dela upp efter rubriker.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta är avgörande för att komma åt Aspose.Words-klasserna och -metoderna.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera ditt projekt

För att komma igång, ställ in ditt projekt i din utvecklingsmiljö. Öppna Visual Studio och skapa en ny konsolapplikation.

1. Skapa ett nytt projekt: Öppna Visual Studio, välj "Skapa ett nytt projekt", välj "Console App (.NET Core)" och klicka på "Nästa".
2. Konfigurera ditt projekt: Namnge ditt projekt, välj en plats för att spara det och klicka på "Skapa".
3.  Installera Aspose.Words för .NET: Använd NuGet Package Manager för att installera Aspose.Words-biblioteket. I NuGet Package Manager, sök efter`Aspose.Words` och installera den.

## Steg 2: Ladda ditt dokument

Därefter måste du ladda Word-dokumentet du vill dela. Se till att ditt dokument är placerat i en katalog som du enkelt kan komma åt.

1. Definiera katalogsökvägen: Skapa en variabel för ditt dokuments katalogsökväg.
2.  Ladda dokumentet: Använd`Document` klass för att ladda ditt Word-dokument.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera HTML-sparalternativ

Låt oss nu konfigurera HTML-sparalternativen för att ange att dokumentet ska delas efter rubriker.

1.  Skapa HtmlSaveOptions: Instantiera`HtmlSaveOptions` klass.
2.  Ställ in dokumentdelningskriterier: Använd`DocumentSplitCriteria` egenskap för att ange att dokumentet ska delas upp efter rubriker.

```csharp
HtmlSaveOptions options = new HtmlSaveOptions
{
    // Dela upp ett dokument i mindre delar, i det här fallet delat efter rubrik.
    DocumentSplitCriteria = DocumentSplitCriteria.HeadingParagraph
};
```

## Steg 4: Spara det delade dokumentet

Slutligen sparar du dokumentet med de angivna HTML-sparalternativen. Detta kommer att generera en HTML-fil delad efter rubriker.

1.  Spara dokumentet: Använd`Save` metod för`Document` klass för att spara dokumentet med de angivna alternativen.

```csharp
doc.Save(dataDir + "SplitDocument.ByHeadingsHtml.html", options);
```

## Slutsats

Och där har du det! Du har framgångsrikt delat upp ett Word-dokument efter rubriker och sparat det som HTML med Aspose.Words för .NET. Denna metod är mycket effektiv för att organisera stora dokument och skapa segmenterade HTML-utdata, vilket gör ditt innehåll mer hanterbart och tillgängligt.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument i .NET-applikationer.

### Kan jag dela upp ett dokument efter andra kriterier?
Ja, Aspose.Words låter dig dela upp dokument efter olika kriterier som sektioner, sidor och mer.

### Är Aspose.Words gratis?
 Aspose.Words erbjuder en gratis provperiod, men för alla funktioner måste du köpa en licens. Kolla deras[köpsida](https://purchase.aspose.com/buy) för mer information.

### Var kan jag hitta dokumentationen?
 Omfattande dokumentation finns tillgänglig[här](https://reference.aspose.com/words/net/).

### Hur får jag stöd?
 För support, besök Aspose.Words[forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
