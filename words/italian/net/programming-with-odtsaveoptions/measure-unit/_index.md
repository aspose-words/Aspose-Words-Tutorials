---
"description": "Scopri come configurare la funzionalità delle unità di misura in Aspose.Words per .NET per preservare la formattazione del documento durante la conversione ODT."
"linktitle": "Unità di misura"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Unità di misura"
"url": "/it/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Unità di misura

## Introduzione

Hai mai dovuto convertire i tuoi documenti Word in formati diversi, ma avevi bisogno di un'unità di misura specifica per il tuo layout? Che si tratti di pollici, centimetri o punti, garantire che il documento mantenga la sua integrità durante il processo di conversione è fondamentale. In questo tutorial, ti mostreremo come configurare la funzionalità delle unità di misura in Aspose.Words per .NET. Questa potente funzionalità garantisce che la formattazione del documento venga mantenuta esattamente come necessario durante la conversione in formato ODT (Open Document Text).

## Prerequisiti

Prima di immergerti nel codice, ecco alcune cose che ti servono per iniziare:

1. Aspose.Words per .NET: assicurati di avere installata l'ultima versione di Aspose.Words per .NET. Se non l'hai ancora installata, puoi scaricarla da [Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: un IDE come Visual Studio per scrivere ed eseguire il codice C#.
3. Conoscenza di base di C#: comprendere le basi di C# ti aiuterà a seguire il tutorial.
4. Un documento Word: tieni pronto un documento Word di esempio da utilizzare per la conversione.

## Importa spazi dei nomi

Prima di iniziare a scrivere codice, assicuriamoci di aver importato i namespace necessari. Aggiungi queste direttive using all'inizio del file di codice:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: imposta la directory dei documenti

Per prima cosa, devi definire il percorso della directory del documento. È qui che si trova il documento Word e dove verrà salvato il file convertito.

```csharp
// Percorso alla directory dei tuoi documenti
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Sostituire `"YOUR DOCUMENTS DIRECTORY"` Con il percorso effettivo della directory. Questo assicura che il codice sappia dove trovare il documento Word.

## Passaggio 2: caricare il documento Word

Successivamente, è necessario caricare il documento Word che si desidera convertire. Questo viene fatto utilizzando `Document` classe da Aspose.Words.

```csharp
// Carica il documento Word
Document doc = new Document(dataDir + "Document.docx");
```

Assicurati che il documento Word, denominato "Document.docx", sia presente nella directory specificata.

## Passaggio 3: configurare l'unità di misura

Ora configuriamo l'unità di misura per la conversione ODT. È qui che avviene la magia. Imposteremo `OdtSaveOptions` utilizzare i pollici come unità di misura.

```csharp
// Configurazione delle opzioni di backup con la funzionalità "Unità di misura"
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

In questo esempio, impostiamo l'unità di misura in pollici. Puoi anche scegliere altre unità di misura, come `OdtSaveMeasureUnit.Centimeters` O `OdtSaveMeasureUnit.Points` a seconda delle vostre esigenze.

## Passaggio 4: convertire il documento in ODT

Infine, convertiremo il documento Word nel formato ODT utilizzando il configurato `OdtSaveOptions`.

```csharp
// Convertire il documento in ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Questa riga di codice salva il documento convertito nella directory specificata con la nuova unità di misura applicata.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi configurare facilmente la funzionalità delle unità di misura in Aspose.Words per .NET per garantire che il layout del documento venga mantenuto durante la conversione. Che tu stia lavorando con pollici, centimetri o punti, questo tutorial ti ha mostrato come gestire facilmente la formattazione del tuo documento.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per lavorare con i documenti Word a livello di programmazione. Consente agli sviluppatori di creare, modificare, convertire ed elaborare documenti Word senza dover utilizzare Microsoft Word.

### Posso usare altre unità di misura oltre ai pollici?
Sì, Aspose.Words per .NET supporta altre unità di misura come centimetri e punti. È possibile specificare l'unità desiderata utilizzando `OdtSaveMeasureUnit` enumerazione.

### È disponibile una versione di prova gratuita di Aspose.Words per .NET?
Sì, puoi scaricare una versione di prova gratuita di Aspose.Words per .NET da [Qui](https://releases.aspose.com/).

### Dove posso trovare la documentazione per Aspose.Words per .NET?
È possibile accedere alla documentazione completa per Aspose.Words per .NET su [questo collegamento](https://reference.aspose.com/words/net/).

### Come posso ottenere supporto per Aspose.Words per .NET?
Per supporto, puoi visitare il forum Aspose.Words all'indirizzo [questo collegamento](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}