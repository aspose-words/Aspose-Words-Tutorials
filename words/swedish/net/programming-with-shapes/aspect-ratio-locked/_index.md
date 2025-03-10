---
title: Bildförhållande låst
linktitle: Bildförhållande låst
second_title: Aspose.Words Document Processing API
description: Lär dig hur du låser bildförhållandet för former i Word-dokument med Aspose.Words för .NET. Följ den här steg-för-steg-guiden för att hålla dina bilder och former proportionerliga.
weight: 10
url: /sv/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bildförhållande låst

## Introduktion

Har du någonsin undrat hur man bibehåller de perfekta proportionerna av bilder och former i dina Word-dokument? Ibland måste du se till att dina bilder och former inte blir förvrängda när du ändrar storlek. Det är här det är praktiskt att låsa bildförhållandet. I den här självstudien kommer vi att utforska hur man ställer in bildförhållandet för former i Word-dokument med Aspose.Words för .NET. Vi delar upp det i steg som är lätta att följa och ser till att du kan tillämpa dessa färdigheter på dina projekt med tillförsikt.

## Förutsättningar

Innan vi dyker in i koden, låt oss gå igenom vad du behöver för att komma igång:

- Aspose.Words for .NET Library: Du måste ha Aspose.Words för .NET installerat. Om du inte redan har gjort det kan du[ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Se till att du har en .NET-utvecklingsmiljö inrättad. Visual Studio är ett populärt val.
- Grundläggande kunskaper i C#: Viss förtrogenhet med C#-programmering kommer att vara till hjälp.

## Importera namnområden

Till att börja med, låt oss importera de nödvändiga namnrymden. Dessa namnrymder ger oss tillgång till de klasser och metoder vi behöver för att arbeta med Word-dokument och former.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Steg 1: Konfigurera din dokumentkatalog

 Innan vi börjar manipulera former måste vi skapa en katalog där våra dokument kommer att lagras. För enkelhetens skull använder vi en platshållare`YOUR DOCUMENT DIRECTORY`. Ersätt detta med den faktiska sökvägen till din dokumentkatalog.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument

Därefter skapar vi ett nytt Word-dokument med Aspose.Words. Detta dokument kommer att fungera som vår arbetsyta för att lägga till former och bilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Här skapar vi en instans av`Document` klass och använd a`DocumentBuilder` för att hjälpa oss bygga dokumentinnehållet.

## Steg 3: Infoga en bild

 Låt oss nu infoga en bild i vårt dokument. Vi kommer att använda`InsertImage` metod för`DocumentBuilder`klass. Se till att du har en bild i din angivna katalog.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Ersätta`dataDir + "Transparent background logo.png"` med sökvägen till din bildfil.

## Steg 4: Lås bildförhållandet

När bilden väl har infogats kan vi låsa dess bildförhållande. Låsning av bildförhållandet säkerställer att bildens proportioner förblir konstanta när du ändrar storlek.

```csharp
shape.AspectRatioLocked = true;
```

 Miljö`AspectRatioLocked` till`true` ser till att bilden bibehåller sitt ursprungliga bildförhållande.

## Steg 5: Spara dokumentet

Slutligen sparar vi dokumentet i den angivna katalogen. Detta steg skriver alla ändringar vi har gjort i dokumentfilen.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Slutsats

Grattis! Du har framgångsrikt lärt dig hur du ställer in bildförhållandet för former i Word-dokument med Aspose.Words för .NET. Genom att följa dessa steg kan du se till att dina bilder och former behåller sina proportioner, vilket gör att dina dokument ser professionella och polerade ut. Experimentera gärna med olika bilder och former för att se hur låsningsfunktionen för bildförhållande fungerar i olika scenarier.

## FAQ's

### Kan jag låsa upp bildförhållandet efter att ha låst det?
Ja, du kan låsa upp bildförhållandet genom att ställa in`shape.AspectRatioLocked = false`.

### Vad händer om jag ändrar storlek på en bild med ett låst bildförhållande?
Bilden kommer att ändra storleken proportionellt och behålla sitt ursprungliga förhållande mellan bredd och höjd.

### Kan jag tillämpa detta på andra former än bilder?
Absolut! Låsningsfunktionen för bildförhållande kan appliceras på alla former, inklusive rektanglar, cirklar och mer.

### Är Aspose.Words for .NET kompatibelt med .NET Core?
Ja, Aspose.Words för .NET stöder både .NET Framework och .NET Core.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
 Du kan hitta omfattande dokumentation[här](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
