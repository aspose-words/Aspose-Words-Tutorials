---
"description": "Lär dig hur du lägger till dubbelriktade (Bidi) markeringar i Word-dokument med Aspose.Words för .NET med den här guiden. Säkerställ korrekt textriktning för flerspråkigt innehåll."
"linktitle": "Lägg till Bidi-markeringar i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Lägg till Bidi-markeringar i Word-dokument"
"url": "/sv/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till Bidi-markeringar i Word-dokument

## Introduktion

dokumentbehandlingens värld kan dubbelriktad (Bidi) text ofta vara lite knepig att hantera. Detta gäller särskilt när man arbetar med språk som har olika textriktningar, som arabiska eller hebreiska. Lyckligtvis gör Aspose.Words för .NET det enkelt att hantera sådana scenarier. I den här handledningen går vi igenom hur man lägger till Bidi-markeringar i ett Word-dokument med hjälp av Aspose.Words för .NET.

## Förkunskapskrav

Innan vi går in i koden, se till att du har följande:

1. Aspose.Words för .NET: Du måste ha Aspose.Words för .NET installerat. Du kan ladda ner det från [Aspose Nedladdningssida](https://releases.aspose.com/words/net/).
2. .NET Framework eller .NET Core: Se till att du har en kompatibel .NET-miljö konfigurerad för att köra exemplen.
3. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# och grundläggande operationer i .NET.

## Importera namnrymder

För att komma igång behöver du importera de nödvändiga namnrymderna. Så här kan du inkludera dem i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Låt oss dela upp processen för att lägga till Bidi-markeringar i ett Word-dokument i tydliga steg. Varje steg guidar dig genom koden och dess syfte.

## Steg 1: Konfigurera ditt dokument

Börja med att skapa en ny instans av `Document` klass och en `DocumentBuilder` för att lägga till innehåll i dokumentet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Skapa dokumentet och lägg till innehåll
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

I det här steget initierar du ett nytt Word-dokument och konfigurerar en `DocumentBuilder` för att underlätta innehållsinmatning.

## Steg 2: Lägg till innehåll i ditt dokument

Lägg sedan till lite text i ditt dokument. Här lägger vi till text på olika språk för att illustrera hantering av Bidi-text.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Här lägger vi först till en standardfras på engelska. Sedan aktiverar vi bidi-textformatering för den efterföljande texten, som är skriven på hebreiska och arabiska. Detta visar hur man införlivar dubbelriktad text.

## Steg 3: Konfigurera sparalternativ för Bidi-märken

För att säkerställa att Bidi-markeringarna sparas korrekt i dokumentet måste du konfigurera `TxtSaveOptions` och aktivera `AddBidiMarks` alternativ.

```csharp
// Lägg till Bidi-märken
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

I det här steget skapar vi en instans av `TxtSaveOptions` och ställ in `AddBidiMarks` egendom till `true`Detta säkerställer att Bidi-markeringarna inkluderas när dokumentet sparas som en textfil.

## Slutsats

Att lägga till Bidi-markeringar i dina Word-dokument kan vara ett avgörande steg när du hanterar flerspråkigt innehåll som inkluderar språk med olika textriktningar. Med Aspose.Words för .NET är denna process enkel och effektiv. Genom att följa stegen som beskrivs ovan kan du säkerställa att dina dokument korrekt representerar Bidi-text, vilket förbättrar läsbarheten och noggrannheten.

## Vanliga frågor

### Vad är Bidi-märken och varför är de viktiga?
Bidi-tecken är specialtecken som används för att styra textens riktning i dokument. De är viktiga för att språk som läses från höger till vänster, som arabiska och hebreiska, ska visas korrekt.

### Kan jag använda Aspose.Words för .NET för att hantera andra typer av textriktningsproblem?
Ja, Aspose.Words för .NET erbjuder omfattande stöd för olika textriktnings- och formateringsbehov, inklusive höger-till-vänster- och vänster-till-höger-språk.

### Är det möjligt att tillämpa Bidi-formatering endast på specifika delar av ett dokument?
Ja, du kan använda Bidi-formatering på specifika stycken eller avsnitt i ditt dokument efter behov.

### I vilka format kan jag spara dokumentet med Bidi-markeringar?
I det visade exemplet sparas dokumentet som en textfil. Aspose.Words har dock även stöd för att spara dokument i olika format samtidigt som Bidi-markeringar bevaras.

### Var kan jag hitta mer information om Aspose.Words för .NET?
Du kan utforska mer om Aspose.Words för .NET via [Aspose-dokumentation](https://reference.aspose.com/words/net/) och få tillgång till [Supportforum](https://forum.aspose.com/c/words/8) för ytterligare hjälp.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}