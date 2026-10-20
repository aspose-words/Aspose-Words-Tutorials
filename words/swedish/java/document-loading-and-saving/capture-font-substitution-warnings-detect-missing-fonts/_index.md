---
category: general
date: 2026-04-04
description: Fånga varningar om teckensnittsbyte när du laddar Word‑dokument med Aspose.Words
  för Java och upptäck saknade teckensnitt automatiskt. Följ den här steg‑för‑steg‑guiden.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: sv
og_description: Fånga varningar om teckensnittssubstitution när du laddar Word‑dokument
  med Aspose.Words för Java och upptäck saknade teckensnitt i några enkla steg.
og_title: Fånga varningar om teckensnittssubstitution – Upptäck saknade teckensnitt
tags:
- Aspose.Words
- Java
- Document Processing
title: Fånga varningar om teckensnittssubstitution – Upptäck saknade teckensnitt
url: /sv/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fånga varningar om teckensnittssubstitution – Upptäck saknade teckensnitt

Har du någonsin behövt **fånga varningar om teckensnittssubstitution** när du öppnar en Word-fil, bara för att upptäcka att ett viktigt teckensnitt saknas? Du är inte ensam. I många företagsarbetsflöden kan ett saknat teckensnitt förvandla en perfekt formaterad rapport till ett rörigt kaos, och den enda ledtråden du får är en tyst varning som de flesta utvecklare aldrig ser.

Den goda nyheten är att Aspose.Words for Java låter dig koppla in i inläsningsprocessen och **upptäcka saknade teckensnitt** innan de ger dig problem senare. I den här handledningen går vi igenom ett komplett, körbart exempel som skriver ut varje substitutionsvarning direkt till konsolen, så att du kan besluta om du ska bädda in rätt teckensnitt, ersätta det eller varna användaren.

Vid slutet av den här guiden kommer du att veta hur man:

* Skapar ett `LoadOptions`-objekt med en anpassad varningscallback.
* Filtrerar callbacken så att den endast reagerar på teckensnittssubstitutions‑händelser.
* Laddar en `.docx`-fil och ser varningarna omedelbart.
* Utökar lösningen för att logga varningar, kasta undantag eller till och med automatiskt installera saknade teckensnitt.

Ingen extern dokumentation krävs – bara några rader Java och Aspose.Words‑JAR‑filen.

## Förutsättningar

Innan vi dyker ner, se till att du har:

* Java 8 eller nyare installerat (den senaste LTS‑versionen fungerar bäst).
* Aspose.Words for Java 23.11 eller senare – du kan hämta Maven‑artefakten eller den vanliga JAR‑filen från Aspose‑webbplatsen.
* Ett Word‑dokument som refererar till ett teckensnitt du inte har på din utvecklingsmaskin (t.ex. “MyFancyFont”).  
* En IDE eller textredigerare du föredrar – jag använder IntelliJ IDEA, men Eclipse eller VS Code fungerar också bra.

Om någon av dessa är obekanta, pausa och installera dem först; resten av handledningen förutsätter att de är klara.

---

## Fånga varningar om teckensnittssubstitution med Aspose.Words

Kärnan i lösningen finns i en `LoadOptions`‑instans. Genom att tilldela en `IWarningCallback` kan vi avlyssna varje varning som biblioteket avger under inläsningsfasen.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Varför detta fungerar:**  
`LoadOptions` talar om för Aspose.Words hur den inkommande filen ska behandlas. `IWarningCallback`‑gränssnittet är en krok som tar emot ett `WarningInfo`‑objekt för *varje* varning. Genom att kontrollera `info.getWarningType()` filtrerar vi bort allt utom `SUBSTITUTED_FONT`. `description`‑egenskapen innehåller ett mänskligt läsbart meddelande som “Font 'MyFancyFont' was substituted with 'Arial'”.

### Förväntad konsolutskrift

Om källdokumentet refererar till ett teckensnitt som inte är installerat, kommer du att se något liknande:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Om dokumentet endast använder teckensnitt som finns på maskinen, förblir callbacken tyst och du får bara den sista raden “Document loaded successfully.”.

---

## Upptäck saknade teckensnitt i ditt dokument

Du kanske undrar, *“Är en substitutionsvarning samma sak som ett saknat teckensnitt?”* I de flesta fall, ja – Aspose.Words ersätter ett saknat teckensnitt med ett reservteckensnitt och rapporterar det via `SUBSTITUTED_FONT`. Det finns dock kantfall där ett teckensnitt finns men den exakta stilen (fet‑kursiv, specifika OpenType‑funktioner) saknas, vilket leder till en subtil substitution.

För att vara helt säker på att du har fångat varje lucka kan du kombinera varningscallbacken med en efter‑inläsnings‑inspektion:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Proffstips:** Om du hittar några körningar som fortfarande refererar till det saknade teckensnittet, kan du ersätta dem i farten:

```java
font.setName("Arial"); // fallback
```

På så sätt garanterar du ett konsekvent visuellt resultat, även om den ursprungliga varningen undertrycktes.

---

## Vanliga fallgropar & hur man undviker dem

| Fallgrop | Varför det händer | Lösning |
|----------|-------------------|--------|
| **Glömma att sätta callbacken** | `LoadOptions` har som standard en ingen‑åtgärd‑callback, så varningar försvinner. | Anropa alltid `loadOptions.setWarningCallback(...)` innan du laddar. |
| **Använda fel varningstyp** | `WarningType.SUBSTITUTED_FONT` är den enda enum‑värdet som signalerar saknade teckensnitt. | Filtrera på `WarningType.SUBSTITUTED_FONT` *exakt*; andra typer (t.ex. `UNKNOWN_FILE_FORMAT`) är orelaterade. |
| **Hårdkoda filsökvägar** | Fungerar lokalt men går sönder i CI/CD‑pipelines. | Använd en relativ sökväg eller skicka filplatsen som ett kommandoradsargument. |
| **Ignorera Unicode‑teckensnitt** | Vissa saknade teckensnitt är bara ett problem för vissa tecken. | Testa med ett dokument som innehåller hela teckenuppsättningen du förväntar dig att stödja. |
| **Köra på en huvudlös server utan teckensnittskonfiguration** | Servern kan sakna alla reservteckensnitt, vilket orsakar oväntade substitutioner. | Installera en minimal uppsättning vanliga teckensnitt (Arial, Times New Roman) på servern. |

---

## Utöka lösningen

Nu när du kan **fånga varningar om teckensnittssubstitution**, kanske du vill:

* **Logga varningar till en fil** – ersätt `System.out.println` med en logger som SLF4J.
* **Kasta ett undantag** – användbart i automatiserade pipelines där ett saknat teckensnitt ska få bygget att misslyckas:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Auto‑installera saknade teckensnitt** – ladda ner den erforderliga TTF/OTF vid körning och lägg till den i Java `GraphicsEnvironment`. Det är ett mer avancerat scenario, men helt möjligt.

---

## Diagram (valfritt)

![Diagram som visar flödet för att fånga varningar om teckensnittssubstitution som visar LoadOptions → WarningCallback → Konsolutdata](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Diagram som visar flödet för att fånga varningar om teckensnittssubstitution och illustrerar hur Aspose.Words dirigerar saknade‑teckensnitt‑varningar till en anpassad callback.”

---

## Slutsats

Vi har precis gått igenom hur man **fångar varningar om teckensnittssubstitution** och **upptäcker saknade teckensnitt** när man laddar Word‑dokument med Aspose.Words för Java. Genom att konfigurera ett `LoadOptions`‑objekt och implementera en liten `IWarningCallback` får du full insyn i teckensnitt‑fallback‑processen, vilket gör att du kan logga, ersätta eller avbryta vid saknade typsnitt.

Kort sagt: sätt callbacken, filtrera på `SUBSTITUTED_FONT`, ladda dokumentet och hantera utskriften på det sätt din applikation behöver. Härifrån kan du utöka till loggningsramverk, CI‑kontroller eller till och med automatiserad teckensnittsförsörjning.

Vill du gå längre? Prova:

* **Bädda in teckensnitt** direkt i det sparade dokumentet (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` med `FontEmbeddingMode.EMBED_ALL`).
* **Generera en PDF** efter att ha fixat teckensnitt, för att säkerställa att slutresultatet ser exakt ut som avsett.
* **Skanna en hel mapp** med dokument för saknade teckensnitt och producera en sammanfattningsrapport.

Det var allt för nu – lycka till med kodandet, och må dina dokument alltid renderas med rätt teckensnitt!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}