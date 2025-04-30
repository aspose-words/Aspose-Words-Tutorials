---
"description": "Scopri come esportare risorse come CSS e font salvando documenti Word in HTML utilizzando Aspose.Words per .NET. Segui la nostra guida passo passo."
"linktitle": "Esportazione di risorse"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Esportazione di risorse"
"url": "/it/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Esportazione di risorse

## Introduzione

Ciao, appassionati di tecnologia! Se vi è mai capitato di dover convertire documenti Word in HTML, siete nel posto giusto. Oggi ci immergiamo nel meraviglioso mondo di Aspose.Words per .NET. Questa potente libreria semplifica l'utilizzo dei documenti Word a livello di programmazione. In questo tutorial, vi guideremo passo dopo passo nell'esportazione di risorse, come font e CSS, quando salvate un documento Word in HTML utilizzando Aspose.Words per .NET. Allacciate le cinture per un'esperienza divertente e istruttiva!

## Prerequisiti

Prima di immergerci nel codice, assicuriamoci di avere tutto il necessario per iniziare. Ecco una breve checklist:

1. Visual Studio: assicurati di aver installato Visual Studio sul tuo computer. Puoi scaricarlo da [Sito web di Visual Studio](https://visualstudio.microsoft.com/).
2. Aspose.Words per .NET: avrai bisogno della libreria Aspose.Words per .NET. Se non l'hai ancora scaricata, puoi scaricarne una prova gratuita da [Rilasci di Aspose](https://releases.aspose.com/words/net/) oppure acquistalo da [Negozio Aspose](https://purchase.aspose.com/buy).
3. Conoscenza di base di C#: una conoscenza di base di C# ti aiuterà a seguire gli esempi di codice.

Tutto chiaro? Ottimo! Passiamo all'importazione degli spazi dei nomi necessari.

## Importa spazi dei nomi

Per utilizzare Aspose.Words per .NET, è necessario includere gli spazi dei nomi pertinenti nel progetto. Ecco come fare:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Questi namespace sono fondamentali per accedere alle classi e ai metodi Aspose.Words che utilizzeremo nel nostro tutorial.

Analizziamo il processo di esportazione delle risorse quando si salva un documento Word in formato HTML. Lo faremo passo dopo passo, così sarà facile da seguire.

## Passaggio 1: imposta la directory dei documenti

Per prima cosa, devi specificare il percorso della directory dei documenti. È qui che si trova il tuo documento Word e dove verrà salvato il file HTML.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Sostituire `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo della tua directory.

## Passaggio 2: caricare il documento Word

Ora, carichiamo il documento Word che desideri convertire in HTML. Per questo tutorial, useremo un documento denominato `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Questa riga di codice carica il documento dalla directory specificata.

## Passaggio 3: configurare le opzioni di salvataggio HTML

Per esportare risorse come CSS e font, è necessario configurare `HtmlSaveOptions`Questo passaggio è fondamentale per garantire che l'output HTML sia ben strutturato e includa le risorse necessarie.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://esempio.com/risorse"
};
```

Analizziamo nel dettaglio le funzioni di ciascuna opzione:
- `CssStyleSheetType = CssStyleSheetType.External`: Questa opzione specifica che gli stili CSS devono essere salvati in un foglio di stile esterno.
- `ExportFontResources = true`: Consente l'esportazione delle risorse dei font.
- `ResourceFolder = dataDir + "Resources"`: Specifica la cartella locale in cui verranno salvate le risorse (come i font e i file CSS).
- `ResourceFolderAlias = "http://example.com/resources"`: Imposta un alias per la cartella delle risorse, che verrà utilizzato nel file HTML.

## Passaggio 4: salvare il documento come HTML

Una volta configurate le opzioni di salvataggio, il passaggio finale consiste nel salvare il documento come file HTML. Ecco come fare:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Questa riga di codice salva il documento in formato HTML, insieme alle risorse esportate.

## Conclusione

Ed ecco fatto! Hai esportato con successo le risorse salvando un documento Word in formato HTML utilizzando Aspose.Words per .NET. Con questa potente libreria, gestire i documenti Word a livello di codice diventa un gioco da ragazzi. Che tu stia lavorando a un'applicazione web o che tu debba semplicemente convertire documenti per l'utilizzo offline, Aspose.Words è la soluzione che fa per te.

## Domande frequenti

### Posso esportare le immagini insieme ai font e al CSS?
Certo che puoi! Aspose.Words per .NET supporta anche l'esportazione di immagini. Assicurati solo di configurare `HtmlSaveOptions` di conseguenza.

### Esiste un modo per incorporare CSS invece di utilizzare un foglio di stile esterno?
Assolutamente. Puoi impostare `CssStyleSheetType` A `CssStyleSheetType.Embedded` se preferisci gli stili incorporati.

### Come posso personalizzare il nome del file HTML di output?
Puoi specificare qualsiasi nome di file che desideri nel `doc.Save` metodo. Ad esempio, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words supporta altri formati oltre a HTML?
Sì, supporta vari formati tra cui PDF, DOCX, TXT e altri. Scopri di più [documentazione](https://reference.aspose.com/words/net/) per un elenco completo.

### Dove posso trovare ulteriore supporto e risorse?
Per ulteriore assistenza, visita il [Forum di supporto di Aspose.Words](https://forum.aspose.com/c/words/8). Puoi anche trovare documentazione dettagliata ed esempi su [Sito web di Aspose](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}