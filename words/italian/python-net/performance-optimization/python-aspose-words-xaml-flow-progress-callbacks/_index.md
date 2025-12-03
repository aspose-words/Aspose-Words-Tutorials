{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
---
"date": "2025-03-29"
"description": "Scopri come ottimizzare il salvataggio dei documenti con Aspose.Words per Python utilizzando il formato di flusso XAML e le callback di avanzamento. Migliora l'efficienza nella gestione dei documenti."
"title": "Ottimizzazione del salvataggio dei documenti in Python - Callback di flusso e avanzamento XAML di Aspose.Words"
"url": "/it/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---

# Come ottimizzare il salvataggio dei documenti in Python utilizzando Aspose.Words: callback di flusso e avanzamento XAML

## Introduzione

Desideri gestire in modo efficiente la conversione dei documenti utilizzando Python? Hai difficoltà a gestire le immagini e a monitorare l'avanzamento durante il salvataggio dei documenti? Questo tutorial ti guiderà nell'ottimizzazione del salvataggio dei documenti con Aspose.Words per Python, concentrandosi su due potenti funzionalità: `XamlFlowSaveOptions` con cartella immagini e callback di avanzamento del salvataggio del documento.

Questa guida completa è perfetta per gli sviluppatori che desiderano migliorare i flussi di lavoro di elaborazione dei documenti utilizzando la libreria Aspose.Words.

**Cosa imparerai:**
- Come salvare un documento nel formato di flusso XAML durante la gestione delle risorse immagine.
- Implementazione di callback di avanzamento durante il salvataggio dei documenti per evitare operazioni lunghe.
- Impostazione e configurazione di Aspose.Words per Python nel tuo ambiente di sviluppo.
- Applicazioni pratiche di queste funzionalità nei sistemi di gestione dei documenti.

Prima di iniziare a scrivere il codice, analizziamo i prerequisiti!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

### Librerie e versioni richieste
- **Aspose.Words per Python**: Assicurati di avere la versione 23.3 o successiva.
- **Pitone**: Si consiglia la versione 3.6 o superiore.

### Requisiti di configurazione dell'ambiente
- Un editor di codice come VSCode o PyCharm.
- Conoscenza di base della programmazione Python.

### Prerequisiti di conoscenza
- Familiarità con i concetti di elaborazione dei documenti.
- Comprensione della gestione dei file e delle directory in Python.

## Impostazione di Aspose.Words per Python

Per iniziare a utilizzare Aspose.Words, è necessario installarlo tramite pip. Apri il terminale o il prompt dei comandi ed esegui:

```bash
pip install aspose-words
```

### Fasi di acquisizione della licenza
1. **Prova gratuita**: Accedi a una licenza temporanea [Qui](https://purchase.aspose.com/temporary-license/) a scopo di test.
2. **Acquistare**: Per un utilizzo a lungo termine, acquistare una licenza [Qui](https://purchase.aspose.com/buy).
3. **Inizializzazione e configurazione di base**:
   - Carica il tuo documento utilizzando `aw.Document()`.
   - Configurare le opzioni di salvataggio in base alle proprie esigenze.

## Guida all'implementazione

Questa sezione ti guiderà nell'implementazione delle due funzionalità principali di questo tutorial: XamlFlowSaveOptions con cartella immagini e callback di avanzamento del salvataggio del documento.

### Funzionalità 1: XamlFlowSaveOptions con cartella immagini

#### Panoramica
Questa funzionalità consente di salvare un documento in formato XAML Flow specificando una cartella immagini e un alias. È ideale per gestire in modo efficiente documenti di grandi dimensioni con immagini incorporate.

#### Fasi di implementazione

##### Passaggio 1: importare le librerie necessarie
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Passaggio 2: definire la classe di callback ImageUriPrinter
Questa classe conta e reindirizza i flussi di immagini a una cartella alias specificata durante la conversione.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # tipo: Elenco[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**Opzioni di configurazione chiave:**
- `images_folder`: Specifica la directory in cui vengono salvate le immagini.
- `images_folder_alias`: Imposta un percorso alias utilizzato durante la conversione del documento.

##### Suggerimenti per la risoluzione dei problemi
- Prima di eseguire il codice, assicurarsi che tutte le directory esistano per evitare errori di file non trovato.
- Controllare i permessi di scrittura nella directory di output.

### Funzionalità 2: Callback di avanzamento del salvataggio del documento

#### Panoramica
Questa funzionalità gestisce il processo di salvataggio utilizzando un callback di avanzamento, consentendo di annullare le operazioni di salvataggio di lunga durata.

#### Fasi di implementazione

##### Passaggio 1: definire la classe SavingProgressCallback
La classe monitora la durata del salvataggio del documento e lo annulla se supera un limite di tempo specificato.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Durata massima consentita in sec.

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**Opzioni di configurazione chiave:**
- `save_format`: Scegli tra XAML_FLOW e XAML_FLOW_PACK.
- `progress_callback`: Monitora l'avanzamento del salvataggio per gestire le operazioni lunghe.

##### Suggerimenti per la risoluzione dei problemi
- Regolare `max_duration` in base alle dimensioni e alla complessità del documento.
- Gestire le eccezioni in modo appropriato per fornire messaggi di errore informativi.

## Applicazioni pratiche

Ecco alcuni casi di utilizzo pratico di queste funzionalità:
1. **Sistemi di gestione dei documenti**: Gestisci in modo efficiente documenti di grandi dimensioni con immagini incorporate specificando le cartelle delle immagini, migliorando così le prestazioni e l'organizzazione.
2. **Strumenti di reporting automatizzati**: Utilizzare callback di avanzamento per garantire che i report vengano generati entro tempi accettabili, migliorando l'esperienza utente.
3. **Reti di distribuzione di contenuti**: Semplifica la conversione dei documenti per la distribuzione sul Web gestendo efficacemente le risorse.

## Considerazioni sulle prestazioni

Per ottimizzare le prestazioni quando si utilizza Aspose.Words con Python:
- **Gestione della memoria**: Monitora l'utilizzo delle risorse e gestisci la memoria in modo efficiente eliminando gli oggetti dopo l'uso.
- **Operazioni di I/O sui file**: Ridurre al minimo le operazioni di lettura/scrittura dei file per migliorare la velocità.
- **Elaborazione batch**: Elaborare i documenti in batch ove possibile per ridurre le spese generali.

## Conclusione

In questo tutorial, abbiamo esplorato come ottimizzare il salvataggio dei documenti con Aspose.Words per Python utilizzando XAML Flow e callback di avanzamento. Implementando queste funzionalità, è possibile migliorare l'efficienza dei flussi di lavoro di elaborazione dei documenti, gestire le risorse in modo efficace e garantire operazioni tempestive.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}