---
title: Mostra Nascondi segnalibri nel documento di Word
linktitle: Mostra Nascondi segnalibri nel documento di Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come mostrare o nascondere dinamicamente i segnalibri in un documento Word utilizzando Aspose.Words per .NET con la nostra guida passo passo. Perfetto per gli sviluppatori.
weight: 10
url: /it/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mostra Nascondi segnalibri nel documento di Word

## introduzione

Ti sei mai trovato a dover nascondere o mostrare dinamicamente alcune parti del tuo documento Word? Bene, sei fortunato! Con Aspose.Words per .NET, puoi gestire facilmente la visibilità dei contenuti aggiunti ai segnalibri nei tuoi documenti. Questo tutorial ti guiderà attraverso il processo di mostrare e nascondere i segnalibri in un documento Word utilizzando Aspose.Words per .NET. Analizzeremo il codice passo dopo passo, quindi che tu sia uno sviluppatore esperto o un principiante, troverai questa guida facile da seguire.

## Prerequisiti

Prima di immergerci nel codice, assicuriamoci di avere tutto ciò di cui hai bisogno:

1.  Aspose.Words per .NET: assicurati di aver installato la libreria Aspose.Words per .NET. In caso contrario, puoi scaricarlo[Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: un IDE come Visual Studio.
3. Conoscenza di base di C#: la familiarità con la programmazione C# sarà utile.
4. Un documento Word: un documento Word di esempio con segnalibri.

## Importa spazi dei nomi

Prima di iniziare con il codice, è necessario importare gli spazi dei nomi necessari. Aggiungi quanto segue all'inizio del file C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Passaggio 1: carica il documento

Per prima cosa, devi caricare il documento Word che contiene i segnalibri. Ecco come puoi farlo:

```csharp
// Il percorso della directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Spiegazione

- dataDir: questo è il percorso della directory in cui si trova il documento Word.
-  Documento doc: inizializza una nuova istanza del file`Document` class con il file specificato.

## Passaggio 2: mostra o nascondi il contenuto dei segnalibri

Successivamente, definiremo un metodo per mostrare o nascondere il contenuto dei segnalibri. Ecco il metodo completo:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD segnalibro}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Spiegazione

- Segnalibro bm: recupera il segnalibro dal documento.
- Generatore DocumentBuilder: aiuta a navigare e modificare il documento.
- Campo campo: inserisce un campo IF per verificare le condizioni del segnalibro.
- Nodo currentNode: attraversa i nodi per trovare l'inizio e la fine del campo.

## Passaggio 3: eseguire la funzione Mostra/Nascondi

 Ora devi chiamare il`ShowHideBookmarkedContent` metodo, passando il documento, il nome del segnalibro e il flag di visibilità:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Spiegazione

- doc: il tuo oggetto documento.
- "MyBookmark1": il nome del segnalibro che desideri mostrare/nascondere.
- false: il flag di visibilità (true per mostrare, false per nascondere).

## Passaggio 4: salva il documento

Infine, salva il documento modificato:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Spiegazione

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": il percorso e il nome del nuovo documento in cui verranno salvate le modifiche.

## Conclusione

E il gioco è fatto! Hai imparato con successo come mostrare e nascondere i segnalibri in un documento Word utilizzando Aspose.Words per .NET. Questa tecnica può essere incredibilmente utile per generare dinamicamente documenti con contenuto condizionale.

## Domande frequenti

### Cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria di elaborazione documenti che consente agli sviluppatori di creare, modificare e convertire documenti Word a livello di codice.

### Come posso ottenere Aspose.Words per .NET?
 È possibile scaricare Aspose.Words per .NET da[Qui](https://releases.aspose.com/words/net/). È disponibile anche una prova gratuita.

### Posso utilizzare questo metodo per altri tipi di segnalibri?
Sì, questo metodo può essere adattato per gestire la visibilità di eventuali segnalibri nel documento Word.

### Cosa succede se il mio documento non contiene il segnalibro specificato?
Se il segnalibro non esiste, il metodo genererà un errore. Assicurarsi che il segnalibro esista prima di tentare di mostrarlo/nasconderlo.

### Come posso ottenere supporto se riscontro problemi?
 Puoi ottenere supporto dalla comunità Aspose[Qui](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
