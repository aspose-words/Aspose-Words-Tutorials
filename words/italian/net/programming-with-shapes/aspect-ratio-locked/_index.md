---
title: Rapporto d'aspetto bloccato
linktitle: Rapporto d'aspetto bloccato
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come bloccare le proporzioni delle forme nei documenti Word usando Aspose.Words per .NET. Segui questa guida passo passo per mantenere proporzionate le tue immagini e forme.
weight: 10
url: /it/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rapporto d'aspetto bloccato

## Introduzione

Ti sei mai chiesto come mantenere le proporzioni perfette di immagini e forme nei tuoi documenti Word? A volte, devi assicurarti che le tue immagini e forme non vengano distorte quando vengono ridimensionate. Ecco dove il blocco delle proporzioni torna utile. In questo tutorial, esploreremo come impostare le proporzioni per le forme nei documenti Word usando Aspose.Words per .NET. Lo suddivideremo in semplici passaggi da seguire, assicurandoti di poter applicare queste competenze ai tuoi progetti con sicurezza.

## Prerequisiti

Prima di immergerci nel codice, rivediamo ciò che occorre per iniziare:

- Libreria Aspose.Words per .NET: devi avere Aspose.Words per .NET installato. Se non lo hai già fatto, puoi[scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: assicurati di avere un ambiente di sviluppo .NET impostato. Visual Studio è una scelta popolare.
- Conoscenza di base di C#: sarà utile avere una certa familiarità con la programmazione in C#.

## Importazione degli spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questi namespace ci daranno accesso alle classi e ai metodi di cui abbiamo bisogno per lavorare con i documenti e le forme di Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Passaggio 1: imposta la directory dei documenti

 Prima di iniziare a manipolare le forme, dobbiamo impostare una directory in cui verranno archiviati i nostri documenti. Per semplicità, useremo un segnaposto`YOUR DOCUMENT DIRECTORY`Sostituiscilo con il percorso effettivo della directory del tuo documento.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: creare un nuovo documento

Successivamente, creeremo un nuovo documento Word usando Aspose.Words. Questo documento servirà come tela per aggiungere forme e immagini.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Qui creiamo un'istanza di`Document` classe e usa un`DocumentBuilder` per aiutarci a costruire il contenuto del documento.

## Passaggio 3: Inserisci un'immagine

 Ora, inseriamo un'immagine nel nostro documento. Useremo il`InsertImage` metodo del`DocumentBuilder`classe. Assicurati di avere un'immagine nella directory specificata.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Sostituire`dataDir + "Transparent background logo.png"` con il percorso del file immagine.

## Passaggio 4: Blocca le proporzioni

Una volta inserita l'immagine, possiamo bloccarne il rapporto d'aspetto. Il blocco del rapporto d'aspetto assicura che le proporzioni dell'immagine rimangano costanti durante il ridimensionamento.

```csharp
shape.AspectRatioLocked = true;
```

 Collocamento`AspectRatioLocked` A`true` assicura che l'immagine mantenga le sue proporzioni originali.

## Passaggio 5: Salvare il documento

Infine, salveremo il documento nella directory specificata. Questo passaggio scrive tutte le modifiche apportate al file del documento.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusione

Congratulazioni! Hai imparato con successo come impostare le proporzioni per le forme nei documenti Word usando Aspose.Words per .NET. Seguendo questi passaggi, puoi assicurarti che le tue immagini e forme mantengano le loro proporzioni, rendendo i tuoi documenti professionali e curati. Sentiti libero di sperimentare con immagini e forme diverse per vedere come funziona la funzionalità di blocco delle proporzioni in vari scenari.

## Domande frequenti

### Posso sbloccare le proporzioni dopo averle bloccate?
Sì, puoi sbloccare il rapporto di aspetto impostando`shape.AspectRatioLocked = false`.

### Cosa succede se ridimensiono un'immagine con proporzioni bloccate?
L'immagine verrà ridimensionata proporzionalmente, mantenendo il rapporto larghezza-altezza originale.

### Posso applicarlo anche ad altre forme oltre alle immagini?
Assolutamente! La funzione di blocco delle proporzioni può essere applicata a qualsiasi forma, inclusi rettangoli, cerchi e altro.

### Aspose.Words per .NET è compatibile con .NET Core?
Sì, Aspose.Words per .NET supporta sia .NET Framework che .NET Core.

### Dove posso trovare ulteriore documentazione su Aspose.Words per .NET?
 Puoi trovare una documentazione completa[Qui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
