---
"description": "Scopri come aggiungere marcatori bidirezionali (Bidi) nei documenti Word utilizzando Aspose.Words per .NET con questa guida. Garantisci il corretto orientamento del testo per i contenuti multilingue."
"linktitle": "Aggiungere segni Bidi nel documento Word"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Aggiungere segni Bidi nel documento Word"
"url": "/it/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere segni Bidi nel documento Word

## Introduzione

Nel mondo dell'elaborazione dei documenti, la gestione del testo bidirezionale (Bidi) può essere spesso un po' complicata. Questo è particolarmente vero quando si ha a che fare con lingue che hanno direzioni di testo diverse, come l'arabo o l'ebraico. Fortunatamente, Aspose.Words per .NET semplifica la gestione di questi scenari. In questo tutorial, spiegheremo come aggiungere indicatori Bidi a un documento Word utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di immergerci nel codice, assicurati di avere quanto segue:

1. Aspose.Words per .NET: è necessario aver installato Aspose.Words per .NET. È possibile scaricarlo da [Pagina dei download di Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework o .NET Core: assicurati di avere configurato un ambiente .NET compatibile per l'esecuzione degli esempi.
3. Conoscenza di base di C#: familiarità con il linguaggio di programmazione C# e operazioni di base in .NET.

## Importa spazi dei nomi

Per iniziare, devi importare gli spazi dei nomi necessari. Ecco come puoi includerli nel tuo progetto:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Analizziamo il processo di aggiunta dei segni Bidi in un documento Word in passaggi chiari. Ogni passaggio ti guiderà attraverso il codice e il suo scopo.

## Passaggio 1: imposta il documento

Inizia creando una nuova istanza di `Document` classe e una `DocumentBuilder` per aggiungere contenuto al documento.

```csharp
// Percorso alla directory dei tuoi documenti
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Crea il documento e aggiungi il contenuto
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In questo passaggio, si inizializza un nuovo documento Word e si imposta un `DocumentBuilder` per facilitare l'inserimento dei contenuti.

## Passaggio 2: aggiungi contenuto al tuo documento

Ora aggiungi del testo al tuo documento. Qui aggiungeremo testo in diverse lingue per illustrare la gestione del testo Bidi.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Qui, aggiungiamo prima una frase standard in inglese. Poi, attiviamo la formattazione bidirezionale per il testo successivo, scritto in ebraico e arabo. Questo dimostra come incorporare testo bidirezionale.

## Passaggio 3: configurare le opzioni di salvataggio per i segni Bidi

Per garantire che i segni Bidi vengano salvati correttamente nel documento, è necessario configurare `TxtSaveOptions` e abilitare il `AddBidiMarks` opzione.

```csharp
// Aggiungi segni Bidi
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

In questo passaggio, creiamo un'istanza di `TxtSaveOptions` e impostare il `AddBidiMarks` proprietà a `true`In questo modo si garantisce che i segni Bidi vengano inclusi quando si salva il documento come file di testo.

## Conclusione

Aggiungere i contrassegni Bidi ai documenti Word può essere un passaggio cruciale quando si gestiscono contenuti multilingue che includono lingue con direzioni di testo diverse. Con Aspose.Words per .NET, questo processo è semplice ed efficiente. Seguendo i passaggi descritti sopra, è possibile garantire che i documenti rappresentino correttamente il testo Bidi, migliorandone la leggibilità e l'accuratezza.

## Domande frequenti

### Cosa sono i segni Bidi e perché sono importanti?
I bidi mark sono caratteri speciali utilizzati per controllare la direzione del testo nei documenti. Sono essenziali per visualizzare correttamente le lingue che si leggono da destra a sinistra, come l'arabo e l'ebraico.

### Posso usare Aspose.Words per .NET per gestire altri tipi di problemi di direzione del testo?
Sì, Aspose.Words per .NET fornisce un supporto completo per varie esigenze di formattazione e direzione del testo, comprese le lingue da destra a sinistra e da sinistra a destra.

### È possibile applicare la formattazione Bidi solo a parti specifiche di un documento?
Sì, puoi applicare la formattazione Bidi a paragrafi o sezioni specifici del tuo documento, a seconda delle tue esigenze.

### In quali formati posso salvare il documento con i segni Bidi?
Nell'esempio fornito, il documento viene salvato come file di testo. Tuttavia, Aspose.Words supporta anche il salvataggio di documenti in vari formati, mantenendo i segni Bidi.

### Dove posso trovare maggiori informazioni su Aspose.Words per .NET?
Puoi esplorare di più su Aspose.Words per .NET tramite [Documentazione di Aspose](https://reference.aspose.com/words/net/) e accedere al [Forum di supporto](https://forum.aspose.com/c/words/8) per ulteriore assistenza.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}