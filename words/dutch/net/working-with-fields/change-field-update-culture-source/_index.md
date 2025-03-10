---
title: Veld wijzigen Cultuurbron bijwerken
linktitle: Veld wijzigen Cultuurbron bijwerken
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u de veldupdatecultuurbron in Aspose.Words voor .NET kunt wijzigen met deze gids. Beheer datumopmaak op basis van verschillende culturen eenvoudig.
weight: 10
url: /nl/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Veld wijzigen Cultuurbron bijwerken

## Invoering

In deze tutorial duiken we in de wereld van Aspose.Words voor .NET en onderzoeken we hoe je de bron van de veldupdatecultuur kunt wijzigen. Als je werkt met Word-documenten met datumvelden en je moet bepalen hoe deze datums worden geformatteerd op basis van verschillende culturen, dan is deze gids iets voor jou. Laten we het proces stap voor stap doorlopen, zodat je elk concept begrijpt en het effectief kunt toepassen in je projecten.

## Vereisten

Voordat we met de code aan de slag gaan, moet u ervoor zorgen dat u het volgende heeft:

-  Aspose.Words voor .NET: U kunt het downloaden van[hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: elke .NET-compatibele IDE (bijv. Visual Studio).
- Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u een basiskennis hebt van C#-programmering.

## Naamruimten importeren

Laten we eerst de benodigde namespaces voor ons project importeren. Dit zorgt ervoor dat we toegang hebben tot alle benodigde klassen en methoden die Aspose.Words biedt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Laten we het voorbeeld nu opsplitsen in meerdere stappen om u te helpen begrijpen hoe u de bron van de veldupdatecultuur in Aspose.Words voor .NET kunt wijzigen.

## Stap 1: Initialiseer het document

 De eerste stap is het maken van een nieuw exemplaar van de`Document` klasse en een`DocumentBuilder`Hiermee wordt de basis gelegd voor het bouwen en bewerken van ons Word-document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Velden met specifieke landinstellingen invoegen

Vervolgens moeten we velden in het document invoegen. Voor dit voorbeeld voegen we twee datumvelden in. We stellen de landinstelling van het lettertype in op Duits (LocaleId = 1031) om te laten zien hoe de cultuur de datumnotatie beïnvloedt.

```csharp
builder.Font.LocaleId = 1031; // Duits
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Stap 3: Stel de bron van de veldupdatecultuur in

 Om de cultuur te controleren die wordt gebruikt bij het bijwerken van de velden, stellen we de`FieldUpdateCultureSource` eigendom van de`FieldOptions`klasse. Deze eigenschap bepaalt of de cultuur uit de veldcode of het document wordt gehaald.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Stap 4: Mail Merge uitvoeren

We moeten nu een mail merge uitvoeren om de velden te vullen met actuele data. In dit voorbeeld stellen we het tweede datumveld in (`Date2`) tot 1 januari 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Stap 5: Sla het document op

Ten slotte slaan we het document op in de opgegeven directory. Deze stap voltooit het proces van het wijzigen van de veldupdatecultuurbron.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Conclusie

En daar heb je het! Je hebt de veldupdatecultuurbron in Aspose.Words voor .NET succesvol gewijzigd. Door deze stappen te volgen, kun je ervoor zorgen dat je Word-documenten datums en andere veldwaarden weergeven volgens de opgegeven cultuurinstellingen. Dit kan met name handig zijn bij het genereren van documenten voor een internationaal publiek.

## Veelgestelde vragen

###  Wat is het doel van het instellen van de`LocaleId`?
 De`LocaleId` Hiermee worden de culturele instellingen voor de tekst opgegeven. Deze bepalen hoe datums en andere landspecifieke gegevens worden opgemaakt.

### Kan ik een andere landinstelling dan Duits gebruiken?
 Ja, u kunt de`LocaleId`naar een geldige locale-ID. Bijvoorbeeld 1033 voor Engels (Verenigde Staten).

###  Wat gebeurt er als ik de`FieldUpdateCultureSource` property?
Als deze eigenschap niet is ingesteld, worden de standaardcultuurinstellingen van het document gebruikt bij het bijwerken van velden.

### Is het mogelijk om velden bij te werken op basis van de documentcultuur in plaats van de veldcode?
 Ja, u kunt instellen`FieldUpdateCultureSource` naar`FieldUpdateCultureSource.Document` om de cultuurinstellingen van het document te gebruiken.

### Hoe kan ik datums in een ander patroon formatteren?
 U kunt het datumnotatiepatroon in de`InsertField` methode door het wijzigen van de`\\@` schakelwaarde.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
