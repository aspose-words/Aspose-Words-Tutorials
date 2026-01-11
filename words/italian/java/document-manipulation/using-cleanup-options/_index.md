---
date: 2026-01-11
description: Scopri come pulire un documento Word usando le opzioni di pulizia di
  Aspose.Words per Java, inclusa la rimozione di paragrafi vuoti, righe di tabella
  vuote e campi inutilizzati.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Pulizia del documento Word usando le opzioni di pulizia di Aspose.Words (Java)
url: /it/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Pulizia di Documenti Word con le Opzioni di Pulizia di Aspose.Words (Java)

In questo tutorial scoprirai come **pulire i file Word** con Aspose.Words per Java. Che tu stia generando fatture, contratti o report di mail‑merge in blocco, paragrafi vuoti indesiderati, campi inutilizzati o righe di tabella vuote possono far apparire il risultato finale poco professionale. Ti guideremo passo‑passo attraverso ciascuna opzione di pulizia, ti mostreremo il codice esatto di cui hai bisogno e spiegheremo *perché* ogni impostazione è importante, così potrai produrre documenti impeccabili ogni volta.

## Risposte Rapide
- **Cosa significa “pulire un documento Word”?** Rimuovere paragrafi vuoti, regioni di merge inutilizzate, righe di tabella vuote e altri elementi ridondanti dopo un'operazione di mail‑merge.  
- **Quale opzione di pulizia rimuove i paragrafi vuoti?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Come posso eliminare le righe di tabella vuote?** Usa `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Posso eliminare i campi che non sono mai stati popolati?** Sì – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` o `REMOVE_EMPTY_FIELDS`.  
- **È necessaria una licenza per eseguire questi esempi?** Una versione di prova gratuita è sufficiente per la valutazione; è richiesta una licenza commerciale per l'uso in produzione.

## Che cosa significa “Pulire un documento Word” nel contesto del Mail Merge?
Quando esegui un mail merge, Aspose.Words inserisce dati nei campi e nelle regioni di merge. Se alcuni campi ricevono `null` o stringhe vuote, il documento può finire con paragrafi sparsi, tabelle vuote o regioni segnaposto. Le **opzioni di pulizia** rimuovono automaticamente questi artefatti, lasciando un documento pulito e pronto per la stampa.

## Perché usare le Opzioni di Pulizia?
- **Aspetto professionale:** Nessuna riga vuota o tabelle orfane.  
- **Dimensione file ridotta:** Rimuovere gli elementi inutilizzati diminuisce il peso del documento.  
- **Elaborazione a valle semplificata:** I documenti puliti sono più facili da convertire in PDF, HTML o altri formati.  
- **Risparmio di tempo:** Un’impostazione a una riga sostituisce script di post‑processing manuali.

## Prerequisiti
- Ambiente di sviluppo Java (JDK 8+).  
- Libreria Aspose.Words per Java – scaricala da [here](https://releases.aspose.com/words/java/).  
- Familiarità di base con i concetti di mail‑merge.

## Guida Passo‑Passo

### Passo 1: Come Rimuovere i Paragrafi Vuoti (Java)
Per prima cosa mostreremo come eliminare i paragrafi che non contengono testo visibile. È particolarmente utile quando un campo di merge risolve a `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Cosa succede qui?**  
- `REMOVE_EMPTY_PARAGRAPHS` indica ad Aspose.Words di eliminare qualsiasi paragrafo che risulta vuoto dopo il merge.  
- Abilitare `cleanupParagraphsWithPunctuationMarks` rimuove anche i paragrafi composti esclusivamente da punteggiatura (ad es., “?”).

### Passo 2: Come Rimuovere le Regioni Non Unificate
Se una regione di mail‑merge non ha dati corrispondenti, puoi scartarla completamente.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Perché è importante:**  
Le regioni inutilizzate spesso lasciano sezioni vuote o intestazioni isolate. Il flag `REMOVE_UNUSED_REGIONS` le pulisce automaticamente.

### Passo 3: Come Rimuovere i Campi Vuoti
Quando un campo riceve una stringa vuota, potresti voler rimuovere l’intero campo anziché lasciare un segnaposto bianco.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Passo 4: Come Rimuovere i Campi Inutilizzati
Se alcuni campi non vengono mai referenziati durante il merge, puoi eliminarli del tutto.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Passo 5: Come Rimuovere i Campi Contenuti
A volte un campo di merge si trova all’interno di un paragrafo che desideri anche eliminare.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Passo 6: Come Rimuovere le Righe di Tabella Vuote
Le tabelle spesso terminano con righe che contengono solo campi vuoti. Questa opzione elimina tali righe.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Problemi Comuni e Risoluzione
- **Paragrafi non rimossi:** Assicurati che `setCleanupParagraphsWithPunctuationMarks(true)` sia chiamato *dopo* aver impostato l’opzione di pulizia.  
- **Righe di tabella vuote persistono:** Verifica che le celle della tabella contengano realmente stringhe vuote (non spazi bianchi).  
- **Campi inutilizzati rimangono:** Controlla di aver usato l’enum corretto (`REMOVE_UNUSED_FIELDS`) e che i campi di merge non siano popolati accidentalmente altrove.

## Domande Frequenti

**D: Qual è la differenza tra `REMOVE_EMPTY_FIELDS` e `REMOVE_UNUSED_FIELDS`?**  
R: `REMOVE_EMPTY_FIELDS` elimina i campi che ricevono una stringa vuota o `null` durante il merge, mentre `REMOVE_UNUSED_FIELDS` rimuove i campi che non sono mai stati referenziati dall’operazione di merge.

**D: Posso combinare più opzioni di pulizia?**  
R: Sì. Il metodo `setCleanupOptions` accetta un OR bitwise dei valori enum, consentendoti di pulire paragrafi, tabelle e regioni in un’unica chiamata.

**D: L’attivazione di `cleanupParagraphsWithPunctuationMarks` influisce sul testo normale?**  
R: Rimuove solo i paragrafi composti esclusivamente da caratteri di punteggiatura (ad es., “?” o “---”). Le frasi regolari rimangono intatte.

**D: È possibile personalizzare quali segni di punteggiatura vengono considerati?**  
R: L’API attuale utilizza un set predefinito di caratteri di punteggiatura. Per un comportamento personalizzato, dovresti post‑processare il documento dopo il merge.

**D: Queste opzioni di pulizia funzionano con la conversione PDF?**  
R: Assolutamente. Una volta pulito il documento Word, puoi convertirlo in PDF, HTML o qualsiasi altro formato supportato senza trasportare gli elementi indesiderati.

## Conclusione
Ora disponi di una cassetta degli attrezzi completa per **pulire i file Word** durante il mail merge con Aspose.Words per Java. Selezionando le opportune `MailMergeCleanupOptions`, puoi rimuovere automaticamente paragrafi vuoti, righe di tabella vuote, campi inutilizzati e molto altro, ottenendo un documento elegante e pronto per la produzione ogni volta.

---

**Ultimo aggiornamento:** 2026-01-11  
**Testato con:** Aspose.Words per Java 24.11  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}