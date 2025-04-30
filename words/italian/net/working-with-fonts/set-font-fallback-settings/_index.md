---
"description": "Scopri come configurare le impostazioni di fallback dei caratteri in Aspose.Words per .NET. Questa guida completa garantisce che tutti i caratteri nei tuoi documenti vengano visualizzati correttamente."
"linktitle": "Imposta le impostazioni di fallback dei caratteri"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Imposta le impostazioni di fallback dei caratteri"
"url": "/it/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Imposta le impostazioni di fallback dei caratteri

## Introduzione

Quando si lavora con documenti che contengono diversi elementi di testo, come lingue diverse o caratteri speciali, è fondamentale assicurarsi che questi elementi vengano visualizzati correttamente. Aspose.Words per .NET offre una potente funzionalità chiamata Font Fallback Settings, che aiuta a definire regole per la sostituzione dei font quando il font originale non supporta determinati caratteri. In questa guida, esploreremo come configurare Font Fallback Settings utilizzando Aspose.Words per .NET in un tutorial passo passo.

## Prerequisiti

Prima di immergerti nel tutorial, assicurati di avere i seguenti prerequisiti:

- Conoscenza di base di C#: familiarità con il linguaggio di programmazione C# e il framework .NET.
- Aspose.Words per .NET: Scarica e installa da [collegamento per il download](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: un ambiente simile a Visual Studio per scrivere ed eseguire il codice.
- Documento di esempio: avere un documento di esempio (ad esempio, `Rendering.docx`) pronto per il test.
- Regole XML per i font di fallback: preparare un file XML che definisca le regole per i font di fallback.

## Importa spazi dei nomi

Per utilizzare Aspose.Words, è necessario importare i namespace necessari. Questo consente l'accesso a diverse classi e metodi necessari per l'elaborazione dei documenti.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Passaggio 1: definire la directory dei documenti

Per prima cosa, definisci la directory in cui è archiviato il documento. Questo è essenziale per individuare ed elaborare il documento.

```csharp
// Il percorso verso la directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: caricare il documento

Carica il tuo documento in Aspose.Words `Document` oggetto. Questo passaggio consente di lavorare con il documento a livello di programmazione.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 3: configurare le impostazioni del carattere

Crea un nuovo `FontSettings` oggetto e caricare le impostazioni di fallback del font da un file XML. Questo file XML contiene le regole per il fallback del font.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Passaggio 4: applicare le impostazioni del carattere al documento

Assegnare il configurato `FontSettings` al documento. Questo garantisce che le regole di fallback dei font vengano applicate durante il rendering del documento.

```csharp
doc.FontSettings = fontSettings;
```

## Passaggio 5: salvare il documento

Infine, salva il documento. Le impostazioni di fallback del font verranno utilizzate durante l'operazione di salvataggio per garantire la corretta sostituzione del font.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## File XML: regole di fallback dei font

Ecco un esempio di come dovrebbe apparire il file XML che definisce le regole di fallback dei font:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Conclusione

Seguendo questi passaggi, è possibile configurare e utilizzare efficacemente le impostazioni di fallback dei font in Aspose.Words per .NET. Questo garantisce che i documenti visualizzino correttamente tutti i caratteri, anche se il font originale non supporta determinati caratteri. L'implementazione di queste impostazioni migliorerà notevolmente la qualità e la leggibilità dei documenti.

## Domande frequenti

### D1: Che cos'è Font Fallback?

Font Fallback è una funzionalità che consente la sostituzione dei font quando il font originale non supporta determinati caratteri, garantendo la corretta visualizzazione di tutti gli elementi di testo.

### D2: Posso specificare più font di fallback?

Sì, è possibile specificare più font di fallback nelle regole XML. Aspose.Words controllerà ogni font nell'ordine specificato finché non ne troverà uno che supporti il carattere.

### D3: Dove posso scaricare Aspose.Words per .NET?

Puoi scaricarlo da [Pagina di download di Aspose](https://releases.aspose.com/words/net/).

### D4: Come posso creare il file XML per le regole di fallback dei font?

Il file XML può essere creato con qualsiasi editor di testo. Dovrebbe seguire la struttura mostrata nell'esempio fornito in questo tutorial.

### D5: È disponibile il supporto per Aspose.Words?

Sì, puoi trovare supporto su [Forum di supporto di Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}