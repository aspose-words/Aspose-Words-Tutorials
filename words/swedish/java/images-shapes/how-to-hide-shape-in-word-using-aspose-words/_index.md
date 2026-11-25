---
category: general
date: 2026-11-25
description: Dölj en form i Word med Aspose.Words och lär dig att skapa ett Word‑dokument
  med Aspose när du infogar en rektangulär form i Word med bara några få rader kod.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: sv
lastmod: 2026-11-25
og_description: Dölj form i Word med Aspose.Words. Denna handledning visar hur du
  skapar ett Word‑dokument med Aspose, infogar en rektangulär form i Word och döljer
  den programmässigt.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Dölj form i Word med Aspose.Words – snabb steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Hur man döljer en form i Word med Aspose.Words
url: /sv/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så döljer du en form i Word med Aspose.Words

Om du behöver **dölja en form i Word** när du genererar dokument programatiskt, gör Aspose.Words det enkelt. I den här guiden får du se exakt hur du skapar ett Word‑dokument med Aspose, infogar en rektangel‑form i Word och sedan döljer den så att den inte visas i layouten. Det kompletta, körbara exemplet finns med så att du kan kopiera‑klistra in det i din IDE och se resultatet omedelbart.

När du är klar med den här handledningen har du en Word‑fil som innehåller en dold rektangel – användbart för platshållare, villkorligt innehåll eller metadata som ska förbli osynlig för läsaren. Inga externa verktyg krävs utöver Aspose.Words för Java (eller .NET).

## Vad du kommer att lära dig

* Hur du **skapar ett Word‑dokument med Aspose** från grunden.  
* Hur du **infogar en rektangel‑form i Word** med `DocumentBuilder`.  
* Hur du sätter formens `hidden`‑egenskap så att den inte renderas i den slutgiltiga layouten.  
* Hur du verifierar att formen är dold och hur du visar den igen om så behövs.  

### Förutsättningar

* Java 17+ (eller .NET 6+ om du föredrar C# – API‑anropen är analogt).  
* Aspose.Words för Java 24.x (senaste versionen vid skrivtillfället).  
* En IDE som IntelliJ IDEA, Eclipse eller VS Code.  

> **Pro tip:** Använd den kostnadsfria temporära licensen från Aspose om du ännu inte har en kommersiell licens. Biblioteket fungerar utan licens för utvärdering, men en licens tar bort utvärderingsvattenstämplar.

## Dölja en form i Word med Aspose.Words

De grundläggande stegen är:

1. **Skapa ett nytt `Document`.**  
2. **Infoga en rektangel‑form** med `DocumentBuilder`.  
3. **Markera formen som dold** så att den inte visas när filen öppnas.  

Varje steg förklaras nedan med kod och resonemang.

### Steg 1: Skapa ett Word‑dokument med Aspose

Först skapar du ett tomt `Document` och en `DocumentBuilder`. Buildern erbjuder ett flytande API för att lägga till innehåll, inklusive former.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:**  
Att skapa ett nytt `Document` ger dig en ren canvas. `DocumentBuilder` är det rekommenderade sättet att modifiera dokumentet eftersom den automatiskt spårar den aktuella infogningspunkten och hanterar sektion‑/sidhantering åt dig.

### Steg 2: Infoga en rektangel‑form i Word

Nu lägger vi till en rektangel‑form. Metoden `insertShape` kräver formtypen och dess dimensioner i punkter (1 punkt = 1/72 tum).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Varför detta är viktigt:**  
`insertShape` skapar ett ritobjekt som lever i dokumentets *drawing*-del. Genom att ange storleken styr du hur mycket utrymme formen skulle ta om den var synlig. Den valfria formgivningen hjälper dig att verifiera formen innan du döljer den.

### Steg 3: Dölj formen så att den inte visas i layouten

Aspose.Words speglar Microsoft Words *Hidden*-attribut. Att sätta det till `true` talar om för Word att utesluta formen från rendering, samtidigt som objektet behålls i dokumentstrukturen.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Varför detta är viktigt:**  
En dold form kan fortfarande nås programatiskt (t.ex. för villkorlig bearbetning) och kan visas igen senare genom att växla egenskapen. Detta är idealiskt för scenarier som **villkorliga platshållare** som bara ska visas för vissa målgrupper.

### Steg 4: Spara och verifiera resultatet

Till sist skriver du dokumentet till disk. Öppna filen i Microsoft Word för att bekräfta att rektangeln inte är synlig. Du kan också inspektera den underliggande XML‑koden för att se den dolda flaggan.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Förväntad utskrift:**  
Programmet skriver ut:

```
Document saved to HideShapeResult.docx
```

När du öppnar *HideShapeResult.docx* i Word ser sidan tom ut (eller innehåller annat innehåll du eventuellt lagt till före formen). Rektangeln finns i filens XML (`<w:hidden>`‑attribut) men renderas inte.

### Steg 5: (Valfritt) Visa formen igen senare

Om du behöver göra formen synlig igen, läs in dokumentet, lokalisera formen och sätt `hidden` till `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Varför detta är viktigt:**  
Att kunna växla den dolda flaggan ger dig full kontroll över dynamisk dokumentgenerering – t.ex. kan du skapa ett huvud‑dokument med alla valfria element dolda och sedan visa dem selektivt baserat på användarpreferenser.

## Fullt, körbart exempel (skapa Word‑dokument med Aspose, infoga rektangel‑form i Word, dölj formen)

Nedan är det kompletta programmet som du kan kompilera och köra direkt.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Kör koden**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Byt ut `aspose-words-24.10.jar` mot den faktiska version du har laddat ner.

### Vad utdatafilerna innehåller

* **HideShapeResult.docx** – rektangeln är dold; sidan ser tom ut.  
* **UnhiddenShape.docx** – samma rektangel är synlig och visar en röd ruta med svart kontur.

## Vanliga frågor & hantering av kantfall

| Fråga | Svar |
|----------|--------|
| *Kommer den dolda formen att påverka sidnumrering?* | Nej. Dolda objekt ignoreras av layout‑motorn, så de skjuter inte text till en ny sida. |
| *Kan jag dölja andra Word‑objekt (t.ex. bilder, tabeller)?* | Ja. De flesta `Node`‑subklasser (inklusive `Shape`, `Paragraph`, `Run`) har en `setHidden(boolean)`‑metod. |
| *Vad händer om dokumentet redan innehåller former?* | Använd `doc.getChildNodes(NodeType.SHAPE, true)` för att iterera och dölja endast de former du vill rikta in dig på. |
| *Ökar dold form filstorleken?* | Lite grann, eftersom formens XML fortfarande finns kvar. Påverkan är försumbar för vanliga dokument. |
| *Behåller den dolda flaggan när dokumentet sparas som PDF?* | Vid konvertering till PDF utesluts dolda former som standard. Du kan styra detta med `PdfSaveOptions` om så önskas. |

## Bästa praxis vid arbete med dolda objekt

* **Ge dina former namn** med `setName("MyPlaceholder")`. Detta underlättar att hitta dem senare.  
* **Gruppera relaterade dolda objekt** i ett `GroupShape` om du vill växla synlighet för flera element samtidigt.  
* **Dokumentera syftet** med dolda element i kommentarer eller en separat specifikationsfil – framtida underhållare kommer att uppskatta kontexten.  
* **Undvik överanvändning av dolda objekt**; de ökar dokumentets komplexitet och kan förvirra slutanvändare som manuellt inspekterar XML.  

## Slutsats

Du vet nu hur du **döljer en form i Word** med Aspose.Words, hur du **skapar ett Word‑dokument med Aspose** och hur du **infogar en rektangel‑form i Word** innan du döljer den. Exemplet visar hela livscykeln: skapande, infogning, dölja, spara och eventuellt visa igen. Använd dessa tekniker för att bygga dynamiska rapporter, villkorliga mallar eller någon automatiserad Word‑arbetsflöde där osynliga platshållare behövs.

### Nästa steg

* Utforska **villkorligt innehåll** genom att kombinera dolda former med mail‑merge‑fält.  
* Lär dig hur du **döljer text‑runs** (`Run.setHidden(true)`) för ännu finare kontroll.  
* Läs Aspose.Words‑dokumentationen om **dokumentskydd** för att förhindra att användare av misstag visar dolda former.

Lycka till med kodandet, och låt dina genererade Word‑filer förbli rena samtidigt som de bär den dolda data du behöver!

## Vad du bör lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}