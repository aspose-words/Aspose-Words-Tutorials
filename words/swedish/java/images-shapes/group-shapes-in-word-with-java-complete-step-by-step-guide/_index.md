---
category: general
date: 2026-08-01
description: Gruppera former i Word med Java med Aspose.Words. Lär dig hur du grupperar
  former och snabbt infogar en rektangel med ett komplett kodexempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: sv
lastmod: 2026-08-01
og_description: Gruppera former i Word med Java. Den här guiden visar hur du grupperar
  former, infogar en rektangel och sparar en DOCX med Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Gruppera former i Word med Java – Fullständig programmeringsgenomgång
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Gruppera former i Word med Java – Komplett steg‑för‑steg guide
url: /sv/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruppera former i Word med Java – Komplett steg-för-steg guide

Om du behöver **gruppera former i Word** med Java, så har den här guiden dig täckt. Oavsett om du bygger en rapportgenerator eller en dynamisk mallmotor, gör gruppering av former dina dokument snygga och håller relaterad grafik tillsammans.

Under de kommande minuterna kommer du att se exakt **hur man grupperar former** och **infogar rektangel‑former** med Aspose.Words, samt ett antal praktiska tips som sparar dig från vanliga fallgropar. Klar att förvandla de lösa rektanglarna och ellipserna till en prydlig grupp? Låt oss dyka ner.

## Vad den här handledningen täcker

* De minsta förutsättningarna (Java 17+, Aspose.Words 24.10 eller senare).  
* Ett komplett, körbart Java‑program som skapar ett Word‑dokument, infogar en rektangel och en ellips, grupperar dem, döljer gruppen om du vill, och sparar filen.  
* Varför varje API‑anrop är viktigt, inte bara vad det gör.  
* Hantering av kantfall för äldre Aspose.Words‑versioner och för gruppering av fler än två former.  
* Förväntad utdata och ett snabbt sätt att verifiera resultatet.

När du är klar kommer du kunna klistra in detta kodsnutt i vilket Java‑projekt som helst och börja gruppera former i Word utan att leta igenom spridda dokument.

---

## Förutsättningar

| Requirement | Varför det är viktigt |
|-------------|-----------------------|
| **Java 17+** | Moderna språkfunktioner och bättre prestanda. |
| **Aspose.Words for Java 24.10+** | Metoden `setHidden` som används senare finns endast från och med denna version. |
| **A Maven or Gradle build** | Gör beroendehantering smärtfri. |
| **An IDE (IntelliJ, Eclipse, VS Code)** | Användbart för snabb testning, men vilken textredigerare som helst fungerar. |

Lägg till Aspose.Words Maven‑beroendet i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Om du föredrar Gradle är motsvarigheten:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Steg 1: Skapa ett nytt dokument och en builder

Först skapar vi ett tomt `Document` och en `DocumentBuilder`. Buildern är arbetshästen som låter oss infoga former, text och mer.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Varför detta steg?*  
`Document` representerar hela DOCX‑filen, medan `DocumentBuilder` erbjuder ett bekvämt cursor‑baserat API. Utan en builder skulle du behöva manipulera låg‑nivå nodsamlingar manuellt – något som är lätt att göra fel på.

---

## Steg 2: Infoga en rektangel‑form (och en ellips)

Nu lägger vi till de två grundformerna vi vill gruppera. Lägg märke till anropet **insert rectangle shape** – detta är exakt det sekundära nyckelordet du söker.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Några saker att ha i åtanke:

* Bredden (`100`) och höjden (`50`) mäts i punkter (1 pt ≈ 1/72 tum). Justera dem för att passa din layout.  
* Rektangeln ritas först, så den ligger bakom ellipsen som standard. Om du behöver omvänd ordning, infoga ellipsen först.  
* Båda formerna ärver builderns aktuella formatering (färg, linjestil). Du kan anpassa dem innan gruppering om du vill.

---

## Steg 3: Hur man grupperar former med Aspose.Words

Här är kärnan i handledningen—**hur man grupperar former**. API‑metoden `insertGroupShape` tar en array av befintliga former och returnerar en ny `Shape` som representerar gruppen.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Varför använda en grupp?

* En grupp flyttas som en enhet, vilket bevarar relativ placering.  
* Du kan applicera transformationer (rotation, skalning) på hela mängden med ett anrop.  
* Gruppering förenklar senare redigering – avgruppera senare om du behöver justera enskilda element.

---

## Steg 4 (valfritt): Dölj gruppen i dokumentvyn

Om du inte vill att gruppen ska visas när användaren öppnar dokumentet i Word, kan du dölja den. Detta steg är valfritt men praktiskt för bakgrundsgrafik eller vattenstämplar.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**Vad händer om du använder en äldre Aspose.Words‑version?**  
Metoden `setHidden` kompilerar inte. I så fall kan du uppnå en liknande effekt genom att sätta formens `WrapType` till `NONE` och flytta den bakom textlagret:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

Det är lite mer omständligt, men det håller fortfarande gruppen ur läsarens väg.

---

## Steg 5: Spara dokumentet

Till sist skriver du dokumentet till disk. Ändra sökvägen till där du vill att filen ska hamna.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

När du öppnar `GroupShapeResult.docx` i Microsoft Word kommer du att se en rektangel och en ellips snyggt sammanslagna. Om du sätter `setHidden(true)` blir gruppen osynlig i editorn men finns fortfarande i filen (användbart för programmatisk bearbetning senare).

---

## Fullt fungerande exempel

När allt sätts ihop, här är den kompletta, fristående Java‑klassen som du kan kopiera‑klistra in i ditt projekt:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Förväntad utdata:** En fil med namnet `GroupShapeResult.docx` som innehåller en enda grupp som håller en blåfylld rektangel och en rödmarkerad ellips (standardfärger). Om du öppnar dokumentet, markerar gruppen och högerklickar → **Group → Ungroup**, så ser du de två ursprungliga formerna återkomma.

---

## Vanliga frågor & kantfall

### 1. Kan jag gruppera fler än två former?

Absolut. Skicka bara en större array till `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

API:n skalar linjärt; den enda begränsningen är minnet för extremt stora grupper.

### 2. Vad händer om jag behöver ändra gruppens position efter skapandet?

Använd gruppens `setLeft`- och `setTop`-metoder, precis som för någon annan form:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Eftersom gruppen beter sig som en enskild form, flyttas alla underordnade former tillsammans.

### 3. Hur applicerar jag en kantlinje eller fyllning på hela gruppen?

Gruppen själv kan ha formatering, men den påverkar inte barnen direkt. Om du vill ha en gemensam kantlinje, omslut formerna i en rektangel först och gruppera sedan allt. Alternativt, iterera över varje barnform och sätt samma `fillColor` eller `strokeWeight`.

### 4. Påverkar `setHidden(true)` utskrift?

Dolda former **skrivs inte** ut som standard i Word, vilket kan vara användbart för vattenstämplar eller mallmarkörer. Om du behöver att formen skrivs ut men förblir osynlig på skärmen, måste du använda en annan metod (t.ex. sätta dess opacitet till 0%).

---

## Proffstips från frontlinjen

* **Namnge dina former** – `groupShape.setName("HeaderGraphics");` gör felsökning enklare när du senare hämtar former efter namn.  
* **Återanvänd buildern** – Efter att ha infogat en grupp stannar builderns markör där gruppen placerades, så du kan fortsätta lägga till stycken direkt efter gruppen utan att återställa positionen.  
* **Version-skydd** – Om du levererar ett bibliotek som kan köras på äldre Aspose.Words‑versioner, omge anropet `setHidden` med en try‑catch för `NoSuchMethodError` och falla tillbaka på `WrapType.NONE`‑tricket som visades tidigare.  
* **Prestandatips** – När du genererar tusentals

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Använda dokumentformer i Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Skapa Word-dokument Java – Lägg till rektangel‑form med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rendera former i Aspose.Words för Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}