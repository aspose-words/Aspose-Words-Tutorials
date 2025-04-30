---
"description": "Scopri come mostrare e nascondere il contenuto aggiunto ai segnalibri nei documenti Word utilizzando Aspose.Words per .NET con questa guida dettagliata e passo dopo passo."
"linktitle": "Mostra Nascondi contenuto aggiunto ai segnalibri nel documento Word"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Mostra Nascondi contenuto aggiunto ai segnalibri nel documento Word"
"url": "/it/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mostra Nascondi contenuto aggiunto ai segnalibri nel documento Word

## Introduzione

Pronti a immergervi nel mondo della manipolazione dei documenti con Aspose.Words per .NET? Che siate sviluppatori che desiderano automatizzare le attività relative ai documenti o semplicemente curiosi di imparare a gestire i file Word a livello di codice, siete nel posto giusto. Oggi esploreremo come mostrare e nascondere il contenuto con segnalibri in un documento Word utilizzando Aspose.Words per .NET. Questa guida passo passo vi aiuterà a diventare esperti nel controllo della visibilità dei contenuti in base ai segnalibri. Iniziamo!

## Prerequisiti

Prima di entrare nei dettagli, ecco alcune cose di cui avrai bisogno:

1. Visual Studio: qualsiasi versione compatibile con .NET.
2. Aspose.Words per .NET: scaricalo [Qui](https://releases.aspose.com/words/net/).
3. Conoscenza di base di C#: se riesci a scrivere un semplice programma "Hello World", sei a posto.
4. Un documento Word con segnalibri: per questo tutorial utilizzeremo un documento di esempio con segnalibri.

## Importa spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo ci assicura di avere tutti gli strumenti necessari per il nostro compito.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Una volta definiti questi namespace, siamo pronti per iniziare il nostro viaggio.

## Passaggio 1: impostazione del progetto

Bene, cominciamo configurando il nostro progetto in Visual Studio.

### Crea un nuovo progetto

Apri Visual Studio e crea un nuovo progetto di app console (.NET Core). Assegnagli un nome accattivante, come "BookmarkVisibilityManager".

### Aggiungi Aspose.Words per .NET

Dovrai aggiungere Aspose.Words per .NET al tuo progetto. Puoi farlo tramite NuGet Package Manager.

1. Vai a Strumenti > Gestore pacchetti NuGet > Gestisci pacchetti NuGet per la soluzione.
2. Cerca "Aspose.Words".
3. Installa il pacchetto.

Ottimo! Ora che il nostro progetto è impostato, passiamo al caricamento del documento.

## Passaggio 2: caricamento del documento

Dobbiamo caricare il documento Word che contiene i segnalibri. Per questo tutorial, useremo un documento di esempio denominato "Segnalibri.docx".

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Questo frammento di codice imposta il percorso alla directory del documento e carica il documento nella `doc` oggetto.

## Passaggio 3: Mostra/Nascondi il contenuto aggiunto ai segnalibri

Ora arriva la parte divertente: mostrare o nascondere il contenuto in base ai segnalibri. Creeremo un metodo chiamato `ShowHideBookmarkedContent` per gestire la situazione.

Ecco il metodo che attiverà o disattivarà la visibilità dei contenuti aggiunti ai preferiti:

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

### Analisi del metodo

- Recupero segnalibro: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` recupera il segnalibro.
- Attraversamento dei nodi: attraversiamo i nodi all'interno del segnalibro.
- Attiva/disattiva visibilità: se il nodo è un `Run` (una sequenza contigua di testo), impostiamo il suo `Hidden` proprietà.

## Fase 4: Applicazione del metodo

Con il nostro metodo in atto, applichiamolo per mostrare o nascondere contenuti in base a un segnalibro.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Questa riga di codice nasconderà il contenuto del segnalibro denominato "MyBookmark1".

## Passaggio 5: salvataggio del documento

Infine, salviamo il documento modificato.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

In questo modo il documento verrà salvato con le modifiche apportate.

## Conclusione

Ed ecco fatto! Hai appena imparato come mostrare e nascondere il contenuto dei segnalibri in un documento Word utilizzando Aspose.Words per .NET. Questo potente strumento semplifica la manipolazione dei documenti, sia che tu stia automatizzando report, creando modelli o semplicemente modificando i file Word. Buona programmazione!

## Domande frequenti

### Posso attivare/disattivare più segnalibri contemporaneamente?
Sì, puoi chiamare il `ShowHideBookmarkedContent` metodo per ogni segnalibro che vuoi attivare/disattivare.

### Nascondere il contenuto influisce sulla struttura del documento?
No, nascondere un contenuto ne compromette solo la visibilità. Il contenuto rimane nel documento.

### Posso usare questo metodo per altri tipi di contenuti?
Questo metodo attiva/disattiva specificamente l'esecuzione del testo. Per altri tipi di contenuto, è necessario modificare la logica di attraversamento dei nodi.

### Aspose.Words per .NET è gratuito?
Aspose.Words offre una prova gratuita [Qui](https://releases.aspose.com/), ma è necessaria una licenza completa per l'uso in produzione. Puoi acquistarla [Qui](https://purchase.aspose.com/buy).

### Come posso ottenere supporto se riscontro problemi?
Puoi ottenere supporto dalla community Aspose [Qui](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}