---
title: Ottieni l'elenco dei font disponibili
linktitle: Ottieni l'elenco dei font disponibili
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come ottenere un elenco di font disponibili usando Aspose.Words per .NET in questo tutorial dettagliato passo dopo passo. Potenzia le tue competenze di gestione dei font.
weight: 10
url: /it/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ottieni l'elenco dei font disponibili

## Introduzione

Ti è mai capitato di avere difficoltà a gestire i font nei tuoi documenti Word? Se sei uno sviluppatore .NET, Aspose.Words per .NET è qui per salvarti! Questa potente libreria non solo ti aiuta a creare e manipolare i documenti Word a livello di programmazione, ma offre anche ampie capacità di gestione dei font. In questa guida, ti guideremo attraverso un tutorial passo dopo passo su come ottenere un elenco di font disponibili utilizzando Aspose.Words per .NET. Lo suddivideremo in passaggi digeribili per assicurarti di poter seguire con facilità. Quindi, tuffiamoci e rendiamo la gestione dei font un gioco da ragazzi!

## Prerequisiti

Prima di iniziare, ecco alcune cose di cui avrai bisogno:

-  Aspose.Words per .NET: assicurati di avere installata la libreria Aspose.Words per .NET. Puoi scaricarla da[Qui](https://releases.aspose.com/words/net/).
- Visual Studio: questo esempio utilizza Visual Studio come ambiente di sviluppo.
- .NET Framework: assicurati che .NET Framework sia installato sul tuo computer.
- Directory dei documenti: percorso della directory in cui sono archiviati i documenti.

## Importazione degli spazi dei nomi

Per prima cosa, importa gli spazi dei nomi necessari nel tuo progetto:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Passaggio 1: inizializzare le impostazioni del carattere

Il primo passo è inizializzare le impostazioni dei font. Questo ti consentirà di gestire le fonti dei font per i tuoi documenti.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: questa classe viene utilizzata per specificare le impostazioni per la sostituzione dei font e le origini dei font.
- fontSources: creiamo un elenco di fonti di font esistenti a partire dalle impostazioni correnti dei font.

## Passaggio 2: definire la directory dei documenti

Poi, specifica il percorso alla directory del tuo documento. È qui che Aspose.Words cercherà i font.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Questa variabile stringa contiene il percorso alla directory in cui si trovano i tuoi font. Sostituisci`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo.

## Passaggio 3: Aggiungi cartella font personalizzata

Ora aggiungi una nuova cartella sorgente per indicare ad Aspose.Words di cercare i font in questa cartella.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: questa classe rappresenta una sorgente di font di cartelle. Il secondo parametro (`true`) indica se cercare i font in modo ricorsivo nelle sottocartelle.

## Passaggio 4: Aggiorna le origini dei font

Aggiungere la cartella dei font personalizzati all'elenco delle origini dei font esistenti e aggiornare le impostazioni dei font.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): aggiunge la cartella dei font personalizzati alle sorgenti dei font esistenti.
- updatedFontSources: converte l'elenco delle sorgenti dei font in un array.

## Passaggio 5: Recupera e visualizza i font

Infine, recupera i font disponibili e visualizzane i dettagli.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): recupera l'elenco dei font disponibili dalla prima sorgente di font nell'elenco aggiornato.
-  fontInfo: Un'istanza di`PhysicalFontInfo` contenente dettagli su ciascun font.

## Conclusione

Congratulazioni! Hai recuperato con successo un elenco di font disponibili utilizzando Aspose.Words per .NET. Questo tutorial ti ha guidato attraverso ogni passaggio, dall'inizializzazione delle impostazioni dei font alla visualizzazione dei dettagli dei font. Con questa conoscenza, ora puoi gestire i font nei tuoi documenti Word con facilità. Ricorda, Aspose.Words per .NET è uno strumento potente che può migliorare significativamente le tue capacità di elaborazione dei documenti. Quindi, vai avanti ed esplora altre funzionalità per rendere il tuo processo di sviluppo ancora più efficiente.

## Domande frequenti

### Posso usare Aspose.Words per .NET con altri framework .NET?
Sì, Aspose.Words per .NET è compatibile con vari framework .NET, tra cui .NET Core e .NET 5+.

### Come faccio a installare Aspose.Words per .NET?
È possibile installarlo tramite NuGet Package Manager in Visual Studio cercando "Aspose.Words".

### È possibile aggiungere più cartelle di font personalizzati?
 Sì, puoi aggiungere più cartelle di font personalizzati creandone più`FolderFontSource` istanze e aggiungerle all'elenco delle origini dei font.

### Posso recuperare i dettagli di un font da una fonte specifica?
 Sì, puoi recuperare i dettagli del font da qualsiasi sorgente di font specificando l'indice della sorgente di font in`updatedFontSources` vettore.

### Aspose.Words per .NET supporta la sostituzione dei font?
Sì, supporta la sostituzione dei font per garantire che il testo venga visualizzato correttamente anche se il font originale non è disponibile.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
