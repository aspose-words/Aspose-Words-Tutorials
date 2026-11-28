---
category: general
date: 2026-01-11
description: Recupera un documento corrotto in C# usando Aspose.Words. Scopri come
  impostare la modalità di recupero, caricare il docx con il recupero e avvisare l'utente
  in caso di errore in pochi semplici passaggi.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: it
og_description: Recupera un documento corrotto in C# impostando la modalità di recupero,
  caricando un DOCX con il recupero e avvisando l'utente in caso di errore. Tutorial
  completo passo‑passo.
og_title: Recupera documento corrotto in C# – Guida rapida
tags:
- Aspose.Words
- C#
- Document Recovery
title: Recupera documento corrotto in C# – Imposta modalità di recupero e avvisa l'utente
url: /it/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recuperare un documento corrotto in C# – Guida completa

Hai mai provato ad aprire un DOCX che sembra a posto in Word ma genera un'eccezione nel tuo codice? Probabilmente ti trovi di fronte a uno scenario di **recover corrupted document**. La buona notizia è che Aspose.Words ti offre un controllo dettagliato su come gestire quei file problematici—che tu voglia correggerli silenziosamente, lanciare un'eccezione o chiedere all'utente cosa fare.

In questo tutorial ti guideremo passo passo su tutto ciò che serve per **recover corrupted document**, dall'installazione della libreria alla scelta dell'opzione corretta **set recovery mode**, **load docx with recovery**, e infine **prompt user on error** quando qualcosa va storto. Nessuna teoria superflua, solo un esempio completo e funzionante da inserire in qualsiasi progetto .NET.

> **Anteprima rapida:** Alla fine avrai un'app console che carica un eventuale `corrupt.docx`, registra tutti gli avvisi e chiede all'utente se vuole continuare quando il recupero fallisce.

---

## Cosa ti servirà

- **.NET 6.0** o versioni successive (il codice funziona anche su .NET Framework 4.6+).  
- **Aspose.Words for .NET** – installa via NuGet (`Install-Package Aspose.Words`).  
- Un file **corrupt DOCX** a disposizione per i test (puoi danneggiare deliberatamente un file aprendo un editor esadecimale o rinominandone l'estensione).  
- Qualsiasi IDE ti piaccia—Visual Studio, Rider o anche VS Code vanno benissimo.

> *Consiglio pro:* Tieni sempre una copia di backup del file originale. Il recupero può riscrivere parti del documento e non vuoi perdere le parti corrette.

---

## Passo 1 – Installa Aspose.Words e aggiungi i namespace

Prima di tutto. Prendi la libreria da NuGet e porta i namespace necessari nello scope.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Questo è tutto ciò che ti serve per il resto della guida. Il namespace `Aspose.Words.Loading` contiene la classe `LoadOptions`, che è la chiave per **set recovery mode**.

---

## Passo 2 – Scegli una modalità di recupero (Primary H2 with Keyword)

### Recuperare un documento corrotto – Impostare la modalità di recupero corretta

Aspose.Words offre tre comportamenti di recupero:

| Modalità | Cosa succede | Quando usarla |
|----------|--------------|---------------|
| **PromptUser** | Mostra una finestra di dialogo (o puoi implementare il tuo prompt) e tenta di riparare il file. | Ideale per strumenti interattivi in cui l'utente può decidere. |
| **Silent** | Tenta di riparare automaticamente, senza UI. | Buono per processi batch o servizi. |
| **ThrowException** | Interrompe l'elaborazione e lancia un'eccezione. | Da usare quando vuoi una convalida rigorosa. |

Di seguito è mostrato come **set recovery mode** su `PromptUser`. Se preferisci una gestione silenziosa, basta sostituire il valore dell'enumerazione.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Perché è importante:** Impostando esplicitamente **set recovery mode**, indichi ad Aspose.Words quanto deve essere aggressivo. Il valore predefinito è `PromptUser`, ma essere espliciti rende l'intento cristallino—sia per i futuri manutentori sia per i motori di ricerca che analizzano il codice.

---

## Passo 3 – Carica il DOCX con il recupero

Ora **load docx with recovery** usando le `LoadOptions` appena configurate. Se il file è danneggiato, Aspose.Words lo riparerà o genererà un avviso, a seconda della modalità.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

Il costruttore `Document` fa il lavoro pesante. In modalità **PromptUser**, vedrai un prompt nella console (o una UI personalizzata se ti colleghi agli eventi di `LoadOptions`) che chiede se continuare. In modalità **Silent**, il metodo tenta semplicemente il meglio e prosegue.

---

## Passo 4 – Ispeziona gli avvisi e chiedi all'utente

Aspose.Words registra tutti i problemi incontrati nella collezione `Warnings`. Iteriamo su di essi e diamo all'utente la possibilità di decidere cosa fare dopo.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Il frammento sopra **prompt user on error** in modo adatto alla console. Se stai creando un'app Windows Forms o WPF, sostituisci `Console.ReadLine` con un `MessageBox` o una finestra di dialogo personalizzata.

---

## Passo 5 – Lavora con il documento recuperato

A questo punto il documento è in memoria, riparato al meglio delle capacità di Aspose.Words. Ora puoi leggere il contenuto, salvare una copia pulita o eseguire qualsiasi manipolazione necessaria.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Eseguire il programma completo su un file danneggiato produrrà un output simile a questo:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Se il file era effettivamente integro, vedrai “Document loaded without any warnings.” e la copia pulita sarà identica all'originale.

---

## Esempio completo funzionante

Ecco l'intero programma in un unico blocco. Copialo in un nuovo progetto console e premi **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Eseguilo, corrompi un file di test e osserva il recupero in azione. 🎉

---

## Casi limite e variazioni

| Scenario | Cosa cambiare | Perché |
|----------|---------------|--------|
| **Batch processing** (nessuna interazione utente) | Imposta `RecoveryMode = RecoveryMode.Silent` e rimuovi il prompt della console. | Mantiene la pipeline in movimento automaticamente. |
| **Strict validation** (fail fast) | Usa `RecoveryMode.ThrowException`. Avvolgi la chiamata di caricamento in try/catch e registra l'eccezione. | Garantisce che non lavori mai con un file parzialmente riparato. |
| **Custom UI** (WinForms/WPF) | Sottoscrivi `LoadOptions.LoadingProgress` o usa gli eventi di `Document.LoadOptions` per mostrare una finestra di dialogo. | Fornisce un'esperienza più ricca rispetto alla console. |
| **Large documents** (vincoli di memoria) | Carica con `LoadOptions.LoadFormat = LoadFormat.Docx` e considera `Document.SaveOptions` per lo streaming dell'output. | Previene eccezioni OutOfMemory. |

---

## Consigli pratici (segnali E‑E‑A‑T)

- **Mantieni sempre un backup** prima di tentare il recupero; il processo può sovrascrivere parti del file.  
- **Registra gli avvisi** su un file per analisi successive; spesso indicano la causa radice (es. parti mancanti, XML corrotto).  
- **Testa con più tipologie di corruzione** – tronca il file, corrompi i tag XML o modifica la struttura zip per vedere come si comporta ogni modalità.  
- **Aggiorna Aspose.Words regolarmente**; le versioni più recenti migliorano gli algoritmi di recupero e aggiungono nuovi tipi di avviso.  
- **Combina con la validazione** – dopo il recupero, esegui rapidamente `document.UpdateFields()` e `document.Save()` per assicurarti che il documento sia pienamente funzionante.

---

## Conclusione

Ora sai come **recover corrupted document** in C# impostando **set recovery mode**, **load docx with recovery** e **prompt user on error** quando qualcosa va storto. L'esempio completo dimostra un flusso pulito, end‑to‑end, che funziona in app console, servizi o progetti UI.

Prossimi passi? Prova a sostituire il prompt della console con una finestra modale in un'app WinForms, sperimenta la modalità **Silent** per job in background, o integra la logica di recupero in un endpoint di upload file ASP.NET così gli utenti possono caricare DOCX danneggiati e ricevere subito una versione riparata.

Buon coding e che i tuoi documenti rimangano integri!  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}