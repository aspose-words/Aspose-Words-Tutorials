---
"description": "Scopri come bloccare le proporzioni delle forme nei documenti Word utilizzando Aspose.Words per .NET. Segui questa guida passo passo per mantenere le proporzioni di immagini e forme."
"linktitle": "Proporzioni bloccate"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Proporzioni bloccate"
"url": "/it/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Proporzioni bloccate

## Introduzione

Ti sei mai chiesto come mantenere le proporzioni perfette di immagini e forme nei tuoi documenti Word? A volte, è necessario assicurarsi che immagini e forme non vengano distorte durante il ridimensionamento. È qui che il blocco delle proporzioni torna utile. In questo tutorial, esploreremo come impostare le proporzioni per le forme nei documenti Word utilizzando Aspose.Words per .NET. Lo suddivideremo in passaggi semplici da seguire, per permetterti di applicare queste competenze ai tuoi progetti con sicurezza.

## Prerequisiti

Prima di immergerci nel codice, vediamo cosa occorre per iniziare:

- Libreria Aspose.Words per .NET: è necessario aver installato Aspose.Words per .NET. Se non lo hai già fatto, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: assicurati di aver configurato un ambiente di sviluppo .NET. Visual Studio è una scelta diffusa.
- Conoscenza di base di C#: sarà utile avere una certa familiarità con la programmazione in C#.

## Importa spazi dei nomi

Per prima cosa, importiamo gli spazi dei nomi necessari. Questi spazi dei nomi ci daranno accesso alle classi e ai metodi necessari per lavorare con documenti e forme di Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Passaggio 1: imposta la directory dei documenti

Prima di iniziare a manipolare le forme, dobbiamo impostare una directory in cui verranno salvati i nostri documenti. Per semplicità, useremo un segnaposto. `YOUR DOCUMENT DIRECTORY`Sostituiscilo con il percorso effettivo della directory del tuo documento.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: creare un nuovo documento

Successivamente, creeremo un nuovo documento Word utilizzando Aspose.Words. Questo documento servirà come base per aggiungere forme e immagini.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Qui creiamo un'istanza di `Document` classe e usa un `DocumentBuilder` per aiutarci a costruire il contenuto del documento.

## Passaggio 3: inserire un'immagine

Ora inseriamo un'immagine nel nostro documento. Useremo il `InsertImage` metodo del `DocumentBuilder` classe. Assicurati di avere un'immagine nella directory specificata.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Sostituire `dataDir + "Transparent background logo.png"` con il percorso al file immagine.

## Passaggio 4: bloccare le proporzioni

Una volta inserita l'immagine, possiamo bloccarne le proporzioni. Bloccare le proporzioni garantisce che le proporzioni dell'immagine rimangano costanti durante il ridimensionamento.

```csharp
shape.AspectRatioLocked = true;
```

Collocamento `AspectRatioLocked` A `true` assicura che l'immagine mantenga le sue proporzioni originali.

## Passaggio 5: salvare il documento

Infine, salveremo il documento nella directory specificata. Questo passaggio salva tutte le modifiche apportate al file del documento.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusione

Congratulazioni! Hai imparato a impostare le proporzioni delle forme nei documenti Word utilizzando Aspose.Words per .NET. Seguendo questi passaggi, puoi garantire che immagini e forme mantengano le loro proporzioni, conferendo ai tuoi documenti un aspetto professionale e curato. Sentiti libero di sperimentare con diverse immagini e forme per vedere come funziona la funzione di blocco delle proporzioni in diversi scenari.

## Domande frequenti

### Posso sbloccare le proporzioni dopo averle bloccate?
Sì, puoi sbloccare il rapporto d'aspetto impostando `shape.AspectRatioLocked = false`.

### Cosa succede se ridimensiono un'immagine con proporzioni bloccate?
L'immagine verrà ridimensionata proporzionalmente, mantenendo il rapporto larghezza-altezza originale.

### Posso applicarlo anche ad altre forme oltre alle immagini?
Assolutamente! La funzione di blocco delle proporzioni può essere applicata a qualsiasi forma, inclusi rettangoli, cerchi e altro ancora.

### Aspose.Words per .NET è compatibile con .NET Core?
Sì, Aspose.Words per .NET supporta sia .NET Framework che .NET Core.

### Dove posso trovare ulteriore documentazione su Aspose.Words per .NET?
Puoi trovare una documentazione completa [Qui](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}