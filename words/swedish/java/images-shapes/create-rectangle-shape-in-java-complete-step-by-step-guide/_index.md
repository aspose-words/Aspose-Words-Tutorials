---
category: general
date: 2026-07-03
description: Skapa en rektangel i Java och lär dig hur du lägger till skugga på formen,
  applicerar skuggeffekten, ställer in formens transparens och snabbt skapar ett tomt
  dokument.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: sv
og_description: Skapa rektangelform i Java med skugga, transparens och ett tomt dokument.
  Följ den här guiden för att behärska formhantering.
og_title: Skapa rektangel i Java – Fullständig programmeringshandledning
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Skapa rektangelform i Java – Komplett steg‑för‑steg‑guide
url: /sv/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Java – Komplett steg‑för‑steg‑guide

Har du någonsin undrat hur man **skapar rektangelform** i ett Word‑dokument med Java? Du är inte ensam—utvecklare behöver ofta ett snabbt sätt att lägga till geometrisk grafik, och sedan ge dem en subtil skugga så layouten känns mer polerad. I den här handledningen går vi igenom hela processen: från att **skapa tomt dokument** till **lägga till skugga på form**, **tillämpa skuggeffekt**, och till och med **ange formens transparens** för den professionella looken.

Kodsnutten nedan är ett fullt fungerande exempel som du kan kopiera‑klistra in i ditt projekt. Ingen extern dokumentation behövs—följ bara stegen, förstå “varför”, och du kommer att generera skuggade rektanglar på några sekunder.

## Vad du kommer att lära dig

- Hur man **skapar rektangelform** programatiskt med Aspose.Words för Java.
- De exakta anropen som behövs för att **lägga till skugga på form** och konfigurera dess visuella egenskaper.
- Sätt att **tillämpa skuggeffekt** och justera parametrar som offset, oskärpe‑radie och färg.
- Tekniker för att **ange formens transparens** för ett mer subtilt utseende.
- Hur man **skapar tomt dokument**, infogar formen och sparar resultatet.

> **Pro tip:** Alla dessa åtgärder utförs på en enda `Document`‑instans, vilket betyder att du kan kedja dem utan att oroa dig för mellansteg med fil‑I/O.

## Förutsättningar

- Java 17 (eller någon nyare JDK) installerad.
- Aspose.Words för Java‑biblioteket tillagt i ditt projekt (Maven‑koordinater: `com.aspose:aspose-words:23.12`).
- En Java‑IDE eller enkel textredigerare—inget avancerat, bara en plats att kompilera och köra.

Om du saknar någon av dessa, hämta JDK:n från Oracle och lägg till Aspose‑beroendet via Maven eller Gradle. När det är gjort är du redo att köra.

## Steg 1: **Skapa tomt dokument** – duken för allt

Det allra första du behöver är ett tomt `Document`‑objekt. Tänk på det som ett färskt papper; utan det finns ingen plats att lägga din rektangel.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Varför börja med ett tomt dokument? För varje form lever den i en `Section`, och ett nyinstansierat `Document` innehåller redan en standardsektion med en kropp redo att ta emot noder. Att hoppa över detta steg skulle tvinga dig att manuellt skapa sektioner senare, vilket lägger till onödig komplexitet.

## Steg 2: **Skapa rektangelform** och definiera dess storlek

Nu när vi har en duk, låt oss **skapa rektangelform**. `Shape`‑klassen tar dokumentreferensen och en `ShapeType`. Här väljer vi `RECTANGLE` och sätter bredd/höjd i punkter (1 pt ≈ 1/72 tum).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Varför sätta `WrapType.INLINE`? Inline‑omslag får formen att bete sig som ett tecken i stycket, vilket säkerställer att den flyttar med omgivande text. Om du behöver flytande beteende, byt till `WrapType.SQUARE` eller `WrapType.TOP_BOTTOM`.

## Steg 3: **Tillämpa skuggeffekt** – ge rektangeln djup

En platt rektangel ser… ja, platt ut. Att lägga till en skugga får den att sticka ut. Vi **tillämpa skuggeffekt** genom att skapa en `ShadowEffect`‑instans och sedan justera dess visuella egenskaper.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Låt oss gå igenom detta lite:

- **Färg** – `Color.getGray(0.5)` ger en 50 % grå, som är neutral och fungerar på de flesta bakgrunder.
- **OffsetX/Y** – Positiva värden skjuter skuggan åt höger och ner; negativa värden skulle flytta den åt vänster/upp.
- **BlurRadius** – Större värden skapar en mjukare, mer diffust skugga.
- **Transparens** – Värden från `0` (opak) till `1` (helt transparent). Här valde vi `0.3` för en subtil effekt.

## Steg 4: **Lägg till skugga på form** – bind effekten

Att skapa effekten räcker inte; vi måste **lägga till skugga på form** genom att tilldela `ShadowEffect`‑objektet till rektangeln.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Bakom kulisserna uppdaterar detta anrop den underliggande OpenXML‑markupen (`<w:shdw>`) som Word använder för att rendera skuggor. Om du inspekterar den sparade `.docx`‑filen ser du ett `<w:effect>`‑element fyllt med de parametrar vi satte.

## Steg 5: **Ange formens transparens** – valfritt men ofta användbart

Ibland vill du att själva rektangeln ska vara halvtransparent så att bakgrundstext syns igenom. `Shape`‑klassen exponerar `setFillColor` och `setFillTransparency`. Här är ett snabbt exempel som gör rektangeln 40 % transparent:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Varför skulle du göra detta? Föreställ dig ett vattenstämpel eller en markerad call‑out där det underliggande innehållet måste förbli läsbart. Justera transparensvärdet så att det passar ditt designspråk.

## Steg 6: Infoga formen i dokumentet

Vi har byggt rektangeln, lagt till en skugga och (valfritt) satt dess transparens. Det sista steget är att **lägga till formen i dokumentets första sektion**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Att lägga till formen i kroppen placerar den i slutet av det första stycket. Om du behöver en specifik infogningspunkt, hämta mål‑`Paragraph` och använd `insertBefore` eller `insertAfter`.

## Steg 7: Spara dokumentet – se resultatet

Allt detta arbete kulminerar i ett enda `save`‑anrop. Välj en sökväg som passar din miljö.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Öppna den resulterande `ShadowShape.docx` i Microsoft Word eller LibreOffice, så ser du en skarp rektangel med en mjuk grå skugga, något transparent om du behöll det valfria steget. Visualiseringen matchar de parametrar vi definierade programatiskt.

![skapa rektangelform med skugga i ett Word‑dokument](https://example.com/images/rectangle-shadow.png "skapa rektangelform med skugga")

*Bild alt‑text:* **skapa rektangelform med skugga** – visuell representation av det slutgiltiga resultatet.

## Vanliga frågor & kantfall

### Vad händer om jag vill ha en annan skuggfärg?

Byt helt enkelt `setColor`‑anropet:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Kom ihåg att alltför livliga skuggor kan se oprofessionella ut; subtila toner fungerar oftast bäst.

### Kan jag tillämpa samma skugga på flera former?

Ja. Skapa en `ShadowEffect`‑instans, konfigurera den och återanvänd den:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Undvik bara att mutera `ShadowEffect` efter att du har fäst den på andra former, såvida du inte avser att uppdatera dem alla.

### Hur ändrar jag skuggens oskärpa dynamiskt?

Exponera en UI‑reglage som mappar till `setBlurRadius`. Värden mellan `2` och `12` är typiska; större tal ger en “glöd” snarare än en skarp skugga.

### Vad händer om jag behöver att formen flyter istället för att vara inline?

Byt omslagstypen:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Flytande former ger dig mer layoutfrihet men kräver extra placeringslogik.

## Fullständigt fungerande exempel

Nedan är det kompletta, copy‑paste‑klara programmet som innehåller alla steg vi diskuterat. Kör det som ett vanligt Java‑program.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Förväntat resultat:** När du öppnar `ShadowShape.docx` ser du en vit rektangel, 200 × 100 pt, centrerad i det första stycket, med en medium‑grå skugga förskjuten 5 pt, oskarp med radie 8 och 30 % transparent. Rektangeln själv är 40 % transparent, så eventuell underliggande text kan skymtas igenom.

## Avslutning

Vi har precis **skapat rektangelform** från grunden, **lagt till skugga på form**, **tillämpat skuggeffekt**, och till och med **ange formens transparens**—allt medan **skapa tomt dokument** låg som grund. Metoden är enkel, bygger på Aspose.Words’ flytande API och kan utökas till cirklar, stjärnor eller anpassade polygoner.

Vad blir nästa steg på din färdplan? Prova att byta `ShapeType.RECTANGLE` mot `ShapeType.OVAL` för att generera skuggade cirklar, eller experimentera med gradientfyllningar för

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Skapa Word‑dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa tomt Word‑dokument med skuggad rektangelform – steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow‑handledning – Lägg till en skugga på Word‑form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}