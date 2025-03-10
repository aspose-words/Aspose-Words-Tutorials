---
title: Lägg till Css Class Name Prefix
linktitle: Lägg till Css Class Name Prefix
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till ett CSS-klassnamnsprefix när du sparar Word-dokument som HTML med Aspose.Words för .NET. Steg-för-steg-guide, kodavsnitt och vanliga frågor ingår.
weight: 10
url: /sv/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till Css Class Name Prefix

## Introduktion

Välkomna! Om du dyker in i Aspose.Words-världen för .NET får du en njutning. Idag ska vi utforska hur man lägger till ett CSS-klassnamnsprefix när man sparar ett Word-dokument som HTML med Aspose.Words för .NET. Den här funktionen är väldigt praktisk när du vill undvika klassnamnskonflikter i dina HTML-filer.

## Förutsättningar

Innan vi börjar, se till att du har följande:

-  Aspose.Words för .NET: Om du inte har installerat det ännu,[ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller någon annan C# IDE.
-  Ett Word-dokument: Vi kommer att använda ett dokument som heter`Rendering.docx`. Placera den i din projektkatalog.

## Importera namnområden

Se först till att du har de nödvändiga namnrymden importerade till ditt C#-projekt. Lägg till dessa överst i din kodfil:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Låt oss nu dyka in i steg-för-steg-guiden!

## Steg 1: Konfigurera ditt projekt

Innan vi kan börja lägga till ett CSS-klassnamnsprefix, låt oss ställa in vårt projekt.

### Steg 1.1: Skapa ett nytt projekt

 Starta din Visual Studio och skapa ett nytt konsolappprojekt. Döp det till något catchy som`AsposeCssPrefixExample`.

### Steg 1.2: Lägg till Aspose.Words för .NET

Om du inte redan har gjort det, lägg till Aspose.Words för .NET till ditt projekt via NuGet. Öppna helt enkelt NuGet Package Manager Console och kör:

```bash
Install-Package Aspose.Words
```

Stor! Nu är vi redo att börja koda.

## Steg 2: Ladda ditt dokument

Det första vi behöver göra är att ladda Word-dokumentet vi vill konvertera till HTML.

### Steg 2.1: Definiera dokumentsökvägen

 Ställ in sökvägen till din dokumentkatalog. För den här handledningens skull, låt oss anta att ditt dokument finns i en mapp med namnet`Documents` i din projektkatalog.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Steg 2.2: Ladda dokumentet

Låt oss nu ladda dokumentet med Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera HTML-sparalternativ

Därefter måste vi konfigurera HTML-sparalternativen så att de inkluderar ett CSS-klassnamnsprefix.

### Steg 3.1: Skapa HTML-sparalternativ

 Instantiera`HtmlSaveOptions` objekt och ställ in CSS-formatmallstypen till`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Steg 3.2: Ange prefix för CSS-klassnamn

 Låt oss nu ställa in`CssClassNamePrefix` egenskap till önskat prefix. För det här exemplet kommer vi att använda`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Steg 4: Spara dokumentet som HTML

Slutligen, låt oss spara dokumentet som en HTML-fil med våra konfigurerade alternativ.


Ange HTML-filens sökväg och spara dokumentet.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Steg 5: Verifiera utdata

 När du har kört ditt projekt, navigera till din`Documents` mapp. Du bör hitta en HTML-fil med namnet`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` . Öppna den här filen i en textredigerare eller webbläsare för att verifiera att CSS-klasserna har prefixet`pfx_`.

## Slutsats

Och där har du det! Genom att följa dessa steg har du framgångsrikt lagt till ett CSS-klassnamnsprefix till din HTML-utdata med Aspose.Words för .NET. Denna enkla men kraftfulla funktion kan hjälpa dig att behålla rena och konfliktfria stilar i dina HTML-dokument.

## FAQ's

### Kan jag använda ett annat prefix för varje sparoperation?
 Ja, du kan anpassa prefixet varje gång du sparar ett dokument genom att ändra`CssClassNamePrefix` egendom.

### Stöder den här metoden inline CSS?
 De`CssClassNamePrefix`egenskapen fungerar med extern CSS. För inline CSS behöver du ett annat tillvägagångssätt.

### Hur kan jag inkludera andra HTML-sparalternativ?
 Du kan konfigurera olika egenskaper för`HtmlSaveOptions` för att anpassa din HTML-utdata. Kontrollera[dokumentation](https://reference.aspose.com/words/net/) för mer information.

### Är det möjligt att spara HTML-koden i en stream?
 Absolut! Du kan spara dokumentet i en ström genom att skicka strömobjektet till`Save` metod.

### Hur får jag support om jag stöter på problem?
 Du kan få stöd från[Aspose forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
