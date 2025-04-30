---
"description": "Lär dig hur du lägger till vattenstämplar i dokument i Aspose.Words för Java. Anpassa text- och bildvattenstämplar för professionellt utseende dokument."
"linktitle": "Använda vattenstämplar i dokument"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda vattenstämplar i dokument i Aspose.Words för Java"
"url": "/sv/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda vattenstämplar i dokument i Aspose.Words för Java


## Introduktion till att lägga till vattenstämplar i dokument i Aspose.Words för Java

I den här handledningen ska vi utforska hur man lägger till vattenstämplar i dokument med hjälp av Aspose.Words för Java API. Vattenstämplar är ett användbart sätt att märka dokument med text eller grafik för att indikera deras status, sekretess eller annan relevant information. Vi kommer att behandla både text- och bildvattenstämplar i den här guiden.

## Konfigurera Aspose.Words för Java

Innan vi börjar lägga till vattenstämplar i dokument måste vi konfigurera Aspose.Words för Java. Följ dessa steg för att komma igång:

1. Ladda ner Aspose.Words för Java från [här](https://releases.aspose.com/words/java/).
2. Lägg till Aspose.Words för Java-biblioteket i ditt Java-projekt.
3. Importera de nödvändiga klasserna i din Java-kod.

Nu när vi har konfigurerat biblioteket kan vi fortsätta med att lägga till vattenstämplar.

## Lägga till vattenstämplar i text

Textvattenmärken är ett vanligt val när du vill lägga till textinformation i dina dokument. Så här kan du lägga till ett textvattenmärke med Aspose.Words för Java:

```java
// Skapa en dokumentinstans
Document doc = new Document("Document.docx");

// Definiera alternativ för text/vattenstämpel
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Ställ in vattenstämpelns text och alternativ
doc.getWatermark().setText("Test", options);

// Spara dokumentet med vattenstämpeln
doc.save("DocumentWithWatermark.docx");
```

## Lägga till vattenstämplar i bilder

Förutom textvattenmärken kan du även lägga till bildvattenmärken i dina dokument. Så här lägger du till ett bildvattenmärke:

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

Du kan anpassa vattenstämplar genom att justera deras utseende och position. För textvattenstämplar kan du ändra teckensnitt, storlek, färg och layout. För bildvattenstämplar kan du ändra deras storlek och position som visas i föregående exempel.

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

// Spara dokumentet utan vattenstämpeln
doc.save("DocumentWithoutWatermark.docx");
```


## Slutsats

I den här handledningen har vi lärt oss hur man lägger till vattenstämplar i dokument med Aspose.Words för Java. Oavsett om du behöver lägga till text- eller bildvattenstämplar, tillhandahåller Aspose.Words verktygen för att anpassa och hantera dem effektivt. Du kan också ta bort vattenstämplar när de inte längre behövs, vilket säkerställer att dina dokument är rena och professionella.

## Vanliga frågor

### Hur kan jag ändra teckensnittet på en textvattenstämpel?

För att ändra teckensnittet på en textvattenstämpel, modifiera `setFontFamily` egendom i `TextWatermarkOptions`Till exempel:

```java
options.setFontFamily("Times New Roman");
```

### Kan jag lägga till flera vattenstämplar i ett enda dokument?

Ja, du kan lägga till flera vattenstämplar i ett dokument genom att skapa flera `Shape` objekt med olika inställningar och lägga till dem i dokumentet.

### Är det möjligt att rotera ett vattenmärke?

Ja, du kan rotera ett vattenmärke genom att ställa in `setRotation` egendom i `Shape` objekt. Positiva värden roterar vattenmärket medurs och negativa värden roterar det moturs.

### Hur kan jag göra ett vattenmärke halvtransparent?

För att göra ett vattenmärke halvtransparent, ställ in `setSemitransparent` egendom till `true` i `TextWatermarkOptions`.

### Kan jag lägga till vattenstämplar i specifika avsnitt i ett dokument?

Ja, du kan lägga till vattenstämplar i specifika avsnitt i ett dokument genom att gå igenom avsnitten och lägga till vattenstämpeln i önskade avsnitt.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}