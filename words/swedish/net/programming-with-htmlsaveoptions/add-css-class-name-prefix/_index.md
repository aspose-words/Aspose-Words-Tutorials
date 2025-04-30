---
"description": "Lär dig hur du lägger till ett CSS-klassnamnsprefix när du sparar Word-dokument som HTML med Aspose.Words för .NET. Steg-för-steg-guide, kodavsnitt och vanliga frågor ingår."
"linktitle": "Lägg till prefix för CSS-klassnamn"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Lägg till prefix för CSS-klassnamn"
"url": "/sv/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till prefix för CSS-klassnamn

## Introduktion

Välkommen! Om du dyker ner i Aspose.Words för .NETs värld har du något att vänta dig. Idag ska vi utforska hur man lägger till ett CSS-klassnamnsprefix när man sparar ett Word-dokument som HTML med Aspose.Words för .NET. Den här funktionen är superpraktisk när du vill undvika klassnamnskonflikter i dina HTML-filer.

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

- Aspose.Words för .NET: Om du inte har installerat det än, [ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller annan C# IDE.
- Ett Word-dokument: Vi kommer att använda ett dokument som heter `Rendering.docx`Placera den i din projektkatalog.

## Importera namnrymder

Se först till att du har importerat de nödvändiga namnrymderna till ditt C#-projekt. Lägg till dessa högst upp i din kodfil:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Nu ska vi dyka ner i steg-för-steg-guiden!

## Steg 1: Konfigurera ditt projekt

Innan vi kan börja lägga till ett CSS-klassnamnsprefix, låt oss konfigurera vårt projekt.

### Steg 1.1: Skapa ett nytt projekt

Starta din Visual Studio och skapa ett nytt Console App-projekt. Ge det något iögonfallande namn, till exempel `AsposeCssPrefixExample`.

### Steg 1.2: Lägg till Aspose.Words för .NET

Om du inte redan har gjort det, lägg till Aspose.Words för .NET i ditt projekt via NuGet. Öppna bara NuGet Package Manager-konsolen och kör:

```bash
Install-Package Aspose.Words
```

Toppen! Nu är vi redo att börja koda.

## Steg 2: Ladda ditt dokument

Det första vi behöver göra är att ladda Word-dokumentet vi vill konvertera till HTML.

### Steg 2.1: Definiera dokumentsökvägen

Ange sökvägen till din dokumentkatalog. För den här handledningens skull antar vi att ditt dokument finns i en mapp med namnet `Documents` i din projektkatalog.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Steg 2.2: Ladda dokumentet

Nu ska vi ladda dokumentet med Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera HTML-sparalternativ

Nästa steg är att konfigurera HTML-sparalternativen så att de inkluderar ett CSS-klassnamnsprefix.

### Steg 3.1: Skapa HTML-alternativ för sparning

Instansiera `HtmlSaveOptions` objektet och ställ in CSS-stilmallstypen till `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Steg 3.2: Ange prefix för CSS-klassnamn

Nu, låt oss ställa in `CssClassNamePrefix` egenskap till ditt önskade prefix. I det här exemplet använder vi `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Steg 4: Spara dokumentet som HTML

Slutligen, låt oss spara dokumentet som en HTML-fil med våra konfigurerade alternativ.


Ange sökvägen för HTML-filen och spara dokumentet.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Steg 5: Verifiera utdata

När du har kört ditt projekt, navigera till din `Documents` mapp. Du borde hitta en HTML-fil med namnet `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`Öppna den här filen i en textredigerare eller webbläsare för att kontrollera att CSS-klasserna har prefixet `pfx_`.

## Slutsats

Och där har du det! Genom att följa dessa steg har du lagt till ett CSS-klassnamnsprefix till din HTML-utdata med Aspose.Words för .NET. Den här enkla men kraftfulla funktionen kan hjälpa dig att upprätthålla rena och konfliktfria stilar i dina HTML-dokument.

## Vanliga frågor

### Kan jag använda ett annat prefix för varje sparåtgärd?
Ja, du kan anpassa prefixet varje gång du sparar ett dokument genom att ändra `CssClassNamePrefix` egendom.

### Stöder den här metoden inline CSS?
De `CssClassNamePrefix` egenskapen fungerar med extern CSS. För inline CSS behöver du en annan metod.

### Hur kan jag inkludera andra HTML-sparalternativ?
Du kan konfigurera olika egenskaper för `HtmlSaveOptions` för att anpassa din HTML-utdata. Kontrollera [dokumentation](https://reference.aspose.com/words/net/) för mer information.

### Är det möjligt att spara HTML-koden till en ström?
Absolut! Du kan spara dokumentet till en ström genom att skicka stream-objektet till `Save` metod.

### Hur får jag support om jag stöter på problem?
Du kan få stöd från [Aspose-forumet](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}