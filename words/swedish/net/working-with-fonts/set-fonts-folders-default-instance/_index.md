---
title: Ställ in typsnittsmappar som standardinstans
linktitle: Ställ in typsnittsmappar som standardinstans
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in teckensnittsmappar för standardinstansen i Aspose.Words för .NET med denna steg-för-steg-handledning. Anpassa dina Word-dokument utan ansträngning.
weight: 10
url: /sv/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in typsnittsmappar som standardinstans

## Introduktion

Hej där, medkodare! Om du arbetar med Word-dokument i .NET vet du antagligen vikten av att ha rätt typsnitt. Idag går vi in på hur man ställer in teckensnittsmappar för standardinstansen med Aspose.Words för .NET. Föreställ dig att du har alla dina anpassade typsnitt till hands, så att dina dokument ser ut precis som du föreställer dig dem. Låter bra, eller hur? Låt oss komma igång!

## Förutsättningar

Innan vi dyker in i detaljerna, låt oss se till att du har allt du behöver:
-  Aspose.Words för .NET: Se till att du har biblioteket installerat. Om inte, kan du[ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller någon annan .NET-kompatibel IDE.
- Grundläggande kunskaper i C#: Du bör vara bekväm med C#-programmering.
- Teckensnittsmapp: En katalog som innehåller dina anpassade typsnitt.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Detta hjälper till att komma åt de klasser och metoder som krävs för att ställa in teckensnittsmappen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss dela upp processen i enkla, lättsmälta steg.

## Steg 1: Definiera datakatalogen

Varje fantastisk resa börjar med ett enda steg, och vår börjar med att definiera katalogen där ditt dokument lagras. Det är här Aspose.Words kommer att leta efter ditt Word-dokument.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Här, byt ut`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentkatalog. Det är här ditt källdokument finns och där utdata kommer att sparas.

## Steg 2: Ställ in mappen Fonts

 Låt oss nu berätta för Aspose.Words var du kan hitta dina anpassade typsnitt. Detta görs genom att ställa in teckensnittsmappen med hjälp av`FontSettings.DefaultInstance.SetFontsFolder` metod.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 I den här raden,`"C:\\MyFonts\\"` är sökvägen till din anpassade typsnittsmapp. Den andra parametern,`true`, indikerar att teckensnitten i den här mappen ska skannas rekursivt.

## Steg 3: Ladda ditt dokument

 Med teckensnittsmappen inställd är nästa steg att ladda ditt Word-dokument i Aspose.Words. Detta görs med hjälp av`Document` klass.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Här,`dataDir + "Rendering.docx"` refererar till hela sökvägen till ditt Word-dokument. Se till att ditt dokument finns i den angivna katalogen.

## Steg 4: Spara dokumentet

Det sista steget är att spara ditt dokument efter att du har ställt in teckensnittsmappen. Detta säkerställer att dina anpassade teckensnitt tillämpas korrekt i utdata.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Den här raden sparar ditt dokument som en PDF med anpassade teckensnitt. Utdatafilen kommer att finnas i samma katalog som ditt källdokument.

## Slutsats

Och där har du det! Att ställa in typsnittsmappar för standardinstansen i Aspose.Words för .NET är enkelt när du delar upp det i enkla steg. Genom att följa den här guiden kan du se till att dina Word-dokument ser ut precis som du vill ha dem, med alla dina anpassade typsnitt på plats. Så varsågod, prova det och få dina dokument att glänsa!

## FAQ's

### Kan jag ställa in flera typsnittsmappar?
 Ja, du kan ställa in flera typsnittsmappar genom att använda`SetFontsFolders` metod som accepterar en rad mappsökvägar.

### Vilka filformat stöder Aspose.Words för att spara dokument?
Aspose.Words stöder olika format inklusive DOCX, PDF, HTML, EPUB och mer.

### Är det möjligt att använda online-teckensnitt i Aspose.Words?
Nej, Aspose.Words stöder för närvarande endast lokala teckensnittsfiler.

### Hur kan jag säkerställa att mina anpassade teckensnitt är inbäddade i den sparade PDF-filen?
 Genom att ställa in`FontSettings` korrekt och se till att typsnitten är tillgängliga, kommer Aspose.Words att bädda in dem i PDF-utdata.

### Vad händer om ett teckensnitt inte hittas i den angivna mappen?
Aspose.Words kommer att använda ett reservteckensnitt om det angivna teckensnittet inte hittas.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
