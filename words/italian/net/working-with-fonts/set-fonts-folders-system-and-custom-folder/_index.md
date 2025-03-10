---
title: Imposta i font, le cartelle di sistema e le cartelle personalizzate
linktitle: Imposta i font, le cartelle di sistema e le cartelle personalizzate
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come impostare le cartelle dei font di sistema e personalizzati nei documenti Word utilizzando Aspose.Words per .NET, assicurandoti che i tuoi documenti vengano visualizzati correttamente in diversi ambienti.
weight: 10
url: /it/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta i font, le cartelle di sistema e le cartelle personalizzate

## Introduzione

Immagina di creare un documento con uno stile di font unico, solo per scoprire che i font non vengono visualizzati correttamente su un'altra macchina. Frustrante, vero? Ecco dove entra in gioco la configurazione delle cartelle dei font. Con Aspose.Words per .NET, puoi definire cartelle di font di sistema e personalizzate per garantire che i tuoi documenti abbiano sempre l'aspetto desiderato. Immergiamoci in come puoi ottenere questo risultato.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

-  Aspose.Words per la libreria .NET: se non l'hai ancora fatto, scaricalo[Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: un IDE come Visual Studio.
- Conoscenza di base di C#: la familiarità con C# ti aiuterà a seguire gli esempi di codice.

## Importazione degli spazi dei nomi

Per prima cosa, importa gli spazi dei nomi necessari nel tuo progetto:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ora scomponiamo il processo in semplici passaggi.

## Passaggio 1: caricare il documento

 Per iniziare, carica il tuo documento Word in Aspose.Words`Document` oggetto. Questo documento sarà quello in cui vuoi impostare le cartelle dei font.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 2: inizializzare le impostazioni del carattere

 Crea una nuova istanza di`FontSettings`Questo oggetto ti consentirà di gestire le fonti dei font.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Passaggio 3: Recupera le origini dei font di sistema

Recupera le fonti dei font di sistema predefinite. Su una macchina Windows, questo include in genere "Windows\Fonts\" directory.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Passaggio 4: aggiungere una cartella di font personalizzata

Aggiungi una cartella personalizzata che contiene i tuoi font aggiuntivi. Questo è utile se hai font specifici non installati nella directory dei font di sistema.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Passaggio 5: Aggiorna le origini dei font

 Convertire l'elenco delle origini dei font in un array e impostarlo su`FontSettings` oggetto.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Passaggio 6: applicare le impostazioni del carattere al documento

 Infine, applicare la configurazione`FontSettings` al tuo documento e salvalo nel formato desiderato, ad esempio PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi assicurarti che i tuoi documenti Word utilizzino i font corretti, che siano font di sistema o personalizzati archiviati in una directory specifica. Questa configurazione aiuta a mantenere l'integrità dell'aspetto del tuo documento in diversi ambienti.

## Domande frequenti

### Cosa succede se un font manca sia nella cartella di sistema che in quella personalizzata?

Aspose.Words utilizzerà un font predefinito per sostituire il font mancante, garantendo così la leggibilità del documento.

### Posso aggiungere più cartelle di font personalizzati?

 Sì, puoi aggiungere più cartelle di font personalizzati ripetendo il processo di creazione`FolderFontSource` oggetti e aggiungerli all'elenco delle sorgenti dei font.

### È possibile utilizzare percorsi di rete per cartelle di font personalizzati?

 Sì, puoi specificare un percorso di rete nel`FolderFontSource` costruttore.

### Quali formati di file supporta Aspose.Words per il salvataggio dei documenti?

Aspose.Words supporta vari formati, tra cui DOCX, PDF, HTML e altri.

### Come gestisco le notifiche di sostituzione dei font?

 È possibile gestire le notifiche di sostituzione dei font utilizzando`FontSettings` di classe`FontSubstitutionWarning`evento.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
