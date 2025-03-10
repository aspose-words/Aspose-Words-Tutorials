---
title: Ställ in typsnittsmapp
linktitle: Ställ in typsnittsmapp
second_title: Aspose.Words Document Processing API
description: Lär dig hur du ställer in en anpassad typsnittsmapp i Aspose.Words för .NET för att säkerställa att dina Word-dokument renderas korrekt utan att teckensnitt saknas.
weight: 10
url: /sv/net/working-with-fonts/set-fonts-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in typsnittsmapp

## Introduktion

Har du någonsin stött på problem med saknade teckensnitt när du arbetar med Word-dokument i din .NET-applikation? Tja, du är inte ensam. Att ställa in rätt teckensnittsmapp kan lösa detta problem sömlöst. I den här guiden går vi igenom hur du ställer in teckensnittsmappen med Aspose.Words för .NET. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

- Visual Studio installerat på din dator
- .NET Framework-inställning
-  Aspose.Words för .NET-bibliotek. Om du inte redan har gjort det kan du ladda ner det från[här](https://releases.aspose.com/words/net/).

## Importera namnområden

Först måste du importera de nödvändiga namnområdena för att arbeta med Aspose.Words. Lägg till följande rader överst i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Det är enkelt att ställa in teckensnittsmappen om du följer dessa steg noggrant.

## Steg 1: Definiera dokumentkatalogen

Före allt annat, definiera sökvägen till din dokumentkatalog. Den här katalogen kommer att innehålla dina Word-dokument och de teckensnitt du vill använda.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Se till att byta ut`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din katalog.

## Steg 2: Initiera FontSettings

 Nu måste du initiera`FontSettings` objekt. Detta objekt låter dig ange anpassade typsnittsmappar.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Steg 3: Ställ in mappen Fonts

 Med hjälp av`SetFontsFolder` metod för`FontSettings` objekt, ange mappen där dina anpassade teckensnitt lagras.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

 Här,`dataDir + "Fonts"` pekar på mappen med namnet "Teckensnitt" i din dokumentkatalog. Den andra parametern,`false`, indikerar att mappen inte är rekursiv.

## Steg 4: Skapa LoadOptions

 Skapa sedan en instans av`LoadOptions` klass. Den här klassen hjälper dig att ladda dokumentet med de angivna teckensnittsinställningarna.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## Steg 5: Ladda dokumentet

 Slutligen laddar du Word-dokumentet med hjälp av`Document` klass och`LoadOptions` objekt.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

 Se till att`"Rendering.docx"` är namnet på ditt Word-dokument. Du kan ersätta den med namnet på din fil.

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt ställa in en anpassad typsnittsmapp i Aspose.Words för .NET, vilket säkerställer att alla dina typsnitt är korrekt renderade. Denna enkla installation kan spara mycket huvudvärk och få dina dokument att se ut precis som du vill att de ska se ut.

## FAQ's

### Varför måste jag ställa in en anpassad typsnittsmapp?
Att ställa in en anpassad typsnittsmapp säkerställer att alla teckensnitt som används i dina Word-dokument är korrekt återgivna, vilket undviker teckensnittsproblem.

### Kan jag ställa in flera typsnittsmappar?
 Ja, du kan använda`SetFontsFolders` metod för att ange flera mappar.

### Vad händer om ett teckensnitt inte hittas?
Aspose.Words kommer att försöka ersätta det saknade teckensnittet med ett liknande från systemteckensnitten.

### Är Aspose.Words kompatibelt med .NET Core?
Ja, Aspose.Words stöder .NET Core tillsammans med .NET Framework.

### Var kan jag få support om jag stöter på problem?
 Du kan få stöd från[Aspose.Words supportforum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
