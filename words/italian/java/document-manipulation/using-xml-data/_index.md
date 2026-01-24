---
date: 2026-01-24
description: Scopri come unire dati XML con Aspose.Words per Java, automatizzare la
  generazione di documenti Java e utilizzare la sintassi Mustache per documenti dinamici.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Come unire XML in Aspose.Words per Java
url: /it/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come unire XML in Aspose.Words per Java

In questa guida completa scoprirai **come unire dati XML** usando Aspose.Words per Java. Ti guideremo attraverso scenari di mail‑merge di base e nidificati, ti mostreremo come **usare la sintassi Mustache** e spiegheremo come **automatizzare progetti di generazione di documenti in stile Java**. Alla fine sarai in grado di generare documenti Word personalizzati direttamente da fonti XML con poche righe di codice.

## Risposte rapide
- **Qual è la classe principale per il mail merge?** `Document` e la sua proprietà `MailMerge`.  
- **Posso unire tabelle XML nidificate?** Sì – usa `executeWithRegions` per dati gerarchici.  
- **La sintassi Mustache è supportata?** Abilitala con `setUseNonMergeFields(true)`.  
- **È necessaria una licenza per la produzione?** È richiesta una licenza commerciale di Aspose.Words.  
- **Quale versione di Java è compatibile?** Java 8+ e successive sono pienamente supportate.

## Cos'è il Mail Merge XML in Aspose.Words?
Il mail merge XML ti consente di collegare set di dati basati su XML a segnaposti in un modello Word. Il motore sostituisce ogni segnaposto con il valore del nodo XML corrispondente, producendo un documento finale senza modifiche manuali.

## Perché usare Aspose.Words per la generazione di documenti basati su XML?
- **Automatizza progetti di generazione di documenti Java** senza dipendenze da Microsoft Office.  
- **Supporto per gerarchie complesse** – tabelle nidificate, sezioni ripetute e contenuti condizionali.  
- **Sintassi Mustache** ti offre segnaposti flessibili, non‑campo‑merge, per templating avanzato.  
- **Cross‑platform** – funziona su Windows, Linux e macOS.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) installato (l'ultima versione).  
- File XML di esempio per clienti, ordini e fornitori (il tutorial utilizza `Mail merge data - Customers.xml`, `Orders.xml` e `Vendors.xml`).  
- Documenti modello Word che contengono campi di merge (ad es., `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Come unire XML – Mail Merge di base

Un mail merge di base importa una singola tabella XML in un modello Word. Segui questi passaggi:

1. Carica il file XML in un `DataSet`.  
2. Apri il documento Word di destinazione.  
3. Esegui il merge usando il nome della tabella.  
4. Salva il documento unito.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Consiglio professionale:** Mantieni la struttura XML piatta per merge semplici – ogni tabella dovrebbe corrispondere direttamente a un insieme di campi di merge.

## Come unire XML – Mail Merge nidificato

Quando il tuo XML contiene relazioni padre‑figlio (ad es., ordini con righe di dettaglio), è necessario un merge nidificato. Il metodo `executeWithRegions` elabora ogni regione in modo ricorsivo.

1. Carica l'XML gerarchico in un `DataSet`.  
2. Disabilita il trimming degli spazi bianchi se hai bisogno di una formattazione esatta.  
3. Chiama `executeWithRegions` per gestire tutte le tabelle nidificate.  
4. Salva il risultato.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Errore comune:** Dimenticare di impostare `setTrimWhitespaces(false)` può causare spazi indesiderati nel documento finale, specialmente per campi di valuta o numerici.

## Come usare la sintassi Mustache con un DataSet

La sintassi Mustache ti consente di inserire segnaposti non‑campo‑merge (ad es., `{{CustomerName}}`) all'interno del tuo modello. Abilitala ed esegui un merge basato su regioni.

1. Carica l'XML del fornitore.  
2. Attiva il supporto Mustache con `setUseNonMergeFields(true)`.  
3. Esegui il merge con le regioni.  
4. Salva l'output.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Perché usare Mustache?** Fornisce un modo pulito e indipendente dal linguaggio per fare riferimento ai dati, rendendo i tuoi modelli più facili da leggere e mantenere, specialmente quando **generi documenti** in flussi di lavoro guidati da XML.

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| Nodi XML non corrispondenti ai campi di merge | Verifica che i nomi degli elementi XML corrispondano esattamente ai nomi dei campi di merge (case‑sensitive). |
| Spazi bianchi appaiono attorno ai valori uniti | Usa `doc.getMailMerge().setTrimWhitespaces(false)` per preservare la spaziatura originale. |
| Le tabelle nidificate vengono ignorate | Assicurati che la regione della tabella padre sia definita nel modello (ad es., `{{#Orders}} … {{/Orders}}`). |
| Segnaposti Mustache non sostituiti | Chiama `setUseNonMergeFields(true)` prima di eseguire il merge. |

## FAQ

### Come posso preparare i miei dati XML per il mail merge?
Assicurati che il tuo XML segua una struttura tabellare in cui ogni elemento `<TableName>` contiene righe (`<Row>`) e colonne che corrispondono ai campi di merge nel tuo modello Word.

### Posso personalizzare il comportamento del trim per i valori del mail merge?
Sì. Usa `doc.getMailMerge().setTrimWhitespaces(false)` per mantenere gli spazi iniziali/finali esattamente come appaiono nell'XML.

### Cos'è la sintassi Mustache e quando dovrei usarla?
La sintassi Mustache (`{{FieldName}}`) consente segnaposti flessibili che non sono limitati ai tradizionali campi di merge. Abilitala con `setUseNonMergeFields(true)` quando hai bisogno di un modello più pulito o vuoi separare la logica dei dati dai codici dei campi Word.

### Come automatizzo i progetti Java di generazione di documenti con questo approccio?
Integra i frammenti di codice sopra nel tuo livello di servizio, leggi XML da database o API, e invoca la routine di merge ogni volta che è necessario un nuovo documento (ad es., generazione di fatture, creazione di contratti).

### È necessaria una licenza commerciale per l'uso in produzione?
Sì, Aspose.Words richiede una licenza valida per le distribuzioni in produzione. È disponibile una licenza temporanea gratuita per la valutazione.

**Ultimo aggiornamento:** 2026-01-24  
**Testato con:** Aspose.Words for Java (ultima versione)  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}