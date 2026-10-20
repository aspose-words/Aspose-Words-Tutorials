---
category: general
date: 2026-03-22
description: Salva documento Word e rileva i caratteri mancanti usando Aspose.Words.
  Scopri come tenere traccia dei caratteri mancanti e catturare gli errori di carattere
  in C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: it
og_description: Salva documento Word e rileva i caratteri mancanti in C#. Questa guida
  mostra come monitorare i caratteri mancanti e catturare gli errori di carattere
  usando una callback di avviso.
og_title: Salva documento Word – Rileva i caratteri mancanti con Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Salva documento Word – Rileva i caratteri mancanti con Aspose.Words
url: /it/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salva documento Word – Rileva caratteri mancanti con Aspose.Words

Ti è mai capitato di dover **salvare il documento Word** ma non eri sicuro se alcuni dei caratteri al suo interno sarebbero sopravvissuti al round‑trip? Succede più spesso di quanto pensi, soprattutto quando i documenti viaggiano tra macchine con librerie di caratteri diverse. La buona notizia? Aspose.Words ti offre un modo integrato per **rilevare caratteri mancanti** mentre **salvi il documento Word**, così puoi registrare, avvisare o persino sostituirli prima che il file arrivi sullo schermo dell'utente.

In questo tutorial ti guideremo attraverso un esempio completo, pronto‑da‑eseguire, che non solo salva un documento Word ma anche **traccia i caratteri mancanti** e **cattura gli errori di carattere** usando un gestore di avvisi personalizzato. Alla fine saprai esattamente perché il callback di avviso è importante, come collegarlo e come appare l'output della console quando avviene una sostituzione. Nessun superfluo—solo il codice che puoi inserire subito in un progetto .NET.

> **Prerequisiti**  
> • .NET 6 (o qualsiasi versione recente di .NET Framework) installato  
> • Visual Studio 2022 o il tuo IDE preferito  
> • Una copia con licenza di **Aspose.Words for .NET** (la versione di prova gratuita funziona per i test)  

Se li hai, iniziamo.

---

## Salva documento Word e rileva caratteri mancanti

L'idea di base è semplice: prima di chiamare `Document.Save`, assegna un oggetto che implementa `IWarningCallback` a `Document.WarningCallback`. Aspose.Words invocherà questo oggetto per ogni avviso che incontra, inclusi gli avvisi di **sostituzione del carattere** che si verificano quando il documento di origine fa riferimento a un carattere che il tuo sistema non riesce a trovare.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Cosa vedrai:**  
Se `input.docx` fa riferimento a un carattere non installato, la console stampa qualcosa del genere:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Quella riga ti indica esattamente quale carattere mancava e quale carattere ha usato Aspose.Words al suo posto—perfetto per **catturare gli errori di carattere** prima di distribuire il file.

---

## Traccia i caratteri mancanti con un callback di avviso (Passo‑per‑Passo)

### 1️⃣ Installa Aspose.Words

Apri la console NuGet del tuo progetto e esegui:

```bash
dotnet add package Aspose.Words
```

Questo scarica l'ultima versione stabile (attualmente 24.10). Mantenere la libreria aggiornata garantisce di ottenere le più recenti funzionalità di **rilevare caratteri mancanti** e le correzioni di bug.

### 2️⃣ Definisci il gestore di avviso

Perché abbiamo bisogno di una classe separata? Implementare `IWarningCallback` ti consente di centralizzare tutta la logica degli avvisi in un unico posto. Potresti anche registrare su un file, inviare telemetria o lanciare un'eccezione se un carattere mancante è un errore critico per il tuo flusso di lavoro.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Consiglio professionale:** Se hai bisogno di **tracciare i caratteri mancanti** su molti documenti, memorizza i messaggi in una `List<string>` all'interno del gestore e rendila disponibile in seguito per la generazione di report.

### 3️⃣ Carica il tuo documento sorgente

Il costruttore `Document` può accettare un percorso file, uno stream o anche byte grezzi. Nella maggior parte dei casi lo punterai a un `.docx` ricevuto da un utente o da un altro sistema.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Se il file è grande, considera l'uso di `LoadOptions` per abilitare il caricamento lazy, che riduce la pressione sulla memoria.

### 4️⃣ Collega il callback

Assegna l'istanza a `doc.WarningCallback`. Da questo punto in poi, ogni avviso (incluse le sostituzioni di caratteri) passerà attraverso il tuo gestore.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Salva il documento

Ora puoi chiamare in sicurezza `Save`. Il gestore di avviso viene eseguito **sincronamente** durante l'operazione di salvataggio, quindi vedrai l'output immediatamente.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Se preferisci salvare in un formato diverso (PDF, HTML, ecc.), lo stesso meccanismo di avviso funziona—Aspose.Words segnalerà comunque i caratteri mancanti prima della conversione.

---

## Cattura gli errori di carattere – Casi limite comuni

Mentre il flusso di base copre la maggior parte degli scenari, i progetti reali spesso incontrano qualche intoppo. Di seguito alcune variazioni che potresti incontrare e come gestirle.

### Carattere mancante in intestazione/piè di pagina

Intestazioni e piè di pagina sono nodi separati, ma il sistema di avviso li tratta allo stesso modo del testo del corpo. Non è necessario alcun codice aggiuntivo; il callback verrà attivato anche per quei caratteri. Basta assicurarsi di caricare il documento completo (il comportamento predefinito lo fa).

### Sostituzioni multiple in un documento

Se un documento utilizza diversi caratteri sconosciuti, il gestore verrà chiamato una volta per ogni sostituzione. Per evitare di intasare la console, potresti deduplicare i messaggi:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Trasformare gli avvisi in eccezioni

A volte un carattere mancante è un ostacolo insormontabile. Lancia un'eccezione all'interno del gestore per abortire il salvataggio:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Ricorda di avvolgere `doc.Save` in un blocco `try/catch` per gestire l'eccezione in modo elegante.

---

## Verifica il risultato – Cosa aspettarsi

Dopo che il salvataggio è completato, apri `output.docx` in Microsoft Word (o in qualsiasi visualizzatore compatibile). Dovresti vedere lo stesso layout visivo dell'originale, ma i caratteri sostituiti appariranno come il fallback osservato nella console. Per ricontrollare, puoi:

1. Aprire **File → Opzioni → Avanzate → Mostra contenuto del documento → Usa qualità bozza** – questo costringe Word a rivelare eventuali sostituzioni di caratteri nascoste.  
2. Utilizzare la finestra di dialogo **Sostituisci caratteri** di Word (`Ctrl+Shift+F`) per vedere quali caratteri sono effettivamente incorporati.

Se tutto corrisponde, hai salvato con successo **il documento Word** mentre **rilevavi i caratteri mancanti** e **catturavi gli errori di carattere**. 🎉

---

## Esempio completo funzionante (pronto per copia‑incolla)

Di seguito trovi l'intero programma che puoi inserire in un nuovo progetto Console App. Sostituisci semplicemente `YOUR_DIRECTORY` con un percorso di cartella reale sul tuo computer.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Output console previsto** (esempio):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Ecco tutta la storia—nessun passaggio nascosto, nessuna documentazione esterna da inseguire.

---

## Conclusione

Ti abbiamo appena mostrato come **salvare il documento Word** rilevendo attivamente **caratteri mancanti**, **tracciando i caratteri mancanti** e **catturando gli errori di carattere** usando il callback di avviso di Aspose.Words. Collegando una piccola implementazione di `IWarningCallback`, ottieni piena visibilità sulle sostituzioni di caratteri al momento del salvataggio, dandoti la possibilità di registrare, sostituire o abortire secondo necessità.

Pronto per la prossima sfida? Prova ad estendere il gestore per scrivere gli avvisi in un log JSON strutturato, oppure combinalo con Aspose.PDF per convertire lo stesso documento preservando le informazioni sui caratteri. Potresti anche esplorare l'incorporamento dei caratteri mancanti direttamente nel file di output—Aspose.Words supporta l'incorporamento dei caratteri tramite `LoadOptions.FontSettings`.

Provalo, adatta il codice al tuo flusso di lavoro e facci sapere come funziona per te. Buona programmazione!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}