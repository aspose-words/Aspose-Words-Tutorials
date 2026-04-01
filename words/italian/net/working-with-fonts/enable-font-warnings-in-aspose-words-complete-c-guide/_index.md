---
category: general
date: 2026-04-01
description: Abilita gli avvisi sui font durante il caricamento dei documenti Word
  con Aspose.Words. Scopri come catturare gli eventi di sostituzione dei font usando
  C# LoadOptions e Impostazioni dei font.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: it
og_description: Abilita gli avvisi sui caratteri durante il caricamento dei documenti
  Word con Aspose.Words. Questo tutorial mostra come catturare gli eventi di sostituzione
  dei caratteri in C#.
og_title: Abilita gli avvisi sui font in Aspose.Words – Guida completa C#
tags:
- Aspose.Words
- C#
- Font Management
title: Abilita gli avvisi dei font in Aspose.Words – Guida completa C#
url: /it/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Abilita gli avvisi di carattere in Aspose.Words – Guida completa C#

Ti sei mai chiesto perché un documento Word appare improvvisamente diverso dopo averlo caricato programmaticamente? **Abilita gli avvisi di carattere** e saprai subito quando Aspose.Words sostituisce un carattere mancante con un fallback. In questo tutorial seguirai un esempio pratico che non solo cattura queste sostituzioni ma spiega anche *perché* avvengono.

Copriamo tutto ciò di cui hai bisogno per partire: il pacchetto NuGet richiesto, la configurazione esatta di `LoadOptions` e un output della console ordinato che indica quali caratteri sono stati sostituiti. Alla fine avrai un modello solido e riutilizzabile per **l'elaborazione di documenti C#** che funziona con qualsiasi versione di Aspose.Words.

## Cosa imparerai

- Come creare un'istanza di `LoadOptions` che traccia le modifiche ai caratteri.  
- Lo scopo dell'evento `SubstitutionWarning` e come collegarlo.  
- Un esempio di codice completo e eseguibile che stampa avvisi chiari sulla console.  
- Suggerimenti per gestire casi limite, come documenti che contengono solo caratteri standard.  

Non è necessaria alcuna esperienza pregressa con Aspose.Words—basta una conoscenza di base di C# e .NET.

---

![Diagramma di avvisi di carattere](placeholder-image.png "Diagramma di avvisi di carattere")

*Testo alternativo: diagramma di avvisi di carattere che mostra il flusso dell'evento quando un carattere mancante viene sostituito.*

## Passo 1: Configura LoadOptions e abilita gli avvisi di carattere

La prima cosa di cui hai bisogno è un oggetto `LoadOptions`. Questo contenitore indica ad Aspose.Words come trattare il file che stai per caricare. Assegnando una nuova istanza di `FontSettings` apri la porta agli eventi relativi ai caratteri.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Perché è importante:**  
Se ometti l'assegnazione di `FontSettings`, Aspose.Words sostituirà comunque i caratteri mancanti, ma non riceverai alcuna notifica. Il meccanismo di avviso vive all'interno di `FontSettings`, quindi inizializzarlo è *cruciale* per il nostro obiettivo.

> **Consiglio:** Puoi anche puntare `FontSettings` a una cartella di caratteri personalizzata usando `SetFontsFolder`. Questo riduce il numero di avvisi che vedrai, perché Aspose.Words può effettivamente trovare i caratteri mancanti.

## Passo 2: Iscriviti all'evento SubstitutionWarning (sostituzione del carattere)

Ora che l'oggetto `FontSettings` esiste, lo colleghiamo al suo evento `SubstitutionWarning`. Questo evento si attiva **ogni volta** che Aspose.Words sostituisce un carattere richiesto con qualcos'altro.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Perché è importante:**  
Senza questo listener non avresti alcuna visibilità sul processo di sostituzione. La riga nella console ti fornisce una rapida traccia di audit, particolarmente utile durante build automatizzate o quando generi PDF per settori con requisiti di conformità elevati.

> **Domanda comune:** *E se volessi sopprimere gli avvisi?*  
> Puoi semplicemente staccare il gestore o impostare `FontSettings.SubstitutionWarning += null;`. Tuttavia, mantenere gli avvisi è solitamente la via più sicura perché le sostituzioni silenziose possono causare problemi di layout.

## Passo 3: Carica il tuo documento con le opzioni configurate (elaborazione di documenti C#)

Con il sistema di avviso pronto, il caricamento del documento è semplice. Passa l'istanza `LoadOptions` al costruttore `Document`, e Aspose.Words farà il resto.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Perché è importante:**  
L'oggetto `LoadOptions` è il ponte tra il file grezzo e l'infrastruttura di avviso. Se lo ometti, il documento si carica silenziosamente e tutti i caratteri mancanti vengono sostituiti senza lasciare traccia.

> **Caso limite:** Alcuni documenti incorporano i file dei caratteri di cui hanno bisogno. In quello scenario non apparirà alcun avviso perché Aspose.Words trova il carattere incorporato. Il codice sopra funziona comunque; vedrai semplicemente un output vuoto nella console.

## Passo 4: Verifica l'output e le insidie comuni

Esegui il programma da un prompt dei comandi o dal debugger del tuo IDE. Se il documento di origine contiene un carattere che non è installato sulla macchina (o non è disponibile nella cartella di caratteri personalizzata), vedrai righe come:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Se non viene stampato nulla, è perché:

1. Tutti i caratteri sono stati trovati, **oppure**  
2. Il gestore `SubstitutionWarning` non è stato collegato correttamente (controlla nuovamente il Passo 2).

### Perché avvengono le sostituzioni di carattere?

- **Carattere di sistema mancante:** Il sistema operativo non ha il tipo di carattere richiesto.  
- **Formato di carattere non supportato:** Aspose.Words può leggere TrueType e OpenType, ma non tutti i formati proprietari.  
- **Restrizioni di licenza:** Alcuni caratteri commerciali bloccano l'incorporamento, costringendo a un fallback.

Comprendere il *perché* ti aiuta a decidere se distribuire i caratteri mancanti con la tua app o a modificare lo stile del documento.

## Bonus: Controllare il carattere di fallback

Se vuoi che ogni carattere mancante ricada su una famiglia specifica (ad esempio, “Calibri”), puoi impostare una regola di sostituzione globale:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Ora la console continuerà a segnalare gli avvisi, ma il risultato visivo sarà coerente per tutti i caratteri mancanti.

---

## Riepilogo

- **Abilita gli avvisi di carattere** creando un `LoadOptions` con un nuovo `FontSettings`.  
- Collega l'evento `SubstitutionWarning` per ricevere avvisi in tempo reale ogni volta che un carattere viene sostituito.  
- Carica il tuo documento usando le opzioni configurate e, facoltativamente, salva in PDF per vedere l'effetto visivo.  
- Diagnostica il motivo di una sostituzione e, se necessario, imposta un carattere di fallback specifico.

Hai appena aggiunto una rete di sicurezza al tuo flusso di lavoro **Aspose.Words** che impedisce modifiche silenziose al layout. Successivamente, potresti esplorare le **impostazioni dei caratteri** come `DefaultFontName` o approfondire le opzioni di **rendering del documento** per perfezionare l'output PDF.

---

### Cosa provare dopo?

- **Esplora altre funzionalità di FontSettings**: `SetFontsFolder`, `LoadFontSources` e `DefaultFontName`.  
- **Combina gli avvisi con framework di logging** (Serilog, NLog) per diagnostica di livello produzione.  
- **Sperimenta con diversi formati di documento** (`.doc`, `.rtf`, `.html`) per vedere come ciascuno gestisce i caratteri mancanti.  

Hai domande o uno scenario particolare? Lascia un commento qui sotto, e buona programmazione!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}