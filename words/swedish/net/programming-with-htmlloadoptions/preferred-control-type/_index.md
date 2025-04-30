---
"description": "Lär dig hur du infogar ett kombinationsruteformulärfält i ett Word-dokument med Aspose.Words för .NET. Följ den här steg-för-steg-guiden för sömlös HTML-innehållsintegration."
"linktitle": "Föredragen kontrolltyp i Word-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Föredragen kontrolltyp i Word-dokument"
"url": "/sv/net/programming-with-htmlloadoptions/preferred-control-type/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Föredragen kontrolltyp i Word-dokument

## Introduktion

Vi dyker in i en spännande handledning om hur man arbetar med HTML-inläsningsalternativ i Aspose.Words för .NET, med särskilt fokus på att ställa in önskad kontrolltyp när man infogar ett kombinationsruteformulärfält i ett Word-dokument. Den här steg-för-steg-guiden hjälper dig att förstå hur du effektivt manipulerar och renderar HTML-innehåll i dina Word-dokument med Aspose.Words för .NET.

## Förkunskapskrav

Innan vi går in i koden finns det några saker du behöver ha på plats:

1. Aspose.Words för .NET: Se till att du har biblioteket Aspose.Words för .NET installerat. Du kan ladda ner det från [webbplats](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Du bör ha en utvecklingsmiljö konfigurerad, som Visual Studio.
3. Grundläggande kunskaper i C#: En grundläggande förståelse för C#-programmering är nödvändig för att följa handledningen.
4. HTML-innehåll: Grundläggande kunskaper i HTML är bra eftersom vi kommer att arbeta med HTML-innehåll i det här exemplet.

## Importera namnrymder

Låt oss först importera de namnrymder som behövs för att komma igång:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Nu ska vi dela upp exemplet i flera steg för att säkerställa tydlighet och förståelse.

## Steg 1: Konfigurera ditt HTML-innehåll

Först måste vi definiera HTML-innehållet som vi vill infoga i Word-dokumentet. Här är HTML-kodavsnittet vi kommer att använda:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>item1</option>
            <option value='val2'></option>                        
        </select>
    </html>
";
```

Denna HTML-kod innehåller en enkel kombinationsruta med två alternativ. Vi kommer att ladda HTML-koden till ett Word-dokument och ange hur den ska renderas.

## Steg 2: Definiera dokumentkatalogen

Ange sedan katalogen där ditt Word-dokument ska sparas. Detta hjälper till att organisera dina filer och hålla sökvägshanteringen tydlig.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara ditt Word-dokument.

## Steg 3: Konfigurera HTML-inläsningsalternativ

Här konfigurerar vi HTML-inläsningsalternativen, med särskilt fokus på `PreferredControlType` egenskap. Detta avgör hur kombinationsrutan ska visas i Word-dokumentet.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

Genom att ställa in `PreferredControlType` till `HtmlControlType.StructuredDocumentTag`, ser vi till att kombinationsrutan återges som en strukturerad dokumenttagg (SDT) i Word-dokumentet.

## Steg 4: Ladda HTML-innehållet i dokumentet

Med hjälp av de konfigurerade laddningsalternativen laddar vi HTML-innehållet till ett nytt Word-dokument.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Här konverterar vi HTML-strängen till en byte-array och laddar den i dokumentet med hjälp av en minnesström. Detta säkerställer att HTML-innehållet tolkas och renderas korrekt av Aspose.Words.

## Steg 5: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen i DOCX-format.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

Detta sparar Word-dokumentet med den renderade kombinationsrutekontrollen på den angivna platsen.

## Slutsats

Och där har du det! Vi har lyckats infoga ett formulärfält med kombinationsrutor i ett Word-dokument med hjälp av Aspose.Words för .NET genom att utnyttja HTML-inläsningsalternativ. Den här steg-för-steg-guiden bör hjälpa dig att förstå processen och tillämpa den i dina projekt. Oavsett om du automatiserar dokumentskapandet eller manipulerar HTML-innehåll, erbjuder Aspose.Words för .NET kraftfulla verktyg för att uppnå dina mål.

## Vanliga frågor

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för dokumenthantering som låter utvecklare skapa, redigera, konvertera och rendera Word-dokument programmatiskt.

### Kan jag använda andra HTML-kontrolltyper med Aspose.Words för .NET?
Ja, Aspose.Words för .NET stöder olika HTML-kontrolltyper. Du kan anpassa hur olika kontroller återges i Word-dokumentet.

### Hur hanterar jag komplext HTML-innehåll i Aspose.Words för .NET?
Aspose.Words för .NET erbjuder omfattande stöd för HTML, inklusive komplexa element. Se till att du konfigurerar `HtmlLoadOptions` på lämpligt sätt för att hantera ditt specifika HTML-innehåll.

### Var kan jag hitta fler exempel och dokumentation?
Du hittar detaljerad dokumentation och exempel på [Dokumentationssida för Aspose.Words för .NET](https://reference.aspose.com/words/net/).

### Finns det en gratis testversion av Aspose.Words för .NET?
Ja, du kan ladda ner en gratis provversion från [Aspose webbplats](https://releases.aspose.com/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}