---
"description": "Leer hoe u relatieve horizontale en verticale posities voor tabellen in Word-documenten instelt met Aspose.Words voor .NET met behulp van deze stapsgewijze handleiding."
"linktitle": "Relatieve horizontale of verticale positie instellen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Relatieve horizontale of verticale positie instellen"
"url": "/nl/net/programming-with-tables/set-relative-horizontal-or-vertical-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Relatieve horizontale of verticale positie instellen

## Invoering

Heb je ooit moeite gehad met het positioneren van tabellen in je Word-documenten zoals jij dat wilt? Nou, je bent niet de enige. Of je nu een professioneel rapport of een stijlvolle brochure maakt, het uitlijnen van tabellen kan een wereld van verschil maken. Daar komt Aspose.Words voor .NET goed van pas. Deze tutorial begeleidt je stap voor stap bij het instellen van relatieve horizontale of verticale posities voor tabellen in je Word-documenten. Laten we beginnen!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1. Aspose.Words voor .NET: Als u het nog niet heeft gedaan, kunt u het downloaden [hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere .NET-compatibele IDE.
3. Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u bekend bent met de basisbeginselen van C#-programmering.

## Naamruimten importeren

Allereerst moet u de benodigde naamruimten importeren. Dit is essentieel voor toegang tot de Aspose.Words-functionaliteit.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Stap 1: Laad uw document

Om te beginnen moet je je Word-document in het programma laden. Zo doe je dat:

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Met dit codefragment wordt het pad naar uw documentmap ingesteld en wordt het specifieke document geladen waaraan u wilt werken. Zorg ervoor dat het documentpad correct is om problemen met laden te voorkomen.

## Stap 2: Toegang tot de tabel

Vervolgens moeten we de tabel in het document benaderen. Normaal gesproken werkt u met de eerste tabel in de body-sectie.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Deze regel code haalt de eerste tabel op uit de hoofdtekst van het document. Als uw document meerdere tabellen bevat, kunt u de index dienovereenkomstig aanpassen.

## Stap 3: Horizontale positie instellen

Laten we nu de horizontale positie van de tabel ten opzichte van een specifiek element instellen. In dit voorbeeld positioneren we de tabel ten opzichte van de kolom.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

Door het instellen van de `HorizontalAnchor` naar `RelativeHorizontalPosition.Column`, dan vertelt u de tabel dat deze zich horizontaal moet uitlijnen ten opzichte van de kolom waarin deze zich bevindt.

## Stap 4: Verticale positie instellen

Net als bij horizontale positionering kun je ook de verticale positie instellen. Hierbij positioneren we de pagina relatief ten opzichte van de pagina.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

Het instellen van de `VerticalAnchor` naar `RelativeVerticalPosition.Page` zorgt ervoor dat de tabel verticaal uitgelijnd is ten opzichte van de pagina.

## Stap 5: Sla uw document op

Sla ten slotte je wijzigingen op in een nieuw document. Dit is een cruciale stap om ervoor te zorgen dat je wijzigingen behouden blijven.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Met deze opdracht slaat u het gewijzigde document op onder een nieuwe naam. Zo voorkomt u dat het oorspronkelijke bestand wordt overschreven.

## Conclusie

En voilà! Je hebt de relatieve horizontale en verticale posities voor een tabel in een Word-document succesvol ingesteld met Aspose.Words voor .NET. Met deze nieuwe vaardigheid kun je de lay-out en leesbaarheid van je documenten verbeteren, waardoor ze er professioneler en verfijnder uitzien. Blijf experimenteren met verschillende posities en kijk wat het beste bij je past.

## Veelgestelde vragen

### Kan ik tabellen relatief ten opzichte van andere elementen positioneren?  
Ja, met Aspose.Words kunt u tabellen positioneren ten opzichte van verschillende elementen, zoals marges, pagina's, kolommen en meer.

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?  
Ja, u kunt een licentie kopen [hier](https://purchase.aspose.com/buy) of een tijdelijke licentie verkrijgen [hier](https://purchase.aspose.com/temporary-license/).

### Is er een gratis proefversie beschikbaar voor Aspose.Words voor .NET?  
Absoluut! Je kunt een gratis proefversie downloaden [hier](https://releases.aspose.com/).

### Kan ik Aspose.Words gebruiken met andere programmeertalen?  
Aspose.Words is primair ontworpen voor .NET, maar er zijn versies beschikbaar voor Java, Python en andere platformen.

### Waar kan ik meer gedetailleerde documentatie vinden?  
Voor meer diepgaande informatie, bekijk de Aspose.Words-documentatie [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}