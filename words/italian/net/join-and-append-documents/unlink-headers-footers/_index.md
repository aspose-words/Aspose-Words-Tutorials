---
title: Scollega intestazioni piè di pagina
linktitle: Scollega intestazioni piè di pagina
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come scollegare intestazioni e piè di pagina nei documenti Word usando Aspose.Words per .NET. Segui la nostra guida dettagliata, passo dopo passo, per padroneggiare la manipolazione dei documenti.
weight: 10
url: /it/net/join-and-append-documents/unlink-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Scollega intestazioni piè di pagina

## Introduzione

Nel mondo dell'elaborazione dei documenti, mantenere intestazioni e piè di pagina coerenti può a volte essere una sfida. Che tu stia unendo documenti o semplicemente cercando di avere intestazioni e piè di pagina diversi per sezioni diverse, sapere come scollegarli è essenziale. Oggi, ci immergeremo in come puoi ottenere questo risultato usando Aspose.Words per .NET. Lo spiegheremo passo dopo passo in modo che tu possa seguire facilmente. Pronti a padroneggiare la manipolazione dei documenti? Cominciamo!

## Prerequisiti

Prima di addentrarci nei dettagli, ecco alcune cose di cui avrai bisogno:

-  Aspose.Words per la libreria .NET: puoi scaricarla da[Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
- .NET Framework: assicurati di aver installato un framework .NET compatibile.
- IDE: Visual Studio o qualsiasi altro ambiente di sviluppo integrato compatibile con .NET.
- Conoscenze di base di C#: è necessaria una conoscenza di base del linguaggio di programmazione C#.

## Importazione degli spazi dei nomi

Per iniziare, assicurati di importare i namespace necessari nel tuo progetto. Questo ti consentirà di accedere alla libreria Aspose.Words e alle sue funzionalità.

```csharp
using Aspose.Words;
```

Per aiutarti a scollegare intestazioni e piè di pagina nei tuoi documenti Word, scomponiamo il processo in passaggi gestibili.

## Passaggio 1: imposta il tuo progetto

Per prima cosa, dovrai impostare l'ambiente del tuo progetto. Apri il tuo IDE e crea un nuovo progetto .NET. Aggiungi un riferimento alla libreria Aspose.Words che hai scaricato in precedenza.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: caricare il documento sorgente

Successivamente, devi caricare il documento sorgente che vuoi modificare. Questo documento avrà le sue intestazioni e piè di pagina non collegati.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Passaggio 3: caricare il documento di destinazione

Ora carica il documento di destinazione in cui aggiungerai il documento sorgente dopo averne scollegato intestazioni e piè di pagina.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Passaggio 4: scollegare intestazioni e piè di pagina

 Questo passaggio è cruciale. Per scollegare le intestazioni e i piè di pagina del documento di origine da quelli del documento di destinazione, utilizzerai il`LinkToPrevious` metodo. Questo metodo assicura che le intestazioni e i piè di pagina non vengano trasferiti al documento allegato.

```csharp
// Scollegare le intestazioni e i piè di pagina nel documento di origine per interrompere questa operazione
//dal continuare le intestazioni e i piè di pagina del documento di destinazione.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Passaggio 5: aggiungere il documento sorgente

 Dopo aver scollegato le intestazioni e i piè di pagina, puoi aggiungere il documento sorgente al documento di destinazione. Utilizza il`AppendDocument` metodo e imposta la modalità del formato di importazione su`KeepSourceFormatting` per mantenere la formattazione originale del documento sorgente.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Passaggio 6: Salvare il documento finale

Infine, salva il documento appena creato. Questo documento avrà il contenuto del documento sorgente aggiunto al documento di destinazione, con le intestazioni e i piè di pagina non collegati.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, hai scollegato con successo le intestazioni e i piè di pagina nel tuo documento sorgente e li hai aggiunti al tuo documento di destinazione usando Aspose.Words per .NET. Questa tecnica può essere particolarmente utile quando lavori con documenti complessi che richiedono intestazioni e piè di pagina diversi per sezioni diverse. Buona codifica!

## Domande frequenti

### Che cos'è Aspose.Words per .NET?  
Aspose.Words per .NET è una potente libreria per lavorare con documenti Word in applicazioni .NET. Consente agli sviluppatori di creare, modificare, convertire e stampare documenti in modo programmatico.

### Posso scollegare intestazioni e piè di pagina solo per sezioni specifiche?  
 Sì, puoi scollegare intestazioni e piè di pagina per sezioni specifiche accedendo a`HeadersFooters` proprietà della sezione desiderata e utilizzando il`LinkToPrevious` metodo.

### È possibile mantenere la formattazione originale del documento sorgente?  
 Sì, quando si aggiunge il documento sorgente, utilizzare`ImportFormatMode.KeepSourceFormatting` opzione per mantenere la formattazione originale.

### Posso usare Aspose.Words per .NET con altri linguaggi .NET oltre a C#?  
Assolutamente! Aspose.Words per .NET può essere utilizzato con qualsiasi linguaggio .NET, inclusi VB.NET e F#.

### Dove posso trovare ulteriore documentazione e supporto per Aspose.Words per .NET?  
 Puoi trovare una documentazione completa su[Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/) e il supporto è disponibile su[Forum di Aspose](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
