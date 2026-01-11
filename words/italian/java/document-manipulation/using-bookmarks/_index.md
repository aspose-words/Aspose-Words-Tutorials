---
date: 2026-01-11
description: Impara come mostrare e nascondere i segnalibri e creare segnalibri Java
  usando Aspose.Words per Java per una navigazione e manipolazione efficiente dei
  documenti.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Mostra/Nascondi i segnalibri con Aspose.Words per Java
url: /it/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mostra/Nascondi Segnalibri con Aspose.Words per Java

## Introduzione all'uso dei segnalibri in Aspose.Words per Java

I segnalibri sono una funzionalità potente in Aspose.Words per Java che consente di **creare bookmark java**, navigare verso contenuti specifici e persino **mostrare nascondere segnalibri** quando è necessario generare versioni diverse del documento. In questa guida passo‑passo vedremo come creare, accedere, aggiornare, copiare e alternare la visibilità dei segnalibri, offrendoti il pieno controllo sulla manipolazione dei documenti.

## Risposte rapide
- **Qual è lo scopo principale dei segnalibri?** Contrassegnare e successivamente recuperare parti specifiche di un documento.  
- **Posso nascondere i marcatori dei segnalibri nell'output finale?** Sì—usa l'API show/hide per alternarne la visibilità.  
- **Come creo un segnalibro all'interno di una cella di tabella?** Avvia e chiudi il segnalibro con `DocumentBuilder` mentre il cursore è nella cella.  
- **È possibile copiare il testo segnalato in un altro documento?** Assolutamente—usa `NodeImporter` per preservare la formattazione.  
- **Quale versione di Aspose.Words è necessaria?** Qualsiasi rilascio recente; il codice funziona con l'ultima build 2026.

## Cos'è la funzionalità “mostra nascondi segnalibri”?

La funzionalità **mostra nascondi segnalibri** consente di visualizzare o nascondere programmaticamente i delimitatori dei segnalibri nel documento salvato. È utile quando si desidera generare un output pulito per gli utenti finali mantenendo al contempo i dati dei segnalibri per l'elaborazione interna.

## Perché usare i segnalibri nell'automazione di documenti Java?

- **Navigazione efficiente** – Salta direttamente alle sezioni senza scansionare l'intero file.  
- **Generazione dinamica di contenuti** – Inserisci, sostituisci o rimuovi testo associato a un segnalibro.  
- **Visibilità condizionale** – Mostra o nascondi i marcatori dei segnalibri in base alle preferenze dell'utente o al formato di output.  
- **Riutilizzabilità** – Copia frammenti segnalati tra documenti preservando gli stili.

## Prerequisiti
- Java Development Kit (JDK) 8 o superiore.  
- Libreria Aspose.Words per Java aggiunta al progetto (Maven/Gradle o JAR).  
- Familiarità di base con le classi `Document` e `DocumentBuilder`.

## Guida passo‑passo

### Passo 1: Creare un segnalibro (create bookmark java)

Per aggiungere un segnalibro, lo si avvia, si scrive il contenuto, quindi lo si chiude. Questo esempio crea un semplice segnalibro chiamato **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Passo 2: Accedere ai segnalibri (access bookmarks java)

I segnalibri possono essere recuperati sia per indice (basato su zero) sia per nome. Il codice qui sotto dimostra entrambi gli approcci.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Passo 3: Aggiornare i dati del segnalibro (update bookmark text)

È possibile rinominare un segnalibro o sostituirne il contenuto testuale. Questo è utile quando il documento di base subisce modifiche.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Passo 4: Lavorare con il testo segnalato (copy bookmarked text)

Copiare un frammento segnalato in un altro documento mantenendo la formattazione originale è semplice con `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Passo 5: Mostrare e nascondere i segnalibri (show hide bookmarks)

Il frammento seguente dimostra come nascondere i marcatori di un segnalibro nel file salvato. Passa `false` per nascondere, `true` per mostrare.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Passo 6: Slegare i segnalibri di riga (bookmark table cell)

Quando i segnalibri attraversano più righe di una tabella, possono diventare intrecciati. I metodi di utilità qui sotto li slegano e consentono di eliminare una riga specifica tramite il suo segnalibro.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| **Segnalibro non trovato** | Verifica che il nome del segnalibro corrisponda esattamente (case‑sensitive) e che il documento sia stato salvato dopo la creazione. |
| **Il testo copiato perde la formattazione** | Usa `ImportFormatMode.KEEP_SOURCE_FORMATTING` con `NodeImporter` come mostrato nel Passo 4. |
| **Show/hide non influisce sull'output** | Assicurati di chiamare `showHideBookmarkedContent` **prima** di salvare il documento. |
| **Segnalibro all'interno di una cella di tabella ignorato** | Esegui le chiamate start/end mentre il cursore del builder è all'interno della cella target. |

## Domande frequenti

**D: Come creo un segnalibro in una cella di tabella?**  
R: Usa `DocumentBuilder` per spostare il cursore nella cella desiderata, quindi chiama `startBookmark` e `endBookmark` attorno al contenuto della cella.

**D: Posso copiare un segnalibro in un altro documento?**  
R: Sì—usa la classe `NodeImporter` (vedi Passo 4) per importare il nodo segnalato mantenendo la formattazione originale.

**D: Come posso eliminare una riga tramite il suo segnalibro?**  
R: Individua prima la riga che contiene il segnalibro, quindi chiama `remove` sul nodo della riga (come mostrato nel Passo 6).

**D: Quali sono alcuni casi d'uso comuni per i segnalibri?**  
R: Generare un indice, estrarre sezioni specifiche per report, e automatizzare l'assemblaggio di documenti in base alle scelte dell'utente.

**D: Dove posso trovare ulteriori informazioni su Aspose.Words per Java?**  
R: Per documentazione dettagliata e download, visita [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Ultimo aggiornamento:** 2026-01-11  
**Testato con:** Aspose.Words per Java 24.11 (2026)  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}