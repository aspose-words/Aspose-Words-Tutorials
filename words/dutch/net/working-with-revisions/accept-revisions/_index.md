---
"description": "Beheers documentrevisies met Aspose.Words voor .NET. Leer moeiteloos wijzigingen te volgen, te accepteren en af te wijzen. Verbeter uw vaardigheden in documentbeheer."
"linktitle": "Accepteer revisies"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Accepteer revisies"
"url": "/nl/net/working-with-revisions/accept-revisions/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Accepteer revisies

## Invoering

Heb je je ooit in een doolhof van documentrevisies bevonden en moeite gehad om alle wijzigingen van meerdere bijdragers bij te houden? Met Aspose.Words voor .NET wordt het beheren van revisies in Word-documenten een fluitje van een cent. Deze krachtige bibliotheek stelt ontwikkelaars in staat om moeiteloos wijzigingen te volgen, te accepteren en af te wijzen, zodat je documenten georganiseerd en up-to-date blijven. In deze tutorial duiken we in het stapsgewijze proces van het verwerken van documentrevisies met Aspose.Words voor .NET, van het initialiseren van het document tot het accepteren van alle wijzigingen.

## Vereisten

Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

- Visual Studio op uw computer geïnstalleerd.
- .NET framework (bij voorkeur de nieuwste versie).
- Aspose.Words voor .NET-bibliotheek. U kunt het downloaden. [hier](https://releases.aspose.com/words/net/).
- Basiskennis van C#-programmering.

Laten we nu eens dieper ingaan op de details en bekijken hoe u documentrevisies kunt uitvoeren met Aspose.Words voor .NET.

## Naamruimten importeren

Allereerst moet je de benodigde naamruimten importeren om met Aspose.Words te kunnen werken. Voeg de volgende using-richtlijnen bovenaan je codebestand toe:

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
```

Laten we het proces opsplitsen in beheersbare stappen. Elke stap wordt gedetailleerd uitgelegd, zodat je elk onderdeel van de code begrijpt.

## Stap 1: Initialiseer het document

Om te beginnen moeten we een nieuw document aanmaken en een aantal alinea's toevoegen. Dit is de basis voor het bijhouden van revisies.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
Body body = doc.FirstSection.Body;
Paragraph para = body.FirstParagraph;

// Voeg tekst toe aan de eerste alinea en voeg vervolgens nog twee alinea's toe.
para.AppendChild(new Run(doc, "Paragraph 1. "));
body.AppendParagraph("Paragraph 2. ");
body.AppendParagraph("Paragraph 3. ");
```

In deze stap hebben we een nieuw document aangemaakt en er drie alinea's aan toegevoegd. Deze alinea's dienen als basis voor onze revisietracking.

## Stap 2: Begin met het bijhouden van revisies

Vervolgens moeten we revisietracking inschakelen. Hiermee kunnen we eventuele wijzigingen in het document vastleggen.

```csharp
// Begin met het bijhouden van revisies.
doc.StartTrackRevisions("John Doe", DateTime.Now);
```

Door te bellen `StartTrackRevisions`zorgen we ervoor dat het document alle volgende wijzigingen kan bijhouden. De naam van de auteur en de huidige datum worden als parameters doorgegeven.

## Stap 3: Een revisie toevoegen

Nu revisietracking is ingeschakeld, voegen we een nieuwe alinea toe. Deze toevoeging wordt gemarkeerd als een revisie.

```csharp
// Deze alinea is een revisie en krijgt de bijbehorende "IsInsertRevision" vlag ingeschakeld.
para = body.AppendParagraph("Paragraph 4. ");
```

Hier wordt een nieuwe alinea ("Paragraaf 4") toegevoegd. Omdat revisietracking is ingeschakeld, wordt deze alinea als revisie gemarkeerd.

## Stap 4: Een alinea verwijderen

Vervolgens verwijderen we een bestaande alinea en bekijken we hoe de revisie wordt bijgehouden.

```csharp
// Haal de alineaverzameling van het document op en verwijder een alinea.
ParagraphCollection paragraphs = body.Paragraphs;
para = paragraphs[2];
para.Remove();
```

In deze stap wordt de derde alinea verwijderd. Dankzij revisietracking wordt deze verwijdering geregistreerd en wordt de alinea gemarkeerd voor verwijdering in plaats van direct uit het document te worden verwijderd.

## Stap 5: Alle revisies accepteren

Laten we tot slot alle bijgehouden revisies accepteren en de wijzigingen in het document vastleggen.

```csharp
// Accepteer alle revisies.
doc.AcceptAllRevisions();
```

Door te bellen `AcceptAllRevisions`, zorgen we ervoor dat alle wijzigingen (toevoegingen en verwijderingen) worden geaccepteerd en in het document worden toegepast. De wijzigingen worden niet langer gemarkeerd en in het document geïntegreerd.

## Stap 6: Stop met het bijhouden van revisies

### Revisietracking uitschakelen

Tot slot kunt u het bijhouden van wijzigingen uitschakelen, zodat er geen verdere wijzigingen meer worden vastgelegd.

```csharp
// Stop met het bijhouden van revisies.
doc.StopTrackRevisions();
```

Met deze stap worden nieuwe wijzigingen niet meer bijgehouden in het document. Alle daaropvolgende bewerkingen worden als gewone inhoud behandeld.

## Stap 7: Sla het document op

Sla ten slotte het gewijzigde document op in de opgegeven directory.

```csharp
// Sla het document op.
doc.Save(dataDir + "WorkingWithRevisions.AcceptRevisions.docx");
```

Door het document op te slaan, zorgen we ervoor dat al onze wijzigingen en geaccepteerde revisies behouden blijven.

## Conclusie

Het beheren van documentrevisies kan een lastige klus zijn, maar met Aspose.Words voor .NET wordt het eenvoudig en efficiënt. Door de stappen in deze handleiding te volgen, kunt u eenvoudig wijzigingen in uw Word-documenten volgen, accepteren en afwijzen, zodat uw documenten altijd up-to-date en nauwkeurig zijn. Dus waar wacht u nog op? Duik in de wereld van Aspose.Words en stroomlijn uw documentbeheer vandaag nog!

## Veelgestelde vragen

### Hoe start ik met het bijhouden van revisies in Aspose.Words voor .NET?

U kunt beginnen met het bijhouden van revisies door de `StartTrackRevisions` op uw documentobject en geeft u de naam van de auteur en de huidige datum door.

### Kan ik op elk moment stoppen met het bijhouden van revisies?

Ja, u kunt het bijhouden van revisies stoppen door de `StopTrackRevisions` methode op uw documentobject.

### Hoe accepteer ik alle revisies in een document?

Om alle revisies te accepteren, gebruikt u de `AcceptAllRevisions` methode op uw documentobject.

### Kan ik specifieke revisies afwijzen?

Ja, u kunt specifieke revisies afwijzen door ernaartoe te navigeren en de `Reject` methode.

### Waar kan ik Aspose.Words voor .NET downloaden?

U kunt Aspose.Words voor .NET downloaden van de [downloadlink](https://releases.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}