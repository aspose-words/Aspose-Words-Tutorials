---
date: '2025-11-12'
description: Scopri come utilizzare LayoutCollector e LayoutEnumerator di Aspose.Words
  per Java per analizzare l'impaginazione, attraversare il layout del documento, implementare
  callback di layout e ripristinare la numerazione delle pagine nelle sezioni continue.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: it
title: Analisi della paginazione Java con gli strumenti di layout di Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Analisi della Paginazione Java con gli Strumenti di Layout di Aspose.Words

## Introduzione  

Se hai bisogno di **analizzare la paginazione** o **esplorare il layout di un documento** in un'applicazione Java, Aspose.Words per Java ti offre due potenti API: **`LayoutCollector`** e **`LayoutEnumerator`**. Queste classi ti consentono di scoprire quante pagine occupa un nodo, percorrere ogni entità di layout, reagire agli eventi di layout e persino riavviare la numerazione delle pagine nelle sezioni continue. In questa guida percorreremo ogni funzionalità passo‑a‑passo, mostreremo snippet di codice reali e spiegheremo i risultati attesi così potrai applicarli subito.

Imparerai a:

* **usare LayoutCollector** per ottenere la pagina iniziale e finale di qualsiasi nodo (use layoutcollector page span)  
* **esplorare il layout del documento** con LayoutEnumerator (traverse document layout)  
* **implementare callback di layout** per reagire agli eventi di paginazione (implement layout callback)  
* **riavviare la numerazione delle pagine** nelle sezioni continue (restart page numbering sections)  

Iniziamo.

## Prerequisiti  

### Librerie richieste  

| Strumento di Build | Dipendenza |
|--------------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Nota:** Il numero di versione è mantenuto per compatibilità; il codice funziona con qualsiasi versione recente di Aspose.Words per Java.

### Ambiente  

* JDK 8 o superiore  
* Un IDE come IntelliJ IDEA o Eclipse  

### Conoscenze  

Una conoscenza di base della programmazione Java e familiarità con Maven/Gradle è sufficiente per seguire gli esempi.

## Configurazione di Aspose.Words  

Prima di poter chiamare qualsiasi API di layout, la libreria deve essere licenziata (o usata in modalità di prova). Lo snippet qui sotto mostra l'inizializzazione minima:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Il codice non modifica alcun documento; prepara semplicemente l'ambiente Aspose.*  

Ora possiamo approfondire le funzionalità principali.

## Funzionalità 1: Utilizzare **LayoutCollector** per Analizzare la Paginazione  

`LayoutCollector` associa ogni nodo in un `Document` alle pagine che occupa. Questo è il modo più affidabile per **use layoutcollector page span** per l'analisi della paginazione.

### Implementazione passo‑a‑passo  

1. **Crea un nuovo documento e collega un LayoutCollector.**  
2. **Inserisci contenuto che forzi la paginazione** (ad es., interruzioni di pagina, interruzioni di sezione).  
3. **Aggiorna il layout** con `updatePageLayout()`.  
4. **Interroga il collector** per la pagina iniziale, finale e il numero totale di pagine occupate.

#### 1️⃣ Inizializza Document e LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Popola il Documento  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Aggiorna il Layout e Recupera le Metriche  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Output previsto**

```
Document spans 5 pages.
```

> **Perché funziona:** `updatePageLayout()` costringe Aspose.Words a ricalcolare il layout, dopodiché `LayoutCollector` può riportare con precisione gli intervalli di pagina.

## Funzionalità 2: Esplorare il Layout del Documento con **LayoutEnumerator**  

Quando è necessario **traverse document layout** (ad es., per rendering personalizzato o analisi), `LayoutEnumerator` fornisce una vista ad albero di pagine, paragrafi, righe e parole.

### Implementazione passo‑a‑passo  

1. Carica un documento esistente che contenga entità di layout.  
2. Crea un'istanza di `LayoutEnumerator`.  
3. Spostati sull'entità radice `PAGE`.  
4. Percorri il layout in avanti e indietro usando metodi di supporto ricorsivi.

#### 1️⃣ Carica il Documento e Crea l'Enumerator  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Posizionati al Livello di Pagina  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Traversata in Avanti (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Traversata all'Indietro  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Metodi di supporto** (`traverseLayoutForward` / `traverseLayoutBackward`) sono implementati ricorsivamente per visitare ogni entità figlia e stampare il suo tipo e l'indice di pagina. Puoi adattarli per raccogliere statistiche, renderizzare grafica o modificare proprietà di layout.

## Funzionalità 3: Implementare **Layout Callbacks**  

A volte è necessario reagire quando Aspose.Words termina il layout di una parte del documento. Implementare `IPageLayout