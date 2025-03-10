---
title: Ancoraggio verticale
linktitle: Ancoraggio verticale
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come impostare le posizioni di ancoraggio verticali per le caselle di testo nei documenti Word utilizzando Aspose.Words per .NET. È inclusa una semplice guida passo-passo.
weight: 10
url: /it/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ancoraggio verticale

## Introduzione

Ti è mai capitato di dover controllare esattamente dove appare il testo all'interno di una casella di testo in un documento Word? Forse vuoi che il tuo testo sia ancorato alla parte superiore, centrale o inferiore della casella di testo? Se è così, sei nel posto giusto! In questo tutorial, esploreremo come usare Aspose.Words per .NET per impostare l'ancoraggio verticale delle caselle di testo nei documenti Word. Pensa all'ancoraggio verticale come alla bacchetta magica che posiziona il tuo testo esattamente dove vuoi all'interno del suo contenitore. Pronto a tuffarti? Cominciamo!

## Prerequisiti

Prima di addentrarci nei dettagli dell'ancoraggio verticale, è necessario disporre di alcune cose:

1.  Aspose.Words per .NET: assicurati di avere installata la libreria Aspose.Words per .NET. Se non ce l'hai ancora, puoi[scaricalo qui](https://releases.aspose.com/words/net/).
2. Visual Studio: questo tutorial presuppone che tu stia utilizzando Visual Studio o un altro IDE .NET per la codifica.
3. Conoscenza di base di C#: la familiarità con C# e .NET ti aiuterà a seguire il corso senza problemi.

## Importazione degli spazi dei nomi

Per iniziare, devi importare i namespace necessari nel tuo codice C#. Qui è dove dici alla tua applicazione dove trovare le classi e i metodi che utilizzerai. Ecco come fare:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Questi namespace forniscono le classi necessarie per lavorare con documenti e forme.

## Passaggio 1: inizializzare il documento

Prima di tutto, devi creare un nuovo documento Word. Pensa a questo come all'impostazione della tua tela prima di iniziare a dipingere.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Qui,`Document` è la tua tela bianca, e`DocumentBuilder` è il tuo pennello, che ti consente di aggiungere forme e testo.

## Passaggio 2: Inserisci una forma di casella di testo

Ora, aggiungiamo una casella di testo al nostro documento. È qui che risiederà il tuo testo. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 In questo esempio,`ShapeType.TextBox` specifica la forma desiderata e`200, 200` sono la larghezza e l'altezza della casella di testo in punti.

## Passaggio 3: impostare l'ancoraggio verticale

Ecco dove avviene la magia! Puoi impostare l'allineamento verticale del testo all'interno della casella di testo. Questo determina se il testo è ancorato alla parte superiore, centrale o inferiore della casella di testo.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 In questo caso,`TextBoxAnchor.Bottom`assicura che il testo venga ancorato alla parte inferiore della casella di testo. Se lo volessi centrato o allineato in alto, useresti`TextBoxAnchor.Center` O`TextBoxAnchor.Top`, rispettivamente.

## Passaggio 4: aggiungere testo alla casella di testo

Ora è il momento di aggiungere del contenuto alla tua casella di testo. Immagina di riempire la tua tela con gli ultimi ritocchi.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Qui,`MoveTo` assicura che il testo venga inserito nella casella di testo e`Write` aggiunge il testo vero e proprio.

## Passaggio 5: Salvare il documento

Il passaggio finale è salvare il documento. È come mettere il dipinto finito in una cornice.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Conclusione

Ed ecco fatto! Hai appena imparato come controllare l'allineamento verticale del testo all'interno di una casella di testo in un documento Word usando Aspose.Words per .NET. Che tu stia ancorando il testo in alto, al centro o in basso, questa funzionalità ti offre un controllo preciso sul layout del tuo documento. Quindi la prossima volta che dovrai modificare il posizionamento del testo del tuo documento, saprai esattamente cosa fare!

## Domande frequenti

### Cos'è l'ancoraggio verticale in un documento Word?
L'ancoraggio verticale controlla la posizione del testo all'interno di una casella di testo, ad esempio l'allineamento in alto, al centro o in basso.

### Posso usare altre forme oltre alle caselle di testo?
Sì, puoi utilizzare l'ancoraggio verticale con altre forme, anche se le caselle di testo rappresentano il caso d'uso più comune.

### Come faccio a modificare il punto di ancoraggio dopo aver creato la casella di testo?
 È possibile modificare il punto di ancoraggio impostando`VerticalAnchor` proprietà sull'oggetto forma della casella di testo.

### È possibile ancorare il testo al centro della casella di testo?
 Assolutamente! Usa semplicemente`TextBoxAnchor.Center` per centrare il testo verticalmente all'interno della casella di testo.

### Dove posso trovare maggiori informazioni su Aspose.Words per .NET?
 Dai un'occhiata al[Documentazione di Aspose.Words](https://reference.aspose.com/words/net/) per maggiori dettagli e guide.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
