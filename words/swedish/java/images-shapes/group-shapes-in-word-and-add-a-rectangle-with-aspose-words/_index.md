---
category: general
date: 2026-09-11
description: Gruppera former i Word och lägg till en rektangelform med Aspose.Words
  för Java. Lär dig hur du ställer in formens storlek, grupperar objekt och sparar
  dokumentet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: sv
lastmod: 2026-09-11
og_description: Gruppera former i Word och lägg till en rektangel med Aspose.Words
  för Java. Denna handledning visar hur du anger formens storlek, grupperar former
  och exporterar dokumentet.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Gruppera former i Word – lägg till rektangel med Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Gruppera former i Word och lägg till en rektangel med Aspose.Words
url: /sv/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruppera former i Word och lägg till en rektangel med Aspose.Words

Om du behöver **gruppera former i Word** samtidigt som du programatiskt lägger till en rektangel, ger den här guiden dig en komplett, färdig‑att‑köra lösning. Du kommer att se exakt hur du infogar en gruppform, lägger till en rektangel, anger formens storlek och slutligen sparar dokumentet så att du kan se resultatet omedelbart.

Att arbeta med Word-dokument innebär ofta att arrangera flera objekt—bilder, diagram eller enkla geometriska former—till en enda logisk enhet. Att gruppera dessa objekt gör det enklare att flytta, rotera eller formatera dem tillsammans. I den här handledningen kommer vi också att gå igenom **hur man lägger till rektangel**-former och **anger formstorlek** för perfekt layoutkontroll.

## Vad du kommer att lära dig

* Hur man skapar ett nytt Word-dokument med Aspose.Words för Java.  
* **Hur man grupperar former** så att de beter sig som ett enda objekt.  
* **Lägg till rektangel** i en grupp och infoga en bild i samma grupp.  
* **Ange formstorlek** för både rektangeln och bilden.  
* Spara dokumentet och öppna det i Microsoft Word för att verifiera resultatet.

### Förutsättningar

* Java 17 eller senare installerat.  
* Maven eller Gradle för att hantera beroenden.  
* En giltig Aspose.Words för Java-licens (eller en gratis utvärderingsnyckel).  
* En bildfil (`sample.png`) placerad i en känd katalog (ersätt `YOUR_DIRECTORY` med din faktiska sökväg).

---

## Hur man grupperar former i Word med Aspose.Words

Det första steget är att skapa ett `Document` och en `DocumentBuilder`. Buildern ger dig ett bekvämt API för att infoga former, text och andra element.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Varför detta är viktigt:** `DocumentBuilder` arbetar direkt med det underliggande `Document`-objektet, vilket gör att du kan infoga former utan att manuellt hantera lågnivå‑nodsamlingar.

### Lägg till en gruppform

En gruppform är en behållare som kan hålla andra former. Tänk på den som en mapp för ritobjekt.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

`insertGroupShape()`‑metoden skapar en `GroupShape`‑nod och returnerar den så att du senare kan lägga till underordnade former.

---

## Lägg till en rektangel i gruppen

Nu kommer vi att **lägga till en rektangel** i den tidigare skapade gruppen. Rektangeln kommer att fungera som en bakgrund eller en ram för bilden.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tips:** Att sätta `FillColor` och `StrokeColor` gör rektangeln synlig i det slutliga dokumentet. Om du utelämnar dessa egenskaper kan formen bli transparent.

### Hur man lägger till rektangel

Koden ovan demonstrerar **hur man lägger till en rektangel** genom att skapa en `Shape`‑instans med `ShapeType.RECTANGLE` och sedan lägga till den i `GroupShape`. Detta mönster fungerar för alla andra formtyper (t.ex. `ELLIPSE`, `POLYLINE`).

---

## Ange formstorlek för rektangel och bild

Rätt storlek säkerställer att rektangeln och bilden aligneras korrekt. Här **anger vi formstorlek** för bilden som vi kommer att infoga härnäst.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Både rektangeln och bilden har nu samma dimensioner (100 × 50 punkter). Eftersom de tillhör samma grupp kommer flyttning eller rotation av gruppen att påverka båda formerna tillsammans.

> **Varför matcha storlekar?** Att justera dimensionerna garanterar att bilden sitter prydligt inom rektangeln, vilket skapar en ren “ramad bild”-effekt.

---

## Spara dokumentet och visa resultatet

Till sist skriver vi dokumentet till disk. När du öppnar filen i Microsoft Word visas de grupperade formerna som ett enda markerbart objekt.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

När du öppnar `output.docx` ser du en rektangel med bilden inuti. När du klickar på formen markeras både rektangeln och bilden eftersom de är **grupperade**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Bild alt‑text:* *group shapes in word example* – ett Word‑dokument som visar en grupperad rektangel och bild.

---

## Vanliga frågor och hantering av kantfall

| Fråga | Svar |
|----------|--------|
| **Vad händer om jag behöver en annan storlek på bilden?** | Justera `picture.setWidth()` och `picture.setHeight()` efter infogning. Rektangeln kan behålla sin ursprungliga storlek, eller så kan du även ändra dess storlek så att den matchar. |
| **Kan jag lägga till fler former i samma grupp?** | Ja. Anropa `group.appendChild(newShape)` för alla ytterligare `Shape`‑objekt. |
| **Hur roterar jag hela gruppen?** | Använd `group.setRotationAngle(double angleInRadians)`. Rotation appliceras på varje underordnad form. |
| **Vad händer om bildfilen saknas?** | `insertImage` kastar `FileNotFoundException`. Omslut anropet i ett try‑catch‑block och tillhandahåll en reserv‑platshållarform. |
| **Är det möjligt att avgruppera senare?** | Anropa `group.removeAllChildren()` för att lossa barnen, och infoga dem sedan tillbaka i dokumentet individuellt. |

---

## Slutsats

Du har nu ett komplett, körbart exempel som visar **hur man grupperar former i Word**, **lägger till en rektangel**, **anger formstorlek** och **sparar** dokumentet med Aspose.Words för Java. Genom att gruppera rektangeln och bilden kan du flytta, ändra storlek eller rotera dem som en enda enhet—precis vad många dokument‑automatiseringsscenarier kräver.

Härifrån kan du utforska:

* Lägga till textrutor i samma grupp (`how to add rectangle`‑stil text).  
* Applicera olika fyllningsmönster eller gradienter (`set shape size` kombinerat med styling).  
* Använda samma teknik för att gruppera diagram, tabeller eller SmartArt (`how to group shapes` över andra objekttyper).  

Känn dig fri att experimentera med andra formtyper, färger och layoutalternativ. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangel med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hur man konverterar Word till PDF med Aspose.Words för Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}