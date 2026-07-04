---
category: general
date: 2026-05-04
description: Skapa Word‑dokument i Java med Aspose.Words och lär dig hur du kontrollerar
  grammatik med en anpassad LLM. Steg‑för‑steg‑guide för Java‑utvecklare.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: sv
og_description: Skapa Word-dokument i Java och se hur du kontrollerar grammatik med
  en anpassad LLM. Komplett Java-handledning med körbar kod.
og_title: Skapa Word‑dokument i Java med anpassad LLM‑grammatikgranskning
tags:
- Java
- Aspose.Words
- LLM
title: Skapa Word-dokument i Java med anpassad LLM-grammatikgranskning
url: /sv/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa word document java med anpassad LLM grammatikgranskning

Har du någonsin undrat hur man **create word document java** projekt som också korrekturläser sig själva? Du är inte ensam—många utvecklare vill ha en enda pipeline som genererar en polerad *.docx*‑fil utan att jonglera med flera verktyg. I den här handledningen går vi igenom exakt det, och visar dig **how to create docx**‑filer med Aspose.Words, ansluter en lokalt hostad LLM, och slutligen **how to check grammar** automatiskt. I slutet har du ett självständigt Java‑program som skriver, validerar och sparar ett Word‑dokument—allt medan du **using custom LLM**‑endpoints du kontrollerar.

## Vad du behöver

Innan vi dyker ner, se till att du har följande på din arbetsstation:

| Förutsättning | Varför det är viktigt |
|--------------|----------------|
| Java 17+ (or any recent JDK) | Moderna språkfunktioner och bättre modulstöd |
| Aspose.Words for Java (latest version) | Biblioteket som låter dig **create word document java** filer programatiskt |
| A locally hosted LLM server (e.g., Ollama, LMStudio) listening on `http://localhost:11434/api/generate` | Krävs för **use custom llm**‑steget som driver grammatikgranskning |
| Maven or Gradle (we’ll use Maven in examples) | Förenklar beroendehantering |
| An IDE or text editor (IntelliJ IDEA, VS Code, etc.) | Gör kodning och felsökning enklare |

Om någon av dessa låter obekanta, panik inte—varje komponent är gratis eller har en community‑edition som fungerar utmärkt för lärande.

## Steg 1 – Ställ in ditt Maven‑projekt

För att snabbt **create word document java** projekt, börja med en minimal Maven `pom.xml`. Denna fil hämtar Aspose.Words‑biblioteket och vilken HTTP‑klient du föredrar (vi använder Apache HttpClient).

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

> **Pro tip:** Om du använder Gradle, placeras samma beroenden under `implementation` i `build.gradle`.

Kör nu `mvn clean install` för att hämta jar‑filerna. När bygget lyckas är du redo att skriva Java‑kod som **creates word document java** filer.

## Steg 2 – Skriv Java‑klassen som **Creates word document java**

Nedan är den fullständiga, körklara källkoden. Den demonstrerar hela flödet: initiera ett tomt dokument, konfigurera en anpassad LLM‑endpoint, anropa grammatikgranskning och slutligen spara resultatet.

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

> **Why this works:**  
> * `Document` är den centrala Aspose.Words‑klassen som representerar en *.docx* i minnet.  
> * `AiEndpoint` talar om för Aspose:s AI‑modul var prompten ska skickas. Genom att peka på `localhost:11434` **use custom llm** istället för en molntjänst.  
> * `checkGrammar` med `AiModelType.CUSTOM` vidarebefordrar dokumentets text till LLM, mottar korrigerad text och skriver om de underliggande Word‑noderna.  
> * Slutligen anropar vi `save` för att skriva filen till disk, vilket ger dig ett polerat Word‑dokument.

### Förväntad utdata

Efter att ha kört `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` bör du se:

```
Document saved to output/GrammarChecked.docx
```

Öppna den resulterande `GrammarChecked.docx` i Microsoft Word (eller LibreOffice). Den ursprungliga meningen *“Ths sentence has a typo and a grammer error.”* kommer nu att vara *“This sentence has a typo and a grammar error.”* – ett bevis på att **how to check grammar**‑steget lyckades.

## Steg 3 – Hur man skapar docx med olika innehåll (Valfritt)

Om du vill generera rikare dokument—tabeller, bilder eller formaterad text—fortsätt bara använda `DocumentBuilder`. Här är ett snabbt kodexempel som demonstrerar hur man lägger till en rubrik och en tabell:

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

Du kan placera denna kod var som helst mellan dokument‑skapande‑blocket (Steg 2.1) och grammatik‑kontroll‑anropet (Steg 2.3). LLM kommer fortfarande att få hela texten, så den kan korrigera alla naturliga språkdelar medan tabeller lämnas orörda.

## Steg 4 – Hantera endpoint‑problem (Använd Custom LLM säkert)

När **using custom llm**‑endpoints, är några problem vanliga:

| Symptom | Trolig orsak | Lösning |
|---------|--------------|-----|
| `Connection refused` error | LLM‑servern kör inte eller fel port | Starta Ollama (`ollama serve`) och verifiera att `http://localhost:11434/api/generate` fungerar med `curl`. |
| Response JSON missing `completion` field | Modellnamn stämmer inte | Säkerställ att modellen du angav (`llama3.1:8b`) är installerad (`ollama list`). |
| Grammar check returns the original text unchanged | Prompten känns inte igen av LLM | Justera modellens system |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}