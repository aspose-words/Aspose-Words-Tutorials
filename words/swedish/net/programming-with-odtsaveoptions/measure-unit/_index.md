---
"description": "Lär dig hur du konfigurerar måttenhetsfunktionen i Aspose.Words för .NET för att bevara dokumentformatering under ODT-konvertering."
"linktitle": "Måttenhet"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Måttenhet"
"url": "/sv/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Måttenhet

## Introduktion

Har du någonsin behövt konvertera dina Word-dokument till olika format men behövt en specifik måttenhet för din layout? Oavsett om du arbetar med tum, centimeter eller punkter är det avgörande att se till att ditt dokument behåller sin integritet under konverteringsprocessen. I den här handledningen går vi igenom hur du konfigurerar måttenhetsfunktionen i Aspose.Words för .NET. Den här kraftfulla funktionen säkerställer att dokumentets formatering bevaras exakt som du behöver den när du konverterar till ODT-format (Open Document Text).

## Förkunskapskrav

Innan du dyker in i koden finns det några saker du behöver för att komma igång:

1. Aspose.Words för .NET: Se till att du har den senaste versionen av Aspose.Words för .NET installerad. Om du inte redan har den kan du ladda ner den från [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio för att skriva och exekvera din C#-kod.
3. Grundläggande kunskaper i C#: Att förstå grunderna i C# hjälper dig att följa handledningen.
4. Ett Word-dokument: Ha ett exempel på ett Word-dokument redo som du kan använda för konvertering.

## Importera namnrymder

Innan vi börjar koda, låt oss se till att vi har importerat de nödvändiga namnrymderna. Lägg till dessa med hjälp av direktiv högst upp i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera din dokumentkatalog

Först måste du ange sökvägen till din dokumentkatalog. Det är här ditt Word-dokument finns och där den konverterade filen kommer att sparas.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Ersätta `"YOUR DOCUMENTS DIRECTORY"` med den faktiska sökvägen till din katalog. Detta säkerställer att din kod vet var den hittar ditt Word-dokument.

## Steg 2: Ladda Word-dokumentet

Nästa steg är att ladda Word-dokumentet som du vill konvertera. Detta görs med hjälp av `Document` klass från Aspose.Words.

```csharp
// Ladda Word-dokumentet
Document doc = new Document(dataDir + "Document.docx");
```

Se till att ditt Word-dokument, med namnet "Document.docx", finns i den angivna katalogen.

## Steg 3: Konfigurera måttenheten

Nu ska vi konfigurera måttenheten för ODT-konverteringen. Det är här magin händer. Vi konfigurerar `OdtSaveOptions` att använda tum som måttenhet.

```csharp
// Konfiguration av säkerhetskopieringsalternativ med funktionen "Måttenhet"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

I det här exemplet ställer vi in måttenheten till tum. Du kan också välja andra enheter, t.ex. `OdtSaveMeasureUnit.Centimeters` eller `OdtSaveMeasureUnit.Points` beroende på dina krav.

## Steg 4: Konvertera dokumentet till ODT

Slutligen konverterar vi Word-dokumentet till ODT-formatet med hjälp av den konfigurerade `OdtSaveOptions`.

```csharp
// Konvertera dokumentet till ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Den här kodraden sparar det konverterade dokumentet i den angivna katalogen med den nya måttenheten tillämpad.

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt konfigurera måttenhetsfunktionen i Aspose.Words för .NET för att säkerställa att dokumentets layout bevaras under konverteringen. Oavsett om du arbetar med tum, centimeter eller punkter har den här handledningen visat dig hur du enkelt kan ta kontroll över dokumentets formatering.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att arbeta med Word-dokument programmatiskt. Det låter utvecklare skapa, modifiera, konvertera och bearbeta Word-dokument utan att behöva Microsoft Word.

### Kan jag använda andra måttenheter än tum?
Ja, Aspose.Words för .NET stöder andra måttenheter som centimeter och punkter. Du kan ange önskad enhet med hjälp av `OdtSaveMeasureUnit` uppräkning.

### Finns det en gratis testversion av Aspose.Words för .NET?
Ja, du kan ladda ner en gratis testversion av Aspose.Words för .NET från [här](https://releases.aspose.com/).

### Var kan jag hitta dokumentation för Aspose.Words för .NET?
Du kan få tillgång till omfattande dokumentation för Aspose.Words för .NET på [den här länken](https://reference.aspose.com/words/net/).

### Hur kan jag få support för Aspose.Words för .NET?
För support kan du besöka Aspose.Words-forumet på [den här länken](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}