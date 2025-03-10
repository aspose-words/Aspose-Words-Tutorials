---
title: Utilizzo delle opzioni di pulizia in Aspose.Words per Java
linktitle: Utilizzo delle opzioni di pulizia
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Migliora la chiarezza del documento con le opzioni di pulizia di Aspose.Words for Java. Scopri come rimuovere paragrafi vuoti, regioni inutilizzate e altro ancora.
weight: 10
url: /it/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo delle opzioni di pulizia in Aspose.Words per Java


## Introduzione all'utilizzo delle opzioni di pulizia in Aspose.Words per Java

In questo tutorial, esploreremo come usare le opzioni di pulizia in Aspose.Words per Java per manipolare e pulire i documenti durante il processo di unione di posta. Le opzioni di pulizia consentono di controllare vari aspetti della pulizia del documento, come la rimozione di paragrafi vuoti, regioni inutilizzate e altro.

## Prerequisiti

 Prima di iniziare, assicurati di avere la libreria Aspose.Words for Java integrata nel tuo progetto. Puoi scaricarla da[Qui](https://releases.aspose.com/words/java/).

## Passaggio 1: rimozione dei paragrafi vuoti

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserisci campi di unione
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Imposta le opzioni di pulizia
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Abilita la pulizia dei paragrafi con segni di punteggiatura
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Esegui unione di posta
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Salva il documento
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

In questo esempio, creiamo un nuovo documento, inseriamo campi di unione e impostiamo le opzioni di pulizia per rimuovere i paragrafi vuoti. Inoltre, abilitiamo la rimozione dei paragrafi con segni di punteggiatura. Dopo aver eseguito la stampa unione, il documento viene salvato con la pulizia specificata applicata.

## Passaggio 2: rimozione delle regioni non unite

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Imposta le opzioni di pulizia per rimuovere le regioni inutilizzate
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Esegui unione di posta con regioni
doc.getMailMerge().executeWithRegions(data);

// Salva il documento
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

In questo esempio, apriamo un documento esistente con aree di unione, impostiamo le opzioni di pulizia per rimuovere le aree inutilizzate e quindi eseguiamo la stampa unione con dati vuoti. Questo processo rimuove automaticamente le aree inutilizzate dal documento.

## Passaggio 3: rimozione dei campi vuoti

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Imposta le opzioni di pulizia per rimuovere i campi vuoti
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Esegui unione di posta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salva il documento
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

In questo esempio, apriamo un documento con campi di unione, impostiamo le opzioni di pulizia per rimuovere i campi vuoti ed eseguiamo la stampa unione con i dati. Dopo l'unione, tutti i campi vuoti saranno rimossi dal documento.

## Passaggio 4: rimozione dei campi inutilizzati

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Imposta le opzioni di pulizia per rimuovere i campi inutilizzati
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Esegui unione di posta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salva il documento
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

In questo esempio, apriamo un documento con campi di unione, impostiamo le opzioni di pulizia per rimuovere i campi inutilizzati ed eseguiamo la stampa unione con i dati. Dopo l'unione, tutti i campi inutilizzati saranno rimossi dal documento.

## Passaggio 5: rimozione dei campi contenenti

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Imposta le opzioni di pulizia per rimuovere i campi contenenti
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Esegui unione di posta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salva il documento
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

In questo esempio, apriamo un documento con campi di unione, impostiamo le opzioni di pulizia per rimuovere i campi contenenti ed eseguiamo la stampa unione con i dati. Dopo l'unione, i campi stessi saranno rimossi dal documento.

## Passaggio 6: rimozione delle righe vuote della tabella

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Imposta le opzioni di pulizia per rimuovere le righe vuote della tabella
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Esegui unione di posta
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Salva il documento
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

In questo esempio, apriamo un documento con una tabella e campi di unione, impostiamo le opzioni di pulizia per rimuovere le righe vuote della tabella ed eseguiamo la stampa unione con i dati. Dopo l'unione, tutte le righe vuote della tabella saranno rimosse dal documento.

## Conclusione

In questo tutorial, hai imparato come usare le opzioni di pulizia in Aspose.Words per Java per manipolare e pulire i documenti durante il processo di unione di posta. Queste opzioni forniscono un controllo dettagliato sulla pulizia dei documenti, consentendoti di creare documenti raffinati e personalizzati con facilità.

## Domande frequenti

### Quali sono le opzioni di pulizia in Aspose.Words per Java?

Le opzioni di pulizia in Aspose.Words per Java sono impostazioni che consentono di controllare vari aspetti della pulizia del documento durante il processo di unione di posta. Consentono di rimuovere elementi non necessari come paragrafi vuoti, regioni inutilizzate e altro, assicurando che il documento finale sia ben strutturato e rifinito.

### Come posso rimuovere i paragrafi vuoti dal mio documento?

 Per rimuovere i paragrafi vuoti dal tuo documento utilizzando Aspose.Words per Java, puoi impostare`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` opzione su true. Ciò eliminerà automaticamente i paragrafi che non hanno contenuto, ottenendo un documento più pulito.

###  Qual è lo scopo del`REMOVE_UNUSED_REGIONS` cleanup option?

 IL`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` l'opzione viene utilizzata per rimuovere le regioni in un documento che non hanno dati corrispondenti durante il processo di unione di posta. Aiuta a mantenere il documento ordinato eliminando i segnaposto inutilizzati.

### Posso rimuovere le righe vuote di una tabella da un documento utilizzando Aspose.Words per Java?

 Sì, puoi rimuovere le righe di tabella vuote da un documento impostando`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`opzione cleanup su true. Questo eliminerà automaticamente tutte le righe della tabella che non contengono dati, assicurando una tabella ben strutturata nel documento.

###  Cosa succede quando imposto il`REMOVE_CONTAINING_FIELDS` option?

 Impostazione del`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` opzione rimuoverà l'intero campo di unione, incluso il paragrafo che lo contiene, dal documento durante il processo di unione di posta. Ciò è utile quando si desidera eliminare i campi di unione e il testo associato.

### Come posso rimuovere i campi unione inutilizzati dal mio documento?

 Per rimuovere i campi di unione non utilizzati da un documento, è possibile impostare`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` opzione su true. Questo eliminerà automaticamente i campi di unione che non sono popolati durante la stampa unione, ottenendo un documento più pulito.

###  Qual è la differenza tra`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 IL`REMOVE_EMPTY_FIELDS` l'opzione rimuove i campi di unione che non hanno dati o sono vuoti durante il processo di unione di posta. D'altra parte, l'`REMOVE_UNUSED_FIELDS`l'opzione rimuove i campi di unione che non sono popolati con dati durante l'unione. La scelta tra di essi dipende se si desidera rimuovere i campi senza contenuto o quelli che non sono utilizzati nell'operazione di unione specifica.

### Come posso abilitare la rimozione dei paragrafi con segni di punteggiatura?

 Per abilitare la rimozione dei paragrafi con segni di punteggiatura, è possibile impostare`cleanupParagraphsWithPunctuationMarks` opzione su true e specifica i segni di punteggiatura da considerare per la pulizia. Ciò consente di creare un documento più raffinato rimuovendo i paragrafi non necessari con sola punteggiatura.

### Posso personalizzare le opzioni di pulizia in Aspose.Words per Java?

Sì, puoi personalizzare le opzioni di pulizia in base alle tue esigenze specifiche. Puoi scegliere quali opzioni di pulizia applicare e configurarle in base ai requisiti di pulizia del documento, assicurandoti che il documento finale soddisfi gli standard desiderati.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
