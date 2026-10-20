---
category: general
date: 2026-10-20
description: Crea un documento Word programmaticamente e aggiungi un pulsante di comando
  usando Aspose.Words. Impara a inserire un controllo ActiveX e impostare la didascalia
  del pulsante.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: it
lastmod: 2026-10-20
og_description: Crea un documento Word programmaticamente e incorpora un pulsante
  di comando ActiveX. Questo tutorial spiega come inserire il controllo e impostarne
  la didascalia con Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Crea documento Word programmaticamente – aggiungi pulsante ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Crea documento Word programmaticamente con un pulsante ActiveX
url: /it/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word programmaticamente con un pulsante ActiveX

Crea un documento Word programmaticamente con Aspose.Words, quindi aggiungi un pulsante di comando su cui gli utenti possono fare clic. Questa guida ti accompagna nell'inserimento di un controllo ActiveX, nella configurazione delle sue proprietà e nel salvataggio del risultato come file **.docx**.

Vedrai un esempio completo e eseguibile che puoi copiare in un'applicazione console. Alla fine del tutorial potrai generare un file Word che contiene un pulsante di comando completamente funzionale e comprenderai come **add command button**, **add activex control**, **insert activex button** e **set button caption** senza uscire dal tuo codice C#.

## Prerequisiti

* .NET 6.0 SDK o versioni successive installate  
* Visual Studio 2022 (o qualsiasi IDE compatibile con C#)  
* Un file di licenza Aspose.Words per .NET (la versione di prova gratuita funziona per questo esempio)  
* Familiarità di base con C# e il sistema di progetti .NET  

Non sono necessari pacchetti NuGet aggiuntivi oltre a **Aspose.Words**, poiché il supporto ActiveX è integrato nella libreria.

## Passo 1: Configura il progetto e aggiungi Aspose.Words

1. Apri un terminale o Visual Studio e crea un nuovo progetto console:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Aggiungi il pacchetto Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Opzionale) Se disponi di un file di licenza, posizionalo nella radice del progetto e aggiungi la seguente riga all'inizio di `Program.cs` per evitare le filigrane di valutazione:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Passo 2: Crea documento Word programmaticamente – inizializza il documento

La prima operazione è **creare un documento Word programmaticamente**. Lo fai istanziando un oggetto `Document` e un `DocumentBuilder` che ti permette di modificare il contenuto del documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` rappresenta l'intero file, mentre `DocumentBuilder` mantiene un cursore che puoi spostare in qualsiasi posizione del documento. Questa separazione mantiene pulita l'API e ti consente di **add activex control** in seguito senza gestire manualmente strutture di basso livello.

## Passo 3: Aggiungi pulsante di comando – inserimento di un controllo ActiveX

Ora **add command button** inserendo un controllo ActiveX di tipo `OleControlType.CommandButton`. Il metodo `InsertForms2OleControl` richiede il tipo di controllo, una posizione (`Point`) e una dimensione (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

La chiamata sopra **insert activex button** nel documento alle coordinate esatte che specifichi. Le coordinate sono misurate in punti (1 pt ≈ 1/72 in). Se hai bisogno del pulsante in un paragrafo specifico, sposta prima il cursore del builder:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Passo 4: Imposta la didascalia del pulsante – personalizzare il testo del pulsante di comando

Un pulsante senza etichetta è confuso, quindi **set button caption** a qualcosa di significativo. La proprietà `Caption` definisce il testo visualizzato sul pulsante, mentre `Name` assegna al controllo un identificatore programmatico.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Se in seguito esporti il documento in un formato abilitato alle macro (`.docm`), il valore `OnClick` deve corrispondere al nome di una macro VBA. Per un semplice `.docx`, la proprietà viene memorizzata ma non eseguita, il che è accettabile per la maggior parte degli scenari di automazione.

## Passo 5: Salva il documento contenente il pulsante ActiveX

Dopo aver configurato il controllo, puoi **save the document**. Scegli una directory a cui hai accesso in scrittura e utilizza l'estensione `.docx` per la massima compatibilità.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Quando apri il file generato in Microsoft Word, vedrai un pulsante etichettato **Submit** alle coordinate specificate. Cliccando il pulsante nel client desktop si tenterà di eseguire la macro `SubmitForm` (se esiste).

## Passo 6: Verifica il risultato e risolvi i problemi comuni

1. Apri `ActiveXCommandButton.docx` in Microsoft Word.  
2. Passa a **Design Mode** (scheda Sviluppatore → **Design Mode**) per vedere i bordi del pulsante.  
3. Se il pulsante non appare, verifica che la scheda **Developer** sia abilitata e che la tua versione di Word supporti i controlli ActiveX.  
4. Per i file abilitati alle macro (`.docm`), assicurati che il nome della macro in `OnClick` corrisponda a una routine VBA; altrimenti Word mostrerà un avviso di sicurezza.

### Consiglio professionale

I controlli ActiveX sono disponibili solo su Windows. Se hai bisogno di interattività multipiattaforma, considera l'uso di **Content Controls** (`RichTextContentControl`) invece di un pulsante ActiveX.

## Codice sorgente completo

Di seguito trovi il programma completo, pronto per l'esecuzione. Copialo in `Program.cs` ed esegui `dotnet run`.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Optional: apply a license to remove evaluation watermarks
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // Step 2: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a paragraph to give context
        builder.Writeln("Please click the button below to submit the form:");
        builder.MoveToDocumentEnd();

        // Step 3: Add command button – insert ActiveX control
        Point position = new Point(100, 150);
        Size size = new Size(120, 30);
        Forms2OleControl commandButton = builder.InsertForms2OleControl(


## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word con pulsante ActiveX – Guida C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Aggiungi pulsante di comando a documento Word con Aspose.Words – Guida completa](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Crea pulsante documento Word con Aspose.Words – Esempio di codice completo](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}