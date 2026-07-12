---
category: general
date: 2026-06-27
description: Leer hoe u lettertypevervangingswaarschuwingen in Java kunt vastleggen
  met Aspose.Words. Deze stapsgewijze tutorial behandelt ook waarschuwing‑callbacks
  en het gebruik van LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: nl
og_description: Vang fontvervangingswaarschuwingen op in Java met Aspose.Words. Volg
  deze gids om waarschuwing‑callbacks in te stellen, LoadOptions te gebruiken en ontbrekende
  lettertypen af te handelen.
og_title: Lettertypevervangingswaarschuwingen vastleggen in Java – Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Lettertypevervangingswaarschuwingen vastleggen in Java met Aspose.Words – Volledige
  gids
url: /nl/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fontvervangingswaarschuwingen vastleggen in Java met Aspose.Words – Complete Guide

Heb je ooit **fontvervangingswaarschuwingen** moeten vastleggen tijdens het laden van een DOCX die exotische lettertypen gebruikt? Je bent niet de enige. In veel real‑world projecten—denk aan geautomatiseerde rapportgeneratoren of batch‑documentconversies—leiden ontbrekende lettertypen tot stille substituties die de lay-outintegriteit kunnen verpesten.  

Gelukkig biedt Aspose.Words een nette manier om naar die waarschuwingen te luisteren. In deze tutorial lopen we door het configureren van **LoadOptions**, het aansluiten van een **Aspose.Words warning callback**, en het afdrukken van elke *font substitution* melding naar de console. Aan het einde weet je precies wanneer een lettertype is vervangen en hoe je hier programmatically op kunt reageren.

> **Wat je krijgt:** een volledig uitvoerbaar Java‑fragment, een uitleg *waarom* elk onderdeel belangrijk is, en tips voor het afhandelen van randgevallen zoals aangepaste lettertype‑mappen.

## Prerequisites & What You’ll Need

Voordat we beginnen, zorg dat je het volgende hebt:

- Java 8 of nieuwer geïnstalleerd (de code werkt ook met Java 11+).
- De nieuwste Aspose.Words for Java JAR (download van de officiële site of Maven Central).
- Een DOCX‑bestand dat verwijst naar lettertypen die niet op je machine geïnstalleerd zijn (bijv. een *font‑rich.docx* uit de Aspose‑demo‑set).
- Een degelijke IDE (IntelliJ IDEA, Eclipse, of zelfs VS Code met Java‑extensies).

Er zijn geen externe libraries nodig buiten Aspose.Words, en het voorbeeld draait in een eenvoudige `main`‑methode.

## Stap 1: LoadOptions instellen – Het toegangspunt voor aangepast laden

`LoadOptions` is de configuratie‑zak van Aspose.Words die de bibliotheek vertelt *hoe* een document te lezen. Standaard vervangt het stilletjes ontbrekende lettertypen, maar je kunt dat gedrag wijzigen met een warning callback.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Waarom dit belangrijk is:** Zonder `LoadOptions` wordt het document stil geladen, en verlies je zichtbaarheid in ontbrekende lettertypen. Door een instantie te maken krijg je een haak voor het waarschuwingssysteem.

## Stap 2: Een Warning Callback definiëren om *Font Substitution Warnings* vast te leggen

Aspose.Words stuurt waarschuwings‑events via de `IWarningCallback`‑interface. Implementeer deze inline (of als een aparte klasse) en filter op `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Uitleg:**  
- `info.getWarningType()` geeft de categorie van de waarschuwing weer.  
- `WarningType.FONT_SUBSTITUTION` is de enum‑waarde die we nodig hebben.  
- `info.getDescription()` bevat een mens‑leesbare boodschap, bv. *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Door de beschrijving af te drukken, **leg je font substitution warnings** in realtime vast.

## Stap 3: Het document laden met de geconfigureerde LoadOptions

Nu de callback is ingesteld, laad je DOCX. De warning callback wordt automatisch geactiveerd tijdens het parsen.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Vervang `YOUR_DIRECTORY` door het daadwerkelijke pad naar je testbestand. Wanneer de `Document`‑constructor wordt uitgevoerd, triggert elke ontbrekende font de eerder gedefinieerde callback, en zie je de substitutie‑meldingen in de console.

## Stap 4: Het geladen document verifiëren (optioneel maar handig)

Na het laden wil je misschien de integriteit van het document bevestigen—aantal pagina's, tekst‑extractie, enz. Deze stap is niet vereist voor het vastleggen van waarschuwingen, maar helpt je de impact van substituties te zien.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Als een font is vervangen, kan de lay-out iets verschuiven; het controleren van het paginacontrole kan zulke veranderingen aan het licht brengen.

## Stap 5: Geavanceerd – Substituted Fonts programmatically afhandelen

Soms wil je niet alleen de waarschuwing loggen—je moet misschien een fallback‑font insluiten of de styling aanpassen. Hieronder een snel patroon dat je kunt gebruiken.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Door Aspose.Words te wijzen naar een map die de originele lettertypen bevat, kun je *voorkomen* dat substitutie plaatsvindt. Als de map ontbreekt, blijft de warning callback het event vastleggen, zodat je een fallback‑strategie hebt.

## Volledig werkend voorbeeld

Alles bij elkaar, hier is het complete, kant‑klaar programma:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Verwachte console‑output** (wanneer een ontbrekend lettertype wordt aangetroffen):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Als alle lettertypen aanwezig zijn, blijft de callback stil—er wordt niets afgedrukt, wat precies is wat je verwacht.

## Veelvoorkomende valkuilen & Pro‑tips

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|----------|
| **Callback wordt nooit getriggerd** | Je bent vergeten de callback aan `LoadOptions` te koppelen **of** hebt de standaardconstructor van `Document` gebruikt zonder `loadOptions` door te geven. | Roep altijd `loadOptions.setWarningCallback(...)` aan **en** gebruik de overload `new Document(path, loadOptions)`. |
| **Te veel waarschuwingen rommelen de log** | Grote documenten met veel ontbrekende lettertypen genereren een waarschuwing per substitutie. | Filter verder door `info.getDescription()` te controleren op specifieke fontnamen, of verzamel waarschuwingen in een lijst voor latere verwerking. |
| **Substituted fonts beïnvloeden lay-out** | Het fallback‑font kan andere metrische waarden hebben (grootte, spatiëring). | Lever een aangepaste fonts‑map (zie Stap 5) of pas de stijl van het document aan na het laden. |
| **Uitvoeren op een headless server** | De standaard font‑fallback kan afhankelijk zijn van systeemfonts die niet op de server geïnstalleerd zijn. | Lever de benodigde lettertypen mee met je applicatie en wijs `FontSettings` naar die map. |

## Veelgestelde vragen

**Q: Werkt dit ook met PDF of andere formaten?**  
A: Ja. De warning callback is formaat‑agnostisch; hij wordt geactiveerd voor elk documenttype dat Aspose.Words laadt (DOC, DOCX, RTF, HTML, enz.). Het enige verschil is de set waarschuwingen die kunnen verschijnen.

**Q: Kan ik andere waarschuwings‑types vastleggen, zoals *image resolution* warnings?**  
A: Absoluut. Binnen de `warning`‑methode inspecteer je `info.getWarningType()` voor andere enum‑waarden zoals `WarningType.IMAGE_RESOLUTION`. Handel ze vervolgens naar wens af.

**Q: Wat als ik de lijst met vervangen lettertypen nodig heb nadat het document is geladen?**  
A: Sla elke `info.getDescription()` op in een `List<String>` binnen de callback. Na het laden heb je een collectie die je kunt loggen, naar een monitoring‑service kunt sturen, of kunt gebruiken om een font‑downloadroutine te starten.

## Conclusie

Je weet nu **hoe je font substitution warnings** kunt vastleggen in Java met Aspose.Words, waarom elk onderdeel van de puzzel belangrijk is, en hoe je de oplossing kunt uitbreiden voor real‑world scenario's. Door gebruik te maken van `LoadOptions`, een `Aspose.Words warning callback` en optioneel `FontSettings`, krijg je volledige zichtbaarheid in ontbrekende lettertypen en kun je je document‑conversiepijplijnen betrouwbaar houden.

Klaar voor de volgende stap? Probeer `System.out.println` te vervangen door een logger zoals SLF4J, of integreer de waarschuwingslijst in een UI die gebruikers waarschuwt voordat ze een batch‑conversie afronden. Je kunt ook de **Aspose.Words warning callback** verkennen voor andere waarschuwings‑types, zoals *unsupported features* of *high‑resolution image* alerts.  

Happy coding, and may your PDFs never suffer from unexpected font swaps again! 

![Schermafbeelding die console‑output van vastgelegde fontvervangingswaarschuwingen toont](image-placeholder.png "fontvervangingswaarschuwingen vastleggen")


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}