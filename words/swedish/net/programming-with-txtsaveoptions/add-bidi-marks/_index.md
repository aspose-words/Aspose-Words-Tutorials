---
title: Lägg till Bidi-märken i Word-dokument
linktitle: Lägg till Bidi-märken i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till dubbelriktade (Bidi)-märken i Word-dokument med Aspose.Words för .NET med den här guiden. Säkerställ korrekt textriktning för flerspråkigt innehåll.
weight: 10
url: /sv/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till Bidi-märken i Word-dokument

## Introduktion

I dokumentbehandlingens värld kan dubbelriktad (Bidi) text ofta vara lite knepig att hantera. Detta gäller särskilt när man har att göra med språk som har olika textriktningar, som arabiska eller hebreiska. Lyckligtvis gör Aspose.Words för .NET det enkelt att hantera sådana scenarier. I den här handledningen går vi igenom hur du lägger till Bidi-märken i ett Word-dokument med Aspose.Words för .NET.

## Förutsättningar

Innan vi dyker in i koden, se till att du har följande:

1. Aspose.Words för .NET: Du måste ha Aspose.Words för .NET installerat. Du kan ladda ner den från[Aspose Nedladdningssida](https://releases.aspose.com/words/net/).
2. .NET Framework eller .NET Core: Se till att du har en kompatibel .NET-miljö inställd för att köra exemplen.
3. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# och grundläggande funktioner i .NET.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden. Så här kan du inkludera dem i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Låt oss dela upp processen att lägga till Bidi-märken i ett Word-dokument i tydliga steg. Varje steg guidar dig genom koden och dess syfte.

## Steg 1: Konfigurera ditt dokument

 Börja med att skapa en ny instans av`Document` klass och a`DocumentBuilder` för att lägga till innehåll i dokumentet.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Skapa dokumentet och lägg till innehåll
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 I det här steget initierar du ett nytt Word-dokument och ställer in en`DocumentBuilder` för att underlätta infogning av innehåll.

## Steg 2: Lägg till innehåll i ditt dokument

Lägg sedan till lite text i ditt dokument. Här kommer vi att lägga till text på olika språk för att illustrera Bidi-texthantering.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Här lägger vi först till en vanlig engelsk fras. Sedan aktiverar vi Bidi-textformatering för den efterföljande texten, som är skriven på hebreiska och arabiska. Detta visar hur man införlivar dubbelriktad text.

## Steg 3: Konfigurera sparalternativ för Bidi-märken

 För att säkerställa att Bidi-märkena sparas korrekt i dokumentet måste du konfigurera`TxtSaveOptions` och aktivera`AddBidiMarks` alternativ.

```csharp
// Lägg till Bidi-märken
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 I det här steget skapar vi en instans av`TxtSaveOptions` och ställ in`AddBidiMarks`egendom till`true`. Detta säkerställer att Bidi-märkena ingår när du sparar dokumentet som en textfil.

## Slutsats

Att lägga till Bidi-märken i dina Word-dokument kan vara ett avgörande steg när du hanterar flerspråkigt innehåll som inkluderar språk med olika textriktningar. Med Aspose.Words för .NET är denna process enkel och effektiv. Genom att följa stegen som beskrivs ovan kan du säkerställa att dina dokument korrekt representerar Bidi-text, vilket förbättrar läsbarheten och noggrannheten.

## FAQ's

### Vad är Bidi-märken och varför är de viktiga?
Bidi-märken är specialtecken som används för att styra textens riktning i dokument. De är viktiga för att korrekt visa språk som läser från höger till vänster, som arabiska och hebreiska.

### Kan jag använda Aspose.Words för .NET för att hantera andra typer av textriktningsproblem?
Ja, Aspose.Words för .NET ger omfattande stöd för olika textriktnings- och formateringsbehov, inklusive höger till vänster och vänster till höger språk.

### Är det möjligt att tillämpa Bidi-formatering endast på specifika delar av ett dokument?
Ja, du kan använda Bidi-formatering på specifika stycken eller avsnitt av ditt dokument efter behov.

### Vilka format kan jag spara dokumentet i med Bidi-märken?
I exemplet sparas dokumentet som en textfil. Men Aspose.Words stöder också att spara dokument i olika format samtidigt som Bidi-märken bevaras.

### Var kan jag hitta mer information om Aspose.Words för .NET?
 Du kan utforska mer om Aspose.Words för .NET genom[Aspose dokumentation](https://reference.aspose.com/words/net/) och få tillgång till[Supportforum](https://forum.aspose.com/c/words/8) för ytterligare hjälp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
