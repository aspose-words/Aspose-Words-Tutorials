---
category: general
date: 2026-05-04
description: Hur man ställer in upplösning för Markdown‑export från Word. Lär dig
  markdown‑bildupplösning, hur man exporterar ekvationer och sparar Word som markdown
  i Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: sv
og_description: Hur man ställer in upplösning för Markdown‑export från Word. Denna
  guide visar bildupplösning i markdown, export av ekvationer och hur man sparar Word
  som markdown.
og_title: Hur man ställer in upplösning när man sparar Word som Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Hur man ställer in upplösning när man sparar Word som Markdown
url: /sv/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så ställer du in upplösning när du sparar Word som Markdown

Har du någonsin funderat på **hur man ställer in upplösning** för bilder som visas i en Markdown‑fil som genererats från ett Word‑dokument? Du är inte ensam. Många utvecklare stöter på problem när de standardrasteriserade matematikbilderna ser suddiga ut, särskilt på hög‑DPI‑skärmar.  

I den här handledningen går vi igenom de exakta stegen för att kontrollera *markdown‑bildupplösning* samtidigt som vi visar **hur man exporterar ekvationer** som LaTeX, och slutligen hur man **sparar Word som markdown** med Aspose.Words för Java. I slutet har du en skarp, produktionsklar Markdown‑fil som renderar ekvationer tydligt och bilder med den kvalitet du behöver.

## Förutsättningar

- Java 17 (eller någon nyare JDK)  
- Aspose.Words for Java 23.6 eller nyare – du kan hämta det från Maven Central  
- Ett Word‑dokument (`.docx`) som innehåller OfficeMath‑objekt (ekvationer) och eventuellt rasterbilder  
- Grundläggande kunskap om Maven/Gradle och en IDE (IntelliJ IDEA, Eclipse, VS Code, etc.)

Inga extra bibliotek krävs; allt annat hanteras av Aspose.Words.

---

## Så ställer du in upplösning för Markdown‑export

> **Proffstips:** Den upplösning du väljer påverkar direkt filstorleken på de genererade bilderna. Ett värde på **300 dpi** är en bra balans för de flesta webbaserade Markdown‑visare.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

`setImageResolution(int dpi)`‑anropet är kärnan i **hur man ställer in upplösning**. Det instruerar Aspose.Words att rasterisera alla reservbilder (t.ex. när en ekvation inte kan representeras i ren LaTeX) med det angivna antalet punkter per tum. Om du utelämnar den här raden återgår biblioteket till sin standard på 220 dpi, vilket kan se suddigt ut på Retina‑skärmar.

### Varför använda LaTeX för ekvationer?

När du exporterar ekvationer som LaTeX (`OfficeMathExportMode.LATEX`) innehåller den resulterande Markdown‑koden rå LaTeX‑kod omsluten av `$…$` eller `$$…$$`. De flesta moderna Markdown‑renderare (GitHub, GitLab, MkDocs med MathJax) renderar dessa som skarpa, skalbara vektorgrafik—ingen upplösningsbekymmer där. Upplösningsinställningen är bara relevant för **markdown‑bildupplösning** av eventuella raster‑reservbilder, såsom inbäddade diagram eller bilder som inte stöds nativt i Markdown.

---

## Så använder du Markdown‑bildupplösning effektivt

Om du behöver bädda in vanliga bilder (t.ex. skärmdumpar) i ditt Word‑dokument, konverteras de till PNG av Aspose.Words. Samma `setImageResolution`‑metod gäller, vilket säkerställer att dessa PNG‑filer ärver den DPI du anger. Här är en snabb checklista:

1. **Välj en DPI som matchar din målplattform** – 72 dpi för äldre webb, 150 dpi för standardskärmar, 300 dpi för utskriftskvalitet‑PDF:er.  
2. **Testa resultatet** – öppna den genererade `.md`‑filen i din föredragna visare och zooma in för att verifiera skärpan.  
3. **Tänk på filstorlek** – högre DPI ger större PNG‑filer; om bandbredd är ett bekymmer, experimentera med 200 dpi och jämför.

---

## Så exporterar du ekvationer som LaTeX

`saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);`‑raden instruerar Aspose.Words att översätta varje OfficeMath‑objekt till LaTeX. Detta är den rekommenderade metoden eftersom:

- **Skalbarhet** – LaTeX renderas i vilken storlek som helst utan att förlora kvalitet.  
- **Redigerbarhet** – Du kan senare justera LaTeX‑koden direkt i Markdown‑filen.  
- **Kompatibilitet** – De flesta statiska webbplatsgeneratorer och dokumentationsverktyg stödjer redan LaTeX‑rendering.

Om du någonsin behöver den gamla bildbaserade reservlösningen, byt helt enkelt till `OfficeMathExportMode.IMAGE`. I så fall blir den DPI du angivit ännu viktigare.

---

## Spara Word som Markdown – Fullt end‑to‑end‑exempel

Nedan är ett komplett, körbart Maven‑projektutdrag som demonstrerar hela flödet, från beroendedeklaration till körning.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Förväntat resultat:** `MathExport.md` kommer att innehålla LaTeX‑block för varje ekvation, och eventuella inbäddade bilder visas som PNG‑länkar med en DPI på 300. Öppna filen i en Markdown‑visare som stödjer MathJax (t.ex. VS Code med tillägget Markdown Preview Enhanced) så bör du se perfekt skarpa ekvationer och bilder.

---

## Vanliga frågor & specialfall

### Vad händer om jag behöver en annan DPI för bara en bild?

Aspose.Words tillämpar DPI globalt via `setImageResolution`. För att hantera DPI per bild måste du efterbearbeta den genererade Markdown‑filen: ersätta PNG‑filerna med högre‑upplösta versioner och justera bildlänkarna manuellt. Inte idealiskt, men genomförbart för ett fåtal specialfall.

### Fungerar detta på Linux/macOS?

Absolut. Biblioteket är rent Java, så samma kod körs var som helst JDK‑t finns. Se bara till att filvägarna använder framåtsnedstreck eller `Paths.get(...)` för plattformsoberoende hantering.

### Vad sägs om SVG‑utdata?

Om du föredrar vektorbilder för diagram kan du sätta `saveOptions.setExportImagesAsSvg(true);`. SVG‑filer ignorerar DPI, så problemet med **markdown‑bildupplösning** försvinner. Dock hanterar inte alla Markdown‑renderare SVG på ett bra sätt, så testa din målplattform först.

### Kan jag bädda in den genererade Markdown‑filen i en statisk webbplatsgenerator?

Ja. Utdata är en ren `.md`‑fil med standard‑Markdown‑syntax plus LaTeX‑avgränsare. De flesta generatorer (Jekyll, Hugo, MkDocs) accepterar den direkt. Kom bara ihåg att aktivera MathJax eller KaTeX i din webbplatskonfiguration.

---

## Slutsats

Vi har gått igenom **hur man ställer in upplösning** för bilder när du **sparar Word som markdown**, utforskat nyanserna kring **markdown‑bildupplösning**, demonstrerat **hur man exporterar ekvationer** som LaTeX, och visat den fullständiga Java‑implementationen. Genom att justera `setImageResolution` och välja rätt `OfficeMathExportMode` får du exakt kontroll över både visuell kvalitet och filstorlek.

Redo för nästa steg? Prova att kombinera detta tillvägagångssätt med Aspose.PDF för att konvertera samma Word‑källa direkt till PDF, eller experimentera med `setExportImagesAsSvg(true)` för vektorbaserad grafik. Teknikerna du har lärt dig här är byggstenar för vilken automatiserad dokumentationspipeline som helst.

Om du fann den här guiden användbar, ge den ett stjärnmärke på GitHub, dela den med kollegor, eller lämna en kommentar nedan med dina egna tips. Lycka till med kodandet!  

![Exempel på hur man ställer in upplösning](resolution.png "Hur man ställer in upplösning när man sparar Word som Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}