---
title: Imposta le cartelle dei font come istanza predefinita
linktitle: Imposta le cartelle dei font come istanza predefinita
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come impostare le cartelle dei font per l'istanza predefinita in Aspose.Words per .NET con questo tutorial passo dopo passo. Personalizza i tuoi documenti Word senza sforzo.
weight: 10
url: /it/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta le cartelle dei font come istanza predefinita

## Introduzione

Ciao, collega programmatore! Se lavori con documenti Word in .NET, probabilmente sai quanto sia importante avere i font giusti. Oggi, ci immergiamo in come impostare le cartelle dei font per l'istanza predefinita usando Aspose.Words per .NET. Immagina di avere tutti i tuoi font personalizzati a portata di mano, che rendono i tuoi documenti esattamente come li immagini. Sembra fantastico, vero? Cominciamo!

## Prerequisiti

Prima di addentrarci nei dettagli, assicuriamoci di avere tutto ciò di cui hai bisogno:
-  Aspose.Words per .NET: assicurati di avere la libreria installata. In caso contrario, puoi[scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE compatibile con .NET.
- Conoscenza di base di C#: è richiesta una certa dimestichezza con la programmazione in C#.
- Cartella Font: una directory contenente i tuoi font personalizzati.

## Importazione degli spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo aiuta ad accedere alle classi e ai metodi richiesti per impostare la cartella dei font.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Scomponiamo il processo in passaggi semplici e digeribili.

## Passaggio 1: definire la directory dei dati

Ogni grande viaggio inizia con un singolo passo, e il nostro inizia con la definizione della directory in cui è archiviato il tuo documento. È qui che Aspose.Words cercherà il tuo documento Word.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Qui, sostituisci`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo della directory del tuo documento. È qui che si trova il tuo documento sorgente e dove verrà salvato l'output.

## Passaggio 2: impostare la cartella dei caratteri

 Ora, diciamo ad Aspose.Words dove trovare i tuoi font personalizzati. Questo si fa impostando la cartella dei font usando`FontSettings.DefaultInstance.SetFontsFolder` metodo.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 In questa linea,`"C:\\MyFonts\\"` è il percorso della cartella dei tuoi font personalizzati. Il secondo parametro,`true`indica che i font in questa cartella devono essere scansionati in modo ricorsivo.

## Passaggio 3: carica il documento

 Con la cartella dei font impostata, il passo successivo è caricare il documento Word in Aspose.Words. Questo viene fatto usando`Document` classe.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Qui,`dataDir + "Rendering.docx"` si riferisce al percorso completo del tuo documento Word. Assicurati che il tuo documento sia nella directory specificata.

## Passaggio 4: Salvare il documento

Il passaggio finale è salvare il documento dopo aver impostato la cartella dei font. Questo assicura che i font personalizzati vengano applicati correttamente nell'output.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Questa riga salva il tuo documento come PDF con i font personalizzati applicati. Il file di output sarà posizionato nella stessa directory del tuo documento sorgente.

## Conclusione

Ed ecco fatto! Impostare le cartelle dei font per l'istanza predefinita in Aspose.Words per .NET è un gioco da ragazzi se lo si suddivide in semplici passaggi. Seguendo questa guida, puoi assicurarti che i tuoi documenti Word abbiano esattamente l'aspetto che desideri, con tutti i tuoi font personalizzati al loro posto. Quindi vai avanti, provaci e fai risplendere i tuoi documenti!

## Domande frequenti

### Posso impostare più cartelle di font?
 Sì, puoi impostare più cartelle di font utilizzando`SetFontsFolders` metodo che accetta un array di percorsi di cartelle.

### Quali formati di file supporta Aspose.Words per il salvataggio dei documenti?
Aspose.Words supporta vari formati, tra cui DOCX, PDF, HTML, EPUB e altri.

### È possibile utilizzare font online in Aspose.Words?
No, attualmente Aspose.Words supporta solo file di font locali.

### Come posso assicurarmi che i miei font personalizzati siano incorporati nel PDF salvato?
 Impostando il`FontSettings` correttamente e assicurandosi che i font siano disponibili, Aspose.Words li incorporerà nell'output PDF.

### Cosa succede se un font non viene trovato nella cartella specificata?
Aspose.Words utilizzerà un font di riserva se il font specificato non viene trovato.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
