---
title: Aktivera Inaktivera teckensnittsersättning
linktitle: Aktivera Inaktivera teckensnittsersättning
second_title: Aspose.Words Document Processing API
description: Lär dig hur du aktiverar eller inaktiverar teckensnittsersättning i Word-dokument med Aspose.Words för .NET. Se till att dina dokument ser konsekventa ut på alla plattformar.
weight: 10
url: /sv/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera Inaktivera teckensnittsersättning

## Introduktion

Har du någonsin hamnat i en situation där dina noggrant valda teckensnitt i ett Word-dokument ersätts när de visas på en annan dator? Irriterande, eller hur? Detta händer på grund av teckensnittsersättning, en process där systemet ersätter ett saknat teckensnitt med ett tillgängligt. Men oroa dig inte! Med Aspose.Words för .NET kan du enkelt hantera och kontrollera teckensnittsersättning. I den här handledningen går vi igenom stegen för att aktivera eller inaktivera teckensnittsersättning i dina Word-dokument, för att säkerställa att dina dokument alltid ser ut precis som du vill ha dem.

## Förutsättningar

Innan vi dyker in i stegen, låt oss se till att du har allt du behöver:

-  Aspose.Words för .NET: Ladda ner den senaste versionen[här](https://releases.aspose.com/words/net/).
- Visual Studio: Alla versioner som stöder .NET.
- Grundläggande kunskaper om C#: Detta hjälper dig att följa med i kodningsexemplen.

## Importera namnområden

För att komma igång, se till att du har de nödvändiga namnrymden importerade i ditt projekt. Lägg till dessa överst i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Låt oss nu dela upp processen i enkla, hanterbara steg.

## Steg 1: Konfigurera ditt projekt

Skapa först ett nytt projekt i Visual Studio och lägg till en referens till Aspose.Words for .NET-biblioteket. Om du inte redan har gjort det, ladda ner den från[Aspose hemsida](https://releases.aspose.com/words/net/).

## Steg 2: Ladda ditt dokument

Ladda sedan in dokumentet du vill arbeta med. Så här gör du:

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentkatalog. Den här koden laddar dokumentet i minnet så att du kan manipulera det.

## Steg 3: Konfigurera teckensnittsinställningar

 Låt oss nu skapa en`FontSettings` objekt för att hantera inställningarna för teckensnittsersättning:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Steg 4: Ställ in standardtypsnittsersättning

Ställ in standardtypsnittsersättningen till ett teckensnitt som du väljer. Detta teckensnitt kommer att användas om det ursprungliga teckensnittet inte är tillgängligt:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

I det här exemplet använder vi Arial som standardteckensnitt.

## Steg 5: Inaktivera Font Info Substitution

För att inaktivera teckensnittsinformationsersättning, som hindrar systemet från att ersätta saknade teckensnitt med tillgängliga, använder du följande kod:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Steg 6: Tillämpa teckensnittsinställningar på dokumentet

Tillämpa nu dessa inställningar på ditt dokument:

```csharp
doc.FontSettings = fontSettings;
```

## Steg 7: Spara ditt dokument

Slutligen, spara ditt ändrade dokument. Du kan spara den i vilket format du vill. För den här handledningen sparar vi den som en PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt kontrollera teckensnittsersättning i dina Word-dokument med Aspose.Words för .NET. Detta säkerställer att dina dokument behåller sitt avsedda utseende och känsla, oavsett var de visas.

## FAQ's

### Kan jag använda andra typsnitt än Arial för ersättning?

 Absolut! Du kan ange alla teckensnitt som är tillgängliga på ditt system genom att ändra teckensnittsnamnet i`DefaultFontName` egendom.

### Vad händer om det angivna standardteckensnittet inte är tillgängligt?

Om standardteckensnittet inte är tillgängligt kommer Aspose.Words att använda en reservmekanism för att hitta en lämplig ersättning.

### Kan jag aktivera teckensnittsersättning igen efter att ha inaktiverat det?

 Ja, du kan växla mellan`Enabled` egendom av`FontInfoSubstitution` tillbaka till`true` om du vill aktivera teckensnittsersättning igen.

### Finns det något sätt att kontrollera vilka typsnitt som ersätts?

Ja, Aspose.Words tillhandahåller metoder för att logga och spåra teckensnittsersättning, så att du kan se vilka teckensnitt som ersätts.

### Kan jag använda den här metoden för andra dokumentformat än DOCX?

Definitivt! Aspose.Words stöder olika format, och du kan tillämpa dessa teckensnittsinställningar på alla format som stöds.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
