---
title: Omtrekrand toepassen
linktitle: Omtrekrand toepassen
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een omtrekrand toepast op een tabel in Word met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding voor perfecte tabelopmaak.
weight: 10
url: /nl/net/programming-with-table-styles-and-formatting/apply-outline-border/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Omtrekrand toepassen

## Invoering

In de tutorial van vandaag duiken we in de wereld van documentmanipulatie met Aspose.Words voor .NET. We gaan specifiek leren hoe we een omtrekrand op een tabel in een Word-document kunnen toepassen. Dit is een fantastische vaardigheid om in je gereedschapskist te hebben als je vaak met geautomatiseerde documentgeneratie en -opmaak werkt. Laten we dus beginnen aan deze reis om je tabellen niet alleen functioneel, maar ook visueel aantrekkelijk te maken.

## Vereisten

Voordat we met de code beginnen, heb je een paar dingen nodig:

1.  Aspose.Words voor .NET: U moet Aspose.Words voor .NET geïnstalleerd hebben. U kunt het downloaden[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een geschikte ontwikkelomgeving zoals Visual Studio.
3. Basiskennis van C#: Een basiskennis van C# helpt u de tutorial te volgen.

## Naamruimten importeren

Zorg er allereerst voor dat u de benodigde namespaces hebt geïmporteerd. Dit is cruciaal voor toegang tot Aspose.Words-functionaliteiten.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Laten we het proces opsplitsen in eenvoudige, beheersbare stappen.

## Stap 1: Laad het document

Eerst moeten we het Word-document laden dat de tabel bevat die we willen opmaken.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

 In deze stap gebruiken we de`Document` klasse van Aspose.Words om een bestaand document te laden. Vervangen`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad waar uw document is opgeslagen.

## Stap 2: Toegang tot de tabel

Vervolgens moeten we toegang krijgen tot de specifieke tabel die we willen opmaken. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

 Hier,`GetChild` methode haalt de eerste tabel in het document op. De parameters`NodeType.Table, 0, true` ervoor zorgen dat we het juiste knooppunttype krijgen.

## Stap 3: De tabel uitlijnen

Laten we de tabel nu centreren op de pagina.

```csharp
table.Alignment = TableAlignment.Center;
```

Met deze stap zorgt u ervoor dat de tafel netjes in het midden staat, waardoor deze er professioneel uitziet.

## Stap 4: Bestaande grenzen wissen

Voordat we nieuwe grenzen aanbrengen, moeten we de bestaande grenzen opruimen.

```csharp
table.ClearBorders();
```

Door de randen te verwijderen, zorgen we ervoor dat onze nieuwe randen netjes worden aangebracht, zonder dat oude stijlen in de weg zitten.

## Stap 5: Stel de omtrekranden in

Laten we nu de groene omtreklijnen op de tabel toepassen.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

 Elk randtype (links, rechts, boven, onder) wordt individueel ingesteld. Wij gebruiken`LineStyle.Single` voor een doorgetrokken lijn,`1.5` voor de lijnbreedte, en`Color.Green` voor de randkleur.

## Stap 6: Celschaduw toepassen

Om de tabel visueel aantrekkelijker te maken, vullen we de cellen met een lichtgroene kleur.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

 Hier,`SetShading` wordt gebruikt om een effen lichtgroene kleur op de cellen toe te passen, waardoor de tabel opvalt.

## Stap 7: Sla het document op

Sla ten slotte het gewijzigde document op.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Deze stap slaat uw document op met de toegepaste opmaak. U kunt het openen om de prachtig opgemaakte tabel te bekijken.

## Conclusie

En daar heb je het! Door deze stappen te volgen, heb je met succes een omtrekrand toegepast op een tabel in een Word-document met Aspose.Words voor .NET. Deze tutorial behandelde het laden van het document, het openen van de tabel, het uitlijnen ervan, het wissen van bestaande randen, het toepassen van nieuwe randen, het toevoegen van celarcering en tot slot het opslaan van het document. 

Met deze vaardigheden kunt u de visuele presentatie van uw tabellen verbeteren, waardoor uw documenten professioneler en aantrekkelijker worden. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik verschillende stijlen toepassen op elke rand van de tabel?  
 Ja, u kunt verschillende stijlen en kleuren op elke rand toepassen door de parameters in de`SetBorder` methode.

### Hoe kan ik de breedte van de rand wijzigen?  
 U kunt de breedte wijzigen door de derde parameter in de`SetBorder` methode. Bijvoorbeeld,`1.5` stelt een breedte in van 1,5 punt.

### Is het mogelijk om schaduw toe te passen op individuele cellen?  
 Ja, u kunt schaduw toepassen op individuele cellen door elke cel te openen en de`SetShading` methode.

### Kan ik andere kleuren gebruiken voor randen en schaduwen?  
 Absoluut! Je kunt elke kleur gebruiken die beschikbaar is in de`System.Drawing.Color` klas.

### Hoe kan ik de tabel horizontaal centreren?  
 De`table.Alignment = TableAlignment.Center;` regel in de code centreert de tabel horizontaal op de pagina.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
