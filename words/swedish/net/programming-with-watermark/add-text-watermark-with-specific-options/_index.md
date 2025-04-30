---
"description": "Lär dig hur du lägger till en textvattenstämpel med specifika alternativ i dina Word-dokument med Aspose.Words för .NET. Anpassa enkelt teckensnitt, storlek, färg och layout."
"linktitle": "Lägg till textvattenstämpel med specifika alternativ"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Lägg till textvattenstämpel med specifika alternativ"
"url": "/sv/net/programming-with-watermark/add-text-watermark-with-specific-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till textvattenstämpel med specifika alternativ

## Introduktion

Vattenstämplar kan vara ett snyggt och funktionellt tillägg till dina Word-dokument, och kan användas för allt från att markera dokument som konfidentiella till att ge en personlig touch. I den här handledningen utforskar vi hur man lägger till en textvattenstämpel i ett Word-dokument med hjälp av Aspose.Words för .NET. Vi går in på de specifika alternativ du kan konfigurera, till exempel teckensnittsfamilj, teckenstorlek, färg och layout. Till sist kommer du att kunna anpassa dokumentets vattenstämpel så att den passar dina exakta behov. Så ta fram din kodredigerare och låt oss sätta igång!

## Förkunskapskrav

Innan vi sätter igång, se till att du har följande på plats:

1. Aspose.Words för .NET-biblioteket: Du behöver ha Aspose.Words-biblioteket installerat. Om du inte redan har gjort det kan du ladda ner det från [Aspose.Words nedladdningslänk](https://releases.aspose.com/words/net/).
2. Grundläggande förståelse för C#: Den här handledningen använder C# som programmeringsspråk. Grundläggande förståelse för C#-syntax är till hjälp.
3. .NET-utvecklingsmiljö: Se till att du har en utvecklingsmiljö konfigurerad (som Visual Studio) där du kan skapa och köra dina .NET-applikationer.

## Importera namnrymder

För att arbeta med Aspose.Words måste du inkludera de nödvändiga namnrymderna i ditt projekt. Här är vad du behöver importera:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Steg 1: Konfigurera ditt dokument

Först måste du ladda dokumentet du vill arbeta med. I den här handledningen använder vi ett exempeldokument med namnet `Document.docx`Se till att det här dokumentet finns i den angivna katalogen.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

I det här steget definierar du katalogen där ditt dokument finns och laddar det till en instans av `Document` klass.

## Steg 2: Konfigurera vattenstämpelalternativ

Konfigurera sedan alternativen för din textvattenstämpel. Du kan anpassa olika aspekter, till exempel teckensnittsfamilj, teckenstorlek, färg och layout. Nu konfigurerar vi dessa alternativ.

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

Här är vad varje alternativ gör:
- `FontFamily`: Anger teckensnittet för vattenstämpelns text.
- `FontSize`Anger storleken på vattenstämpelns text.
- `Color`: Definierar färgen på vattenstämpelns text.
- `Layout`: Bestämmer vattenstämpelns orientering (horisontell eller diagonal).
- `IsSemitrasparent`: Anger om vattenstämpeln är halvtransparent.

## Steg 3: Lägg till vattenstämpeltexten

Använd nu vattenstämpeln på ditt dokument med de tidigare konfigurerade alternativen. I det här steget ställer du in vattenstämpelns text till "Test" och tillämpar de alternativ du definierat.

```csharp
doc.Watermark.SetText("Test", options);
```

Den här kodraden lägger till vattenstämpeln med texten "Test" i dokumentet och tillämpar de angivna alternativen.

## Steg 4: Spara dokumentet

Slutligen, spara dokumentet med den nya vattenstämpeln. Du kan spara det med ett nytt namn för att undvika att skriva över originaldokumentet.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Det här kodavsnittet sparar det ändrade dokumentet i samma katalog med ett nytt filnamn.

## Slutsats

Att lägga till en textvattenstämpel i dina Word-dokument med Aspose.Words för .NET är en enkel process när du delar upp den i hanterbara steg. Genom att följa den här handledningen har du lärt dig hur du konfigurerar olika vattenstämpelalternativ, inklusive teckensnitt, storlek, färg, layout och transparens. Med dessa färdigheter kan du nu anpassa dina dokument för att bättre möta dina behov eller inkludera viktig information som sekretess eller varumärkesbyggande.

Om du har några frågor eller behöver ytterligare hjälp är du välkommen att titta in på [Aspose.Words-dokumentation](https://reference.aspose.com/words/net/) eller besök [Aspose Supportforum](https://forum.aspose.com/c/words/8) för mer hjälp.

## Vanliga frågor

### Kan jag använda olika teckensnitt för vattenmärket?

Ja, du kan välja vilket teckensnitt som helst som är installerat på ditt system genom att ange `FontFamily` egendom i `TextWatermarkOptions`.

### Hur ändrar jag färgen på vattenstämpeln?

Du kan ändra vattenstämpelns färg genom att ställa in `Color` egendom i `TextWatermarkOptions` till vilken som helst `System.Drawing.Color` värde.

### Är det möjligt att lägga till flera vattenstämplar i ett dokument?

Aspose.Words stöder att lägga till en vattenstämpel i taget. För att lägga till flera vattenstämplar måste du skapa och tillämpa dem i tur och ordning.

### Kan jag justera vattenstämpelns position?

De `WatermarkLayout` Egenskapen bestämmer orienteringen, men exakta positioneringsjusteringar stöds inte direkt. Du kan behöva använda andra tekniker för exakt placering.

### Vad händer om jag behöver ett halvtransparent vattenmärke?

Ställ in `IsSemitrasparent` egendom till `true` för att göra ditt vattenmärke halvtransparent.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}