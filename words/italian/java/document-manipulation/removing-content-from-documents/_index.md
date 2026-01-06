---
date: 2026-01-06
description: Scopri come rimuovere i piè di pagina dai documenti Word usando Aspose.Words
  per Java, oltre a come eliminare interruzioni di sezione, interruzioni di pagina
  e altro.
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Come rimuovere i piè di pagina dai documenti Word usando Aspose.Words per Java
url: /it/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come rimuovere i piè di pagina dai documenti Word usando Aspose.Words per Java

## Introduzione ad Aspose.Words per Java

In questo tutorial scoprirai **come rimuovere i piè di pagina da Word** file programmaticamente con Aspose.Words per Java. Che tu debba pulire report generati, rimuovere informazioni riservate, o semplicemente sistemare un modello, questa guida ti accompagna attraverso gli scenari più comuni di rimozione di contenuti—interruzioni di pagina, interruzioni di sezione, piè di pagina e indici. Iniziamo!

## Risposte rapide
- **Posso rimuovere i piè di pagina senza influire su altri contenuti?** Sì, l'API ti consente di mirare solo ai nodi del piè di pagina.
- **È necessaria una licenza per eseguire questi esempi?** Una prova gratuita è sufficiente per lo sviluppo; è richiesta una licenza per la produzione.
- **Quali formati Word sono supportati?** DOC, DOCX, DOCM e formati basati su OOXML.
- **Il codice è compatibile con Java 8 e versioni successive?** Assolutamente, la libreria è compatibile con Java dalla versione 8 in poi.
- **Come posso eliminare le interruzioni di sezione?** Vedi la sezione “Come eliminare le interruzioni di sezione” più sotto.

## Che cosa significa “rimuovere i piè di pagina da Word”?

Rimuovere i piè di pagina da un documento Word significa eliminare i nodi `HeaderFooter` che appaiono nella parte inferiore di ogni pagina. Questa operazione è comune quando si desidera produrre un layout pulito con solo intestazioni o quando i piè di pagina contengono dati sensibili che non devono essere condivisi.

## Perché usare Aspose.Words per Java per questo compito?

Aspose.Words fornisce un modello di oggetti di alto livello che astrae la complessità del formato file DOCX. Puoi manipolare paragrafi, run, sezioni e piè di pagina con poche righe di codice Java, senza la necessità di avere Microsoft Word installato sul server.

## Prerequisiti
- Java Development Kit (JDK) 8 o versioni successive.
- Libreria Aspose.Words per Java (scaricabile dal sito Aspose).
- Un documento Word di esempio (`Document.docx`) posizionato in una directory nota.

## Rimozione delle interruzioni di pagina

Le interruzioni di pagina controllano l'impaginazione ma a volte devono essere rimosse. Il frammento seguente analizza ogni paragrafo, cancella il flag `PageBreakBefore` e rimuove eventuali caratteri di interruzione di pagina espliciti.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*Consiglio:* Esegui questo prima di rimuovere i piè di pagina se desideri un layout a pagina singola.

## Come eliminare le interruzioni di sezione

Le interruzioni di sezione dividono un documento in sezioni indipendenti, ciascuna con le proprie intestazioni, piè di pagina e impostazioni di pagina. Per unire le sezioni ed eliminare efficacemente le **interruzioni di sezione**, itera in ordine inverso, anteponi il contenuto di ogni sezione precedente a quella finale, e poi rimuovi la sezione ora vuota.

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

Questo approccio preserva tutti i contenuti eliminando al contempo la rottura strutturale.

## Rimozione dei piè di pagina (Obiettivo principale: rimuovere i piè di pagina da Word)

I piè di pagina contengono spesso numeri di pagina, date o note riservate. Il codice qui sotto rimuove **tutti i tipi di piè di pagina**—prima pagina, principale e anche pagine pari—da ogni sezione.

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

Dopo aver eseguito questo frammento, il documento risultante non avrà **nessun piè di pagina**, raggiungendo l'obiettivo principale di “rimuovere i piè di pagina da Word”.

## Rimozione dell'indice (Table of Contents)

Un indice (TOC) è memorizzato come campo. Per eliminarlo, individua il campo TOC tramite il suo indice e rimuovi il nodo associato.

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(Il metodo `removeTableOfContents` fa parte degli esempi di Aspose.Words e rimuove il nodo TOC specificato.)*

## Problemi comuni e risoluzione

| Sintomo | Causa probabile | Risoluzione |
|---------|-----------------|-------------|
| I piè di pagina compaiono ancora dopo l'esecuzione del codice | Il documento contiene coppie **header/footer** che non vengono accedute (ad esempio, `FOOTER_FIRST` mancante) | Itera su tutti i valori `HeaderFooterType` o verifica che non siano `null` prima di chiamare `remove()`. |
| Il layout della pagina cambia inaspettatamente dopo l'eliminazione delle interruzioni di sezione | Le impostazioni di pagina specifiche della sezione (margini, orientamento) sono state perse | Copia le impostazioni della sezione nella sezione di destinazione prima della rimozione. |
| `ControlChar.PAGE_BREAK` non è stato rimosso | Il documento utilizza **interruzioni di sezione** invece di caratteri di interruzione di pagina | Usa prima il metodo “Come eliminare le interruzioni di sezione”. |

## Domande frequenti

**Q: Posso rimuovere solo specifici piè di pagina (ad esempio, solo il piè di pagina della prima pagina)?**  
A: Sì. Recupera il piè di pagina per il suo tipo (`FOOTER_FIRST`) e chiama `remove()` solo su quella istanza.

**Q: Come posso eliminare le interruzioni di sezione senza unire i contenuti?**  
A: Puoi rimuovere direttamente un nodo `Section` se non è necessario preservare il suo contenuto, ma tieni presente che tutte le intestazioni/piè di pagina collegati a quella sezione verranno anch'essi persi.

**Q: È possibile rilevare programmaticamente se un documento contiene un indice (TOC) prima di provare a eliminarlo?**  
A: Usa `doc.getRange().getFields()` e verifica la presenza di campi di tipo `FieldType.FIELD_TABLE_OF_CONTENTS`.

**Q: Aspose.Words supporta la rimozione dei piè di pagina da file Word crittografati?**  
A: Sì, basta aprire il documento con la password: `new Document(path, new LoadOptions(password))`.

**Q: La rimozione dei piè di pagina influirà sull'impaginazione del documento?**  
A: Rimuovere i piè di pagina non modifica i numeri di pagina, a meno che il piè di pagina stesso contenga il campo del numero di pagina. Se è necessario rinumerare le pagine, aggiorna i campi del numero di pagina di conseguenza.

## Conclusione

Abbiamo coperto tutto ciò di cui hai bisogno per **rimuovere i piè di pagina da documenti Word** usando Aspose.Words per Java, insieme a compiti correlati come l'eliminazione delle interruzioni di pagina, **come eliminare le interruzioni di sezione**, e la rimozione degli indici. Sfruttando questi frammenti, puoi produrre documenti puliti e professionali su misura per i requisiti della tua applicazione.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Ultimo aggiornamento:** 2026-01-06  
**Testato con:** Aspose.Words for Java 24.12  
**Autore:** Aspose