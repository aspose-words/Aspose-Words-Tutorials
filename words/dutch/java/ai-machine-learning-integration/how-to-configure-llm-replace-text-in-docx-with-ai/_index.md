---
category: general
date: 2026-03-04
description: Hoe LLM te configureren voor Document AI en tekst in DOCX te vervangen
  met AI – stapsgewijze handleiding met volledige Java‑code.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: nl
og_description: Hoe configureer je een LLM voor Document AI en vervang je tekst in
  DOCX met AI – volledige gids met uitvoerbare Java-code.
og_title: Hoe LLM te configureren – Tekst in DOCX vervangen met AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /nl/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe LLM te configureren – Tekst in DOCX vervangen met AI

Heb je je ooit afgevraagd **hoe je LLM moet configureren** zodat het een Word‑bestand voor je kan bewerken? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur aan wanneer ze programmatic een zin in een `.docx` moeten vervangen zonder Microsoft Word te openen. Het goede nieuws? Met een lokale LLM en een kleine Document AI‑wrapper kun je tekst in een DOCX‑bestand vervangen in slechts een paar regels Java.

In deze tutorial lopen we het volledige proces door: van het opzetten van de LLM‑verbinding, het laden van een DOCX, tot het gebruiken van **Document AI** om een doelzin te vervangen. Aan het einde heb je een zelfstandige, uitvoerbare voorbeeldcode die je in elk Maven‑ of Gradle‑project kunt plaatsen. Geen externe API‑sleutels, geen cloudkosten — alleen je eigen model dat luistert op `http://localhost:8080/v1`.

> **Snelle winst:** Als je al een lokale LLM hebt (zoals Llama 3 of Mistral) die een OpenAI‑compatibel eindpunt aanbiedt, werkt de onderstaande code direct uit de doos.

---

![Diagram van hoe LLM te configureren voor Document AI](/images/configure-llm-diagram.png){: .center-image alt="diagram hoe LLM te configureren"}

## Wat je nodig hebt

- **Java 17** (of een recente JDK)  
- Een **lokale LLM** die een OpenAI‑stijl `/v1`‑endpoint aanbiedt (bijv. Ollama, LMStudio)  
- De **Document AI Java‑bibliotheek** (stel `com.example:document-ai:1.2.0` op Maven Central)  
- Een voorbeeld‑DOCX‑bestand (`input.docx`) in een bekende map  

Als je iets hiervan mist, start dan snel Ollama:

```bash
ollama serve &
ollama run llama3
```

Dat start een server op `http://localhost:8080/v1` die klaar is om verzoeken te ontvangen.

---

## Hoe LLM te configureren voor Document AI

Het eerste wat we doen is de `DocumentAi`‑client vertellen waar het model te vinden is en welk model te gebruiken. Dit is de **hoe LLM te configureren**‑stap die veel tutorials overslaan.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Waarom dit belangrijk is:*  
Het `AiModelConfig`‑object verbergt de HTTP‑details, zodat `DocumentAi` zich kan richten op de inhoud. Als je ooit overstapt naar een gehoste provider, wijzig je alleen de `baseUrl` en `apiKey` — de rest van je code blijft ongewijzigd.

---

## Het DOCX‑document laden en voorbereiden

Vervolgens laden we het Word‑bestand in het geheugen. De `Document`‑klasse behandelt zowel `.docx` als `.pdf` onder de motorkap, maar hier gaat het alleen om DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Pro‑tip:* Gebruik een absoluut pad tijdens het debuggen om de “bestand niet gevonden”‑verrassing te vermijden. Zodra je zeker bent, schakel je terug naar een relatief pad voor draagbaarheid.

---

## Tekst in DOCX vervangen met AI

Nu volgt het hart van de tutorial — **hoe tekst te vervangen** in een DOCX‑bestand met AI‑ondersteuning. De `replaceText`‑methode stuurt de documentinhoud naar de LLM, vraagt om de substitutie en geeft de aangepaste tekst terug.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Wat er achter de schermen gebeurt:*  
`DocumentAi` serialiseert de DOCX naar platte tekst, bouwt een prompt zoals:

> “In het volgende document, vervang elke keer dat ‘oude zin’ voorkomt door ‘nieuwe zin’ en retourneer alleen de bijgewerkte tekst.”

De LLM verwerkt het verzoek en stuurt de gewijzigde inhoud terug. Deze aanpak werkt zelfs wanneer de zin zich over meerdere runs of alinea’s uitstrekt — iets wat eenvoudige tekenreeksvervanging vaak mist.

---

## Verifiëren en de aangepaste tekst weergeven

Tot slot printen we de AI‑aangepaste tekst naar de console. In een echte applicatie zou je het resultaat waarschijnlijk terugschrijven naar een nieuw DOCX‑bestand, maar printen laat je snel verifiëren.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Verwachte output** (ervan uitgaande dat het originele DOCX‑bestand de zin “This is the old phrase we want to change.” bevatte):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Als je de nieuwe zin ziet verschijnen, gefeliciteerd — **je hebt net geleerd hoe je Document AI kunt gebruiken om een zin met AI te vervangen**.

---

## Volledig werkend voorbeeld

Alles samengevoegd, hier is een complete, kant‑en‑klaar uitvoerbare Java‑klasse. Kopieer‑en‑plak hem gerust naar `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Hoe uit te voeren

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Zorg ervoor dat de LLM‑server draait voordat je het programma start; anders krijg je een time‑out bij de verbinding.

---

## Randgevallen & Veelvoorkomende valkuilen

| Situatie | Waar op te letten | Aanbevolen oplossing |
|----------|-------------------|----------------------|
| **Zin niet gevonden** | De LLM retourneert de originele tekst ongewijzigd. | Controleer spelling en hoofdlettergevoeligheid; je kunt `ignoreCase:true` aan de prompt toevoegen als je wrapper dat ondersteunt. |
| **Grote documenten (>5 MB)** | Prompt‑grootte kan de token‑limiet van het model overschrijden. | Splits de DOCX in secties, verwerk elke afzonderlijk, en concateneer daarna de resultaten. |
| **Lokale LLM geeft fouten** | Vaak veroorzaakt door een onjuiste modelnaam. | Controleer of de modelnaam in de LLM‑UI (`ollama list`) overeenkomt met `modelConfig.setModelName`. |
| **Unicode‑tekens worden vervormd** | Coderingproblemen bij het lezen van de DOCX. | Zorg dat je Java‑runtime UTF‑8 gebruikt (voeg `-Dfile.encoding=UTF-8` toe aan de JVM‑argumenten). |

---

## Volgende stappen

Nu je **weet hoe je tekst in DOCX kunt vervangen met AI**, kun je verder verkennen:

- **Hoe Document AI te gebruiken** voor complexere taken zoals tabel‑extractie of stijlbehoud.  
- **Zin vervangen met AI** in PDF’s door het argument van de `Document`‑constructor te wijzigen.  
- **Batch‑verwerking**: doorloop een map met DOCX‑bestanden en pas dezelfde vervanging toe.  

Al deze scenario’s bouwen voort op dezelfde `AiModelConfig`‑ en `DocumentAi`‑basis, zodat je niet opnieuw hoeft te beginnen.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}