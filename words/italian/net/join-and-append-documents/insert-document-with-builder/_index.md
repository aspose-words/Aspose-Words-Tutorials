---
"description": "Scopri come unire due documenti Word utilizzando Aspose.Words per .NET. Guida passo passo per inserire un documento con DocumentBuilder mantenendo la formattazione."
"linktitle": "Inserisci documento con Builder"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Inserisci documento con Builder"
"url": "/it/net/join-and-append-documents/insert-document-with-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci documento con Builder

## Introduzione

Quindi, hai due documenti Word e vuoi unirli in uno solo. Potresti chiederti: "Esiste un modo semplice per farlo a livello di codice?". Assolutamente! Oggi ti guiderò attraverso il processo di inserimento di un documento in un altro utilizzando la libreria Aspose.Words per .NET. Questo metodo è estremamente utile, soprattutto quando si gestiscono documenti di grandi dimensioni o si ha bisogno di automatizzare il processo. Cominciamo subito!

## Prerequisiti

Prima di iniziare, assicuriamoci di avere tutto ciò di cui hai bisogno:

1. Aspose.Words per .NET: se non l'hai già fatto, puoi scaricarlo da [Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: assicurati di aver installato Visual Studio o un altro IDE adatto.
3. Conoscenza di base di C#: una minima conoscenza di C# può essere molto utile.

## Importa spazi dei nomi

Per prima cosa, devi importare i namespace necessari per accedere alle funzionalità della libreria Aspose.Words. Ecco come fare:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ora che abbiamo definito i prerequisiti, analizziamo il processo passo dopo passo.

## Passaggio 1: impostazione della directory dei documenti

Prima di iniziare a scrivere codice, è necessario impostare il percorso della directory dei documenti. È qui che vengono archiviati i documenti di origine e di destinazione.

```csharp
// Percorso alla directory dei documenti 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Sostituire `"YOUR DOCUMENT DIRECTORY"` Con il percorso effettivo in cui si trovano i tuoi documenti. Questo aiuterà il programma a trovare facilmente i tuoi file.

## Passaggio 2: caricamento dei documenti di origine e di destinazione

Successivamente, dobbiamo caricare i documenti con cui vogliamo lavorare. In questo esempio, abbiamo un documento sorgente e un documento di destinazione.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Qui stiamo usando il `Document` classe dalla libreria Aspose.Words per caricare i nostri documenti. Assicurati che i nomi dei file corrispondano a quelli presenti nella tua directory.

## Passaggio 3: creazione di un oggetto DocumentBuilder

IL `DocumentBuilder` La classe è un potente strumento della libreria Aspose.Words. Ci permette di navigare e manipolare il documento.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

In questo passaggio abbiamo creato un `DocumentBuilder` oggetto per il nostro documento di destinazione. Questo ci aiuterà a inserire contenuti nel documento.

## Fase 4: Spostamento alla fine del documento

Dobbiamo spostare il cursore del builder alla fine del documento di destinazione prima di inserire il documento di origine.

```csharp
builder.MoveToDocumentEnd();
```

In questo modo si garantisce che il documento di origine venga inserito alla fine del documento di destinazione.

## Passaggio 5: inserimento di un'interruzione di pagina

Per mantenere le cose in ordine, aggiungiamo un'interruzione di pagina prima di inserire il documento sorgente. Questo farà sì che il contenuto del documento sorgente inizi su una nuova pagina.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Un'interruzione di pagina garantisce che il contenuto del documento sorgente inizi su una nuova pagina, conferendo al documento unito un aspetto professionale.

## Passaggio 6: inserimento del documento sorgente

Adesso arriva la parte emozionante: l'inserimento effettivo del documento sorgente nel documento di destinazione.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

Utilizzando il `InsertDocument` metodo, possiamo inserire l'intero documento sorgente nel documento di destinazione. Il `ImportFormatMode.KeepSourceFormatting` garantisce che la formattazione del documento sorgente venga preservata.

## Passaggio 7: salvataggio del documento unito

Infine, salviamo il documento unito. Questo combinerà i documenti di origine e di destinazione in un unico file.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Salvando il documento, completiamo il processo di unione dei due documenti. Il nuovo documento è ora pronto e salvato nella directory specificata.

## Conclusione

Ed ecco fatto! Hai inserito correttamente un documento in un altro utilizzando Aspose.Words per .NET. Questo metodo non solo è efficiente, ma preserva anche la formattazione di entrambi i documenti, garantendo un'unione perfetta. Che tu stia lavorando a un progetto singolo o che tu abbia bisogno di automatizzare l'elaborazione dei documenti, Aspose.Words per .NET è la soluzione che fa per te.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?  
Aspose.Words per .NET è una potente libreria che consente agli sviluppatori di creare, modificare, convertire e manipolare documenti Word a livello di programmazione.

### Posso mantenere la formattazione del documento sorgente?  
Sì, utilizzando `ImportFormatMode.KeepSourceFormatting`la formattazione del documento di origine viene mantenuta quando viene inserito nel documento di destinazione.

### Ho bisogno di una licenza per utilizzare Aspose.Words per .NET?  
Sì, Aspose.Words per .NET richiede una licenza per la piena funzionalità. Puoi ottenere una [licenza temporanea](https://purchase.aspose.com/temporary-license/) per la valutazione.

### Posso automatizzare questo processo?  
Assolutamente! Il metodo descritto può essere integrato in applicazioni più ampie per automatizzare le attività di elaborazione dei documenti.

### Dove posso trovare ulteriori risorse e supporto?  
Per maggiori informazioni, puoi consultare il [documentazione](https://reference.aspose.com/words/net/), oppure visita il [forum di supporto](https://forum.aspose.com/c/words/8) per assistenza.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}