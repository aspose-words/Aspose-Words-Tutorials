---
category: general
date: 2026-11-22
description: Impara a inserire un controllo Forms2Ole in Word con C#. Questa guida
  passo passo copre DocumentBuilder, il posizionamento del pulsante di comando e il
  salvataggio del .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: it
lastmod: 2026-11-22
og_description: Inserisci il controllo Forms2Ole in Word con C#. Segui questa guida
  per aggiungere un pulsante di comando usando Aspose.Words e DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Inserire il controllo Forms2Ole in Word con C# – guida completa
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come inserire il controllo Forms2Ole in Word usando C# e Aspose.Words
url: /it/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire il controllo Forms2Ole in Word usando C# e Aspose.Words

Se hai bisogno di **inserire il controllo Forms2Ole in Word**, questo tutorial ti mostra esattamente come farlo con C#. Che tu stia creando un modello compilabile o automatizzando la creazione di moduli, la soluzione qui sotto ti permette di aggiungere un pulsante di comando programmaticamente.

Imparerai a creare un documento vuoto, usare `DocumentBuilder` per posizionare il controllo e salvare il risultato come `.docx`. La guida copre anche le difficoltà più comuni, come i sistemi di coordinate e la compatibilità con versioni più vecchie di Word.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+)
* Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`)
* Una conoscenza di base di C# e del modello a oggetti di Word
* Un IDE come Visual Studio o VS Code

## Passo 1: Configura il progetto e importa i namespace

Crea una nuova applicazione console e aggiungi il pacchetto Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

In `Program.cs` importa i namespace richiesti:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Suggerimento:** Usa l'ultima versione di Aspose.Words per ottenere il supporto completo all'API `Forms2OleControl`.

## Passo 2: Crea un documento vuoto e inizializza DocumentBuilder

La classe `Document` rappresenta il file Word, mentre `DocumentBuilder` fornisce i metodi per inserire contenuti.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funziona come un cursore; dopo questa riga puoi iniziare a posizionare elementi ovunque nel documento.

## Passo 3: Definisci la posizione e le dimensioni del pulsante

Word misura le coordinate in punti (1 pt ≈ 1/72 in). La struttura `Rectangle` di `System.Drawing` descrive i confini del controllo.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` posiziona il controllo nell'angolo in alto a sinistra della pagina corrente.
* Modifica `x` e `y` per spostare il pulsante altrove (ad esempio `new Rectangle(150, 200, 100, 30)`).

## Passo 4: Inserisci il pulsante di comando Forms2Ole

Ora usa `InsertForms2OleControl` per aggiungere il controllo. Il metodo richiede il tipo di controllo, un nome e i confini definiti sopra.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

L'oggetto `Forms2OleControl` restituito ti consente di modificare proprietà come `Enabled`, `Visible` o anche di associare un nome macro in seguito.

### Perché usare Forms2Ole?

* **Compatibilità legacy** – I controlli Forms2Ole funzionano in Word 97‑2003 (`.doc`) e nei file `.docx` più recenti.
* **Supporto macro** – Possono attivare macro VBA, rendendoli ideali per modelli interattivi.
* **Posizionamento preciso** – A differenza dei controlli di contenuto, controlli le coordinate esatte.

## Passo 5: Salva il documento

Infine, scrivi il file su disco. Scegli una cartella in cui hai i permessi di scrittura.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Apri `output.docx` in Microsoft Word. Vedrai un pulsante etichettato **ClickMe** nell'angolo in alto a sinistra della prima pagina. Cliccarlo in Word non farà nulla finché non assegnerai una macro, ma il controllo è pienamente funzionante.

## Gestione dei casi limite più comuni

| Situazione | Come affrontarla |
|-----------|-------------------|
| **Il pulsante appare fuori pagina** | Verifica che le coordinate di `Rectangle` siano entro i margini della pagina. Usa `builder.PageSetup.PageWidth` e `PageHeight` per calcolare limiti sicuri. |
| **Il controllo non è visibile in versioni più vecchie di Word** | Salva il documento come `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) per garantire la compatibilità Forms2Ole con Word 97‑2003. |
| **È necessario cambiare la didascalia** | Dopo l'inserimento, imposta `commandButton.Caption = "Submit";`. |
| **Assegnare una macro** | Imposta `commandButton.MacroName = "MyMacro"`; la macro deve esistere nel progetto VBA del documento. |
| **Pulsanti multipli** | Ripeti il Passo 4 con valori `Rectangle` diversi e nomi univoci. |

## Esempio completo, eseguibile

Mettendo tutto insieme, ecco un programma autonomo che puoi copiare, incollare ed eseguire:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output previsto:** Dopo aver eseguito il programma, `output.docx` si apre in Word con un pulsante cliccabile etichettato *Click Me!* posizionato in alto a sinistra della prima pagina.

## Conclusione

Ora sai come **inserire il controllo Forms2Ole in Word** usando C# e Aspose.Words. Il processo prevede la creazione di un `Document`, il posizionamento di un `Rectangle` e la chiamata a `InsertForms2OleControl` tramite `DocumentBuilder`. Con il codice completo e le indicazioni sui casi limite, puoi integrare pulsanti di comando in qualsiasi flusso di lavoro automatizzato di Word.

### Prossimi passi

* Esplora altri valori di `ControlType` come `CheckBox` o `OptionButton`.
* Combina i controlli Forms2Ole con macro VBA per moduli interattivi.
* Usa `DocumentBuilder.MoveTo` per posizionare i pulsanti su paragrafi o tabelle specifiche.
* Consulta la documentazione di Aspose.Words **Forms2Ole** per impostazioni avanzate delle proprietà.

Buona programmazione e divertiti a creare documenti Word più ricchi con C# e Aspose.Words!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci alternativi nei tuoi progetti.

- [Come inserire un pulsante di comando OLE in un documento Word usando C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Come aggiungere un controllo ActiveX in Word con Aspose.Words – guida passo‑a‑passo](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Aggiungere un pulsante di comando a un documento Word con Aspose.Words – Guida completa](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}