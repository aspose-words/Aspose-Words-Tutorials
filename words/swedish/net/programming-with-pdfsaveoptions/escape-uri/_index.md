---
"description": "Lär dig hur du använder Aspose.Words för .NET för att ta bort URI&#58;er. Den här detaljerade guiden vägleder dig genom processen steg för steg."
"linktitle": "Escape-URI i PDF-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Escape-URI i PDF-dokument"
"url": "/sv/net/programming-with-pdfsaveoptions/escape-uri/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Escape-URI i PDF-dokument

## Introduktion

Hej! Har du någonsin undrat hur man hanterar URI:er när man sparar ett Word-dokument som PDF med Aspose.Words för .NET? Då har du kommit rätt! Idag ska vi fördjupa oss i hur man använder escape-URI:er i PDF-dokument för att säkerställa att de fungerar korrekt när dokumentet konverteras. Låt oss ge oss ut på den här resan tillsammans, steg för steg, och se till att du förstår varje koncept längs vägen.

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver:

1. Aspose.Words för .NET: Se till att du har den senaste versionen. Du kan ladda ner den [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan .NET-utvecklingsmiljö.
3. Grundläggande kunskaper i C#: Den här handledningen förutsätter att du har grundläggande förståelse för C#-programmering.

## Importera namnrymder

Först och främst måste du importera de nödvändiga namnrymderna. Detta är avgörande för att komma åt Aspose.Words-funktioner.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Okej, låt oss dela upp processen i lättsmälta steg. Följ med så blir du ett proffs på att escape URI:er på nolltid!

## Steg 1: Konfigurera din dokumentkatalog

Innan du går in i koden, ange sökvägen till din dokumentkatalog. Det är här dina filer kommer att sparas.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara ditt PDF-dokument.

## Steg 2: Skapa ett nytt dokument

Nästa steg är att skapa ett nytt dokument med Aspose.Words. Dokumentet kommer att fungera som vår arbetsyta för att infoga hyperlänkar.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Här, `Document` är ditt nya Word-dokument, och `DocumentBuilder` är en hjälpklass som förenklar processen att skapa dokument.

## Steg 3: Infoga en hyperlänk

Nu ska vi infoga en hyperlänk i dokumentet. Denna hyperlänk kommer att vara fokus för vår URI-escape-process.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose", false);
```

I den här raden, `"Testlink"` är visningstexten för hyperlänken, och `"https://www.google.com/search?q= aspose"` är URL:en. Den `false` Parametern anger att länken inte ska formateras som en hyperlänk (dvs. den kommer inte att vara understruken och blå).

## Steg 4: Spara dokumentet som PDF

Slutligen, spara dokumentet som en PDF. Det är här Aspose.Words tar hand om att escape URI:n i PDF-utdata.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

Den här raden sparar dokumentet till den angivna katalogen med filnamnet `WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## Slutsats

Och där har du det! Du har precis lärt dig hur man escapear URI:er när du sparar ett Word-dokument som en PDF med Aspose.Words för .NET. Den här processen säkerställer att dina hyperlänkar förblir funktionella och korrekt formaterade i den resulterande PDF-filen. 

Kom ihåg att behärskning av dessa små men viktiga tekniker kan avsevärt förbättra kvaliteten och funktionaliteten hos dina dokument. Lycka till med kodningen!

## Vanliga frågor

### Vad är Aspose.Words för .NET?

Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, manipulera och konvertera Word-dokument i .NET-applikationer.

### Varför är URI-escape viktigt i PDF-filer?

URI-escape säkerställer att specialtecken i URL:er tolkas korrekt, vilket förhindrar trasiga länkar och säkerställer att de fungerar som avsett.

### Kan jag använda andra typer av länkar i Aspose.Words för .NET?

Absolut! Aspose.Words stöder olika typer av länkar, inklusive interna dokumentlänkar, bokmärken och externa webbadresser.

### Hur kan jag få en gratis provversion av Aspose.Words för .NET?

Du kan få en gratis provperiod [här](https://releases.aspose.com/).

### Var kan jag hitta mer detaljerad dokumentation om Aspose.Words för .NET?

Du hittar den detaljerade dokumentationen [här](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}