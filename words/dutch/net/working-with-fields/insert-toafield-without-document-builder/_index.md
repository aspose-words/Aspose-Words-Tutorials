---
"description": "Leer hoe u een inhoudsopgaveveld invoegt zonder een documentbuilder te gebruiken in Aspose.Words voor .NET. Volg onze stapsgewijze handleiding om juridische citaten efficiënt te beheren."
"linktitle": "TOA-veld invoegen zonder documentbouwer"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "TOA-veld invoegen zonder documentbouwer"
"url": "/nl/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# TOA-veld invoegen zonder documentbouwer

## Invoering

Het creëren van een tabel met bronvermeldingen (TOA) in een Word-document kan aanvoelen als het leggen van een complexe puzzel. Met Aspose.Words voor .NET verloopt het proces echter soepel en eenvoudig. In dit artikel leiden we je door de stappen om een TOA-veld in te voegen zonder een documentbuilder te gebruiken, zodat je gemakkelijk citaten en juridische verwijzingen in je Word-documenten kunt beheren.

## Vereisten

Voordat we met de tutorial beginnen, bespreken we eerst de basisbenodigdheden:

- Aspose.Words voor .NET: Zorg ervoor dat je de nieuwste versie hebt geïnstalleerd. Je kunt deze downloaden van de [Aspose-website](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Een .NET-compatibele IDE zoals Visual Studio.
- Basiskennis van C#: Kennis van de basissyntaxis en concepten van C# is nuttig.
- Voorbeeld Word-document: Maak een voorbeelddocument of houd het bij de hand waarin u het inhoudsopgaveveld wilt invoegen.

## Naamruimten importeren

Om te beginnen moet u de benodigde naamruimten importeren uit de Aspose.Words-bibliotheek. Deze configuratie zorgt ervoor dat u toegang hebt tot alle klassen en methoden die nodig zijn voor documentmanipulatie.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Laten we het proces opsplitsen in eenvoudige, gemakkelijk te volgen stappen. We begeleiden je door elke fase en leggen uit wat elk stukje code doet en hoe het bijdraagt aan het creëren van het TOA-veld.

## Stap 1: Initialiseer het document

Eerst moet u een exemplaar van de `Document` klasse. Dit object vertegenwoordigt het Word-document waaraan u werkt.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Deze code initialiseert een nieuw Word-document. Je kunt het zien als het creëren van een leeg canvas waaraan je je inhoud toevoegt.

## Stap 2: Het TA-veld maken en configureren

Vervolgens voegen we een TA-veld (Table of Authorities) toe. Dit veld markeert de items die in de TOA verschijnen.

```csharp
Paragraph para = new Paragraph(doc);

// We willen de velden TA en TOA als volgt invoegen:
// { TA \c 1 \l "Waarde 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Hier is een overzicht:
- Paragraaf para = new Paragraph(doc);: Maakt een nieuwe alinea in het document.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Voegt een TA-veld toe aan de alinea. De `FieldType.FieldTOAEntry` geeft aan dat dit een TOA-invoerveld is.
- fieldTA.EntryCategory = "1";: Stelt de itemcategorie in. Dit is handig voor het categoriseren van verschillende typen items.
- fieldTA.LongCitation = "Waarde 0";: Specificeert de lange citatietekst. Dit is de tekst die in de inhoudsopgave (TOA) wordt weergegeven.
- doc.FirstSection.Body.AppendChild(para);: Voegt de alinea met het TA-veld toe aan de hoofdtekst van het document.

## Stap 3: Voeg het TOA-veld toe

Nu voegen we het eigenlijke TOA-veld in dat alle TA-vermeldingen in een tabel samenvoegt.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

In deze stap:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Voegt een TOA-veld toe aan de alinea.
- fieldToa.EntryCategory = "1";: Filtert de items zodat alleen de items worden opgenomen die zijn gemarkeerd met categorie "1".

## Stap 4: Werk het TOA-veld bij

Nadat u het TOA-veld hebt ingevoegd, moet u het bijwerken om ervoor te zorgen dat het de nieuwste vermeldingen bevat.

```csharp
fieldToa.Update();
```

Met deze opdracht vernieuwt u het TOA-veld, zodat alle gemarkeerde items correct in de tabel worden weergegeven.

## Stap 5: Sla het document op

Sla ten slotte uw document op met het nieuw toegevoegde TOA-veld.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Deze regel code slaat het document op in de opgegeven directory. Zorg ervoor dat u `"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad waar u uw bestand wilt opslaan.

## Conclusie

En voilà! U hebt met succes een inhoudsopgave (TOA)-veld aan een Word-document toegevoegd zonder een documentbuilder te gebruiken. Door deze stappen te volgen, kunt u efficiënt citaten beheren en uitgebreide bronvermeldingstabellen in uw juridische documenten maken. Aspose.Words voor .NET maakt dit proces soepel en efficiënt en biedt u de tools om complexe documenttaken eenvoudig uit te voeren.

## Veelgestelde vragen

### Kan ik meerdere TA-velden met verschillende categorieën toevoegen?
Ja, u kunt meerdere TA-velden met verschillende categorieën toevoegen door de `EntryCategory` eigendom dienovereenkomstig.

### Hoe kan ik het uiterlijk van de TOA aanpassen?
U kunt het uiterlijk van de inhoudsopgave aanpassen door de eigenschappen van het inhoudsopgaveveld te wijzigen, zoals de opmaak van de vermeldingen en categorielabels.

### Is het mogelijk om het TOA-veld automatisch bij te werken?
Hoewel u het TOA-veld handmatig kunt bijwerken met behulp van de `Update` methode, Aspose.Words ondersteunt momenteel geen automatische updates op wijzigingen in documenten.

### Kan ik TA-velden programmatisch toevoegen aan specifieke delen van het document?
Ja, u kunt TA-velden op specifieke locaties toevoegen door ze in de gewenste alinea's of secties in te voegen.

### Hoe verwerk ik meerdere TOA-velden in één document?
U kunt meerdere TOA-velden beheren door verschillende `EntryCategory` waarden en ervoor zorgen dat elk TOA-veld items filtert op basis van de categorie.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}