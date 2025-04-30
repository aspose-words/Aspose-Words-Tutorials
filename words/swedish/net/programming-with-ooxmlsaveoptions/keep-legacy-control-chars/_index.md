---
"description": "Lär dig hur du bevarar äldre kontrolltecken i Word-dokument med Aspose.Words för .NET med den här steg-för-steg-guiden."
"linktitle": "Behåll äldre kontrolltecken"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Behåll äldre kontrolltecken"
"url": "/sv/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Behåll äldre kontrolltecken

## Introduktion

Har du någonsin blivit förbryllad över de där konstiga, osynliga kontrolltecknen i dina Word-dokument? De är som små, dolda gremlin-tecken som kan störa formatering och funktionalitet. Som tur är erbjuder Aspose.Words för .NET en praktisk funktion för att hålla dessa äldre kontrolltecken intakta när du sparar dokument. I den här handledningen går vi djupare in i hur man hanterar dessa kontrolltecken med Aspose.Words för .NET. Vi går igenom det steg för steg, så att du förstår varje detalj längs vägen. Redo att komma igång? Nu kör vi!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET: Ladda ner och installera från [här](https://releases.aspose.com/words/net/).
2. En giltig Aspose-licens: Du kan få en tillfällig licens [här](https://purchase.aspose.com/temporary-license/).
3. Utvecklingsmiljö: Visual Studio eller annan IDE som stöder .NET.
4. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# är meriterande.

## Importera namnrymder

Innan du skriver din kod måste du importera de nödvändiga namnrymderna. Lägg till följande rader högst upp i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera ditt projekt

Först måste du konfigurera ditt projekt i Visual Studio (eller din föredragna IDE). 

1. Skapa ett nytt C#-projekt: Öppna Visual Studio och skapa ett nytt C#-konsolapplikationsprojekt.
2. Installera Aspose.Words för .NET: Använd NuGet Package Manager för att installera Aspose.Words för .NET. Högerklicka på ditt projekt i Solution Explorer, välj "Hantera NuGet-paket", sök efter "Aspose.Words" och installera det.

## Steg 2: Ladda ditt dokument

Därefter laddar du Word-dokumentet som innehåller de äldre kontrolltecknen.

1. Ange dokumentsökvägen: Ange sökvägen till din dokumentkatalog.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. Ladda dokumentet: Använd `Document` klass för att ladda ditt dokument.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Steg 3: Konfigurera sparalternativ

Nu ska vi konfigurera sparalternativen för att behålla de äldre kontrolltecknen intakta.

1. Skapa sparalternativ: Initiera en instans av `OoxmlSaveOptions` och ställ in `KeepLegacyControlChars` egendom till `true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Steg 4: Spara dokumentet

Spara slutligen dokumentet med de konfigurerade sparalternativen.

1. Spara dokumentet: Använd `Save` metod för `Document` klassen för att spara dokumentet med de angivna sparalternativen.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du säkerställa att dina äldre kontrolltecken bevaras när du arbetar med Word-dokument i Aspose.Words för .NET. Den här funktionen kan vara en livräddare, särskilt när du hanterar komplexa dokument där kontrolltecken spelar en avgörande roll. 

## Vanliga frågor

### Vad är äldre kontrolltecken?

Äldre kontrolltecken är tecken som inte skrivs ut och som används i äldre dokument för att styra formatering och layout.

### Kan jag ta bort dessa kontrolltecknen istället för att behålla dem?

Ja, du kan använda Aspose.Words för .NET för att ta bort eller ersätta dessa tecken om det behövs.

### Är den här funktionen tillgänglig i alla versioner av Aspose.Words för .NET?

Den här funktionen är tillgänglig i senare versioner. Se till att använda den senaste versionen för att få tillgång till alla funktioner.

### Behöver jag en licens för att använda Aspose.Words för .NET?

Ja, du behöver ett giltigt körkort. Du kan få ett tillfälligt körkort för utvärderingsändamål. [här](https://purchase.aspose.com/temporary-license/).

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?

Du kan hitta detaljerad dokumentation [här](https://reference.aspose.com/words/net/).
 


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}