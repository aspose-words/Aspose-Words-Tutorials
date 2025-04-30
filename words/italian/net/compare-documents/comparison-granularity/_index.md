---
"description": "Scopri la funzionalità Confronta granularità nei documenti Word di Aspose.Words per .NET, che consente di confrontare i documenti carattere per carattere, segnalando le modifiche apportate."
"linktitle": "Granularità del confronto nel documento Word"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Granularità del confronto nel documento Word"
"url": "/it/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Granularità del confronto nel documento Word

Di seguito è riportata una guida dettagliata che spiega il codice sorgente C#, che utilizza la funzionalità Confronta granularità nei documenti Word di Aspose.Words per .NET.

## Fase 1: Introduzione

La funzionalità "Confronta granularità" di Aspose.Words per .NET consente di confrontare i documenti a livello di carattere. Ciò significa che ogni carattere verrà confrontato e le modifiche verranno segnalate di conseguenza.

## Fase 2: Impostazione dell'ambiente

Prima di iniziare, è necessario configurare l'ambiente di sviluppo per Aspose.Words per .NET. Assicurarsi di aver installato la libreria Aspose.Words e di avere un progetto C# adatto in cui incorporare il codice.

## Passaggio 3: aggiungere gli assembly richiesti

Per utilizzare la funzionalità Confronta Granularità di Aspose.Words per .NET, è necessario aggiungere gli assembly necessari al progetto. Assicurarsi di avere i riferimenti corretti ad Aspose.Words nel progetto.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Fase 4: Creazione di documenti

In questa fase, creeremo due documenti utilizzando la classe DocumentBuilder. Questi documenti verranno utilizzati per il confronto.

```csharp
// Creare il documento A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Creare il documento B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Passaggio 5: configurazione delle opzioni di confronto

In questa fase, configureremo le opzioni di confronto per specificare la granularità del confronto. Qui utilizzeremo la granularità a livello di carattere.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Fase 6: Confronto dei documenti

Ora confrontiamo i documenti usando il metodo Compare della classe Document. Le modifiche verranno salvate nel documento A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

IL `Compare` Il metodo confronta il documento A con il documento B e salva le modifiche nel documento A. È possibile specificare il nome dell'autore e la data del confronto come riferimento.

## Conclusione

In questo articolo abbiamo esplorato la funzionalità "Compare Granularity" di Aspose.Words per .NET. Questa funzionalità consente di confrontare i documenti a livello di carattere e di segnalare le modifiche. È possibile utilizzare queste informazioni per eseguire confronti dettagliati dei documenti nei propri progetti.

### Esempio di codice sorgente per la granularità del confronto utilizzando Aspose.Words per .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Conclusione

In questo tutorial abbiamo esplorato la funzionalità di granularità del confronto di Aspose.Words per .NET. Questa funzionalità consente di specificare il livello di dettaglio durante il confronto dei documenti. Scegliendo diversi livelli di granularità, è possibile eseguire confronti dettagliati a livello di carattere, parola o blocco, a seconda delle esigenze specifiche. Aspose.Words per .NET offre una funzionalità di confronto dei documenti flessibile e potente, che semplifica l'identificazione delle differenze nei documenti con diversi livelli di granularità.

### Domande frequenti

#### D: Qual è lo scopo dell'utilizzo della granularità di confronto in Aspose.Words per .NET?

R: La granularità del confronto in Aspose.Words per .NET consente di specificare il livello di dettaglio durante il confronto dei documenti. Con questa funzionalità, è possibile confrontare documenti a diversi livelli, come a livello di carattere, di parola o persino di blocco. Ogni livello di granularità fornisce un diverso livello di dettaglio nei risultati del confronto.

#### D: Come si usa la granularità di confronto in Aspose.Words per .NET?

A: Per utilizzare la granularità di confronto in Aspose.Words per .NET, seguire questi passaggi:
1. Imposta il tuo ambiente di sviluppo con la libreria Aspose.Words.
2. Aggiungi gli assembly necessari al tuo progetto facendo riferimento ad Aspose.Words.
3. Crea i documenti che vuoi confrontare utilizzando `DocumentBuilder` classe.
4. Configurare le opzioni di confronto creando un `CompareOptions` oggetto e impostazione del `Granularity` proprietà al livello desiderato (ad esempio, `Granularity.CharLevel` per il confronto a livello di personaggio).
5. Utilizzare il `Compare` metodo su un documento, passando l'altro documento e il `CompareOptions` oggetto come parametri. Questo metodo confronterà i documenti in base alla granularità specificata e salverà le modifiche nel primo documento.

#### D: Quali sono i livelli di granularità del confronto disponibili in Aspose.Words per .NET?

A: Aspose.Words per .NET offre tre livelli di granularità di confronto:
- `Granularity.CharLevel`: Confronta i documenti a livello di carattere.
- `Granularity.WordLevel`: Confronta i documenti a livello di parola.
- `Granularity.BlockLevel`: Confronta i documenti a livello di blocco.

#### D: Come posso interpretare i risultati del confronto con granularità a livello di carattere?

R: Con la granularità a livello di carattere, ogni carattere nei documenti confrontati viene analizzato per individuare eventuali differenze. I risultati del confronto mostreranno le modifiche a livello di singolo carattere, incluse aggiunte, eliminazioni e modifiche.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}