---
category: general
date: 2026-07-06
description: Skapa DocumentConfig i Java för att spåra saknade teckensnitt med Aspose.Words
  – en komplett steg‑för‑steg‑guide för utvecklare.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: sv
og_description: Skapa DocumentConfig i Java för att spåra saknade teckensnitt med
  Aspose.Words. Lär dig hela arbetsflödet, från konfiguration till hantering av varningar.
og_title: Skapa DocumentConfig i Java – Spåra saknade teckensnitt
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Skapa DocumentConfig i Java – Spåra saknade teckensnitt med Aspose.Words
url: /sv/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa DocumentConfig i Java – Spåra saknade teckensnitt med Aspose.Words

**Skapa DocumentConfig i Java** för att övervaka varningar om teckensnittssubstitution när ett Word‑dokument laddas. Har du någonsin undrat varför vissa tecken ser konstiga ut efter att du öppnat en DOCX? Oftast beror det på att originalteckensnittet saknas på maskinen, och Aspose.Words byter det tyst. I den här handledningen visar vi exakt hur du **spårar saknade teckensnitt** så att du aldrig blir överraskad av ett felaktigt tecken igen.

Vi går igenom allt du behöver: Maven/Gradle‑inställningarna, koden som skapar ett `DocumentConfig`, en anpassad `IWarningCallback` som filtrerar endast teckensnittssubstitutionsvarningar, och ett snabbt sätt att logga dessa meddelanden. När du är klar har du ett körbart exempel som skriver ut varje varning om saknat teckensnitt till konsolen (eller till en fil, om du föredrar).

---

## Vad du kommer att lära dig

- Varför ett `DocumentConfig` är rätt plats för att avlyssna teckensnittssubstitutions‑händelser.  
- Hur du **spårar saknade teckensnitt** utan att förorena dina loggar med irrelevanta varningar.  
- Ett komplett, copy‑paste‑klart Java‑program som demonstrerar tekniken.  
- Tips för att utöka lösningen – t.ex. skriva varningar till en databas eller skicka e‑post‑aviseringar.

### Förutsättningar

| Krav | Orsak |
|------|-------|
| Java 8 or newer | Aspose.Words för Java stöder JDK 8+. |
| Aspose.Words for Java library (latest version) | Tillhandahåller `DocumentConfig`, `IWarningCallback`, osv. |
| An IDE or build tool (IntelliJ, Eclipse, Maven/Gradle) | För att kompilera och köra exempelprogrammet. |
| A DOCX file that references fonts you don’t have installed | För att se varningen i praktiken. |

Om du redan har ett projekt, lägg bara till Aspose‑beroendet så är du klar att köra.

---

## Steg 1: Lägg till Aspose.Words i ditt bygge

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Proffstips:** Den kostnadsfria provversionen fungerar utmärkt för testning, men kom ihåg att tillämpa en licens för produktion för att ta bort utvärderingsvattenstämpeln.

---

## Steg 2: Skapa DocumentConfig och registrera en varningsåteruppringning

Kärnan i lösningen finns i detta kodsnutt. Vi **skapar ett DocumentConfig**, bifogar en anpassad `IWarningCallback` och instruerar den att endast **spåra saknade teckensnitt**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Varför detta fungerar:** När Aspose.Words analyserar ett dokument, genererar det `WarningInfo`‑objekt för alla avvikelser. Genom att tillhandahålla en återuppringning fångar du dessa varningar *innan* de försvinner i tomrummet. `if`‑kontrollen garanterar att vi endast **spårar saknade teckensnitt**, och ignorerar andra varningar som föråldrade taggar eller funktioner som inte stöds.

---

## Steg 3: Kör exemplet och observera utskriften

Placera en DOCX‑fil som refererar till ett teckensnitt du inte har (t.ex. “Comic Sans MS” på en Linux‑maskin). Kör programmet:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Du bör se något liknande:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Varje rad motsvarar ett saknat teckensnitt som Aspose automatiskt ersatte. Om inga saknade teckensnitt finns, förblir programmet tyst – precis vad du vill ha för en ren logg.

---

## Steg 4: Spara listan över saknade teckensnitt (valfritt)

Att skriva ut till konsolen är praktiskt för demo, men i en verklig tjänst vill du sannolikt lagra data. Här är ett snabbt sätt att skriva varningarna till en textfil.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Nu lägger varje saknat‑teckensnitt‑händelse till en rad i `missing-fonts.log`. Du kan senare parsra filen, mata in den i en övervakningsdashboard, eller till och med trigga en avisering om ett kritiskt teckensnitt försvinner från din server.

---

## Steg 5: Vanliga fallgropar och hur du undviker dem

| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|--------|
| Inga varningar visas även om DOCX-filen använder okända teckensnitt | Återuppringning inte registrerad eller `setWarningCallback` anropad efter att dokumentet laddats | Säkerställ att `config.setWarningCallback(...)` körs **innan** `Document`‑instansen skapas. |
| Applikationen kraschar med `NullPointerException` | `info.getDescription()` returnerar `null` för vissa sällsynta varningstyper | Skydda mot null: `String desc = info.getDescription(); if (desc != null) …` |
| För många orelaterade varningar översvämmar konsolen | Återuppringning filtrerar endast `FONT_SUBSTITUTION`? | Dubbelkolla `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`‑villkoret. |
| Prestandan saktar ner vid stora batcher | Skriver till fil synkront för varje varning | Batcha skrivningar eller använd en `BufferedWriter` för att minska I/O‑bördan. |

---

## Steg 6: Utöka lösningen – Från konsol till företag

- **Databasloggning:** Byt ut `FileWriter` mot ett JDBC‑insert; lagra `documentName`, `missingFont` och `timestamp`.  
- **E‑post‑aviseringar:** Koppla in JavaMail; skicka en sammanfattning efter att en batch dokument har bearbetats.  
- **Anpassad substitueringslogik:** Istället för att låta Aspose välja en reserv, kan du ladda en lokal teckensnittssamling via `FontSettings.setFontsFolder()` och köra om laddningen om en substitution sker.

Dessa utökningar behåller kärnidén – **skapa DocumentConfig** och **spåra saknade teckensnitt** – intakt samtidigt som de skalar till produktionsbehov.

---

## Slutsats

Du har nu ett robust, copy‑and‑paste‑klart mönster för **att skapa ett DocumentConfig** i Java och använda det för att **spåra saknade teckensnitt** med Aspose.Words. Metoden är lättviktig, kräver bara några rader kod och ger dig full kontroll över hur teckensnittssubstitutions‑varningar hanteras. Oavsett om du bygger en dokument‑konverteringstjänst, en automatiserad rapportgenerator eller ett efterlevnads‑audit‑verktyg, kan kunskap om exakt vilka teckensnitt som saknas spara timmar av felsökning.

Nästa steg? Prova att byta ut konsolutskriften mot en strukturerad JSON‑logg, eller integrera återuppringningen i en Spring Boot‑mikrotjänst som bearbetar uppladdningar i realtid. Och om du stöter på kantfall – t.ex. ett anpassat OpenType‑teckensnitt som Aspose inte kan läsa – lämna en kommentar nedan; vi felsöker tillsammans.

Lycka till med kodandet, och må dina PDF‑filer alltid renderas med de teckensnitt du förväntar dig!

## Vad du bör lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Använda teckensnitt i Aspose.Words för Java](/words/english/java/using-document-elements/using-fonts/)
- [Anpassa temafärger och teckensnitt i Aspose.Words Java: En omfattande guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Hur man skapar PDF-dokument med Aspose.Words för Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}