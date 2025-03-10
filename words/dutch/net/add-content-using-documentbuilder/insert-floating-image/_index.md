---
title: Zwevende afbeelding invoegen in Word-document
linktitle: Zwevende afbeelding invoegen in Word-document
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een zwevende afbeelding in een Word-document invoegt met Aspose.Words voor .NET met deze gedetailleerde stapsgewijze handleiding. Perfect voor het verbeteren van uw documenten.
weight: 10
url: /nl/net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zwevende afbeelding invoegen in Word-document

## Invoering

Stel je voor dat je een verbluffend rapport of voorstel maakt waarin afbeeldingen perfect zijn gepositioneerd om je tekst aan te vullen. Met Aspose.Words voor .NET kun je dit moeiteloos bereiken. Deze bibliotheek biedt krachtige functies voor documentmanipulatie, waardoor het een go-to-oplossing is voor ontwikkelaars. In deze tutorial richten we ons op het invoegen van een zwevende afbeelding met behulp van de DocumentBuilder-klasse. Of je nu een doorgewinterde ontwikkelaar bent of net begint, deze gids leidt je door elke stap.

## Vereisten

Voordat we beginnen, willen we er zeker van zijn dat u alles bij de hand hebt om te beginnen:

1.  Aspose.Words voor .NET: U kunt de bibliotheek downloaden van de[Aspose releases pagina](https://releases.aspose.com/words/net/).
2. Visual Studio: elke versie die .NET-ontwikkeling ondersteunt.
3. Basiskennis van C#: Kennis van de basisprincipes van C#-programmering is nuttig.
4. Afbeeldingsbestand: Een afbeeldingsbestand dat u wilt invoegen, zoals een logo of een foto.

## Naamruimten importeren

Om Aspose.Words in uw project te gebruiken, moet u de benodigde namespaces importeren. Dit doet u door de volgende regels bovenaan uw C#-bestand toe te voegen:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Nu deze vereisten en naamruimten zijn ingesteld, kunnen we beginnen met onze zelfstudie.

Laten we het proces van het invoegen van een zwevende afbeelding in een Word-document opsplitsen in beheersbare stappen. Elke stap wordt gedetailleerd uitgelegd, zodat u het zonder haperingen kunt volgen.

## Stap 1: Stel uw project in

Maak eerst een nieuw C#-project in Visual Studio. U kunt een Console App kiezen voor de eenvoud.

1. Open Visual Studio en maak een nieuw project.
2. Selecteer 'Console-app (.NET Core)' en klik op 'Volgende'.
3. Geef je project een naam en kies een locatie om het op te slaan. Klik op "Create."
4. Installeer Aspose.Words voor .NET via NuGet Package Manager. Klik met de rechtermuisknop op uw project in de Solution Explorer, selecteer "Manage NuGet Packages" en zoek naar "Aspose.Words". Installeer de nieuwste versie.

## Stap 2: Initialiseer Document en DocumentBuilder

Nu uw project is ingesteld, kunt u de objecten Document en DocumentBuilder initialiseren.

1.  Maak een nieuw exemplaar van de`Document` klas:

```csharp
Document doc = new Document();
```

2. Initialiseer een DocumentBuilder-object:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

 De`Document` object vertegenwoordigt het Word-document en de`DocumentBuilder` helpt bij het toevoegen van inhoud.

## Stap 3: Definieer het afbeeldingspad

Geef vervolgens het pad naar uw afbeeldingsbestand op. Zorg ervoor dat uw afbeelding toegankelijk is vanuit de map van uw project.

Definieer de map met afbeeldingen en de naam van het afbeeldingsbestand:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad waar uw afbeelding is opgeslagen.

## Stap 4: De zwevende afbeelding invoegen

Nu alles is ingesteld, kunnen we de zwevende afbeelding in het document invoegen.

 Gebruik de`InsertImage` methode van de`DocumentBuilder` klasse om de afbeelding in te voegen:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Dit is wat elke parameter betekent:
- `imagePath`: Het pad naar uw afbeeldingsbestand.
- `RelativeHorizontalPosition.Margin`: De horizontale positie ten opzichte van de marge.
- `100`: De horizontale offset vanaf de marge (in punten).
- `RelativeVerticalPosition.Margin`: De verticale positie ten opzichte van de marge.
- `100`: De verticale offset vanaf de marge (in punten).
- `200`: De breedte van de afbeelding (in punten).
- `100`: De hoogte van de afbeelding (in punten).
- `WrapType.Square`: De tekstomloopstijl rond de afbeelding.

## Stap 5: Sla het document op

Sla het document ten slotte op de gewenste locatie op.

1. Geef het pad naar het uitvoerbestand op:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Sla het document op:

```csharp
doc.Save(outputPath);
```

Uw Word-document met de zwevende afbeelding is nu klaar!

## Conclusie

Het invoegen van een zwevende afbeelding in een Word-document met Aspose.Words voor .NET is een eenvoudig proces wanneer het wordt opgedeeld in beheersbare stappen. Door deze handleiding te volgen, kunt u professioneel ogende afbeeldingen toevoegen aan uw documenten, waardoor hun visuele aantrekkingskracht wordt vergroot. Aspose.Words biedt een robuuste API die het manipuleren van documenten een fluitje van een cent maakt, of u nu werkt aan rapporten, voorstellen of een ander documenttype.

## Veelgestelde vragen

### Kan ik meerdere afbeeldingen invoegen met Aspose.Words voor .NET?

 Ja, u kunt meerdere afbeeldingen invoegen door de`InsertImage` methode voor elke afbeelding met de gewenste parameters.

### Hoe verander ik de positie van de afbeelding?

 U kunt de`RelativeHorizontalPosition`, `RelativeVerticalPosition`en offsetparameters om de afbeelding naar wens te positioneren.

### Welke andere manieren om afbeeldingen in te pakken zijn er?

 Aspose.Words ondersteunt verschillende wrap-types zoals`Inline`, `TopBottom`, `Tight`, `Through`, en meer. U kunt degene kiezen die het beste bij uw documentlay-out past.

### Kan ik verschillende afbeeldingsformaten gebruiken?

Ja, Aspose.Words ondersteunt een breed scala aan afbeeldingsformaten, waaronder JPEG, PNG, BMP en GIF.

### Hoe krijg ik een gratis proefversie van Aspose.Words voor .NET?

 U kunt een gratis proefversie krijgen van de[Aspose gratis proefpagina](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
