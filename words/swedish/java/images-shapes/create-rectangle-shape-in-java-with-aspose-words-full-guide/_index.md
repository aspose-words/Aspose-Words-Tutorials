---
category: general
date: 2026-07-06
description: Skapa en rektangel i Java med Aspose.Words – lär dig hur du lägger till
  skugga på formen, ställer in formens transparens och sparar dokumentet som PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: sv
og_description: Skapa en rektangel i Java med Aspose.Words. Den här guiden visar hur
  du lägger till skugga på formen, ställer in formens transparens och sparar dokumentet
  som PDF.
og_title: Skapa rektangel i Java – Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Skapa rektangelform i Java med Aspose.Words – Fullständig guide
url: /sv/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Java med Aspose.Words – Fullständig guide

Har du någonsin undrat hur man **skapar rektangelform** i Java utan att kämpa med lågnivå‑ritnings‑API:er? Du är inte ensam. Många utvecklare behöver ett snabbt, pålitligt sätt att lägga in en rektangel i ett Word‑dokument, ge den en subtil skugga, justera dess transparens och sedan leverera resultatet som en PDF.  

I den här handledningen går vi igenom exakt det—steg för steg, med komplett, körbar kod. I slutet kommer du att veta **hur man lägger till skugga** på en form, hur man **ställer in formens transparens**, och hur man **sparar dokument som PDF** med Aspose.Words för Java. Inga onödiga detaljer, bara praktisk vägledning som du kan kopiera‑klistra in i ditt projekt idag.

## Vad du kommer att lära dig

- Den minsta konfiguration som krävs för att arbeta med Aspose.Words i ett Java‑projekt.  
- Hur man **skapar rektangelform** programatiskt.  
- De exakta anropen som behövs för att **lägga till skugga på formen** och justera dess suddighet, förskjutning och opacitet.  
- Sätt att **ställa in formens transparens** så att rektangeln blandas snyggt med omgivande innehåll.  
- Den enklaste metoden för att **spara dokument som PDF** utan extra konverteringssteg.  

Om du är bekväm med grundläggande Java och har en Maven‑ eller Gradle‑byggnad, är du redo att köra.

## Förutsättningar

- Java 8 eller nyare.  
- Aspose.Words for Java 23.x (eller den senaste versionen vid läsningstillfället).  
- En IDE eller kommandorads‑byggverktyg (IntelliJ, Eclipse, Maven, Gradle — välj det du föredrar).  

> **Pro tip:** Aspose erbjuder en gratis temporär licens för utvärdering. Hämta den från ditt kontopanel och placera `license.xml`‑filen i din classpath; annars kommer du att se ett vattenmärke i PDF‑filen.

---

## Steg 1: **Skapa rektangelform** med Aspose.Words

Det första vi behöver är ett tomt `Document` och en `DocumentBuilder`. Buildern är arbetsmaskinen som låter oss infoga former direkt i dokumentets flöde.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Varför detta är viktigt:** `ShapeType.RECTANGLE` talar om för Aspose att vi vill ha en perfekt rektangel. Bredd och höjd uttrycks i punkter (1 pt ≈ 1/72 in), vilket ger dig fin‑granulär kontroll över den slutliga storleken.

---

## Steg 2: **Lägg till skugga på formen**

Nu när vi har en rektangel, låt oss ge den en subtil drop‑shadow. Objektet `ShadowFormat` exponerar allt vi behöver — suddighetsradie, X/Y‑förskjutning och även transparens.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Varför detta är viktigt:** En skugga utan suddighet ser ut som en hård linje, vilket sällan är vad designers vill ha. Anropet `setBlur` mjukar upp kanterna, medan `setTransparency` låter skuggan tona in i bakgrunden. Justera dessa värden för att matcha dina UI‑riktlinjer.

---

## Steg 3: **Ställ in formens transparens**

Ibland behöver du att själva rektangeln är halvtransparent — kanske för att överlagra en logotyp eller vattenstämpel. Aspose gör detta med en enda rad kod.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Varför detta är viktigt:** Transparens kan vara en livräddare när du lagerlägger former. Observera att skuggans egen transparens är oberoende, så du kan ha en svag form med en mörkare skugga om det passar din design.

---

## Steg 4: **Spara dokument som PDF**

Allt visuellt arbete är klart; sista steget är att persistera dokumentet. Aspose.Words kan skriva direkt till PDF, vilket eliminerar behovet av ett separat konverteringsbibliotek.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Varför detta är viktigt:** Genom att ange `SaveFormat.PDF` hanterar biblioteket inbäddning av teckensnitt, bildkomprimering och PDF/A‑kompatibilitet bakom kulisserna. Den resulterande filen är klar för distribution, utskrift eller arkivering.

---

## Fullt fungerande exempel

Sätter vi ihop allt får du den kompletta, körklara klassen. Kopiera‑klistra in, justera utdatamappen, så har du en PDF med en rektangel som kastar en realistisk skugga.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Förväntat resultat:** När du öppnar `RectangleWithShadow.pdf` ser du en ljusgrå rektangel centrerad på första sidan, försiktigt lyft från sidan av en mjuk, halvtransparent skugga. Formen själv är 20 % transparent, vilket låter eventuell underliggande text (om du lagt till någon) skymta igenom.

---

## Vanliga frågor & kantfall

### 1️⃣ Vad händer om jag behöver en större rektangel?

Ändra bara bredd‑ och höjdpunkterna i `insertShape`. Kom ihåg att 72 pt = 1 in, så `400.0, 200.0` ger dig en rektangel på 5,5 × 2,8 tum.

### 2️⃣ Kan jag använda en annan färg för skuggan?

Absolut. Klassen `ShadowFormat` exponerar också `setColor(java.awt.Color)`. För en subtil grå skugga, prova `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ Fungerar `save document as pdf` på alla plattformar?

Ja. Aspose.Words for Java är plattformsoberoende; samma kod körs på Windows, macOS och Linux så länge du har en kompatibel JRE.

### 4️⃣ Hur tar jag bort skuggan senare?

Anropa `rect.getShadowFormat().clear();` eller sätt egenskapen `Visible` till `false` (`shadow.setVisible(false);`).

### 5️⃣ Vad sägs om DPI och bildkvalitet?

När du sparar till PDF använder Aspose automatiskt 300 DPI för vektorgrafik som former, så du får skarpa resultat oavsett zoomnivå.

---

## Pro‑tips & bästa praxis

- **Batch‑behandling:** Om du behöver generera dussintals PDF‑filer, återanvänd en enda `Document`‑instans och rensa bara dess sektioner mellan iterationer för att minska GC‑trycket.  
- **Licensiering:** Placera `License license = new License(); license.setLicense("license.xml");` i början av `main` för att undvika utvärderingsvattenmärket.  
- **Prestanda:** Skuggrendering är billig för enkla former, men komplexa banor kan sakta ner PDF‑genereringen. Profilera om du bearbetar stora batcher.  
- **Testning:** Använd Aspose’s `Document.save(..., SaveFormat.DOCX)` först för att verifiera att formen visas korrekt i Word innan du konverterar till PDF.

---

## Slutsats

Du vet nu hur du **skapar rektangelform** i Java med Aspose.Words, **lägger till skugga på formen**, **ställer in formens transparens**, och slutligen **sparar dokument som PDF**. Koden är självständig, fungerar med det senaste Aspose‑biblioteket och demonstrerar de viktigaste API‑anropen du kommer att behöva för de flesta dokument‑automatiseringsscenarier.

Redo för nästa utmaning? Prova att byta ut rektangeln mot en ellips, experimentera med gradientfyllningar, eller utforska hur du **lägger till skugga** på textramar. Samma principer gäller, och Aspose‑API‑et får det att kännas som en barnlek.

Lycka till med kodandet, och tveka inte att lämna en kommentar om du stöter på problem!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hur man sparar dokument som pdf med Aspose.Words för Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}