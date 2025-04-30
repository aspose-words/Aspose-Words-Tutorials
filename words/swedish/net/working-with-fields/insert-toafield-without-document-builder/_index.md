---
"description": "Lär dig hur du infogar ett TOA-fält utan att använda en dokumentbyggare i Aspose.Words för .NET. Följ vår steg-för-steg-guide för att effektivt hantera juridiska hänvisningar."
"linktitle": "Infoga TOA-fält utan dokumentbyggare"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga TOA-fält utan dokumentbyggare"
"url": "/sv/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga TOA-fält utan dokumentbyggare

## Introduktion

Att skapa ett TOA-fält (Förteckning över auktoriteter) i ett Word-dokument kan kännas som att lägga ett komplext pussel. Men med hjälp av Aspose.Words för .NET blir processen smidig och okomplicerad. I den här artikeln guidar vi dig genom stegen för att infoga ett TOA-fält utan att använda en dokumentbyggare, vilket gör det enkelt för dig att hantera dina citat och juridiska referenser i dina Word-dokument.

## Förkunskapskrav

Innan vi går in i handledningen, låt oss gå igenom det viktigaste du behöver:

- Aspose.Words för .NET: Se till att du har den senaste versionen installerad. Du kan ladda ner den från [Aspose webbplats](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: En .NET-kompatibel IDE som Visual Studio.
- Grundläggande C#-kunskaper: Att förstå grundläggande C#-syntax och koncept kommer att vara till hjälp.
- Exempel på Word-dokument: Skapa eller ha ett exempeldokument redo där du vill infoga användarvillkorsfältet.

## Importera namnrymder

För att komma igång måste du importera de nödvändiga namnrymderna från Aspose.Words-biblioteket. Denna installation säkerställer att du har tillgång till alla klasser och metoder som krävs för dokumenthantering.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Låt oss dela upp processen i enkla steg som är lätta att följa. Vi guidar dig genom varje steg och förklarar vad varje kodbit gör och hur den bidrar till att skapa TOA-fältet.

## Steg 1: Initiera dokumentet

Först måste du skapa en instans av `Document` klass. Det här objektet representerar Word-dokumentet du arbetar med.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Den här koden initierar ett nytt Word-dokument. Du kan tänka på det som att skapa en tom arbetsyta där du lägger till ditt innehåll.

## Steg 2: Skapa och konfigurera TA-fältet

Nästa steg är att lägga till ett TA-fält (Tabell över auktoriteter). Det här fältet markerar de poster som kommer att visas i användarvillkoren.

```csharp
Paragraph para = new Paragraph(doc);

// Vi vill infoga TA- och TOA-fält så här:
// { TA \c 1 \l "Värde 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Här är en sammanfattning:
- Stycke para = new Stycke(doc);: Skapar ett nytt stycke i dokumentet.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Lägger till ett TA-fält till stycket. De `FieldType.FieldTOAEntry` anger att detta är ett inmatningsfält för användarvillkor.
- fieldTA.EntryCategory = "1";: Anger postkategorin. Detta är användbart för att kategorisera olika typer av poster.
- fieldTA.LongCitation = "Värde 0";: Anger den långa hänvisningstexten. Det här är texten som kommer att visas i användarvillkoren.
- doc.FirstSection.Body.AppendChild(para);: Lägger till stycket med TA-fältet i dokumentets brödtext.

## Steg 3: Lägg till användarvillkorsfältet

Nu infogar vi själva TOA-fältet som sammanställer alla TA-poster i en tabell.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

I det här steget:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Lägger till ett TOA-fält till stycket.
- fieldToa.EntryCategory = "1";: Filtrerar posterna så att endast de som är markerade med kategori "1" inkluderas.

## Steg 4: Uppdatera användarvillkorsfältet

Efter att du har infogat användarvillkorsfältet måste du uppdatera det för att säkerställa att det återspeglar de senaste posterna.

```csharp
fieldToa.Update();
```

Det här kommandot uppdaterar användarvillkorsfältet och säkerställer att alla markerade poster visas korrekt i tabellen.

## Steg 5: Spara dokumentet

Slutligen, spara ditt dokument med det nyligen tillagda användarvillkorsfältet.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Den här kodraden sparar dokumentet i den angivna katalogen. Se till att ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara filen.

## Slutsats

Och där har du det! Du har lagt till ett användarvillkorsfält i ett Word-dokument utan att använda en dokumentbyggare. Genom att följa dessa steg kan du effektivt hantera hänvisningar och skapa omfattande auktoritetsförteckningar i dina juridiska dokument. Aspose.Words för .NET gör den här processen smidig och effektiv, vilket ger dig verktygen för att hantera komplexa dokumentuppgifter med lätthet.

## Vanliga frågor

### Kan jag lägga till flera TA-fält med olika kategorier?
Ja, du kan lägga till flera TA-fält med olika kategorier genom att ställa in `EntryCategory` egendom i enlighet därmed.

### Hur kan jag anpassa utseendet på användarvillkoren?
Du kan anpassa utseendet på användarvillkoret genom att ändra egenskaperna i fältet, till exempel formatering av poster och kategorietiketter.

### Är det möjligt att uppdatera användarvillkorsfältet automatiskt?
Även om du kan uppdatera användarvillkorsfältet manuellt med hjälp av `Update` Metoden Aspose.Words stöder för närvarande inte automatiska uppdateringar av dokumentändringar.

### Kan jag lägga till TA-fält programmatiskt i specifika delar av dokumentet?
Ja, du kan lägga till TA-fält på specifika platser genom att infoga dem i önskade stycken eller avsnitt.

### Hur hanterar jag flera användarvillkorsfält i ett enda dokument?
Du kan hantera flera användarvillkorsfält genom att tilldela olika `EntryCategory` värden och säkerställa att varje TOA-fält filtrerar poster baserat på dess kategori.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}