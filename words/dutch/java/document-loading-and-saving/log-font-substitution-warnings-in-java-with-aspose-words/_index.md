---
category: general
date: 2026-06-17
description: Log waarschuwingen voor lettertypevervanging in Java met Aspose.Words
  – registreer ontbrekende lettertypen tijdens het laden van het document en houd
  uw output consistent.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: nl
og_description: Log waarschuwingen voor lettertypevervanging in Java met Aspose.Words.
  Leer hoe je waarschuwingen voor ontbrekende lettertypen tijdens het laden van documenten
  kunt vastleggen en je PDF's onberispelijk houdt.
og_title: Log waarschuwingen voor lettertypevervanging in Java – Complete gids
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
title: Log waarschuwingen voor lettertypevervanging in Java met Aspose.Words
url: /nl/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Log Font Substitutie Waarschuwingen in Java – Complete Gids

Heb je je ooit afgevraagd hoe je **log font substitutie waarschuwingen** kunt **loggen** wanneer een Word‑document een lettertype ophaalt dat je niet op de server hebt? Je bent niet de enige die zich afvraagt waarom lettertypen stilletjes worden vervangen. Het goede nieuws? Aspose.Words for Java biedt een nette manier om die substituties te vangen op het moment dat een document wordt geladen.

In deze tutorial lopen we een praktische voorbeeld stap voor stap door dat precies laat zien hoe je een waarschuwing‑callback registreert, filtert op font‑substitutie‑meldingen, en ze naar de console schrijft (of naar elke logger die je verkiest). Aan het einde heb je een herbruikbare code‑fragment die je in elk Java‑project kunt plaatsen dat **Aspose.Words Java** gebruikt.

## Wat je zult leren

- Hoe je **LoadOptions** configureert om waarschuwingen vast te leggen.
- Hoe je een **IWarningCallback** implementeert die alleen reageert op **font substitution**‑gebeurtenissen.
- Hoe je een document veilig laadt terwijl je een duidelijk audit‑pad van ontbrekende lettertypen bijhoudt.
- Tips om de oplossing uit te breiden naar bestands‑gebaseerde logs of monitoringsystemen.

### Vereisten

- Java 8 of nieuwer (de code werkt ook met Java 11+).
- Aspose.Words for Java bibliotheek (versie 23.10 of later wordt aanbevolen).
- Een voorbeeld‑`.docx` die een lettertype verwijst dat niet op je machine is geïnstalleerd (bijv. `MissingFont.docx`).

Er zijn geen extra frameworks nodig—alleen plain Java en de Aspose‑JARs.

---

## Stap 1: Configureer LoadOptions voor Aspose.Words Java

Voordat je waarschuwingen kunt onderscheppen, heb je een **LoadOptions**‑instantie nodig. Dit object vertelt Aspose.Words hoe het zich moet gedragen tijdens het parseren van het binnenkomende bestand.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Waarom is deze stap cruciaal? Zonder een `LoadOptions`‑object vervangt de bibliotheek stilletjes ontbrekende lettertypen en zie je nooit een spoor. Door er expliciet een te maken, open je de deur naar een aangepaste **warning callback** die precies kan loggen waar je om geeft.

> **Pro tip:** Als je veel documenten in één batch laadt, hergebruik dan een enkele `LoadOptions`‑instantie om onnodige objectcreatie te vermijden.

---

## Stap 2: Implementeer een Warning Callback voor Font Substitutie

Aspose.Words wordt geleverd met de `IWarningCallback`‑interface. Door deze te implementeren kun je bepalen wat er gebeurt wanneer de engine een `WarningInfo` genereert. In ons geval willen we alleen reageren op `WarningType.FONT_SUBSTITUTION`.

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

Een paar dingen om op te merken:

1. **Filtering** – De `if`‑statement zorgt ervoor dat we ongerelateerde waarschuwingen (zoals lay‑outproblemen) negeren en het logboek netjes houden.
2. **Thread safety** – De callback draait op dezelfde thread die het document laadt, dus je hebt geen extra synchronisatie nodig voor eenvoudige console‑output. Als je naar een gedeelde logger schrijft, zorg er dan voor dat deze thread‑veilig is.
3. **Extensibility** – Wil je naar een bestand schrijven? Vervang `System.out.println` door `java.util.logging.Logger` of een logging‑framework van derden.

---

## Stap 3: Laad het Document met de Geconfigureerde Opties

Nu de callback aanwezig is, laad je je Word‑bestand. Op het moment dat Aspose.Words het document parseert, zal elk ontbrekend lettertype de hierboven gedefinieerde callback activeren.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Als het bronbestand een lettertype verwijst dat niet geïnstalleerd is, zie je een output vergelijkbaar met:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Die regel is de **log font substitutie waarschuwingen** waar je naar op zoek was. Je kunt er nu op reageren—bijvoorbeeld een gebruiker waarschuwen, overschakelen naar een fallback‑stylesheet, of simpelweg een registratie bijhouden voor compliance.

---

## Stap 4: Ga Door met Normale Verwerking

Na het laden gedraagt het document zich net als elk ander `Document`‑object. Voel je vrij om secties te inspecteren, tekst te extraheren of naar PDF te converteren. Het loggen van waarschuwingen gebeurt automatisch tijdens de laadstap, dus je hebt geen extra code nodig.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

De console zal nu zowel de font‑substitutie‑waarschuwing (indien aanwezig) **als** het aantal secties tonen, wat bevestigt dat het document volledig functioneel is.

---

## Geavanceerde Tips & Randgevallen

### Loggen naar een Bestand in Plaats van de Console

Als je een persistent log wilt, vervang dan de `System.out.println`‑call door een `FileWriter`:

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

Vergeet niet om `IOException` correct af te handelen in productcode.

### Meerdere Documenten Vastleggen in een Loop

Bij het verwerken van een map met documenten kun je dezelfde callback hergebruiken:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Aangezien de callback is gekoppeld aan `loadOptions`, logt elke iteratie automatisch eventuele font‑substitutie‑gebeurtenissen.

### Omgaan met Ingebedde Lettertypen

Aspose.Words kan ontbrekende lettertypen insluiten als je het inschakelt:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Zelfs met insluiting ingeschakeld, wordt de warning callback nog steeds geactiveerd, waardoor je inzicht krijgt in wat er is vervangen.

---

## Volledig Werkend Voorbeeld

Hieronder staat het volledige, kant‑klaar programma. Kopieer het naar een klasse genaamd `FontSubstitutionDiagnostics.java`, pas het bestandspad aan, en voer het uit.

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

**Verwachte output** (ervan uitgaande dat het bron‑doc een ontbrekend lettertype verwijst):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Zowel de console als `font_substitution_log.txt` zullen de waarschuwing bevatten, waardoor je een betrouwbaar audit‑pad krijgt.

---

## Conclusie

We hebben je net laten zien hoe je **font substitutie waarschuwingen** in Java kunt **loggen** met Aspose.Words. Door `LoadOptions` te configureren, een `IWarningCallback` aan te sluiten, en het document te laden, krijg je volledige zichtbaarheid op alle ontbrekende‑lettertype‑gebeurtenissen die anders onopgemerkt zouden blijven. Vanaf hier kun je:

- Waarschuwingen doorsturen naar een centrale logging‑service.
- Alert‑meldingen activeren voor kwaliteits‑control pipelines.
- Deze techniek combineren met andere **document loading**‑strategieën, zoals PDF‑conversie of mail‑merge.

Voel je vrij om te experimenteren—vervang de console‑logger door SLF4J, voeg tijdstempels toe, of stuur alerts naar een monitoring‑dashboard. Het kernpatroon blijft hetzelfde, en nu heb je een solide basis voor robuuste font‑afhandeling in elke Java‑gebaseerde document‑workflow.

Heb je een variant die je wilt delen? Misschien heb je dit geïntegreerd met Spring Boot of een cloud‑functie. Laat een reactie achter hieronder, en laten we het gesprek voortzetten. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}