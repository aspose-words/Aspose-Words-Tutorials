---
category: general
date: 2026-04-24
description: Lär dig hur du sparar Word-dokument med Aspose.Words samtidigt som du
  ställer in teckensnittsinställningar och hanterar saknade teckensnitt med lättföljd
  Java‑kod.
draft: false
keywords:
- save word document
- set font settings
- how to set font settings
- aspose words font substitution
- handle missing fonts
language: sv
og_description: Spara Word-dokument med Aspose.Words samtidigt som du ställer in teckensnittsinställningar
  och hanterar saknade teckensnitt. Komplett Java-guide för utvecklare.
og_title: Spara Word-dokument – Ställ in teckensnittinställningar, hantera saknade
  teckensnitt
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Spara Word-dokument – Ställ in teckensnittsinställningar, hantera saknade teckensnitt
url: /sv/java/document-loading-and-saving/save-word-document-set-font-settings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara Word‑dokument – Ställ in teckensnittinställningar, hantera saknade teckensnitt

Har du någonsin behövt **spara Word‑dokument** men källfilen använder teckensnitt som din server inte har? Det är ett vanligt hinder som kan förvandla en smidig automationspipeline till ett huvudvärkstillstånd.  

Den goda nyheten? Med Aspose.Words kan du **ställa in teckensnittinställningar** i farten, fånga varningar om saknade teckensnitt och ändå få ett perfekt sparat Word‑dokument. I den här handledningen går vi igenom ett komplett Java‑exempel som visar **hur man ställer in teckensnittinställningar**, hanterar de fruktade *teckensnittssubstitutions*‑varningarna och slutligen **sparar Word‑dokument** utan överraskningar.

## Vad du kommer att lära dig

- Hur du konfigurerar `LoadOptions` med ett anpassat `FontSettings`‑objekt.  
- Hur du registrerar en varnings‑callback som rapporterar **aspose words font substitution**‑händelser.  
- Hur du laddar en DOCX, låter Aspose ersätta saknade teckensnitt och **sparar Word‑dokument** till en ny plats.  
- Tips för att hantera kantfall som krypterade filer eller dokument med inbäddade teckensnitt.  

Inga extra bibliotek utöver Aspose.Words behövs, och koden fungerar med den senaste 24.x‑utgåvan (från och med april 2026).  

---

![Diagram som illustrerar arbetsflödet för att spara Word‑dokument med teckensnittinställningar och varnings‑callback](font-workflow.png "Diagram som visar arbetsflödet för att spara Word‑dokument")

## Spara Word‑dokument med anpassade teckensnittinställningar

Det första steget är att berätta för Aspose.Words vad som ska göras när det inte kan hitta ett teckensnitt som källdokumentet refererar till. Här kommer **set font settings** in i bilden.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 1: Prepare LoadOptions with a fresh FontSettings instance.
        // -----------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        // By default FontSettings uses system fonts, but we can add folders later.
        loadOptions.setFontSettings(new FontSettings());

        // -----------------------------------------------------------------
        // Step 2: Register a warning callback to catch FONT_SUBSTITUTION alerts.
        // -----------------------------------------------------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about missing‑font warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // -----------------------------------------------------------------
        // Step 3: Load the source document using the configured options.
        // -----------------------------------------------------------------
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // -----------------------------------------------------------------
        // Step 4: Save the processed document – fonts have been substituted.
        // -----------------------------------------------------------------
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Varför detta fungerar:**  
- `LoadOptions` talar om för Aspose.Words att använda de medföljande `FontSettings` när filen analyseras.  
- `IWarningCallback` fångar upp alla **aspose words font substitution**‑meddelanden och ger dig en levande logg över vilka teckensnitt som saknades.  
- När du anropar `document.save(...)` ersätter Aspose automatiskt de saknade teckensnitten med de närmaste matchningarna från systemet eller de mappar du lagt till i `FontSettings`.

### Förväntat resultat

När programmet körs skrivs rader som följande ut:

```
Font substitution: Font 'Calibri' was not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria' was not found. Substituted with 'Times New Roman'.
```

Och du får en `output.docx` som ser exakt ut som originalet – förutom att de saknade teckensnitten har ersatts, och filen har framgångsrikt **saved word document** på disken.

## Hur du ställer in teckensnittinställningar i Aspose.Words

Om du behöver mer kontroll – till exempel att peka Aspose mot en egen teckensnittsmapp eller bädda in ett reservteckensnitt – justera bara `FontSettings`‑objektet innan du tilldelar det till `LoadOptions`.

```java
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder that contains your private fonts.
fontSettings.setFontsFolder("C:/MyCustomFonts", true);

// Optionally, set a default substitution font (e.g., "Arial").
fontSettings.setDefaultFontName("Arial");

// Attach the configured FontSettings to LoadOptions.
loadOptions.setFontSettings(fontSettings);
```

**När du använder detta:**  
- Din applikation körs i en container som bara levereras med ett minimalt urval av systemteckensnitt.  
- Du har företags‑branding‑teckensnitt som finns på en säker nätverksdelning.  
- Du vill garantera att ett specifikt reservteckensnitt (t.ex. “Arial”) alltid används, för att undvika oförutsägbara substitutioner.

## Hantera saknade teckensnitt – Callback för teckensnittssubstitution

Den varnings‑callback vi registrerade tidigare är kärnan i logiken för **handle missing fonts**. Du kan utöka den för att:

1. **Samla varningar** i en lista för senare rapportering.  
2. **Kasta ett undantag** om ett kritiskt teckensnitt saknas (t.ex. ett logotyp‑teckensnitt).  
3. **Logga till ett övervakningssystem** (Splunk, ELK osv.) för revisionsspår.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    private final List<String> missingFonts = new ArrayList<>();

    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String msg = "Missing font: " + info.getDescription();
            System.out.println(msg);
            missingFonts.add(msg);
        }
    }

    // Helper to retrieve all missing‑font messages after loading.
    public List<String> getMissingFonts() {
        return missingFonts;
    }
});
```

**Pro‑tips:** Om du behöver avbryta operationen när ett specifikt teckensnitt saknas, jämför `info.getDescription()` mot en vitlista och kasta ett `RuntimeException` när matchen misslyckas.

## Fullständigt Java‑exempel – Från början till slut

När allt har satts ihop ser du här ett självständigt program som du kan kopiera och klistra in i din IDE. Se till att du har Aspose.Words for Java‑JAR‑filen på din klassväg.

```java
import com.aspose.words.*;
import java.util.*;

public class SaveWordWithFontHandling {
    public static void main(String[] args) throws Exception {
        // ------------------- Configure FontSettings -------------------
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains any custom fonts you might need.
        fontSettings.setFontsFolder("C:/CustomFonts", true);
        // Ensure a safe fallback.
        fontSettings.setDefaultFontName("Arial");

        // ------------------- Prepare LoadOptions -------------------
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setFontSettings(fontSettings);

        // ------------------- Warning callback (handle missing fonts) -------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            private final List<String> missing = new ArrayList<>();

            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBstitution) {
                    String msg = "Font substitution: " + info.getDescription();
                    System.out.println(msg);
                    missing.add(msg);
                }
            }

            public List<String> getMissing() {
                return missing;
            }
        });

        // ------------------- Load the source DOCX -------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ------------------- Save the result -------------------
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Kör programmet, håll ett öga på konsolen för eventuella **font

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}