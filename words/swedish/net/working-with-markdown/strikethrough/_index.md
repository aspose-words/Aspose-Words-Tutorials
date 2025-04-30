---
"description": "Lär dig hur du använder genomstruken formatering på text med Aspose.Words för .NET med vår steg-för-steg-guide. Förbättra dina dokumentbehandlingsfärdigheter."
"linktitle": "Genomstruken"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Genomstruken"
"url": "/sv/net/working-with-markdown/strikethrough/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Genomstruken

## Introduktion

Välkommen till den här detaljerade guiden om hur du använder genomstruken formatering på text med Aspose.Words för .NET. Om du vill förbättra dina dokumentbehandlingsfärdigheter och ge din text en unik touch har du kommit rätt. Nu kör vi!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

- Aspose.Words för .NET: Ladda ner det [här](https://releases.aspose.com/words/net/).
- .NET Framework: Se till att du har .NET Framework installerat på ditt system.
- Utvecklingsmiljö: En IDE som Visual Studio.
- Grundläggande kunskaper i C#: Bekantskap med C#-programmering är nödvändig.

## Importera namnrymder

För att börja måste du importera de nödvändiga namnrymderna. Dessa är viktiga för att komma åt Aspose.Words-biblioteket och dess funktioner.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Initiera DocumentBuilder

De `DocumentBuilder` klassen är ett kraftfullt verktyg i Aspose.Words som låter dig enkelt lägga till innehåll i ditt dokument.

```csharp
// Initiera en DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Steg 2: Ställ in egenskapen Strikethrough

Nu ska vi tillämpa egenskapen genomstrykning på vår text. Detta innebär att ställa in `StrikeThrough` egendomen tillhörande `Font` invända mot `true`.

```csharp
// Gör texten genomstruken.
builder.Font.StrikeThrough = true;
```

## Steg 3: Skriv text med genomstruken text

Med egenskapen "streckthrough" inställd kan vi nu lägga till vår text. `Writeln` Metoden lägger till texten i dokumentet.

```csharp
// Skriv text med genomstruken text.
builder.Writeln("This text will be StrikeThrough");
```

## Slutsats

Och där har du det! Du har lagt till genomstruken formatering i din text med Aspose.Words för .NET. Detta kraftfulla bibliotek öppnar upp en värld av möjligheter för dokumentbehandling och anpassning. Oavsett om du skapar rapporter, brev eller någon annan typ av dokument, kommer att bemästra dessa funktioner utan tvekan förbättra din produktivitet och kvaliteten på dina utskrifter.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt dokumentbehandlingsbibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument programmatiskt.

### Kan jag använda Aspose.Words för .NET i ett kommersiellt projekt?
Ja, du kan använda Aspose.Words för .NET i kommersiella projekt. För köpalternativ, besök [köpsida](https://purchase.aspose.com/buy).

### Finns det en gratis testversion av Aspose.Words för .NET?
Ja, du kan ladda ner en gratis provperiod [här](https://releases.aspose.com/).

### Hur får jag support för Aspose.Words för .NET?
Du kan få stöd från Aspose-communityn och experter på [supportforum](https://forum.aspose.com/c/words/8).

### Kan jag använda andra textformateringsalternativ med Aspose.Words för .NET?
Absolut! Aspose.Words för .NET stöder en mängd olika textformateringsalternativ, inklusive fetstil, kursiv stil, understrykning och mer.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}