---
category: general
date: 2026-11-18
description: Crea un documento Word vuoto e inserisci un pulsante ActiveX con C#.
  Scopri come aggiungere il controllo, impostare la didascalia del pulsante e salvare
  il file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: it
lastmod: 2026-11-18
og_description: Crea un documento Word vuoto e inserisci un pulsante ActiveX usando
  C#. Segui questo tutorial completo per aggiungere il controllo, impostare la didascalia
  del pulsante e salvare il risultato.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Crea un documento Word vuoto e inserisci un pulsante ActiveX – guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Crea un documento Word vuoto e inserisci un pulsante ActiveX
url: /it/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e inserisci un pulsante ActiveX

Se hai bisogno di **creare un documento Word vuoto** e posizionare al suo interno un pulsante ActiveX interattivo, questa guida ti mostra esattamente come farlo con Aspose.Words per .NET. Vedrai il codice completo, comprenderai perché ogni riga è importante e imparerai a **impostare la didascalia del pulsante** in modo che il controllo appaia pronto per l’interazione dell’utente.

Oltre all’obiettivo principale, tratteremo **come inserire ActiveX**, i passaggi **come aggiungere un controllo** a un file Word e le sfumature di **inserire un pulsante ActiveX** con una didascalia personalizzata. Alla fine avrai un modello riutilizzabile per qualsiasi scenario di automazione di documenti che richieda elementi UI incorporati.

## Cosa imparerai

* Come **creare un documento Word vuoto** programmaticamente.  
* Le chiamate API esatte necessarie per **inserire un pulsante ActiveX** e configurarne le proprietà.  
* Come **impostare la didascalia del pulsante** affinché il controllo mostri il testo desiderato.  
* Suggerimenti per salvare il file nella posizione desiderata e gestire le insidie più comuni.

### Prerequisiti

* .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+).  
* Aspose.Words per .NET installato (`Install-Package Aspose.Words`).  
* Familiarità di base con C# e Visual Studio o qualsiasi IDE compatibile con .NET.

---

## Crea un documento Word vuoto con Aspose.Words

Il primo passo è istanziare un oggetto `Document` vuoto. Questo oggetto rappresenta un file Word che non contiene contenuto finché non aggiungiamo qualcosa.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Perché è importante*: Un `Document` vuoto ti offre una tela pulita. Potrai aggiungere successivamente paragrafi, tabelle o controlli senza preoccuparti di formattazioni preesistenti.

---

## Inizializza un DocumentBuilder per lavorare con il documento

`DocumentBuilder` è una classe di supporto che ti permette di inserire contenuto nella posizione corrente del cursore. Tiene automaticamente traccia di dove ti trovi nel documento.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Perché è importante*: Senza un `DocumentBuilder` dovresti manipolare manualmente l’albero dei nodi a basso livello. Il builder semplifica l’inserimento di testo, immagini e controlli ActiveX.

---

## Come inserire un pulsante ActiveX (insert activex button)

Ora utilizziamo `InsertForms2OleControl` per incorporare un controllo ActiveX. Il metodo richiede tre argomenti:

1. Il tipo di controllo (`OleControlType.CommandButton`).  
2. Un nome interno per il controllo (usato da VBA o dal codice macro).  
3. Un `RectangleF` che definisce la posizione e le dimensioni sulla pagina.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Perché è importante*: Questo è il nucleo di **come inserire activex** in un documento Word. Le coordinate del rettangolo sono espresse in punti (1 punto = 1/72 di pollice). Regolale per posizionare il pulsante dove ti serve.

### Suggerimento

Se desideri che il pulsante compaia in una pagina specifica, sposta prima il cursore del builder:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Come impostare la didascalia del pulsante (set button caption)

Dopo aver posizionato il controllo, puoi modificarne le proprietà. La proprietà più visibile è `Caption`, che determina il testo mostrato sul pulsante.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Perché è importante*: Gli utenti vedono la didascalia, non il nome interno. Cambiarla rende il pulsante significativo nel documento finale.

---

## Salva il documento contenente il pulsante

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi formato supportato (`.docx`, `.pdf`, ecc.). Qui lo salviamo come documento Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Perché è importante*: Persistere il file ti permette di aprirlo in Microsoft Word e testare il pulsante. Quando il documento viene aperto, il pulsante apparirà con la didascalia “Press”.

### Risultato atteso

Aprendo `with_button.docx` in Word si visualizza una pagina vuota con un pulsante rettangolare etichettato **Press**. Cliccare il pulsante non produce alcuna azione di default perché non è associata alcuna macro VBA, ma il controllo è pienamente funzionante e può essere collegato a codice in seguito.

---

## Come aggiungere un controllo a un paragrafo specifico (how to add control)

A volte vuoi il pulsante all’interno di un paragrafo particolare, ad esempio dopo del testo istruttivo. Usa `MoveTo` per posizionare il builder prima di inserire il controllo.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Perché è importante*: Questo modello dimostra **come aggiungere un controllo** in contesto, garantendo che il layout del documento rimanga logico.

---

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|---------------|-----------|
| Il pulsante appare fuori dalla pagina | Le coordinate del rettangolo sono al di fuori dei margini | Usa `builder.PageSetup` per ottenere le dimensioni della pagina e calcolare un `RectangleF` sicuro. |
| La didascalia non viene visualizzata | `Caption` impostata prima che il controllo sia completamente inizializzato | Imposta `Caption` **dopo** la chiamata a `InsertForms2OleControl`, come mostrato al Passo 4. |
| Il documento si salva senza il pulsante | Il cursore del builder è stato spostato dopo l’inserimento senza confermare le modifiche | Mantieni il builder sulla stessa pagina o chiama `builder.Document.UpdatePageLayout()` prima di salvare. |

---

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Crea un file Word vuoto, inserisce un pulsante ActiveX, ne imposta la didascalia e salva il risultato.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output**: Dopo aver eseguito il programma, apri `C:\Temp\with_button.docx` in Microsoft Word. Vedrai una singola pagina con il testo “Below is an ActiveX button created programmatically:” seguito da un pulsante etichettato **Press**.

---

## Conclusione

Ora sai come **creare un documento Word vuoto**, **inserire un pulsante ActiveX**, **impostare la didascalia del pulsante** e **salvare** il risultato usando Aspose.Words per .NET. Lo stesso schema può essere esteso ad altri controlli ActiveX (checkbox, list box, ecc.) modificando `OleControlType`.  

Successivamente, potresti esplorare **come inserire eventi del pulsante ActiveX** con VBA, o **come aggiungere un controllo** a documenti esistenti che contengono già contenuto. Entrambi gli argomenti si basano direttamente sui concetti trattati qui.

Buona programmazione, e sentiti libero di sperimentare con diverse dimensioni, posizioni e didascalie per adattarle ai requisiti UI della tua applicazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un documento Word C# con un pulsante di comando ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Come aggiungere un pulsante ActiveX in un documento Word con Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}