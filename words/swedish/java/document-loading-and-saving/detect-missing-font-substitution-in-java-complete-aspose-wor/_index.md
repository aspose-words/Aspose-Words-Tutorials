---
category: general
date: 2026-06-05
description: detektera saknad teckensnittssubstitution i Java med Aspose.Words. Lär
  dig hur du konfigurerar LoadOptions, FontSettings och varningsåteruppringningar
  för pålitlig dokumentbehandling.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: sv
og_description: Detektera saknad teckensnittssubstitution i Java med Aspose.Words.
  Denna guide visar steg för steg hur du konfigurerar LoadOptions, FontSettings och
  en varningsåteruppringning för att fånga saknade teckensnitt.
og_title: detektera saknad teckensnittssubstitution i Java – Fullständig Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: Detektera saknad teckensnittssubstitution i Java – Komplett Aspose.Words-guide
url: /sv/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Detektera saknad teckensnittssubstitution i Java – Komplett Aspose.Words‑guide

Har du någonsin funderat på hur du **detekterar saknad teckensnittssubstitution** när du laddar ett Word‑dokument i Java? Du är inte ensam. Saknade teckensnitt kan tyst förstöra dina PDF‑filer eller renderade sidor, och att upptäcka dem tidigt sparar timmar av felsökning. I den här handledningen går vi igenom en praktisk lösning som inte bara laddar ett dokument utan också talar om exakt när en teckensnittssubstitution sker.

Vi täcker allt från att skapa `LoadOptions` till att koppla en `WarningCallback` som skriver ut ett tydligt meddelande varje gång Aspose.Words byter ut ett saknat teckensnitt. I slutet har du ett återanvändbart kodexempel som fungerar med vilken `.docx`‑fil som helst, och du förstår *varför* varje del är viktig. Inga extra bibliotek, bara ren Java och Aspose.Words.

## Vad du kommer att lära dig

- Hur du konfigurerar **LoadOptions** för att använda anpassade **FontSettings**.  
- Hur du implementerar ett **IWarningCallback** som fångar `FONT_SUBSTITUTION`‑varningar.  
- Hur du laddar ett dokument samtidigt som du säkert övervakar saknade teckensnitt.  
- Förväntad konsolutdata och hur du anpassar koden för loggningsramverk.  

**Förutsättningar**: Java 8+ installerat, Aspose.Words för Java (v23.12 eller nyare) på din classpath, samt ett exempel‑`.docx`‑dokument som refererar till ett teckensnitt du inte har installerat. Det är allt—inga extra byggverktyg behövs.

---

## Steg 1: Ställ in projektet och lägg till Aspose.Words

Innan vi dyker ner i koden, se till att Aspose.Words är tillgängligt. Om du använder Maven, lägg till följande beroende i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Om du föredrar Gradle, är motsvarigheten:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

När biblioteket finns på classpath är du redo att **detektera saknad teckensnittssubstitution** med ett enda metodanrop.

---

## Steg 2: Skapa LoadOptions och anslut FontSettings

Kärnan i lösningen ligger i att förbereda en `LoadOptions`‑instans som vet hur den ska hålla utkik efter teckensnittsproblem. Här är koden rad för rad.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Varför detta är viktigt**: `LoadOptions` talar om för Aspose.Words *hur* den ska tolka den inkommande filen. Genom att koppla in en anpassad `FontSettings` ger vi laddaren en krok (`IWarningCallback`) som triggas **exakt när ett saknat teckensnitt ersätts**. Utan denna callback skulle Aspose.Words tyst ersätta teckensnittet och du skulle aldrig få veta det.

---

## Steg 3: Ladda dokumentet med de konfigurerade alternativen

Nu när varningssystemet är på plats blir dokumentladdningen enkel.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

När anropet `new Document(...)` körs läser Aspose.Words filen, kontrollerar varje teckensnittreferens, och om den inte hittar ett matchande teckensnitt på systemet, utlöser den `warning`‑metoden vi definierade tidigare. Konsolen visar omedelbart en rad som:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Den raden är den **detektera saknad teckensnittssubstitution**‑utdata du letade efter.

---

## Steg 4: Verifiera resultatet och finjustera callbacken (Avancerat)

### 4.1 Snabb verifiering

Kör programmet från din IDE eller via `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Om dokumentet refererar till ett teckensnitt du inte har, kommer du att se varningsmeddelandet skrivet. Om konsolen förblir tyst, finns antingen teckensnittet på din maskin eller så begär dokumentet inga saknade teckensnitt.

### 4.2 Loggning istället för `System.out`

I produktionskod vill du förmodligen använda en logger:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Den lilla förändringen får **detektera saknad teckensnittssubstitution**‑mekanismen att fungera smidigt med befintliga logg‑pipelines.

### 4.3 Hantera andra varningstyper

Callbacken tar emot *alla* varningar, inte bara teckensnittsrelaterade. Om du vill hålla koll på andra problem (t.ex. `UNKNOWN_STYLE`), lägg till extra `if`‑grenar. Här är ett snabbt exempel:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## Steg 5: Vanliga fallgropar och pro‑tips

| Fallgrop | Varför det händer | Åtgärd |
|----------|-------------------|--------|
| **Ingen varning visas** | Teckensnittet finns faktiskt på OS‑et, eller dokumentet använder en fallback som Aspose.Words betraktar som “hittad”. | Ta bort teckensnittet tillfälligt från systemet eller använd ett riktigt saknat teckensnittsnamn i källdokumentet. |
| **Callbacken anropas aldrig** | `setWarningCallback` anropades på en *annan* `FontSettings`‑instans än den som är kopplad till `LoadOptions`. | Se till att du anropar `loadOptions.setFontSettings(fontSettings)` **efter** att du konfigurerat callbacken. |
| **Prestandaförsämring** | Att ladda många stora dokument med callbacks kan lägga till overhead. | Cacha en enda `FontSettings`‑instans och återanvänd den över flera laddningar om du bearbetar batcher. |
| **Flera trådar** | `FontSettings` är inte trådsäker som standard. | Skapa en separat `FontSettings` per tråd eller synkronisera åtkomsten. |

**Pro‑tips**: Om du genererar PDF‑filer för en webbtjänst kan du samla alla substitutionsvarningar i en lista och returnera dem i API‑svaret, istället för att skriva ut dem i konsolen.

---

## Fullständigt fungerande exempel (Kopiera‑klistra‑klart)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Förväntad konsolutdata** (förutsatt att filen refererar till ett saknat teckensnitt):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Om inga saknade teckensnitt finns, ser du bara den sista raden “Document loaded successfully.”.

---

## Slutsats

Vi har just demonstrerat hur du **detekterar saknad teckensnittssubstitution** i Java med Aspose.Words. Genom att konfigurera `LoadOptions`, skapa en `FontSettings`‑instans och koppla en `IWarningCallback` får du full insyn i varje teckensnitt som biblioteket byter bakom kulisserna. Detta förhindrar tysta renderingsbuggar och ger dig en krok för loggning, larm eller till och med automatisk inbäddning av reservteckensnitt.

Från här kan du:

- Utöka callbacken för att samla varningar i en lista för API‑svar.  
- Kombinera tekniken med **LoadOptions‑konfiguration** för andra scenarier (t.ex. anpassad resurshämtning).  
- Utforska det bredare **Java Aspose.Words**‑ekosystemet: konvertera till PDF, extrahera text eller utföra mail‑merges.

Prova det, justera loggern, och låt dina applikationer tala när ett teckensnitt saknas. Lycka till med kodandet!


## Vad du bör lära dig härnäst


Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}