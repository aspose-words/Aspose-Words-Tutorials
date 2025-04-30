---
"description": "Scopri come scollegare intestazioni e piè di pagina nei documenti Word utilizzando Aspose.Words per .NET. Segui la nostra guida dettagliata e passo passo per padroneggiare la manipolazione dei documenti."
"linktitle": "Scollega intestazioni e piè di pagina"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Scollega intestazioni e piè di pagina"
"url": "/it/net/join-and-append-documents/unlink-headers-footers/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Scollega intestazioni e piè di pagina

## Introduzione

Nel mondo dell'elaborazione dei documenti, mantenere intestazioni e piè di pagina coerenti può a volte essere una sfida. Che si tratti di unire documenti o semplicemente di avere intestazioni e piè di pagina diversi per sezioni diverse, sapere come scollegarli è essenziale. Oggi approfondiremo come ottenere questo risultato utilizzando Aspose.Words per .NET. Lo spiegheremo passo dopo passo in modo che possiate seguirlo facilmente. Pronti a padroneggiare la manipolazione dei documenti? Iniziamo!

## Prerequisiti

Prima di addentrarci nei dettagli, ecco alcune cose di cui avrai bisogno:

- Aspose.Words per la libreria .NET: puoi scaricarla da [Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
- .NET Framework: assicurati di aver installato un framework .NET compatibile.
- IDE: Visual Studio o qualsiasi altro ambiente di sviluppo integrato compatibile con .NET.
- Nozioni di base di C#: è necessaria una conoscenza di base del linguaggio di programmazione C#.

## Importa spazi dei nomi

Per iniziare, assicurati di importare gli spazi dei nomi necessari nel tuo progetto. Questo ti permetterà di accedere alla libreria Aspose.Words e alle sue funzionalità.

```csharp
using Aspose.Words;
```

Per aiutarti a scollegare intestazioni e piè di pagina nei tuoi documenti Word, scomponiamo il processo in passaggi gestibili.

## Passaggio 1: imposta il tuo progetto

Per prima cosa, devi configurare l'ambiente del progetto. Apri l'IDE e crea un nuovo progetto .NET. Aggiungi un riferimento alla libreria Aspose.Words scaricata in precedenza.

```csharp
// Percorso alla directory dei documenti 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: caricare il documento sorgente

Successivamente, è necessario caricare il documento sorgente che si desidera modificare. Intestazioni e piè di pagina di questo documento saranno scollegati.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Passaggio 3: caricare il documento di destinazione

Adesso carica il documento di destinazione in cui aggiungerai il documento sorgente dopo averne scollegato intestazioni e piè di pagina.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Passaggio 4: scollegare intestazioni e piè di pagina

Questo passaggio è fondamentale. Per scollegare le intestazioni e i piè di pagina del documento di origine da quelli del documento di destinazione, utilizzerai il `LinkToPrevious` metodo. Questo metodo garantisce che le intestazioni e i piè di pagina non vengano trasferiti al documento allegato.

```csharp
// Scollegare le intestazioni e i piè di pagina nel documento di origine per interrompere questo
// dal continuare le intestazioni e i piè di pagina del documento di destinazione.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Passaggio 5: aggiungere il documento sorgente

Dopo aver scollegato intestazioni e piè di pagina, è possibile aggiungere il documento di origine al documento di destinazione. Utilizzare il `AppendDocument` metodo e imposta la modalità di formato di importazione su `KeepSourceFormatting` per mantenere la formattazione originale del documento sorgente.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Passaggio 6: Salvare il documento finale

Infine, salva il documento appena creato. Questo documento avrà il contenuto del documento di origine aggiunto al documento di destinazione, con intestazioni e piè di pagina scollegati.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, hai scollegato con successo intestazioni e piè di pagina dal documento sorgente e li hai aggiunti al documento di destinazione utilizzando Aspose.Words per .NET. Questa tecnica può essere particolarmente utile quando si lavora con documenti complessi che richiedono intestazioni e piè di pagina diversi per sezioni diverse. Buona scrittura!

## Domande frequenti

### Che cos'è Aspose.Words per .NET?  
Aspose.Words per .NET è una potente libreria per lavorare con documenti Word nelle applicazioni .NET. Consente agli sviluppatori di creare, modificare, convertire e stampare documenti a livello di codice.

### Posso scollegare intestazioni e piè di pagina solo per sezioni specifiche?  
Sì, puoi scollegare intestazioni e piè di pagina per sezioni specifiche accedendo a `HeadersFooters` proprietà della sezione desiderata e utilizzando il `LinkToPrevious` metodo.

### È possibile mantenere la formattazione originale del documento sorgente?  
Sì, quando si aggiunge il documento sorgente, utilizzare `ImportFormatMode.KeepSourceFormatting` opzione per mantenere la formattazione originale.

### Posso utilizzare Aspose.Words per .NET con altri linguaggi .NET oltre a C#?  
Assolutamente! Aspose.Words per .NET può essere utilizzato con qualsiasi linguaggio .NET, inclusi VB.NET e F#.

### Dove posso trovare ulteriore documentazione e supporto per Aspose.Words per .NET?  
Puoi trovare una documentazione completa su [Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/)e il supporto è disponibile su [Forum di Aspose](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}