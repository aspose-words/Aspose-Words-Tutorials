---
title: Exporteer bronnen
linktitle: Exporteer bronnen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u bronnen zoals CSS en lettertypen kunt exporteren terwijl u Word-documenten opslaat als HTML met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exporteer bronnen

## Invoering

Hallo, mede-tech-enthousiasteling! Als je ooit Word-documenten naar HTML hebt moeten converteren, ben je hier aan het juiste adres. Vandaag duiken we in de wondere wereld van Aspose.Words voor .NET. Deze krachtige bibliotheek maakt het een fluitje van een cent om programmatisch met Word-documenten te werken. In deze tutorial nemen we je mee door de stappen om bronnen, zoals lettertypen en CSS, te exporteren bij het opslaan van een Word-document als HTML met Aspose.Words voor .NET. Maak je klaar voor een leuke, informatieve rit!

## Vereisten

Voordat we in de code duiken, zorgen we ervoor dat je alles hebt wat je nodig hebt om te beginnen. Hier is een snelle checklist:

1.  Visual Studio: Zorg ervoor dat Visual Studio op uw machine is geïnstalleerd. U kunt het downloaden van de[Visual Studio-website](https://visualstudio.microsoft.com/).
2.  Aspose.Words voor .NET: U hebt de Aspose.Words voor .NET-bibliotheek nodig. Als u deze nog niet hebt, download dan een gratis proefversie van[Aspose-releases](https://releases.aspose.com/words/net/) of koop het bij de[Aspose-winkel](https://purchase.aspose.com/buy).
3. Basiskennis van C#: Een basiskennis van C# helpt u de codevoorbeelden te volgen.

Heb je dat allemaal? Geweldig! Laten we doorgaan met het importeren van de benodigde naamruimten.

## Naamruimten importeren

Om Aspose.Words voor .NET te gebruiken, moet u de relevante namespaces in uw project opnemen. Dit is hoe u dat doet:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Deze naamruimten zijn cruciaal voor toegang tot de Aspose.Words-klassen en -methoden die we in onze tutorial zullen gebruiken.

Laten we het proces van het exporteren van bronnen bij het opslaan van een Word-document als HTML eens uitsplitsen. We doen het stap voor stap, zodat het makkelijk te volgen is.

## Stap 1: Stel uw documentenmap in

Allereerst moet u het pad naar uw documentenmap opgeven. Dit is waar uw Word-document zich bevindt en waar het HTML-bestand wordt opgeslagen.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw directory.

## Stap 2: Laad het Word-document

 Laten we nu het Word-document laden dat u wilt converteren naar HTML. Voor deze tutorial gebruiken we een document met de naam`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Met deze regel code wordt het document geladen vanuit de opgegeven directory.

## Stap 3: Configureer HTML-opslagopties

Om bronnen zoals CSS en lettertypen te exporteren, moet u de volgende instellingen configureren:`HtmlSaveOptions`Deze stap is cruciaal om ervoor te zorgen dat uw HTML-uitvoer goed gestructureerd is en de benodigde bronnen bevat.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://voorbeeld.com/resources"
};
```

Laten we eens kijken wat elke optie doet:
- `CssStyleSheetType = CssStyleSheetType.External`: Met deze optie geeft u aan dat CSS-stijlen in een extern stijlblad moeten worden opgeslagen.
- `ExportFontResources = true`: Hiermee kunt u lettertypebronnen exporteren.
- `ResourceFolder = dataDir + "Resources"`: Geeft de lokale map op waar bronnen (zoals lettertypen en CSS-bestanden) worden opgeslagen.
- `ResourceFolderAlias = "http://example.com/resources"`: Stelt een alias in voor de resourcemap, die in het HTML-bestand wordt gebruikt.

## Stap 4: Sla het document op als HTML

Met de opslagopties geconfigureerd, is de laatste stap het opslaan van het document als een HTML-bestand. Dit is hoe u dat doet:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Deze regel code slaat het document op in HTML-formaat, samen met de geëxporteerde bronnen.

## Conclusie

En daar heb je het! Je hebt succesvol resources geëxporteerd terwijl je een Word-document opsloeg als HTML met Aspose.Words voor .NET. Met deze krachtige bibliotheek wordt het programmatisch verwerken van Word-documenten een fluitje van een cent. Of je nu werkt aan een webapplicatie of gewoon documenten wilt converteren voor offline gebruik, Aspose.Words heeft het allemaal.

## Veelgestelde vragen

### Kan ik afbeeldingen samen met lettertypen en CSS exporteren?
 Ja, dat kan! Aspose.Words voor .NET ondersteunt ook het exporteren van afbeeldingen. Zorg er wel voor dat u de`HtmlSaveOptions` overeenkomstig.

### Is er een manier om CSS in te sluiten in plaats van een extern stylesheet te gebruiken?
 Absoluut. Je kunt instellen`CssStyleSheetType` naar`CssStyleSheetType.Embedded` als u de voorkeur geeft aan ingebedde stijlen.

### Hoe kan ik de naam van het HTML-uitvoerbestand aanpassen?
 U kunt elke gewenste bestandsnaam opgeven in de`doc.Save` methode. Bijvoorbeeld,`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Ondersteunt Aspose.Words andere formaten dan HTML?
 Ja, het ondersteunt verschillende formaten, waaronder PDF, DOCX, TXT en meer. Bekijk de[documentatie](https://reference.aspose.com/words/net/) voor een volledige lijst.

### Waar kan ik meer ondersteuning en middelen krijgen?
Voor meer hulp, bezoek de[Aspose.Words Ondersteuningsforum](https://forum.aspose.com/c/words/8) . Gedetailleerde documentatie en voorbeelden vindt u ook op de[Aspose-website](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
