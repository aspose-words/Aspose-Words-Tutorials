---
title: Exportera textinmatningsformulärfält som text
linktitle: Exportera textinmatningsformulärfält som text
second_title: Aspose.Words Document Processing API
description: Lär dig hur du exporterar textinmatningsformulär som vanlig text med Aspose.Words för .NET med denna omfattande, steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportera textinmatningsformulärfält som text

## Introduktion

Så du dyker in i Aspose.Words-världen för .NET? Fantastiskt val! Om du vill lära dig hur du exporterar ett textinmatningsformulär som text har du kommit rätt. Oavsett om du precis har börjat eller fräscha upp dina kunskaper, kommer den här guiden att gå igenom allt du behöver veta. Låt oss börja, ska vi?

## Förutsättningar

Innan vi dyker in i det nitty-gritty, låt oss se till att du har allt du behöver för att följa med smidigt:

-  Aspose.Words för .NET: Ladda ner och installera den senaste versionen från[här](https://releases.aspose.com/words/net/).
- IDE: Visual Studio eller någon C#-utvecklingsmiljö.
- Grundläggande C#-kunskaper: Förståelse av grundläggande C#-syntax och objektorienterade programmeringskoncept.
- Dokument: Ett exempel på Word-dokument (`Rendering.docx`) med textinmatningsformulärfält.

## Importera namnområden

Först och främst måste du importera de nödvändiga namnrymden. Dessa är som byggstenarna som gör att allt fungerar sömlöst.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Okej, nu när vi har våra namnutrymmen redo, låt oss hoppa in i handlingen!

## Steg 1: Konfigurera projektet

Innan vi går in i koden, låt oss se till att vårt projekt är korrekt konfigurerat.

## Skapar projektet

1. Öppna Visual Studio: Börja med att öppna Visual Studio eller din föredragna C#-utvecklingsmiljö.
2.  Skapa ett nytt projekt: Navigera till`File > New > Project` . Välja`Console App (.NET Core)` eller någon annan relevant projekttyp.
3.  Namnge ditt projekt: Ge ditt projekt ett meningsfullt namn, något liknande`AsposeWordsExportExample`.

## Lägger till Aspose.Words

1.  Hantera NuGet-paket: Högerklicka på ditt projekt i Solution Explorer och välj`Manage NuGet Packages`.
2.  Sök efter Aspose.Words: I NuGet Package Manager, sök efter`Aspose.Words`.
3.  Installera Aspose.Words: Klicka på`Install` för att lägga till Aspose.Words-biblioteket till ditt projekt.

## Steg 2: Ladda Word-dokumentet

Nu när vårt projekt är konfigurerat, låt oss ladda Word-dokumentet som innehåller textinmatningsformulärfälten.

1. Specificera dokumentkatalogen: Definiera sökvägen till katalogen där ditt dokument är lagrat.
2.  Ladda dokumentet: Använd`Document` klass för att ladda ditt Word-dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Förbered exportkatalogen

Innan vi exporterar, låt oss se till att vår exportkatalog är klar. Det är här vår HTML-fil och bilder kommer att sparas.

1. Definiera exportkatalogen: Ange sökvägen där de exporterade filerna ska sparas.
2. Kontrollera och rensa katalogen: Se till att katalogen finns och är tom.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Steg 4: Konfigurera sparalternativ

Här händer magin. Vi måste ställa in våra sparalternativ för att exportera textinmatningsformulärfältet som vanlig text.

1.  Skapa sparalternativ: Initiera ett nytt`HtmlSaveOptions` objekt.
2.  Ställ in exporttextalternativ: Konfigurera`ExportTextInputFormFieldAsText`egendom till`true`.
3. Ställ in bildmapp: Definiera mappen där bilderna ska sparas.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Steg 5: Spara dokumentet som HTML

Slutligen, låt oss spara Word-dokumentet som en HTML-fil med hjälp av våra konfigurerade sparaalternativ.

1. Definiera utdatasökvägen: Ange sökvägen där HTML-filen ska sparas.
2.  Spara dokumentet: Använd`Save` metod för`Document`klass för att exportera dokumentet.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Slutsats

Och där har du det! Du har framgångsrikt exporterat ett textinmatningsformulärfält som vanlig text med Aspose.Words för .NET. Den här guiden borde ha gett dig en tydlig, steg-för-steg-strategi för att uppnå denna uppgift. Kom ihåg att övning ger färdighet, så fortsätt att experimentera med olika alternativ och inställningar för att se vad du mer kan göra med Aspose.Words.

## FAQ's

### Kan jag exportera andra typer av formulärfält med samma metod?

 Ja, du kan exportera andra typer av formulärfält genom att konfigurera olika egenskaper för`HtmlSaveOptions` klass.

### Vad händer om mitt dokument har bilder?

 Bilderna kommer att sparas i den angivna bildmappen. Se till att ställa in`ImagesFolder` egendom i`HtmlSaveOptions`.

### Behöver jag en licens för Aspose.Words?

 Ja, du kan få en gratis provperiod[här](https://releases.aspose.com/) eller köp en licens[här](https://purchase.aspose.com/buy).

### Kan jag anpassa den exporterade HTML-koden?

 Absolut! Aspose.Words erbjuder olika alternativ för att anpassa HTML-utdata. Se till[dokumentation](https://reference.aspose.com/words/net/) för mer information.

### Är Aspose.Words kompatibelt med .NET Core?

Ja, Aspose.Words är kompatibelt med .NET Core, .NET Framework och andra .NET-plattformar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
