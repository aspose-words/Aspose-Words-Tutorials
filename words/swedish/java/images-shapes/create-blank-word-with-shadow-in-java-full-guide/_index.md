---
category: general
date: 2026-05-04
description: Skapa ett tomt Word‑dokument i Java och lär dig hur du ställer in skuggfärg,
  oskärpa och förskjutning för former – snabb handledning.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: sv
og_description: Skapa ett tomt Word‑dokument i Java och lär dig hur du ställer in
  skuggfärg, oskärpa och förskjutning för former. Följ den här steg‑för‑steg‑handledningen.
og_title: Skapa ett tomt ord med skugga i Java – Fullständig guide
tags:
- Aspose.Words
- Java
- Document Automation
title: Skapa ett tomt ord med skugga i Java – Fullständig guide
url: /sv/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tomt Word‑dokument med skugga i Java – Fullständig guide

Har du någonsin behövt **create blank word**‑filer från kod och få dem att se lite snyggare ut? Du är inte ensam. I många rapporterings‑ eller mallgenereringsprojekt är det första du gör att skapa ett tomt Word‑dokument, och sedan lägga till en form med en skugga för att ge det en polerad känsla.  

I den här handledningen går vi igenom exakt det — hur man skapar ett tomt Word‑dokument med Aspose.Words for Java, **how to add shadow** till en form, samt detaljerna för **set shadow color**, **how to set blur** och **how to set offset**. I slutet har du en färdig `.docx`‑fil som visar en rektangel med en fint oskarp, halvtransparent röd skugga.

## Vad du behöver

- **Aspose.Words for Java** (valfri nyare version; koden fungerar med 23.9+)
- JDK 8 eller nyare
- En IDE eller enkel textredigerare plus en terminal
- Grundläggande Java‑kunskaper — inget avancerat, bara förmågan att köra en `main`‑metod

Ingen extra Maven‑ eller Gradle‑konfiguration krävs för demonstrationen; släpp bara Aspose‑JAR‑filen på din classpath så är du klar.

---

![exempel på tomt Word-dokument med skugga](image-placeholder.png){: .center alt="exempel på tomt Word-dokument med skugga"}

## Skapa tomt Word‑dokument – Initiering av dokumentet

Det första steget är att skapa en helt ny, tom Word‑fil. Tänk på den som en ren duk där du senare kan rita former, tabeller eller text.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Varför detta är viktigt:** `Document` representerar hela `.docx`‑paketet. Genom att skapa den med standardkonstruktorn utför du i praktiken **create blank word** – det finns inget innehåll, inga sektioner, bara filstrukturen redo att fyllas i.

## Hur man lägger till skugga på en form

Nu när vi har ett rent dokument, låt oss infoga en rektangel som ska hålla vår skugga. Här börjar den visuella magin.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Proffstips:** Anropet `insertShape` lägger automatiskt till formen i det aktuella stycket, så du behöver inte hantera positionering manuellt om du inte vill ha absolut placering.

## Ställ in skuggfärg – få skuggan att sticka ut

En skugga utan färg är bara en grå oskärpa, vilket kan se platt ut. Genom att sätta skuggans färg kan du matcha varumärket eller helt enkelt få den att sticka ut.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **Vad som händer:** `ShadowFormat` styr varje visuellt aspekt av skuggan. Att aktivera `setVisible(true)` slår på effekten, och `setColor` låter dig välja vilken `java.awt.Color` som helst. I vårt exempel valde vi röd för att tydligt demonstrera **set shadow color**.

## Hur man ställer in oskärpa för en subtil effekt

En skarp, hårdkantad skugga kan se hård ut. Genom att lägga till oskärpa mjukas kanterna upp, vilket ger ett mer naturligt utseende.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Varför oskärpa är viktigt:** Värdet för `setBlur` mäts i punkter. Ett värde på `5.0` skapar en mjuk diffusion; öka det för en mer molnig skugga, minska för en skarpare kontur.

## Hur man ställer in offset – placering av skuggan

Offset bestämmer var skuggan hamnar i förhållande till formen. Tänk på dem som X‑ och Y‑förskjutningar.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Förklaring av offset:** Positiv X flyttar skuggan åt höger, positiv Y flyttar den nedåt. Lek med negativa tal om du vill att skuggan ska visas på motsatt sida.

## Finjustering av transparens

Om du vill att skuggan ska vara mindre dominerande, justera dess transparens. Detta steg är inte ett nyckelordskrav men kompletterar den visuella kontrollen.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Spara dokumentet – se resultatet

Till sist skriver du dokumentet till disk. Du får en `.docx` som du kan öppna i Word, LibreOffice eller någon annan visare som stödjer formatet.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **Vad du bör se:** Öppna `ShadowShape.docx`. En enda sida visar en 150 × 80 pt rektangel med en röd, lätt oskarp skugga som är förskjuten 8 pt nedåt och åt höger. Skuggan är 30 % transparent, så rektangeln förblir tydligt synlig.

---

## Vanliga frågor och specialfall

### Vad händer om jag behöver en annan form?

Byt ut `ShapeType.RECTANGLE` mot något annat enum‑värde (`ELLIPSE`, `CLOUD`, `CALLOUT` osv.). Skugginställningarna fungerar identiskt för alla former.

### Kan jag applicera samma skugga på flera former utan att upprepa kod?

Absolut. Skapa en hjälpfunktion:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Anropa sedan `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` för vilken form som helst.

### Fungerar detta med äldre Aspose‑versioner?

`ShadowFormat`‑API:et har varit stabilt sedan version 19.8, så du bör klara dig med de flesta nyare versioner. Om du använder en mycket gammal build, kontrollera Javadoc för `ShadowFormat` för att verifiera metodnamnen.

### Hur exporterar man till PDF samtidigt som skuggan behålls?

Anropa bara `document.save("output.pdf");` efter att formen har skapats. Aspose.Words renderar skuggor korrekt i PDF, och bevarar oskärpa och transparens.

## Sammanfattning – skapa tomt Word‑dokument med en anpassad skugga

Vi började med att **create blank word** med `new Document()`, sedan infogade en rektangel, **set shadow color**, lärde oss **how to add shadow**, justerade **how to set blur**, och slutligen ändrade **how to set offset** för att placera den exakt rätt. Den kompletta, körbara koden finns i kodsnutten ovan, och den resulterande filen visar effekten tydligt.

## Vad blir nästa steg?

- **Experimentera med andra skuggegenskaper** som `ShadowFormat.setStyle(ShadowStyle.OUTER)` för olika visuella stilar.
- **Kombinera flera former** var och en med sin egen skugga för att bygga komplexa diagram.
- **Lägg till text i formen** med `builder.insertHtml("<b>Hello</b>")` innan du infogar formen, och tillämpa sedan samma skugglogik.
- **Utforska andra formateringsalternativ** som linjestil, fyllningsfärg eller gradientfyllningar — Aspose.Words erbjuder ett rikt API för alla dessa.

Känn dig fri att justera blur‑radien, offset eller färger tills skuggan känns helt rätt för ditt dokuments designspråk. Lycka till med kodandet, och må dina genererade Word‑filer alltid se lite mer polerade ut!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}