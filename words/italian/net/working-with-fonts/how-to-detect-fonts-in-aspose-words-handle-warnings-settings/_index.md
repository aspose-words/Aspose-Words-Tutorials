---
category: general
date: 2026-01-03
description: Come rilevare i font in Aspose.Words e gestire gli avvisi utilizzando
  le impostazioni dei font Aspose – una guida passo‑passo per gli sviluppatori.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: it
og_description: Come rilevare i font in Aspose.Words e configurare gli avvisi con
  le impostazioni dei font Aspose. Scopri l'intero flusso di lavoro in pochi minuti.
og_title: Come rilevare i font in Aspose.Words – Gestire gli avvisi
tags:
- Aspose.Words
- C#
- Document Processing
title: Come rilevare i font in Aspose.Words – Gestire avvisi e impostazioni
url: /it/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rilevare i font in Aspose.Words – Gestire avvisi e impostazioni

Ti sei mai chiesto **come rilevare i font** in un documento Word prima che vada in produzione? Non sei l'unico. I font mancanti possono causare incubi di layout e, senza avvisi adeguati, potresti distribuire un PDF o un DOCX difettoso senza nemmeno accorgertene.  

In questo tutorial vedremo **come rilevare i font** usando Aspose.Words, mostreremo **come gestire gli avvisi** e modificheremo **le impostazioni dei font di Aspose** così da **configurare gli avvisi** esattamente come ti serve. Alla fine avrai uno snippet pronto all'uso che stampa ogni sostituzione effettuata da Aspose, e saprai come adattarlo ai tuoi progetti.

## Prerequisiti

- .NET 6+ (o .NET Framework 4.6+).  
- Aspose.Words per .NET installato via NuGet (`Install-Package Aspose.Words`).  
- Un file Word che faccia riferimento intenzionalmente a un font mancante (ad es., *DocumentWithMissingFonts.docx*).  

Se li hai già, ottimo—iniziamo.

![screenshot di come rilevare i font](https://example.com/detect-fonts.png "esempio di output di come rilevare i font")

## Come rilevare i font con Aspose.Words

Il primo passo è dire ad Aspose.Words che ti interessano gli eventi di sostituzione dei font. Questo si ottiene fornendo un callback di avviso personalizzato tramite **le impostazioni dei font di Aspose**. Il callback riceve un oggetto `WarningInfo` per ogni sostituzione, permettendoti di **rilevare i font** a runtime.

### Passo 1: Creare una classe di callback per gli avvisi

Implementa l'interfaccia `IWarningCallback`. All'interno del metodo `Warning`, filtra per `WarningType.FontSubstitution` e registra i dettagli.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Consiglio:** La stringa `info.Description` contiene sia il nome del font mancante sia il sostituto scelto da Aspose. Puoi analizzarla se ti serve un report strutturato.

### Passo 2: Configurare LoadOptions con le impostazioni dei font di Aspose

Crea un'istanza di `LoadOptions`, allega un nuovo oggetto `FontSettings` e imposta `WarningCallback` sul gestore appena creato. Questo indica ad Aspose **come configurare gli avvisi**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Se hai una cartella di font privata, puoi aggiungerla così:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Quella riga mostra un altro aspetto delle **impostazioni dei font di Aspose**—controlli esattamente dove Aspose cerca i font prima di decidere di sostituirli.

### Passo 3: Caricare il documento e attivare il callback

Ora carica il documento di destinazione con le `loadOptions`. Mentre Aspose analizza il file, ogni font mancante attiva il gestore degli avvisi, rilevando **i font** al volo.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Quando esegui il programma, vedrai un output simile a:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Passo 4: (Facoltativo) Raccogliere gli avvisi per un uso successivo

Se devi memorizzare i dati di sostituzione per un report, modifica il gestore in modo da accumulare i messaggi in una lista.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

In seguito potrai scrivere `handler.Substitutions` in un file JSON, inviarlo a un servizio di logging o visualizzarlo in un'interfaccia utente.

### Passo 5: Verificare il risultato programmaticamente

A volte vuoi assicurarti che *nessuna* sostituzione sia avvenuta (ad es., in una build CI). Ecco un controllo rapido:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Quello snippet dimostra **come gestire gli avvisi** in modo deterministico, dandoti pieno controllo sul pipeline di build.

## Domande frequenti (e casi limite)

**E se devo ignorare certe sostituzioni?**  
Puoi aggiungere logica condizionale dentro `Warning` e semplicemente restituire senza registrare per i font che consideri accettabili.

**Posso sopprimere tutti gli avvisi e ottenere solo un risultato booleano?**  
Sì—imposta `loadOptions.WarningCallback = null` e poi ispeziona `doc.FontInfo` dopo il caricamento (anche se perderai il log dettagliato).

**Funziona con la conversione PDF?**  
Assolutamente. Lo stesso meccanismo di avviso si attiva quando chiami `doc.Save("out.pdf")`. Il callback catturerà qualsiasi scambio di font effettuato durante la conversione.

**C'è un impatto sulle prestazioni?**  
Il sovraccarico è minimo—solo qualche chiamata di metodo in più per ogni font mancante. Per grandi batch potresti voler cacheare i risultati.

## Riepilogo: cosa abbiamo coperto

- **Come rilevare i font** implementando un `IWarningCallback` personalizzato.  
- **Come gestire gli avvisi** tramite `LoadOptions.WarningCallback`.  
- Modifica delle **impostazioni dei font di Aspose** (aggiunta di cartelle di font personalizzate, abilitazione/disabilitazione degli avvisi).  
- **Come configurare gli avvisi** sia per l'output immediato sulla console sia per analisi successive.  

Con questi elementi a disposizione, puoi processare documenti Word in modo sicuro, garantire che i font mancanti vengano segnalati e mantenere un output coerente tra ambienti diversi.

## Prossimi passi

- Esplora `FontSettings.SubstitutionSettings` per un controllo più granulare (ad es., mappare font mancanti specifici a sostituti scelti).  
- Combina questo approccio con Aspose.PDF per generare PDF che mantengano la tipografia esatta.  
- Automatizza il controllo degli avvisi in una pipeline CI/CD per bloccare le release che contengono problemi di font—perfetto per i team che **gestiscono gli avvisi** come parte dei gate di qualità.

Hai altre domande su **le impostazioni dei font di Aspose** o ti serve aiuto per integrare tutto questo in un servizio più grande? Lascia un commento qui sotto, e buona programmazione!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}