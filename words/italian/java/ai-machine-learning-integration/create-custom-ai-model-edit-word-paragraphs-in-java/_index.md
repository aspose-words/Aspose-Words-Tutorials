---
category: general
date: 2026-03-25
description: Crea un modello AI personalizzato per modificare documenti Word – impara
  a rendere il testo più formale, sostituire il testo di un paragrafo e riscrivere
  un paragrafo Word usando Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: it
og_description: Crea un modello AI personalizzato per modificare documenti Word. Scopri
  come rendere il testo più formale, sostituire il testo di un paragrafo e riscrivere
  un paragrafo Word usando Aspose.Words AI.
og_title: Crea modello AI personalizzato – Modifica paragrafi Word in Java
tags:
- Aspose.Words
- Java
- AI integration
title: Crea modello AI personalizzato – Modifica paragrafi Word in Java
url: /it/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea Modello AI Personalizzato – Modifica Paragrafi Word in Java

Hai mai avuto bisogno di **create custom AI model** che possa perfezionare un paragrafo all'interno di un file Word? Forse hai un batch di contratti che suonano tutti un po' troppo informali, e ti piacerebbe rendere il testo più formale con una sola riga di codice. La buona notizia è che puoi fare esattamente questo—senza servizi esterni, senza SDK ingombranti, solo Aspose.Words per Java e un endpoint compatibile con OpenAI.

In questo tutorial percorreremo tutti i passaggi necessari per **create custom AI model**, collegarlo a un server LLM locale e poi usarlo per *replace paragraph text* con una versione più formale. Alla fine avrai un programma Java eseguibile che **edit paragraph with AI**, riscrive un paragrafo Word e salva il risultato su disco. Niente fronzoli, solo una soluzione pratica che puoi copiare‑incollare nel tuo progetto.

> **Cosa ti servirà**  
> • Java 17 o superiore (il codice compila anche con versioni precedenti, ma 17 è il punto ideale)  
> • Aspose.Words for Java 23.9 (o l'ultima release)  
> • Un server LLM compatibile con OpenAI in esecuzione (ad es., Ollama, LocalAI) in ascolto su `http://localhost:8000/v1`  
> • Un documento Word di input (`input.docx`) posizionato in una cartella che controlli  

Se ti chiedi *why bother building a custom model* invece di chiamare direttamente OpenAI, la risposta è flessibilità: controlli l'endpoint, puoi cambiare modello senza modificare il codice e mantieni le chiavi API fuori dal tuo repository sorgente. Immergiamoci.

---

## Crea Modello AI Personalizzato – Configurazione e Setup

Per prima cosa dobbiamo indicare ad Aspose.Words dove si trova il nostro LLM. La classe `AiModelEndpoint` contiene l'URL e la chiave API opzionale. Poiché stiamo usando un server locale, la chiave può essere una stringa vuota, ma il parametro è obbligatorio.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Consiglio professionale:** se mai passi a un modello hosted (ad es., Azure OpenAI), basta cambiare l'URL e la chiave—non sono necessarie altre modifiche al codice.

---

## Carica il Documento Word

Ora carichiamo il file sorgente in memoria. `Document` può leggere `.docx`, `.doc`, `.rtf` e molti altri formati, ma per questo esempio ci limitiamo a `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Assicurati che `YOUR_DIRECTORY` punti a una cartella reale; altrimenti otterrai una `FileNotFoundException`. In un'applicazione reale potresti passare il percorso come argomento da riga di comando o leggerlo da un file di configurazione.

---

## Inizializza il Modello AI Personalizzato

Creiamo un `AiModel` di tipo `CUSTOM` e gli assegniamo l'endpoint definito in precedenza. Questo indica ad Aspose.Words di instradare tutte le chiamate AI attraverso il nostro server.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Dietro le quinte Aspose.Words costruisce un piccolo client HTTP che comunica con il LLM usando lo schema standard di chat/completion di OpenAI. Ecco perché l'endpoint deve essere *OpenAI‑compatible*.

---

## Recupera e Riscrivi il Primo Paragrafo

Qui è dove effettivamente **make text more formal**. Preleviamo il primo paragrafo, inviamo il suo testo grezzo al modello con un prompt e riceviamo la versione modificata.

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

Il secondo argomento (`"Make it more formal"`) è l'istruzione che diamo al modello. Puoi sostituirlo con qualsiasi direttiva—**replace paragraph text**, **summarize**, **translate**, ecc. Il metodo restituisce una stringa semplice, che inseriremo più tardi nel documento.

> **Perché funziona:** `editText` invia un payload JSON come `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. L'LLM vede il paragrafo originale e l'istruzione, quindi risponde con il testo revisionato.

---

## Sostituisci il Contenuto del Paragrafo Originale

Ora **replace paragraph text** all'interno del modello a oggetti di Word. Rimuoviamo eventuali run esistenti (i pezzi di testo a basso livello) e inseriamo un nuovo `Run` contenente la stringa generata dall'AI.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Fai attenzione a non chiamare `firstParagraph.setText()`—quel metodo rimuoverebbe tutta la formattazione. Usare `Run` preserva lo stile del paragrafo (intestazione, elenco puntato, ecc.) mentre sostituisce i caratteri.

---

## Salva il Documento Modificato

Infine, scriviamo il documento modificato su disco. Puoi sovrascrivere il file originale o, come facciamo qui, creare una nuova copia.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Quando apri `output.docx` dovresti vedere il primo paragrafo ora notevolmente più formale. Se l'LLM non ha seguito perfettamente l'istruzione, puoi modificare il prompt o provare una versione diversa del modello.

---

## Esempio Completo Funzionante

Di seguito il programma completo—copialo in `LlmDemo.java`, regola i percorsi e eseguilo con `javac` + `java`.

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

**Output atteso:** Apri `output.docx` e vedrai il paragrafo originale trasformato. Per esempio, una frase informale come “We’ll get the thing done soon.” potrebbe diventare “We shall complete the task promptly.” La formulazione esatta dipende dal modello che stai usando.

---

## Domande Frequenti & Casi Limite

### E se il mio documento ha più sezioni?

Il codice sopra tocca solo il *primo* paragrafo della *prima* sezione. Per **edit paragraph with AI** su tutto il file, itera su `document.getSections()` e poi su ciascun `section.getBody().getParagraphs()`. Ricorda di saltare i paragrafi vuoti, altrimenti l'LLM riceve una stringa vuota e non restituisce nulla.

### Come gestire paragrafi lunghi che superano i limiti di token?

La maggior parte degli LLM limita l'input a circa 4 000 token. Se un paragrafo è insolitamente lungo, dividilo in blocchi più piccoli prima di chiamare `editText`. Puoi riutilizzare la stessa istanza `AiModel`; basta fare attenzione ai limiti di velocità sul tuo server locale.

### Posso usare un'istruzione diversa, come “summarize” o “translate to French”?

Assolutamente. Il secondo argomento di `editText` è libero. Per un riassunto potresti passare `"Summarize in one sentence"`. Per la traduzione, `"Translate to French, keep the tone formal"` funziona altrettanto bene. Questa flessibilità ti consente di **replace paragraph text** per molti scenari senza modificare alcun codice.

### Il modello preserva lo stile del paragrafo (font, colori)?

Poiché sostituiamo solo il `Run` all'interno dello stesso oggetto `Paragraph`, gli stili esistenti (livello di intestazione, elenco puntato, rientro) rimangono intatti. Se devi cambiare lo stile stesso, puoi manipolare `Paragraph.getParagraphFormat()` dopo la sostituzione.

### E se il mio server LLM richiede HTTPS con un certificato autofirmato?

`AiModelEndpoint` accetta un URL con `https://`. Se il certificato non è attendibile, dovrai configurare il contesto SSL di Java per fidartene, oppure eseguire il server con un certificato valido. Questa configurazione è fuori dall'ambito di questo tutorial ma ben documentata nelle guide SSL per Java.

---

## Consigli per l'Integrazione Pronta alla Produzione

| Tip | Why it matters |
|-----|----------------|
| **Cache l'endpoint** | Ricreare `AiModelEndpoint` ad ogni richiesta aggiunge overhead. |
| **Modifiche batch** | Se hai molti paragrafi, inviali in un'unica richiesta (ad es., array JSON) per ridurre la latenza. |
| **Convalida l'output LLM** | Controlla sempre che la stringa restituita non sia null o vuota prima di inserirla. |
| **Registra prompt e risposte** | Utile per il debug e per la conformità quando riscrivi testi legali. |
| **Fallback elegante** | Se l'LLM è inattivo, ricorri al paragrafo originale o a una riscrittura euristica semplice. |

---

## Conclusione

Ti abbiamo mostrato come **create custom AI model** con Aspose.Words, collegarlo a un endpoint compatibile con OpenAI e poi **edit paragraph with AI** per **make text more formal**. Seguendo i sei passaggi—definire l'endpoint, caricare il documento, inizializzare il modello,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}