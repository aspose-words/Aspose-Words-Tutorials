---
category: general
date: 2026-05-30
description: Registreer een waarschuwingscallback in Java om ontbrekende lettertypen
  bij te houden en pas het laden van documenten aan met Aspose.Words. Leer de volledige
  stapsgewijze oplossing.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: nl
og_description: Registreer waarschuwingscallback in Java om ontbrekende lettertypen
  bij te houden en het laden van documenten aan te passen. Volledige gids met code
  en uitleg.
og_title: Waarschuwingscallback registreren in Java – Ontbrekende lettertypen bijhouden
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Waarschuwingscallback registreren in Java – Ontbrekende lettertypen bijhouden
url: /nl/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Waarschuwingscallback registreren in Java – Ontbrekende lettertypen bijhouden

Heb je je ooit afgevraagd hoe je **ontbrekende lettertypen kunt bijhouden** bij het laden van een Word‑document met Aspose.Words for Java? Misschien heb je die stille lettertype‑vervangingen gezien en gedacht: “Wat is er met mijn lay‑out gebeurd?” Het goede nieuws is dat je niet hoeft te raden. Door **een waarschuwingscallback te registreren** kun je elk lettertype‑vervangings‑evenement vastleggen op het moment dat het document wordt gelezen, en kun je ook **documentladen aanpassen** zodat het in je pipeline past.

In deze tutorial lopen we een real‑world voorbeeld door dat precies laat zien hoe je de callback instelt, waarom het belangrijk is, en hoe je de rest van je verwerkingspipeline schoon houdt. Aan het einde heb je een kant‑klaar Java‑klasse die elke ontbrekende‑lettertype‑waarschuwing naar de console schrijft en een verwerkte kopie van het document opslaat. Geen externe referenties nodig – alleen pure, uitvoerbare code.

> **Wat je krijgt:**  
> • Een compleet Java‑programma met Aspose.Words  
> • Stapsgewijze uitleg van elke regel  
> • Tips voor het afhandelen van randgevallen zoals versleutelde bestanden of grote batches  
> • Een snelle sanity‑check die je op elk `.docx`‑bestand kunt uitvoeren

## Vereisten

Voordat we beginnen, zorg dat je het volgende hebt:

- **Java 17** (of een recente JDK) geïnstalleerd en `JAVA_HOME` ingesteld.  
- **Aspose.Words for Java** JAR op je classpath. Je kunt de nieuwste versie ophalen uit de Maven Central‑repository:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Een voorbeeld‑Word‑document (`input.docx`) waarvan je vermoedt dat het lettertypen bevat die niet op je machine zijn geïnstalleerd.  
- Een IDE of command‑line build‑tool (Maven/Gradle) waar je je prettig bij voelt.

Dat is alles. Geen extra lettertypen, geen extra services – alleen plain Java en Aspose.Words.

## Waarom een waarschuwingscallback registreren?

Beschouw de **waarschuwingscallback** als een beveiligingscamera voor je document‑laadproces. Wanneer Aspose.Words een ontbrekende glyph tegenkomt, gooit het geen uitzondering; het vervangt stilletjes door een fallback‑lettertype. Die stille vervanging kan je lay‑out breken, vooral in merk‑kritieke PDF’s of facturen. Door een callback te registreren kun je:

1. **Realtime inzicht krijgen** – elke `FONT_SUBSTITUTION`‑waarschuwing wordt direct geleverd.  
2. **Loggen of reageren** – je kunt naar een bestand loggen, een alarm activeren, of zelfs het lettertype programmatisch vervangen.  
3. **Schone output behouden** – weten welke lettertypen ontbreken stelt je in staat de bron‑documenten te corrigeren vóór publicatie.

Kortom, de callback maakt van een verborgen probleem een zichtbaar probleem, waardoor je document‑pipeline veel betrouwbaarder wordt.

## Stap 1 – Maak `LoadOptions` om aan te passen hoe het document wordt geladen

Het eerste wat we doen is `LoadOptions` instantieren. Dit object is de poort voor elke laad‑tijd‑aanpassing die je nodig kunt hebben, van wachtwoord‑afhandeling tot onze **register warning callback**‑functie.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Waarom niet gewoon `new Document("file.docx")` aanroepen? Omdat je zonder `LoadOptions` de kans verliest om in te haken op de laad‑events. `LoadOptions` is de enige plek waar Aspose.Words je **documentladen kunt aanpassen**.

## Stap 2 – Registreer een waarschuwingscallback om ontbrekende lettertypen bij te houden

Nu komt de ster van de show: we **registreren een waarschuwingscallback** die `IWarningCallback` implementeert. Binnen de `warning`‑methode filteren we op `WarningType.FONT_SUBSTITUTION` en printen we een nuttig bericht.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Een paar dingen om op te merken:

- **Waarom `IWarningCallback`?** Het is de interface die Aspose.Words gebruikt voor alle waarschuwings‑typen, waardoor je één toegangspunt hebt voor vele mogelijke issues.  
- **Filtering is cruciaal** – zonder de `if`‑check zie je waarschuwingen over ontbrekende afbeeldingen, verouderde functies, enz., wat je logs zou vervuilen.  
- **Thread‑safety** – de callback draait op dezelfde thread die het document laadt, dus je kunt veilig gedeelde structuren bijwerken als je later resultaten wilt aggregeren.

Dat fragment **registreert de waarschuwingscallback**, en vanaf nu wordt elk ontbrekend‑lettertype‑event naar `stdout` geprint. Dit is de kern van **ontbrekende lettertypen bijhouden**.

## Stap 3 – Laad het document met de geconfigureerde `LoadOptions`

Met de callback op zijn plaats, laden we eindelijk het bestand. Als het document een lettertype aanroept dat je niet hebt, wordt de callback geactiveerd voordat het documentobject volledig is opgebouwd.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Vervang `YOUR_DIRECTORY` door het daadwerkelijke pad op jouw machine. De `Document`‑constructor leest het bestand, past eventueel een wachtwoord toe (als je er één in `loadOptions` hebt gezet), en triggert de waarschuwingscallback voor elk ontbrekend lettertype. Je ziet output zoals:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Die regel bewijst dat je succesvol **ontbrekende lettertypen hebt bijgehouden**.

## Stap 4 – Verwerk het document verder (optioneel)

In deze fase kun je het document manipuleren zoals je wilt – tekst vervangen, afbeeldingen invoegen, of zelfs programmatisch de vervangen lettertypen uitwisselen. De callback heeft je al een lijst gegeven van problematische lettertypen, dus kun je bijvoorbeeld een fallback‑lettertype insluiten:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Voel je vrij om dit blok over te slaan als je alleen **ontbrekende lettertypen wilt bijhouden**. Het belangrijkste is dat je nu de informatie hebt om een weloverwogen beslissing te nemen.

## Stap 5 – Sla het verwerkte document op

Tot slot persisteer je het document. Je kunt het origineel overschrijven, opslaan op een nieuwe locatie, of exporteren naar PDF – alles zonder de waarschuwingsdata die je eerder hebt vastgelegd te verliezen.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Het uitvoeren van de volledige klasse levert console‑output voor elk ontbrekend lettertype en een nieuw bestand genaamd `processed.docx` in dezelfde map.

## Volledig werkend voorbeeld

Hieronder staat de volledige Java‑klasse die je kunt copy‑pasten in je IDE. Hij bevat alles wat we hebben besproken, plus een kleine `main`‑method wrapper.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Verwachte output

Wanneer je het programma draait tegen een document dat een lettertype gebruikt dat niet op je systeem is geïnstalleerd, zie je iets als:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Als het document **geen ontbrekende lettertypen** bevat, blijft de console stil tot de laatste regel “Document saved successfully.” – precies wat je zou verwachten van een goed‑gedragende **register warning callback**‑implementatie.

## Pro‑tips & veelvoorkomende valkuilen

- **Meerdere callbacks?** Aspose.Words staat slechts één waarschuwingshandler toe. Als je zowel naar een bestand als naar de console wilt loggen, implementeer dan een samengestelde callback die de waarschuwing naar meerdere bestemmingen doorstuurt.  
- **Grote batches** – bij het verwerken van honderden bestanden kun je beter één `LoadOptions`‑instantie hergebruiken; per bestand een nieuwe maken voegt onnodige overhead toe.  
- **Versleutelde documenten** – stel het wachtwoord in op `LoadOptions` vóór het laden, anders krijg je een `IncorrectPasswordException` voordat de callback ooit wordt geactiveerd.  
- **Prestaties** – de callback draait synchroon. Als je naar een externe service logt, buffer dan de berichten en flush ze pas na het laden om I/O‑knelpunten te vermijden.  
- **Lettertype‑fallback** – je kunt ook een aangepaste `FontSource`‑collectie leveren als je propriëtaire lettertypen hebt die Aspose.Words moet overwegen vóór het terugvallen op systeem‑lettertypen.

## Conclusie

Je hebt zojuist geleerd hoe je **een waarschuwingscallback registreert** in Java, effectief **ontbrekende lettertypen bijhoudt**, en **documentladen aanpast** met Aspose.Words. De oplossing is zelf‑voorzienend, draait met één `main`‑methode, en geeft je directe zichtbaarheid in elke lettertype‑vervanging die anders onopgemerkt zou blijven.

Volgende stappen? Probeer de callback uit te breiden zodat waarschuwingen naar een CSV‑bestand worden geschreven voor auditdoeleinden, of combineer hem met een batch‑processor die automatisch ontbrekende lettertypen insluit. Je kunt ook andere waarschuwings‑typen verkennen zoals `IMAGE_SUBSTITUTION` of `DEPRECATED_FEATURE` – hetzelfde patroon is van toepassing.

Happy coding, en moge je documenten altijd precies renderen zoals je bedoeld hebt!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")

## Wat kun je hierna leren?

- [Waarschuwingscallback in Word‑document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Thema‑kleuren & lettertypen aanpassen in Aspose.Words Java: Een uitgebreide gids](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Wijzigingen bijhouden in Word‑documenten met Aspose.Words Java: Een complete gids voor documentrevisies](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}