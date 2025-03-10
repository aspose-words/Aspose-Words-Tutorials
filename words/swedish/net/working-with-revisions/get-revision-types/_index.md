---
title: Få revisionstyper av ord
linktitle: Få revisionstyper av ord
second_title: Aspose.Words Document Processing API
description: Lär dig hur du får versionstyper av ord i ett Word-dokument med Aspose.Words för .NET. Den här steg-för-steg-guiden hjälper dig att hantera dokumentrevisioner effektivt.
weight: 10
url: /sv/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Få revisionstyper av ord

## Introduktion

Har du någonsin befunnit dig i ett hav av dokumentrevisioner och undrat vem som flyttade vad och när? Du är inte ensam. Att hantera dokumentrevideringar kan vara en tråkig uppgift, särskilt när det handlar om omfattande dokument. Men oroa dig inte! Med Aspose.Words för .NET kan du enkelt identifiera och hantera dessa revisioner. I den här guiden går vi igenom en steg-för-steg-process om hur du får versionstyper av ord i ett Word-dokument med Aspose.Words för .NET. Så spänn på dig och låt oss dyka in!

## Förutsättningar

Innan vi smutsar ner händerna med lite kod finns det några saker du behöver:

1.  Aspose.Words för .NET Library: Om du inte redan har gjort det, ladda ner det från[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan .NET-kompatibel IDE.
3. Grundläggande kunskaper i C#: Förståelse av C# programmeringsspråk kommer att vara fördelaktigt.
4.  Ett Word-dokument med ändringar: Se till att du har en`.docx`fil med spårade ändringar för att testa koden.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden i ditt C#-projekt. Detta ger dig tillgång till funktionerna som tillhandahålls av Aspose.Words för .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Låt oss dela upp exemplet i flera steg för bättre förståelse och implementering.

## Steg 1: Konfigurera din dokumentkatalog

Först och främst måste du definiera sökvägen till din dokumentkatalog. Det är här ditt Word-dokument med revisioner kommer att finnas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentmapp.

## Steg 2: Ladda ditt Word-dokument

Därefter måste du ladda Word-dokumentet i ditt projekt. Det här dokumentet bör ha de revisioner som du vill analysera.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

 Se till att filen`Revisions.docx` finns i den angivna katalogen.

## Steg 3: Öppna styckesamlingen

Nu när ditt dokument är laddat måste du komma åt styckena i den första delen av dokumentets brödtext. Detta hjälper dig att iterera igenom varje stycke för att leta efter ändringar.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Steg 4: Iterera genom stycken och leta efter ändringar

Här händer magin. Du går igenom varje stycke och kontrollerar om det har flyttats (raderats eller infogats).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

 Denna loop går igenom varje stycke och använder`IsMoveFromRevision` och`IsMoveToRevision` egenskaper för att avgöra om stycket har flyttats (raderats) eller flyttats (infogats).

## Slutsats

Och där har du det! Med bara några rader kod kan du enkelt identifiera typerna av revisioner i ditt Word-dokument med Aspose.Words för .NET. Detta kraftfulla bibliotek gör det enkelt att hantera dokumentrevideringar, vilket gör att du kan fokusera på viktigare uppgifter. 

## FAQ's

### Kan jag använda Aspose.Words för .NET för att spåra ändringar gjorda av specifika användare?

Ja, Aspose.Words för .NET tillhandahåller funktionalitet för att komma åt revisionsdetaljer, inklusive författaren till ändringarna.

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?

 Absolut! Du kan få en gratis provperiod[här](https://releases.aspose.com/).

### Hur kan jag ansöka om en tillfällig licens för Aspose.Words för .NET?

 Du kan begära och ansöka om en tillfällig licens från[här](https://purchase.aspose.com/temporary-license/).

### Var kan jag hitta mer detaljerad dokumentation för Aspose.Words för .NET?

 Detaljerad dokumentation finns tillgänglig på[Aspose hemsida](https://reference.aspose.com/words/net/).

### Kan jag använda Aspose.Words för .NET i ett icke-kommersiellt projekt?

Ja, Aspose.Words för .NET kan användas i både kommersiella och icke-kommersiella projekt, men se till att kontrollera licensvillkoren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
