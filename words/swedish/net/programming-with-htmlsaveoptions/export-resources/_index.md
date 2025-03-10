---
title: Exportera resurser
linktitle: Exportera resurser
second_title: Aspose.Words Document Processing API
description: Lär dig hur du exporterar resurser som CSS och typsnitt samtidigt som du sparar Word-dokument som HTML med Aspose.Words för .NET. Följ vår steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportera resurser

## Introduktion

Hej där, andra teknikentusiast! Om du någonsin har märkt att du behöver konvertera Word-dokument till HTML, är du på rätt plats. Idag dyker vi in i den underbara världen av Aspose.Words för .NET. Detta kraftfulla bibliotek gör det enkelt att arbeta med Word-dokument programmatiskt. I den här handledningen går vi igenom stegen för att exportera resurser, såsom typsnitt och CSS, när du sparar ett Word-dokument som HTML med Aspose.Words för .NET. Spänn dig för en rolig, informativ åktur!

## Förutsättningar

Innan vi dyker in i koden, låt oss se till att du har allt du behöver för att komma igång. Här är en snabb checklista:

1.  Visual Studio: Se till att du har Visual Studio installerat på din dator. Du kan ladda ner den från[Visual Studio hemsida](https://visualstudio.microsoft.com/).
2.  Aspose.Words for .NET: Du behöver Aspose.Words for .NET-biblioteket. Om du inte har det ännu, prova gratis från[Aspose släpper](https://releases.aspose.com/words/net/) eller köp den från[Aspose Store](https://purchase.aspose.com/buy).
3. Grundläggande kunskaper om C#: En grundläggande förståelse av C# hjälper dig att följa med i kodexemplen.

Har du allt det där? Stor! Låt oss gå vidare till att importera de nödvändiga namnrymden.

## Importera namnområden

För att använda Aspose.Words för .NET måste du inkludera relevanta namnområden i ditt projekt. Så här gör du:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dessa namnutrymmen är avgörande för att komma åt Aspose.Words-klasserna och metoderna som vi kommer att använda i vår handledning.

Låt oss bryta ner processen för att exportera resurser när du sparar ett Word-dokument som HTML. Vi tar det steg för steg, så det är lätt att följa.

## Steg 1: Konfigurera din dokumentkatalog

Först och främst måste du ange sökvägen till din dokumentkatalog. Det är här ditt Word-dokument finns och där HTML-filen kommer att sparas.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din katalog.

## Steg 2: Ladda Word-dokumentet

 Låt oss sedan ladda Word-dokumentet du vill konvertera till HTML. För den här handledningen använder vi ett dokument med namnet`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Denna kodrad laddar dokumentet från den angivna katalogen.

## Steg 3: Konfigurera HTML-sparalternativ

För att exportera resurser som CSS och typsnitt måste du konfigurera`HtmlSaveOptions`. Detta steg är avgörande för att säkerställa att din HTML-utdata är välstrukturerad och inkluderar de nödvändiga resurserna.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resurser"
};
```

Låt oss dela upp vad varje alternativ gör:
- `CssStyleSheetType = CssStyleSheetType.External`: Det här alternativet anger att CSS-stilar ska sparas i en extern stilmall.
- `ExportFontResources = true`: Detta möjliggör export av teckensnittsresurser.
- `ResourceFolder = dataDir + "Resources"`: Anger den lokala mapp där resurser (som typsnitt och CSS-filer) kommer att sparas.
- `ResourceFolderAlias = "http://example.com/resources"`: Ställer in ett alias för resursmappen, som kommer att användas i HTML-filen.

## Steg 4: Spara dokumentet som HTML

Med sparalternativen konfigurerade är det sista steget att spara dokumentet som en HTML-fil. Så här gör du:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Denna kodrad sparar dokumentet i HTML-format, tillsammans med de exporterade resurserna.

## Slutsats

Och där har du det! Du har framgångsrikt exporterat resurser medan du sparat ett Word-dokument som HTML med Aspose.Words för .NET. Med detta kraftfulla bibliotek blir hanteringen av Word-dokument programmatiskt en pjäs. Oavsett om du arbetar med en webbapplikation eller bara behöver konvertera dokument för offlineanvändning, har Aspose.Words dig täckt.

## FAQ's

### Kan jag exportera bilder tillsammans med typsnitt och CSS?
 Ja, det kan du! Aspose.Words för .NET stöder även export av bilder. Se bara till att konfigurera`HtmlSaveOptions` följaktligen.

### Finns det något sätt att bädda in CSS istället för att använda en extern stilmall?
 Absolut. Du kan ställa in`CssStyleSheetType` till`CssStyleSheetType.Embedded` om du föredrar inbäddade stilar.

### Hur kan jag anpassa HTML-filens namn?
 Du kan ange vilket filnamn du vill i`doc.Save` metod. Till exempel,`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Stöder Aspose.Words andra format än HTML?
 Ja, det stöder olika format inklusive PDF, DOCX, TXT och mer. Kolla in[dokumentation](https://reference.aspose.com/words/net/) för en fullständig lista.

### Var kan jag få mer support och resurser?
För mer hjälp, besök[Aspose.Words Support Forum](https://forum.aspose.com/c/words/8) . Du kan också hitta detaljerad dokumentation och exempel på[Aspose hemsida](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
