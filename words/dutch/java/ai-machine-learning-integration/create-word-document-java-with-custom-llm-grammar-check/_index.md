---
category: general
date: 2026-05-04
description: Maak een Word‑document in Java met Aspose.Words en leer hoe je grammatica
  kunt controleren met een aangepaste LLM. Stapsgewijze gids voor Java‑ontwikkelaars.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: nl
og_description: Maak een Word‑document in Java en zie hoe je grammatica kunt controleren
  met een aangepaste LLM. Complete Java‑tutorial met uitvoerbare code.
og_title: Maak een Word-document in Java met aangepaste LLM-grammaticacontrole
tags:
- Java
- Aspose.Words
- LLM
title: Maak Word‑document Java met aangepaste LLM‑grammatica‑controle
url: /nl/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document Java met Aangepaste LLM-grammatica Controle

Heb je je ooit afgevraagd hoe je **maak Word-document Java** projecten kunt maken die zichzelf ook proeflezen? Je bent niet alleen—veel ontwikkelaars willen een enkele pijplijn die een gepolijste *.docx*‑file oplevert zonder meerdere tools te jongleren. In deze tutorial lopen we precies dat stap voor stap door, en laten we je zien **hoe je docx maakt** met Aspose.Words, een lokaal gehoste LLM koppelt, en uiteindelijk **hoe je grammatica controleert** automatisch. Aan het einde heb je een zelfstandige Java‑programma dat een Word‑document schrijft, valideert en opslaat—terwijl je **aangepaste LLM**‑eindpunten gebruikt die je zelf beheert.

## Wat je nodig hebt

| Voorwaarde | Waarom het belangrijk is |
|------------|--------------------------|
| Java 17+ (of een recente JDK) | Moderne taalfeatures en betere module‑ondersteuning |
| Aspose.Words for Java (latest version) | De bibliotheek die je in staat stelt **Word-document Java**‑bestanden programmatisch te maken |
| Een lokaal gehoste LLM‑server (bijv. Ollama, LMStudio) die luistert op `http://localhost:11434/api/generate` | Vereist voor de **aangepaste LLM gebruiken** stap die grammatica‑controle mogelijk maakt |
| Maven of Gradle (we gebruiken Maven in de voorbeelden) | Vereenvoudigt afhankelijkheidsbeheer |
| Een IDE of teksteditor (IntelliJ IDEA, VS Code, enz.) | Maakt coderen en debuggen makkelijker |

Als een van deze je onbekend voorkomt, geen paniek—elk item is gratis of heeft een community‑editie die perfect werkt voor leerdoeleinden.

## Stap 1 – Zet je Maven‑project op

Om snel **Word-document Java** projecten te maken, begin je met een minimale Maven `pom.xml`. Dit bestand haalt de Aspose.Words‑bibliotheek en elke HTTP‑client die je verkiest binnen (we gebruiken Apache HttpClient).

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

**Pro tip:** Als je Gradle gebruikt, komen dezelfde afhankelijkheden onder `implementation` in `build.gradle`.

Voer nu `mvn clean install` uit om de jars op te halen. Zodra de build slaagt, ben je klaar om Java‑code te schrijven die **Word-document Java**‑bestanden maakt.

## Stap 2 – Schrijf de Java‑klasse die **Word-document Java** maakt

Hieronder staat het volledige, kant‑klaar te draaien bronbestand. Het demonstreert de volledige stroom: een leeg document initialiseren, een aangepast LLM‑eindpunt configureren, grammatica‑controle aanroepen, en uiteindelijk het resultaat opslaan.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Waarom dit werkt:**  
* `Document` is de kernklasse van Aspose.Words die een *.docx* in het geheugen representeert.  
* `AiEndpoint` vertelt de AI‑module van Aspose waar de prompt naartoe moet. Door het te wijzen op `localhost:11434` **gebruiken we aangepaste LLM** in plaats van een cloudservice.  
* `checkGrammar` met `AiModelType.CUSTOM` stuurt de tekst van het document naar de LLM, ontvangt gecorrigeerde tekst, en herschrijft de onderliggende Word‑nodes.  
* Ten slotte roepen we `save` aan om het bestand naar schijf te schrijven, waardoor je een gepolijst Word‑bestand krijgt.

### Verwachte Output

Na het uitvoeren van `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` zou je moeten zien:

```
Document saved to output/GrammarChecked.docx
```

Open het resulterende `GrammarChecked.docx` in Microsoft Word (of LibreOffice). De oorspronkelijke zin *“Ths sentence has a typo and a grammer error.”* zal nu lezen *“This sentence has a typo and a grammar error.”* – bewijs dat de **hoe je grammatica controleert** stap geslaagd is.

## Stap 3 – Hoe je docx maakt met verschillende inhoud (optioneel)

Als je rijkere documenten wilt genereren—tabellen, afbeeldingen of opgemaakte tekst—blijf dan `DocumentBuilder` gebruiken. Hier is een kort fragment dat laat zien hoe je een koptekst en een tabel toevoegt:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

Je kunt deze code overal tussen het document‑creatieblok (Stap 2.1) en de grammatica‑controle‑aanroep (Stap 2.3) plaatsen. De LLM ontvangt nog steeds de volledige tekst, zodat hij elk natuurlijk‑taaldeel kan corrigeren terwijl tabellen onaangeroerd blijven.

## Stap 4 – Omgaan met eindpunt‑problemen (Aangepaste LLM veilig gebruiken)

Wanneer **aangepaste LLM gebruiken** eindpunten, komen een paar veelvoorkomende haperingen voor:

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| `Connection refused` fout | LLM‑server draait niet of verkeerde poort | Start Ollama (`ollama serve`) en controleer dat `http://localhost:11434/api/generate` werkt met `curl`. |
| Response‑JSON mist `completion`‑veld | Modelnaam komt niet overeen | Zorg ervoor dat het model dat je instelt (`llama3.1:8b`) geïnstalleerd is (`ollama list`). |
| Grammatica‑controle retourneert de originele tekst ongewijzigd | Prompt niet herkend door LLM | Pas het systeem van het model aan |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}