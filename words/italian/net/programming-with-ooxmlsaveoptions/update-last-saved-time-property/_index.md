---
"description": "Scopri come aggiornare la proprietà \"Ultimo salvataggio\" nei documenti Word utilizzando Aspose.Words per .NET. Segui la nostra guida dettagliata e passo passo."
"linktitle": "Aggiorna proprietà dell'ora dell'ultimo salvataggio"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Aggiorna proprietà dell'ora dell'ultimo salvataggio"
"url": "/it/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiorna proprietà dell'ora dell'ultimo salvataggio

## Introduzione

Vi siete mai chiesti come tenere traccia della proprietà "Ultimo salvataggio" nei vostri documenti Word a livello di codice? Se avete a che fare con più documenti e dovete gestirne i metadati, aggiornare la proprietà "Ultimo salvataggio" può essere molto utile. Oggi vi guiderò in questo processo utilizzando Aspose.Words per .NET. Quindi, allacciate le cinture e iniziamo!

## Prerequisiti

Prima di passare alla guida dettagliata, ecco alcune cose di cui avrai bisogno:

1. Aspose.Words per .NET: assicurati di aver installato Aspose.Words per .NET. In caso contrario, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: un ambiente di sviluppo come Visual Studio.
3. Conoscenza di base di C#: sarà utile comprendere le basi della programmazione C#.

## Importa spazi dei nomi

Per iniziare, assicurati di importare gli spazi dei nomi necessari nel tuo progetto. Questo ti permetterà di accedere alle classi e ai metodi necessari per la manipolazione dei documenti Word.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ora, scomponiamo il processo in semplici passaggi. Ogni passaggio ti guiderà attraverso l'aggiornamento della proprietà "Ultimo salvataggio" nel tuo documento Word.

## Passaggio 1: imposta la directory dei documenti

Per prima cosa, devi specificare il percorso della directory del documento. Qui è dove è archiviato il documento esistente e dove verrà salvato il documento aggiornato.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Sostituire `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo della tua directory.

## Passaggio 2: carica il documento Word

Successivamente, carica il documento Word che desideri aggiornare. Puoi farlo creando un'istanza di `Document` classe e passando il percorso del documento.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Assicurarsi che il documento denominato `Document.docx` è presente nella directory specificata.

## Passaggio 3: configurare le opzioni di salvataggio

Ora, crea un'istanza di `OoxmlSaveOptions` classe. Questa classe consente di specificare le opzioni per il salvataggio del documento nel formato Office Open XML (OOXML). Qui, imposterai `UpdateLastSavedTimeProperty` A `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

In questo modo si indica ad Aspose.Words di aggiornare l'ultima proprietà di salvataggio del documento.

## Passaggio 4: salvare il documento aggiornato

Infine, salva il documento utilizzando il `Save` metodo del `Document` classe, passando il percorso in cui si desidera salvare il documento aggiornato e le opzioni di salvataggio.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

In questo modo il documento verrà salvato con l'ultima proprietà di salvataggio aggiornata.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi aggiornare facilmente la proprietà "Ultimo salvataggio" dei tuoi documenti Word utilizzando Aspose.Words per .NET. Questo è particolarmente utile per mantenere metadati accurati nei documenti, il che può essere fondamentale per i sistemi di gestione dei documenti e diverse altre applicazioni.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per creare, modificare e convertire documenti Word nelle applicazioni .NET.

### Perché dovrei aggiornare l'ultima proprietà di ora salvata?
L'aggiornamento della proprietà relativa all'ora dell'ultimo salvataggio aiuta a mantenere metadati accurati, essenziali per il monitoraggio e la gestione dei documenti.

### Posso aggiornare altre proprietà utilizzando Aspose.Words per .NET?
Sì, Aspose.Words per .NET consente di aggiornare varie proprietà del documento, come titolo, autore e oggetto.

### Aspose.Words per .NET è gratuito?
Aspose.Words per .NET offre una prova gratuita, ma per usufruire di tutte le funzionalità è necessaria una licenza. È possibile ottenere una licenza. [Qui](https://purchase.aspose.com/buy).

### Dove posso trovare altri tutorial su Aspose.Words per .NET?
Puoi trovare altri tutorial e documentazione [Qui](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}