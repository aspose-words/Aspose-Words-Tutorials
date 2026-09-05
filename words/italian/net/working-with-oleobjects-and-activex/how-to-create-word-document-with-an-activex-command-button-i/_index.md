---
category: general
date: 2026-09-05
description: Crea un documento Word usando Aspose.Words C# e impara come inserire
  un pulsante di comando ActiveX, impostare le dimensioni del pulsante e aggiungere
  funzionalità interattive al pulsante.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: it
lastmod: 2026-09-05
og_description: Crea un documento Word in C# e inserisci un pulsante di comando ActiveX.
  Questo tutorial mostra come impostare le dimensioni del pulsante e aggiungere funzionalità
  interattive al pulsante.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Crea un documento Word con pulsante di comando ActiveX in C# – guida passo‑passo
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Come creare un documento Word con un pulsante di comando ActiveX in C#
url: /it/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word con un pulsante di comando ActiveX in C#

Se hai bisogno di **creare un documento Word** programmaticamente e incorporare un elemento UI cliccabile, questa guida ti mostra esattamente come fare. Utilizzando Aspose.Words per .NET puoi **creare un documento Word**, **aggiungere un pulsante di comando** e controllarne l'aspetto—tutto senza aprire Microsoft Word.

Imparerai **come inserire controlli ActiveX**, **impostare le dimensioni del pulsante** e far sì che il pulsante si comporti come un componente UI interattivo. Non è necessaria alcuna esperienza pregressa con COM o VBA; basta un ambiente di sviluppo .NET e la libreria Aspose.Words.

## Cosa otterrai

* **Crea un documento Word** da zero con C#.
* **Inserisci un pulsante di comando ActiveX** (il classico controllo “Click Me”).
* **Imposta le dimensioni del pulsante** e la posizione con precisione.
* Aggiungi facoltativamente una semplice logica di **pulsante interattivo** (ad esempio, un segnaposto macro).
* Salva il file come `.docx` che può essere aperto in Microsoft Word o in qualsiasi visualizzatore compatibile.

### Prerequisiti

| Requisito | Motivo |
|-----------|--------|
| .NET 6.0 o successivo | Fornisce il runtime per il codice C#. |
| Aspose.Words per .NET (ultima versione) | Fornisce le API `Document`, `DocumentBuilder` e `Forms2OleControl` usate nell'esempio. |
| Visual Studio 2022 (o qualsiasi IDE C#) | Rende facile compilare ed eseguire il campione. |
| Conoscenza di base di C# | Necessaria per comprendere il flusso del codice. |

> **Suggerimento:** Se stai usando una versione di prova di Aspose.Words, assicurati di impostare la licenza prima di eseguire il codice per evitare filigrane di valutazione.

## Come creare un documento Word – flusso di lavoro generale

Il processo consiste in quattro passaggi logici:

1. **Inizializza un nuovo documento** e un `DocumentBuilder` per modificarlo.  
2. **Inserisci un pulsante di comando ActiveX** usando `InsertForms2OleControl`.  
3. **Configura il pulsante** – didascalia, dimensioni e posizione.  
4. **Salva** il documento su disco.

Ogni passaggio è spiegato nella propria sezione di seguito.

![Documento Word con un pulsante ActiveX](/images/activex-button.png "Screenshot di un documento Word che contiene un pulsante di comando ActiveX creato con C#")

## Come inserire un pulsante di comando ActiveX

La parte **come inserire activex** inizia con il metodo `InsertForms2OleControl`. Questo metodo crea un controllo basato su COM che Word tratta come un oggetto ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Perché funziona:** `OleControlType.CommandButton` indica ad Aspose.Words di creare il classico pulsante in stile VB. Le dimensioni e la posizione sono espresse in punti (1 punto = 1/72 di pollice), il che consente un controllo preciso del layout.

## Come aggiungere un pulsante di comando e impostare le dimensioni del pulsante

Dopo che il controllo è stato inserito puoi regolare le sue proprietà visive. Il passaggio **add command button** copre anche **set button size**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Spiegazione:**  

* `Caption` è l'etichetta visualizzata sul pulsante.  
* `Width` e `Height` ti permettono di **impostare le dimensioni del pulsante** dopo l'inserimento iniziale—utile quando le dimensioni dipendono da dati a runtime.  
* `Left` e `Top` riposizionano il controllo senza ricreare il documento.

> **Errore comune:** Dimenticare di usare i punti invece dei pixel farà apparire il pulsante troppo piccolo o troppo grande. Converti sempre i valori in pixel (`px * 72 / DPI`) se parti da misurazioni dello schermo.

## Come aggiungere un pulsante interattivo (opzionale)

Un pulsante ActiveX può eseguire una macro quando viene cliccato, ma incorporare codice VBA da C# è fuori dallo scopo di un flusso di lavoro puro Aspose.Words. Invece, puoi aggiungere una proprietà segnaposto che Word riconoscerà come nome di macro.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Quando l'utente apre il `.docx` generato in Word, cliccando il pulsante si tenterà di eseguire `MyMacroName`. Se la macro non esiste, Word chiederà all'utente di crearla.

**Perché potresti usarlo:** Per i moduli aziendali in cui una macro compila i campi, il codice C# deve solo posizionare il pulsante; la logica della macro vive nel progetto VBA del documento.

## Salva il documento e verifica il risultato

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Output previsto:** Aprendo `CommandButton.docx` in Microsoft Word viene mostrato un pulsante etichettato **Click Me** posizionato a 100 pts dal margine sinistro e a 120 pts dall'alto. Le dimensioni del pulsante sono **200 pts × 80 pts**. Cliccando il pulsante si attiva il segnaposto macro (se presente).

## Esempio completo funzionante

Di seguito trovi il programma completo e eseguibile che mette tutto insieme. Copialo in un nuovo progetto Console App, aggiungi il pacchetto NuGet Aspose.Words e esegui.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Esegui il programma, poi apri il file generato. Vedrai il **pulsante interattivo** pronto per ulteriori personalizzazioni.

## Domande frequenti

| Domanda | Risposta |
|----------|----------|
| **Funziona con .NET Core?** | Sì. Aspose.Words supporta .NET Standard, quindi lo stesso codice funziona su .NET 5/6/7. |
| **Posso usare altri controlli ActiveX (ad es., CheckBox)?** | Assolutamente. Sostituisci `OleControlType.CommandButton` con `OleControlType.CheckBox`, `OleControlType.OptionButton`, ecc. |
| **E se ho bisogno di un pulsante più grande su una pagina in orientamento orizzontale?** | Regola le proprietà `Width`, `Height`, `Left` e `Top` proporzionalmente. Ricorda che i punti rimangono gli stessi indipendentemente dall'orientamento della pagina. |
| **È necessaria una macro perché il pulsante sia cliccabile?** | No. Il pulsante è pienamente funzionale come elemento UI; una macro aggiunge solo un comportamento personalizzato al click. |

## Conclusione

Ora sai come **creare un documento Word** con Aspose.Words, **aggiungere un pulsante di comando**, **impostare le dimensioni del pulsante**, e facoltativamente collegare il pulsante a una macro per il comportamento di **add interactive button**. Questo approccio ti consente di automatizzare la creazione di moduli, generare report dinamici o costruire prototipi UI basati su Word direttamente da C#.

Successivamente, potresti esplorare:

* **Come inserire caselle di controllo ActiveX** per moduli di sondaggio.  
* **Come aggiungere contenuto di testo formattato** attorno al pulsante usando `DocumentBuilder`.  
* **Come proteggere il documento** mantenendo il pulsante funzionale.  

Sentiti libero di sperimentare con diversi tipi di controllo, dimensioni e nomi di macro per adattarli al tuo scenario specifico. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Inserisci immagine inline in documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Crea un documento Word con tabella usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}