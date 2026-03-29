---
category: general
date: 2026-03-28
description: Come catturare gli avvisi durante il caricamento di un DOCX con Aspose.Words
  e ottenere messaggi di avviso per i font mancanti. Impara a gestire i font mancanti
  in modo efficiente.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: it
og_description: Come catturare gli avvisi durante il caricamento di un DOCX con Aspose.Words,
  ottenere i messaggi di avviso e gestire i font mancanti con esempi di codice pratici.
og_title: Come catturare gli avvisi in Aspose.Words – Guida completa C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Come catturare gli avvisi in Aspose.Words – Guida completa C#
url: /it/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come catturare gli avvisi in Aspose.Words – Guida completa C#

Ti sei mai chiesto **come catturare gli avvisi** che compaiono quando carichi un documento Word con Aspose.Words? Forse stai vedendo strani cambiamenti di carattere e hai bisogno di sapere esattamente il motivo. In breve, puoi agganciarti al sistema di avvisi della libreria, **ottenere i messaggi di avviso** e persino **gestire i caratteri mancanti** prima che rovinino il layout.  

In questo tutorial percorreremo uno scenario reale: caricare un DOCX, raccogliere ogni avviso emesso dal motore e stampare i dettagli di qualsiasi sostituzione di carattere che si verifica. Alla fine avrai un esempio di codice pronto all'uso, comprenderai il “perché” di ogni passaggio e saprai come estendere l'approccio per i tuoi progetti.

## Cosa imparerai

- Come configurare `LoadOptions` in modo che gli avvisi vengano catturati automaticamente.  
- Il modo esatto per **ottenere i messaggi di avviso** dalla `WarningInfoCollection`.  
- Come identificare e reagire ai **caratteri mancanti** tramite il flag `WarningType.FontSubstitution`.  
- Suggerimenti per risolvere casi limite, come documenti con caratteri incorporati o cartelle di caratteri personalizzate.

Non sono necessari riferimenti esterni – tutto ciò di cui hai bisogno è qui.

---

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.7+).  
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`).  
- Un file DOCX di esempio (`input.docx`) che o manca di alcuni caratteri o utilizza caratteri non installati sulla tua macchina.  

È tutto. Se sei già a tuo agio con C# e Visual Studio, puoi copiare‑incollare il codice e eseguirlo subito.

---

## Passo 1: Preparare le Load Options e un Callback per gli avvisi

La prima cosa che Aspose.Words fa quando chiami `new Document(path, loadOptions)` è analizzare il file. Durante l'analisi può incontrare caratteri mancanti, funzionalità non supportate o markup deprecato. Per intercettare quegli eventi è necessario un oggetto **warning callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Perché è importante:** Senza un callback, Aspose.Words registra silenziosamente gli avvisi sulla console (o li scarta), lasciandoti all'oscuro delle sostituzioni di carattere che potrebbero influenzare il layout. Fornendo una `WarningInfoCollection` dedicata, ottieni piena visibilità.

> **Consiglio professionale:** Se ti interessano solo gli avvisi relativi ai caratteri, puoi filtrare in seguito – ma raccogliere *tutti* gli avvisi ti fornisce una rete di sicurezza per problemi futuri.

## Passo 2: Caricare il documento con le opzioni configurate

Ora che il callback è pronto, carica il file. Il costruttore `Document` invocherà automaticamente il callback per qualsiasi problema rilevato.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Cosa succede dietro le quinte?** Aspose.Words analizza l'Open XML, risolve gli stili e tenta di mappare ogni riferimento di carattere a un carattere installato nel sistema. Se non viene trovata una corrispondenza, crea una voce `WarningInfo` di tipo `FontSubstitution`.

## Passo 3: Recuperare e ispezionare gli avvisi raccolti

Dopo il completamento del caricamento, il tuo `warningCollector` contiene ora tutti gli avvisi che si sono verificati. Estraiamoli e concentriamoci sui messaggi di sostituzione dei caratteri.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Output di esempio** (la tua console potrebbe mostrare qualcosa del genere):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Se vuoi *tutti* gli avvisi, rimuovi semplicemente il controllo `if` o registra `warning.Type` per ogni voce.

## Passo 4: Gestire i caratteri mancanti – Oltre il semplice logging

Catturare gli avvisi è utile, ma spesso è necessario **gestire i caratteri mancanti** programmaticamente. Ecco due strategie comuni:

### 4.1 Sostituire i caratteri mancanti con un fallback specifico

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Ora qualsiasi carattere mancante verrà sostituito con *Calibri* invece del fallback predefinito della libreria.

### 4.2 Incorporare dinamicamente un carattere sostitutivo

Se hai un file di carattere personalizzato (ad esempio, `MyFallback.ttf`) puoi registrarlo a runtime:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Questo approccio è utile quando distribuisci un carattere aziendale specifico con la tua applicazione.

> **Caso limite:** I documenti che già incorporano il carattere richiesto ignoreranno le regole di sostituzione del sistema. In quello scenario, la raccolta degli avvisi sarà vuota per quel carattere, che è esattamente ciò che desideri.

## Passo 5: Esempio completo funzionante (pronto per copia‑incolla)

Di seguito trovi un programma autonomo che dimostra tutto dall'inizio alla fine. Sostituisci semplicemente `YOUR_DIRECTORY/input.docx` con il percorso del tuo file di prova.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Cosa aspettarsi**

- La console stampa ogni avviso di sostituzione del carattere, preceduto da un'emoji di avviso per visibilità.  
- Il DOCX di output (`output.docx`) utilizza *Calibri* ovunque sia stato rilevato un carattere mancante.  
- Nessuna eccezione non gestita – il sistema di avvisi gestisce elegantemente qualsiasi carattere sconosciuto.

## Domande frequenti e risposte

**D: Funzionerà con i PDF generati da Word?**  
R: Sì. Aspose.Words tratta i PDF come un altro formato di output. La cattura degli avvisi avviene durante la fase di *caricamento*, quindi è indipendente dall'esportazione finale.

**D: E se devo catturare gli avvisi per **tutte** le operazioni sul documento (salvataggio, conversione, ecc.)?**  
R: Puoi riutilizzare la stessa `WarningInfoCollection` assegnandola a `Document.WarningCallback` dopo l'istanziazione del documento. Ogni operazione successiva aggiungerà nuove voci alla stessa collezione.

**D: Il warning callback influisce sulle prestazioni?**  
R: In modo trascurabile. La collezione memorizza semplicemente oggetti; a meno che tu non stia elaborando migliaia di avvisi in un ciclo serrato, non noterai alcun rallentamento.

**D: Come posso sopprimere gli avvisi che non mi interessano?**  
R: Implementa una classe personalizzata che eredita `IWarningCallback` e filtra all'interno del metodo `Warning`. La `WarningInfoCollection` integrata si limita a memorizzare, non filtra.

## Consigli professionali e insidie

- **Consiglio professionale:** Controlla sempre `Warning.Description` – contiene il nome esatto del carattere mancante. Questo può aiutarti a decidere se includere il carattere nella tua app.  
- **Attenzione ai caratteri incorporati:** Se il DOCX di origine incorpora già il carattere necessario, Aspose.Words non emetterà un avviso di sostituzione, anche se il carattere non è installato localmente.  
- **Sicurezza dei thread:** `WarningInfoCollection` non è thread‑safe. Se carichi più documenti contemporaneamente, assegna a ogni thread la propria collezione.  
- **Verifica della versione:** L'API degli avvisi è stabile dalla versione Aspose.Words 20.8. Assicurati di utilizzare una versione recente per non perdere i nuovi tipi di avviso.

## Conclusione

Abbiamo coperto **come catturare gli avvisi** da Aspose.Words, dimostrato come **ottenere i messaggi di avviso** e mostrato modi pratici per **gestire i caratteri mancanti** tramite font di fallback o cartelle di caratteri personalizzate. L'esempio completo è pronto per essere inserito in qualsiasi progetto .NET, e i concetti si adattano a pipeline di automazione più grandi.

Successivamente, potresti esplorare:

- Utilizzare `Document.WarningCallback` per catturare gli avvisi durante le operazioni di **salvataggio**.  
- Registrare gli avvisi su un file o su un sistema di telemetria per il monitoraggio in produzione.  
- Estendere il callback per sostituire automaticamente i caratteri mancanti con tipografie specifiche del brand.

Sentiti libero di sperimentare—cambia il font di fallback, aggiungi più documenti al batch o integra il raccoglitore di avvisi in una pipeline CI che segnala regressioni legate ai caratteri. Buona programmazione, e che i tuoi documenti vengano sempre renderizzati esattamente come ti aspetti!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}