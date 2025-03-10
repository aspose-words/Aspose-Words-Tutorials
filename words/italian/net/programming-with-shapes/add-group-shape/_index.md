---
title: Aggiungi forma di gruppo
linktitle: Aggiungi forma di gruppo
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come aggiungere forme di gruppo ai documenti Word utilizzando Aspose.Words per .NET con questo tutorial completo e dettagliato.
weight: 10
url: /it/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi forma di gruppo

## Introduzione

Creare documenti complessi con elementi visivi ricchi può a volte essere un compito arduo, soprattutto quando si ha a che fare con forme di gruppo. Ma non temere! Aspose.Words per .NET semplifica questo processo, rendendolo facile come una torta. In questo tutorial, ti guideremo attraverso i passaggi per aggiungere forme di gruppo ai tuoi documenti Word. Pronti a tuffarcisi? Cominciamo!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1.  Aspose.Words per .NET: puoi scaricarlo da[Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE compatibile con .NET.
3. Conoscenza di base di C#: la familiarità con la programmazione C# è un plus.

## Importazione degli spazi dei nomi

Per iniziare, dobbiamo importare i namespace necessari nel nostro progetto. Questi namespace forniscono accesso alle classi e ai metodi richiesti per manipolare documenti Word con Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Passaggio 1: inizializzare il documento

Per prima cosa, inizializziamo un nuovo documento Word. Immagina di creare una tela bianca in cui aggiungeremo le nostre forme di gruppo.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Qui,`EnsureMinimum()` aggiunge un set minimo di nodi necessari per il documento.

## Passaggio 2: creare l'oggetto GroupShape

 Successivamente, dobbiamo creare un`GroupShape`oggetto. Questo oggetto servirà da contenitore per altre forme, consentendoci di raggrupparle insieme.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Passaggio 3: aggiungere forme al GroupShape

 Ora, aggiungiamo forme individuali al nostro`GroupShape` contenitore. Inizieremo con una forma di bordo accentato e poi aggiungeremo una forma di pulsante di azione.

### Aggiunta di una forma di bordo accentato

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Questo frammento di codice crea una forma di bordo accentato con una larghezza e un'altezza di 100 unità e la aggiunge a`GroupShape`.

### Aggiunta di una forma di pulsante di azione

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Qui creiamo una forma di pulsante di azione, la posizioniamo e la aggiungiamo al nostro`GroupShape`.

## Passaggio 4: definire le dimensioni di GroupShape

 Per garantire che le nostre forme si adattino bene al gruppo, dobbiamo impostare le dimensioni del`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Questo definisce la larghezza e l'altezza del`GroupShape` come 200 unità e imposta di conseguenza la dimensione delle coordinate.

## Passaggio 5: inserire GroupShape nel documento

 Ora inseriamo il nostro`GroupShape` nel documento utilizzando`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` fornisce un modo semplice per aggiungere nodi, comprese forme, al documento.

## Passaggio 6: Salvare il documento

Infine, salva il documento nella directory specificata.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Ed ecco fatto! Il tuo documento con le forme di gruppo è pronto.

## Conclusione

Aggiungere forme di gruppo ai tuoi documenti Word non deve essere un processo complicato. Con Aspose.Words per .NET, puoi creare e manipolare forme con facilità, rendendo i tuoi documenti visivamente più accattivanti e funzionali. Segui i passaggi descritti in questo tutorial e diventerai un professionista in men che non si dica!

## Domande frequenti

### Posso aggiungere più di due forme a un GroupShape?
 Sì, puoi aggiungere tutte le forme di cui hai bisogno a un`GroupShape` . Usa semplicemente il`AppendChild` metodo per ogni forma.

### È possibile definire lo stile delle forme all'interno di un GroupShape?
 Assolutamente! Ogni forma può essere stilizzata individualmente utilizzando le proprietà disponibili in`Shape` classe.

### Come posso posizionare GroupShape all'interno del documento?
 Puoi posizionare il`GroupShape` impostando il suo`Left` E`Top` proprietà.

### Posso aggiungere testo alle forme all'interno di GroupShape?
 Sì, puoi aggiungere testo alle forme utilizzando`AppendChild` metodo per aggiungere un`Paragraph` contenente`Run` nodi con testo.

### È possibile raggruppare le forme in modo dinamico in base all'input dell'utente?
Sì, è possibile creare e raggruppare dinamicamente le forme in base all'input dell'utente, modificando di conseguenza le proprietà e i metodi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
