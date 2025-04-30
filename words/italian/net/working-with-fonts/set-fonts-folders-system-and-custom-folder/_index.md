---
"description": "Scopri come impostare cartelle di font di sistema e personalizzati nei documenti Word utilizzando Aspose.Words per .NET, assicurandoti che i tuoi documenti vengano visualizzati correttamente in diversi ambienti."
"linktitle": "Imposta le cartelle dei caratteri di sistema e la cartella personalizzata"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Imposta le cartelle dei caratteri di sistema e la cartella personalizzata"
"url": "/it/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Imposta le cartelle dei caratteri di sistema e la cartella personalizzata

## Introduzione

Immagina di creare un documento con uno stile di font unico e di scoprire che i font non vengono visualizzati correttamente su un altro computer. Frustrante, vero? È qui che entra in gioco la configurazione delle cartelle dei font. Con Aspose.Words per .NET, puoi definire cartelle di sistema e personalizzate per i font per garantire che i tuoi documenti abbiano sempre l'aspetto desiderato. Vediamo come puoi ottenere questo risultato.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

- Aspose.Words per la libreria .NET: se non l'hai ancora fatto, scaricalo [Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: un IDE come Visual Studio.
- Conoscenza di base di C#: la familiarità con C# ti aiuterà a seguire gli esempi di codice.

## Importa spazi dei nomi

Per prima cosa, importa gli spazi dei nomi necessari nel tuo progetto:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ora scomponiamo il processo in semplici passaggi.

## Passaggio 1: caricare il documento

Per iniziare, carica il tuo documento Word in Aspose.Words `Document` oggetto. Questo sarà il documento in cui vorrai impostare le cartelle dei font.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 2: inizializzare le impostazioni del carattere

Crea una nuova istanza di `FontSettings`Questo oggetto ti consentirà di gestire le fonti dei font.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Passaggio 3: recuperare le fonti dei font di sistema

Recupera le fonti predefinite dei font di sistema. Su un computer Windows, questo in genere include la directory "Windows\Fonts".

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Passaggio 4: aggiungere una cartella di font personalizzata

Aggiungi una cartella personalizzata contenente i tuoi font aggiuntivi. Questa opzione è utile se hai font specifici non installati nella directory di sistema.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Passaggio 5: aggiorna le origini dei font

Convertire l'elenco delle sorgenti dei font in un array e impostarlo su `FontSettings` oggetto.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Passaggio 6: applicare le impostazioni del carattere al documento

Infine, applicare la configurazione `FontSettings` al tuo documento e salvalo nel formato desiderato, ad esempio PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi assicurarti che i tuoi documenti Word utilizzino i font corretti, che si tratti di font di sistema o personalizzati memorizzati in una directory specifica. Questa configurazione aiuta a mantenere l'integrità dell'aspetto del documento in diversi ambienti.

## Domande frequenti

### Cosa succede se un font manca sia nella cartella di sistema che in quella personalizzata?

Aspose.Words utilizzerà un font predefinito per sostituire il font mancante, garantendo così la leggibilità del documento.

### Posso aggiungere più cartelle di font personalizzati?

Sì, puoi aggiungere più cartelle di font personalizzati ripetendo il processo di creazione `FolderFontSource` oggetti e aggiungerli all'elenco delle sorgenti dei font.

### È possibile utilizzare percorsi di rete per cartelle di font personalizzati?

Sì, puoi specificare un percorso di rete nel `FolderFontSource` costruttore.

### Quali formati di file supporta Aspose.Words per il salvataggio dei documenti?

Aspose.Words supporta vari formati, tra cui DOCX, PDF, HTML e altri.

### Come gestisco le notifiche di sostituzione dei font?

È possibile gestire le notifiche di sostituzione dei font utilizzando `FontSettings` della classe `FontSubstitutionWarning` evento.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}