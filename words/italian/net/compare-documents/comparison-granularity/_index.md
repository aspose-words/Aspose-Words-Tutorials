---
title: Granularità di confronto nel documento Word
linktitle: Granularità di confronto nel documento Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri la funzionalità Confronta granularità nei documenti Word di Aspose.Words per .NET, che consente di confrontare i documenti carattere per carattere, segnalando le modifiche apportate.
weight: 10
url: /it/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Granularità di confronto nel documento Word

Di seguito è riportata una guida dettagliata per spiegare il codice sorgente C#, che utilizza la funzionalità Confronta granularità nei documenti Word di Aspose.Words per .NET.

## Fase 1: Introduzione

La funzionalità Compare Granularity di Aspose.Words per .NET consente di confrontare i documenti a livello di carattere. Ciò significa che ogni carattere verrà confrontato e le modifiche verranno segnalate di conseguenza.

## Fase 2: Impostazione dell'ambiente

Prima di iniziare, devi configurare il tuo ambiente di sviluppo per lavorare con Aspose.Words per .NET. Assicurati di avere la libreria Aspose.Words installata e di avere un progetto C# adatto in cui incorporare il codice.

## Passaggio 3: aggiungere gli assembly richiesti

Per usare la funzionalità Compare Granularity di Aspose.Words per .NET, devi aggiungere gli assembly necessari al tuo progetto. Assicurati di avere i riferimenti corretti ad Aspose.Words nel tuo progetto.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Fase 4: Creazione di documenti

In questo passaggio, creeremo due documenti utilizzando la classe DocumentBuilder. Questi documenti saranno utilizzati per il confronto.

```csharp
// Creare il documento A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Creare il documento B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Passaggio 5: configurazione delle opzioni di confronto

In questo passaggio, configureremo le opzioni di confronto per specificare la granularità del confronto. Qui useremo la granularità a livello di carattere.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Fase 6: Confronto dei documenti

Ora confrontiamo i documenti usando il metodo Compare della classe Document. Le modifiche saranno salvate nel documento A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 IL`Compare`metodo confronta il documento A con il documento B e salva le modifiche al documento A. È possibile specificare il nome dell'autore e la data del confronto come riferimento.

## Conclusione

In questo articolo, abbiamo esplorato la funzionalità Compare Granularity di Aspose.Words per .NET. Questa funzionalità consente di confrontare i documenti a livello di carattere e segnalare le modifiche. È possibile utilizzare questa conoscenza per eseguire confronti dettagliati di documenti nei progetti.

### Esempio di codice sorgente per la granularità di confronto utilizzando Aspose.Words per .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Conclusione

In questo tutorial, abbiamo esplorato la funzionalità Comparison Granularity di Aspose.Words per .NET. Questa funzionalità consente di specificare il livello di dettaglio quando si confrontano documenti. Scegliendo diversi livelli di granularità, è possibile eseguire confronti dettagliati a livello di carattere, parola o blocco, a seconda delle esigenze specifiche. Aspose.Words per .NET fornisce una funzionalità di confronto documenti flessibile e potente, semplificando l'identificazione delle differenze nei documenti con diversi livelli di granularità.

### Domande frequenti

#### D: Qual è lo scopo dell'utilizzo della granularità di confronto in Aspose.Words per .NET?

A: La granularità di confronto in Aspose.Words per .NET consente di specificare il livello di dettaglio quando si confrontano i documenti. Con questa funzionalità, è possibile confrontare i documenti a diversi livelli, come a livello di carattere, a livello di parola o persino a livello di blocco. Ogni livello di granularità fornisce un diverso livello di dettaglio nei risultati del confronto.

#### D: Come si usa la granularità di confronto in Aspose.Words per .NET?

A: Per utilizzare la granularità di confronto in Aspose.Words per .NET, seguire questi passaggi:
1. Imposta il tuo ambiente di sviluppo con la libreria Aspose.Words.
2. Aggiungi gli assembly necessari al tuo progetto facendo riferimento ad Aspose.Words.
3.  Crea i documenti che vuoi confrontare utilizzando`DocumentBuilder` classe.
4.  Configurare le opzioni di confronto creando un`CompareOptions` oggetto e impostazione del`Granularity` proprietà al livello desiderato (ad esempio,`Granularity.CharLevel` per il confronto a livello di carattere).
5.  Utilizzare il`Compare`metodo su un documento, passando l'altro documento e il`CompareOptions` oggetto come parametri. Questo metodo confronterà i documenti in base alla granularità specificata e salverà le modifiche nel primo documento.

#### D: Quali sono i livelli di granularità del confronto disponibili in Aspose.Words per .NET?

A: Aspose.Words per .NET fornisce tre livelli di granularità di confronto:
- `Granularity.CharLevel`: Confronta i documenti a livello di carattere.
- `Granularity.WordLevel`: Confronta i documenti a livello di parola.
- `Granularity.BlockLevel`: Confronta i documenti a livello di blocco.

#### D: Come posso interpretare i risultati del confronto con granularità a livello di carattere?

R: Con la granularità a livello di carattere, ogni carattere nei documenti confrontati viene analizzato per le differenze. I risultati del confronto mostreranno i cambiamenti a livello di singolo carattere, tra cui aggiunte, eliminazioni e modifiche.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
