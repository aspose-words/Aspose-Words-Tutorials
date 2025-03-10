---
title: Escape URI i PDF-dokument
linktitle: Escape URI i PDF-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du undkommer URIer i PDF-filer med Aspose.Words för .NET. Denna detaljerade guide leder dig genom processen steg för steg.
weight: 10
url: /sv/net/programming-with-pdfsaveoptions/escape-uri/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Escape URI i PDF-dokument

## Introduktion

Hej där! Har du någonsin undrat hur man hanterar URI:er när du sparar ett Word-dokument som PDF med Aspose.Words för .NET? Du är på rätt plats! Idag ska vi dyka djupt ner i flyktiga URI:er i PDF-dokument för att säkerställa att de fungerar korrekt när ditt dokument konverteras. Låt oss ge oss ut på denna resa tillsammans, steg-för-steg, så att du förstår varje koncept på vägen.

## Förutsättningar

Innan vi börjar, låt oss se till att du har allt du behöver:

1.  Aspose.Words för .NET: Se till att du har den senaste versionen. Du kan ladda ner den[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan .NET-utvecklingsmiljö.
3. Grundläggande kunskaper om C#: Denna handledning förutsätter att du har en grundläggande förståelse för C#-programmering.

## Importera namnområden

Först och främst måste du importera de nödvändiga namnrymden. Detta är avgörande för att få tillgång till Aspose.Words-funktioner.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Okej, låt oss dela upp processen i smältbara steg. Följ med så blir du proffs på att fly URI på nolltid!

## Steg 1: Konfigurera din dokumentkatalog

Innan du dyker in i koden, ställ in sökvägen till din dokumentkatalog. Det är här dina filer kommer att sparas.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara ditt PDF-dokument.

## Steg 2: Skapa ett nytt dokument

Därefter skapar vi ett nytt dokument med Aspose.Words. Detta dokument kommer att fungera som vår arbetsyta för att infoga hyperlänkar.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Här,`Document` är ditt nya Word-dokument och`DocumentBuilder` är en hjälpklass som förenklar processen för att skapa dokument.

## Steg 3: Infoga en hyperlänk

Låt oss nu infoga en hyperlänk i dokumentet. Den här hyperlänken kommer att vara i fokus för vår URI-escape-process.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose", false);
```

 I den här raden,`"Testlink"` är visningstexten för hyperlänken, och`"https://www.google.com/search?q= aspose"` är URL:en. De`false` parametern indikerar att länken inte ska formateras som en hyperlänk (dvs. den kommer inte att vara understruken och blå).

## Steg 4: Spara dokumentet som en PDF

Slutligen, spara dokumentet som en PDF. Det är här Aspose.Words tar hand om att undvika URI:n i PDF-utdata.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

 Denna rad sparar dokumentet i den angivna katalogen med filnamnet`WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## Slutsats

Och där har du det! Du har precis lärt dig hur du undkommer URI när du sparar ett Word-dokument som en PDF med Aspose.Words för .NET. Denna process säkerställer att dina hyperlänkar förblir funktionella och korrekt formaterade i den resulterande PDF-filen. 

Kom ihåg att att behärska dessa små men betydelsefulla tekniker kan avsevärt förbättra kvaliteten och funktionaliteten hos dina dokument. Glad kodning!

## FAQ's

### Vad är Aspose.Words för .NET?

Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument i .NET-applikationer.

### Varför är URI-escape viktigt i PDF-filer?

URI-escape säkerställer att specialtecken i URL:er tolkas korrekt, förhindrar trasiga länkar och säkerställer att de fungerar som avsett.

### Kan jag använda andra typer av länkar i Aspose.Words för .NET?

Absolut! Aspose.Words stöder olika typer av länkar, inklusive interna dokumentlänkar, bokmärken och externa webbadresser.

### Hur kan jag få en gratis provversion av Aspose.Words för .NET?

 Du kan få en gratis provperiod[här](https://releases.aspose.com/).

### Var kan jag hitta mer detaljerad dokumentation om Aspose.Words för .NET?

 Du kan hitta den detaljerade dokumentationen[här](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
