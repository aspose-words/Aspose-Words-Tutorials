---
category: general
date: 2026-04-28
description: Skapa PDF‑UA‑dokument med Aspose.Words för Java. Lär dig att läsa in
  docx med återställning, exportera ekvationer till LaTeX, spara markdown från Word
  och hämta saknade teckensnitt.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: sv
og_description: Skapa PDF UA-dokument med Aspose.Words för Java. Steg‑för‑steg‑guide
  som täcker återställningsladdning, LaTeX‑export, Markdown‑sparande och hämtning
  av saknade teckensnitt.
og_title: Skapa PDF UA-dokument – Komplett Java-handledning
tags:
- Aspose.Words
- Java
- PDF/UA
title: Skapa PDF UA-dokument med Aspose.Words – Fullständig Java-guide
url: /sv/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa PDF UA‑dokument – Komplett Java‑handledning

Behöver du **skapa ett PDF UA‑dokument** från en Word‑fil samtidigt som du hanterar korrupt innehåll? I den här handledningen går vi igenom hur du laddar en DOCX med återställning, exporterar ekvationer till LaTeX, sparar Markdown från Word och hämtar saknade teckensnitt – allt med Aspose.Words för Java.  

Om du någonsin har stirrat på en trasig .docx och undrat varför din PDF inte är tillgänglig, är du på rätt plats. När du är klar har du en fullt kompatibel PDF/UA 1‑fil, en Markdown‑version som innehåller LaTeX‑ekvationer och en tydlig lista över eventuella teckensnittssubstitutioner som skedde under inläsningen.

## Vad du behöver

- **Aspose.Words for Java** (senaste versionen 2026) – lägg till Maven/Gradle‑beroendet eller JAR‑filen i din classpath.  
- Java 17 eller senare (API:t använder streams, så en aktuell JDK rekommenderas).  
- En exempel‑`input.docx` som kan innehålla korrupta sektioner, Office Math‑ekvationer och flytande former.  

Inga extra bibliotek behövs; allt finns i Aspose.Words.

---

## Steg 1 – Ladda DOCX med återställningsläge  

När ett dokument är delvis skadat kastar standardladdaren ett undantag. Genom att aktivera återställningsläge säger du åt Aspose.Words att fortsätta och rapportera varningar istället.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Varför detta är viktigt:* Återställningsläge förhindrar att hela din pipeline bryts på grund av ett enda felaktigt stycke. Det fyller även i `doc.getWarnings()` så att du senare kan **hämta saknade teckensnitt** och andra problem.

---

## Steg 2 – Exportera ekvationer till LaTeX i en Markdown‑fil  

De flesta utvecklare älskar Markdown för dokumentation, men Words inbyggda ekvationer är svåra att kopiera. Aspose.Words kan översätta dem direkt till LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Proffstips:* Callback‑funktionen ser till att varje extraherad bild hamnar under `imgs/`. Detta efterliknar hur GitHub renderar Markdown – rent och portabelt.

---

## Steg 3 – Skapa PDF / UA‑dokument med korrekt taggning  

PDF/UA (Universal Accessibility) är obligatoriskt för många offentliga projekt. Följande alternativ får Aspose.Words att tagga flytande former korrekt och sätta PDF/UA‑kompatibilitetsflaggan.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Vad du kommer att se:* När du öppnar `output.pdf` i Adobe Acrobat Pro visas “PDF/UA‑1 compliant” under dokumentegenskaperna. Alla flytande former (textrutor, bilder) får lämpliga taggar för skärmläsare.

---

## Steg 4 – Justera en forms skugga (valfri styling)  

Inte ett krav för tillgänglighet, men att justera visuella detaljer kan vara praktiskt för interna rapporter.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Varför bry sig?* Om PDF‑en också är ett marknadsföringsmaterial ger en subtil skugga layouten en mer polerad känsla utan att bryta mot kraven.

---

## Steg 5 – Hämta saknade teckensnitt och andra varningar  

Under återställningsladdningen registrerar Aspose.Words alla teckensnittssubstitutioner. Att lista dem hjälper dig avgöra om du ska bädda in rätt teckensnitt eller acceptera reservvarianten.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Typisk utskrift* (din konsol visar något i stil med):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Om du ser kritiska teckensnitt saknas, överväg att installera dem på servern eller bädda in dem via `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Fullt fungerande exempel  

Nedan är den kompletta, körklara Java‑klassen. Klistra in den i din IDE, justera sökvägarna och tryck på **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Förväntade resultat**

| Utdata | Beskrivning |
|--------|-------------|
| `output.md` | Markdown‑fil där varje Office Math‑ekvation visas som LaTeX (`$…$`). Bilder lagras under `imgs/`. |
| `output.pdf` | PDF/UA‑1‑kompatibelt dokument; öppna i Acrobat för att se “PDF/UA‑1” under Arkiv → Egenskaper → Standarder. |
| Konsol | Lista över eventuella saknade teckensnitt, t.ex. “Missing: Calibri → substituted: Arial”. |

---

## Vanliga frågor (FAQ)

**Q: Fungerar detta med äldre versioner av Aspose.Words?**  
A: Enums `RecoveryMode`, `OfficeMathExportMode.LATEX` och `PdfCompliance.PDF_UA_1` introducerades i 22.8. Om du använder en äldre version, uppgradera – tillgänglighetsfunktionerna har inte bakåtkopierats.

**Q: Vad gör jag om jag vill bädda in originalteckensnitten istället för substitution?**  
A: Sätt `pdfOptions.setEmbedFullFonts(true)` och se till att teckensnittsfilerna är åtkomliga via JVM:s teckensnittssökväg.

**Q: Kan jag exportera till andra markup‑format (t.ex. HTML) och behålla LaTeX‑ekvationer?**  
A: Ja. Använd `HtmlSaveOptions` och sätt `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – samma enum fungerar över format.

**Q: Min DOCX innehåller många flytande former; kommer de alla att taggas?**  
A: Med `setExportFloatingShapesAsInlineTag(true)` omsluter Aspose.Words varje flytande form i en `<Figure>`‑tagg för PDF/UA, vilket uppfyller de flesta skärmläsarkontroller.

---

## Sammanfattning  

Vi har just visat hur du **skapar ett PDF UA‑dokument** från en Word‑källa, samtidigt som du **laddar docx med återställning**, **exporterar ekvationer till LaTeX**, **sparar markdown från Word** och **hämtar saknade teckensnitt**. Koden är helt självständig, körs i vilken Java 17+‑miljö som helst och producerar tillgångar som är redo för både tillgänglighetsgranskning och utvecklare.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}