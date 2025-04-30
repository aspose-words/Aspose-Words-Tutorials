---
"description": "Lär dig hur du låser bildförhållandet för former i Word-dokument med Aspose.Words för .NET. Följ den här steg-för-steg-guiden för att hålla dina bilder och former proportionella."
"linktitle": "Bildförhållande låst"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Bildförhållande låst"
"url": "/sv/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bildförhållande låst

## Introduktion

Har du någonsin undrat hur du bibehåller perfekta proportioner för bilder och former i dina Word-dokument? Ibland behöver du se till att dina bilder och former inte förvrängs när de ändras i storlek. Det är här det är praktiskt att låsa bildförhållandet. I den här handledningen utforskar vi hur du ställer in bildförhållandet för former i Word-dokument med Aspose.Words för .NET. Vi delar upp det i lättförståeliga steg, så att du kan tillämpa dessa färdigheter i dina projekt med tillförsikt.

## Förkunskapskrav

Innan vi går in i koden, låt oss gå igenom vad du behöver för att komma igång:

- Aspose.Words för .NET-bibliotek: Du måste ha Aspose.Words för .NET installerat. Om du inte redan har gjort det kan du [ladda ner den här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Se till att du har en .NET-utvecklingsmiljö konfigurerad. Visual Studio är ett populärt val.
- Grundläggande kunskaper i C#: Viss förtrogenhet med C#-programmering är meriterande.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna. Dessa namnrymder ger oss tillgång till de klasser och metoder vi behöver för att arbeta med Word-dokument och former.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Steg 1: Konfigurera din dokumentkatalog

Innan vi börjar manipulera former måste vi skapa en katalog där våra dokument ska lagras. För enkelhetens skull använder vi en platshållare. `YOUR DOCUMENT DIRECTORY`Ersätt detta med den faktiska sökvägen till din dokumentkatalog.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument

Nästa steg är att skapa ett nytt Word-dokument med Aspose.Words. Dokumentet kommer att fungera som vår arbetsyta för att lägga till former och bilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Här skapar vi en instans av `Document` klass och använd en `DocumentBuilder` för att hjälpa oss att bygga dokumentinnehållet.

## Steg 3: Infoga en bild

Nu ska vi infoga en bild i vårt dokument. Vi använder `InsertImage` metod för `DocumentBuilder` klass. Se till att du har en avbildning i din angivna katalog.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Ersätta `dataDir + "Transparent background logo.png"` med sökvägen till din bildfil.

## Steg 4: Lås bildförhållandet

När bilden har infogats kan vi låsa dess bildförhållande. Att låsa bildförhållandet säkerställer att bildens proportioner förblir konstanta när du ändrar storlek.

```csharp
shape.AspectRatioLocked = true;
```

Miljö `AspectRatioLocked` till `true` säkerställer att bilden behåller sitt ursprungliga bildförhållande.

## Steg 5: Spara dokumentet

Slutligen sparar vi dokumentet i den angivna katalogen. I det här steget sparas alla ändringar vi har gjort i dokumentfilen.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Slutsats

Grattis! Du har nu lärt dig hur du ställer in bildförhållandet för former i Word-dokument med Aspose.Words för .NET. Genom att följa dessa steg kan du se till att dina bilder och former behåller sina proportioner, vilket gör att dina dokument ser professionella och eleganta ut. Experimentera gärna med olika bilder och former för att se hur låsfunktionen för bildförhållandet fungerar i olika scenarier.

## Vanliga frågor

### Kan jag låsa upp bildförhållandet efter att jag har låst det?
Ja, du kan låsa upp bildförhållandet genom att ställa in `shape.AspectRatioLocked = false`.

### Vad händer om jag ändrar storlek på en bild med ett låst bildförhållande?
Bildens storlek ändras proportionellt och det ursprungliga förhållandet mellan bredd och höjd bibehålls.

### Kan jag tillämpa detta på andra former förutom bilder?
Absolut! Funktionen för att låsa bildförhållandet kan tillämpas på alla former, inklusive rektanglar, cirklar med mera.

### Är Aspose.Words för .NET kompatibelt med .NET Core?
Ja, Aspose.Words för .NET stöder både .NET Framework och .NET Core.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
Du kan hitta omfattande dokumentation [här](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}