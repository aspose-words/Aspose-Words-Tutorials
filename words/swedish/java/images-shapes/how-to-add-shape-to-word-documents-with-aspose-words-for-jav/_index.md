---
category: general
date: 2026-11-22
description: Lär dig hur du lägger till en form i Word med Aspose.Words för Java –
  infoga en rektangel och dölja den programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: sv
lastmod: 2026-11-22
og_description: Lägg till en form i Word med Aspose.Words för Java. Denna handledning
  visar hur du infogar en rektangel, döljer formen och sparar dokumentet.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Lägg till form i Word med Aspose.Words – Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Hur du lägger till en form i Word‑dokument med Aspose.Words för Java
url: /sv/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till form i Word‑dokument med Aspose.Words för Java

Om du behöver **lägga till form i Word**‑dokument programatiskt, gör Aspose.Words för Java det enkelt. I den här guiden kommer du att lära dig **hur man infogar en form**, kontrollera dess synlighet och **hur man döljer en form** så att den slutliga filen ser exakt ut som du förväntar dig.

Du kommer att gå igenom ett komplett, körbart exempel som laddar en befintlig `.docx`, infogar en rektangel, döljer den och sparar resultatet. Inga externa skript eller manuella steg krävs, och handledningen täcker vanliga varianter såsom att skapa ett nytt dokument från grunden eller dölja en form endast vid utskrift.

## Förutsättningar

* Java 17 (eller senare) installerat – äldre versioner fungerar men den senaste LTS‑versionen ger bättre prestanda.  
* Maven 3.8+ för beroendehantering.  
* En giltig Aspose.Words för Java‑licens (den fria utvärderingen fungerar för lärande).  
* En IDE eller textredigerare du föredrar (t.ex. IntelliJ IDEA, VS Code).

## Steg 1: Lägg till Aspose.Words i ditt Maven‑projekt

Lägg till följande beroende i din `pom.xml`. Detta hämtar den senaste stabila versionen (från och med november 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Proffstips:** Använd ett `<scope>provided</scope>`‑villkor om du planerar att distribuera JAR‑filen med din egen licenslogik.

## Lägg till form i Word – initiering av dokumentet

Det första funktionella steget är att få ett `Document`‑objekt. Du kan antingen ladda en befintlig fil eller skapa en ny.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Varför detta är viktigt*: `Document`‑klassen är ingångspunkten för all Word‑manipulation. Att ladda en befintlig fil bevarar stilar, sidhuvuden och sidfötter, medan ett nytt dokument ger dig en ren start.

## Hur man infogar en form i ett Word‑dokument

Skapa sedan en `DocumentBuilder` för att ändra dokumentets innehåll. Buildern ger dig metoder för att infoga text, tabeller och **former**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

`insertShape`‑anropet returnerar ett `Shape`‑objekt som du kan konfigurera vidare (färg, kant, text osv.). Dimensionerna anges i punkter (1 pt = 1/72 in).

*Varför du kanske vill använda en rektangel*: Rektanglar är den vanligaste behållaren för kommentarer, vattenstämplar eller platshållare. Du kan ersätta `ShapeType.RECTANGLE` med `ShapeType.ELLIPSE`, `ShapeType.LINE` osv. för att möta olika visuella behov.

## Hur man döljer en form i Word

Ibland behöver du en form för layoutberäkningar men vill inte att den syns i den slutliga renderingen. Aspose.Words tillhandahåller metoden `setHidden(true)` för att uppnå detta.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Den dolda flaggan fungerar som **Hidden**‑formateringsalternativet i Microsoft Word: formen utesluts från den visuella layouten men deltar fortfarande i dokumentets objektmodell. Detta är användbart för:

* Att lagra metadata eller markörer som din applikation läser senare.  
* Att skapa platshållare som tas bort precis innan publicering.  
* Att kontrollera synlighet för olika utdataformat (t.ex. dölja i HTML men behålla i PDF).

> **Obs:** Dolda former exporteras fortfarande till PDF som standard. Om du vill att de också ska uteslutas från PDF, sätt `rectangle.getWrapType( ) = WrapType.NONE` och justera `Hidden`‑egenskapen därefter.

## Steg 4: Spara det modifierade dokumentet

Slutligen, skriv förändringarna till en ny fil.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

När du öppnar `output.docx` i Microsoft Word kommer rektangeln inte att vara synlig, men den förblir en del av dokumentträdet. Du kan verifiera dess närvaro programatiskt genom att ladda om filen och kontrollera `Shape.isHidden()`.

### Förväntat resultat

* Filen `output.docx` öppnas utan några synliga former.  
* Om du granskar dokumentet med Aspose.Words (t.ex. `doc.getChildNodes(NodeType.SHAPE, true).size()`), kommer antalet former att vara **1**, vilket bekräftar att formen finns men är dold.

## Avancerade varianter och kantfall

### 1. Skapa en form i ett nytt dokument

Om du börjar från början, ersätt laddningsraden med:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Positionera formen exakt

Som standard placerar `insertShape` formen vid den aktuella markörpositionen. För att positionera den absolut:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Kontrollera synlighet per utdataformat

Om du vill att formen ska vara synlig i Word‑gränssnittet men dold vid export till PDF, använd `Shape.setWrapType(WrapType.NONE)` tillsammans med `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Lägg till text i formen

En rektangel kan innehålla en textram:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Du kan sedan dölja textrutan med samma `setHidden(true)`‑anrop.

## Vanliga fallgropar och hur man undviker dem

| Symptom | Orsak | Lösning |
|---------|-------|---------|
| Formen visas trots `setHidden(true)` | Dokumentet sparades innan den dolda flaggan sattes. | Se till att du anropar `setHidden(true)` **innan** `doc.save()`. |
| Formens storlek ser förvrängd ut | Förvirring mellan punkter och pixlar på hög‑DPI‑skärmar. | Använd punkter (72 pt = 1 in) för konsekvent storlek på alla plattformar. |
| Dold form skrivs ändå ut | Vissa skrivare ignorerar den dolda flaggan. | Sätt `Shape.setWrapType(WrapType.NONE)` och rensa även `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Slutsats

Du vet nu hur du **lägger till form i Word**‑dokument med Aspose.Words för Java, **hur du infogar en form**, och **hur du döljer en form** så att den förblir osynlig för slutanvändaren men fortfarande är en del av dokumentstrukturen. Det kompletta exemplet ovan laddar en fil, infogar en rektangel, döljer den och sparar resultatet, och täcker både typiska användningsfall och flera kantfall.

Härifrån kan du utforska relaterade ämnen som **hur man infogar en form** med anpassade fyllningsfärger, **hur man döljer en form i Word** för villkorad utskrift, eller automatisering av massbearbetning av dokument med Aspose.Words. Experimentera med olika `ShapeType`‑värden, placeringsalternativ och synlighetsflaggor för att passa ditt specifika arbetsflöde.

Happy coding, and enjoy the flexibility that programmatic Word manipulation brings to your Java applications!

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa ett Word‑dokument programatiskt, lägg till och dölj en form i Java med Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Hur man döljer en form i ett Word‑dokument med Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Skapa ett tomt .docx‑Word‑dokument och lägg till en dold rektangulär form med Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}