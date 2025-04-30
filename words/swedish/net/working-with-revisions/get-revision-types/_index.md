---
"description": "Lär dig hur du hämtar revisionstyper för ord i ett Word-dokument med Aspose.Words för .NET. Den här steg-för-steg-guiden hjälper dig att hantera dokumentrevisioner effektivt."
"linktitle": "Hämta revisionstyper av ord"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Hämta revisionstyper av ord"
"url": "/sv/net/working-with-revisions/get-revision-types/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hämta revisionstyper av ord

## Introduktion

Har du någonsin befunnit dig knädjupt i ett hav av dokumentrevisioner och undrat vem som flyttade vad och när? Du är inte ensam. Att hantera dokumentrevisioner kan vara en mödosam uppgift, särskilt när man har att göra med omfattande dokument. Men oroa dig inte! Med Aspose.Words för .NET kan du enkelt identifiera och hantera dessa revisioner. I den här guiden guidar vi dig genom en steg-för-steg-process för hur du får revisionstyper av ord i ett Word-dokument med hjälp av Aspose.Words för .NET. Så spänn fast säkerhetsbältet och låt oss dyka in!

## Förkunskapskrav

Innan vi börjar med lite kod, finns det några saker du behöver:

1. Aspose.Words för .NET-biblioteket: Om du inte redan har gjort det, ladda ner det från [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan .NET-kompatibel IDE.
3. Grundläggande kunskaper i C#: Förståelse för programmeringsspråket C# är meriterande.
4. Ett Word-dokument med revideringar: Se till att du har en `.docx` fil med spårade ändringar för att testa koden.

## Importera namnrymder

För att komma igång måste du importera de nödvändiga namnrymderna i ditt C#-projekt. Detta ger dig tillgång till funktionerna som tillhandahålls av Aspose.Words för .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Låt oss dela upp exemplet i flera steg för bättre förståelse och implementering.

## Steg 1: Konfigurera din dokumentkatalog

Först och främst måste du ange sökvägen till din dokumentkatalog. Det är här ditt Word-dokument med ändringarna kommer att finnas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentmapp.

## Steg 2: Ladda ditt Word-dokument

Sedan behöver du ladda Word-dokumentet till ditt projekt. Dokumentet ska innehålla de revisioner som du vill analysera.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

Se till att filen `Revisions.docx` finns i den angivna katalogen.

## Steg 3: Få åtkomst till styckesamlingen

Nu när ditt dokument är laddat behöver du komma åt styckena i den första delen av dokumentets brödtext. Detta hjälper dig att gå igenom varje stycke för att kontrollera om det finns några revideringar.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Steg 4: Gå igenom stycken och kontrollera om det finns revideringar

Det är här magin händer. Du kommer att gå igenom varje stycke och kontrollera om det har flyttats (borttaget eller infogats).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

Denna loop går igenom varje stycke och använder `IsMoveFromRevision` och `IsMoveToRevision` egenskaper för att avgöra om stycket flyttades (raderades) eller flyttades (infogades).

## Slutsats

Och där har du det! Med bara några få rader kod kan du enkelt identifiera typerna av revisioner i ditt Word-dokument med hjälp av Aspose.Words för .NET. Detta kraftfulla bibliotek gör hanteringen av dokumentrevisioner till en barnlek, så att du kan fokusera på viktigare uppgifter. 

## Vanliga frågor

### Kan jag använda Aspose.Words för .NET för att spåra ändringar gjorda av specifika användare?

Ja, Aspose.Words för .NET tillhandahåller funktioner för att komma åt revisionsinformation, inklusive vem som skapat ändringarna.

### Finns det en gratis testversion av Aspose.Words för .NET?

Absolut! Du kan få en gratis provperiod [här](https://releases.aspose.com/).

### Hur kan jag ansöka om en tillfällig licens för Aspose.Words för .NET?

Du kan begära och ansöka om ett tillfälligt körkort från [här](https://purchase.aspose.com/temporary-license/).

### Var kan jag hitta mer detaljerad dokumentation för Aspose.Words för .NET?

Detaljerad dokumentation finns tillgänglig på [Aspose webbplats](https://reference.aspose.com/words/net/).

### Kan jag använda Aspose.Words för .NET i ett icke-kommersiellt projekt?

Ja, Aspose.Words för .NET kan användas i både kommersiella och icke-kommersiella projekt, men se till att kontrollera licensvillkoren.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}