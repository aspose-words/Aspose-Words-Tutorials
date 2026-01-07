---
category: general
date: 2026-01-06
description: Scopri come ottenere avvisi durante il caricamento dei documenti e come
  monitorare i font usando Aspose.Words. Questa guida copre le callback di avviso
  e il tracciamento della sostituzione dei font.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: it
og_description: Come ottenere avvisi in Aspose.Words? Segui questo tutorial passo‑passo
  per monitorare i font e catturare i messaggi di sostituzione durante il caricamento
  dei documenti.
og_title: Come ottenere avvisi in Aspose.Words – Monitorare i font
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Come ottenere avvisi in Aspose.Words – Monitorare i font in C#
url: /it/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come ottenere avvisi in Aspose.Words – Monitorare i font in C#

Ti sei mai chiesto **come ottenere avvisi** quando un documento Word contiene font che non hai installato? È un inconveniente comune: la tua app sostituisce silenziosamente i font mancanti e non sai cosa è cambiato. La buona notizia è che puoi agganciarti al sistema di avvisi di Aspose.Words e **monitorare i font** in tempo reale.

In questo tutorial ti mostreremo esattamente come catturare quegli avvisi di sostituzione dei font, perché è importante e cosa fare con le informazioni una volta ottenute. Nessuna documentazione esterna, solo un esempio completo e funzionante che puoi incollare subito in Visual Studio.

> **Consiglio professionale:** se stai costruendo una pipeline di conversione documenti, registrare i font mancanti in anticipo ti salva da brutte sorprese di layout a valle.

---

## Cosa ti serve

- **Aspose.Words for .NET** (ultima versione; l'API non è cambiata dalla v23.10)
- Un ambiente di sviluppo .NET (Visual Studio, Rider o VS Code con l'estensione C#)
- Un file `.docx` di esempio che faccia riferimento a un font che non hai installato (ad es., **“NonExistentFont”**)

Questo è tutto—nessun pacchetto NuGet aggiuntivo oltre a Aspose.Words.

---

## Passo 1 – Configurare un raccoglitore di avvisi (Parola chiave principale nell'intestazione)

La prima cosa di cui hai bisogno è un posto dove memorizzare gli avvisi man mano che si verificano. Aspose.Words fornisce la proprietà `WarningCallback` su `LoadOptions` proprio per questo scopo.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Perché è importante:**  
Quando la libreria incontra un font mancante, non lancia un'eccezione; emette un oggetto `WarningInfo`. Collegando un raccoglitore, ottieni piena visibilità su ogni evento di sostituzione, permettendoti di **monitorare i font** senza inquinare la console con messaggi non pertinenti.

---

## Passo 2 – Caricare il documento con le opzioni abilitate per gli avvisi

Ora leggiamo effettivamente il file. Le `LoadOptions` preparate nel passo precedente garantiscono che tutti gli avvisi relativi ai font vengano catturati.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Cosa succede dietro le quinte?**  
Aspose.Words analizza il file Word, risolve i font e, ogni volta che non riesce a trovare un font richiesto, ricade su un sostituto (di solito Arial). Il ricorso attiva un avviso `WarningType.FontSubstitution`, che finisce in `warningCollector`.

---

## Passo 3 – Ispezionare gli avvisi raccolti (Parola chiave principale appare di nuovo)

Dopo aver caricato il documento, iteriamo semplicemente su `warningCollector` e stampiamo tutti i messaggi di sostituzione dei font.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Output previsto** (supponendo che il font mancante sia *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Se il documento contiene più font sconosciuti, vedrai una riga per ogni sostituzione—perfetto per il logging o per inviare avvisi.

---

## Passo 4 – Opzionale: Registrare o persistere le informazioni sugli avvisi

In produzione probabilmente vuoi più di un semplice `Console.WriteLine`. Ecco un esempio rapido che scrive gli avvisi in un file JSON per analisi successive.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Ora hai un registro permanente che puoi alimentare a una dashboard di monitoraggio, o addirittura attivare una richiesta automatica per i file dei font mancanti.

---

## Passo 5 – Verificare il risultato e pulire

Esegui il programma. Se vedi i messaggi di sostituzione, hai ottenuto con successo **avvisi** e stai ora **monitorando i font**. Se non appare nulla, ricontrolla che il documento di test faccia davvero riferimento a un font non installato sulla macchina.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Un conteggio pari a zero di solito indica una delle seguenti situazioni:

1. Tutti i font sono stati risolti (forse il font *è* installato localmente), oppure
2. Il documento non conteneva riferimenti a font che necessitassero di sostituzione.

---

## Problemi comuni e come evitarli

| Problema | Perché succede | Soluzione |
|----------|----------------|-----------|
| **Nessun avviso appare** | Il font esiste effettivamente sul sistema, o il documento usa solo font integrati. | Rinomina il font nel file sorgente con qualcosa di impossibile (es., `XYZ123`) e riprova. |
| **Troppi avvisi (rumore)** | Stai caricando molti documenti in un ciclo senza svuotare il raccoglitore. | Ricrea `WarningInfoCollection` per ogni documento, o chiama `warningCollector.Clear()` dopo la lavorazione. |
| **Impatto sulle prestazioni** | Un logging eccessivo su disco può rallentare l'elaborazione batch. | Accumula gli avvisi in memoria e scrivili in blocco, o usa I/O asincrono. |
| **Manca `using Aspose.Words.Loading;`** | La classe `LoadOptions` si trova in questo namespace. | Aggiungi la direttiva `using` mancante, come mostrato nel Passo 1. |

---

## Estendere la soluzione – Monitorare altri tipi di avviso

Sebbene la sostituzione dei font sia la più visibile, Aspose.Words può emettere avvisi per:

- **Funzionalità deprecate** (`WarningType.Deprecated`),
- **Possibile perdita di dati** (`WarningType.DataLoss`),
- **Formati di file non supportati** (`WarningType.UnsupportedFileFormat`).

Puoi ampliare il filtro nel Passo 3 per catturare anche questi:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

In questo modo non solo **come monitorare i font**, ma anche **come ottenere avvisi** per qualsiasi scenario la tua applicazione possa incontrare.

---

## Esempio completo funzionante (pronto da copiare e incollare)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Eseguilo:** Compila il progetto, avvialo e vedrai gli avvisi stampati e salvati. Questa è la risposta completa a **come ottenere avvisi** e **come monitorare i font** con Aspose.Words.

---

## Conclusione

Ora sai **come ottenere avvisi** da Aspose.Words, in particolare per scenari di sostituzione dei font, e hai imparato **come monitorare i font** durante il processo di caricamento del documento. Collegando un `WarningCallback`, iterando gli oggetti `WarningInfo` raccolti e, opzionalmente, persistendo i dati, ottieni piena trasparenza sugli eventi di font mancanti—una capacità essenziale per qualsiasi pipeline di elaborazione documenti.

Passi successivi? Prova ad ampliare il filtro degli avvisi per includere perdite di dati o avvisi di funzionalità deprecate, o integra il log JSON in una dashboard di monitoraggio come Grafana. Lo stesso schema funziona per tutti i tipi di avviso, così sarai ben equipaggiato per tenere d'occhio qualsiasi problema che Aspose.Words ti segnala.

Buona programmazione, e che i tuoi documenti vengano sempre renderizzati esattamente come ti aspetti! 

---

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}