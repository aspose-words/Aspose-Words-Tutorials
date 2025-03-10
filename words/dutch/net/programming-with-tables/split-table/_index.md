---
title: Gesplitste tabel
linktitle: Gesplitste tabel
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u tabellen in Word-documenten kunt splitsen met Aspose.Words voor .NET. Onze stapsgewijze handleiding maakt tabelbeheer eenvoudig en efficiënt.
weight: 10
url: /nl/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gesplitste tabel

## Invoering

Heb je ooit met een grote tabel in een Word-document gewerkt en wilde je deze graag opsplitsen in twee kleinere, beter beheersbare tabellen? Vandaag duiken we in hoe je dit precies kunt bereiken met Aspose.Words voor .NET. Of je nu werkt met uitgebreide datatabellen of complexe documentstructuren, het splitsen van tabellen kan de leesbaarheid en organisatie verbeteren. Laten we het stapsgewijze proces bekijken om een tabel te splitsen met Aspose.Words voor .NET.

## Vereisten

Voordat we met de tutorial beginnen, moet u ervoor zorgen dat u het volgende heeft:

1.  Aspose.Words voor .NET-bibliotheek: Zorg ervoor dat u de Aspose.Words voor .NET-bibliotheek hebt gedownload en geïnstalleerd. U kunt deze verkrijgen via de[Aspose releases pagina](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Stel een ontwikkelomgeving in met ondersteuning voor .NET Framework, zoals Visual Studio.
3. Voorbeeld document: Maak een Word document (`Tables.docx`) met ten minste één tabel om de splitsingsbewerking toe te passen.

## Naamruimten importeren

Importeer eerst de benodigde namespaces naar uw project. Hiermee krijgt u toegang tot de klassen en methoden die Aspose.Words biedt.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Stap 1: Laad het document

Laten we beginnen met het laden van het document met de tabel die u wilt splitsen. Zorg ervoor dat u het juiste pad naar uw document opgeeft.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Stap 2: Identificeer de tabel die u wilt splitsen

Identificeer en haal vervolgens de tabel op die u wilt splitsen. In dit voorbeeld richten we ons op de eerste tabel in het document.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Stap 3: Selecteer de rij waarop u wilt splitsen

Bepaal de rij waar u de tabel wilt splitsen. Hier splitsen we de tabel op de derde rij (inclusief).

```csharp
Row row = firstTable.Rows[2];
```

## Stap 4: Een nieuwe tabelcontainer maken

Maak een nieuwe tabelcontainer voor de rijen die uit de oorspronkelijke tabel worden verplaatst.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Stap 5: De nieuwe tabelcontainer invoegen

Plaats de nieuwe tabelcontainer direct na de oorspronkelijke tabel in het document.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Stap 6: Voeg een bufferparagraaf toe

Voeg een bufferalinea toe tussen de twee tabellen om ervoor te zorgen dat ze gescheiden blijven.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Stap 7: Rijen naar de nieuwe tabel verplaatsen

Verplaats de rijen van de originele tabel naar de nieuwe tabelcontainer. Deze lus gaat door totdat de opgegeven rij (inclusief) is verplaatst.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## Stap 8: Sla het document op

Sla ten slotte het gewijzigde document op met de gesplitste tabellen.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Conclusie

En daar heb je het! Door deze stappen te volgen, kun je eenvoudig een tabel in een Word-document splitsen met Aspose.Words voor .NET. Deze aanpak helpt je om grote tabellen effectiever te beheren, wat de leesbaarheid en organisatie van je documenten verbetert. Probeer het eens uit en zie hoe het je werk met tabellen in Word-documenten vereenvoudigt.

## Veelgestelde vragen

### Kan ik een tabel in meerdere rijen splitsen?
Ja, u kunt een tabel in meerdere rijen splitsen door het proces voor elk splitsingspunt te herhalen.

### Wat gebeurt er met de opmaak van de originele tabel?
De nieuwe tabel erft de opmaak van de originele tabel. Eventuele specifieke opmaakwijzigingen kunnen indien nodig op de nieuwe tabel worden toegepast.

### Is het mogelijk om tabellen weer samen te voegen?
Ja, u kunt tabellen samenvoegen door rijen van de ene tabel naar de andere te verplaatsen met behulp van vergelijkbare methoden.

### Werkt deze methode met geneste tabellen?
Ja, Aspose.Words voor .NET ondersteunt ook bewerkingen op geneste tabellen.

### Kan ik dit proces voor meerdere documenten automatiseren?
Absoluut! U kunt een script of applicatie maken om het tabelsplitsingsproces voor meerdere documenten te automatiseren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
