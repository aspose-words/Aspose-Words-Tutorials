---
"description": "Scopri come impostare la priorità delle cartelle dei font nei documenti Word utilizzando Aspose.Words per .NET. La nostra guida garantisce che i tuoi documenti vengano visualizzati perfettamente ogni volta."
"linktitle": "Imposta le cartelle dei font con priorità"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Imposta le cartelle dei font con priorità"
"url": "/it/net/working-with-fonts/set-fonts-folders-with-priority/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Imposta le cartelle dei font con priorità

## Introduzione

Nel mondo della manipolazione dei documenti, l'impostazione di cartelle di font personalizzate può fare la differenza nel garantire una visualizzazione perfetta dei documenti, indipendentemente da dove vengano visualizzati. Oggi approfondiremo come impostare le cartelle di font con priorità nei documenti Word utilizzando Aspose.Words per .NET. Questa guida completa vi guiderà passo passo, rendendo il processo il più fluido possibile.

## Prerequisiti

Prima di iniziare, assicuriamoci di avere tutto il necessario. Ecco una breve lista di controllo:

- Aspose.Words per .NET: è necessario che questa libreria sia installata. Se non l'hai ancora, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: assicurati di disporre di un ambiente di sviluppo .NET funzionante, come Visual Studio.
- Directory dei documenti: assicurati di avere una directory per i tuoi documenti. Per i nostri esempi, useremo `"YOUR DOCUMENT DIRECTORY"` come segnaposto per questo percorso.

## Importa spazi dei nomi

Per prima cosa, dobbiamo importare i namespace necessari. Questi namespace sono essenziali per accedere alle classi e ai metodi forniti da Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ora analizziamo nel dettaglio ogni passaggio per impostare le cartelle dei font in base alla priorità.

## Passaggio 1: imposta le origini dei font

Per iniziare, è necessario definire le origini dei font. È qui che si indica ad Aspose.Words dove cercare i font. È possibile specificare più cartelle di font e persino impostarne la priorità.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

In questo esempio, stiamo impostando due sorgenti di font:
- SystemFontSource: questa è la sorgente font predefinita che include tutti i font installati sul sistema.
- FolderFontSource: questa è una cartella di font personalizzati situata in `C:\\MyFonts\\`. IL `true` il parametro specifica che questa cartella deve essere scansionata ricorsivamente e `1` stabilisce la sua priorità.

## Passaggio 2: carica il documento

Quindi, carica il documento su cui desideri lavorare. Assicurati che il documento si trovi nella directory specificata.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Questa riga di codice carica un documento denominato `Rendering.docx` dalla directory dei documenti.

## Passaggio 3: salva il documento con le nuove impostazioni del carattere

Infine, salva il documento. Quando salvi il documento, Aspose.Words utilizzerà le impostazioni del font specificate.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

Questo salva il documento come PDF nella directory dei documenti con il nome `WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Conclusione

Ed ecco fatto! Hai configurato correttamente le cartelle dei font con priorità utilizzando Aspose.Words per .NET. Specificando cartelle e priorità personalizzate, puoi garantire che i tuoi documenti vengano visualizzati in modo coerente, indipendentemente da dove vengano visualizzati. Questo è particolarmente utile negli ambienti in cui font specifici non sono installati di default.

## Domande frequenti

### Perché dovrei impostare cartelle di font personalizzate?
L'impostazione di cartelle di font personalizzate garantisce che i documenti vengano visualizzati correttamente, anche se utilizzano font non installati sul sistema in cui vengono visualizzati.

### Posso impostare più cartelle di font personalizzati?
Sì, puoi specificare più cartelle di font. Aspose.Words ti consente di impostare la priorità per ogni cartella, assicurandoti che i font più importanti vengano trovati per primi.

### Cosa succede se un font manca da tutte le fonti specificate?
Se un font risulta mancante da tutte le fonti specificate, Aspose.Words utilizzerà un font di riserva per garantire che il documento sia ancora leggibile.

### Posso modificare la priorità dei font di sistema?
I font di sistema sono sempre inclusi per impostazione predefinita, ma è possibile impostarne la priorità in relazione alle cartelle dei font personalizzati.

### È possibile utilizzare percorsi di rete per cartelle di font personalizzati?
Sì, è possibile specificare percorsi di rete come cartelle di font personalizzate, consentendo di centralizzare le risorse dei font in una posizione di rete.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}