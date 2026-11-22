---
category: general
date: 2026-11-22
description: Lägg till en rektangel i ett Word‑dokument med Java, ange formens storlek,
  gruppera flera former och lägg till en form i gruppen på ett effektivt sätt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: sv
lastmod: 2026-11-22
og_description: Lägg till en rektangelform i ett Word‑dokument med Java, ställ sedan
  in formens storlek, gruppera flera former och lägg till en form i gruppen i ett
  enda arbetsflöde.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Lägg till rektangelform och gruppera former i Java – fullständig guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Lägg till rektangelform och gruppera former i Java
url: /sv/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till rektangelform och gruppera former i Java

Om du behöver **add rectangle shape** till ett Word‑dokument med Java, guidar den här guiden dig genom de exakta stegen. Du kommer också att lära dig hur du **set shape size**, **group multiple shapes** och **append shape to group** utan att lämna IDE:n.

Att arbeta med vektorgrafik i en DOCX‑fil känns ofta som att jonglera med separata API:er. I slutet av den här tutorialen har du ett enda, självständigt program som skapar en rektangel, en ellips och eventuella ytterligare former du kan behöva, och sedan grupperar dem så att de rör sig som ett objekt. Inga externa verktyg krävs förutom Aspose.Words for Java.

## Förutsättningar

Innan du börjar, se till att du har:

* Java 17 eller senare installerat.
* Maven 3.8+ (eller Gradle) för att hantera beroenden.
* En giltig Aspose.Words for Java‑licens (utvärderingslicens fungerar för testning).
* En IDE som IntelliJ IDEA eller VS Code, även om vilken textredigerare som helst fungerar.

Dessa krav gör att koden kan kompileras och köras i vilken modern utvecklingsmiljö som helst.

## Steg 1: Ställ in Maven‑projektet

Skapa ett nytt Maven‑projekt eller lägg till Aspose.Words‑beroendet i en befintlig `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Beroendet hämtar alla klasser som behövs för dokumentmanipulation, inklusive `Document`, `DocumentBuilder`, `Shape` och `GroupShape`. Maven laddar ner JAR‑filerna automatiskt när du kör `mvn compile`.

## Steg 2: Ladda dokumentet och skapa en DocumentBuilder

`DocumentBuilder` erbjuder ett flytande API för att infoga innehåll. Ladda ett befintligt DOCX‑dokument eller starta från ett tomt dokument:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Att skapa buildern tidigt ger dig en markör placerad i början av dokumentet, redo för att infoga former.

## Lägg till rektangelform i ett Word‑dokument

### Steg 3: Infoga rektangelformen

Rektangeln är det första visuella elementet vi vill placera i dokumentet. Genom att använda `Shape`‑konstruktorn med `ShapeType.RECTANGLE` får du ett fullt redigerbart objekt.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Att lägga till rektangeln i detta skede påverkar inte layouten förrän dess storlek har definierats och den har lagts till i en behållare.

### Ställ in formens storlek och dimensioner

#### Steg 4: Definiera bredd och höjd

Att ange formens dimensioner bestämmer hur den visas på sidan. Bredd‑ och höjdvärden mäts i punkter (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Du kan justera dessa siffror för att matcha dina designkrav. Samma metoder gäller för alla `Shape`‑instanser, så du kan återanvända dem för cirklar, pilar eller anpassade teckningar.

#### Steg 5: Infoga rektangeln i dokumentet

Nu när rektangeln har en storlek, placera den på sidan. Metoden `insertShape` i `DocumentBuilder` lägger till formen vid den aktuella markörpositionen.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

I detta skede visas rektangeln ensam på sidan. Nästa steg visar hur du kombinerar den med andra former.

## Gruppera flera former tillsammans

Att gruppera former låter dig flytta, rotera eller ändra storlek på dem som en enhet. Detta är särskilt användbart för att skapa komplexa diagram.

### Steg 6: Skapa en gruppformbehållare

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`insertGroupShape`‑anropet lägger till en tom behållare i dokumentet. Alla former som läggs till i denna behållare blir en del av gruppen.

### Lägg till form i grupp

#### Steg 7: Lägg till rektangeln i gruppen

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Att lägga till flyttar rektangeln från dokumentkroppen till gruppens interna samling. Rektangeln följer nu gruppens transformationer.

#### Steg 8: Lägg till en ellips för demonstration

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Ellipsen delar samma koordinatrymd som rektangeln, så du kan visuellt justera dem genom att ändra deras `setLeft`‑ och `setTop`‑egenskaper om så behövs.

### Steg 9: Spara dokumentet

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

När programmet körs genereras `output.docx`. Öppna filen i Microsoft Word eller LibreOffice; du kommer att se en rektangel och en ellips grupperade tillsammans. Att markera någon av formerna markerar hela gruppen, vilket bekräftar att **append shape to group** lyckades.

![Exempel på att lägga till rektangelform i Java](image.png){alt="Exempel på att lägga till rektangelform i Java"}

*Skärmbilden visar rektangeln och ellipsen i en enda grupp, redo för gemensam manipulation.*

## Varför detta tillvägagångssätt är viktigt

* **Single source of truth** – Alla formegenskaper sätts innan gruppen skapas, vilket förhindrar layoutfel.
* **Reusability** – Samma `setWidth`/`setHeight`‑metoder fungerar för alla former, så du kan utöka exemplet till pilar, stjärnor eller anpassade SVG‑filer.
* **Performance** – Gruppering minskar antalet ritobjekt som Word‑renderaren måste hantera, vilket förbättrar öppningshastigheten för stora dokument.
* **Maintainability** – Genom att hålla skapande av former och grupperingslogik tillsammans kan framtida utvecklare ändra dimensioner eller lägga till nya former utan att söka igenom orelaterad kod.

## Vanliga variationer och kantfall

| Scenario | Justering |
|----------|-----------|
| **Olika enheter** | Använd `PointsToPixels`‑konvertering eller sätt `Shape.setWrapType(WrapType.INLINE)` för inline‑placering. |
| **Rotera gruppen** | Anropa `groupShape.setRotation(45);` för att rotera alla underordnade former med 45°. |
| **Lägga till text i en form** | Använd `Shape.setText("Label");` efter att ha satt storlek. |
| **Dynamisk storlek** | Hämta sidans dimensioner via `doc.getFirstSection().getPageSetup().getPageWidth()` och beräkna formernas storlekar proportionellt. |

Dessa variationer illustrerar hur kärnmönstret — **add rectangle shape**, **set shape size**, **group multiple shapes**, **append shape to group** — anpassas till många verkliga krav.

## Slutsats

Du vet nu hur du **add rectangle shape** till ett Word‑dokument med Java, **set shape size**, **group multiple shapes** och **append shape to group** på ett rent, underhållbart sätt. Det kompletta exemplet kompileras till en enda körbar klass, och den resulterande DOCX‑filen visar det förväntade resultatet.

Härifrån kan du utforska:

* Lägga till textetiketter eller hyperlänkar till varje form.
* Nästla grupper för att bygga hierarkiska diagram.
* Exportera dokumentet till PDF samtidigt som formgrupper bevaras.

Känn dig fri att experimentera med olika dimensioner, färger och ytterligare formtyper. Att behärska formmanipulation öppnar dörren till automatiserad rapportgenerering, dynamiska diagram och rika dokumentupplevelser – allt direkt från Java‑kod.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga rektangelform i Java – gruppera och positionera former](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Hur man skapar och infogar ellips- och rektangelformer i en gruppform i ett Word‑dokument med Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Skapa rektangelform i ett Word‑dokument med Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}