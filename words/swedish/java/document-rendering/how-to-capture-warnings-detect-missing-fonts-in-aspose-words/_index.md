---
category: general
date: 2026-03-19
description: Lär dig hur du fångar varningar i Aspose.Words för Java och upptäcker
  saknade teckensnitt. Denna steg‑för‑steg‑guide visar också hur du hanterar saknade
  teckensnitt på ett smidigt sätt.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: sv
og_description: Hur man fångar varningar i Aspose.Words för Java, upptäcker saknade
  teckensnitt och hanterar saknade teckensnitt med ett komplett kodexempel.
og_title: Hur man fångar varningar – Upptäck saknade teckensnitt i Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Hur man fångar varningar – Upptäck saknade teckensnitt i Aspose.Words
url: /sv/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så fångar du varningar – Upptäck saknade teckensnitt i Aspose.Words

Har du någonsin undrat **hur man fångar varningar** när ett Word‑dokument laddas och vissa teckensnitt inte finns på maskinen? Du är inte ensam. I många verkliga projekt orsakar saknade teckensnitt tysta layoutförändringar, och det enda sättet att veta vad som hänt är att lyssna på varningsströmmen som Aspose.Words avger.  

I den här handledningen går vi igenom ett komplett, färdigt exempel som **upptäcker saknade teckensnitt**, visar dig **hur man upptäcker saknade teckensnitt** programatiskt, och ger även ett snabbt tips om **hantering av saknade teckensnitt** så att ditt resultat förblir förutsägbart.

> **Snabb notering:** Koden fungerar med Aspose.Words 23.9 (eller nyare) och kräver Java 8+.

---

## Vad du behöver

- **Aspose.Words for Java** (Maven/Gradle‑beroende eller JAR på klassvägen)  
- En Word‑fil (`input.docx`) som refererar till ett teckensnitt som inte är installerat på ditt system (t.ex. “Comic Sans MS”)  
- En Java‑IDE eller enkel `javac`/`java`‑kommandoradsuppsättning  

Inga andra bibliotek behövs – allt annat finns i Aspose.Words‑paketet.

---

## Steg 1 – Ställ in LoadOptions för att fånga varningar  

För att börja lyssna på varningar måste du skapa en `LoadOptions`‑instans. Detta objekt instruerar laddaren att hålla reda på eventuella problem den stöter på, såsom saknade teckensnitt.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Varför detta är viktigt:** Utan `LoadOptions` ersätter laddaren tyst saknade teckensnitt med systemets standardteckensnitt, och du skulle aldrig veta att en ersättning skedde. Att aktivera varningar ger dig full insyn.

---

## Steg 2 – Ladda dokumentet med LoadOptions  

Nu laddar vi faktiskt dokumentet. `LoadOptions`‑instansen vi just skapade skickas till konstruktorn, så eventuella varningar som genereras under parsning fångas.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Proffstips:** Om du bearbetar många filer i ett batch‑jobb, återanvänd samma `LoadOptions`‑instans för att undvika onödig objekt‑skapande.

---

## Steg 3 – Iterera över fångade varningar  

Aspose.Words lagrar varje varning som ett `WarningInfo`‑objekt. Vi är bara intresserade av teckensnittsrelaterade varningar, så vi filtrerar på `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Förklaring:**  
- `document.getWarnings()` returnerar en lista med alla varningar som inträffade under inläsning.  
- `FontSubstitutionWarningInfo` innehåller två viktiga data: det **begärda teckensnittet** (det som DOCX‑filen efterfrågar) och det **faktiska teckensnittet** som Aspose.Words föll tillbaka på.  
- Genom att skriva ut båda ser du omedelbart vilka teckensnitt som saknas och vilken ersättning som gjordes.

---

## Steg 4 – (Valfritt) Hantera saknade teckensnitt programatiskt  

Att fånga varningar är bara halva historien. När du vet att ett teckensnitt saknas kan du vilja **hantera saknade teckensnitt** genom att tillhandahålla en anpassad ersättning eller logga problemet för senare granskning.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Varför göra detta?**  
- Säkerställer konsekvent rendering på olika maskiner.  
- Förhindrar oväntade layoutförändringar i PDF‑ eller bildfiler som genereras senare.  

Du kan också lagra varningsdetaljerna i en databas, skicka ett e‑postmeddelande till innehållsteamet, eller till och med avbryta processen om ett kritiskt teckensnitt saknas.

---

## Fullständigt fungerande exempel  

Nedan är det kompletta, körbara programmet. Byt bara ut `YOUR_DIRECTORY/input.docx` mot sökvägen till din testfil, lägg till Aspose.Words‑JAR‑filen i din klassväg och kör.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Förväntad utskrift** (när “Comic Sans MS” saknas):

```
Requested: Comic Sans MS → Substituted: Arial
```

Efter att den valfria reservkoden har körts kommer den sparade `output.docx` att renderas med **Arial** där “Comic Sans MS” ursprungligen refererades.

---

## Vanliga frågor & edge‑cases  

| Question | Answer |
|----------|--------|
| *Vad händer om dokumentet har flera saknade teckensnitt?* | Loopen kommer att generera en varning för varje teckensnitt. Du kan samla dem i en `Map<String, String>` för batch‑behandling. |
| *Fungerar detta för PDF‑filer som genereras från dokumentet?* | Absolut. Teckensnittsersättning sker under inläsningsfasen, så alla senare exporteringar (PDF, HTML, bild) använder de lösta teckensnitten. |
| *Kan jag undertrycka varningarna istället för att fånga dem?* | Ja—sätt `loadOptions.setWarningCallback(null);` men du förlorar insyn i saknade teckensnitt. |
| *Rensas varningslistan efter sparning?* | Varningssamlingen tillhör `Document`‑instansen. Efter att du anropar `document.save()` förblir listan oförändrad såvida du inte skapar ett nytt `Document`. |
| *Vad händer med anpassade teckensnitt som är inbäddade i DOCX‑filen?* | Inbäddade teckensnitt betraktas som tillgängliga; Aspose.Words kommer att använda dem även om de inte är installerade på värdsystemet. |

---

## Proffstips för produktionsanvändning  

- **Cachea FontSettings:** Om du bearbetar hundratals filer, skapa en enda `FontSettings` med dina föredragna reservteckensnitt och återanvänd den för att undvika extra kostnad.  
- **Logga strukturerad data:** Istället för vanlig `System.out`, skriv varningar till en JSON‑logg – detta gör efterföljande analys (t.ex. “mest saknade teckensnitt”) enkelt.  
- **Validera tidigt:** Kör en snabb “dry‑load” med `LoadOptions` innan tung bearbetning; avbryt tidigt om kritiska teckensnitt saknas.  
- **Trådsäkerhet:** `Document`‑objekt är inte trådsäkra. Håll varje fils bearbetning i en egen tråd eller använd en trådlokal `LoadOptions`.  

---

## Slutsats  

Du vet nu **hur man fångar varningar** i Aspose.Words för Java, **upptäcker saknade teckensnitt**, och **hanterar saknade teckensnitt** med en ren reservstrategi. Genom att utnyttja `LoadOptions` och iterera över `document.getWarnings()` får du full insikt i teckensnittsersättningshändelser, vilket säkerställer att dina genererade dokument ser exakt ut som avsett i alla miljöer.

Redo för nästa steg? Prova att utöka detta mönster för att **upptäcka saknade bilder**, **spåra ej stödda funktioner**, eller till och med **automatiskt bädda in saknade teckensnitt** i utdatafilen. Samma varningsfångstmetod fungerar för många andra dokumentbehandlingsscenarier, vilket gör din kod robust och framtidssäker.

Lycka till med kodningen, och må dina dokument alltid renderas vackert!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}