---
"description": "Lär dig hur du sammanfogar Word-dokument samtidigt som du bevarar formateringen med Aspose.Words för .NET. Perfekt för utvecklare som vill automatisera dokumentsammansättningsuppgifter."
"linktitle": "Behåll källformatering"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Behåll källformatering"
"url": "/sv/net/join-and-append-documents/keep-source-formatting/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Behåll källformatering

## Introduktion

den här handledningen utforskar vi hur man sammanfogar och lägger till Word-dokument med hjälp av Aspose.Words för .NET. Detta kraftfulla bibliotek ger utvecklare omfattande möjligheter att manipulera Word-dokument programmatiskt. Vi fokuserar på metoden för att behålla källformateringen intakt under dokumentsammanfogning, vilket säkerställer att de ursprungliga stilarna och layouterna bevaras sömlöst.

## Förkunskapskrav

Innan du börjar med handledningen, se till att du har följande förutsättningar konfigurerade:

- Utvecklingsmiljö: Visual Studio eller någon IDE som stöder .NET-utveckling.
- Aspose.Words för .NET-bibliotek: Ladda ner och installera biblioteket från [här](https://releases.aspose.com/words/net/).
- Grundläggande kunskaper i C#-programmering: Bekantskap med C#-syntax och objektorienterade programmeringskoncept.

## Importera namnrymder

Börja med att importera de nödvändiga namnrymderna i ditt C#-projekt:

```csharp
using Aspose.Words;
```

## Steg 1: Konfigurera ditt projekt

Skapa en ny C#-konsolapplikation i Visual Studio och installera Aspose.Words NuGet-paketet. Det här paketet innehåller de bibliotek som behövs för att arbeta med Word-dokument i ditt projekt.

## Steg 2: Inkludera Aspose.Words-namnrymden

Se till att du inkluderar namnrymden Aspose.Words i början av din C#-fil för att komma åt Aspose.Words-klasserna och metoderna.

## Steg 3: Initiera dokumentsökvägar

Definiera sökvägen till din dokumentkatalog där käll- och destinationsdokumenten finns.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Steg 4: Skapa måldokument

Initiera en ny instans av Document-klassen för att skapa ett måldokument där det sammanfogade innehållet ska lagras.

```csharp
Document dstDoc = new Document();
```

## Steg 5: Ladda källdokument

På samma sätt skapar du ett annat dokumentobjekt för att läsa in källdokumentet som du vill lägga till i måldokumentet.

```csharp
Document srcDoc = new Document();
```

## Steg 6: Lägg till källdokument med bibehållen formatering

För att sammanfoga källdokumentet med måldokumentet samtidigt som den ursprungliga formateringen bevaras, använd AppendDocument-metoden med ImportFormatMode inställt på KeepSourceFormatting.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Steg 7: Spara det sammanslagna dokumentet

Spara slutligen det sammanslagna dokumentet i den angivna katalogen med hjälp av Spara-metoden.

```csharp
dstDoc.Save(dataDir + "MergedDocument.docx");
```

## Slutsats

I den här handledningen har vi gått igenom hur man sammanfogar Word-dokument samtidigt som den ursprungliga formateringen bibehålls med hjälp av Aspose.Words för .NET. Den här metoden säkerställer att stilar, teckensnitt och layouter från källdokumenten integreras sömlöst i destinationsdokumentet, vilket ger en robust lösning för dokumentsammansättningsuppgifter.

## Vanliga frågor

### Kan jag sammanfoga flera dokument i en operation med Aspose.Words för .NET?
Ja, du kan sammanfoga flera dokument genom att lägga till varje dokument i tur och ordning i destinationsdokumentet.

### Bevarar Aspose.Words alla formateringsattribut under dokumentsammanslagning?
Aspose.Words stöder olika importlägen; läget KeepSourceFormatting säkerställer att de flesta formateringsattributen behålls.

### Är Aspose.Words kompatibelt med .NET Core-applikationer?
Ja, Aspose.Words stöder .NET Core, vilket gör att du kan använda det på olika plattformar.

### Hur kan jag hantera stora dokument effektivt med Aspose.Words?
Aspose.Words tillhandahåller effektiva API:er för att arbeta med stora dokument, inklusive funktioner för paginering och minneshantering.

### Var kan jag hitta fler resurser och support för Aspose.Words?
Besök [Aspose.Words för .NET-dokumentation](https://reference.aspose.com/words/net/) för detaljerade API-referenser, exempel och guider.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}