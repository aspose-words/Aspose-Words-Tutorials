---
title: Districare i segnalibri di riga nel documento di Word
linktitle: Districare i segnalibri di riga nel documento di Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Districa facilmente i segnalibri di righe aggrovigliati nei tuoi documenti Word utilizzando Aspose.Words per .NET. Questa guida ti guida attraverso il processo per una gestione dei segnalibri più pulita e sicura.
weight: 10
url: /it/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Districare i segnalibri di riga nel documento di Word

## Introduzione

Hai mai riscontrato una situazione in cui l'eliminazione di una riga in un documento Word tramite un segnalibro rovina altri segnalibri nelle righe adiacenti? Questo può essere incredibilmente frustrante, soprattutto quando si ha a che fare con tabelle complesse. Per fortuna, Aspose.Words per .NET offre una soluzione potente: districare i segnalibri di riga. 

Questa guida ti guiderà attraverso il processo di districare i segnalibri di riga nei tuoi documenti Word utilizzando Aspose.Words per .NET. Suddivideremo il codice in passaggi di facile comprensione e spiegheremo lo scopo di ciascuna funzione, consentendoti di affrontare con sicurezza quei fastidiosi problemi relativi ai segnalibri.

## Prerequisiti

Prima di immergerti, avrai bisogno di alcune cose:

1.  Aspose.Words per .NET: questa libreria commerciale fornisce funzionalità per lavorare con documenti Word a livello di codice. 2. Puoi scaricare una versione di prova gratuita da[collegamento per il download](https://releases.aspose.com/words/net/) o acquistare una licenza da[acquistare](https://purchase.aspose.com/buy).
3. Ambiente di sviluppo AC#: Visual Studio o qualsiasi altro IDE C# funzionerà perfettamente.
4. Un documento Word con segnalibri di riga: utilizzeremo un documento di esempio denominato "Segnalibri colonna tabella.docx" a scopo dimostrativo.

## Importa spazi dei nomi

Il primo passaggio prevede l'importazione degli spazi dei nomi necessari nel progetto C#. Questi spazi dei nomi forniscono l'accesso alle classi e alle funzionalità che utilizzeremo da Aspose.Words per .NET:

```csharp
using Aspose.Words;
using System;
```

## Passaggio 1: caricare il documento Word

 Iniziamo caricando il documento Word contenente i segnalibri delle righe aggrovigliate. IL`Document` la classe gestisce la manipolazione dei documenti in Aspose.Words. Ecco come caricare il documento:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Sostituisci con la posizione del documento
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Ricordarsi di sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo del file "Colonna tabella bookmarks.docx".

## Passaggio 2: districare i segnalibri delle righe

 È qui che avviene la magia! IL`Untangle` la funzione si occupa di districare i segnalibri delle righe. Analizziamo le sue funzionalità:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Ottieni la riga madre sia del segnalibro che della fine del segnalibro
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Controlla se le righe sono valide e adiacenti
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Sposta la fine del segnalibro all'ultimo paragrafo dell'ultima cella della riga superiore
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Ecco una spiegazione passo passo di cosa fa il codice:

 Iteriamo attraverso tutti i segnalibri nel documento utilizzando a`foreach` ciclo continuo.
Per ogni segnalibro, recuperiamo la riga madre sia dell'inizio del segnalibro (`bookmark.BookmarkStart`) e la fine del segnalibro (`bookmark.BookmarkEnd` ) utilizzando il`GetAncestor` metodo.
Controlliamo quindi se sono state trovate entrambe le righe (`row1 != null`E`row2 != null`) e se sono righe adiacenti (`row1.NextSibling == row2`). Ciò garantisce di modificare solo i segnalibri che si estendono su righe adiacenti.
Se le condizioni sono soddisfatte, spostiamo il nodo finale del segnalibro alla fine dell'ultimo paragrafo nell'ultima cella della riga superiore (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) districandoli efficacemente.

## Passaggio 3: Elimina riga tramite segnalibro

 Ora che i segnalibri sono districati, possiamo eliminare in sicurezza le righe utilizzando i nomi dei segnalibri. IL`DeleteRowByBookmark` la funzione gestisce questo compito:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Ecco una ripartizione di questa funzione:

Prendiamo il nome del segnalibro (`bookmarkName`) come input.
 Recuperiamo l'oggetto segnalibro corrispondente utilizzando`doc.Range.Bookmarks[bookmarkName]`.
Quindi otteniamo che la riga madre del segnalibro inizi a utilizzare`GetAncestor` (simile a`Untangle` funzione).
Infine, controlliamo se il segnalibro e la riga esistono (`bookmark != null` E

## Passaggio 4: verificare la districazione

 Mentre il`Untangle` La funzione dovrebbe garantire la sicurezza degli altri segnalibri, è sempre buona norma verificarla. Ecco come possiamo verificare se il processo di districazione non ha eliminato accidentalmente la fine di un altro segnalibro:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Questo frammento di codice controlla se la fine del segnalibro denominato "ROW1" esiste ancora dopo aver eliminato la riga con il segnalibro "ROW2". Se è nullo, viene generata un'eccezione, che indica un problema con il processo di districazione. 

## Passaggio 5: salva il documento

 Infine, dopo aver districato i segnalibri ed eventualmente eliminato le righe, salva il documento modificato utilizzando il file`Save` metodo:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Ciò salva il documento con i segnalibri districati e tutte le righe cancellate con un nuovo nome file "WorkingWithBookmarks.UntangleRowBookmarks.docx". 

## Conclusione

 Seguendo questi passaggi e utilizzando il file`Untangle`funzione, puoi districare efficacemente i segnalibri di riga nei tuoi documenti Word con Aspose.Words per .NET. Ciò garantisce che l'eliminazione di righe tramite segnalibri non causi conseguenze indesiderate con altri segnalibri nelle righe adiacenti. Ricordati di sostituire i segnaposto come`"YOUR DOCUMENT DIRECTORY"` con i percorsi effettivi e i nomi dei file.

## Domande frequenti

### Aspose.Words per .NET è gratuito?

 Aspose.Words per .NET è una libreria commerciale con una versione di prova gratuita disponibile. Puoi scaricarlo da[collegamento per il download](https://releases.aspose.com/words/net/).

### Posso districare manualmente i segnalibri di riga in Word?

Sebbene tecnicamente possibile, districare manualmente i segnalibri in Word può essere noioso e soggetto a errori. Aspose.Words per .NET automatizza questo processo, risparmiando tempo e fatica.

###  Cosa succede se il`Untangle` function encounters an error?

Il codice include un gestore di eccezioni che genera un'eccezione se il processo di districazione elimina accidentalmente la fine di un altro segnalibro. È possibile personalizzare la gestione degli errori in base alle proprie esigenze specifiche.

### Posso utilizzare questo codice per districare i segnalibri su righe non adiacenti?

Attualmente, il codice si concentra sul districare i segnalibri che si estendono su righe adiacenti. La modifica del codice per gestire righe non adiacenti richiederebbe logica aggiuntiva per identificare e gestire tali scenari.

### Ci sono limitazioni all’utilizzo di questo approccio?

Questo approccio presuppone che i segnalibri siano ben definiti all'interno delle celle della tabella. Se i segnalibri vengono posizionati all'esterno delle celle o in posizioni impreviste, il processo di districazione potrebbe non funzionare come previsto.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
