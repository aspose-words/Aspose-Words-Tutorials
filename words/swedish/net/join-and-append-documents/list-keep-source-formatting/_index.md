---
"description": "Lär dig hur du sammanfogar Word-dokument samtidigt som du bevarar formateringen med Aspose.Words för .NET. Den här handledningen ger steg-för-steg-vägledning för sömlös dokumentsammanfogning."
"linktitle": "Lista Behåll källformatering"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Lista Behåll källformatering"
"url": "/sv/net/join-and-append-documents/list-keep-source-formatting/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lista Behåll källformatering

## Introduktion

I den här handledningen ska vi utforska hur man använder Aspose.Words för .NET för att sammanfoga dokument samtidigt som källformateringen bevaras. Denna funktion är avgörande för scenarier där det är avgörande att behålla dokumentens ursprungliga utseende.

## Förkunskapskrav

Innan du fortsätter, se till att du har följande förutsättningar:

- Visual Studio installerat på din dator.
- Aspose.Words för .NET installerat. Du kan ladda ner det från [här](https://releases.aspose.com/words/net/).
- Grundläggande kunskaper i C#-programmering och .NET-miljö.

## Importera namnrymder

Importera först de nödvändiga namnrymderna till ditt C#-projekt:

```csharp
using Aspose.Words;
```

## Steg 1: Konfigurera ditt projekt

Börja med att skapa ett nytt C#-projekt i Visual Studio. Se till att Aspose.Words för .NET refereras i ditt projekt. Om inte kan du lägga till det via NuGet Package Manager.

## Steg 2: Initiera dokumentvariabler

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Ladda käll- och måldokument
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Document destination with list.docx");
```

## Steg 3: Konfigurera sektionsinställningar

För att bibehålla ett kontinuerligt flöde i det sammanfogade dokumentet, justera avsnittets början:

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

## Steg 4: Sammanfoga dokument

Lägg till innehållet i källdokumentet (`srcDoc`) till destinationsdokumentet (`dstDoc`) samtidigt som den ursprungliga formateringen bibehålls:

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Steg 5: Spara det sammanslagna dokumentet

Slutligen, spara det sammanslagna dokumentet i din angivna katalog:

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.ListKeepSourceFormatting.docx");
```

## Slutsats

Sammanfattningsvis är det enkelt att sammanfoga dokument samtidigt som de behåller sin ursprungliga formatering med Aspose.Words för .NET. Den här handledningen har guidat dig genom processen och säkerställt att ditt sammanfogade dokument behåller källdokumentets layout och stil.

## Vanliga frågor

### Vad händer om mina dokument har olika stilar?
Aspose.Words hanterar olika stilar elegant och bevarar den ursprungliga formateringen så nära som möjligt.

### Kan jag sammanfoga dokument i olika format?
Ja, Aspose.Words stöder sammanfogning av dokument i olika format, inklusive DOCX, DOC, RTF och andra.

### Är Aspose.Words kompatibelt med .NET Core?
Ja, Aspose.Words har fullt stöd för .NET Core, vilket möjliggör utveckling över flera plattformar.

### Hur kan jag hantera stora dokument effektivt?
Aspose.Words tillhandahåller effektiva API:er för dokumenthantering, optimerade för prestanda även med stora dokument.

### Var kan jag hitta fler exempel och dokumentation?
Du kan utforska fler exempel och detaljerad dokumentation på [Aspose.Words-dokumentation](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}