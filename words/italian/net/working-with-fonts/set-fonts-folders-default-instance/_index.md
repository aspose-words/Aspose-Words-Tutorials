---
"description": "Scopri come impostare le cartelle dei font per l'istanza predefinita in Aspose.Words per .NET con questo tutorial passo passo. Personalizza i tuoi documenti Word senza sforzo."
"linktitle": "Imposta istanza predefinita delle cartelle dei caratteri"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Imposta istanza predefinita delle cartelle dei caratteri"
"url": "/it/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Imposta istanza predefinita delle cartelle dei caratteri

## Introduzione

Ciao, amico programmatore! Se lavori con documenti Word in .NET, probabilmente conosci l'importanza di avere font perfetti. Oggi approfondiremo come impostare le cartelle dei font per l'istanza predefinita utilizzando Aspose.Words per .NET. Immagina di avere tutti i tuoi font personalizzati a portata di mano, con i tuoi documenti esattamente come li immagini. Fantastico, vero? Iniziamo!

## Prerequisiti

Prima di entrare nei dettagli, assicuriamoci di avere tutto ciò di cui hai bisogno:
- Aspose.Words per .NET: assicurati di aver installato la libreria. In caso contrario, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE compatibile con .NET.
- Conoscenza di base di C#: è richiesta una buona conoscenza della programmazione in C#.
- Cartella Font: una directory contenente i tuoi font personalizzati.

## Importa spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo ci aiuterà ad accedere alle classi e ai metodi necessari per impostare la cartella dei font.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Scomponiamo il processo in passaggi semplici e digeribili.

## Passaggio 1: definire la directory dei dati

Ogni grande viaggio inizia con un singolo passo, e il nostro inizia con la definizione della directory in cui è archiviato il tuo documento. È qui che Aspose.Words cercherà il tuo documento Word.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Qui, sostituisci `"YOUR DOCUMENT DIRECTORY"` Con il percorso effettivo della directory del documento. È qui che si trova il documento sorgente e dove verrà salvato l'output.

## Passaggio 2: imposta la cartella dei caratteri

Ora, indichiamo ad Aspose.Words dove trovare i tuoi font personalizzati. Questo si fa impostando la cartella dei font tramite `FontSettings.DefaultInstance.SetFontsFolder` metodo.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

In questa linea, `"C:\\MyFonts\\"` è il percorso della cartella dei tuoi font personalizzati. Il secondo parametro, `true`, indica che i font in questa cartella devono essere scansionati in modo ricorsivo.

## Passaggio 3: carica il documento

Con la cartella dei font impostata, il passo successivo è caricare il documento Word in Aspose.Words. Questo viene fatto utilizzando `Document` classe.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Qui, `dataDir + "Rendering.docx"` Si riferisce al percorso completo del documento Word. Assicurati che il documento si trovi nella directory specificata.

## Passaggio 4: salvare il documento

Il passaggio finale consiste nel salvare il documento dopo aver impostato la cartella dei font. Questo garantisce che i font personalizzati vengano applicati correttamente nell'output.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Questa riga salva il documento come PDF con i font personalizzati applicati. Il file di output si troverà nella stessa directory del documento sorgente.

## Conclusione

Ed ecco fatto! Impostare le cartelle dei font per l'istanza predefinita in Aspose.Words per .NET è un gioco da ragazzi se lo si suddivide in semplici passaggi. Seguendo questa guida, puoi assicurarti che i tuoi documenti Word abbiano esattamente l'aspetto che desideri, con tutti i tuoi font personalizzati al loro posto. Quindi, provaci e fai risplendere i tuoi documenti!

## Domande frequenti

### Posso impostare più cartelle di font?
Sì, puoi impostare più cartelle di font utilizzando `SetFontsFolders` metodo che accetta un array di percorsi di cartelle.

### Quali formati di file supporta Aspose.Words per il salvataggio dei documenti?
Aspose.Words supporta vari formati, tra cui DOCX, PDF, HTML, EPUB e altri.

### È possibile utilizzare font online in Aspose.Words?
No, attualmente Aspose.Words supporta solo file di font locali.

### Come posso assicurarmi che i miei font personalizzati siano incorporati nel PDF salvato?
Impostando il `FontSettings` correttamente e assicurandosi che i font siano disponibili, Aspose.Words li incorporerà nell'output PDF.

### Cosa succede se un font non viene trovato nella cartella specificata?
Aspose.Words utilizzerà un font di fallback se il font specificato non viene trovato.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}