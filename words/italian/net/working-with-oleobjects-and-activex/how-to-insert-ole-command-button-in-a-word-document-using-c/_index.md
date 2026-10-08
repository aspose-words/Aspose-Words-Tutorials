---
category: general
date: 2026-10-07
description: Impara come inserire un pulsante di comando OLE in un documento Word
  con Aspose.Words C#. Guida passo‑passo che copre DocumentBuilder, proprietà e salvataggio
  del file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: it
lastmod: 2026-10-07
og_description: Inserisci un pulsante di comando OLE in un documento Word usando C#.
  Segui questo conciso tutorial per aggiungere, configurare e salvare un CommandButton
  funzionante con Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Inserire un pulsante di comando OLE in Word con C# – guida completa ad Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Come inserire un pulsante di comando OLE in un documento Word usando C#
url: /it/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire un pulsante di comando OLE in un documento Word usando C#

Se hai bisogno di **inserire un pulsante di comando OLE** in un file Word in modo programmatico, questa guida ti mostra esattamente come farlo con Aspose.Words per .NET. Che tu stia creando un report compilato con un modulo o automatizzando un modello che richiede l'interazione dell'utente, i passaggi seguenti ti forniscono una soluzione completa e eseguibile.

Imparerai a creare un documento vuoto, usare il `DocumentBuilder` per posizionare un `Forms2OleControl`, impostare la didascalia e il nome del pulsante e infine salvare il `.docx`. Non sono necessari strumenti esterni oltre alla libreria Aspose.Words.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.7+)
* Una licenza valida di Aspose.Words per .NET o una chiave di valutazione gratuita
* Visual Studio 2022 (o qualsiasi IDE C# tu preferisca)
* Familiarità di base con la sintassi C# e i concetti OLE di Word

> **Suggerimento:** Se stai usando la valutazione gratuita, il documento generato conterrà una piccola filigrana. Una versione con licenza la rimuove automaticamente.

## Passo 1: Installare Aspose.Words

Aggiungi il pacchetto Aspose.Words al tuo progetto tramite NuGet:

```bash
dotnet add package Aspose.Words
```

Il pacchetto include gli spazi dei nomi `Aspose.Words.Drawing` e `Aspose.Words.Drawing.Ole` necessari per i controlli OLE.

## Passo 2: Inserire il pulsante di comando OLE con DocumentBuilder

Il cuore del tutorial è il metodo `InsertForms2OleControl`. Crea un **Forms2 OLE CommandButton** in una posizione e dimensione specifiche.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Perché funziona

* `DocumentBuilder` è l'API principale per creare documenti Word in modo programmatico.  
* `InsertForms2OleControl` indica ad Aspose.Words di incorporare un **controllo Forms2 OLE**, che è la tecnologia di modulo legacy di Word che supporta pulsanti di comando, caselle di controllo, ecc.  
* Il valore enum `OleControlType.CommandButton` specifica che il controllo inserito è un **pulsante di comando** — il tipo esatto che hai richiesto quando volevi **inserire un pulsante di comando OLE**.  
* Il `Rectangle` determina il posizionamento visivo. Regola le coordinate X/Y o la larghezza/altezza per adattarle al tuo layout.

## Passo 3: Salvare il documento

Dopo aver configurato il pulsante, scrivi il documento su disco. Puoi scegliere qualsiasi formato supportato da Aspose.Words (`.docx`, `.pdf`, `.odt`, …). Per questo tutorial salveremo come documento Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando apri `CommandButton.docx` in Microsoft Word, vedrai un pulsante cliccabile con l'etichetta **Click Me**. Premendolo in Word si attiva la finestra di dialogo predefinita “Esegui macro” perché il pulsante è un controllo di modulo OLE; in seguito potrai collegare una macro o codice VBA se necessario.

## Passo 4: Verificare il risultato (output previsto)

Apri il file generato:

1. Il pulsante appare alle coordinate specificate (circa 1,4 pollici dalla sinistra e dall'alto della pagina).  
2. La didascalia è **Click Me**.  
3. La proprietà Name (`cmdSubmit`) è visibile nel riquadro **Sviluppatore → Proprietà** di Word, utile quando devi fare riferimento al controllo da VBA.

![Esempio di inserimento di un pulsante di comando OLE in un documento Word](insert-ole-button.png)

*Testo alternativo dell'immagine*: **Esempio di inserimento di un pulsante di comando OLE in un documento Word** (include la parola chiave principale per l'accessibilità e SEO).

## Casi limite e domande frequenti

### 1. Cosa succede se il pulsante non appare dove mi aspetto?

* Word utilizza i punti, non i pixel. Converti i pixel dello schermo in punti (`points = pixels * 72 / DPI`).  
* Assicurati che il rettangolo non intersechi i margini della pagina; altrimenti Word potrebbe spostare il controllo.

### 2. Posso inserire il pulsante in un documento esistente?

Sì. Carica il documento con `new Document("Existing.docx")` e utilizza lo stesso flusso di lavoro `DocumentBuilder`. Ricorda solo di spostare il cursore del builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, ecc.) prima di chiamare `InsertForms2OleControl`.

### 3. Come posso collegare una macro al pulsante?

Aspose.Words non crea codice VBA, ma puoi incorporare una macro dopo che il documento è stato generato:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Funziona con .NET Core su Linux?

Il controllo OLE è una funzionalità specifica di Windows perché si basa su COM. Su Linux il pulsante verrà inserito, ma apparirà come un'immagine statica senza comportamento interattivo. Per moduli interattivi multipiattaforma, considera l'uso dei controlli di contenuto (`StructuredDocumentTag`).

### 5. Cosa fare se ho bisogno di una dimensione diversa o di più pulsanti?

Crea ulteriori oggetti `Rectangle` con coordinate uniche e ripeti la chiamata a `InsertForms2OleControl`. Ogni pulsante può avere la propria `Caption` e `Name`.

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare in un'applicazione console. Include tutte le direttive `using` necessarie, la gestione degli errori e i commenti.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Esegui il programma, apri il `CommandButton.docx` generato e vedrai il pulsante **Click Me** pronto per ulteriori personalizzazioni.

## Conclusione

Adesso sai come **inserire un pulsante di comando OLE** in un documento Word usando C# e Aspose.Words. Il tutorial ha coperto:

* Installazione del pacchetto Aspose.Words  
* Uso di `DocumentBuilder.InsertForms2OleControl` con `OleControlType.CommandButton`  
* Impostazione delle proprietà del pulsante (`Caption`, `Name`)  
* Salvataggio e verifica dell'output

Da qui puoi esplorare argomenti correlati come **Aspose.Words OLE control** per caselle di controllo, caselle combinate o l'incorporamento di intere cartelle di lavoro Excel. Potresti anche sperimentare l'automazione del **pulsante di comando OLE di Word** in modelli più grandi, o sostituire i controlli OLE con i moderni **controlli di contenuto** per un migliore supporto multipiattaforma.

Sentiti libero di adattare i valori del rettangolo, aggiungere più pulsanti o collegare macro VBA per soddisfare le esigenze della tua applicazione. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}