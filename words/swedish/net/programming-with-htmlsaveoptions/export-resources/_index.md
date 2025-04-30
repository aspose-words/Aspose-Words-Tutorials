---
"description": "Lär dig hur du exporterar resurser som CSS och typsnitt samtidigt som du sparar Word-dokument som HTML med Aspose.Words för .NET. Följ vår steg-för-steg-guide."
"linktitle": "Exportera resurser"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Exportera resurser"
"url": "/sv/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportera resurser

## Introduktion

Hej där, teknikälskare! Om du någonsin har behövt konvertera Word-dokument till HTML har du kommit rätt. Idag dyker vi ner i Aspose.Words för .NETs underbara värld. Detta kraftfulla bibliotek gör det enkelt att arbeta med Word-dokument programmatiskt. I den här handledningen går vi igenom stegen för att exportera resurser, som teckensnitt och CSS, när du sparar ett Word-dokument som HTML med Aspose.Words för .NET. Spänn fast säkerhetsbältet för en rolig och informativ resa!

## Förkunskapskrav

Innan vi går in i koden, låt oss se till att du har allt du behöver för att komma igång. Här är en snabb checklista:

1. Visual Studio: Se till att du har Visual Studio installerat på din dator. Du kan ladda ner det från [Visual Studio-webbplats](https://visualstudio.microsoft.com/).
2. Aspose.Words för .NET: Du behöver biblioteket Aspose.Words för .NET. Om du inte har det än kan du hämta en gratis provversion från [Aspose-utgåvor](https://releases.aspose.com/words/net/) eller köp den från [Aspose-butik](https://purchase.aspose.com/buy).
3. Grundläggande kunskaper i C#: En grundläggande förståelse för C# hjälper dig att följa kodexemplen.

Förstår du allt? Toppen! Nu går vi vidare till att importera de nödvändiga namnrymderna.

## Importera namnrymder

För att använda Aspose.Words för .NET måste du inkludera relevanta namnrymder i ditt projekt. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dessa namnrymder är avgörande för att komma åt Aspose.Words-klasserna och metoderna som vi kommer att använda i vår handledning.

Låt oss gå igenom processen för att exportera resurser när man sparar ett Word-dokument som HTML. Vi tar det steg för steg, så att det är lätt att följa.

## Steg 1: Konfigurera din dokumentkatalog

Först och främst måste du ange sökvägen till din dokumentkatalog. Det är här ditt Word-dokument finns och där HTML-filen kommer att sparas.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din katalog.

## Steg 2: Ladda Word-dokumentet

Nu ska vi ladda Word-dokumentet du vill konvertera till HTML. I den här handledningen använder vi ett dokument som heter `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Den här kodraden laddar dokumentet från den angivna katalogen.

## Steg 3: Konfigurera HTML-sparalternativ

För att exportera resurser som CSS och teckensnitt måste du konfigurera `HtmlSaveOptions`Det här steget är avgörande för att säkerställa att din HTML-utdata är välstrukturerad och innehåller nödvändiga resurser.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://exempel.com/resurser"
};
```

Låt oss gå igenom vad varje alternativ gör:
- `CssStyleSheetType = CssStyleSheetType.External`Det här alternativet anger att CSS-stilar ska sparas i ett externt stilark.
- `ExportFontResources = true`Detta möjliggör export av teckensnittsresurser.
- `ResourceFolder = dataDir + "Resources"`: Anger den lokala mappen där resurser (som teckensnitt och CSS-filer) ska sparas.
- `ResourceFolderAlias = "http://example.com/resources"`: Anger ett alias för resursmappen, som kommer att användas i HTML-filen.

## Steg 4: Spara dokumentet som HTML

När sparalternativen är konfigurerade är det sista steget att spara dokumentet som en HTML-fil. Så här gör du:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Den här kodraden sparar dokumentet i HTML-format, tillsammans med de exporterade resurserna.

## Slutsats

Och där har du det! Du har lyckats exportera resurser samtidigt som du sparat ett Word-dokument som HTML med hjälp av Aspose.Words för .NET. Med detta kraftfulla bibliotek blir det enkelt att hantera Word-dokument programmatiskt. Oavsett om du arbetar med en webbapplikation eller bara behöver konvertera dokument för offline-användning, har Aspose.Words det du behöver.

## Vanliga frågor

### Kan jag exportera bilder tillsammans med teckensnitt och CSS?
Ja, det kan du! Aspose.Words för .NET stöder även export av bilder. Se bara till att konfigurera `HtmlSaveOptions` följaktligen.

### Finns det något sätt att bädda in CSS istället för att använda ett externt stylesheet?
Absolut. Du kan ställa in `CssStyleSheetType` till `CssStyleSheetType.Embedded` om du föredrar inbäddade stilar.

### Hur kan jag anpassa namnet på den utgående HTML-filen?
Du kan ange vilket filnamn du vill i `doc.Save` metod. Till exempel, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Stöder Aspose.Words andra format förutom HTML?
Ja, den stöder olika format inklusive PDF, DOCX, TXT och mer. Kolla in [dokumentation](https://reference.aspose.com/words/net/) för en fullständig lista.

### Var kan jag få mer stöd och resurser?
För mer hjälp, besök [Aspose.Words supportforum](https://forum.aspose.com/c/words/8)Du kan också hitta detaljerad dokumentation och exempel på [Aspose webbplats](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}