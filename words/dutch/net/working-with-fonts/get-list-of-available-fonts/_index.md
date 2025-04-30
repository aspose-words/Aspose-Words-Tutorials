---
"description": "Ontdek hoe je een lijst met beschikbare lettertypen kunt verkrijgen met Aspose.Words voor .NET in deze gedetailleerde stapsgewijze tutorial. Verbeter je vaardigheden in lettertypebeheer."
"linktitle": "Lijst met beschikbare lettertypen ophalen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Lijst met beschikbare lettertypen ophalen"
"url": "/nl/net/working-with-fonts/get-list-of-available-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lijst met beschikbare lettertypen ophalen

## Invoering

Heb je ooit moeite gehad met het beheren van lettertypen in je Word-documenten? Ben je een .NET-ontwikkelaar? Dan is Aspose.Words voor .NET er om je te redden! Deze krachtige bibliotheek helpt je niet alleen bij het programmatisch maken en bewerken van Word-documenten, maar biedt ook uitgebreide mogelijkheden voor lettertypebeheer. In deze handleiding leggen we je stap voor stap uit hoe je een lijst met beschikbare lettertypen kunt verkrijgen met Aspose.Words voor .NET. We leggen het uit in begrijpelijke stappen, zodat je het gemakkelijk kunt volgen. Laten we aan de slag gaan en lettertypebeheer een fluitje van een cent maken!

## Vereisten

Voordat we beginnen, heb je een paar dingen nodig:

- Aspose.Words voor .NET: Zorg ervoor dat je de Aspose.Words voor .NET-bibliotheek hebt geïnstalleerd. Je kunt deze downloaden van [hier](https://releases.aspose.com/words/net/).
- Visual Studio: in dit voorbeeld wordt Visual Studio als ontwikkelomgeving gebruikt.
- .NET Framework: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd.
- Documentmap: een map waarin uw documenten zijn opgeslagen.

## Naamruimten importeren

Importeer eerst de benodigde naamruimten in uw project:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Stap 1: Initialiseer lettertype-instellingen

De eerste stap is het initialiseren van de lettertype-instellingen. Hiermee kunt u de lettertypebronnen voor uw documenten beheren.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Deze klasse wordt gebruikt om de instellingen voor lettertypevervanging en lettertypebronnen op te geven.
- fontSources: We maken een lijst met bestaande lettertypebronnen op basis van de huidige lettertype-instellingen.

## Stap 2: Documentdirectory definiëren

Geef vervolgens het pad naar uw documentmap op. Hier zoekt Aspose.Words naar lettertypen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: Deze tekenreeksvariabele bevat het pad naar de map waar uw lettertypen zich bevinden. Vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad.

## Stap 3: Aangepaste lettertypemap toevoegen

Voeg nu een nieuwe bronmap toe om Aspose.Words de opdracht te geven om in deze map naar lettertypen te zoeken.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Deze klasse vertegenwoordigt een lettertypebron voor een map. De tweede parameter (`true`geeft aan of er recursief naar lettertypen in submappen moet worden gezocht.

## Stap 4: Lettertypebronnen bijwerken

Voeg de map met aangepaste lettertypen toe aan de lijst met bestaande lettertypebronnen en werk de lettertype-instellingen bij.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Voegt de aangepaste lettertypemap toe aan de bestaande lettertypebronnen.
- updatedFontSources: converteert de lijst met lettertypebronnen naar een array.

## Stap 5: Lettertypen ophalen en weergeven

Haal ten slotte de beschikbare lettertypen op en geef de details ervan weer.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Haalt de lijst met beschikbare lettertypen op uit de eerste lettertypebron in de bijgewerkte lijst.
- fontInfo: Een exemplaar van `PhysicalFontInfo` met details over elk lettertype.

## Conclusie

Gefeliciteerd! Je hebt met succes een lijst met beschikbare lettertypen opgehaald met Aspose.Words voor .NET. Deze tutorial heeft je door elke stap geleid, van het initialiseren van lettertype-instellingen tot het weergeven van lettertypedetails. Met deze kennis kun je nu eenvoudig lettertypen in je Word-documenten beheren. Vergeet niet dat Aspose.Words voor .NET een krachtige tool is die je documentverwerking aanzienlijk kan verbeteren. Ga dus aan de slag en ontdek meer functies om je ontwikkelingsproces nog efficiënter te maken.

## Veelgestelde vragen

### Kan ik Aspose.Words voor .NET gebruiken met andere .NET-frameworks?
Ja, Aspose.Words voor .NET is compatibel met diverse .NET-frameworks, waaronder .NET Core en .NET 5+.

### Hoe installeer ik Aspose.Words voor .NET?
U kunt het installeren via NuGet Package Manager in Visual Studio door te zoeken naar "Aspose.Words".

### Is het mogelijk om meerdere aangepaste lettertypemappen toe te voegen?
Ja, u kunt meerdere aangepaste lettertypemappen toevoegen door meerdere mappen te maken. `FolderFontSource` instanties en deze aan de lijst met lettertypebronnen toevoegen.

### Kan ik lettertypegegevens uit een specifieke lettertypebron ophalen?
Ja, u kunt lettertypegegevens ophalen uit elke lettertypebron door de index van de lettertypebron op te geven in de `updatedFontSources` reeks.

### Ondersteunt Aspose.Words voor .NET lettertypevervanging?
Ja, het ondersteunt lettertypevervanging. Zo weet u zeker dat tekst correct wordt weergegeven, ook als het oorspronkelijke lettertype niet beschikbaar is.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}