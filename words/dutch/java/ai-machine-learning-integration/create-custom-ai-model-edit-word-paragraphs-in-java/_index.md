---
category: general
date: 2026-03-25
description: Maak een aangepast AI‑model om Word‑documenten te bewerken – leer hoe
  je tekst formeler maakt, alinea‑tekst vervangt en een Word‑alinea herschrijft met
  Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: nl
og_description: Maak een aangepast AI‑model om Word‑documenten te bewerken. Leer hoe
  je tekst formeler maakt, alinea‑tekst vervangt en een Word‑alinea herschrijft met
  Aspose.Words AI.
og_title: Maak een aangepast AI‑model – Bewerk Word‑paragrafen in Java
tags:
- Aspose.Words
- Java
- AI integration
title: Maak een aangepast AI‑model – Bewerk Word‑paragrafen in Java
url: /nl/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aangepast AI‑model maken – Word‑paragrafen bewerken in Java

Heb je ooit een **aangepast AI‑model maken** nodig gehad die een alinea in een Word‑bestand kan verfijnen? Misschien heb je een stapel contracten die allemaal een beetje te informeel klinken, en wil je de tekst formeler maken met één regel code. Het goede nieuws is dat je precies dat kunt doen—geen externe services, geen zware SDK's, alleen Aspose.Words for Java en een OpenAI‑compatible endpoint.

In deze tutorial lopen we stap voor stap door alles wat nodig is om **aangepast AI‑model maken**, het te koppelen aan een lokale LLM‑server, en het vervolgens te gebruiken om *paragraaftekst te vervangen* door een formelere versie. Aan het einde heb je een uitvoerbaar Java‑programma dat **paragraaf bewerken met AI**, een Word‑paragraaf herschrijft, en het resultaat terug opslaat op schijf. Geen poespas, alleen een praktische oplossing die je kunt copy‑paste in je eigen project.

> **Wat je nodig hebt**  
> • Java 17 of nieuwer (de code compileert met eerdere versies, maar 17 is de optimale keuze)  
> • Aspose.Words for Java 23.9 (of de nieuwste release)  
> • Een draaiende OpenAI‑compatible LLM‑server (bijv. Ollama, LocalAI) die luistert op `http://localhost:8000/v1`  
> • Een invoer‑Word‑document (`input.docx`) geplaatst in een map die je beheert  

Als je je afvraagt *waarom een aangepast model bouwen* in plaats van direct OpenAI aan te roepen, is het antwoord flexibiliteit: je beheert het endpoint, je kunt modellen wisselen zonder code‑wijzigingen, en je houdt API‑sleutels buiten je broncode‑repository. Laten we duiken in.

---

## Aangepast AI‑model maken – Installatie en configuratie

Eerst moeten we Aspose.Words vertellen waar onze LLM zich bevindt. De `AiModelEndpoint`‑klasse bevat de URL en een optionele API‑sleutel. Omdat we een lokale server gebruiken, kan de sleutel een lege string zijn, maar de parameter is vereist.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** Als je ooit overschakelt naar een gehost model (bijv. Azure OpenAI), wijzig dan gewoon de URL en sleutel—geen andere code‑wijzigingen nodig.

---

## Word‑document laden

Nu laden we het bronbestand in het geheugen. `Document` kan `.docx`, `.doc`, `.rtf` en vele andere formaten lezen, maar voor dit voorbeeld gebruiken we `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Zorg ervoor dat `YOUR_DIRECTORY` naar een echte map wijst; anders krijg je een `FileNotFoundException`. In een echte applicatie kun je het pad als command‑line‑argument doorgeven of uit een configuratiebestand lezen.

---

## Aangepast AI‑model initialiseren

We maken een `AiModel` van type `CUSTOM` en geven het het endpoint dat we eerder hebben gedefinieerd. Dit vertelt Aspose.Words om alle AI‑aanroepen via onze eigen server te routeren.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Achter de schermen bouwt Aspose.Words een kleine HTTP‑client die met de LLM communiceert via het standaard OpenAI‑chat/completion‑schema. Daarom moet het endpoint *OpenAI‑compatible* zijn.

---

## Eerste alinea ophalen en herschrijven

Hier maken we de tekst daadwerkelijk **formeler**. We pakken de eerste alinea, sturen de ruwe tekst naar het model met een prompt, en ontvangen de bewerkte versie.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Het tweede argument (`"Make it more formal"`) is de instructie die we aan het model geven. Je kunt het vervangen door elke gewenste opdracht—**replace paragraph text**, **summarize**, **translate**, enz. De methode retourneert een gewone string, die we later terug in het document zullen invoegen.

> **Waarom dit werkt:** `editText` stuurt een JSON‑payload zoals `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. De LLM ziet de originele alinea en de instructie, en beantwoordt met de aangepaste tekst.

---

## Originele alinea‑inhoud vervangen

Nu **replace paragraph text** binnen het Word‑objectmodel. We wissen alle bestaande runs (de laag‑niveau tekstonderdelen) en voegen een nieuwe `Run` toe die de AI‑gegenereerde string bevat.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Wees voorzichtig om niet `firstParagraph.setText()` aan te roepen—die methode zou alle opmaak verwijderen. Het gebruik van `Run` behoudt de stijl van de alinea (kop, opsomming, enz.) terwijl de daadwerkelijke tekens worden vervangen.

---

## Bewerkte document opslaan

Tot slot schrijven we het aangepaste document terug naar schijf. Je kunt het originele bestand overschrijven of, zoals hier, een nieuwe kopie maken.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Wanneer je `output.docx` opent, zou de eerste alinea nu aanzienlijk formeler moeten klinken. Als de LLM de instructie niet perfect heeft opgevolgd, kun je de prompt aanpassen of een andere modelversie proberen.

---

## Volledig werkend voorbeeld

Hieronder staat het volledige programma—kopieer het naar `LlmDemo.java`, pas de paden aan, en voer het uit met `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Verwachte output:** Open `output.docx` en je ziet de originele alinea getransformeerd. Bijvoorbeeld, een informele zin als “We’ll get the thing done soon.” kan worden “We shall complete the task promptly.” De exacte formulering hangt af van het model dat je gebruikt.

---

## Veelgestelde vragen & randgevallen

### Wat als mijn document meerdere secties heeft?

De bovenstaande code wijzigt alleen de *eerste* alinea van de *eerste* sectie. Om **paragraaf bewerken met AI** over het hele bestand toe te passen, loop je door `document.getSections()` en vervolgens door elke `section.getBody().getParagraphs()`. Vergeet niet lege alinea's over te slaan, anders ontvangt de LLM een lege string en geeft niets terug.

### Hoe ga ik om met grote alinea's die de token‑limiet overschrijden?

De meeste LLM's beperken de invoer tot ongeveer 4 000 tokens. Als een alinea uitzonderlijk lang is, splits deze dan in kleinere stukken voordat je `editText` aanroept. Je kunt dezelfde `AiModel`‑instantie hergebruiken; houd alleen rekening met de snelheidslimieten van je lokale server.

### Kan ik een andere instructie gebruiken, zoals “summarize” of “translate to French”?

Zeker. Het tweede argument van `editText` is vrij te formuleren. Voor een samenvatting kun je bijvoorbeeld `"Summarize in one sentence"` doorgeven. Voor vertaling werkt `"Translate to French, keep the tone formal"` even goed. Deze flexibiliteit stelt je in staat om **replace paragraph text** voor vele scenario's te gebruiken zonder code te wijzigen.

### Behoudt het model de alinea‑opmaak (lettertypen, kleuren)?

Omdat we alleen de `Run` binnen hetzelfde `Paragraph`‑object vervangen, blijven bestaande stijlen (kopniveau, opsomming, inspringen) behouden. Als je de stijl zelf wilt wijzigen, kun je `Paragraph.getParagraphFormat()` aanpassen na de vervanging.

### Wat als mijn LLM‑server HTTPS vereist met een zelf‑ondertekend certificaat?

`AiModelEndpoint` accepteert een URL met `https://`. Als het certificaat niet vertrouwd wordt, moet je de SSL‑context van Java configureren om het te vertrouwen, of de server draaien met een geldig certificaat. Die configuratie valt buiten de scope van deze tutorial maar is goed gedocumenteerd in de Java‑SSL‑handleidingen.

---

## Tips voor productie‑klare integratie

| Tip | Waarom het belangrijk is |
|-----|--------------------------|
| **Cache het endpoint** | Het opnieuw aanmaken van `AiModelEndpoint` bij elk verzoek voegt overhead toe. |
| **Batchbewerkingen** | Als je veel alinea's hebt, stuur ze in één verzoek (bijv. JSON‑array) om de latentie te verminderen. |
| **LLM‑output valideren** | Controleer altijd de geretourneerde string op null of lege waarden voordat je deze invoegt. |
| **Log prompts en antwoorden** | Handig voor debugging en voor compliance wanneer je juridische tekst herschrijft. |
| **Graceful fallback** | Als de LLM offline is, val dan terug op de originele alinea of een eenvoudige heuristische herschrijving. |

---

## Conclusie

We hebben je laten zien hoe je **aangepast AI‑model maken** met Aspose.Words, het verbindt met een OpenAI‑compatible endpoint, en vervolgens **paragraaf bewerken met AI** om **tekst formeler te maken**. Door de zes stappen te volgen—definieer het endpoint, laad het document, initialiseert het model,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}