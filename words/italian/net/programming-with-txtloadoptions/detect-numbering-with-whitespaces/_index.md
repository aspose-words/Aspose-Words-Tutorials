---
"description": "Scopri come utilizzare Aspose.Words per .NET per rilevare la numerazione con spazi nei documenti di testo normale e garantire che gli elenchi vengano riconosciuti correttamente."
"linktitle": "Rileva la numerazione con spazi vuoti"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Rileva la numerazione con spazi vuoti"
"url": "/it/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rileva la numerazione con spazi vuoti

## Introduzione

Aspose.Words per gli appassionati di .NET! Oggi approfondiremo un'affascinante funzionalità che può semplificare la gestione degli elenchi nei documenti in chiaro. Avete mai avuto a che fare con file di testo in cui alcune righe dovrebbero essere elenchi, ma non appaiono correttamente una volta caricate in un documento Word? Bene, abbiamo un asso nella manica: rilevare la numerazione con gli spazi vuoti. Questo tutorial vi guiderà nell'utilizzo di Aspose.Words. `DetectNumberingWithWhitespaces` opzione in Aspose.Words per .NET per garantire che gli elenchi vengano riconosciuti correttamente, anche quando sono presenti spazi vuoti tra i numeri e il testo.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

- Aspose.Words per .NET: puoi scaricarlo da [Rilasci di Aspose](https://releases.aspose.com/words/net/) pagina.
- Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE C#.
- .NET Framework installato sul computer.
- Conoscenza di base di C#: comprendere le basi ti aiuterà a seguire gli esempi.

## Importa spazi dei nomi

Prima di iniziare a scrivere il codice, assicurati di aver importato i namespace necessari nel tuo progetto. Ecco un breve frammento per iniziare:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Scomponiamo il processo in passaggi semplici e gestibili. Ogni passaggio ti guiderà attraverso il codice necessario e ti spiegherà cosa sta succedendo.

## Passaggio 1: definire la directory dei documenti

Per prima cosa, impostiamo il percorso per la directory dei documenti. È qui che verranno archiviati i file di input e output.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: creare un documento in testo normale

Successivamente, creeremo un documento di testo normale come stringa. Questo documento conterrà parti che possono essere interpretate come elenchi.

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

Per rilevare la numerazione con spazi vuoti, dobbiamo impostare `DetectNumberingWithWhitespaces` opzione per `true` in un `TxtLoadOptions` oggetto.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Passaggio 4: caricare il documento

Ora carichiamo il documento utilizzando il `TxtLoadOptions` come parametro. Questo garantisce che la quarta lista (con spazi vuoti) venga rilevata correttamente.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Passaggio 5: salvare il documento

Infine, salva il documento nella directory specificata. Verrà generato un documento Word con gli elenchi rilevati correttamente.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Conclusione

Ed ecco fatto! Con poche righe di codice, hai imparato a rilevare la numerazione con spazi vuoti nei documenti di testo normale utilizzando Aspose.Words per .NET. Questa funzionalità può essere incredibilmente utile quando si gestiscono diversi formati di testo e si garantisce che gli elenchi siano rappresentati accuratamente nei documenti Word. Così, la prossima volta che ti imbatterai in quegli elenchi ostici, saprai esattamente cosa fare.

## Domande frequenti

### Cosa è `DetectNumberingWithWhitespaces` in Aspose.Words per .NET?
`DetectNumberingWithWhitespaces` è un'opzione in `TxtLoadOptions` che consente ad Aspose.Words di riconoscere gli elenchi anche quando sono presenti spazi vuoti tra la numerazione e il testo della voce di elenco.

### Posso usare questa funzionalità per altri delimitatori come elenchi puntati e parentesi?
Sì, Aspose.Words rileva automaticamente gli elenchi con delimitatori comuni come punti elenco e parentesi quadre. `DetectNumberingWithWhitespaces` aiuta in particolare con gli elenchi che contengono spazi vuoti.

### Cosa succede se non lo uso? `DetectNumberingWithWhitespaces`?
Senza questa opzione, gli elenchi con spazi vuoti tra la numerazione e il testo potrebbero non essere riconosciuti come elenchi e gli elementi potrebbero apparire come semplici paragrafi.

### Questa funzionalità è disponibile anche in altri prodotti Aspose?
Questa funzionalità specifica è pensata su misura per Aspose.Words per .NET, progettato per gestire l'elaborazione di documenti Word.

### Come posso ottenere una licenza temporanea per Aspose.Words per .NET?
È possibile ottenere una licenza temporanea dal [Licenza temporanea Aspose](https://purchase.aspose.com/temporary-license/) pagina.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}