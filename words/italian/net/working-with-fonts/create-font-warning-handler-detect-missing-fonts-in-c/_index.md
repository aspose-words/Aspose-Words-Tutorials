---
category: general
date: 2026-02-12
description: Crea un gestore di avvisi sui font per rilevare i font mancanti e tenere
  traccia dei font mancanti in Aspose.Words. Scopri come registrare gli avvisi in
  modo efficiente.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: it
og_description: Crea un gestore di avvisi sui font in C# per rilevare i font mancanti
  e impara come registrare gli avvisi quando Aspose.Words sostituisce i font.
og_title: Crea gestore di avvisi sui font – Rileva i font mancanti
tags:
- Aspose.Words
- C#
- Document Processing
title: Crea Gestore di Avvisi sui Font – Rileva Font Mancanti in C#
url: /it/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea Gestore di Avvisi di Font – Rileva i Font Mancanti in C#

Hai mai avuto bisogno di **creare un gestore di avvisi di font** perché un documento Word ha sostituito silenziosamente un font che non ti aspettavi? Non sei l'unico. Quando Aspose.Words carica un DOCX che fa riferimento a un font assente sul server, passa silenziosamente a un font predefinito, lasciando il layout leggermente rotto.  

In questo tutorial ti mostreremo esattamente come **rilevare i font mancanti**, **tenere traccia dei font mancanti** e **registrare gli avvisi** in modo da individuare queste sostituzioni prima che diventino un problema. Alla fine avrai un gestore di avvisi riutilizzabile che stampa ogni evento di sostituzione del font sulla console (o su qualsiasi logger tu preferisca). Nessun mistero, solo codice chiaro e azionabile.

## Prerequisiti

- .NET 6.0 o successivo (l'API è la stessa per .NET Framework 4.6+)
- Aspose.Words per .NET installato (`dotnet add package Aspose.Words`)
- Un file Word che fa riferimento a un font non installato sulla tua macchina (ad es., `MissingFont.docx`)

Se hai già tutto questo, ottimo—passiamo subito al lavoro.

## Passo 1: Configura LoadOptions con un Callback di Avviso  

La prima cosa da fare quando vuoi **creare un gestore di avvisi di font** è dire ad Aspose.Words di lanciare un callback ogni volta che incontra un problema. `LoadOptions` è il contenitore per questa configurazione.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Perché è importante:**  
`LoadOptions` è l'unico posto in cui puoi collegare un `IWarningCallback`. Senza di esso, Aspose.Words registra gli avvisi internamente ma non li vedrai mai. Assegnando `FontWarningHandler` otteniamo il pieno controllo su cosa succede quando un font mancante viene sostituito.

## Passo 2: Implementa la Classe FontWarningHandler  

Ora creiamo effettivamente il codice per **creare un gestore di avvisi di font**. La classe implementa `IWarningCallback` e riceve un oggetto `WarningInfo` per ogni avviso sollevato da Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Spiegazione:**  
- `info.Type` indica la categoria dell'avviso. Ci interessa `WarningType.FontSubstitution` perché è quello che segnala un font mancante.  
- `info.Description` contiene un messaggio leggibile dall'uomo, ad esempio *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Scrivendo su `Console.WriteLine` **registriamo gli avvisi** immediatamente. In un'applicazione reale potresti sostituire ciò con `ILogger`, un writer su file o un servizio di telemetria.

> **Consiglio:** Se devi raccogliere tutti i font mancanti per un report successivo, memorizza `info.Description` in una `List<string>` invece di stamparla.

## Passo 3: Carica il Documento Usando le LoadOptions Configurate  

Con il callback in atto, il caricamento di un documento attiverà automaticamente il nostro gestore ogni volta che un font è mancante.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Cosa vedrai:**  
Eseguendo il programma verrà stampato qualcosa di simile a:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Quella riga conferma che hai **rilevato con successo i font mancanti** e ora stai **tenendo traccia dei font mancanti** in tempo reale.

## Passo 4: Verifica che il Gestore Funzioni con Scenari Diversi  

È facile presumere che il gestore funzioni solo per file DOCX, ma Aspose.Words supporta molti formati. Prova a caricare un PDF che fa riferimento a un font incorporato, o un vecchio file `.doc`. Lo stesso callback viene attivato per qualsiasi formato che passa attraverso la pipeline di risoluzione dei font.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Se il PDF fa riferimento a un font non installato, otterrai lo stesso output sulla console. Questo dimostra che la tua soluzione per **creare un gestore di avvisi di font** è indipendente dal formato.

## Passo 5: Estendere il Gestore – Registrare su File  

L'output sulla console è comodo per le demo, ma il codice di produzione di solito scrive su un file di log. Ecco una rapida modifica.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Ora, ogni volta che un font viene sostituito, il messaggio viene aggiunto a `font-warnings.log`. Questo soddisfa la parte **come registrare gli avvisi** del brief e ti fornisce una traccia di audit persistente.

## Passo 6: Metti Tutto Insieme – Esempio Completo e Eseguibile  

Di seguito trovi il programma completo che puoi copiare‑incollare in un'app console. Non mancano parti; sostituisci semplicemente il percorso del file con il tuo documento.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Risultato atteso:**  

- La console stampa ogni riga di sostituzione.  
- `font-warnings.log` ora contiene un record con timestamp di ogni evento di font mancante.  
- Il file `output.pdf` viene creato usando i font sostituiti, garantendo che la conversione riesca anche quando i font originali non sono disponibili.

## Domande Frequenti & Casi Limite  

| Domanda | Risposta |
|----------|--------|
| *E se volessi ignorare alcuni font?* | All'interno di `Warning`, controlla `info.Description` per il nome del font e usa `return;` subito per i font che consideri accettabili. |
| *Il gestore si attiverà per i font incorporati?* | No—i font incorporati sono sempre disponibili per il documento, quindi non viene generato alcun avviso di sostituzione. |
| *Posso catturare altri tipi di avviso (ad es., problemi di risoluzione delle immagini)?* | Assolutamente. Rimuovi il controllo `if (info.Type == WarningType.FontSubstitution)` o aggiungi blocchi `if` aggiuntivi per `WarningType.ImageResolution`. |
| *Il gestore è thread‑safe?* | L'implementazione predefinita scrive su file senza sincronizzazione. Per scenari multithread, avvolgi le scritture su file in un lock o utilizza un logger concorrente. |

## Prossimi Passi  

Ora che sai **come registrare gli avvisi** per i font mancanti, potresti voler:

- **Rilevare i font mancanti** durante un processo di importazione batch e generare un report riepilogativo.  
- **Tenere traccia dei font mancanti** su più documenti e inviare un avviso email quando un determinato font appare frequentemente.  
- **Integrare con un sistema di monitoraggio** (ad es., Azure Application Insights) per visualizzare le tendenze di sostituzione dei font nel tempo.  

Tutte queste estensioni si basano sulla stessa fondazione `IWarningCallback` che abbiamo creato.

---

*Buon coding! Se incontri stranezze—magari una cartella di font personalizzata o una condivisione di rete—lascia un commento qui sotto. La community (e io) siamo sempre felici di aiutarti a perfezionare la tua strategia di avvisi sui font.* 

![esempio di gestore di avvisi di font](image-placeholder.png "esempio di gestore di avvisi di font")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}