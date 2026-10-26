---
category: general
date: 2026-10-26
description: Lär dig hur du skapar Word-dokument programatiskt, lägger till en form
  och döljer ett objekt i Word med Aspose.Words för Java – steg‑för‑steg‑guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: sv
lastmod: 2026-10-26
og_description: Skapa Word-dokument programatiskt, lär dig hur du lägger till en form
  och döljer ett objekt i Word med Aspose.Words för Java. Komplett, körbart exempel.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Skapa Word-dokument programatiskt – lägg till och dölj former i Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Skapa ett Word‑dokument programatiskt och lägg till en form i Java
url: /sv/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt och lägg till en form i Java

Om du behöver **skapa Word-dokument programatiskt**, den här handledningen visar exakt hur du gör det, lägger till en form och sedan döljer objektet i Word. Oavsett om du bygger en rapportgenerator eller ett automatiserat kontraktsystem, får du en komplett, färdig‑att‑köra lösning på bara några minuter.

Du kommer att lära dig hur du:

* Initiera ett Word-dokument med Aspose.Words for Java.  
* Infoga en ellips (eller någon annan form) med hjälp av **hur man lägger till en form**‑tekniken.  
* Dölja den formen så att den aldrig visas när filen öppnas, vilket svarar på frågan **hur man döljer en form**.  

Inga externa verktyg krävs utöver Aspose.Words‑biblioteket, och koden fungerar med Java 17 och senare.

## Förutsättningar

Innan du börjar, se till att du har:

* Java Development Kit (JDK) 17 eller nyare installerat.  
* Maven eller Gradle för att hantera beroenden (exemplet använder Maven).  
* En giltig Aspose.Words for Java‑licens (den kostnadsfria utvärderingen fungerar för testning).  

Om du är ny på Aspose.Words, se den officiella Getting Started‑guiden, men du behöver inte läsa den för att följa den här handledningen.

## Maven‑beroende

Lägg till följande beroende i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Proffstips:** Håll versionsnumret uppdaterat; nyare versioner innehåller buggfixar för hantering av former.

## Steg 1: Skapa Word-dokument programatiskt – initiera dokumentet

Det första du gör när du **skapar Word-dokument programatiskt** är att instansiera ett `Document`‑objekt. Detta objekt representerar hela .docx‑filen i minnet.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta steg är viktigt*: `Document`‑klassen är ingångspunkten för alla Word‑behandlingsoperationer. Utan den kan du inte lägga till sidor, stycken eller former.

## Steg 2: Hur man lägger till en form – infoga en ellips

Nu tar vi itu med **hur man lägger till en form**‑delen av handledningen. Aspose.Words stöder många formtyper (Ellipse, Rectangle, TextBox, etc.). Nedan infogar vi en ellips med en bredd och höjd på 50 punkter.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

Metoden `insertShape` returnerar ett `Shape`‑objekt som du kan anpassa ytterligare—färg, linjestil, rotation och mer. Koordinaterna mäts i punkter (1/72 tum).

*Varför du kanske vill lägga till en form*: Former är användbara för vattenstämplar, dekorativa element eller platshållare som du senare döljer eller ersätter.

## Steg 3: Hur man döljer en form – gör objektet osynligt i Word

För att svara på frågan **hur man döljer en form**, sätt helt enkelt formens `Hidden`‑egenskap till `true`. Detta får Word att behandla formen som ett dolt objekt, så den aldrig renderas i dokumentvyn eller utskriften.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Om du behöver **dölja objekt i Word** för en specifik användare eller villkor, kan du växla denna egenskap vid körning baserat på din affärslogik.

> **Obs!** Dolda former är fortfarande en del av dokumentets XML‑struktur. De kan avslöjas senare genom att sätta `setHidden(false)`.

## Steg 4: Spara dokumentet

Efter att ha lagt till och dolt formen, skriv dokumentet till disk.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

När du öppnar `HiddenShapeDemo.docx` i Microsoft Word kommer du att se en tom sida eftersom ellipsen är dold. Dokumentet beter sig annars som vilket normalt Word‑fil som helst.

## Fullt fungerande exempel

Genom att sätta ihop alla delar får du det kompletta, körbara programmet:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Förväntat resultat**

```
Document created successfully.
```

Att öppna `HiddenShapeDemo.docx` visar en tom sida; den dolda ellipsen renderas inte, vilket bekräftar att **dölja objekt i Word**‑operationen lyckades.

## Kantfall och variationer

| Situation | Vad som ska ändras | Varför |
|-----------|--------------------|--------|
| Dölj en rektangel istället för en ellips | Använd `ShapeType.RECTANGLE` i `insertShape` | Olika visuellt platshållare |
| Dölj flera former på en gång | Loopa igenom `doc.getChildNodes(NodeType.SHAPE, true)` och sätt `setHidden(true)` | Användbart för massbearbetning |
| Visa formen endast i utskriftsvyn | Sätt `shape.setVisible(false)` och `shape.setPrint(true)` | Word skiljer mellan skärm- och utskriftsvisning |
| Använd en annan mätenhet | Anropa `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Stämmer överens med dina layoutkrav |

## Vanliga fallgropar

* **Glömmer att anropa `setHidden(true)`** – formen kommer att visas som vanligt.  
* **Spara dokumentet innan formen döljs** – ordningen är viktig; dölj först, spara sedan.  
* **Använder en föråldrad Aspose.Words‑version** – äldre versioner kan sakna `setHidden`‑API:t.  

Testa alltid den genererade filen i den målversion av Microsoft Word som du avser för att säkerställa att det dolda tillståndet fungerar som förväntat.

## Slutsats

I den här guiden lärde du dig hur du **skapar Word-dokument programatiskt**, **lägger till en form**, och **döljer objekt i Word** med Aspose.Words for Java. Det kompletta exemplet visar de exakta stegen, från att initiera dokumentet till att spara en fil där formen aldrig visas.  

Från här kan du:

* Experimentera med andra formtyper (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Kombinera dolda former med bokmärken för att skapa dynamiska mallar.  
* Utforska egenskaperna `setVisible` och `setPrint` för mer finstyrd kontroll över objektets synlighet.

Lycka till med kodandet, och njut av att automatisera dina Word-dokument!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create blank word document with Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}