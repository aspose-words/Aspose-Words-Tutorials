---
"description": "Lär dig hur du ställer in teckensnittsmappar för standardinstansen i Aspose.Words för .NET med den här steg-för-steg-handledningen. Anpassa dina Word-dokument utan ansträngning."
"linktitle": "Ange standardinstans för teckensnittsmappar"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ange standardinstans för teckensnittsmappar"
"url": "/sv/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ange standardinstans för teckensnittsmappar

## Introduktion

Hej där, kodare! Om du arbetar med Word-dokument i .NET vet du förmodligen vikten av att ha dina teckensnitt precis rätt. Idag dyker vi ner i hur man ställer in teckensnittsmappar för standardinstansen med Aspose.Words för .NET. Tänk dig att ha alla dina anpassade teckensnitt nära till hands, vilket gör att dina dokument ser ut exakt som du föreställer dig dem. Låter bra, eller hur? Nu sätter vi igång!

## Förkunskapskrav

Innan vi går in på de allra minsta detaljerna, låt oss se till att du har allt du behöver:
- Aspose.Words för .NET: Se till att du har biblioteket installerat. Om inte, kan du [ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller annan .NET-kompatibel IDE.
- Grundläggande kunskaper i C#: Du bör vara bekväm med C#-programmering.
- Typsnittsmapp: En katalog som innehåller dina anpassade typsnitt.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Detta hjälper till att komma åt de klasser och metoder som krävs för att ställa in fontmappen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss dela upp processen i enkla, lättsmälta steg.

## Steg 1: Definiera datakatalogen

Varje stor resa börjar med ett enda steg, och vårt börjar med att definiera katalogen där ditt dokument lagras. Det är här Aspose.Words letar efter ditt Word-dokument.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Här, ersätt `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentkatalog. Det är här ditt källdokument finns och där resultatet kommer att sparas.

## Steg 2: Ställ in teckensnittsmappen

Nu ska vi tala om för Aspose.Words var dina anpassade typsnitt finns. Detta görs genom att ställa in typsnittsmappen med hjälp av `FontSettings.DefaultInstance.SetFontsFolder` metod.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

I den här raden, `"C:\\MyFonts\\"` är sökvägen till din mapp för anpassade teckensnitt. Den andra parametern, `true`, indikerar att teckensnitten i den här mappen ska skannas rekursivt.

## Steg 3: Ladda ditt dokument

När fontmappen är konfigurerad är nästa steg att ladda ditt Word-dokument till Aspose.Words. Detta görs med hjälp av `Document` klass.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Här, `dataDir + "Rendering.docx"` hänvisar till den fullständiga sökvägen till ditt Word-dokument. Se till att ditt dokument finns i den angivna katalogen.

## Steg 4: Spara dokumentet

Det sista steget är att spara dokumentet efter att du har ställt in teckensnittsmappen. Detta säkerställer att dina anpassade teckensnitt tillämpas korrekt i resultatet.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Den här raden sparar ditt dokument som en PDF med de anpassade teckensnitten tillämpade. Utdatafilen kommer att finnas i samma katalog som ditt källdokument.

## Slutsats

Och där har du det! Att ställa in teckensnittsmappar för standardinstansen i Aspose.Words för .NET är enkelt när du delar upp det i enkla steg. Genom att följa den här guiden kan du se till att dina Word-dokument ser ut exakt som du vill ha dem, med alla dina anpassade teckensnitt på plats. Så fortsätt, prova och få dina dokument att glänsa!

## Vanliga frågor

### Kan jag ställa in flera mappar för teckensnitt?
Ja, du kan ställa in flera mappar med teckensnitt genom att använda `SetFontsFolders` metod som accepterar en array av mappsökvägar.

### Vilka filformat stöder Aspose.Words för att spara dokument?
Aspose.Words stöder olika format inklusive DOCX, PDF, HTML, EPUB och mer.

### Är det möjligt att använda online-typsnitt i Aspose.Words?
Nej, Aspose.Words stöder för närvarande endast lokala typsnittsfiler.

### Hur kan jag se till att mina anpassade teckensnitt är inbäddade i den sparade PDF-filen?
Genom att ställa in `FontSettings` korrekt och säkerställer att teckensnitten är tillgängliga, kommer Aspose.Words att bädda in dem i PDF-utdata.

### Vad händer om ett teckensnitt inte hittas i den angivna mappen?
Aspose.Words kommer att använda ett reservteckensnitt om det angivna teckensnittet inte hittas.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}