---
category: general
date: 2026-02-15
description: Leer hoe u ontbrekende lettertypen kunt vinden bij het laden van een
  Word‑document in Java met Aspose.Words. Inclusief waarschuwings‑callbacks en afhandeling
  van lettertype‑substitutie.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: nl
og_description: Hoe ontbrekende lettertypen in Java met Aspose.Words te verkrijgen.
  Ontdek waarschuwingscallbacks, het afhandelen van lettertypevervanging en best practices
  voor documentverwerking.
og_title: Hoe ontbrekende lettertypen in Java te verkrijgen – Aspose.Words-gids
tags:
- Aspose.Words
- Java
- Font Management
title: Hoe ontbrekende lettertypen in Java te verkrijgen – Aspose.Words-gids
url: /nl/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

.

Make sure to keep all shortcodes at end.

Now produce final content.

Be careful with markdown formatting: keep blank lines.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe ontbrekende lettertypen in Java te verkrijgen – Aspose.Words‑gids

Heb je ooit een Word‑document in Java geopend en zag je vreemde lettertype‑vervangingen en vroeg je je af **hoe je ontbrekende lettertypen kunt verkrijgen**? Je bent niet de eerste die die verrassing ervaart. In veel bedrijfsapplicaties kunnen waarschuwingen over ontbrekende lettertypen de visuele nauwkeurigheid van rapporten, contracten of marketingmateriaal breken.

Het goede nieuws? Aspose.Words biedt een nette manier om die waarschuwingen vast te leggen via een callback, zodat je kunt loggen, vervangen of zelfs gebruikers kunt waarschuwen voordat het document wordt gerenderd. In deze tutorial lopen we een volledig, uitvoerbaar voorbeeld door dat laat zien **hoe je ontbrekende lettertypen kunt verkrijgen**, uitlegt waarom de callback belangrijk is, en behandelt een paar edge‑case‑trucs die je in real‑world projecten nodig kunt hebben.

> **Pro tip:** Als je al Aspose.Words 22.12 of nieuwer gebruikt, werkt de hieronder getoonde API direct uit de doos zonder extra configuratie.

---

![Diagram dat laat zien hoe ontbrekende lettertypen te verkrijgen met behulp van de Aspose.Words‑waarschuwing callback](how-to-get-missing-fonts-diagram.png "diagram hoe ontbrekende lettertypen te verkrijgen")

## Wat deze tutorial behandelt

- Het instellen van een **Java LoadOptions warning callback** om font‑substitutie‑waarschuwingen vast te leggen.  
- Het filteren van de waarschuwingen zodat je alleen diegene ziet die met ontbrekende lettertypen te maken hebben.  
- Het afdrukken van een duidelijk, menselijk leesbaar rapport over welke lettertypen zijn vervangen en waarmee ze zijn vervangen.  
- Tips voor het verwerken van grote documenten, het aanpassen van het waarschuwingsniveau, en het integreren van de oplossing in een grotere verwerkings‑pipeline.

Aan het einde van deze gids kun je de vraag “**hoe je ontbrekende lettertypen kunt verkrijgen**?” beantwoorden met een kant‑klaar code‑fragment en een solide begrip van de onderliggende mechanismen.

### Vereisten

- Java 8 of nieuwer geïnstalleerd.  
- Aspose.Words for Java‑bibliotheek (download van de officiële site of toevoegen via Maven/Gradle).  
- Een Word‑document dat verwijst naar een lettertype dat niet op je machine is geïnstalleerd (bijv. `MissingFont.docx`).  

Als je een van deze onderdelen mist, haal de bibliotheek dan nu—het toevoegen aan Maven is zo simpel als:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Stap 1: Een collectie voorbereiden voor font‑substitutie‑waarschuwingen

Voordat we het document laden, hebben we een plek nodig om eventuele waarschuwingen die Aspose.Words uitzendt op te slaan. Een `ArrayList<WarningInfo>` werkt prima omdat het de volgorde behoudt en ons later laat itereren.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Waarom dit belangrijk is:* De waarschuwings‑callback kan tientallen keren afgaan voor één enkel bestand—denk aan elke ontbrekende glyf, elk probleem met een ingesloten afbeelding, enzovoort. Door ze eerst te verzamelen, houd je de laadfase snel en verwerk je ze later in een gecontroleerde lus.

---

## Stap 2: LoadOptions configureren met een waarschuwings‑callback

Aspose.Words laat je een `IWarningCallback` injecteren. Binnen de callback voegen we elke `WarningInfo` toe aan onze lijst uit Stap 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Uitleg:* De `warning`‑methode wordt **synchroon** aangeroepen tijdens het laden van het document. Door simpelweg de `WarningInfo` in `fontWarnings` te plaatsen, vermijden we zware I/O (zoals loggen naar een bestand) die het laden zou kunnen vertragen. Dit patroon—verzamelen‑dan‑verwerken—is de aanbevolen manier om grote aantallen waarschuwingen af te handelen.

---

## Stap 3: Het document laden met de geconfigureerde opties

Nu lezen we daadwerkelijk het Word‑bestand. Als het document lettertypen bevat die niet geïnstalleerd zijn, zal Aspose.Words ze automatisch substitueren en de waarschuwings‑callback activeren die we zojuist hebben gekoppeld.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Wat er onder de motorkap gebeurt:* Aspose.Words analyseert de font‑tabel van het bestand, vergelijkt deze met de lettertypen die beschikbaar zijn op het host‑OS, en voor elke ontbrekende entry maakt het een `WarningInfo` met `WarningSource.FontSubstitution`. Die bron is de sleutel die we gebruiken om de waarschuwingen over ontbrekende lettertypen te isoleren.

---

## Stap 4: Alleen font‑substitutie‑waarschuwingen filteren en weergeven

Na het laden kan `fontWarnings` een mix van berichten bevatten (bijv. verouderde functies, afbeeldingsproblemen). We zijn alleen geïnteresseerd in ontbrekende lettertypen, dus lopen we door de lijst en printen we een beknopt rapport.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Voorbeeldoutput**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Waarom dit nuttig is:* Het veld `description` vertelt je welk lettertype het document vroeg, terwijl `additionalInfo` aangeeft welk lettertype Aspose.Words daadwerkelijk heeft gebruikt. Met die gegevens kun je:

- De gebruiker vragen het ontbrekende lettertype te installeren.  
- Programma­matig een vervangend lettertype in het document embedden (`doc.getFontInfos().add(...)`).  
- Het evenement loggen voor compliance‑audits.

---

## Edge‑cases en veelvoorkomende variaties behandelen

### 1. Niet‑font‑waarschuwingen onderdrukken

Als je alleen font‑gerelateerde berichten wilt, kun je de callback strakker maken:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Dit vermindert het geheugenverbruik bij het verwerken van enorme batches.

### 2. Waarschuwings‑ernst aanpassen

Aspose.Words categoriseert waarschuwingen op `WarningType`. Voor ontbrekende lettertypen zie je meestal `WarningType.FontSubstitution`. Als je ze als fouten wilt behandelen (bijv. het laden aborteren), gooi dan een uitzondering in de callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Werken met streams in plaats van bestanden

Soms komen documenten uit een database of een HTTP‑verzoek. Dezelfde aanpak werkt met een `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Vergeet alleen niet de stream te sluiten na het laden.

### 4. Een aangepaste lettertype‑map gebruiken

Als je een verzameling bedrijfslettertypen op een gedeelde schijf hebt, wijs Aspose.Words dan naar die map:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Nu zoekt de bibliotheek daar *voordat* hij terugvalt op systeemlettertypen, waardoor het aantal ontbrekende‑lettertype‑waarschuwingen drastisch wordt verminderd.

---

## Volledig werkend voorbeeld

Alles samengevoegd, hier is een zelfstandige klasse die je in elk Java‑project kunt plaatsen:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Voer dit programma uit, en je ziet een nette lijst van elk lettertype dat Aspose.Words moest vervangen. Geen extra bibliotheken, geen verborgen magie—alleen pure Java en de kracht van de **Aspose.Words missing font**‑API.

---

## Conclusie

We hebben de kernvraag beantwoord **hoe je ontbrekende lettertypen kunt verkrijgen** in een Java‑omgeving met behulp van Aspose.Words. Door een `LoadOptions`‑warning callback te koppelen, `WarningInfo`‑objecten te verzamelen en te filteren op `FontSubstitution`‑bronnen, krijg je volledige zichtbaarheid op font‑gerelateerde problemen voordat er iets wordt gerenderd. De aanpak schaalt van single‑file utilities tot massale batch‑processors, en is flexibel genoeg om aangepaste lettertype‑mappen, ernst‑afhandeling of stream‑gebaseerde invoer te ondersteunen.

Volgende stappen? Probeer de vervangen lettertypen direct in het document te embedden (`doc.getFontInfos().add(...)`) zodat het uiteindelijke bestand echt zelf‑voorzienend is, of integreer het waarschuwingsrapport in een monitoring‑dashboard. Je kunt ook gerelateerde onderwerpen verkennen zoals **document processing Java**, **Aspose.Words font substitution warning**, en **Java LoadOptions warning callback** om je expertise verder uit te breiden.

Happy coding, en moge je documenten altijd renderen met de lettertypen die je verwacht!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}