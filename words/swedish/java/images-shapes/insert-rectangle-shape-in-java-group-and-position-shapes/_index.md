---
category: general
date: 2026-07-26
description: Infoga rektangelform i Java med Aspose.Words. Lär dig hur du ställer
  in formens storlek, placerar formen och hur du grupperar former i en DOCX‑fil.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: sv
lastmod: 2026-07-26
og_description: Infoga rektangelform i Java för att skapa rika DOCX‑grafik. Följ den
  här steg‑för‑steg‑guiden för att enkelt ställa in formens storlek, placera formen
  och gruppera former.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Infoga rektangelform i Java – Behärska gruppering och positionering
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Infoga rektangelform i Java – gruppera och placera former
url: /sv/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga rektangelform i Java – Gruppera och positionera former

Har du någonsin behövt **infoga rektangelform** i ett Word‑dokument medan du skriver Java‑kod? Du är inte ensam—utvecklare som bygger rapporter, fakturor eller anpassade mallar stöter på detta problem hela tiden. Den goda nyheten är att med några rader Aspose.Words for Java kan du **infoga rektangelform**, **ange formens storlek**, **positionera formen**, och till och med **hur man grupperar former** så att de rör sig som en enhet.

I den här guiden går vi igenom hela processen från att skapa ett tomt dokument till att spara en `.docx` som innehåller två rektanglar snyggt grupperade tillsammans. I slutet vet du **hur man lägger till rektangel**‑objekt, styr deras dimensioner, placerar dem exakt där du vill, och samlar dem i en återanvändbar grupp. Inga externa bibliotek utöver Aspose.Words behövs, och koden fungerar med Java 8‑plus.

## Förutsättningar

- Java 8 eller nyare installerat (jag använder JDK 17, men allt som stödjer Maven fungerar)
- Aspose.Words for Java 23.9 eller senare – lägg till beroendet i din `pom.xml` eller ladda ner JAR‑filen
- Grundläggande förståelse för Java‑syntax (om du kan skriva en `main`‑metod, är du klar)
- En IDE eller textredigerare efter eget val (IntelliJ IDEA, Eclipse, VS Code…)

> **Proffstips:** Om du använder Maven ser beroendet ut så här:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nu när vi har lagt grunden, låt oss dyka ner i koden.

## Infoga rektangelform och ange dess storlek

Det första du gör är att skapa ett nytt `Document` och en `DocumentBuilder`. Buildern är ditt “penna” som ritar former på sidan. Nedan **infogar vi rektangelform** och sätter omedelbart **formens storlek** till 100 × 80 punkter.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Lägg märke till hur anropen `setWidth`/`setHeight` **sätter formens storlek** i punkter (1 pt ≈ 1/72 tum). Du kan också använda `setSize` om du föredrar en enda metod, men de explicita anropen gör avsikten kristallklar.

## Positionera formen på sidan

Efter att vi har den första rektangeln behöver vi **positionera formen** för den andra så att den inte överlappar den första. Positionering fungerar på samma sätt: du sätter `Left`‑ och `Top`‑egenskaperna relativt gruppens ursprung.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Om du undrar varför vi använder `setLeft` istället för `setX`, så beror det på att Aspose.Words använder det klassiska Windows GDI‑koordinatsystemet—`Left` är den horisontella förskjutningen, `Top` är den vertikala förskjutningen. Genom att ändra dessa värden kan du finjustera layouten utan att rota med tabeller eller stycken.

## Hur man grupperar former

Du kanske undrar: “Varför ens använda en grupp?” Gruppering är meningsfull när du vill att former ska flyttas tillsammans, roteras som en enhet, eller dela en gemensam stil. I kodsnutten ovan har vi redan skapat ett `GroupShape` via `builder.insertGroupShape`. Det objektet är i princip en behållare—tänk på det som en mapp som håller andra form‑filer.

> **Varför detta är viktigt:** Om du senare bestämmer dig för att lägga till en bildtext eller rotera hela diagrammet, behöver du bara ändra gruppen, inte varje rektangel individuellt.

## Hur man lägger till en rektangel i en grupp

Att **lägga till rektangel** i gruppen är helt enkelt att anropa `group.appendChild(rectangle)`. Under huven uppdaterar Aspose.Words gruppens interna samling och räknar automatiskt om den omgivande rutan så att gruppen fortfarande passar den deklarerade bredden och höjden.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Du kan experimentera med andra `ShapeType`s—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` osv.—och samma `appendChild`‑mönster fungerar.

## Spara dokumentet

Till sist sparar vi dokumentet till disk. Sökvägen kan vara absolut eller relativ; se bara till att mappen finns.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

När du öppnar `GroupShape.docx` i Microsoft Word ser du två rektanglar sida‑vid‑sida, båda låsta i en ljusgrå ruta. Att markera den grå rutan markerar båda rektanglarna samtidigt—bevis på att **hur man grupperar former** verkligen fungerar.

![Grupperade rektanglar i ett Word‑dokument](placeholder-image.png){: .center-image alt="Exempel på infogad rektangelform som visar två rektanglar grupperade i en Java‑genererad DOCX‑fil"}

*Bild‑alt‑text (SEO):* **exempel på infogad rektangelform som visar två rektanglar grupperade i en Java‑genererad DOCX‑fil**.

## Förväntat resultat

- En `GroupShape.docx`‑fil placerad i `output`‑mappen.
- I dokumentet: en 400 × 200 pt‑grupp som innehåller två rektanglar (100 × 80 pt och 120 × 60 pt) placerade på (20, 30) respektive (150, 50).
- Gruppen har en tunn svart kantlinje och en ljusgrå fyllning, vilket gör gruppering visuellt tydlig.

Öppna filen och prova att dra den grå rutan—båda rektanglarna ska röra sig tillsammans. Om de inte gör det, dubbelkolla att du anropade `group.appendChild` för varje form.

## Vanliga fallgropar & kantfall

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| **Rektanglar visas utanför sidan** | `Left`/`Top`‑värdena överstiger gruppens dimensioner | Öka gruppens storlek (`insertGroupShape(width, height)`) eller minska förskjutningarna |
| **Gruppen försvinner efter sparning** | Gruppens `Width`/`Height` är satt till 0 | Ange icke‑noll dimensioner när du anropar `insertGroupShape` |
| **Formens färger ser felaktiga ut** | Standardfyllning är transparent; Word kan rendera den som vit | Ange explicit `setFillColor` eller använd `ShapeStyle` |
| **Undantag `ArgumentOutOfRangeException`** | Användning av negativa koordinater | Håll `Left` och `Top` icke‑negativa |

## Sammanfattning & nästa steg

Vi har gått igenom hela livscykeln för **infoga rektangelform** i Java: skapa ett dokument, **ange formens storlek**, **positionera formen**, **hur man grupperar former**, och **hur man lägger till rektangel** i den gruppen. Det kompletta, körbara exemplet finns i kodblocket ovan, och du kan klistra in det direkt i ett Maven‑projekt för att se resultatet.

Vad blir nästa steg? Överväg att experimentera med:

- Lägga till text inuti varje rektangel via

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Skapa Word‑dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa tomt Word‑dokument med skuggad rektangelform – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}