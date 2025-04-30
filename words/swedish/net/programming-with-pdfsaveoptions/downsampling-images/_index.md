---
"description": "Minska PDF-dokumentstorleken genom att nedsampla bilder med Aspose.Words för .NET. Optimera dina PDF-filer för snabbare uppladdnings- och nedladdningstider."
"linktitle": "Minska PDF-dokumentstorleken med nedsampling av bilder"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Minska PDF-dokumentstorleken med nedsampling av bilder"
"url": "/sv/net/programming-with-pdfsaveoptions/downsampling-images/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Minska PDF-dokumentstorleken med nedsampling av bilder

## Introduktion

PDF-filer är en stapelvara i den digitala världen och används för allt från att dela dokument till att skapa e-böcker. Deras storlek kan dock ibland vara ett hinder, särskilt när det gäller bildrikt innehåll. Det är här nedsampling av bilder kommer in i bilden. Genom att minska upplösningen på bilder i PDF-filen kan du minska filstorleken avsevärt utan att kompromissa för mycket med kvaliteten. I den här handledningen går vi igenom stegen för att uppnå detta med Aspose.Words för .NET.

## Förkunskapskrav

Innan vi går in i koden, låt oss se till att du har allt du behöver:

1. Aspose.Words för .NET: Se till att du har Aspose.Words-biblioteket installerat. Om inte kan du ladda ner det. [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Valfri .NET-utvecklingsmiljö som Visual Studio.
3. Grundläggande kunskaper i C#: Att förstå grunderna i C#-programmering kommer att vara till hjälp.
4. Ett exempeldokument: Ett Word-dokument (t.ex. `Rendering.docx`) med bilder för att konvertera till PDF.

## Importera namnrymder

Först och främst måste du importera de nödvändiga namnrymderna. Lägg till dessa högst upp i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nu ska vi dela upp processen i hanterbara steg.

## Steg 1: Ladda dokumentet

Det första steget är att ladda ditt Word-dokument. Det är här du anger sökvägen till din dokumentkatalog.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

I det här steget laddar vi Word-dokumentet från den angivna katalogen. Se till att ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen dit ditt dokument finns.

## Steg 2: Konfigurera nedsamplingsalternativ

Nästa steg är att konfigurera nedsamplingsalternativen. Detta innebär att ställa in upplösningen och upplösningströskeln för bilderna.

```csharp
// Vi kan sätta ett minimitröskelvärde för nedsampling.
// Det här värdet förhindrar att den andra bilden i indatadokumentet nedsamplas.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

Här skapar vi en ny instans av `PdfSaveOptions` och inställning av `Resolution` till 36 DPI och `ResolutionThreshold` till 128 DPI. Det betyder att alla bilder med en upplösning högre än 128 DPI kommer att nedsamplas till 36 DPI.

## Steg 3: Spara dokumentet som PDF

Slutligen sparar vi dokumentet som en PDF med de konfigurerade alternativen.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

I det här sista steget sparar vi dokumentet som en PDF i samma katalog med de angivna nedsamplingsalternativen.

## Slutsats

Och där har du det! Du har lyckats minska storleken på din PDF genom att nedsampla bilder med Aspose.Words för .NET. Detta gör inte bara dina PDF-filer mer hanterbara utan bidrar också till snabbare uppladdningar, nedladdningar och smidigare visningsupplevelser.

## Vanliga frågor

### Vad är nedsampling?
Nedsampling är processen att minska upplösningen på bilder, vilket hjälper till att minska filstorleken på dokument som innehåller dessa bilder.

### Kommer nedsampling att påverka bildernas kvalitet?
Ja, nedsampling kommer att minska bildkvaliteten. Effekten beror dock på graden av upplösningsminskning. Det är en avvägning mellan filstorlek och bildkvalitet.

### Kan jag välja vilka bilder jag vill nedsampla?
Ja, genom att ställa in `ResolutionThreshold`, kan du styra vilka bilder som ska nedsamplas baserat på deras ursprungliga upplösning.

### Vilken är den ideala upplösningen för nedsampling?
Den ideala upplösningen beror på dina specifika behov. Vanligtvis används 72 DPI för webbbilder, medan högre upplösningar används för utskriftskvalitet.

### Är Aspose.Words för .NET gratis?
Aspose.Words för .NET är en kommersiell produkt, men du kan ladda ner en gratis provversion [här](https://releases.aspose.com/) eller ansöka om en [tillfällig licens](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}