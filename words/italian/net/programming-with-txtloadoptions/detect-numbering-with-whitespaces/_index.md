---
title: Rileva la numerazione con gli spazi vuoti
linktitle: Rileva la numerazione con gli spazi vuoti
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come utilizzare Aspose.Words per .NET per rilevare la numerazione con spazi nei documenti di testo normale e garantire che i tuoi elenchi vengano riconosciuti correttamente.
weight: 10
url: /it/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rileva la numerazione con gli spazi vuoti

## Introduzione

Aspose.Words per gli appassionati di .NET! Oggi ci immergiamo in una funzionalità affascinante che può semplificare la gestione degli elenchi nei documenti in testo normale. Hai mai avuto a che fare con file di testo in cui alcune righe dovrebbero essere elenchi, ma non sembrano proprio corretti quando vengono caricati in un documento Word? Bene, abbiamo un bel trucco nella manica: rilevare la numerazione con spazi vuoti. Questo tutorial ti guiderà attraverso l'uso di`DetectNumberingWithWhitespaces` opzione in Aspose.Words per .NET per garantire che gli elenchi vengano riconosciuti correttamente, anche quando sono presenti spazi vuoti tra i numeri e il testo.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

-  Aspose.Words per .NET: puoi scaricarlo da[Rilasci di Aspose](https://releases.aspose.com/words/net/) pagina.
- Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE C#.
- .NET Framework installato sul tuo computer.
- Conoscenza di base di C#: comprendere le basi ti aiuterà a seguire gli esempi.

## Importazione degli spazi dei nomi

Prima di buttarti nel codice, assicurati di aver importato i namespace necessari nel tuo progetto. Ecco un breve frammento per iniziare:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Analizziamo il processo in semplici passaggi gestibili. Ogni passaggio ti guiderà attraverso il codice necessario e spiegherà cosa sta succedendo.

## Passaggio 1: definire la directory dei documenti

Per prima cosa, impostiamo il percorso per la directory dei tuoi documenti. È qui che verranno archiviati i tuoi file di input e output.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: creare un documento in testo normale

Successivamente, creeremo un documento di testo normale come stringa. Questo documento conterrà parti che potrebbero essere interpretate come elenchi.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Passaggio 3: configurare LoadOptions

 Per rilevare la numerazione con spazi vuoti, dobbiamo impostare`DetectNumberingWithWhitespaces` opzione per`true` in un`TxtLoadOptions` oggetto.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Passaggio 4: caricare il documento

 Ora carichiamo il documento utilizzando`TxtLoadOptions` come parametro. Ciò assicura che il quarto elenco (con spazi vuoti) venga rilevato correttamente.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Passaggio 5: Salvare il documento

Infine, salva il documento nella directory specificata. Questo produrrà un documento Word con elenchi rilevati correttamente.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Conclusione

Ed ecco fatto! Con solo poche righe di codice, hai padroneggiato l'arte di rilevare la numerazione con spazi vuoti nei documenti di testo normale usando Aspose.Words per .NET. Questa funzionalità può essere incredibilmente utile quando si ha a che fare con vari formati di testo e si garantisce che i tuoi elenchi siano rappresentati in modo accurato nei tuoi documenti Word. Quindi la prossima volta che ti imbatterai in quegli elenchi difficili, saprai esattamente cosa fare.

## Domande frequenti

###  Cosa è`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` è un'opzione in`TxtLoadOptions` che consente ad Aspose.Words di riconoscere gli elenchi anche quando sono presenti spazi vuoti tra la numerazione e il testo dell'elemento dell'elenco.

### Posso usare questa funzionalità per altri delimitatori come elenchi puntati e parentesi?
 Sì, Aspose.Words rileva automaticamente gli elenchi con delimitatori comuni come punti elenco e parentesi.`DetectNumberingWithWhitespaces` aiuta in particolare con gli elenchi che contengono spazi vuoti.

###  Cosa succede se non lo uso`DetectNumberingWithWhitespaces`?
Senza questa opzione, gli elenchi con spazi vuoti tra la numerazione e il testo potrebbero non essere riconosciuti come elenchi e gli elementi potrebbero apparire come semplici paragrafi.

### Questa funzionalità è disponibile in altri prodotti Aspose?
Questa funzionalità specifica è pensata su misura per Aspose.Words per .NET, progettato per gestire l'elaborazione dei documenti Word.

### Come posso ottenere una licenza temporanea per Aspose.Words per .NET?
 È possibile ottenere una licenza temporanea dall'[Licenza temporanea Aspose](https://purchase.aspose.com/temporary-license/) pagina.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
