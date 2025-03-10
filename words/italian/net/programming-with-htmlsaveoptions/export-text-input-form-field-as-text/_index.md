---
title: Esporta il campo del modulo di immissione testo come testo
linktitle: Esporta il campo del modulo di immissione testo come testo
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come esportare i campi del modulo di immissione testo come testo normale utilizzando Aspose.Words per .NET con questa guida completa e dettagliata.
weight: 10
url: /it/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Esporta il campo del modulo di immissione testo come testo

## Introduzione

Quindi, ti stai tuffando nel mondo di Aspose.Words per .NET? Ottima scelta! Se stai cercando di imparare come esportare un campo di un modulo di input di testo come testo, sei nel posto giusto. Che tu stia appena iniziando o che tu stia ripassando le tue competenze, questa guida ti guiderà attraverso tutto ciò che devi sapere. Cominciamo, va bene?

## Prerequisiti

Prima di addentrarci nei dettagli, assicuriamoci di avere tutto il necessario per seguire senza problemi:

-  Aspose.Words per .NET: Scarica e installa l'ultima versione da[Qui](https://releases.aspose.com/words/net/).
- IDE: Visual Studio o qualsiasi ambiente di sviluppo C#.
- Conoscenza di base del linguaggio C#: comprensione della sintassi di base del linguaggio C# e dei concetti di programmazione orientata agli oggetti.
- Documento: Un esempio di documento Word (`Rendering.docx`) con campi di immissione testo.

## Importazione degli spazi dei nomi

Per prima cosa, devi importare i namespace necessari. Sono come i mattoni che fanno funzionare tutto senza problemi.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Bene, ora che i nostri namespace sono pronti, passiamo all'azione!

## Passaggio 1: impostare il progetto

Prima di entrare nel codice, assicuriamoci che il nostro progetto sia impostato correttamente.

## Creazione del progetto

1. Aprire Visual Studio: iniziare aprendo Visual Studio o il proprio ambiente di sviluppo C# preferito.
2.  Crea un nuovo progetto: vai a`File > New > Project` Selezionare`Console App (.NET Core)` o qualsiasi altro tipo di progetto rilevante.
3.  Dai un nome al tuo progetto: dai al tuo progetto un nome significativo, qualcosa come`AsposeWordsExportExample`.

## Aggiunta di Aspose.Words

1.  Gestisci pacchetti NuGet: fai clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e seleziona`Manage NuGet Packages`.
2.  Cerca Aspose.Words: nel NuGet Package Manager, cerca`Aspose.Words`.
3.  Installa Aspose.Words: fai clic su`Install` per aggiungere la libreria Aspose.Words al tuo progetto.

## Passaggio 2: caricare il documento Word

Ora che il nostro progetto è impostato, carichiamo il documento Word che contiene i campi del modulo di immissione del testo.

1. Specificare la directory del documento: definire il percorso della directory in cui è archiviato il documento.
2.  Carica il documento: usa il`Document` classe per caricare il documento Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 3: preparare la directory di esportazione

Prima di esportare, assicuriamoci che la nostra directory di esportazione sia pronta. È qui che verranno salvati il nostro file HTML e le nostre immagini.

1. Definisci la directory di esportazione: specifica il percorso in cui verranno salvati i file esportati.
2. Controllare e pulire la directory: assicurarsi che la directory esista e sia vuota.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Passaggio 4: Configurare le opzioni di salvataggio

Ecco dove avviene la magia. Dobbiamo impostare le nostre opzioni di salvataggio per esportare il campo del modulo di immissione testo come testo normale.

1.  Crea opzioni di salvataggio: Inizializza un nuovo`HtmlSaveOptions` oggetto.
2.  Imposta l'opzione di esportazione del testo: configura l'`ExportTextInputFormFieldAsText`proprietà a`true`.
3. Imposta cartella immagini: definisce la cartella in cui verranno salvate le immagini.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Passaggio 5: Salvare il documento come HTML

Infine, salviamo il documento Word come file HTML utilizzando le opzioni di salvataggio configurate.

1. Definisci il percorso di output: specifica il percorso in cui verrà salvato il file HTML.
2.  Salva il documento: usa il`Save` metodo del`Document`classe per esportare il documento.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Conclusione

Ed ecco fatto! Hai esportato con successo un campo di modulo di immissione testo come testo normale usando Aspose.Words per .NET. Questa guida dovrebbe averti fornito un approccio chiaro e dettagliato per raggiungere questo obiettivo. Ricorda, la pratica rende perfetti, quindi continua a sperimentare diverse opzioni e impostazioni per vedere cos'altro puoi fare con Aspose.Words.

## Domande frequenti

### Posso esportare altri tipi di campi modulo utilizzando lo stesso metodo?

 Sì, puoi esportare altri tipi di campi modulo configurando diverse proprietà del`HtmlSaveOptions` classe.

### Cosa succede se il mio documento contiene immagini?

 Le immagini verranno salvate nella cartella immagini specificata. Assicurati di impostare`ImagesFolder` proprietà nella`HtmlSaveOptions`.

### Ho bisogno di una licenza per Aspose.Words?

 Sì, puoi ottenere una prova gratuita[Qui](https://releases.aspose.com/) o acquistare una licenza[Qui](https://purchase.aspose.com/buy).

### Posso personalizzare l'HTML esportato?

 Assolutamente! Aspose.Words fornisce varie opzioni per personalizzare l'output HTML. Fare riferimento a[documentazione](https://reference.aspose.com/words/net/) per maggiori dettagli.

### Aspose.Words è compatibile con .NET Core?

Sì, Aspose.Words è compatibile con .NET Core, .NET Framework e altre piattaforme .NET.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
