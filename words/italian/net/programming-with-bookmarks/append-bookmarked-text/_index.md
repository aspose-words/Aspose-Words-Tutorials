---
title: Aggiungi testo con segnalibro nel documento Word
linktitle: Aggiungi testo con segnalibro nel documento Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come aggiungere testo con segnalibro in un documento Word usando Aspose.Words per .NET con questa guida passo-passo. Perfetta per gli sviluppatori.
weight: 10
url: /it/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi testo con segnalibro nel documento Word

## Introduzione

Ciao! Hai mai provato ad aggiungere testo da una sezione con segnalibro in un documento Word e l'hai trovato complicato? Sei fortunato! Questo tutorial ti guiderà attraverso il processo usando Aspose.Words per .NET. Lo suddivideremo in semplici passaggi in modo che tu possa seguirli facilmente. Immergiamoci e aggiungiamo quel testo con segnalibro come un professionista!

## Prerequisiti

Prima di iniziare, assicuriamoci di avere tutto ciò di cui hai bisogno:

-  Aspose.Words per .NET: assicurati di averlo installato. In caso contrario, puoi[scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: qualsiasi ambiente di sviluppo .NET come Visual Studio.
- Conoscenza di base di C#: sarà utile comprendere i concetti base della programmazione C#.
- Documento Word con segnalibri: un documento Word con segnalibri impostati, che utilizzeremo per aggiungere testo.

## Importazione degli spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo ci assicurerà di avere tutti gli strumenti di cui abbiamo bisogno a portata di mano.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Analizziamo l'esempio nei passaggi dettagliati.

## Passaggio 1: caricare il documento e inizializzare le variabili

Bene, iniziamo caricando il nostro documento Word e inizializzando le variabili di cui avremo bisogno.

```csharp
// Caricare i documenti di origine e di destinazione.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inizializzare l'importatore di documenti.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Trova il segnalibro nel documento di origine.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Passaggio 2: identificare i paragrafi iniziali e finali

Ora, individuiamo i paragrafi in cui inizia e finisce il segnalibro. Questo è fondamentale perché dobbiamo gestire il testo entro questi limiti.

```csharp
// Questo è il paragrafo che contiene l'inizio del segnalibro.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Questo è il paragrafo che contiene la fine del segnalibro.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Passaggio 3: convalidare i genitori del paragrafo

Dobbiamo assicurarci che i paragrafi iniziali e finali abbiano lo stesso genitore. Questo è uno scenario semplice per mantenere le cose dirette.

```csharp
// Limitiamoci a uno scenario abbastanza semplice.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Passaggio 4: identificare il nodo da interrompere

Poi, dobbiamo determinare il nodo in cui interromperemo la copia del testo. Questo sarà il nodo immediatamente dopo il paragrafo finale.

```csharp
// Vogliamo copiare tutti i paragrafi dal paragrafo iniziale fino al paragrafo finale (incluso),
// pertanto il nodo in cui ci fermiamo è quello dopo il paragrafo finale.
Node endNode = endPara.NextSibling;
```

## Passaggio 5: aggiungere il testo aggiunto ai segnalibri al documento di destinazione

Infine, eseguiamo un ciclo attraverso i nodi dal paragrafo iniziale al nodo successivo al paragrafo finale e aggiungiamoli al documento di destinazione.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Ciò crea una copia del nodo corrente e la importa (la rende valida) nel contesto
    // del documento di destinazione. L'importazione significa adattare correttamente stili e identificatori di elenco.
    Node newNode = importer.ImportNode(curNode, true);

    // Aggiungere il nodo importato al documento di destinazione.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Salvare il documento di destinazione con il testo allegato.
dstDoc.Save("appended_document.docx");
```

## Conclusione

Ed ecco fatto! Hai aggiunto con successo del testo da una sezione con segnalibro in un documento Word usando Aspose.Words per .NET. Questo potente strumento rende la manipolazione dei documenti un gioco da ragazzi, e ora hai un altro asso nella manica. Buona codifica!

## Domande frequenti

### Posso aggiungere testo da più segnalibri in una volta sola?
Sì, puoi ripetere il procedimento per ogni segnalibro e aggiungere il testo di conseguenza.

### Cosa succede se i paragrafi iniziale e finale hanno genitori diversi?
L'esempio attuale presuppone che abbiano lo stesso genitore. Per genitori diversi, è richiesta una gestione più complessa.

### Posso mantenere la formattazione originale del testo allegato?
 Assolutamente! Il`ImportFormatMode.KeepSourceFormatting` garantisce che la formattazione originale venga preservata.

### È possibile aggiungere del testo in una posizione specifica nel documento di destinazione?
Sì, puoi aggiungere il testo in qualsiasi posizione navigando fino al nodo desiderato nel documento di destinazione.

### Cosa succede se devo aggiungere del testo da un segnalibro a una nuova sezione?
È possibile creare una nuova sezione nel documento di destinazione e aggiungervi il testo.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
