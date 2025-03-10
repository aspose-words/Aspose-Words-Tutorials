---
title: Konvertera metafiler till emf eller wmf
linktitle: Konvertera metafiler till emf eller wmf
second_title: Aspose.Words Document Processing API
description: Steg-för-steg-guide för att konvertera metafiler till EMF- eller WMF-format vid konvertering av ett dokument till HTML med Aspose.Words för .NET.
weight: 10
url: /sv/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera metafiler till emf eller wmf

## Introduktion

Välkommen till ännu en djupdykning i Aspose.Words för .NET-världen. Idag tar vi oss an ett snyggt knep: konvertera SVG-bilder till EMF- eller WMF-format i dina Word-dokument. Det här kanske låter lite tekniskt, men oroa dig inte. I slutet av denna handledning kommer du att vara ett proffs på det. Oavsett om du är en erfaren utvecklare eller precis har börjat med Aspose.Words för .NET, kommer den här guiden att gå igenom allt du behöver veta, steg för steg.

## Förutsättningar

Innan vi dyker in i koden, låt oss se till att vi har allt inställt. Här är vad du behöver:

1.  Aspose.Words för .NET Library: Se till att du har den senaste versionen. Om du inte har det kan du ladda ner det från[här](https://releases.aspose.com/words/net/).
2. .NET Framework: Se till att du har .NET Framework installerat på din dator.
3. Utvecklingsmiljö: En IDE som Visual Studio kommer att göra ditt liv enklare.
4. Grundläggande kunskaper i C#: Du behöver inte vara expert, men en grundläggande förståelse hjälper.

Har du allt? Stor! Låt oss börja.

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnrymden. Detta är avgörande eftersom det talar om för vårt program var de ska hitta klasserna och metoderna vi kommer att använda.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dessa namnområden täcker allt från grundläggande systemfunktioner till den specifika Aspose.Words-funktionaliteten vi behöver för den här handledningen.

## Steg 1: Konfigurera din dokumentkatalog

Låt oss börja med att definiera sökvägen till din dokumentkatalog. Det är här ditt Word-dokument kommer att sparas efter att vi konverterat metafilerna.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen där du vill spara ditt dokument.

## Steg 2: Skapa HTML-strängen med SVG

Därefter behöver vi en HTML-sträng som innehåller SVG-bilden vi vill konvertera. Här är ett enkelt exempel:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' width='500' height='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Detta HTML-kodavsnitt innehåller en grundläggande SVG som säger "Hello world!".

## Steg 3: Ladda HTML med alternativet ConvertSvgToEmf

 Nu använder vi`HtmlLoadOptions` för att specificera hur vi vill hantera SVG-bilderna i HTML. Miljö`ConvertSvgToEmf` till`true` ser till att SVG-bilder konverteras till EMF-format.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 Detta kodavsnitt skapar en ny`Document` objekt genom att ladda HTML-strängen i den med de angivna laddningsalternativen.

## Steg 4: Ställ in HtmlSaveOptions för metafilformat

 För att spara dokumentet med rätt metafilformat använder vi`HtmlSaveOptions` . Här sätter vi`MetafileFormat` till`HtmlMetafileFormat.Png` , men du kan ändra detta till`Emf` eller`Wmf` beroende på dina behov.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Steg 5: Spara dokumentet

Slutligen sparar vi dokumentet med de angivna sparalternativen.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Detta sparar dokumentet i den angivna katalogen med metafilformatet konverterat enligt definitionen.

## Slutsats

Och där har du det! Genom att följa dessa steg har du framgångsrikt konverterat SVG-bilder till EMF- eller WMF-format i dina Word-dokument med Aspose.Words för .NET. Denna metod är praktisk för att säkerställa kompatibilitet och bibehålla den visuella integriteten för dina dokument på olika plattformar. Glad kodning!

## FAQ's

### Kan jag konvertera andra bildformat med den här metoden?
Ja, du kan konvertera olika bildformat genom att justera laddnings- och sparaalternativen därefter.

### Är det nödvändigt att använda en specifik .NET Framework-version?
Aspose.Words för .NET stöder flera .NET Framework-versioner, men det är alltid en bra idé att använda den senaste versionen för bästa kompatibilitet och funktioner.

### Vad är fördelen med att konvertera SVG till EMF eller WMF?
Konvertering av SVG till EMF eller WMF säkerställer att vektorgrafik bevaras och återges korrekt i miljöer som kanske inte stöder SVG fullt ut.

### Kan jag automatisera den här processen för flera dokument?
Absolut! Du kan gå igenom flera HTML-filer och använda samma process för att automatisera konverteringen för batchbearbetning.

### Var kan jag hitta fler resurser och support för Aspose.Words för .NET?
 Du kan hitta omfattande dokumentation[här](https://reference.aspose.com/words/net/) och få stöd från Aspose-gemenskapen[här](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
