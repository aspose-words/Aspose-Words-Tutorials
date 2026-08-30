---
category: general
date: 2026-05-04
description: Vytvořte Word dokument v Javě pomocí Aspose.Words a naučte se, jak kontrolovat
  gramatiku pomocí vlastního LLM. Průvodce krok za krokem pro vývojáře Javy.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: cs
og_description: Vytvořte Word dokument v Javě a zjistěte, jak kontrolovat gramatiku
  pomocí vlastního LLM. Kompletní Java tutoriál se spustitelným kódem.
og_title: Vytvořte Word dokument v Javě s vlastní kontrolou gramatiky LLM
tags:
- Java
- Aspose.Words
- LLM
title: Vytvořit Word dokument v Javě s vlastním LLM kontrolou gramatiky
url: /cs/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte word document java s vlastním LLM kontrolou gramatiky

Už jste se někdy zamýšleli, jak **create word document java** projekty, které se zároveň samy kontrolují? Nejste sami — mnoho vývojářů chce jediné řešení, které vygeneruje upravený *.docx* soubor bez nutnosti přepínat mezi několika nástroji. V tomto tutoriálu vás provedeme přesně tímto procesem, ukážeme vám **how to create docx** soubory pomocí Aspose.Words, připojíme lokálně hostovaný LLM a nakonec **how to check grammar** automaticky. Na konci budete mít samostatný Java program, který zapisuje, ověřuje a ukládá Word dokument — a to vše při **using custom LLM** endpointů, které ovládáte.

## Co budete potřebovat

Než se pustíme dál, ujistěte se, že máte na svém počítači následující:

| Požadavek | Proč je důležité |
|--------------|----------------|
| Java 17+ (or any recent JDK) | Moderní jazykové funkce a lepší podpora modulů |
| Aspose.Words for Java (latest version) | Knihovna, která vám umožní **create word document java** soubory programově |
| A locally hosted LLM server (e.g., Ollama, LMStudio) listening on `http://localhost:11434/api/generate` | Vyžadováno pro krok **use custom llm**, který napájí kontrolu gramatiky |
| Maven or Gradle (we’ll use Maven in examples) | Zjednodušuje správu závislostí |
| An IDE or text editor (IntelliJ IDEA, VS Code, etc.) | Usnadňuje psaní kódu a ladění |

Pokud některá z těchto položek neznáte, nepanikařte — každá z nich je zdarma nebo má komunitní edici, která je pro výukové účely naprosto dostačující.

## Krok 1 – Nastavte svůj Maven projekt

Pro rychlé vytvoření **create word document java** projektů začněte s minimálním Maven `pom.xml`. Tento soubor načte knihovnu Aspose.Words a libovolného HTTP klienta, který preferujete (použijeme Apache HttpClient).

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

> **Tip:** Pokud používáte Gradle, stejné závislosti patří pod `implementation` v `build.gradle`.

Nyní spusťte `mvn clean install`, aby se stáhly jar soubory. Jakmile sestavení uspěje, můžete psát Java kód, který **creates word document java** soubory.

## Krok 2 – Napište Java třídu, která **Creates word document java**

Níže je kompletní, připravený ke spuštění zdrojový soubor. Ukazuje celý tok: inicializuje prázdný dokument, nakonfiguruje vlastní LLM endpoint, spustí kontrolu gramatiky a nakonec výsledek uloží.

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

> **Proč to funguje:**  
> * `Document` je hlavní třída Aspose.Words, která představuje *.docx* v paměti.  
> * `AiEndpoint` říká AI modulu Aspose, kam má odeslat prompt. Když ho nasměrujeme na `localhost:11434`, **use custom llm** místo cloudové služby.  
> * `checkGrammar` s `AiModelType.CUSTOM` předá text dokumentu LLM, získá opravený text a přepíše podkladové Word uzly.  
> * Nakonec zavoláme `save`, aby se soubor zapsal na disk, a získáte upravený Word soubor.

### Očekávaný výstup

Po spuštění `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` byste měli vidět:

```
Document saved to output/GrammarChecked.docx
```

Otevřete vzniklý `GrammarChecked.docx` v Microsoft Word (nebo LibreOffice). Původní věta *„Ths sentence has a typo and a grammer error.“* bude nyní *„This sentence has a typo and a grammar error.“* — důkaz, že krok **how to check grammar** byl úspěšný.

## Krok 3 – Jak vytvořit docx s různým obsahem (volitelné)

Pokud chcete generovat bohatší dokumenty — tabulky, obrázky nebo stylovaný text — stačí nadále používat `DocumentBuilder`. Zde je rychlý úryvek, který ukazuje přidání nadpisu a tabulky:

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

Tento kód můžete vložit kdekoliv mezi blokem vytváření dokumentu (Krok 2.1) a voláním kontroly gramatiky (Krok 2.3). LLM stále obdrží celý text, takže může opravit jakékoli části v přirozeném jazyce, zatímco tabulky zůstane nedotčeny.

## Krok 4 – Řešení problémů s endpointy (bezpečné používání Custom LLM)

Při **using custom llm** endpointů se často vyskytují následující potíže:

| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| `Connection refused` error | LLM server neběží nebo špatný port | Spusťte Ollama (`ollama serve`) a ověřte, že `http://localhost:11434/api/generate` funguje pomocí `curl`. |
| Response JSON missing `completion` field | Neshoda názvu modelu | Ujistěte se, že nastavený model (`llama3.1:8b`) je nainstalován (`ollama list`). |
| Grammar check returns the original text unchanged | Prompt not recognized by LLM | Adjust the model’s system |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}