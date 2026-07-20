---
category: general
date: 2026-07-20
description: Skapa ett tomt Word‑dokument i Java med Aspose.Words. Lär dig hur du
  skapar en grupp, infogar en rektangulär form och bäddar in en bild i formen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: sv
lastmod: 2026-07-20
og_description: Skapa ett tomt Word‑dokument i Java med Aspose.Words. Den här guiden
  visar hur du skapar en grupp, infogar en rektangulär form och bäddar in en bild
  i formen för dynamiska Word‑filer.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Skapa tomt Word-dokument med grupperad form – Java-guide
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Skapa ett tomt Word‑dokument med grupperad form – Java‑guide
url: /sv/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tomt Word-dokument med grupperad form – Java‑guide

Har du någonsin undrat hur man **skapa tomt Word-dokument** som redan innehåller en snyggt grupperad form? Kanske bygger du en rapportmall, eller så behöver du en platshållare för en logotyp och en bildtext. Oavsett är problemet vanligt: du börjar med en tom fil, sedan måste du lägga till en grupp, släppa in en rektangel och slutligen bädda in en bild – allt programatiskt.

I den här handledningen går vi igenom ett komplett, färdigt att köra Java‑exempel som gör exakt det. Du kommer att lära dig **hur man skapar grupp**, **infoga rektangelform**, och **lägga till bild i Word-dokument** i samma grupp. I slutet har du en Word‑fil som ser ut som en polerad mall, redo för vidare anpassning.

> **Vad du får:** en fullt funktionell Java‑klass, steg‑för‑steg‑förklaringar, tips för hantering av filsökvägar och en förhandsgranskning av det förväntade resultatet. Ingen extern dokumentation behövs – allt du behöver finns här.

---

## Skapa tomt Word-dokument – steg‑för‑steg‑översikt

Det första vi behöver är en riktigt tom Word‑fil. Aspose.Words gör detta enkelt: bara skapa en instans av `Document`‑klassen med dess standardkonstruktor. Detta ger dig en ren canvas, motsvarande att öppna Word och klicka på **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Varför börja med ett tomt dokument?**  
> Ett tomt dokument garanterar att inga dolda stilar eller sektioner stör de former du lägger till senare. Det håller också filstorleken minimal, vilket är praktiskt när du genererar dussintals filer i ett batch‑jobb.

---

## Hur man skapar grupp och lägger till former

En **group shape** är i princip en behållare som kan hålla flera underordnade former – tänk på den som en mapp för ritobjekt. Genom att gruppera kan du flytta, ändra storlek eller rotera hela uppsättningen med ett enda kommando.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

`insertGroupShape`‑metoden returnerar ett `GroupShape`‑objekt som vi kommer att använda som förälder för rektangeln och bilden. Storleken uttrycks i punkter (1 point = 1/72 tum), så 200 punkter ger dig ungefär en 2,78 × 2,78 tum‑ruta.

> **Pro‑tips:** Om du behöver att gruppen ska vara transparent, sätt `group.setFillColor(Color.getWhite());` efter skapandet.

Nu när gruppen finns måste vi tala om för byggaren var nästa former ska placeras. Byggarens markör måste vara placerad i gruppens första stycke.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Infoga rektangelform i gruppen

En rektangel används ofta som en platshållare för text eller som en visuell ledtråd. Att lägga till den som **first child** i gruppen säkerställer att den ligger bakom eventuella efterföljande bilder.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Rektangeln ärver gruppens koordinatsystem, så dess 100 × 50‑punkt‑storlek kommer att centreras som standard. Du kan stilisera den ytterligare – lägga till en kantlinje, ändra fyllningsfärgen eller applicera en skugga – genom att komma åt det returnerade `Shape`‑objektet.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Lägg till bild i Word-dokument – bädda in bild i form

Nu till den roliga delen: **embed image in shape**. Vi kommer att infoga en JPEG‑bild som det andra barnet i samma grupp. Eftersom markören fortfarande är i gruppen blir bilden automatiskt ett barn‑nod.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Om bildfilen inte hittas kastar Aspose.Words ett `FileNotFoundException`. För att undvika detta, placera `sample.jpg` i projektets arbetskatalog eller använd en absolut sökväg.

> **Vad händer om du behöver ett annat bildformat?**  
> Aspose.Words stödjer PNG, BMP, GIF, TIFF och till och med SVG. Byt bara filändelsen så hanterar biblioteket konverteringen.

---

## Spara dokumentet och se resultatet

Till sist sparar vi det minnesbaserade dokumentet till disk. Den resulterande `.docx`‑filen kommer att innehålla en enda sida med en grupperad form som innehåller både rektangeln och bilden.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

När du öppnar `output.docx` i Microsoft Word bör du se en 200 × 200‑punkt‑grupp i det övre vänstra hörnet. Inuti gruppen sitter en ljusgrå rektangel högst upp, och precis under den visas bilden du angav, perfekt justerad.

![Grouped shape example](grouped-shape.png){:alt="Skärmdump av ett tomt Word-dokument med en grupperad form som innehåller en rektangel och en inbäddad bild"}

---

## Vanliga varianter och hantering av kantfall

| Scenario | Vad som ska ändras | Varför det är viktigt |
|----------|--------------------|-----------------------|
| **Olika gruppstorlek** | Justera parametrarna för `insertGroupShape(width, height)` | Större grupper kan rymma mer komplexa layouter. |
| **Flera bilder** | Anropa `builder.insertImage()` upprepade gånger efter att ha flyttat till gruppens stycke varje gång | Varje anrop lägger till ett nytt barn; du kan också positionera dem med `Shape.setLeft()` / `setTop()`. |
| **Dynamiska bildvägar** | Använd `String.format("images/%s.jpg", imageName)` | Gör koden återanvändbar för batch‑bearbetning. |
| **Spara som PDF** | Byt ut `doc.save("output.pdf")` | Aspose.Words kan konvertera i farten, så du kan generera PDF‑filer direkt. |
| **Rotera gruppen** | `group.setRotation(45);` | Användbart för dekorativa vattenstämplar eller stiliserade rubriker. |

---

## Förväntat resultat och verifiering

Efter att ha kört klassen:

1. `output.docx` visas i projektmappen.  
2. När du öppnar filen visas en enda sida med en grupperad form.  
3. Inuti gruppen är rektangeln placerad längst upp till vänster, och bilden sitter direkt under den.  
4. När du markerar gruppen i Word markeras båda barnobjekten, vilket bekräftar att de verkligen är grupperade.

Om något av dessa steg misslyckas, dubbelkolla bildvägen och se till att Aspose.Words‑JAR‑filen finns på din classpath.

---

## Slutsats

Du vet nu **hur man skapar tomt Word-dokument** och hur du kan berika den med en grupperad form som innehåller en rektangel och en inbäddad bild. Genom att behärska **hur man skapar grupp**, **infoga rektangelform**, och **lägga till bild i Word-dokument**, kan du bygga sofistikerade Word‑mallar helt i kod – ingen manuell justering behövs.

Redo för nästa utmaning? Prova att lägga till textrutor i samma grupp, eller experimentera med olika formstilar för att matcha ditt företags varumärke. Du kan till och med generera ett helt rapportbibliotek där varje dokument börjar med exakt detta layout.

Lycka till med kodandet, och dela gärna dina egna varianter i kommentarerna nedan!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}