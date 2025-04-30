---
"description": "Leer hoe u samenvoegvelden in Word-documenten kunt invoegen en configureren met Aspose.Words voor .NET met deze uitgebreide, stapsgewijze zelfstudie."
"linktitle": "Samenvoegveld invoegen met behulp van DOM"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Samenvoegveld invoegen met behulp van DOM"
"url": "/nl/net/working-with-fields/insert-merge-field-using-dom/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Samenvoegveld invoegen met behulp van DOM

## Invoering

Als je met documentverwerking in .NET werkt, ben je waarschijnlijk Aspose.Words tegengekomen. Deze krachtige bibliotheek biedt een breed scala aan functies voor het programmatisch bewerken van Word-documenten. In deze tutorial richten we ons op één specifieke functie: het invoegen van een samenvoegveld met behulp van het Document Object Model (DOM) in Aspose.Words voor .NET. Deze handleiding begeleidt je door elke stap, van het instellen van je omgeving tot het invoegen en bijwerken van een samenvoegveld in een Word-document.

## Vereisten

Voordat we met de code aan de slag gaan, controleren we of je alles hebt wat je nodig hebt om deze tutorial te volgen.

1. Basiskennis van C#: U moet vertrouwd zijn met C#-programmering.
2. Visual Studio geïnstalleerd: zorg ervoor dat Visual Studio of een andere C# IDE op uw computer is geïnstalleerd.
3. Aspose.Words voor .NET: Download en installeer de nieuwste versie van Aspose.Words voor .NET van de [Uitgaven](https://releases.aspose.com/words/net/).
4. Geldig rijbewijs: Als u geen rijbewijs heeft, kunt u een [tijdelijke licentie](https://purchase.aspose.com/temporary-license/) voor evaluatie.

## Stap 1: Stel uw project in

Laten we eerst een nieuw project in Visual Studio opzetten.

1. Visual Studio openen.
2. Maak een nieuw project: Ga naar Bestand > Nieuw > Project. Selecteer een C# Console-app.
3. Geef uw project een naam: Geef uw project een betekenisvolle naam en klik op Maken.

## Stap 2: Aspose.Words installeren

Om Aspose.Words te gebruiken, moet je het aan je project toevoegen. Dit kan via NuGet Package Manager.

1. Open NuGet Package Manager: klik met de rechtermuisknop op uw project in Solution Explorer en selecteer vervolgens NuGet-pakketten beheren.
2. Zoeken naar Aspose.Words: Zoek in de NuGet Package Manager naar "Aspose.Words".
3. Installeer het pakket: Klik op Installeren om Aspose.Words aan uw project toe te voegen.

## Stap 3: Naamruimten importeren

Om Aspose.Words te kunnen gebruiken, moet je de benodigde naamruimten in je project importeren. Zo doe je dat:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## Stap 4: Initialiseer uw document

Nu alles is ingesteld, kunnen we een nieuw Word-document maken en de DocumentBuilder initialiseren.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Maak het document en de DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 5: Verplaats de cursor naar een specifieke alinea

Vervolgens moeten we de cursor verplaatsen naar de specifieke alinea in het document waar we het samenvoegveld willen invoegen.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## Stap 6: Het samenvoegveld invoegen

Het invoegen van een samenvoegveld is eenvoudig. We gebruiken de `InsertField` methode van de `DocumentBuilder` klas.

```csharp
// Samenvoegveld invoegen.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## Stap 7: Het samenvoegveld configureren

Nadat u het samenvoegveld hebt ingevoegd, kunt u verschillende eigenschappen instellen om het veld naar uw wensen te configureren.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## Stap 8: Het document bijwerken en opslaan

Werk ten slotte het veld bij om er zeker van te zijn dat alle instellingen zijn toegepast en sla het document op.

```csharp
// Werk het veld bij.
field.Update();

// Sla het document op.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## Conclusie

Door deze stappen te volgen, kunt u eenvoudig samenvoegvelden invoegen en configureren in een Word-document met Aspose.Words voor .NET. Deze tutorial behandelde de essentiële stappen, van het instellen van uw omgeving tot het opslaan van het definitieve document. Met Aspose.Words kunt u complexe documentverwerkingstaken automatiseren, waardoor uw .NET-applicaties krachtiger en efficiënter worden.

## Veelgestelde vragen

###  Wat is een samenvoegveld?
Een samenvoegveld is een tijdelijke aanduiding in een document die dynamisch kan worden vervangen door gegevens uit een gegevensbron, zoals een database of een CSV-bestand.

###  Kan ik Aspose.Words gratis gebruiken?
Aspose.Words biedt een gratis proefversie aan die u kunt downloaden [hier](https://releases.aspose.com/)Voor langdurig gebruik dient u een licentie aan te schaffen.

###  Hoe krijg ik een tijdelijke licentie voor Aspose.Words?
U kunt een tijdelijke licentie verkrijgen via de Aspose-website [hier](https://purchase.aspose.com/temporary-license/).

### Welke versies van .NET worden ondersteund door Aspose.Words?
Aspose.Words ondersteunt meerdere versies van .NET, waaronder .NET Framework, .NET Core en .NET Standard.

###  Waar kan ik de API-documentatie voor Aspose.Words vinden?
De API-documentatie is beschikbaar [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}