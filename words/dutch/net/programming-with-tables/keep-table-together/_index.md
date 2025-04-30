---
"description": "Leer hoe u kunt voorkomen dat tabellen over pagina's in Word-documenten worden verdeeld met Aspose.Words voor .NET. Volg onze handleiding om professionele, leesbare documenten te onderhouden."
"linktitle": "Houd de tafel bij elkaar"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Houd de tafel bij elkaar"
"url": "/nl/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Houd de tafel bij elkaar

## Invoering

Raak je ooit gefrustreerd wanneer een tabel in je Word-document over twee pagina's wordt verdeeld? Het is alsof je zorgvuldig opgemaakte informatie halverwege plotseling een pauze neemt! Tabellen bij elkaar op één pagina houden is cruciaal voor de leesbaarheid en presentatie. Of het nu gaat om een rapport, een projectvoorstel of gewoon een persoonlijk document, het splitsen van tabellen kan behoorlijk verwarrend zijn. Gelukkig voor ons heeft Aspose.Words voor .NET een handige manier om dit probleem op te lossen. In deze tutorial laten we je zien hoe je je tabellen intact en strak houdt. Laten we beginnen!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1. Aspose.Words voor .NET - Als u het nog niet hebt geïnstalleerd, kunt u het hier downloaden [hier](https://releases.aspose.com/words/net/).
2. Een Word-document met een tabel: we werken met een voorbeelddocument met een tabel die zich over meerdere pagina's uitstrekt.
3. Basiskennis van C# - In deze tutorial wordt ervan uitgegaan dat u een basiskennis van C#-programmering hebt.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Dit geeft ons toegang tot de klassen en methoden die we nodig hebben van Aspose.Words voor .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Laten we het proces opsplitsen in eenvoudige, begrijpelijke stappen. We beginnen met het laden van ons document en eindigen met het opslaan van het bijgewerkte document, waarbij de tabel intact blijft.

## Stap 1: Het document laden

Om met een Word-document te kunnen werken, moeten we het eerst laden. We gebruiken de `Document` klas hiervoor.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Stap 2: Toegang tot de tabel

Vervolgens moeten we de tabel selecteren die we bij elkaar willen houden. We gaan ervan uit dat dit de eerste tabel in het document is.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Stap 3: KeepWithNext instellen voor alinea's

Om te voorkomen dat de tabel over pagina's heen wordt verdeeld, moeten we de `KeepWithNext` eigenschap voor elke alinea in de tabel, met uitzondering van de laatste alinea's in de laatste rij.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Stap 4: Sla het document op

Ten slotte slaan we het bijgewerkte document op. Dit past onze wijzigingen toe en zorgt ervoor dat de tabel op één pagina blijft staan.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusie

En voilà! Met slechts een paar regels code voorkom je dat je tabellen in je Word-documenten over meerdere pagina's worden verdeeld. Deze eenvoudige maar effectieve oplossing zorgt ervoor dat je tabellen er netjes en professioneel uitzien, wat de leesbaarheid van je documenten verbetert. Aspose.Words voor .NET maakt het oplossen van dergelijke opmaakproblemen een fluitje van een cent, zodat jij je kunt concentreren op het creëren van geweldige content.

## Veelgestelde vragen

### Kan ik met deze methode meerdere tabellen bij elkaar houden?  
Ja, u kunt dezelfde logica toepassen op meerdere tabellen door door elke tabel in uw document te itereren.

### Wat als mijn tabel te groot is voor één pagina?  
Als een tabel te groot is voor één pagina, wordt deze nog steeds over meerdere pagina's verdeeld. Deze methode zorgt ervoor dat kleinere tabellen intact blijven zonder te splitsen.

### Is er een manier om dit te automatiseren voor alle tabellen in een document?  
Ja, u kunt door alle tabellen in uw document heen lussen en de `KeepWithNext` eigenschap aan elke alinea toe.

### Heb ik een betaalde licentie nodig voor Aspose.Words voor .NET?  
U kunt beginnen met een gratis proefperiode vanaf [hier](https://releases.aspose.com/), maar voor volledige functionaliteit wordt een betaalde licentie aanbevolen.

### Kan ik een andere opmaak op de tabel toepassen zonder de tabel te wijzigen?  
Absoluut! Je kunt je tabel naar wens opmaken en er tegelijkertijd voor zorgen dat deze op één pagina blijft staan.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}