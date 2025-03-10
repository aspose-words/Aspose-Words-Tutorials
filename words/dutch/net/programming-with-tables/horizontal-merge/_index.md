---
title: Horizontale samenvoeging
linktitle: Horizontale samenvoeging
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u cellen in een Word-document horizontaal samenvoegt met Aspose.Words voor .NET met deze gedetailleerde, stapsgewijze zelfstudie.
weight: 10
url: /nl/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Horizontale samenvoeging

## Invoering

Hallo! Klaar om in de wereld van Aspose.Words voor .NET te duiken? Vandaag gaan we een superhandige functie aanpakken: horizontaal samenvoegen in tabellen. Dit klinkt misschien een beetje technisch, maar maak je geen zorgen, ik sta achter je. Aan het einde van deze tutorial ben je een pro in het programmatisch samenvoegen van cellen in je Word-documenten. Dus, laten we de mouwen opstropen en aan de slag gaan!

## Vereisten

Voordat we in de details duiken, zijn er een paar dingen die u moet regelen:

1. Aspose.Words voor .NET-bibliotheek: Als u dat nog niet hebt gedaan, download dan de Aspose.Words voor .NET-bibliotheek. U kunt het pakken[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u een geschikte ontwikkelomgeving hebt ingesteld, zoals Visual Studio.
3. Basiskennis van C#: Een basiskennis van C#-programmering is nuttig.

Zodra je dit geregeld hebt, ben je klaar om te gaan!

## Naamruimten importeren

Voordat we in de code duiken, moeten we ervoor zorgen dat we de benodigde namespaces hebben geïmporteerd. Zorg ervoor dat u in uw C#-project het volgende opneemt:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Oké, laten we het proces van het horizontaal samenvoegen van tabelcellen in een Word-document met behulp van Aspose.Words voor .NET eens nader bekijken.

## Stap 1: Uw document instellen

 Allereerst moeten we een nieuw Word-document maken en het initialiseren.`DocumentBuilder`:

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Met dit codefragment wordt een nieuw document opgezet en wordt de`DocumentBuilder` voor actie.

## Stap 2: De eerste cel invoegen

Vervolgens beginnen we met het invoegen van de eerste cel en markeren we deze voor horizontale samenvoeging:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Hier voegen we een nieuwe cel in en stellen deze in`HorizontalMerge`eigendom van`CellMerge.First`, wat aangeeft dat deze cel het begin is van een samengevoegde celsequentie.

## Stap 3: De samengevoegde cel invoegen

Nu voegen we de cel in die met de vorige wordt samengevoegd:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Deze cel is ingesteld om samen te voegen met de vorige cel door gebruik te maken van`CellMerge.Previous` . Let op hoe we de rij eindigen met`builder.EndRow()`.

## Stap 4: Niet-samengevoegde cellen invoegen

Om het verschil te illustreren, voegen we een aantal niet-samengevoegde cellen in:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Hier voegen we twee cellen in zonder horizontale samenvoeging. Dit laat zien hoe cellen zich gedragen als ze geen deel uitmaken van een samengevoegde sequentie.

## Stap 5: De tafel afwerken

Ten slotte sluiten we de tabel af en slaan het document op:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Met dit codefragment wordt de tabel voltooid en wordt het document opgeslagen in de opgegeven map.

## Conclusie

En daar heb je het! Je hebt zojuist de kunst van het horizontaal samenvoegen van cellen in een Word-document onder de knie gekregen met Aspose.Words voor .NET. Door deze stappen te volgen, kun je eenvoudig complexe tabelstructuren maken. Blijf experimenteren en ontdek de mogelijkheden van Aspose.Words om je documenten zo dynamisch en flexibel te maken als je nodig hebt. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars Word-documenten programmatisch kunnen maken, bewerken en manipuleren in .NET-toepassingen.

### Kan ik cellen verticaal samenvoegen met Aspose.Words voor .NET?
 Ja, u kunt cellen ook verticaal samenvoegen met behulp van de`CellFormat.VerticalMerge` eigendom.

### Is Aspose.Words voor .NET gratis te gebruiken?
 Aspose.Words voor .NET biedt een gratis proefversie, maar voor volledige functionaliteit moet u een licentie aanschaffen. U kunt een tijdelijke licentie krijgen[hier](https://purchase.aspose.com/temporary-license/).

### Hoe kan ik meer te weten komen over Aspose.Words voor .NET?
 U kunt de gedetailleerde documentatie bekijken[hier](https://reference.aspose.com/words/net/).

### Waar kan ik ondersteuning krijgen voor Aspose.Words voor .NET?
 Voor vragen of problemen kunt u terecht op het Aspose-ondersteuningsforum[hier](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
