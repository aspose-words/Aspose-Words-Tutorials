---
category: general
date: 2026-09-11
description: Hur man redigerar diagram i ett Word‑dokument med Java – lär dig att
  uppdatera diagraminställningar, aktivera diagramrutnät, ändra diagramalternativ
  och spara det uppdaterade dokumentet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: sv
lastmod: 2026-09-11
og_description: Hur man redigerar diagram i ett Word‑dokument med Java. Följ den här
  guiden för att uppdatera diagraminställningar, aktivera diagramrutnät, ändra diagramalternativ
  och spara det uppdaterade dokumentet.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Hur man redigerar diagram i ett Word‑dokument med Java – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Hur man redigerar diagram i ett Word‑dokument med Java
url: /sv/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man redigerar diagram i ett Word‑dokument med Java

Om du behöver **redigera diagram** i en Word‑fil, visar den här guiden de exakta stegen. Du kommer att lära dig hur du uppdaterar diagraminställningar, aktiverar diagramrutnät, ändrar diagramalternativ och slutligen **sparar det uppdaterade dokumentet** utan att förlora någon formatering.

Att arbeta med diagram programatiskt känns ofta som en svart‑låda‑operation, särskilt när du vill finjustera visuella detaljer som graderingar eller rutnät. Denna handledning täcker allt du behöver veta, från att läsa in dokumentet till att spara ändringarna. Inga externa verktyg krävs—bara Aspose.Words for Java‑biblioteket (version 24.9 eller senare).

I slutet av den här artikeln kommer du att kunna:

* Ladda en `.docx`‑fil som innehåller ett diagram.
* Hitta diagramformen och ändra dess egenskaper.
* Aktivera diagramrutnät (graderingar) och justera andra alternativ.
* **Spara det uppdaterade dokumentet** till en ny fil.

## Förutsättningar

* Java 17 eller senare installerat på din maskin.  
* Maven eller Gradle för att hantera beroenden.  
* Aspose.Words for Java 24.9+ (versionen som introducerade `setShowGraduations`).  
* Ett Word‑dokument (`input.docx`) som redan innehåller minst ett diagram.

Om du inte är bekant med Aspose.Words, tänk på det som ett fullständigt API som låter dig läsa, ändra och skriva Word‑dokument programatiskt—likt hur du skulle manipulera ett DOM i en webbläsare.

## Steg 1: Ställ in projektet och importera biblioteket

Skapa ett nytt Maven‑projekt eller lägg till beroendet i ett befintligt projekt:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Proffstips:** Använd den senaste stabila versionen för att säkerställa att du har `setShowGraduations`‑metoden. Äldre versioner kommer inte att kompilera.

## Steg 2: Läs in Word‑dokumentet som innehåller ett diagram

Den första åtgärden i alla **redigera diagram**‑arbetsflöden är att läsa in källfilen. Aspose.Words representerar hela dokumentet med klassen `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

`Document`‑objektet ger dig åtkomst till varje nod i filen, inklusive former, tabeller och stycken.

## Steg 3: Hitta den första diagramformen i dokumentet

Diagram lagras som `Shape`‑noder vars renderare är ett `Chart`. För att redigera ett diagram måste du först hämta den noden.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Om dokumentet innehåller flera diagram, iterera över `shapes` och kontrollera `chartShape.getChart() != null` innan du castar. Detta förhindrar `ClassCastException` och säkerställer att du **ändrar diagramalternativ** endast på giltiga diagramobjekt.

## Steg 4: Aktivera diagramrutnät (graderingar) – en ny egenskap i version 24.9

Egenskapen `setShowGraduations` växlar synligheten för mindre rutnät på värdeaxeln. Att aktivera dem förbättrar ofta läsbarheten för täta datamängder.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Varför detta är viktigt:** Rutnät ger betraktaren en visuell referens för varje datapunkt, vilket gör trender enklare att upptäcka. Standardvärdet är `false`, så du måste uttryckligen aktivera dem när det behövs.

Du kan också anpassa andra aspekter, såsom huvudrutnät, axeltitlar eller legendplacering. Nedan är ett exempel på att ändra diagramtiteln och legendens position—båda en del av **ändra diagramalternativ**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Steg 5: Spara dokumentet med de uppdaterade diagraminställningarna

Efter att ha ändrat diagrammet, spara ändringarna. Detta steg slutför fasen **spara uppdaterat dokument**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

När programmet körs skapas `output.docx` där diagrammet nu visar rutnät, en ny titel och en flyttad legend. Öppna filen i Microsoft Word för att verifiera de visuella förändringarna.

## Fullständig källkod (körbar)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Förväntat resultat

När du öppnar `output.docx`:

* Diagrammet visar mindre rutnät på värdeaxeln.  
* Titeln visar **“Sales Overview 2026”**.  
* Legenden visas längst ner i diagrammet.

Om det ursprungliga diagrammet redan hade rutnät, förblir den visuella utformningen oförändrad, vilket bekräftar att koden är **idempotent**.

## Vanliga frågor och hantering av kantfall

### Vad händer om dokumentet saknar diagram?

Att försöka casta en form som inte är ett diagram kommer att kasta en `ClassCastException`. Skydda mot detta genom att kontrollera formtypen:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Hur redigerar man ett specifikt diagram istället för det första?

Iterera genom `shapes` och matcha en känd titel eller en alternativ identifierare:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Kan jag inaktivera rutnät igen senare?

Ja, sätt helt enkelt egenskapen till `false`:

```java
chart.setShowGraduations(false);
```

### Fungerar detta med `.doc` (binära) filer?

Aspose.Words abstraherar filformatet, så samma kod fungerar för `.doc` och `.docx`. Vissa nyare diagramfunktioner (som graderingar) lagras dock endast i OOXML‑formatet, så du ser effekten endast när du sparar som `.docx`.

## Tips för produktionsklar kod

* **Validera inmatningsvägar** – använd `Files.exists(Paths.get(inputPath))` innan du läser in.  
* **Omslut API‑anrop** i try‑catch‑block för att visa `Exception`‑detaljer, särskilt när du hanterar korrupta dokument.  
* **Frigör resurser** – även om Aspose.Words hanterar minnet, kan ett anrop till `doc.close()` (eller användning av try‑with‑resources om tillgängligt) frigöra inhemska handtag tidigare.  
* **Versionskontroll** – säkerställ att runtime‑bibliotekets version är ≥ 24.9 innan du anropar `setShowGraduations`. Du kan fråga `License.getVersion()` om du behöver ett programatiskt skydd.

## Slutsats

Du vet nu **hur man redigerar diagram**‑objekt i ett Word‑dokument med Java. Processen—läs in dokumentet, hitta diagrammet, aktivera diagramrutnät, ändra diagramalternativ och **spara det uppdaterade dokumentet**—täcker de vanligaste scenarierna för programmatisk diagrammanipulation.

Härifrån kan du utforska ytterligare anpassningar som att ändra färger på dataserier, tillämpa diagramstilar eller exportera diagrammet som en bild. Varje uppgift följer samma mönster: hämta `Chart`‑instansen, justera dess egenskaper och **spara det uppdaterade dokumentet**.

Lycka till med kodandet, och känn dig fri att experimentera med andra diagraminställningar för att passa dina rapporteringsbehov!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hur man sparar dokument som PDF med Aspose.Words för Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Ställ in standardalternativ för datamärkningar i ett diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}