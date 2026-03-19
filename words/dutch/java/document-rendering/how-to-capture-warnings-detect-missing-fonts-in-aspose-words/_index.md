---
category: general
date: 2026-03-19
description: Leer hoe u waarschuwingen kunt vastleggen in Aspose.Words voor Java en
  ontbrekende lettertypen kunt detecteren. Deze stapsgewijze gids laat ook zien hoe
  u ontbrekende lettertypen op een elegante manier kunt afhandelen.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: nl
og_description: Hoe waarschuwingen vast te leggen in Aspose.Words voor Java, ontbrekende
  lettertypen te detecteren en ontbrekende lettertypen af te handelen met een volledig
  codevoorbeeld.
og_title: Hoe waarschuwingen vast te leggen – Ontbrekende lettertypen detecteren in
  Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Hoe waarschuwingen vast te leggen – Ontdek ontbrekende lettertypen in Aspose.Words
url: /nl/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe waarschuwingen vast te leggen – Ontbrekende lettertypen detecteren in Aspose.Words

Heb je je ooit afgevraagd **hoe je waarschuwingen kunt vastleggen** wanneer een Word‑document wordt geladen en sommige lettertypen niet beschikbaar zijn op de machine? Je bent niet de enige. In veel real‑world projecten veroorzaken ontbrekende lettertypen stille lay‑outverschuivingen, en de enige manier om te weten wat er is gebeurd is door te luisteren naar de waarschuwingsstroom die Aspose.Words uitzendt.  

In deze tutorial lopen we een volledig, kant‑klaar voorbeeld door dat **ontbrekende lettertypen detecteert**, je **laat zien hoe je ontbrekende lettertypen** programmatisch kunt detecteren, en zelfs een snelle tip geeft over **het omgaan met ontbrekende lettertypen** zodat je output voorspelbaar blijft.

> **Snelle opmerking:** De code werkt met Aspose.Words 23.9 (of nieuwer) en vereist Java 8+.

---

## Wat je nodig hebt

- **Aspose.Words for Java** (Maven/Gradle‑dependency of JAR op het classpath)  
- Een Word‑bestand (`input.docx`) dat een lettertype verwijst dat niet op je systeem is geïnstalleerd (bijv. “Comic Sans MS”)  
- Een Java‑IDE of eenvoudige `javac`/`java`‑commandoregel‑setup  

Er zijn geen andere bibliotheken vereist—alles andere zit in het Aspose.Words‑pakket.

---

## Stap 1 – LoadOptions instellen om waarschuwingen vast te leggen  

Om te beginnen met het luisteren naar waarschuwingen moet je een `LoadOptions`‑instantie maken. Dit object vertelt de loader om alle problemen die het tegenkomt bij te houden, zoals ontbrekende lettertypen.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Waarom dit belangrijk is:** Zonder `LoadOptions` vervangt de loader stilzwijgend ontbrekende lettertypen door het standaard systeemlettertype, en je zou nooit weten dat er een substitutie heeft plaatsgevonden. Het inschakelen van waarschuwingen geeft je volledige zichtbaarheid.

---

## Stap 2 – Het document laden met LoadOptions  

Nu laden we daadwerkelijk het document. De `LoadOptions` die we zojuist hebben gemaakt wordt doorgegeven aan de constructor, zodat alle waarschuwingen die tijdens het parseren worden gegenereerd worden vastgelegd.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Pro tip:** Als je veel bestanden in een batch verwerkt, hergebruik dan dezelfde `LoadOptions`‑instantie om onnodige objectcreatie te vermijden.

---

## Stap 3 – Door de vastgelegde waarschuwingen itereren  

Aspose.Words slaat elke waarschuwing op als een `WarningInfo`‑object. We zijn alleen geïnteresseerd in waarschuwingen gerelateerd aan lettertypen, dus filteren we op `FontSubstitutionWarningInfo`.

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

**Uitleg:**  
- `document.getWarnings()` retourneert een lijst van elke waarschuwing die tijdens het laden is opgetreden.  
- `FontSubstitutionWarningInfo` bevat twee cruciale gegevens: het **aangevraagde lettertype** (het lettertype dat de DOCX vroeg) en het **werkelijke lettertype** waarnaar Aspose.Words terugvalt.  
- Door beide te printen zie je onmiddellijk welke lettertypen ontbreken en welke substitutie heeft plaatsgevonden.

---

## Stap 4 – (Optioneel) Ontbrekende lettertypen programmatisch afhandelen  

Waarschuwingen vastleggen is slechts de helft van het verhaal. Zodra je weet dat een lettertype ontbreekt, wil je misschien **ontbrekende lettertypen afhandelen** door een aangepaste substitutie te bieden of door het probleem te loggen voor later onderzoek.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Waarom dit doen?**  
- Garandeert consistente weergave over verschillende machines.  
- Voorkomt onverwachte lay‑outveranderingen in later gegenereerde PDF‑s of afbeeldingen.  

Je kunt de waarschuwingsdetails ook opslaan in een database, een e‑mail sturen naar het contentteam, of zelfs het proces afbreken als een kritisch lettertype ontbreekt.

---

## Volledig werkend voorbeeld  

Hieronder staat het volledige, uitvoerbare programma. Vervang gewoon `YOUR_DIRECTORY/input.docx` door het pad naar je testbestand, voeg de Aspose.Words‑JAR toe aan je classpath, en voer uit.

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

**Verwachte output** (wanneer “Comic Sans MS” ontbreekt):

```
Requested: Comic Sans MS → Substituted: Arial
```

Nadat de optionele fallback‑code is uitgevoerd, zal het opgeslagen `output.docx` **Arial** gebruiken waar “Comic Sans MS” oorspronkelijk werd verwezen.

---

## Veelgestelde vragen & randgevallen  

| Vraag | Antwoord |
|----------|--------|
| *Wat als het document meerdere ontbrekende lettertypen heeft?* | De lus zal voor elk een waarschuwing genereren. Je kunt ze verzamelen in een `Map<String, String>` voor batchverwerking. |
| *Werkt dit voor PDF's die uit het document worden gegenereerd?* | Absoluut. Lettertype‑substitutie gebeurt tijdens de laadfase, dus elke latere export (PDF, HTML, afbeelding) gebruikt de opgeloste lettertypen. |
| *Kan ik de waarschuwingen onderdrukken in plaats van ze vast te leggen?* | Ja—stel `loadOptions.setWarningCallback(null);` in, maar je verliest zichtbaarheid op ontbrekende lettertypen. |
| *Wordt de waarschuwingslijst gewist na het opslaan?* | De waarschuwingscollectie behoort tot de `Document`‑instantie. Nadat je `document.save()` hebt aangeroepen, blijft de lijst ongewijzigd tenzij je een nieuw `Document` maakt. |
| *Wat gebeurt er met aangepaste lettertypen die in de DOCX zijn ingesloten?* | Ingesloten lettertypen worden beschouwd als beschikbaar; Aspose.Words zal ze gebruiken zelfs als ze niet op het host‑systeem zijn geïnstalleerd. |

---

## Pro‑tips voor productiegebruik  

- **Cache FontSettings:** Als je honderden bestanden verwerkt, maak dan één enkele `FontSettings` met je gewenste fallback‑opties en hergebruik deze om overhead te vermijden.  
- **Log gestructureerde data:** In plaats van gewone `System.out`, schrijf waarschuwingen naar een JSON‑log—dit maakt downstream‑analyse (bijv. “meeste ontbrekende lettertypen”) triviaal.  
- **Vroegtijdig valideren:** Voer een snelle “dry‑load” uit met `LoadOptions` vóór zware verwerking; breek vroeg af als kritieke lettertypen ontbreken.  
- **Thread‑veiligheid:** `Document`‑objecten zijn niet thread‑safe. Houd de verwerking van elk bestand in een eigen thread of gebruik een thread‑local `LoadOptions`.  

---

## Conclusie  

Je weet nu **hoe je waarschuwingen kunt vastleggen** in Aspose.Words voor Java, **ontbrekende lettertypen kunt detecteren**, en **ontbrekende lettertypen kunt afhandelen** met een schone fallback‑strategie. Door `LoadOptions` te gebruiken en te itereren over `document.getWarnings()`, krijg je volledig inzicht in lettertype‑substitutie‑gebeurtenissen, waardoor je gegenereerde documenten er precies zo uitzien als bedoeld in alle omgevingen.

Klaar voor de volgende stap? Probeer dit patroon uit te breiden naar **ontbrekende afbeeldingen detecteren**, **onondersteunde functies bijhouden**, of zelfs **ontbrekende lettertypen automatisch insluiten** in het uitvoerbestand. Dezelfde waarschuwing‑vastleg‑aanpak werkt voor veel andere document‑verwerkingsscenario's, waardoor je code robuust en toekomstbestendig wordt.

Veel plezier met coderen, en moge je documenten altijd prachtig renderen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}