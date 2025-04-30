---
"description": "Scopri come impostare le posizioni di ancoraggio verticali per le caselle di testo nei documenti Word utilizzando Aspose.Words per .NET. Una semplice guida passo passo è inclusa."
"linktitle": "Ancoraggio verticale"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Ancoraggio verticale"
"url": "/it/net/programming-with-shapes/vertical-anchor/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ancoraggio verticale

## Introduzione

Ti è mai capitato di dover controllare esattamente dove appare il testo all'interno di una casella di testo in un documento Word? Forse desideri che il testo sia ancorato alla parte superiore, centrale o inferiore della casella di testo? Se sì, sei nel posto giusto! In questo tutorial, esploreremo come utilizzare Aspose.Words per .NET per impostare l'ancoraggio verticale delle caselle di testo nei documenti Word. Pensa all'ancoraggio verticale come alla bacchetta magica che posiziona il testo esattamente dove desideri all'interno del suo contenitore. Pronti a iniziare? Iniziamo!

## Prerequisiti

Prima di addentrarci nei dettagli dell'ancoraggio verticale, è necessario disporre di alcune cose:

1. Aspose.Words per .NET: assicurati di aver installato la libreria Aspose.Words per .NET. Se non l'hai ancora installata, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
2. Visual Studio: in questo tutorial si presuppone che si utilizzi Visual Studio o un altro IDE .NET per la codifica.
3. Conoscenza di base di C#: la familiarità con C# e .NET ti aiuterà a seguire il corso senza problemi.

## Importa spazi dei nomi

Per iniziare, devi importare gli spazi dei nomi necessari nel codice C#. È qui che indichi all'applicazione dove trovare le classi e i metodi che utilizzerai. Ecco come fare:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Questi namespace forniscono le classi necessarie per lavorare con documenti e forme.

## Passaggio 1: inizializzare il documento

Per prima cosa, devi creare un nuovo documento Word. Consideralo come la preparazione della tua tela prima di iniziare a dipingere.

```csharp
// Percorso alla directory dei documenti 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Qui, `Document` è la tua tela bianca, e `DocumentBuilder` è il tuo pennello, che ti consente di aggiungere forme e testo.

## Passaggio 2: inserire una forma di casella di testo

Ora aggiungiamo una casella di testo al nostro documento. È qui che verrà inserito il tuo testo. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

In questo esempio, `ShapeType.TextBox` specifica la forma desiderata e `200, 200` sono la larghezza e l'altezza della casella di testo in punti.

## Passaggio 3: impostare l'ancoraggio verticale

Ed è qui che avviene la magia! Puoi impostare l'allineamento verticale del testo all'interno della casella di testo. Questo determina se il testo verrà ancorato alla parte superiore, centrale o inferiore della casella di testo.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

In questo caso, `TextBoxAnchor.Bottom` assicura che il testo venga ancorato alla parte inferiore della casella di testo. Se lo si desidera centrato o allineato in alto, si dovrebbe usare `TextBoxAnchO.Center` or `TextBoxAnchor.Top`, rispettivamente.

## Passaggio 4: aggiungere testo alla casella di testo

Ora è il momento di aggiungere del contenuto alla casella di testo. Immagina di riempire la tua tela con gli ultimi ritocchi.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

Qui, `MoveTo` assicura che il testo venga inserito nella casella di testo e `Write` aggiunge il testo vero e proprio.

## Passaggio 5: salvare il documento

Il passaggio finale è salvare il documento. È come incorniciare il dipinto finito.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Conclusione

Ed ecco fatto! Hai appena imparato a controllare l'allineamento verticale del testo all'interno di una casella di testo in un documento Word utilizzando Aspose.Words per .NET. Che tu stia ancorando il testo in alto, al centro o in basso, questa funzione ti offre un controllo preciso sul layout del documento. Così, la prossima volta che dovrai modificare il posizionamento del testo nel tuo documento, saprai esattamente cosa fare!

## Domande frequenti

### Cos'è l'ancoraggio verticale in un documento Word?
L'ancoraggio verticale controlla la posizione del testo all'interno di una casella di testo, ad esempio l'allineamento in alto, al centro o in basso.

### Posso usare altre forme oltre alle caselle di testo?
Sì, puoi utilizzare l'ancoraggio verticale con altre forme, anche se le caselle di testo rappresentano il caso d'uso più comune.

### Come faccio a modificare il punto di ancoraggio dopo aver creato la casella di testo?
È possibile modificare il punto di ancoraggio impostando `VerticalAnchor` proprietà sull'oggetto forma della casella di testo.

### È possibile ancorare il testo al centro della casella di testo?
Assolutamente! Usalo e basta `TextBoxAnchor.Center` per centrare il testo verticalmente all'interno della casella di testo.

### Dove posso trovare maggiori informazioni su Aspose.Words per .NET?
Dai un'occhiata al [Documentazione di Aspose.Words](https://reference.aspose.com/words/net/) per maggiori dettagli e guide.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}