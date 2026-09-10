---
category: general
date: 2026-01-11
description: Scopri come catturare gli avvisi di sostituzione dei font utilizzando
  Aspose.Words per Java. Questo tutorial passo‑passo copre anche LoadOptions e i callback
  di avviso.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: it
og_description: Cattura gli avvisi di sostituzione dei font con Aspose.Words per Java.
  Segui questa guida per configurare LoadOptions e una callback di avviso per un caricamento
  affidabile dei documenti.
og_title: Cattura gli avvisi di sostituzione dei font in Java – Tutorial completo
tags:
- Aspose.Words
- Java
- Document Processing
title: Cattura gli avvisi di sostituzione dei font in Java con Aspose.Words – Guida
  completa
url: /it/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Catturare gli avvisi di sostituzione dei font – Tutorial completo Java

Ti è mai capitato di dover **catturare gli avvisi di sostituzione dei font** aprendo un documento Word con font mancanti? È un problema comune, soprattutto quando generi PDF o stampi su un server che non ha installato tutti i tipi di carattere. La buona notizia? Aspose.Words per Java lo rende semplice: basta configurare un oggetto `LoadOptions` e collegare un callback di avviso. In questa guida vedrai esattamente come farlo, perché è importante e cosa aspettarti quando l’avviso viene generato.

Tratteremo anche argomenti correlati come **Aspose.Words font substitution**, l’uso di un **Java warning callback**, e le migliori pratiche per **LoadOptions usage**. Alla fine avrai uno snippet pronto‑da‑eseguire che registra ogni evento di font mancante, così il tuo processo a valle non ti sorprenderà.

## Prerequisiti

- Java 17 (o qualsiasi JDK recente) installato e configurato.  
- Aspose.Words per Java 23.10 (o più recente) nel tuo classpath.  
- Un documento Word che faccia riferimento a un font che non possiedi localmente (ad es., `DocWithMissingFont.docx`).  
- Familiarità di base con i blocchi `try/catch` di Java—nulla di complesso.

Se qualcuno di questi punti ti è sconosciuto, fermati un attimo e installa la libreria da Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Ora che le basi sono pronte, entriamo nel codice.

## Passo 1: Configurare un callback di avviso per **catturare gli avvisi di sostituzione dei font**

La prima cosa di cui hai bisogno è un callback che Aspose.Words invocherà ogni volta che incontra un font mancante. È qui che **catturiamo gli avvisi di sostituzione dei font**. Il callback implementa l’interfaccia `IWarningCallback` e verifica il `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Why this matters:** Senza un callback, Aspose.Words sostituisce silenziosamente il font mancante con uno predefinito, e non saprai mai che l’aspetto visivo è cambiato. Catturando l’avviso, puoi registrare, segnalare o addirittura abortire il caricamento se il font mancante è critico.

## Passo 2: Configurare **LoadOptions** e registrare il callback

Ora creiamo un’istanza di `LoadOptions` e colleghiamo il nostro `FontWarningCallback`. Questo passaggio è essenziale per **LoadOptions usage** e garantisce che ogni caricamento di documento passi attraverso lo stesso filtro di avviso.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Tip:** Puoi riutilizzare lo stesso oggetto `LoadOptions` per più documenti, risparmiando qualche riga di boilerplate e garantendo una gestione coerente degli **document loading warnings** in tutta l’applicazione.

## Passo 3: Caricare il documento e osservare l'output

Con il callback collegato, basta caricare il tuo file Word. Se il documento fa riferimento a un font non installato, il callback verrà attivato e stamperà i dettagli sulla console.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Output previsto della console

Supponendo che `DocWithMissingFont.docx` faccia riferimento al font mancante *“Comic Sans MS”*, vedrai qualcosa di simile:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Se il documento non contiene **font mancanti**, la console mostrerà solo l’ultima riga, confermando che il tuo callback non ha prodotto falsi positivi.

## Passo 4: Gestire i casi limite e le insidie comuni

### Font mancanti multipli

Se un documento utilizza diversi font non disponibili, il callback viene eseguito una volta per ogni font. Otterrai una serie di messaggi, ciascuno con il proprio `source` e `description`. Non è necessario alcun codice aggiuntivo—basta assicurarsi che il sistema di logging possa gestire chiamate rapide consecutive.

### Sopprimere gli avvisi

In rari casi potresti voler ignorare certe sostituzioni (ad es., sai che un determinato fallback è accettabile). Estendi la logica del callback:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Sicurezza dei thread

`LoadOptions` di Aspose.Words non è thread‑safe per impostazione predefinita. Se carichi documenti in parallelo, crea un’istanza separata di `LoadOptions` per ogni thread, o sincronizza il callback per evitare condizioni di gara.

## Passo 5: Verificare il font sostituito nel documento risultante

Dopo il caricamento, potresti voler confermare che la sostituzione sia avvenuta effettivamente. L’API ti permette di iterare su tutti i run e ispezionare il nome del font effettivo:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Questo snippet stampa ogni run di testo con il suo font finale. È un utile controllo di sanità quando costruisci pipeline automatizzate di conversione PDF.

## Esempio completo funzionante

Mettendo tutto insieme, ecco il programma completo, pronto‑da‑eseguire:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Salva questo file come `FontSubstitutionInfo.java`, compila con `javac` ed esegui `java FontSubstitutionInfo`. Dovresti vedere i messaggi di avviso (se presenti) seguiti dall’elenco dei run e dei loro font finali.

## Guida visiva

![Screenshot dell'output della console che mostra gli avvisi di sostituzione dei font](/images/font-substitution-warning.png "esempio di avvisi di sostituzione dei font")

*Testo alternativo:* **catturare gli avvisi di sostituzione dei font** – output della console dopo il caricamento di un documento con font mancanti.

## Conclusione

Ora sai come **catturare gli avvisi di sostituzione dei font** usando Aspose.Words per Java. Configurando un oggetto `LoadOptions` e fornendo un `IWarningCallback` personalizzato, ottieni piena visibilità su qualsiasi evento di font mancante che altrimenti potrebbe influenzare silenziosamente l’aspetto del documento. Questa tecnica si integra direttamente nella gestione di **Aspose.Words font substitution**, garantisce avvisi affidabili durante il **document loading**, e ti offre la flessibilità di registrare, segnalare o abortire in base alle regole di business.

### Prossimi passi

- Esplora i pattern di **Java warning callback** per altri tipi di avviso (ad es., `DEPRECATED_FEATURE`).  
- Combina questo approccio con la **PDF conversion** per assicurarti che i font sostituiti non rompano il layout.  
- Approfondisci l’**uso di LoadOptions**—sperimenta con `Password`, `Encoding` e `ResourceLoadingCallback` per scenari più avanzati.

Sentiti libero di modificare il callback, indirizzare gli avvisi a un framework di logging, o persino lanciare un’eccezione personalizzata se un font critico è mancante. Il cielo è il limite, e ora hai una solida base su cui costruire.

Buon coding, e che i tuoi documenti vengano sempre renderizzati esattamente come ti aspetti!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}