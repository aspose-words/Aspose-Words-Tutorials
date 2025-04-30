---
"description": "Leer hoe je de bron van de veldupdatecultuur in Aspose.Words voor .NET kunt wijzigen met deze handleiding. Beheer de datumopmaak eenvoudig op basis van verschillende culturen."
"linktitle": "Veld wijzigen Cultuurbron bijwerken"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Veld wijzigen Cultuurbron bijwerken"
"url": "/nl/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Veld wijzigen Cultuurbron bijwerken

## Invoering

In deze tutorial duiken we in de wereld van Aspose.Words voor .NET en ontdekken we hoe je de bron van de veldupdatecultuur kunt wijzigen. Als je werkt met Word-documenten met datumvelden en je wilt bepalen hoe deze datums worden opgemaakt op basis van verschillende culturen, dan is deze handleiding iets voor jou. Laten we het proces stap voor stap doorlopen, zodat je elk concept begrijpt en effectief kunt toepassen in je projecten.

## Vereisten

Voordat we in de code duiken, moet u ervoor zorgen dat u het volgende heeft:

- Aspose.Words voor .NET: U kunt het downloaden van [hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Elke .NET-compatibele IDE (bijv. Visual Studio).
- Basiskennis van C#: in deze tutorial wordt ervan uitgegaan dat u een basiskennis hebt van C#-programmering.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten voor ons project importeren. Dit zorgt ervoor dat we toegang hebben tot alle vereiste klassen en methoden van Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Laten we het voorbeeld opsplitsen in meerdere stappen om u te helpen begrijpen hoe u de bron van de veldupdatecultuur in Aspose.Words voor .NET kunt wijzigen.

## Stap 1: Initialiseer het document

De eerste stap is het maken van een nieuw exemplaar van de `Document` klasse en een `DocumentBuilder`Dit vormt de basis voor het bouwen en bewerken van ons Word-document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Velden met specifieke landinstellingen invoegen

Vervolgens moeten we velden in het document invoegen. In dit voorbeeld voegen we twee datumvelden toe. We stellen de landinstelling van het lettertype in op Duits (LocaleId = 1031) om te laten zien hoe de cultuur de datumnotatie beïnvloedt.

```csharp
builder.Font.LocaleId = 1031; // Duits
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Stap 3: Veldupdatecultuurbron instellen

Om de cultuur te controleren die wordt gebruikt bij het bijwerken van de velden, stellen we de `FieldUpdateCultureSource` eigendom van de `FieldOptions` klasse. Deze eigenschap bepaalt of de cultuur uit de veldcode of het document wordt gehaald.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Stap 4: Mail Merge uitvoeren

We moeten nu een samenvoeging uitvoeren om de velden met daadwerkelijke gegevens te vullen. In dit voorbeeld stellen we het tweede datumveld in (`Date2`) tot 1 januari 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Stap 5: Sla het document op

Ten slotte slaan we het document op in de opgegeven directory. Deze stap voltooit het proces van het wijzigen van de bron van de veldupdatecultuur.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Conclusie

En voilà! U hebt de bron van de veldupdatecultuur in Aspose.Words voor .NET succesvol gewijzigd. Door deze stappen te volgen, zorgt u ervoor dat uw Word-documenten datums en andere veldwaarden weergeven volgens de opgegeven cultuurinstellingen. Dit kan met name handig zijn bij het genereren van documenten voor een internationaal publiek.

## Veelgestelde vragen

### Wat is het doel van het instellen van de `LocaleId`?
De `LocaleId` Hiermee worden de cultuurinstellingen voor de tekst opgegeven, die van invloed zijn op de manier waarop datums en andere landspecifieke gegevens worden opgemaakt.

### Kan ik een andere landinstelling dan Duits gebruiken?
Ja, u kunt de `LocaleId` naar een geldige locale-ID. Bijvoorbeeld 1033 voor Engels (Verenigde Staten).

### Wat gebeurt er als ik de `FieldUpdateCultureSource` eigendom?
Als deze eigenschap niet is ingesteld, worden de standaardcultuurinstellingen van het document gebruikt bij het bijwerken van velden.

### Is het mogelijk om velden bij te werken op basis van de documentcultuur in plaats van op basis van de veldcode?
Ja, u kunt instellen `FieldUpdateCultureSource` naar `FieldUpdateCultureSource.Document` om de cultuurinstellingen van het document te gebruiken.

### Hoe kan ik datums volgens een ander patroon formatteren?
U kunt het datumnotatiepatroon in de `InsertField` methode door het wijzigen van de `\\@` schakelwaarde.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}