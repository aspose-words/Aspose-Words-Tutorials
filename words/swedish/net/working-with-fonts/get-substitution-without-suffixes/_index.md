---
title: Få substitution utan suffix
linktitle: Få substitution utan suffix
second_title: Aspose.Words Document Processing API
description: Lär dig hur du hanterar teckensnittsersättning utan suffix i Aspose.Words för .NET. Följ vår steg-för-steg-guide för att säkerställa att dina dokument ser perfekta ut varje gång.
weight: 10
url: /sv/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Få substitution utan suffix

## Introduktion

Välkommen till den här omfattande guiden om hur du hanterar teckensnittsersättning med Aspose.Words för .NET. Om du någonsin har kämpat med att teckensnitt inte visas korrekt i dina dokument, har du kommit till rätt plats. Denna handledning tar dig igenom en steg-för-steg-process för att effektivt hantera teckensnittsersättning utan suffix.

## Förutsättningar

Innan du dyker in i handledningen, se till att du har följande:

- Grundläggande kunskaper om C#: Att förstå C#-programmering gör det lättare att följa och implementera stegen.
-  Aspose.Words för .NET Library: Ladda ner och installera biblioteket från[nedladdningslänk](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Konfigurera en utvecklingsmiljö som Visual Studio för att skriva och köra din kod.
-  Exempeldokument: Ett exempeldokument (t.ex.`Rendering.docx`) att arbeta med under denna handledning.

## Importera namnområden

Först måste vi importera de nödvändiga namnområdena för att komma åt klasserna och metoderna som tillhandahålls av Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Steg 1: Definiera dokumentkatalogen

För att börja, ange katalogen där ditt dokument finns. Detta hjälper dig att hitta dokumentet du vill arbeta med.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ställ in utbytesvarningshanteraren

Därefter måste vi ställa in en varningshanterare som kommer att meddela oss när en teckensnittsersättning inträffar under dokumentbehandlingen. Detta är avgörande för att fånga upp och hantera eventuella teckensnittsproblem.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Steg 3: Lägg till anpassade teckensnittskällor

I det här steget kommer vi att lägga till anpassade teckensnittskällor för att säkerställa att Aspose.Words kan hitta och använda rätt typsnitt. Detta är särskilt användbart om du har specifika teckensnitt lagrade i anpassade kataloger.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

I denna kod:
-  Vi hämtar de aktuella teckensnittskällorna och lägger till en ny`FolderFontSource` pekar på vår anpassade teckensnittskatalog (`C:\\MyFonts\\`).
- Vi uppdaterar sedan teckensnittskällorna med denna nya lista.

## Steg 4: Spara dokumentet

Slutligen sparar du dokumentet efter att du har tillämpat inställningarna för teckensnittsersättning. För den här handledningen sparar vi den som en PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Steg 5: Skapa varningshanterarens klass

 För att hantera varningar effektivt, skapa en anpassad klass som implementerar`IWarningCallback` gränssnitt. Den här klassen kommer att fånga och logga alla varningar för teckensnittsersättning.

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
-  De`Warning`metoden fångar varningar relaterade till teckensnittsersättning.
-  De`FontWarnings` insamling lagrar dessa varningar för vidare inspektion eller loggning.

## Slutsats

Du har nu bemästrat processen att hantera teckensnittsersättning utan suffix med Aspose.Words för .NET. Denna kunskap säkerställer att dina dokument behåller sitt avsedda utseende, oavsett vilka teckensnitt som finns tillgängliga i systemet. Fortsätt att experimentera med olika inställningar och källor för att fullt ut utnyttja kraften i Aspose.Words.

## FAQ's

### Hur kan jag använda typsnitt från flera anpassade kataloger?

 Du kan lägga till flera`FolderFontSource` instanser till`fontSources` lista och uppdatera teckensnittskällorna därefter.

### Var kan jag ladda ner en gratis testversion av Aspose.Words för .NET?

 Du kan ladda ner en gratis testversion från[Aspose gratis provsida](https://releases.aspose.com/).

###  Kan jag hantera flera typer av varningar med`IWarningCallback`?

 Ja, den`IWarningCallback` gränssnitt låter dig hantera olika typer av varningar, inte bara teckensnittsersättning.

### Var kan jag få support för Aspose.Words?

 För support, besök[Aspose.Words supportforum](https://forum.aspose.com/c/words/8).

### Är det möjligt att köpa en tillfällig licens?

 Ja, du kan få en tillfällig licens från[sida för tillfällig licens](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
