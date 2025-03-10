---
title: Använda vattenstämplar till dokument i Aspose.Words för Java
linktitle: Använda vattenstämplar till dokument
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du lägger till vattenstämplar i dokument i Aspose.Words för Java. Anpassa text- och bildvattenstämplar för professionella dokument.
weight: 15
url: /sv/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använda vattenstämplar till dokument i Aspose.Words för Java


## Introduktion till att lägga till vattenstämplar till dokument i Aspose.Words för Java

den här handledningen kommer vi att utforska hur man lägger till vattenstämplar i dokument med Aspose.Words för Java API. Vattenstämplar är ett användbart sätt att märka dokument med text eller grafik för att ange deras status, konfidentialitet eller annan relevant information. Vi kommer att täcka både text- och bildvattenstämplar i den här guiden.

## Konfigurera Aspose.Words för Java

Innan vi börjar lägga till vattenstämplar i dokument måste vi ställa in Aspose.Words för Java. Följ dessa steg för att komma igång:

1.  Ladda ner Aspose.Words för Java från[här](https://releases.aspose.com/words/java/).
2. Lägg till Aspose.Words for Java-biblioteket till ditt Java-projekt.
3. Importera de nödvändiga klasserna i din Java-kod.

Nu när vi har satt upp biblioteket, låt oss fortsätta med att lägga till vattenstämplar.

## Lägga till textvattenstämplar

Textvattenstämplar är ett vanligt val när du vill lägga till textinformation i dina dokument. Så här kan du lägga till en textvattenstämpel med Aspose.Words för Java:

```java
// Skapa en dokumentinstans
Document doc = new Document("Document.docx");

// Definiera TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Ställ in vattenstämpelns text och alternativ
doc.getWatermark().setText("Test", options);

// Spara dokumentet med vattenstämpeln
doc.save("DocumentWithWatermark.docx");
```

## Lägga till bildvattenstämplar

Förutom textvattenstämplar kan du även lägga till bildvattenstämplar i dina dokument. Så här lägger du till en bildvattenstämpel:

```java
// Skapa en dokumentinstans
Document doc = new Document("Document.docx");

// Ladda bilden för vattenstämpeln
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Ställ in vattenstämpelns storlek och position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Lägg till vattenstämpeln i dokumentet
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Spara dokumentet med vattenstämpeln
doc.save("DocumentWithImageWatermark.docx");
```

## Anpassa vattenstämplar

Du kan anpassa vattenstämplar genom att justera deras utseende och placering. För textvattenstämplar kan du ändra teckensnitt, storlek, färg och layout. För bildvattenstämplar kan du ändra deras storlek och position enligt de tidigare exemplen.

## Ta bort vattenstämplar

För att ta bort vattenstämplar från ett dokument kan du använda följande kod:

```java
// Skapa en dokumentinstans
Document doc = new Document("DocumentWithWatermark.docx");

// Ta bort vattenstämpeln
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Spara dokumentet utan vattenstämpel
doc.save("DocumentWithoutWatermark.docx");
```


## Slutsats

den här handledningen har vi lärt oss hur man lägger till vattenstämplar i dokument med Aspose.Words för Java. Oavsett om du behöver lägga till text- eller bildvattenstämplar, tillhandahåller Aspose.Words verktygen för att anpassa och hantera dem effektivt. Du kan också ta bort vattenstämplar när de inte längre behövs, och se till att dina dokument är rena och professionella.

## FAQ's

### Hur kan jag ändra teckensnittet för en textvattenstämpel?

 För att ändra teckensnittet för en textvattenstämpel, ändra`setFontFamily` egendom i`TextWatermarkOptions`. Till exempel:

```java
options.setFontFamily("Times New Roman");
```

### Kan jag lägga till flera vattenstämplar i ett enda dokument?

 Ja, du kan lägga till flera vattenstämplar i ett dokument genom att skapa flera`Shape` objekt med olika inställningar och lägga till dem i dokumentet.

### Är det möjligt att rotera en vattenstämpel?

 Ja, du kan rotera en vattenstämpel genom att ställa in`setRotation` egendom i`Shape` objekt. Positiva värden roterar vattenstämpeln medurs och negativa värden roterar den moturs.

### Hur gör jag en vattenstämpel halvtransparent?

 För att göra en vattenstämpel halvtransparent, ställ in`setSemitransparent`egendom till`true` i`TextWatermarkOptions`.

### Kan jag lägga till vattenstämplar i specifika delar av ett dokument?

Ja, du kan lägga till vattenstämplar i specifika avsnitt av ett dokument genom att iterera genom avsnitten och lägga till vattenstämpeln i de önskade avsnitten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
