---
"description": "Padroneggia l'unione verticale nelle tabelle di Word utilizzando Aspose.Words per .NET con questa guida dettagliata. Scopri istruzioni dettagliate per una formattazione professionale dei documenti."
"linktitle": "Unione verticale"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Unione verticale"
"url": "/it/net/programming-with-tables/vertical-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Unione verticale

## Introduzione

Ti sei mai trovato invischiato nella complessità della gestione delle tabelle nei documenti Word? Con Aspose.Words per .NET, puoi semplificare il tuo lavoro e rendere i tuoi documenti più organizzati e accattivanti. In questo tutorial, approfondiremo il processo di unione verticale nelle tabelle, una funzionalità utile che consente di unire le celle verticalmente, creando un flusso di dati fluido. Che tu stia creando fatture, report o qualsiasi documento che includa dati tabellari, padroneggiare l'unione verticale può portare la formattazione dei tuoi documenti a un livello superiore.

## Prerequisiti

Prima di addentrarci nei dettagli dell'unione verticale, assicuriamoci di aver configurato tutto per un'esperienza fluida. Ecco cosa ti servirà:

- Aspose.Words per .NET: assicurati di aver installato Aspose.Words per .NET. In caso contrario, puoi scaricarlo da [Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: un ambiente di sviluppo funzionante come Visual Studio.
- Conoscenza di base di C#: sarà utile avere familiarità con il linguaggio di programmazione C#.

## Importa spazi dei nomi

Per iniziare a lavorare con Aspose.Words, è necessario importare gli spazi dei nomi necessari nel progetto. Questo può essere fatto aggiungendo le seguenti righe all'inizio del codice:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ora che abbiamo definito i prerequisiti e importato gli spazi dei nomi, passiamo alla guida dettagliata all'unione verticale.

## Passaggio 1: impostazione del documento

Il primo passo è creare un nuovo documento e un generatore di documenti. Il generatore di documenti ci aiuterà ad aggiungere e manipolare facilmente gli elementi al suo interno.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Qui creiamo un nuovo documento e inizializziamo un oggetto DocumentBuilder per lavorare con il nostro documento.

## Passaggio 2: inserimento della prima cella

Ora inseriamo la prima cella nella nostra tabella e impostiamo la sua unione verticale sulla prima cella di un intervallo unito.

```csharp
builder.InsertCell();
builder.CellFormat.VerticalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

In questo passaggio, inseriamo la prima cella e impostiamo la sua proprietà di unione verticale su `CellMerge.First`, indicando che questa è la cella iniziale dell'unione. Aggiungiamo quindi del testo a questa cella.

## Passaggio 3: inserimento della seconda cella nella stessa riga

Successivamente inseriamo un'altra cella nella stessa riga, ma non la uniamo verticalmente.

```csharp
builder.InsertCell();
builder.CellFormat.VerticalMerge = CellMerge.None;
builder.Write("Text in one cell");
builder.EndRow();
```

Qui inseriamo una cella, impostiamo la sua proprietà di unione verticale su `CellMerge.None`e aggiungiamo del testo. Quindi concludiamo la riga corrente.

## Passaggio 4: inserimento della seconda riga e unione verticale

In questo passaggio inseriamo la seconda riga e uniamo verticalmente la prima cella con la cella superiore.

```csharp
builder.InsertCell();
// Questa cella è unita verticalmente alla cella soprastante e dovrebbe essere vuota.
builder.CellFormat.VerticalMerge = CellMerge.Previous;
builder.InsertCell();
builder.CellFormat.VerticalMerge = CellMerge.None;
builder.Write("Text in another cell");
builder.EndRow();
builder.EndTable();
```

Iniziamo inserendo una cella e impostando la sua proprietà di unione verticale su `CellMerge.Previous`, indicando che deve essere unita alla cella superiore. Quindi inseriamo un'altra cella nella stessa riga, aggiungiamo del testo e concludiamo la tabella.

## Passaggio 5: salvataggio del documento

Infine, salviamo il nostro documento nella directory specificata.

```csharp
doc.Save(dataDir + "WorkingWithTables.VerticalMerge.docx");
```

Questa riga salva il documento con il nome file specificato nella directory designata.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, hai implementato con successo l'unione verticale in un documento Word utilizzando Aspose.Words per .NET. Questa funzionalità può migliorare significativamente la leggibilità e l'organizzazione dei tuoi documenti, rendendoli più professionali e facili da consultare. Che tu abbia a che fare con semplici tabelle o strutture dati complesse, padroneggiare l'unione verticale ti darà un vantaggio nella formattazione dei documenti.

## Domande frequenti

### Cos'è l'unione verticale nelle tabelle di Word?
L'unione verticale consente di unire più celle di una colonna in un'unica cella, creando un layout di tabella più snello e organizzato.

### Posso unire le celle sia verticalmente che orizzontalmente?
Sì, Aspose.Words per .NET supporta sia l'unione verticale che quella orizzontale delle celle in una tabella.

### Aspose.Words per .NET è compatibile con le diverse versioni di Word?
Sì, Aspose.Words per .NET è compatibile con diverse versioni di Microsoft Word, garantendo il funzionamento ottimale dei tuoi documenti su diverse piattaforme.

### Per utilizzare Aspose.Words per .NET è necessario avere installato Microsoft Word?
No, Aspose.Words per .NET funziona indipendentemente da Microsoft Word. Non è necessario che Word sia installato sul computer per creare o modificare documenti Word.

### Posso usare Aspose.Words per .NET per manipolare documenti Word esistenti?
Assolutamente sì! Aspose.Words per .NET consente di creare, modificare e gestire documenti Word esistenti con facilità.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}