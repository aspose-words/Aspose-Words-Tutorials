---
"description": "Leer hoe u tabellen rechtstreeks in Word-documenten kunt invoegen met Aspose.Words voor .NET. Volg onze gedetailleerde, stapsgewijze handleiding om uw documentcreatie te stroomlijnen."
"linktitle": "Tabel direct invoegen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Tabel direct invoegen"
"url": "/nl/net/programming-with-tables/insert-table-directly/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tabel direct invoegen

## Invoering
Het programmatisch aanmaken van tabellen kan een hele uitdaging zijn, vooral als het gaat om complexe documentstructuren. Maar maak je geen zorgen, wij leggen het je graag uit! In deze handleiding leggen we je uit hoe je een tabel rechtstreeks in een Word-document kunt invoegen met Aspose.Words voor .NET. Of je nu een ervaren ontwikkelaar bent of net begint, deze tutorial helpt je het proces moeiteloos onder de knie te krijgen.

## Vereisten

Voordat we de code induiken, controleren we of je alles hebt wat je nodig hebt om aan de slag te gaan. Hier is een korte checklist:

1. Aspose.Words voor .NET-bibliotheek: Zorg ervoor dat je de Aspose.Words voor .NET-bibliotheek hebt gedownload en geïnstalleerd. Je kunt deze vinden op de [downloadpagina](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een ontwikkelomgeving zoals Visual Studio.
3. Basiskennis van C#: inzicht in de basisprincipes van C#-programmering.
4. Documentmap: een map waarin u uw documenten opslaat.

Als u aan deze vereisten voldoet, kunt u beginnen met coderen!

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Deze naamruimten voorzien ons van de klassen en methoden die nodig zijn om met Word-documenten te werken.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Nu we de naamruimten hebben ingesteld, kunnen we verder met het leukste gedeelte: tabellen maken en rechtstreeks in een Word-document invoegen.

## Stap 1: Het document instellen

Laten we beginnen met het aanmaken van een nieuw Word-document. Hier wordt onze tabel ingevoegd.

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Deze code initialiseert een nieuw Word-document. U moet het vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw documentenmap.

## Stap 2: Het tabelobject maken

Vervolgens maken we het tabelobject aan. Hier definiëren we de structuur van onze tabel.

```csharp
// We beginnen met het aanmaken van het tabelobject. Let op: we moeten het documentobject doorgeven.
// aan de constructor van elk knooppunt. Dit komt omdat elk knooppunt dat we creëren, moet behoren tot
// naar een document.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

Hier maken we een nieuwe tabel en voegen deze toe aan de hoofdtekst van het eerste gedeelte van ons document.

## Stap 3: Rijen en cellen toevoegen

Een tabel bestaat uit rijen en cellen. Laten we deze elementen stap voor stap toevoegen.

### Een rij toevoegen

```csharp
// Hier zouden we EnsureMinimum kunnen aanroepen om de rijen en cellen voor ons aan te maken. Deze methode wordt gebruikt
// Om ervoor te zorgen dat het opgegeven knooppunt geldig is. In dit geval moet een geldige tabel minstens één rij en één cel bevatten.
// In plaats daarvan zullen wij zelf de rij en de tabel aanmaken.
// Dit zou de beste manier zijn om dit te doen als we een tabel binnen een algoritme zouden maken.
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

Deze code maakt een nieuwe rij aan en voegt deze toe aan onze tabel.

### Cellen toevoegen aan de rij

Laten we nu een aantal cellen aan onze rij toevoegen. 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

In dit fragment maken we een cel aan, stellen we de achtergrondkleur in op lichtblauw en definiëren we de breedte. Vervolgens voegen we een alinea en een run toe aan de cel om onze tekst te plaatsen.

## Stap 4: Cellen klonen

Om het proces van het toevoegen van cellen te versnellen, kunnen we bestaande cellen klonen.

```csharp
// Vervolgens herhalen we het proces voor de andere cellen en rijen in de tabel.
// We kunnen het proces ook versnellen door bestaande cellen en rijen te klonen.
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

Deze code kloont de bestaande cel en voegt deze toe aan de rij. Vervolgens voegen we een alinea en een run toe aan de nieuwe cel.

## Stap 5: Instellingen voor automatisch aanpassen toepassen

Ten slotte passen we de instellingen voor automatisch aanpassen toe op onze tabel, zodat de kolommen een vaste breedte hebben.

```csharp
// We kunnen nu alle instellingen voor automatisch aanpassen toepassen.
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## Stap 6: Het document opslaan

Nu de tabel helemaal is ingesteld, is het tijd om het document op te slaan.

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

Deze code slaat het document op met de ingevoegde tabel.

## Conclusie

Gefeliciteerd! Je hebt met succes een tabel rechtstreeks in een Word-document ingevoegd met Aspose.Words voor .NET. Dit proces kan worden gebruikt om complexe tabellen programmatisch te maken, waardoor je documentautomatisering veel eenvoudiger wordt. Of je nu rapporten, facturen of andere documenttypen genereert, het is cruciaal om te weten hoe je tabellen moet bewerken.

## Veelgestelde vragen

### Hoe kan ik Aspose.Words voor .NET downloaden?
U kunt Aspose.Words voor .NET downloaden van de [downloadpagina](https://releases.aspose.com/words/net/).

### Kan ik Aspose.Words voor .NET uitproberen voordat ik het koop?
Ja, u kunt een aanvraag indienen [gratis proefperiode](https://releases.aspose.com/) om de bibliotheek te evalueren alvorens tot aankoop over te gaan.

### Hoe kan ik Aspose.Words voor .NET kopen?
U kunt Aspose.Words voor .NET kopen bij de [aankooppagina](https://purchase.aspose.com/buy).

### Waar kan ik de documentatie voor Aspose.Words voor .NET vinden?
De documentatie is beschikbaar [hier](https://reference.aspose.com/words/net/).

### Wat als ik ondersteuning nodig heb bij het gebruik van Aspose.Words voor .NET?
Voor ondersteuning kunt u terecht op de [Aspose.Words forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}