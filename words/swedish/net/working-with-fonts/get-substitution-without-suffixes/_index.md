---
"description": "Lär dig hur du hanterar teckensnittsersättning utan suffix i Aspose.Words för .NET. Följ vår steg-för-steg-guide för att säkerställa att dina dokument ser perfekta ut varje gång."
"linktitle": "Hämta substitution utan suffix"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Hämta substitution utan suffix"
"url": "/sv/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hämta substitution utan suffix

## Introduktion

Välkommen till den här omfattande guiden om hur du hanterar typsnittsersättning med Aspose.Words för .NET. Om du någonsin har haft problem med att typsnitt inte visas korrekt i dina dokument har du kommit till rätt ställe. Den här handledningen tar dig igenom en steg-för-steg-process för att effektivt hantera typsnittsersättning utan suffix.

## Förkunskapskrav

Innan du går in i handledningen, se till att du har följande:

- Grundläggande kunskaper i C#: Att förstå C#-programmering gör det lättare att följa och implementera stegen.
- Aspose.Words för .NET-biblioteket: Ladda ner och installera biblioteket från [nedladdningslänk](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Konfigurera en utvecklingsmiljö som Visual Studio för att skriva och köra din kod.
- Exempeldokument: Ett exempeldokument (t.ex. `Rendering.docx`) att arbeta med under den här handledningen.

## Importera namnrymder

Först måste vi importera de namnrymder som behövs för att komma åt klasserna och metoderna som tillhandahålls av Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Steg 1: Definiera dokumentkatalogen

Börja med att ange katalogen där ditt dokument finns. Detta hjälper dig att hitta det dokument du vill arbeta med.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Konfigurera hanteraren för ersättningsvarningar

Nästa steg är att konfigurera en varningshanterare som meddelar oss när ett teckensnittsbyte sker under dokumentbearbetningen. Detta är avgörande för att upptäcka och hantera eventuella teckensnittsproblem.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Steg 3: Lägg till anpassade teckensnittskällor

I det här steget lägger vi till anpassade typsnittskällor för att säkerställa att Aspose.Words kan hitta och använda rätt typsnitt. Detta är särskilt användbart om du har specifika typsnitt lagrade i anpassade kataloger.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

I den här koden:
- Vi hämtar de aktuella teckensnittskällorna och lägger till en ny `FolderFontSource` pekar på vår anpassade typsnittskatalog (`C:\\MyFonts\\`).
- Sedan uppdaterar vi teckensnittskällorna med den här nya listan.

## Steg 4: Spara dokumentet

Slutligen, spara dokumentet efter att du har tillämpat inställningarna för teckensnittsersättning. I den här handledningen sparar vi det som en PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Steg 5: Skapa varningshanterarklassen

För att hantera varningar effektivt, skapa en anpassad klass som implementerar `IWarningCallback` gränssnitt. Den här klassen kommer att fånga och logga alla varningar om teckensnittsersättning.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

I den här klassen:
- De `Warning` Metoden fångar upp varningar relaterade till teckensnittsersättning.
- De `FontWarnings` samlingen lagrar dessa varningar för vidare inspektion eller loggning.

## Slutsats

Du har nu bemästrat processen att hantera teckensnittsersättning utan suffix med Aspose.Words för .NET. Denna kunskap säkerställer att dina dokument behåller sitt avsedda utseende, oavsett vilka teckensnitt som finns tillgängliga i systemet. Fortsätt experimentera med olika inställningar och källor för att fullt ut utnyttja kraften i Aspose.Words.

## Vanliga frågor

### Hur kan jag använda teckensnitt från flera anpassade kataloger?

Du kan lägga till flera `FolderFontSource` instanser till `fontSources` lista och uppdatera teckensnittskällorna därefter.

### Var kan jag ladda ner en gratis testversion av Aspose.Words för .NET?

Du kan ladda ner en gratis provversion från [Aspose gratis provperiodsida](https://releases.aspose.com/).

### Kan jag hantera flera typer av varningar med hjälp av `IWarningCallback`?

Ja, den `IWarningCallback` Gränssnittet låter dig hantera olika typer av varningar, inte bara teckensnittsersättning.

### Var kan jag få support för Aspose.Words?

För support, besök [Aspose.Words supportforum](https://forum.aspose.com/c/words/8).

### Är det möjligt att köpa en tillfällig licens?

Ja, du kan få ett tillfälligt körkort från [sida om tillfällig licens](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}