---
category: general
date: 2026-08-14
description: Come aggiungere un pulsante ActiveX in un documento Word usando Aspose.Words
  – impara a creare un documento Word vuoto e inserire un pulsante ActiveX programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: it
lastmod: 2026-08-14
og_description: Come aggiungere un pulsante ActiveX in un documento Word con Aspose.Words.
  Questo tutorial ti mostra come creare un documento Word vuoto, inserire un pulsante
  ActiveX e salvare il risultato.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Come aggiungere un pulsante ActiveX in Word – Guida Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Come aggiungere un pulsante ActiveX in un documento Word con Aspose.Words
url: /it/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere un pulsante ActiveX in un documento Word con Aspose.Words

Se hai bisogno di **come aggiungere ActiveX** controlli in un file Word generato, questa guida ti mostra i passaggi esatti. Imparerai a **inserire pulsante ActiveX** programmaticamente, partendo da un **creare documento Word vuoto** e terminando con un file salvato che può essere aperto in Microsoft Word.

Aggiungere un pulsante che esegue codice VBA o attiva una macro è una necessità comune per generatori di report automatizzati, modelli di modulo o contratti interattivi. Usare Aspose.Words per .NET ti consente di costruire il documento senza avviare Office, mantenendo il processo veloce e adatto ai server.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 (o successivo) SDK installato.  
* Visual Studio 2022 o qualsiasi IDE compatibile con C#.  
* Pacchetto NuGet Aspose.Words per .NET (`Aspose.Words` versione 24.9 o più recente).  
  Installalo con:
  ```bash
  dotnet add package Aspose.Words
  ```
* Un ambiente Windows se prevedi di testare il pulsante ActiveX, perché i controlli ActiveX richiedono la versione Windows di Microsoft Word.

## Passo 1: Creare un documento Word vuoto

Il primo compito è **creare documento Word vuoto** in memoria. Aspose.Words fornisce la classe `Document` a questo scopo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` rappresenta l'intero file .docx. A questo punto il documento non contiene pagine, ma puoi iniziare ad aggiungere contenuti immediatamente.

## Passo 2: Inizializzare un DocumentBuilder

`DocumentBuilder` è un helper che ti permette di inserire testo, immagini e altri oggetti nel documento. Funziona sull'istanza `Document` appena creata.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder mantiene una posizione del cursore; tutto ciò che inserisci dopo questa riga apparirà all'inizio della prima pagina.

## Passo 3: Inserire un controllo ActiveX CommandButton

Aspose.Words espone il metodo `InsertForms2OleControl` per aggiungere controlli di modulo legacy, inclusi gli ActiveX. Il metodo richiede il tipo di controllo e le sue dimensioni in punti.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

L'oggetto `Forms2OleControl` restituito ti consente di configurare proprietà come il nome del controllo e la didascalia.

## Passo 4: Configurare le proprietà del pulsante

Impostare un `Name` significativo ti permette di fare riferimento al controllo dal codice VBA in seguito. La `Caption` è il testo che l'utente vede sul pulsante.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Mantieni il nome breve e alfanumerico; Word rifiuterà nomi che contengono spazi o caratteri speciali.

## Passo 5: Salvare il documento

Infine, scrivi il documento su disco. Usa l'estensione `.docx` per i file Word moderni; il pulsante ActiveX funziona allo stesso modo nei file `.doc`, ma `.docx` è il formato preferito per i nuovi progetti.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Quando apri `ActiveXButton.docx` in Microsoft Word, vedrai un pulsante **Submit** cliccabile. Se abiliti le macro, puoi collegare del codice VBA a `btnSubmit_Click` e farlo eseguire quando l'utente preme il pulsante.

## Esempio completo, eseguibile

Unire tutti i pezzi ti fornisce un programma autonomo che puoi copiare, incollare ed eseguire.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output previsto** – Dopo aver eseguito il programma, la console stampa il percorso di salvataggio e, aprendo il file generato in Word, viene mostrato un pulsante etichettato **Submit** posizionato in alto nella prima pagina.

## Gestione di domande comuni e casi limite

### Il pulsante funziona in tutte le versioni di Word?

I controlli ActiveX sono supportati nella versione desktop di Word su Windows. Non vengono visualizzati in Word Online, Word per macOS o nei client mobili. Se ti serve interattività multipiattaforma, considera l'uso di controlli di contenuto o soluzioni basate su HTML.

### E se ho bisogno di una dimensione o posizione diversa?

`InsertForms2OleControl` posiziona il controllo al cursore corrente del builder. Per spostarlo, regola il cursore con `builder.MoveTo` prima dell'inserimento, oppure modifica le proprietà `Left` e `Top` del controllo dopo la creazione:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Posso aggiungere altri tipi di ActiveX?

Sì. L'enumerazione `Forms2OleControlType` include `CheckBox`, `OptionButton`, `ListBox` e altro. Sostituisci `CommandButton` con il valore enum desiderato e adatta le proprietà di conseguenza.

### È necessaria una macro perché il pulsante faccia qualcosa?

Il pulsante di per sé non fa nulla finché non gli associ del codice VBA. In Word, premi **Alt+F11** per aprire l'editor VBA, individua `btnSubmit_Click` e scrivi la logica desiderata. Il documento generato manterrà il progetto VBA se usi il formato **SaveFormat.Doc** (legacy `.doc`), ma i file `.docx` non possono contenere macro VBA. Usa il formato `.doc` se ti servono macro incorporate.

## Conclusione

Ora sai **come aggiungere ActiveX** controlli a un file Word usando Aspose.Words. Seguendo i passaggi per **creare documento Word vuoto**, inizializzare un `DocumentBuilder`, **inserire pulsante ActiveX**, configurarne le proprietà e salvare il file, puoi generare modelli Word interattivi direttamente dal tuo codice .NET.

Successivamente, esplora argomenti correlati come la gestione degli eventi di **insert ActiveX button**, l'aggiunta di **create word document aspose** per tabelle o immagini, e la protezione dei documenti abilitati alle macro per la distribuzione aziendale. Sperimenta con diversi tipi di controllo e opzioni di layout per adattare l'esperienza utente alle esigenze della tua applicazione.

Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word con intestazione e piè di pagina usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea un documento Word con tabella usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}