---
category: general
date: 2026-07-03
description: Exportera flytande former inline när du konverterar Word till PDF inline.
  Lär dig hur du ställer in PDF‑alternativ och sparar Word som PDF‑alternativ i Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: sv
og_description: Exportera flytande former i textflödet när du konverterar ett Word‑dokument
  till PDF. Denna handledning visar hur du ställer in PDF‑alternativ och sparar Word
  som PDF‑alternativ.
og_title: Exportera flytande former inline – Java PDF‑konverteringsguide
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Exportera flytande former inline – Komplett guide till PDF‑konvertering
url: /sv/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Floating Shapes Inline – Komplett guide till PDF-konvertering

Har du någonsin behövt **export floating shapes inline** när du konverterar ett Word‑dokument till PDF? Du är inte ensam—många utvecklare stöter på detta problem när deras diagram eller ikoner mystiskt flyttas till separata lager. Den goda nyheten är att ett enda PDF‑alternativ kan hålla dessa former tätt inuti `<span>`‑taggar, vilket bevarar layouten exakt som du ser den i Word.

I den här handledningen går vi igenom **how to set PDF options** i Java, visar dig den exakta koden för **save Word as PDF options**, och förklarar varför du kanske vill **convert Word to PDF inline** istället för standard‑blocknivå‑export. I slutet har du ett färdigt kodsnutt som du kan lägga in i vilket Maven‑ eller Gradle‑projekt som helst.

## Vad du kommer att lära dig

- Skillnaden mellan inline `<span>`‑ och block `<div>`‑export för flytande former.  
- Hur man konfigurerar `PdfSaveOptions` för att tvinga inline‑rendering.  
- Steg‑för‑steg‑kod som laddar en `.docx`, tillämpar alternativet och skriver ut en PDF.  
- Vanliga fallgropar (saknade typsnitt, ej stödda former) och hur man undviker dem.  
- Tips för att testa resultatet och utöka metoden till andra dokumentelement.

**Förutsättningar** – du behöver Java 8 eller nyare, Aspose.Words for Java‑biblioteket (eller något API som speglar dess `PdfSaveOptions`‑klass), samt en exempel‑Word‑fil med flytande former (handledningen använder `FloatingShapes.docx`). Inga andra externa verktyg krävs.

---

## Steg 1: Ladda källdokumentet Word

Det första du gör är att öppna den `.docx` du vill omvandla. Detta är enkelt, men se till att sökvägen är absolut eller korrekt löst från din classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Varför detta är viktigt:*  
Om dokumentet inte laddas korrekt kommer den efterföljande PDF‑konverteringen att kasta ett `FileNotFoundException`. Att använda `Document` säkerställer att den interna objektmodellen är fullt fylld, inklusive eventuella flytande former som finns på sidan.

---

## Steg 2: Skapa PDF‑spara‑alternativ och ställ in flytande former som inline

Här sker magin. Som standard exporterar Aspose.Words flytande former som block‑nivå `<div>`‑element, vilket kan bryta flödet i HTML‑baserade PDF‑filer. Att sätta `setExportFloatingShapesAsInlineTag(true)` instruerar motorn att omsluta varje form i en inline `<span>` istället.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Varför detta är viktigt:*  
- **Layout‑trohet** – Inline‑taggar håller formen i linje med omgivande text, vilket undviker oönskade luckor.  
- **Sökbarhet** – Inline‑element är mer benägna att indexeras korrekt av PDF‑läsare.  
- **Stilkontroll** – Du kan rikta in dig på `<span>` med CSS om du senare konverterar PDF‑filen tillbaka till HTML.

> **Proffstips:** Om du någonsin behöver det gamla blockbeteendet för ett specifikt dokument, skicka helt enkelt `false` eller utelämna anropet helt.

---

## Steg 3: Spara dokumentet som PDF med de konfigurerade alternativen

Nu kombinerar du det laddade `Document` med `PdfSaveOptions` och skriver ut filen. Denna enda rad utför det tunga arbetet.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Varför detta är viktigt:*  
`save`‑metoden respekterar varje flagga du satt på `pdfOptions`. Att glömma att skicka med alternativen återgår till standard block‑export, vilket motverkar syftet med **export floating shapes inline**.

---

## Fullt fungerande exempel

När allt sätts ihop, här är ett kompakt program som du kan kompilera och köra direkt. Ersätt `YOUR_DIRECTORY` med en faktisk sökväg på din maskin.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Förväntat resultat** – Efter att ha kört programmet, öppna `FloatingShapes.pdf`. Du bör se formerna ligga i linje med texten, utan extra vitt utrymme, och HTML‑representationen (om du inspekterar PDF:ens interna struktur) kommer att innehålla `<span>`‑taggar runt varje form.

![Export floating shapes inline example](https://example.com/export-inline.png "Skärmdump som visar flytande former renderade inline i PDF:en")

*Bildtext:* **export floating shapes inline** skärmdump av PDF med inline‑former.

---

## Vanliga frågor & edge‑cases

### 1. “Vad händer om mitt dokument innehåller komplex SmartArt?”

SmartArt behandlas som ett ritobjekt. Inline‑flaggan fungerar för de flesta vektorformer, men mycket invecklad SmartArt kan fortfarande renderas som en bild. I sådana fall, överväg att platta till SmartArt i Word innan konvertering, eller använd `pdfOptions.setExportSmartArtAsImage(true)` för att tvinga bild‑export.

### 2. “Kan jag kombinera inline‑ och block‑export i samma dokument?”

Tyvärr tillämpas inställningen globalt i API:et. Om du behöver blandat beteende, dela upp dokumentet i sektioner, exportera varje sektion separat med olika alternativ, och slå sedan ihop PDF‑filerna med `PdfMerger`.

### 3. “Påverkar detta teckensnittsinbäddning?”

Nej. Teckensnittsinbäddning styrs av `pdfOptions.setEmbedFullFonts(true)` (standard). Du kan säkert aktivera eller inaktivera det utan att röra inline‑form‑flaggan.

### 4. “Hur verifierar jag att formerna verkligen är `<span>`?”

Öppna den resulterande PDF‑filen i ett verktyg som **PDF.js** eller **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Du kommer att se formen omsluten av ett `<span>`‑element i den underliggande XML‑strukturen. Om du ser `<div>` har alternativet inte tillämpats.

---

## Utöka metoden – Relaterade alternativ

Medan du är här kan du också vilja utforska andra PDF‑konverteringsinställningar:

| Alternativ | Vad den gör | Typiskt användningsfall |
|------------|-------------|--------------------------|
| `setCompressImages(true)` | Minskar bildstorlek | Snabbare nedladdningar |
| `setUseHighQualityRendering(true)` | Förbättrar vektorrendering | Utskriftsklara PDF‑filer |
| `setExportDocumentStructure(true)` | Lägger till strukturella taggar för tillgänglighet | WCAG‑efterlevnad |
| `setSaveFormat(SaveFormat.PDF)` | Anger explicit format (sällan behövt) | Multi‑format pipelines |

Dessa inställningar passar bra ihop med **convert word to pdf inline**‑scenarier där du behöver både layout‑trohet och prestanda.

---

## Testa din konvertering

1. **Visuell kontroll** – Öppna PDF‑filen i två visare (Chrome och Adobe Reader) för att säkerställa att formerna ligger i linje.  
2. **Automatiserad diff** – Använd ett bibliotek som `pdfbox` för att extrahera XML och påstå närvaron av `<span>`‑taggar.  
3. **Prestandamätning** – Mät tiden som tas med och utan `setCompressImages` för att se avvägningen.

Ett snabbt JUnit‑exempel:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Slutsats

Du har nu en solid, helhetslösning för **export floating shapes inline** när du **convert Word to PDF inline**. Genom att konfigurera `PdfSaveOptions` styr du vilken HTML‑tagg som används för varje form, vilket håller dina PDF‑filer prydliga och sökbara. Kom ihåg att testa resultatet, justera relaterade alternativ som bildkomprimering och hantera edge‑cases som komplex SmartArt.

Redo för nästa steg? Prova att tillämpa samma teknik för **export floating tables inline** eller experimentera med CSS‑stylade PDF‑filer med Aspose’s `HtmlSaveOptions`. Samma mönster—ladda, konfigurera, spara—gäller för nästan alla dokument‑till‑PDF‑scenarier.

Har du fler frågor om **how to set pdf options** eller behöver hjälp med **save word as pdf options** för ett annat bibliotek? Lämna en kommentar, och lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Konvertera Word till PDF med Aspose.Words for Java](/words/english/java/document-converting/)
- [Hur man sparar dokument som pdf med Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Exportera Word-dokumentstruktur till PDF-dokument](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}