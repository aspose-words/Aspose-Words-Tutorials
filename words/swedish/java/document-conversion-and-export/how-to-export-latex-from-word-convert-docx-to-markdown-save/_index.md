---
category: general
date: 2025-12-25
description: Hur man exporterar LaTeX när du konverterar DOCX till markdown och sparar
  dokumentet som PDF—steg‑för‑steg‑guide med Java‑kod.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save document as pdf
- how to save pdf
- save word as markdown
language: sv
og_description: Lär dig hur du exporterar LaTeX när du konverterar DOCX till markdown
  och sparar dokumentet som PDF med Java. Komplett kod och tips.
og_title: Hur man exporterar LaTeX från Word – Konvertera DOCX till Markdown och spara
  PDF
tags:
- Aspose.Words
- Java
- Document Conversion
title: 'Hur man exporterar LaTeX från Word: Konvertera DOCX till Markdown och spara
  som PDF'
url: /sv/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man exporterar LaTeX från Word: Konvertera DOCX till Markdown & Spara som PDF

Har du någonsin undrat **hur man exporterar LaTeX** från en Word‑fil utan att förlora någon av de avancerade ekvationerna? Du är inte ensam. I många projekt—akademiska artiklar, tekniska bloggar eller interna dokument—behöver folk extrahera LaTeX från en `.docx`, konvertera hela filen till markdown och ändå behålla en prydlig PDF‑version för distribution.  

I den här handledningen går vi igenom hela pipeline:n: **konvertera docx till markdown**, **exportera LaTeX** och **spara dokument som PDF** med hjälp av Aspose.Words for Java‑biblioteket. I slutet har du ett färdigt Java‑program som gör allt, samt ett antal praktiska tips som du kan kopiera och klistra in i din egen kodbas.

## Vad du kommer att lära dig

- Ladda ett eventuellt korrupt Word‑dokument i återställningsläge.  
- Exportera Office Math‑ekvationer som LaTeX när du sparar till markdown.  
- Spara samma dokument som PDF samtidigt som du hanterar flytande former som inline‑taggar.  
- Anpassa bildhantering vid markdown‑export (lagra bilder i en dedikerad mapp).  
- Hur man **sparar Word som markdown** och ändå behåller en högkvalitativ PDF‑kopia.  

**Förutsättningar**: Java 17 eller nyare, Maven eller Gradle, och en Aspose.Words for Java‑licens (gratis provversion fungerar för experiment). Inga andra tredjepartsbibliotek krävs.

---

## Steg 1: Ställ in ditt projekt

Först och främst—låt oss få Aspose.Words‑jar‑filen på classpath. Om du använder Maven, lägg till detta beroende i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

För Gradle är det en endradning:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Proffstips:** Använd alltid den senaste stabila versionen; den innehåller buggfixar för återställningsläge och LaTeX‑export.

Skapa en ny Java‑klass kallad `DocxProcessor.java`. Vi kommer importera allt vi behöver:

```java
import com.aspose.words.*;

import java.io.File;
import java.io.IOException;
```

---

## Steg 2: Ladda dokumentet i återställningsläge

Korrupta filer händer—särskilt när de skickas via e‑post eller molnsynkronisering. Aspose.Words låter dig öppna dem i *återställningsläge* så att du inte förlorar hela dokumentet.

```java
public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // Adjust these paths to match your environment
        String inputPath = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown = "YOUR_DIRECTORY/output.md";
        String outputPdf = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown = "YOUR_DIRECTORY/output_with_custom_images.md";

        // Step 2: Load with recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // STRICT, IGNORE are alternatives
        Document doc = new Document(inputPath, loadOptions);

        // Continue with export steps...
```

Varför använda `RecoveryMode.RECOVER`? Det försöker rädda så mycket innehåll som möjligt, men kastar fortfarande ett undantag om filen är helt oläsbar. Detta balanserar säkerhet med praktisk användning.

---

## Steg 3: Exportera LaTeX medan du konverterar DOCX till Markdown

Nu kommer stjärnan i showen: **hur man exporterar LaTeX** från Word‑dokumentet. Klassen `MarkdownSaveOptions` har en egenskap `OfficeMathExportMode` som låter dig välja LaTeX, MathML eller bildutmatning. Vi väljer LaTeX.

```java
        // Step 3: Export Office Math as LaTeX during markdown conversion
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);
```

Den resulterande `output.md` kommer att innehålla LaTeX‑fragment inslagna i `$…$` för inline‑ekvationer eller `$$…$$` för display‑ekvationer. Om du öppnar filen i en markdown‑redigerare som stödjer MathJax eller KaTeX, renderas ekvationerna vackert.

> **Varför LaTeX?** För att det är det gemensamma språket inom vetenskaplig publicering. Att exportera direkt till LaTeX undviker den förlustfyllda konverteringen du skulle få om du valde bilder.

---

## Steg 4: Spara dokumentet som PDF (och bevara flytande former)

Ofta behöver du fortfarande en PDF‑version för granskare som inte är bekväma med markdown. Aspose.Words gör detta enkelt, och du kan styra hur flytande former (som diagram) hanteras.

```java
        // Step 4: Save as PDF, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);
```

Genom att sätta `ExportFloatingShapesAsInlineTag` till `true` konverteras varje flytande form till en inline `<span>`‑tagg i PDF:ens interna struktur, vilket kan vara användbart för efterföljande bearbetning (t.ex. PDF‑tillgänglighetsverktyg).

---

## Steg 5: Anpassa bildhantering vid sparande av Markdown

Som standard dumpas varje bild av Aspose.Words till samma mapp som markdown‑filen och namnges sekventiellt. Om du föredrar en prydlig `images/`‑undermapp kan du ansluta till `ResourceSavingCallback`.

```java
        // Step 5: Custom image folder for markdown export
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Place each image under YOUR_DIRECTORY/images/
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs(); // Ensure the folder exists
                args.setFileName(imageFolder + args.getFileName());
                // You could also modify the stream here or skip saving if needed
            }
        });

        doc.save(customMarkdown, customMdOptions);
```

Nu lagras alla bilder som refereras i `output_with_custom_images.md` prydligt under `images/`. Detta gör versionskontrollen renare och speglar den typiska layouten du skulle se på GitHub.

---

## Fullt fungerande exempel

När allt sätts ihop, här är den kompletta `DocxProcessor.java`‑filen som du kan kompilera och köra:

```java
import com.aspose.words.*;

import java.io.File;

public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // ==== USER CONFIGURATION ====
        String inputPath        = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown   = "YOUR_DIRECTORY/output.md";
        String outputPdf        = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown   = "YOUR_DIRECTORY/output_with_custom_images.md";

        // ==== 1️⃣ Load document with recovery mode ====
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER);
        Document doc = new Document(inputPath, loadOptions);

        // ==== 2️⃣ Export LaTeX while converting to markdown ====
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);

        // ==== 3️⃣ Save as PDF, handling floating shapes ====
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);

        // ==== 4️⃣ Custom image folder for markdown export ====
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs();
                args.setFileName(imageFolder + args.getFileName());
            }
        });
        doc.save(customMarkdown, customMdOptions);

        System.out.println("All exports completed successfully!");
    }
}
```

### Förväntad output

- `output.md` – markdown‑fil med LaTeX‑ekvationer (`$…$` och `$$…$$`).  
- `output.pdf` – högupplöst PDF, flytande former omvandlade till inline‑taggar.  
- `output_with_custom_images.md` – samma markdown men alla bilder lagrade under `images/`.  

Öppna markdown‑filen i VS Code med *Markdown Preview Enhanced*-tillägget, så ser du ekvationerna renderade exakt som de såg ut i den ursprungliga Word‑filen.

---

## Vanliga frågor (FAQ)

**Q: Fungerar detta med .doc‑filer eller bara .docx?**  
A: Ja. Aspose.Words upptäcker automatiskt formatet. Ändra bara filändelsen i `inputPath`.

**Q: Vad händer om jag behöver MathML istället för LaTeX?**  
A: Byt `OfficeMathExportMode.LATEX` mot `OfficeMathExportMode.MATHML`. Resten av pipeline:n förblir identisk.

**Q: Kan jag hoppa över PDF‑steget?**  
A: Absolut. Kommentera bara ut PDF‑blocket. Koden är modulär, så du kan **spara dokument som PDF** endast när du behöver det.

**Q: Hur hanterar jag lösenordsskyddade dokument?**  
A: Använd `LoadOptions.setPassword("yourPassword")` innan du skapar `Document`‑instansen.

**Q: Finns det ett sätt att bädda in LaTeX direkt i PDF?**  
A: Inte nativt; PDF:er förstår inte LaTeX. Du skulle behöva rendera ekvationerna som bilder först, vilket går emot syftet med en ren LaTeX‑export.

---

## Edge Cases & Tips

- **Corrupted Images**: Om en bild inte kan läsas, kommer Aspose.Words att infoga en platshållare. Du kan upptäcka detta i `ResourceSavingCallback` genom att kontrollera `args.getStream().available()`.
- **Large Documents**: För filer över 100 MB, överväg att strömma PDF‑utdata (`doc.save(outputPdf, pdfOptions)` där `outputPdf` är en `FileOutputStream`) för att undvika minnesbelastning.
- **Performance**: Aktivering av `RecoveryMode.IGNORE` snabbar upp inläsning men kan tappa innehåll. Använd `RECOVER` för ett balanserat tillvägagångssätt.
- **License Enforcement**: I provläge får varje sparat dokument ett vattenstämpel. Registrera en licens för att ta bort den—anropa bara `License license = new License(); license.setLicense("Aspose.Words.lic");` innan någon bearbetning.

---

## Slutsats

Där har du det—**hur man exporterar LaTeX** från en Word‑fil, **konverterar docx till markdown**, och **sparar dokument som PDF** i ett enda, prydligt Java‑program. Vi gick igenom inläsning i återställningsläge, LaTeX‑export, PDF‑generering med hantering av flytande former, och anpassade bildmappar för markdown.

Härifrån kan du experimentera med andra exportformat (HTML, EPUB), integrera logiken i en webbtjänst, eller automatisera batch‑bearbetning av dussintals filer. Byggstenarna är på plats, och Aspose.Words‑API:n gör det enkelt att utöka arbetsflödet.

Om du fann den här guiden hjälpsam, ge den ett stjärnmärke på GitHub, dela den med kollegor, eller lämna en kommentar nedan med dina egna justeringar. Lycka till med kodandet, och må din LaTeX alltid renderas felfritt! 

![Diagram som visar konverteringspipeline från DOCX → Markdown (med LaTeX) → PDF, alt text: "Hur man exporterar LaTeX medan man konverterar DOCX till markdown och sparar som PDF"]{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}