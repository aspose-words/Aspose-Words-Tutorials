---
"description": "Scopri come aggiungere e configurare i riquadri attività delle estensioni Web nei documenti Word utilizzando Aspose.Words per .NET in questo tutorial dettagliato e passo dopo passo."
"linktitle": "Utilizzo dei riquadri attività dell'estensione Web"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Utilizzo dei riquadri attività dell'estensione Web"
"url": "/it/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo dei riquadri attività dell'estensione Web

## Introduzione

Benvenuti a questo tutorial approfondito sull'utilizzo dei riquadri attività delle estensioni Web in un documento Word con Aspose.Words per .NET. Se avete mai desiderato arricchire i vostri documenti Word con riquadri attività interattivi, siete nel posto giusto. Questa guida vi guiderà passo dopo passo per raggiungere questo obiettivo senza problemi.

## Prerequisiti

Prima di iniziare, assicuriamoci di avere tutto ciò di cui hai bisogno:

- Aspose.Words per .NET: puoi scaricarlo [Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo .NET: Visual Studio o qualsiasi altro IDE di tua preferenza.
- Conoscenza di base di C#: ti aiuterà a seguire gli esempi di codice.
- Licenza per Aspose.Words: puoi acquistarne una [Qui](https://purchase.aspose.com/buy) o ottenere una licenza temporanea [Qui](https://purchase.aspose.com/temporary-license/).

## Importa spazi dei nomi

Prima di iniziare a scrivere il codice, assicurati di aver importato i seguenti namespace nel tuo progetto:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Guida passo passo

Ora scomponiamo il processo in passaggi facili da seguire.

### Passaggio 1: impostazione della directory dei documenti

Per prima cosa, dobbiamo impostare il percorso per la directory dei documenti. È qui che verrà salvato il documento Word.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Sostituire `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo della cartella dei documenti.

### Passaggio 2: creazione di un nuovo documento

Successivamente creeremo un nuovo documento Word utilizzando Aspose.Words.

```csharp
Document doc = new Document();
```

Questa riga inizializza una nuova istanza di `Document` classe, che rappresenta un documento Word.

### Passaggio 3: aggiunta di un riquadro attività

Ora aggiungeremo un riquadro attività al nostro documento. I riquadri attività sono utili per fornire funzionalità e strumenti aggiuntivi all'interno di un documento Word.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

Qui creiamo un nuovo `TaskPane` oggetto e aggiungerlo al documento `WebExtensionTaskPanes` collezione.

### Passaggio 4: configurazione del riquadro attività

Per rendere visibile il nostro Task Pane e impostarne le proprietà, utilizziamo il seguente codice:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` Imposta dove verrà visualizzato il Riquadro Attività. In questo caso, è a destra.
- `IsVisible` assicura che il riquadro attività sia visibile.
- `Width` imposta la larghezza del riquadro attività.

### Passaggio 5: impostazione del riferimento all'estensione Web

Successivamente, impostiamo il riferimento all'estensione Web che include ID, versione, tipo di archivio e archivio.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` è un identificatore univoco per l'estensione web.
- `Version` specifica la versione dell'estensione.
- `StoreType` indica il tipo di negozio (in questo caso, OMEX).
- `Store` specifica il codice lingua/cultura del negozio.

### Passaggio 6: aggiunta di proprietà all'estensione Web

Puoi aggiungere proprietà alla tua estensione web per definirne il comportamento o il contenuto.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

Qui aggiungiamo una proprietà denominata `mailchimpCampaign`.

### Passaggio 7: associazione dell'estensione Web

Infine, aggiungiamo dei collegamenti alla nostra estensione web. I collegamenti consentono di collegare l'estensione a parti specifiche del documento.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` è il nome della rilegatura.
- `WebExtensionBindingType.Text` indica che la rilegatura è di tipo testo.
- `194740422` è l'ID della parte del documento a cui è associata l'estensione.

### Passaggio 8: salvataggio del documento

Dopo aver impostato tutto, salva il documento.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Questa riga salva il documento nella directory specificata con il nome file indicato.

### Passaggio 9: caricamento e visualizzazione delle informazioni del riquadro attività

Per verificare e visualizzare le informazioni del riquadro attività, carichiamo il documento e scorriamo i riquadri attività.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Questo codice carica il documento e stampa il provider, la versione e l'identificatore del catalogo di ciascun riquadro attività nella console.

## Conclusione

Ecco fatto! Hai aggiunto e configurato correttamente un riquadro attività di estensione Web in un documento Word utilizzando Aspose.Words per .NET. Questa potente funzionalità può migliorare significativamente i tuoi documenti Word fornendo funzionalità aggiuntive direttamente al loro interno. 

## Domande frequenti

### Che cos'è un riquadro attività in Word?
Un riquadro attività è un elemento dell'interfaccia che fornisce strumenti e funzionalità aggiuntivi all'interno di un documento Word, migliorando l'interazione e la produttività dell'utente.

### Posso personalizzare l'aspetto del riquadro attività?
Sì, puoi personalizzare l'aspetto del riquadro attività impostando proprietà come `DockState`, `IsVisible`, E `Width`.

### Cosa sono le proprietà delle estensioni Web?
Le proprietà dell'estensione web sono proprietà personalizzate che puoi aggiungere a un'estensione web per definirne il comportamento o il contenuto.

### Come posso associare un'estensione Web a una parte del documento?
È possibile associare un'estensione Web a una parte del documento utilizzando `WebExtensionBinding` classe, specificando il tipo di binding e l'ID di destinazione.

### Dove posso trovare maggiori informazioni su Aspose.Words per .NET?
Puoi trovare la documentazione dettagliata [Qui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}