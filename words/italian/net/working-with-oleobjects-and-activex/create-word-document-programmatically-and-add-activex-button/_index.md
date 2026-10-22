---
category: general
date: 2026-08-10
description: Crea un documento Word programmaticamente con Aspose.Words, quindi aggiungi
  un pulsante ActiveX. Inserisci un pulsante di comando ActiveX in pochi minuti.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: it
lastmod: 2026-08-10
og_description: Crea un documento Word programmaticamente usando Aspose.Words, quindi
  aggiungi un pulsante Word ActiveX. Scopri come inserire rapidamente un pulsante
  di comando ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Crea un documento Word programmaticamente – aggiungi un pulsante ActiveX
  in C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Crea un documento Word programmaticamente e aggiungi un pulsante ActiveX
url: /it/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word programmaticamente e aggiungi un pulsante ActiveX

Se hai bisogno di **creare un documento Word programmaticamente**, questa guida ti accompagna passo passo attraverso l'intero processo con Aspose.Words per .NET. Imparerai anche come **aggiungere elementi di controllo ActiveX** e **inserire oggetti pulsante di comando ActiveX** in un unico esempio autonomo.

Generare file Word dal codice elimina il passaggio manuale di aprire Microsoft Word, consentendoti di creare report, fatture o contratti basati su dati in modo automatico. Alla fine di questo tutorial avrai un'app console C# pronta all'uso che produce un file `.docx` contenente un pulsante di comando ActiveX interattivo.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK o versioni successive (il codice funziona anche con .NET Framework 4.6+)
* Visual Studio 2022 o qualsiasi IDE che supporti lo sviluppo .NET
* Una licenza valida di Aspose.Words per .NET (puoi utilizzare la chiave di valutazione gratuita per i test)
* Familiarità di base con la sintassi C# e il concetto di controlli COM/ActiveX

> **Suggerimento professionale:** Se prevedi di distribuire il documento generato a utenti che non hanno Word installato, incorpora i file runtime del controllo ActiveX accanto al `.docx` o fornisci un modello abilitato alle macro.

## Create word document programmatically – initial setup

First, add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

Then create a new console project (if you don’t already have one):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Open the generated `Program.cs` file – we’ll replace its contents with the full solution below.

## Step 1: Import namespaces and configure the license

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Perché è importante*: Importare `Aspose.Words.Drawing` ti dà accesso a `Forms2OleControl`, la classe che rappresenta un controllo ActiveX all'interno di un documento Word. Impostare una licenza subito evita avvisi di runtime in produzione.

## Step 2: Create a blank document and a DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

L'oggetto `Document` è la rappresentazione in memoria di un file `.docx`. `DocumentBuilder` funziona come un cursore che si sposta nel documento per inserire elementi.

## Step 3: Insert an ActiveX CommandButton control

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` crea un oggetto OLE che Word tratta come un controllo ActiveX. Il sistema di coordinate utilizza i punti (1 punto = 1/72 di pollice), che corrisponde al motore di layout di Word.

## Step 4: Set the button’s caption and optional properties

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Impostare la proprietà `Caption` è il modo più comune per etichettare il pulsante. Se hai bisogno che il pulsante esegua una macro VBA, assegna il nome della macro a `OnAction`. Questo tutorial si concentra sulla parte visiva; l'integrazione delle macro è trattata nella sezione “Passaggi successivi”.

## Step 5: Save the document

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Quando esegui il programma, vedrai un messaggio nella console che conferma che `ActiveX_CommandButton.docx` è stato scritto su disco.

### Full source code (copy‑paste ready)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Eseguendo lo snippet si genera un file Word che contiene un **pulsante di comando ActiveX** cliccabile. Apri il file in Microsoft Word, passa alla **Modalità Design** (scheda Sviluppatore → Modalità Design) e vedrai il pulsante renderizzato esattamente dove lo hai posizionato.

## Step 6: Verify the result

1. Apri `ActiveX_CommandButton.docx` in Microsoft Word.
2. Abilita la scheda **Sviluppatore** se non è visibile (`File → Opzioni → Personalizza barra multifunzione → spunta Sviluppatore`).
3. Fai clic su **Modalità Design**. Il pulsante dovrebbe apparire con l'etichetta “Submit”.
4. Se hai aggiunto una macro `OnAction`, fai clic sul pulsante con la Modalità Design disattivata per attivare la macro.

Se il pulsante non appare, assicurati che le impostazioni di sicurezza di Word consentano i controlli ActiveX (`File → Opzioni → Centro protezione → Impostazioni Centro protezione → Impostazioni ActiveX`).

## Common questions and edge cases

| Domanda | Risposta |
|----------|--------|
| **Posso inserire altri tipi di ActiveX?** | Sì. L'enumerazione `Forms2OleControlType` include `CheckBox`, `OptionButton`, `ComboBox`, ecc. Sostituisci `CommandButton` con il valore enum desiderato |

## What Should You Learn Next?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea un documento Word con intestazione e piè di pagina usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Inserisci immagine in linea in un documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}