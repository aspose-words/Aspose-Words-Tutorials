---
title: Genomstruken
linktitle: Genomstruken
second_title: Aspose.Words Document Processing API
description: Lär dig hur du tillämpar genomstruken formatering på text med Aspose.Words för .NET med vår steg-för-steg-guide. Förbättra dina färdigheter i dokumentbehandling.
weight: 10
url: /sv/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Genomstruken

## Introduktion

Välkommen till den här detaljerade guiden om hur du använder genomstruken formatering på text med Aspose.Words för .NET. Om du vill förbättra dina färdigheter i dokumentbehandling och lägga till en unik touch till din text, är du på rätt plats. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

-  Aspose.Words för .NET: Ladda ner det[här](https://releases.aspose.com/words/net/).
- .NET Framework: Se till att du har .NET Framework installerat på ditt system.
- Utvecklingsmiljö: En IDE som Visual Studio.
- Grundläggande kunskaper i C#: Bekantskap med C#-programmering är nödvändig.

## Importera namnområden

Till att börja med måste du importera de nödvändiga namnrymden. Dessa är viktiga för att komma åt Aspose.Words-biblioteket och dess funktioner.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Initiera DocumentBuilder

 De`DocumentBuilder` class är ett kraftfullt verktyg i Aspose.Words som låter dig lägga till innehåll till ditt dokument med lätthet.

```csharp
// Initiera en DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Steg 2: Ställ in genomstruken egenskap

Låt oss nu tillämpa egenskapen genomstruken på vår text. Detta innebär att ställa in`StrikeThrough` egendom av`Font` invända mot`true`.

```csharp
// Gör texten genomstruken.
builder.Font.StrikeThrough = true;
```

## Steg 3: Skriv text med genomstruken

 Med egenskapsuppsättningen genomstruken kan vi nu lägga till vår text. De`Writeln` metod lägger till texten i dokumentet.

```csharp
// Skriv text med Strikethrough.
builder.Writeln("This text will be StrikeThrough");
```

## Slutsats

Och där har du det! Du har framgångsrikt lagt till genomstruken formatering till din text med Aspose.Words för .NET. Detta kraftfulla bibliotek öppnar upp en värld av möjligheter för dokumentbearbetning och anpassning. Oavsett om du skapar rapporter, brev eller någon annan typ av dokument, kommer att behärska dessa funktioner utan tvekan förbättra din produktivitet och kvaliteten på dina utdata.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt dokumentbehandlingsbibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument programmatiskt.

### Kan jag använda Aspose.Words för .NET i ett kommersiellt projekt?
 Ja, du kan använda Aspose.Words för .NET i kommersiella projekt. För inköpsalternativ, besök[köpsida](https://purchase.aspose.com/buy).

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?
 Ja, du kan ladda ner en gratis testversion[här](https://releases.aspose.com/).

### Hur får jag support för Aspose.Words för .NET?
Du kan få stöd från Aspose-gemenskapen och experter på[supportforum](https://forum.aspose.com/c/words/8).

### Kan jag använda andra textformateringsalternativ med Aspose.Words för .NET?
Absolut! Aspose.Words för .NET stöder ett brett utbud av textformateringsalternativ inklusive fetstil, kursiv stil, understrykning och mer.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
