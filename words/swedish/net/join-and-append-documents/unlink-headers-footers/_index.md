---
title: Ta bort länk sidhuvuden Sidfot
linktitle: Ta bort länk sidhuvuden Sidfot
second_title: Aspose.Words Document Processing API
description: Lär dig hur du kopplar bort sidhuvuden och sidfötter i Word-dokument med Aspose.Words för .NET. Följ vår detaljerade steg-för-steg-guide för att behärska dokumentmanipulation.
weight: 10
url: /sv/net/join-and-append-documents/unlink-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ta bort länk sidhuvuden Sidfot

## Introduktion

dokumentbehandlingens värld kan det ibland vara en utmaning att hålla sidhuvuden och sidfötter konsekventa. Oavsett om du slår samman dokument eller bara vill ha olika sidhuvuden och sidfötter för olika avsnitt är det viktigt att veta hur man kopplar bort dem. Idag ska vi dyka in i hur du kan uppnå detta med Aspose.Words för .NET. Vi delar upp det steg-för-steg så att du enkelt kan följa med. Är du redo att bemästra dokumenthantering? Låt oss komma igång!

## Förutsättningar

Innan vi dyker in i det nitty-gritty, finns det några saker du behöver:

-  Aspose.Words för .NET Library: Du kan ladda ner det från[Aspose releaser sida](https://releases.aspose.com/words/net/).
- .NET Framework: Se till att du har ett kompatibelt .NET Framework installerat.
- IDE: Visual Studio eller någon annan .NET-kompatibel integrerad utvecklingsmiljö.
- Grundläggande förståelse för C#: Du behöver en grundläggande förståelse för programmeringsspråket C#.

## Importera namnområden

För att komma igång, se till att importera de nödvändiga namnrymden i ditt projekt. Detta gör att du kommer åt Aspose.Words-biblioteket och dess funktioner.

```csharp
using Aspose.Words;
```

Låt oss dela upp processen i hanterbara steg för att hjälpa dig att koppla bort sidhuvuden och sidfötter i dina Word-dokument.

## Steg 1: Konfigurera ditt projekt

Först måste du konfigurera din projektmiljö. Öppna din IDE och skapa ett nytt .NET-projekt. Lägg till en referens till Aspose.Words-biblioteket som du laddade ner tidigare.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda källdokumentet

Därefter måste du ladda källdokumentet som du vill ändra. Det här dokumentet kommer att ha sina sidhuvuden och sidfötter bortkopplade.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Steg 3: Ladda destinationsdokumentet

Ladda nu måldokumentet där du ska lägga till källdokumentet efter att du har tagit bort länken till dess sidhuvuden och sidfötter.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Steg 4: Koppla bort sidhuvuden och sidfötter

 Detta steg är avgörande. För att ta bort länkarna till sidhuvuden och sidfötter i källdokumentet från de i måldokumentet, använder du`LinkToPrevious` metod. Denna metod säkerställer att sidhuvuden och sidfötter inte överförs till det bifogade dokumentet.

```csharp
// Ta bort länkarna till sidhuvuden och sidfötter i källdokumentet för att stoppa detta
//från att fortsätta destinationsdokumentets sidhuvuden och sidfötter.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Steg 5: Bifoga källdokumentet

 När du har kopplat bort sidhuvuden och sidfötter kan du lägga till källdokumentet till måldokumentet. Använd`AppendDocument` metod och ställ in importformatläget till`KeepSourceFormatting` för att behålla den ursprungliga formateringen av källdokumentet.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Steg 6: Spara det slutliga dokumentet

Slutligen, spara det nyskapade dokumentet. Det här dokumentet kommer att ha källdokumentets innehåll bifogat till måldokumentet, med sidhuvuden och sidfötter olänkade.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Slutsats

Och där har du det! Genom att följa dessa steg har du lyckats koppla bort sidhuvuden och sidfötter i ditt källdokument och lagt till dem i måldokumentet med Aspose.Words för .NET. Den här tekniken kan vara särskilt användbar när du arbetar med komplexa dokument som kräver olika sidhuvuden och sidfötter för olika avsnitt. Glad kodning!

## FAQ's

### Vad är Aspose.Words för .NET?  
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument i .NET-applikationer. Det låter utvecklare skapa, ändra, konvertera och skriva ut dokument programmatiskt.

### Kan jag koppla bort sidhuvuden och sidfötter endast för specifika avsnitt?  
 Ja, du kan koppla bort sidhuvuden och sidfötter för specifika avsnitt genom att gå till`HeadersFooters` egenskapen för önskad sektion och använda`LinkToPrevious` metod.

### Är det möjligt att behålla originalformateringen av källdokumentet?  
 Ja, när du lägger till källdokumentet, använd`ImportFormatMode.KeepSourceFormatting` alternativet för att behålla den ursprungliga formateringen.

### Kan jag använda Aspose.Words för .NET med andra .NET-språk än C#?  
Absolut! Aspose.Words för .NET kan användas med alla .NET-språk, inklusive VB.NET och F#.

### Var kan jag hitta mer dokumentation och support för Aspose.Words för .NET?  
 Du kan hitta omfattande dokumentation på[Aspose.Words för .NET dokumentationssida](https://reference.aspose.com/words/net/) , och support finns tillgänglig på[Aspose forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
