---
title: Mostra Nascondi Contenuto Segnalibro Nel Documento Word
linktitle: Mostra Nascondi Contenuto Segnalibro Nel Documento Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come mostrare e nascondere il contenuto aggiunto ai segnalibri nei documenti Word utilizzando Aspose.Words per .NET con questa guida dettagliata e dettagliata.
weight: 10
url: /it/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mostra Nascondi Contenuto Segnalibro Nel Documento Word

## Introduzione

Pronti a tuffarvi nel mondo della manipolazione dei documenti con Aspose.Words per .NET? Che siate uno sviluppatore che cerca di automatizzare le attività sui documenti o semplicemente qualcuno curioso di gestire i file Word a livello di programmazione, siete nel posto giusto. Oggi esploreremo come mostrare e nascondere il contenuto con segnalibri in un documento Word utilizzando Aspose.Words per .NET. Questa guida passo passo vi renderà dei professionisti nel controllo della visibilità dei contenuti in base ai segnalibri. Cominciamo!

## Prerequisiti

Prima di entrare nei dettagli, ecco alcune cose di cui avrai bisogno:

1. Visual Studio: qualsiasi versione compatibile con .NET.
2.  Aspose.Words per .NET: Scaricalo[Qui](https://releases.aspose.com/words/net/).
3. Nozioni di base di C#: se riesci a scrivere un semplice programma "Hello World", sei a posto.
4. Un documento Word con segnalibri: per questo tutorial utilizzeremo un documento di esempio con segnalibri.

## Importazione degli spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo ci assicura di avere tutti gli strumenti di cui abbiamo bisogno per il nostro compito.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Una volta definiti questi namespace, siamo pronti per iniziare il nostro viaggio.

## Fase 1: Impostazione del progetto

Bene, cominciamo configurando il nostro progetto in Visual Studio.

### Crea un nuovo progetto

Apri Visual Studio e crea un nuovo progetto Console App (.NET Core). Assegnagli un nome accattivante, come "BookmarkVisibilityManager".

### Aggiungi Aspose.Words per .NET

Dovrai aggiungere Aspose.Words per .NET al tuo progetto. Puoi farlo tramite NuGet Package Manager.

1. Vai su Strumenti > Gestore pacchetti NuGet > Gestisci pacchetti NuGet per la soluzione.
2. Cerca "Aspose.Words".
3. Installa il pacchetto.

Ottimo! Ora che il nostro progetto è impostato, passiamo al caricamento del nostro documento.

## Fase 2: Caricamento del documento

Dobbiamo caricare il documento Word che contiene i segnalibri. Per questo tutorial, useremo un documento di esempio denominato "Bookmarks.docx".

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Questo frammento di codice imposta il percorso alla directory del documento e carica il documento nella`doc` oggetto.

## Passaggio 3: Mostra/Nascondi il contenuto aggiunto ai segnalibri

Ora arriva la parte divertente: mostrare o nascondere il contenuto in base ai segnalibri. Creeremo un metodo chiamato`ShowHideBookmarkedContent` per gestire la situazione.

Ecco il metodo che attiverà o disattiva la visibilità dei contenuti aggiunti ai preferiti:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Ripartizione del metodo

-  Recupero segnalibro:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` recupera il segnalibro.
- Attraversamento dei nodi: attraversiamo i nodi all'interno del segnalibro.
-  Attiva/disattiva visibilità: se il nodo è un`Run` (una sequenza contigua di testo), impostiamo il suo`Hidden` proprietà.

## Fase 4: applicazione del metodo

Con il nostro metodo in atto, applichiamolo per mostrare o nascondere i contenuti in base a un segnalibro.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Questa riga di codice nasconderà il contenuto del segnalibro denominato "MyBookmark1".

## Passaggio 5: salvataggio del documento

Infine, salviamo il nostro documento modificato.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

In questo modo il documento verrà salvato con le modifiche apportate.

## Conclusione

Ed ecco fatto! Hai appena imparato come mostrare e nascondere i contenuti con segnalibro in un documento Word usando Aspose.Words per .NET. Questo potente strumento semplifica la manipolazione dei documenti, sia che tu stia automatizzando report, creando modelli o semplicemente armeggiando con i file Word. Buona codifica!

## Domande frequenti

### Posso attivare/disattivare più segnalibri contemporaneamente?
 Sì, puoi chiamare il`ShowHideBookmarkedContent` metodo per ogni segnalibro che vuoi attivare/disattivare.

### Nascondere il contenuto influisce sulla struttura del documento?
No, nascondere il contenuto influisce solo sulla sua visibilità. Il contenuto rimane nel documento.

### Posso usare questo metodo per altri tipi di contenuti?
Questo metodo commuta specificamente le esecuzioni di testo. Per altri tipi di contenuto, dovrai modificare la logica di attraversamento del nodo.

### Aspose.Words per .NET è gratuito?
 Aspose.Words offre una prova gratuita[Qui](https://releases.aspose.com/) , ma è richiesta una licenza completa per l'uso in produzione. Puoi acquistarla[Qui](https://purchase.aspose.com/buy).

### Come posso ottenere supporto se riscontro problemi?
 Puoi ottenere supporto dalla comunità Aspose[Qui](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
