---
"description": "Leer hoe je een omtreklijn aan een tabel in Word toevoegt met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding voor perfecte tabelopmaak."
"linktitle": "Omtrekrand toepassen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Omtrekrand toepassen"
"url": "/nl/net/programming-with-table-styles-and-formatting/apply-outline-border/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Omtrekrand toepassen

## Invoering

In de tutorial van vandaag duiken we in de wereld van documentmanipulatie met Aspose.Words voor .NET. We leren specifiek hoe je een omtreklijn toepast op een tabel in een Word-document. Dit is een fantastische vaardigheid om in je gereedschapskist te hebben als je vaak met geautomatiseerde documentgeneratie en -opmaak werkt. Laten we dus aan de slag gaan om je tabellen niet alleen functioneel, maar ook visueel aantrekkelijk te maken.

## Vereisten

Voordat we in de code duiken, heb je een paar dingen nodig:

1. Aspose.Words voor .NET: Je moet Aspose.Words voor .NET geïnstalleerd hebben. Je kunt het downloaden. [hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een geschikte ontwikkelomgeving, zoals Visual Studio.
3. Basiskennis van C#: Een basiskennis van C# helpt u de tutorial te volgen.

## Naamruimten importeren

Zorg er allereerst voor dat u de benodigde naamruimten hebt geïmporteerd. Dit is cruciaal voor toegang tot de Aspose.Words-functionaliteiten.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Laten we het proces opdelen in eenvoudige, beheersbare stappen.

## Stap 1: Het document laden

Eerst moeten we het Word-document laden dat de tabel bevat die we willen opmaken.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

In deze stap gebruiken we de `Document` klasse van Aspose.Words om een bestaand document te laden. Vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad waar uw document is opgeslagen.

## Stap 2: Toegang tot de tabel

Vervolgens moeten we toegang krijgen tot de specifieke tabel die we willen opmaken. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

Hier, `GetChild` methode haalt de eerste tabel in het document op. De parameters `NodeType.Table, 0, true` ervoor zorgen dat we het juiste knooppunttype krijgen.

## Stap 3: De tabel uitlijnen

Laten we de tabel nu midden op de pagina uitlijnen.

```csharp
table.Alignment = TableAlignment.Center;
```

Met deze stap zorgt u ervoor dat de tafel netjes in het midden staat, waardoor deze er professioneel uitziet.

## Stap 4: Bestaande randen wissen

Voordat we nieuwe grenzen aanbrengen, moeten we de bestaande grenzen opruimen.

```csharp
table.ClearBorders();
```

Door de randen te verwijderen, zorgen we ervoor dat onze nieuwe randen netjes worden aangebracht, zonder dat de oude stijlen in de weg zitten.

## Stap 5: Randen instellen

Laten we nu de groene omtreklijnen op de tabel toepassen.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

Elk randtype (links, rechts, boven, onder) wordt individueel ingesteld. We gebruiken `LineStyle.Single` voor een doorgetrokken lijn, `1.5` voor de lijnbreedte, en `Color.Green` voor de randkleur.

## Stap 6: Celarcering toepassen

Om de tabel visueel aantrekkelijker te maken, vullen we de cellen met een lichtgroene kleur.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

Hier, `SetShading` wordt gebruikt om een effen lichtgroene kleur op de cellen toe te passen, waardoor de tabel beter opvalt.

## Stap 7: Sla het document op

Sla ten slotte het gewijzigde document op.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Met deze stap wordt uw document opgeslagen met de toegepaste opmaak. U kunt het openen en de prachtig opgemaakte tabel bekijken.

## Conclusie

En voilà! Door deze stappen te volgen, heb je met succes een omtreklijn toegepast op een tabel in een Word-document met Aspose.Words voor .NET. Deze tutorial behandelde het laden van het document, het openen van de tabel, het uitlijnen ervan, het wissen van bestaande randen, het toepassen van nieuwe randen, het toevoegen van celarcering en het opslaan van het document. 

Met deze vaardigheden kunt u de visuele presentatie van uw tabellen verbeteren, waardoor uw documenten professioneler en aantrekkelijker worden. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik verschillende stijlen toepassen op elke rand van de tabel?  
Ja, u kunt verschillende stijlen en kleuren op elke rand toepassen door de parameters in de `SetBorder` methode.

### Hoe kan ik de breedte van de rand wijzigen?  
U kunt de breedte wijzigen door de derde parameter in de `SetBorder` methode. Bijvoorbeeld, `1.5` stelt een breedte in van 1,5 punt.

### Is het mogelijk om schaduw toe te passen op individuele cellen?  
Ja, u kunt schaduw toepassen op individuele cellen door elke cel te openen en de `SetShading` methode.

### Kan ik andere kleuren gebruiken voor randen en schaduw?  
Absoluut! Je kunt elke beschikbare kleur gebruiken. `System.Drawing.Color` klas.

### Hoe kan ik de tabel horizontaal centreren?  
De `table.Alignment = TableAlignment.Center;` regel in de code centreert de tabel horizontaal op de pagina.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}