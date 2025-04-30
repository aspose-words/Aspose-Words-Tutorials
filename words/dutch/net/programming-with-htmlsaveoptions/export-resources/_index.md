---
"description": "Leer hoe je bronnen zoals CSS en lettertypen kunt exporteren en tegelijkertijd Word-documenten als HTML kunt opslaan met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding."
"linktitle": "Exporteer bronnen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Exporteer bronnen"
"url": "/nl/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exporteer bronnen

## Invoering

Hallo, mede-technologiefanaat! Als je ooit Word-documenten naar HTML moest converteren, ben je hier aan het juiste adres. Vandaag duiken we in de wondere wereld van Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het werken met Word-documenten een fluitje van een cent. In deze tutorial laten we je de stappen zien om bronnen, zoals lettertypen en CSS, te exporteren wanneer je een Word-document als HTML opslaat met Aspose.Words voor .NET. Maak je klaar voor een leuke en leerzame rit!

## Vereisten

Voordat we in de code duiken, zorgen we ervoor dat je alles hebt wat je nodig hebt om aan de slag te gaan. Hier is een korte checklist:

1. Visual Studio: Zorg ervoor dat Visual Studio op uw computer is geïnstalleerd. U kunt het downloaden van de [Visual Studio-website](https://visualstudio.microsoft.com/).
2. Aspose.Words voor .NET: Je hebt de Aspose.Words voor .NET-bibliotheek nodig. Als je deze nog niet hebt, download dan een gratis proefversie. [Aspose-releases](https://releases.aspose.com/words/net/) of koop het bij de [Aspose Winkel](https://purchase.aspose.com/buy).
3. Basiskennis van C#: Een fundamenteel begrip van C# helpt u de codevoorbeelden te volgen.

Alles begrepen? Geweldig! Laten we verdergaan met het importeren van de benodigde naamruimten.

## Naamruimten importeren

Om Aspose.Words voor .NET te gebruiken, moet u de relevante naamruimten in uw project opnemen. Zo doet u dat:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Deze naamruimten zijn essentieel voor de toegang tot de Aspose.Words-klassen en -methoden die we in deze zelfstudie gebruiken.

Laten we het proces van het exporteren van bronnen bij het opslaan van een Word-document als HTML-bestand eens nader bekijken. We doen dit stap voor stap, zodat het gemakkelijk te volgen is.

## Stap 1: Stel uw documentenmap in

Allereerst moet u het pad naar uw documentenmap opgeven. Dit is waar uw Word-document zich bevindt en waar het HTML-bestand wordt opgeslagen.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw directory.

## Stap 2: Laad het Word-document

Laten we nu het Word-document laden dat je naar HTML wilt converteren. Voor deze tutorial gebruiken we een document met de naam `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Met deze regel code wordt het document geladen vanuit de opgegeven directory.

## Stap 3: Configureer HTML-opslagopties

Om bronnen zoals CSS en lettertypen te exporteren, moet u de volgende instellingen gebruiken: `HtmlSaveOptions`Deze stap is cruciaal om ervoor te zorgen dat uw HTML-uitvoer goed gestructureerd is en de benodigde bronnen bevat.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://voorbeeld.com/bronnen"
};
```

Laten we eens kijken wat elke optie doet:
- `CssStyleSheetType = CssStyleSheetType.External`: Met deze optie wordt opgegeven dat CSS-stijlen in een extern stijlblad moeten worden opgeslagen.
- `ExportFontResources = true`: Hiermee kunt u lettertypebronnen exporteren.
- `ResourceFolder = dataDir + "Resources"`: Geeft de lokale map op waar bronnen (zoals lettertypen en CSS-bestanden) worden opgeslagen.
- `ResourceFolderAlias = "http://example.com/resources"`: Hiermee stelt u een alias in voor de resourcemap, die in het HTML-bestand wordt gebruikt.

## Stap 4: Sla het document op als HTML

Nadat de opslagopties zijn geconfigureerd, is de laatste stap het opslaan van het document als HTML-bestand. Zo doet u dat:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Deze regel code slaat het document op in HTML-formaat, samen met de geëxporteerde bronnen.

## Conclusie

En voilà! Je hebt met succes bronnen geëxporteerd terwijl je een Word-document als HTML opsloeg met Aspose.Words voor .NET. Met deze krachtige bibliotheek wordt het programmatisch verwerken van Word-documenten een fluitje van een cent. Of je nu werkt aan een webapplicatie of documenten wilt converteren voor offline gebruik, Aspose.Words helpt je daarbij.

## Veelgestelde vragen

### Kan ik afbeeldingen samen met lettertypen en CSS exporteren?
Ja, dat kan! Aspose.Words voor .NET ondersteunt ook het exporteren van afbeeldingen. Zorg er wel voor dat je de `HtmlSaveOptions` overeenkomstig.

### Is er een manier om CSS in te sluiten in plaats van een extern stijlblad te gebruiken?
Absoluut. Je kunt instellen `CssStyleSheetType` naar `CssStyleSheetType.Embedded` als u de voorkeur geeft aan ingebedde stijlen.

### Hoe kan ik de naam van het HTML-uitvoerbestand aanpassen?
U kunt elke gewenste bestandsnaam opgeven in de `doc.Save` methode. Bijvoorbeeld, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Ondersteunt Aspose.Words andere formaten dan HTML?
Ja, het ondersteunt verschillende formaten, waaronder PDF, DOCX, TXT en meer. Bekijk de [documentatie](https://reference.aspose.com/words/net/) voor een volledige lijst.

### Waar kan ik meer ondersteuning en middelen krijgen?
Voor meer hulp, bezoek de [Aspose.Words Ondersteuningsforum](https://forum.aspose.com/c/words/8)Gedetailleerde documentatie en voorbeelden vindt u ook op de [Aspose-website](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}