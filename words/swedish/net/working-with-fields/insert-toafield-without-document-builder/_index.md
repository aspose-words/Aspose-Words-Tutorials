---
title: Infoga TOA-fält utan dokumentbyggare
linktitle: Infoga TOA-fält utan dokumentbyggare
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar ett TOA-fält utan att använda ett dokumentbyggare i Aspose.Words för .NET. Följ vår steg-för-steg-guide för att effektivt hantera juridiska hänvisningar.
weight: 10
url: /sv/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga TOA-fält utan dokumentbyggare

## Introduktion

Att skapa ett Table of Authorities-fält (TOA) i ett Word-dokument kan kännas som att lägga ihop ett komplext pussel. Men med hjälp av Aspose.Words för .NET blir processen smidig och okomplicerad. I den här artikeln guidar vi dig genom stegen för att infoga ett TOA-fält utan att använda ett dokumentbyggare, vilket gör det enkelt för dig att hantera dina citat och juridiska referenser i dina Word-dokument.

## Förutsättningar

Innan vi dyker in i handledningen, låt oss täcka det väsentliga du behöver:

-  Aspose.Words för .NET: Se till att du har den senaste versionen installerad. Du kan ladda ner den från[Aspose hemsida](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: En .NET-kompatibel IDE som Visual Studio.
- Grundläggande C#-kunskap: Att förstå grundläggande C#-syntax och begrepp kommer att vara till hjälp.
- Exempel på Word-dokument: Skapa eller ha ett exempeldokument redo där du vill infoga TOA-fältet.

## Importera namnområden

För att komma igång måste du importera de nödvändiga namnrymden från Aspose.Words-biblioteket. Denna inställning säkerställer att du har tillgång till alla klasser och metoder som krävs för dokumentmanipulation.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Låt oss dela upp processen i enkla steg som är lätta att följa. Vi guidar dig genom varje steg och förklarar vad varje del av kod gör och hur den bidrar till att skapa TOA-fältet.

## Steg 1: Initiera dokumentet

 Först måste du skapa en instans av`Document` klass. Detta objekt representerar Word-dokumentet du arbetar med.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Den här koden initierar ett nytt Word-dokument. Du kan se det som att du skapar en tom duk där du lägger till ditt innehåll.

## Steg 2: Skapa och konfigurera TA-fältet

Därefter lägger vi till ett TA-fält (Table of Authorities). Detta fält markerar de poster som kommer att visas i TOA.

```csharp
Paragraph para = new Paragraph(doc);

// Vi vill infoga TA- och TOA-fält så här:
// { TA \c 1 \l "Värde 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Här är en uppdelning:
- Paragraph para = new Paragraph(doc);: Skapar ett nytt stycke i dokumentet.
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Lägger till ett TA-fält till stycket. De`FieldType.FieldTOAEntry` anger att detta är ett TOA-inmatningsfält.
- fieldTA.EntryCategory = "1";: Ställer in postkategorin. Detta är användbart för att kategorisera olika typer av poster.
- fieldTA.LongCitation = "Värde 0";: Anger den långa citattexten. Det här är texten som kommer att visas i TOA.
- doc.FirstSection.Body.AppendChild(para);: Lägger till stycket med TA-fältet till dokumentets brödtext.

## Steg 3: Lägg till TOA-fältet

Nu kommer vi att infoga det faktiska TOA-fältet som kompilerar alla TA-poster i en tabell.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

I det här steget:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Lägger till ett TOA-fält till stycket.
- fieldToa.EntryCategory = "1";: Filtrerar posterna så att de endast inkluderar de markerade med kategori "1".

## Steg 4: Uppdatera TOA-fältet

När du har infogat TOA-fältet måste du uppdatera det för att säkerställa att det återspeglar de senaste posterna.

```csharp
fieldToa.Update();
```

Detta kommando uppdaterar TOA-fältet och säkerställer att alla markerade poster visas korrekt i tabellen.

## Steg 5: Spara dokumentet

Slutligen, spara ditt dokument med det nyligen tillagda TOA-fältet.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

 Denna kodrad sparar dokumentet i den angivna katalogen. Se till att byta ut`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara din fil.

## Slutsats

Och där har du det! Du har framgångsrikt lagt till ett TOA-fält i ett Word-dokument utan att använda en dokumentbyggare. Genom att följa dessa steg kan du effektivt hantera hänvisningar och skapa omfattande tabeller över myndigheter i dina juridiska dokument. Aspose.Words för .NET gör denna process smidig och effektiv, vilket ger dig verktygen för att hantera komplexa dokumentuppgifter med lätthet.

## FAQ's

### Kan jag lägga till flera TA-fält med olika kategorier?
 Ja, du kan lägga till flera TA-fält med olika kategorier genom att ställa in`EntryCategory`egendom i enlighet därmed.

### Hur kan jag anpassa utseendet på TOA?
Du kan anpassa TOA:s utseende genom att ändra TOA-fältets egenskaper, såsom inmatningsformatering och kategorietiketter.

### Är det möjligt att uppdatera TOA-fältet automatiskt?
 Medan du kan uppdatera TOA-fältet manuellt med hjälp av`Update` metod, Aspose.Words stöder för närvarande inte automatiska uppdateringar av dokumentändringar.

### Kan jag lägga till TA-fält programmatiskt i specifika delar av dokumentet?
Ja, du kan lägga till TA-fält på specifika platser genom att infoga dem i önskade stycken eller avsnitt.

### Hur hanterar jag flera TOA-fält i ett enda dokument?
 Du kan hantera flera TOA-fält genom att tilldela olika`EntryCategory` värden och se till att varje TOA-fält filtrerar poster baserat på sin kategori.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
