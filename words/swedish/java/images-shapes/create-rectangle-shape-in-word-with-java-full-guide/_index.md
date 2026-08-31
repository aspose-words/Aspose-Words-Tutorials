---
category: general
date: 2026-02-10
description: Skapa en rektangulär form i ett Word‑dokument med Aspose.Words för Java.
  Lär dig hur du ställer in skuggfärg, hur du lägger till skugga och hur du skapar
  ett Word‑dokument programatiskt.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: sv
og_description: Skapa en rektangelform i ett Word‑dokument med Aspose.Words för Java.
  Följ den här steg‑för‑steg‑handledningen för att ställa in skuggfärg, lägga till
  skugga och skapa ett Word‑dokument.
og_title: Skapa rektangel i Word med Java – Fullständig guide
tags:
- Aspose.Words
- Java
- Document Automation
title: Skapa rektangelform i Word med Java – Fullständig guide
url: /sv/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Word med Java – Fullständig guide

Har du någonsin behövt **skapa rektangelform** i ett Word‑dokument men inte vetat var du ska börja? Du är inte ensam—många utvecklare stöter på samma hinder när de först försöker rita grafik i Word programatiskt. Den goda nyheten? Med Aspose.Words för Java kan du enkelt lägga till en rektangel på en sida, ge den en fin skugga och spara filen på några sekunder. I den här handledningen går vi igenom exakt **hur man lägger till skugga**, **sätter skuggfärg** och **skapar Word‑dokument** från grunden.  

Vi täcker allt du behöver: de nödvändiga biblioteken, varje kodrad, varför vissa inställningar är viktiga, och några knep du kanske inte hittar i den officiella dokumentationen. I slutet har du ett färdigt exempel som skapar en rektangel med en mjuk grå skugga, sparad som *Shadow.docx*.

## Förutsättningar – Vad du behöver innan du börjar

Innan vi dyker ner i koden, se till att du har följande:

| Krav | Orsak |
|------|-------|
| Java Development Kit (JDK) 8 eller nyare | Aspose.Words fungerar på alla moderna JDK. |
| Maven eller Gradle (valfritt) | Förenklar tillägget av Aspose.Words‑beroendet. |
| Aspose.Words för Java‑licens (eller en gratis provversion) | Biblioteket är kommersiellt; en provversion räcker för testning. |
| En IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Hjälper dig att snabbt köra och felsöka exemplet. |

Om du redan har ett Java‑projekt, lägg bara till Maven‑koordinaten:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Ingen avancerad konfiguration behövs—endast en enkel `public static void main`‑metod räcker.

![create rectangle shape example](https://example.com/rectangle-shadow.png "create rectangle shape with shadow in Word")

*Bildtext: exempel på rektangelform som visar en cyan rektangel med en grå skugga.*

## Steg 1 – Skapa ett nytt Word‑dokument

Det första vi måste göra är att starta ett tomt dokument. Tänk på det som att öppna en ny Word‑fil som du senare ska måla på.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Varför börja med ett tomt `Document`? För att Aspose.Words behandlar `Document`‑klassen som en målarduk för alla efterföljande operationer—lägga till stycken, tabeller eller former. Hoppar du över detta steg får du ett `NullPointerException` så fort du försöker infoga något.

## Steg 2 – Ställ in en DocumentBuilder

En `DocumentBuilder` är din vänliga penna som skriver in i `Document`. Det är det rekommenderade sättet att lägga till innehåll eftersom den automatiskt hanterar markörens position.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Du kanske undrar: “Varför inte manipulera dokumentet direkt?” Svaret: byggaren abstraherar bort lågnivådetaljer som sektionhantering, vilket gör koden renare och mindre felbenägen.

## Steg 3 – Infoga rektangelformen

Nu blir det roligt—**hur man skapar form**. Vi infogar en rektangel som är 100 × 50 punkter och ger den en cyan fyllning så att du faktiskt kan se den.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Några anmärkningar:

* `ShapeType.RECTANGLE` talar om för Aspose att vi vill ha en rektangel; du kan byta ut den mot `OVAL`, `LINE` osv.
* Måtten anges i punkter (1 pt ≈ 1/72 tum). Justera dem efter ditt layoutbehov.
* Utan en fyllningsfärg skulle formen vara osynlig mot en vit sida—därför cyan.

## Steg 4 – Lägg till en skugga och **sätt skuggfärg**

Här svarar vi på **hur man lägger till skugga**‑delen av pusslet. `ShadowFormat`‑objektet styr varje visuellt aspekt av skuggan, från färg till suddradie.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Varför just dessa värden?

* **Synlighet** – Utan `setVisible(true)` ignoreras resten av inställningarna.
* **Färg** – Grå är ett neutralt val som fungerar på både ljusa och mörka bakgrunder. Byt gärna ut `java.awt.Color.GRAY` mot någon annan `java.awt.Color` du föredrar.
* **Suddradie** – Värdet `5.0` ger en mjuk fjäder; högre tal gör skuggan mer diffus.
* **OffsetX/Y** – Offset flyttar skuggan åt höger och ner, vilket efterliknar ett ljus från övre vänstra hörnet.
* **Transparens** – En halvtransparent skugga smälter bättre in i sidan, särskilt vid utskrift.

Om du vill ha en skarpare look, sänk suddradiet till `0` och öka offseten. Experimentera gärna—skuggor är starkt visuella och rätt inställningar beror på ditt dokuments design.

## Steg 5 – Spara dokumentet

Till sist sparar vi allt till en `.docx`‑fil. Du kan välja vilken sökväg du vill; se bara till att katalogen finns.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

När du öppnar *Shadow.docx* i Microsoft Word ser du en cyan rektangel med en subtil grå skugga som ligger 4 pt åt höger och ner. Det är hela **skapa word dokument**‑arbetsflödet.

### Förväntat resultat

| Element | Utseende |
|---------|----------|
| Rektangel | Cyan fyllning, 100 × 50 pt storlek |
| Skugga | Grå, 30 % transparent, 5 pt suddradie, offset (4, 4) |
| Fil | `Shadow.docx` sparad på den angivna sökvägen |

Om formen inte visas, dubbelkolla att fyllningsfärgen inte är samma som sidbakgrunden och att skuggan är satt till synlig.

## Pro‑tips & Vanliga fallgropar

* **Pro‑tips:** Använd `rectangle.setStrokeColor(java.awt.Color.BLACK);` om du vill ha en kantlinje runt formen. Det får rektangeln att framträda bättre på en utskriven sida.
* **Se upp för:** Att spara till en skrivskyddad mapp kastar ett `IOException`. Välj en skrivbar plats eller justera filbehörigheterna.
* **Edge case:** Om du behöver en transparent fyllning (ingen färg), anropa `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. Formen kastar fortfarande en skugga, vilket kan vara användbart för vattenstämpel‑liknande grafik.
* **Prestanda‑notering:** Att lägga till hundratals former i en loop kan öka minnesanvändningen. Anropa `document.save` endast en gång efter att alla former har lagts till.

## Fullt fungerande exempel

Nedan är hela programmet som du kan kopiera‑klistra in i en Java‑klass kallad `ShadowDemo`. Det kompileras och körs som det är (förutsatt att du har Aspose.Words‑JAR‑filen på classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Kör programmet, öppna den resulterande *Shadow.docx*, och du kommer att se rektangeln med sin skugga exakt som beskrivet.

## Vad händer om du behöver fler former?

Du kanske undrar, “Kan jag **skapa rektangelform** flera gånger eller använda andra former?” Absolut. Loopa bara över infogningskoden och justera koordinater med `builder.moveTo` eller `builder.insertParagraph`. Samma skugginställningar kan återanvändas genom att extrahera dem till en hjälpfunktion:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Anropa `applyStandardShadow(rectangle);` efter varje forminfogning för att hålla koden DRY (Don’t Repeat Yourself).

## Nästa steg – Gå bortom grunderna

Nu när du vet **hur man lägger till skugga**, överväg att utforska dessa relaterade ämnen:

* **Hur man sätter skuggfärg** för textstycken – ger rubriker ett subtilt lyft.
* **Skapa word dokument** med tabeller och bilder – kombinera former med annat innehåll.
* **Hur man skapar form**‑animationer med Words inbyggda verktyg

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}