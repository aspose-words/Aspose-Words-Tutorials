---
date: '2025-11-12'
description: Scopri come utilizzare LayoutCollector e LayoutEnumerator di Aspose.Words
  per Java per determinare gli intervalli di pagina, attraversare le entità di layout
  e ripristinare la numerazione delle pagine nelle sezioni continue.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: it
title: 'Aspose.Words Java: Guida a LayoutCollector e LayoutEnumerator'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: Guida a LayoutCollector e LayoutEnumerator

## Introduzione  

Stai avendo difficoltà a **determinare l’intervallo di pagine**, analizzare la paginazione o riavviare la numerazione delle pagine in documenti Java complessi? Con **Aspose.Words for Java** puoi risolvere rapidamente questi problemi usando `LayoutCollector` e `LayoutEnumerator`. In questa guida ti mostreremo **come usare LayoutCollector**, **come attraversare LayoutEnumerator** e come controllare la numerazione delle pagine nelle sezioni continue—tutto con codice chiaro, passo‑per‑passo, pronto da eseguire oggi.

Imparerai a:

1. Usare `LayoutCollector` per **determinare l’intervallo di pagine** di qualsiasi nodo.  
2. **Attraversare le entità di layout** con `LayoutEnumerator`.  
3. Implementare callback di layout per il rendering dinamico.  
4. **Riavviare la numerazione delle pagine** nelle sezioni continue.  

Iniziamo assicurandoci che l’ambiente sia pronto.

## Prerequisiti  

### Librerie richieste  

> **Nota:** Il codice funziona con l’ultima versione di Aspose.Words for Java (non è necessario indicare il numero di versione).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### Ambiente  

- JDK 17 o versioni successive.  
- IntelliJ IDEA, Eclipse o qualsiasi IDE Java preferiate.  

### Conoscenze  

Una conoscenza di base della sintassi Java e dei concetti di programmazione orientata agli oggetti ti aiuterà a seguire gli esempi.

## Configurazione di Aspose.Words  

Per prima cosa, aggiungi la libreria Aspose.Words al tuo progetto e applica una licenza (o utilizza la versione di prova). Il frammento seguente mostra come caricare la licenza e verificare che la libreria sia pronta:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Suggerimento:** Conserva il file di licenza al di fuori del controllo di versione per proteggere le tue credenziali.

Ora possiamo approfondire le due funzionalità principali.

## 1. Come utilizzare LayoutCollector per l'analisi dell’intervallo di pagine  

`LayoutCollector` ti consente di **determinare l’intervallo di pagine** per qualsiasi nodo in un documento, funzione fondamentale per l’analisi della paginazione.

### Implementazione passo‑per‑passo  

1. **Crea un nuovo Document e un'istanza di LayoutCollector.**  
2. **Aggiungi contenuto che si estende su più pagine.**  
3. **Aggiorna il layout e interroga le metriche dell’intervallo di pagine.**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Spiegazione**

- `DocumentBuilder` inserisce testo e interruzioni, creando un documento che naturalmente occupa diverse pagine.  
- `updatePageLayout()` forza Aspose.Words a calcolare il layout, garantendo numeri di pagina accurati.  
- `getNumPagesSpanned()` restituisce il totale delle pagine coperte dal nodo fornito (qui l’intero documento).

## 2. Come attraversare LayoutEnumerator  

`LayoutEnumerator` fornisce una **vista strutturata delle entità di layout** (pagine, paragrafi, run, ecc.) e consente di spostarsi in avanti o indietro tra di esse.

### Implementazione passo‑per‑passo  

1. Carica un documento esistente che contiene entità di layout.  
2. Crea un'istanza di `LayoutEnumerator`.  
3. Passa al livello di pagina, quindi attraversa in avanti e indietro usando i metodi di supporto.  

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Nota:** I metodi `traverseLayoutForward` e `traverseLayoutBackward` sono helper ricorsivi che percorrono l’albero di layout. Puoi personalizzarli per raccogliere informazioni come bounding box, dettagli di carattere o metadati personalizzati.

## 3. Come implementare i callback di layout di pagina  

Talvolta è necessario reagire a eventi di layout—ad esempio, quando una sezione termina il reflow o quando la conversione in un altro formato è completata. Implementa l’interfaccia `IPageLayoutCallback` per ricevere queste notifiche.

### Implementazione passo‑per‑passo  

1. Imposta un’istanza di callback nelle opzioni di layout del documento.  
2. Definisci la logica del callback per gestire gli eventi `PART_REFLOW_FINISHED` e `CONVERSION_FINISHED`.  

```java
// 1. Register the callback
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();   // Triggers the callback during layout processing

// 2. Callback implementation
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs args) throws Exception {
        if (args.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            renderPage(args, args.getPageIndex());
        } else if (args.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            System.out.println("Document conversion finished.");
        }
    }

    private void renderPage(PageLayoutCallbackArgs args, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            args.getDocument().save(stream, saveOptions);
        }
    }
}
```

**Spiegazione**

- `notify()` riceve ogni evento di layout. Filtr