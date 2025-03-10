---
title: Lägg till textvattenstämpel med specifika alternativ
linktitle: Lägg till textvattenstämpel med specifika alternativ
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till en textvattenstämpel med specifika alternativ till dina Word-dokument med Aspose.Words för .NET. Anpassa lätt teckensnitt, storlek, färg och layout.
weight: 10
url: /sv/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till textvattenstämpel med specifika alternativ

## Introduktion

Vattenstämplar kan vara ett elegant och funktionellt tillägg till dina Word-dokument, som tjänar allt från att markera dokument som konfidentiella till att lägga till en personlig touch. I den här handledningen kommer vi att utforska hur man lägger till en textvattenstämpel i ett Word-dokument med Aspose.Words för .NET. Vi kommer att dyka in i de specifika alternativen du kan konfigurera, såsom teckensnittsfamilj, teckenstorlek, färg och layout. I slutet kommer du att kunna anpassa ditt dokuments vattenstämpel för att passa dina exakta behov. Så ta tag i din kodredigerare och låt oss komma igång!

## Förutsättningar

Innan vi börjar rulla, se till att du har följande på plats:

1.  Aspose.Words för .NET Library: Du behöver Aspose.Words-biblioteket installerat. Om du inte redan har gjort det kan du ladda ner det från[Aspose.Words nedladdningslänk](https://releases.aspose.com/words/net/).
2. Grundläggande förståelse för C#: Denna handledning kommer att använda C# som programmeringsspråk. Ett grundläggande grepp om C#-syntax kommer att vara till hjälp.
3. .NET-utvecklingsmiljö: Se till att du har en utvecklingsmiljö inställd (som Visual Studio) där du kan skapa och köra dina .NET-applikationer.

## Importera namnområden

För att arbeta med Aspose.Words måste du inkludera de nödvändiga namnrymden i ditt projekt. Här är vad du behöver importera:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Steg 1: Konfigurera ditt dokument

 Först måste du ladda dokumentet du vill arbeta med. För den här handledningen använder vi ett exempeldokument med namnet`Document.docx`. Se till att detta dokument finns i din angivna katalog.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 I det här steget definierar du katalogen där ditt dokument finns och laddar det i en instans av`Document` klass.

## Steg 2: Konfigurera vattenstämpelalternativ

Konfigurera sedan alternativen för din textvattenstämpel. Du kan anpassa olika aspekter, såsom teckensnittsfamilj, teckenstorlek, färg och layout. Låt oss ställa in dessa alternativ.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Så här gör varje alternativ:
- `FontFamily`: Anger teckensnittet för vattenstämpeltexten.
- `FontSize`: Ställer in storleken på vattenstämpeltexten.
- `Color`: Definierar färgen på vattenstämpeltexten.
- `Layout`Bestämmer orienteringen för vattenstämpeln (horisontell eller diagonal).
- `IsSemitrasparent`: Anger om vattenstämpeln är halvtransparent.

## Steg 3: Lägg till vattenstämpeltexten

Applicera nu vattenstämpeln på ditt dokument med de tidigare konfigurerade alternativen. I det här steget ställer du in vattenstämpeltexten till "Test" och tillämpar de alternativ du definierat.

```csharp
doc.Watermark.SetText("Test", options);
```

Denna kodrad lägger till vattenstämpeln med texten "Test" till dokumentet, med de angivna alternativen.

## Steg 4: Spara dokumentet

Slutligen sparar du dokumentet med den nya vattenstämpeln. Du kan spara det med ett nytt namn för att undvika att skriva över originaldokumentet.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Detta kodavsnitt sparar det ändrade dokumentet i samma katalog med ett nytt filnamn.

## Slutsats

Att lägga till en textvattenstämpel i dina Word-dokument med Aspose.Words för .NET är en enkel process när du delar upp den i hanterbara steg. Genom att följa den här handledningen har du lärt dig hur du konfigurerar olika vattenstämpelalternativ, inklusive teckensnitt, storlek, färg, layout och transparens. Med dessa färdigheter kan du nu anpassa dina dokument för att bättre möta dina behov eller för att inkludera viktig information som konfidentialitet eller varumärke.

 Om du har några frågor eller behöver mer hjälp, kolla gärna in[Aspose.Words dokumentation](https://reference.aspose.com/words/net/) eller besöka[Aspose Support Forum](https://forum.aspose.com/c/words/8) för mer hjälp.

## FAQ's

### Kan jag använda olika typsnitt för vattenstämpeln?

 Ja, du kan välja vilket typsnitt som helst som är installerat på ditt system genom att ange`FontFamily` egendom i`TextWatermarkOptions`.

### Hur ändrar jag färgen på vattenstämpeln?

 Du kan ändra färgen på vattenstämpeln genom att ställa in`Color` egendom i`TextWatermarkOptions` till någon`System.Drawing.Color` värde.

### Är det möjligt att lägga till flera vattenstämplar i ett dokument?

Aspose.Words stöder att lägga till en vattenstämpel åt gången. För att lägga till flera vattenstämplar måste du skapa och använda dem i tur och ordning.

### Kan jag justera placeringen av vattenstämpeln?

 De`WatermarkLayout`egenskapen bestämmer orienteringen, men exakta positionsjusteringar stöds inte direkt. Du kan behöva använda andra tekniker för exakt placering.

### Vad händer om jag behöver en halvtransparent vattenstämpel?

 Ställ in`IsSemitrasparent`egendom till`true` för att göra din vattenstämpel halvtransparent.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
