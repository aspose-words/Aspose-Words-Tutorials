---
title: Föredragen kontrolltyp i Word-dokument
linktitle: Föredragen kontrolltyp i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar ett formulärfält med kombinationsruta i ett Word-dokument med Aspose.Words för .NET. Följ den här steg-för-steg-guiden för sömlös HTML-innehållsintegration.
weight: 10
url: /sv/net/programming-with-htmlloadoptions/preferred-control-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Föredragen kontrolltyp i Word-dokument

## Introduktion

vi dyker in i en spännande handledning om hur man arbetar med HTML-laddningsalternativ i Aspose.Words för .NET, och fokuserar specifikt på att ställa in den föredragna kontrolltypen när man infogar ett formulärfält med kombinationsruta i ett Word-dokument. Den här steg-för-steg-guiden hjälper dig att förstå hur du effektivt manipulerar och renderar HTML-innehåll i dina Word-dokument med Aspose.Words för .NET.

## Förutsättningar

Innan vi går in i koden finns det några saker du måste ha på plats:

1.  Aspose.Words for .NET: Se till att du har Aspose.Words for .NET-biblioteket installerat. Du kan ladda ner den från[webbplats](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Du bör ha en utvecklingsmiljö inrättad, som Visual Studio.
3. Grundläggande kunskaper om C#: En grundläggande förståelse för C#-programmering är nödvändig för att följa med handledningen.
4. HTML-innehåll: Grundläggande kunskaper om HTML är till hjälp eftersom vi kommer att arbeta med HTML-innehåll i det här exemplet.

## Importera namnområden

Låt oss först importera de nödvändiga namnområdena för att komma igång:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Låt oss nu dela upp exemplet i flera steg för att säkerställa klarhet och förståelse.

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

Denna HTML innehåller en enkel kombinationsruta med två alternativ. Vi kommer att ladda denna HTML i ett Word-dokument och specificera hur den ska renderas.

## Steg 2: Definiera dokumentkatalogen

Ange sedan katalogen där ditt Word-dokument ska sparas. Detta hjälper till att organisera dina filer och hålla sökvägshanteringen ren.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara ditt Word-dokument.

## Steg 3: Konfigurera HTML-laddningsalternativ

 Här konfigurerar vi HTML-laddningsalternativen, särskilt med fokus på`PreferredControlType`egendom. Detta bestämmer hur kombinationsrutan ska renderas i Word-dokumentet.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

 Genom att ställa in`PreferredControlType` till`HtmlControlType.StructuredDocumentTag`, ser vi till att kombinationsrutan renderas som en strukturerad dokumenttagg (SDT) i Word-dokumentet.

## Steg 4: Ladda HTML-innehållet i dokumentet

Med hjälp av de konfigurerade laddningsalternativen laddar vi HTML-innehållet i ett nytt Word-dokument.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Här konverterar vi HTML-strängen till en byte-array och laddar in den i dokumentet med hjälp av en minnesström. Detta säkerställer att HTML-innehållet tolkas och återges korrekt av Aspose.Words.

## Steg 5: Spara dokumentet

Slutligen, spara dokumentet i den angivna katalogen i DOCX-format.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

Detta sparar Word-dokumentet med den renderade kombinationsrutan på den angivna platsen.

## Slutsats

Och där har du det! Vi har framgångsrikt infogat ett formulärfält med kombinationsruta i ett Word-dokument med Aspose.Words för .NET genom att använda HTML-laddningsalternativ. Den här steg-för-steg-guiden bör hjälpa dig att förstå processen och tillämpa den på dina projekt. Oavsett om du automatiserar dokumentskapande eller manipulerar HTML-innehåll, erbjuder Aspose.Words för .NET kraftfulla verktyg för att uppnå dina mål.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt dokumentmanipuleringsbibliotek som låter utvecklare skapa, redigera, konvertera och rendera Word-dokument programmatiskt.

### Kan jag använda andra HTML-kontrolltyper med Aspose.Words för .NET?
Ja, Aspose.Words för .NET stöder olika HTML-kontrolltyper. Du kan anpassa hur olika kontroller renderas i Word-dokumentet.

### Hur hanterar jag komplext HTML-innehåll i Aspose.Words för .NET?
 Aspose.Words för .NET ger omfattande stöd för HTML, inklusive komplexa element. Se till att du konfigurerar`HtmlLoadOptions`för att hantera ditt specifika HTML-innehåll.

### Var kan jag hitta fler exempel och dokumentation?
 Du kan hitta detaljerad dokumentation och exempel på[Aspose.Words för .NET dokumentationssida](https://reference.aspose.com/words/net/).

### Finns det en gratis testversion tillgänglig för Aspose.Words för .NET?
 Ja, du kan ladda ner en gratis testversion från[Aspose hemsida](https://releases.aspose.com/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
