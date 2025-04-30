---
"description": "Leer hoe u voet- en eindnootposities in Word-documenten instelt met Aspose.Words voor .NET met deze gedetailleerde stapsgewijze handleiding."
"linktitle": "Stel de positie van de voetnoot en eindnoot in"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Voetnoot- en eindnootpositie instellen"
"url": "/nl/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voetnoot- en eindnootpositie instellen

## Invoering

Als je met Word-documenten werkt en voetnoten en eindnoten effectief wilt beheren, is Aspose.Words voor .NET dé bibliotheek voor jou. Deze tutorial begeleidt je bij het instellen van voet- en eindnootposities in een Word-document met Aspose.Words voor .NET. We leggen elke stap uit, zodat je ze gemakkelijk kunt volgen en implementeren.

## Vereisten

Voordat u met de tutorial begint, moet u ervoor zorgen dat u het volgende hebt:

- Aspose.Words voor .NET-bibliotheek: U kunt het downloaden van [hier](https://releases.aspose.com/words/net/).
- Visual Studio: Elke recente versie werkt prima.
- Basiskennis van C#: Als u de basis begrijpt, kunt u de cursus gemakkelijk volgen.

## Naamruimten importeren

Importeer eerst de benodigde naamruimten in uw C#-project:

```csharp
using System;
using Aspose.Words;
```

## Stap 1: Laad het Word-document

Om te beginnen moet u uw Word-document laden in het Aspose.Words Document-object. Dit stelt u in staat om de inhoud van het document te bewerken.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Vervang in deze code `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad waar uw document zich bevindt.

## Stap 2: Stel de positie van de voetnoot in

Vervolgens stelt u de positie van de voetnoten in. Met Aspose.Words voor .NET kunt u voetnoten onder aan de pagina of onder de tekst plaatsen.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

Hier hebben we de voetnoten zo ingesteld dat ze onder de tekst verschijnen. Als u ze liever onderaan de pagina wilt hebben, kunt u dit doen. `FootnotePosition.BottomOfPage`.

## Stap 3: Eindnootpositie instellen

Op dezelfde manier kunt u de positie van eindnoten instellen. Eindnoten kunnen aan het einde van de sectie of aan het einde van het document worden geplaatst.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

In dit voorbeeld worden eindnoten aan het einde van elke sectie geplaatst. Om ze aan het einde van het document te plaatsen, gebruikt u `EndnotePosition.EndOfDocument`.

## Stap 4: Sla het document op

Sla ten slotte het document op om de wijzigingen toe te passen. Zorg ervoor dat u het juiste bestandspad en de juiste naam voor het uitvoerdocument opgeeft.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Met deze regel wordt het gewijzigde document opgeslagen in de door u opgegeven directory.

## Conclusie

Het instellen van voet- en eindnoten in Word-documenten met Aspose.Words voor .NET is eenvoudig zodra u de stappen kent. Door deze handleiding te volgen, kunt u uw documenten aanpassen aan uw wensen, zodat voet- en eindnoten precies op de gewenste plaats worden geplaatst.

## Veelgestelde vragen

### Kan ik verschillende posities instellen voor afzonderlijke voetnoten of eindnoten?

Nee, Aspose.Words voor .NET stelt de positie van alle voetnoten en eindnoten in een document uniform in.

### Is Aspose.Words voor .NET compatibel met alle versies van Word-documenten?

Ja, Aspose.Words voor .NET ondersteunt een breed scala aan Word-documentindelingen, waaronder DOC, DOCX, RTF en meer.

### Kan ik Aspose.Words voor .NET gebruiken met andere programmeertalen?

Aspose.Words voor .NET is ontworpen voor .NET-toepassingen, maar u kunt het gebruiken met iedere door .NET ondersteunde taal, zoals C#, VB.NET, enz.

### Is er een gratis proefversie beschikbaar voor Aspose.Words voor .NET?

Ja, u kunt een gratis proefperiode krijgen [hier](https://releases.aspose.com/).

### Waar kan ik meer gedetailleerde documentatie vinden voor Aspose.Words voor .NET?

Gedetailleerde documentatie is beschikbaar [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}