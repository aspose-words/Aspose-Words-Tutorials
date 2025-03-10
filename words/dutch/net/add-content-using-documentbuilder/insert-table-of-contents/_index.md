---
title: Inhoudsopgave invoegen in Word-document
linktitle: Inhoudsopgave invoegen in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een inhoudsopgave in Word invoegt met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding voor naadloze documentnavigatie.
weight: 10
url: /nl/net/add-content-using-documentbuilder/insert-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inhoudsopgave invoegen in Word-document

## Invoering
In deze tutorial leert u hoe u efficiënt een inhoudsopgave (TOC) toevoegt aan uw Word-documenten met Aspose.Words voor .NET. Deze functie is essentieel voor het organiseren en navigeren van lange documenten, het verbeteren van de leesbaarheid en het bieden van een snel overzicht van documentsecties.

## Vereisten

Voordat u begint, moet u ervoor zorgen dat u over het volgende beschikt:

- Basiskennis van C# en .NET Framework.
- Visual Studio op uw computer geïnstalleerd.
-  Aspose.Words voor .NET-bibliotheek. Als u het nog niet hebt geïnstalleerd, kunt u het downloaden van[hier](https://releases.aspose.com/words/net/).

## Naamruimten importeren

Om te beginnen importeert u de benodigde naamruimten in uw C#-project:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Laten we het proces opsplitsen in duidelijke stappen:

## Stap 1: Initialiseer Aspose.Words Document en DocumentBuilder

 Initialiseer eerst een nieuwe Aspose.Words`Document` object en een`DocumentBuilder` om mee te werken:

```csharp
// Initialiseer Document en DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Voeg de inhoudsopgave in

 Voeg nu de inhoudsopgave in met behulp van de`InsertTableOfContents` methode:

```csharp
// Inhoudsopgave invoegen
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## Stap 3: Start de documentinhoud op een nieuwe pagina

Om een correcte opmaak te garanderen, begint u de daadwerkelijke documentinhoud op een nieuwe pagina:

```csharp
// Een pagina-einde invoegen
builder.InsertBreak(BreakType.PageBreak);
```

## Stap 4: Structureer uw document met koppen

Organiseer de inhoud van uw document met behulp van de juiste koptekststijlen:

```csharp
// Koptekststijlen instellen
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## Stap 5: De inhoudsopgave bijwerken en invullen

Werk de inhoudsopgave bij zodat deze de documentstructuur weergeeft:

```csharp
// De velden van de inhoudsopgave bijwerken
doc.UpdateFields();
```

## Stap 6: Sla het document op

Sla ten slotte uw document op in de opgegeven map:

```csharp
// Sla het document op
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Conclusie

Het toevoegen van een inhoudsopgave met Aspose.Words voor .NET is eenvoudig en verbetert de bruikbaarheid van uw documenten aanzienlijk. Door deze stappen te volgen, kunt u complexe documenten efficiënt organiseren en erdoorheen navigeren.

## Veelgestelde vragen

### Kan ik het uiterlijk van de inhoudsopgave aanpassen?
Ja, u kunt het uiterlijk en gedrag van de inhoudsopgave aanpassen met Aspose.Words voor .NET API's.

### Ondersteunt Aspose.Words het automatisch bijwerken van velden?
Ja, met Aspose.Words kunt u velden zoals de inhoudsopgave dynamisch bijwerken op basis van wijzigingen in het document.

### Kan ik meerdere inhoudsopgaven in één document genereren?
Met Aspose.Words kunt u meerdere inhoudsopgaven met verschillende instellingen binnen één document genereren.

### Is Aspose.Words compatibel met verschillende versies van Microsoft Word?
Ja, Aspose.Words garandeert compatibiliteit met verschillende versies van Microsoft Word-formaten.

### Waar kan ik meer hulp en ondersteuning vinden voor Aspose.Words?
 Voor meer hulp, bezoek de[Aspose.Woorden Forum](https://forum.aspose.com/c/words/8) of bekijk de[officiële documentatie](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
