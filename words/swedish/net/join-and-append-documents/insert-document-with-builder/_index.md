---
title: Infoga dokument med Builder
linktitle: Infoga dokument med Builder
second_title: Aspose.Words Document Processing API
description: Lär dig hur du slår samman två Word-dokument med Aspose.Words för .NET. Steg-för-steg-guide för att infoga ett dokument med DocumentBuilder och bevara formateringen.
weight: 10
url: /sv/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga dokument med Builder

## Introduktion

Så du har två Word-dokument och du vill slå samman dem till ett. Du kanske tänker: "Finns det ett enkelt sätt att göra detta programmatiskt?" Absolut! Idag ska jag gå igenom processen att infoga ett dokument i ett annat med hjälp av Aspose.Words for .NET-biblioteket. Den här metoden är väldigt praktisk, speciellt när du har att göra med stora dokument eller behöver automatisera processen. Låt oss dyka direkt in!

## Förutsättningar

Innan vi börjar, låt oss se till att du har allt du behöver:

1.  Aspose.Words för .NET: Om du inte redan har gjort det kan du ladda ner det från[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Se till att du har Visual Studio eller någon annan lämplig IDE installerad.
3. Grundläggande kunskaper om C#: En liten förtrogenhet med C# kommer att räcka långt.

## Importera namnområden

Först och främst måste du importera de nödvändiga namnområdena för att komma åt Aspose.Words-bibliotekets funktioner. Så här kan du göra det:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nu när vi har våra förutsättningar på plats, låt oss bryta ner processen steg för steg.

## Steg 1: Konfigurera din dokumentkatalog

Innan vi börjar koda måste du ange sökvägen till din dokumentkatalog. Det är här dina käll- och måldokument lagras.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där dina dokument finns. Detta kommer att hjälpa programmet att enkelt hitta dina filer.

## Steg 2: Ladda käll- och måldokument

Därefter måste vi ladda de dokument vi vill arbeta med. I det här exemplet har vi ett källdokument och ett måldokument.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

 Här använder vi`Document` klass från Aspose.Words-biblioteket för att ladda våra dokument. Se till att filnamnen matchar dem i din katalog.

## Steg 3: Skapa ett DocumentBuilder-objekt

 De`DocumentBuilder` class är ett kraftfullt verktyg i Aspose.Words-biblioteket. Det tillåter oss att navigera och manipulera dokumentet.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

 I det här steget har vi skapat en`DocumentBuilder` objekt för vårt destinationsdokument. Detta hjälper oss att infoga innehåll i dokumentet.

## Steg 4: Flytta till slutet av dokumentet

Vi måste flytta byggarmarkören till slutet av måldokumentet innan vi infogar källdokumentet.

```csharp
builder.MoveToDocumentEnd();
```

Detta säkerställer att källdokumentet infogas i slutet av måldokumentet.

## Steg 5: Infoga en sidbrytning

För att hålla det snyggt, låt oss lägga till en sidbrytning innan vi infogar källdokumentet. Detta kommer att starta innehållet i källdokumentet på en ny sida.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

En sidbrytning säkerställer att källdokumentets innehåll börjar på en ny sida, vilket gör att det sammanslagna dokumentet ser professionellt ut.

## Steg 6: Infoga källdokumentet

Nu kommer den spännande delen - att faktiskt infoga källdokumentet i måldokumentet.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

 Med hjälp av`InsertDocument` metod kan vi infoga hela källdokumentet i måldokumentet. De`ImportFormatMode.KeepSourceFormatting` säkerställer att formateringen av källdokumentet bevaras.

## Steg 7: Spara det sammanslagna dokumentet

Slutligen, låt oss spara det sammanslagna dokumentet. Detta kommer att kombinera käll- och måldokumenten till en fil.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Genom att spara dokumentet slutför vi processen att slå samman de två dokumenten. Ditt nya dokument är nu klart och sparat i den angivna katalogen.

## Slutsats

Och där har du det! Du har framgångsrikt infogat ett dokument i ett annat med Aspose.Words för .NET. Denna metod är inte bara effektiv utan bevarar också formateringen av båda dokumenten, vilket säkerställer en sömlös sammanslagning. Oavsett om du arbetar med ett engångsprojekt eller behöver automatisera dokumentbehandlingen, har Aspose.Words för .NET dig täckt.

## FAQ's

### Vad är Aspose.Words för .NET?  
Aspose.Words för .NET är ett kraftfullt bibliotek som låter utvecklare skapa, redigera, konvertera och manipulera Word-dokument programmatiskt.

### Kan jag behålla formateringen av källdokumentet?  
 Ja, genom att använda`ImportFormatMode.KeepSourceFormatting`, formateringen av källdokumentet bevaras när det infogas i måldokumentet.

### Behöver jag en licens för att använda Aspose.Words för .NET?  
 Ja, Aspose.Words för .NET kräver en licens för full funktionalitet. Du kan få en[tillfällig licens](https://purchase.aspose.com/temporary-license/) för utvärdering.

### Kan jag automatisera denna process?  
Absolut! Metoden som beskrivs kan införlivas i större applikationer för att automatisera dokumentbearbetningsuppgifter.

### Var kan jag hitta mer resurser och support?  
 För mer information kan du kontrollera[dokumentation](https://reference.aspose.com/words/net/) , eller besök[supportforum](https://forum.aspose.com/c/words/8) för hjälp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
