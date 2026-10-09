---
category: general
date: 2026-03-04
description: Come configurare LLM per Document AI e sostituire il testo in DOCX usando
  l'IA – guida passo‑passo con codice Java completo.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: it
og_description: Come configurare LLM per Document AI e sostituire il testo in DOCX
  usando l'IA – guida completa con codice Java eseguibile.
og_title: How to Configure LLM – Replace Text in DOCX with AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: Come configurare LLM – Sostituire il testo in DOCX con l'IA
url: /it/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come Configurare LLM – Sostituire Testo in DOCX con AI

Ti sei mai chiesto **come configurare LLM** in modo che possa modificare un file Word per te? Non sei il solo. Molti sviluppatori si trovano in difficoltà quando devono sostituire programmaticamente una frase all'interno di un `.docx` senza aprire Microsoft Word. La buona notizia? Con un LLM locale e un piccolo wrapper Document AI, puoi scambiare il testo in un file DOCX in poche righe di Java.

In questo tutorial percorreremo l’intero processo: dalla configurazione della connessione LLM, al caricamento di un DOCX, fino all’uso di **Document AI** per sostituire una frase target. Alla fine avrai un esempio autonomo, eseguibile, che potrai inserire in qualsiasi progetto Maven o Gradle. Nessuna chiave API esterna, nessuna tariffa cloud—solo il tuo modello che ascolta su `http://localhost:8080/v1`.

> **Vantaggio rapido:** Se hai già un LLM locale (come Llama 3 o Mistral) che espone un endpoint compatibile OpenAI, il codice qui sotto funziona subito.

---

![Diagramma di come configurare LLM per Document AI](/images/configure-llm-diagram.png){: .center-image alt="diagramma di come configurare llm"}

## Cosa Ti Serve

- **Java 17** (o qualsiasi JDK recente)  
- Un **local LLM** che espone un endpoint in stile OpenAI `/v1` (es. Ollama, LMStudio)  
- La **Document AI Java library** (presumibilmente `com.example:document-ai:1.2.0` su Maven Central)  
- Un file DOCX di esempio (`input.docx`) collocato in una cartella nota  

Se ti manca qualcuno di questi, avvia rapidamente Ollama:

```bash
ollama serve &
ollama run llama3
```

Questo avvierà un server su `http://localhost:8080/v1` pronto a ricevere richieste.

---

## Come Configurare LLM per Document AI

La prima cosa che facciamo è indicare al client `DocumentAi` dove trovare il modello e quale modello utilizzare. Questo è il passaggio **come configurare LLM** che molti tutorial trascurano.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Perché è importante:*  
L'oggetto `AiModelConfig` astrae i dettagli HTTP, permettendo a `DocumentAi` di concentrarsi sul contenuto. Se mai dovessi passare a un provider hosted, devi solo modificare `baseUrl` e `apiKey`—il resto del tuo codice rimane invariato.

---

## Caricare e Preparare il Documento DOCX

Ora carichiamo il file Word in memoria. La classe `Document` gestisce sia `.docx` che `.pdf` internamente, ma qui ci interessa solo DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Consiglio:* Usa un percorso assoluto durante il debug per evitare la sorpresa “file non trovato”. Una volta sicuro, torna a un percorso relativo per la portabilità.

---

## Sostituire Testo in DOCX Usando l'AI

Ecco il cuore del tutorial—**come sostituire testo** in un file DOCX con l'assistenza dell'AI. Il metodo `replaceText` invia il contenuto del documento al LLM, gli chiede di eseguire la sostituzione e restituisce il testo revisionato.

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

*Cosa succede dietro le quinte?*  
`DocumentAi` serializza il DOCX in testo semplice, costruisce un prompt del tipo:

> “Nel documento seguente, sostituisci ogni occorrenza di ‘old phrase’ con ‘new phrase’ e restituisci solo il testo aggiornato.”

Il LLM elabora la richiesta e restituisce il contenuto modificato. Questo approccio funziona anche quando la frase si estende su più run o paragrafi—qualcosa che la semplice sostituzione di stringhe spesso non rileva.

---

## Verificare e Stampare il Testo Revisionato

Infine stampiamo il testo revisionato dall'AI sulla console. In un'app reale probabilmente scriveresti il risultato in un nuovo DOCX, ma la stampa ti permette di verificare rapidamente.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Output atteso** (supponendo che il DOCX originale contenga “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Se vedi comparire la nuova frase, congratulazioni—**hai appena imparato come usare Document AI per sostituire una frase con l'AI**.

---

## Esempio Completo Funzionante

Mettendo tutto insieme, ecco una classe Java completa, pronta per l'esecuzione. Sentiti libero di copiare‑incollare in `src/main/java/com/example/ReplaceInDocx.java`.

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

### Come Eseguire

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Assicurati che il server LLM sia attivo prima di eseguire il programma; altrimenti otterrai un timeout di connessione.

---

## Casi Limite & Problemi Comuni

| Situazione | Cosa Controllare | Correzione Suggerita |
|------------|------------------|----------------------|
| **Frase non trovata** | Il LLM restituisce il testo originale invariato. | Ricontrolla ortografia e sensibilità al maiuscolo/minuscolo; puoi aggiungere `ignoreCase:true` al prompt se il tuo wrapper lo supporta. |
| **Documenti grandi (>5 MB)** | La dimensione del prompt può superare il limite di token del modello. | Dividi il DOCX in sezioni, elabora ciascuna separatamente, poi concatena i risultati. |
| **LLM locale restituisce errori** | Spesso causato da nome modello non corrispondente. | Verifica che il nome del modello nell'interfaccia LLM (`ollama list`) corrisponda a `modelConfig.setModelName`. |
| **Caratteri Unicode corrotti** | Problemi di codifica nella lettura del DOCX. | Assicurati che il runtime Java usi UTF‑8 (aggiungi `-Dfile.encoding=UTF-8` agli argomenti JVM). |

---

## Prossimi Passi

Ora che sai **come sostituire testo in DOCX** con l'AI, potresti voler esplorare:

- **Come usare Document AI** per compiti più complessi come l'estrazione di tabelle o la preservazione dello stile.  
- **Sostituire frase con AI** nei PDF cambiando l'argomento del costruttore `Document`.  
- **Elaborazione batch**: iterare su una cartella di file DOCX e applicare la stessa sostituzione.  

Ognuno di questi si basa sulla stessa base `AiModelConfig` e `DocumentAi`, così non dovrai ricominciare da zero.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}