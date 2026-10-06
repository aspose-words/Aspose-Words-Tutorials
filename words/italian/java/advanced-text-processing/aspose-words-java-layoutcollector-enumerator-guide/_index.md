---
date: '2026-01-14'
description: Impara come riavviare la numerazione delle pagine con Aspose.Words Java
  e utilizzare LayoutCollector per estrarre i dati di impaginazione, aggiornare il
  layout della pagina e renderizzare le pagine come immagini.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Riavviare la numerazione delle pagine con Aspose.Words Java – LayoutCollector
  e LayoutEnumerator
url: /it/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Riavviare la numerazione delle pagine con Aspose.Words Java – LayoutCollector e LayoutEnumerator

## Introduzione

Stai avendo difficoltà a **riavviare la numerazione delle pagine** in documenti Java di grandi dimensioni e allo stesso tempo hai bisogno di analizzare la paginazione o di renderizzare le pagine come immagini? Con **Aspose.Words for Java** puoi sfruttare `LayoutCollector` e `LayoutEnumerator` non solo per riavviare la numerazione delle pagine, ma anche per **estrarre dati di paginazione**, **aggiornare il layout delle pagine** e **renderizzare le pagine come immagini** per anteprime o PDF. Questa guida ti accompagna passo passo, dall'installazione della libreria all'implementazione di callback che ti danno il pieno controllo sul rendering del documento.

**Ciò che imparerai**
- Come usare `LayoutCollector` per estrarre dati di paginazione e determinare l’estensione delle pagine.
- Come attraversare il layout del documento con `LayoutEnumerator`.
- Come implementare callback di layout di pagina per **renderizzare le pagine come immagini**.
- **Riavviare la numerazione delle pagine** in sezioni continue usando le opzioni di layout.
- Suggerimenti per **aggiornare il layout delle pagine** in modo efficiente.

## Risposte rapide
- **Come riavvio la numerazione delle pagine in un documento Java?** Usa `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` e chiama `doc.updatePageLayout()`.
- **Quale classe estrae i dati di paginazione?** `LayoutCollector` fornisce gli indici di pagina iniziale/finale per qualsiasi nodo.
- **Posso renderizzare ogni pagina come immagine?** Sì—implementa `IPageLayoutCallback` e usa `ImageSaveOptions`.
- **Devo chiamare manualmente l’aggiornamento del layout della pagina?** Dopo aver modificato le opzioni di layout, chiama sempre `doc.updatePageLayout()`.
- **Quale versione di Aspose.Words è necessaria?** Gli esempi funzionano con Aspose.Words for Java 25.3 (o successive).

## Cos’è il riavvio della numerazione delle pagine?

Riavviare la numerazione delle pagine consente di iniziare una nuova sequenza numerica in una sezione specifica del documento, fondamentale per rapporti, libri o contratti che richiedono una numerazione separata per capitoli o appendici. Aspose.Words fornisce un’opzione di layout che permette di controllare questo comportamento senza ricorrere a trucchi manuali con interruzioni di pagina.

## Perché usare LayoutCollector e LayoutEnumerator?

- **LayoutCollector** ti dà accesso programmatico ai dettagli della paginazione, permettendoti di **estrarre dati di paginazione** come la prima e l’ultima pagina di qualsiasi nodo.
- **LayoutEnumerator** ti consente di percorrere l’albero di layout visivo, facilitando la localizzazione di pagine, paragrafi o righe per rendering personalizzati o analisi.
- Insieme semplificano compiti di layout complessi che altrimenti richiederebbero costose conversioni PDF o calcoli manuali.

## Prerequisiti

### Librerie richieste e versioni
Assicurati di avere installato Aspose.Words for Java versione 25.3 (o più recente).

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Requisiti per l’ambiente di sviluppo
- Java Development Kit (JDK) installato.
- IntelliJ IDEA, Eclipse o qualsiasi IDE Java di tua scelta.
- Una licenza valida di Aspose.Words (la versione di prova gratuita è sufficiente per la valutazione).

### Conoscenze preliminari
È sufficiente una conoscenza di base della programmazione Java.

## Configurazione di Aspose.Words
Per prima cosa, integra la libreria Aspose.Words nel tuo progetto. Puoi ottenere una licenza di prova gratuita [qui](https://releases.aspose.com/words/java/) o utilizzare una licenza temporanea per i test.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

Con la libreria pronta, possiamo approfondire le funzionalità principali.

## Guida all’implementazione

### Funzionalità 1: Uso di LayoutCollector per l’analisi dell’estensione delle pagine
La funzionalità `LayoutCollector` ti permette di determinare come i nodi si estendono tra le pagine, base per **estrarre dati di paginazione**.

#### Panoramica
Sfruttando `LayoutCollector`, puoi recuperare gli indici di pagina iniziale e finale di qualsiasi nodo e calcolare il numero totale di pagine occupate.

#### Passaggi di implementazione

**1. Inizializza Document e LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Popola il documento**
Qui aggiungeremo contenuto che si estende su più pagine:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Aggiorna il layout e recupera le metriche**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### Spiegazione
- **`DocumentBuilder`** inserisce testo e interruzioni di pagina/sezione.
- **`updatePageLayout()`** ricalcola le informazioni di layout affinché i dati di paginazione siano accurati.

### Funzionalità 2: Attraversamento con LayoutEnumerator
`LayoutEnumerator` consente una navigazione efficiente attraverso l’albero di layout visivo.

#### Panoramica
Puoi percorrere pagine, paragrafi, righe e altre entità di layout, utile per rendering personalizzati o diagnosi.

#### Passaggi di implementazione

**1. Inizializza Document e LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. Traversing forward e backward**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Spiegazione
- **`moveParent()`** sposta l’enumeratore all’entità genitore (in questo caso, il livello di pagina).
- I metodi di traversamento ricorsivo ti permettono di esplorare l’intera gerarchia di layout.

### Funzionalità 3: Callback di layout di pagina
Implementa callback per monitorare gli eventi di layout e **renderizzare le pagine come immagini** quando necessario.

#### Panoramica
L’interfaccia `IPageLayoutCallback` ti notifica quando una parte del documento termina il reflow o quando la conversione è completata.

#### Passaggi di implementazione

**1. Imposta il callback**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Implementa i metodi del callback**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### Spiegazione
- **`notify()`** reagisce agli eventi di layout.
- **`ImageSaveOptions`** insieme a `PageSet` ti permette di **renderizzare le pagine come immagini** (PNG in questo esempio).

### Funzionalità 4: Riavviare la numerazione delle pagine in sezioni continue
Controlla la numerazione delle pagine quando hai più sezioni che fluiscono in modo continuo.

#### Panoramica
Impostando l’opzione `ContinuousSectionRestart`, puoi decidere se i numeri di pagina si riavviano su una nuova pagina o continuano senza interruzioni.

#### Passaggi di implementazione

**1. Carica il documento**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Configura le opzioni di numerazione delle pagine**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### Spiegazione
- **`setContinuousSectionPageNumberingRestart()`** indica ad Aspose.Words come gestire la numerazione nelle sezioni continue.
- Dopo aver modificato l’opzione, **aggiorna il layout della pagina** per applicare le modifiche.

## Applicazioni pratiche
1. **Analisi della paginazione del documento** – Usa `LayoutCollector` per verificare come il contenuto si distribuisce tra le pagine e regola margini o interruzioni di conseguenza.
2. **Rendering PDF** – Combina `LayoutEnumerator` con il callback per generare immagini di pagina ad alta fedeltà prima della conversione in PDF.
3. **Aggiornamenti dinamici del documento** – Reagisci agli eventi di layout (ad esempio, dopo l’espansione di una tabella) e renderizza automaticamente le pagine interessate.
4. **Report multi‑sezione** – Applica **riavvio della numerazione delle pagine** per dare a ogni capitolo la propria numerazione mantenendo un flusso continuo.

## Considerazioni sulle prestazioni
- Rimuovi sezioni inutilizzate o contenuti nascosti prima di chiamare `updatePageLayout()` per mantenere veloce l’elaborazione.
- Usa le API di streaming per documenti di grandi dimensioni per evitare di caricare l’intero file in memoria.
- Limita la profondità del traversamento ricorsivo in `LayoutEnumerator` se ti servono solo informazioni a livello di pagina.

## Problemi comuni e soluzioni
| Problema | Causa | Soluzione |
|----------|-------|-----------|
| `layoutCollector.getNumPagesSpanned()` restituisce 0 | Layout non aggiornato | Chiama `doc.updatePageLayout()` prima di interrogare |
| Le immagini non vengono generate nel callback | Configurazione mancante di `ImageSaveOptions` | Assicurati che `saveOptions.setPageSet(new PageSet(pageIndex))` sia impostato |
| I numeri di pagina non si riavviano | Valore errato di `ContinuousSectionRestart` | Usa `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` per un vero riavvio |

## Domande frequenti

**D: Posso estrarre il numero di pagina esatto di un paragrafo specifico?**  
R: Sì—usa `LayoutCollector` per ottenere la pagina iniziale del nodo paragrafo e poi chiama `doc.updatePageLayout()` per garantire che i dati siano aggiornati.

**D: L’`update page layout` influisce sul contenuto del documento?**  
R: No. Ricalcola solo le informazioni di layout; il testo e la formattazione rimangono invariati.

**D: Come renderizzo efficientemente tutte le pagine di un documento voluminoso come immagini?**  
R: Implementa `IPageLayoutCallback` e processa ogni pagina in sequenza, eventualmente usando il multithreading per le operazioni di I/O di salvataggio.

**D: È possibile riavviare la numerazione solo per alcune sezioni?**  
R: Sì—applica `setContinuousSectionPageNumberingRestart` alle opzioni di layout della sezione specifica prima di chiamare `updatePageLayout()`.

**D: Quale versione di Aspose.Words ha introdotto `LayoutCollector`?**  
R: `LayoutCollector` è disponibile sin dalle versioni del 2020; gli esempi usano la versione 25.3.

## Conclusione
Padroneggiando **riavvio della numerazione delle pagine**, `LayoutCollector` e `LayoutEnumerator`, ora disponi di un toolkit potente per l’elaborazione avanzata del testo in Aspose.Words for Java. Che tu debba **estrarre dati di paginazione**, **renderizzare le pagine come immagini** o semplicemente controllare la numerazione delle pagine tra le sezioni, queste API ti offrono un controllo preciso e programmatico mantenendo alte le prestazioni.

---

**Ultimo aggiornamento:** 2026-01-14  
**Testato con:** Aspose.Words for Java 25.3  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}