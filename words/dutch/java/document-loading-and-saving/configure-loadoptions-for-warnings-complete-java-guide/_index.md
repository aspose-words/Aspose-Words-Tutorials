---
category: general
date: 2026-06-30
description: Configureer LoadOptions voor waarschuwingen in Aspose.Words Java. Leer
  hoe u een waarschuwingscallback instelt voor lettertypevervanging en andere load‑options‑waarschuwingen.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: nl
og_description: Configureer LoadOptions voor waarschuwingen in Aspose.Words Java.
  Deze gids laat zien hoe u waarschuwingen voor lettertype‑substitutie kunt vastleggen
  met een waarschuwingscallback.
og_title: Configureer LoadOptions voor waarschuwingen – Java‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Configureer LoadOptions voor waarschuwingen – Complete Java-gids
url: /nl/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LoadOptions configureren voor waarschuwingen – Complete Java-gids

Heb je ooit **LoadOptions voor waarschuwingen moeten configureren** bij het openen van een Word‑document met Aspose.Words voor Java? Je bent niet de enige. Veel ontwikkelaars lopen tegen een probleem aan wanneer een ontbrekend lettertype stilletjes wordt vervangen, waardoor de uiteindelijke PDF er niet meer volgens het merk uitziet. Het goede nieuws? Door een **Java‑waarschuwings‑callback** in je `LoadOptions` te integreren, kun je elke waarschuwing voor lettertype‑vervanging opvangen op het moment dat deze zich voordoet.

In deze tutorial lopen we een praktische voorbeeld stap voor stap door, dat niet alleen laat zien hoe je de callback instelt, maar ook uitlegt *waarom* elk onderdeel belangrijk is. Aan het einde kun je **lettertype‑waarschuwingen afhandelen**, ze loggen, of zelfs lettertypen on‑the‑fly vervangen — zonder giswerk.

## Wat je zult meenemen

- Een volledig uitvoerbaar Java‑programma dat elke lettertype‑vervangingswaarschuwing afdrukt.
- Een begrip van de werking van **Aspose.Words lettertype‑vervanging**.
- Tips voor het aanpassen van waarschuwingafhandeling voor grotere projecten.
- Inzicht in **document‑laadopties** en wanneer je ze moet aanpassen.

> **Voorvereiste:** Java 8+ en de Aspose.Words voor Java‑bibliotheek (versie 23.9 of later). Geen andere externe afhankelijkheden zijn nodig.

---

## Stap 1: LoadOptions configureren voor waarschuwingen

Het eerste wat je nodig hebt is een `LoadOptions`‑instantie die weet dat hij waarschuwingen moet rapporteren. Beschouw `LoadOptions` als de gereedschapskist die je aan Aspose.Words geeft voordat het bestand zelfs maar wordt geopend.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Waarom dit belangrijk is:**  
`LoadOptions` bepaalt hoe de bibliotheek het document leest. Door een `IWarningCallback` toe te wijzen, vertel je Aspose.Words om jouw code aan te roepen telkens wanneer het iets merkwaardigs tegenkomt — zoals een ontbrekend lettertype. Zonder dit zou de bibliotheek stilletjes het lettertype vervangen en zou je het nooit weten.

> **Pro‑tip:** Als je *alle* waarschuwingen wilt vastleggen, laat dan de `if`‑controle weg. Voor nu richten we ons op lettertype‑problemen omdat die de meest voorkomende bron van lay‑out‑verrassingen zijn.

---

## Stap 2: Het document laden met de geconfigureerde opties

Nu de callback klaar is, laad je je `.docx` (of een ander ondersteund formaat) met dezelfde `LoadOptions`. Hier komen de **document‑laadopties** daadwerkelijk in werking.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Achter de schermen:**  
Wanneer Aspose.Words `input.docx` parseert, scant het de lettertype‑tabellen. Als een in het document gerefereerd lettertype niet op de host‑machine is geïnstalleerd, genereert de engine een `FONT_SUBSTITUTION`‑waarschuwing, die onmiddellijk de eerder gedefinieerde callback activeert.

---

## Stap 3: Het document opslaan – De waarschuwingen zijn al afgedrukt

Het document opslaan is eenvoudig, maar het is het moment waarop je kunt verifiëren dat de callback correct is geactiveerd. Alle waarschuwingen worden tijdens de laadstap afgedrukt, dus de opslaan‑bewerking is slechts een opruiming.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Verwachte console‑output:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Als je niets ziet, gebruikte het document alleen geïnstalleerde lettertypen, of was de callback niet correct gekoppeld — controleer stap 1 nogmaals.

---

## Stap 4: Breid de callback uit om **lettertype‑waarschuwingen** elegant af te handelen

Afdrukken naar de console is prima voor demo's, maar productcode vereist vaak een uitgebreidere afhandeling: loggen naar een bestand, waarschuwingen verzenden, of zelfs lettertypen programmatically vervangen.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Waarom je dit zou doen:**  
Een logbestand geeft je post‑mortem inzicht, vooral bij het verwerken van batches documenten. Het optionele substitutie‑blok laat zien hoe je **LoadOptions voor waarschuwingen configureert** *en* ingrijpt om een bedrijfs‑lettertype‑beleid af te dwingen.

---

## Geavanceerd: Andere **Aspose.Words lettertype‑vervanging** scenario's beheren

De waarschuwing‑callback is niet beperkt tot ontbrekende lettertypen. Je kunt ook vangen:

- **Niet‑ondersteunde Unicode‑tekens** (`WarningType.UNSUPPORTED_CHAR`).
- **Complexe script‑problemen** (`WarningType.COMPLEX_SCRIPT`).

Breid simpelweg de `if`‑statement uit:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Dit maakt je oplossing robuust voor meertalige documenten, een veelvoorkomende randgeval in wereldwijde toepassingen.

---

## Volledig werkend voorbeeld

Hieronder staat het volledige, kant‑klaar programma. Plak het in een Java‑IDE, vervang de `YOUR_DIRECTORY`‑plaatsaanduidingen, en klik op *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Verwacht resultaat

- Console drukt eventuele lettertype‑vervangingswaarschuwingen af.
- `font-warnings.log` bevat een tijdstempel‑lijst (als je de optionele logging hebt behouden).
- `output.docx` wordt opgeslagen met vervangen lettertypen, overeenkomstig de fallback die je hebt gedefinieerd.

---

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|-----------|
| **Geen waarschuwingen verschijnen** | De callback was niet gekoppeld, of het document gebruikt alleen geïnstalleerde lettertypen. | Controleer dat `loadOptions.setWarningCallback(...)` wordt aangeroepen *voordat* het document wordt geladen. |
| **FileNotFoundException** op `input.docx` | Pad is onjuist of het bestand is niet bij het project inbegrepen. | Gebruik een absoluut pad of plaats het bestand in de resources‑map van het project. |
| **Prestatie‑vertraging** bij het verwerken van duizenden documenten | Overmatig loggen naar schijf bij elke waarschuwing. | Buffer logs en schrijf in batches, of beperk logging tot alleen kritieke waarschuwingen. |
| **Onverwachte lettertype‑vervanging** ondanks fallback | De substitutietabel werd niet vroeg genoeg toegepast. | Stel de substitutie‑instellingen **voor** het laden van het document in, of gebruik `FontSettings.setSubstitutionSettings` globaal. |

---

## Volgende stappen

Nu je **LoadOptions voor waarschuwingen hebt geconfigureerd** beheerst, overweeg deze vervolgonderwerpen:

- **Batchverwerking**: Loop over een map met documenten en verzamel alle lettertype‑waarschuwingen in één rapport.
- **Aangepaste lettertype‑providers**: Laad lettertypen vanaf een netwerkschijf of ingebedde resources in plaats van het lokale OS.
- **Integreren met logging‑frameworks** zoals Log4j voor enterprise‑traceerbaarheid.
- Verken andere **document‑laadopties** zoals `LoadFormat`‑detectie of `Password`‑afhandeling voor beveiligde bestanden.

Elk van deze bouwt voort op hetzelfde patroon — maak een `LoadOptions`‑object, koppel de juiste callbacks, en laat Aspose.Words het zware werk doen.

---

## Conclusie

We hebben een grondige duik genomen in hoe je **LoadOptions voor waarschuwingen configureert** in Aspose.Words voor Java, een **Java‑waarschuwings‑callback** hebt opgezet, en die informatie gebruikt om **lettertype‑waarschuwingen** intelligent af te handelen. De code is compact, de concepten zijn duidelijk, en je hebt nu een stevige basis om waarschuwingafhandeling uit te breiden naar andere scenario's zoals niet‑ondersteunde tekens of complexe scripts.

Probeer het, pas de substitutietabel aan om bij je merklettertypen te passen, en zie die stille lettertype‑vervangingen verdwijnen. Veel programmeerplezier!

--- 

![Diagram showing the flow of configuring LoadOptions for warnings, loading a document, capturing font substitution events, and saving the output](configure-loadoptions-for-warnings-diagram.png "Configure LoadOptions for warnings flow")


## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Lettertype‑vervangingswaarschuwingen vastleggen in Java met Aspose.Words – Complete gids](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Hoe LoadOptions in te stellen in Aspose.Words voor Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Hoe RTF‑documenten te laden met het configureren van RTF‑Load‑Options in Aspose.Words voor Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}