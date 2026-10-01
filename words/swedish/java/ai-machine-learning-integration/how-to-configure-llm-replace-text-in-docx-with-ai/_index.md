---
category: general
date: 2026-03-04
description: Hur man konfigurerar LLM för Document AI och ersätter text i DOCX med
  AI – steg‑för‑steg‑guide med fullständig Java‑kod.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: sv
og_description: How to configure LLM for Document AI and replace text in DOCX using
  AI – complete guide with runnable Java code.
og_title: Hur man konfigurerar LLM – Ersätt text i DOCX med AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: Hur man konfigurerar LLM – Ersätt text i DOCX med AI
url: /sv/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man konfigurerar LLM – Ersätt text i DOCX med AI

Har du någonsin undrat **hur man konfigurerar LLM** så att den kan redigera en Word‑fil åt dig? Du är inte ensam. Många utvecklare stöter på problem när de behöver programatiskt ersätta en fras i en `.docx` utan att öppna Microsoft Word. Den goda nyheten? Med en lokal LLM och ett litet Document AI‑omslag kan du byta ut text i en DOCX‑fil med bara några rader Java.

I den här handledningen går vi igenom hela processen: från att koppla upp LLM‑anslutningen, läsa in en DOCX, till att använda **Document AI** för att ersätta en målfras. När du är klar har du ett självständigt, körbart exempel som du kan slänga in i vilket Maven‑ eller Gradle‑projekt som helst. Inga externa API‑nycklar, inga molnavgifter – bara din egen modell som lyssnar på `http://localhost:8080/v1`.

> **Snabb vinst:** Om du redan har en lokal LLM (som Llama 3 eller Mistral) som exponerar en OpenAI‑kompatibel endpoint, fungerar koden nedan direkt ur lådan.

---

![Diagram över hur man konfigurerar LLM för Document AI](/images/configure-llm-diagram.png){: .center-image alt="hur man konfigurerar llm diagram"}

## Vad du behöver

- **Java 17** (eller någon nyare JDK)  
- En **local LLM** som exponerar en OpenAI‑stil `/v1`‑endpoint (t.ex. Ollama, LMStudio)  
- Det **Document AI Java‑biblioteket** (anta `com.example:document-ai:1.2.0` på Maven Central)  
- En exempel‑DOCX‑fil (`input.docx`) placerad i en känd mapp  

Om du saknar någon av dessa, starta snabbt Ollama:

```bash
ollama serve &
ollama run llama3
```

Det kommer att starta en server på `http://localhost:8080/v1` redo att ta emot förfrågningar.

---

## Så konfigurerar du LLM för Document AI

Det första vi gör är att tala om för `DocumentAi`‑klienten var modellen finns och vilken modell som ska användas. Detta är steget **hur man konfigurerar LLM** som många handledningar förbiser.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Varför detta är viktigt:*  
`AiModelConfig`‑objektet abstraherar bort HTTP‑detaljerna, så att `DocumentAi` kan fokusera på innehållet. Om du någonsin byter till en hostad leverantör ändrar du bara `baseUrl` och `apiKey` – resten av koden förblir oförändrad.

---

## Läs in och förbered DOCX‑dokumentet

Nästa steg är att läsa in Word‑filen i minnet. `Document`‑klassen hanterar både `.docx` och `.pdf` under huven, men här bryr vi oss bara om DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Proffstips:* Använd en absolut sökväg under felsökning för att undvika överraskningen “filen hittades inte”. När du är säker, byt tillbaka till en relativ sökväg för portabilitet.

---

## Ersätt text i DOCX med AI

Nu kommer hjärtat i handledningen – **hur man ersätter text** i en DOCX‑fil med AI‑hjälp. `replaceText`‑metoden skickar dokumentets innehåll till LLM, ber den utföra substitutionen och returnerar den reviderade texten.

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

*Vad händer bakom kulisserna?*  
`DocumentAi` serialiserar DOCX‑filen till ren text, bygger en prompt som:

> “I följande dokument, ersätt varje förekomst av ‘old phrase’ med ‘new phrase’ och returnera endast den uppdaterade texten.”

LLM bearbetar förfrågan och skickar tillbaka det modifierade innehållet. Detta tillvägagångssätt fungerar även när frasen sträcker sig över flera runs eller stycken – något som vanlig strängersättning ofta missar.

---

## Verifiera och skriv ut den reviderade texten

Till sist skriver vi ut den AI‑reviderade texten till konsolen. I en verklig applikation skulle du troligen skriva resultatet tillbaka till en ny DOCX, men utskrift låter dig snabbt verifiera.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Förväntad utskrift** (förutsatt att den ursprungliga DOCX‑filen innehöll “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Om du ser den nya frasen dyka upp, grattis – **du har just lärt dig hur man använder Document AI för att ersätta en fras med AI**.

---

## Fullt fungerande exempel

När vi sätter ihop allt får du en komplett, klar‑att‑köra Java‑klass. Känn dig fri att kopiera‑klistra in i `src/main/java/com/example/ReplaceInDocx.java`.

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

### Så kör du

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Se till att LLM‑servern är igång innan du kör programmet; annars får du ett anslutningstidsgräns‑fel.

---

## Edge Cases & Vanliga fallgropar

| Situation | Vad du bör hålla utkik efter | Föreslagen lösning |
|-----------|------------------------------|--------------------|
| **Phrase not found** | LLM returnerar den ursprungliga texten oförändrad. | Dubbelkolla stavning och skiftlägeskänslighet; du kan lägga till `ignoreCase:true` i prompten om ditt omslag stödjer det. |
| **Large documents (>5 MB)** | Promptens storlek kan överskrida modellens token‑gräns. | Dela upp DOCX‑filen i sektioner, bearbeta varje separat och slå sedan ihop resultaten. |
| **Local LLM returns errors** | Ofta orsakat av fel modellnamn. | Verifiera att modellnamnet i LLM‑gränssnittet (`ollama list`) matchar `modelConfig.setModelName`. |
| **Unicode characters get garbled** | Kodningsproblem när DOCX läses. | Säkerställ att din Java‑runtime använder UTF‑8 (lägg till `-Dfile.encoding=UTF-8` i JVM‑argumenten). |

---

## Nästa steg

Nu när du vet **hur man ersätter text i DOCX** med AI, kanske du vill utforska:

- **How to use Document AI** för mer komplexa uppgifter som tabellutdrag eller stilbevarande.  
- **Replace phrase with AI** i PDF‑filer genom att byta argumentet i `Document`‑konstruktorn.  
- **Batch processing**: loopa över en katalog med DOCX‑filer och applicera samma ersättning.  

Var och en av dessa bygger på samma `AiModelConfig` och `DocumentAi`‑grund, så du behöver inte börja från början

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}