---
title: Laatst opgeslagen tijd eigenschap bijwerken
linktitle: Laatst opgeslagen tijd eigenschap bijwerken
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u de laatst opgeslagen tijdeigenschap in Word-documenten kunt bijwerken met Aspose.Words voor .NET. Volg onze gedetailleerde, stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Laatst opgeslagen tijd eigenschap bijwerken

## Invoering

Heb je je ooit afgevraagd hoe je de laatst opgeslagen tijdeigenschap in je Word-documenten programmatisch kunt bijhouden? Als je met meerdere documenten werkt en hun metagegevens moet onderhouden, kan het erg handig zijn om de laatst opgeslagen tijdeigenschap bij te werken. Vandaag ga ik je door dit proces leiden met behulp van Aspose.Words voor .NET. Dus, gesp je vast en laten we erin duiken!

## Vereisten

Voordat we met de stapsgewijze handleiding beginnen, zijn er een paar dingen die u nodig hebt:

1.  Aspose.Words voor .NET: Zorg ervoor dat u Aspose.Words voor .NET hebt geïnstalleerd. Als u dat niet hebt gedaan, kunt u[download het hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Een ontwikkelomgeving zoals Visual Studio.
3. Basiskennis van C#: Kennis van de basisprincipes van C#-programmering is nuttig.

## Naamruimten importeren

Zorg er allereerst voor dat u de benodigde namespaces in uw project importeert. Dit geeft u toegang tot de klassen en methoden die nodig zijn voor het manipuleren van Word-documenten.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Laten we het proces nu opsplitsen in eenvoudige stappen. Elke stap begeleidt u door het proces van het updaten van de laatst opgeslagen tijdeigenschap in uw Word-document.

## Stap 1: Stel uw documentenmap in

Eerst moet u het pad naar uw documentdirectory opgeven. Dit is waar uw bestaande document is opgeslagen en waar het bijgewerkte document zal worden opgeslagen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het werkelijke pad naar uw directory.

## Stap 2: Laad uw Word-document

 Laad vervolgens het Word-document dat u wilt bijwerken. U kunt dit doen door een exemplaar van de`Document` klasse en het pad van uw document doorgeven.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

 Zorg ervoor dat het document met de naam`Document.docx` is aanwezig in de opgegeven directory.

## Stap 3: Configureer opslagopties

 Maak nu een instantie van de`OoxmlSaveOptions` klasse. Met deze klasse kunt u opties opgeven voor het opslaan van uw document in de Office Open XML (OOXML)-indeling. Hier stelt u de`UpdateLastSavedTimeProperty` naar`true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Hiermee wordt Aspose.Words verteld om de laatst opgeslagen tijdseigenschap van het document bij te werken.

## Stap 4: Sla het bijgewerkte document op

 Sla het document ten slotte op met behulp van de`Save` methode van de`Document` klasse, waarbij u het pad doorgeeft waar u het bijgewerkte document wilt opslaan en de opslagopties.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Hiermee wordt het document opgeslagen met de bijgewerkte eigenschap voor de laatste keer dat het is opgeslagen.

## Conclusie

En daar heb je het! Door deze stappen te volgen, kun je eenvoudig de laatst opgeslagen tijdeigenschap van je Word-documenten bijwerken met Aspose.Words voor .NET. Dit is vooral handig voor het onderhouden van nauwkeurige metagegevens in je documenten, wat cruciaal kan zijn voor documentbeheersystemen en verschillende andere toepassingen.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het maken, bewerken en converteren van Word-documenten in .NET-toepassingen.

### Waarom moet ik de eigenschap 'Laatst opgeslagen tijd' bijwerken?
Door de eigenschap 'Laatst opgeslagen tijd' bij te werken, blijven de metagegevens nauwkeurig. Dit is essentieel voor het bijhouden en beheren van documenten.

### Kan ik andere eigenschappen bijwerken met Aspose.Words voor .NET?
Ja, met Aspose.Words voor .NET kunt u verschillende documenteigenschappen bijwerken, zoals titel, auteur en onderwerp.

### Is Aspose.Words voor .NET gratis?
 Aspose.Words voor .NET biedt een gratis proefversie, maar voor volledige functionaliteit is een licentie vereist. U kunt een licentie verkrijgen[hier](https://purchase.aspose.com/buy).

### Waar kan ik meer tutorials vinden over Aspose.Words voor .NET?
 kunt meer tutorials en documentatie vinden[hier](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
