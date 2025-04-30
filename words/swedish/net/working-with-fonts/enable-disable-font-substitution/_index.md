---
"description": "Lär dig hur du aktiverar eller inaktiverar teckensnittsersättning i Word-dokument med Aspose.Words för .NET. Se till att dina dokument ser enhetliga ut på alla plattformar."
"linktitle": "Aktivera Inaktivera teckensnittsersättning"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Aktivera Inaktivera teckensnittsersättning"
"url": "/sv/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera Inaktivera teckensnittsersättning

## Introduktion

Har du någonsin hamnat i en situation där dina noggrant utvalda teckensnitt i ett Word-dokument ersätts när det visas på en annan dator? Irriterande, eller hur? Detta händer på grund av teckensnittsersättning, en process där systemet ersätter ett saknat teckensnitt med ett tillgängligt. Men oroa dig inte! Med Aspose.Words för .NET kan du enkelt hantera och kontrollera teckensnittsersättning. I den här handledningen guidar vi dig genom stegen för att aktivera eller inaktivera teckensnittsersättning i dina Word-dokument, så att dina dokument alltid ser ut precis som du vill.

## Förkunskapskrav

Innan vi går vidare till stegen, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET: Ladda ner den senaste versionen [här](https://releases.aspose.com/words/net/).
- Visual Studio: Alla versioner som stöder .NET.
- Grundläggande kunskaper i C#: Detta hjälper dig att följa kodningsexemplen.

## Importera namnrymder

För att komma igång, se till att du har importerat de nödvändiga namnrymderna i ditt projekt. Lägg till dessa högst upp i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nu ska vi dela upp processen i enkla, hanterbara steg.

## Steg 1: Konfigurera ditt projekt

Först, skapa ett nytt projekt i Visual Studio och lägg till en referens till Aspose.Words för .NET-biblioteket. Om du inte redan har gjort det, ladda ner det från [Aspose webbplats](https://releases.aspose.com/words/net/).

## Steg 2: Ladda ditt dokument

Ladda sedan in dokumentet du vill arbeta med. Så här gör du:

```csharp
// Sökväg till din dokumentkatalog 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentkatalog. Den här koden laddar dokumentet till minnet så att du kan manipulera det.

## Steg 3: Konfigurera teckensnittsinställningar

Nu ska vi skapa en `FontSettings` objekt för att hantera inställningarna för teckensnittsersättning:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Steg 4: Ställ in standardteckensnittsersättning

Ställ in standardteckensnittsersättningen till ett teckensnitt du själv väljer. Detta teckensnitt används om originalteckensnittet inte är tillgängligt:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

det här exemplet använder vi Arial som standardteckensnitt.

## Steg 5: Inaktivera ersättning av teckensnittsinformation

För att inaktivera ersättning av teckensnittsinformation, vilket hindrar systemet från att ersätta saknade teckensnitt med tillgängliga, använd följande kod:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Steg 6: Tillämpa teckensnittsinställningar på dokumentet

Tillämpa nu dessa inställningar på ditt dokument:

```csharp
doc.FontSettings = fontSettings;
```

## Steg 7: Spara ditt dokument

Slutligen, spara ditt ändrade dokument. Du kan spara det i vilket format du vill. I den här handledningen sparar vi det som en PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt styra teckensnittsersättning i dina Word-dokument med hjälp av Aspose.Words för .NET. Detta säkerställer att dina dokument behåller sitt avsedda utseende och känsla, oavsett var de visas.

## Vanliga frågor

### Kan jag använda andra typsnitt än Arial som ersättning?

Absolut! Du kan ange vilket teckensnitt som helst som finns tillgängligt på ditt system genom att ändra teckensnittsnamnet i `DefaultFontName` egendom.

### Vad händer om det angivna standardteckensnittet inte är tillgängligt?

Om standardteckensnittet inte är tillgängligt kommer Aspose.Words att använda en systemåterställningsmekanism för att hitta en lämplig ersättning.

### Kan jag aktivera teckensnittsersättning igen efter att jag har inaktiverat det?

Ja, du kan växla `Enabled` egendom av `FontInfoSubstitution` tillbaka till `true` om du vill aktivera teckensnittsersättning igen.

### Finns det något sätt att kontrollera vilka typsnitt som ersätts?

Ja, Aspose.Words tillhandahåller metoder för att logga och spåra teckensnittsersättning, så att du kan se vilka teckensnitt som ersätts.

### Kan jag använda den här metoden för andra dokumentformat förutom DOCX?

Absolut! Aspose.Words stöder olika format, och du kan tillämpa dessa teckensnittsinställningar på alla format som stöds.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}