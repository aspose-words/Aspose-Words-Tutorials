---
"description": "Leer hoe u de eigenschap 'Laatst opgeslagen tijd' in Word-documenten kunt bijwerken met Aspose.Words voor .NET. Volg onze gedetailleerde, stapsgewijze handleiding."
"linktitle": "Laatst opgeslagen tijd eigenschap bijwerken"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Laatst opgeslagen tijd eigenschap bijwerken"
"url": "/nl/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Laatst opgeslagen tijd eigenschap bijwerken

## Invoering

Heb je je ooit afgevraagd hoe je de eigenschap 'laatst opgeslagen tijd' in je Word-documenten programmatisch kunt bijhouden? Als je met meerdere documenten werkt en de metadata ervan moet bijhouden, kan het bijwerken van de eigenschap 'laatst opgeslagen tijd' erg handig zijn. Vandaag neem ik je mee door dit proces met behulp van Aspose.Words voor .NET. Dus, riemen vast en laten we beginnen!

## Vereisten

Voordat we met de stapsgewijze handleiding beginnen, heb je een paar dingen nodig:

1. Aspose.Words voor .NET: Zorg ervoor dat je Aspose.Words voor .NET hebt geïnstalleerd. Zo niet, dan kun je... [download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een ontwikkelomgeving zoals Visual Studio.
3. Basiskennis van C#: Kennis van de basisprincipes van C#-programmering is nuttig.

## Naamruimten importeren

Zorg er allereerst voor dat u de benodigde naamruimten in uw project importeert. Zo krijgt u toegang tot de klassen en methoden die nodig zijn om Word-documenten te bewerken.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Laten we het proces nu opsplitsen in eenvoudige stappen. Elke stap begeleidt u door het proces van het bijwerken van de laatst opgeslagen tijdseigenschap in uw Word-document.

## Stap 1: Stel uw documentenmap in

Eerst moet u het pad naar uw documentmap opgeven. Dit is waar uw bestaande document wordt opgeslagen en waar het bijgewerkte document wordt opgeslagen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Vervangen `"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw directory.

## Stap 2: Laad uw Word-document

Laad vervolgens het Word-document dat u wilt bijwerken. U kunt dit doen door een exemplaar van de `Document` klasse en het pad van uw document doorgeven.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Zorg ervoor dat het document met de naam `Document.docx` is aanwezig in de opgegeven directory.

## Stap 3: Opties voor opslaan configureren

Maak nu een instantie van de `OoxmlSaveOptions` klasse. Met deze klasse kunt u opties opgeven voor het opslaan van uw document in de Office Open XML-indeling (OOXML). Hier stelt u de `UpdateLastSavedTimeProperty` naar `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Hiermee krijgt Aspose.Words de opdracht om de laatst opgeslagen tijdseigenschap van het document bij te werken.

## Stap 4: Sla het bijgewerkte document op

Sla het document ten slotte op met behulp van de `Save` methode van de `Document` klasse, waarbij u het pad doorgeeft waar u het bijgewerkte document wilt opslaan en de opties voor opslaan.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Hiermee wordt het document opgeslagen met de bijgewerkte eigenschap 'laatste opslagtijd'.

## Conclusie

En voilà! Door deze stappen te volgen, kunt u eenvoudig de laatst opgeslagen tijdseigenschap van uw Word-documenten bijwerken met Aspose.Words voor .NET. Dit is vooral handig voor het bijhouden van accurate metadata in uw documenten, wat cruciaal kan zijn voor documentbeheersystemen en diverse andere applicaties.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het maken, bewerken en converteren van Word-documenten in .NET-toepassingen.

### Waarom moet ik de eigenschap 'Laatst opgeslagen tijd' bijwerken?
Door de eigenschap 'Laatst opgeslagen tijd' bij te werken, blijven de metagegevens nauwkeurig, wat essentieel is voor het bijhouden en beheren van documenten.

### Kan ik andere eigenschappen bijwerken met Aspose.Words voor .NET?
Ja, met Aspose.Words voor .NET kunt u verschillende documenteigenschappen bijwerken, zoals titel, auteur en onderwerp.

### Is Aspose.Words voor .NET gratis?
Aspose.Words voor .NET biedt een gratis proefperiode, maar voor volledige functionaliteit is een licentie vereist. U kunt een licentie verkrijgen [hier](https://purchase.aspose.com/buy).

### Waar kan ik meer tutorials vinden over Aspose.Words voor .NET?
Meer tutorials en documentatie vindt u hier [hier](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}