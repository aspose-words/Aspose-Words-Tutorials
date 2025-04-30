---
"description": "Leer hoe u watermerken toevoegt aan documenten in Aspose.Words voor Java. Pas tekst- en afbeeldingswatermerken aan voor professioneel ogende documenten."
"linktitle": "Watermerken gebruiken in documenten"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Watermerken gebruiken in documenten in Aspose.Words voor Java"
"url": "/nl/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Watermerken gebruiken in documenten in Aspose.Words voor Java


## Inleiding tot het toevoegen van watermerken aan documenten in Aspose.Words voor Java

In deze tutorial laten we zien hoe je watermerken aan documenten kunt toevoegen met behulp van de Aspose.Words voor Java API. Watermerken zijn een handige manier om documenten te labelen met tekst of afbeeldingen om hun status, vertrouwelijkheid of andere relevante informatie aan te geven. In deze handleiding behandelen we zowel tekst- als afbeeldingswatermerken.

## Aspose.Words instellen voor Java

Voordat we watermerken aan documenten gaan toevoegen, moeten we Aspose.Words voor Java configureren. Volg deze stappen om aan de slag te gaan:

1. Download Aspose.Words voor Java van [hier](https://releases.aspose.com/words/java/).
2. Voeg de Aspose.Words voor Java-bibliotheek toe aan uw Java-project.
3. Importeer de benodigde klassen in uw Java-code.

Nu de bibliotheek is ingesteld, kunnen we watermerken toevoegen.

## Tekstwatermerken toevoegen

Tekstwatermerken zijn een veelgebruikte keuze wanneer u tekstuele informatie aan uw documenten wilt toevoegen. Zo voegt u een tekstwatermerk toe met Aspose.Words voor Java:

```java
// Een documentinstantie maken
Document doc = new Document("Document.docx");

// Definieer TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Stel de watermerktekst en -opties in
doc.getWatermark().setText("Test", options);

// Sla het document op met het watermerk
doc.save("DocumentWithWatermark.docx");
```

## Watermerken aan afbeeldingen toevoegen

Naast tekstwatermerken kunt u ook afbeeldingswatermerken aan uw documenten toevoegen. Zo voegt u een afbeeldingswatermerk toe:

```java
// Een documentinstantie maken
Document doc = new Document("Document.docx");

// Laad de afbeelding voor het watermerk
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Stel de grootte en positie van het watermerk in
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Voeg het watermerk toe aan het document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Sla het document op met het watermerk
doc.save("DocumentWithImageWatermark.docx");
```

## Watermerken aanpassen

kunt watermerken aanpassen door hun uiterlijk en positie aan te passen. Voor tekstwatermerken kunt u het lettertype, de grootte, de kleur en de lay-out wijzigen. Voor afbeeldingswatermerken kunt u de grootte en positie aanpassen zoals in de vorige voorbeelden is uitgelegd.

## Watermerken verwijderen

Om watermerken uit een document te verwijderen, kunt u de volgende code gebruiken:

```java
// Een documentinstantie maken
Document doc = new Document("DocumentWithWatermark.docx");

// Verwijder het watermerk
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Sla het document op zonder watermerk
doc.save("DocumentWithoutWatermark.docx");
```


## Conclusie

In deze tutorial hebben we geleerd hoe je watermerken aan documenten toevoegt met Aspose.Words voor Java. Of je nu tekst- of afbeeldingswatermerken wilt toevoegen, Aspose.Words biedt de tools om ze efficiënt aan te passen en te beheren. Je kunt watermerken ook verwijderen wanneer ze niet meer nodig zijn, zodat je documenten er netjes en professioneel uitzien.

## Veelgestelde vragen

### Hoe kan ik het lettertype van een tekstwatermerk wijzigen?

Om het lettertype van een tekstwatermerk te wijzigen, wijzigt u de `setFontFamily` eigendom in de `TextWatermarkOptions`. Bijvoorbeeld:

```java
options.setFontFamily("Times New Roman");
```

### Kan ik meerdere watermerken aan één document toevoegen?

Ja, u kunt meerdere watermerken aan een document toevoegen door meerdere watermerken te maken. `Shape` objecten met verschillende instellingen en deze aan het document toevoegen.

### Is het mogelijk om een watermerk te roteren?

Ja, u kunt een watermerk roteren door de `setRotation` eigendom in de `Shape` object. Positieve waarden roteren het watermerk met de klok mee, en negatieve waarden roteren het tegen de klok in.

### Hoe kan ik een watermerk semi-transparant maken?

Om een watermerk semi-transparant te maken, stelt u de `setSemitransparent` eigendom van `true` in de `TextWatermarkOptions`.

### Kan ik watermerken aan specifieke delen van een document toevoegen?

Ja, u kunt watermerken toevoegen aan specifieke secties van een document door door de secties te itereren en het watermerk aan de gewenste secties toe te voegen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}