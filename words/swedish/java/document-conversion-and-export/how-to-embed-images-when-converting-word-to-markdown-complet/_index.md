---
category: general
date: 2026-02-28
description: Lär dig hur du bäddar in bilder när du konverterar doc till markdown.
  Exportera markdown med bilder och få inbäddade bilder i markdown med Java.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: sv
og_description: Upptäck hur du bäddar in bilder när du konverterar ett Word‑dokument
  till Markdown. Den här guiden visar dig hur du exporterar markdown med bilder och
  behåller dem i linjen.
og_title: Hur du bäddar in bilder när du konverterar Word till Markdown
tags:
- markdown
- java
- Aspose.Words
- image handling
title: Hur man bäddar in bilder vid konvertering från Word till Markdown – Komplett
  guide
url: /sv/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man bäddar in bilder vid konvertering av Word till Markdown – Komplett guide

Har du någonsin funderat **hur man bäddar in bilder** i en Markdown‑fil som du genererar från ett Word‑dokument? Kanske har du provat en snabb export, bara för att sluta med en massa hängande bildfiler och trasiga länkar. Det är ett vanligt problem—särskilt när du behöver en enda, portabel `.md` som du kan släppa in i en static‑site‑generator eller ett GitHub‑README.

Den goda nyheten? Du kan instruera exportören att infoga varje bild som en Base64‑kodad sträng, så den resulterande Markdown‑filen blir självständig. I den här handledningen går vi igenom de exakta stegen, visar dig den fullständiga Java‑koden och förklarar varför varje del är viktig. I slutet kommer du att kunna **convert doc to markdown** med inbäddade bilder, och du kommer också att se hur du kan justera processen för andra scenarier som “export markdown with images” eller “inline images in markdown”.

## Vad du kommer att lära dig

- De nödvändiga biblioteken och en minimal projektuppsättning.  
- Hur man konfigurerar `MarkdownSaveOptions` så att bilder blir Base64‑data‑URI:er.  
- Varför användning av en `ResourceSavingCallback` är det renaste sättet att kontrollera bildhantering.  
- Hur man verifierar att Markdown‑filen faktiskt innehåller de inbäddade bilderna.  
- Tips för kantfall (stora bilder, olika MIME‑typer och prestandaöverväganden).  

Ingen förhandsexpertis med Aspose.Words behövs; en grundläggande Java‑bakgrund räcker.

---

## Förutsättningar

Innan vi dyker ner i koden, se till att du har:

| Krav | Varför det är viktigt |
|------|------------------------|
| **Java 17+** (or any recent JDK) | Aspose.Words for Java‑API:et riktar sig mot Java 8+, men att använda den senaste JDK:n ger dig de inbyggda `Base64`‑verktygen. |
| **Aspose.Words for Java** (latest version) | Detta bibliotek tillhandahåller `MarkdownSaveOptions` och den callback‑infrastruktur vi kommer att använda. |
| **A Word document** (`.docx`) that contains at least one image | Vi behöver något att konvertera; exemplet förutsätter en fil som heter `sample.docx`. |
| **An IDE or text editor** (IntelliJ, VS Code, etc.) | För att snabbt kompilera och köra exemplet. |

Lägg till Aspose‑beroendet i din `pom.xml` (Maven) eller `build.gradle` (Gradle). Här är Maven‑snutten:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Om du föredrar Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Aspose erbjuder en gratis 30‑dagars provperiod. Skaffa en tillfällig licensnyckel och registrera den tidigt för att undvika vattenstämpelmeddelanden.

## Steg 1: Skapa Markdown‑spara‑alternativen

Det första vi gör är att instansiera `MarkdownSaveOptions`. Detta objekt talar om för Aspose hur vi vill att konverteringen ska fungera—teckensnittshantering, listformatering och, viktigast för oss, bildhantering.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

I Java är syntaxen identisk; ersätt bara `csharp`‑nyckelordet med `java` i kodblocket senare.  
Varför detta är viktigt: utan att anpassa alternativen kommer Aspose att skriva varje bild till en separat fil bredvid `.md`. Genom att förbereda options‑objektet nu får vi en krok för att avbryta det standardbeteendet.

## Steg 2: Intercepta bildresurser och koda dem som Base64

Aspose utlöser en callback varje gång den vill skriva en resurs (bild, CSS, etc.). Genom att implementera `IResourceSavingCallback` kan vi bestämma vad som ska göras med varje resurs. Kodsnutten nedan kontrollerar om resursen är en bild, rensar filnamnet (så ingen extern fil skapas), kodar binärdata till Base64 och sätter rätt MIME‑typ.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**Vad händer under huven?**

1. **`args.getResourceType()`** – Aspose klassificerar varje utgående blob. Vi bryr oss bara om `ResourceType.IMAGE`.  
2. **`args.setResourceFileName(null)`** – Genom att sätta filnamnet till null säger vi till biblioteket *att* inte skriva en fysisk fil.  
3. **`Base64.getEncoder().encodeToString(...)`** – Den råa byte‑arrayen blir en textsträng som säkert kan placeras i en Markdown‑data‑URI.  
4. **`args.setResourceContentType("image/png")`** – Detta säkerställer att den genererade Markdown‑taggen ser ut som `![alt](data:image/png;base64,…)`. Om ditt källdokument innehåller JPEG‑filer kan du inspektera de ursprungliga bytena och välja `"image/jpeg"` istället.

> **Varför Base64?**  
> Markdown‑processorer som förstår data‑URI:er kommer att rendera bilden direkt, och den resulterande filen förblir portabel—inga extra resurser att kopiera runt. Det är särskilt praktiskt för GitHub‑READMEs eller dokumentationssajter som förbjuder externa resurser.

## Steg 3: Utför konverteringen

Nu när alternativen är klara, ladda helt enkelt ditt Word‑dokument och anropa `save`. Sökvägen du anger blir platsen för den genererade Markdown‑filen.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

Det är allt—två rader med faktisk konverteringskod. Det tunga arbetet (läsa DOCX, extrahera bilder, konvertera stycken) hanteras helt av Aspose.

## Steg 4: Verifiera resultatet – Inbäddade bilder visas

Öppna `output/doc.md` i någon textredigerare. Du bör se något liknande:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Om du klistrar in Markdown i en visare som stödjer data‑URI:er (GitHub, VS Code‑förhandsgranskning eller en static‑site‑generator), kommer bilden att renderas utan några extra filer.

**Snabb kontroll**:  

- **Sök efter `data:image/`** – Om du hittar några långa strängar har inbäddningen fungerat.  
- **Räkna `![](`‑mönstren** – De bör motsvara antalet bilder i det ursprungliga Word‑dokumentet.

## Hantera kantfall

### Stora bilder

Base64 ökar den ursprungliga storleken med ungefär **33 %**. För mycket stora bilder (t.ex. högupplösta foton) kan Markdown‑filen bli otymplig. Överväg dessa strategier:

| Strategi | När den ska användas |
|----------|----------------------|
| **Ändra storlek före konvertering** – Använd `java.awt.Image` för att skala ner. | När källdokumentet innehåller högupplösta resurser som inte behövs i full storlek. |
| **Byt till JPEG** – Ändra `args.setResourceContentType("image/jpeg")`. | För fotografier där PNG:s förlustfria format är överdrivet. |
| **Dela upp dokumentet** – Dela Word‑filen i sektioner och exportera varje separat. | När du behöver hålla Markdown‑filen under en viss storleksgräns (t.ex. GitHubs 10 MB‑gräns). |

### Icke‑PNG‑bilder

Om ditt Word‑dokument innehåller blandade format kan du dynamiskt upptäcka MIME‑typen:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose fyller redan i `ResourceContentType`, så du behöver ofta inte hårdkoda `"image/png"`.

### Prestandatips

- **Återanvänd en enda `Base64.Encoder`‑instans** om du konverterar många bilder i en loop.  
- **Aktivera `markdownSaveOptions.setExportImagesAsBase64(true)`** (om API‑versionen stödjer det) för att undvika callback‑en helt.  
- **Kör konverteringen i en bakgrundstråd** när du bearbetar många dokument i en servermiljö.

## Fullt fungerande exempel (allt ihop)

Nedan är ett kopiera‑och‑klistra‑klart Java‑program som inkluderar imports, felhantering och hela flödet vi diskuterade.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Förväntat resultat**: en enda `doc.md`‑fil som innehåller inbäddade Base64‑bilder, klar för vilket Markdown‑medvetet verktyg som helst.

## Vanliga frågor

**Q1: Fungerar detta med äldre versioner av Aspose.Words?**  
*Vanligtvis ja.* Callback‑API:et har varit stabilt sedan version 19. Dock dök `setExportImagesAsBase64`‑kortkommandot upp i senare releaser, så om du använder en äldre build måste du använda den explicita callback‑en som visas ovan.

**Q2: Vad händer om jag behöver exportera till GitHub Flavored Markdown (GFM)?**  
Aspose’s `MarkdownSaveOptions` avger redan GFM‑kompatibel syntax. Det enda extra steget är att säkerställa att ditt repos renderingsmotor stödjer data‑URI:er—GitHub gör det.

**Q3: Kan jag använda detta tillvägagångssätt för andra format, som HTML?**  
Absolut. Samma `ResourceSavingCallback` fungerar för `HtmlSaveOptions`. Byt bara ut options‑klassen och behåll Base64‑logiken.

##

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}