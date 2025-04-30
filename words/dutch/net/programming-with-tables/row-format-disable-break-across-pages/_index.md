---
"description": "Leer hoe u rij-einden op pagina's in Word-documenten kunt uitschakelen met Aspose.Words voor .NET, zodat de leesbaarheid en opmaak van tabellen behouden blijven."
"linktitle": "Rijopmaak Uitschakelen Splitsen over pagina's"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Rijopmaak Uitschakelen Splitsen over pagina's"
"url": "/nl/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rijopmaak Uitschakelen Splitsen over pagina's

## Invoering

Wanneer u met tabellen in Word-documenten werkt, wilt u er mogelijk voor zorgen dat rijen niet over pagina's worden verdeeld. Dit kan essentieel zijn voor de leesbaarheid en opmaak van uw documenten. Aspose.Words voor .NET biedt een eenvoudige manier om rij-afbrekingen over pagina's uit te schakelen.

In deze tutorial laten we je zien hoe je rij-einden op pagina's in een Word-document kunt uitschakelen met behulp van Aspose.Words voor .NET.

## Vereisten

Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
- Aspose.Words voor .NET-bibliotheek geïnstalleerd.
- Een Word-document met een tabel die meerdere pagina's beslaat.

## Naamruimten importeren

Importeer eerst de benodigde naamruimten in uw project:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Stap 1: Het document laden

Laad het document met de tabel die meerdere pagina's beslaat.

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Stap 2: Toegang tot de tabel

Ga naar de eerste tabel in het document. Hierbij wordt ervan uitgegaan dat de tabel die u wilt wijzigen de eerste tabel in het document is.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Stap 3: Schakel het afbreken over pagina's voor alle rijen uit

Loop door elke rij in de tabel en stel de `AllowBreakAcrossPages` eigendom van `false`Zo voorkom je dat rijen over pagina's worden verdeeld.

```csharp
// Schakel het afbreken over pagina's uit voor alle rijen in de tabel.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Stap 4: Sla het document op

Sla het gewijzigde document op in de door u opgegeven directory.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Conclusie

In deze tutorial hebben we laten zien hoe je rij-einden over pagina's in een Word-document kunt uitschakelen met Aspose.Words voor .NET. Door de bovenstaande stappen te volgen, zorg je ervoor dat je tabelrijen intact blijven en niet over pagina's worden verdeeld, waardoor de leesbaarheid en opmaak van het document behouden blijven.

## Veelgestelde vragen

### Kan ik rij-einden op pagina's uitschakelen voor een specifieke rij in plaats van voor alle rijen?  
Ja, u kunt rij-einden voor specifieke rijen uitschakelen door de gewenste rij te openen en de bijbehorende instellingen in te stellen. `AllowBreakAcrossPages` eigendom van `false`.

### Werkt deze methode voor tabellen met samengevoegde cellen?  
Ja, deze methode werkt voor tabellen met samengevoegde cellen. De eigenschap `AllowBreakAcrossPages` geldt voor de gehele rij, ongeacht of cellen zijn samengevoegd.

### Werkt deze methode als de tabel in een andere tabel is genest?  
Ja, u kunt geneste tabellen op dezelfde manier openen en wijzigen. Zorg ervoor dat u correct naar de geneste tabel verwijst via de index of andere eigenschappen.

### Hoe kan ik controleren of een rij over pagina's mag worden verdeeld?  
U kunt controleren of een rij over pagina's kan worden verdeeld door de `AllowBreakAcrossPages` eigendom van de `RowFormat` en de waarde ervan controleren.

### Is er een manier om deze instelling toe te passen op alle tabellen in een document?  
Ja, u kunt door alle tabellen in het document heen lopen en deze instelling op elke tabel toepassen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}