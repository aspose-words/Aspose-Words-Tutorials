---
"description": "Lär dig hur du sömlöst sammanfogar två Word-dokument med Aspose.Words för .NET. Följ vår steg-för-steg-guide för en smidig och effektiv dokumentsammanfogning."
"linktitle": "Gå med kontinuerligt"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Gå med kontinuerligt"
"url": "/sv/net/join-and-append-documents/join-continuous/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gå med kontinuerligt

## Introduktion

Vill du smidigt sammanfoga två Word-dokument till ett utan några brytningar? Aspose.Words för .NET erbjuder ett fantastiskt sätt att uppnå detta genom att använda funktionen för kontinuerlig avsnittsbrytning. Den här handledningen guidar dig steg för steg genom processen, så att du enkelt kan sammanfoga dokument utan problem. Nu kör vi!

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET: Om du inte redan har gjort det, ladda ner och installera [Aspose.Words för .NET](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Du kan använda Visual Studio eller någon annan .NET-utvecklingsmiljö.
- Exempeldokument: Ha två Word-dokument redo som du vill sammanfoga.

## Importera namnrymder

För att använda Aspose.Words för .NET måste du importera de nödvändiga namnrymderna i ditt projekt. Så här gör du:

```csharp
using Aspose.Words;
```

Låt oss nu dela upp exemplet i flera steg för tydlighetens skull.

## Steg 1: Konfigurera din dokumentkatalog

Först måste vi konfigurera katalogen där dina dokument lagras. Detta gör att vår kod kan hitta de filer vi vill sammanfoga.

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där dina dokument lagras.

## Steg 2: Ladda käll- och måldokumenten

Härnäst laddar vi käll- och destinationsdokumenten i vårt program. Det är de två dokumenten du vill sammanfoga.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Se till att filnamnen och sökvägarna matchar de filer du vill använda.

## Steg 3: Ställ in sektionsstart som kontinuerlig

För att innehållet i källdokumentet ska visas direkt efter destinationsdokumentet måste vi ställa in `SectionStart` egenskapen för det första avsnittet i källdokumentet till `Continuous`.

```csharp
// Få dokumentet att visas direkt efter måldokumentets innehåll.
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

Detta säkerställer att det inte blir några pauser mellan dokumenten när de sammanfogas.

## Steg 4: Lägg till källdokumentet

Nu lägger vi till källdokumentet i destinationsdokumentet. Detta steg säkerställer att innehållet från källdokumentet läggs till i slutet av destinationsdokumentet.

```csharp
// Lägg till källdokumentet med de ursprungliga formaten som finns i källdokumentet.
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

Användning `ImportFormatMode.KeepSourceFormatting` säkerställer att formateringen från källdokumentet bevaras i det slutliga sammanfogade dokumentet.

## Steg 5: Spara det sammanslagna dokumentet

Slutligen sparar vi det sammanfogade dokumentet i den angivna katalogen. Detta slutför processen att sammanfoga dokumenten.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.JoinContinuous.docx");
```

Se till att sökvägen och filnamnet är korrekta för dina behov.

## Slutsats

Och där har du det! Med bara några få rader kod har du lyckats slå samman två Word-dokument till ett sammanhängande dokument med hjälp av Aspose.Words för .NET. Denna process är inte bara enkel utan också mycket effektiv, vilket säkerställer att dina dokument behåller sin ursprungliga formatering.

## Vanliga frågor

### Kan jag sammanfoga fler än två dokument?
Ja, du kan upprepa processen för att sammanfoga flera dokument genom att ladda ytterligare dokument och lägga till dem i tur och ordning.

### Kommer den ursprungliga formateringen att bevaras?
Ja, använder `ImportFormatMode.KeepSourceFormatting` säkerställer att formateringen från källdokumentet bevaras.

### Är Aspose.Words för .NET kompatibelt med .NET Core?
Ja, Aspose.Words för .NET är kompatibelt med både .NET Framework och .NET Core.

### Kan jag sammanfoga dokument med olika sidinställningar?
Ja, men du kan behöva justera sidinställningarna för att säkerställa en sömlös sammanfogning.

### Var kan jag få stöd om jag stöter på problem?
Du kan få stöd från Aspose communityforum [här](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}