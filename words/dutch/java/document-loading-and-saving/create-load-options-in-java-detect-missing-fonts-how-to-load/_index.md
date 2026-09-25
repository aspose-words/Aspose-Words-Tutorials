---
category: general
date: 2026-02-18
description: Maak laadopties in Java om ontbrekende lettertypen te detecteren en leer
  hoe je DOCX‑bestanden kunt laden met een waarschuwingscallback.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: nl
og_description: Maak laadopties in Java om ontbrekende lettertypen te detecteren en
  leer hoe je DOCX‑bestanden kunt laden met een waarschuwingscallback.
og_title: Creëer laadopties in Java – Detecteer ontbrekende lettertypen en hoe je
  DOCX laadt
tags:
- java
- aspose-words
- document-processing
title: Maak laadopties in Java – Detecteer ontbrekende lettertypen & hoe DOCX te laden
url: /nl/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

alt attribute is part of HTML attribute; it's text, okay.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Load Options maken in Java – Ontbrekende lettertypen detecteren & hoe een DOCX te laden

Heb je je ooit afgevraagd hoe je **load options maken** die niet alleen een DOCX lezen, maar je ook laten weten wanneer een lettertype ontbreekt? Je bent niet de enige. Ontbrekende lettertypen kunnen een perfect opgemaakt document veranderen in een rommelig geheel, en ze vroegtijdig opsporen bespaart uren debuggen. In deze tutorial lopen we de exacte stappen door om **ontbrekende lettertypen te detecteren** terwijl we je laten zien **hoe een DOCX**-bestanden laadt met een aangepaste waarschuwing‑callback.

## Wat je zult leren

- Hoe je `LoadOptions` instantiateert en een warning‑handler configureert.  
- Waarom de warning‑callback essentieel is voor het opvangen van font‑substitutie‑problemen.  
- De exacte code die nodig is om **een DOCX**‑bestand veilig te **laden**, plus een paar praktische tips voor real‑world projecten.  
- Edge‑case handling, zoals omgaan met andere warning‑types of het laden van PDF’s met dezelfde aanpak.

Geen externe documentatie nodig—alles wat je nodig hebt staat hier.

## Vereisten

- Java 17 of hoger (de API werkt op oudere versies, maar 17 is de ideale keuze).  
- Aspose.Words for Java‑bibliotheek toegevoegd aan je project (`aspose-words-x.x.jar`).  
- Een basisbegrip van Java‑exception handling.  

Als je dat hebt, laten we erin duiken.

![Diagram dat de stroom van het maken van load options, het instellen van een warning‑callback en het laden van een DOCX‑bestand toont](/images/create-load-options-diagram.png){: .center-image alt="Diagram van Load Options stroom"}

## Stap 1: Load Options maken (Hoe een DOCX te laden)

Het eerste wat je moet doen is **load options maken**. Dit object vertelt Aspose.Words hoe het zich moet gedragen wanneer het een bestand opent. Beschouw het als een set instructies die je aan de bibliotheek geeft voordat deze de DOCX ziet.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Waarom niet gewoon `new Document("file.docx")` aanroepen? Omdat je zonder `LoadOptions` het vermogen verliest om te reageren op warnings—zoals ontbrekende lettertypen—tot nadat het document al geladen is, wat voor bepaalde workflows te laat kan zijn.

## Stap 2: Een warning‑callback instellen om ontbrekende lettertypen te detecteren

Nu koppelen we een callback die wordt aangeroepen telkens wanneer Aspose.Words een situatie tegenkomt waarover het je wil waarschuwen. In ons geval zijn we geïnteresseerd in `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Een paar dingen om op te merken:

- **Waarom een callback?** Het wordt uitgevoerd *tijdens* het laadproces, waardoor je de kans krijgt om te loggen of zelfs de bewerking af te breken voordat het document volledig gematerialiseerd is.  
- **Waarom `WarningType.FONT_SUBSTITUTION` controleren?** Dat is de exacte enum‑waarde die Aspose.Words gebruikt voor scenario's met ontbrekende lettertypen. Andere warning‑types (bijv. `TABLE_STRUCTURE`) kunnen op dezelfde manier worden gefilterd indien nodig.  
- **Performance‑tip:** De callback is lichtgewicht; vermijd zware I/O binnen de callback. Als je naar een bestand moet schrijven, zet de berichten in een wachtrij en schrijf ze weg na het laden.

## Stap 3: Het DOCX‑bestand laden met de geconfigureerde opties

Met de opties en callback klaar, kun je eindelijk de DOCX laden. Dit is het gedeelte dat **hoe een docx te laden** beantwoordt terwijl de waarschuwingen die je hebt ingesteld gerespecteerd worden.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Wat gebeurt er onder de motorkap?** Terwijl het bestand wordt gestreamd, controleert Aspose.Words elke font‑referentie. Als een verwezen font niet geïnstalleerd is, activeert het de warning‑callback die we eerder hebben gedefinieerd. Je ziet output zoals:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Die directe feedback is van onschatbare waarde wanneer je batches bestanden op een server verwerkt.

## Volledig werkend voorbeeld

Alles bij elkaar genomen, hier is een zelfstandige programma dat je kunt kopiëren‑plakken in je IDE.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Verwachte output**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Als het bestand geen ontbrekende lettertypen bevat, blijft de callback stil en verschijnt de regel “DOCX loaded”.

## Pro‑tips & edge‑cases

| Situation | What to Do |
|-----------|------------|
| **Meerdere ontbrekende lettertypen** | De callback wordt voor elk font geactiveerd, dus je krijgt een regel per lettertype. Voeg ze samen in een `List<String>` als je later een samenvatting nodig hebt. |
| **Je wilt ook andere warnings opvangen** | Voeg `else if`‑branches toe voor `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT`, enz. |
| **Grote DOCX‑bestanden laden** | Gebruik `LoadOptions.setLoadFormat(LoadFormat.DOCX)` om het formaat aan te geven en de detectie te versnellen. |
| **Draaien in een webservice** | Vermijd `System.out.println`; inject in plaats daarvan een logger (`SLF4J`, `Log4j`) in de callback. |
| **Lettertypen worden tijdens runtime geïnstalleerd** | Na het detecteren van een ontbrekend lettertype kun je het programmatisch laden via `GraphicsEnvironment.registerFont(...)` en het document opnieuw laden. |

## Waarom deze aanpak beter is dan de “Alleen try‑catch”‑methode

Veel ontwikkelaars wikkelen `new Document(...)` simpelweg in een try‑catch‑blok, in de hoop dat een exception hen vertelt over ontbrekende lettertypen. Helaas behandelt Aspose.Words font‑substitutie als een *warning*, niet als een fout, dus er wordt geen exception gegooid. Door **load options te maken** en een warning‑callback toe te voegen, krijg je deterministische inzicht in font‑problemen zonder prestatieverlies.

## Volgende stappen

- **Ontbrekende lettertypen in PDF’s detecteren** – hetzelfde `LoadOptions`‑patroon werkt voor PDF’s, wijzig alleen het bestandspad en het load‑formaat.  
- **Font‑installatie automatiseren** – combineer de callback met een script dat ontbrekende lettertypen uit een gedeelde repository haalt.  
- **Andere warning‑types verkennen** – Aspose.Words kan je waarschuwen voor verouderde tags, complexe tabellen en meer.  

Voel je vrij om te experimenteren: vervang de `Document`‑constructor door een stream (`new Document(InputStream, loadOptions)`) als je met in‑memory data werkt, of koppel meerdere callbacks met een composite‑patroon voor grootschalige verwerkings‑pipelines.

---

### TL;DR

We hebben je laten zien hoe je **load options maakt** in Java, een callback instelt die **ontbrekende lettertypen detecteert**, en uiteindelijk een **DOCX**‑bestand veilig laadt. Met slechts drie beknopte stappen heb je nu een herbruikbaar patroon dat je in elk Aspose.Words‑project kunt gebruiken.

Heb je vragen over andere bestandsformaten of heb je hulp nodig bij het afstemmen van de callback voor jouw specifieke omgeving? Laat een reactie achter hieronder, en happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}