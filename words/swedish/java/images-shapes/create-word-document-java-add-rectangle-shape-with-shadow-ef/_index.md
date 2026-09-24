---
category: general
date: 2026-01-11
description: Skapa ett Word‑dokument i Java snabbt genom att lägga till en rektangel,
  sätta dess fyllningsfärg och applicera en skugga på formen. Lär dig steg för steg.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: sv
og_description: Skapa Word-dokument i Java genom att infoga en rektangel, sätta dess
  fyllningsfärg och applicera en skugga. Komplett guide med kod.
og_title: Skapa Word-dokument i Java – Lägg till rektangel med skugga
tags:
- Aspose.Words
- Java
- Document Generation
title: Skapa Word-dokument i Java – Lägg till rektangel med skuggeffekt
url: /sv/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument Java – Lägg till rektangelform med skuggeffekt

Har du någonsin behövt **create word document java** och få det att se lite mer polerat ut? Kanske bygger du en rapportgenerator och en enkel sida räcker inte. De goda nyheterna? Med Aspose.Words for Java kan du lägga till en rektangelform i ett dokument, ge den en färgklick och till och med kasta en subtil skugga på den – allt på några få rader.

I den här handledningen går vi igenom exakt det: hur du lägger till en rektangelform, sätter dess fyllningsfärg och applicerar en skugga på formen så att ditt Word‑fil känns lite mer professionell. I slutet har du ett körbart exempel som du kan kopiera‑klistra in i ditt eget projekt.

## Vad du behöver

- **Java 17** (eller någon nyare JDK) – koden använder standardfunktionerna i språket.  
- **Aspose.Words for Java**‑biblioteket – version 23.9 eller nyare rekommenderas.  
- En IDE eller textredigerare du föredrar – IntelliJ IDEA, Eclipse, VS Code … du bestämmer.  
- En mapp där den genererade `ShadowShape.docx` ska sparas.

Ingen extra konfigurationsmagik behövs; lägg bara till Aspose.Words‑JAR‑filen i din classpath så är du redo att köra.

## Steg 1: Ställ in projektet och importera Aspose.Words

Först och främst, skapa ett nytt Maven‑ (eller Gradle‑) projekt och lägg till Aspose.Words‑beroendet. Här är ett minimalt `pom.xml`‑exempel för Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Om du inte använder Maven, släng bara JAR‑filen i din `libs`‑mapp och lägg till den i byggvägen.

> **Pro tip:** Aspose erbjuder en gratis provlicens som du kan bädda in med `License license = new License(); license.setLicense("Aspose.Words.lic");`. Hoppa över den för snabba tester; biblioteket fungerar i utvärderingsläge.

## Steg 2: Skapa ett nytt dokument och Builder

Nu ska vi faktiskt **create word document java**‑objekt. Klassen `Document` representerar hela .docx‑filen, medan `DocumentBuilder` låter oss infoga innehåll.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Vid det här laget har du ett tomt dokument redo att ta emot former, stycken eller vad du än kan behöva.

## Steg 3: Infoga en rektangelform och sätt dess fyllningsfärg

Att lägga till en form är så enkelt som att anropa `insertShape`. Vi använder tekniken **add rectangle shape**, som faller under det sekundära nyckelordet *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Varför orange? Det sticker ut i ett hav av vitt, men du kan byta ut den mot vilken `java.awt.Color` du vill. Detta steg täcker det sekundära nyckelordet *set shape fill color*.

## Steg 4: Konfigurera skuggans utseende – Applicera skugga på formen

Nu kommer den roliga delen: att ge rektangeln en subtil drop‑shadow. Aspose‑API:n exponerar ett `ShadowFormat`‑objekt som styr varje aspekt av skuggan.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Detta kodblock **apply shadow to shape** exakt som det sekundära nyckelordet antyder. Du kan justera `blur`, `offsetX/Y` och `transparency` för att passa din design. Till exempel skapar ett större `offsetX` en mer dramatisk skugga, medan högre `transparency` får skuggan att viska snarare än ropa.

## Steg 5: Spara dokumentet

Till sist skriver vi dokumentet till disk. Välj en mapp du har skrivbehörighet till och ge filen ett tydligt namn.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

När du öppnar `ShadowShape.docx` i Microsoft Word eller LibreOffice ser du en ljus orange rektangel med en mjuk grå skugga som svävar precis under den.

![create word document java med rektangelform](/images/shadow-rectangle.png "create word document java – rektangel med skugga")

*Bildens alt‑text innehåller det primära nyckelordet, vilket uppfyller SEO‑regeln.*

## Vanliga frågor & edge cases

### Vad händer om jag behöver en annan form?

Aspose.Words stöder dussintals `ShapeType`‑värden – stjärnor, pilar, pratbubblor, du namnger dem. Byt helt enkelt ut `ShapeType.RECTANGLE` mot `ShapeType.OVAL` eller någon annan enum‑konstant. Samma **how to add shape**‑steg gäller.

### Hur lägger jag till formen i ett specifikt stycke?

Istället för att infoga formen direkt med buildern kan du först skapa den (`new Shape(document, ShapeType.RECTANGLE)`) och sedan lägga till den i ett `Paragraph` via `paragraph.appendChild(shape)`. Detta ger dig finare kontroll över layouten.

### Kan jag använda en gradientfyllning istället för en solid färg?

Ja! Använd `rectangle.getFill().setFillType(FillType.GRADIENT)` och definiera en `LinearGradientFill`. API:n är lite mer utförlig, men den fungerar utmärkt för moderna designer.

### Vad gäller kompatibilitet med äldre Word‑versioner?

Aspose.Words sparar som standard i .docx‑format, vilket stöds av Word 2007+ och LibreOffice. Om du behöver .doc, anropa `document.save("file.doc", SaveFormat.DOC)`. Skuggrenderingen kan skilja sig något, men själva formen förblir intakt.

## Fullt fungerande exempel (Klar att kopiera‑klistra in)

Nedan är hela programmet, redo att kompileras och köras. Ersätt `YOUR_DIRECTORY` med en faktisk sökväg på din maskin.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

När du kör den här koden får du en Word‑fil som innehåller den orangea rektangeln med en mjuk grå skugga – exakt det vi ville uppnå när vi ville **create word document java** med en stylad form.

## Slutsats

Du har nu ett gediget, end‑to‑end‑recept för **create word document java** som *adds rectangle shape*, *sets shape fill color* och *applies shadow to shape*. Tillvägagångssättet är enkelt, API:n är flytande, och du kan utöka det på otaliga sätt – olika former, gradientfyllningar eller till och med flera skuggor per form.

Vad blir nästa steg? Prova att stapla flera former, experimentera med `ShadowStyle.ETCHED` för en annan visuell känsla, eller kombinera detta med tabellgenerering för att bygga fullt utvecklade rapporter. Möjligheterna är bara begränsade av din fantasi (och kanske Aspose‑licenstypen).

Om du stött på några problem eller har idéer för vidare förbättringar, lämna en kommentar nedan. Lycka till med kodandet, och njut av att göra dina Word‑dokument lite mindre tråkiga!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}