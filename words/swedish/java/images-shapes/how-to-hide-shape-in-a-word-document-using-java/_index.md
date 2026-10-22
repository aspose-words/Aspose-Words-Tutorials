---
category: general
date: 2026-10-04
description: Lär dig hur du döljer en form i Word med Java. Denna steg‑för‑steg‑guide
  visar dig hur du döljer en form i Word, gör en form osynlig i Word och döljer en
  form i Microsoft Word programmässigt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: sv
lastmod: 2026-10-04
og_description: Hur man döljer en form i Word med Java. Följ den här guiden för att
  dölja en form i Word, göra en form osynlig i Word och dölja en form i Microsoft
  Word med några rader kod.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Hur man döljer en form i ett Word-dokument med Java – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: Hur man döljer en form i ett Word‑dokument med Java
url: /sv/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur du döljer en form i ett Word‑dokument med Java

Om du behöver dölja en form i en Word‑fil visar den här guiden exakt **hur du döljer en form** programatiskt. Oavsett om du genererar rapporter, rensar upp mallar eller förbereder dokument för efterlevnad, kan du göra en form osynlig utan att ta bort den från filstrukturen.

I avsnitten nedan kommer du att lära dig hur du döljer en form i Word, gör en form osynlig i Word och döljer en form i Microsoft Word med hjälp av Aspose.Words för Java‑biblioteket. Tutorialen förutsätter att du har grundläggande kunskaper i Java och en fungerande Java‑utvecklingsmiljö.

## Förutsättningar

Innan du börjar, se till att du har:

* Java Development Kit (JDK) 8 eller nyare  
* Maven eller Gradle för beroendehantering  
* Aspose.Words för Java (version 23.9 eller senare) – lägg till Maven‑koordinaten `com.aspose:aspose-words:23.9`  
* Ett Word‑dokument (`input.docx`) som innehåller minst en form (t.ex. en bild, textruta eller SmartArt)

## Steg 1: Ställ in projektet och importera Aspose.Words

Skapa ett nytt Maven‑projekt eller lägg till Aspose.Words‑beroendet i ett befintligt projekt.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

Biblioteket tillhandahåller klasserna `Document`, `NodeType` och `Shape` som används i de följande stegen. Importera dem högst upp i din Java‑källfil:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## Steg 2: Läs in Word‑dokumentet

Att läsa in dokumentet är det första steget i alla Word‑bearbetningsflöden. `Document`‑konstruktorn läser filen till minnet och bevarar alla noder, inklusive dolda former.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Varför detta är viktigt*: När filen läses in skapas en DOM (Document Object Model) som låter dig navigera, fråga och modifiera enskilda noder såsom former, stycken eller tabeller.

## Steg 3: Hämta målformen

Om dokumentet innehåller flera former kan du lokalisera en specifik genom index, namn eller andra kriterier. För en snabb demonstration hämtar exemplet den första formen i dokumenthierarkin, inklusive former som är inbäddade i tabeller eller grupper.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Varför detta är viktigt*: Metoden `getChild` med `true` för flaggan `isDeep` traverserar hela nodträdet och säkerställer att du fångar former som inte är direkta barn till dokumentkroppen.

## Steg 4: Dölj formen

Genom att sätta egenskapen `Hidden` till `true` instrueras Microsoft Word att exkludera formen från layout‑renderingen samtidigt som den behålls i dokumentstrukturen. Formen kommer inte att vara synlig när filen öppnas i Word, men den förblir åtkomlig för senare bearbetning.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*Varför detta är viktigt*: Att dölja en form är användbart när du behöver bevara formen för senare aktivering (t.ex. villkorligt innehåll, versionering) utan att visa den för slutanvändaren.

## Steg 5: Spara det modifierade dokumentet

Efter att du har ändrat formens synlighet, skriv tillbaka dokumentet till disk. Du kan skriva över originalfilen eller skapa en ny; exemplet skriver till `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

När du öppnar `HiddenShape.docx` i Microsoft Word kommer formen att vara osynlig, men dokumentets layout kommer att återspegla dess dolda tillstånd (ingen extra vitrymd).

## Komplett körbart exempel

Att sätta ihop alla steg ger ett självständigt program som du kan kompilera och köra direkt.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Förväntat resultat**  
När programmet körs skapas `HiddenShape.docx`. När du öppnar den filen i Microsoft Word visas det ursprungliga innehållet, men formen som fanns i `input.docx` är inte längre synlig. Dokumentets struktur innehåller fortfarande form‑noden, som kan avdöljas senare genom att anropa `shape.setHidden(false)`.

## Varför dölja en form istället för att ta bort den?

* **Bevara metadata** – Former bär ofta alternativ text, hyperlänkar eller anpassad data som du kan behöva senare.  
* **Villkorlig visning** – Vid kopplad utskrift eller rapportgenerering kan du visa formen endast för specifika mottagare.  
* **Versionskontroll** – Genom att hålla formen dold kan du behålla en enda mall och växla synlighet programatiskt.

## Vanliga varianter och kantfall

| Situation | Rekommenderad justering |
|-----------|------------------------|
| Flera former, behöver en specifik | Använd `doc.getChild(NodeType.SHAPE, index, true)` med rätt index, eller iterera genom `doc.getChildNodes(NodeType.SHAPE, true)` och matcha på `shape.getName()` eller `shape.getAlternativeText()`. |
| Formen är inuti en GroupShape | Den djupa sökningen (`true`) når redan in i grupper, men du kan behöva kasta till `GroupShape` först om du bara vill dölja en medlem i gruppen. |
| Du vill dölja alla former | Loopa över alla form‑noder och anropa `setHidden(true)` inom loopen. |
| Kompatibilitet med äldre Word‑versioner | `Hidden`‑flaggan stöds sedan Word 2000. Äldre format (`.doc`) respekterar den också, men testa på målversionen om du stöter på oväntade layout‑ändringar. |

**Proffstips:** Efter att ha dolt en form kan du anropa `doc.updatePageLayout()` om du behöver att sidlayouten räknas om innan sparning. Detta är sällan nödvändigt eftersom Word automatiskt omflödar innehållet vid öppning, men det kan vara användbart för server‑sidig förhandsgranskning.

## Testa resultatet programatiskt

Om du vill bekräfta att formen är dold utan att öppna Word kan du fråga efter egenskapen efter sparning:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## Nästa steg

Nu när du vet hur du döljer en form i Word, överväg dessa relaterade ämnen:

* **Dölj form i Word baserat på anpassade villkor** – Kombinera `Hidden`‑flaggan med kopplade fält för att växla synlighet per mottagare.  
* **Gör en form osynlig i Word med VBA** – För on‑device‑automation kan samma egenskap sättas via VBA (`Shape.Visible = msoFalse`).  
* **Dölj former i Microsoft Word i bulk** – Processa en mapp med dokument i en loop som applicerar samma kod på varje fil.  

Att utforska dessa tillägg fördjupar din kontroll över Word‑dokumentautomatisering och håller dina genererade filer rena och professionella.

--- 

*Denna tutorial följer Google Developer Documentation Style Guide, använder aktiv röst, andra‑personsperspektiv och erbjuder en komplett, citeringsvärd lösning för både sökmotorer och AI‑assistenter.*

## Vad bör du lära dig härnäst?


Följande tutorials täcker närliggande ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}