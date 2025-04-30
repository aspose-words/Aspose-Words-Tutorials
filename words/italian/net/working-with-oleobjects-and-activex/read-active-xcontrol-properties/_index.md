---
"description": "Scopri come leggere le proprietà dei controlli ActiveX dai file Word utilizzando Aspose.Words per .NET in una guida passo passo. Migliora le tue competenze di automazione dei documenti."
"linktitle": "Leggi le proprietà di Active XControl dal file Word"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Leggi le proprietà di Active XControl dal file Word"
"url": "/it/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Leggi le proprietà di Active XControl dal file Word

## Introduzione

Nell'era digitale odierna, l'automazione è fondamentale per migliorare la produttività. Se si lavora con documenti Word che contengono controlli ActiveX, potrebbe essere necessario leggerne le proprietà per vari scopi. I controlli ActiveX, come caselle di controllo e pulsanti, possono contenere dati importanti. Utilizzando Aspose.Words per .NET, è possibile estrarre e manipolare questi dati in modo efficiente a livello di codice.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. Aspose.Words per la libreria .NET: puoi scaricarla da [Qui](https://releases.aspose.com/words/net/).
2. Visual Studio o qualsiasi IDE C#: per scrivere ed eseguire il codice.
3. Un documento Word con controlli ActiveX: ad esempio, "Controlli ActiveX.docx".
4. Conoscenza di base di C#: per seguire il corso è necessaria la familiarità con la programmazione C#.

## Importa spazi dei nomi

Per prima cosa, importiamo gli spazi dei nomi necessari per lavorare con Aspose.Words per .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Passaggio 1: caricare il documento Word

Per iniziare, dovrai caricare il documento Word che contiene i controlli ActiveX.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Passaggio 2: inizializzare una stringa per contenere le proprietà

Successivamente, inizializzare una stringa vuota per memorizzare le proprietà dei controlli ActiveX.

```csharp
string properties = "";
```

## Passaggio 3: scorrere le forme nel documento

Dobbiamo scorrere tutte le forme del documento per trovare i controlli ActiveX.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Elaborare il controllo ActiveX
    }
}
```

## Passaggio 4: estrarre le proprietà dai controlli ActiveX

All'interno del ciclo, verifica se il controllo è un Forms2OleControl. In tal caso, esegui il cast ed estrai le proprietà.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Passaggio 5: conteggio totale dei controlli ActiveX

Dopo aver esaminato tutte le forme, conta il numero totale di controlli ActiveX trovati.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Passaggio 6: visualizzare le proprietà

Infine, stampare le proprietà estratte sulla console.

```csharp
Console.WriteLine("\n" + properties);
```

## Conclusione

Ed ecco fatto! Hai imparato con successo a leggere le proprietà dei controlli ActiveX da un documento Word utilizzando Aspose.Words per .NET. Questo tutorial ha trattato il caricamento di un documento, l'iterazione tra le forme e l'estrazione delle proprietà dai controlli ActiveX. Seguendo questi passaggi, puoi automatizzare l'estrazione di dati importanti dai tuoi documenti Word, migliorando l'efficienza del flusso di lavoro.

## Domande frequenti

### Cosa sono i controlli ActiveX nei documenti Word?
I controlli ActiveX sono oggetti interattivi incorporati nei documenti Word, come caselle di controllo, pulsanti e campi di testo, utilizzati per creare moduli e automatizzare attività.

### Posso modificare le proprietà dei controlli ActiveX utilizzando Aspose.Words per .NET?
Sì, Aspose.Words per .NET consente di modificare le proprietà dei controlli ActiveX a livello di programmazione.

### Aspose.Words per .NET è gratuito?
Aspose.Words per .NET offre una prova gratuita, ma è necessario acquistare una licenza per continuare a utilizzarlo. Puoi ottenere una prova gratuita. [Qui](https://releases.aspose.com/).

### Posso utilizzare Aspose.Words per .NET con altri linguaggi .NET oltre a C#?
Sì, Aspose.Words per .NET può essere utilizzato con qualsiasi linguaggio .NET, inclusi VB.NET e F#.

### Dove posso trovare ulteriore documentazione su Aspose.Words per .NET?
Puoi trovare la documentazione dettagliata [Qui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}