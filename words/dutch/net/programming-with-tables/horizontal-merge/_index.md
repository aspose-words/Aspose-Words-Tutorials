---
"description": "Leer hoe u cellen in een Word-document horizontaal kunt samenvoegen met Aspose.Words voor .NET met deze gedetailleerde, stapsgewijze zelfstudie."
"linktitle": "Horizontale samenvoeging"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Horizontale samenvoeging"
"url": "/nl/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Horizontale samenvoeging

## Invoering

Hallo! Klaar om de wereld van Aspose.Words voor .NET te betreden? Vandaag gaan we een superhandige functie aanpakken: horizontaal samenvoegen in tabellen. Dit klinkt misschien wat technisch, maar maak je geen zorgen, ik sta voor je klaar. Aan het einde van deze tutorial ben je een pro in het programmatisch samenvoegen van cellen in je Word-documenten. Dus, laten we de handen uit de mouwen steken en aan de slag gaan!

## Vereisten

Voordat we in de details duiken, zijn er een paar dingen die u moet regelen:

1. Aspose.Words voor .NET-bibliotheek: Als je dat nog niet hebt gedaan, download dan de Aspose.Words voor .NET-bibliotheek. Je kunt hem hier downloaden. [hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u een geschikte ontwikkelomgeving hebt ingesteld, zoals Visual Studio.
3. Basiskennis van C#: Een basiskennis van C#-programmering is nuttig.

Zodra je dit geregeld hebt, ben je klaar om te gaan!

## Naamruimten importeren

Voordat we de code induiken, controleren we of de benodigde naamruimten zijn geïmporteerd. Zorg ervoor dat je het volgende in je C#-project opneemt:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Oké, laten we het proces van het horizontaal samenvoegen van tabelcellen in een Word-document met behulp van Aspose.Words voor .NET eens nader bekijken.

## Stap 1: Uw document instellen

Het eerste wat we moeten doen, is een nieuw Word-document maken en het initialiseren. `DocumentBuilder`:

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Met dit codefragment wordt een nieuw document aangemaakt en wordt de `DocumentBuilder` voor actie.

## Stap 2: De eerste cel invoegen

Vervolgens beginnen we met het invoegen van de eerste cel en markeren we deze voor horizontale samenvoeging:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Hier voegen we een nieuwe cel in en stellen we deze in `HorizontalMerge` eigendom van `CellMerge.First`, wat aangeeft dat deze cel het begin is van een samengevoegde celreeks.

## Stap 3: De samengevoegde cel invoegen

Nu voegen we de cel in die met de vorige wordt samengevoegd:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

Deze cel wordt zo ingesteld dat deze wordt samengevoegd met de vorige cel door gebruik te maken van `CellMerge.Previous`Let op hoe we de rij eindigen met `builder.EndRow()`.

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

Hier voegen we twee cellen in zonder horizontale samenvoeging. Dit laat zien hoe cellen zich gedragen wanneer ze geen deel uitmaken van een samengevoegde reeks.

## Stap 5: De tafel afwerken

Ten slotte sluiten we de tabel af en slaan we het document op:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Met dit codefragment wordt de tabel voltooid en wordt het document in de opgegeven map opgeslagen.

## Conclusie

En voilà! Je hebt zojuist de kunst van het horizontaal samenvoegen van cellen in een Word-document onder de knie met Aspose.Words voor .NET. Door deze stappen te volgen, kun je eenvoudig complexe tabelstructuren maken. Blijf experimenteren en de mogelijkheden van Aspose.Words verkennen om je documenten zo dynamisch en flexibel te maken als je wilt. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, bewerken en manipuleren in .NET-toepassingen.

### Kan ik cellen verticaal samenvoegen met Aspose.Words voor .NET?
Ja, u kunt cellen ook verticaal samenvoegen met behulp van de `CellFormat.VerticalMerge` eigendom.

### Is Aspose.Words voor .NET gratis te gebruiken?
Aspose.Words voor .NET biedt een gratis proefperiode, maar voor volledige functionaliteit moet u een licentie aanschaffen. U kunt een tijdelijke licentie krijgen. [hier](https://purchase.aspose.com/temporary-license/).

### Hoe kan ik meer te weten komen over Aspose.Words voor .NET?
U kunt de gedetailleerde documentatie bekijken [hier](https://reference.aspose.com/words/net/).

### Waar kan ik ondersteuning krijgen voor Aspose.Words voor .NET?
Voor vragen of problemen kunt u terecht op het Aspose-ondersteuningsforum [hier](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}