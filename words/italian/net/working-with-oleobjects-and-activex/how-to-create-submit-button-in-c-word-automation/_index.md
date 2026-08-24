---
category: general
date: 2026-08-23
description: Crea un pulsante di invio in C# per l'automazione di Word. Impara ad
  aggiungere un pulsante ActiveX, impostare il nome del pulsante, la didascalia e
  il testo programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: it
lastmod: 2026-08-23
og_description: Crea un pulsante di invio in automazione Word con C#. Questa guida
  mostra come aggiungere un pulsante ActiveX, impostarne nome, didascalia e testo
  usando Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Crea pulsante di invio in automazione Word con C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Come creare un pulsante di invio in automazione Word con C#
url: /it/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un pulsante di invio in C# Word automation

Se hai bisogno di **creare un pulsante di invio** all'interno di un documento Word usando C#, questa guida ti accompagna passo passo. Vedrai come aggiungere un pulsante ActiveX, assegnare un nome programmatico e impostare la didascalia del pulsante in modo che assomigli a un normale controllo *Submit*.

L'automazione dei controlli modulo in Word può sostituire il lavoro manuale di layout e garantire coerenza su centinaia di documenti. Nei passaggi seguenti imparerai anche come **impostare il testo del pulsante**, **impostare il nome del pulsante** e **impostare la didascalia del pulsante** — tutti essenziali quando il pulsante partecipa a un flusso di lavoro guidato da macro.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 (o successivo) installato.
* Un riferimento a **Aspose.Words for .NET** (la libreria che fornisce `DocumentBuilder.InsertForms2OleControl`).
* Conoscenza di base di C# e dei controlli modulo ActiveX di Word.

Puoi installare Aspose.Words tramite NuGet:

```bash
dotnet add package Aspose.Words
```

> **Consiglio:** Usa l'ultima versione stabile di Aspose.Words per beneficiare di correzioni di bug e nuove funzionalità relative ai controlli ActiveX.

## Panoramica della soluzione

Il tutorial è organizzato in tre passaggi chiari:

1. **Aggiungere pulsante ActiveX** – utilizza il metodo `InsertForms2OleControl` per inserire un pulsante di comando nel documento.  
2. **Impostare il nome del pulsante** – assegna un identificatore programmatico unico con la proprietà `Name`.  
3. **Impostare la didascalia del pulsante** – definisci il testo visibile sul pulsante tramite la proprietà `Caption` (che controlla anche il **set button text** visualizzato nell'interfaccia).

Al termine della guida avrai una routine **creare pulsante di invio** completamente funzionale che potrai riutilizzare in qualsiasi progetto di automazione Word.

## Passo 1: Aggiungere un pulsante ActiveX al documento

Il primo compito è **aggiungere un pulsante activex** al file Word. Aspose.Words espone l'enumerazione `Forms2OleControlType.CommandButton` a questo scopo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Perché questo passaggio è importante:**  
I controlli ActiveX sono gli unici elementi modulo di Word che possono eseguire macro VBA o interagire con codice esterno. Aggiungere il controllo crea un segnaposto che i passaggi successivi possono configurare.

> **Caso limite:** Se il documento contiene già un controllo con lo stesso nome, Word rinominerà automaticamente quello nuovo (ad es., `CommandButton1`). Impostare esplicitamente il nome nel passaggio successivo evita tali collisioni.

## Passo 2: Impostare il nome del pulsante

Un affidabile **set button name** è fondamentale quando è necessario fare riferimento al controllo da VBA o da altre parti del tuo codice C#. La proprietà `Name` assegna al pulsante un identificatore programmatico.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Perché dovresti impostare un nome:**  
Quando il documento viene aperto, VBA può recuperare il pulsante tramite `ActiveDocument.InlineShapes("btnSubmit")`. Un nome significativo come `btnSubmit` chiarisce anche l'intento quando si ispeziona l'XML del documento.

> **Consiglio:** Mantieni i nomi brevi, alfanumerici e che inizino con una lettera per rimanere compatibili con le regole di denominazione VBA.

## Passo 3: Impostare la didascalia del pulsante (testo visibile)

Il testo che gli utenti vedono sul pulsante è controllato dalla proprietà **set button caption**. Nell'interfaccia di Word questo appare come l'etichetta del pulsante, che è anche il **set button text** che desideri visualizzare.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Perché la didascalia è importante:**  
La didascalia è l'etichetta visibile all'utente. Modificarla in seguito non influisce sul nome del pulsante, così puoi localizzare l'interfaccia senza rompere il codice che dipende da `btnSubmit`.

> **Domanda comune:** *Posso impostare sia Caption che Value?*  
> Per un `CommandButton`, `Caption` controlla l'etichetta, mentre `Value` non è usato. Se ti serve un valore nascosto, memorizzalo in una proprietà documento personalizzata.

## Esempio completo funzionante

Unendo i tre passaggi ottieni una routine completa che puoi inserire in qualsiasi applicazione console o Windows:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Output previsto

Eseguendo il programma viene creato `SubmitButton.docx`. Quando apri il file in Microsoft Word:

* Un pulsante **Submit** appare nella posizione specificata.
* Il nome del pulsante è `btnSubmit` (verifica tramite *Developer → Design Mode → Properties*).
* Cliccando il pulsante in modalità design viene mostrata la didascalia *Submit*.

Ora hai un blocco riutilizzabile per qualsiasi soluzione Word basata su moduli.

## Considerazioni aggiuntive

### Gestione delle collisioni di denominazione

Se esegui la routine più volte sullo stesso documento, Word potrebbe rinominare automaticamente i controlli duplicati. Per garantire l'unicità, puoi anteporre un GUID:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Localizzare la didascalia del pulsante

Per documenti multilingua, memorizza le didascalie in un file di risorse e assegnale a runtime:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Rispondere al click del pulsante

Il pulsante stesso non contiene logica di click in C#. Tipicamente si associa una macro VBA:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Poiché hai **set button name** a `btnSubmit`, il nome della macro segue automaticamente la convenzione `<Name>_Click`.

## FAQ di risoluzione problemi

| Domanda | Risposta |
|----------|--------|
| **Perché il pulsante appare vuoto?** | Assicurati di impostare la proprietà `Caption`; senza di essa il pulsante non mostra testo. |
| **Posso usare un controllo ActiveX diverso?** | Sì. Sostituisci `Forms2OleControlType.CommandButton` con `CheckBox`, `OptionButton`, ecc., ma le proprietà differiscono. |
| **È compatibile con .NET Core?** | Aspose.Words for .NET supporta .NET 6+, quindi lo stesso codice funziona su .NET Core e .NET Framework. |
| **E se il documento ha già un pulsante?** | Usa un `Name` unico (ad esempio aggiungendo un GUID) per evitare conflitti. |

## Conclusione

Ora sai come **creare un pulsante di invio** programmaticamente in un documento Word usando C#. Seguendo i tre passaggi—**add activex button**, **set button name** e **set button caption**—puoi impostare in modo affidabile **set button text**, **set button name** e **set button caption** per qualsiasi soluzione di modulo automatizzata.

Da qui potresti esplorare:

* Aggiungere macro VBA che reagiscono al click del **submit button**.
* Stilizzare il pulsante con caratteri o colori personalizzati tramite l'XML sottostante.
* Generare più pulsanti in un ciclo per moduli dinamici.

Sentiti libero di sperimentare con diverse didascalie, nomi e posizioni per adattarle al tuo flusso di lavoro specifico. Buona automazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}