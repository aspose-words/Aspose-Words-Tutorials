---
title: Rijopmaak Schakel pagina-indeling uit
linktitle: Rijopmaak Schakel pagina-indeling uit
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u rij-einden op pagina's in Word-documenten kunt uitschakelen met Aspose.Words voor .NET, zodat de leesbaarheid en opmaak van tabellen behouden blijven.
weight: 10
url: /nl/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rijopmaak Schakel pagina-indeling uit

## Invoering

Wanneer u met tabellen in Word-documenten werkt, wilt u er wellicht voor zorgen dat rijen niet over pagina's worden verdeeld. Dit kan essentieel zijn voor het behoud van de leesbaarheid en opmaak van uw documenten. Aspose.Words voor .NET biedt een eenvoudige manier om rij-einden over pagina's uit te schakelen.

In deze tutorial laten we u zien hoe u rij-einden op pagina's in een Word-document kunt uitschakelen met behulp van Aspose.Words voor .NET.

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

## Stap 1: Laad het document

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

 Loop door elke rij in de tabel en stel de`AllowBreakAcrossPages`eigendom van`false`Hiermee wordt voorkomen dat rijen over pagina's worden verdeeld.

```csharp
// Schakel het opsplitsen over pagina's uit voor alle rijen in de tabel.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Stap 4: Sla het document op

Sla het gewijzigde document op in de door u opgegeven map.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Conclusie

In deze tutorial hebben we laten zien hoe u rij-einden over pagina's in een Word-document kunt uitschakelen met Aspose.Words voor .NET. Door de hierboven beschreven stappen te volgen, kunt u ervoor zorgen dat uw tabelrijen intact blijven en niet over pagina's worden gesplitst, waardoor de leesbaarheid en opmaak van het document behouden blijven.

## Veelgestelde vragen

### Kan ik rij-einden op pagina's uitschakelen voor een specifieke rij in plaats van voor alle rijen?  
 Ja, u kunt rij-einden voor specifieke rijen uitschakelen door de gewenste rij te openen en de rij-einden in te stellen.`AllowBreakAcrossPages`eigendom van`false`.

### Werkt deze methode voor tabellen met samengevoegde cellen?  
 Ja, deze methode werkt voor tabellen met samengevoegde cellen. De eigenschap`AllowBreakAcrossPages` geldt voor de hele rij, ongeacht of cellen zijn samengevoegd.

### Werkt deze methode als de tabel in een andere tabel is genest?  
Ja, u kunt geneste tabellen op dezelfde manier benaderen en wijzigen. Zorg ervoor dat u de geneste tabel correct verwijst via de index of andere eigenschappen.

### Hoe kan ik controleren of een rij over pagina's mag worden verdeeld?  
 U kunt controleren of een rij over pagina's kan worden verdeeld door de`AllowBreakAcrossPages` eigendom van de`RowFormat` en de waarde ervan controleren.

### Is er een manier om deze instelling op alle tabellen in een document toe te passen?  
Ja, u kunt door alle tabellen in het document heen lopen en deze instelling op elke tabel toepassen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
