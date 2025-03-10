---
title: Gestructureerd document tagbereik start XML-toewijzing
linktitle: Gestructureerd document tagbereik start XML-toewijzing
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u XML-gegevens dynamisch kunt binden aan gestructureerde documenttags in Word met behulp van Aspose.Words voor .NET. Volg onze stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gestructureerd document tagbereik start XML-toewijzing

## Invoering

Heb je ooit dynamisch XML-gegevens in een Word-document willen invoegen? Nou, dan heb je geluk! Aspose.Words voor .NET maakt deze taak een fluitje van een cent. In deze tutorial duiken we diep in gestructureerde document tag range start XML-toewijzing. Met deze functie kun je aangepaste XML-onderdelen aan inhoudsbesturingselementen koppelen, zodat de inhoud van je document naadloos wordt bijgewerkt met je XML-gegevens. Klaar om je documenten om te vormen tot dynamische meesterwerken.

## Vereisten

Voordat we met coderen beginnen, willen we eerst controleren of je alles hebt wat je nodig hebt:

1.  Aspose.Words voor .NET Library: Zorg ervoor dat u de nieuwste versie hebt. U kunt het downloaden[hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere IDE die C# ondersteunt.
3. Basiskennis van C#: Kennis van C#-programmering is een must.
4. Word-document: een voorbeeld van een Word-document om mee te werken.

## Naamruimten importeren

Laten we eerst de benodigde namespaces importeren. Dit zorgt ervoor dat we toegang hebben tot alle benodigde klassen en methoden in Aspose.Words voor .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Stap 1: Stel uw documentenmap in

Elk project heeft een basis nodig, toch? Hier stellen we het pad naar uw documentdirectory in.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 2: Laad het Word-document

Vervolgens laden we het Word-document. Dit is het document waarin we onze XML-gegevens invoegen.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Stap 3: Aangepast XML-onderdeel toevoegen

We moeten een XML-onderdeel maken met de gegevens die we willen invoegen en dit toevoegen aan de CustomXmlPart-collectie van het document. Dit aangepaste XML-onderdeel zal dienen als de gegevensbron voor onze gestructureerde documenttags.

### Een XML-onderdeel maken

Genereer eerst een unieke ID voor het XML-onderdeel en definieer de inhoud ervan.

```csharp
// Maak een XML-onderdeel dat gegevens bevat en voeg het toe aan de CustomXmlPart-verzameling van het document.
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

Een Structured Document Tag (SDT) is een content control die kan worden gekoppeld aan een XML-onderdeel. Hier maken we een SDT die de inhoud van ons aangepaste XML-onderdeel weergeeft.

Zoek eerst het beginpunt van het SDT-bereik in het document.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Stap 5: XML-toewijzing instellen voor de SDT

Nu is het tijd om ons XML-gedeelte aan de SDT te binden. Door een XML-toewijzing in te stellen, specificeren we welk deel van de XML-gegevens in de SDT moet worden weergegeven.

 De XPath wijst naar het specifieke element in het XML-gedeelte dat we willen weergeven. Hier wijzen we naar de tweede`<text>` element binnen de`<root>` element.

```csharp
// Stel een toewijzing in voor onze StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Stap 6: Sla het document op

Sla het document ten slotte op om de wijzigingen in actie te zien. De SDT in het Word-document geeft nu de opgegeven XML-inhoud weer.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusie

En daar heb je het! Je hebt met succes een XML-onderdeel toegewezen aan een gestructureerde documenttag in een Word-document met Aspose.Words voor .NET. Deze krachtige functie stelt je in staat om moeiteloos dynamische en datagestuurde documenten te maken. Of je nu rapporten, facturen of een ander documenttype genereert, XML-toewijzing kan je workflow aanzienlijk stroomlijnen.

## Veelgestelde vragen

### Wat is een gestructureerde documenttag in Word?
Gestructureerde documenttags, ook wel content controls genoemd, zijn containers voor specifieke typen content in Word-documenten. Ze kunnen worden gebruikt om gegevens te binden, bewerkingen te beperken of gebruikers te begeleiden bij het maken van documenten.

### Hoe kan ik de inhoud van een XML-onderdeel dynamisch bijwerken?
 U kunt de inhoud van het XML-onderdeel bijwerken door de`xmlPartContent` string voordat u deze aan het document toevoegt. Werk de string eenvoudigweg bij met de nieuwe gegevens en voeg deze toe aan de`CustomXmlParts` verzameling.

### Kan ik meerdere XML-onderdelen aan verschillende SDT's in hetzelfde document binden?
Ja, u kunt meerdere XML-onderdelen aan verschillende SDT's in hetzelfde document binden. Elke SDT kan zijn eigen unieke XML-onderdeel en XPath-toewijzing hebben.

### Is het mogelijk om complexe XML-structuren toe te wijzen aan SDT's?
Absoluut! U kunt complexe XML-structuren toewijzen aan SDT's door gedetailleerde XPath-expressies te gebruiken die nauwkeurig verwijzen naar de gewenste elementen binnen het XML-gedeelte.

### Hoe kan ik een XML-onderdeel uit een document verwijderen?
 U kunt een XML-onderdeel verwijderen door de`Remove` methode op de`CustomXmlParts` verzameling, het passeren van de`xmlPartId` van het XML-onderdeel dat u wilt verwijderen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
