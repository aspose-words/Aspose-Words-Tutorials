---
"description": "Scopri come preservare i caratteri di controllo legacy nei documenti Word utilizzando Aspose.Words per .NET con questa guida dettagliata."
"linktitle": "Mantieni i caratteri di controllo legacy"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Mantieni i caratteri di controllo legacy"
"url": "/it/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mantieni i caratteri di controllo legacy

## Introduzione

Vi siete mai chiesti perché quei caratteri di controllo strani e invisibili nei vostri documenti Word vi abbiano incuriosito? Sono come piccoli gremlin nascosti che possono compromettere la formattazione e la funzionalità. Fortunatamente, Aspose.Words per .NET offre una comoda funzionalità per mantenere intatti questi caratteri di controllo legacy durante il salvataggio dei documenti. In questo tutorial, approfondiremo la gestione di questi caratteri di controllo utilizzando Aspose.Words per .NET. Lo spiegheremo passo dopo passo, assicurandovi di comprendere ogni dettaglio. Pronti a iniziare? Cominciamo!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. Aspose.Words per .NET: Scarica e installa da [Qui](https://releases.aspose.com/words/net/).
2. Una licenza Aspose valida: puoi ottenere una licenza temporanea [Qui](https://purchase.aspose.com/temporary-license/).
3. Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE che supporti .NET.
4. Conoscenza di base di C#: sarà utile avere familiarità con il linguaggio di programmazione C#.

## Importa spazi dei nomi

Prima di scrivere il codice, è necessario importare gli spazi dei nomi necessari. Aggiungere le seguenti righe all'inizio del file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: impostazione del progetto

Per prima cosa, dovrai configurare il progetto in Visual Studio (o nel tuo IDE preferito). 

1. Crea un nuovo progetto C#: apri Visual Studio e crea un nuovo progetto Applicazione console C#.
2. Installa Aspose.Words per .NET: utilizza NuGet Package Manager per installare Aspose.Words per .NET. Fai clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, seleziona "Gestisci pacchetti NuGet", cerca "Aspose.Words" e installalo.

## Passaggio 2: carica il documento

Successivamente, caricherai il documento Word che contiene i caratteri di controllo legacy.

1. Specificare il percorso del documento: imposta il percorso della directory del documento.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. Carica il documento: usa il `Document` classe per caricare il documento.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Passaggio 3: configurare le opzioni di salvataggio

Ora configuriamo le opzioni di salvataggio per mantenere intatti i caratteri di controllo legacy.

1. Crea opzioni di salvataggio: Inizializza un'istanza di `OoxmlSaveOptions` e impostare il `KeepLegacyControlChars` proprietà a `true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Passaggio 4: salvare il documento

Infine, salva il documento con le opzioni di salvataggio configurate.

1. Salvare il documento: utilizzare il `Save` metodo del `Document` classe per salvare il documento con le opzioni di salvataggio specificate.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi garantire che i tuoi caratteri di controllo legacy vengano mantenuti quando lavori con documenti Word in Aspose.Words per .NET. Questa funzionalità può rivelarsi una vera e propria salvezza, soprattutto quando si tratta di documenti complessi in cui i caratteri di controllo svolgono un ruolo cruciale. 

## Domande frequenti

### Cosa sono i caratteri di controllo legacy?

I caratteri di controllo legacy sono caratteri non stampabili utilizzati nei documenti più vecchi per controllare la formattazione e il layout.

### Posso rimuovere questi caratteri di controllo invece di mantenerli?

Sì, puoi utilizzare Aspose.Words per .NET per rimuovere o sostituire questi caratteri, se necessario.

### Questa funzionalità è disponibile in tutte le versioni di Aspose.Words per .NET?

Questa funzionalità è disponibile nelle versioni più recenti. Assicurati di utilizzare la versione più recente per accedere a tutte le funzionalità.

### Ho bisogno di una licenza per utilizzare Aspose.Words per .NET?

Sì, è necessaria una licenza valida. È possibile ottenere una licenza temporanea a scopo di valutazione. [Qui](https://purchase.aspose.com/temporary-license/).

### Dove posso trovare ulteriore documentazione su Aspose.Words per .NET?

Puoi trovare la documentazione dettagliata [Qui](https://reference.aspose.com/words/net/).
 


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}