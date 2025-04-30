---
"description": "Scopri come inserire e manipolare forme nei documenti Word utilizzando Aspose.Words per .NET con la nostra guida dettagliata."
"linktitle": "Inserisci forma"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Inserisci forma"
"url": "/it/net/programming-with-shapes/insert-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci forma

## Introduzione

Quando si tratta di creare documenti Word visivamente accattivanti e ben strutturati, le forme possono svolgere un ruolo fondamentale. Che si aggiungano frecce, caselle o persino forme personalizzate complesse, la possibilità di manipolare questi elementi a livello di codice offre una flessibilità senza pari. In questo tutorial, esploreremo come inserire e manipolare forme nei documenti Word utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di immergerti nel tutorial, assicurati di avere i seguenti prerequisiti:

1. Aspose.Words per .NET: Scarica e installa la versione più recente da [Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: un ambiente di sviluppo .NET adatto, come Visual Studio.
3. Conoscenza di base di C#: familiarità con il linguaggio di programmazione C# e i concetti di base.

## Importa spazi dei nomi

Per iniziare, dovrai importare gli spazi dei nomi necessari nel tuo progetto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Passaggio 1: imposta il tuo progetto

Prima di poter iniziare a inserire forme, è necessario configurare il progetto e aggiungere la libreria Aspose.Words per .NET.

1. Crea un nuovo progetto: apri Visual Studio e crea un nuovo progetto di applicazione console C#.
2. Aggiungi Aspose.Words per .NET: installa la libreria Aspose.Words per .NET tramite NuGet Package Manager.

```bash
Install-Package Aspose.Words
```

## Passaggio 2: inizializzare il documento

Per prima cosa, dovrai inizializzare un nuovo documento e un generatore di documenti, che ti aiuterà a costruire il documento.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inizializzare un nuovo documento
Document doc = new Document();

// Inizializza un DocumentBuilder per facilitare la creazione del documento
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 3: inserire una forma

Ora inseriamo una forma nel documento. Inizieremo aggiungendo una semplice casella di testo.

```csharp
// Inserire una forma di casella di testo nel documento
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Ruota la forma
shape.Rotation = 30.0;
```

In questo esempio, inseriamo una casella di testo nella posizione (100, 100) con larghezza e altezza di 50 unità ciascuna. Ruotiamo anche la forma di 30 gradi.

## Passaggio 4: aggiungi un'altra forma

Aggiungiamo un'altra forma al documento, questa volta senza specificarne la posizione.

```csharp
// Aggiungi un'altra forma di casella di testo
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Ruota la forma
secondShape.Rotation = 30.0;
```

Questo frammento di codice inserisce un'altra casella di testo con le stesse dimensioni e rotazione della prima, ma senza specificarne la posizione.

## Passaggio 5: salvare il documento

Dopo aver aggiunto le forme, il passaggio finale è salvare il documento. Useremo il `OoxmlSaveOptions` per specificare il formato di salvataggio.

```csharp
// Definisci le opzioni di salvataggio con conformità
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Salva il documento
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Conclusione

Ed ecco fatto! Hai inserito e manipolato con successo le forme in un documento Word utilizzando Aspose.Words per .NET. Questo tutorial ha trattato le basi, ma Aspose.Words offre molte funzionalità più avanzate per lavorare con le forme, come stili personalizzati, connettori e forme di gruppo.

Per informazioni più dettagliate, visitare il sito [Documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/).

## Domande frequenti

### Come posso inserire diversi tipi di forme?
Puoi cambiare il `ShapeType` nel `InsertShape` Metodo per inserire diversi tipi di forme, come cerchi, rettangoli e frecce.

### Posso aggiungere del testo all'interno delle forme?
Sì, puoi usare il `builder.Write` Metodo per aggiungere testo all'interno delle forme dopo averle inserite.

### È possibile dare uno stile alle forme?
Sì, puoi definire lo stile delle forme impostando proprietà come `FillColor`, `StrokeColor`, E `StrokeWeight`.

### Come posso posizionare le forme rispetto ad altri elementi?
Utilizzare il `RelativeHorizontalPosition` E `RelativeVerticalPosition` proprietà per posizionare le forme rispetto ad altri elementi nel documento.

### Posso raggruppare più forme insieme?
Sì, Aspose.Words per .NET consente di raggruppare le forme utilizzando `GroupShape` classe.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}