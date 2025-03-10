---
title: Aggiorna proprietà ultima ora salvata
linktitle: Aggiorna proprietà ultima ora salvata
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come aggiornare la proprietà dell'ultimo orario salvato nei documenti Word usando Aspose.Words per .NET. Segui la nostra guida dettagliata, passo dopo passo.
weight: 10
url: /it/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiorna proprietà ultima ora salvata

## Introduzione

Ti sei mai chiesto come tenere traccia della proprietà dell'ultimo orario salvato nei tuoi documenti Word a livello di programmazione? Se hai a che fare con più documenti e devi mantenerne i metadati, aggiornare la proprietà dell'ultimo orario salvato può essere molto utile. Oggi ti guiderò attraverso questo processo usando Aspose.Words per .NET. Quindi, allaccia le cinture e tuffiamoci!

## Prerequisiti

Prima di passare alla guida dettagliata, ecco alcune cose di cui avrai bisogno:

1.  Aspose.Words per .NET: assicurati di avere Aspose.Words per .NET installato. Se non lo hai, puoi[scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: un ambiente di sviluppo come Visual Studio.
3. Conoscenza di base di C#: sarà utile comprendere le basi della programmazione in C#.

## Importazione degli spazi dei nomi

Per iniziare, assicurati di importare i namespace necessari nel tuo progetto. Ciò ti consentirà di accedere alle classi e ai metodi richiesti per manipolare i documenti Word.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ora, scomponiamo il processo in semplici passaggi. Ogni passaggio ti guiderà attraverso il processo di aggiornamento della proprietà dell'ultimo orario salvato nel tuo documento Word.

## Passaggio 1: imposta la directory dei documenti

Per prima cosa, devi specificare il percorso della directory del tuo documento. È qui che è archiviato il tuo documento esistente e dove verrà salvato il documento aggiornato.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo della tua directory.

## Passaggio 2: carica il documento Word

 Quindi, carica il documento Word che vuoi aggiornare. Puoi farlo creando un'istanza di`Document` classe e passando il percorso del documento.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

 Assicurarsi che il documento denominato`Document.docx` è presente nella directory specificata.

## Passaggio 3: Configurare le opzioni di salvataggio

 Ora, crea un'istanza di`OoxmlSaveOptions` classe. Questa classe consente di specificare le opzioni per salvare il documento nel formato Office Open XML (OOXML). Qui, imposterai la`UpdateLastSavedTimeProperty` A`true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Questo indica ad Aspose.Words di aggiornare l'ultima proprietà di ora salvata del documento.

## Passaggio 4: salvare il documento aggiornato

 Infine, salva il documento utilizzando il`Save` metodo del`Document` classe, passando il percorso in cui si desidera salvare il documento aggiornato e le opzioni di salvataggio.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

In questo modo il documento verrà salvato con la proprietà aggiornata relativa all'ultimo salvataggio.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi aggiornare facilmente la proprietà dell'ultimo orario salvato dei tuoi documenti Word usando Aspose.Words per .NET. Ciò è particolarmente utile per mantenere metadati accurati nei tuoi documenti, il che può essere cruciale per i sistemi di gestione dei documenti e varie altre applicazioni.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per creare, modificare e convertire documenti Word nelle applicazioni .NET.

### Perché dovrei aggiornare l'ultima proprietà di ora salvata?
L'aggiornamento della proprietà relativa all'ora dell'ultimo salvataggio aiuta a mantenere metadati accurati, essenziali per il monitoraggio e la gestione dei documenti.

### Posso aggiornare altre proprietà utilizzando Aspose.Words per .NET?
Sì, Aspose.Words per .NET consente di aggiornare varie proprietà del documento, come titolo, autore e oggetto.

### Aspose.Words per .NET è gratuito?
 Aspose.Words per .NET offre una prova gratuita, ma per la piena funzionalità è richiesta una licenza. È possibile ottenere una licenza[Qui](https://purchase.aspose.com/buy).

### Dove posso trovare altri tutorial su Aspose.Words per .NET?
Puoi trovare altri tutorial e documentazione[Qui](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
