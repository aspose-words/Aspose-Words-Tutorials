---
category: general
date: 2026-06-17
description: Logga varningar för teckensnittssubstitution i Java med Aspose.Words
  – fånga saknade teckensnitt vid dokumentladdning och håll ditt resultat konsekvent.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: sv
og_description: Logga varningar för teckensnittssubstitution i Java med Aspose.Words.
  Lär dig att fånga varningar om saknade teckensnitt vid dokumentladdning och håll
  dina PDF-filer fläckfria.
og_title: Logga varningar om teckensnittsersättning i Java – Komplett guide
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Logga varningar för teckensnittssubstitution i Java med Aspose.Words
url: /sv/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Logga varningar för teckensnittssubstitution i Java – Komplett guide

Har du någonsin undrat hur du **loggar varningar för teckensnittssubstitution** när ett Word‑dokument hämtar ett teckensnitt som du inte har på servern? Du är inte den enda som kliar sig i huvudet över saknade teckensnitt som tyst byts ut. Den goda nyheten? Aspose.Words for Java ger dig ett rent sätt att fånga dessa substitutioner i samma ögonblick som ett dokument laddas.

I den här handledningen går vi igenom ett praktiskt exempel som visar exakt hur du registrerar en varnings‑callback, filtrerar efter teckensnittssubstitutions‑larm och skriver dem till konsolen (eller någon logger du föredrar). I slutet har du ett återanvändbart kodsnutt som du kan lägga in i vilket Java‑projekt som helst som använder **Aspose.Words Java**.

## Vad du kommer att lära dig

- Hur du konfigurerar **LoadOptions** för att fånga varningar.
- Hur du implementerar en **IWarningCallback** som endast reagerar på **font substitution**‑händelser.
- Hur du laddar ett dokument säkert samtidigt som du behåller en tydlig revisionsspårning av saknade teckensnitt.
- Tips för att utöka lösningen till filbaserade loggar eller övervakningssystem.

### Förutsättningar

- Java 8 eller nyare (koden fungerar även med Java 11+).
- Aspose.Words for Java‑biblioteket (version 23.10 eller senare rekommenderas).
- Ett exempel‑`.docx`‑dokument som refererar till ett teckensnitt som inte är installerat på din maskin (t.ex. `MissingFont.docx`).

Inga ytterligare ramverk krävs – bara ren Java och Aspose‑JAR‑filerna.

---

## Steg 1: Konfigurera LoadOptions för Aspose.Words Java

Innan du kan fånga några varningar behöver du en **LoadOptions**‑instans. Detta objekt talar om för Aspose.Words hur det ska bete sig när det parsar den inkommande filen.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Varför är detta steg avgörande? Utan ett `LoadOptions`‑objekt ersätter biblioteket tyst saknade teckensnitt och du ser aldrig någon spårning. Genom att explicit skapa ett öppnar du dörren för en anpassad **warning callback** som kan logga exakt det du bryr dig om.

> **Proffstips:** Om du laddar många dokument i en batch, återanvänd en enda `LoadOptions`‑instans för att undvika onödig objekt‑skapning.

---

## Steg 2: Implementera en varnings‑callback för teckensnittssubstitution

Aspose.Words levereras med gränssnittet `IWarningCallback`. Att implementera det låter dig bestämma vad som ska göras när motorn genererar en `WarningInfo`. I vårt fall vill vi bara reagera på `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Några saker att notera:

1. **Filtrering** – `if`‑satsen säkerställer att vi ignorerar orelaterade varningar (som layout‑problem) och håller loggen prydlig.
2. **Trådsäkerhet** – Callbacken körs på samma tråd som laddar dokumentet, så du behöver ingen extra synkronisering för enkel konsolutskrift. Om du skriver till en gemensam logger, se till att den är trådsäker.
3. **Utbyggbarhet** – Vill du skriva till en fil? Byt `System.out.println` mot `java.util.logging.Logger` eller ett tredjeparts‑loggningsramverk.

---

## Steg 3: Ladda dokumentet med de konfigurerade alternativen

Nu när callbacken är på plats, ladda ditt Word‑fil. I samma ögonblick som Aspose.Words parsar dokumentet kommer varje saknat teckensnitt att utlösa callbacken som definierades ovan.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Om källfilen refererar till ett teckensnitt som inte är installerat, kommer du att se en utskrift liknande:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Den raden är **loggningen av teckensnittssubstitutions‑varningar** du letade efter. Du kan nu agera på den – kanske varna en användare, byta till en reserv‑stylesheet, eller helt enkelt behålla en post för efterlevnad.

---

## Steg 4: Fortsätt normal bearbetning

Efter laddning beter sig dokumentet precis som vilket annat `Document`‑objekt som helst. Känn dig fri att inspektera sektioner, extrahera text eller konvertera till PDF. Varningsloggningen sker automatiskt under laddningssteget, så du behöver ingen extra kod.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Konsolen kommer nu att visa både teckensnittssubstitutions‑varningen (om någon) **och** sektionräkningen, vilket bekräftar att dokumentet är fullt funktionellt.

---

## Avancerade tips & kantfall

### Logga till en fil istället för konsolen

Om du föredrar en bestående logg, ersätt anropet `System.out.println` med en `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Kom ihåg att hantera `IOException` på rätt sätt i produktionskod.

### Fånga flera dokument i en loop

När du bearbetar en mapp med dokument kan du återanvända samma callback:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Eftersom callbacken är knuten till `loadOptions` loggar varje iteration automatiskt eventuella teckensnittssubstitutions‑händelser.

### Hantera inbäddade teckensnitt

Aspose.Words kan bädda in saknade teckensnitt om du aktiverar det:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Även med inbäddning aktiverad avfyras varnings‑callbacken, vilket ger dig insyn i vad som ersattes.

---

## Fullt fungerande exempel

Nedan är det kompletta, körklara programmet. Kopiera det till en klass som heter `FontSubstitutionDiagnostics.java`, justera filsökvägen och kör.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Förväntad utskrift** (förutsatt att källdokumentet refererar till ett saknat teckensnitt):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Både konsolen och `font_substitution_log.txt` kommer att innehålla varningen, vilket ger dig en pålitlig revisionsspårning.

---

## Slutsats

Vi har just visat dig hur du **loggar varningar för teckensnittssubstitution** i Java med Aspose.Words. Genom att konfigurera `LoadOptions`, koppla en `IWarningCallback` och ladda dokumentet får du full insyn i alla saknade‑teckensnitt‑händelser som annars kunde gå obemärkt förbi. Härifrån kan du:

- Skicka varningar till en central loggtjänst.
- Utlösa larm för kvalitetssäkrings‑pipelines.
- Kombinera denna teknik med andra **document loading**‑strategier, såsom PDF‑konvertering eller mail‑merge.

Känn dig fri att experimentera – byt ut konsolloggern mot SLF4J, lägg till tidsstämplar, eller till och med skicka larm till en övervakningsdashboard. Kärnmönstret förblir detsamma, och nu har du en solid grund för robust teckensnittshantering i vilket Java‑baserat dokumentflöde som helst.

Har du en variant du vill dela? Kanske har du integrerat detta med Spring Boot eller en molnfunktion. Lämna en kommentar nedan, så fortsätter vi diskussionen. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}