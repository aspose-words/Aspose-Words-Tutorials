---
category: general
date: 2026-08-04
description: Crea un documento Word programmaticamente usando C#. Scopri come aggiungere
  programmaticamente un pulsante di comando con Aspose.Words in pochi passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: it
lastmod: 2026-08-04
og_description: Crea un documento Word programmaticamente con Aspose.Words. Questa
  guida mostra come aggiungere programmaticamente un pulsante di comando, configurarlo
  e salvare il file.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Crea un documento Word programmaticamente – tutorial completo C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crea documento Word programmaticamente – guida passo passo
url: /it/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word programmaticamente – tutorial completo C#

Se hai bisogno di **creare documenti Word programmaticamente**, questa guida ti mostra esattamente come farlo con Aspose.Words per .NET. In poche righe di C# puoi generare un file `.docx` vuoto, **aggiungere programmaticamente** controlli **command button**, impostare le loro proprietà e salvare il risultato.  

I passaggi seguenti coprono tutto, dalla configurazione del progetto alla gestione dei casi limite, così potrai copiare il codice nella tua applicazione e eseguirlo senza modifiche.

## Cosa otterrai

Alla fine di questo tutorial sarai in grado di:

* Inizializzare un nuovo documento Word interamente in memoria.  
* **Aggiungere programmaticamente** controlli OLE **command button** in qualsiasi posizione e dimensione.  
* Configurare la didascalia del pulsante, il nome interno e altre proprietà OLE.  
* Salvare il documento generato su disco o in uno stream per ulteriori elaborazioni.

### Prerequisiti

* .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+).  
* Una licenza valida di Aspose.Words per .NET (o una valutazione gratuita).  
* Familiarità di base con C# e Visual Studio (o qualsiasi IDE di tua scelta).  

> **Consiglio professionale:** Se esegui il campione senza licenza, Aspose.Words aggiungerà una piccola filigrana di valutazione alla prima pagina.

## Passo 1: Configura il progetto e importa i namespace richiesti

Crea una nuova Console App (o integrala in un servizio esistente) e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Quindi includi i namespace essenziali all'inizio del tuo file `.cs`:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Queste importazioni ti danno accesso a `Document`, `DocumentBuilder`, `Forms2OleControl` e alla struttura `RectangleF` usata per il posizionamento.

## Passo 2: Inizializza un nuovo documento Word

La prima operazione in qualsiasi flusso **creare documento Word programmaticamente** è istanziare un oggetto `Document`. Questo oggetto vive solo in memoria finché non lo salvi esplicitamente.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` agisce come un cursore che traccia dove verrà posizionato il prossimo elemento. Usarlo mantiene il codice conciso e rispecchia il modo in cui si scriverebbe direttamente in Word.

## Passo 3: Inserisci un controllo OLE command button

Aspose.Words fornisce il metodo `InsertForms2OleControl` per incorporare oggetti OLE come command button, caselle di controllo o caselle combinate. Il metodo richiede tre argomenti:

1. Il valore enum `ControlType` (qui `CommandButton`).  
2. Un `RectangleF` che definisce la posizione X‑Y e la larghezza‑altezza del controllo (misurati in punti, dove 72 pt = 1 inch).  
3. Facoltativamente, proprietà OLE aggiuntive (non necessarie per il pulsante di base).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Perché funziona:** `InsertForms2OleControl` crea un contenitore OLE nel documento e restituisce un wrapper `Forms2OleControl`. Il wrapper ti consente di manipolare l'oggetto OLE sottostante (il pulsante reale) senza dover gestire l'interoperabilità COM a basso livello.

## Passo 4: Configura la didascalia e il nome interno del pulsante

Dopo l'inserimento, di solito vuoi assegnare al pulsante un'etichetta visibile all'utente e un identificatore interno che la tua macro o add‑in possa riferire in seguito.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` è il testo visualizzato sul pulsante nell'interfaccia di Word.  
* `Name` è l'identificatore programmatico usato da VBA o script di automazione esterni.

### Opzionale: Assegna una macro al pulsante

Se prevedi di eseguire una macro VBA quando il pulsante viene cliccato, puoi collegare il nome della macro:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Caso limite:** Quando il documento di destinazione verrà aperto su una macchina senza la macro, Word mostrerà un avviso di sicurezza. Firma sempre le tue macro o informa gli utenti delle impostazioni richieste.

## Passo 5: Salva il documento

Puoi scrivere il file su disco, in un `MemoryStream` o direttamente in un oggetto di risposta in una web API. L'approccio più semplice per una demo console è salvare in una cartella locale:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Il `.docx` risultante si apre in Microsoft Word con un pulsante command button funzionante che mostra “Click Me”. Cliccando il pulsante verrà attivata la macro assegnata (se presente) o verrà semplicemente mostrato un messaggio predefinito.

## Esempio completo funzionante

Copia il programma seguente in `Program.cs` ed eseguilo. Dimostra l'intero flusso **creare documento Word programmaticamente**, inclusa la gestione degli errori.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Risultato atteso:** Aprendo `CommandButton.docx` in Word appare un pulsante etichettato “Click Me”. Passando il mouse sopra il pulsante si rivela il nome `cmdClickMe` nel riquadro delle proprietà.

## Domande comuni e risoluzione dei problemi

| Domanda | Risposta |
|----------|--------|
| *Posso aggiungere il pulsante a un documento esistente?* | Sì. Carica il file con `new Document("Existing.docx")`, poi usa la stessa chiamata `InsertForms2OleControl`. |
| *Quali unità usa `RectangleF`?* | Punti (1 inch = 72 pt). Regola i valori per posizionare il pulsante con precisione. |
| *Il pulsante funzionerà su Word per Mac?* | I controlli OLE sono supportati solo su Word per Windows. Su Mac il pulsante appare come un'immagine statica. |
| *È necessaria una licenza per l'uso in produzione?* | Una licenza commerciale rimuove le filigrane di valutazione e sblocca tutte le funzionalità. |
| *Come modifico le dimensioni del pulsante dopo l'inserimento?* | Modifica `commandButton.Width` e `commandButton.Height` o reinserisci con un nuovo `RectangleF`. |

## Estendere la soluzione

Ora che sai come **aggiungere programmaticamente** controlli **command button**, puoi approfondire questi argomenti correlati:

* **Inserire altri controlli di modulo** – usa `ControlType.CheckBox`, `ControlType.OptionButton`, ecc. (copre la keyword secondaria *Aspose.Words InsertForms2OleControl*).  
* **Popolare il documento con dati dinamici** – unisci dati da un database in tabelle o campi di stampa unione.  
* **Esportare in PDF** – dopo aver aggiunto il pulsante, chiama `doc.Save("output.pdf", SaveFormat.Pdf)` per produrre una versione PDF (rilevante per *C# Word automation*).  

## Conclusione

Ora disponi di un modello completo e pronto per la produzione per **creare documenti Word programmaticamente** e **aggiungere programmaticamente command button** usando Aspose.Words per .NET. Il tutorial ha coperto la configurazione del progetto, l'inizializzazione del documento, l'inserimento del pulsante OLE, la configurazione delle proprietà e il salvataggio del file. Sentiti libero di adattare il codice per inserire altri controlli di modulo, allegare macro o integrare la logica in servizi web o processi in background.

Buon coding e buona automazione dei documenti Word!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word con Aspose.Words – Guida passo‑passo](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Crea un documento Word con tabella usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}