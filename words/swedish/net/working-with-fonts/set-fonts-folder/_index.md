---
"description": "Lär dig hur du ställer in en mapp för anpassade teckensnitt i Aspose.Words för .NET för att säkerställa att dina Word-dokument återges korrekt utan att teckensnitt saknas."
"linktitle": "Ange teckensnittsmapp"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ange teckensnittsmapp"
"url": "/sv/net/working-with-fonts/set-fonts-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ange teckensnittsmapp

## Introduktion

Har du någonsin stött på problem med saknade teckensnitt när du arbetat med Word-dokument i ditt .NET-program? Då är du inte ensam. Att ställa in rätt teckensnittsmapp kan lösa problemet smidigt. I den här guiden går vi igenom hur du ställer in teckensnittsmappen med Aspose.Words för .NET. Nu kör vi!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

- Visual Studio installerat på din dator
- .NET Framework-konfiguration
- Aspose.Words för .NET-biblioteket. Om du inte redan har gjort det kan du ladda ner det från [här](https://releases.aspose.com/words/net/).

## Importera namnrymder

Först måste du importera de namnrymder som krävs för att fungera med Aspose.Words. Lägg till följande rader högst upp i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Att konfigurera fontmappen är enkelt om du följer dessa steg noggrant.

## Steg 1: Definiera dokumentkatalogen

Innan du gör något annat, ange sökvägen till din dokumentkatalog. Den här katalogen kommer att innehålla dina Word-dokument och de teckensnitt du vill använda.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Se till att byta ut `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din katalog.

## Steg 2: Initiera teckensnittsinställningar

Nu behöver du initialisera `FontSettings` objekt. Det här objektet låter dig ange anpassade teckensnittsmappar.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Steg 3: Ställ in teckensnittsmappen

Använda `SetFontsFolder` metod för `FontSettings` objekt, ange mappen där dina anpassade teckensnitt lagras.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

Här, `dataDir + "Fonts"` pekar på mappen med namnet "Teckensnitt" i din dokumentkatalog. Den andra parametern, `false`, indikerar att mappen inte är rekursiv.

## Steg 4: Skapa LoadOptions

Skapa sedan en instans av `LoadOptions` klass. Den här klassen hjälper dig att ladda dokumentet med de angivna teckensnittsinställningarna.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## Steg 5: Ladda dokumentet

Slutligen, ladda Word-dokumentet med hjälp av `Document` klass och `LoadOptions` objekt.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

Se till att `"Rendering.docx"` är namnet på ditt Word-dokument. Du kan ersätta det med namnet på din fil.

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt skapa en mapp med anpassade teckensnitt i Aspose.Words för .NET, vilket säkerställer att alla dina teckensnitt återges korrekt. Denna enkla installation kan bespara dig mycket huvudbry och få dina dokument att se ut precis som du vill.

## Vanliga frågor

### Varför behöver jag skapa en mapp för anpassade teckensnitt?
Att skapa en mapp för anpassade teckensnitt säkerställer att alla teckensnitt som används i dina Word-dokument återges korrekt, vilket undviker problem med att sakna teckensnitt.

### Kan jag ställa in flera mappar för teckensnitt?
Ja, du kan använda `SetFontsFolders` metod för att ange flera mappar.

### Vad händer om ett typsnitt inte hittas?
Aspose.Words kommer att försöka ersätta det saknade teckensnittet med ett liknande från systemteckensnitten.

### Är Aspose.Words kompatibelt med .NET Core?
Ja, Aspose.Words stöder .NET Core tillsammans med .NET Framework.

### Var kan jag få stöd om jag stöter på problem?
Du kan få stöd från [Aspose.Words supportforum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}