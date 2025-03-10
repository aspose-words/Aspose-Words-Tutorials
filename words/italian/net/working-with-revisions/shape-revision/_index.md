---
title: Revisione della forma
linktitle: Revisione della forma
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come gestire le revisioni delle forme nei documenti Word usando Aspose.Words per .NET con questa guida completa. Padroneggia il tracciamento delle modifiche, l'inserimento di forme e altro ancora.
weight: 10
url: /it/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Revisione della forma

## Introduzione

Modificare i documenti Word a livello di programmazione può essere un compito arduo, soprattutto quando si tratta di gestire le forme. Che tu stia creando report, progettando modelli o semplicemente automatizzando la creazione di documenti, la capacità di tracciare e gestire le revisioni delle forme è fondamentale. Aspose.Words per .NET offre una potente API per rendere questo processo fluido ed efficiente. In questo tutorial, approfondiremo le specifiche della revisione delle forme nei documenti Word, assicurandoti di avere gli strumenti e le conoscenze per gestire i tuoi documenti con facilità.

## Prerequisiti

Prima di immergerci nel codice, assicuriamoci di avere tutto ciò di cui hai bisogno:

-  Aspose.Words per .NET: assicurati di avere installata la libreria Aspose.Words. Puoi[scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: dovresti avere configurato un ambiente di sviluppo, come Visual Studio.
- Nozioni di base di C#: familiarità con il linguaggio di programmazione C# e concetti di base della programmazione orientata agli oggetti.
- Documento Word: un documento Word con cui lavorare oppure puoi crearne uno durante il tutorial.

## Importazione degli spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questi ci forniranno l'accesso alle classi e ai metodi richiesti per gestire documenti e forme di Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Passaggio 1: impostazione della directory dei documenti

Prima di iniziare a lavorare con le forme, dobbiamo definire il percorso della nostra directory dei documenti. È qui che salveremo i nostri documenti modificati.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: creazione di un nuovo documento

Creiamo un nuovo documento Word in cui inseriremo e modificheremo le forme.

```csharp
Document doc = new Document();
```

## Passaggio 3: inserimento di una forma in linea

Inizieremo inserendo una forma in linea nel nostro documento senza tracciare le revisioni. Una forma in linea è una forma che scorre con il testo.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Fase 4: Inizio del monitoraggio delle revisioni

Per tracciare le modifiche nel nostro documento, dobbiamo abilitare il monitoraggio delle revisioni. Ciò è essenziale per identificare le modifiche apportate alle forme.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Passaggio 5: inserimento di un'altra forma con revisioni

Ora che il monitoraggio delle revisioni è abilitato, inseriamo un'altra forma. Questa volta, tutte le modifiche saranno monitorate.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Passaggio 6: recupero e modifica delle forme

Possiamo recuperare tutte le forme nel documento e modificarle come necessario. Qui, otterremo le forme e rimuoveremo la prima.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Passaggio 7: salvataggio del documento

Dopo aver apportato le modifiche, dobbiamo salvare il documento. Questo assicura che tutte le revisioni e le modifiche siano archiviate.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Fase 8: Gestione delle revisioni dello spostamento delle forme

Quando una forma viene spostata, Aspose.Words la traccia come una revisione. Ciò significa che ci saranno due istanze della forma: una nella sua posizione originale e una nella sua nuova posizione.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Conclusione

Ed ecco fatto! Hai imparato con successo a gestire le revisioni delle forme nei documenti Word usando Aspose.Words per .NET. Che tu stia gestendo modelli di documenti, automatizzando report o semplicemente tenendo traccia delle modifiche, queste competenze sono inestimabili. Seguendo questa guida passo passo, non solo hai padroneggiato le basi, ma hai anche acquisito informazioni su tecniche di gestione dei documenti più avanzate.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria che consente agli sviluppatori di creare, modificare e convertire documenti Word a livello di programmazione utilizzando C#.

### Posso tenere traccia delle modifiche apportate ad altri elementi in un documento Word?
Sì, Aspose.Words per .NET supporta il monitoraggio delle modifiche apportate a vari elementi, tra cui testo, tabelle e altro ancora.

### Come posso ottenere una prova gratuita di Aspose.Words per .NET?
 Puoi ottenere una prova gratuita di Aspose.Words per .NET[Qui](https://releases.aspose.com/).

### È possibile accettare o rifiutare le revisioni a livello di programmazione?
Sì, Aspose.Words per .NET fornisce metodi per accettare o rifiutare le revisioni a livello di programmazione.

### Posso usare Aspose.Words per .NET con altri linguaggi .NET oltre a C#?
Assolutamente! Aspose.Words per .NET può essere utilizzato con qualsiasi linguaggio .NET, inclusi VB.NET e F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
