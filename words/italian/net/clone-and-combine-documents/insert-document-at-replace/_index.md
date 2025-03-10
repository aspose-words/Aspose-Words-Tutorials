---
title: Inserisci documento in sostituzione
linktitle: Inserisci documento in sostituzione
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come inserire senza problemi un documento Word in un altro usando Aspose.Words per .NET con la nostra guida dettagliata passo dopo passo. Perfetto per gli sviluppatori che vogliono semplificare l'elaborazione dei documenti.
weight: 10
url: /it/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci documento in sostituzione

## Introduzione

Ciao, maestri dei documenti! Ti sei mai trovato immerso fino alle ginocchia nel codice, cercando di capire come inserire un documento Word in un altro senza problemi? Niente paura, perché oggi ci immergiamo nel mondo di Aspose.Words per .NET per rendere questo compito un gioco da ragazzi. Ti guideremo passo dopo passo in una guida dettagliata su come usare questa potente libreria per inserire documenti in punti specifici durante un'operazione di ricerca e sostituzione. Pronti a diventare un mago di Aspose.Words? Cominciamo!

## Prerequisiti

Prima di passare al codice, ecco alcune cose che devi sapere:

-  Visual Studio: assicurati di avere Visual Studio installato sul tuo computer. Se non lo hai ancora, puoi scaricarlo da[Qui](https://visualstudio.microsoft.com/).
-  Aspose.Words per .NET: avrai bisogno della libreria Aspose.Words. Puoi ottenerla da[Sito web di Aspose](https://releases.aspose.com/words/net/).
- Conoscenze di base di C#: una conoscenza di base di C# e .NET ti aiuterà a seguire questo tutorial.

Bene, dopo aver chiarito questo punto, sporcamoci le mani con un po' di codice!

## Importazione degli spazi dei nomi

Prima di tutto, dobbiamo importare i namespace necessari per lavorare con Aspose.Words. È come raccogliere tutti gli strumenti prima di iniziare un progetto. Aggiungi queste direttive using in cima al tuo file C#:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Ora che abbiamo i nostri prerequisiti, scomponiamo il processo in piccoli passaggi. Ogni passaggio è cruciale e ci avvicinerà al nostro obiettivo.

## Passaggio 1: Impostazione della directory dei documenti

Per prima cosa, dobbiamo specificare la directory in cui sono archiviati i nostri documenti. È come preparare il palco prima della grande esibizione.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso della tua directory. È qui che i tuoi documenti vivranno e respireranno.

## Passaggio 2: caricare il documento principale

Poi, carichiamo il documento principale in cui vogliamo inserire un altro documento. Pensate a questo come al nostro palco principale in cui avverrà tutta l'azione.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Questo codice carica il documento principale dalla directory specificata.

## Passaggio 3: imposta le opzioni Trova e sostituisci

Per trovare la posizione specifica in cui vogliamo inserire il nostro documento, utilizziamo la funzionalità di ricerca e sostituzione. È come usare una mappa per trovare il punto esatto in cui inserire la nostra nuova aggiunta.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Qui impostiamo la direzione all'indietro e specifichiamo un gestore di callback personalizzato che definiremo in seguito.

## Passaggio 4: eseguire l'operazione di sostituzione

Ora diciamo al nostro documento principale di cercare uno specifico testo segnaposto e di non sostituirlo con nulla, mentre utilizziamo il nostro callback personalizzato per inserire un altro documento.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Questo codice esegue l'operazione di ricerca e sostituzione e quindi salva il documento aggiornato.

## Passaggio 5: creare un gestore di callback di sostituzione personalizzato

Il nostro gestore di callback personalizzato è dove avviene la magia. Questo gestore definirà come viene eseguito l'inserimento del documento durante l'operazione di ricerca e sostituzione.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Inserire un documento dopo il paragrafo contenente il testo corrispondente.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Rimuovi il paragrafo con il testo corrispondente.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Qui carichiamo il documento da inserire e poi chiamiamo un metodo helper per eseguire l'inserimento.

## Passaggio 6: definire il metodo di inserimento del documento

L'ultimo pezzo del nostro puzzle è il metodo che inserisce effettivamente il documento nella posizione specificata.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Controllare se la destinazione di inserimento è un paragrafo o una tabella
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Crea un NodeImporter per importare i nodi dal documento di origine
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Eseguire un ciclo attraverso tutti i nodi a livello di blocco nelle sezioni del documento sorgente
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Salta l'ultimo paragrafo vuoto di una sezione
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importa e inserisci il nodo nella destinazione
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Questo metodo si occupa di importare i nodi dal documento da inserire e di posizionarli nel punto giusto del documento principale.

## Conclusione

Ed ecco fatto! Una guida completa per inserire un documento in un altro usando Aspose.Words per .NET. Seguendo questi passaggi, puoi facilmente automatizzare le attività di assemblaggio e manipolazione dei documenti. Che tu stia creando un sistema di gestione dei documenti o che tu abbia semplicemente bisogno di semplificare il flusso di lavoro di elaborazione dei documenti, Aspose.Words è il tuo fedele compagno.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per la manipolazione programmatica di documenti Word. Consente di creare, modificare, convertire ed elaborare documenti Word con facilità.

### Posso inserire più documenti contemporaneamente?
Sì, è possibile modificare il gestore di callback per gestire più inserimenti iterando su una raccolta di documenti.

### È disponibile una prova gratuita?
 Assolutamente! Puoi scaricare una prova gratuita da[Qui](https://releases.aspose.com/).

### Come posso ottenere supporto per Aspose.Words?
 Puoi ottenere supporto visitando il[Forum di Aspose.Words](https://forum.aspose.com/c/words/8).

### Posso mantenere la formattazione del documento inserito?
 Sì, il`NodeImporter` La classe consente di specificare come gestire la formattazione durante l'importazione di nodi da un documento a un altro.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
