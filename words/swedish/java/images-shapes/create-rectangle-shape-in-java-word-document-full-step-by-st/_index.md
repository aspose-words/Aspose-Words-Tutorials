---
category: general
date: 2026-05-26
description: Skapa en rektangel i ett Java Word‑dokument och applicera skuggeffekt.
  Lär dig hur du lägger till skugga på formen, ställer in skuggavstånd och sparar
  filen.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: sv
og_description: Skapa en rektangelform i ett Java Word‑dokument, applicera skuggeffekt,
  lägg till formskugga och ställ in skuggavståndet med Aspose.Words.
og_title: Skapa rektangelform i Java Word-dokument – Komplett guide
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Skapa rektangelform i Java Word-dokument – Fullständig steg‑för‑steg‑guide
url: /sv/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Java Word-dokument – Full steg‑för‑steg‑guide

Har du någonsin behövt **create rectangle shape** i ett Java Word-dokument men varit osäker på var du ska börja? Du är inte ensam—många utvecklare stöter på detta problem när de genererar rapporter eller fakturor programmässigt. I den här handledningen går vi igenom exakt hur du **create rectangle shape**, applicerar en polerad skugga och finjusterar skuggavståndet så resultatet ser professionellt ut.

Vi kommer att använda Aspose.Words for Java, ett robust bibliotek som låter dig manipulera Word-filer utan att behöva Microsoft Office installerat. I slutet av den här guiden kommer du att kunna **create word document java**-projekt som **add shape shadow**, **apply shadow effect** och **set shadow distance** med bara några rader kod.

---

## Vad du kommer att bygga

- En ny `.docx`-fil som innehåller en cyan rektangel.
- En realistisk drop‑shadow som är suddig, vinklad och delvis transparent.
- Full kontroll över skuggans avstånd från formen.
- En färdig‑att‑köra Java-klass som du kan släppa in i vilket Maven- eller Gradle‑projekt som helst.

Inga externa verktyg, inga manuella UI‑steg—bara ren kod.

## Förutsättningar

- Java 8 eller nyare (koden fungerar på Java 11, Java 17 osv.).
- Aspose.Words for Java‑biblioteket (tillgängligt via Maven Central).
- En IDE eller textredigerare du föredrar (IntelliJ IDEA, Eclipse, VS Code…).
- Grundläggande kunskap om Java‑syntax.

Om du aldrig har lagt till ett Maven‑beroende tidigare, här är det snabba kodsnutten:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Nu, låt oss dyka in.

## Steg 1: Skapa rektangelform i ett Word-dokument

Det första vi behöver är ett tomt dokument och en `DocumentBuilder`. Tänk på buildern som en penna som skriver i dokumentet. När vi har den kan vi **create rectangle shape** med ett enda metodanrop.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Varför detta är viktigt:** `insertShape`‑metoden skapar inte bara geometrin utan lägger också till formen i dokumentets interna samling, så du kan omedelbart börja styla den.

## Steg 2: Applicera skuggeffekt på formen

Nu när rektangeln finns på sidan kommer vi att **apply shadow effect**. Skuggor ger djup, vilket får formen att kännas som om den lyfts från sidan—en subtil UI‑förbättring som kan öka läsbarheten i rapporter.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Proffstips:** En oskärpa på `5.0` ser naturlig ut för de flesta skärm‑visade dokument. Om du skriver ut kan du vilja ha ett något lägre värde för att undvika ett suddigt utseende.

## Steg 3: Ställ in skuggavstånd – finjustera placeringen

Skuggor handlar inte bara om oskärpa; de behöver också rätt förskjutning. Här är vi **set shadow distance**. Ett avstånd på `7.0` punkter skapar en måttlig förskjutning som är märkbar men inte överväldigande.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **Vad händer om du behöver en större förskjutning?** Öka värdet; minska det för ett tajtare utseende. Kom ihåg att avståndet samverkar med vinkeln för att placera skuggan korrekt.

## Steg 4: Spara dokumentet – bevara ditt arbete

Till sist skriver vi dokumentet till disk. Ändra sökvägen till var du vill att filen ska ligga.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

När klassen körs skapas en `shadow.docx`‑fil som, när den öppnas i Microsoft Word eller LibreOffice, visar en cyan rektangel med en mjuk grå skugga vinklad 45° och förskjuten med 7 punkter.

## Fullt fungerande exempel

Nedan är den kompletta, kopiera‑och‑klistra‑klara koden. Den innehåller alla imports, kommentarer och det sista `save`‑anropet.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Förväntat resultat:** Öppna `shadow.docx` → du kommer att se en cyan rektangel centrerad på första sidan, som kastar en subtil grå skugga som är lite förskjuten mot nedre‑höger. Skuggans oskärpa och transparens får den att se ut som naturligt ljus.

## Vanliga frågor & specialfall

### “Kan jag använda en annan form?”

Absolut. Byt ut `ShapeType.RECTANGLE` mot `ShapeType.OVAL`, `ShapeType.LINE` eller någon annan stödd enum. Resten av skuggkoden förblir densamma.

### “Vad händer om jag behöver flera skuggor?”

Aspose.Words stödjer bara en enda skugga per form. För att simulera flera skuggor, duplicera formen, förskjut varje kopia och justera transparensen.

### “Är skuggan synlig i LibreOffice?”

Ja—Aspose.Words skriver standard‑OOXML, vilket LibreOffice tolkar korrekt. Skuggan kan se något annorlunda ut på grund av renderingsmotorer, men effekten kvarstår.

### “Hur ändrar jag skuggans färg så den matchar mitt varumärke?”

Byt bara ut `java.awt.Color.GRAY` mot någon `java.awt.Color` du föredrar, till exempel `new java.awt.Color(0, 120, 215)` för en företagsblå.

## Bildillustration

![create rectangle shape i Java Word-dokument](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** illustration som visar en cyan rektangel med en grå drop‑shadow i ett Word‑dokument.

## Sammanfattning & nästa steg

Vi har gått igenom hur man **create rectangle shape**, **apply shadow effect**, **add shape shadow** och **set shadow distance** med Aspose.Words for Java. Koden är självständig, körs på vilken modern JDK som helst och producerar en polerad `.docx`‑fil klar för distribution.

Vill du gå längre? Prova:

- Lägg till text inuti rektangeln med `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- Skapa en tabell med former för att bygga ett diagram.
- Exportera dokumentet till PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

Var och en av dessa bygger på samma grunder som vi just utforskade, så du kommer att känna dig bekväm med att utöka exemplet.

## Slutliga tankar

Att behärska **create word document java**‑uppgifter som formning och skuggning ger dig ett stort försprång när du automatiserar rapporter, kontrakt eller marknadsföringsmaterial. Tillvägagångssättet som visas här är rent, underhållbart och—framför allt—lätt att justera för vilken visuell stil du än behöver.

Kör koden, justera oskärpan, vinkeln och avståndet, och se hur dina dokument förvandlas från tråkiga till polerade. Om du stöter på ett problem, lämna en kommentar nedan; jag hjälper gärna till.

Lycka till med kodandet!

## Relaterade handledningar

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create PDF from Word with Barcode Generation – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}