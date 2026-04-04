---
category: general
date: 2026-04-04
description: Leg waarschuwingen voor lettertypevervanging vast tijdens het laden van
  Word‑documenten met Aspose.Words for Java en detecteer automatisch ontbrekende lettertypen.
  Volg deze stapsgewijze handleiding.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: nl
og_description: Leg waarschuwingen voor lettertypevervanging vast tijdens het laden
  van Word‑documenten met Aspose.Words voor Java en detecteer ontbrekende lettertypen
  in een paar eenvoudige stappen.
og_title: Vang waarschuwingen voor lettertypevervanging op – Detecteer ontbrekende
  lettertypen
tags:
- Aspose.Words
- Java
- Document Processing
title: Vang waarschuwingen voor lettertypevervanging op – Detecteer ontbrekende lettertypen
url: /nl/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font‑substitutiewaarschuwingen vastleggen – Ontdek ontbrekende lettertypen

Heb je ooit **font‑substitutiewaarschuwingen** moeten vastleggen bij het openen van een Word‑bestand, om vervolgens te ontdekken dat een cruciaal lettertype ontbreekt? Je bent niet de enige. In veel bedrijfsprocessen kan een ontbrekend lettertype een perfect opgemaakte rapport veranderen in een onleesbare rommel, en de enige aanwijzing is een stille waarschuwing die de meeste ontwikkelaars nooit zien.

Het goede nieuws is dat Aspose.Words for Java je laat inhaken op het laadproces en **ontbrekende lettertypen** kunt **detecteren** voordat ze later problemen veroorzaken. In deze tutorial lopen we een volledig, uitvoerbaar voorbeeld door dat elke substitutiewaarschuwing direct naar de console print, zodat je kunt beslissen of je het juiste lettertype moet insluiten, vervangen of de gebruiker moet waarschuwen.

Aan het einde van deze gids weet je hoe je:

* Een `LoadOptions`‑object instelt met een aangepaste waarschuwingscallback.
* De callback filtert zodat deze alleen reageert op font‑substitutie‑gebeurtenissen.
* Elk `.docx`‑bestand laadt en de waarschuwingen direct ziet.
* De oplossing uitbreidt om waarschuwingen te loggen, uitzonderingen te gooien of zelfs ontbrekende lettertypen automatisch te installeren.

Geen externe documentatie nodig—slechts een paar regels Java en de Aspose.Words‑JAR.

## Voorvereisten

Voordat we beginnen, zorg dat je het volgende hebt:

* Java 8 of nieuwer geïnstalleerd (de nieuwste LTS‑versie werkt het beste).
* Aspose.Words for Java 23.11 of later – je kunt het Maven‑artifact of de gewone JAR van de Aspose‑website halen.
* Een Word‑document dat een lettertype gebruikt dat niet op je ontwikkelmachine staat (bijv. “MyFancyFont”).  
* Een IDE of teksteditor naar keuze – ik gebruik IntelliJ IDEA, maar Eclipse of VS Code volstaat ook.

Als een van deze onderdelen je onbekend voorkomt, pauzeer dan en installeer ze eerst; de rest van de tutorial gaat ervan uit dat ze klaar zijn.

---

## Font‑substitutiewaarschuwingen vastleggen met Aspose.Words

De kern van de oplossing zit in een `LoadOptions`‑instantie. Door een `IWarningCallback` toe te wijzen, kunnen we elke waarschuwing die de bibliotheek tijdens de laadfase uitzendt onderscheppen.

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

**Waarom dit werkt:**  
`LoadOptions` vertelt Aspose.Words hoe het inkomende bestand moet behandelen. De `IWarningCallback`‑interface is een haakpunt dat een `WarningInfo`‑object ontvangt voor *elke* waarschuwing. Door `info.getWarningType()` te controleren, filteren we alles behalve `SUBSTITUTED_FONT`. De eigenschap `description` bevat een menselijk leesbaar bericht zoals “Font 'MyFancyFont' was substituted with 'Arial'”.

### Verwachte console‑output

Als het bron‑document een lettertype referereert dat niet geïnstalleerd is, zie je iets als:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Als het document alleen lettertypen gebruikt die op de machine aanwezig zijn, blijft de callback stil en krijg je alleen de laatste regel “Document loaded successfully.”.

---

## Ontbrekende lettertypen in je document detecteren

Je vraagt je misschien af: *“Is een substitutiewaarschuwing hetzelfde als een ontbrekend lettertype?”* In de meeste gevallen wel—Aspose.Words vervangt een ontbrekend lettertype door een fallback en meldt dit via `SUBSTITUTED_FONT`. Er zijn echter randgevallen waarin een lettertype wel aanwezig is, maar de exacte stijl (vet‑cursief, specifieke OpenType‑functies) niet, wat leidt tot een subtiele substitutie.

Om er absoluut zeker van te zijn dat je elke leemte hebt opgemerkt, kun je de waarschuwingscallback combineren met een inspectie na het laden:

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

**Pro‑tip:** Als je nog steeds runs vindt die naar het ontbrekende lettertype verwijzen, kun je ze ter plekke vervangen:

```java
font.setName("Arial"); // fallback
```

Zo garandeer je een consistent visueel resultaat, zelfs als de oorspronkelijke waarschuwing onderdrukt was.

---

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|----------|
| **Vergeten de callback in te stellen** | `LoadOptions` heeft standaard een no‑op‑callback, waardoor waarschuwingen verdwijnen. | Roep altijd `loadOptions.setWarningCallback(...)` aan vóór het laden. |
| **Het verkeerde waarschuwings‑type gebruiken** | `WarningType.SUBSTITUTED_FONT` is de enige enum die ontbrekende lettertypen signaleert. | Filter **exact** op `WarningType.SUBSTITUTED_FONT`; andere types (bijv. `UNKNOWN_FILE_FORMAT`) zijn niet relevant. |
| **Hard‑coded bestands‑paden** | Werkt lokaal maar breekt in CI/CD‑pipelines. | Gebruik een relatief pad of geef de bestandslocatie door als command‑line‑argument. |
| **Unicode‑lettertypen negeren** | Sommige ontbrekende lettertypen zijn alleen een probleem voor bepaalde tekens. | Test met een document dat de volledige tekenreeks bevat die je verwacht te ondersteunen. |
| **Uitvoeren op een headless server zonder font‑configuratie** | De server mist mogelijk fallback‑lettertypen, wat onverwachte substituties veroorzaakt. | Installeer een minimale set gangbare lettertypen (Arial, Times New Roman) op de server. |

---

## De oplossing uitbreiden

Nu je **font‑substitutiewaarschuwingen** kunt **vastleggen**, wil je misschien:

* **Waarschuwingen naar een bestand loggen** – vervang `System.out.println` door een logger zoals SLF4J.
* **Een uitzondering gooien** – nuttig in geautomatiseerde pipelines waar een ontbrekend lettertype de build moet laten falen:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Ontbrekende lettertypen automatisch installeren** – download de benodigde TTF/OTF tijdens runtime en voeg deze toe aan de Java `GraphicsEnvironment`. Dat is een geavanceerder scenario, maar volledig haalbaar.

---

## Diagram (optioneel)

![Diagram van het vastleggen van lettertype‑substitutiewaarschuwingen dat LoadOptions → WarningCallback → console‑output toont](capture-font-substitution-warnings-diagram.png)

*Alt‑tekst:* “Diagram van het vastleggen van lettertype‑substitutiewaarschuwingen dat LoadOptions → WarningCallback → console‑output toont”.

---

## Conclusie

We hebben net behandeld hoe je **font‑substitutiewaarschuwingen** kunt **vastleggen** en **ontbrekende lettertypen** kunt **detecteren** bij het laden van Word‑documenten met Aspose.Words for Java. Door een `LoadOptions`‑object te configureren en een kleine `IWarningCallback` te implementeren, krijg je volledige zichtbaarheid op het fallback‑proces van lettertypen, waardoor je kunt loggen, vervangen of afbreken bij ontbrekende typefaces.

Kort samengevat: stel de callback in, filter op `SUBSTITUTED_FONT`, laad het document en verwerk de output zoals jouw applicatie vereist. Vanaf hier kun je uitbreiden naar log‑frameworks, CI‑controles of zelfs geautomatiseerde font‑provisioning.

Wil je verder gaan? Probeer:

* **Lettertypen insluiten** direct in het opgeslagen document (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` met `FontEmbeddingMode.EMBED_ALL`).
* **Een PDF genereren** na het corrigeren van lettertypen, zodat de uiteindelijke output er precies uitziet zoals bedoeld.
* **Een hele map** met documenten scannen op ontbrekende lettertypen en een samenvattend rapport produceren.

Dat is alles voor nu—veel plezier met coderen, en moge je documenten altijd met het juiste lettertype worden weergegeven!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}