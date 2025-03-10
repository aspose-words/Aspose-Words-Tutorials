---
title: Tabel en cel opmaken met verschillende randen
linktitle: Tabel en cel opmaken met verschillende randen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u tabellen en cellen met verschillende randen kunt opmaken met Aspose.Words voor .NET. Verbeter uw Word-documenten met aangepaste tabelstijlen en celarcering.
weight: 10
url: /nl/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabel en cel opmaken met verschillende randen

## Invoering

Heb je ooit geprobeerd om je Word-documenten er professioneler uit te laten zien door de randen van tabellen en cellen aan te passen? Zo niet, dan staat je een traktatie te wachten! Deze tutorial leidt je door het proces van het opmaken van tabellen en cellen met verschillende randen met behulp van Aspose.Words voor .NET. Stel je voor dat je de macht hebt om het uiterlijk van je tabellen te veranderen met slechts een paar regels code. Geïntrigeerd? Laten we erin duiken en ontdekken hoe je dit eenvoudig kunt bereiken.

## Vereisten

Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende voorwaarden voldoet:
- Basiskennis van C#-programmering.
- Visual Studio op uw computer geïnstalleerd.
-  Aspose.Words voor .NET-bibliotheek. Als u het nog niet hebt geïnstalleerd, kunt u het downloaden[hier](https://releases.aspose.com/words/net/).
-  Een geldige Aspose-licentie. U kunt een gratis proefversie of een tijdelijke licentie krijgen van[hier](https://purchase.aspose.com/temporary-license/).

## Naamruimten importeren

Om met Aspose.Words voor .NET te werken, moet u de benodigde naamruimten importeren in uw project. Voeg het volgende toe met behulp van richtlijnen boven aan uw codebestand:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Stap 1: Initialiseer Document en DocumentBuilder

Eerst moet u een nieuw document maken en de DocumentBuilder initialiseren, die helpt bij het opbouwen van de documentinhoud. 

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Begin met het maken van een tabel

Gebruik vervolgens de DocumentBuilder om een tabel te maken en voeg de eerste cel in.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## Stap 3: Tabelranden instellen

Stel de randen in voor de gehele tabel. Deze stap zorgt ervoor dat alle cellen in de tabel een consistente randstijl hebben, tenzij anders gespecificeerd.

```csharp
// Stel de randen voor de hele tabel in.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Stap 4: Celschaduw toepassen

Pas schaduw toe op de cellen om ze visueel te onderscheiden. In dit voorbeeld stellen we de achtergrondkleur van de eerste cel in op rood.


```csharp
// Stel de celarcering voor deze cel in.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Stap 5: Voeg een andere cel in met een andere arcering

Voeg de tweede cel in en pas een andere schaduwkleur toe. Dit maakt de tabel kleurrijker en gemakkelijker te lezen.

```csharp
builder.InsertCell();
// Geef een andere celarcering op voor de tweede cel.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Stap 6: Celopmaak wissen

Wis de celopmaak van eerdere bewerkingen om ervoor te zorgen dat de volgende cellen niet dezelfde stijlen overnemen.


```csharp
// Wis de celopmaak van eerdere bewerkingen.
builder.CellFormat.ClearFormatting();
```

## Stap 7: Randen voor specifieke cellen aanpassen

Pas de randen voor specifieke cellen aan om ze te laten opvallen. Hier stellen we grotere randen in voor de eerste cel van de nieuwe rij.

```csharp
builder.InsertCell();
// Maak grotere randen voor de eerste cel van deze rij. Dit zal anders zijn
// vergeleken met de randen die voor de tabel zijn ingesteld.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Stap 8: Laatste cel invoegen

Voeg de laatste cel in en zorg ervoor dat de opmaak is gewist, zodat de standaardopmaakprofielen van de tabel worden gebruikt.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## Stap 9: Sla het document op

Sla het document ten slotte op in de opgegeven map.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Conclusie

En daar heb je het! Je hebt net geleerd hoe je tabellen en cellen met verschillende randen kunt opmaken met Aspose.Words voor .NET. Door tabelranden en celschaduw aan te passen, kun je de visuele aantrekkingskracht van je documenten aanzienlijk verbeteren. Dus ga je gang, experimenteer met verschillende stijlen en laat je documenten opvallen!

## Veelgestelde vragen

### Kan ik voor elke cel een andere randstijl gebruiken?
 Ja, u kunt voor elke cel verschillende randstijlen instellen met behulp van de`CellFormat.Borders` eigendom.

### Hoe kan ik alle randen van een tabel verwijderen?
 U kunt alle randen verwijderen door de randstijl in te stellen op`LineStyle.None`.

### Is het mogelijk om voor elke cel een andere randkleur in te stellen?
 Absoluut! U kunt de randkleur voor elke cel aanpassen met behulp van de`CellFormat.Borders.Color` eigendom.

### Kan ik afbeeldingen gebruiken als celachtergrond?
Hoewel Aspose.Words geen directe ondersteuning biedt voor afbeeldingen als celachtergrond, kunt u wel een afbeelding in een cel invoegen en de grootte ervan aanpassen, zodat deze het hele celoppervlak beslaat.

### Hoe voeg ik cellen in een tabel samen?
 U kunt cellen samenvoegen met behulp van de`CellFormat.HorizontalMerge` En`CellFormat.VerticalMerge` eigenschappen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
