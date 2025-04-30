---
"description": "Leer hoe u XML-gegevens dynamisch kunt koppelen aan gestructureerde documenttags in Word met Aspose.Words voor .NET. Volg onze stapsgewijze handleiding."
"linktitle": "Gestructureerd document tagbereik start XML-toewijzing"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Gestructureerd document tagbereik start XML-toewijzing"
"url": "/nl/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gestructureerd document tagbereik start XML-toewijzing

## Invoering

Heb je ooit XML-gegevens dynamisch in een Word-document willen invoegen? Dan heb je geluk! Aspose.Words voor .NET maakt deze taak een fluitje van een cent. In deze tutorial duiken we diep in de gestructureerde XML-toewijzing van het tagbereik van documenten. Met deze functie kun je aangepaste XML-onderdelen koppelen aan inhoudsbesturingselementen, zodat de inhoud van je document naadloos wordt bijgewerkt met je XML-gegevens. Klaar om je documenten om te vormen tot dynamische meesterwerken?

## Vereisten

Voordat we met coderen beginnen, willen we eerst controleren of je alles hebt wat je nodig hebt:

1. Aspose.Words voor .NET-bibliotheek: zorg ervoor dat u de nieuwste versie hebt. U kunt deze downloaden. [hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere IDE die C# ondersteunt.
3. Basiskennis van C#: Kennis van C#-programmering is een must.
4. Word-document: een voorbeeld van een Word-document om mee te werken.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren. Dit zorgt ervoor dat we toegang hebben tot alle vereiste klassen en methoden in Aspose.Words voor .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Stap 1: Stel uw documentenmap in

Elk project heeft een basis nodig, toch? Hier stellen we het pad naar je documentenmap in.

```csharp
// Pad naar uw documentenmap 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Laad het Word-document

Vervolgens laden we het Word-document. Dit is het document waarin we onze XML-gegevens gaan invoegen.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Stap 3: Aangepast XML-onderdeel toevoegen

We moeten een XML-onderdeel maken met de gegevens die we willen invoegen en dit toevoegen aan de CustomXmlPart-collectie van het document. Dit aangepaste XML-onderdeel dient als gegevensbron voor onze gestructureerde documenttags.

### Een XML-onderdeel maken

Genereer eerst een unieke ID voor het XML-onderdeel en definieer de inhoud ervan.

```csharp
// Maak een XML-onderdeel dat gegevens bevat en voeg het toe aan de verzameling CustomXmlPart van het document.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Controleer de XML-onderdeelinhoud

Om er zeker van te zijn dat het XML-onderdeel correct wordt toegevoegd, printen we de inhoud ervan.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Stap 4: Een gestructureerde documenttag maken

Een Structured Document Tag (SDT) is een content control die aan een XML-onderdeel kan worden gekoppeld. Hier maken we een SDT die de inhoud van ons aangepaste XML-onderdeel weergeeft.

Zoek eerst het beginpunt van het SDT-bereik in het document.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Stap 5: XML-toewijzing instellen voor de SDT

Nu is het tijd om ons XML-gedeelte aan de SDT te koppelen. Door een XML-mapping in te stellen, specificeren we welk deel van de XML-gegevens in de SDT moet worden weergegeven.

Het XPath verwijst naar het specifieke element in het XML-gedeelte dat we willen weergeven. Hier verwijzen we naar het tweede element. `<text>` element binnen de `<root>` element.

```csharp
// Stel een mapping in voor onze StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Stap 6: Sla het document op

Sla ten slotte het document op om de wijzigingen in actie te zien. De SDT in het Word-document geeft nu de opgegeven XML-inhoud weer.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusie

En voilà! Je hebt met succes een XML-onderdeel gekoppeld aan een gestructureerde documenttag in een Word-document met Aspose.Words voor .NET. Deze krachtige functie stelt je in staat om moeiteloos dynamische en datagestuurde documenten te maken. Of je nu rapporten, facturen of andere documenttypen genereert, XML-koppeling kan je workflow aanzienlijk stroomlijnen.

## Veelgestelde vragen

### Wat is een gestructureerde documenttag in Word?
Gestructureerde documenttags, ook wel inhoudsbeheer genoemd, zijn containers voor specifieke typen inhoud in Word-documenten. Ze kunnen worden gebruikt om gegevens te binden, bewerkingen te beperken of gebruikers te begeleiden bij het maken van documenten.

### Hoe kan ik de XML-onderdeelinhoud dynamisch bijwerken?
U kunt de inhoud van het XML-onderdeel bijwerken door de `xmlPartContent` string voordat u deze aan het document toevoegt. Werk de string eenvoudigweg bij met de nieuwe gegevens en voeg deze toe aan de `CustomXmlParts` verzameling.

### Kan ik meerdere XML-onderdelen aan verschillende SDT's in hetzelfde document binden?
Ja, u kunt meerdere XML-onderdelen aan verschillende SDT's in hetzelfde document koppelen. Elke SDT kan zijn eigen unieke XML-onderdeel en XPath-toewijzing hebben.

### Is het mogelijk om complexe XML-structuren naar SDT's te mappen?
Absoluut! Je kunt complexe XML-structuren toewijzen aan SDT's door gedetailleerde XPath-expressies te gebruiken die nauwkeurig verwijzen naar de gewenste elementen in het XML-gedeelte.

### Hoe kan ik een XML-onderdeel uit een document verwijderen?
U kunt een XML-onderdeel verwijderen door de `Remove` methode op de `CustomXmlParts` verzameling, het doorgeven van de `xmlPartId` van het XML-gedeelte dat u wilt verwijderen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}